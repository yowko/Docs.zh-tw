---
title: 使用同步伺服器通訊端
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- synchronous server sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- server sockets
- receiving data, sockets
- Socket class, synchronous server sockets
- protocols, sockets
- sockets, synchronous server sockets
- Internet, sockets
ms.assetid: d1ce882e-653e-41f5-9289-844ec855b804
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 2e79c9a75e4513be91af1104195af3614b49092d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2018
ms.locfileid: "47398546"
---
# <a name="using-a-synchronous-server-socket"></a><span data-ttu-id="f23b1-102">使用同步伺服器通訊端</span><span class="sxs-lookup"><span data-stu-id="f23b1-102">Using a Synchronous Server Socket</span></span>
<span data-ttu-id="f23b1-103">同步伺服器通訊端會暫停應用程式執行，直到在通訊端上收到連線要求為止。</span><span class="sxs-lookup"><span data-stu-id="f23b1-103">Synchronous server sockets suspend the execution of the application until a connection request is received on the socket.</span></span> <span data-ttu-id="f23b1-104">同步伺服器通訊端不適用於大量使用網路以進行作業的應用程式，但它們可能適合簡單網路應用程式。</span><span class="sxs-lookup"><span data-stu-id="f23b1-104">Synchronous server sockets are not suitable for applications that make heavy use of the network in their operation, but they can be suitable for simple network applications.</span></span>  
  
 <span data-ttu-id="f23b1-105">使用 <xref:System.Net.Sockets.Socket.Bind%2A> 和 <xref:System.Net.Sockets.Socket.Listen%2A> 方法設定 <xref:System.Net.Sockets.Socket> 以接聽端點之後，便已準備好使用 <xref:System.Net.Sockets.Socket.Accept%2A> 方法接受連入的連線要求。</span><span class="sxs-lookup"><span data-stu-id="f23b1-105">After a <xref:System.Net.Sockets.Socket> is set to listen on an endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> and <xref:System.Net.Sockets.Socket.Listen%2A> methods, it is ready to accept incoming connection requests using the <xref:System.Net.Sockets.Socket.Accept%2A> method.</span></span> <span data-ttu-id="f23b1-106">應用程式會暫停，直到呼叫 **Accept** 方法收到連線要求為止。</span><span class="sxs-lookup"><span data-stu-id="f23b1-106">The application is suspended until a connection request is received when the **Accept** method is called.</span></span>  
  
 <span data-ttu-id="f23b1-107">收到連線要求時，**Accept** 會傳回與連線用戶端建立關聯的新 **Socket** 執行個體。</span><span class="sxs-lookup"><span data-stu-id="f23b1-107">When a connection request is received, **Accept** returns a new **Socket** instance that is associated with the connecting client.</span></span> <span data-ttu-id="f23b1-108">下列範例會從用戶端讀取資料、將它顯示在主控台中，然後將資料回應傳回給用戶端。</span><span class="sxs-lookup"><span data-stu-id="f23b1-108">The following example reads data from the client, displays it on the console, and echoes the data back to the client.</span></span> <span data-ttu-id="f23b1-109">**Socket** 未指定任何傳訊通訊協定，因此字串 "\<EOF>" 會標記訊息資料的結束。</span><span class="sxs-lookup"><span data-stu-id="f23b1-109">The **Socket** does not specify any messaging protocol, so the string "\<EOF>" marks the end of the message data.</span></span> <span data-ttu-id="f23b1-110">它假設名為 `listener` 的**通訊端**已初始化並繫結至端點。</span><span class="sxs-lookup"><span data-stu-id="f23b1-110">It assumes that a **Socket** named `listener` has been initialized and bound to an endpoint.</span></span>  
  
```vb  
Console.WriteLine("Waiting for a connection...")  
Dim handler As Socket = listener.Accept()  
Dim data As String = Nothing  
  
While True  
    bytes = New Byte(1024) {}  
    Dim bytesRec As Integer = handler.Receive(bytes)  
    data += Encoding.ASCII.GetString(bytes, 0, bytesRec)  
    If data.IndexOf("<EOF>") > - 1 Then  
        Exit While  
    End If  
End While  
  
Console.WriteLine("Text received : {0}", data)  
  
Dim msg As Byte() = Encoding.ASCII.GetBytes(data)  
handler.Send(msg)  
handler.Shutdown(SocketShutdown.Both)  
handler.Close()  
```  
  
```csharp  
Console.WriteLine("Waiting for a connection...");  
Socket handler = listener.Accept();  
String data = null;  
  
while (true) {  
    bytes = new byte[1024];  
    int bytesRec = handler.Receive(bytes);  
    data += Encoding.ASCII.GetString(bytes,0,bytesRec);  
    if (data.IndexOf("<EOF>") > -1) {  
        break;  
    }  
}  
  
Console.WriteLine( "Text received : {0}", data);  
  
byte[] msg = Encoding.ASCII.GetBytes(data);  
handler.Send(msg);  
handler.Shutdown(SocketShutdown.Both);  
handler.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="f23b1-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="f23b1-111">See Also</span></span>  
 [<span data-ttu-id="f23b1-112">使用非同步伺服器通訊端</span><span class="sxs-lookup"><span data-stu-id="f23b1-112">Using an Asynchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [<span data-ttu-id="f23b1-113">同步伺服器通訊端範例</span><span class="sxs-lookup"><span data-stu-id="f23b1-113">Synchronous Server Socket Example</span></span>](../../../docs/framework/network-programming/synchronous-server-socket-example.md)  
 [<span data-ttu-id="f23b1-114">透過通訊端接聽</span><span class="sxs-lookup"><span data-stu-id="f23b1-114">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)
