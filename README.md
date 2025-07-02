# Git Branch 관리

---

## 🌱 브랜치 만들기

### 기본 브랜치 생성

현재 체크아웃된 로컬 브랜치로부터 새 브랜치를 생성합니다.

```bash
git branch [branch_name]
```

### 브랜치 생성과 동시에 전환

특정 브랜치에서 새 브랜치를 생성하고 바로 해당 브랜치로 이동합니다.

```bash
git checkout -b [new_branch] [parent_branch]
```

**예시: develop 브랜치에서 feature 브랜치 생성**

```bash
git checkout -b feature-branch develop
```

위 명령어는 다음 세 단계와 동일합니다:

```bash
git checkout develop                # develop 브랜치로 이동
git branch feature-branch          # feature-branch 생성
git checkout feature-branch        # feature-branch로 이동
```

---

## 👀 브랜치 목록 보기

### 로컬 브랜치 목록

```bash
git branch
```

```
* mybranch    # 현재 브랜치 (*)
  master
```

### 원격 브랜치 목록

```bash
git branch -r    # 원격(remote) 브랜치만 표시
```

### 모든 브랜치 목록

```bash
git branch -a    # 로컬 + 원격 브랜치 모두 표시
```

---

## 🔄 작업 브랜치 전환하기

### HEAD 포인터란?

Git은 현재 작업 중인 브랜치를 가리키는 **HEAD**라는 포인터를 사용합니다. 브랜치 전환은 이 HEAD 포인터를 이동하는 것입니다.

> 💡 **쉬운 이해**: HEAD를 포스트잇으로 생각해보세요. 어떤 브랜치에 붙어있던 포스트잇을 떼어서 다른 브랜치에 붙이는 것입니다.

### 브랜치 전환

```bash
git checkout [이동할_브랜치명]
```

### 원격 브랜치 가져오기

원격 저장소의 브랜치를 로컬로 가져와서 추적합니다.

```bash
git checkout -t origin/[브랜치명]
```

**예시:**

```bash
git checkout -t origin/ft-01
```

---

## 🗑️ 브랜치 삭제

### 삭제 전 확인사항

- 현재 작업 중인 브랜치는 삭제할 수 없습니다
- 먼저 다른 브랜치로 이동한 후 삭제해야 합니다
- 작업 내용이 다른 브랜치나 원격 저장소에 병합된 후 삭제하는 것이 안전합니다

### 브랜치 삭제 방법

```bash
git checkout [다른_브랜치]           # 삭제할 브랜치에서 다른 브랜치로 이동
git branch -d [삭제할_브랜치명]      # 브랜치 삭제
```

**예시:**

```bash
git checkout main
git branch -d feature-branch
```

---

### 브랜치 명명 규칙

```
feature/기능명     # 새 기능 개발
bugfix/버그명      # 버그 수정
hotfix/긴급수정명  # 긴급 수정
release/버전명     # 릴리즈 준비
```

### 자주 사용하는 명령어 조합

```bash
# 새 기능 브랜치 생성 후 작업 시작
git checkout -b feature/login-system develop

# 작업 완료 후 develop으로 돌아가서 브랜치 삭제
git checkout develop
git branch -d feature/login-system
```

---
