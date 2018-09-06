---
title: 'Fixed 的關鍵字 （F #）'
description: "了解如何在您可以 [pin] 若要避免使用 F # 集合至堆疊本機 'fixed' 關鍵字。"
ms.date: 04/24/2017
ms.openlocfilehash: 1bf1b2ad67d2dd7f854e569cfca7c06e8aec7f4c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "44039277"
---
# <a name="the-fixed-keyword"></a><span data-ttu-id="72799-103">Fixed 的關鍵字</span><span class="sxs-lookup"><span data-stu-id="72799-103">The Fixed Keyword</span></span>

<span data-ttu-id="72799-104">F # 4.1 導入了`fixed`關鍵字，可讓您 「 釘選 」 到堆疊上的本機可防止它們所收集或在記憶體回收期間移動。</span><span class="sxs-lookup"><span data-stu-id="72799-104">F# 4.1 introduces the `fixed` keyword, which allows you to "pin" a local onto the stack to prevent it from being collected or moved during garbage-collection.</span></span>  <span data-ttu-id="72799-105">它用於低層級的程式設計案例。</span><span class="sxs-lookup"><span data-stu-id="72799-105">It is used for low-level programming scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="72799-106">語法</span><span class="sxs-lookup"><span data-stu-id="72799-106">Syntax</span></span>

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a><span data-ttu-id="72799-107">備註</span><span class="sxs-lookup"><span data-stu-id="72799-107">Remarks</span></span>

<span data-ttu-id="72799-108">這會擴充語法的運算式，以允許擷取指標和繫結至從所收集或在記憶體回收期間移動使得的名稱。</span><span class="sxs-lookup"><span data-stu-id="72799-108">This extends the syntax of expressions to allow extracting a pointer and binding it to a name which is prevented from being collected or moved during garbage-collection.</span></span>  

<span data-ttu-id="72799-109">從運算式的指標透過固定`fixed`關鍵字會繫結至透過識別碼`use`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="72799-109">A pointer from an expression is fixed via the `fixed` keyword is bound to an identifier via the `use` keyword.</span></span>  <span data-ttu-id="72799-110">資源管理，透過這樣的語意如下`use`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="72799-110">The semantics of this are similar to resource management via the `use` keyword.</span></span>  <span data-ttu-id="72799-111">固定在範圍內，而一旦超出範圍時，它不再被固定的指標。</span><span class="sxs-lookup"><span data-stu-id="72799-111">The pointer is fixed while it is in scope, and once it is out of scope, it is no longer fixed.</span></span>  <span data-ttu-id="72799-112">`fixed` 不能使用的內容之外`use`繫結。</span><span class="sxs-lookup"><span data-stu-id="72799-112">`fixed` cannot be used outside the context of a `use` binding.</span></span>  <span data-ttu-id="72799-113">您必須將指標繫結至名稱與`use`。</span><span class="sxs-lookup"><span data-stu-id="72799-113">You must bind the pointer to a name with `use`.</span></span>

<span data-ttu-id="72799-114">使用`fixed`必須發生在函式或方法中的運算式。</span><span class="sxs-lookup"><span data-stu-id="72799-114">Use of `fixed` must occur within an expression in a function or a method.</span></span>  <span data-ttu-id="72799-115">它不能在指令碼層級或模組層級的範圍。</span><span class="sxs-lookup"><span data-stu-id="72799-115">It cannot be used at a script-level or module-level scope.</span></span>

<span data-ttu-id="72799-116">類似所有指標的程式碼，這是不安全的功能，而且會發出警告時使用。</span><span class="sxs-lookup"><span data-stu-id="72799-116">Like all pointer code, this is an unsafe feature and will emit a warning when used.</span></span>

## <a name="example"></a><span data-ttu-id="72799-117">範例</span><span class="sxs-lookup"><span data-stu-id="72799-117">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="72799-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72799-118">See also</span></span>

- [<span data-ttu-id="72799-119">NativePtr 模組</span><span class="sxs-lookup"><span data-stu-id="72799-119">NativePtr Module</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)
