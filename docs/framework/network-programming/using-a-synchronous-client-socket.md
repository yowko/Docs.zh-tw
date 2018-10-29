---
title: 使用同步用戶端通訊端
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- synchronous client sockets
- Socket class, synchronous client sockets
- receiving data, sockets
- sockets, synchronous client sockets
- protocols, sockets
- Internet, sockets
- client sockets
ms.assetid: 945d00c6-7202-466c-9df9-140b84156d43
ms.openlocfilehash: 8036421f937385edbaefb8df4ee3915798084c64
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50192430"
---
# <a name="using-a-synchronous-client-socket"></a>使用同步用戶端通訊端
在網路作業完成時，同步用戶端通訊端會暫止應用程式。 同步通訊端不適用於大量使用網路以進行作業的應用程式，但它們可以啟用其他應用程式的網路服務簡單存取。  
  
 若要傳送資料，請傳遞位元組陣列給其中一個 <xref:System.Net.Sockets.Socket> 類別的資料傳送方法 (<xref:System.Net.Sockets.Socket.Send%2A> 和 <xref:System.Net.Sockets.Socket.SendTo%2A>)。 下列範例會使用 <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> 屬性將字串編碼成位元組陣列緩衝區，然後使用 **Send** 方法將緩衝區傳送給網路裝置。 **Send** 方法會傳回送給網路裝置的位元組數目。  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 **Send** 方法從緩衝區移除位元組，並將它們佇列到要傳送至網路裝置的網路介面。 網路介面可能不會立即傳送資料，但它終究會傳送，只要以 <xref:System.Net.Sockets.Socket.Shutdown%2A> 方法正常關閉連線。  
  
 若要從網路裝置接收資料，請傳遞緩衝區給其中一個 **Socket** 類別的資料接收方法 (<xref:System.Net.Sockets.Socket.Receive%2A> 和 <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>)。 同步通訊端會暫停應用程式，直到從網路收到位元組或通訊端關閉為止。 下列範例會從網路接收資料，再將它顯示在主控台上。 此範例假設來自網路的資料為 ASCII 編碼的文字。 **Receive** 方法會傳回從網路收到的位元組數目。  
  
```vb  
Dim bytes(1024) As Byte  
Dim bytesRec = s.Receive(bytes)  
Console.WriteLine("Echoed text = {0}", _  
    System.Text.Encoding.ASCII.GetString(bytes, 0, bytesRec))  
```  
  
```csharp  
byte[] bytes = new byte[1024];  
int bytesRec = s.Receive(bytes);  
Console.WriteLine("Echoed text = {0}",  
    System.Text.Encoding.ASCII.GetString(bytes, 0, bytesRec));  
```  
  
 當不再需要通訊端時，您需要藉由呼叫 <xref:System.Net.Sockets.Socket.Shutdown%2A> 方法，然後呼叫 **Close** 方法釋放它。 下列範例會釋放**通訊端**。 <xref:System.Net.Sockets.SocketShutdown> 列舉定義常數，表示傳送、接收或是兩者時，是否應該關閉通訊端。  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## <a name="see-also"></a>請參閱  
 [使用非同步用戶端通訊端](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [透過通訊端接聽](../../../docs/framework/network-programming/listening-with-sockets.md)  
 [同步用戶端通訊端範例](../../../docs/framework/network-programming/synchronous-client-socket-example.md)
