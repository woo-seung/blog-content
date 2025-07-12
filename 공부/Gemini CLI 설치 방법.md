---
title: 
draft: false
---
# Window

https://nodejs.org/en/download/current 에서 운영체제에 맞는 인스톨러를 다운한 후 node 설치

![](Attachment/Pasted%20image%2020250712204053.png)

터미널 창에서 아래 처럼 입력해서 node 설치 확인하기

![](Attachment/Pasted%20image%2020250712204114.png)

파워쉘 관리자권한으로 연 후 아래 명령어 입력

`Set-ExecutionPolicy RemoteSigned`

`y` 입력해서 권한 부여

아래 명령어 입력해서 설치 시작

`npm install -g @google/gemini-cli`

설치되니 아래처럼 나왔다.

![](Attachment/Pasted%20image%2020250712204126.png)

# Mac

https://nodejs.org/en/download/current 에서 운영체제에 맞는 인스톨러를 다운한 후 node 설치

![](Attachment/Pasted%20image%2020250712204133.png)

![](Attachment/Pasted%20image%2020250712204142.png)

터미널에서 아래처럼 입력해서 설치 확인

![](Attachment/Pasted%20image%2020250712204149.png)

터미널에서 아래 명령어 입력해서 설치

`sudo npm install -g @google/gemini-cli`

설치 완료된 화면은 다음과 같다.

![](Attachment/Pasted%20image%2020250712204158.png)

# 공통사항

터미널 창에 `gemini` 치면 바로 실행됨.

실행된 화면이 이뿌다..

![](Attachment/Pasted%20image%2020250712204205.png)

인증은 간편하게 구글 로그인으로 했음. 테마 등 설정하면 되고 그런 설정값들은 홈디렉토리의 ~/.gemini 폴더에 저장됨. 초기화하고싶으면 지워버리고 다시 `gemini`쳐서 시작하면 됨.

업데이트가 필요할 때는 터미널에 아래 명령어 입력

`npm upgrade -g @google/gemini-cli`