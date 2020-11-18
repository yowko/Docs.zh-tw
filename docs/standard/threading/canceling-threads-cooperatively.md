---
title: 以合作方式取消執行緒
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threads, cancellation
ms.assetid: d2d6d5fd-e263-4fa0-847b-2fc3e0d82337
ms.openlocfilehash: 9e9224e9dc9ac57defe75e916dd6b9844bba7f12
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826608"
---
# <a name="canceling-threads-cooperatively"></a><span data-ttu-id="fca1c-102">以合作方式取消執行緒</span><span class="sxs-lookup"><span data-stu-id="fca1c-102">Canceling threads cooperatively</span></span>

<span data-ttu-id="fca1c-103">在 .NET Framework 4 之前，.NET 未提供任何內建的方法，可在啟動後以合作方式取消執行緒。</span><span class="sxs-lookup"><span data-stu-id="fca1c-103">Prior to .NET Framework 4, .NET provided no built-in way to cancel a thread cooperatively after it was started.</span></span> <span data-ttu-id="fca1c-104">不過，從 .NET Framework 4 開始，您可以使用 <xref:System.Threading.CancellationToken?displayProperty=nameWithType> 來取消執行緒，就像您可以使用它們來取消 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 物件或 PLINQ 查詢一樣。</span><span class="sxs-lookup"><span data-stu-id="fca1c-104">However, starting with .NET Framework 4, you can use a <xref:System.Threading.CancellationToken?displayProperty=nameWithType> to cancel threads, just as you can use them to cancel <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or PLINQ queries.</span></span> <span data-ttu-id="fca1c-105">雖然 <xref:System.Threading.Thread?displayProperty=nameWithType> 類別不提供取消語彙基元的內建支援，您仍可透過使用採取 <xref:System.Threading.Thread> 委派的 <xref:System.Threading.ParameterizedThreadStart> 建構函式，將語彙基元傳遞至執行緒程序。</span><span class="sxs-lookup"><span data-stu-id="fca1c-105">Although the <xref:System.Threading.Thread?displayProperty=nameWithType> class does not offer built-in support for cancellation tokens, you can pass a token to a thread procedure by using the <xref:System.Threading.Thread> constructor that takes a <xref:System.Threading.ParameterizedThreadStart> delegate.</span></span> <span data-ttu-id="fca1c-106">下列範例示範如何進行這項操作。</span><span class="sxs-lookup"><span data-stu-id="fca1c-106">The following example demonstrates how to do this.</span></span>  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="fca1c-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="fca1c-107">See also</span></span>

- [<span data-ttu-id="fca1c-108">使用執行緒和執行緒</span><span class="sxs-lookup"><span data-stu-id="fca1c-108">Using Threads and Threading</span></span>](using-threads-and-threading.md)
