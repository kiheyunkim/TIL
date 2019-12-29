# Docker



### Dockerfile을 이용한 도커 이미지 생성 시 유의 사항

* #### Dockerfile의 명령어 단위로 레이어가 생성되므로 불필요한 명령 실행은 자체해야 한다.

  >gedit Dockerfile

  

* #### 파일 내용

  > FROM ubuntu
  >
  > RUN mkdir /echo
  >
  > RUN fallocate -l 100m /echo/dummy
  >
  > RUN rm /echo/dummy

  

* #### 생성

  > docker build -t falloc100m  .

  

* #### 위 의 파일 내용은 다음과 같이 쓸 수 도 있음

  > FROM ubuntu
  >
  > RUN mkdir /echo && fallocate -l 100m /echo/dummy && rm /echo/dummy

  

* #### 도커 이미지를 도커 허브에 등록

  * ##### DOCKERHUB_ID/IMAGE_NAME:TAG_NAME 형식을 준수

    > docker image tag example/echo:latest kiheyunkim/echo:lastest

  * ##### docker login 명령어로 로그인

    > docker login -u kiheyunkim

  * ##### docker image push 명령어로 푸시함

    > docker image push kiheyunkim/echo:latest

    

* #### 도커 이미지, 컨테이너 호출

  > docker image ls -a
  >
  > docker container ls -a

  

* #### 도커 실행 

  > docker container run -p 9000:8080  //호스트 9000 도커 8000포트 대응해서 실행
  > docker container run -p 9000:8080 -d  example/echo:latest 
  > docker container run -p 9000:8080 -it example/echo:latest  	
  > docker container run -p 9000:8080 -itd example/echo:latest
  > docker container run -p 9000:8080 -it example/echo:latest /bin/bash
  > docker container run -p 9000:8080 -itd example/echo:latest /bin/bash
  > docker container run -p 9003:8080 -itd --name CONTAINER_NAME example/echo:latest /bin/bash
  > docker container run -p 8080 -itd example/echo:latest /bin/bash
  >
  > 
  >
  > -d는 백그라운드 실행
  >
  > -i interative 서로간의 통신
  > -t tty 실행
  > -p 포트지정
  > -P 포트 랜덤 지정 컨테이너는 EXPOSE로 부터 가져옴

  

  

* #### 백그라운드에서 실행되는 Container에 접속

  > docker attach Container_ID_or_Name

  

* #### 컨테이너 탈출법(-it일때)

  * 입력을 받을 수 없는 경우 => 새로운 터미널에서 docker stop  Container_ID_or_Name
  * 입력을 받을 수 있는 경우 => Ctrl+C  or Ctrl+PQ
  * 쉘이 제공되는 경우 => exit or Ctrl+PQ

  

* #### 컨테이너 실행 중지

  * docker container start Container_ID_or_Name
  * docker container stop Container_ID_or_Name

  

* #### 컨테이너 상태 확인

  * docker container ps

  * docker container ls

  * docker container ps -a

  * docker container ls -a

    

* #### 컨테이너 모두 정지 (쉘 스크립트 이용)

  * docker container stop $(docker container ls -q)		//-q는 id 리턴



* #### DockerFile 생성

