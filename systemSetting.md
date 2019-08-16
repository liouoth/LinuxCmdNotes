# 系统管理命令

### 【ps】

【描述】ps(Process Status的缩写)，常用来列出进程。ps命令列出的是使用命令时刻进程的快照。

>  【主要参数】
>
>  e	显示所有进程,环境变量
>  f	全格式
>  h	不显示标题
>  l	长格式
>  w	宽输出
>  a	显示终端上地所有进程,包括其他用户地进程
>  r	只显示正在运行地进程
>  x	显示没有控制终端地进程
>  u	以用户为主的格式来显示程序状况
>  au	显示较详细的资讯
>  aux	显示所有包含其他使用者的行程
>  -C<命令>	列出指定命令的状况
>  --lines<行数>	每页显示的行数
>  --width<字符数>	每页显示的字符数
>  --help	显示帮助信息--version	显示版本显示

##### 【示例】

常用：

列出全进程：ps -ef 和 ps-aux

查找进程：ps -ef | grep xxx 捕捉名为xxx的进程



### 【kill】发送信号

【描述】kill 命令很容易让人产生误解，以为它仅仅就是用来杀死进程的。我们来看一下 man page 对它的解释：kill - send a signal to a process.

​		从官方的解释不难看出，kill 是向进程发送信号的命令。当然我们可以向进程发送一个终止运行的信号，此时的 kill 命令才是名至实归。事实上如果我们不给 kill 命令传递信号参数，它默认传递终止进程运行的信号给进程！这是 kill 命令最主要的用法，也是本文要介绍的内容。

> **参数说明**：
>
> - -l <信息编号> 　若不加<信息编号>选项，则-l参数会列出全部的信息名称。
> - -s <信息名称或编号> 　指定要送出的信息。
> - [程序] 　[程序]可以是程序的PID或是PGID，也可以是工作编号。

示例：一般用于进程终止，当kill后面跟着进程号时，默认发送 kill -15以正常方式终结进程

kill 123 以正常的方式终止123进程 

kill -KILL 123强制终止123

kill -9 123 彻底杀死123

使用我们可以使用ps -ef | grep 捕捉到进程pid，然后再用kill去终结进程

> 【可发送信号】
>
> ```shell
> # kill -l
> 1) SIGHUP     2) SIGINT     3) SIGQUIT     4) SIGILL     5) SIGTRAP
> 6) SIGABRT     7) SIGBUS     8) SIGFPE     9) SIGKILL    10) SIGUSR1
> 11) SIGSEGV    12) SIGUSR2    13) SIGPIPE    14) SIGALRM    15) SIGTERM
> 16) SIGSTKFLT    17) SIGCHLD    18) SIGCONT    19) SIGSTOP    20) SIGTSTP
> 21) SIGTTIN    22) SIGTTOU    23) SIGURG    24) SIGXCPU    25) SIGXFSZ
> 26) SIGVTALRM    27) SIGPROF    28) SIGWINCH    29) SIGIO    30) SIGPWR
> 31) SIGSYS    34) SIGRTMIN    35) SIGRTMIN+1    36) SIGRTMIN+2    37) SIGRTMIN+3
> 38) SIGRTMIN+4    39) SIGRTMIN+5    40) SIGRTMIN+6    41) SIGRTMIN+7    42) SIGRTMIN+8
> 43) SIGRTMIN+9    44) SIGRTMIN+10    45) SIGRTMIN+11    46) SIGRTMIN+12    47) SIGRTMIN+13
> 48) SIGRTMIN+14    49) SIGRTMIN+15    50) SIGRTMAX-14    51) SIGRTMAX-13    52) SIGRTMAX-12
> 53) SIGRTMAX-11    54) SIGRTMAX-10    55) SIGRTMAX-9    56) SIGRTMAX-8    57) SIGRTMAX-7
> 58) SIGRTMAX-6    59) SIGRTMAX-5    60) SIGRTMAX-4    61) SIGRTMAX-3    62) SIGRTMAX-2
> 63) SIGRTMAX-1    64) SIGRTMAX
> ```











