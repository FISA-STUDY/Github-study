## 커밋 컨벤션이란?

- 간단히 말하면, 원격 저장소에 commit 할 때 보내는 commit message에 대한 약속  
- 크게 제목 / 본문 / 꼬리말로 나뉨  
- body와 footer는 선택 사항이므로 title만 적어도 무방

<br/>

### 📌 기본 형식
| type: subject |
 <br/>
| body          |
 <br/>
| footer        |

---

## 커밋 타입 규칙

- 아래와 같은 태그 뒤에 제목을 작성함

<img width="522" alt="Image" src="https://github.com/user-attachments/assets/9755c4d4-7482-4905-b58b-82af2645b2d1" />

> 예시 태그: `Feat`, `Fix`, `Docs`, `Style`, `Refactor`, `Test`, `Chore` 등

---

## Subject Rule

- 제목은 최대 50자  
- 마침표 및 특수기호 사용 X  
- 영어로 작성 시 첫 글자는 대문자  
- 명령문 형태로 간결하게 작성

---

## Body Rule

- 한 줄당 72자 내로 작성  
- 기능에 대한 상세한 설명  
- **어떻게** 보다는 **무엇을**, **왜** 했는지를 중심으로 작성

---

## Footer Rule

- `#이슈 번호` 형식으로 작성  
- 이슈 트래커 ID 명시  
- 여러 개 이슈가 있을 경우 `,`로 구분


---

## 예시

- Feat: 로그인 기능 구현
   <br/>
  SNS, 이메일 중복 확인 및 API 개발
   <br/>
  Resolves: #222


---
## Gitmoji

- 커밋 메시지에 이모지를 사용해 의미를 전달할 수도 있음  
- VSCode 등 확장에서 `gitmoji` 검색해서 설치 가능

### 예시 목록
- ✨ Feat: 기능 추가  
- 🐛 Fix: 버그 수정  
- 📝 Docs: 문서 작성  
- 🎨 Style: 코드 포맷팅, 세미콜론 누락 등  
- 🔧 Chore: 빌드 업무, 패키지 매니저 수정 등  

---
