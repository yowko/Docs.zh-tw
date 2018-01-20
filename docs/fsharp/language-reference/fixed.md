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
# <a name="the-fixed-keyword"></a><span data-ttu-id="f5f34-104">Fixed 的關鍵字</span><span class="sxs-lookup"><span data-stu-id="f5f34-104">The Fixed Keyword</span></span>

<span data-ttu-id="f5f34-105">F # 4.1 導入了`fixed`關鍵字，可讓您可防止它們所收集或在記憶體回收期間移動到堆疊上的本機 「 釘選 」。</span><span class="sxs-lookup"><span data-stu-id="f5f34-105">F# 4.1 introduces the `fixed` keyword, which allows you to "pin" a local onto the stack to prevent it from being collected or moved during garbage-collection.</span></span>  <span data-ttu-id="f5f34-106">它用於低階程式設計案例。</span><span class="sxs-lookup"><span data-stu-id="f5f34-106">It is used for low-level programming scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="f5f34-107">語法</span><span class="sxs-lookup"><span data-stu-id="f5f34-107">Syntax</span></span>

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a><span data-ttu-id="f5f34-108">備註</span><span class="sxs-lookup"><span data-stu-id="f5f34-108">Remarks</span></span>

<span data-ttu-id="f5f34-109">這會擴充以允許擷取指標，並繫結的名稱，會導致從正在收集或在記憶體回收期間移動至運算式的語法。</span><span class="sxs-lookup"><span data-stu-id="f5f34-109">This extends the syntax of expressions to allow extracting a pointer and binding it to a name which is prevented from being collected or moved during garbage-collection.</span></span>  

<span data-ttu-id="f5f34-110">從運算式的指標透過固定`fixed`透過應用程式識別項繫結關鍵字`use`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f5f34-110">A pointer from an expression is fixed via the `fixed` keyword is bound to an identifier via the `use` keyword.</span></span>  <span data-ttu-id="f5f34-111">資源管理，透過的語意如下`use`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f5f34-111">The semantics of this are similar to resource management via the `use` keyword.</span></span>  <span data-ttu-id="f5f34-112">指標被固定在範圍內，而一旦超出範圍時，它不再被固定的。</span><span class="sxs-lookup"><span data-stu-id="f5f34-112">The pointer is fixed while it is in scope, and once it is out of scope, it is no longer fixed.</span></span>  <span data-ttu-id="f5f34-113">`fixed`不能使用的內容之外`use`繫結。</span><span class="sxs-lookup"><span data-stu-id="f5f34-113">`fixed` cannot be used outside the context of a `use` binding.</span></span>  <span data-ttu-id="f5f34-114">必須繫結指標的名稱與`use`。</span><span class="sxs-lookup"><span data-stu-id="f5f34-114">You must bind the pointer to a name with `use`.</span></span>

<span data-ttu-id="f5f34-115">使用`fixed`必須發生在函式或方法中的運算式。</span><span class="sxs-lookup"><span data-stu-id="f5f34-115">Use of `fixed` must occur within an expression in a function or a method.</span></span>  <span data-ttu-id="f5f34-116">它不能在指令碼層級或模組層級的範圍。</span><span class="sxs-lookup"><span data-stu-id="f5f34-116">It cannot be used at a script-level or module-level scope.</span></span>

<span data-ttu-id="f5f34-117">像所有指標的程式碼，這是不安全的功能，並將發出警告時使用。</span><span class="sxs-lookup"><span data-stu-id="f5f34-117">Like all pointer code, this is an unsafe feature and will emit a warning when used.</span></span>

## <a name="example"></a><span data-ttu-id="f5f34-118">範例</span><span class="sxs-lookup"><span data-stu-id="f5f34-118">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f5f34-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="f5f34-119">See Also</span></span>

[<span data-ttu-id="f5f34-120">NativePtr 模組</span><span class="sxs-lookup"><span data-stu-id="f5f34-120">NativePtr Module</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)
