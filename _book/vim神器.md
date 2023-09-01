> 在编程过程中，一把好的兵器就是一个好的战斧，使你能够更高效的完成所布置的任务。而vim恰恰是一个不可多得的兵器。下面开始"锻造"之旅

#### 【vim的安装】

新的linux系统在使用的时候，自带的vim是不好用的，需要卸载并更新到最新的vim，才能更好的使用

```
sudo apt remove vim-common
sudo apt install vim 
```

**注意：都2023年了，已经不需要使用apt-get了，直接apt就可以**

#### 【配置vim颜色】

1> 在用户跟目录下创建 .vim文件夹

```
mkdir ~/.vim
```

2> 在~/.vim 新建colors 文件夹，之后会将GitHub中的*.vim文件移动到这里

```
cd ~/.vim
mkdir colors
```

3> 在~/.vim 文件夹下git clone 颜色主题，和colors目录平级

```
git clone https://github.com/flazz/vim-colorschemes.git
```

4> 进入到vim-colorschemes 文件夹里的colors文件夹下，拷贝出所有的vim文件到colors

```
cd vim-colorschemes/colors

cp *.vim ~/.vim/colors
```

5> vi随便打开一个文件，在里面先手动设置主题颜色

```
:colorscheme twilight256
```

6> 要想永久生效，需要更改vimrc（有些是在根目录下的~/.vimrc）

```
vi /etc/vim/vimrc

在任意一行加入 

colorscheme twilight256 这一行
```

7> 如果想要在不同的编辑框内使用默认的vim，需要在bashrc里面加入新的alias

```
vi ~/.bashrc

alias vib='vi --clean -c "set number"'

source ~/.bashrc
```

这时候在打开新的终端，直接用vib来打开，如果想保持不变，还是用vi打开文件



#### 【vim的使用命令】

1> 常用命令

```
i   进入编辑模式
：wq 保存并退出，另外，小写的x也可以实现。 （：x 会更快一些）
esc键进入命令模式，不能输入
h 左键
j 下键
k 上键
l 右键
yy 复制 ； n行 yy，复制n行
p 粘贴
dd 删除 ； n dd 删除指定的行数 ； D删除光标后面的所有内容；d0 删除光标前本行的所有内容
dw 删除光标开始位置的字，包含光标所在字符。
u 一步一步撤销
ctr + r 反撤销
. 点表示重复上一次操作的命令。
gg=G 自动缩进
w 向后移动一个字
b 向前移动一个字
{ 按段移动，上移
} 按段移动，下移
G 移动到指定行，行号
M 光标移动到中间行
o 向上直开一行，插入一行
O 向下 直开一行，插入行首
A 插入行末，一行最尾部
I 插入行首，一行最头部。
L 将光标移到最后一行行首
G 将光标移到文件末尾
gg 光标移动到文件开头
x 删除光标后一个字符，相当于del
X 删除光标前一个字符，相当于backspace
a 光标之后插入一个字符，与i 相反
ctr + d 向下翻半屏
ctr +u 向上翻半屏
ctr +f 向下翻一屏
ctr +b 向上翻一屏
v： 按字符移动，选中文本
V 按行移动
p 在光标所在位置向下新开一行，粘贴
：%s/abc/456/g 替换命令
：1,10s/abc/456/g 末行模式下，将第一行至第十行之间的abc替换成456
：x退出，很快
r 替换当前字符； R 替换当前行光标后的字符。
dw 删除一个单词
：3-8> 第3行到第8行向右移动
V选中之后，一个>向右移多少格
shift +6 也就是 ^可以跳到一行的行首；或者home键
shift+4 也就是 $ 可以跳到一行的行尾。

```



2> vim其他常用搜索命令

```
/  在搜索命令下，正向搜索
？ 在搜索命令下，反向搜索
n  继续搜索下一个匹配的单词
N 继续搜索上一个匹配的单词
* 在normal下，正向搜索当前光标下的单词
# 在normal下，反向搜索当前光标下的单词
```



3> 对应键（相反键）

```

w-b 向下，向上一个单词

w-b 向下，向上一个单词

ctr + d 向下翻半屏；ctr +u 向上翻半屏

ctr +f 向下翻一屏：ctr +b 向上翻一屏

b在快捷键里面有两个作用，b是向上跳一个单词，ctr+b是向上翻一屏

G 移动到文件末尾；gg移动到文件开头

x----del ；X-----backspace

u----撤销；ctr+ r 反撤销

点是重复上一次操作的命令

’ > 文本行 右移

’ < 文本行 左移

r 替换当前字符；R替换当前光标后的字符。
```

4> VIM高级搜索命令

> 为了更好的进行搜索，vim支持正则表达式

```
^ 一行的开头
$ 一行的结尾
.  任意一个字符
* 匹配0次或n次
```

5> 高阶玩法(**都是在esc模式下**)

（1）删除引号中的内容

```
di"  光标定位到引号里面，删除"中的内容
```

（2）跳转到一行最前面

```
0
```

（3）跳转到一行最末尾

```
$
```

（4）删掉光标之前的字

```
d0
```

（5）删除光标之后的所有字

```
d$
```

（6) 删除一个单词、行首、行尾、整行

```
x:删除当前光标处字符
dw:删除当前光标处一个单词
d0:删除光标处到行首的字符
d$:删除光标处到行尾的字符
dd:删除整行
ndd:删除n行
di"  删除"中的内容
```

（7）替换

```
:%s/abc/456/g 替换命令
```

#### 【set命令】

```
:set number                " 显示行号
:set nonumber            " 关闭行号


:set tabstop=4             " 设置 tab space 为4个空格
:set ts=4                " 同 tabstop
:set expandtab            " 将tab替换为指定数量的空格
:set autoindent            " 设置为自动缩进

:set background=dark        " 设置背景颜色

:set guifont=consolas:h14        " 设置字体为 consolas，字号为14


:set history=700        " 设置保存命令的行数


:set autoread        " 设置当文件变化时，自动读取新文件


:set wrap        " 启动折行
:set nowrap        " 禁止折行


" 切换文件格式，ff是 fileformat 的缩写
:set ff=unix            " 将文件切换为 unix 格式，每行以 "\n" 结尾
:set ff=dos                " 切换为 Windows 格式，每行以 "\r\n" 结尾


" 设置编码格式
:set encoding=utf-8            " 设置 vim 展示文本时的编码格式
:set fileencoding=utf-8        " 设置 vim 写入文件时的编码格式

:set filetype=html            " 设定文件类型，方便语法高亮

:set hlsearch                " 高亮显示搜索结果

:set paste                    " 设置为 paste 模式，在粘贴前设置该模式，可以避免各种 auto-formating
:set nopaste                " 切换回 normal 模式
```

**注意：在命令行模式下，也就是“：”模式下，不能输入多条set指令以下都是不起作用的**

以下这些执行不成功：

```
:colo default;set numer
:set numer && colo default
:set colo default numer
```

