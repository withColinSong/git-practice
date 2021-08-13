# 목차
- [목차](#목차)
- [1. 계정 1개 등록하기](#1-계정-1개-등록하기)
  - [1.1 SSH key](#11-ssh-key)
    - [1.1.1 code](#111-code)
  - [1.2. SSH 등록](#12-ssh-등록)
  - [1.3. 깃허브에 SSH 등록](#13-깃허브에-ssh-등록)


한 컴퓨터에 깃 계정 2개 사용하기
> 회사 계정과, 개인 계정을 노트북에서 사용하고 싶어 찾아보고 테스트 완료 후 정리 예정<br>
> 환경 : window, git bash<br>
> 먼저 계정 1개를 등록 후에 추가적인 설정을 정리 예정

# 1. 계정 1개 등록하기

## 1.1 SSH key
```
$ssh-keygen -t rsa -C '계정이메일1'
```
- git 계정으로 등록 되어 있는 메일로 등록할 것
### 1.1.1 code

```
$ ssh-keygen -t rsa -C "test@gmail.com"
```

```
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/USER/.ssh/id_rsa): // 지정하지 않는다면 enter
```
![image](https://user-images.githubusercontent.com/71534090/129359168-26e807de-c8d6-435a-9ee5-258a39e1c732.png)
- path를 설정하지 않으면 기본으로 `(/c/Users/USER/.ssh)` 경로의 `id_rsa`파일명으로 키가 저장됨<br>
- 경로를 지정할 수 있음. 경로를 지정하지 않는다면 enter
- `id_rsa` / `id_rsa.pub` 생성됨

```
Enter passphrase (empty for no passphrase): // 비밀번호 설정 하지 않는다면 enter
Enter same passphrase again: // enter
```


## 1.2. SSH 등록

```
ssh-add ~/.ssh/id_rsa
ssh-add ~/.ssh/id_rsa_company
```
- 아래와 같은 오류가 뜬다면 `$eval $(ssh-agent)` 을 입력한다.
```
Could not open a connection to your authentication agent.
```

```
$eval $(ssh-agent)
```

```
Agent pid 1234 // 뜬다면 ok.
```
- ssh-agent는 개인키의 비밀번호를 암호화 해 기억해두고 처음 한 번만 개인키 비밀번호를 입력하면  다음부터는 기억한 비밀번호를 이용하므로 사용자는 또 비밀번호를 입력하지 않아도 된다. <br>
> 비밀번호를 입력하지 않았다면 사실상 의미가 없음.

## 1.3. 깃허브에 SSH 등록
1. 깃허브 로그인
2. 마이페이지 > setting > SSH and GPG keys
![image](https://user-images.githubusercontent.com/71534090/129361629-e4f11fc5-29f5-4d46-9b07-410d3f1501e9.png)

git bash
```
$cat .ssh/id_rsa.pub // 공개키 복사
```
- `.pub`은 공개키

![image](https://user-images.githubusercontent.com/71534090/129361983-3aab6016-9e81-450f-b479-27429e1ce2cf.png)
- 복사한 키를 key에 넣어주고, title은 구분이 쉽도록 적어준다.
