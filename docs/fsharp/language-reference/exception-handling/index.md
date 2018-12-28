---
title: 例外狀況處理
description: 了解例外狀況處理中的基本概念F#並尋找例外狀況處理運算式和函式的連結。
ms.date: 05/16/2016
ms.openlocfilehash: 187236ca380c7de0b3714160f6c3703f8fb93d5a
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614437"
---
# <a name="exception-handling"></a><span data-ttu-id="b3876-103">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="b3876-103">Exception Handling</span></span>

<span data-ttu-id="b3876-104">本節包含 F# 語言例外狀況處理支援的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b3876-104">This section contains information about exception handling support in the F# language.</span></span>

## <a name="exception-handling-basics"></a><span data-ttu-id="b3876-105">例外狀況處理基本概念</span><span class="sxs-lookup"><span data-stu-id="b3876-105">Exception Handling Basics</span></span>
<span data-ttu-id="b3876-106">例外狀況處理是 .NET Framework 中處理錯誤狀況的標準方式。</span><span class="sxs-lookup"><span data-stu-id="b3876-106">Exception handling is the standard way of handling error conditions in the .NET Framework.</span></span> <span data-ttu-id="b3876-107">因此，任何 .NET 語言都必須支援此機制，包括 F#。</span><span class="sxs-lookup"><span data-stu-id="b3876-107">Thus, any .NET language must support this mechanism, including F#.</span></span> <span data-ttu-id="b3876-108">「例外狀況」是封裝錯誤之相關資訊的物件。</span><span class="sxs-lookup"><span data-stu-id="b3876-108">An *exception* is an object that encapsulates information about an error.</span></span> <span data-ttu-id="b3876-109">發生錯誤時，即會引發例外狀況並停止一般執行。</span><span class="sxs-lookup"><span data-stu-id="b3876-109">When errors occur, exceptions are raised and regular execution stops.</span></span> <span data-ttu-id="b3876-110">而執行階段會針對例外狀況搜尋適合的處理常式。</span><span class="sxs-lookup"><span data-stu-id="b3876-110">Instead, the runtime searches for an appropriate handler for the exception.</span></span> <span data-ttu-id="b3876-111">搜尋會在目前的函式中開始執行，繼續向上搜尋堆疊，遍及呼叫端層級，直到找到相符的處理常式為止。</span><span class="sxs-lookup"><span data-stu-id="b3876-111">The search starts in the current function, and proceeds up the stack through the layers of callers until a matching handler is found.</span></span> <span data-ttu-id="b3876-112">接著，就會執行這個處理常式。</span><span class="sxs-lookup"><span data-stu-id="b3876-112">Then the handler is executed.</span></span>

<span data-ttu-id="b3876-113">此外，當堆疊回溯時，執行階段會執行 `finally` 區塊中的所有程式碼，確保在回溯程序期間正確清除物件。</span><span class="sxs-lookup"><span data-stu-id="b3876-113">In addition, as the stack is unwound, the runtime executes any code in `finally` blocks, to guarantee that objects are cleaned up correctly during the unwinding process.</span></span>

## <a name="related-topics"></a><span data-ttu-id="b3876-114">相關主題</span><span class="sxs-lookup"><span data-stu-id="b3876-114">Related Topics</span></span>

|<span data-ttu-id="b3876-115">標題</span><span class="sxs-lookup"><span data-stu-id="b3876-115">Title</span></span>|<span data-ttu-id="b3876-116">描述</span><span class="sxs-lookup"><span data-stu-id="b3876-116">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="b3876-117">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="b3876-117">Exception Types</span></span>](exception-types.md)|<span data-ttu-id="b3876-118">描述如何宣告例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="b3876-118">Describes how to declare an exception type.</span></span>|
|[<span data-ttu-id="b3876-119">例外狀況：`try...with`運算式</span><span class="sxs-lookup"><span data-stu-id="b3876-119">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)|<span data-ttu-id="b3876-120">描述支援例外狀況處理的語言建構。</span><span class="sxs-lookup"><span data-stu-id="b3876-120">Describes the language construct that supports exception handling.</span></span>|
|[<span data-ttu-id="b3876-121">例外狀況：`try...finally`運算式</span><span class="sxs-lookup"><span data-stu-id="b3876-121">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)|<span data-ttu-id="b3876-122">描述當例外狀況擲回時，可讓您於堆疊回溯時執行清除程式碼的語言建構。</span><span class="sxs-lookup"><span data-stu-id="b3876-122">Describes the language construct that enables you to execute clean-up code as the stack unwinds when an exception is thrown.</span></span>|
|[<span data-ttu-id="b3876-123">例外狀況：`raise` 函式</span><span class="sxs-lookup"><span data-stu-id="b3876-123">Exceptions: the `raise` Function</span></span>](the-raise-Function.md)|<span data-ttu-id="b3876-124">描述如何擲回例外狀況物件。</span><span class="sxs-lookup"><span data-stu-id="b3876-124">Describes how to throw an exception object.</span></span>|
|[<span data-ttu-id="b3876-125">例外狀況：`failwith`函式</span><span class="sxs-lookup"><span data-stu-id="b3876-125">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)|<span data-ttu-id="b3876-126">描述如何產生一般 F# 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b3876-126">Describes how to generate a general F# exception.</span></span>|
|[<span data-ttu-id="b3876-127">例外狀況：`invalidArg`函式</span><span class="sxs-lookup"><span data-stu-id="b3876-127">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)|<span data-ttu-id="b3876-128">描述如何產生無效引數例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b3876-128">Describes how to generate an invalid argument exception.</span></span>|