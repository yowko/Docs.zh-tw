---
title: 使用同步伺服器通訊端
description: 此範例顯示 .NET Framework 中的同步伺服器通訊端，此通訊端會暫停應用程式，直到在通訊端上收到連接要求為止。
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
ms.openlocfilehash: 305feaa71304bef749f999a078b0b5f4fa7be3cc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278150"
---
# <a name="using-a-synchronous-server-socket"></a>使用同步伺服器通訊端

同步伺服器通訊端會暫停應用程式執行，直到在通訊端上收到連線要求為止。 同步伺服器通訊端不適用於大量使用網路以進行作業的應用程式，但它們可能適合簡單網路應用程式。  
  
 使用 <xref:System.Net.Sockets.Socket.Bind%2A> 和 <xref:System.Net.Sockets.Socket.Listen%2A> 方法設定 <xref:System.Net.Sockets.Socket> 以接聽端點之後，便已準備好使用 <xref:System.Net.Sockets.Socket.Accept%2A> 方法接受連入的連線要求。 應用程式會暫停，直到呼叫 **Accept** 方法收到連線要求為止。  
  
 收到連線要求時，**Accept** 會傳回與連線用戶端建立關聯的新 **Socket** 執行個體。 下列範例會從用戶端讀取資料、將它顯示在主控台中，然後將資料回應傳回給用戶端。 **通訊端** 不會指定任何訊息通訊協定，因此字串 " \<EOF> " 會標示訊息資料的結尾。 它假設名為 `listener` 的 **通訊端** 已初始化並繫結至端點。  
  
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
  
## <a name="see-also"></a>另請參閱

- [使用非同步伺服器通訊端](using-an-asynchronous-server-socket.md)
- [同步伺服器通訊端範例](synchronous-server-socket-example.md)
- [透過通訊端接聽](listening-with-sockets.md)
