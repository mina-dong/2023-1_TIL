# Chapter5_연산

5.1 연산기 개요
---

연산기 구조
>* 처리할 데이터(입력)  - 입력으로 두개의 데이터를 받음, 데이터는 레지스터에 저장된 값일 수도 있고 레지스터에 저장된 값일 수도 있다.
>*  제어신호(입력)  
>*  연산결과(출력)  
>*  상태정보(출력)  

연산의 종류
>*  단항 연산자 (unary operator) - (음수 만들기), 1의 보수(NOT), 왼쪽/오른쪽 시프트, 증가, 감소
>* 이항 연산자 (binary operator) - 사칙 연산(+, -, ⅹ, /), 논리 연산(AND, OR, XOR), 비교(compare, test)

5.2 정수 표현
---

부호 없는 수 - 0을 포함하여 양정수만을 표현  
부호있는 수 - 0과 양수, 음수를 모두 표현한다.   
실수 - 소수점을 표현하는 수. 부동소수점 소수 라고도 부름.   

### 5.2.1 부호화 크기
부호화 크기는 사람이 상요아는 양수와 음수를 표현하는 방법과 개념적으로 비슷함.. 데이터를 표현하는 N비트의 단어의 가장 왼쪽 비트를 부호 비트로 사용한다. 

부호 비트(sign bit): S = a_n-1  

19_2 = 10011_2  
+19 = 8비트로 0001 0011_2 임.
-19는 +19에서 가장 왼쪽의 부호 비트를 1로 변경하여 표현함. 즉, -19는 1001 0011_2 임.  

n비트 표현 범위: -(2n-1-1) ~ +(2n-1-1)  

0이 두 개: 0000_0000, 1000_0000  
덧셈, 뺄셈을 계산할 때, 부호를 별도로 고려해야 한다.

### 5.2.2 보수
보수 - 서로 보호하는 수  

임의의 R진법에 N에 대한 보수는 R-1 보수와 R의 보수 두 가지가 있다.

10진수는, 9의 보수와 10의 보수가 있고  
2진수는 2의 보수와 1의 보수가 있다.

(R-1)의 보수: N + C_(R-1) = R^n- 1
R의 보수: N + C_R = R^n = 10…0


(예제 1) 3자리 10진수 457  
9의 보수 = 1000 - 457 = 542   
10의 보수 = 9의 보수 + 1 = 543  

(예제 2) 8비트 2진수 0011_1000
1의 보수 = 1111_1111 - 0011_1000 = 1100_0111
2의 보수 = 1의 보수 + 1 = 1100_0111 + 1 = 1100_1000 

8비트를 벗어난 수는 제거한다.

### 5.2.3 2의 보수

표현 범위  
n비트 정수의 표현 범위: -2^n-1 ~ +(2^n-1-1) 

8비트라면 -2^8-1 ~ +(2^8-1 -1) = -128 ~ (128-1) = -128 ~ 127

부호 확장 (sign expansion)  
>* n비트 정수를 p비트로 확장 (n<p)
>* 늘어나는 비트를 부호 비트로 채워야 크기가 변하지 않는다.

+106과 -106에 대한 16비트 표현
>* +10610 = 0100_10102 = 0000_0000_0100_1010
>* –10610 = 1011_01102 = 1111_1111_1011_0110

5.3 논리 연산
---
### 5.3.1 NOT 연산
Not 연산
>* 오퍼랜드의 각 비트를 NOT
>* 명령어: NOT R // R  R에 대한 1의 보수

[예제 5-7] R0 = 0010_1011일 때, NOT R0 실행 결과는?
>* 명령어 NOT R0
>* 실행 결과 R0 = 1101_0100

### 5.3.2 AND 연산
AND 연산
>* 비트 단위로 AND 연산을 수행한다. 
>* 명령어 AND R1, R2 // R1 <- R1 AND R2

마스크(mask) 연산
>* 특정 비트를 0으로 만든다.
>* R2의 값 = 마스크 패턴

### 5.3.3 OR 연산
>* 비트 단위로 OR 연산을 수행한다.
>* 명령어 OR R1, R2 // R1 <- R1 OR R2
 
선택적 세트(selective set) 연산
>* 특정 비트를 1로 만든다.

### 5.3.4 XOR 연산

XOR 연산
>* 비트 단위로 XOR 연산을 수행한다.
>* 명령어 XOR R1, R2 // R1  R1 XOR R2

선택적 보수 (selective complement) 연산
>* 특정 비트를 보수로 만든다.
>* 자신에 대한 XOR 연산 결과는 항상 0000_0000

체크섬(checksum)
>* 일련의 데이터에 대하여 XOR 연산으로 만들어진 값
>* 데이터 무결성 확인용