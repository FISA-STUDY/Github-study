이미지

# Git Hook이란?

Git의 특정 이벤트에 갈고리(Hook)를 걸어 자동으로 스크립트를 실행할 수 있게 해주는 기능.

→ 코드 품질 관리, 배포 자동화 등 다양한 작업을 자동화 가능.

## Git Hook 개요

모든 훅은 Git 저장소의 `.git/hooks` 디렉토리에 기본 탑재돼있음. 

여긴 10개의 hook이 있는데, 파일의 확장자인 .sample을 지우면 git hook가 실행됨.

이미지

Git Hook은 크게 클라이언트 측 훅과 서버 측 훅으로 나뉨.

## 1. 주요 클라이언트(로컬 컴퓨터) 측 훅

### 커밋 워크플로우 훅

- **pre-commit**: 커밋 메시지를 작성하기 전에 실행됨. 주로 코드 스타일 검사, 테스트 실행 등에 사용됨
- **prepare-commit-msg**: 커밋 메시지 편집기가 실행되기 전, 기본 메시지가 생성된 후 실행
- **commit-msg**: 커밋 메시지를 검증하는 데 사용. 특정 형식을 강제하거나 특정 정보를 포함하도록 할 수 있음.
- **post-commit**: 커밋 프로세스가 완료된 후 실행. 주로 알림이나 로깅에 사용됨

### 이메일 워크플로우 훅

- **applypatch-msg**: git am 명령으로 패치를 적용할 때 최초로 실행.
- **pre-applypatch**: 패치 적용 후, 커밋이 생성되기 전에 실행.
- **post-applypatch**: 커밋이 생성된 후 실행.

### 기타 클라이언트 훅

- **pre-rebase**: git rebase 명령이 실행되기 전에 실행.
- **post-rewrite**: git commit --amend, git rebase와 같이 커밋을 변경하는 명령 이후에 실행됨.
- **post-checkout**: git checkout 명령 이후에 실행됩다. 작업 디렉토리 설정이나 종속성 설치에 유용함.
- **post-merge**: git merge 성공 후 실행됨.
- **pre-push**: git push 명령 실행 시, 리모트 참조가 업데이트되기 전에 실행됨.

## 2. 주요 서버(git 원격 저장소) 측 훅

- **pre-receive**: 푸시를 받을 때 참조가 업데이트되기 전에 실행됨.
- **update**: pre-receive와 비슷하지만 업데이트되는 각 브랜치마다 한 번씩 실행됨.
- **post-receive**: 푸시 프로세스가 성공적으로 완료된 후 실행된다. 주로 사용자에게 알림을 보내거나 CI/CD 파이프라인을 트리거하는 데 사용됨.

## 3. Git Hook 활용 예시

```bash
#!/bin/bash
# pre-commit 훅 예시 - 코드 린팅

echo "Running code linting..."
npm run lint

# 린팅에 실패하면 커밋 중단
if [ $? -ne 0 ]; then
  echo "Linting failed! Commit aborted."
  exit 1
fi

exit 0

```

## 5. Git Hook 설정 방법

1. .git/hooks 디렉토리에 원하는 이름의 파일을 생성 (예: pre-commit)
2. 파일에 실행 권한을 부여: `chmod +x .git/hooks/pre-commit`
3. 스크립트 내용을 작성

## 6. 팀 전체에 Git Hook 공유하기

Git Hook은 기본적으로 로컬에만 존재함. 팀 전체에 공유하려면 

- 훅 스크립트를 저장소에 포함시키고 설치 스크립트 제공
- Husky와 같은 npm 패키지 사용
- git template 활용

## 7. 유용한 Git Hook 도구

- **Husky**: npm 프로젝트에서 Git Hook을 쉽게 설정할 수 있게 해주는 도구
- **pre-commit**: 특정 파일 타입에 대한 검사를 쉽게 설정할 수 있는 프레임워크
- **commitlint**: 커밋 메시지를 검증하는 도구
- **lint-staged**: 스테이징된 파일에 대해서만 린터를 실행하는 도구