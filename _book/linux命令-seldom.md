#### 【linux不常用但特别好用的命令】

- 查找一个目录的所有文件中"字段在哪个文件里"

  ```
  cd ./filename
  egrep -i -r "time.sleep"
  ```

- 将某个文件下的所以文件（不含文件夹）拷贝到另外一个目录下

  ```
  find 03 -type f -exec cp {} /home/target-path/
  ```

- 关闭筛选出来的所有进程（以edge浏览器为例子）

  ```
  ps -aux|grep msedge |awk '{print $2}'|xargs sudo kill -9
  ```

  