---
title: 
draft: false
date: 2025-07-12
---
# --help (-h): 도움말 표시

Gemini CLI에서는 다양한 옵션들이 존재하며 이들을 통해 동작환경 조절이 가능함. 아래와 같이 입력하여 다양한 옵션들 확인 가능.

```bash
gemini --help
```

![[Pasted image 20250713100756.png]]

# --model (-m): LLM 모델 선택

아래 옵션을 통해 gemini CLI 구동 시 사용할 모델 선택 가능. 빠른 응답이 필요한 경우 flash 모델 지정을 권장함.

```bash
gemini -m "gemini-1.5-flash"
```

# --prompt (-p): 단순 질문 즉시 전달

단순히 프롬프트 하나만 전달하고 답변만 빠르게 받아보고 싶은 경우, 아래와 같이 입력하여 중간과정 생략하고 바로 답변을 전달해 줌.

```bash
gemini -p "오늘 서울 날씨 알려줘"
```

gemini CLI 자체를 스크립트에서 실행한다면 유용하게 쓸 수 있을거같음. 단, 출력결과가 나오고나면 gemini CLI가 바로 종료되므로 맥락 유지 불가.

# --sandbox (-s): 격리된 환경에서 실행

Gemini CLI는 로컬 파일 조작 툴을 가지고 있고, MCP 서버도 사용할 수 있음. 이것이 의도치않게 작동될 경우 위험한 상황 발생 가능함. 그래서 사용자가 정한 환경(도커)에서만 gemini CLI가 구동되도록 격리 시키기 위해 sandbox 옵션을 제공함.

아래에서 설명할 --yolo 옵션 사용 시 -s 옵션이 자동 사용됨.

기본적으로 기본 도커이미지인 `gemini-cli-sandbox`가 사용됨. 커스텀이 필요하다면 아래 양식에 따라 Dockerfile 작성 후 프로젝트 `프로젝트root디렉토리/.gemini/sandbox.Dockerfile`에 넣기.

```dockerfile
FROM gemini-cli-sandbox

# Add your custom dependencies or configurations here
# For example:
# RUN apt-get update && apt-get install -y some-package
# COPY ./my-config /app/my-config
```

`.gemini/sandbox.Dockerfile`를 사용하고 싶은 경우, 아래와 같이 `BUILD_SANDBOX` 환경변수를 사용하면 해당 도커 이미지가 자동으로 빌드되며 그 환경에서 gemini CLI가 실행됨.

```shell
BUILD_SANDBOX=1 gemini -s
```

뒤에 `--sandbox-image=<도커이미지주소>`와 같이 붙여서 기존 도커 이미지도 활용 가능함.

# --debug (-d): 디버그 모드로 작동

내부 작동 과정을 자세히 출력해줌. 여러 단계를 거쳐 응답이 나오는 경우 해당 결과가 나온 과정이 궁금할 때 유용할 듯. 아래 처럼 -p 옵션이랑 같이 사용도 가능함.

```bash
gemini -d -p "뭔가 프롬프트"
```

# --all-files (-a): 현재 디렉토리 내 모든 파일 포함

설정된 경우, 현재 디렉토리 내의 모든 파일을 프롬프트의 컨텍스트에 재귀적으로 포함시킴.

# --show_memory_usage: 메모리 사용 현황 표시

모델 호출 시 발생하는 메모리 사용량을 표현

# --yolo (-y): 툴 자동 사용 모드

LLM 모델이 툴 사용 시 사용자 승인을 받지 않고 자동으로 모든 작업 수행함. 툴을 반복적으로 요청해야하는 경우 유용할 듯. --yolo 옵션 사용 시, 자동으로 sandbox 모드가 적용됨.

# --telemetry: 운영 상태 모니터링 옵션

Gemini CLI의 성능, 상태 및 사용량에 대한 정보를 얻을 수 있음. 이 옵션을 활성화하면 추적, 메트릭 및 구조화된 로그를 통해 운영을 모니터링하고, 디버깅하고, 툴 사용을 최적화할 수 있음. 상세한 사용법은 좀 복잡해서 [[Gemini CLI telemetry]]에서 공부해 볼 예정임.

# --checkpointing (-c): 스냅샷 기능

체크포인트 옵션을 사용하면 파일 수정 등이 이루어지기 전에 프로젝트 상태의 스냅샷을 자동으로 저장함. 만약 문제 생긴 경우, 저장된 스냅샷 중 하나로 돌아갈 수 있음. 상세한 사용법은 [[Gemini CLI checkpointing]]에서 공부해 볼 예정임.

# --extensions (-e): 사용할 익스텐션 지정

아래와 같이 사용하면 해당 세션에서 사용할 수 있는 익스텐션(MCP 서버 등 도구들의 모음)들을 지정할 수 있음. 해당 옵션을 명시하지 않으면 모든 가능한 익스텐션이 사용됨. extensions와 MCP 관련 사용법은 [[Gemini CLI MCP 사용법]]에서 공부해 볼 예정.

```bash
gemini -e my-extension -e my-other-extension
```

아래와 같이 사용하면 모든 익스텐션을 비활성화 할 수 있음.

```bash
gemini -e none
```

`--list-extensions` (**`-l`**)를 사용하면 사용 가능한 모든 익스텐션의 리스트가 출력됨.

# --version (-v): 버전 정보 출력

현재 gemini CLI의 버전이 출력됨

---

위 내용은 아래 글들을 기반으로 정리한 내용임.
- https://digitalbourgeois.tistory.com/1557
- https://dpcks5959.tistory.com/144
- https://github.com/google-gemini/gemini-cli/blob/main/docs/cli/configuration.md