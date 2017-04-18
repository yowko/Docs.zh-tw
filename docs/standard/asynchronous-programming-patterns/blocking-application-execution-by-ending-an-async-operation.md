---
title: "Blocking Application Execution by Ending an Async Operation | Microsoft Docs"
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
  - "blocks, asynchronous operations"
  - "AsyncWaitHandle property"
  - "asynchronous programming, blocking applications"
  - "blocking application execution"
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Blocking Application Execution by Ending an Async Operation
無法在等候非同步作業的結果時繼續執行其他工作的應用程式必須封鎖，直到作業完成為止。  請使用下列其中一個選項，在等候非同步作業完成時，封鎖應用程式的主執行緒：  
  
-   呼叫非同步作業的 **End** *OperationName*方法。  此主題中會示範這個方法。  
  
-   請使用非同步作業的**Begin** *OperationName* 方法所傳回之 <xref:System.IAsyncResult> 的 <xref:System.IAsyncResult.AsyncWaitHandle%2A> 屬性。  如需進行這個方法的範例，請參閱[Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md)。  
  
 直到非同步作業完成之前，其使用 **End** *OperationName*方法來封鎖的應用程式，通常會先呼叫 **Begin** *OperationName* 方法，再執行不需要作業結果即可完成的所有工作，然後呼叫 **End** *OperationName*。  
  
## 範例  
 下列程式碼範例會示範使用 <xref:System.Net.Dns> 類別中的非同步方法，以擷取使用者指定之電腦的網域名稱系統資訊。  請注意，`null` \(在 Visual Basic 中為 `Nothing`\) 會傳遞給 <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` 和 `stateObject` 參數，因為在使用這個方法時，並不需要這些引數。  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## 請參閱  
 [Event\-based Asynchronous Pattern \(EAP\)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)   
 [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)