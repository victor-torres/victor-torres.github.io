---
layout: post
title:  "Trocando elementos de uma lista com Python"
date: 2020-02-05 22:55:54 -0300
categories: python
comments: true
---
A dica de hoje é bem simples. Eu já sabia dela há algum tempo, mas acho que vale a pena compartilhar aqui. 

Você já deve saber que pra trocar o valor de duas variáveis com Python, não precisa usar uma terceira variável temporária como no exemplo a seguir:

```python
# Valores iniciais
a = 20
b = 30

# Fazendo a troca
temp = a
a = b
b = temp

# Valores finais
assert a == 30
assert b == 20
```

Basta fazer o seguinte:

```python
# Valores iniciais
a = 20
b = 30

# Fazendo a troca
a, b = b, a

# Valores finais
assert a == 30
assert b == 20
```

Curiosamente, o mesmo funciona com listas!

Então se eu tenho a seguinte lista:

```python
# Valores iniciais
lista = [1, 2, 3, 4, 5]
```

Se eu quiser trocar o primeiro com o segundo elemento, posso fazer simplesmente:

```python
# Fazendo a troca
lista[0], lista[1] = lista[1], lista[0]

# Valores finais
assert lista == [2, 1, 3, 4, 5]
```

Legal, né? Eu programo em Python há um tempão, mas esse tipo de coisa ainda me desperta alegria.