>FROM ubuntu
>
>RUN apt-get update
>
>RUN apt-get install apache2 -y ⇐ ##1 
>
>ADD hello.html /var/www/html/  ⇐ ##2
>
>WORKDIR /var/www/html      ⇐ ##3
>
>RUN [ "/bin/bash", "-c", "echo hello2 >> hello2.html" ] ⇐ ##4 
>
>EXPOSE 80            ⇐ ##5
>
>CMD apachectl -DFOREGROUND   ⇐ ##6
>
>
>
>-----
>
>\##1 -y : docker build 과정에서 사용자 입력이 발생하면 오류로 처리하므로 사용자 입력이 발생하지 않도록 하기 위한 옵션
>
>\##2 ADD, COPY : 호스트의 파일 또는 디렉터리를 이미지 내부로 복사 COPY는 호스트의 로컬 파일만 복사가 가능ADD는 호스트의 로컬 파일 뿐 아니라 외부 URL 또는 tar 파일도 복사가 가능 (tar 파일인 경우 압축을 해제해서 복사)일반적으로 COPY 사용을 권장	
>
>
>##3 WORKDIR : cd 명령어와 동일. 명령어를 실행 위치를 지정
>
>##4 [] 형식의 인자 = JSON 배열 형식 → 쉘을 실행하지 않음을 의미  RUN *command* 형식은 /bin/sh -c *command* 형식으로 실행
>
>##5 EXPOSE : 이미지에서 노출할 포트를 설정 
>
>##6 CMD : 컨테이너가 실행될 때 마다 실행할 명령어 (반드시 한번만 사용이 가능)



* #### 컨테이너 생성중에 오류
  * 컨테이너를 생성할 때 같은 이름 가진 컨테이너가 있으면 오류가 난다.
  * 중지 시켜놓은 컨테이너가 있어도 오류가 난다.
  * 결론 : **제거한 다음 만들어야한다.**



```bash
#./etc/bash
# run.sh $1컨테이너이름 $2생성할이미지이름
if [ $# -lt 2 ]
then
    echo Invalid Paramter
fi

echo Existing Container ID
cid=$(docker container ls -a --filter="name=^/$1$" -q)


if [ -n  "$cid"  ]
then
    docker container rm -f $cid
    echo remove $cid Container
fi

echo Create New Container
docker container run -d -P --name $1 $2
```



* #### 컨테이너의 환경변수

  >FROM ubuntu
  >
  >ENV workspace /workspace
  >
  >RUN mkdir $workspace
  >
  >WORKDIR $workspace
  >
  >RUN touch $workspace/mytouchfile

  

  

  ```
  root@server:~/webserver# docker run -itd -e workspace=/tmp envimage /bin/bash
  
  -e : 환경변수
  
  환경변수를 지정해놓고 또 따로 주면 덮어 쓴다.
  안주면 기존에 설정된 환경 변수를 따라간다.
  ```



* #### 컨테이너 실시간 자원 사용 현황

  * docker status



* #### MYSQL 받기

  * ##### \#1 MySQL 이미지를 이용한 데이터베이스 컨테이너를 생성https://hub.docker.com/mysql

  >root@server:~# cd ~
  >
  >root@server:~# mkdir wblog
  >
  >root@server:~# cd wblog
  >
  >root@server:~/wblog# 
  >
  >
  >
  >root@server:~/wblog# docker run -d --name wordpressdb 
  >
  >\\> -e MYSQL_ROOT_PASSWORD=passwd 
  >
  >\\> -e MYSQL_DATABASE=wordpress
  >
  >\\> mysql:5.7

  

* #### 워드 프레스 받기

  * ##### \#2 워드프로세스 이미지를 이용한 웹 서버 컨테이너를 생성https://hub.docker.com/wordpress

  >root@server:~/wblog# docker run -d 
  >
  >\\> -e WORDPRESS_DB_PASSWORD=passwd                             
  >
  >\\> --name wordpress 
  >
  >\\> --link wordpressdb:mysql  ⇐ 컨테이너 별명(alias)으로 접근할 수 있도록 설정
  >
  >\\> -p 80 
  >
  >\\> wordpress



* #### 컨테이너 실행을 확인

  > root@server:~/docker/wblog# docker images
  > REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
  > serverimg           latest              0b6e59752a64        About an hour ago   188MB
  > envimage            latest              f60fa6f842f5        About an hour ago   64.2MB
  > wordpress           latest              a9f43b7c47db        6 days ago          539MB
  > ubuntu              latest              549b9b86cb8d        7 days ago          64.2MB엧
  > mysql               5.7                 1e4405fe1ea9        4 weeks ago         437MB

* 호스트(ubuntu)에서 http://localhost:32837/로 접속