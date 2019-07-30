---
title: 例外狀況：raise 函式
description: 瞭解「引發F# 」函數如何用來表示發生錯誤或例外狀況。
ms.date: 05/16/2016
ms.openlocfilehash: e0cc8da8310203c537b8081af8a225671bd8c6a3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630283"
---
# <a name="exceptions-the-raise-function"></a><span data-ttu-id="92b36-103">例外狀況：raise 函式</span><span class="sxs-lookup"><span data-stu-id="92b36-103">Exceptions: the raise Function</span></span>

<span data-ttu-id="92b36-104">`raise`函數是用來表示發生錯誤或例外狀況。</span><span class="sxs-lookup"><span data-stu-id="92b36-104">The `raise` function is used to indicate that an error or exceptional condition has occurred.</span></span> <span data-ttu-id="92b36-105">錯誤的相關資訊會在例外狀況物件中捕捉。</span><span class="sxs-lookup"><span data-stu-id="92b36-105">Information about the error is captured in an exception object.</span></span>

## <a name="syntax"></a><span data-ttu-id="92b36-106">語法</span><span class="sxs-lookup"><span data-stu-id="92b36-106">Syntax</span></span>

```fsharp
raise (expression)
```

## <a name="remarks"></a><span data-ttu-id="92b36-107">備註</span><span class="sxs-lookup"><span data-stu-id="92b36-107">Remarks</span></span>

<span data-ttu-id="92b36-108">`raise`函式會產生例外狀況物件, 並起始堆疊回溯進程。</span><span class="sxs-lookup"><span data-stu-id="92b36-108">The `raise` function generates an exception object and initiates a stack unwinding process.</span></span> <span data-ttu-id="92b36-109">堆疊回溯程式是由 common language runtime (CLR) 所管理, 因此此進程的行為與任何其他 .NET 語言相同。</span><span class="sxs-lookup"><span data-stu-id="92b36-109">The stack unwinding process is managed by the common language runtime (CLR), so the behavior of this process is the same as it is in any other .NET language.</span></span> <span data-ttu-id="92b36-110">堆疊回溯程式是搜尋符合所產生之例外狀況的例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="92b36-110">The stack unwinding process is a search for an exception handler that matches the generated exception.</span></span> <span data-ttu-id="92b36-111">搜尋會從目前`try...with`的運算式開始 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="92b36-111">The search starts in the current `try...with` expression, if there is one.</span></span> <span data-ttu-id="92b36-112">區塊中的`with`每個模式會依序進行檢查。</span><span class="sxs-lookup"><span data-stu-id="92b36-112">Each pattern in the `with` block is checked, in order.</span></span> <span data-ttu-id="92b36-113">找到相符的例外狀況處理常式時, 會將例外狀況視為已處理;否則, 會先展開堆疊並`with`封鎖呼叫鏈, 直到找到相符的處理常式為止。</span><span class="sxs-lookup"><span data-stu-id="92b36-113">When a matching exception handler is found, the exception is considered handled; otherwise, the stack is unwound and `with` blocks up the call chain are checked until a matching handler is found.</span></span> <span data-ttu-id="92b36-114">當`finally`堆疊回溯時, 在呼叫鏈中遇到的任何區塊也會依序執行。</span><span class="sxs-lookup"><span data-stu-id="92b36-114">Any `finally` blocks that are encountered in the call chain are also executed in sequence as the stack unwinds.</span></span>

<span data-ttu-id="92b36-115">函數等同于或C++中的C# `throw` `raise`</span><span class="sxs-lookup"><span data-stu-id="92b36-115">The `raise` function is the equivalent of `throw` in C# or C++.</span></span> <span data-ttu-id="92b36-116">在`reraise` catch 處理常式中使用, 將相同的例外狀況向上傳播至呼叫鏈。</span><span class="sxs-lookup"><span data-stu-id="92b36-116">Use `reraise` in a catch handler to propagate the same exception up the call chain.</span></span>

<span data-ttu-id="92b36-117">下列程式碼範例說明如何使用`raise`函數來產生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="92b36-117">The following code examples illustrate the use of the `raise` function to generate an exception.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

<span data-ttu-id="92b36-118">`raise`函數也可以用來引發 .net 例外狀況, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="92b36-118">The `raise` function can also be used to raise .NET exceptions, as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]

## <a name="see-also"></a><span data-ttu-id="92b36-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92b36-119">See also</span></span>

- [<span data-ttu-id="92b36-120">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="92b36-120">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="92b36-121">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="92b36-121">Exception Types</span></span>](exception-types.md)
- [<span data-ttu-id="92b36-122">例外狀況：`try...with`運算式</span><span class="sxs-lookup"><span data-stu-id="92b36-122">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
- [<span data-ttu-id="92b36-123">例外狀況：`try...finally`運算式</span><span class="sxs-lookup"><span data-stu-id="92b36-123">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)
- [<span data-ttu-id="92b36-124">例外狀況：`failwith`函式</span><span class="sxs-lookup"><span data-stu-id="92b36-124">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)
- [<span data-ttu-id="92b36-125">例外狀況：`invalidArg`函式</span><span class="sxs-lookup"><span data-stu-id="92b36-125">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)
