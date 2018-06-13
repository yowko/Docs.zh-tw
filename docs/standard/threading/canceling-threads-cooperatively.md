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
ms.openlocfilehash: 3edd0f9c991df8d8d70b14f4439c5c477e8f1401
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581338"
---
# <a name="canceling-threads-cooperatively"></a><span data-ttu-id="18813-102">以合作方式取消執行緒</span><span class="sxs-lookup"><span data-stu-id="18813-102">Canceling Threads Cooperatively</span></span>
<span data-ttu-id="18813-103">在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]之前，.NET Framework 不會提供內建，以便在執行緒啟動後以合作方式加以取消。</span><span class="sxs-lookup"><span data-stu-id="18813-103">Prior to the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the .NET Framework provided no built-in way to cancel a thread cooperatively after it was started.</span></span> <span data-ttu-id="18813-104">不過，在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 中，您可以使用取消語彙基元來取消執行緒，就如同您可以使用它們來取消 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 物件或 PLINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="18813-104">However, in [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use cancellation tokens to cancel threads, just as you can use them to cancel <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or PLINQ queries.</span></span> <span data-ttu-id="18813-105">雖然 <xref:System.Threading.Thread?displayProperty=nameWithType> 類別不提供取消語彙基元的內建支援，您仍可透過使用採取 <xref:System.Threading.ParameterizedThreadStart> 委派的 <xref:System.Threading.Thread> 建構函式，將語彙基元傳遞至執行緒程序。</span><span class="sxs-lookup"><span data-stu-id="18813-105">Although the <xref:System.Threading.Thread?displayProperty=nameWithType> class does not offer built-in support for cancellation tokens, you can pass a token to a thread procedure by using the <xref:System.Threading.Thread> constructor that takes a <xref:System.Threading.ParameterizedThreadStart> delegate.</span></span> <span data-ttu-id="18813-106">下列範例示範如何進行這項操作。</span><span class="sxs-lookup"><span data-stu-id="18813-106">The following example demonstrates how to do this.</span></span>  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="18813-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="18813-107">See Also</span></span>  
 [<span data-ttu-id="18813-108">使用執行緒和執行緒處理</span><span class="sxs-lookup"><span data-stu-id="18813-108">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
