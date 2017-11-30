---
title: "使用 AsyncCallback 委派和狀態物件"
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
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e8793a78289e9b58407038f41cc9d403ff9f9940
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a><span data-ttu-id="50729-102">使用 AsyncCallback 委派和狀態物件</span><span class="sxs-lookup"><span data-stu-id="50729-102">Using an AsyncCallback Delegate and State Object</span></span>
<span data-ttu-id="50729-103">當您使用<xref:System.AsyncCallback>委派處理不同的執行緒中的非同步作業的結果、 回呼之間傳遞資訊，以及擷取最終的結果，您可以使用狀態物件。</span><span class="sxs-lookup"><span data-stu-id="50729-103">When you use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread, you can use a state object to pass information between the callbacks and to retrieve a final result.</span></span> <span data-ttu-id="50729-104">本主題示範展開的範例中的該作法[使用 AsyncCallback 委派結束非同步作業](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="50729-104">This topic demonstrates that practice by expanding the example in [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="50729-105">範例</span><span class="sxs-lookup"><span data-stu-id="50729-105">Example</span></span>  
 <span data-ttu-id="50729-106">下列程式碼範例示範如何使用中的非同步方法<xref:System.Net.Dns>類別來擷取指定使用者電腦的網域名稱系統 (DNS) 資訊。</span><span class="sxs-lookup"><span data-stu-id="50729-106">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="50729-107">這個範例會定義並使用`HostRequest`類別來儲存狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="50729-107">This example defines and uses the `HostRequest` class to store state information.</span></span> <span data-ttu-id="50729-108">A`HostRequest`取得建立使用者輸入的每個電腦名稱的物件。</span><span class="sxs-lookup"><span data-stu-id="50729-108">A `HostRequest` object gets created for each computer name entered by the user.</span></span> <span data-ttu-id="50729-109">這個物件傳遞至<xref:System.Net.Dns.BeginGetHostByName%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="50729-109">This object is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A> method.</span></span> <span data-ttu-id="50729-110">`ProcessDnsInformation`在要求完成每次呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="50729-110">The `ProcessDnsInformation` method is called each time a request completes.</span></span> <span data-ttu-id="50729-111">`HostRequest`使用擷取物件<xref:System.IAsyncResult.AsyncState%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="50729-111">The `HostRequest` object is retrieved using the <xref:System.IAsyncResult.AsyncState%2A> property.</span></span> <span data-ttu-id="50729-112">`ProcessDnsInformation`方法會使用`HostRequest`儲存物件<xref:System.Net.IPHostEntry>由要求傳回或<xref:System.Net.Sockets.SocketException>要求所擲回。</span><span class="sxs-lookup"><span data-stu-id="50729-112">The `ProcessDnsInformation` method uses the `HostRequest` object to store the <xref:System.Net.IPHostEntry> returned by the request or a <xref:System.Net.Sockets.SocketException> thrown by the request.</span></span> <span data-ttu-id="50729-113">應用程式的所有要求完成時，會逐一`HostRequest`物件並顯示 DNS 資訊或<xref:System.Net.Sockets.SocketException>錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="50729-113">When all requests are complete, the application iterates over the `HostRequest` objects and displays the DNS information or <xref:System.Net.Sockets.SocketException> error message.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="50729-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50729-114">See Also</span></span>  
 [<span data-ttu-id="50729-115">事件架構非同步模式 (EAP)</span><span class="sxs-lookup"><span data-stu-id="50729-115">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="50729-116">事件架構非同步模式概觀</span><span class="sxs-lookup"><span data-stu-id="50729-116">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [<span data-ttu-id="50729-117">使用 AsyncCallback 委派結束非同步作業</span><span class="sxs-lookup"><span data-stu-id="50729-117">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
