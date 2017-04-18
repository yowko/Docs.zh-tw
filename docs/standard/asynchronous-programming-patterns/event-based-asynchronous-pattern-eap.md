---
title: "Event-based Asynchronous Pattern (EAP) | Microsoft Docs"
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
  - "asynchronous calls"
  - "asynchronous programming, design patterns"
  - "asynchronous programming"
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
caps.latest.revision: 20
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 20
---
# Event-based Asynchronous Pattern (EAP)
將非同步功能公開到用戶端程式碼的方式有許多種；  事件架構非同步模式會針對要呈現非同步行為之類別指示一個方法。  
  
> [!NOTE]
>  從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 開始，工作平行程式庫會為非同步處理和平行程式設計提供新的模型。  如需詳細資訊，請參閱[Parallel Programming](../../../docs/standard/parallel-programming/index.md)。  
  
## 在本節中  
 [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 描述事件架構非同步模式如何提供多執行緒應用程式的優點，同時隱藏多執行緒設計中許多原有的複雜問題。  
  
 [Implementing the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 描述將具有非同步功能的類別封裝起來的標準化方式。  
  
 [實作事件架構非同步模式的最佳作法](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 描述根據事件架構非同步模式來公開非同步功能的需求。  
  
 [Deciding When to Implement the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 描述如何判斷何時應該選擇實作事件架構非同步模式，而不是 <xref:System.IAsyncResult> 模式。  
  
 [Walkthrough: Implementing a Component That Supports the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 說明如何建立實作事件架構非同步模式的元件。  其實作方式是使用 <xref:System.ComponentModel?displayProperty=fullName> 命名空間中的 Helper 類別，以確保此元件可在任何應用程式模型下正常運作。  
  
 [How to: Use Components That Support the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 描述如何使用可支援事件架構非同步模式的元件。  
  
## 參考  
 <xref:System.ComponentModel.AsyncOperation>  
 描述 <xref:System.ComponentModel.AsyncOperation> 類別並且連結到它所有的成員。  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 描述 <xref:System.ComponentModel.AsyncOperationManager> 類別並且連結到它所有的成員。  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 描述 <xref:System.ComponentModel.BackgroundWorker> 元件並且連結到它所有的成員。  
  
## 相關章節  
 [Task Parallel Library \(TPL\)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 描述非同步處理和平行作業的程式設計模型。  
  
 [Threading](../../../docs/standard/threading/index.md)  
 說明在 .NET Framework 的多執行緒處理功能。  
  
 [執行緒](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md)  
 說明 C\# 和 Visual Basic 語言的多執行緒處理功能。  
  
## 請參閱  
 [Managed Threading Best Practices](../../../docs/standard/threading/managed-threading-best-practices.md)   
 [事件](../../../docs/standard/events/index.md)   
 [元件中的多執行緒](../Topic/Multithreading%20in%20Components.md)   
 [Asynchronous Programming Design Patterns](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)