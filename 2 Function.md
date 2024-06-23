# 1 함수의 개념
## 1) 함수 와 합성 함수
### 함수 f와 함수 g가 있고 함수 f의 출력이 함수 g의 입력이 될 때 두 함수의 관계를 합성 함수라고 한다.
### $h(x)=g(f(x))=g\circ f$ 

## 2) 함수의 극한, 연속
### 함수의 극한 $\lim_{x = a} f(x)=L$ a의 양반향에서 값은 극한 값을 가져야 한다. f(a)=L이 될 필요는 없다.
### [극한 개념](https://ko.khanacademy.org/math/precalculus/x9e81a4f98389efdf:limits-and-continuity/x9e81a4f98389efdf:defining-limits-and-using-limit-notation/a/limits-intro)

### 함수의 연속성 : f 함수가 x=a에서 연속이라는 것은 그 점에서의 극한 값과 함수 값이 존재하고 두 값이 일치함을 의미한다.  
### $\lim_{x = a} f(x)=f(a)$

### 최대 최소정리(Exterme value theorem) : 함수 그래프가 끊임 없이 매끄럽게 이어지면 그 함수는 연속이라고 정리할 수 있고, 이때 함수가 폐구간[a,b]에서 연속이면 함수가 최댓값과 최솟값을 갖는다.  

### 중간값 정리[Intermediate value theorem](https://ko.khanacademy.org/math/precalculus/x9e81a4f98389efdf:limits-and-continuity/x9e81a4f98389efdf:working-with-the-intermediate-value-theorem/v/intermediate-value-theorem-example)  
### 어떤 함수가 폐구간[a,b]에서 연속이고 f(a)와 f(b)의 값이 같지 않은 조건에서 f(a)와 f(b)사이의 어떤 값 k에 대해 f(c)=k인 c가 적어도 한 개 이상 존재하는 것을 의미 한다.

# 2 미분의 이해
## 1)도함수와 정적분(Definite integral)
### 함수의 극한이 정의 되면, 함수의 국소적 또는 순간적 특징을 나타내는 도함수와 함수의 전체적인 특징을 나타내는 정적분을 정의 할 수 있다.  
### 도함수 정의 $f'(x)=\lim_{\Delta x \to 0} \frac{f(a+\Delta x)-f(a)}{\Delta x}$  
### 기본 미분 공식  
### $\frac{d}{dx}x^n=nx^{n-1}, \quad \frac{d}{dx}\text{ln}x=\frac{1}{x}, \quad \frac{d}{dx}e^x=e^x, \quad \frac{d}{dx}(fg)=f\frac{dg}{dx}+g\frac{df}{dx}$  
### 연쇄법칙(Chain rule) - 합성함수의 도함수를 구할 때 활용 $f\circ g$의 도함수는 $f'(g(x))g'(x)$로 구함수 있다.

```python
# sympy 필요 x,y,z와 같이 symbolic지원


import sympy as sp
x=sp.Symbol('x')
print(sp.diff(3*x**2+1,x)) # 6*x 도함수

# scipy는 과학 계삭에 필요
from scipy.misc import derivative

def f(x):
  return 3*x**2+1

def d(x):
  return derivate(f,x)

print(d(2.0))  # 12.0 answer. sp.diff(3*x**2+1).subs(x,2)

```
# 정분의 이해
### 1) 부정적분과 정적분  
### 부정적분(indefinite integral)로 구간이 정해 있지 않아, 상수항을 C로 나타낸다. 미분의 역 연산(anti-derivate)  
### 정적분(definte integral)로 구간이 정해져 있는 경우로, 넓이나 부피를 구할 때 사용 한다.
### $F'(x)=f(x) \quad \longrightarrow \int_{a}^{b}f(x)dx =F(b)-F(a)$
```python
import sympy as sp
x=sp.Symbo('x')
sp.integrate(3.0*x**2+1) # 부정적분

from scipy.integrate import quad

def f(x):
  return 3.0*x**2+1
i=qaud(f,0,2) # 정적분 구간[0,2]
i[0] # 정적분 값
i[1] # 정적분의 오
```
