---
title: 彈性類型
description: 瞭解如何使用F#彈性類型注釋, 這表示參數、變數或值的類型與指定的類型相容。
ms.date: 05/16/2016
ms.openlocfilehash: 43caa6cd35630df648beda5cc43cffae2ecd6f6a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630257"
---
# <a name="flexible-types"></a>彈性類型

*彈性類型注釋*表示參數、變數或值的類型與指定的類型相容, 其中的相容性取決於類別或介面的物件導向階層架構中的位置。 當類型階層中較高的類型自動轉換不會發生, 但您仍想要讓您的功能可以使用階層中的任何類型, 或任何可執行介面的類型時, 彈性類型特別有用。

## <a name="syntax"></a>語法

```fsharp
#type
```

## <a name="remarks"></a>備註

在先前的語法中,*類型*代表基底類型或介面。

彈性型別相當於具有條件約束的泛型型別, 它會將允許的類型限制為與基底或介面類別型相容的類型。 也就是說, 下列兩行程式碼是相等的。

```fsharp
#SomeType

'T when 'T :> SomeType
```

彈性類型適用于數種類型的情況。 例如, 當您有更高順序函式 (接受函式做為引數的函數) 時, 讓函式傳回彈性類型通常會很有用。 在下列範例中, 在中`iterate2`使用具有順序引數的彈性類型, 可讓高階函數與產生序列、陣列、清單和任何其他可列舉類型的函式搭配運作。

請考慮下列兩個函數, 其中一個會傳回序列, 另一個則會傳回彈性類型。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

另舉一個例子, 請考慮[Seq](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712)程式庫函式:

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

您可以將下列任何可列舉序列傳遞給此函式:

- 清單清單
- 陣列清單
- 清單的陣列
- 序列的陣列
- 可列舉序列的任何其他組合

下列程式碼會`Seq.concat`使用來示範您可以使用彈性類型來支援的案例。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

輸出如下。

```
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

在F#中, 如同其他物件導向語言, 會將實介面的衍生型別或型別自動轉換成基底類型或介面型別。 這些自動轉換會在直接引數中進行, 但不會在類型位於從屬位置時, 做為更複雜類型的一部分 (例如函式類型的傳回類型), 或做為類型引數。 因此, 彈性類型標記法主要適用于您要套用它的類型是更複雜類型的一部分。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [泛型](./generics/index.md)
