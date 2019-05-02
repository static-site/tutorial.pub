# nginx.conf

```
worker_processes 2;
```

```
events {
     worker_connections 1024;
}
```

```
http {
     include mime.types;
     default_type application/octet-stream;
     sendfile on;
     keepalive_timeout 65;
     gzip on;

     upstream fastcgi_backend {
         server 127.0.0.1:9001;
         server 127.0.0.1:9002;
     }

     server {
         listen 8000;
         listen 192.168.100.4:80;
         
        location / {
            root D:/env/win/ProgramData/nginx/html;
            index index.html index.php;
            autoindex on;
            try_files $uri $uri/ /index.php$uri$is_args$args;
        }
        
        error_page 500 502 503 504 /50x.html;
        location = /50x.html {
            root html;
        }
        
        location ~ \.php($|/) {
            root D:/env/win/ProgramData/nginx/html;
            fastcgi_pass fastcgi_backend;
            fastcgi_read_timeout 150;
            fastcgi_index index.php;
            fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
            
            fastcgi_split_path_info ^(.+\.php)(/.*)$;
            fastcgi_param PATH_INFO $fastcgi_path_info;
            fastcgi_param RUNTIME_ENVIROMENT 'PRO';
            
            include fastcgi_params;
        }
    }
    
    server {
        listen 8080;
        listen 192.168.100.4:80;
        server_name taurus Pisces;
        
        location / {
            root D:/env;
            index index.html index.htm;
            autoindex on;
        }
    }
    
    server {
        listen 443 ssl;
        server_name urlnk.host;
        
        ssl_certificate D:/env/win/ProgramData/nginx/conf/cert/urlnk.host.crt;
        ssl_certificate_key D:/env/win/ProgramData/nginx/conf/cert/urlnk.host.key;
        
        ssl_session_cache shared:SSL:1m;
        ssl_session_timeout 5m;
        
        ssl_ciphers HIGH:!aNULL:!MD5;        
        ssl_prefer_server_ciphers on;
        
        location / {
            root D:/www/work/cdn;
            index index.html index.htm;
            autoindex on;
        }
    }
    
    include extra/vhosts.conf;
}
```
