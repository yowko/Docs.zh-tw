---
title: Fixed 關鍵字
description: "瞭解如何「釘選」到堆疊上的本機，以防止使用 F # ' fixed ' 關鍵字進行收集。"
ms.date: 08/15/2020
ms.openlocfilehash: b4b0d1ae101d5f7b65bff80fa070c9fd54de8d66
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740350"
---
# <a name="the-fixed-keyword"></a>Fixed 關鍵字

`fixed`關鍵字可讓您將本機的「釘選」至堆疊，以防止在垃圾收集期間收集或移動它。  它是用於低層級的程式設計案例。

## <a name="syntax"></a>語法

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a>備註

這會擴充運算式的語法，以允許將指標解壓縮，並將其系結至無法在垃圾收集期間收集或移動的名稱。  

運算式的指標是透過關鍵詞系結至識別碼，藉此修正 `fixed` `use` 。  這種方式的語法類似于透過關鍵詞的資源管理 `use` 。  指標在範圍內是固定的，而且一旦超出範圍，就不會再修正。  `fixed` 無法在系結的內容之外使用 `use` 。  您必須使用來系結名稱的指標 `use` 。

使用 `fixed` 必須發生在函式或方法的運算式內。  它不能用在腳本層級或模組層級的範圍。

就像所有指標程式碼一樣，這是一項不安全的功能，會在使用時發出警告。

## <a name="example"></a>範例

```fsharp
open Microsoft.FSharp.NativeInterop

type Point = { mutable X: int; mutable Y: int}

let squareWithPointer (p: nativeptr<int>) =
    // Dereference the pointer at the 0th address.
    let mutable value = NativePtr.get p 0

    // Perform some work
    value <- value * value

    // Set the value in the pointer at the 0th address.
    NativePtr.set p 0 value

let pnt = { X = 1; Y = 2 }
printfn $"pnt before - X: %d{pnt.X} Y: %d{pnt.Y}" // prints 1 and 2

// Note that the use of 'fixed' is inside a function.
// You cannot fix a pointer at a script-level or module-level scope.
let doPointerWork() =
    use ptr = fixed &pnt.Y

    // Square the Y value
    squareWithPointer ptr
    printfn $"pnt after - X: %d{pnt.X} Y: %d{pnt.Y}" // prints 1 and 4

doPointerWork()
```

## <a name="see-also"></a>另請參閱

- [NativePtr 模組](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-nativeinterop-nativeptrmodule.html)
