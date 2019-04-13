# Socket编程基础

**TCP：传输控制协议面向连接，可靠的数据传输协议**

**UDP：用户数据报协议无连接，不可靠的数据连接协议**

**IP：尽力而为交付服务**

![1550802608344](/home/changyin/.config/Typora/typora-user-images/1550802608344.png)

### 应用层协议定义了：

**交换报文类型，例如请求报文和响应报文 **

**各种报文类型的语法，如报文中各个字段的定义以及这些字段的描述**

**字段的语义，即这些字段中包含信息的含义**

**一个进程何时以及如何发送报文，对文件进行响应的规则**



### 可供应用程序使用的运输服务

**应用程序服务要求：**

**可靠数据传输 **

**吞吐量 **

**定时 **

**安全性**

### SOCKET() 创建 SOCKET

**int socket(int domain, int type, int protocol);**

**domain: AF_INET, AF_INET6, AF_LOCAL, AF_ROUTE**

**type: SOCK_STREAM, SOCK_DGRAM, SOCK_PACKET, SOCK_SEQPACKET**

**protocol:  IPPROTO_TCP,  IPPTOTO_UDP, IPPROTO_STCP, IPPROTO_TIPC**

**返回值：Socket 文件描述符**



### BIND()绑定IP地址及端口

**int bind(int sockfd, const struct sockaddr *addr, socketlen_t addrlen);**

**sockfd是调用socked返回的文件描述符。**

