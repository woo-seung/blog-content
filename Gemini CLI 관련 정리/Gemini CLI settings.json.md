---
title: 
draft: false
date: 2025-07-15
---
`--checkpointing` 같은 [[Gemini CLI Command-Line Arguments|command line arguments]]는 자주 사용하게 됨. 근데 이걸 실행할 때 마다 넣는건 너무 불편함. 이럴 때 사용할 수 있는게 `settings.json` 파일임.

이 파일에 선호하는 세팅값들을 적어놓으면 Gemini CLI 시작할 때 자동으로 적용됨. gemini cli가 시작될 때 우선 홈디렉토리의 `~/.gemini/settings.json`을 찾음. 여기에는 보통 테마, 인증방식, 선호하는 에디터 등이 포함된.

다음으로 프로젝트 폴더 내부의 `.gemini/settings.json`을 탐색함. 이 파일은 해당 디렉토리에서 gemini cli가 실행될 때만 적용됨. 즉 프로젝트별로 다르게 설정해둘 수 있음.

다양한 설정값들은 아래 순위에 따라 우선적용됨.

홈디렉토리 설정값 < 프로젝트별 설정값 < [[Gemini CLI Command-Line Arguments|command line arguments]]

모든 [[Gemini CLI Command-Line Arguments|command line arguments]]를 `settings.json`에 등록할 수 있는건 아님. 상세 설명은 [gemini-cli/docs/cli/configuration.md at main · google-gemini/gemini-cli](https://www.google.com/search?q=https://github.com/google-gemini/gemini-cli/blob/main/docs/cli/configuration.md)를 참고하기.

아래는 현재 세팅해 둔 `settings.json` 설정값

```json
{
	// "theme": "Dracula",
	// "selectedAuthType": "oauth-personal",
	"checkpointing": {
		"enabled": true
	},
	"telemetry": {
		"enabled": false,
		"target": "local",
		"logPrompts": false
	},
	"usageStatisticsEnabled": false,
	"preferredEditor": "vscode",
	"mcpServers": {
		"sequential-thinking": {
			"command": "npx",
			"args": ["-y", "@modelcontextprotocol/server-sequential-thinking"],
			"trust": true
		},
		"context7": {
			"command": "npx",
			"args": ["-y", "@upstash/context7-mcp"],
			"trust": true
		}
	}
}
```