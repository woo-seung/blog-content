---
title: 
draft: false
date: 2025-07-15
---
MCP 서버에 연결해 gemini cli에 기본 제공되는 툴 외에도 커스텀 툴들을 연결해서 사용할 수 있음.

[[Gemini CLI settings.json|settings.json]]에 추가하면 간편하게 사용할 수 있음. 설정 예시는 아래와 같음. 자주 사용하는 MCP들은 홈디렉토리의 [[Gemini CLI settings.json|settings.json]]에 등록해두면 모든 프로젝트에서 바로 쓸 수 있으니 편함.

```json
{
  "mcpServers": {
    "sequential-thinking": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-sequential-thinking"
      ]
    }
  }
}
```

설정 시 사용되는 변수는 아래와 같음.

- `command` (string, required): MCP 서버를 시작하기 위해 실행할 명령어
- `args` (array of strings, optional): 명령어에 전달할 인자(arguments) 배열
- `env` (object, optional): 서버 프로세스에 설정할 환경 변수
- `cwd` (string, optional): 서버를 시작할 작업 디렉토리
- `timeout` (number, optional): 해당 MCP 서버로의 요청에 대한 타임아웃 시간(밀리초 단위)
- `trust` (boolean, optional): 이 서버를 신뢰하고 모든 도구 호출 확인을 건너뛸지 여부를 설정

사용 예시는 아래와 같음.

```json
"mcpServers": {
	"myPythonServer": {
		"command": "python",
		"args": ["mcp_server.py", "--port", "8080"],
		"cwd": "./mcp_tools/python",
		"timeout": 5000
	},
	"myNodeServer": {
		"command": "node",
		"args": ["mcp_server.js"],
		"cwd": "./mcp_tools/node"
	},
	"myDockerServer": {
		"command": "docker",
		"args": ["run", "-i", "--rm", "-e", "API_KEY", "ghcr.io/foo/bar"],
		"env": {
		  "API_KEY": "$MY_API_TOKEN"
		}
	}
}
```

세팅한 후 터미널에서 gemini CLI를 실행한 후 `/mcp desc`를 입력하면 아래와 같이 설명이 나오는걸 확인할 수 있음.

![[Pasted image 20250715224952.png]]

[이 글](https://www.reddit.com/r/Bard/comments/1lp13mx/geminicli_disappointing/)에서는 gemini CLI 사용 시 Sequential Thinking MCP 쓰는걸 강추한다고 함.

그 외 MCP 서버 추천은 [[MCP 서버 추천 및 활용 예시]]에서 다룰 예정.

---

공부자료: https://github.com/google-gemini/gemini-cli/blob/main/docs/cli/configuration.md