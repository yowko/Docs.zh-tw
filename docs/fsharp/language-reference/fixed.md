---
title: Fixed 關鍵字
description: "瞭解如何「釘選」到堆疊上的本機，以防止使用 F # ' fixed ' 關鍵字進行收集。"
ms.date: 08/15/2020
ms.openlocfilehash: 786ffd706c243fc83f8fb3afc2201d2a34536372
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559176"
---
# <a name="the-fixed-keyword"></a><span data-ttu-id="9825e-103">Fixed 關鍵字</span><span class="sxs-lookup"><span data-stu-id="9825e-103">The fixed keyword</span></span>

<span data-ttu-id="9825e-104">`fixed`關鍵字可讓您將本機的「釘選」至堆疊，以防止在垃圾收集期間收集或移動它。</span><span class="sxs-lookup"><span data-stu-id="9825e-104">The `fixed` keyword allows you to "pin" a local onto the stack to prevent it from being collected or moved during garbage-collection.</span></span>  <span data-ttu-id="9825e-105">它是用於低層級的程式設計案例。</span><span class="sxs-lookup"><span data-stu-id="9825e-105">It is used for low-level programming scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="9825e-106">語法</span><span class="sxs-lookup"><span data-stu-id="9825e-106">Syntax</span></span>

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a><span data-ttu-id="9825e-107">備註</span><span class="sxs-lookup"><span data-stu-id="9825e-107">Remarks</span></span>

<span data-ttu-id="9825e-108">這會擴充運算式的語法，以允許將指標解壓縮，並將其系結至無法在垃圾收集期間收集或移動的名稱。</span><span class="sxs-lookup"><span data-stu-id="9825e-108">This extends the syntax of expressions to allow extracting a pointer and binding it to a name which is prevented from being collected or moved during garbage-collection.</span></span>  

<span data-ttu-id="9825e-109">運算式的指標是透過關鍵詞系結至識別碼，藉此修正 `fixed` `use` 。</span><span class="sxs-lookup"><span data-stu-id="9825e-109">A pointer from an expression is fixed via the `fixed` keyword is bound to an identifier via the `use` keyword.</span></span>  <span data-ttu-id="9825e-110">這種方式的語法類似于透過關鍵詞的資源管理 `use` 。</span><span class="sxs-lookup"><span data-stu-id="9825e-110">The semantics of this are similar to resource management via the `use` keyword.</span></span>  <span data-ttu-id="9825e-111">指標在範圍內是固定的，而且一旦超出範圍，就不會再修正。</span><span class="sxs-lookup"><span data-stu-id="9825e-111">The pointer is fixed while it is in scope, and once it is out of scope, it is no longer fixed.</span></span>  <span data-ttu-id="9825e-112">`fixed` 無法在系結的內容之外使用 `use` 。</span><span class="sxs-lookup"><span data-stu-id="9825e-112">`fixed` cannot be used outside the context of a `use` binding.</span></span>  <span data-ttu-id="9825e-113">您必須使用來系結名稱的指標 `use` 。</span><span class="sxs-lookup"><span data-stu-id="9825e-113">You must bind the pointer to a name with `use`.</span></span>

<span data-ttu-id="9825e-114">使用 `fixed` 必須發生在函式或方法的運算式內。</span><span class="sxs-lookup"><span data-stu-id="9825e-114">Use of `fixed` must occur within an expression in a function or a method.</span></span>  <span data-ttu-id="9825e-115">它不能用在腳本層級或模組層級的範圍。</span><span class="sxs-lookup"><span data-stu-id="9825e-115">It cannot be used at a script-level or module-level scope.</span></span>

<span data-ttu-id="9825e-116">就像所有指標程式碼一樣，這是一項不安全的功能，會在使用時發出警告。</span><span class="sxs-lookup"><span data-stu-id="9825e-116">Like all pointer code, this is an unsafe feature and will emit a warning when used.</span></span>

## <a name="example"></a><span data-ttu-id="9825e-117">範例</span><span class="sxs-lookup"><span data-stu-id="9825e-117">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9825e-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9825e-118">See also</span></span>

- [<span data-ttu-id="9825e-119">NativePtr 模組</span><span class="sxs-lookup"><span data-stu-id="9825e-119">NativePtr Module</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-nativeinterop-nativeptrmodule.html)
