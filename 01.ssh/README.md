# 한 컴퓨터에 깃 계정 2개 사용하기

> 회사 계정과, 개인 계정을 노트북에서 사용하고 싶어 찾아보고 테스트 완료 후 정리 예정<br>
> 환경 : window

## 1.1 SSH key
```
ssh-keygen -t rsa -C '계정이메일1'
ssh-keygen -t rsa -C '계정이메일2'
```

## 1.2. ssh-agent

```
eval $(ssh-agent)
```
