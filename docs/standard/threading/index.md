---
title: "Managed Threading | Microsoft Docs"
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
  - "threading [.NET Framework], about threading"
  - "managed threading"
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# Managed Threading
無論您開發的應用程式是要供具有一個或是多個處理器的電腦使用，您都會希望即使應用程式目前正在執行其他工作，還是能夠提供使用者最快速的回應互動。  使用多個執行緒是讓您達成這個目標的強大方法之一，這麼做能夠讓應用程式保持對使用者的回應性，同時又能在多個使用者事件之間，甚或是在使用者事件的發生期間使用處理器。  雖然本章節是簡介執行緒處理的基本概念，但主要還是針對 Managed 執行緒處理概念和使用 Managed 執行緒處理進行說明。  
  
> [!NOTE]
>  從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]起，多執行緒程式設計已透過下列項目而大幅簡化：<xref:System.Threading.Tasks.Parallel?displayProperty=fullName> 和 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 類別、[Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)、<xref:System.Collections.Concurrent?displayProperty=fullName> 命名空間中的新並行集合類別，以及根據工作概念 \(而非執行緒\) 而建立的新程式設計模型。  如需詳細資訊，請參閱 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)。  
  
## 在本節中  
 [Managed Threading Basics](../../../docs/standard/threading/managed-threading-basics.md)  
 提供 Managed 執行緒處理的概觀，並且討論何時使用多執行緒。  
  
 [Using Threads and Threading](../../../docs/standard/threading/using-threads-and-threading.md)  
 說明如何建立、開始、暫停、繼續和中止執行緒。  
  
 [Managed Threading Best Practices](../../../docs/standard/threading/managed-threading-best-practices.md)  
 討論同步處理的層級、如何避免死結 \(Deadlock\) 和競爭情形、單一處理器和多處理器電腦，以及其他執行緒處理的問題。  
  
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)  
 描述可以用於同步處理執行緒活動的 Managed 類別和在不同執行緒上存取的物件資料，並且提供執行緒集區執行緒的概觀。  
  
## 參考  
 <xref:System.Threading>  
 包含可使用及同步處理 Managed 執行緒的類別。  
  
 <xref:System.Collections.Concurrent>  
 包含可放心用於多執行緒的集合類別。  
  
 <xref:System.Threading.Tasks>  
 包含建立與排程並行處理工作的類別。  
  
## 相關章節  
 [應用程式定義域](../../../docs/framework/app-domains/application-domains.md)  
 提供應用程式定義域和 Common Language Infrastructure 如何使用它們的概觀。  
  
 [非同步檔案 I\/O](../../../docs/standard/io/非同步檔案-i-o.md)  
 描述非同步 I\/O 的效能利益和基本作業。  
  
 [Event\-based Asynchronous Pattern \(EAP\)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 提供非同步程式設計的概觀。  
  
 [Calling Synchronous Methods Asynchronously](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 說明如何使用委派的內建功能，在執行緒集區執行緒上呼叫方法。  
  
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)  
 說明平行程式設計程式庫，這些可以簡化應用程式中多個執行緒的用法。  
  
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 說明以平行方式執行查詢的系統，以善用多處理器。