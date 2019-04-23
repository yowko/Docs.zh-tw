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
ms.openlocfilehash: c3d5a7d6040038eb6d768815b1ae9e8ad45c5810
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59109950"
---
# <a name="listening-with-sockets"></a>透過通訊端接聽
接聽程式或伺服器通訊端會開啟網路的連接埠，等候用戶端連接到該連接埠。 雖然有其他的網路位址系列和通訊協定存在，但此範例會示範如何建立遠端服務的 TCP/IP 網路連線。  
  
 定義 TCP/IP 服務唯一位址的方式，是結合主機的 IP 位址與服務的連接埠號碼，建立服務的端點。 <xref:System.Net.Dns> 類別提供的方法，會傳回區域網路裝置支援的網路位址相關資訊。 當區域網路裝置有多個網路位址，或本機系統支援多部網路裝置時，**Dns** 類別會傳回所有網路位址的相關資訊，而應用程式必須選擇適當的服務位址。 Internet Assigned Numbers Authority (Iana) 定義了通用服務的連接埠編號。如需詳細資訊，請參閱 [服務名稱與傳輸通訊協定連接埠號碼登錄](https://www.iana.org/assignments/port-numbers)  其他服務的登錄連接埠號碼範圍可以是 1,024 到 65,535。  
  
 下列範例會結合主機電腦 **Dns** 傳回的第一個 IP 位址，和從已登錄連接埠號碼範圍中選擇的連接埠號碼，為伺服器建立 <xref:System.Net.IPEndPoint>。  
  
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
  
 決定本機端點之後，<xref:System.Net.Sockets.Socket> 必須使用 <xref:System.Net.Sockets.Socket.Bind%2A> 方法建立與該端點的關聯，並使用 <xref:System.Net.Sockets.Socket.Listen%2A> 方法設定接聽端點。 如已使用特定位址和連接埠的組合，**Bind** 會擲回例外狀況。 下列範例會示範建立**通訊端**與 **IPEndPoint** 的關聯。  
  
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
  
 **Listen** 方法會採用單一參數，指定在伺服器忙碌錯誤傳回至連線的用戶端之前，允許的**通訊端**暫止連線數目。 在本例中，在伺服器忙碌回應傳回至用戶端編號 101 之前，連線佇列中最多放置 100 個用戶端。  
  
## <a name="see-also"></a>另請參閱

- [使用同步伺服器通訊端](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)
- [使用非同步伺服器通訊端](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)
- [使用用戶端通訊端](../../../docs/framework/network-programming/using-client-sockets.md)
- [如何：建立通訊端](../../../docs/framework/network-programming/how-to-create-a-socket.md)
- [通訊端](../../../docs/framework/network-programming/sockets.md)
