---
title: \[사이드 프로젝트\] USB 실시간 모니터링 솔루션 개발
excerpt: 실시간 USB탐지를 위한 클라이언트 프로그램과 서버 개발
categories: dev
---

# PART. 01 USB

CHAPTER. 01 USB 제어방식
========================

Point. 01 USB의 의미
--------------------

-   윈도우 및 리눅스 컴퓨터 시스템에 있는 직렬버스를 의미한다.

-   본 프로젝트에서는 저장소로 사용되는 USB만을 대상으로 한다. 즉,
    키보드 및 마우스는 제외된다.

Point. 02 USB 제어방식
----------------------

-   USB는 특정 디렉토리(탐색기)가 변경 되었을 때 탐지하는 방법과 윈도우
    메시지를 수신하여 탐지하는 방법으로 구분된다.

- 특정 디렉토리 변경  
> 윈도우 탐색기에서 USB가 인식되면 D: 혹은 E: 드라이버 등이 추가적으로 생성된다.  
> FindFirstChanageNotification, FindNext
ChanageNotification 등과 같은 API를
사용해서 구현이 가능하다.  
> Application Level에서 탐지되는 방식


-  윈도우 메시지 탐지  
> 실시간으로 전송되는 윈도우 메시지를 수신하여 WM_DEVICECHANGE 메시지가 전송되는 탐지한다.  
> 윈도우 Message loop 및 Window Procedure를 구현해야 한다.  
> OS Level에서 실시간 메시지를 탐지한다.

CHAPTER. 02 개인정보취급자 USB 사용내역 실시간 탐지
===================================================

Point. 01 USB 실시간 탐지의 의미
--------------------------------

-   개인정보취급자가 업무용으로 사용되는 PC에 등록되지 않은 USB를
    삽입하면 실시간으로 USB Manager에서 그 내역을 전송하여 통제한다.

Point. 02 USB 실시간 탐지 시스템 구조
-------------------------------------  
 
> ![]({{site.url}}/assets/images/usbdetect/image3.png)  
> \[그림\] 소프트웨어 아키텍처 도식화

- USB 제어 개발 프로그램  
> USB Detection : 실시간으로 USB 사용을 탐지한다.  
(Visual C++, Windows OS 7이상)  

> Client Socket : USB 삽입 시에 해당 볼륨 정보를 서버로 전송한다.  
(Visual C++, Windows OS 7이상)  

> Server Socket : 클라이언트 소켓에서 송신되는 정보를 실시간 수신한다.  
(gcc, Linux OS)

Point. 03 개발 프로그램의 범위
------------------------------

-   클라이언트 기기에서 USB가 삽입 될 경우 실시간을 모니터링 한다.

-   클라이언트는 USB가 삽입되면 서버에 해당 볼륨의 정보를 전송한다.

-   서버는 전송된 정보들을 화면에 출력한다.

CHAPTER. 03 소프트웨어 구조
===========================

Point 01. USB Detection
-----------------------

-   WM_DEVICECHANGE Message를 탐지하여 USB 삽입 및 제거 여부를 식별한다.
> ![]({{site.url}}/assets/images/usbdetect/image4.png)
> \[그림\] 처리 흐름도  

```cpp
	// 메시지 루프 동작
	MSG Msg;
	while (0 < GetMessage(&Msg, NULL, 0, 0))
	{
		TranslateMessage(&Msg);
		DispatchMessage(&Msg);
	}

```  
> 메시지 루프  

```cpp
	switch (uMsg)
	{
	case WM_CLOSE:
		DestroyWindow(hwnd);
		break;
	case WM_DESTROY:
		PostQuitMessage(0);
		break;
	case WM_DEVICECHANGE:	// 장치 상태가 변경
		ProcessDeviceChangeMsg(uMsg, wParam, lParam);
		break;
	default:
		return DefWindowProc(hwnd, uMsg, wParam, lParam);
	}
```
> 윈도우 프로시저  

