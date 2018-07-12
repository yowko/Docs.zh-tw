---
title: 使用 AsyncCallback 委派結束非同步作業
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e67cd0fca1532aa2f52aeb7d34f604c1feb0723e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567402"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a><span data-ttu-id="a9920-102">使用 AsyncCallback 委派結束非同步作業</span><span class="sxs-lookup"><span data-stu-id="a9920-102">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>
<span data-ttu-id="a9920-103">可等待非同步作業的結果而執行其他工作的應用程式不應封鎖等待，直到作業完成為止。</span><span class="sxs-lookup"><span data-stu-id="a9920-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="a9920-104">使用下列其中一個選項，在等候非同步作業完成時繼續執行指示：</span><span class="sxs-lookup"><span data-stu-id="a9920-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="a9920-105">使用 <xref:System.AsyncCallback> 委派以處理不同執行緒中非同步作業的結果。</span><span class="sxs-lookup"><span data-stu-id="a9920-105">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="a9920-106">本主題將示範這個方法。</span><span class="sxs-lookup"><span data-stu-id="a9920-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="a9920-107">請使用非同步作業的 *Begin***OperationName 方法所傳回 <xref:System.IAsyncResult> 的 <xref:System.IAsyncResult.IsCompleted%2A> 屬性，判斷作業是否已完成。</span><span class="sxs-lookup"><span data-stu-id="a9920-107">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin***OperationName* method to determine whether the operation has completed.</span></span> <span data-ttu-id="a9920-108">如需說明這項技巧的範例，請參閱[輪詢非同步作業的狀態](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="a9920-108">For an example that demonstrates this approach, see [Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9920-109">範例</span><span class="sxs-lookup"><span data-stu-id="a9920-109">Example</span></span>  
 <span data-ttu-id="a9920-110">下列範例示範在 <xref:System.Net.Dns> 類別中使用非同步方法，以擷取使用者指定電腦的網域名稱系統 (DNS) 資訊。</span><span class="sxs-lookup"><span data-stu-id="a9920-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="a9920-111">此範例會建立參考`ProcessDnsInformation`方法的 <xref:System.AsyncCallback> 委派。</span><span class="sxs-lookup"><span data-stu-id="a9920-111">This example creates an <xref:System.AsyncCallback> delegate that references the `ProcessDnsInformation` method.</span></span> <span data-ttu-id="a9920-112">此方法會呼叫每一個非同步要求一次以取得 DNS 資訊。</span><span class="sxs-lookup"><span data-stu-id="a9920-112">This method is called once for each asynchronous request for DNS information.</span></span>  
  
 <span data-ttu-id="a9920-113">請注意，使用者指定的主機會傳遞給 <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> 參數。</span><span class="sxs-lookup"><span data-stu-id="a9920-113">Note that the user-specified host is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> parameter.</span></span> <span data-ttu-id="a9920-114">如需示範定義和使用更複雜狀態物件的範例，請參閱[使用 AsyncCallback 委派和狀態物件](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)。</span><span class="sxs-lookup"><span data-stu-id="a9920-114">For an example that demonstrates defining and using a more complex state object, see [Using an AsyncCallback Delegate and State Object](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).</span></span>  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="a9920-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="a9920-115">See Also</span></span>  
 [<span data-ttu-id="a9920-116">事件架構非同步模式 (EAP)</span><span class="sxs-lookup"><span data-stu-id="a9920-116">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="a9920-117">事件架構非同步模式概觀</span><span class="sxs-lookup"><span data-stu-id="a9920-117">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [<span data-ttu-id="a9920-118">使用 IAsyncResult 呼叫非同步方法</span><span class="sxs-lookup"><span data-stu-id="a9920-118">Calling Asynchronous Methods Using IAsyncResult</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)  
 [<span data-ttu-id="a9920-119">使用 AsyncCallback 委派和狀態物件</span><span class="sxs-lookup"><span data-stu-id="a9920-119">Using an AsyncCallback Delegate and State Object</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
