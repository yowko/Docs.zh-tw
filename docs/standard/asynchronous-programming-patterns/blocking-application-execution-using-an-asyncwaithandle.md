---
title: 使用 AsyncWaitHandle 封鎖應用程式執行
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 054af36987d60c8aeb752c9c711f1cce19733efc
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2018
ms.locfileid: "46705539"
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a><span data-ttu-id="a6971-102">使用 AsyncWaitHandle 封鎖應用程式執行</span><span class="sxs-lookup"><span data-stu-id="a6971-102">Blocking Application Execution Using an AsyncWaitHandle</span></span>
<span data-ttu-id="a6971-103">等待非同步作業的結果而無法繼續執行其他工作的應用程式必須封鎖，直到作業完成為止。</span><span class="sxs-lookup"><span data-stu-id="a6971-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="a6971-104">使用下列其中一個選項，在等候非同步作業完成時封鎖應用程式的主執行緒：</span><span class="sxs-lookup"><span data-stu-id="a6971-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="a6971-105">使用非同步作業的 \*Begin\*\*\*OperationName 方法所傳回 <xref:System.IAsyncResult> 的 <xref:System.IAsyncResult.AsyncWaitHandle%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="a6971-105">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's \**Begin\*\*\*OperationName* method.</span></span> <span data-ttu-id="a6971-106">本主題將示範這個方法。</span><span class="sxs-lookup"><span data-stu-id="a6971-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="a6971-107">呼叫非同步作業的 \*End\*\*\*OperationName 方法。</span><span class="sxs-lookup"><span data-stu-id="a6971-107">Call the asynchronous operation's \**End\*\*\*OperationName* method.</span></span> <span data-ttu-id="a6971-108">如需示範此方法的範例，請參閱[以結束非同步作業的方式封鎖應用程式執行](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="a6971-108">For an example that demonstrates this approach, see [Blocking Application Execution by Ending an Async Operation](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
 <span data-ttu-id="a6971-109">在非同步作業完成之前，使用一個或多個 <xref:System.Threading.WaitHandle> 物件封鎖的應用程式通常都會呼叫 \*Begin\*\*\*OperationName 方法來執行不需要作業結果即可完成的工作，然後在非同步作業完成之前維持封鎖。</span><span class="sxs-lookup"><span data-stu-id="a6971-109">Applications that use one or more <xref:System.Threading.WaitHandle> objects to block until an asynchronous operation is complete will typically call the \**Begin\*\*\*OperationName* method, perform any work that can be done without the results of the operation, and then block until the asynchronous operation(s) completes.</span></span> <span data-ttu-id="a6971-110">使用 <xref:System.IAsyncResult.AsyncWaitHandle%2A> 來呼叫其中一個 <xref:System.Threading.WaitHandle.WaitOne%2A> 方法，可在單一作業上封鎖應用程式。</span><span class="sxs-lookup"><span data-stu-id="a6971-110">An application can block on a single operation by calling one of the <xref:System.Threading.WaitHandle.WaitOne%2A> methods using the <xref:System.IAsyncResult.AsyncWaitHandle%2A>.</span></span> <span data-ttu-id="a6971-111">若要在等待一組非同步作業完成時封鎖，請將相關的 <xref:System.IAsyncResult.AsyncWaitHandle%2A> 物件儲存在陣列，並呼叫其中一個 <xref:System.Threading.WaitHandle.WaitAll%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="a6971-111">To block while waiting for a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAll%2A> methods.</span></span> <span data-ttu-id="a6971-112">若要在等待一組非同步作業的任何一個作業完成時封鎖，請將相關的 <xref:System.IAsyncResult.AsyncWaitHandle%2A> 物件儲存在陣列，並呼叫其中一個 <xref:System.Threading.WaitHandle.WaitAny%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="a6971-112">To block while waiting for any one of a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAny%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6971-113">範例</span><span class="sxs-lookup"><span data-stu-id="a6971-113">Example</span></span>  
 <span data-ttu-id="a6971-114">下列範例示範在 DNS 類別中使用非同步方法，以擷取使用者指定電腦的網域名稱系統資訊。</span><span class="sxs-lookup"><span data-stu-id="a6971-114">The following code example demonstrates using asynchronous methods in the DNS class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="a6971-115">此範例示範使用與非同步作業相關聯的 <xref:System.Threading.WaitHandle> 進行封鎖。</span><span class="sxs-lookup"><span data-stu-id="a6971-115">The example demonstrates blocking using the <xref:System.Threading.WaitHandle> associated with the asynchronous operation.</span></span> <span data-ttu-id="a6971-116">請注意，因為使用此方式時並不需要 <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` 與`stateObject` 參數，所以已為其傳遞 `null` (在 Visual Basic 中為 `Nothing`)。</span><span class="sxs-lookup"><span data-stu-id="a6971-116">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a6971-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6971-117">See also</span></span>

- [<span data-ttu-id="a6971-118">事件架構非同步模式 (EAP)</span><span class="sxs-lookup"><span data-stu-id="a6971-118">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
- [<span data-ttu-id="a6971-119">事件架構非同步模式概觀</span><span class="sxs-lookup"><span data-stu-id="a6971-119">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
