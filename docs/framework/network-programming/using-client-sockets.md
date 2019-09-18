---
title: 使用用戶端通訊端
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- Socket class, client sockets
- protocols, sockets
- Internet, sockets
- sockets, client sockets
- client sockets
ms.assetid: 81de9f59-8177-4d98-b25d-43fc32a98383
ms.openlocfilehash: fe2ad55c3f60347369c0e92bc834d81d98f3870e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046949"
---
# <a name="using-client-sockets"></a><span data-ttu-id="5bfd3-102">使用用戶端通訊端</span><span class="sxs-lookup"><span data-stu-id="5bfd3-102">Using Client Sockets</span></span>
<span data-ttu-id="5bfd3-103">在透過 <xref:System.Net.Sockets.Socket> 起始交談之前，您必須先建立應用程式和遠端裝置之間的資料管道。</span><span class="sxs-lookup"><span data-stu-id="5bfd3-103">Before you can initiate a conversation through a <xref:System.Net.Sockets.Socket>, you must create a data pipe between your application and the remote device.</span></span> <span data-ttu-id="5bfd3-104">雖然有其他的網路位址系列和通訊協定存在，但此範例會示範如何建立遠端服務的 TCP/IP 連線。</span><span class="sxs-lookup"><span data-stu-id="5bfd3-104">Although other network address families and protocols exist, this example shows how to create a TCP/IP connection to a remote service.</span></span>  
  
 <span data-ttu-id="5bfd3-105">TCP/IP 會使用網路位址和服務連接埠編號來唯一識別服務。</span><span class="sxs-lookup"><span data-stu-id="5bfd3-105">TCP/IP uses a network address and a service port number to uniquely identify a service.</span></span> <span data-ttu-id="5bfd3-106">網路位址可識別網路上的特定裝置；連接埠編號則可識別該裝置上要連線的特定服務。</span><span class="sxs-lookup"><span data-stu-id="5bfd3-106">The network address identifies a specific device on the network; the port number identifies the specific service on that device to connect to.</span></span> <span data-ttu-id="5bfd3-107">網路位址和服務連接埠的組合稱為端點，在 .NET Framework 中是以 <xref:System.Net.EndPoint> 類別表示。</span><span class="sxs-lookup"><span data-stu-id="5bfd3-107">The combination of network address and service port is called an endpoint, which is represented in the .NET Framework by the <xref:System.Net.EndPoint> class.</span></span> <span data-ttu-id="5bfd3-108">每個支援的位址系列已定義 **EndPoin** 的子系；對於 IP 位址系列，此類別是 <xref:System.Net.IPEndPoint>。</span><span class="sxs-lookup"><span data-stu-id="5bfd3-108">A descendant of **EndPoint** is defined for each supported address family; for the IP address family, the class is <xref:System.Net.IPEndPoint>.</span></span>  
  
 <span data-ttu-id="5bfd3-109"><xref:System.Net.Dns> 類別會提供網域名稱服務給使用 TCP/IP 網際網路服務的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5bfd3-109">The <xref:System.Net.Dns> class provides domain-name services to applications that use TCP/IP Internet services.</span></span> <span data-ttu-id="5bfd3-110"><xref:System.Net.Dns.Resolve%2A> 方法會查詢 DNS 伺服器，以將使用者易記的網域名稱 (例如 "host.contoso.com") 對應到數字的網際網路位址 (例如 192.168.1.1)。</span><span class="sxs-lookup"><span data-stu-id="5bfd3-110">The <xref:System.Net.Dns.Resolve%2A> method queries a DNS server to map a user-friendly domain name (such as "host.contoso.com") to a numeric Internet address (such as 192.168.1.1).</span></span> <span data-ttu-id="5bfd3-111">**Resolve** 會傳回 <xref:System.Net.IPHostEntry>，其中包含位址和所要求名稱之別名的清單。</span><span class="sxs-lookup"><span data-stu-id="5bfd3-111">**Resolve** returns an <xref:System.Net.IPHostEntry> that contains a list of addresses and aliases for the requested name.</span></span> <span data-ttu-id="5bfd3-112">在大部分情況下，您可以使用 <xref:System.Net.IPHostEntry.AddressList%2A> 陣列中傳回的第一個位址。</span><span class="sxs-lookup"><span data-stu-id="5bfd3-112">In most cases, you can use the first address returned in the <xref:System.Net.IPHostEntry.AddressList%2A> array.</span></span> <span data-ttu-id="5bfd3-113">下列程式碼可取得包含伺服器 host.contoso.com 之 IP 位址的 <xref:System.Net.IPAddress>。</span><span class="sxs-lookup"><span data-stu-id="5bfd3-113">The following code gets an <xref:System.Net.IPAddress> containing the IP address for the server host.contoso.com.</span></span>  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 <span data-ttu-id="5bfd3-114">Internet Assigned Numbers Authority (Iana) 定義了通用服務的連接埠編號 (如需詳細資訊，請參閱[服務名稱與傳輸通訊協定連接埠號碼登錄](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml) \(英文\))。</span><span class="sxs-lookup"><span data-stu-id="5bfd3-114">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (for more information, see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="5bfd3-115">其他服務的登錄連接埠號碼範圍可以是 1,024 到 65,535。</span><span class="sxs-lookup"><span data-stu-id="5bfd3-115">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span> <span data-ttu-id="5bfd3-116">下列程式碼會合併 host.contoso.com 的 IP 位址與連接埠編號，以建立連線的遠端端點。</span><span class="sxs-lookup"><span data-stu-id="5bfd3-116">The following code combines the IP address for host.contoso.com with a port number to create a remote endpoint for a connection.</span></span>  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 <span data-ttu-id="5bfd3-117">在判斷遠端裝置的位址並選擇要用於連線的連接埠之後，應用程式可以嘗試建立與遠端裝置的連線。</span><span class="sxs-lookup"><span data-stu-id="5bfd3-117">After determining the address of the remote device and choosing a port to use for the connection, the application can attempt to establish a connection with the remote device.</span></span> <span data-ttu-id="5bfd3-118">下列範例會使用現有 **IPEndPoint** 連線到遠端裝置，並捕捉任何擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5bfd3-118">The following example uses an existing **IPEndPoint** to connect to a remote device and catches any exceptions that are thrown.</span></span>  
  
