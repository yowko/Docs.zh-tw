---
title: 如何：建立通訊端
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- Networking
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- Socket class, creating sockets
- Network Resources
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- sockets, creating
ms.assetid: c64a049c-5981-43bc-a2dc-1851473589c7
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 2ec87d45a4e7140aa2c1d901492952cd25634025
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47192211"
---
# <a name="how-to-create-a-socket"></a><span data-ttu-id="a0cf5-102">如何：建立通訊端</span><span class="sxs-lookup"><span data-stu-id="a0cf5-102">How to: Create a Socket</span></span>
<span data-ttu-id="a0cf5-103">在您使用通訊端與遠端裝置進行通訊之前，必須先使用通訊協定和網路位址資訊初始化通訊端。</span><span class="sxs-lookup"><span data-stu-id="a0cf5-103">Before you can use a socket to communicate with remote devices, the socket must be initialized with protocol and network address information.</span></span> <span data-ttu-id="a0cf5-104"><xref:System.Net.Sockets.Socket> 類別的建構函式所擁有的參數，可指定通訊端用來建立連線的位址家族、通訊端類型和通訊協定類型。</span><span class="sxs-lookup"><span data-stu-id="a0cf5-104">The constructor for the <xref:System.Net.Sockets.Socket> class has parameters that specify the address family, socket type, and protocol type that the socket uses to make connections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0cf5-105">範例</span><span class="sxs-lookup"><span data-stu-id="a0cf5-105">Example</span></span>  
 <span data-ttu-id="a0cf5-106">下列範例會建立可在 TCP/IP 網路 (例如網際網路) 上用於通訊的通訊端。</span><span class="sxs-lookup"><span data-stu-id="a0cf5-106">The following example creates a Socket that can be used to communicate on a TCP/IP-based network, such as the Internet.</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 <span data-ttu-id="a0cf5-107">若要使用 UDP 而不是 TCP，請變更通訊協定類型，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="a0cf5-107">To use UDP instead of TCP, change the protocol type, as in the following example:</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <span data-ttu-id="a0cf5-108"><xref:System.Net.Sockets.AddressFamily> 列舉會指定 **Socket** 用來解析網路位址的標準位址系列 (例如，**AddressFamily.InterNetwork** 成員指定 IP 第 4 版位址系列)。</span><span class="sxs-lookup"><span data-stu-id="a0cf5-108">The <xref:System.Net.Sockets.AddressFamily> enumeration specifies the standard address families used by the **Socket** class to resolve network addresses (for example, the **AddressFamily.InterNetwork** member specifies the IP version 4 address family).</span></span>  
  
 <span data-ttu-id="a0cf5-109"><xref:System.Net.Sockets.SocketType> 列舉會指定通訊端類型 (例如，**SocketType.Stream** 成員指出使用流量控制傳送和接收資料的標準通訊端)。</span><span class="sxs-lookup"><span data-stu-id="a0cf5-109">The <xref:System.Net.Sockets.SocketType> enumeration specifies the type of socket (for example, the **SocketType.Stream** member indicates a standard socket for sending and receiving data with flow control).</span></span>  
  
 <span data-ttu-id="a0cf5-110"><xref:System.Net.Sockets.ProtocolType> 列舉會指定在 **Socket** 上進行通訊時，要使用的網路通訊協定 (例如，**ProtocolType.Tcp** 指出通訊端會使用 TCP；**ProtocolType.Udp** 則指出通訊端會使用 UDP)。</span><span class="sxs-lookup"><span data-stu-id="a0cf5-110">The <xref:System.Net.Sockets.ProtocolType> enumeration specifies the network protocol to use when communicating on the **Socket** (for example, **ProtocolType.Tcp** indicates that the socket uses TCP; **ProtocolType.Udp** indicates that the socket uses UDP).</span></span>  
  
 <span data-ttu-id="a0cf5-111">建立 **Socket** 之後，它可以初始化與遠端端點的連線或接收來自遠端裝置的連線。</span><span class="sxs-lookup"><span data-stu-id="a0cf5-111">After a **Socket** is created, it can either initiate a connection to a remote endpoint or receive connections from remote devices.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0cf5-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="a0cf5-112">See Also</span></span>  
 [<span data-ttu-id="a0cf5-113">使用用戶端通訊端</span><span class="sxs-lookup"><span data-stu-id="a0cf5-113">Using Client Sockets</span></span>](../../../docs/framework/network-programming/using-client-sockets.md)  
 [<span data-ttu-id="a0cf5-114">透過通訊端接聽</span><span class="sxs-lookup"><span data-stu-id="a0cf5-114">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)
