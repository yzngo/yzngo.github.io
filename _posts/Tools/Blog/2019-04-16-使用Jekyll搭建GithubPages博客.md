---
title: 使用Jekyll搭建GithubPages博客
date: 2019-04-16 14:10:00 +0800
categories: [Tools, Blog]
tags: [jekyll,blog]
---

记录Github Pages搭建流程，以备以后查阅。

## 资源网站

1. [http://jekyllthemes.org/](Jekyll官方主题站)



## 安装Jekyll Docs

跟随[Jekyll Docs](https://jekyllrb.com/docs/installation/)安装  `Ruby, RubyGems, Jekyll, Bundler`

- 具体步骤简单记录如下

    1. 安装  [RubyInstaller](https://rubyinstaller.org/)  -> [Ruby+Devkit 3.1.1-1 (x64)](https://github.com/oneclick/rubyinstaller2/releases/download/RubyInstaller-3.1.1-1/rubyinstaller-devkit-3.1.1-1-x64.exe) 

    2. 在安装向导的最后一步， 执行 `ridk install`

    3. 安装完成后打开一个新的终端，运行 `gem install jekyll bundler`

    4. 检查 Jekyll 是否安装成功 `jekyll -v`



## 创建Github Pages仓库

经过对比，最后选择了 [Chirpy](http://jekyllthemes.org/themes/jekyll-theme-chirpy/ ) 主题，下面的步骤是使用此主题的创建步骤，其他的也大同小异。

1. 登录Github，通过   [**Chirpy Starter**](https://github.com/cotes2020/chirpy-starter/generate) 创建新的repo, 命名为`[username].github.io`

2. 把此repo Push到本地。

3. 预览

    - 在仓库根目录运行
        - `Bundle`
        -  `bundle exec jekyll s`
    - 浏览器打开 _<http://127.0.0.1:4000>_

4. 部署**（仅第一次）**

    - 检查 `_config.yml`中的 url 是否配置成  `[username].github.io`

    - 确保 .github/workflows/pages-deploy.yml 文件存在

        - `on.push.branches` 应该和默认分支相同

    - 确保 tools/deploy.sh 存在

    - 更新lock file

        ```console
        bundle lock --add-platform x86_64-linux
        ```

    - Push and commit

        - 等待 GitHub Actions 运行完
        - 会增加一个新的分支 `gh-pages`

5. 发布

    - repo -> Settings -> Pages 

        - 修改Source为：`gh-pages   /(root) `
        - 保存



## 配置博客

1. 大多数配置都在 `./config.yml` 根据注释配置即可
    - 重点需要关注：url，avatar，timezone，lang
2. 配置favicon，参考： [2019-08-11-customize-the-favicon.md](https://github.com/cotes2020/jekyll-theme-chirpy/blob/master/_posts/2019-08-11-customize-the-favicon.md)
3. 启用GooglePV，参考：[2021-01-03-enable-google-pv.md](https://github.com/cotes2020/jekyll-theme-chirpy/blob/master/_posts/2021-01-03-enable-google-pv.md)



## 文章格式

1. 所有文件放到 `_posts` 文件夹下，子文件夹可以随意建立，对blog透明
2. 文件名约定格式 `YYYY-MM-DD-TITLE.md`
3. 网站上的文件夹， Tags 会根据文章中的元数据划分
4. [`Jekyll-Compose`](https://github.com/jekyll/jekyll-compose) - 一个文件生成工具，方便填写元数据



## Front Matter

[Front Matter](https://jekyllrb.com/docs/front-matter/) 为文章提供一系列的元数据，需要放到页首。

```yaml
---
title: TITLE
date: YYYY-MM-DD HH:MM:SS +0800					# 时间 + 时区
categories: [TOP_CATEGORIE, SUB_CATEGORIE]		# 大驼峰，最多两级
tags: [game, shader, c#,...]				# 全小写，使用单数

### 可选
pin: true								# 是否置顶，默认false
toc: false								# 是否显示目录，默认true
math: true								# 是否启用数学公式，默认false
mermaid: true							# 是否启用Mermaid图表，默认false
comments: false							# 是否开启评论 
image:									# 页首y图片
	path: 								# 图床路径，不能空
	w: 1000								# in pixels，不能空
	h: 400								# in pixels，不能空
	alt: This is an image.	  			# 替代文本，可空
author: <author_id>						# 如果在 _data/authors.yml中设置了作者信息
---
```



## 作者信息

1. 作者信息默认会从 `_config.yml` 中提取。

    ```yaml
    social.name
    social.links
    ```

2. 也可以自定义，新建文件 `_data/authors.yml`, 填入以下内容

    ```yaml
    <author_id>:
      name: <full name>
      twitter: <twitter_of_author>				# good for SEO
      url: <homepage_of_author>
    ```

    {: file="_data/authors.yml" }



## Upgrading

1. 修改 `Gemfile`{: .filepath} 更新主题版本

    ```diff
    - gem "jekyll-theme-chirpy", "~> 3.2", ">= 3.2.1"
    + gem "jekyll-theme-chirpy", "~> 3.3", ">= 3.3.0"
    ```

    {: .nolineno file="Gemfile" }

2. 执行以下命令

    ```console
    $ bundle update jekyll-theme-chirpy
    ```

3. 更新内容查看

    [Upgrade-Guide](https://github.com/cotes2020/jekyll-theme-chirpy/wiki/Upgrade-Guide)

