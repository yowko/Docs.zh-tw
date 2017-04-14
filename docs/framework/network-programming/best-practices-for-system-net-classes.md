---
title: "System.Net 類別的最佳作法 | Microsoft Docs"
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
  - "傳送資料，最佳作法"
  - "從網際網路要求資料，最佳作法"
  - "WebRequest 類別，最佳作法"
  - "資料要求，最佳作法"
  - "WebResponse 類別，最佳作法"
  - "最佳作法，資料要求"
  - "接收資料，最佳作法"
ms.assetid: 716decc6-5952-47b7-9c5a-ba6fc5698684
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# System.Net 類別的最佳作法
下列建議將協助您在 <xref:System.Net> 包含的類別為其最佳優點:  
  
-   使用 <xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse> 盡可能而不是將轉型為子代類別的型別。  使用 **WebRequest** 和 **WebResponse** 的應用程式可以使用新的網際網路通訊協定，而不需要大量程式碼變更。  
  
-   使用 **System.Net** 類別時，在撰寫在伺服器上執行的 ASP.NET 應用程式中，從效能的觀點來看，通常是良好，為 <xref:System.Net.WebRequest.GetResponse%2A> 和 <xref:System.Net.WebResponse.GetResponseStream%2A>使用非同步方法。  
  
-   開啟的連接數目與網際網路資源可能會對網路效能和產能有顯著的影響。  根據預設**System.Net** 使用每個應用程式的兩種連結至每一個主機。  設定 <xref:System.Net.ServicePoint> 的 <xref:System.Net.ServicePoint.ConnectionLimit%2A> 屬性應用程式可以針對特定主機數字遞增。  設定 <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=fullName> 屬性會為所有主機加入這個預設值。  
  
-   在寫入通訊端層級通訊協定，嘗試使用 [TCPClient](frlrfsystemnetsocketstcpclientclasstopic) 或 [UDPClient](frlrfsystemnetsocketsudpclientclasstopic) 盡可能 \(而不是直接寫入至 <xref:System.Net.Sockets.Socket>。  這兩個用戶端類別會封裝 TCP 和 UDP 通訊端的建立，而不需要您自行管理連接的細節。  
  
-   在存取時需要認證的網站，使用 <xref:System.Net.CredentialCache> 類別建立快取認證而不是提供給它們對每個要求。  **CredentialCache** 類別搜尋快取尋找適合的認證以要求，釋放您建立並將根據 URL 的認證的責任。  
  
## 請參閱  
 [以 .NET Framework 進行網路程式設計](../../../docs/framework/network-programming/index.md)