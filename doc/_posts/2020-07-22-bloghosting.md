---
title: "깃허브 블로그(3) jekyll 블로그 생성과 github로 호스팅"
excerpt: 설치한 jekyll로 블로그를 생성하고 github로 호스팅 하자
categories:
 - gitblog
---

## 샘플 블로그 생성
- 설치 된 jekyll을 이용해서 샘플 블로그를 생성한다.
- 경로를 별도로 지정하지 않으면 현재 디렉토리에 생성된다.
```
jekyll new <my blog name>
```
[![]({{site.url}}/assets/images/gitblog/8_jekyllblogcreate.png)]({{site.url}}/assets/images/gitblog/8_jekyllblogcreate.png)
[![]({{site.url}}/assets/images/gitblog/8_jekyllblogcreate2.png)]({{site.url}}/assets/images/gitblog/8_jekyllblogcreate2.png)
[![]({{site.url}}/assets/images/gitblog/8_jekyllblogcreate3.png)]({{site.url}}/assets/images/gitblog/8_jekyllblogcreate3.png)
## 로컬에서 샘플 블로그 호스팅
- 127.0.0.1 또는 localhost 즉, 자신의 시스템에서 호스팅이 되는지 테스트를 해본다. 포트는 4000번 사용
- 생성된 블로그 디렉토리에서 명령어를 실행해야 정상적으로 돌아간다.
```
cd <my blog name>
jekyll serve
```  
[![]({{site.url}}/assets/images/gitblog/9_hostingtest.png)]({{site.url}}/assets/images/gitblog/9_hostingtest.png)

- 브라우저에서 로컬로 접근하여 샘플블로그가 제대로 호스팅되는지 확인 해본다.
```
127.0.0.1:4000 or localhost:4000
```
[![]({{site.url}}/assets/images/gitblog/9_hostingtest_2.png)]({{site.url}}/assets/images/gitblog/9_hostingtest_2.png)