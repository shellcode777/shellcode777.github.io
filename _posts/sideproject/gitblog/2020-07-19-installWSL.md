---
title: "(1) 리눅스용 Windows 하위 시스템 설치  "
excerpt: WSL 설치를 위한 옵션 변경 및 리눅스 설치
categories:
 - gitblog
---
  
## 리눅스용 Windows 하위 시스템 옵션 기능을 사용으로 변경  
- 제어판 > 프로그램 및 기능 > Windows 기능 켜기/끄기  
- Linux용 Windows 하위 시스템 체크 > 확인   
![]({{site.url}}/assets/images/gitblog/1_win10function.PNG)  
- 또는 Powershell 관리자 권한 실행 후 명령어 입력  
```
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```  
- 모든 설치가 끝나면 재부팅  
![]({{site.url}}/assets/images/gitblog/1_win10function2.PNG)
## 가상머신 플랫폼 기능 사용으로 변경
- 가상머신 플랫폼 체크 > 확인
![]({{site.url}}/assets/images/gitblog/1_win10function3.PNG)  
- 또는 Powershell 관리자 권한 실행 후 명령어 입력
~~~
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
~~~  
- 모든 설치가 끝나면 재부팅
- 기본 버전을 WSL 2로 지정할 경우 powershell에서 명령어 입력
```
wsl --set-default-version 2  
```  
## 리눅스 배포판 설치  
- Microsoft Store에서 리눅스 배포판 검색 후 설치  
- 이 포스트에서는 우분투를 설치 했습니다.  
![]({{site.url}}/assets/images/gitblog/2_win10ubuntu_1.PNG)      
- 설치가 완료 되면 bash 명령어를 입력해서 리눅스 실행  
- 콘솔창이 열리면 자동으로 설치가 된다.
- 설치가 완료되고 계정정보를 입력하면 끝
![]({{site.url}}/assets/images/gitblog/3_win10bash_shell.PNG) 
![]({{site.url}}/assets/images/gitblog/2_win10ubuntu2.PNG) 
![]({{site.url}}/assets/images/gitblog/3_win10bash_shell_1.PNG)  

## 마운트가 안되어 있을 경우 해결방법  
- 파일시스템 중 하나를 탑재하는 중 오류가 발생했습니다. 라는 오류와 함께 /mnt/c 디렉토리가 비어 있을 경우
```
mount -t drvfs C: /mnt/c -o metadata
```
- 위 명령어로 파일시스템을 수동으로 마운트시키면 윈도우 파일시스템의 파일들이 리눅스에서 접근이된다.
- 자동으로 마운트가 되지않는게 2020년 5월 Insider preview 배포버전 버그 같은데 수정이 된 것인지 미확인