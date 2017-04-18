---
title: "Task Parallel Library (TPL) | Microsoft Docs"
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
  - ".NET, concurrency in"
  - ".NET, parallel programming in"
  - "Parallel Programming"
ms.assetid: b8f99f43-9104-45fd-9bff-385a20488a23
caps.latest.revision: 37
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 37
---
# Task Parallel Library (TPL)
工作平行程式庫 \(TPL\) 是 <xref:System.Threading?displayProperty=fullName> 和 <xref:System.Threading.Tasks?displayProperty=fullName> 命名空間中的一組公用類型和 API。  TPL 的目的是透過簡化將平行處理原則和並行加入至應用程式的流程，讓開發人員更有生產力。  TPL 可動態調整並行程度，最有效率地使用所有可用的處理器。  此外，TPL 還會處理工作分割、<xref:System.Threading.ThreadPool> 上執行緒的排程、取消支援、狀態管理和其他低階細節。  使用 TPL，可讓您發揮程式碼的最大效能，同時專注於程式所應完成的工作。  
  
 自 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 開始，TPL 是撰寫多執行緒和平行程式碼較好的方法。  但是，並非所有程式碼都適用於平行化作業；例如，如果迴圈只會在每個反覆項目執行少量工作，或是迴圈執行的反覆項目並不多，則平行化作業帶來的額外負荷可能會讓程式碼的執行速度變慢。  再者，就像任何多執行緒執行碼，平行化作業會使程式執行變得複雜。  雖然 TPL 可簡化多執行緒案例，但建議您應先了解執行緒處理的基本概念 \(例如鎖定、死結、競爭情況等\)，以有效使用 TPL。  
  
## 相關主題  
  
|||  
|-|-|  
|標題|描述|  
|[Data Parallelism](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)|說明如何建立平行 `for` 和 `foreach` 迴圈 \(在 Visual Basic 中為 `For` 和 `For Each`\)。|  
|[Task Parallelism](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)|說明如何使用 <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=fullName> \(以隱含方式\) 或直接使用 <xref:System.Threading.Tasks.Task> 物件 \(以明確方式\) 建立和執行工作。|  
|[資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)|說明如何使用 TPL 資料流程程式庫中的資料流程元件，以處理必須彼此通訊的多項作業，或是在資料可用時處理資料。|  
|[Using TPL with Other Asynchronous Patterns](../../../docs/standard/parallel-programming/using-tpl-with-other-asynchronous-patterns.md)|說明如何將 TPL 搭配 .NET 中的其他非同步模式使用|  
|[Potential Pitfalls in Data and Task Parallelism](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)|說明一些常見陷阱以及如何避免這些陷阱。|  
|[Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)|說明如何使用 LINQ 查詢達到資料平行處理原則。|  
|[Parallel Programming](../../../docs/standard/parallel-programming/index.md)|.NET 平行程式設計的最上層節點。|  
  
## 請參閱  
 [使用 .NET Framework 進行平行程式設計的範例](http://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)