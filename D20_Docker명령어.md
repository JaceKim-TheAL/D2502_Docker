<p style="text-align: right"> 
    <a href="./README.md">[INDEX]</a>
</p>

---
## Docker에서 자주 사용하는 명령어

### 1. Docker 엔진 시작 / 종료

- 도커 엔진: 자동 실행 설정 활성화시, 컴퓨터를 켰을 때 함께 자동으로 실행

> * Docker Desktop은 도커 엔진 자동으로 실행하도록 설정 되어있음.
![images](./images/docker-desktop.png)
> * 리눅스 명령어로 엔진 시작, 종료, 자동 실행 설정 방법

>> - systemctrl: 서비스 시작 및 중지 관련 리눅스 명령어 (system control)

```console

# 엔진 시작
sudo systemctl start docker

# 엔진 종료
sudo systemctl stop docker

# 자동 실행 설정
sudo systemctl enable docker

```

- 컨테이너: 
> - 실행시킬 스크립트가 따로 필요. <br/> 
> - 컴퓨터를 켰을 때 함께 자동으로 실행 되지 않음.
<br/>
<br/>

### 2. 컨테이너의 기본적인 사용 방법

- 컨테이너를 다루는 모든 명령어는 docker 명령어로 시작

- 도커 명령어 구성: docker 커맨드(무엇을 어떻게) 대상
> * `+ 옵션, 인자`: docker 커맨드(무엇을 어떻게) 옵션 대상 인자
> * 상위 커맨드는 생략 가능하다?! `ex) docker run, docker start`
>> - 커맨드(무엇을 어떻게)는 상위커맨드와 하위커맨드로 나뉘어짐.
>> - container 상위 커맨들를 생략하는 경우가 있음.
>> - 도커 1.13부터 커맨드가 재편되면서 상위 커맨드와 하위 커맨드의 조합 형태로 일원화 되고 일부 커맨드는 커맨드 자체가 변경되기도 했음. 이전 커맨드와 호환성을 유지하기 위해 상위 커맨드가 없는 명령어로도 실행 가능하지만 언제 수정될지 모르니 이사실을 기억하고 있자!

- 리눅스 관련 깨알지식

>> - **옵션**
>>> - `- or —` 로 시작하는 것이 일반적이지만, -를 붙이지 않는 경우도 있음. 커맨드 작성자 취향
>>> - 옵션 뒤에 옵션의 값을 지정: 커맨드에 어떤 값을 전달하고 싶은 경우. `ex) —name penguin`
>>> - -를 하나만 사용하는 옵션은 한꺼번에 모아쓸 수 있음. `ex) -dit = -d + -i + -t`

>> - **인자**
>>> - 옵션이랑 다른점이 모야? → 인자는 “대상에 전달할 값을 지정” `ex) 문자 코드, 포트 번호`
>>> - `- or --`로 시작하는 경우가 많다
>>> - `예) --mode=1, --style nankyoku`

>> - **데몬**
>>> - 유닉스, 리눅스에서 동작하는 프로그램 중에서 백그라운드에서 항상 동작하는 프로그램을 관례적으로 데몬(daemon)이라고 부름. `ex)메일러 데몬`

