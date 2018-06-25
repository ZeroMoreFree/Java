### 下载和安装resin
  * 去到resin官网下载zip文件，有pro版本的，pro版本需要付费，也可以选择不付费的非pro版本。
  * 将resin的解压路径设置为RESIN_HOME环境变量
  * 解压后在根目录下有setup的程序，可以直接运行这个程序，设置相关的JDK参数，生成一个resin服务器。
  * 根目录下同时还有resin.exe这样子的程序，可以直接运行，用于控制resin的start或者stop。
  * start之后，在浏览器输入localhost:8080,有default页面则视为安装成功。
### 部署
  * start了服务器之后，将一个web应用打包成war包，放入resin目录的webapps目录下，即可访问项目。
  
### 商务平台的部署
  * resin的部署方式有好几种，并不是一定要将项目打包成war文件放入webapps下面。也可以用配置文件告诉resin项目的所在。
  * 商务平台的启动命令如下：/usr/bin/java -Dfile.encoding=UTF-8 -Dsvr=resin-portal -jar /usr/local/resin/lib/resin.jar -resin-home /usr/local/resin -conf /home/faier/etc/resin/portal.conf start，是在启动resin的时候，告诉resin，通过/home/faier/etc/resin/portal.conf文件去寻找项目，仔细的项目参数就配在该文件里面。
  * 我以前开发一直用的web2.5的规范，忘了在3.0规范中,web.xml文件并不是必要的。同时，由于以前的项目比较小，都不是用servlet，而是直接用jsp写的，所以就更用不到web.xml文件了。
