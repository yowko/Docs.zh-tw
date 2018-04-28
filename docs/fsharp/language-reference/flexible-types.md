---
title: 彈性類型 (F#)
description: '了解如何使用 F # 彈性類型註釋，用於指出參數、 變數或值都有類型與指定的型別相容。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: bee2364a6c30b1fbdc09aa0aac2249e3f0c295e8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="flexible-types"></a>彈性類型

A*彈性類型註釋*表示參數、 變數或值具有相容的類型使用指定的型別，其中的相容性由類別或介面的物件導向的階層中的位置。 彈性類型適合，特別是當時不會發生自動轉換為型別階層架構中較高的類型，但您仍然想要啟用您要使用的階層架構中任何類型或實作介面的任何類型的功能。

## <a name="syntax"></a>語法

```fsharp
#type
```

## <a name="remarks"></a>備註

在先前的語法，*類型*表示基底類型或介面。

彈性類型相當於泛型類型條件約束，以限制所允許的類型與基底或介面類型相容的類型。 也就是下列兩行程式碼是相等的。

```fsharp
#SomeType

'T when 'T :> SomeType
```

彈性類型可用於數種類型的情況。 例如，當您有較高順序函式 （使用做為引數的函式的函式），通常很有用的彈性的型別傳回的函式。 在下列範例中，使用彈性的型別中有順序引數與`iterate2`啟用較高順序函式處理順序、 陣列、 清單和任何其他可列舉型別所產生的函式。

請考慮下列兩個函式，其中的序列傳回，其中另傳回彈性的型別。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

另舉一例，請考慮[Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712)程式庫函式：

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

您可以傳遞任何下列的可列舉順序的這個函式：

- 清單的清單
- 陣列的清單
- 陣列的清單
- 陣列的順序
- 任何其他組合的可列舉的序列

下列程式碼會使用`Seq.concat`示範您可以透過使用彈性類型支援的案例。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

輸出如下。

```
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

在 F # 中，如同其他物件導向語言中，有在其中衍生型別或實作介面的型別會自動轉換成基底類型或介面類型的內容。 直接引數中，則不在型別是在次級的位置，一部分的更複雜的類型，例如函式類型的傳回型別或型別引數時，就會發生這些自動轉換。 因此，彈性的型別標記法時，主要是要套用至它的類型是複雜類型的一部分。

## <a name="see-also"></a>另請參閱

[F# 語言參考](index.md)

[泛型](generics/index.md)
