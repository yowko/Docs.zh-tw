---
title: TCP-UDP
ms.date: 03/30/2017
helpviewer_keywords:
- protocols, TCP/UDP
- network resources, TCP/UDP
- sending data, TCP/UDP
- TCP/UDP
- TcpClient class, about TcpClient class
- application protocols, TCP/UDP
- receiving data, TCP/UDP
- TcpListener class, about TcpListener class
- Socket class, about Socket class
- UDP
- data requests, TCP/UDP
- requesting data from Internet, TCP/UDP
- Internet, TCP/UDP
ms.assetid: df29b4b0-49e8-4923-82b9-13150dfc40f5
ms.openlocfilehash: d35278ab7feb42453b5a0adbc86c47b7ac3ff5ca
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047104"
---
# <a name="tcp-udp"></a><span data-ttu-id="402cc-102">TCP-UDP</span><span class="sxs-lookup"><span data-stu-id="402cc-102">TCP-UDP</span></span>
<span data-ttu-id="402cc-103">應用程式可以使用「傳輸控制通訊協定 (TCP)」和「使用者資料包通訊協定 (UDP)」服務，搭配 <xref:System.Net.Sockets.TcpClient>、<xref:System.Net.Sockets.TcpListener> 和 <xref:System.Net.Sockets.UdpClient> 類別。</span><span class="sxs-lookup"><span data-stu-id="402cc-103">Applications can use Transmission Control Protocol (TCP) and User Datagram Protocol (UDP) services with the <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes.</span></span> <span data-ttu-id="402cc-104">這些通訊協定類別建立在 <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> 類別之上，並負責傳送資料的細節。</span><span class="sxs-lookup"><span data-stu-id="402cc-104">These protocol classes are built on top of the <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class and take care of the details of transferring data.</span></span>  
  
 <span data-ttu-id="402cc-105">通訊協定類別使用 **Socket** 類別的同步方法，以提供簡單且直接的網路服務存取，不需要維護狀態資訊或了解設定通訊協定特定通訊端的詳細資料等成本。</span><span class="sxs-lookup"><span data-stu-id="402cc-105">The protocol classes use the synchronous methods of the **Socket** class to provide simple and straightforward access to network services without the overhead of maintaining state information or knowing the details of setting up protocol-specific sockets.</span></span> <span data-ttu-id="402cc-106">若要使用非同步 **Socket** 方法，您可以使用 <xref:System.Net.Sockets.NetworkStream> 類別所提供的非同步方法。</span><span class="sxs-lookup"><span data-stu-id="402cc-106">To use asynchronous **Socket** methods, you can use the asynchronous methods supplied by the <xref:System.Net.Sockets.NetworkStream> class.</span></span> <span data-ttu-id="402cc-107">若要存取 **Socket** 類別中通訊協定類別未公開的功能，您必須使用 **Socket** 類別。</span><span class="sxs-lookup"><span data-stu-id="402cc-107">To access features of the **Socket** class not exposed by the protocol classes, you must use the **Socket** class.</span></span>  
  
 <span data-ttu-id="402cc-108">**TcpClient** 和 **TcpListener** 代表使用 **NetworkStream** 類別的網路。</span><span class="sxs-lookup"><span data-stu-id="402cc-108">**TcpClient** and **TcpListener** represent the network using the **NetworkStream** class.</span></span> <span data-ttu-id="402cc-109">您使用 <xref:System.Net.Sockets.TcpClient.GetStream%2A> 方法來傳回網路資料流，然後呼叫資料流的 <xref:System.Net.Sockets.NetworkStream.Read%2A> 和 <xref:System.Net.Sockets.NetworkStream.Write%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="402cc-109">You use the <xref:System.Net.Sockets.TcpClient.GetStream%2A> method to return the network stream, and then call the stream's <xref:System.Net.Sockets.NetworkStream.Read%2A> and <xref:System.Net.Sockets.NetworkStream.Write%2A> methods.</span></span> <span data-ttu-id="402cc-110">**NetworkStream** 並未擁有通訊協定類別的基礎通訊端，因此關閉它並不會影響通訊端。</span><span class="sxs-lookup"><span data-stu-id="402cc-110">The **NetworkStream** does not own the protocol classes' underlying socket, so closing it does not affect the socket.</span></span>  
  
 <span data-ttu-id="402cc-111">**UdpClient** 類別使用位元組陣列來保留 UDP 資料包。</span><span class="sxs-lookup"><span data-stu-id="402cc-111">The **UdpClient** class uses an array of bytes to hold the UDP datagram.</span></span> <span data-ttu-id="402cc-112">您使用 <xref:System.Net.Sockets.UdpClient.Send%2A> 方法將資料傳送到網路，及使用 <xref:System.Net.Sockets.UdpClient.Receive%2A> 方法來接收連入的資料包。</span><span class="sxs-lookup"><span data-stu-id="402cc-112">You use the <xref:System.Net.Sockets.UdpClient.Send%2A> method to send the data to the network and the <xref:System.Net.Sockets.UdpClient.Receive%2A> method to receive an incoming datagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="402cc-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="402cc-113">See also</span></span>

- [<span data-ttu-id="402cc-114">使用 TCP 服務</span><span class="sxs-lookup"><span data-stu-id="402cc-114">Using TCP Services</span></span>](using-tcp-services.md)
- [<span data-ttu-id="402cc-115">使用 UDP 服務</span><span class="sxs-lookup"><span data-stu-id="402cc-115">Using UDP Services</span></span>](using-udp-services.md)
- [<span data-ttu-id="402cc-116">在網路上使用資料流</span><span class="sxs-lookup"><span data-stu-id="402cc-116">Using Streams on the Network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="402cc-117">使用非同步伺服器通訊端</span><span class="sxs-lookup"><span data-stu-id="402cc-117">Using an Asynchronous Server Socket</span></span>](using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="402cc-118">使用非同步用戶端通訊端</span><span class="sxs-lookup"><span data-stu-id="402cc-118">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="402cc-119">使用應用程式通訊協定</span><span class="sxs-lookup"><span data-stu-id="402cc-119">Using Application Protocols</span></span>](using-application-protocols.md)
