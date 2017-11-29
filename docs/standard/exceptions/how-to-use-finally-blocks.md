---
title: "如何：使用 Finally 區塊"
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
- exceptions, finally blocks
- try/catch blocks
- finally blocks
- ArgumentOutOfRangeException class
ms.assetid: 4b9c0137-04af-4468-91d1-b9014df8ddd2
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b303582a62f211091b1ebee0e88cf380da8b03d9
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2017
---
# <a name="how-to-use-finally-blocks"></a><span data-ttu-id="2b208-102">如何使用 finally 區塊</span><span class="sxs-lookup"><span data-stu-id="2b208-102">How to use finally blocks</span></span>

<span data-ttu-id="2b208-103">發生例外狀況時，執行會停止，並將控制權交給適當的例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="2b208-103">When an exception occurs, execution stops and control is given to the appropriate exception handler.</span></span> <span data-ttu-id="2b208-104">這通常表示會略過您預期要執行的程式碼行。</span><span class="sxs-lookup"><span data-stu-id="2b208-104">This often means that lines of code you expect to be executed are bypassed.</span></span> <span data-ttu-id="2b208-105">某些資源清除作業 (例如關閉檔案) 即使擲回例外狀況也必須執行。</span><span class="sxs-lookup"><span data-stu-id="2b208-105">Some resource cleanup, such as closing a file, needs to be done even if an exception is thrown.</span></span> <span data-ttu-id="2b208-106">若要這樣做，您可以使用 `finally` 區塊。</span><span class="sxs-lookup"><span data-stu-id="2b208-106">To do this, you can use a `finally` block.</span></span> <span data-ttu-id="2b208-107">`finally` 區塊永遠會執行，而不論是否擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2b208-107">A `finally` block always executes, regardless of whether an exception is thrown.</span></span>

<span data-ttu-id="2b208-108">下列程式碼範例使用 `try`/`catch` 區塊來攔截 <xref:System.ArgumentOutOfRangeException>。</span><span class="sxs-lookup"><span data-stu-id="2b208-108">The following code example uses a `try`/`catch` block to catch an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="2b208-109">`Main` 方法會建立兩個陣列，並嘗試將其中一個陣列複製到另一個陣列。</span><span class="sxs-lookup"><span data-stu-id="2b208-109">The `Main` method creates two arrays and attempts to copy one to the other.</span></span> <span data-ttu-id="2b208-110">此動作會產生 <xref:System.ArgumentOutOfRangeException>，並會將錯誤寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="2b208-110">The action generates an <xref:System.ArgumentOutOfRangeException> and the error is written to the console.</span></span> <span data-ttu-id="2b208-111">不論複製動作的結果為何，`finally` 區塊都會執行。</span><span class="sxs-lookup"><span data-stu-id="2b208-111">The `finally` block executes regardless of the outcome of the copy action.</span></span>

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="2b208-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b208-112">See Also</span></span>  
[<span data-ttu-id="2b208-113">例外狀況</span><span class="sxs-lookup"><span data-stu-id="2b208-113">Exceptions</span></span>](index.md)   
