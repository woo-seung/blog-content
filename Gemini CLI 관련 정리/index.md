---
title: Gemini CLI 관련 정리
draft: false
---
Cursor AI를 쓰던 중 주피터 노트북에서 잘 작동되지 않아 고민을 하던 중 Gemini CLI에서 분당 60회, 일일 1000회 요청까지 Gemini 2.5 Pro를 무료로 제공해준다는 사실을 알게 되었다. 심지어 Gemini 2.5 Pro는 컨텍스트 윈도우가 100만 [[토큰]]이라서 좀 복잡한 연구 프로젝트 구현에 더 적합해 보였다.

현재는 사용자가 많아져서 그런지 조금만 사용해도 Gemini flash 모델로 자동 전환되는 한계점이 있긴 하지만 MCP 서버 연결의 용이성, settings.json이나 GEMINI.md 파일을 활용한 프로젝트 관리, 체크포인트 기능 등 Cursor AI를 굳이 사용할 이유가 없어 보여 전환하기로 결정했다.

[gemini-cli 공식 깃허브](https://github.com/google-gemini/gemini-cli)에 나오는 소개글도 솔깃했다.

>With the Gemini CLI you can:
> - Query and edit large codebases in and beyond Gemini's 1M token context window.
> - Generate new apps from PDFs or sketches, using Gemini's multimodal capabilities.
> - Automate operational tasks, like querying pull requests or handling complex rebases.
> - Use tools and MCP servers to connect new capabilities, including [media generation with Imagen, Veo or Lyria](https://github.com/GoogleCloudPlatform/vertex-ai-creative-studio/tree/main/experiments/mcp-genmedia)
> - Ground your queries with the [Google Search](https://ai.google.dev/gemini-api/docs/grounding) tool, built in to Gemini.

공부할 겸 기록용으로 설치부터 명령어, 사용법 등을 정리해봤다.
