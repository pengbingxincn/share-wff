# 1、jupyter notebook 安装

## 1.1 通过pip安装所需套件

```
pip3 install jupyter notebook
pip3 install pandoc #可以将笔记导出为pdf格式
pip3 install jupyter-cjk-xelatex #pandoc所需套件
```

## 1.2 打开运行环境 jupyter notebook

```
jupyter notebook
```



## 1.3 配置jupyter 默认笔记本保存路径

```
jupyter notebook --generate-config

#找到配置文件jupyter_notebook_config.py里面的

#更改工作目录
##The directory to use for notebooks and kernels.
#c.NotebookApp.notebook_dir = ‘工作目录绝对路径’
```

## 1.4 设置jupyter notebook网络访问

### 生成密码

进入Python编译器中执行

```python
from notebook.auth import passwd 
p = passwd() 
print(p)
```

这个时候就会让你设置密码。
连续输入两次密码后，你会得一个字符串（**sha1:…**），也就是加密后的密码，如图所示：

![image-20211205212535531](C:\Users\helloff\AppData\Roaming\Typora\typora-user-images\image-20211205212535531.png)

**把得到的这个字符串复制下来。**



### 把密码写入配置文件

打开jupyter_notebook_config.py文件。
![image-20211205212643808](C:\Users\helloff\AppData\Roaming\Typora\typora-user-images\image-20211205212643808.png)

保存，完成。

重启Jupyter Notebook,会要求你输入密码：

<img src="C:\Users\helloff\AppData\Roaming\Typora\typora-user-images\image-20211205212752466.png" alt="image-20211205212752466" style="zoom: 50%;" />

## 1.5jupyter notebook常用插件安装

### jupyter_contrib_nbextensions、ipywidgets、Autopep8插件安装

```
pip3 install ipywidgets autopep8 jupyter_contrib_nbextensions jupyter_nbextensions_configurator

jupyter contrib nbextension install

jupyter nbextensions_configurator enable

jupyter nbextension enable
```



### 安装完，常用选项卡

1 Table of Contents：更容易导航

2 Autopep8：轻轻一击就能获得简洁代码
3 variable inspector：跟踪你的工作空间
4 ExecuteTime：显示单元格的运行时间和耗时
5 隐藏代码输入：隐藏过程，展示结果#隐藏所有输入的插件让你能够立即隐藏 notebook 中的所有代码，只保留结果。
6 Collapsible headings：这个扩展在大型Notebook中非常有用，可折叠的标题能帮你收起/放下Notebook中的某些内容，使整个页面看起来更干净整洁。
7 Notify：这是Jupyter Notebook中的通知机制，有时如果需要跑一些耗时较久的任务，你会把它放在一边自己去做别的事，而Notify功能就能在任务处理完后及时向你发送通知。
8 Code folding：在Jupyter Notebook中，你能折叠的不只有标题，还有代码。
9 tqdm_notebook：这事实上不是Notebook原有的插件。tqdm原本是一个Python模块，它可以为循环代码显示执行进度条，但有时它无法在Jupyter Notebook上工作。几天前，Jupyter Notebook新加入了tqdm_notebook扩展，从此你就无需再为进度条担忧了。
10 %debug：这也不是Notebook原生的。它最初是IPython magic的一个命令，支持两种激活调试器的方式：一是在执行代码之前激活调试器，二是在验尸模式下激活调试器。简而言之，就是当代码出现异常后，输入%debug可以直接激活调试器跳到出现错误的地方，而且你还可以检查前后代码情况。它实现了即时调试+快速迭代，更多细节可以参考Radek Osmulski的推文。
11 Hinterland：勾选此插件为代码单元格中的每次按键启用“代码自动补全”菜单，而不是仅用Tab键时启用。
12 Snippets Menu：向Jupyter笔记本添加可定制的菜单项，以插入代码片段、样板文件和示例。勾选此插件后，会多出一个Snippets的菜单项，菜单里包含多个模块的示例，通过简单的点击就能生成示例代码，可根据自己的需求稍作修改即可运行，减少代码工作量。
13 Scratchpad：为Jupyter Notebook提供一个草稿cell，方便随时测试输出。
一些小型扩展和特殊技巧
%lsmagic：执行%lsmagic，它会列出所有可用的IPython magics。
Zen mode extension：隐藏活动状态栏，方便你把注意力集中在代码上。
Execute time extension：显示运行的时间。
autoreload：无需退出Jupyter Notebook就能动态修改代码。它的具体操作是：
%load_ext autoreload
%autoreload 2
ipywidgets：ipywidgets是交互HTML小工具, 主要有一个安装 ipywidgets, 会同时安装 widgetsnbextension

### 让jupyter notebook支持markdown格式的.md文件格式

用pip安装notedown：
pip install notedown
打开配置文件jupyter_notebook_config.py（前文已有），添加或者找到相应设置修改：
c.NotebookApp.contents_manager_class = ‘notedown.NotedownContentsManager’

## jupyter notebook主题设置

### 安装

pip3 install jupyterthemes

## 列出可用主题

jt -l
Available Themes:

chesterish
grade3
gruvboxd
gruvboxl
monokai
oceans16
onedork
solarizedd
solarizedl

### 选择主题

jt -t onedork

### 恢复默认主题

jt -r

### 下面例子供参考：

```
jt -t monokai -f roboto -nf robotosans -tf robotosans -N -T -cellw 70% -dfs 10 -ofs 10
```



### 字体

主题可以更改字体，但对于字体有要求，不是所有字体都可以使用，如果只希望修改字体的话，对于chrome有个最简单的方法修改字体：
chrome->设置->自定义字体->宽度固定的字体、



## 配置代码提示与自动补齐

```
pip install jupyter_contrib_nbextensions

jupyter contrib nbextension install --user

pip install jupyter_nbextensions_configurator

jupyter nbextensions_configurator enable --user
```

安装完成后打开Jupyter Notebook。此时可以看到菜单项上（与Files、Running等一行）增加了一个Nbextensions；点击Nbextensions进行配置如图，勾选Hinterland

<img src="C:\Users\helloff\AppData\Roaming\Typora\typora-user-images\image-20211205213034266.png" alt="image-20211205213034266" style="zoom: 67%;" />







配置可更换环境

```
pip install ipykernel
```

安装完成之后，重启jupyter notebook 可以看到kernel选项



![image-20211205213250899](C:\Users\helloff\AppData\Roaming\Typora\typora-user-images\image-20211205213250899.png)

手动添加你的kernel（需要添加的环境）到jupyter

```
Python -m ipykernel install --user --name torchV 
```

