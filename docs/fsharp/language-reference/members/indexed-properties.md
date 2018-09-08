---
title: 索引屬性 (F#)
description: '深入了解 F # 編製索引的屬性，可提供已排序資料的類似陣列存取屬性。'
ms.date: 05/16/2016
ms.openlocfilehash: e56e4e2ea3f35df4c8ec46012357242cb6ce69f3
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44179269"
---
# <a name="indexed-properties"></a>索引屬性

*索引屬性*提供類似陣列的存取權的屬性排序資料。 它們有三種形式：

* `Item`
* `Ordinal`
* `Cardinal`

F # 成員必須命名為其中一個提供與陣列存取這三個名稱。 `IndexerName` 用來代表任何下列三個選項：

## <a name="syntax"></a>語法

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.IndexerName
    with get(index-variable) =
        get-function-body
    and set index-variablesvalue-variables =
        set-function-body

// Indexed property that has get only.
member self-identifier.IndexerName(index-variable) =
    get-function-body

// Alternative syntax for indexed property with get only
member self-identifier.IndexerName
    with get(index-variables) =
        get-function-body

// Indexed property that has set only.
member self-identifier.IndexerName
    with set index-variablesvalue-variables = 
        set-function-body
```

## <a name="remarks"></a>備註

先前的語法中的表單會顯示如何定義索引的屬性都有`get`和`set`方法中，有`get`方法，或有`set`僅方法。 您也可以結合這兩僅 get 和集合，顯示的語法所示的語法，並產生具有 get 和 set 的屬性。 此第二個表單可讓您將不同的存取範圍修飾詞和屬性放在 get 和 set 方法。

當*IndexerName*是`Item`，編譯器會將屬性視為預設索引屬性。 A*預設索引屬性*是屬性，您可以存取的物件執行個體上使用類似陣列的語法。 例如，如果`obj`會定義此屬性，語法類型的物件`obj.[index]`用來存取屬性。

提供屬性的名稱和括號中的索引為存取編製索引的非預設屬性的語法。 例如，如果屬性是`Ordinal`，您撰寫`obj.Ordinal(index)`存取它。

不論您使用哪一個表單，您應該一律使用的局部調用的形式`set`索引屬性上的方法。 如需局部調用的函式的詳細資訊，請參閱[函式](../functions/index.md)。

## <a name="example"></a>範例

下列程式碼範例說明如何定義和使用預設值和非預設索引的屬性，有 get 和 set 方法。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a>輸出

```
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-variables"></a>具有多個索引變數的索引的屬性

索引的屬性可以有一個以上的索引變數。 在此情況下，變數會以逗號分隔的屬性使用時。 在這類屬性的 set 方法必須有兩個局部調用的引數，其中第一個 tuple，其中包含索引鍵，而第二個所設定的值。

下列程式碼示範如何使用多個索引變數的索引屬性。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]

## <a name="see-also"></a>另請參閱

- [成員](index.md)