- 명령어 정리
<table>
    <thead>
        <tr>
            <th>docker 명령</th>
            <th>상위 커맨드</th>
            <th>하위 커맨드</th>
            <th></th>
            <th>주요 옵션</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>docker</td>
            <td>container</td>
            <td>start</td>
            <td>컨테이너 실행</td>
            <td>-i</td>
        </tr>
        <tr>
            <td></td>
            <td></td>
            <td>stop</td>
            <td>컨테이너 정지</td>
            <td></td>
        </tr>
        <tr>
            <td></td>
            <td></td>
            <td>create</td>
            <td>(이미지로 부터) 컨테이너 생성</td>
            <td>—name, -e, -p, -v</td>
        </tr>
        <tr>
            <td></td>
            <td></td>
            <td>run</td>
            <td>세개의 명령을 하나로 합침(이미지 내려받기, 컨테이너 생성, 실행) <br> docker image pull <br>docker container create <br>docker
                container start</td>
            <td>—name, -e, -p, -v, -d, -i, -t</td>
        </tr>
        <tr>
            <td></td>
            <td></td>
            <td>rm</td>
            <td>정지 상태 컨테이너 삭제</td>
            <td></td>
        </tr>
        <tr>
            <td></td>
            <td></td>
            <td>exec</td>
            <td>실행중인 컨테이너 속에서 프로그램 실행</td>
            <td>-i -t</td>
        </tr>
        <tr>
            <td></td>
            <td></td>
            <td>ps <br>ls (상위커멘드 생략 X)</td>
            <td>(실행 중인)컨테이너 목록 출력</td>
            <td>-a (정지상태 컨테이너 포함)</td>
        </tr>
        <tr>
            <td></td>
            <td></td>
            <td>cp</td>
            <td>도커 컨테이너 - 도커 호스트 간에 파일 복사</td>
            <td></td>
        </tr>
        <tr>
            <td></td>
            <td></td>
            <td>commit</td>
            <td>도커 컨테이너를 이미지로 변환</td>
            <td></td>
        </tr>
        <tr>
            <td></td>
            <td>image</td>
            <td>pull</td>
            <td>도커 허브 리포지토리에서 이미지 다운</td>
            <td></td>
        </tr>
        <tr>
            <td></td>
            <td></td>
            <td>rm</td>
            <td>도커 이미지 삭제</td>
            <td></td>
        </tr>
        <tr>
            <td></td>
            <td></td>
            <td>ls</td>
            <td>내려받은 이미지 목록</td>
            <td></td>
        </tr>
        <tr>
            <td></td>
            <td></td>
            <td>build</td>
            <td>이미지 생성</td>
            <td>-t</td>
        </tr>
        <tr>
            <td></td>
            <td>volume</td>
            <td>create</td>
            <td>볼륨 생성</td>
            <td>—name</td>
        </tr>
        <tr>
            <td></td>
            <td></td>
            <td>inspect</td>
            <td>볼륨 상세 정보</td>
            <td></td>
        </tr>
        <tr>
            <td></td>
            <td></td>
            <td>ls</td>
            <td>볼륨 목록</td>
            <td>-a</td>
        </tr>
        <tr>
            <td></td>
            <td></td>
            <td>prune</td>
            <td>현재 마운트되지 않은 볼륨을 모든 삭제</td>
            <td></td>
        </tr>
        <tr>
            <td></td>
            <td></td>
            <td>rm</td>
            <td>볼륨 삭제</td>
            <td></td>
        </tr>
        <tr>
            <td></td>
            <td>network</td>
            <td>connect</td>
            <td>네트워크 연결</td>
            <td></td>
        </tr>
        <tr>
            <td></td>
            <td></td>
            <td>disconnect</td>
            <td>네트워크 연결 해제</td>
            <td></td>
        </tr>
        <tr>
            <td></td>
            <td></td>
            <td>create</td>
            <td>네트워크 생성</td>
            <td></td>
        </tr>
        <tr>
            <td></td>
            <td></td>
            <td>inspect</td>
            <td>네트워크 상세 정보</td>
            <td></td>
        </tr>
        <tr>
            <td></td>
            <td></td>
            <td>ls</td>
            <td>네트워크 목록</td>
            <td></td>
        </tr>
        <tr>
            <td></td>
            <td></td>
            <td>prune</td>
            <td>현재 컨테이너가 접속하지 않은 네트워크 모두 삭제</td>
            <td></td>
        </tr>
        <tr>
            <td></td>
            <td></td>
            <td>rm</td>
            <td>네트워크 삭제</td>
            <td></td>
        </tr>
    </tbody>
</table>
<br/>

- 특수 커멘드 (상위 커맨드 없이 단독. 주로 도커 허브의 검색, 로그인)
<table>
    <thead>
        <tr>
            <th>단독 커맨드</th>
            <th>내용</th>
            <th>주요 옵션</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>login</td>
            <td>도커 레지스트리에 로그인</td>
            <td>-u, -p</td>
        </tr>
        <tr>
            <td>logout</td>
            <td>도커 레지스트리에 로그아웃</td>
            <td></td>
        </tr>
        <tr>
            <td>search</td>
            <td>도커 레지스트리 검색</td>
            <td></td>
        </tr>
        <tr>
            <td>version</td>
            <td>도커 엔진 및 명령행 도구의 버전 출력</td>
            <td></td>
        </tr>
    </tbody>
</table>
<br/>

- 주요 옵션
> - 컨테이너에 따라 지정 가능한 옵션/인자가 달라짐
> - 컨테이너는 ‘한 번만 실행되는 컨테이너’와 ‘데몬 형태로 동작하는 컨테이너’가 있음.

<table>
    <thead>
        <tr>
            <th>옵션 형식</th>
            <th>내용</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>—name 컨테이너_이름</td>
            <td>컨테이너 이름 지정</td>
        </tr>
        <tr>
            <td>-p 호스트_포트번호:컨테이너_포트번호</td>
            <td>포트번호 지정 <br>(—publish 생략형)</td>
        </tr>
        <tr>
            <td>-v 호스트_디스크:컨테이너_디렉터리</td>
            <td>볼륨 마운트 <br>(—volume 생략형)</td>
        </tr>
        <tr>
            <td>—net=네트워크_이름</td>
            <td>컨테이너 네트워크에 연결</td>
        </tr>
        <tr>
            <td>-e 환경변수_이름=값</td>
            <td>환경변수 설정 <br>(—env 생략형)</td>
        </tr>
        <tr>
            <td>-d</td>
            <td>백그라운드로 실행 <br>(—detach 생략형)</td>
        </tr>
        <tr>
            <td>-i</td>
            <td>컨테이너에 터미널(키보드)을 연결함 <br>(—interactive 생략형)</td>
        </tr>
        <tr>
            <td>-t</td>
            <td>특수 키 사용 가능 <br>(—tty 생략형)</td>
        </tr>
        <tr>
            <td>-help</td>
            <td>사용 방법 안내 메시지</td>
        </tr>
    </tbody>
</table>
<br/>

### 3. 컨테이너 생성, 삭제, 실행, 정지
```docker 
docker run (옵션) 이미지 (인자)

docker stop 컨테이너_이름

docker rm 컨테이너_이름

docker ps -a
```

**예제**
- 아파치 이미지(httpd)
> - docker run --name apa000ex1 -d httpd
> - -d: —detach 백그라운드로 실행

