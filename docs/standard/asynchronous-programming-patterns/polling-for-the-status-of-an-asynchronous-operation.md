---
title: "Polling for the Status of an Asynchronous Operation | Microsoft Docs"
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
  - "asynchronous programming, status polling"
  - "polling asynchronous operation status"
  - "status information [.NET Framework], asynchronous operations"
ms.assetid: b541af31-dacb-4e20-8847-1b1ff7c35363
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# Polling for the Status of an Asynchronous Operation
可等待非同步作業結果，並同時執行其他工作的應用程式，不應該在作業完成之前封鎖等待。  請使用下列其中一個選項，在等待非同步作業完成時，繼續執行指令：  
  
-   請使用非同步作業的 **Begin** *OperationName* 方法所傳回之 <xref:System.IAsyncResult> 的 <xref:System.IAsyncResult.IsCompleted%2A> 屬性，判斷作業是否已完成。  這種方法稱為輪詢，本主題中將會加以示範。  
  
-   請使用 <xref:System.AsyncCallback> 委派，處理個別執行緒中非同步作業的結果。  如需進行這個方法的範例，請參閱[Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)。  
  
## 範例  
 下列程式碼範例會示範使用 <xref:System.Net.Dns> 類別中的非同步方法，以擷取使用者指定之電腦的網域名稱系統資訊。  這個範例會啟動非同步作業，然後會在作業完成之前在主控台列印句號 \("."\)。  請注意，**null** \(在 Visual Basic 中為 **Nothing**\) 會傳遞給 <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.AsyncCallback> 和 <xref:System.Object> 參數，因為在使用這個方法時，並不需要這些引數。  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## 請參閱  
 [Event\-based Asynchronous Pattern \(EAP\)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)   
 [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)