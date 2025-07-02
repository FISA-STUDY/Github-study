
# Git flow

Git과 flow를 합친 말로, Git에서 제공하는 브랜치 기능을 활용한 이력 관리 전략을 말함.

---

## 📌 Git flow의 5 브랜치

- **main(master)** : 서비스를 직접 배포하는 브랜치  
- **feature(기능)** : 각 기능을 개발하는 브랜치  
- **develop(개발)** : feature에서 개발된 내용을 가진 브랜치  
- **release(배포)** : 배포 전 품질을 검사(QA)하기 위한 브랜치  
- **hotfix(수정)** : main 브랜치로 배포 후 문제가 생겨 수정을 하기 위한 브랜치  

<br/>

> main과 develop 브랜치는 보통 필수적으로 만들고  
> 나머지는 선택이므로, 본인이 진행 중인 프로젝트의 성격과 특징에 따라 브랜치를 생성 및 이용하면 됨

<br/>

![Image](https://github.com/user-attachments/assets/b73422d6-292f-4cd4-ba18-158a22c81d51)

---

## 🔎 왜 Git flow를 사용할까?

- 브랜치의 효율적인 유지 및 보수를 위함  
- 협업 중 각자 수정하는 코드의 충돌을 방지하기 위함  
- 개발 중인 기능이나 수정 사항이 서로 독립적이게 되며  
  각 작업 단위의 Rollback이 가능함

---

## 🔁 vs GitHub Flow

- 단일 브랜치(`master`)만을 사용  
- `master` 브랜치에서는 배포를 위한 소스코드를 관리  
- `feature` 브랜치에서는 신규 기능 개발  
- 작업 완료 시 Pull Request를 생성해 리뷰를 요청하고  
  이를 accept하면 해당 feature 브랜치를 `master` 브랜치로 merge함

<br/>

![Image](https://github.com/user-attachments/assets/e96ce770-47f1-46f0-bacc-b0f1c3725765)

---

## ⚖️ 그렇다면 어떤 걸 사용해야 할까?

### 브랜치 수에 따른 비교

- Git Flow: 다양한 브랜치 사용  
- GitHub Flow: 단일 브랜치 사용

### 배포 방식

- Git Flow: `release`나 `hotfix` 브랜치를 통한 정확한 배포 절차  
- GitHub Flow: 단순하며 지속적인 배포 강조

<br/>

- Git Flow의 경우 구조가 복잡하며, 다 인원이 참여하는 프로젝트에 유리함  
  하지만 빠른 수정이나 배포 등 유연성에서 떨어짐

- GitHub Flow는 복잡한 테스트 절차를 거치지 않으면 위험성이 있지만  
  빠르고 유연한 배포가 가능함

---
