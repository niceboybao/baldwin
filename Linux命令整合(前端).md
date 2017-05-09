## Linux命令整合大全

### 1.命令格式：mv
```
[-fiv] source destination
参数说明：
-f:force，强制直接移动而不询问
-i:若目标文件(destination)已经存在，就会询问是否覆盖
-u:若目标文件已经存在，且源文件比较新，才会更新
```

#### 案例：将/test1目录下的file1复制到/test3目录，并将文件名改为file2,可输入以下命令：

```
mv /test1/file1 /test3/file2
```

### 2.命令格式 ls cd 
```
ls  显示文件或目录
cd  切换目录
```

