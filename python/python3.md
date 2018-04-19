# Python3
한줄읽고 한줄 실행하는 Interpreter언어
**컴파일  과정이 없으므로 빠른 실행이 가능함, 대화식 프로그래밍이 가능함**

- 코드가 읽기 쉽고 성능도 뛰어남
- 강력한 데이터 분석 라이브러리들을 제공
- 기계학습과 데이터 과학 분야에서 널리 사용되고 있음 
- 범용적 언어 


## 파이썬 라이브러리
- Numpy - 수치 계산용
- Pandas - 데이터 분석용
- Matplotlib - 그래프 출력용

## Anaconda 
데이터 분석에 유용한 라이브러리가 많이 포함된 배포판 

### Anaconda update 
conda update conda

### 변수 선언 
```python
num_student = 5
```

### for 문 
```python
for i in range(3):
    print(i)
```

`:` 블럭과 같은 개념 

### if else 문
```python
num_student = 5
if num_student > 4:
    print(True)
else: 
    print(False)
```

### 함수 정의 
```python
def message():
    print("hello python")
    
message()
```

### 도움말 사용 방법
뒤에 ?를 붙인다. 
```python
message? 
```

### ipyton에서 사용이 가능한 매직명령어 
%를 사용한다. 
```python
%who 
```

### 변수 삭제 
```python
a = 3
del a 
```

### 변수 선언 
```python
a,b,c,d,e = 10,20,30,40,50
```

### 시간 측정 
range(n): 범위 지정 0~n
sum(n) : 1~n까지의 합계
10 ** 3 : 10의 3제곱
```python
range(10) 
```
```python
for i range(10):
    print(i)
```
0~9까지 출력 

```python
sum(n)
```

## 기본자료형 
### 예약어 


