# Mxnet-Gluon 学习记录

这里的内容是我基于 李沐-动手学机器学习 的个人记录！

这里的主要内容fork自github，并添加个人理解和一些心得体会。以后可能会增加一些个人的代码，并不确定！

————————————————————————————————————————————————————————————
————————————————————————————————————————————————————————————

## 官方主页及讨论区

主页在 [https://zh.gluon.ai/](https://zh.gluon.ai/)

请使用 [https://discuss.gluon.ai](https://discuss.gluon.ai) 讨论或报告问题

将门直播 https://www.douyu.com/1086863

## 如何贡献

所有notebook是用markdown格式存储，这样方便merge改动。jupyter可以通过notedown来直接使用markdown，[参考这里安装](./chapter00_preface/install.md#使用notedown插件来读写github源文件)

build服务器在 http://gluon-ci.mxnet.io 。这台服务器有一块Nvidia M60。

所有markdown文件需要在提交前清除output，它们会在服务器上重新执行生成结果。所以需要保证每个notebook执行不要太久，目前限制是4min。

在本地可以如下build html（需要GPU支持）

```{.python .input}
conda env update -f build/build.yml
source activate gluon_zh_docs
make html
```

生成的html会在`_build/html`。

如果没有改动notebook里面源代码，所以不想执行notebook，可以使用

```{.python .input}
make html EVAL=0
```

但这样生成的html将不含有输出结果。

## 编译PDF版本

编译pdf版本需要xelatex，和思源字体。在Ubuntu可以这样安装

```{.python .input}
sudo apt-get install texlive-full
```

```{.python .input}
wget https://github.com/adobe-fonts/source-han-sans/raw/release/OTF/SourceHanSansHWSC.zip
wget https://github.com/adobe-fonts/source-han-serif/raw/release/OTF/SourceHanSerifSC_EL-M.zip
unzip SourceHanSansHWSC.zip
unzip SourceHanSerifSC_EL-M.zip
sudo mv SourceHanSansHWSC SourceHanSerifSC_EL-M /usr/share/fonts/opentype/
sudo fc-cache -f -v
```

这时候可以通过 `fc-list :lang=zh` 来查看安装的中文字体。

然后可以编译了

```{.python .input}
make latex
cd _build/latex
xelatex -interaction nonstopmode gluon_tutorials_zh.tex
```
