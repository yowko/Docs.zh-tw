---
title: "如何：使用 Catch 區塊中的特定例外狀況"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try/catch blocks
- catch blocks
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 94e5840ca4bb5f871a0ae91f53404de6a60d749d
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2017
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a><span data-ttu-id="f5f11-102">如何在 catch 區塊中使用特定的例外狀況</span><span class="sxs-lookup"><span data-stu-id="f5f11-102">How to use specific exceptions in a catch block</span></span>

<span data-ttu-id="f5f11-103">一般情況下，它是良好的程式設計作法攔截特定類型的例外狀況，而不是使用基本`catch`陳述式。</span><span class="sxs-lookup"><span data-stu-id="f5f11-103">In general, it's good programming practice to catch a specific type of exception rather than use a basic `catch` statement.</span></span>

<span data-ttu-id="f5f11-104">發生例外狀況時，該例外狀況會在堆疊中向上傳遞，讓每個 catch 區塊都有機會處理。</span><span class="sxs-lookup"><span data-stu-id="f5f11-104">When an exception occurs, it is passed up the stack and each catch block is given the opportunity to handle it.</span></span> <span data-ttu-id="f5f11-105">Catch 陳述式的順序很重要。</span><span class="sxs-lookup"><span data-stu-id="f5f11-105">The order of catch statements is important.</span></span> <span data-ttu-id="f5f11-106">請將針對特定例外狀況的 catch 區塊放在一般例外狀況的 catch 區塊之前，否則編譯器可能會發出錯誤。</span><span class="sxs-lookup"><span data-stu-id="f5f11-106">Put catch blocks targeted to specific exceptions before a general exception catch block or the compiler might issue an error.</span></span> <span data-ttu-id="f5f11-107">藉由比對 catch 區塊中指定的例外狀況類型與例外狀況名稱，即可決定正確的 catch 區塊。</span><span class="sxs-lookup"><span data-stu-id="f5f11-107">The proper catch block is determined by matching the type of the exception to the name of the exception specified in the catch block.</span></span> <span data-ttu-id="f5f11-108">如果沒有特定 catch 區塊，則會由一般 catch 區塊 (如果有的話) 攔截例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f5f11-108">If there is no specific catch block, the exception is caught by a general catch block, if one exists.</span></span>

<span data-ttu-id="f5f11-109">下列程式碼範例使用 `try`/`catch` 區塊來攔截 <xref:System.InvalidCastException>。</span><span class="sxs-lookup"><span data-stu-id="f5f11-109">The following code example uses a `try`/`catch` block to catch an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="f5f11-110">此範例會建立具有員工層級 (`Emlevel`) 之單一屬性的類別，稱為 `Employee`。</span><span class="sxs-lookup"><span data-stu-id="f5f11-110">The sample creates a class called `Employee` with a single property, employee level (`Emlevel`).</span></span> <span data-ttu-id="f5f11-111">`PromoteEmployee` 方法會採用一個物件並遞增員工層級。</span><span class="sxs-lookup"><span data-stu-id="f5f11-111">A method, `PromoteEmployee`, takes an object and increments the employee level.</span></span> <span data-ttu-id="f5f11-112"><xref:System.InvalidCastException> 會在 <xref:System.DateTime> 執行個體傳遞給 `PromoteEmployee` 方法時發生。</span><span class="sxs-lookup"><span data-stu-id="f5f11-112">An <xref:System.InvalidCastException> occurs when a <xref:System.DateTime> instance is passed to the `PromoteEmployee` method.</span></span>

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)] 

## <a name="see-also"></a><span data-ttu-id="f5f11-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5f11-113">See Also</span></span>  
[<span data-ttu-id="f5f11-114">例外狀況</span><span class="sxs-lookup"><span data-stu-id="f5f11-114">Exceptions</span></span>](index.md)
