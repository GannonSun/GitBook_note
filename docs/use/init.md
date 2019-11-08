# GitBook创建

## 建立GitHub仓库

首先我们先创建一个GitHub仓库，创建之后将他拉取到本地，在本地进行创建GitBook。

```
git clone xxxxxx.git
```

## 创建GitBook

在创建GitBook之前，为了方便我们之后发布到GitHub上，我们将对目录结构进行一些修改

```
//创建一个content文件夹存放gitbook文件
mkdir content
cd content
gitbook init
```

此时我们的目录结构应该是这样的：

```
gitbook_note
--content
  --SUMMARY.MD
  --README.MD
--README.MD
```

这时候你已经可以通过输入 gitbook serve /content /docs命令才启动本地测试环境了。

这里课外科普一下，/content是指gitbook init的目录，而后面那个/docs是指启动serve之后打包生成的html所存放的目录，如果不写的话，默认是存放到_book目录

这里可能有人会问了，为什么要把生成的文件存放到docs里，不能默认吗？这个你继续往下看就会明白。

由于这样的命令行实在是太长了，所以将它转换成一个node项目是一个好思路。进入到项目根目录下执行以下命令：

```
npm init -y
```

再次课外科普一下，这里的-y是指默认所有选择yes，直接生成默认的package.json。

命令执行之后，你们会发现根目录下多了一个package.json，狠狠地在IDE打开它，进行编辑。

```
"scripts": {
		"start": "gitbook serve ./content ./docs",
		"build": "gitbook build ./content ./docs",
		"test": "echo \"Error: no test specified\" && exit 1"
	},
```

在script中加入头两句，这个时候你就可以用npm start来启动服务了，然后用npm run build进行gitbook打包。

## GitBook发布到GitHub

在发布之前当然要先把我们刚刚所作的操作都提交到GitHub上，在项目根目录下打开git base here，执行以下命令：

```
git add .
git commit -m 'gitbook创建'
git push
```

提交之后到GitHub中检查代码是否成功提交，成功提交后来到仓库配置页面中，往下滑会看到一个Github Pages选项，Source 一项设置为 master branch docs folder 意思就是 master 分支的 docs 文件夹。

这个时候你应该就明白之前为什么我们要将生成的文件存放到docs文件夹里了吧，就是为了方便一键发布。

这时候你只需要访问Github Pages提示给你的url就好了。发布成功！

