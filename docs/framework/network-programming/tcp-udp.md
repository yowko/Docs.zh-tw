---
title: TCP-UDP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
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
caps.latest.revision: 8
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f067d24b59fbb5b49803605a625cef52d12fdbea
ms.contentlocale: zh-tw
ms.lasthandoff: 08/21/2017

---
# <a name="tcp-udp"></a>TCP-UDP
應用程式可以使用「傳輸控制通訊協定 (TCP)」和「使用者資料包通訊協定 (UDP)」服務，搭配 <xref:System.Net.Sockets.TcpClient>、<xref:System.Net.Sockets.TcpListener> 和 <xref:System.Net.Sockets.UdpClient> 類別。 這些通訊協定類別建立在 <xref:System.Net.Sockets.Socket?displayProperty=fullName> 類別之上，並負責傳送資料的細節。  
  
 通訊協定類別使用 **Socket** 類別的同步方法，以提供簡單且直接的網路服務存取，不需要維護狀態資訊或了解設定通訊協定特定通訊端的詳細資料等成本。 若要使用非同步 **Socket** 方法，您可以使用 <xref:System.Net.Sockets.NetworkStream> 類別所提供的非同步方法。 若要存取 **Socket** 類別中通訊協定類別未公開的功能，您必須使用 **Socket** 類別。  
  
 **TcpClient** 和 **TcpListener** 代表使用 **NetworkStream** 類別的網路。 您使用 <xref:System.Net.Sockets.TcpClient.GetStream%2A> 方法來傳回網路資料流，然後呼叫資料流的 <xref:System.Net.Sockets.NetworkStream.Read%2A> 和 <xref:System.Net.Sockets.NetworkStream.Write%2A> 方法。 **NetworkStream** 並未擁有通訊協定類別的基礎通訊端，因此關閉它並不會影響通訊端。  
  
 **UdpClient** 類別使用位元組陣列來保留 UDP 資料包。 您使用 <xref:System.Net.Sockets.UdpClient.Send%2A> 方法將資料傳送到網路，及使用 <xref:System.Net.Sockets.UdpClient.Receive%2A> 方法來接收連入的資料包。  
  
## <a name="see-also"></a>另請參閱  
 [使用 TCP 服務](../../../docs/framework/network-programming/using-tcp-services.md)   
 [使用 UDP 服務](../../../docs/framework/network-programming/using-udp-services.md)   
 [在網路上使用資料流](../../../docs/framework/network-programming/using-streams-on-the-network.md)   
 [使用非同步伺服器通訊端](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)   
 [使用非同步用戶端通訊端](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)   
 [使用應用程式通訊協定](../../../docs/framework/network-programming/using-application-protocols.md)

