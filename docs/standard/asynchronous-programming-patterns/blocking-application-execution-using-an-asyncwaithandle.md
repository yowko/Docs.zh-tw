---
title: "使用 AsyncWaitHandle 封鎖應用程式執行"
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
helpviewer_keywords:
- blocks, asynchronous operations
- ending asynchronous operations
- asynchronous programming, ending operations
- asynchronous programming, blocking applications
- stopping asynchronous operations
- blocking application execution
ms.assetid: 3e32daf2-8161-4e8f-addd-9fd9ff101b03
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2660b3cbf7e8ee43a22edbfb66a4262684983b87
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a><span data-ttu-id="d8da7-102">使用 AsyncWaitHandle 封鎖應用程式執行</span><span class="sxs-lookup"><span data-stu-id="d8da7-102">Blocking Application Execution Using an AsyncWaitHandle</span></span>
<span data-ttu-id="d8da7-103">無法繼續執行其他工作在等候非同步作業的結果時的應用程式必須封鎖直到作業完成為止。</span><span class="sxs-lookup"><span data-stu-id="d8da7-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="d8da7-104">您可以使用下列選項的其中一個來等候非同步作業完成時，封鎖您的應用程式主執行緒：</span><span class="sxs-lookup"><span data-stu-id="d8da7-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="d8da7-105">使用<xref:System.IAsyncResult.AsyncWaitHandle%2A>屬性<xref:System.IAsyncResult>非同步作業所傳回**開始** *OperationName*方法。</span><span class="sxs-lookup"><span data-stu-id="d8da7-105">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin** *OperationName* method.</span></span> <span data-ttu-id="d8da7-106">本主題會示範這個方法。</span><span class="sxs-lookup"><span data-stu-id="d8da7-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="d8da7-107">呼叫非同步作業的**結束** *OperationName*方法。</span><span class="sxs-lookup"><span data-stu-id="d8da7-107">Call the asynchronous operation's **End** *OperationName* method.</span></span> <span data-ttu-id="d8da7-108">如需示範這種方法的範例，請參閱[封鎖應用程式執行，藉由結束非同步作業](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="d8da7-108">For an example that demonstrates this approach, see [Blocking Application Execution by Ending an Async Operation](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
 <span data-ttu-id="d8da7-109">使用一或多個應用程式<xref:System.Threading.WaitHandle>來封鎖，直到非同步作業已完成的物件通常會呼叫**開始** *OperationName*方法，執行任何可以完成的工作作業，然後再封鎖，直到非同步作業的結果不會完成。</span><span class="sxs-lookup"><span data-stu-id="d8da7-109">Applications that use one or more <xref:System.Threading.WaitHandle> objects to block until an asynchronous operation is complete will typically call the **Begin** *OperationName* method, perform any work that can be done without the results of the operation, and then block until the asynchronous operation(s) completes.</span></span> <span data-ttu-id="d8da7-110">應用程式可以在單一作業上封鎖透過呼叫其中一個<xref:System.Threading.WaitHandle.WaitOne%2A>方法使用<xref:System.IAsyncResult.AsyncWaitHandle%2A>。</span><span class="sxs-lookup"><span data-stu-id="d8da7-110">An application can block on a single operation by calling one of the <xref:System.Threading.WaitHandle.WaitOne%2A> methods using the <xref:System.IAsyncResult.AsyncWaitHandle%2A>.</span></span> <span data-ttu-id="d8da7-111">若要封鎖等候一組非同步作業完成時，儲存相關聯<xref:System.IAsyncResult.AsyncWaitHandle%2A>中物件的陣列，呼叫其中一個<xref:System.Threading.WaitHandle.WaitAll%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="d8da7-111">To block while waiting for a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAll%2A> methods.</span></span> <span data-ttu-id="d8da7-112">若要封鎖等候任何一個的一組非同步作業完成時，儲存相關聯<xref:System.IAsyncResult.AsyncWaitHandle%2A>中物件的陣列，呼叫其中一個<xref:System.Threading.WaitHandle.WaitAny%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="d8da7-112">To block while waiting for any one of a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAny%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8da7-113">範例</span><span class="sxs-lookup"><span data-stu-id="d8da7-113">Example</span></span>  
 <span data-ttu-id="d8da7-114">下列程式碼範例示範如何使用 DNS 類別中的非同步方法，擷取指定使用者電腦的網域名稱系統資訊。</span><span class="sxs-lookup"><span data-stu-id="d8da7-114">The following code example demonstrates using asynchronous methods in the DNS class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="d8da7-115">此範例示範封鎖使用<xref:System.Threading.WaitHandle>與非同步作業相關聯。</span><span class="sxs-lookup"><span data-stu-id="d8da7-115">The example demonstrates blocking using the <xref:System.Threading.WaitHandle> associated with the asynchronous operation.</span></span> <span data-ttu-id="d8da7-116">請注意， `null` (`Nothing`在 Visual Basic 中) 的傳遞<xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback`和`stateObject`參數因為這些並不需要使用這個方式時。</span><span class="sxs-lookup"><span data-stu-id="d8da7-116">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d8da7-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8da7-117">See Also</span></span>  
 [<span data-ttu-id="d8da7-118">事件架構非同步模式 (EAP)</span><span class="sxs-lookup"><span data-stu-id="d8da7-118">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="d8da7-119">事件架構非同步模式概觀</span><span class="sxs-lookup"><span data-stu-id="d8da7-119">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
