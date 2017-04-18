---
title: "How to: Implement a Producer-Consumer Dataflow Pattern | Microsoft Docs"
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
  - "TPL dataflow library, implementing producer-consumer pattern"
  - "Task Parallel Library, dataflows"
  - "producer-consumer patterns, implementing [TPL]"
ms.assetid: 47a1d38c-fe9c-44aa-bd15-937bd5659b0b
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# How to: Implement a Producer-Consumer Dataflow Pattern
本文件說明如何使用 TPL 資料流程式庫實作生產者 \- 消費者模式。  在這個模式中，「*生產者*」\(Producer\) 會傳送訊息至訊息區塊，而「*消費者*」\(Consumer\) 則會從該區塊讀取訊息。  
  
> [!TIP]
>  TPL 資料流程式庫 \(<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName> 命名空間\) 並沒有和 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 配置在一起。  若要安裝 <xref:System.Threading.Tasks.Dataflow> 命名空間，請在 [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] 中開啟您的專案，從 \[專案\] 功能表中選擇 \[**管理 NuGet 封裝**\]，並且線上搜尋 `Microsoft.Tpl.Dataflow` 封裝。  
  
## 範例  
 下列範例示範如何使用資料流中的生產者\-消費者模式。  `Produce` 方法會寫入包含隨機位元組資料至 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=fullName> 物件， `Consume` 方法會從 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=fullName> 物件的位元組陣列。  將扮演 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> 和 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> 介面，而不是其衍生的型別，您可以撰寫在各種資料流程區塊類型運作的可重複使用的程式碼。  這個範例會使用 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 類別。  由於 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 類別做為來源區塊，因此當目標區塊、生產者和消費者可以使用的傳輸資料的共用物件。  
  
 `Produce` 方法在迴圈中呼叫 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> 方法給目標區塊同步寫入資料。  在 `Produce` 方法給目標區塊後將任何資料，它會呼叫 <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> 方法指示區塊永遠不會有不同的可用資料。  `Consume` 方法會使用 [非同步](../Topic/async%20\(C%23%20Reference\).md) 和 [等候](../Topic/await%20\(C%23%20Reference\).md) 運算子 \([Async](../Topic/Async%20\(Visual%20Basic\).md) 和 [等候](../Topic/Await%20Operator%20\(Visual%20Basic\).md) 在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]\) 非同步計算從 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> 物件接收的位元組總數。  若要執行非同步作業， `Consume` 方法會呼叫 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> 方法時接收通知，當來源區塊有可用的資料，還有當來源區塊永遠不會有不同的可用資料。  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## 編譯程式碼  
 請複製範例程式碼並將它貼在 Visual Studio 專案中，或是貼在名為  `DataflowProducerConsumer.cs`的檔案中 \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 的 `DataflowProducerConsumer.vb` \) ，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.vb**  
  
## 穩固程式設計  
 這個範例會使用單一消費者處理來源資料。  如果您有多個消費者在應用程式中，如下列範例所示，請使用 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> 方法會從來源區塊的資料。  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 當沒有資料是可用時，<xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> 方法回傳 `False` 。  當多個消費者必須同時存取來源區塊，這個機制來確保資料在呼叫之後可供 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>。  
  
## 請參閱  
 [資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)