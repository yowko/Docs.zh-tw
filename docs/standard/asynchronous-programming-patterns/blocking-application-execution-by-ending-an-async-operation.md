---
title: "以結束非同步作業的方式封鎖應用程式執行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- blocks, asynchronous operations
- AsyncWaitHandle property
- asynchronous programming, blocking applications
- blocking application execution
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
dev_langs:
- csharp
- vb
ms.openlocfilehash: ccca6e1e4f6b5cdf098018b59426fb2262e2b346
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a><span data-ttu-id="f344d-102">以結束非同步作業的方式封鎖應用程式執行</span><span class="sxs-lookup"><span data-stu-id="f344d-102">Blocking Application Execution by Ending an Async Operation</span></span>
<span data-ttu-id="f344d-103">無法繼續執行其他工作在等候非同步作業的結果時的應用程式必須封鎖直到作業完成為止。</span><span class="sxs-lookup"><span data-stu-id="f344d-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="f344d-104">您可以使用下列選項的其中一個來等候非同步作業完成時，封鎖您的應用程式主執行緒：</span><span class="sxs-lookup"><span data-stu-id="f344d-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="f344d-105">呼叫非同步作業**結束** *OperationName*方法。</span><span class="sxs-lookup"><span data-stu-id="f344d-105">Call the asynchronous operations **End** *OperationName* method.</span></span> <span data-ttu-id="f344d-106">本主題會示範這個方法。</span><span class="sxs-lookup"><span data-stu-id="f344d-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="f344d-107">使用<xref:System.IAsyncResult.AsyncWaitHandle%2A>屬性<xref:System.IAsyncResult>非同步作業所傳回**開始** *OperationName*方法。</span><span class="sxs-lookup"><span data-stu-id="f344d-107">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin** *OperationName* method.</span></span> <span data-ttu-id="f344d-108">如需示範這種方法的範例，請參閱[使用 AsyncWaitHandle 封鎖應用程式執行](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md)。</span><span class="sxs-lookup"><span data-stu-id="f344d-108">For an example that demonstrates this approach, see [Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
 <span data-ttu-id="f344d-109">使用應用程式**結束** *OperationName*通常呼叫方法來封鎖，直到非同步作業完成為止，將**開始** *OperationName*方法，執行任何工作，可以作業的結果的情況下完成，然後呼叫**結束** *OperationName*。</span><span class="sxs-lookup"><span data-stu-id="f344d-109">Applications that use the **End** *OperationName* method to block until an asynchronous operation is complete will typically call the **Begin** *OperationName* method, perform any work that can be done without the results of the operation, and then call **End** *OperationName*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f344d-110">範例</span><span class="sxs-lookup"><span data-stu-id="f344d-110">Example</span></span>  
 <span data-ttu-id="f344d-111">下列程式碼範例示範如何使用中的非同步方法<xref:System.Net.Dns>類別來擷取指定使用者電腦的網域名稱系統資訊。</span><span class="sxs-lookup"><span data-stu-id="f344d-111">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="f344d-112">請注意， `null` (`Nothing`在 Visual Basic 中) 的傳遞<xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback`和`stateObject`參數因為使用這個方式時，不需要這些引數。</span><span class="sxs-lookup"><span data-stu-id="f344d-112">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f344d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f344d-113">See Also</span></span>  
 [<span data-ttu-id="f344d-114">事件架構非同步模式 (EAP)</span><span class="sxs-lookup"><span data-stu-id="f344d-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="f344d-115">事件架構非同步模式概觀</span><span class="sxs-lookup"><span data-stu-id="f344d-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
