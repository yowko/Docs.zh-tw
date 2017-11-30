---
title: "使用 AsyncCallback 委派結束非同步作業"
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
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bbe170588776daa97fec4c736d4b1bdd871de518
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a><span data-ttu-id="3108f-102">使用 AsyncCallback 委派結束非同步作業</span><span class="sxs-lookup"><span data-stu-id="3108f-102">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>
<span data-ttu-id="3108f-103">應用程式可以執行其他工作在等候非同步作業的結果時，不應該封鎖，等待，直到作業完成。</span><span class="sxs-lookup"><span data-stu-id="3108f-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="3108f-104">使用下列選項的其中一個來繼續等候非同步作業完成時執行的指示：</span><span class="sxs-lookup"><span data-stu-id="3108f-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
-   <span data-ttu-id="3108f-105">使用<xref:System.AsyncCallback>委派以處理不同的執行緒中的非同步作業的結果。</span><span class="sxs-lookup"><span data-stu-id="3108f-105">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="3108f-106">本主題會示範這個方法。</span><span class="sxs-lookup"><span data-stu-id="3108f-106">This approach is demonstrated in this topic.</span></span>  
  
-   <span data-ttu-id="3108f-107">使用<xref:System.IAsyncResult.IsCompleted%2A>屬性<xref:System.IAsyncResult>非同步作業所傳回**開始** *OperationName*方法來判斷作業是否完成。</span><span class="sxs-lookup"><span data-stu-id="3108f-107">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin** *OperationName* method to determine whether the operation has completed.</span></span> <span data-ttu-id="3108f-108">如需示範這種方法的範例，請參閱[輪詢非同步作業的狀態](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="3108f-108">For an example that demonstrates this approach, see [Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3108f-109">範例</span><span class="sxs-lookup"><span data-stu-id="3108f-109">Example</span></span>  
 <span data-ttu-id="3108f-110">下列程式碼範例示範如何使用中的非同步方法<xref:System.Net.Dns>類別來擷取指定使用者電腦的網域名稱系統 (DNS) 資訊。</span><span class="sxs-lookup"><span data-stu-id="3108f-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="3108f-111">這個範例會建立<xref:System.AsyncCallback>委派，參考`ProcessDnsInformation`方法。</span><span class="sxs-lookup"><span data-stu-id="3108f-111">This example creates an <xref:System.AsyncCallback> delegate that references the `ProcessDnsInformation` method.</span></span> <span data-ttu-id="3108f-112">這個方法是針對每個非同步要求的 DNS 資訊一次呼叫。</span><span class="sxs-lookup"><span data-stu-id="3108f-112">This method is called once for each asynchronous request for DNS information.</span></span>  
  
 <span data-ttu-id="3108f-113">請注意，在使用者指定的主機會傳遞至<xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object>參數。</span><span class="sxs-lookup"><span data-stu-id="3108f-113">Note that the user-specified host is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> parameter.</span></span> <span data-ttu-id="3108f-114">如需示範如何定義及使用更複雜的狀態物件的範例，請參閱[使用 AsyncCallback 委派和狀態物件](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)。</span><span class="sxs-lookup"><span data-stu-id="3108f-114">For an example that demonstrates defining and using a more complex state object, see [Using an AsyncCallback Delegate and State Object](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).</span></span>  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="3108f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3108f-115">See Also</span></span>  
 [<span data-ttu-id="3108f-116">事件架構非同步模式 (EAP)</span><span class="sxs-lookup"><span data-stu-id="3108f-116">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="3108f-117">事件架構非同步模式概觀</span><span class="sxs-lookup"><span data-stu-id="3108f-117">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [<span data-ttu-id="3108f-118">使用 IAsyncResult 呼叫非同步方法</span><span class="sxs-lookup"><span data-stu-id="3108f-118">Calling Asynchronous Methods Using IAsyncResult</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)  
 [<span data-ttu-id="3108f-119">使用 AsyncCallback 委派和狀態物件</span><span class="sxs-lookup"><span data-stu-id="3108f-119">Using an AsyncCallback Delegate and State Object</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
