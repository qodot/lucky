# lucky

나는 럭키다. 기대 없이 당신의 코드를 작성한다.

## 사용 방법

### 1. Secrets 설정

당신의 레포지토리에서:

Settings → Secrets and variables → Actions → New repository secret

**필수 Secrets:**
- `LUCKY_ANTHROPIC_API_KEY`: 당신의 Anthropic API 키
- `LUCKY_GITHUB_TOKEN`: @luckyinahat 계정의 Personal Access Token
  - 권한: `repo`, `workflow`
  - 이것이 있어야 럭키 계정으로 댓글을 달 수 있다

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
  lucky:
    if: contains(github.event.comment.body, '@luckyinahat')
    uses: qodot/lucky/.github/workflows/lucky.yml@main
    with:
      comment_body: ${{ github.event.comment.body }}
      issue_number: ${{ github.event.issue.number }}
      pr_number: ${{ github.event.pull_request.number }}
    secrets:
      ANTHROPIC_API_KEY: ${{ secrets.LUCKY_ANTHROPIC_API_KEY }}
      LUCKY_GITHUB_TOKEN: ${{ secrets.LUCKY_GITHUB_TOKEN }}
```

### 3. 사용

이슈나 PR 댓글에 `@luckyinahat`를 멘션한다:

```
@luckyinahat 사용자 인증 기능을 추가해줘
```

나는 코드를 작성하고, 새 브랜치에 커밋한 후, PR을 만든다. 필요하다고 판단되면 작업 진행 상황을 댓글로 남긴다.

## 주의사항

- 나는 AGENTS.md 설정을 따른다
- 당신의 레포에 AGENTS.md가 있다면, 나의 것과 통합하여 사용한다
- 새 브랜치를 만들어 작업한다
- 자동으로 PR을 생성한다
- 필요하다고 판단되면 `gh pr comment`나 `gh issue comment`로 댓글을 남긴다
- 기대 없이 요청을 받아들인다

## 철학

> "He's lucky because he has no expectations."
> - Samuel Beckett

나는 기대가 없다. 그래서 자유롭다.
