---
title: \[개인 프로젝트\] 소켓통신의 이해 악성메일 훈련도구 개발
excerpt: MS워드 매크로를 이용한 훈련용 바이러스와 서버 개발
categories: dev
---  

CHAPTER. 01 소켓통신 프로그램
=============================

Point. 01 TCP/IP
----------------

1.  TCP 프로토콜

-   전송계층에서 동작하는 연결 지향 서비스

-   Segment 단위로 전송 된다.

    1.  TCP 정보 확인

-   netstat 명령어로 TCP 프로토콜의 활성 상태를 확인 할 수 있다.

> [![]({{site.url}}/assets/images/mail/image2.png)]({{site.url}}/assets/images/mail/image2.png)  
> \[그림\] netstat 명령어

-   서버와 클라이언트 간에 연결이 완료 되면 ESTABLISHED 상태가 된다.

    1.  3-way handshaking

-   클라이언트와 서버 간에 연결을 수행 하는 방법이다

-   Client가 SYN을 보내 연결요청을 하면 Server는 SYN/ACK로 응답을 하고
    응답을 받은 Client는 ACK를 보내어 연결을 확립하고 Established 상태가
    된다.

-   이때 서버는 Listen 상태로 응답을 기다린다.

> [![]({{site.url}}/assets/images/mail/image3.png)]({{site.url}}/assets/images/mail/image3.png)  
> \[그림\] 3-way handshaking  


> [![]({{site.url}}/assets/images/mail/image4.png)]({{site.url}}/assets/images/mail/image4.png)  
> \[그림\] localhost 서버와 클라이언트 간 3-way handshaking 동작 스니핑  


Point. 02 리눅스 윈도우 통신 프로그램
-------------------------------------

1.  리눅스 서버 프로그램

    1.  sys/socket.h

-   네트워크 통신 라이브러리

-   소켓 인터페이스 자료형, 구조체, 함수들을 정의 한다.

    2.  소켓 생성

```c
	int server_socket, client_socket;
        struct sockaddr_in server_addr, client_addr;
        char buff[BUFF_SIZE];
	int client_addr_size;
	server_socket = socket(PF_INET,SOCK_STREAM,0);
	server_addr.sin_family	= AF_INET;
	server_addr.sin_port		= htons(5000);
	server_addr.sin_addr.s_addr	= htons(INADDR_ANY);
	bind(server_socket, (struct sockaddr*)&server_addr, sizeof(server_addr));
	listen(server_socket,7);
        client_addr_size=sizeof(client_addr);
```  

> PF_INET : IPv4 인터넷 프로토콜  
>SOCK_STREAM : 양방향 연결 기반 바이트 스트림을 제공하는 소켓유형 TCP 사용  
> server_addr.sin_family = AF_INET; : IPv4 인터넷 주소패밀리  
> server_addr.sin_port = htons(5000); : 5000번 포트 사용  
> server_addr.sin_addr.s_addrv = htons(INADDR_ANY); : 모든 IP에 대해 연결요청 처리  

> accept — 새로운 연결을 수락한다.  
> bind — 소켓에 주소를 할당한다.  
> connect — 소켓을 연결한다.  
> getpeername — 상대 소켓의 주소를 얻는다.  
> getsockname — 소켓의 주소를 얻는다.  
> getsockopt — 소켓 옵션을 얻는다.  
> listen — 소켓 연결을 대기한다.  
> recv — 연결 소켓에서 메시지를 수신한다.  
> recvfrom — 소켓에서 메시지를 수신한다.  
> recvmsg — 소켓에서 메시지를 수신한다.  
> send — 소켓으로 메시지를 전송한다.  
> sendmsg — 소켓으로 메시지 구조를 이용하여 전송한다.  
> sendto — 소켓으로 메시지를 전송한다.  
> setsockopt — 소켓 옵션을 설정한다.  
> shutdown — 소켓의 송/수신을 멈추게 한다.  
> socket — 새로운 소켓을 생성한다.  


3.  연결 요청 수락 및 메시지 수신

