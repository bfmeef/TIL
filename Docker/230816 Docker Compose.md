생활코딩 링크: https://youtu.be/EK6iYRCIjYs

Docker Container를 만드는 명령이 있다. 컨테이너를 만들 때마다 매번 명령을 써주기도 번거롭고, 동료들이 잘 모를 수도 있다.

이때 `docker-compose.yml`이라는 파일을 만들고 컨테이너를 만들 수 있는 역할을 똑같이 하는 코드를 작성한다.

그리고 터미널에
```
docker-compose up
```
위 명령어를 실행하면 컨테이너가 만들어진다.


## Docker Compose
- ``docker-compose up``: 실행
- ``docker-compose down``: 실행 정지

- docker-compose version 설정
- services: (만들고 싶은 컨테이너들이 들어옴)
- image: mysql5.7 (mysql을 생성하라고 할 수 있음)
- 이름을 지정하고 싶으면 `db:` 이런 식으로 작성 가능
- volumes: host에 db 폴더를 만들어 컨테이너와 연결
- depends_on: 먼저 생성되어야 하는 컨테이너명을 적는다.
- ports: 포트 포워드
- environment: 환경변수 설정
