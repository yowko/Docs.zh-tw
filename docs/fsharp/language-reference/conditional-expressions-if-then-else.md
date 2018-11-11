---
title: 條件運算式：if... then...else (F#)
description: 了解如何撰寫 F# 來執行的程式碼的不同分支中的條件運算式。
ms.date: 05/16/2016
ms.openlocfilehash: 10e4224bef772f00520cf5a0fff2f2920147c2fc
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "44177597"
---
# <a name="conditional-expressions-ifthenelse"></a>條件運算式： `if...then...else`

`if...then...else`運算式執行的程式碼的不同分支，也會評估為不同的值，根據指定的布林運算式。

## <a name="syntax"></a>語法

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a>備註

在先前的語法*expression1*時，則為 True 的運算式評估為執行`true`; 否則*expression2*執行。

不同於其他語言，`if...then...else`建構是運算式，不是陳述式。 也就是說，它會產生一個值，也就是執行的分支中的最後一個運算式的值。 產生每個分支中的值的類型必須相符。 如果沒有任何明確`else`分支，其型別是`unit`。 因此，如果的型別`then`分支是任何型別以外`unit`，必須要有`else`分支並具有相同的傳回類型。 當鏈結`if...then...else`運算式在一起，您可以使用關鍵字`elif`而不是`else if`; 它們相等。

## <a name="example"></a>範例

下列範例說明如何使用`if...then...else`運算式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
