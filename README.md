DevOps 구축 무작정 시작하기
===
2022.6.20
1. 무엇이 필요할까?
* docker, API 서버, Jenkins, Python Script(테스트 코드), GitHub 간단한 프론트엔드라고 생각하고 출발
* 뒤늦게 적어놓고보니 API 서버 설정에 많은 내용이 필요할 것 같다.
    - 우선 DB를 클라우드 DB를 써보고 싶다. mongdb를 써봤으니 mySQL이 제공한다고 본 것 같으니 이번엔 이쪽을 알아볼까 싶다.
2. WSL을 설정 후 docker 설정부터 시작해보자
- windows 10 부터는 윈도우에서 제공하니까 설정하고 마켓에서 리눅스 받으면 끝
3. WSL에 docker 설치
```
sudo apt-get update
sudo apt-get install docker.io
```
4. DockerFile을 짤 것인가? docker image를 만들어서 그대로 쓸 것인가?
- Jenkins 배포를 위해서는 docker build 파일을 짤 필요가 있는 것 같다.
- 우선 jdk 1.8을 설치한 DockerFile을 생성하고 docker image를 생성해본다.
```
### set base image
FROM ubuntu:20.04

RUN apt update && apt install -y git
```

5. 생각해보니 windows 에서 docker를 사용하려면 docker desktop이 필요했음..
- https://docs.microsoft.com/ko-kr/windows/wsl/tutorials/wsl-containers

- wsl1을 wsl2로 변경까지 하니까 잘된다. 여기까지 시간을 꽤 잡아먹음
- 중간에 꼬인것 같은데 wsl1에서도 docker desktop을 설정하고 작업했으면 잘 됐을것 같다.
- DockerFile을 잘 읽어들여서 docker image를 생성하나 확인

```
docker build -t ubuntu:git .
```
- 