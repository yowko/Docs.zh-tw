---
title: "例外狀況：raise 函式 (F#)"
description: "了解如何使用 F # 'raise' 函式來指示已發生錯誤或例外狀況。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b00da469-4789-4cdd-9f77-7a2e29f28637
ms.openlocfilehash: dc524a06d075b982a6aa1fd266769bfc7d883517
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-the-raise-function"></a><span data-ttu-id="7172a-104">例外狀況：raise 函式</span><span class="sxs-lookup"><span data-stu-id="7172a-104">Exceptions: the raise Function</span></span>

<span data-ttu-id="7172a-105">`raise`函數用來指示已發生錯誤或例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7172a-105">The `raise` function is used to indicate that an error or exceptional condition has occurred.</span></span> <span data-ttu-id="7172a-106">例外狀況物件中擷取錯誤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7172a-106">Information about the error is captured in an exception object.</span></span>


## <a name="syntax"></a><span data-ttu-id="7172a-107">語法</span><span class="sxs-lookup"><span data-stu-id="7172a-107">Syntax</span></span>

```fsharp
raise (expression)
```

## <a name="remarks"></a><span data-ttu-id="7172a-108">備註</span><span class="sxs-lookup"><span data-stu-id="7172a-108">Remarks</span></span>
<span data-ttu-id="7172a-109">`raise`函式會產生例外狀況物件，並起始堆疊回溯處理序。</span><span class="sxs-lookup"><span data-stu-id="7172a-109">The `raise` function generates an exception object and initiates a stack unwinding process.</span></span> <span data-ttu-id="7172a-110">堆疊回溯處理程序是由 common language runtime (CLR)，管理，使此程序的行為都相同，因為它是任何其他.NET 語言。</span><span class="sxs-lookup"><span data-stu-id="7172a-110">The stack unwinding process is managed by the common language runtime (CLR), so the behavior of this process is the same as it is in any other .NET language.</span></span> <span data-ttu-id="7172a-111">堆疊回溯處理序會搜尋符合產生的例外狀況的例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="7172a-111">The stack unwinding process is a search for an exception handler that matches the generated exception.</span></span> <span data-ttu-id="7172a-112">搜尋會開始在目前`try...with`運算式，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="7172a-112">The search starts in the current `try...with` expression, if there is one.</span></span> <span data-ttu-id="7172a-113">在每個模式`with`勾選區塊，順序。</span><span class="sxs-lookup"><span data-stu-id="7172a-113">Each pattern in the `with` block is checked, in order.</span></span> <span data-ttu-id="7172a-114">找到相符的例外狀況處理常式時，例外狀況會被視為處理;否則，回溯堆疊時，`with`呼叫鏈結的區塊會檢查，直到找到相符的處理常式。</span><span class="sxs-lookup"><span data-stu-id="7172a-114">When a matching exception handler is found, the exception is considered handled; otherwise, the stack is unwound and `with` blocks up the call chain are checked until a matching handler is found.</span></span> <span data-ttu-id="7172a-115">任何`finally`一樣堆疊回溯時，發生在呼叫鏈結中的區塊也執行序列中。</span><span class="sxs-lookup"><span data-stu-id="7172a-115">Any `finally` blocks that are encountered in the call chain are also executed in sequence as the stack unwinds.</span></span>

<span data-ttu-id="7172a-116">`raise`函式相當於`throw`C# 或 c + +。</span><span class="sxs-lookup"><span data-stu-id="7172a-116">The `raise` function is the equivalent of `throw` in C# or C++.</span></span> <span data-ttu-id="7172a-117">使用`reraise`中傳送相同的例外狀況呼叫鏈結的 catch 處理常式。</span><span class="sxs-lookup"><span data-stu-id="7172a-117">Use `reraise` in a catch handler to propagate the same exception up the call chain.</span></span>

<span data-ttu-id="7172a-118">下列程式碼範例說明使用`raise`產生例外狀況的函式。</span><span class="sxs-lookup"><span data-stu-id="7172a-118">The following code examples illustrate the use of the `raise` function to generate an exception.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

<span data-ttu-id="7172a-119">`raise`函式也可用來引發.NET 例外狀況，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="7172a-119">The `raise` function can also be used to raise .NET exceptions, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]
    
## <a name="see-also"></a><span data-ttu-id="7172a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7172a-120">See Also</span></span>
[<span data-ttu-id="7172a-121">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="7172a-121">Exception Handling</span></span>](index.md)

[<span data-ttu-id="7172a-122">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="7172a-122">Exception Types</span></span>](exception-types.md)

[<span data-ttu-id="7172a-123">例外狀況：`try...with` 運算式</span><span class="sxs-lookup"><span data-stu-id="7172a-123">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)

[<span data-ttu-id="7172a-124">例外狀況：`try...finally` 運算式</span><span class="sxs-lookup"><span data-stu-id="7172a-124">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)

[<span data-ttu-id="7172a-125">例外狀況：`failwith` 函式</span><span class="sxs-lookup"><span data-stu-id="7172a-125">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)

[<span data-ttu-id="7172a-126">例外狀況：`invalidArg` 函式</span><span class="sxs-lookup"><span data-stu-id="7172a-126">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)
