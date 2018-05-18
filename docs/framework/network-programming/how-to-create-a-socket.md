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
manager: markl
ms.openlocfilehash: 600ea82965c332c8620db689abb50965f15f0067
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-socket"></a>如何：建立通訊端
在您使用通訊端與遠端裝置進行通訊之前，必須先使用通訊協定和網路位址資訊初始化通訊端。 <xref:System.Net.Sockets.Socket> 類別的建構函式所擁有的參數，可指定通訊端用來建立連線的位址家族、通訊端類型和通訊協定類型。  
  
## <a name="example"></a>範例  
 下列範例會建立可在 TCP/IP 網路 (例如網際網路) 上用於通訊的通訊端。  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 若要使用 UDP 而不是 TCP，請變更通訊協定類型，如下列範例所示：  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <xref:System.Net.Sockets.AddressFamily> 列舉會指定 **Socket** 用來解析網路位址的標準位址系列 (例如，**AddressFamily.InterNetwork** 成員指定 IP 第 4 版位址系列)。  
  
 <xref:System.Net.Sockets.SocketType> 列舉會指定通訊端類型 (例如，**SocketType.Stream** 成員指出使用流量控制傳送和接收資料的標準通訊端)。  
  
 <xref:System.Net.Sockets.ProtocolType> 列舉會指定在 **Socket** 上進行通訊時，要使用的網路通訊協定 (例如，**ProtocolType.Tcp** 指出通訊端會使用 TCP；**ProtocolType.Udp** 則指出通訊端會使用 UDP)。  
  
 建立 **Socket** 之後，它可以初始化與遠端端點的連線或接收來自遠端裝置的連線。  
  
## <a name="see-also"></a>請參閱  
 [使用用戶端通訊端](../../../docs/framework/network-programming/using-client-sockets.md)  
 [透過通訊端接聽](../../../docs/framework/network-programming/listening-with-sockets.md)
