---
title: 例外狀況：raise 函式 (F#)
description: 了解 F# 'raise' 函式用來指示已發生錯誤或例外狀況。
ms.date: 05/16/2016
ms.openlocfilehash: 537d274659d29404380bfdd56310ac267372bb98
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "43778255"
---
# <a name="exceptions-the-raise-function"></a><span data-ttu-id="d0b07-103">例外狀況：raise 函式</span><span class="sxs-lookup"><span data-stu-id="d0b07-103">Exceptions: the raise Function</span></span>

<span data-ttu-id="d0b07-104">`raise`函式用來表示已發生錯誤或例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d0b07-104">The `raise` function is used to indicate that an error or exceptional condition has occurred.</span></span> <span data-ttu-id="d0b07-105">例外狀況物件中擷取錯誤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d0b07-105">Information about the error is captured in an exception object.</span></span>

## <a name="syntax"></a><span data-ttu-id="d0b07-106">語法</span><span class="sxs-lookup"><span data-stu-id="d0b07-106">Syntax</span></span>

```fsharp
raise (expression)
```

## <a name="remarks"></a><span data-ttu-id="d0b07-107">備註</span><span class="sxs-lookup"><span data-stu-id="d0b07-107">Remarks</span></span>

<span data-ttu-id="d0b07-108">`raise`函式會產生例外狀況物件，並起始堆疊回溯程序。</span><span class="sxs-lookup"><span data-stu-id="d0b07-108">The `raise` function generates an exception object and initiates a stack unwinding process.</span></span> <span data-ttu-id="d0b07-109">在堆疊回溯程序被受 common language runtime (CLR)，使此程序的行為都相同，因為它是以任何其他.NET 語言。</span><span class="sxs-lookup"><span data-stu-id="d0b07-109">The stack unwinding process is managed by the common language runtime (CLR), so the behavior of this process is the same as it is in any other .NET language.</span></span> <span data-ttu-id="d0b07-110">在堆疊回溯程序會搜尋符合產生的例外狀況的例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="d0b07-110">The stack unwinding process is a search for an exception handler that matches the generated exception.</span></span> <span data-ttu-id="d0b07-111">開始在目前的搜尋`try...with`運算式，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="d0b07-111">The search starts in the current `try...with` expression, if there is one.</span></span> <span data-ttu-id="d0b07-112">在每個模式`with`勾選區塊，順序。</span><span class="sxs-lookup"><span data-stu-id="d0b07-112">Each pattern in the `with` block is checked, in order.</span></span> <span data-ttu-id="d0b07-113">找到相符的例外狀況處理常式時，例外狀況會視為處理;否則，回溯堆疊時和`with`會檢查呼叫鏈結的區塊，直到找到相符的處理常式。</span><span class="sxs-lookup"><span data-stu-id="d0b07-113">When a matching exception handler is found, the exception is considered handled; otherwise, the stack is unwound and `with` blocks up the call chain are checked until a matching handler is found.</span></span> <span data-ttu-id="d0b07-114">任何`finally`於堆疊回溯呼叫鏈結中發生的區塊也會依序執行。</span><span class="sxs-lookup"><span data-stu-id="d0b07-114">Any `finally` blocks that are encountered in the call chain are also executed in sequence as the stack unwinds.</span></span>

<span data-ttu-id="d0b07-115">`raise`函式相當於`throw`C# 或 c + +。</span><span class="sxs-lookup"><span data-stu-id="d0b07-115">The `raise` function is the equivalent of `throw` in C# or C++.</span></span> <span data-ttu-id="d0b07-116">使用`reraise`catch 處理常式傳播相同的例外狀況呼叫鏈結中。</span><span class="sxs-lookup"><span data-stu-id="d0b07-116">Use `reraise` in a catch handler to propagate the same exception up the call chain.</span></span>

<span data-ttu-id="d0b07-117">下列程式碼範例說明使用`raise`函式來產生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d0b07-117">The following code examples illustrate the use of the `raise` function to generate an exception.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

<span data-ttu-id="d0b07-118">`raise`函式也可用來引發.NET 例外狀況，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d0b07-118">The `raise` function can also be used to raise .NET exceptions, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]

## <a name="see-also"></a><span data-ttu-id="d0b07-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0b07-119">See also</span></span>

- [<span data-ttu-id="d0b07-120">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="d0b07-120">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="d0b07-121">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="d0b07-121">Exception Types</span></span>](exception-types.md)
- [<span data-ttu-id="d0b07-122">例外狀況：`try...with` 運算式</span><span class="sxs-lookup"><span data-stu-id="d0b07-122">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
- [<span data-ttu-id="d0b07-123">例外狀況：`try...finally` 運算式</span><span class="sxs-lookup"><span data-stu-id="d0b07-123">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)
- [<span data-ttu-id="d0b07-124">例外狀況：`failwith` 函式</span><span class="sxs-lookup"><span data-stu-id="d0b07-124">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)
- [<span data-ttu-id="d0b07-125">例外狀況：`invalidArg` 函式</span><span class="sxs-lookup"><span data-stu-id="d0b07-125">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)
