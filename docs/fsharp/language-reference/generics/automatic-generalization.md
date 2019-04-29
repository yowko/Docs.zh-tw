---
title: 自動一般化
description: 了解如何F#，讓它們能夠具有多個類型，可能的話，會自動一般化的引數和類型的函式。
ms.date: 05/16/2016
ms.openlocfilehash: 15ecf8e6f07da19bb015fd028a7465ba8b837190
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937536"
---
# <a name="automatic-generalization"></a>自動一般化

F#使用型別推斷，來評估函式和運算式的類型。 本主題描述如何F#，讓它們能夠具有多個類型時，這會自動一般化的引數和類型的函式。

## <a name="automatic-generalization"></a>自動一般化

F#編譯器，函式上執行型別推斷時決定是否指定的參數可以是泛型。 編譯器會檢查每個參數，並判斷函數是否有該參數的特定類型的相依性。 如果不存在，會推斷型別為泛型。

下列程式碼範例會說明編譯器會推斷為泛型的函式。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

型別推斷為`'a -> 'a -> 'a`。

類型表示這是函式會採用相同的未知類型的兩個引數並傳回該相同類型的值。 其中一個原因，先前的函式可以是泛型是較大者-運算子 (`>`) 本身是泛型。 較大者為非運算子的簽章`'a -> 'a -> bool`。 並非所有運算子都是泛型，和如果函式中的程式碼會使用與非泛型函式或運算子的參數類型，該參數的類型無法一般化。

因為`max`是泛型，它可以與類型搭配使用這類`int`，`float`等等，如下列範例所示。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

不過，兩個引數必須是相同的型別。 簽章`'a -> 'a -> 'a`，而非`'a -> 'b -> 'a`。 因此，下列程式碼產生錯誤，因為類型不相符。

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

`max`函式也適用於任何支援較大的類型-than 運算子。 因此，您也可以使用它來處理字串，如下列程式碼所示。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet104.fs)]

## <a name="value-restriction"></a>值限制

編譯器會執行自動一般化，只有具有明確的引數的完整的函式定義和簡單的不可變值。

這表示編譯器會發出錯誤，如果您嘗試編譯夠未限制為特定的類型，但也不是一般化的程式碼。 此問題的錯誤訊息指的是這項限制的值做為自動一般化*值限制*。

通常，當您想要為泛型的建構，但編譯器有足夠的資訊進行一般化，或當您不小心省略足夠在非泛型建構的類型資訊時，就會發生值限制的錯誤。 值限制錯誤的解決方案是以提供更完整其中一種以下列方式限制型別推斷問題，更明確的資訊：

- 將為非泛型的值或參數中加入明確的型別註解類型的限制。

- 如果問題使用 nongeneralizable 建構來定義的泛型函式，例如函式組合，或完全套用局部調用的函式引數，請嘗試重寫為一般函式定義函式。

- 如果問題是一般化，讓它執行函式，方法是新增額外的、 未使用的參數太複雜的運算式。

- 新增明確的泛型型別參數。 此選項很少使用。

- 下列程式碼範例將說明每個案例。

案例 1:運算式太複雜。 在此範例中，清單`counter`就是要`int option ref`，但它並未定義為簡單的不可變值。

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

案例 2:您可以使用 nongeneralizable 建構，定義的泛型函式。 在此範例中，建構會是 nongeneralizable，因為它牽涉到部分套用函式引數。

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

案例 3:新增額外的、 未使用的參數。 因為此運算式不是簡單的一般化，編譯器會發出值限制的錯誤。

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

案例 4:加入類型參數。

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

在最後一個案例中，值會成為類型函式，可用來建立值的許多不同的類型，例如，如下所示：

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a>另請參閱

- [類型推斷](../type-inference.md)
- [泛型](index.md)
- [以統計方式解析的類型參數](statically-resolved-type-parameters.md)
- [條件約束](constraints.md)