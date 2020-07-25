---
title: "(2) 정적 웹 호스팅 도구 jekyll 설치"
excerpt: 패키지 관리 툴 업데이트 및 ruby와 jekyll 설치
categories:
 - gitblog
---

## 패키지 관리도구 업그레이드 & 업데이트  
- apt(Advanced Packaging Tool)는 우분투 및 데비안 계열의 리눅스에서 사용되는 패키지 관련 명령어 도구이다.  
~~~
sudo apt-get upgrade
sudo apt-get update
sudo apt-get upgrade -y && update -y
#sudo는 root 권한으로 실행 
#-y 옵션은 설치지 확인사항을 모두 Y로
# and, 즉 &&연산자를 이용하여 명령어 한 줄로 실행
~~~
![]({{site.url}}/assets/images/gitblog/4_apt-get_update_upgrade.PNG)  

## 루비 설치
- 루비는 유키히로 마츠모토가 만든 스크립트 언어의 일종이자 객체지향 언어, 명령형 프로그래밍 언어, 함수형 언어이다
- apt 명령어를 이용해서 루비도 설치 한다.
~~~
sudo apt-get install ruby-full build-essential zlib1g-dev
~~~ 
- 설치가 완료 되었으면 정상설치 여부 확인
~~~
ruby -v
~~~
- 지킬은 root 계정로 ruby gems 설치를 권장하지 않고 user계정에 설치를 권장하여 사용자 계정 쉘 ./bashrc에 ruby gems 경로를 지정하는 환경설정을 하라고 알려준다.
~~~
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
~~~
- 마지막으로 jekyll 설치
~~~
gem install jekyll bundler
~~~
![]({{site.url}}/assets/images/gitblog/7_jekyllinstall.PNG)
###### ref. https://jekyllrb.com/docs/installation/ubuntu/