# Hooks



## 同步多个仓库
1. 在 GitHub 新建一个仓库，并在 Gitee 导入这个库
2. 远程服务器克隆这个库，并且添加 remote gitee
3. 编写钩子脚本
   ```sh
   git pull origin master
   git push gitee master
   ```
4. 添加 GitHub Webhooks
    http://api.urlnk.com/v1/git/hooks
