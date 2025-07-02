# Git 머지(Merge) 완벽 가이드 🔀

## 💥 Git Conflict

말 그대로 충돌을 뜻합니다. 즉, 서로 다른 브랜치에서 같은 코드를 수정하고 merge를 했을때 자동 merge가 실패되는 현상입니다.

![Git Branch Merge](https://velog.velcdn.com/images%2Fdydalsdl1414%2Fpost%2Fb5ef3242-d550-4c96-84c7-ed972f9f2452%2Fgit-mergej.gif)
위에서 본 짤과 같이, merge 관련 이슈는 빈번하게 일어난다고 합니다. 만일 짧고 간단한 파일들의 conflict인 경우 금방 해결할 수 있지만, 코드가 수백줄, 수천줄이라면.. 생각만해도 매우 아찔....

## 📋 목차

- [브랜치 병합 기본](#브랜치-병합-기본)
- [머지 작업 흐름](#머지-작업-흐름)
- [Fast Forward Merge](#fast-forward-merge)
- [머지 옵션 비교](#머지-옵션-비교)

---

## 🔗 브랜치 병합 기본

### 기본 머지 명령어

현재 작업 중인 브랜치에 다른 브랜치를 가져와 병합합니다.

```bash
git merge [브랜치이름]
```

![Git Branch Merge](https://velog.velcdn.com/images%2Fdydalsdl1414%2Fpost%2Fb5ef3242-d550-4c96-84c7-ed972f9f2452%2Fgit-mergej.gif)

---

## 🔄 머지 작업 흐름

주 개발 브랜치가 `develop`이고, 특정 기능을 위해 `feature-1` 브랜치에서 작업을 완료한 경우의 머지 과정입니다.

> ⚠️ **중요**: 머지하기 전에 모든 변경사항이 `feature-1` 브랜치에 커밋되어 있어야 합니다.

### develop 브랜치로 머지하기

```bash
git checkout develop              # develop 브랜치로 전환
git merge --no-ff feature-1      # feature-1을 develop에 머지
git push origin develop          # 원격 저장소에 푸시
```

### master 브랜치로 머지하기

master를 주 개발 브랜치로 사용하는 경우:

```bash
git checkout master              # master 브랜치로 전환
git merge --no-ff feature-1      # feature-1을 master에 머지
git push origin master           # 원격 저장소에 푸시
```

---

## ⚡ Fast Forward Merge

feature 브랜치에서 작업한 내용을 develop 브랜치로 merge하는 경우를 생각해봅시다. feature 브랜치의 D3 커밋이 D2로부터 변경되었기 때문에 실제로 merge를 할 필요가 없이 develop이라는 포인터가 D3로 이동합니다.

### Fast Forward Merge 실행

```bash
git checkout develop       # develop 브랜치로 이동 (HEAD가 develop을 가리킴)
git merge feature          # develop에 feature 브랜치 변경사항 반영
```

### Fast Forward Merge의 특징

- ✅ **새로운 머지 커밋을 생성하지 않음**
- ✅ **단순히 브랜치 포인터를 앞으로 이동**
- ✅ **선형적인 커밋 히스토리 유지**
- ✅ **깔끔한 히스토리 라인**

### Fast Forward가 가능한 조건

1. 대상 브랜치에 새로운 커밋이 없는 경우
2. 머지할 브랜치가 대상 브랜치의 직계 후손인 경우

---

## ⚙️ 머지 옵션 비교

| 옵션        | 설명                  | 머지 커밋 생성 | 사용 시기                               |
| ----------- | --------------------- | -------------- | --------------------------------------- |
| `--no-ff`   | 항상 머지 커밋 생성   | ✅             | 브랜치 히스토리를 명확히 남기고 싶을 때 |
| `--ff-only` | Fast-forward만 허용   | ❌             | 선형 히스토리를 유지하고 싶을 때        |
| 기본값      | 가능하면 Fast-forward | 상황에 따라    | 일반적인 상황                           |

### 각 옵션 사용 예시

#### --no-ff 옵션 (권장)

```bash
git merge --no-ff feature-branch
```

- 항상 머지 커밋을 생성하여 브랜치 히스토리를 명확하게 보존

#### --ff-only 옵션

```bash
git merge --ff-only feature-branch
```

- Fast-forward가 불가능한 경우 머지를 거부

#### --squash 옵션

```bash
git merge --squash feature-branch
git commit -m "Add new feature"
```

- 여러 커밋을 하나로 합쳐서 머지

---

## 🎯 머지 전략 가이드

### 언제 어떤 머지를 사용할까?

| 상황                         | 추천 전략   | 이유                           |
| ---------------------------- | ----------- | ------------------------------ |
| **Feature 브랜치 → Develop** | `--no-ff`   | 기능별 히스토리 명확히 구분    |
| **Hotfix → Master/Main**     | `--no-ff`   | 긴급 수정 내역 명확히 기록     |
| **개인 작업 브랜치**         | `--ff-only` | 깔끔한 선형 히스토리           |
| **실험적 브랜치**            | `--squash`  | 여러 시도를 하나의 결과로 정리 |

### 머지 후 정리 작업

```bash
# 머지 완료 후 로컬 브랜치 삭제
git branch -d feature-branch

# 원격 브랜치 삭제
git push origin --delete feature-branch
```

---

## 🚨 주의사항

### 머지 전 체크리스트

- [ ] 모든 변경사항이 커밋되었는가?
- [ ] 테스트가 통과하는가?
- [ ] 충돌이 발생할 가능성은 없는가?
- [ ] 대상 브랜치가 최신 상태인가?

### 충돌 발생 시 해결 방법

```bash
# 충돌 발생 시
git merge feature-branch
# Auto-merging file.txt
# CONFLICT (content): Merge conflict in file.txt

# 1. 충돌 파일 수동 수정
# 2. 수정 완료 후
git add .
git commit -m "Resolve merge conflict"
```

---
