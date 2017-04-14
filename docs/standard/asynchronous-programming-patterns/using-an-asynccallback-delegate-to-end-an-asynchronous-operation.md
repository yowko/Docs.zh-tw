---
title: "Using an AsyncCallback Delegate to End an Asynchronous Operation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ending asynchronous operations"
  - "asynchronous programming, ending operations"
  - "AsyncCallback delegate"
  - "stopping asynchronous operations"
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# Using an AsyncCallback Delegate to End an Asynchronous Operation
可等待非同步作業結果，並同時執行其他工作的應用程式，不應該在作業完成之前封鎖等待。  請使用下列其中一個選項，在等待非同步作業完成時，繼續執行指令：  
  
-   請使用 <xref:System.AsyncCallback> 委派，處理個別執行緒中非同步作業的結果。  此主題中會示範這個方法。  
  
-   請使用非同步作業的 **Begin** *OperationName* 方法所傳回之 <xref:System.IAsyncResult> 的 <xref:System.IAsyncResult.IsCompleted%2A> 屬性，判斷作業是否已完成。  如需進行這個方法的範例，請參閱[Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md)。  
  
## 範例  
 下列程式碼範例會示範使用 <xref:System.Net.Dns> 類別中的非同步方法，以擷取使用者指定之電腦的網域名稱系統 \(DNS\) 資訊。  此範例會建立參考 `ProcessDnsInformation` 方法的 <xref:System.AsyncCallback> 委派。  這個方法會對 DNS 資訊的每個非同步要求都呼叫一次。  
  
 請注意，使用者指定的主機會傳遞到 <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object> 參數。  如需定義和使用更為複雜狀態物件的範例，請參閱[Using an AsyncCallback Delegate and State Object](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)。  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## 請參閱  
 [Event\-based Asynchronous Pattern \(EAP\)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)   
 [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)   
 [Calling Asynchronous Methods Using IAsyncResult](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)   
 [Using an AsyncCallback Delegate and State Object](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)