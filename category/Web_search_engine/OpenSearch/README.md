# OpenSearch
http://www.opensearch.org/

https://github.com/dewitt/opensearch

## 自动发现 / 新闻供稿
```html
<link rel="search"
      type="application/opensearchdescription+xml"
      href="http://example.com/content-search.xml"
      title="Content search" />
```
- HTML：head 元素里
- RSS: channel 元素里，<atom:link />
- Atom: feed 元素里

## 添加搜索到浏览器

## 描述文档

```xml
<?xml version="1.0" encoding="UTF-8"?>
<OpenSearchDescription xmlns="http://a9.com/-/spec/opensearch/1.1/">
  <ShortName>Web Search</ShortName>
  <Description>Use Example.com to search the Web.</Description>
  <Tags>example web</Tags>
  <Contact>admin@example.com</Contact>
  <Url type="application/rss+xml"
       template="http://example.com/?q={searchTerms}&amp;pw={startPage?}&amp;format=rss"/>
</OpenSearchDescription>
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<OpenSearchDescription xmlns="http://a9.com/-/spec/opensearch/1.1/">
  <ShortName>Web Search</ShortName>
  <Description>Use Example.com to search the Web.</Description>
  <Tags>example web</Tags>
  <Contact>admin@example.com</Contact>
  <Url type="application/atom+xml"
       template="http://example.com/?q={searchTerms}&amp;pw={startPage?}&amp;format=atom"/>
  <Url type="application/rss+xml"
       indexOffset="0"
       template="http://example.com/?q={searchTerms}&amp;pw={startPage?}&amp;format=rss"/>
  <Url type="text/html"
       template="http://example.com/?q={searchTerms}&amp;pw={startPage?}"/>
  <Url type="application/json"
       rel="suggestions"
       template="http://example.com/suggest?q={searchTerms}" />
  <Url type="application/opensearchdescription+xml"
       rel="self"
       template="http://example.com/osd.xml" />
  <LongName>Example.com Web Search</LongName>
  <Image height="64" width="64" type="image/png">http://example.com/websearch.png</Image>
  <Image height="16" width="16" type="image/vnd.microsoft.icon">http://example.com/websearch.ico</Image>
  <Query role="example" searchTerms="cat" />
  <Developer>Example.com Development Team</Developer>
  <Attribution>
    Search data Copyright 2005, Example.com, Inc., All Rights Reserved
  </Attribution>
  <SyndicationRight>open</SyndicationRight>
  <AdultContent>false</AdultContent>
  <Language>en-us</Language>
  <OutputEncoding>UTF-8</OutputEncoding>
  <InputEncoding>UTF-8</InputEncoding>
</OpenSearchDescription>
```

### 元素

#### OpenSearchDescription
- 根节点
- XML 命名空间：http://a9.com/-/spec/opensearch/1.1/

#### ShortName
- 必要
- <= 16 个纯文本字符

#### Description
- 必要
- <= 1024 个纯文本字符

#### Url
- 必要

属性：
##### type
- 必须的
- 必须为有效的 MIME type

##### template
- 必须

##### rel
- results（默认）
- suggestions
- self
- collection

##### indexOffset
- 必须为整数
- 默认 1

##### pageOffset
- 必须为整数
- 默认 1

---

更加完善和友好：

#### Tags
- <= 256 个纯文本字符
- 单个或者空格字符分隔

#### LongName
- <= 48 个纯文本字符

#### Image

属性：
##### height
- 必须是非负整数

##### width
- 必须是非负整数

##### type
- 必须为有效的 MIME type

#### Query
搜索客户端可以使用此示例查询来验证搜索引擎是否正常工作


---

署名和权利：

#### Contact
- 必须符合 RFC 2822 地址规范

#### Deveploer
创建描述文档的个人或实体
- <= 64 个纯文本字符



#### Attribution
内容的所有来源或实体
- <= 256 个纯文本字符

#### SyndicationRight
查询、显示和重新分发此搜索结果的程度


---

内容限制、语言和编码：

#### AdultContent
- false（默认）
- true


#### Language
- 默认 *
- 必须符合 RFC 5646 规范定义

#### InputEncoding
- 默认 UTF-8