```cpp
client_socket=accept(server_socket, (struct sockaddr*)&client_addr, &client_addr_size);
                                memset(packet,0x00,sizeof(packet));
                                recv (client_socket, packet, BUFF_SIZE, 0);
                                printf("Connect Done : %s\n",packet);
close(client_socket);
close(server_socket);
```  

> client_socket=accept(server_socket, (struct sockaddr\*)&client_addr, &client_addr_size);  
클라이언트 IP로 연결 요청 수락  

> recv (client_socket, packet, BUFF_SIZE, 0);  

> printf(\"Connect Done : %s\\n\",packet);  
메시지 수신 및 출력  

2.  리눅스 클라이언트

    1.  리눅스 클라이언트 프로그램

```cpp
int client_socket;
   struct sockaddr_in   server_addr;
   char   buff[BUFF_SIZE];
   client_socket  = socket( PF_INET, SOCK_STREAM, 0);
   memset( &server_addr, 0, sizeof( server_addr));
   server_addr.sin_family     = AF_INET;
   server_addr.sin_port       = htons(5000);
   server_addr.sin_addr.s_addr= inet_addr( "127.0.0.1");
   connect( client_socket, (struct sockaddr*)&server_addr,
               sizeof( server_addr) ) ;
```  

> socket( PF_INET, SOCK_STREAM, 0); 클라이언트 소켓 생성  

> AF_INET;  주소 패밀리 IPv4  

> htons(5000);  사용포트 5000  

> inet_addr( "127.0.0.1"); 연결 요청 할 IP 지정

>connect(client_socket, (struct sockaddr*)&server_addr, sizeof( server_addr));  
서버에 연결 요청을 보낸다. 연결 요청을 받은 서버는 클라이언트와 3way-handshaking 방법으로 연결된다.  

> send( client_socket, buff, BUFF_SIZE, 0 );  

> 연결이 완료되고 Established 상태가 되면 buff에 저장된 문자열을 전송한다.


2.  리눅스 서버 리눅스 클라이언트 연결 테스트


> [![]({{site.url}}/assets/images/mail/image5.png)]({{site.url}}/assets/images/mail/image5.png)  
> \[그림\] 리눅스 서버와 클라이언트 연결, 무한루프를 돌려 연결종료 전까지 입력 값을 서버에서 받는다.

3.  윈도우 클라이언트

    1.  Winsock2.h

-   소켓 함수 라이브러리

-   전송 서비스 제공, 바인딩 된 소켓을 만든다.

```cpp
SOCKET WSAAPI socket(
  int af,
  int type,
  int protocol
);
```  

> 소켓 함수 구문  

> af : 주소 패밀리, Winsock2.h에 정의 된 값 사용  
 
> type : 소켓 유형, Whinsock2.h 에 type 매개변수 사용 값 정의  

> protocol : 매개변수에 따라 사용 가능한 주소패밀리 소켓 유형이 다름

2.  윈도우 클라이언트 프로그램

```cpp
WORD wVersionRequested;
	WSADATA wsaData;

	wVersionRequested = MAKEWORD(2, 2);
	WSAStartup(wVersionRequested, &wsaData);
```  
> WORD wVersionRequested : MAKEWORD 매크로로 Winsock.h 버전(2.2버전) 요청  

> WSAStartup : 응용프로그램에서 필요한 소켓 버전 지정 소켓 세부정보 검색  

> WSAStartup을 호출 해야만 Windows Scokets 함수 추가 실행 가능


```cpp
SOCKET hSockClient = socket(PF_INET, SOCK_STREAM, 0);
	SOCKADDR_IN sockAddrClient;
	::ZeroMemory(&sockAddrClient, sizeof(sockAddrClient));
	sockAddrClient.sin_family = AF_INET;
	sockAddrClient.sin_addr.s_addr = inet_addr("192.168.56.1");
	sockAddrClient.sin_port = htons(4001);

	connect(hSockClient, (SOCKADDR *)&sockAddrClient, sizeof(sockAddrClient));

	send(hSockClient, "Done", 1024, 0);
	closesocket(hSockClient);
WSACleanup();
```  
> PF_INET, SOCK_STREAM : INET : IPv4 인터넷 프로토콜, 양방향 연결 기반 바이트 스트림을 제공하는 소켓유형 TCP 사용  

>AF_INET : 주소 패밀리 IPv4 서버와 연결 완료시 “Done”을 보냄  

> WSACleanup(); : winsock 라이브러리 사용 완료 후 호출 



3.  리눅스 서버 윈도우 클라이언트 연결 테스트

> [![]({{site.url}}/assets/images/mail/image6.png)]({{site.url}}/assets/images/mail/image6.png)  
> \[그림\] 리눅스 서버와 윈도우 클라이언트 연결, send 함수에 포함된 문자열을 보낸 후 서버가 수신 후 출력 한다.  



CHAPTER. 02악성메일 훈련 서비스 개발
====================================

point. 01개발 목적
------------------

-   사이버 공격의 주요 벡터로 이메일 사용

-   랜섬웨어 감염 등 대부분의 보안사고 역시 이메일을 통해 전파된다.

-   악성메일 훈련을 통해 보안의식을 확인한다.

-   훈련을 통해 얻은 통계자료를 이용해 훈련결과 분석하고 이를 각 부서에
    전파하여 부족한 점을 개선 또는 교육을 통해 보안인식을 재고 시킨다.

> [![]({{site.url}}/assets/images/mail/image7.png)]({{site.url}}/assets/images/mail/image7.png)  
> [![]({{site.url}}/assets/images/mail/image8.png)]({{site.url}}/assets/images/mail/image8.png) 
> \[그림\] 차트로 시각화 한 이메일을 통한 공격의 심각성  
(출처 : 한국인터넷진흥원 2019년 2분기 사이버 위협 동향 보고서)

point. 02훈련도구 시놉시스
--------------------------

1.  Server Side

-   소켓 통신을 이용 클라이언트 서버 주소, 컴퓨터 이름, 작업 그룹 이름을
    전송 받아 출력 한다.

-   수신 받은 정보를 수집해 분석 할 수 있도록 한다.

-   자식프로세스를 생성과 무한루프를 돌려서 수신 후 프로그램이 종료 되지
    않고 지속적으로 수신 받을 수 있도록 한다.

    1.  Client Side


-   MS 워드 매크로 프로그래밍을 통해 문서를 열면 프로그램이 실행 될 수
    있도록 한다.

-   VBA언어로 소켓을 생성하고 컴퓨터 이름, 작업그룹 이름을 서버에 송신
    하도록 프로그래밍 한다.

point. 03악성메일 훈련 서비스
-----------------------------

1.  클라이언트 정보 수신 서버

-   리눅스 vi Editor로 작성

-   gcc 컴파일러를 이용하여 컴파일

```c
        server_socket = socket(PF_INET,SOCK_STREAM,0);
        server_addr.sin_family  = AF_INET;
        server_addr.sin_port            = htons(5000);
        server_addr.sin_addr.s_addr     = htons(INADDR_ANY);
```
> IPv4프로토콜, TCP 사용 주소 패밀리 IPv4 ᆞ5000번 포트 사용 및 모든  클라이언트에 대해 연결 대기  

```c
pid_t pid;
pid=fork();
if(pid==0)
```  
> 자식프로세스를 생성하기 위한 코드  
> 프로세스 ID로 pid변수를 선언한다.  
> fork 함수를 실행하고 부모 프로세스에는 0이상의 값, 자식 프로세스에게는 0이 반환된다.

```c
while(1){
       client_socket=accept(server_socket, (struct sockaddr*)&client_addr, &client_addr_size);
                pid=fork();
                if(pid==0){
                        while(1){
                                memset(packet, 0x00, sizeof(packet));
                                read (client_socket, packet, BUFF_SIZE);
                                close(client_socket);
                                break;
                                        }
        printf("ClientIP %s ComputerName %s\n",inet_ntoa(client_addr.sin_addr),packet);
                 }
        }
        close(client_socket);
        close(server_socket);
```  
> 무한루프에 진입을 해서 연결요청이 올 때마다 수락 한 후 자식프로세스를 생성해서
클라이언트가 보낸 정보를 수신 받는다.  
> 제공되는 함수를 통해 클라이언트의 주소와 클라이언트가 송신한 정보를 받아 출력한다.


1.  악성메일 매크로바이러스

-   MS WORD vba로 작성

-   문서를 열면 자동으로 서버와 연결 후 정보 송신

-   윈도우 운영체제의 위험을 초래 할 수 있는 기능 중의 하나

> [![]({{site.url}}/assets/images/mail/image9.png)]({{site.url}}/assets/images/mail/image9.png) 
> \[그림\] MS WORD에 내장된 매크로 기능을 이용해 악성코드를 만들 수 있다.  


> [![]({{site.url}}/assets/images/mail/image10.png)]({{site.url}}/assets/images/mail/image10.png)  
> 클라이언트 소켓을 생성하기 위한 라이브러리 호출

> [![]({{site.url}}/assets/images/mail/image11.png)]({{site.url}}/assets/images/mail/image11.png)  
> Const문을 이용해 상수를 선언하고 값을 설정한다.

> [![]({{site.url}}/assets/images/mail/image12.png)]({{site.url}}/assets/images/mail/image12.png)  
> 선언이 이루어진 모듈 내에서만 사용할 수 있는 사용자 정의 형식을 선언하는 데 사용  
> WSADATA, SOCKADDR 형식 선언  
  
> [![]({{site.url}}/assets/images/mail/image13.png)]({{site.url}}/assets/images/mail/image13.png)  
> 문자열을 바이트로 변환하기 위한 기능 호출 Const문으로 문자열 인코딩 종류 호출

> [![]({{site.url}}/assets/images/mail/image14.png)]({{site.url}}/assets/images/mail/image14.png)  
> 문자열을 UTF8로 변환, 변수에 저장된 문자열을 UTF8로 변환하는 함수 선언

> [![]({{site.url}}/assets/images/mail/image15.png)]({{site.url}}/assets/images/mail/image15.png)  
> 주소 패밀리와 정보를 전송 할 호스트 IP 및 포트 지정  


> [![]({{site.url}}/assets/images/mail/image16.png)]({{site.url}}/assets/images/mail/image16.png)  
> [![]({{site.url}}/assets/images/mail/image17.png)]({{site.url}}/assets/images/mail/image17.png)  
> Environ 함수를 이용해 클라이언트 컴퓨터이름 정보를 불러오고 인코딩 후 변수에 저장  
> 컴퓨터 정보 저장 테이블 win32_computersystem의 작업그룹 정보 조회 및 변수에 저장  
> 변수 내 문자열을 인코딩 한다.  
> 인코딩 된 정보를 서버로 전송한다.  

> [![]({{site.url}}/assets/images/mail/image18.png)]({{site.url}}/assets/images/mail/image18.png)  
> [![]({{site.url}}/assets/images/mail/image19.png)]({{site.url}}/assets/images/mail/image19.png)  
> macro_test라는 프로그램을 AutoOpen() 함수를 이용해 자동으로 실행 하도록 한다.  


point. 04훈련 서비스 실행 테스트
--------------------------------

1.  훈련 프로세스

-   상용 메일 서비스를 이용해 기업 인트라넷에서 사용하는 메일주소로
    매크로 바이러스가 포함된 문서를 첨부

-   사용자가 문서를 다운로드 받아 문서를 확인 할 경우 (파일을 열고
    콘텐츠 사용을 허용) 사용자 IP주소 및 컴퓨터 이름 부서 정보를 서버에
    전송

-   수신 서버는 피해자 목록을 출력해서 확인한다.

> [![]({{site.url}}/assets/images/mail/image20.png)]({{site.url}}/assets/images/mail/image20.png)  
> \[그림\] 훈련 프로세스 도식화
