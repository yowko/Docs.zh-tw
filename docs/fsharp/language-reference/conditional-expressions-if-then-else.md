---
title: "條件運算式：if... then...else (F#)"
description: "了解如何撰寫 F # 執行程式碼的不同分支中的條件式運算式。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 16e1871c-4d4d-4691-9ab2-bd2c6f65589a
ms.openlocfilehash: 3531a112eb53657d5e9102d5e5f3be988360b76e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="conditional-expressions-ifthenelse"></a>條件運算式：`if...then...else`

`if...then...else`運算式執行不同的分支程式碼，也會評估為不同的值，根據給定的布林運算式。


## <a name="syntax"></a>語法

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a>備註
在先前的語法， *expression1*時評估為的布林運算式執行`true`，否則*expression2*執行。

不同於其他語言，`if...then...else`建構是一個運算式，而不是陳述式。 也就是說，它會產生的值，這是在執行的分支中的最後一個運算式的值。 產生每個分支中的值的類型必須相符。 如果沒有任何明確`else`分支中，它的類型是`unit`。 因此，如果類型`then`分支不是任何類型`unit`，必須要有`else`分支與相同的傳回類型。 當鏈結`if...then...else`運算式組合在一起，您可以使用關鍵字`elif`而不是`else if`; 它們相等。

## <a name="example"></a>範例
下列範例說明如何使用`if...then...else`運算式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
John
910 is less than 20
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a>另請參閱
[F# 語言參考](index.md)

