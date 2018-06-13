---
title: 自動產生 (F#)
description: '了解如何 F # 自動一般化的引數和類型的函式，讓它們能夠以盡可能多個類型。'
ms.date: 05/16/2016
ms.openlocfilehash: 858c8bab4a1a37f44a700744e70ebfa8a5abf12c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565071"
---
# <a name="automatic-generalization"></a>自動一般化

F # 使用類型推斷來評估函式和運算式的類型。 本主題描述如何 F # 自動一般化的引數和類型的函式，讓它們能夠以多個類型時，這是可行的。


## <a name="automatic-generalization"></a>自動一般化
F # 編譯器，函式上執行類型推斷時判斷給定的參數是否為泛型。 編譯器會檢查每個參數，並判斷函式是否有該參數的特定類型上相依性。 如果不存在，推斷的類型是泛型。

下列程式碼範例說明的函式，編譯器會推斷為泛型。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

型別就會推斷`'a -> 'a -> 'a`。

類型表示這是函數會採用相同的類型不明的兩個引數並傳回該相同類型的值。 其中一個原因可能是先前的函式，一般是較大-運算子 (`>`) 本身為泛型。 較大者為非運算子具有的簽章`'a -> 'a -> bool`。 並非所有運算子都是泛型，並無法一般化函式中的程式碼會使用參數型別與非泛型函式或運算子，如果該參數的型別。

因為`max`是泛型，它可以與類型搭配使用這類`int`， `float`，依此類推，如下列範例所示。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

不過，兩個引數必須是相同的型別。 簽章`'a -> 'a -> 'a`，而非`'a -> 'b -> 'a`。 因此，下列程式碼產生的錯誤，因為類型不相符。

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

`max`函式也可以搭配任何支援較大的類型-高於運算子。 因此，您也可以使用它來處理字串，如下列程式碼所示。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet104.fs)]
    
## <a name="value-restriction"></a>值限制
只有完整的函式定義，具有明確的引數，與簡單不可變的值，編譯器會執行自動一般化。

這表示編譯器會發出錯誤，如果您嘗試編譯的程式碼完全不被限制為特定的類型，但是也不是一般化。 這個問題的錯誤訊息是指在自動產生的值做為這項限制*值限制*。

通常，當您想要的建構泛型，但編譯器有足夠的資訊來一般化，或當您不小心省略足夠的類型資訊的非泛型建構時，就會發生值限制的錯誤。 值限制錯誤解決方法是提供更明確的資訊，以更完整限制類型推斷問題，請以下列方式之一：


- 限制為非泛型的值或參數中加入明確的型別註解的類型。

- 如果問題使用定義的泛型函式，例如函式複合 nongeneralizable 建構，或是完全套用局部調用函式引數，請重寫為一般函式定義函式。

- 如果問題太複雜，一般化的運算式，讓它成為函式加入額外的、 未使用的參數。

- 新增明確的泛型型別參數。 很少使用這個選項。

- 下列程式碼範例將說明每個案例。

案例 1： 太複雜的運算式。 在此範例中，清單`counter`將`int option ref`，但它不定義為簡單的不變值。

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

案例 2： 使用 nongeneralizable 建構的泛型函式定義。 在此範例中，建構是 nongeneralizable，因為它涉及套用部分函式引數。

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

案例 3： 加入額外的、 未使用的參數。 因為此運算式不是簡單的一般化，編譯器會發出值限制的錯誤。

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

案例 4： 加入型別參數。

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

在最後一個案例中，這個值會成為類型函式，可用於建立值的許多不同的型別，例如，如下所示：

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a>另請參閱
[類型推斷](../type-inference.md)

[泛型](index.md)

[以統計方式解析的類型參數](statically-resolved-type-parameters.md)

[條件約束](constraints.md)