#### OutputEncoding
- 默认 UTF-8



## 网址模板

```xml
<!-- 参数名前缀 -->
<Url type="application/rss+xml"
     xmlns:example="http://example.com/opensearchextensions/1.0/"
    template="http://example.com?q={searchTerms}&amp;c={example:color?}"/>
```

### 参数
参数名后加问号“?”，代表是可选的（并且可以用空字符串替换）

#### searchTerms
- 必须

#### count
- 必须是非负整数

#### startIndex
- 必须是整数

#### startPage
- 必须是整数

---

上文（描述文档元素）已经介绍过：

#### language

#### inputEncoding

#### outputEncoding




## 查询元素

```xml
<Query role="request" searchTerms="cat" startPage="1" />

<!-- 更正“OpenSurch”拼写 -->
<Query role="correction" searchTerms="OpenSearch" totalResults="854000" title="Spelling correction" />

<!-- 自定义扩展角色 -->
<Query xmlns:custom="http://example.com/opensearchextensions/1.0/"
       role="custom:synonym"
       title="Synonym of 'cat'"
       searchTerms="feline" />

<!-- 自定义扩展参数 -->
<Query xmlns:custom="http://example.com/opensearchextensions/1.0/"
       role="example"
       searchTerms="cat"
       custom:color="blue"
       title="Sample search" />
```

### 属性

#### role
- 必须的
- 可选值：example，request，correction，related，subset，superset

#### title
包含描述搜索请求的人类可读的纯文本字符串
- <= 256 个纯文本字符

#### totalResults
- 必须是非负整数

---

上文（网址模板参数）已经介绍过：

#### searchTerms

#### count

#### startIndex

#### startPage

#### language

#### inputEncoding

#### outputEncoding



## 响应元素

搜索结果页例子：
```xml
<?xml version="1.0" encoding="UTF-8"?>
<rss version="2.0"
     xmlns:opensearch="http://a9.com/-/spec/opensearch/1.1/"
     xmlns:atom="http://www.w3.org/2005/Atom">
  <channel>
    <title>Example.com Search: New York history</title>
    <link>http://example.com/New+York+history</link>
    <description>Search results for "New York history" at Example.com</description>
    <opensearch:totalResults>4230000</opensearch:totalResults>
    <opensearch:startIndex>21</opensearch:startIndex>
    <opensearch:itemsPerPage>10</opensearch:itemsPerPage>
    <atom:link rel="search" type="application/opensearchdescription+xml" href="http://example.com/opensearchdescription.xml"/>
    <opensearch:Query role="request" searchTerms="New York History" startPage="1" />
    <item>
      <title>New York History</title>
      <link>http://www.columbia.edu/cu/lweb/eguids/amerihist/nyc.html</link>
      <description>
        ... Harlem.NYC - A virtual tour and information on
        businesses ... with historic photos of Columbia's own New York
        neighborhood ... Internet Resources for the City's History. ...
      </description>
    </item>
    <!-- ... -->
  </channel>
</rss>
```

### 元素

#### Query
上文（查询元素）已经介绍过

#### itemsPerPage
- 必须是非负整数

---

上文（查询元素属性）已经介绍过：

#### totalResults

#### startIndex


### HTML 中的响应元数据
head 属性 profile 和 meta 元素
```html
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
  <head profile="http://a9.com/-/spec/opensearch/1.1/" >
    <title>Example.com Search: New York history</title>
    <link rel="search"
          type="application/opensearchdescription+xml"
          href="http://example.com/opensearchdescription.xml"
          title="Example.com Web Search" />
    <meta name="totalResults" content="4230000"/>
    <meta name="startIndex" content"1"/>
    <meta name="itemsPerPage" content="10"/>
  </head>
  <body>
    <ul>
      <li>
        <a href="http://www.columbia.edu/cu/lweb/eguids/amerihist/nyc.html">
          New York History
        </a>
        <div>
          ... Harlem.NYC - A virtual tour and information on
          businesses ... with historic photos of Columbia's own New York
          neighborhood ... Internet Resources for the City's History. ...
        </div>
      </li>
      <!-- ... -->
    </ul>
  </body>
</html>
```
