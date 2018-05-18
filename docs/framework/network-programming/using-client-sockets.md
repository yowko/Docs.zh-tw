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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 458e67861bfd40b69f7a6f756ddee8be433e9e2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="using-client-sockets"></a>使用用戶端通訊端
在透過 <xref:System.Net.Sockets.Socket> 起始交談之前，您必須先建立應用程式和遠端裝置之間的資料管道。 雖然有其他的網路位址系列和通訊協定存在，但此範例會示範如何建立遠端服務的 TCP/IP 連線。  
  
 TCP/IP 會使用網路位址和服務連接埠編號來唯一識別服務。 網路位址可識別網路上的特定裝置；連接埠編號則可識別該裝置上要連線的特定服務。 網路位址和服務連接埠的組合稱為端點，在 .NET Framework 中是以 <xref:System.Net.EndPoint> 類別表示。 每個支援的位址系列已定義 **EndPoin** 的子系；對於 IP 位址系列，此類別是 <xref:System.Net.IPEndPoint>。  
  
 <xref:System.Net.Dns> 類別會提供網域名稱服務給使用 TCP/IP 網際網路服務的應用程式。 <xref:System.Net.Dns.Resolve%2A> 方法會查詢 DNS 伺服器，以將使用者易記的網域名稱 (例如 "host.contoso.com") 對應到數字的網際網路位址 (例如 192.168.1.1)。 **Resolve** 會傳回 <xref:System.Net.IPHostEntry>，其中包含位址和所要求名稱之別名的清單。 在大部分情況下，您可以使用 <xref:System.Net.IPHostEntry.AddressList%2A> 陣列中傳回的第一個位址。 下列程式碼可取得包含伺服器 host.contoso.com 之 IP 位址的 <xref:System.Net.IPAddress>。  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 Internet Assigned Numbers Authority (Iana) 定義了通用服務的連接埠編號 (如需詳細資訊，請參閱 www.iana.org/assignments/port-numbers)。 其他服務的已登錄連接埠編號範圍可以是 1,024 到 65,535。 下列程式碼會合併 host.contoso.com 的 IP 位址與連接埠編號，以建立連線的遠端端點。  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 在判斷遠端裝置的位址並選擇要用於連線的連接埠之後，應用程式可以嘗試建立與遠端裝置的連線。 下列範例會使用現有 **IPEndPoint** 連線到遠端裝置，並捕捉任何擲回的例外狀況。  
  
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
  
## <a name="see-also"></a>請參閱  
 [使用同步用戶端通訊端](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)  
 [使用非同步用戶端通訊端](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [如何：建立通訊端](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
 [通訊端](../../../docs/framework/network-programming/sockets.md)
