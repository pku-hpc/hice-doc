# Hice文档
> 文档基于gitbook，部署在github pages上，支持中英文，文档网址为https://pku-hpc.github.io/hice-doc

## 文档开发流程

### 前期准备

* nodejs

  由于gitbook是用npm安装的，所以首先本地应配置node环境，直接全局安装可参考[链接](http://www.runoob.com/nodejs/nodejs-install-setup.html)，或者也可以通过安装[nvm](http://bubkoo.com/2017/01/08/quick-tip-multiple-versions-node-nvm/)来管理node。

* gitbook

  上一步成功后，直接执行

  ```shell
  npm install gitbook -g
  ```

  即可成功在本地配置gitbook环境。

### 修改文档

* 从仓库中克隆最新的文档

  ```shell
  git clone https://github.com/pku-hpc/hice-doc.git
  ```

  其中`en`下为英文文档，`zh`下为中文文档。

  新增或修改对应的中英文文档，进入对应的目录，增加自己的`markdown`文件并修改`SUMMARY.md`（目录结构文件）。

* 本地运行

  提交前先在本地运行，检查修改效果，首先需要安装依赖插件（katex, prism等），在`hice-doc/`目录下执行：

  ```shell
  gitbook install
  gitbook serve
  ```

  服务启动后可根据提示在`localhost:4000`下查看效果。

* 提交修改

  分为两步，`master`分支下为文档源码，`gh-pages`分支下为`github pages`静态站点的内容，即文档编译后的HTML文件，所以需要首先提交对master源码分支的修改。本地编译后生成的HTML文件在`hice-doc/_book`下，克隆`gh-pages`分支到本地

  ```shell
  git clone -b gh-pages https://github.com/pku-hpc/hice-doc.git
  ```

  将`hice-doc/_book`下的内容需拷贝到本地的`gh-pages`分支文件夹下，最后提交对`gh-pages`分支的修改。

## 其它

文档的数学公式由Katex渲染，添加数学公式时需按照对应语法，否则会报错，或显示不正确。

## 参考链接

[gitbook简明教程](http://www.chengweiyang.cn/gitbook/basic-usage/README.html)

[发布到Github Pages](http://www.chengweiyang.cn/gitbook/github-pages/README.html)