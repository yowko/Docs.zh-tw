---
title: 使用 AsyncCallback 委派和狀態物件
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 259f7de52dff04af043554382a5bad35355d9926
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567233"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a><span data-ttu-id="7c6c2-102">使用 AsyncCallback 委派和狀態物件</span><span class="sxs-lookup"><span data-stu-id="7c6c2-102">Using an AsyncCallback Delegate and State Object</span></span>
<span data-ttu-id="7c6c2-103">當您使用 <xref:System.AsyncCallback> 委派以處理不同執行緒中非同步作業的結果，可以使用狀態物件傳遞回呼之間的資訊以擷取最終結果。</span><span class="sxs-lookup"><span data-stu-id="7c6c2-103">When you use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread, you can use a state object to pass information between the callbacks and to retrieve a final result.</span></span> <span data-ttu-id="7c6c2-104">本主題透過展開[使用 AsyncCallback 委派結束非同步作業](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)中的範例來示範該做法。</span><span class="sxs-lookup"><span data-stu-id="7c6c2-104">This topic demonstrates that practice by expanding the example in [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c6c2-105">範例</span><span class="sxs-lookup"><span data-stu-id="7c6c2-105">Example</span></span>  
 <span data-ttu-id="7c6c2-106">下列範例示範在 <xref:System.Net.Dns> 類別中使用非同步方法，以擷取使用者指定電腦的網域名稱系統 (DNS) 資訊。</span><span class="sxs-lookup"><span data-stu-id="7c6c2-106">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="7c6c2-107">此範例定義和使用 `HostRequest` 類別來儲存狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="7c6c2-107">This example defines and uses the `HostRequest` class to store state information.</span></span> <span data-ttu-id="7c6c2-108">為使用者所輸入的每個電腦名稱建立 `HostRequest` 物件。</span><span class="sxs-lookup"><span data-stu-id="7c6c2-108">A `HostRequest` object gets created for each computer name entered by the user.</span></span> <span data-ttu-id="7c6c2-109">此物件會傳遞給 <xref:System.Net.Dns.BeginGetHostByName%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="7c6c2-109">This object is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A> method.</span></span> <span data-ttu-id="7c6c2-110">每次要求完成時都會呼叫 `ProcessDnsInformation` 方法。</span><span class="sxs-lookup"><span data-stu-id="7c6c2-110">The `ProcessDnsInformation` method is called each time a request completes.</span></span> <span data-ttu-id="7c6c2-111">使用 <xref:System.IAsyncResult.AsyncState%2A> 屬性擷取 `HostRequest` 物件。</span><span class="sxs-lookup"><span data-stu-id="7c6c2-111">The `HostRequest` object is retrieved using the <xref:System.IAsyncResult.AsyncState%2A> property.</span></span> <span data-ttu-id="7c6c2-112">`ProcessDnsInformation` 方法會使用 `HostRequest` 物件儲存要求傳回的 <xref:System.Net.IPHostEntry> 或要求所擲回的 <xref:System.Net.Sockets.SocketException>。</span><span class="sxs-lookup"><span data-stu-id="7c6c2-112">The `ProcessDnsInformation` method uses the `HostRequest` object to store the <xref:System.Net.IPHostEntry> returned by the request or a <xref:System.Net.Sockets.SocketException> thrown by the request.</span></span> <span data-ttu-id="7c6c2-113">當所有要求都完成時，應用程式會逐一查看 `HostRequest` 物件並顯示 DNS 資訊或 <xref:System.Net.Sockets.SocketException> 錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="7c6c2-113">When all requests are complete, the application iterates over the `HostRequest` objects and displays the DNS information or <xref:System.Net.Sockets.SocketException> error message.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="7c6c2-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="7c6c2-114">See Also</span></span>  
 [<span data-ttu-id="7c6c2-115">事件架構非同步模式 (EAP)</span><span class="sxs-lookup"><span data-stu-id="7c6c2-115">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="7c6c2-116">事件架構非同步模式概觀</span><span class="sxs-lookup"><span data-stu-id="7c6c2-116">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [<span data-ttu-id="7c6c2-117">使用 AsyncCallback 委派結束非同步作業</span><span class="sxs-lookup"><span data-stu-id="7c6c2-117">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
