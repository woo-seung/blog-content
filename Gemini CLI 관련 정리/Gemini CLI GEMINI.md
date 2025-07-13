---
title: Gemini CLI GEMINI.md
draft: false
---
# GEMINI.md 란?

`GEMINI.md` 파일은 Gemini 모델에 제공되는 "지시적 컨텍스트" 또는 "메모리"를 설정하는 핵심적인 역할을 함. 이 파일을 통해 **프로젝트별 지침, 코딩 스타일 가이드, 관련 배경 정보** 등을 AI에 미리 알려주어, 사용자의 요구에 더 정확하고 맞춤화된 답변을 생성하도록 만들 수 있음.

CLI 화면 하단에는 현재 로드된 컨텍스트 파일의 개수가 표시되어 활성화된 컨텍스트를 쉽게 확인할 수 있음.

# 예시

아래는 `GEMINI.md` 파일의 예시임. 프로젝트 개요, 일반 지침, 코딩 스타일, 특정 컴포넌트 규칙 등을 정의할 수 있음.

```Markdown
# 프로젝트: My Awesome TypeScript Library

## 일반 지침:

- 새로운 TypeScript 코드 생성 시 기존 코딩 스타일을 따라주세요.
- 모든 새 함수와 클래스에는 JSDoc 주석을 포함해야 합니다.
- 적절한 경우 함수형 프로그래밍 패러다임을 선호합니다.
- 모든 코드는 TypeScript 5.0 및 Node.js 18+와 호환되어야 합니다.

## 코딩 스타일:

- 들여쓰기는 2칸 공백을 사용합니다.
- 인터페이스 이름 앞에는 `I`를 붙입니다. (예: `IUserService`)
- 비공개 클래스 멤버 앞에는 언더스코어(`_`)를 붙입니다.
- 항상 엄격한 동등성(`===` 및 `!==`)을 사용합니다.

## 특정 컴포넌트: `src/api/client.ts`

- 이 파일은 모든 외부 API 요청을 처리합니다.
- 새로운 API 호출 함수 추가 시 강력한 오류 처리 및 로깅을 포함해야 합니다.
- 모든 GET 요청에는 기존 `fetchWithRetry` 유틸리티를 사용합니다.
```

# GEMINI.md 파일 위치 및 계층 구조

`GEMINI.md` 파일은 여러 위치에 존재할 수 있으며, Gemini CLI는 이들을 모두 찾아 하나의 지침 세트로 결합함. 계층 구조를 가지며, 검색 순서는 다음과 같음. 하위 디렉토리(더 구체적인) 파일의 내용이 상위 디렉토리(더 일반적인) 파일의 내용을 덮어쓰거나 보완함.

- **전역 컨텍스트 파일**: 홈 디렉토리의 `~/.gemini/GEMINI.md`에 위치하며 모든 프로젝트에 적용되는 규칙을 담음.
- **프로젝트 및 상위 컨텍스트 파일**: 프로젝트의 루트 디렉토리에 위치하며 프로젝트 전반의 규칙을 담음.
- **로컬 컨텍스트 파일**: 하위 디렉토리에 위치하며 특정 모듈이나 컴포넌트에 대한 매우 구체적인 지침을 담음.

# 컨텍스트 새로고침

`GEMINI.md` 파일을 외부 편집기에서 수정한 경우, CLI 내에서 아래 명령어를 통해 다시 불러와야 함.

```bash
/memory refresh
```

---

위 내용은 아래 글들을 기반으로 정리한 내용임.
- https://medium.com/google-cloud/gemini-cli-tutorial-series-part-2-gemini-cli-command-line-parameters-e64e21b157be
- https://github.com/google-gemini/gemini-cli/blob/main/docs/cli/configuration.md#context-files-hierarchical-instructional-context