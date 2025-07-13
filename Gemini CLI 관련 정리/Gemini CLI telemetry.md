---
title: 
draft: false
date: 2025-07-13
---
Gemini CLI의 사용량을 확인하는 방법은 아래 두가지가 있음.

- **/stats 명령어**: CLI를 사용하는 중 언제든지 이 명령어를 입력해 현재까지의 세션 통계를 확인할 수 있음.
- **종료 시 요약**: CLI를 종료하면 세션 동안의 토큰 사용량, 소요 시간 등의 요약 정보를 보여줌.

### 고급 모니터링: OpenTelemetry

단순한 사용량을 넘어 **성능, 상태, 상세 사용량** 등 깊이 있는 데이터를 얻고 싶다면, Gemini CLI는 **OpenTelemetry** 기반의 완전한 원격 측정 시스템을 제공함. 이 기능을 활성화하면 **추적(traces), 메트릭(metrics), 구조화된 로그(logs)**를 통해 운영 상태를 모니터링하고, 문제를 디버깅하며, 도구 사용을 최적화할 수 있음.

이 기능을 제대로 활용하려면 OpenTelemetry의 기본 개념(Collector, Exporter 등)과 Google Cloud Platform 사용법에 대한 사전 지식이 필요함. 다음에 필요하면 아래 자료들 공부해보는걸로..

- https://github.com/google-gemini/gemini-cli/blob/770f862832dfef477705bee69bd2a84397d105a8/docs/telemetry.md#gemini-cli-observability-guide
- https://medium.com/google-cloud/gemini-cli-tutorial-series-part-2-gemini-cli-command-line-parameters-e64e21b157be