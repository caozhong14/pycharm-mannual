# pycharm-mannual
problems for record
<a href = http://www.jianshu.com/p/79df9ac88e96>如何通过pycharm实现远程代码的调试和开发</a>
144 作者 如烟花非花
2017.04.27 15:57 字数 954 阅读 98评论 0喜欢 2
写在前面

前段时间去总部出差，实现一个功能的交接工作，因为分公司的网络和总部的内网有所隔离，并且远程安装的系统为centos server版本，所以调试bug比较困难。于是打算通过pycharm远程连接到服务器上，通过同步本地和服务器代码进行远程调试。
环境准备

默认的开发语言是python，那么python开发的一个重要事项是包管理。想想那么多负责的包，如果没有好的包管理系统，在本机搭建一个包环境是多么复杂。于是放弃了本地构建包的想法——使用远程包。
pycharm作为一款强大的IDE，很好的实现了这个功能。

    1.点击file->settings，找到如图示所示的页面（project Interpreter），点击下拉框后边的设置图标，能找到红框标识的选项，点击“Add Remote”。

        图示1.png

    2.这里选择ssh这种方式连接，这块没什么好说的，按照要填写的信息填写好点确定就ok了。

    图示2.png
    ３.上述这部完成后还需要注意一个细节，看下图，这里需要把这个也给设置了，这个就是需要把你本地的工程和远程的工程对接起来。

    图示3.png
    4.分别按照步骤将local path和remote path选择好。其中local path对应本地的工程位置，remote path对应要连接的工程的位置。

    图示4.png
    5.设置完后得到的结果如下，然后点击ok退出设置。

    图示5.png

至此，等待IDE加载完这些包，包环境已经搞定了，这时候点击运行已经能执行了，看到下图的执行结果说明配置成功了。这个时候，不管是运行还是调试，运行调用的环境和代码都是远程的了，打断点调试也可以执行了。（注意: 这里的本机代码必须和服务器代码相同，否则断点可能不是期望的那个断点位置。）

图示6.png
更进一步

上面已经能满足远程调试的需求了，但是调试意味着要修改一部分代码。前面调试注意点说到要统一两边的代码，那么问题来了，我们该一两行代码，难道要用ssh来回改文件么？其实不用！接着往下看。

    1.创建开发模式的sftp连接。设置位置如下图：

    图示7.png
    2. 点击加号，弹出下框，名字自己填，type下拉选择sftp，弹出框后，按照需求把相关的字段填好。如图示9所示。

        图示8.png


        图示9.png
    3.完成图示9的操作时候，不要着急关闭，选择红框所示的右边的“Mappings”这个标签页，把红框标识的两个路径选择好，还是第一个是本地工程的路径，第二个路径是远程服务器上面的工程路径。完成图示10，此时可以点击ok。

    图示10.png

搞定上述的那些操作，就可以随意的修改代码和远程代码进行随意同步了。

图示11.png

这里改了一部分代码，只需要点击右键，然后选择下图的选项，两边的代码就同步了。

图示12.png

ok，从现在开始，像本机一样开发吧。