**addr 是指数据结构struct sockaddr的指针，它保存你的地址(即端口和IP地址）信息。**

**addrlen设置为sizeof(struct sockaddr)**

**返回值：-1为错误，并设置errno**



### LISTEN()监听SOCKET

**int listen(int sockfd, int backlog);**

**sockfd是调用socket()返回的套接字文件描述符。**

**backlog是在进入队列中允许的链接数目。**

**返回值：发生错误的时候返回-1， 并设置全局错误变量errno**

### CONNECT()建立链接

**int connect(int sockfd, const struct sockaddr *addr, socklen_t addrlen);**

**sockfd 是系统调用socket() 返回的套接字文件描述符。**

**addr是保存着目的端口和IP地址的数据结构 struct sockaddr**

**addrlen 设置为sizeof(struct sockaddr)**

**返回值：-1为错误， 并设置errno**



### ACCEPT()接收链接

**int accept(int sockfd, struct sockaddr  *addr, socklen_t *addrlen);**

**函数说明： accept()用来接受参数sockfd的socket连线。**

**参数sockfd的socket必须先经bind(), listen()函数处理过，当有连线进来时accept()会返回一个新的sockfd处理代码，往后的数据传送与读取就是经由新的socket处理，而原来参数socket的socket能继续使用accept()来接受新的连线要求。连接成功时，参数addr所指的结构会被系统填入远程主机的地址数据，参数addrlen为scokaddr的结构长**

**返回值：成功则返回新的socket处理代码，失败返回-1，错误原因存于errno中**



### GETPEERNAME()获取对端地址

**int getpeername(int sockfd, struct sockaddr *addr, int *addrlen);**

**sockfd 是连接的流式套接字的描述符。**

**addr是一个指向结构struct sockaddr (或者是struct sockaddr_in) 的指针，它保存着连接的另一边的信息。**

**addrlen 是一个int 型的指针， 他初始为sizeof(struct sockaddr)。**

**返回值：函数在错误的时候返回-1， 设置相应的errno**

**后续操作：inet_ntoa, gethostbyaddr**



### GETHOSTNAME()获取本地主机名

**int gethostname(char *hostname, size_t size);**

**hostname 是一个字符数组指针，他将在函数返回时白村主机名。**

**size 是hostname数组的字节长度。**

**返回值：函数调用成功时返回0，失败时返回-1， 并设置errno。**

### SEND() 发送数据

**int send(int sockfd, const void *msg, int len, int flags);**

**~sockfd是你想发送数据的套接字描述符(或者是调用socket() 或者是accept()返回的。)msg是指你想发送的数据的指针。len是数据长度，flags 设置为0就可以啦。**

**返回值：返回实际发送的数据的字节数。**

**错误的时候返回-1，并设置errno**



### RECV()接收数据

**int recv(int sockfd, void *buf, int len, unsigned int flags);**

**sockfd 是要读的套接字描述符**

**buf 是要读的信息的缓冲**

**len 是缓冲的最大长度**

**flags 可以设置为0**

**返回值：实际读入缓冲的数据的字节数。或者在错误的时候返回-1，同时设置errno**

### **函数原型：**

int socket(int **domain**, int ***type***, int ***protocol***);

参数说明：　　

**domain**：协议域，又称协议族（family）。常用的协议族有AF_INET、AF_INET6、AF_LOCAL（或称AF_UNIX，Unix域Socket）、AF_ROUTE等。协议族决定了socket的地址类型，在通信中必须采用对应的地址，如AF_INET决定了要用ipv4地址（32位的）与端口号（16位的）的组合、AF_UNIX决定了要用一个绝对路径名作为地址。

***type***：指定Socket类型。常用的socket类型有SOCK_STREAM、SOCK_DGRAM、SOCK_RAW、SOCK_PACKET、SOCK_SEQPACKET等。流式Socket（SOCK_STREAM）是一种面向连接的Socket，针对于面向连接的TCP服务应用。数据报式Socket（SOCK_DGRAM）是一种无连接的Socket，对应于无连接的[UDP](https://baike.baidu.com/item/UDP)服务应用。

***protocol***：指定协议。常用协议有IPPROTO_TCP、IPPROTO_UDP、IPPROTO_STCP、IPPROTO_TIPC等，分别对应TCP传输协议、UDP传输协议、STCP传输协议、TIPC传输协议。

注意：1.type和protocol不可以随意组合，如SOCK_STREAM不可以跟IPPROTO_UDP组合。当第三个参数为0时，会自动选择第二个参数类型对应的默认协议。

2.WindowsSocket下***protocol***参数中不存在IPPROTO_STCP　　

返回值：

如果调用成功就返回新创建的[套接字](https://baike.baidu.com/item/%E5%A5%97%E6%8E%A5%E5%AD%97)的描述符，如果失败就返回INVALID_SOCKET（Linux下失败返回-1）。套接字描述符是一个整数类型的值。每个进程的进程空间里都有一个套接字描述符表，该表中存放着套接字描述符和套接字数据结构的对应关系。该表中有一个字段存放新创建的套接字的描述符，另一个字段存放套接字数据结构的地址，因此根据套接字描述符就可以找到其对应的套接字数据结构。每个进程在自己的进程空间里都有一个套接字描述符表但是套接字数据结构都是在操作系统的[内核](https://baike.baidu.com/item/%E5%86%85%E6%A0%B8)缓冲里。

**绑定**

函数原型：

int bind(SOCKET ***socket***, const struct sockaddr* ***address***, socklen_t ***address_len***);

参数说明：

***socket***：是一个[套接字](https://baike.baidu.com/item/%E5%A5%97%E6%8E%A5%E5%AD%97)描述符。

***address***：是一个sockaddr结构[指针](https://baike.baidu.com/item/%E6%8C%87%E9%92%88)，该结构中包含了要结合的地址和[端口号](https://baike.baidu.com/item/%E7%AB%AF%E5%8F%A3%E5%8F%B7)。

**address_len**：确定address[缓冲区](https://baike.baidu.com/item/%E7%BC%93%E5%86%B2%E5%8C%BA)的长度。

返回值：

如果函数执行成功，返回值为0，否则为SOCKET_ERROR。

**接收**

函数原型：

int recv(SOCKET **socket**, char FAR* ***buf***, int **len**, int ***flags***);

参数说明：　　

***s******ocket***：一个标识已连接[套接口](https://baike.baidu.com/item/%E5%A5%97%E6%8E%A5%E5%8F%A3)的描述字。

**buf**：用于接收数据的[缓冲区](https://baike.baidu.com/item/%E7%BC%93%E5%86%B2%E5%8C%BA)。

**len**：缓冲区长度。

***flags***：指定调用方式。取值：MSG_PEEK 查看当前数据，数据将被复制到缓冲区中，但并不从输入队列中删除；MSG_OOB 处理[带外数据](https://baike.baidu.com/item/%E5%B8%A6%E5%A4%96%E6%95%B0%E6%8D%AE)。

返回值：

若无错误发生，recv()返回读入的字节数。如果连接已中止，返回0。否则的话，返回SOCKET_ERROR错误，应用程序可通过WSAGetLastError()获取相应[错误代码](https://baike.baidu.com/item/%E9%94%99%E8%AF%AF%E4%BB%A3%E7%A0%81)。

函数原型：

ssize_t recvfrom(int ***sockfd***, void ***buf***, int ***len***, unsigned int ***flags***, struct socketaddr* ***from***, socket_t* ***fromlen***);

参数说明：

***sockfd***：标识一个已连接[套接口](https://baike.baidu.com/item/%E5%A5%97%E6%8E%A5%E5%8F%A3)的描述字。

***buf***：接收[数据缓冲区](https://baike.baidu.com/item/%E6%95%B0%E6%8D%AE%E7%BC%93%E5%86%B2%E5%8C%BA)。

***len***：缓冲区长度。

***flags***：调用操作方式。是以下一个或者多个标志的组合体，可通过or操作连在一起：

（1）MSG_DONTWAIT：操作不会被阻塞；

（2）MSG_ERRQUEUE： 指示应该从套接字的错误队列上接收错误值，依据不同的协议，错误值以某种辅佐性消息的方式传递进来，使用者应该提供足够大的缓冲区。导致错误的原封包通过msg_iovec作为一般的数据来传递。导致错误的数据报原目标地址作为msg_name被提供。错误以sock_extended_err结构形态被使用。

（3）MSG_PEEK：指示数据接收后，在接收队列中保留原数据，不将其删除，随后的读操作还可以接收相同的数据。

（4）MSG_TRUNC：返回封包的实际长度，即使它比所提供的缓冲区更长， 只对packet套接字有效。

（5）MSG_WAITALL：要求阻塞操作，直到请求得到完整的满足。然而，如果捕捉到信号，错误或者连接断开发生，或者下次被接收的数据类型不同，仍会返回少于请求量的数据。

（6）MSG_EOR：指示记录的结束，返回的数据完成一个记录。

（7）MSG_TRUNC：指明数据报尾部数据已被丢弃，因为它比所提供的缓冲区需要更多的空间。　　

**/\*(MSG_TRUNC使用错误,4才是MSG_TRUNC的正确解释)\*/**

（8）MSG_CTRUNC：指明由于缓冲区空间不足，一些控制数据已被丢弃。

（9）MSG_OOB：指示接收到out-of-band数据(即需要优先处理的数据)。

（10）MSG_ERRQUEUE：指示除了来自套接字错误队列的错误外，没有接收到其它数据。

***from***：（可选）[指针](https://baike.baidu.com/item/%E6%8C%87%E9%92%88)，指向装有源地址的缓冲区。

**fromlen**：（可选）指针，指向from缓冲区长度值。

**发送**

函数原型：

int sendto( SOCKET **s**, const char FAR* ***buf***, int ***size***, int ***flags***, const struct sockaddr FAR* ***to***, int ***tolen***);

参数说明：

***s***：[套接字](https://baike.baidu.com/item/%E5%A5%97%E6%8E%A5%E5%AD%97)

***buf***：待发送数据的缓冲区

**size**：缓冲区长度

***flags***：调用方式标志位, 一般为0, 改变Flags，将会改变Sendto发送的形式

***addr***：（可选）[指针](https://baike.baidu.com/item/%E6%8C%87%E9%92%88)，指向目的套接字的地址

***tolen***：addr所指地址的长度

返回值：

如果成功，则返回发送的字节数，失败则返回SOCKET_ERROR。

**接收连接请求**

函数原型：

int accept( int **fd**, struct socketaddr* ***addr***, socklen_t* ***len***);

参数说明：

***fd***：套接字描述符。

***addr***：返回连接着的地址

***len***：接收返回地址的缓冲区长度

返回值：

成功返回客户端的文件描述符，失败返回-1。