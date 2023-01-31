# 备忘录
> 记录一些常用的命令或方法以免找不到。
## Linux tar命令
Linux tar（英文全拼：tape archive ）命令用于备份文件。
tar 是用来建立，还原备份文件的工具程序，它可以加入，解开备份文件内的文件。
通常，我们会用tar命令来实现解压缩操作。
### 常规打包/解包

```
# 打包文件（tar默认只是打包不压缩，参数-z打包后进行gzip压缩，参数-j打包后进行bzip2压缩）
tar -cvf files.tar 目录名 文件名 # 得到files.tar打包文件
tar -zcvf files.tar.gz 目录名 文件名 # 得到files.tar.gz打包文件
tar -jcvf files.tar.bz2 目录名 文件名 # 得到files.tar.bz2打包文件

# 查看备份文件中的文件
tar -tf files.tar # 只是列出文件
tar -tvf files.tar # 列出文件，包括文件信息

# 删除备份文件中的指定文件
tar -vf files.tar --delete ./a.txt

#解包文件
tar -xvf files.tar # 解包files.tar
tar -zxvf files.tar.gz # 解包files.tar.gz
tar -jxvf files.tar.bz2 # 解包files.tar.bz2
```
参数：
- -c：--create 创建一个新的归档（压缩包）
- -v：--verbose 详细的列出处理的文件
- -f：--files=ARCHIVE 使用档案文件或设备（通常必选）
- -x：解包
### 其他参数

```
--exclude 目录名/文件名 # 排除所选打包范围内的某些文件
-A/--catenate # 新增文件到已存在的备份文件
```
### 加密打包/解包
tar打包时本身无法进行加密处理，通常使用openssl命令来加密。

```
# 使用openssl通过des3算法进行加密并用pbkdf2进行口令加密，得到加密打包文件files.tar.gz
tar -czvf - 目录名 文件名 | openssl des3 -pbkdf2 -k 密码 -out files.tar.gz

# 将当前目录下的filess.tar.gz进行解密解包
openssl des3 -d -pbkdf2 -k 密码 -in files.tar.gz | tar xzvf -
```
