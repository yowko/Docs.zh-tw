---
title: Fixed 的關鍵字 （F#）
description: 了解如何在您可以 [pin] 若要避免使用 F# 集合至堆疊本機 'fixed' 關鍵字。
ms.date: 04/24/2017
ms.openlocfilehash: 1bf1b2ad67d2dd7f854e569cfca7c06e8aec7f4c
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "45624505"
---
# <a name="the-fixed-keyword"></a>Fixed 的關鍵字

F# 4.1 導入了`fixed`關鍵字，可讓您 「 釘選 」 到堆疊上的本機可防止它們所收集或在記憶體回收期間移動。  它用於低層級的程式設計案例。

## <a name="syntax"></a>語法

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a>備註

這會擴充語法的運算式，以允許擷取指標和繫結至從所收集或在記憶體回收期間移動使得的名稱。  

從運算式的指標透過固定`fixed`關鍵字會繫結至透過識別碼`use`關鍵字。  資源管理，透過這樣的語意如下`use`關鍵字。  固定在範圍內，而一旦超出範圍時，它不再被固定的指標。  `fixed` 不能使用的內容之外`use`繫結。  您必須將指標繫結至名稱與`use`。

使用`fixed`必須發生在函式或方法中的運算式。  它不能在指令碼層級或模組層級的範圍。

類似所有指標的程式碼，這是不安全的功能，而且會發出警告時使用。

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
printfn "pnt before - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 2

// Note that the use of 'fixed' is inside a function.
// You cannot fix a pointer at a script-level or module-level scope.
let doPointerWork() =
    use ptr = fixed &pnt.Y

    // Square the Y value
    squareWithPointer ptr
    printfn "pnt after - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 4

doPointerWork()
```

## <a name="see-also"></a>另請參閱

- [NativePtr 模組](https://msdn.microsoft.com/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)
