---
title: "System.Net 類別的最佳作法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sending data, best practices
- requesting data from Internet, best practices
- WebRequest class, best practices
- data requests, best practices
- WebResponse class, best practices
- best practices, data requests
- receiving data, best practices
ms.assetid: 716decc6-5952-47b7-9c5a-ba6fc5698684
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 90722abbdb4568be115c0ac77007d5f18984df6f
ms.sourcegitcommit: 32172ca05d5dcce7ef3d327b9c8639c736e0fe2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2018
---
# <a name="best-practices-for-systemnet-classes"></a><span data-ttu-id="1e1fd-102">System.Net 類別的最佳作法</span><span class="sxs-lookup"><span data-stu-id="1e1fd-102">Best Practices for System.Net Classes</span></span>
<span data-ttu-id="1e1fd-103">下列建議將協助您善加利用 <xref:System.Net> 中所含的類別：</span><span class="sxs-lookup"><span data-stu-id="1e1fd-103">The following recommendations will help you use the classes contained in <xref:System.Net> to their best advantage:</span></span>  
  
-   <span data-ttu-id="1e1fd-104">傳輸層安全性 (TLS) 的最佳作法，請參閱[傳輸層安全性 (TLS) 的最佳作法，以.NET Framework](tls.md)。</span><span class="sxs-lookup"><span data-stu-id="1e1fd-104">For Transport Layer Security (TLS) best practices, see [Transport Layer Security (TLS) best practices with .NET Framework](tls.md).</span></span>

-   <span data-ttu-id="1e1fd-105">可能的話，請使用 <xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse>，而不是對子系類別進行類型轉換。</span><span class="sxs-lookup"><span data-stu-id="1e1fd-105">Use <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> whenever possible instead of type casting to descendant classes.</span></span> <span data-ttu-id="1e1fd-106">使用 **WebRequest** 和 **WebResponse** 的應用程式可以利用新的網際網路通訊協定，而不需要大量的程式碼變更。</span><span class="sxs-lookup"><span data-stu-id="1e1fd-106">Applications that use **WebRequest** and **WebResponse** can take advantage of new Internet protocols without needing extensive code changes.</span></span>  
  
-   <span data-ttu-id="1e1fd-107">使用 **System.Net** 類別撰寫在伺服器上執行的 ASP.NET 應用程式時，其效能通常會比使用 <xref:System.Net.WebRequest.GetResponse%2A> 和 <xref:System.Net.WebResponse.GetResponseStream%2A> 的非同步方法還要好。</span><span class="sxs-lookup"><span data-stu-id="1e1fd-107">When writing ASP.NET applications that run on a server using the **System.Net** classes, it is often better, from a performance standpoint, to use the asynchronous methods for <xref:System.Net.WebRequest.GetResponse%2A> and <xref:System.Net.WebResponse.GetResponseStream%2A>.</span></span>  
  
-   <span data-ttu-id="1e1fd-108">開啟至網際網路資源的連線數目，會對網路效能和輸送量造成明顯影響。</span><span class="sxs-lookup"><span data-stu-id="1e1fd-108">The number of connections opened to an Internet resource can have a significant impact on network performance and throughput.</span></span> <span data-ttu-id="1e1fd-109">**System.Net** 預設會為每個主機的每個應用程式使用兩個連線。</span><span class="sxs-lookup"><span data-stu-id="1e1fd-109">**System.Net** uses two connections per application per host by default.</span></span> <span data-ttu-id="1e1fd-110">在應用程式的 <xref:System.Net.ServicePoint> 中設定 <xref:System.Net.ServicePoint.ConnectionLimit%2A> 屬性，可能會針對特定主機增加這個數目。</span><span class="sxs-lookup"><span data-stu-id="1e1fd-110">Setting the <xref:System.Net.ServicePoint.ConnectionLimit%2A> property in the <xref:System.Net.ServicePoint> for your application can increase this number for a particular host.</span></span> <span data-ttu-id="1e1fd-111">設定 <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> 屬性可以為所有主機增加這個預設值。</span><span class="sxs-lookup"><span data-stu-id="1e1fd-111">Setting the <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> property can increase this default for all hosts.</span></span>  
  
-   <span data-ttu-id="1e1fd-112">撰寫通訊端層級通訊協定時，請盡可能嘗試使用 <xref:System.Net.Sockets.TcpClient> 或 <xref:System.Net.Sockets.UdpClient>，而不是直接寫入至 <xref:System.Net.Sockets.Socket>。</span><span class="sxs-lookup"><span data-stu-id="1e1fd-112">When writing socket-level protocols, try to use <xref:System.Net.Sockets.TcpClient> or <xref:System.Net.Sockets.UdpClient> whenever possible instead of writing directly to a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="1e1fd-113">這兩個用戶端類別會封裝 TCP 和 UDP 通訊端的建立，而不需要您處理連線的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="1e1fd-113">These two client classes encapsulate the creation of TCP and UDP sockets without requiring you to handle the details of the connection.</span></span>  
  
-   <span data-ttu-id="1e1fd-114">存取需要認證的網站時，請使用 <xref:System.Net.CredentialCache> 類別建立認證的快取，而不是每個要求都提供它們。</span><span class="sxs-lookup"><span data-stu-id="1e1fd-114">When accessing sites that require credentials, use the <xref:System.Net.CredentialCache> class to create a cache of credentials rather than supplying them with every request.</span></span> <span data-ttu-id="1e1fd-115">**CredentialCache** 類別會搜尋快取，以透過要求找到要呈現的適當認證，讓您不需要負責根據 URL 來建立和呈現認證。</span><span class="sxs-lookup"><span data-stu-id="1e1fd-115">The **CredentialCache** class searches the cache to find the appropriate credential to present with a request, relieving you of the responsibility of creating and presenting credentials based on the URL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e1fd-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e1fd-116">See Also</span></span>  
 [<span data-ttu-id="1e1fd-117">以 .NET Framework 進行網路程式設計</span><span class="sxs-lookup"><span data-stu-id="1e1fd-117">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)
