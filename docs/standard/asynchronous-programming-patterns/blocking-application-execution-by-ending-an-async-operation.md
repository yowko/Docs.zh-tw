---
title: 以結束非同步作業的方式封鎖應用程式執行
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- blocks, asynchronous operations
- AsyncWaitHandle property
- asynchronous programming, blocking applications
- blocking application execution
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
ms.openlocfilehash: 854528670bbddbc2dc318bf4a5ecd12368a5e8d1
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2019
ms.locfileid: "54361972"
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a><span data-ttu-id="16333-102">以結束非同步作業的方式封鎖應用程式執行</span><span class="sxs-lookup"><span data-stu-id="16333-102">Blocking Application Execution by Ending an Async Operation</span></span>
<span data-ttu-id="16333-103">等待非同步作業的結果而無法繼續執行其他工作的應用程式必須封鎖，直到作業完成為止。</span><span class="sxs-lookup"><span data-stu-id="16333-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="16333-104">使用下列其中一個選項，在等候非同步作業完成時封鎖應用程式的主執行緒：</span><span class="sxs-lookup"><span data-stu-id="16333-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="16333-105">呼叫非同步作業的 **End**_OperationName_ 方法。</span><span class="sxs-lookup"><span data-stu-id="16333-105">Call the asynchronous operations **End**_OperationName_ method.</span></span> <span data-ttu-id="16333-106">本主題將示範這個方法。</span><span class="sxs-lookup"><span data-stu-id="16333-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="16333-107">使用非同步作業 **Begin**_OperationName_ 方法所傳回 <xref:System.IAsyncResult> 的 <xref:System.IAsyncResult.AsyncWaitHandle%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="16333-107">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method.</span></span> <span data-ttu-id="16333-108">如需示範此方法的範例，請參閱[使用 AsyncWaitHandle 封鎖應用程式執行](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md)。</span><span class="sxs-lookup"><span data-stu-id="16333-108">For an example that demonstrates this approach, see [Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
 <span data-ttu-id="16333-109">在非同步作業完成之前，使用 **End**_OperationName_ 方法封鎖的應用程式通常都會呼叫 **Begin**_OperationName_ 方法來執行不需要作業結果即可完成的工作，然後呼叫 **End**_OperationName_。</span><span class="sxs-lookup"><span data-stu-id="16333-109">Applications that use the **End**_OperationName_ method to block until an asynchronous operation is complete will typically call the **Begin**_OperationName_ method, perform any work that can be done without the results of the operation, and then call **End**_OperationName_.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16333-110">範例</span><span class="sxs-lookup"><span data-stu-id="16333-110">Example</span></span>  
 <span data-ttu-id="16333-111">下列範例示範在 <xref:System.Net.Dns> 類別中使用非同步方法，以擷取使用者指定電腦的網域名稱系統資訊。</span><span class="sxs-lookup"><span data-stu-id="16333-111">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="16333-112">請注意，因為使用此方式時並不需要 <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` 與 `stateObject` 參數，所以已為這些引數傳遞 `null` (在 Visual Basic 中為 `Nothing`)。</span><span class="sxs-lookup"><span data-stu-id="16333-112">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="16333-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16333-113">See also</span></span>

- [<span data-ttu-id="16333-114">事件架構非同步模式 (EAP)</span><span class="sxs-lookup"><span data-stu-id="16333-114">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
- [<span data-ttu-id="16333-115">事件架構非同步模式概觀</span><span class="sxs-lookup"><span data-stu-id="16333-115">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
