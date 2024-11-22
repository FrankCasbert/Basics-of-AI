
# Chapter 2 -- introduction to prolog.

Prolog 基本语法
## 1. 事实（Facts）
事实是简单的陈述句，表示某个关系为真。

``` prolog
father(john, bob).  % John 是 Bob 的父亲
mother(mary, bob).  % Mary 是 Bob 的母亲
```
## 2. 规则（Rules）
规则用于定义更复杂的关系，通常包含子目标（子句）。

``` prolog
grandparent(X, Z) :- parent(X, Y), parent(Y, Z).
```
在这个例子中，grandparent(X, Z) 表示 X 是 Z 的祖父母，如果 X 是 Y 的父母且 Y 是 Z 的父母。

## 3. 查询（Queries）
查询用于询问 Prolog 数据库中的信息。
``` prolog
?- father(john, bob).  % 查询 John 是否是 Bob 的父亲
?- grandparent(john, bob).  % 查询 John 是否是 Bob 的祖父母
```
## 4. 变量（Variables）
变量以大写字母开头，用于表示未知的值。
``` prolog
?- father(john, X).  % 查询 John 的孩子是谁
?- parent(X, bob).  % 查询 Bob 的父母是谁
```
## 5. 常量（Constants）
常量可以是原子（atom）、数字或字符串。
``` prolog
parent(john, bob).  % 原子
age(bob, 30).  % 数字
name(bob, "Bob Smith").  % 字符串
```
## 6. 列表（Lists）
列表是用方括号 [ ] 表示的，可以包含元素或子列表。
``` prolog
list([1, 2, 3]).  % 列表 [1, 2, 3]
empty_list([]).  % 空列表 []

% 列表操作
member(X, [X | _]).  % X 是列表的第一个元素
member(X, [_ | T]) :- member(X, T).  % X 在列表的剩余部分中
```
## 7. 连接符（Conjunctions and Disjunctions）
使用 `,`表示逻辑与（and），使用`;` 表示逻辑或（or）。
``` prolog
both_true :- A, B.  % A 和 B 都为真
one_true :- A ; B.  % A 或 B 至少一个为真
```
## 8. 否定（Negation）
使用 `\+` 表示逻辑非（not）。
``` prolog
not_parent(X, Y) :- \+ parent(X, Y).
```
## 9. 递归（Recursion）
递归是 Prolog 中常用的技术，用于处理列表和其他数据结构。
``` Prolog
% 计算列表的长度
length([], 0).
length([_|T], N) :- length(T, M), N is M + 1.

% 逆序列表
reverse([], []).
reverse([H|T], Rev) :- reverse(T, RevT), append(RevT, [H], Rev).
```
## 10. 动态数据库（Dynamic Database）
可以动态地添加和删除事实和规则。
``` Prolog
% 添加事实
assert(parent(john, bob)).

% 删除事实
retract(parent(john, bob)).
```
## 11. 输入输出（Input/Output）
Prolog 提供了一些基本的输入输出函数。
``` prolog
% 输出
write('Hello, World!').

% 输入
read(X).
```
## 12. 控制结构（Control Structures）
Prolog 提供了一些控制结构，如 if-then-else。
``` prolog
% if-then-else
(Condition -> ThenPart ; ElsePart)
```

Reference:

https://ruanyifeng.com/blog/2019/01/prolog.html

https://www.youtube.com/watch?v=SykxWpFwMGs

https://www.swi-prolog.org/pldoc/man?section=quickstart
