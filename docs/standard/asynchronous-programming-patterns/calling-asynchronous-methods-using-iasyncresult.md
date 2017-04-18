---
title: "Calling Asynchronous Methods Using IAsyncResult | Microsoft Docs"
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
  - "waiting for asynchronous operations"
  - "asynchronous method calling"
  - "calling asynchronous methods"
  - "asynchronous programming, calling asynchronous methods"
  - "IAsyncResult interface, calling asynchronous methods"
  - "stopping asynchronous operations"
ms.assetid: 07fba116-045b-473c-a0b7-acdbeb49861f
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# Calling Asynchronous Methods Using IAsyncResult
.NET Framework 和協力廠商類別庫 \(Class Library\) 中的型別能夠提供方法，讓應用程式在繼續執行的同時，可以在主應用程式執行緒以外的執行緒中執行非同步作業。  下列章節描述並提供程式碼範例，以說明能夠呼叫使用 <xref:System.IAsyncResult> 設計模式之非同步方法的不同方式。  
  
-   [Blocking Application Execution by Ending an Async Operation](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
-   [Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
-   [Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
-   [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## 請參閱  
 [Event\-based Asynchronous Pattern \(EAP\)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)   
 [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)