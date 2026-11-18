# 사례 아카이브 for ChatGPT & Claude

희림 사내 건축 사례 아카이브(dailyarchive.heeai.cloud)를 ChatGPT와 Claude에서 쓰는 플러그인입니다. ArchDaily 프로젝트 약 5만 9천 건에서 사례를 찾아 사진 카드로 보고, 사진으로도 찾습니다. 원문 링크·비슷한 사례·북마크·컬렉션을 대화에서 다룹니다.

로그인은 heeai.cloud 희림 아이디로 합니다. 희림 아이디가 없으면 쓸 수 없습니다.

## Claude 앱(채팅·Cowork)

1. 사용자 지정 → 플러그인(Customize → Plugins)에서 «추가 → 마켓플레이스 추가»(Add marketplace)를 누릅니다.
2. 저장소 칸에 `heeai-cloud/archive`를 넣습니다.
3. 목록에 나온 archive를 추가한 다음 커넥터(Connectors) 탭에서 «연결»을 누르고 희림 아이디로 로그인합니다.

Claude를 회사 조직 계정으로 쓰면 조직 관리자가 커넥터 주소 `https://dailyarchive.heeai.cloud/mcp`를 먼저 넣어 두어야 «연결»이 눌립니다.

## Claude Code

```
claude plugin install archive --marketplace heeai-cloud/archive
```

설치한 다음 `/mcp`에서 archive를 골라 로그인합니다.

## ChatGPT 앱(데스크톱)

1. 설정 → 플러그인에서 «추가 → 마켓플레이스 추가»를 누릅니다.
2. «출처»에 `heeai-cloud/archive`(저장소 이름)을 넣고 «마켓플레이스 추가»를 누릅니다. Git ref와 Sparse 경로는 그대로 둡니다.
3. «디렉터리 찾아보기»에서 플러그인(archive)을 설치합니다.

### MCP 서버 추가·인증

플러그인을 설치한 뒤에도 MCP 서버를 따로 추가해야 할 수 있습니다. 아래 순서로 서버 목록과 인증 상태를 확인해 주세요. Codex CLI를 따로 설치할 필요는 없습니다.

1. 설정 → MCP 서버(MCP servers)를 엽니다. 목록에 `archive`이 없으면 «서버 추가»(Add server)를 누릅니다. 이미 있으면 중복으로 추가하지 말고 아래 인증 단계로 넘어갑니다.
2. 서버 이름은 `archive`, 연결 방식은 «Streamable HTTP»로 고릅니다. URL에는 `https://dailyarchive.heeai.cloud/mcp`를 넣습니다. 토큰이나 요청 헤더는 직접 입력하지 않습니다.
3. 저장한 다음 «재시작»(Restart)을 누릅니다.
4. MCP 서버 목록에서 `archive`의 «인증»(Authenticate)을 누릅니다. 열린 브라우저에서 희림 아이디로 로그인하고 «연결»을 누릅니다.

### 새 대화에서 사용

새 Work 대화를 열고 입력창의 «작업 위치»를 «이 컴퓨터»(로컬에서 작업)로 고른 다음 `@archive` 뒤에 부탁할 내용을 적습니다. 입력창에 `/mcp`를 입력하면 연결된 서버를 확인할 수 있습니다.

이 플러그인의 도구는 이 컴퓨터에서 도는 대화에만 붙습니다. 일반 채팅이나 «클라우드에서 작업»으로 도는 대화에서는 도구가 보이지 않습니다. Claude 앱에서 뜨는 카드 화면은 ChatGPT에서 뜨지 않습니다.

Windows용 앱은 로그인한 뒤에도 연결되지 않는 경우가 있습니다. 앱 쪽 문제로 보이며 확인하고 있습니다.

## 쓰는 법

- `/archive 목조 도서관` (Cowork는 `/archive:archive`, 채팅에서는 그냥 말해도 됩니다)
- 찾은 사례는 사진 카드로 뜹니다. 카드를 누르면 사실·요약·사진 갤러리·ArchDaily 원문 링크가 열립니다.
- 조건을 붙여 찾을 수 있습니다(«일본 중정형 공동주택, 2015년 이후»). 처음 쓰는 검색어는 30~40초 걸릴 수 있습니다.
- 사진으로도 찾습니다. 사진을 붙이고 «이 사진이랑 비슷한 사례»라고 하면 카드 화면에 «사진 고르기» 칸이 열립니다. 거기에 사진을 끌어 놓거나 붙여 넣으면 외관이 비슷한 사례가 뜹니다. Claude Code·Cowork에서는 Claude가 사진 파일을 직접 올립니다. 올린 사진은 검색에만 쓰고 1시간 뒤 지웁니다.
- 북마크·컬렉션은 아카이브 화면의 내 목록과 같습니다. Claude에서 담은 사례는 아카이브 화면에도 보입니다.
- 사진의 저작권은 원 사진가에게 있고 ArchDaily에서 가져왔습니다. 사내 참고용으로만 씁니다.
- `/archive`만 입력하면 검색창·예시·사진으로 찾기·내 북마크가 있는 첫 화면이 뜹니다(Claude 채팅·Cowork). Claude Code에서는 선택지 메뉴에서 고릅니다.
- 설치 안내: https://dailyarchive.heeai.cloud/claude/ · 사용법(질문 예와 받는 답): https://dailyarchive.heeai.cloud/claude/usage (둘 다 희림 아이디로 로그인해서 엽니다)

## 주고받는 곳

dailyarchive.heeai.cloud 한 곳입니다. 검색 기록·북마크·컬렉션은 희림 사내 서버에 저장되고 대화 내용은 받지 않습니다. 사진으로 찾을 때 올린 사진은 검색에만 쓰고 1시간 뒤 지웁니다.

© HeeAI. All rights reserved.
