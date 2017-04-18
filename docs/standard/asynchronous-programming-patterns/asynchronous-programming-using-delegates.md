---
title: "Asynchronous Programming Using Delegates | Microsoft Docs"
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
  - "BeginInvoke method"
  - "asynchronous programming, delegates"
  - "asynchronous delegates"
  - "calling synchronous methods in asynchronous manner"
  - "EndInvoke method"
  - "calling asynchronous methods"
  - "delegates [.NET Framework], asynchronous"
  - "synchronous calling in asynchronous manner"
ms.assetid: 38a345ca-6963-4436-9608-5c9defef9c64
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# Asynchronous Programming Using Delegates
委派 \(Delegate\) 可讓您以非同步方式呼叫同步方法。  同步呼叫委派時，`Invoke` 方法會在目前的執行緒上直接呼叫目標方法。  如果呼叫 `BeginInvoke` 方法，則 Common Language Runtime \(CLR\) 會將要求放進佇列，並立即傳回給呼叫端。  在執行緒集區的執行緒上，隨即以非同步方式呼叫目標方法。  送出要求的原始執行緒可與目標方法無限制地持續平行執行。  如果在 `BeginInvoke` 方法的呼叫中指定了回呼 \(Callback\) 方法，則當目標方法結束時，即會呼叫此回呼方法。  在此回呼方法中，`EndInvoke` 方法會取得傳回值和任何輸入\/輸出或僅能輸出的參數。  如果在呼叫 `BeginInvoke` 時未指定任何回呼方法，則可以從稱為 `BeginInvoke` 的執行緒呼叫 `EndInvoke`。  
  
> [!IMPORTANT]
>  編譯器 \(Compiler\) 應該使用使用者指定的委派簽章，搭配 `Invoke`、`BeginInvoke` 和 `EndInvoke` 方法來發出委派類別。  `BeginInvoke` 和 `EndInvoke` 方法應該裝飾為原生 \(Native\)。  因為這些方法被標記為原生，所以 CLR 在類別載入期間會自動提供實作。  載入器將確保它們不會被覆寫。  
  
## 在本節中  
 [Calling Synchronous Methods Asynchronously](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 討論如何使用委派以非同步方式呼叫一般方法，並提供簡單的程式碼範例，示範四種等待非同步呼叫傳回的方式。  
  
 [非同步委派程式設計範例](../Topic/Asynchronous%20Delegates%20Programming%20Sample.md)  
 以較為複雜的程式碼範例示範如何使用委派進行非同步呼叫，這範例會將一些數字因數分解。  
  
## 相關章節  
 [Event\-based Asynchronous Pattern \(EAP\)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 描述使用 .NET Framework 進行的非同步程式設計。  
  
## 請參閱  
 <xref:System.Delegate>