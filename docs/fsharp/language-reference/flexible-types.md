---
title: 彈性類型
description: 了解如何使用F#有彈性的型別附註，表示參數、 變數或值具有與指定的型別相容的類型。
ms.date: 05/16/2016
ms.openlocfilehash: 32857cc317bc6b4b7baf53b623b551e8e0733e41
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613670"
---
# <a name="flexible-types"></a>彈性類型

A*彈性類型註解*表示參數、 變數或值具有相容類型使用指定的型別，其中的相容性由類別或介面的物件導向階層中的位置。 彈性類型很有用，特別是當時不會發生自動轉換為型別階層架構中較高的類型，但您仍想要啟用您使用階層中的任何型別或實作介面的任何類型的功能。

## <a name="syntax"></a>語法

```fsharp
#type
```

## <a name="remarks"></a>備註

在先前的語法*型別*表示基底類型或介面。

彈性類型相當於泛型型別具有條件約束，以限制允許的類型與基底或介面類型相容的類型。 也就是下列兩行程式碼是相等的。

```fsharp
#SomeType

'T when 'T :> SomeType
```

彈性類型可用於數種類型的情況。 比方說，當您有較高順序函式 （接受做為引數的函式的函式） 時，通常很有用的函式傳回具彈性的類型。 在下列範例中，使用彈性的型別中有順序引數與`iterate2`可讓要產生序列、 陣列、 清單和任何其他可列舉類型的函式所使用的較高順序函式。

請考慮下列兩個函式，其中的序列傳回，其中另傳回具彈性的類型。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

另舉一例，請考慮[Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712)程式庫函式：

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

您可以傳遞任何下列的可列舉序列，此函式：

- 一份清單
- 陣列清單
- 清單陣列
- 陣列的序列
- 可列舉序列的任何其他組合

下列程式碼會使用`Seq.concat`示範您可以使用彈性類型支援的案例。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

輸出如下。

```
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

在F#，如同其他物件導向語言中，在其中的內容衍生型別或實作介面的型別會自動轉換成基底類型或介面型別。 直接的引數中，而不是當類型是在次級的位置，做為一部分的更複雜的類型，例如函式類型，傳回型別或型別引數的時候，就會發生這些自動轉換。 因此，彈性的型別標記法時，主要是您會將它套用至型別是更複雜類型的組件。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [泛型](generics/index.md)