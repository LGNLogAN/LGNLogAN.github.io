---
layout: single
title:  "Python을 활용한 패스워드 설정 프로그램"
---

# Last modified 2023-05-17  

# Python 의 예외처리 , Class 문을 활용해서 패스워드 규칙 ( 대문자 포함 , 특수문자 포함 등 )을 적용

```python  

print("******************비밀번호 규칙******************\n1. 최소 10글자에서 최대 20글자\n2. 공백(space) 포함 불가\n3. 특수문자 ~ , ! , @ 중 하나 이상을 반드시 포함\n*************************************************")

class myerror1(Exception):
  def __str__(self):
    return "10 ~ 20 글자로 입력해주세요"

class myerror2(Exception):
  def __str__(self):
    return "공백 ( Space )는 포함 불가입니다"

class myerror3(Exception):
  def __str__(self):
    return "특수문자 ~ , ! , @  중 하나 이상을 반드시 포함해주세요"

while True:
  try:
    pwd = input("비밀번호를 입력하세요 : ")
    pwd2 = len(pwd)

    if pwd2 < 10:    
      raise myerror1()
      
    elif pwd2 > 20:
      raise myerror1()

    elif pwd.find(" ") != -1:
      raise myerror2()

    elif pwd.find("!") == -1 and pwd.find("@") == -1 and pwd.find("~") == -1:
      raise myerror3()
    
    else:
      print("비밀번호는 %s입니다"%pwd)
      break

  except myerror1 as e:
    print(e)
  except myerror2 as e:
    print(e)
  except myerror3 as e:
    print(e)
```
