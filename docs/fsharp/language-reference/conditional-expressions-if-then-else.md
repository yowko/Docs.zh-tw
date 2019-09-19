---
title: 條件運算式： if .。。然後 .。。東西
description: 瞭解如何在中F#撰寫條件運算式，以執行程式碼的不同分支。
ms.date: 05/16/2016
ms.openlocfilehash: d9763f37cd9170c42e968282b54a3ce925e92591
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083025"
---
# <a name="conditional-expressions-ifthenelse"></a>條件運算式：`if...then...else`

`if...then...else`運算式會執行不同的程式碼分支，也會根據指定的布林運算式，評估為不同的值。

## <a name="syntax"></a>語法

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a>備註

在先前的語法中，*運算式*會在布林運算式評估為`true`時執行，否則會執行*運算式*2。

不同于其他語言， `if...then...else`結構是運算式，而不是語句。 這表示它會產生值，這是執行之分支中最後一個運算式的值。 每個分支中產生的數值型別必須相符。 如果沒有明確`else`分支，其類型為`unit`。 因此，如果`then`分支的型別是`unit`以外的任何型別`else` ，則必須有一個具有相同傳回型別的分支。 將運算式`if...then...else`連結在一起時，您可以使用`elif`關鍵字， `else if`而不是，它們是相等的。

## <a name="example"></a>範例

下列範例說明如何使用`if...then...else`運算式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```console
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
