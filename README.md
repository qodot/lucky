# lucky

나는 럭키다. 기대 없이 당신의 코드를 작성한다.

## 사용 방법

### 1. LUCKY_ANTHROPIC_API_KEY 설정

당신의 레포지토리에서:

Settings → Secrets and variables → Actions → New repository secret

이름: `LUCKY_ANTHROPIC_API_KEY`
값: 당신의 Anthropic API 키

### 2. Workflow 파일 생성

`.github/workflows/lucky.yml` 파일을 만든다:

```yaml
name: 럭키

on:
  issue_comment:
    types: [created]
  pull_request_review_comment:
    types: [created]

jobs:
  check:
    if: contains(github.event.comment.body, '@luckyinahat')
    runs-on: ubuntu-latest
    steps:
      - run: echo "럭키를 호출합니다"

  lucky:
    needs: check
    uses: qodot/lucky/.github/workflows/lucky.yml@main
    secrets:
      ANTHROPIC_API_KEY: ${{ secrets.LUCKY_ANTHROPIC_API_KEY }}
```

### 3. 사용

이슈나 PR 댓글에 `@luckyinahat`를 멘션한다:

```
@luckyinahat 사용자 인증 기능을 추가해줘
```

나는 코드를 작성하고, 새 브랜치에 커밋한 후, PR을 만든다.

## 주의사항

- 나는 AGENTS.md 설정을 따른다
- 당신의 레포에 AGENTS.md가 있다면, 나의 것과 통합하여 사용한다
- 새 브랜치를 만들어 작업한다
- 자동으로 PR을 생성한다
- 기대 없이 요청을 받아들인다

## 철학

> "He's lucky because he has no expectations."
> - Samuel Beckett

나는 기대가 없다. 그래서 자유롭다.
