
# 파이썬 람다 함수 (Lambda Functions)

람다 함수는 파이썬에서 익명 함수(이름이 없는 함수)를 정의할 때 사용되는 키워드입니다. 람다 함수는 주로 간단한 연산을 수행할 때 사용되며, 함수형 프로그래밍에서 중요한 역할을 합니다.

## 1. 람다 함수의 기본 구조

람다 함수는 `lambda` 키워드를 사용하여 정의되며, 다음과 같은 구조를 가집니다:

```python
lambda 인수1, 인수2, ... : 표현식
```

- `lambda` 키워드는 람다 함수를 정의합니다.
- `인수`: 람다 함수에 전달되는 입력값입니다.
- `표현식`: 인수를 사용하여 계산될 단일 표현식입니다. 이 표현식의 결과가 함수의 반환값이 됩니다.

### 예제 1: 간단한 덧셈 람다 함수

```python
# 두 수를 더하는 람다 함수
add = lambda x, y: x + y
result = add(2, 3)
# add 함수는 2와 3을 더하여 5를 반환합니다.
print(result)  # 출력: 5
```

### 예제 2: 리스트 정렬에서의 람다 함수 사용

```python
# 각 문자열의 길이를 기준으로 리스트를 정렬하는 예제
words = ['apple', 'banana', 'cherry', 'date']
sorted_words = sorted(words, key=lambda word: len(word))
# sorted 함수는 각 문자열의 길이를 기준으로 리스트를 정렬합니다.
# 최종적으로 ['date', 'apple', 'banana', 'cherry']가 됩니다.
print(sorted_words)  # 출력: ['date', 'apple', 'banana', 'cherry']
```

## 2. 함수형 프로그래밍과 람다 함수

함수형 프로그래밍은 프로그래밍 패러다임 중 하나로, **순수 함수**와 **상태가 없는 데이터 처리**를 강조합니다. 이는 같은 입력이 주어지면 항상 같은 출력을 내는 함수로 프로그램을 구성하는 방식을 의미합니다. 함수형 프로그래밍은 다음과 같은 주요 특징을 가집니다:

- **순수 함수**: 외부 상태를 변경하지 않고, 같은 입력값에 대해 항상 같은 출력을 반환하는 함수입니다.
- **불변성**: 데이터는 한 번 생성되면 변경되지 않습니다. 데이터의 변경이 필요한 경우, 새로운 데이터를 생성하여 사용합니다.
- **고차 함수**(Higher-order Functions): 다른 함수를 인수로 받거나, 함수를 반환하는 함수입니다. 고차 함수는 함수형 프로그래밍의 중요한 개념입니다.

람다 함수는 이러한 함수형 프로그래밍의 개념을 실현하는 도구로서, 파이썬에서 간결하고 명확한 코드를 작성하는 데 매우 유용합니다.

### 예제 3: map() 함수와 람다 함수

```python
# 리스트의 각 요소를 제곱하는 예제
numbers = [1, 2, 3, 4, 5]
squared_numbers = list(map(lambda x: x ** 2, numbers))
# map 함수는 리스트의 각 요소에 대해 람다 함수를 적용하여 제곱값을 계산합니다.
# 최종적으로 [1, 4, 9, 16, 25]가 됩니다.
print(squared_numbers)  # 출력: [1, 4, 9, 16, 25]
```

### 예제 4: filter() 함수와 람다 함수

```python
# 리스트에서 짝수만 필터링하는 예제
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))
# filter 함수는 리스트의 각 요소에 대해 람다 함수를 적용하여 짝수만 필터링합니다.
# 최종적으로 [2, 4, 6, 8, 10]이 됩니다.
print(even_numbers)  # 출력: [2, 4, 6, 8, 10]
```

## 3. 일급 객체 (First-Class Objects)와 람다 함수

파이썬에서 함수는 **일급 객체**로 취급됩니다. 일급 객체란, 프로그래밍 언어에서 다음과 같은 특성을 가지는 객체를 의미합니다:

1. **변수나 데이터 구조에 할당할 수 있다.**
2. **다른 함수의 인수로 전달할 수 있다.**
3. **다른 함수의 반환값으로 사용할 수 있다.**

이러한 특성 덕분에, 파이썬의 함수는 매우 유연하게 사용될 수 있습니다. 아래는 이러한 특성을 설명하는 예제들입니다.

### 예제 5: 함수의 변수 할당

```python
# 함수 정의
def greet(name):
    return f"Hello, {name}!"

# 함수를 변수에 할당
greeting = greet

# 변수를 통해 함수 호출
print(greeting("Alice"))  # 출력: Hello, Alice!
```

### 예제 6: 함수의 인수로 함수 전달

```python
# 함수 정의
def call_function(func, value):
    return func(value)

# 람다 함수를 인수로 전달
result = call_function(lambda x: x ** 2, 5)
print(result)  # 출력: 25
```

### 예제 7: 함수의 반환값으로 함수 사용

```python
# 함수 정의
def make_multiplier(factor):
    return lambda x: x * factor

# 함수 반환값으로 람다 함수 사용
double = make_multiplier(2)
print(double(10))  # 출력: 20
```

람다 함수는 이러한 일급 객체의 특성을 최대한 활용하여 간단하게 익명 함수를 정의할 수 있는 수단을 제공합니다. 특히, 일시적인 연산을 위해 짧고 단순한 함수를 정의할 때 매우 유용합니다. 람다 함수는 코드의 간결함과 명확성을 제공하며, 함수형 프로그래밍에서 중요한 역할을 합니다.
