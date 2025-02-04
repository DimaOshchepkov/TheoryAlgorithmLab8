# Доказательства и анализ асимптотической сложности
## Задание 1

### Транзитивность:
Если $f(n) = \Theta(g(n))$ и $g(n) = \Theta(h(n))$, то $f(n) = \Theta(h(n))$.

Доказательство:
$f(n) = \Theta(g(n)) \Rightarrow \exists n_0 \in \mathbb{N}, 0 < c_1 \le c_2 : \forall n \ge n_0, c_1 \cdot g(n) \le f(n) \le c_2 \cdot g(n)$
$g(n) = \Theta(h(n)) \Rightarrow \exists n_0' \in \mathbb{N}, 0 < c_1' \le c_2' : \forall n \ge n_0', c_1' \cdot h(n) \le g(n) \le c_2' \cdot h(n)$

Перемножив неравенства, получим:
$c_1 \cdot c_1' \cdot h(n) \le f(n) \le c_2 \cdot c_2' \cdot h(n)$
Введем новые константы: $c_1'' = c_1 \cdot c_1'$, $c_2'' = c_2 \cdot c_2'$, $n_0'' = \max(n_0, n_0')$. Тогда:
$\exists n_0'' \in \mathbb{N}, 0 < c_1'' \le c_2'' : \forall n \ge n_0'', c_1'' \cdot h(n) \le f(n) \le c_2'' \cdot h(n)$

Следовательно, $f(n) = \Theta(h(n))$.

Аналогично доказывается, что если $f(n) = O(g(n))$ и $g(n) = O(h(n))$, то $f(n) = O(h(n))$.

Аналогично доказывается, что если $f(n) = \Omega(g(n))$ и $g(n) = \Omega(h(n))$, то $f(n) = \Omega(h(n))$.

### Рефлексивность:
$f(n) = \Theta(f(n))$

Доказательство:
Достаточно взять $c_1 = c_2 = 1$ и $n_0 = 1$.
$g(n) = \Theta(h(n)) \Rightarrow \exists n_0 \in \mathbb{N}, 0 < c_1=1 \le c_2=1 : \forall n \ge n_0, c_1 \cdot h(n) \le g(n) \le c_2 \cdot h(n)$


$f(n) = O(f(n))$
Доказательство:
Аналогично, достаточно взять $c = 1$ и $n_0 = 1$.


$f(n) = \Omega(f(n))$
Доказательство:
Аналогично, достаточно взять $c = 1$ и $n_0 = 1$.

Симметричность:
$f(n) = \Theta(g(n)) \Leftrightarrow g(n) = \Theta(f(n))$

Доказательство:
$f(n) = \Theta(g(n)) \Rightarrow \exists n_0 \in \mathbb{N}, 0 < c_1 \le c_2 : \forall n \ge n_0, c_1 \cdot g(n) \le f(n) \le c_2 \cdot g(n)$

Разделив все части неравенства на $c_1$ и $c_2$ (учитывая, что они положительны), получим:

$\frac{1}{c_2} \cdot f(n) \le g(n) \le \frac{1}{c_1} \cdot f(n)$

Следовательно, $g(n) = \Theta(f(n))$.

Симметрично доказывается обратное утверждение.

$f(n) = O(g(n)) \nLeftrightarrow g(n) = O(f(n))$
О-обозначение не симметрично. Контрпример: $f(n) = n$, $g(n) = n^2$.



### Обращение:

$f(n) = O(g(n)) \Leftrightarrow g(n) = \Omega(f(n))$

Доказательство:
$f(n) = O(g(n)) \Leftrightarrow g(n) = \Omega(f(n))$ 
$\exists n_0 \in \mathbb{N}, \exists c > 0 : \forall n \ge n_0, f(n) \le c \cdot g(n)$ 
$\forall n \ge n_0 : g(n)$ ограничивает $f(n)$  сверху:  $g(n) \le c_1 \cdot f(n) \Rightarrow \frac{1}{c_1} g(n) \le f(n) \Rightarrow g(n) = \Omega(f(n))$ 
$\forall n \ge n_0 : f(n)$  ограничивает $g(n)$  снизу: $c_1 \cdot f(n) \le g(n) \Rightarrow f(n) \le \frac{1}{c_1} g(n) \Rightarrow f(n) = O(g(n))$


# Задание 2

##### Сравнение $f(n) = n^2$ и $g(n) = n^2 + 1000n$:

Докажем, что $f(n) = \Theta(g(n))$:

Необходимо показать, что существуют константы $c_1$, $c_2$ и $n_0$ такие, что:
$c_1(n^2 + 1000n) \le n^2 \le c_2(n^2 + 1000n)$ для всех $n \ge n_0$

Левое неравенство: возьмем $c_1 = \frac{1}{1001}$ и $n_0 = 1$. Тогда:
$\frac{1}{1001}(n^2 + 1000n) \le n^2$ для всех $n \ge 1$.

Правое неравенство: возьмем $c_2 = 1$ и $n_0 = 1$. Тогда:
$n^2 \le n^2 + 1000n$ для всех $n \ge 1$.

Таким образом, $f(n) = \Theta(g(n))$.


##### Сравнение $f_1(n) = n^2$ и $f_3(n)$:

$f_1(n) \neq O(f_3(n))$:
Не существует $n_0$ (при нечетных n должно выполняться $n^2 \le c*n$, что невозможно)

$f_3(n) \neq \Omega(f_1(n))$:
Не существует $n_0$ (при четных n должно выполняться $n^3 \le c*n^2$, что невозможно)


##### Сравнение $f_1(n)$ и $f_4(n)$:

$f_1(n) = O(f_4(n))$:
Выберем $c = 1$ и $n_0 = 101$. Тогда $n^2 \le n^3$ для всех $n > n_0$.

$f_4(n) = \Omega(f_1(n))$:
Выберем $c = \frac{1}{101}$ и $n_0 = 101$. Тогда $n^3 \ge \frac{1}{101}n^2$ для всех $n > n_0$.



##### Сравнение $f_2(n) = n^2 + 1000n$ и $f_3(n)$:

$f_2(n) \neq O(f_3(n))$:
Не существует $n_0$ (при нечетных n $n^2 + 1000n \le c*n$, что невозможно)

$f_3(n) \neq \Omega(f_2(n))$:
Не существует $n_0$ (при четных n должно выполняться $n^3 \le c*(n^2 + 1000n)$, что невозможно)


##### Сравнение $f_2(n) = n^2 + 1000n$ и $f_4(n)$:

$f_2(n) = O(f_4(n))$:
Выберем $c = 5$ и $n_0 = 1010000$. Тогда $n^2 + 1000n \le c*n^3$ для всех $n > n_0$.

$f_4(n) = \Omega(f_2(n))$:
Выберем $c = \frac{1}{101}$ и $n_0 = 1010000$. Тогда $n^3 \ge \frac{1}{101}(n^2 + 1000n)$ для всех $n > n_0$.

##### Сравнение $f_3(n)$ и $f_4(n)$:

$f_3(n) = O(f_4(n))$:
Выберем $c = 1$ и $n_0 = 1$. Тогда $n^3 \le c*n^3$ для всех $n > n_0$ для четных n и подавдно для нечетных.

$f_4(n) = \Omega(f_3(n))$:
Возьмем с = 1 $n_0 = 1$  $с*n^3 \le n^3$



# Задание 3

$2^{n+1} = O(2^{n+1})$

По определению О-нотации, необходимо найти такие константы $c \ge 0$ и $n_0 \in \mathbb{N}$, что для всех $n \ge n_0$ выполняется неравенство:

$2^{n+1} \le c \cdot 2^{n+1}$

Это неравенство выполняется для любых $n$ при $c \ge 1$. Следовательно, $2^{n+1} = O(2^{n+1})$.

$2^{2n} = O(2^n)$


$2^{2n} \le c \cdot 2^n$

Разделим обе части неравенства на $2^n$ (это допустимо, так как $2^n > 0$ для всех $n$):

$2^{2n - n} \le c$

Однако, $2^{2n - n}$ стремится к бесконечности при $n \to \infty$, в то время как $c$ - константа. Получили противоречие. Значит, $2^{2n} \ne O(2^n)$.

# Задание 4

Определим, является ли данная функция O-большим от указанной:

17 и 1

Необходимо найти такие константы $c \ge 0$ и $n_0 \in \mathbb{N}$, что для всех $n \ge n_0$ выполняется неравенство:

$17 \le c \cdot 1$

Это неравенство выполняется для всех $n$ при $c \ge 17$. Следовательно, $17 = O(1)$.

$n(n-1)/2$ и $n^2$

Необходимо найти такие константы $c \ge 0$ и $n_0 \in \mathbb{N}$, что для всех $n \ge n_0$ выполняется неравенство:

$\frac{n(n-1)}{2} \le c \cdot n^2$

Раскроем скобки в левой части:
$\frac{n^2 - n}{2} \le c \cdot n^2$

Это неравенство выполняется для всех $n \ge 1$ при $c \ge \frac{1}{2}$. Следовательно, $\frac{n(n-1)}{2} = O(n^2)$.

$max(n^3, 10n^2)$ и $n^3$

Необходимо найти такие константы $c \ge 0$ и $n_0 \in \mathbb{N}$, что для всех $n \ge n_0$ выполняется неравенство:

$max(n^3, 10n^2) \le c \cdot n^3$

Заметим, что при $n \ge 10$ выполняется $n^3 \ge 10n^2$, поэтому:
$max(n^3, 10n^2) = n^3$ для всех $n \ge 10$.

Тогда неравенство принимает вид:
$n^3 \le c \cdot n^3$

Оно выполняется для всех $n \ge 10$ при $c \ge 1$.
Следовательно, $max(n^3, 10n^2) = O(n^3)$.

# Задание 5

Сумма

Докажем, что если $T_1(n) = \Omega(g(n))$ и $T_2(n) = \Omega(f(n))$, то $T_1(n) + T_2(n) = \Omega(max(g(n), f(n)))$.

По определению $\Omega$-нотации:

$T_1(n) = \Omega(g(n)) \Rightarrow \exists n_0 \in \mathbb{N}, c > 0 : \forall n \ge n_0, c \cdot g(n) \le T_1(n)$

$T_2(n) = \Omega(f(n)) \Rightarrow \exists n_0' \in \mathbb{N}, c_1 > 0 : \forall n \ge n_0', c_1 \cdot f(n) \le T_2(n)$

Сложим неравенства:
$T_1(n) + T_2(n) \ge c \cdot g(n) + c_1 \cdot f(n)$

Так как $c > 0$ и $c_1 > 0$, то:
$T_1(n) + T_2(n) \ge \min(c, c_1) \cdot (g(n) + f(n))$

Очевидно, что $g(n) + f(n) \ge max(g(n), f(n))$, поэтому:
$T_1(n) + T_2(n) \ge \min(c, c_1) \cdot \max(g(n), f(n))$ для всех $n \ge \max(n_0, n_0')$.

Обозначим $c'' = \min(c, c_1)$.

Таким образом, мы показали, что существуют такие $c'' > 0$ и $n''_0 = \max(n_0, n_0')$, что для всех $n \ge n''_0$ выполняется:

$T_1(n) + T_2(n) \ge c'' \cdot \max(g(n), f(n))$

Это по определению означает, что $T_1(n) + T_2(n) = \Omega(max(g(n), f(n)))$.

Произведение

Докажем, что если $T_1(n) = \Omega(g(n))$ и $T_2(n) = \Omega(f(n))$, то $T_1(n) \cdot T_2(n) = \Omega(g(n) \cdot f(n))$.

По определению $\Omega$-нотации:
* $T_1(n) = \Omega(g(n)) \Rightarrow \exists n_0 \in \mathbb{N}, c > 0 : \forall n \ge n_0, c \cdot g(n) \le T_1(n)$
* $T_2(n) = \Omega(f(n)) \Rightarrow \exists n_0' \in \mathbb{N}, c_1 > 0 : \forall n \ge n_0', c_1 \cdot f(n) \le T_2(n)$

Перемножим неравенства:
$T_1(n) \cdot T_2(n) \ge c \cdot g(n) \cdot c_1 \cdot f(n) = (c \cdot c_1) \cdot (g(n) \cdot f(n))$ для всех $n \ge \max(n_0, n_0')$.

Обозначим $c'' = c \cdot c_1$.

Таким образом, мы показали, что существуют такие $c'' > 0$ и $n''_0 = \max(n_0, n_0')$, что для всех $n \ge n''_0$ выполняется:

$T_1(n) \cdot T_2(n) \ge c'' \cdot (g(n) \cdot f(n))$

Это по определению означает, что $T_1(n) \cdot T_2(n) = \Omega(g(n) \cdot f(n))$.
        