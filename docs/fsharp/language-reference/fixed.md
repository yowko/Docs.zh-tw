---
title: "Fixed 的關鍵字 （F #）"
description: "了解如何您可以 [pin] 若要避免使用 F # 集合至堆疊本機 'fixed' 關鍵字。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 5795ce1f-11bf-4798-9f1f-6e44ffa1477e
ms.openlocfilehash: 1605603bc35941e21c798600140036fb678869b5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="the-fixed-keyword"></a>Fixed 的關鍵字

F # 4.1 導入了`fixed`關鍵字，可讓您可防止它們所收集或在記憶體回收期間移動到堆疊上的本機 「 釘選 」。  它用於低階程式設計案例。

## <a name="syntax"></a>語法

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a>備註

這會擴充以允許擷取指標，並繫結的名稱，會導致從正在收集或在記憶體回收期間移動至運算式的語法。  

從運算式的指標透過固定`fixed`透過應用程式識別項繫結關鍵字`use`關鍵字。  資源管理，透過的語意如下`use`關鍵字。  指標被固定在範圍內，而一旦超出範圍時，它不再被固定的。  `fixed`不能使用的內容之外`use`繫結。  必須繫結指標的名稱與`use`。

使用`fixed`必須發生在函式或方法中的運算式。  它不能在指令碼層級或模組層級的範圍。

像所有指標的程式碼，這是不安全的功能，並將發出警告時使用。

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

## <a name="see-also"></a>請參閱

[NativePtr 模組](https://msdn.microsoft.com/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)
