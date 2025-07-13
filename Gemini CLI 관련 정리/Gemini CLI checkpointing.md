---
title: 
draft: false
---
# Checkpoint 란?

Checkpoint는 AI 도구가 파일을 수정하는 등의 작업을 수행하기 직전, 프로젝트 상태의 **스냅샷을 자동으로 저장**하는 기능임. 이 기능을 통해 AI가 생성한 코드 변경 사항을 안전하게 실험하고 적용할 수 있으며, 만약 문제가 발생했을 경우 도구가 실행되기 직전 상태로 **즉시 되돌릴 수 있음.**

# 사용법

이 기능은 기본적으로 비활성화되어 있으므로, Gemini CLI를 시작할 때 `-c` 또는 `--checkpointing` 플래그를 추가하여 직접 활성화해야 함.

```Bash
gemini -c
```

활성화 되고 나면 다음 과정을 통해 사용됨:

1.  AI 도구를 통한 파일 수정 작업을 아직 수행하지 않았다면, `/restore` 명령을 입력해도 "No restorable tool calls found." 라는 메시지가 나타남.
2. 이제 Gemini에게 "이 프로젝트를 위한 README.md 파일 생성해 줘" 와 같이 파일 생성을 요청함.
3. Gemini가 `WriteFile`과 같은 파일 쓰기 도구를 사용하겠다고 요청하면, 이를 승인함.
4. 파일 생성이 완료된 후 다시 `/restore` 명령을 실행하면, 복원 가능한 체크포인트 목록(파일 생선 전 상태)가 표시됨. 체크포인트 ID는 `timestamp-<filename>-<toolname>`와 같이 명명됨.
5. 원하는 체크포인트의 ID를 선택하면 프로젝트가 해당 상태로 되돌아감.

---

위 내용은 아래 글들을 기반으로 정리한 내용임.
- https://medium.com/google-cloud/gemini-cli-tutorial-series-part-2-gemini-cli-command-line-parameters-e64e21b157be
- https://github.com/google-gemini/gemini-cli/blob/770f862832dfef477705bee69bd2a84397d105a8/docs/checkpointing.md