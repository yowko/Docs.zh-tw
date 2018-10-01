---
title: 透過通訊端接聽
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- sockets, listening with sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- protocols, sockets
- listening with sockets
- Internet, sockets
ms.assetid: 40e426cc-13db-4371-95eb-f7388bd23ebf
author: mcleblanc
ms.author: markl
ms.openlocfilehash: c518c3bea980e23367477bd1b9851630454b728b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2018
ms.locfileid: "47209882"
---
# <a name="listening-with-sockets"></a><span data-ttu-id="c0123-102">透過通訊端接聽</span><span class="sxs-lookup"><span data-stu-id="c0123-102">Listening with Sockets</span></span>
<span data-ttu-id="c0123-103">接聽程式或伺服器通訊端會開啟網路的連接埠，等候用戶端連接到該連接埠。</span><span class="sxs-lookup"><span data-stu-id="c0123-103">Listener or server sockets open a port on the network and then wait for a client to connect to that port.</span></span> <span data-ttu-id="c0123-104">雖然有其他的網路位址系列和通訊協定存在，但此範例會示範如何建立遠端服務的 TCP/IP 網路連線。</span><span class="sxs-lookup"><span data-stu-id="c0123-104">Although other network address families and protocols exist, this example shows how to create remote service for a TCP/IP network.</span></span>  
  
 <span data-ttu-id="c0123-105">定義 TCP/IP 服務唯一位址的方式，是結合主機的 IP 位址與服務的連接埠號碼，建立服務的端點。</span><span class="sxs-lookup"><span data-stu-id="c0123-105">The unique address of a TCP/IP service is defined by combining the IP address of the host with the port number of the service to create an endpoint for the service.</span></span> <span data-ttu-id="c0123-106"><xref:System.Net.Dns> 類別提供的方法，會傳回區域網路裝置支援的網路位址相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c0123-106">The <xref:System.Net.Dns> class provides methods that return information about the network addresses supported by the local network device.</span></span> <span data-ttu-id="c0123-107">當區域網路裝置有多個網路位址，或本機系統支援多部網路裝置時，**Dns** 類別會傳回所有網路位址的相關資訊，而應用程式必須選擇適當的服務位址。</span><span class="sxs-lookup"><span data-stu-id="c0123-107">When the local network device has more than one network address, or if the local system supports more than one network device, the **Dns** class returns information about all network addresses, and the application must choose the proper address for the service.</span></span> <span data-ttu-id="c0123-108">Internet Assigned Numbers Authority (Iana) 定義了通用服務的連接埠編號。如需詳細資訊，請參閱 [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/port-numbers) (服務名稱與傳輸通訊協定連接埠號碼登錄)。</span><span class="sxs-lookup"><span data-stu-id="c0123-108">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services; for more information, see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="c0123-109">其他服務的登錄連接埠號碼範圍可以是 1,024 到 65,535。</span><span class="sxs-lookup"><span data-stu-id="c0123-109">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="c0123-110">下列範例會結合主機電腦 **Dns** 傳回的第一個 IP 位址，和從已登錄連接埠號碼範圍中選擇的連接埠號碼，為伺服器建立 <xref:System.Net.IPEndPoint>。</span><span class="sxs-lookup"><span data-stu-id="c0123-110">The following example creates an <xref:System.Net.IPEndPoint> for a server by combining the first IP address returned by **Dns** for the host computer with a port number chosen from the registered port numbers range.</span></span>  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
Dim localEndPoint As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
IPEndPoint localEndPoint = new IPEndPoint(ipAddress, 11000);  
```  
  
 <span data-ttu-id="c0123-111">決定本機端點之後，<xref:System.Net.Sockets.Socket> 必須使用 <xref:System.Net.Sockets.Socket.Bind%2A> 方法建立與該端點的關聯，並使用 <xref:System.Net.Sockets.Socket.Listen%2A> 方法設定接聽端點。</span><span class="sxs-lookup"><span data-stu-id="c0123-111">After the local endpoint is determined, the <xref:System.Net.Sockets.Socket> must be associated with that endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> method and set to listen on the endpoint using the <xref:System.Net.Sockets.Socket.Listen%2A> method.</span></span> <span data-ttu-id="c0123-112">如已使用特定位址和連接埠的組合，**Bind** 會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c0123-112">**Bind** throws an exception if the specific address and port combination is already in use.</span></span> <span data-ttu-id="c0123-113">下列範例會示範建立**通訊端**與 **IPEndPoint** 的關聯。</span><span class="sxs-lookup"><span data-stu-id="c0123-113">The following example demonstrates associating a **Socket** with an **IPEndPoint**.</span></span>  
  
```vb  
Dim listener As New Socket(ipAddress.AddressFamily, _  
    SocketType.Stream, ProtocolType.Tcp) 
listener.Bind(localEndPoint)  
listener.Listen(100)  
```  
  
```csharp  
Socket listener = new Socket(ipAddress.AddressFamily,
    SocketType.Stream, ProtocolType.Tcp);
listener.Bind(localEndPoint);  
listener.Listen(100);  
```  
  
 <span data-ttu-id="c0123-114">**Listen** 方法會採用單一參數，指定在伺服器忙碌錯誤傳回至連線的用戶端之前，允許的**通訊端**暫止連線數目。</span><span class="sxs-lookup"><span data-stu-id="c0123-114">The **Listen** method takes a single parameter that specifies how many pending connections to the **Socket** are allowed before a server busy error is returned to the connecting client.</span></span> <span data-ttu-id="c0123-115">在本例中，在伺服器忙碌回應傳回至用戶端編號 101 之前，連線佇列中最多放置 100 個用戶端。</span><span class="sxs-lookup"><span data-stu-id="c0123-115">In this case, up to 100 clients are placed in the connection queue before a server busy response is returned to client number 101.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0123-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="c0123-116">See Also</span></span>  
 [<span data-ttu-id="c0123-117">使用同步伺服器通訊端</span><span class="sxs-lookup"><span data-stu-id="c0123-117">Using a Synchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)  
 [<span data-ttu-id="c0123-118">使用非同步伺服器通訊端</span><span class="sxs-lookup"><span data-stu-id="c0123-118">Using an Asynchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [<span data-ttu-id="c0123-119">使用用戶端通訊端</span><span class="sxs-lookup"><span data-stu-id="c0123-119">Using Client Sockets</span></span>](../../../docs/framework/network-programming/using-client-sockets.md)  
 [<span data-ttu-id="c0123-120">如何：建立通訊端</span><span class="sxs-lookup"><span data-stu-id="c0123-120">How to: Create a Socket</span></span>](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
 [<span data-ttu-id="c0123-121">通訊端</span><span class="sxs-lookup"><span data-stu-id="c0123-121">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
