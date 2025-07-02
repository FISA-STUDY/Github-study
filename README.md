# 원격 저장소

# 원격 저장소(remote repository) VS 지역 저장소(local repository)

![제목_없는_다이어그램 drawio](https://github.com/user-attachments/assets/7f0ea65f-3ccb-4f63-afa4-0e74b0b9f50d)

## Github깃허브

원격 저장소의 기능을 웹에서 제공하는 서비스 중 하나가 깃허브(Github)이다

# git clone vs git pull

## git clone

**git clone : 리모트 설정을 자동으로 해주는 초기 다운로드 때 사용**

**git clone {URL}**

**→ git init + git remote add origin {URL} + git pull origin master**

<aside>

git init : git 프로젝트를 시작함

git remote add origin {URL} : url을 원격 레포지토리로 지정함

git pull origin master: 원격 리포지토리를 현재 master에 병합함

</aside>

## git pull

**git pull : 리모트 설정이 이미 되어 있을 때 업데이트 사항 등을 다운로드 할때 사용**

<aside>

git remote -v로 현재 연결되어있는지 확인 가능함

</aside>

# git bash 실습 해보기

![image](https://github.com/user-attachments/assets/e0c62919-9038-4e34-b63b-63819a27a7eb)

일단 fork를 눌러서 제 github에 저장하고 그 뒤 clone으로 작업해보겠습니다.


![image 1](https://github.com/user-attachments/assets/43c996c2-5a9a-47c8-ac5b-df3ec5fda968)

```bash
git clone https://github.com/hyewon8245/Github-study.git
```

![image 2](https://github.com/user-attachments/assets/af1a9406-ef89-45a2-9d94-9b77d8c68fef)


```bash
$ git branch -a
#현재 branch를 모두 보여줌
#현재 브렌치는 main만 있는 걸 확인가능
```

![image 3](https://github.com/user-attachments/assets/5fd3b4c7-9c47-4891-b45b-89a93d438997)

```bash
$ git checkout -b hyewon
# branch 생성 및 변경
#예시로 hyewon을 branch를 생성함
```


![image 4](https://github.com/user-attachments/assets/8aac6fad-b98e-46dd-8ace-5bf017e36c43)

```bash
$ git config --global user.name "hyewon8245"
$ git config --global user.email "yully8245@gmail.com"
#git 초기 설정

```

![image 5](https://github.com/user-attachments/assets/99fb113a-67af-4039-b7ef-bde455c4a1c4)


```bash
git status
git add hyewon_check.txt
#hyewon_check.txt 개인적으로 만든 파일 넣기
```

![image 6](https://github.com/user-attachments/assets/b5086f33-7504-4593-a393-dba44aa6a529)


```bash
 git push -u origin hyewon
 #origin 저장소에 branch hyewon에 저장하기
 #아직 되진 않음. github에 로그인을 해야함
```

![image 7](https://github.com/user-attachments/assets/dd7aeef7-41a2-4eda-9613-1fdfa33efa25)


```bash
git status
#현재 branch와 상태 확인가능
git commit -m "Your commit message here"
#commit -m으로 commti message를 바로 적을 수 있음
git push origin hyewon
#push한다

```

![image 8](https://github.com/user-attachments/assets/bb707c47-8fda-4d07-9ae8-042a08dbe31f)


<aside>

text파일이 저장된 걸 확인할 수 있음

</aside>
