### 安装
  1.需要计算机上面已经安装了JDK
	2.下载和解压maven
	3.把maven解压后的根目录设置为一个系统环境变量，变量名为M2_HOME
	4.设置一个M2系统环境变量，变量值为M2_HOME的bin目录（windows系统为%M2_HOME%\bin）
	5.把M2变量设置为PATH变量的一部分。
	6.在command命令行程序输入mvn -version，输入版本号则为成功。
### POM文件
  1.每一个项目都需要有一个POM文件，该文件需要放置在项目的根目录。
	2.modelVersion应该设置为你正在使用的POM model版本，该版本需要对应你正在使用的maven版本。
	3.groupId是一个独一无二的ID，用于组织或者项目。通常情况下，它的值应该和你的Java顶级的package名字是一样的，比如com.zero
	4.artifactId说明了你正在构建的项目的名称
	5.versionId，说明了你正在构建的项目的版本号。
	6.POM文件可以继承，默认继承自super pom，如果没有super pom，则默认继承自base pom
	7.Effective POM，POM文件可以有自己的继承体系，这样一来，难以一下子知道统合起来的POM文件是怎么样的，于是可以输入mvn help:effective-pom来查看统合的POM文件，该文件称为Effective POM
### 仓库
  1.本地仓库：本地计算机的
  2.远程仓库：通常是公司的内网仓库，用于公司团队协作开发的。
  3.中央仓库：大家可以通过网络访问的公共仓库，比如maven的central仓库
### 标准布局
  1.官网参考路径：http://maven.apache.org/guides/introduction/introduction-to-the-standard-directory-layout.html
  
