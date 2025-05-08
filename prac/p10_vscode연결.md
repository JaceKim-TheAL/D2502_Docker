# Get Started with Dev Containver in VS Code

VSCode에서 Extension
- Remote Development
- Docker

원격탐색기에서 
개발 컨테이너를 마치 로컬 개발 환경처럼 사용할 수 있도록 하기

### [WSL을 사용하여 Windows에 Linux를 설치하는 방법][link-wsl-install]

- WSL 설치 및 실행
```powershell
# WSL1에서 WLS2로 변경경
wsl --set-version Ubuntu 2

# 사용가능한 배포판 목록 확인
wsl --list --online
또는
wsl -l -o

### 배포판 설치
wsl --install -d <Distribution Name>

### 배포판 실행
wsl -d <Distribution Name>

### WSL 종료
wsl --shudown

### WSL 기본 배포판 변경
wsl --set-default Ubuntu-20.04

### WSL 다시 시작, Ubuntu 20.04가 기본적으로 실행
wsl

```

Tip.
> - PowerShell 또는 명령 프롬프트가 아닌 Linux/Bash 명령줄 내에서 추가 배포판을 설치하려면 <br/>
> wsl.exe --install -d <Distribution Name> 명령 또는 wsl.exe -l -o 명령(사용 가능한 배포판을 나열하려는 경우)에서 .exe를 사용해야 합니다.





[도커와 VSCode 연결해서 사용하기][link-youtube]


[link-youtube]: https://www.youtube.com/watch?v=dyR6Wt3Nt-I

[link-wsl-install]: https://learn.microsoft.com/ko-kr/windows/wsl/install