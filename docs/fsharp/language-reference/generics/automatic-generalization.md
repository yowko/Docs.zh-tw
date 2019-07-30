---
title: 自動一般化
description: 瞭解如何F#自動一般化引數和類型的函式, 以便在可能的情況下使用多個類型。
ms.date: 05/16/2016
ms.openlocfilehash: 501749a190d9770cbcd9848e3d528cba32fe6762
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630633"
---
# <a name="automatic-generalization"></a>自動一般化

F#使用型別推斷來評估函數和運算式的類型。 本主題描述如何F#自動一般化引數和類型的函式, 以便在可能的情況下使用多個類型。

## <a name="automatic-generalization"></a>自動一般化

當F#編譯器在函式上執行型別推斷時, 會判斷指定的參數是否可以是泛型。 編譯器會檢查每個參數, 並判斷函數是否相依于該參數的特定類型。 如果不是, 則會將型別推斷為泛型。

下列程式碼範例說明編譯器推斷為泛型的函式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

類型推斷為`'a -> 'a -> 'a`。

類型指出這是一個函式, 該函式接受相同未知類型的兩個引數, 並傳回該相同類型的值。 先前的函式可以是泛型的其中一個原因是, 大於運算子 (`>`) 本身就是泛型。 大於運算子具有`'a -> 'a -> bool`簽章。 並非所有運算子都是泛型的, 而且如果函式中的程式碼使用參數類型搭配非泛型函數或運算子, 則該參數類型無法一般化。

因為`max`是泛型, 所以可以搭配`int`、 `float`等類型使用, 如下列範例所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

不過, 這兩個引數必須屬於相同的類型。 簽章為`'a -> 'a -> 'a`, 而`'a -> 'b -> 'a`非。 因此, 下列程式碼會產生錯誤, 因為類型不相符。

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

`max`函數也適用于任何支援大於運算子的類型。 因此, 您也可以在字串上使用它, 如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet104.fs)]

## <a name="value-restriction"></a>值限制

編譯器只會在具有明確引數的完整函式定義和簡單的不可變值上執行自動一般化。

這表示編譯器會在您嘗試編譯的程式碼未充分限制為特定類型, 但也無法歸納時發出錯誤。 此問題的錯誤訊息指的是對值進行自動一般化的限制, 做為*值限制*。

一般而言, 當您想要將結構設為泛型, 但編譯器沒有足夠的資訊來將它一般化, 或當您不小心在非泛型結構中省略足夠的類型資訊時, 就會發生值限制錯誤。 「值限制」錯誤的解決方案, 是以下列其中一種方式提供更明確的資訊, 以更完整地限制型別推斷問題:

- 將明確的類型注釋新增至值或參數, 以將類型限制為非泛型。

- 如果問題是使用 nongeneralizable 結構來定義泛型函式, 例如函式組合或未完全套用的擴充函式引數, 請嘗試重寫函數做為一般函式定義。

- 如果問題是太複雜而無法一般化的運算式, 請新增額外的未使用參數, 使其進入函式。

- 加入明確的泛型型別參數。 此選項很少使用。

- 下列程式碼範例將說明每個案例。

案例 1:運算式太複雜。 在此範例中, 清單`counter`的目的`int option ref`是, 但未定義為簡單的不可變值。

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

案例 2:使用 nongeneralizable 結構來定義泛型函數。 在此範例中, 結構是 nongeneralizable 的, 因為它牽涉到部分應用函式引數。

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

案例 3:加入額外、未使用的參數。 因為此運算式不夠簡單, 無法進行一般化, 所以編譯器會發出值限制錯誤。

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

案例 4:加入型別參數。

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

在最後一個案例中, 值會變成類型函式, 可用來建立許多不同類型的值, 例如, 如下所示:

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a>另請參閱

- [類型推斷](../type-inference.md)
- [泛型](index.md)
- [以統計方式解析的類型參數](statically-resolved-type-parameters.md)
- [條件約束](constraints.md)
