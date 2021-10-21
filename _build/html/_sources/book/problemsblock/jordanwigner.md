---
jupytext:
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

(quantchembasic)=

# Преобразование Жордана-Вигнера

## Описание лекции


## Введение

## Спины, фермионы и бозоны

## Переход от спинов к фермионам

Мы можем попробовать сопоставить спину фермион сказав что спин вниз значит что фермион есть, а спин вверх -- что его нет.
Другими словами, используя оператор количества частиц $\hat{n}_i = c^\dagger_i c_i$, где $c^\dagger_i$ и $c_i$ это операторы
создания и разрушения (creation and annihilation) соответсвенно, мы хотели бы сопоставить
$$\hat{\sigma}_i^z = 1 - 2\hat{n}_i$$

Тогда лестничные (ladder) операторы $\sigma^- = (\hat{\sigma}_i^x-i\hat{\sigma}_i^y)/2$ и 
$\sigma^+= (\hat{\sigma}_i^x+i\hat{\sigma}_i^y)/2$ соответствуют операторам создания и разрушения. 
Действительно, на одной вершине эти операторы выполняют фермионное антикоммутационное отношение
$$ \{ \sigma^+_j, \sigma^-_j} = 1. $$

К сожалению, на разных вершинах эти операторы коммутируют, а не антикоммутируют. Чтобы это исправить, мы "прикрепляем"
к каждому фермиону "нить" (string):
$$\sigma^+_i = \left[ \prod_{j< i} (1-2c^\dagger_j c_j) \right] c_i$$
$$\sigma^-_i = \left[ \prod_{j< i} (1-2c^\dagger_j c_j) \right] c^\dagger_i$$

Oператор $\prod_{j_i} (1-2c^\dagger_j c_j)$ равен $\pm 1$ в зависимости от четности количества фермионов слева от вершины $i$.

Заметим, что  $c_k$ антикоммутирует с  $(1-2c^\dagger_k c_k)$:
$$ \{ c_j, (1-2c^\dagger_j c_j)} = c_j (1-2c^\dagger_j c_j) +  c_j (1-2c^\dagger_j c_j)c_j  =
c_j  -2c_jc^\dagger_j c_j +  c_j -2c^\dagger_j c_jc_j = c_j  -2c_j+  c_j  = 0,$$
и, следовательно с нитью $\prod_{j_i} (1-2c^\dagger_j c_j) $ (интуивно, если сначала разрушить фермион, то четность изменится).

Пусть, без ограничения общности, $\ell>k$:
$$\sigma^+_k \sigma^-_\ell = \left[ \prod_{j<k} (1-2c^\dagger_j c_j) \right] c_k \left[ \prod_{m< \ell} (1-2c^\dagger_m c_m) \right] c^\dagger_\ell $$
Если мы перенесем $c_k$ вправо, то выражение умножится на -1 дважды (один раз из-за изменения четности $\ell$-нити, 
и один раз из-за обмена с $c^\dagger_\ell$) $i$-нить коммутирует со всем, поэтому ее мы можем перенести вправо без изменений:
$$\sigma^+_k \sigma^-_\ell 
= \left[ \prod_{j<k} (1-2c^\dagger_j c_j) \right] c_k \left[ \prod_{m< \ell} (1-2c^\dagger_m c_m) \right] c^\dagger_\ell
=  \left[ \prod_{m< \ell} (1-2c^\dagger_m c_m) \right] c^\dagger_\ell \left[ \prod_{j<k} (1-2c^\dagger_j c_j) \right] c_k =
= \sigma^-_\ell  \sigma^+_k, $$
как и требовалось. Мы так же можем записать обратное отношение:
$$c_i = \left[ \prod_{j< i} \sigma^z_j \right] \sigma^+_i$$
$$c^\dagger_i = \left[ \prod_{j< i} \sigma^z_j \right] \sigma^+_j.$$
Проверка антикоммутаторов оставляется читателю в качестве упражнения.

Таким образом мы установили соответсвие между фермионной и спиновой системами, но операторы в обоих случаях очень нелокальны.