### 安装
  * 1.需要计算机上面已经安装了JDK
	* 2.下载和解压maven
	* 3.把maven解压后的根目录设置为一个系统环境变量，变量名为M2_HOME
	* 4.设置一个M2系统环境变量，变量值为M2_HOME的bin目录（windows系统为%M2_HOME%\bin）
	* 5.把M2变量设置为PATH变量的一部分。
	* 6.在command命令行程序输入mvn -version，输入版本号则为成功。
### POM文件
  * 1.每一个项目都需要有一个POM文件，该文件需要放置在项目的根目录。
	* 2.modelVersion应该设置为你正在使用的POM model版本，该版本需要对应你正在使用的maven版本。
	* 3.groupId是一个独一无二的ID，用于组织或者项目。通常情况下，它的值应该和你的Java顶级的package名字是一样的，比如com.zero
	* 4.artifactId说明了你正在构建的项目的名称
	* 5.versionId，说明了你正在构建的项目的版本号。
	* 6.POM文件可以继承，默认继承自super pom，如果没有super pom，则默认继承自base pom
	* 7.Effective POM，POM文件可以有自己的继承体系，这样一来，难以一下子知道统合起来的POM文件是怎么样的，于是可以输入mvn help:effective-pom来查看统合的POM文件，该文件称为Effective POM
### 仓库
  * 1.本地仓库：本地计算机的
  * 2.远程仓库：通常是公司的内网仓库，用于公司团队协作开发的。
  * 3.中央仓库：大家可以通过网络访问的公共仓库，比如maven的central仓库
### 标准布局
  * 1.官网参考路径：http://maven.apache.org/guides/introduction/introduction-to-the-standard-directory-layout.html
### 生命周期、阶段、目标
	* 1.maven的项目构建有三个生命周期：default,clean,site
	* 2.每个生命周期由若干个阶段(phases)构成，每个阶段由若干个目标(goals)构成。
  * 3.当输入mvn 生命周期 这样的格式的时候，这个生命周期下的所有阶段都会被执行。
	* 4.default生命周期有几个阶段：validate，compile，test,package,install,deploy。
	* 5.默认情况下，mvn走的是default生命周期，比如说，想要执行default的package阶段，则输入mvn package就可以了。
	* 6.执行某个阶段，则会连同这个阶段之前的所有阶段都先执行，比如执行compile，则会先执行validate，再执行compile。
### HelloWorld
	* 1.建立一个目录，作为项目的根目录，在里面放置一个pom文件，还有放置一个标准的maven布局，然后在src-main-java文件夹里面写一个HelloWorld文件
	* 2.在项目根目录输入mvn package，则maven会为你生成一个target目录，并将HelloWorld文件打包成jar包放入对应位置。
###	Maven Archetypes
	* 1.使用archetype命令能够让maven为你生成项目的模板，模板有很多种，可以在命令输入mvn archetype进行了解、
	* 2.输入 mvn idea:idea可以生成用于idea IDE的项目模板，然后从idea直接导入项目就可以了
	* 3.输入 mvn eclipse:eclipse可以生成用于eclipse IDE的项目模板。
### Maven Unit Test Report
	* 1.maven能够运行你的test代码，然后生成HTML文件，让你查看测试的结果怎么样。
	* 2.可以通过输入mvn surefire-report:report或者mvn surefire-report:report-only来得到你想要的测试结果。
	* 3，测试结果放置在your-project/target/site/surefire-report.html。
