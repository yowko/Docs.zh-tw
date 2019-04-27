---
title: 索引屬性
description: 深入了解索引的屬性，在F#，可讓已排序的資料類似陣列存取。
ms.date: 10/17/2018
ms.openlocfilehash: bc330641c451973ddefa0a34fe6e757a808f6cb7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903821"
---
# <a name="indexed-properties"></a>索引屬性

在定義類別，用來對已排序的資料擷取時，有時候很有幫助，而不會公開基礎實作中提供索引的存取該資料。 做法是使用`Index`成員。

## <a name="syntax"></a>語法

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.Index
    with get(index-values) =
        get-member-body
    and set index-values values-to-set =
        set-member-body

// Indexed property with get only
member self-identifier.Index
    with get(index-values) =
        get-member-body

// Indexed property that has set only.
member self-identifier.Index
    with set index-values values-to-set =
        set-member-body
```

## <a name="remarks"></a>備註

先前的語法中的表單會顯示如何定義索引的屬性都有`get`和`set`方法中，有`get`方法，或有`set`僅方法。 您也可以結合這兩僅 get 和集合，顯示的語法所示的語法，並產生具有 get 和 set 的屬性。 此第二個表單可讓您將不同的存取範圍修飾詞和屬性放在 get 和 set 方法。

使用名稱`Item`，編譯器會將屬性視為預設索引屬性。 A*預設索引屬性*是屬性，您可以存取的物件執行個體上使用類似陣列的語法。 例如，如果`o`會定義此屬性，語法類型的物件`o.[index]`用來存取屬性。

存取非預設的索引的屬性的語法是要提供屬性的索引，就像一般成員一樣括號括住的名稱。 例如，如果上的屬性`o`稱為`Ordinal`，您撰寫`o.Ordinal(index)`存取它。

不論您使用哪一個表單，您應該一律使用局部調用的形式的索引屬性上的 set 方法。 如需局部調用的函式的詳細資訊，請參閱[函式](../functions/index.md)。

## <a name="example"></a>範例

下列程式碼範例說明如何定義和使用預設值和非預設索引的屬性，有 get 和 set 方法。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a>Output

```console
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-values"></a>具有多個索引值的索引的屬性

索引的屬性可以有一個以上的索引值。 在此情況下，值會以逗號分隔的屬性使用時。 在這類屬性的 set 方法必須有兩個局部調用的引數，其中第一個是包含索引鍵，元組和第二個是要設定的值。

下列程式碼示範如何使用具有多個索引值的索引屬性。

```fsharp
open System.Collections.Generic

/// Basic implementation of a sparse matrix based on a dictionary
type SparseMatrix() =
    let table = new Dictionary<(int * int), float>()
    member __.Item
        // Because the key is comprised of two values, 'get' has two index values
        with get(key1, key2) = table.[(key1, key2)]

        // 'set' has two index values and a new value to place in the key's position
        and set (key1, key2) value = table.[(key1, key2)] <- value

let sm = new SparseMatrix()
for i in 1..1000 do
    sm.[i, i] <- float i * float i
```

## <a name="see-also"></a>另請參閱

- [成員](index.md)