```vb  
Try  
    s.Connect(ipe)  
Catch ae As ArgumentNullException  
    Console.WriteLine("ArgumentNullException : {0}", _  
        ae.ToString())  
Catch se As SocketException  
    Console.WriteLine("SocketException : {0}", se.ToString())  
Catch e As Exception  
    Console.WriteLine("Unexpected exception : {0}", e.ToString())  
End Try  
```  
  
```csharp  
try {  
    s.Connect(ipe);  
} catch(ArgumentNullException ae) {  
    Console.WriteLine("ArgumentNullException : {0}", ae.ToString());  
} catch(SocketException se) {  
    Console.WriteLine("SocketException : {0}", se.ToString());  
} catch(Exception e) {  
    Console.WriteLine("Unexpected exception : {0}", e.ToString());  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="5bfd3-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bfd3-119">See also</span></span>

- [<span data-ttu-id="5bfd3-120">使用同步用戶端通訊端</span><span class="sxs-lookup"><span data-stu-id="5bfd3-120">Using a Synchronous Client Socket</span></span>](using-a-synchronous-client-socket.md)
- [<span data-ttu-id="5bfd3-121">使用非同步用戶端通訊端</span><span class="sxs-lookup"><span data-stu-id="5bfd3-121">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="5bfd3-122">如何：建立通訊端</span><span class="sxs-lookup"><span data-stu-id="5bfd3-122">How to: Create a Socket</span></span>](how-to-create-a-socket.md)
- [<span data-ttu-id="5bfd3-123">通訊端</span><span class="sxs-lookup"><span data-stu-id="5bfd3-123">Sockets</span></span>](sockets.md)
