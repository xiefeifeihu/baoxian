baoxian
=======
git配置使用方法：
1、京东上注册、登陆帐号，从中央代码库https://code.jd.com/twoface/tx-biz上派生一个到自己的仓库
2、切换到自己的操控中心，添加ssh公钥。使用ssh后就不用每次都输用户名和密码了。
	a、首先需要在Git中配置用户名和邮箱
		可通过git config命令，也可以在Git GUI中配置
	b、生成ssh密钥
		在项目文件夹下点右键进入“ssh bash”，输入命令 ssh-keygen -t rsa -C “you@example.com” ，按3个回车，密码为空。
		在用户文件夹下的.ssh文件夹中发现了两个文件，test_rsa和test_rsa.pub。将test_rsa.pub文件中的内容添加到京东代码库SSH中。
3、修改TortoiseGit的ssh client为Git提供的ssh客户端
	找到TortoiseGit -> Settings -> Network，将SSH client指向~\Git\bin\ssh.exe
	因为乌龟Git和Git冲突，可能会报“disconnected no supported authentication methods available(server sent: publickey，keyboard interactive）错误
4、从自己的私有代码库中clone代码库到本机
	git clone git@code.jd.com:你的用户名/tx-biz.git
	然后不停地写代码，提交git commit -m "备注信息"。
	要休息了，但某个任务在公司没干完时可以git push到私有库里，回家后git pull到家中电脑上继续开发。这一步用命令行、TortoiseGit、IDEA集成的git都可以完成。
5、某个任务完成后从私有代码库发布到中央代码库
	a、建立本地代码库到中央代码库的链接
		git remote add cc（cc是自己取的中央代码库的别名） git@code.jd.com:twoface/tx-biz.git
	b、将本地代码库同步到中央代码库
		git push cc
	这两步需用命令行或TortoiseGit客户端完成，IDEA不支持。TortoiseGit客户端Push时可以选择远程仓库目标地址。
