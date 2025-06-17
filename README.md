参考链接
https://blog.ackerven.com/archives/91/  

[管理个人访问令牌 - GitHub 文档 ](https://docs.github.com/zh/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#创建-personal-access-token-classic) 

主要步骤分为：初始化公开仓库、新建个人令牌、新建私有仓库存储博客源文件、设置私有仓库的Action。

## 一、初始化公开仓库

可以先建个README文件，确保已经初始化。



## 二、新建个人令牌  

新建个人令牌参考GitHub文档。

然后在私有仓库的`Setting->Secrets and variables->Actions`里新建secret来存储刚刚的个人令牌

## 三、创建Action

在私有仓库里新建`.github/workflows/deploy.yml`文件

填入以下内容

```yaml
name: Deploy Jekyll site to GitHub Pages

on:
  push:
    branches:
      - master #分支名称
  workflow_dispatch:  

jobs:
  build-deploy:
    runs-on: ubuntu-latest
    permissions:
      contents: write  
    steps:
      - name: Checkout source code
        uses: actions/checkout@v4
        with:
          persist-credentials: false 
          fetch-depth: 0
      - name: Set up Ruby
        uses: ruby/setup-ruby@v1
        with:
          ruby-version: '3.1'

      - name: Install dependencies
        run: |
          gem install bundler
          bundle install

      - name: Build Jekyll site
        run: |
          bundle exec jekyll build

      - name: Deploy to GitHub Pages
        run: |
          cd _site
          git init
          git checkout -b gh-pages #分支名称
          git add -A
          git -c user.name="GitHub Actions" -c user.email="actions@github.com" commit -m "Deploy via GitHub Actions"
          git remote add origin https://${{secrets.这里是刚刚创建的secret的名字}}@github.com/用户名/用户名.github.io.git
          git push origin gh-pages -f -q
```
