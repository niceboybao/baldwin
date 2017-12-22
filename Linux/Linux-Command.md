# Linux命令整合大全

## 1.最常用Linux命令

```sh
ls  显示文件或目录
cd  切换目录
pwd 查看当前文件目录
control+c npm ru的时候结束进程
```

## 2.命令格式：mv

```sh
[-fiv] source destination
参数说明：
-f:force，强制直接移动而不询问
-i:若目标文件(destination)已经存在，就会询问是否覆盖
-u:若目标文件已经存在，且源文件比较新，才会更新
```

### 案例：将/test1目录下的file1复制到/test3目录，并将文件名改为file2,可输入以下命令：

```sh
mv /test1/file1 /test3/file2
```