```cpp
	case DBT_DEVICEARRIVAL:
		if (DBT_DEVTYP_VOLUME == pVolume->dbcv_devicetype)	
// 연결된 장치가 Volume(Disk) 인 경우
		{
			char cDriveName = GetDriveName(pVolume->dbcv_unitmask);
			char volumeName[10] = { cDriveName, ':', '\\', };
			char diskName[MAX_PATH+1] = { 0, };
			char fileSystem[MAX_PATH+1] = { 0, };
			char comName[MAX_PATH + 1] = { 0, };
			char Serial[MAX_PATH + 1] = { 0, };
			char InfoBuff[1024] = { 0, };
			GetVolumeInformation(volumeName, diskName, MAX_PATH, &dwSerialNo,
                         NULL, NULL, fileSystem, MAX_PATH);
			GetComputerNameA(comName, &bufCharCount);			
			// 관련 정보 출력
			printf("A new USB storage Arrival\n");
			printf("  [%s] -> Disk Name [%s], File System [%s],
                         SerialNumber[%X] \n", volumeName, diskName, fileSystem,
                         dwSerialNo);
			printf("ComputerName [%s]\n", comName);

```  

- USB 탐지  

Point 02. Client Socket
-----------------------

-   USB의 정보들 서버에 전송한다.
```cpp
		wVersionRequested = MAKEWORD(2, 0);
	WSAStartup(wVersionRequested, &wsaData);
	SOCKET hSockClient = socket(PF_INET, SOCK_STREAM, 0);
	SOCKADDR_IN sockAddrClient;
	::ZeroMemory(&sockAddrClient, sizeof(sockAddrClient));
	sockAddrClient.sin_family = AF_INET;

	sockAddrClient.sin_addr.s_addr = inet_addr("192.168.56.1");
	sockAddrClient.sin_port = htons(5000);
  //USB Manager Server와 연결
```
  


```cpp
			strncpy(InfoBuff, comName, sizeof(comName));
			strcat(InfoBuff," ");
			strcat(InfoBuff, volumeName);
			strcat(InfoBuff, " ");
			strcat(InfoBuff, diskName);
			strcat(InfoBuff, " ");
			strcat(InfoBuff, fileSystem);
			strcat(InfoBuff, " ");
			strcat(InfoBuff, Serial);
      //USB 정보 버퍼에 저장
```  
```cpp
			send(hSockClient, InfoBuff, 50, 0);

			closesocket(hSockClient);
			WSACleanup();

      //서버에 전송 및 소켓 종료
```  


Point 03. Server Socket
-----------------------

-   클라이언트에서의 송신 정보 수신 및 출력

```cpp
int server_socket, client_socket;
        struct sockaddr_in server_addr, client_addr;
        char packet[BUFF_SIZE];
        int client_addr_size;
        char *buff;
        pid_t pid;

        server_socket = socket(PF_INET,SOCK_STREAM,0);
        server_addr.sin_family  = AF_INET;
        server_addr.sin_port            = htons(5000);
        server_addr.sin_addr.s_addr     = htons(INADDR_ANY);
        bind(server_socket, (struct sockaddr*)&server_addr, sizeof(server_addr));
        listen(server_socket,7);
        client_addr_size=sizeof(client_addr);

//소켓 생성 및 수신 대기  
```  


```cpp  
int server_socket, client_socket;
        struct sockaddr_in server_addr, client_addr;
pid=fork();
if(pid==0){
           while(1){
                   memset(packet, 0x00, sizeof(packet));
                   read (client_socket, packet, BUFF_SIZE);

                        close(client_socket);
                        break;
                        }
//자식프로세스 생성 및 클라이언트 송신 정보 수신  
```



```cpp
printf("ClientIP %s ComputerName %s\n", inet_ntoa(client_addr.sin_addr),packet);
//서버는 수신된 정보를 출력한다.
```  

  

CHAPTER. 03 USB 탐지기 테스트 결과
==================================

Point 01. USB 탐지기 테스트
---------------------------


> ![]({{site.url}}/assets/images/usbdetect/image5.jpeg)  
> ![]({{site.url}}/assets/images/usbdetect/image6.jpeg)  
> 실제 사용하는 USB를 활용하여 프로그램 동작 테스트  

Point 02. Client
----------------

> ![]({{site.url}}/assets/images/usbdetect/image7.png)  
> 클라이언트 usb 정보 출력

Point 03. Server
----------------

>![]({{site.url}}/assets/images/usbdetect/image8.png)  
> 서버는 수신된 정보를 출력한다.

