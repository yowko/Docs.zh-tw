---
title: 以合作方式取消執行緒
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threads, cancellation
ms.assetid: d2d6d5fd-e263-4fa0-847b-2fc3e0d82337
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd32deb9c8719a12b76aaea8ec91a17471cf18f9
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44259856"
---
# <a name="canceling-threads-cooperatively"></a><span data-ttu-id="8a44a-102">以合作方式取消執行緒</span><span class="sxs-lookup"><span data-stu-id="8a44a-102">Canceling threads cooperatively</span></span>

<span data-ttu-id="8a44a-103">在 .NET Framework 4 之前，.NET Framework 不會提供內建，以便在執行緒啟動後以合作方式加以取消。</span><span class="sxs-lookup"><span data-stu-id="8a44a-103">Prior to the .NET Framework 4, the .NET Framework provided no built-in way to cancel a thread cooperatively after it was started.</span></span> <span data-ttu-id="8a44a-104">不過，從 .NET Framework 4 開始，您可以使用 <xref:System.Threading.CancellationToken?displayProperty=nameWithType> 來取消執行緒，就如同您可以用以取消 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 物件或 PLINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="8a44a-104">However, starting with the .NET Framework 4, you can use a <xref:System.Threading.CancellationToken?displayProperty=nameWithType> to cancel threads, just as you can use them to cancel <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or PLINQ queries.</span></span> <span data-ttu-id="8a44a-105">雖然 <xref:System.Threading.Thread?displayProperty=nameWithType> 類別不提供取消語彙基元的內建支援，您仍可透過使用採取 <xref:System.Threading.Thread> 委派的 <xref:System.Threading.ParameterizedThreadStart> 建構函式，將語彙基元傳遞至執行緒程序。</span><span class="sxs-lookup"><span data-stu-id="8a44a-105">Although the <xref:System.Threading.Thread?displayProperty=nameWithType> class does not offer built-in support for cancellation tokens, you can pass a token to a thread procedure by using the <xref:System.Threading.Thread> constructor that takes a <xref:System.Threading.ParameterizedThreadStart> delegate.</span></span> <span data-ttu-id="8a44a-106">下列範例示範如何進行這項操作。</span><span class="sxs-lookup"><span data-stu-id="8a44a-106">The following example demonstrates how to do this.</span></span>  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="8a44a-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a44a-107">See also</span></span>

- [<span data-ttu-id="8a44a-108">使用執行緒和執行緒處理</span><span class="sxs-lookup"><span data-stu-id="8a44a-108">Using Threads and Threading</span></span>](using-threads-and-threading.md)
