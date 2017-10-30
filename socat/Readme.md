http://www.dest-unreach.org/socat/

https://github.com/hctsaie/socat-windows

https://stackoverflow.com/questions/34791674/socat-port-forwarding-for-https
Change 127.0.0.1 to A Website in hosts file

http://palimpsest.minivi.com/socat/portforwarding/
Port Forwarding / Redirection Using socat

http://zoomq.qiniudn.com/ZQScrapBook/ZqFLOSS/data/20120319170018/index.html
再來一個大家喜歡用的例子。在一個NAT環境，如何從外部連接到內部的一個端口呢？只要能夠在內部運行socat就可以了。
外部：c:\>socat tcp-listen:1234 tcp-listen:3389
內部：c:\>socat tcp:outerhost:1234 tcp:192.168.12.34:3389
這樣，你外部機器上的3389就影射在內部網192.168.12.34的3389端口上。

再看文件傳遞的例子。nc也經常用來傳遞文件，但是nc有一個缺點，就是不知道文件什麼時候傳完了，一般要用Ctrl+c來終止，或者估計一個時間，用-w參數來讓他自動終止。用socat就不用這麼麻煩了：
on host 1: c:\>socat -u open:myfile.exe,binary tcp-listen:999
on host 2: c:\>socat -u tcp:host1:999 open:myfile.exe,create,binary
這個命令把文件myfile.exe用二進制的方式，從host 1 傳到host 2。-u 表示數據單向流動，從第一個參數到第二個參數，-U表示從第二個到第一個。文件傳完了，自動退出。

https://unix.stackexchange.com/questions/316923/is-there-a-way-to-make-socat-not-open-the-target-connection-until-it-receives-a


http://www.jianshu.com/p/432f893037a2


http://brieflyx.me/2015/linux-tools/socat-introduction/

http://www.rubyguides.com/2012/07/socat-cheatsheet/

https://artkond.com/2017/03/23/pivoting-guide/


https://www.seceye.cn/821.html
