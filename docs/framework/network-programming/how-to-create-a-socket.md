---
title: "如何：建立通訊端 | Microsoft Docs"
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
  - "應用程式通訊協定，通訊端"
  - "網路"
  - "傳送資料，通訊端"
  - "資料要求，通訊端"
  - "從網際網路要求資料，通訊端"
  - "通訊端類別，建立通訊端"
  - "網路資源"
  - "接收資料，通訊端"
  - "通訊協定，通訊端"
  - "網際網路，通訊端"
  - "通訊端，建立"
ms.assetid: c64a049c-5981-43bc-a2dc-1851473589c7
caps.latest.revision: 7
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 7
---
# 如何：建立通訊端
在您可以使用通訊端與遠端裝置目前通訊，必須初始化通訊端的通訊協定和網路位址資訊。  <xref:System.Net.Sockets.Socket> 類別的建構函式有指定通訊協定家族 \(Family\)、通訊端類型和通訊協定類型使用通訊端進行連接的參數。  
  
## 範例  
 下列範例會在以 TCP\/IP 網路可用於通訊的通訊端，例如網際網路。  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
  
```  
  
 若要使用 TCP、UDP 而不是，請變更通訊協定類型，如下列範例所示:  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
  
```  
  
 <xref:System.Net.Sockets.AddressFamily> 列舉型別指定 **Socket** 類別用於的標準通訊協定家族 \(Family\) 解析位址 \(例如， **AddressFamily.InterNetwork** 成員指定 IP 第 4 版通訊協定家族\)。  
  
 <xref:System.Net.Sockets.SocketType> 列舉型別指定通訊端類型 \(例如， **SocketType.Stream** 成員表示傳送和接收之資料的標準通訊端與流程控制\)。  
  
 <xref:System.Net.Sockets.ProtocolType> 列舉時所使用的網路通訊協定進行通訊。 **Socket** \(例如， **ProtocolType.Tcp** 指示使用 TCP 通訊端; **ProtocolType.Udp** 指示使用 UDP 通訊端\)。  
  
 在 **Socket** 建立之後，它會先與遠端端點的連接或從遠端裝置接收資料連接。  
  
## 請參閱  
 [使用用戶端通訊端](../../../docs/framework/network-programming/using-client-sockets.md)   
 [透過通訊端接聽](../../../docs/framework/network-programming/listening-with-sockets.md)