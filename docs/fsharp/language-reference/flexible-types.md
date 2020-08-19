---
title: 彈性類型
description: '瞭解如何使用 F # 彈性類型注釋，這表示參數、變數或值的類型與指定的類型相容。'
ms.date: 08/15/2020
ms.openlocfilehash: 44241ad082cd7f3de9e0cc6a48b8a8946e7b33d3
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557746"
---
# <a name="flexible-types"></a>彈性類型

*彈性類型注釋*指出參數、變數或值的類型與指定的類型相容，其中的相容性是由類別或介面的物件導向階層中的位置所決定。 彈性型別特別適用于自動轉換類型階層中較高的類型時，但您仍然想要讓您的功能使用階層中的任何類型，或任何實介面的型別。

## <a name="syntax"></a>語法

```fsharp
#type
```

## <a name="remarks"></a>備註

在先前的語法中， *type* 代表基底類型或介面。

彈性型別相當於具有條件約束的泛型型別，其條件約束會將允許的類型限制為與基底或介面類別型相容的類型。 也就是說，下列兩行程式碼是相等的。

```fsharp
#SomeType

'T when 'T :> SomeType
```

彈性類型適用于數種類型的情況。 例如，當您有較高階的函式 (使用函式做為引數) 的函式時，讓函式傳回彈性型別通常會很有用。 在下列範例中，在中使用具有 sequence 引數的彈性型別，可 `iterate2` 讓更高的 order 函數使用可產生序列、陣列、清單和任何其他可列舉型別的函數。

請考慮下列兩個函式，其中一個會傳回序列，另一個則會傳回彈性型別。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

另舉一個範例，請考慮採用 [Seq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#concat) 程式庫函數：

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

您可以將下列任何可列舉的序列傳遞給此函式：

- 清單清單
- 陣列清單
- 清單的陣列
- 序列的陣列
- 可列舉序列的任何其他組合

下列 `Seq.concat` 程式碼會使用來示範您可以使用彈性類型來支援的案例。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

輸出如下。

```console
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

在 F # 中，如同其他物件導向的語言，有一些內容會將實介面的衍生類型或型別自動轉換成基底類型或介面型別。 這些自動轉換會在直接引數中進行，但不會在型別位於從屬位置、成為更複雜型別的一部分（例如函式類型的傳回型別），或做為型別引數。 因此，當您要套用它的型別是更複雜型別的一部分時，彈性型別標記法主要很有用。

## <a name="see-also"></a>另請參閱

- [F # 語言參考](index.md)
- [泛型](./generics/index.md)
