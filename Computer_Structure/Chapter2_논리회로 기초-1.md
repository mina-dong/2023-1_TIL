# Chapter2_논리회로 기초

2.1 수와 코드
---
부호 없는 수(unsigned number)를 대상으로 컴퓨터가 수를 다루는 방법

### 2.1.1 수의 체계

| 수의 표현 | 1    | 2    | 3    | 4 |. | 5|6 |
|-----------|------|------|------|---|-- | -- |-- |
| 자릿수    | 3    | 2    | 1    | 0 |  |-1|-2 |
| 무게      | 10^3 | 10^2 | 10^1 | 10^0 |  |10^-1 | 10^-2|

(예제)  
(519.87)₁₀ = 5\*10^2  +  10\*10^1  +  9\*10^0 + 8\*10^-1 + 7\*10^-2  
= 500 + 10 + 9+ 0.8 + 0.07  
= 519.87


### 2.1.2 R진법의 수

10진수의 적용한 개념을 임의의 R진법의 수로 확장할 수 있다.

### 2.1.3 진법 변환

(예제)  
1) (527)₁₀ → 8진수  

527/8=65...7 (X0 =7)  
65/8= 8...1 (X1 =1)   
8/8= 1...0 (X2 =0)   
1/8= 0...1 (X3 =1)

(527)₁₀ = (1017)₈

2) (27)10 → 2진수  

27/2=13...1(X0 =1)  
13/2= 6...1 (X1 =1)  
6/2= 3...0 (X2 =0)  
3/2= 1...1 (X3 =1)  
1/2= 0...1 (X4 =1)  

(27)₁₀ = (11011)₂

### 2.1.4 2진수, 8진수, 16진수
컴퓨터 안에서는 2진수를 사용하지만, 사람이 직접 다루기에는 불편하다. 2진수로 변환이 쉬운 8진수 또는 16진수를 사용하는 것이 더 편리하다. (즉, 2진수를 3자리씩 읽으면 8진수. 2진수를 4자리씩 읽으면 16진수. 2^3 = 8, 2^4 = 16)

(예제)  
10110001101011.111100100  


010_110_001_101_011.111_100_100   
2 6 1 5 3. 7 4 4

0010_1100_0110_1011.1111_0010   
2 C 6 B. F 2

8진수(3자리씩)
| 010 | 110 | 001 | 101 | 011 |. |111|100|100|
|--|------|------|------|---|-- | -- |-- |--|
| 2    | 6    | 1    | 5    | 3 | . |7|4 |4|


16진수(4자리씩)
| 0010 | 1100 | 0110 | 1011 | . | 1111 | 0010 |
|------|------|------|------|---|------|------|
| 2    | C    | 6    | B    | . | F    | 2    |

### 2.1.5 코드(Code)
 유한 개의 원소로 구성된 집합의 원소들에게, 서로를 구분할 수 있는 유일한 수를 부여한 숫자.

 자주 사용하는 코드는 숫자코드, 문자코드, 그리고 명령어 코드. 숫자코드와 문자코드는 표준화 되어있으나, 명령오 코드는 컴퓨터의 중앙처리장치마다 다르게 정의되어 있음.


 ### 2.1.6 이진화 십진 코드(BCD, Binary Coded Decimal)
 10진법의 수를 표현한 코드로, 0부터 9까지 열 개의 기호에 2진법의 수를 할당하여 서로 구별할 수 있도록 만든 코드임. 

 기호는 모두 10개 이므로, 최소 4비트가 필요하다. (2^3(8)  < 10 < 2^4(16))

 | 10진수 | 8421 BCD 코드 | 3초과 8CD 코드 |
|--------|---------------|----------------|
| 0      | 0000          | 0011           |
| 1      | 0001          | 0010           |
| 2      | 0010          | 0001           |
| 3      | 0011          | 0000           |
| 4      | 0100          | 1111           |
| 5      | 0101          | 1110           |
| 6      | 0110          | 1101           |
| 7      | 0111          | 1100           |
| 8      | 1000          | 1011           |
| 9      | 1001          | 1010           |

 8421 BCD 코드는  각 자리의 무게를 더하여 만든 코드임.(이런 코드를 무게 코드라고 함)
 3초과 BDC 코드는, 8421 코드의 값에 3(0011)을 더해 만든 코드임. 

 (예제)  1225
 
8421 BCD 코드 : 0001_0010_0010_0101
3초과 BDC 코드 : 0100_0101_0101_1000

 ### 2.1.7 문자코드
 영문자와 특수기호, 숫자를 표현하는 코드임. 미국에서 제정된 ASCII(American Standard for Information Interchange)를 많이 사용한다.

 | 이진수 | 문자 | 이진수 | 문자 | 이진수 | 문자 | 이진수 | 문자 |
|--------|-------|--------|-------|--------|-------|--------|-------|
| 0000000| NUL   | 0100000| Space | 1000000| @     | 1100000| `     |
| 0000001| SOH   | 0100001| !     | 1000001| A     | 1100001| a     |
| 0000010| STX   | 0100010| "     | 1000010| B     | 1100010| b     |
| 0000011| ETX   | 0100011| #     | 1000011| C     | 1100011| c     |
| 0000100| EOT   | 0100100| $     | 1000100| D     | 1100100| d     |
| 0000101| ENQ   | 0100101| %     | 1000101| E     | 1100101| e     |
| 0000110| ACK   | 0100110| &     | 1000110| F     | 1100110| f     |
| 0000111| BEL   | 0100111| '     | 1000111| G     | 1100111| g     |
| 0001000| BS    | 0101000| (     | 1001000| H     | 1101000| h     |
| 0001001| HT    | 0101001| )     | 1001001| I     | 1101001| i     |
| 0001010| LF    | 0101010| *     | 1001010| J     | 1101010| j     |
| 0001011| VT    | 0101011| +     | 1001011| K     | 1101011| k     |
| 0001100| FF    | 0101100| ,     | 1001100| L     | 1101100| l     |
| 0001101| CR    | 0101101| -     | 1001101| M     | 1101101| m     |
| 0001110| SO    | 0101110| .     | 1001110| N     | 1101110| n     |
| 0001111| SI    | 0101111| /     | 1001111| O     | 1101111| o     |
| 0010000| DLE   | 0110000| 0     | 1010000| P     | 1110000| p     |
| 0010001| DC1   | 0110001| 1     | 1010001| Q     | 1110001| q     |
| 0010010| DC2   | 0110010| 2     | 1010010| R     | 1110010| r     |
| 0010011| DC3   | 0110011| 3     | 1010011| S     | 1110011| s    

7비트 코드로, 일반 적으로 맨 앞에 0을 추가하여 8비트로 표현한다.  
(예) G => 100_0111 -> 0100_0111 -> 4_7 -> 47h