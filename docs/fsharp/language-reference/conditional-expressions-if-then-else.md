---
title: 条件表达式：if... then...else (F#)
description: '了解如何编写在 F # 中执行代码的不同分支的条件表达式。'
ms.date: 05/16/2016
ms.openlocfilehash: 10e4224bef772f00520cf5a0fff2f2920147c2fc
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2018
ms.locfileid: "44177596"
---
# <a name="conditional-expressions-ifthenelse"></a>条件表达式： `if...then...else`

`if...then...else`表达式在运行代码的不同分支，还可以为不同的值，具体取决于给定的布尔表达式计算。

## <a name="syntax"></a>语法

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a>备注

在上述语法中， *expression1*运行时的布尔表达式的计算结果为`true`; 否则为*expression2*运行。

不同于其他语言中`if...then...else`构造是一个表达式，而不是语句。 这意味着它会生成一个值，该值是在执行的分支中的最后一个表达式的值。 每个分支中生成的值的类型必须匹配。 如果未显式`else`分支，其类型是`unit`。 因此，如果的类型`then`分支而不是任何类型`unit`，必须有`else`分支具有相同的返回类型。 当链接`if...then...else`表达式组合在一起，可以使用关键字`elif`而不是`else if`; 它们是等效。

## <a name="example"></a>示例

下面的示例演示如何使用`if...then...else`表达式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a>请参阅

- [F# 语言参考](index.md)
