# ApkRepackage
## Apk反编译重新打包

### 1.工具下载地址
[apktool](http://ibotpeaches.github.io/Apktool/install/)

[dex2jar](http://sourceforge.net/projects/dex2jar/files/)

[jd-gui](http://jd.benow.ca/)

[ procyon](https://bitbucket.org/mstrobel/procyon)





### 2.反编译

**反编译apk资源文件**
> apktool d demo.apk

**反编译代码**

*把apk解压缩后，得到classes.dex*
*Mac在终端商执行.sh文件*
> d2j-dex2jar classes.dex
*如果出现Permission denied权限问题，可以在文件夹用以下命令求情权限*
>chmod a+x *.sh

*得到classes.jar后，可以用jd-gui打开查看class代码，也可以用procyon反编译成java代码*
> java -jar procyon.jar -jar classes.jar -o out


### 3.加入新的类
例如要加入test.java文件。
比较容易的办法是把test.java放入到一个新的Android工程中，如法炮制，用apktool反编译后，得到smali文件。
把这个smali文件复制到demo.apk反编译后的文件夹中。
另，AndroidManifest中的内容可以直接修改。

### 4.重新打包
>apktool b [文件夹] -o demo2.apk

### 5.重新签名
用AndroidStudio 任意生成一个证书 栗子： *1.jks*

**jarsigner工具在JDK/bin目录下**
>jarsigner V:\build\demo2.apk -keystore  V:\build\1.jks -storepass 123456 1 -keypass 123456


