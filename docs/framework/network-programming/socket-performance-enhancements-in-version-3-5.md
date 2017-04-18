---
title: "3.5 版中的通訊端效能增強功能 | Microsoft Docs"
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
ms.assetid: 225aa5f9-c54b-4620-ab64-5cd100cfd54c
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# 3.5 版中的通訊端效能增強功能
<xref:System.Net.Sockets.Socket?displayProperty=fullName> 類別在 3.5 版中已針對使用非同步網路 I\/O 以達到最高效能的應用程式使用。  一系列新增類別做為提供另一種非同步模式可由特定高效能通訊端應用程式使用的增強功能集合的一部分。 <xref:System.Net.Sockets.Socket> 類別。  這些增強功能是特別針對需要高效能的網路伺服器應用程式所設計。  應用程式在其應用程式做為目標的高活動區域可以完全只使用增強型非同步模式或 \(例如在接收大量資料時\)，  
  
## 類別增強功能  
 這些增強功能的主要特色，是能夠在大量非同步通訊端 I\/O 期間，避免不斷重複配置和同步處理物件。  非同步通訊端 I\/O 的 <xref:System.Net.Sockets.Socket> 目前由類別實作的 Begin\/End 設計模式需要 <xref:System.IAsyncResult?displayProperty=fullName> 物件為每個非同步通訊端作業所配置。  
  
 在新的 <xref:System.Net.Sockets.Socket> 類別增強功能，非同步通訊端作業是由可重複使用的 <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=fullName> 類別所描述的物件配置和維護應用程式。  高效能通訊端應用程式最了解必須維持的重疊通訊端作業量。  應用程式可以視需要，建立不限數目的 <xref:System.Net.Sockets.SocketAsyncEventArgs> 物件。  例如，在中，如果伺服器應用程式需要有 15 的通訊端接受作業未完成的支援連入用戶端連接速率，它可以預先配置 15 可重複使用的物件 <xref:System.Net.Sockets.SocketAsyncEventArgs> 該目的。  
  
 使用這個類別以執行非同步通訊端作業的模式，包含下列步驟：  
  
1.  配置新的 <xref:System.Net.Sockets.SocketAsyncEventArgs> 內容物件，或從應用程式集區取得可使用的物件。  
  
2.  將內容物件上的屬性設定為要執行的作業 \(例如回呼委派方法和資料緩衝區，所以\)。  
  
3.  呼叫適當的通訊端方法 \(xxxAsync\) 以初始化非同步作業。  
  
4.  如果非同步通訊端方法 \(xxxAsync\) 傳回 true 回呼，在查詢完成狀態的內容屬性。  
  
5.  如果非同步通訊端方法 \(xxxAsync\) 傳回錯誤，在回呼同步完成的作業。  您可以查詢內容屬性以取得作業結果。  
  
6.  將內容重複使用於其他作業、放回集區或捨棄內容。  
  
 新的非同步通訊端作業內容物件的存留期是由應用程式程式碼和非同步 I\/O 參考的參考。  在非同步通訊端作業內容物件的參考做為參數傳送至其中一個非同步通訊端作業方法後，應用程式不需要保留此物件的參考。  它會一直被參考直到完成回呼傳回為止。  不過有用處針對應用程式保留內容物件的參考，以便針對未來的非同步通訊端作業重複使用。  
  
## 請參閱  
 <xref:System.Net.Sockets.Socket?displayProperty=fullName>   
 <xref:System.Net.Sockets.SendPacketsElement?displayProperty=fullName>   
 <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=fullName>   
 <xref:System.Net.Sockets.SocketAsyncOperation?displayProperty=fullName>   
 [網路程式設計範例](../../../docs/framework/network-programming/network-programming-samples.md)   
 [Socket 效能技術範例](http://go.microsoft.com/fwlink/?LinkID=179570)