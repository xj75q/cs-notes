### wmctrl使用

> 这是一个允许您从命令行控制窗口管理器的工具。比xdotool要好用



#### 查看有哪些窗口：

```
wmctrl l
```

显示如下，第一列为id，第四列为name

```
0x02600008 -1 ubuntu Desktop
0x05400003  0 ubuntu /usr/bin/bash
0x06200003  0 ubuntu Sublime Text
```

#### 激活窗口（使用name激活）

```
wmctrl -a "/usr/bin/bash"
```



使用id激活

```
wmctrl -i -a 0x04e00007
```



#### 设置窗口的大小

```
wmctrl -i -r 0x0780004d -e 0,0,550,750,300
```

-e后面的参数说明：

```
第一个0，不用管
第二个0，屏幕的x坐标
第三个550，屏幕的y坐标
第四个750，浏览器的长度
第四个300，浏览器的高度
```





#### 将窗口至于最前

```
wmctrl -i -r 0x0780004d -e 0,0,550,750,300  -b add,above
```

其中，-b后面的参数是有用的，-b后面参数选项：

```
add,above 表示设置为最前
remove,above表示最前设置的取消
```



