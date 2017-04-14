---
title: "TCP/UDP | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "通訊協定，TCP/UDP"
  - "網路資源，TCP/UDP"
  - "傳送資料，TCP/UDP"
  - "TCP/UDP"
  - "TcpClient 類別，關於 TcpClient 類別"
  - "應用程式通訊協定，TCP/UDP"
  - "接收資料，TCP/UDP"
  - "TcpListener 類別，關於 TcpListener 類別"
  - "通訊端類別，關於通訊端類別"
  - "UDP"
  - "資料要求，TCP/UDP"
  - "從網際網路要求資料，TCP/UDP"
  - "網際網路，TCP/UDP"
ms.assetid: df29b4b0-49e8-4923-82b9-13150dfc40f5
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# TCP/UDP
應用程式可以使用傳輸控制通訊協定 \(TCP\) \(TCP\) 和使用者資料包通訊協定與 <xref:System.Net.Sockets.TcpClient>、 <xref:System.Net.Sockets.TcpListener>和 <xref:System.Net.Sockets.UdpClient> 類別 \(UDP\) 的服務。  這些通訊協定類別會建立在 <xref:System.Net.Sockets.Socket?displayProperty=fullName> 類別最上方並負責傳輸之資料的詳細資料。  
  
 通訊協定類別會使用類別的 **Socket** 同步方法提供對 Web 服務的簡單而直接的存取，而不需額外負荷維護狀態資訊或知悉設定通訊端通訊協定的特定詳細資料。  若要使用非同步 **Socket** 方法，您可以使用 <xref:System.Net.Sockets.NetworkStream> 類別所提供的非同步方法。  若要存取 **Socket** 的功能分類中公開由通訊協定類別，您必須使用 **Socket** 類別。  
  
 使用 **NetworkStream** 類別，**TcpClient** 和 **TcpListener** 表示網路。  您可以使用 <xref:System.Net.Sockets.TcpClient.GetStream%2A> 方法傳回網路資料流，然後呼叫將資料流的 <xref:System.Net.Sockets.NetworkStream.Read%2A> 和 <xref:System.Net.Sockets.NetworkStream.Write%2A> 方法。  **NetworkStream** 並未擁有通訊協定類別的基礎通訊端，因此，關閉它並不會影響通訊端。  
  
 **UdpClient** 類別使用位元組陣列保留 UDP 資料包。  您可以使用 <xref:System.Net.Sockets.UdpClient.Send%2A> 方法傳送資料至 Web 和 <xref:System.Net.Sockets.UdpClient.Receive%2A> 方法接收一個輸入資料包。  
  
## 請參閱  
 [使用 TCP 服務](../../../docs/framework/network-programming/using-tcp-services.md)   
 [使用 UDP 服務](../../../docs/framework/network-programming/using-udp-services.md)   
 [在網路上使用資料流](../../../docs/framework/network-programming/using-streams-on-the-network.md)   
 [使用非同步伺服器通訊端](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)   
 [使用非同步用戶端通訊端](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)   
 [使用應用程式通訊協定](../../../docs/framework/network-programming/using-application-protocols.md)