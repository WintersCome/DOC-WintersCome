1. 인증/인가 
2. 마이페이지
3. 게시판
--- 

## 도메인

> 추가 예정

## 이름 형식

> url : cebab-case   
> param: camelCase

#### result 형식

```
{
  "code": 200,
  "message": "success"
}
```

```
{
  "code": 400,
  "message": "user not found"
}
```

```
{
  "code": 200,
  "message": "success"
  "data": {
    "name": "aaa",
    ...
  }
}

```

---

## 인증/인가

### 회원가입

POST   
> /api/member

|key|required|description|example|
|---|---|---|---|
|nickName|Y|유저 닉네임, 프로필 이름|YunHee|
|email|Y|유저 이메일|abc@gmail.com|
|password|Y|유저 비밀번호|qwer1234!|
|age|Y|유저 나이|20|
|phone|Y|유저 핸드폰 번호|010-1231-1234|
|zipcode|Y|유저 우편번호|01023|
|address|Y|유저 기본 주소|광화문우체국사서함 45|
|addressDetail|Y|유저 상세 주소|A아파트 11동 1234호|

패스워드 규칙: 영소문자(a~z), 숫자(0~9), 특수문자 조합으로 최소 9자 최대 14자




### 로그인

POST  
> /api/signin

|key|required|description|example|
|---|---|---|---|
|email|Y|유저 이메일|abc@gmail.com|
|password|Y|유저 비밀번호|qwer1234!|

- 응답 값으로 토큰을 받음
- 토큰 유효기간은 24시간

```
{
  "code": 200,
  "message": "success"
  "token": "sdfasdfsdf.sfasdfsdfsaas.dasdasa"
}
```


### 로그아웃

POST  
> /api/signout  
헤더에 토큰 넣어서 요청 보낼 것 

---

## 마이페이지

### 회원정보 불러오기
GET
> /api/member  
헤더에 토큰 넣어서 요청 보낼 것 


```
{
  "code": 200,
  "message": "success"
  "data": {
    "nickName": ""
    ... email, age, phone, zipcode, address, addressDetail
  }
}
```


### 회원정보 수정
PUT
> /api/member  
헤더에 토큰 넣어서 요청 보낼 것 


### 회원 비밀번호 수정

PUT  
> /api/member/password  
헤더에 토큰 넣어서 요청 보낼 것

|key|required|description|example|
|---|---|---|---|
|password|Y|유저 비밀번호|qwer1234!|



### 회원 비밀번호 초기화
PUT  
> /api/member/password  
헤더에 토큰 넣어서 요청 보낼 것

|key|required|description|example|
|---|---|---|---|
|email|Y|유저 이메일|abc@gmail.com|
|nickName|Y|유저 닉네임, 프로필 이름|YunHee|

- 이메일, 닉네임을 값으로 주고 요청 시 해당 이메일에 패스워드 초기화 링크를 보내준다
- 이메일 링크 클릭: 패스워드 변경 화면으로 이동 후 임시 토큰을 응답 값으로 받는다  
- 헤더에 임시 토큰을 넣고, 바디에 변경된 패스워드 값 보내기
- 요청 성공 시 패스워드 변경


### 회원탈퇴

DELETE  
> /api/member
헤더에 토큰 넣어서 요청 보낼 것  

- 회원 탈퇴는 5분 후 삭제되도록 처리
- 탈퇴 성공 시 로그아웃 처리


===/// 다음 작성 예정 ///===

### 회원탈퇴 취소

--- 

## 게시판

### 목록 불러오기 

### 글 추가

### 글 삭제 

### 글 수정

### 덧글 불러오기

### 덧글 추가

### 덧글 삭제 

### 덧글 수정

---


