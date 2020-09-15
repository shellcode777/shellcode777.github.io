---
title: \[MYSQL\] mysql Archived 버전 설치
excerpt: windows 10 환경, mysql version 8.0.20
categories: db
---

### MySQL 아카이브 버전 다운로드  
> [https://dev.mysql.com/downloads/mysql/](https://dev.mysql.com/downloads/mysql/){: target="_blank"} 해당 URL에서 Archives 선택  
> ![]({{site.url}}/assets/images/mysqlinst/image1.png)  
  
- 원하는 버전을 선택한 후 ZIP Archive 다운로드  
> ![]({{site.url}}/assets/images/mysqlinst/image2.png)  
- 다운로드 완료 후 원하는 경로에 압축해제 해당 포스트에서는 `C:\mysql`에 위치 시켰다.  
  
### 환경변수 설정  
- `내 컴퓨터 > 속성 > 고급 시스템 설정 > 환경변수 > 시스템변수 > Path` 변수 `편집 > 새로 만들기 > bin 디렉토리` 경로 입력 해당 포스트에서는 `C:\mysql\bin`  
> ![]({{site.url}}/assets/images/mysqlinst/image3.png)  
> ![]({{site.url}}/assets/images/mysqlinst/image4.png)  

### data 디렉토리 생성
- 관리자 모드로 명령프롬프트에서 `mysqld --initialized-insecure` 명령어 입력
> ![]({{site.url}}/assets/images/mysqlinst/image5.png)  
> `data` 디렉토리가 생성되고 디렉토리 내부에 설정 파일 등이 생성된다.  
  
### mysql 서비스 등록 및 시작
- 명령프롬프트에서 `mysqld --install` 명령어 입력 후 성공하면 `Service successfully installed` 메시지가 나온다.  
- 명령프롬프트에서 `net start mysql` 명령어를 입력해서 서비스를 실행한다.  
  
### mysql 접속 및 root 암호 변경
- `root -u root -p` 입력 후 `Enter password` 가 나오면 암호 입력 없이 엔터를 치면 접속되고 명령창이 `mysqld>` 로 변경이 되면 데이터베이스에 접속이 성공한 것이다.  
> ![]({{site.url}}/assets/images/mysqlinst/image6.png)  
- `root`계정 접속 후 아래와 같이 입력하여 비밀번호를 변경한다.    

~~~sql
alter user 'root'@'localhost' identified by 'yourpassword'
~~~  
- `exit`로 데이터베이스를 종료하고 다시 접속하여 패스워드가 등록됐는지 확인해본다.