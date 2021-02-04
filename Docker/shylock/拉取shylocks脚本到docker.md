1.在自己的github新建一个仓库，仓库名字随意，但是要记住这个名字，在第5步的时候要用上，选择为公开的仓库，名字随意即可，然后点击Actions，点击set up a workflow yourself，把sync-shylocks-Loon-main.yml文件内的代码粘贴进去后，点击Start commit。
2.点击右上角的个人头像，Settings -> Developer settings -> Personal access tokens -> Generate new token，Note栏随意填写，勾选repo、workflow，点击下方绿色的Generate token，复制并找个地方储存一下绿色勾的那一串字符。
3.回到刚刚你自己新建的仓库，Settings -> Secrets -> New repository secret，Name栏只能填写PAT，Value栏只能填写刚刚存储的那一串字符，然后点击绿色的Add secret。
4.点击Actions，点击All woekflows，选择shylocks-Loon-master，点击Run workflow，等待一下就同步完成了。
5.打开自己的docker京东文件夹，找到config文件夹，在文件夹里面新建一个diy.sh文件，并打开diy.sh.sample文件按要求修改好第四行，第四行很重要，第三行就自己去自己的仓库里面看你需要拉取什么脚本，有几个例子在里面了，自己写上就好，最后再把diy.sh.sample文件内的代码复制粘贴到diy.sh文件内并保存。
6.编辑config.sh文件，找到EnableExtraShell这个变量，双引号内填写true，然后保存文件。
7.在服务器输入命令，docker exec -it 容器名 bash git_pull，容器名这里一般是jd，除非你自己创建容器的时候没有使用默认的命令。
8.编辑crontab.list文件，例子为：30,31 12-23/1 * * * bash jd shylocks_jd_live_redrain_half，因为这些拉取的脚本名不能以jd_开头，所以就在拉取脚本的时候自动给脚本加上了shylocks_区别开。
