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
# 3 정분의 이해
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
# 4 필요 개념
### 1) '해'를 찾는 방법 예를 들어 2차 함수에 대한 미분 값이 x+3일 때 x+3=0이 되는 해를 구하는 방법
``` python
from scipy.optimize import fsolve
line =lambda x : x+3

solution=fsolve(line, -2) # -2부터 해를 찾아 간다. fsolve함수의 경우 첫 인자는 수식, 두 번째 인자는 초기 시작 조건
```
### 2) 편미분(Partial derivative)  
### E=f(x,y,z) 인 경우 3가지 변수에 대하 미분을 할 수 있다. 변수 x에 대해 미분 한 경우 (partial derivative of with respect to x로 읽음) $\frac{\partial f}{\partial x}$ 표시한다.
### 이렇게 다변수 함수에서 여러 개의 편도함수를 구할 수 있고, 다변수 함수의 모든 편도함수를 다음처럼 한 묶음으로 표현 할 수 있는데 이를 그라디언트벡터(gradient vector:기울기 벡터)라 부른다.  
### 함수 f(x,y,z)의 기울기 벡터 $\nabla f=grad f=(\frac{\partial f}{\partial x},\frac{\partial f}{\partial y},\frac{\partial f}{\partial z})$ 로 표시할 수 있다.  
### $\nabla$은 편미분 연산자($\frac{\partial }{\partial x},\frac{\partial }{\partial y},\frac{\partial }{\partial z}$)를 표시한다.  
### 기울기벡터(gradient vector)는 매끄러운 곡면 f(x,y,z)=0에 수직인 법선 벡터이다. 즉, 고면 위의 임의의 점을 잡았을 때 그 점을 지나는 곡면 위의 모든 곡선의 접선 벡터에 수직인 벡터를 나타내게 된다.

### 3)경사하강법(gradient descent)  
### 미분을 통해 최적의 값을 찾는 방법. 예를 들어 2차 함수의 경우 경우 기울기의 변화가 +에서-로 혹은 그 반대일 경우에 최소 혹은 최대 값을 가지는 것을 찾을 수 있다.
### 인공지능에서는 뉴턴랩슨 메서드가 대표적이다.
``` python
def f(x):
  return (x**3-1)

from scipy import optimize

root=optimize.newton(f,1.5) # 1.5지점에서 시작하여 뉴턴랩슨 메서드로 x의 해를 구함
root=optimize.newton(f,1.5,fprime=lambda x : 3x**2) # f(x)의 미분값을 추가로 넣어준 경우, 위에 식 보다 더 정확한 값.
```

### fsolve와 newton메서드의 차이 : 전자는 '해'를 직접 구하는 방식이고, 후자는 경사 하강법(기울기의 변화 추이를 추적)을 통해 산출

### $y=(x+5)^2$의 국소[-10,10] 최솟값을 경사 하강법을 통해 구해 보자  
### 1단계 : x의 초기 값을 3 $x_{0}=3$으로 하고 기울기를 찾아본다. dy/dx=2*(x+5)가 된다.  
### 2단계 : 1단계에 구한 기울기를 x축에서 왼쪽 방향으로 움직인다. 그런데 얼마씩 움직일지를 정한다 이를 학슬률(Learning rate)이라고 한다. 일단 0.01로 설정  
### 3단계 : 2단계를 반복하는데, 2단계에서 새로 계산된 x값을 다음 단계의 초기 값으로 사용  
### 이전 단계의 x와 다음 단계의 x를 비교하면 값의 차이가 점점 줄어드는 것을 알 수 있고, 이 차이가 기준 값(tolerance rate)보다 작아지면 반복 작업을 멈춘다.
###  일반식 $x_{n+1}=x_{n}-\text{lr} \times \frac{d y}{dx}$ 된다. 이를 풀어 쓰면 아래와 같다.  
###  $x_{1}=x_{0}-0.01 \times  2 \times (x_{0}+5)=3-0.01 \times 2 \times(3+5)=2.84$  
###  $x_{2}=x_{1}-0.01 \times  2 \times (x_{1}+5)=2.84-0.001 \times 2 \times (2.84 +5)=2.6832 \quad\cdots $
### 상기 수식을 사용하는 방법이 newton함수이며 이를 풀어서 구현 하면 다음과 같다.
``` python
cur_x=3 # initial x value
rate =0.01 # Learning rate
precision = 0.000001 # tolerance rate
previous_step_size=1
max_iters =10000 # maximun repetation number
iters =0 # initial iteration value
df = lambda x : 2*(x+5) # derivate function

while (previous_step_size>precision) and (iters <max_iters):
  prev_x =cur_x # Copy current x to previous x
  cur_x=cur_x-rate*df(prev_x) # gradient descent
  previous_step_size=abs(cur_x-prev_x) # delta value
  iters=iters+1

