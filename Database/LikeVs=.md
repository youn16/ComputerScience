### like와 =의 차이

`=` : 동등 조건
`like` : 포함 조건

```
SELECT * FROM employees WHERE email LIKE 'ze%';
 
SELECT * FROM employees WHERE email LIKE '%com';
 
SELECT * FROM employees WHERE first_name LIKE '%재%';--앞뒤로 뭐가 오든 상관없는데 재를 포함하는것을 가져와라
```

' % ' 이 표시말고 LKIE 에서는 ' _ ' 언더바 표시역시 사용이 가능합니다.

' _ ' 언더바 이 표시는 문자 하나만 임의의 문자를 허용하는 조건을 지정합니다.

