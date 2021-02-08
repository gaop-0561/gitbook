# gitbook

1. 首先需要安装NodeJs，具体步骤详见[官网](https://nodejs.org/en/)；

2. 通过npm安装gitbook的命令行工具，`npm install gitbook-cli -g`；

3. 通过命令行工具安装gitbook，`gitbook install`；

4. 在自己电脑上新建一个文件夹，在命令行中进入该目录；

5. 在命令行中执行`gitbook init`来初始化这个目录为gitbook的目录，初始化后该目录下会自动生成两个文件；

   1. `SUMMARY.md` : 这是一个主目录文件，这个文件非常重要，后面新增加的文件都需要到这里登记才能被访问！
   2. `README.md`: 首页文件，可以修改里面的内容，不能删除，也不能移动。

6. 增加第一篇文章；

   1. 一般会新建一个目录，例如`mkdir md`，创建一个md的文件夹；
   2. 在新的目录下新建第一个markdown文件，`touch gitbook.md`;
   3. 把新添加的文件加入到 `SUMMARY.md`文件中，`* [Gitbook](md/gitbook.md)`；

7. 运行预览gitbook，`gitbook serve`，从提示中可以看到，已经在`http://127.0.0.1:4000`启动了一个服务器，在浏览器中打开这个地址，可以看到现在一共有两个文件，默认生成的`README`和我们新建的`Gitbook`；

8. `gitbook serve`命令可以监控文件的变化，只要文件保存后，服务会重新编译并发布；

9. `gitbook serve`命令执行后可以看到文件加中多了一个`_book`目录，这个就是我们在浏览器中看到的HTML页面；

10. 发布到github上，使用Github pages服务提供在线查看；

    1. 首先需要有一个github的账号，然后新建一个仓库，这两部太简单了，就不啰嗦了；

    2. 因为github pages发布的时候只能选择`root`或者`docs`目录，根目录我们放了原始的Markdown文件，所以我们需要把HTML文件放到`docs`目录下；

    3. 修改`gitbook serve`命令为`gitbook serve . ./docs`，意思是把HTML文件输出到`docs`目录下，然后我为这个命令起了个别名，`echo 'alias gbs="gitbook serve . ./docs"' >> ~/.zshrc | source ~/.zshrc`；

    4. 使用gbs部署并预览，然后删掉默认的`_book`目录，`rm -r _book`；

    5. 目前项目目录如下：

       ```sh
       ➜  gitbook git:(master) ✗ tree -L 2
       .
       ├── README.md											首页文件
       ├── SUMMARY.md										目录文件
       ├── docs													生成的HTML文件加
       │   ├── gitbook
       │   ├── index.html
       │   ├── search_index.json
       │   └── src
       └── src														源文件加
           └── gitbook.md								源文件
       
       4 directories, 5 files
       ```

    6. 把本地的文档推送到github上；

       ```sh
       git add .
       git commit
       git push -u origin master
       ```

    7. 在github的仓库中选择`Settings`页面，找到`Github Pages`，在Source中选择master分支和docs目录，点击Save后就开始部署了，部署完成后可以通过上方的链接进行访问；

       ![image-20210208143412997](https://img-1259707131.cos.ap-shanghai.myqcloud.com/20210208143413.png)

