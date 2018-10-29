---
title: Web 和通訊端權限
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- positions [.NET Framework], accepting
- sockets, permissions
- network, permissions
- Internet, permissions
- Network Resources
- SocketPermission class, about SocketPermission class
- positions [.NET Framework], connecting
- WebPermission class, about WebPermission class
- permissions [.NET Framework], sockets
- security [.NET Framework], Internet
- positions [.NET Framework], granting
ms.assetid: d51ad8cb-03ae-4a51-bfcd-cfcf6b98afa9
ms.openlocfilehash: b5767f4e16e691fec5714f98114b3ed9d5692a50
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2018
ms.locfileid: "50205083"
---
# <a name="web-and-socket-permissions"></a><span data-ttu-id="2efcb-102">Web 和通訊端權限</span><span class="sxs-lookup"><span data-stu-id="2efcb-102">Web and Socket Permissions</span></span>
<span data-ttu-id="2efcb-103">使用 <xref:System.Net> 命名空間之應用程式的網際網路安全性是透過 <xref:System.Net.WebPermission> 和 <xref:System.Net.SocketPermission> 類別提供。</span><span class="sxs-lookup"><span data-stu-id="2efcb-103">Internet security for applications using the <xref:System.Net> namespace is provided by the <xref:System.Net.WebPermission> and <xref:System.Net.SocketPermission> classes.</span></span> <span data-ttu-id="2efcb-104">**WebPermission** 類別可控制應用程式向 URI 要求資料，或提供 URI 給網際網路的權限。</span><span class="sxs-lookup"><span data-stu-id="2efcb-104">The **WebPermission** class controls an application's right to request data from a URI or to serve a URI to the Internet.</span></span> <span data-ttu-id="2efcb-105">**SocketPermission** 類別則可控制應用程式根據通訊端的主機、連接埠編號和傳輸通訊協定，使用 <xref:System.Net.Sockets.Socket> 在本機連接埠上接受資料，或使用另一個位址上的傳輸通訊協定連絡遠端裝置的權限。</span><span class="sxs-lookup"><span data-stu-id="2efcb-105">The **SocketPermission** class controls an application's right to use a <xref:System.Net.Sockets.Socket> to accept data on a local port or to contact remote devices using a transport protocol at another address, based on the host, port number, and transport protocol of the socket.</span></span>  
  
 <span data-ttu-id="2efcb-106">使用的權限類別取決於您的應用程式類型。</span><span class="sxs-lookup"><span data-stu-id="2efcb-106">Which permission class you use depends on your application type.</span></span> <span data-ttu-id="2efcb-107">使用 <xref:System.Net.WebRequest> 和其子系的應用程式應使用 **WebPermission** 類別來管理權限。</span><span class="sxs-lookup"><span data-stu-id="2efcb-107">Applications that use <xref:System.Net.WebRequest> and its descendants should use the **WebPermission** class to manage permissions.</span></span> <span data-ttu-id="2efcb-108">使用通訊端層級存取的應用程式應使用 **SocketPermission** 類別來管理權限。</span><span class="sxs-lookup"><span data-stu-id="2efcb-108">Applications that use socket-level access should use the **SocketPermission** class to manage permissions.</span></span>  
  
 <span data-ttu-id="2efcb-109">**WebPermission** 和 **SocketPermission** 定義兩個權限：接受和連線。</span><span class="sxs-lookup"><span data-stu-id="2efcb-109">**WebPermission** and **SocketPermission** define two permissions: accept and connect.</span></span> <span data-ttu-id="2efcb-110">接受可授與應用程式回應來自另一方之連入連線的權限。</span><span class="sxs-lookup"><span data-stu-id="2efcb-110">Accept grants the application the right to answer an incoming connection from another party.</span></span> <span data-ttu-id="2efcb-111">連線可授與應用程式起始與另一方之連線的權限。</span><span class="sxs-lookup"><span data-stu-id="2efcb-111">Connect grants the application the right to initiate a connection to another party.</span></span>  
  
 <span data-ttu-id="2efcb-112">若是 **SocketPermission** 執行個體，接受表示應用程式可以在本機傳輸位址上接受連入連線；連線表示應用程式可以連線到某個遠端 (或本機) 傳輸位址。</span><span class="sxs-lookup"><span data-stu-id="2efcb-112">For **SocketPermission** instances, accept means that an application can accept incoming connections on a local transport address; connect means that an application can connect to some remote (or local) transport address.</span></span>  
  
 <span data-ttu-id="2efcb-113">若是 **WebPermission** 執行個體，接受表示應用程式可以將 **WebPermission** 所控制的 URI 匯出到全世界；連線表示應用程式可以存取該 URI (不論它是遠端或本機)。</span><span class="sxs-lookup"><span data-stu-id="2efcb-113">For **WebPermission** instances, accept means that an application can export the URI controlled by the **WebPermission** to the world; connect means that an application can access that URI (whether it is remote or local).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2efcb-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="2efcb-114">See Also</span></span>  
 [<span data-ttu-id="2efcb-115">安全性</span><span class="sxs-lookup"><span data-stu-id="2efcb-115">Security</span></span>](../../../docs/standard/security/index.md)  
 [<span data-ttu-id="2efcb-116">網路程式設計的安全性</span><span class="sxs-lookup"><span data-stu-id="2efcb-116">Security in Network Programming</span></span>](../../../docs/framework/network-programming/security-in-network-programming.md)