> ![]({{site.url}}/assets/images/usbdetect/image9.png)  
> AWS EC2 우분투 서버 정보

> ![]({{site.url}}/assets/images/usbdetect/image10.png)  
> 클라이언트와 클라우드 환경 서버간 usb 정보 송수신 테스트

CHAPTER. 04 실시간 USB 탐지 솔루션 개선 방안
============================================

Point 01. Pro\*C, C API를 사용한 DB 연동
----------------------------------------

-   프로그램과 데이터베이스 간 연동 방법

    -   오라클 Pro\*C

        -   오라클에서 제공하는 외부 C 프로그램과 결합 할 수 있는
            선행컴파일러

        -   오라클 DB와 연동 가능한 C프로그램

        -   C 프로그램 내에 SQL 코드작성이 가능하다.

```cpp
#include <stdio.h> 
#include <sqlca.h> 
EXEC SQL BEGIN DECLARE SECTION; 
VARCHAR uid[20]; /* DB USER ID */ 
VARCHAR pwd[20]; /* DB PASSSWORD */ 
Int empno; 
EXEC SQL END DECLARE SECTION; 
void main 
{ 
	/* Log on oracle */ 
	strcpy((char *)uid.arr, "userid");
	uid.len = (short)strlen((char *)uid.arr);
	strcpy((char *)pwd.arr, "password");
	pwd.len = (short)strlen((char *)pwd.arr);
	EXEC SQL CONNECT :uid IDENTIFIED BY :pwd;
	if(sqlca.sqlcode != 0) {
		printf("[ERROR] Connect Error SQL_MSG : [%d].\n",
		           sqlca.sqlerrm.sqlerrmc);
		           exit(0); 
		           } 
EXEC SQL SELECT empno 
INTO :empno 
FROM scott.emp 
```  

> Pro\*C example code  



-   Mysql C API  

```cpp
#include <my_global.h>
#include <mysql.h>
int main(int argc, char **argv)
{  
  MYSQL *con = mysql_init(NULL);
  if (con == NULL) 
  {
      fprintf(stderr, "%s\n", mysql_error(con));
      exit(1);
  }
  if (mysql_real_connect(con, "localhost", "root", "root_pswd", 
          NULL, 0, NULL, 0) == NULL) 
  {
      fprintf(stderr, "%s\n", mysql_error(con));
      mysql_close(con);
      exit(1);
  }  
  if (mysql_query(con, "CREATE DATABASE testdb")) 
  {
      fprintf(stderr, "%s\n", mysql_error(con));
      mysql_close(con);
      exit(1);
  }
  mysql_close(con);
  exit(0);
}

```
> Mysql C API example code  

-   DMBS에서 제공하는 선행 컴파일러를 이용하여 신뢰 할 수 있는 USB 목록
    관리 기능 추가가 가능하다.

Point 02. 등록되지 않은 USB 자동 제거
-------------------------------------

1.  미등록 USB eject 모듈

    -   각 USB는 고유한 식별값을 가진다.

    -   DB 혹은 파일에 등록된 고유 식별번호를 활용하여 미등록 디바이스의
        접근차단

2.  윈도우 API를 통한 디바이스 컨트롤

```cpp
BOOL DeviceIoControl(
  HANDLE       hDevice,
  DWORD        dwIoControlCode,
  LPVOID       lpInBuffer,
  DWORD        nInBufferSize,
  LPVOID       lpOutBuffer,
  DWORD        nOutBufferSize,
  LPDWORD      lpBytesReturned,
  LPOVERLAPPED lpOverlapped
);

BOOL DeviceIoControl(
  (HANDLE) hDevice,            // handle to device
  IOCTL_STORAGE_MEDIA_REMOVAL, // dwIoControlCode(LPVOID) lpInBuffer,// input buffer 
  (DWORD) nInBufferSize,       // size of input buffer 
  NULL,                        
//lpOutBuffer0,//nOutBufferSize(LPDWORD)lpBytesReturned,// number of bytes returned
  (LPOVERLAPPED) lpOverlapped  // OVERLAPPED structure
);
```
> Device Control Function  


-   윈도우에서 제공하는 API를 활용하여 usb 제어 기능을 수행 할 수 있다.
