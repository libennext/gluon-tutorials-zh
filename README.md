<<<<<<< HEAD
# 通过MXNet/Gluon来动手学习深度学习

主页在 [https://zh.gluon.ai/](https://zh.gluon.ai/)

请使用 [https://discuss.gluon.ai](https://discuss.gluon.ai) 讨论或报告问题

## 如何贡献

所有notebook是用markdown格式存储，这样方便merge改动。jupyter可以通过notedown来直接使用markdown，[参考这里安装](./chapter00_preface/install.md#使用notedown插件来读写github源文件)

build服务器在 http://gluon-ci.mxnet.io 。这台服务器有一块Nvidia M60。

所有markdown文件需要在提交前清除output，它们会在服务器上重新执行生成结果。所以需要保证每个notebook执行不要太久，目前限制是4min。

在本地可以如下build html（需要GPU支持）

```bash
conda env update -f build/build.yml
source activate gluon_zh_docs
make html
```

生成的html会在`_build/html`。

如果没有改动notebook里面源代码，所以不想执行notebook，可以使用

```
make html EVAL=0
```

但这样生成的html将不含有输出结果。

## 编译PDF版本

编译pdf版本需要xelatex，和思源字体。在Ubuntu可以这样安装

```bash
sudo apt-get install texlive-full
```

```bash
wget https://github.com/adobe-fonts/source-han-sans/raw/release/OTF/SourceHanSansHWSC.zip
wget https://github.com/adobe-fonts/source-han-serif/raw/release/OTF/SourceHanSerifSC_EL-M.zip
unzip SourceHanSansHWSC.zip
unzip SourceHanSerifSC_EL-M.zip
sudo mv SourceHanSansHWSC SourceHanSerifSC_EL-M /usr/share/fonts/opentype/
sudo fc-cache -f -v
```

这时候可以通过 `fc-list :lang=zh` 来查看安装的中文字体。

然后可以编译了

```bash
make latex
cd _build/latex
xelatex -interaction nonstopmode gluon_tutorials_zh.tex
```
=======
## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/libennext/HOLLO-2/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/libennext/HOLLO-2/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
>>>>>>> upstream/master
