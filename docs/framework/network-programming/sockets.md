---
title: "通訊端 | Microsoft Docs"
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
  - "傳送資料，通訊端"
  - "資料要求，通訊端"
  - "Windows Sockets"
  - "通訊端，關於通訊端"
  - "通訊端類別，關於通訊端類別"
  - "通訊端"
  - "從網際網路要求資料，通訊端"
  - "網路，通訊端"
  - "接收資料，通訊端"
  - "通訊協定，通訊端"
  - "網際網路，通訊端"
ms.assetid: 10d22735-bd37-42c1-a2be-c1932f979a7d
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 6
---
# 通訊端
<xref:System.Net.Sockets> 命名空間包含 Windows Sockets 介面的 Managed 實作。  在 <xref:System.Net> 命名空間的其他網路存取類別來建置在通訊端的這個實作的頂端。  
  
 .NET Framework <xref:System.Net.Sockets.Socket> 類別是 Winsock32 提供服務的通訊端的 Managed 程式碼版本 API。  在許多情況下， **Socket** 類別方法封送處理資料到它們的原生 Win32 對應和管理所有必要的安全性檢查。  
  
 **Socket** 類別支援兩種基本模式，同步和非同步。  在同步模式中，要執行的函式的呼叫網路作業 \(例如和\) <xref:System.Net.Sockets.Socket.Send%2A><xref:System.Net.Sockets.Socket.Receive%2A>等候，直到作業在控制項完成之前傳回給呼叫程式。  以非同步模式，這些呼叫會立即傳回。  
  
## 請參閱  
 [如何：建立通訊端](../../../docs/framework/network-programming/how-to-create-a-socket.md)   
 [TCP\/UDP](../../../docs/framework/network-programming/tcp-udp.md)   
 [使用應用程式通訊協定](../../../docs/framework/network-programming/using-application-protocols.md)