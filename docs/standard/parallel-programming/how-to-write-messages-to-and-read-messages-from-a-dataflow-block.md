---
title: "How to: Write Messages to and Read Messages from a Dataflow Block | Microsoft Docs"
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
  - "Task Parallel Library, dataflows"
  - "TPL dataflow library, reading and writing messages"
ms.assetid: 1a9bf078-aa82-46eb-b95a-f87237f028c5
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# How to: Write Messages to and Read Messages from a Dataflow Block
本文件說明如何使用 TPL 資料流程式庫寫入訊息至和讀取資料流程區塊的訊息。  TPL 資料流程式庫為寫入訊息至和讀取資料流程區塊的訊息提供同步和非同步方法。  本文件使用 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=fullName> 類別。  <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 類別緩衝訊息並做為訊息來源和訊息的目標。  
  
> [!TIP]
>  TPL 資料流程式庫 \(<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName> 命名空間\) 並沒有和 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 配置在一起。  若要安裝 <xref:System.Threading.Tasks.Dataflow> 命名空間，請在 [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] 中開啟您的專案，從 \[專案\] 功能表中選擇 \[**管理 NuGet 封裝**\]，並且線上搜尋 `Microsoft.Tpl.Dataflow` 封裝。  
  
## 同步寫入和讀取資料流程區塊。  
 下列範例會使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> 方法來讀取相同物件的 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 資料流程區塊和 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> 方法寫入。  
  
 [!code-csharp[TPLDataflow_ReadWrite#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#2)]
 [!code-vb[TPLDataflow_ReadWrite#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#2)]  
  
 如下列範例所示，您也可以使用 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> 方法從資料流程區塊，讀取。  當您為資料時，有時候會輪詢 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> 方法不會封鎖目前的執行緒也很有用。  
  
 [!code-csharp[TPLDataflow_ReadWrite#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#3)]
 [!code-vb[TPLDataflow_ReadWrite#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#3)]  
  
 因為 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> 方法同步動作，在第二個迴圈讀取資料前上述範例的 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 物件接收所有資料。  下列範例會擴充第一個範例使用 <xref:System.Threading.Tasks.Parallel.Invoke%2A> 讀取和寫入訊息區塊同時寫入。  由於 <xref:System.Threading.Tasks.Parallel.Invoke%2A> 同時執行動作，值給 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 物件不會被覆寫以任何特定的順序。  
  
 [!code-csharp[TPLDataflow_ReadWrite#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#4)]
 [!code-vb[TPLDataflow_ReadWrite#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#4)]  
  
## 非同步寫入和讀取資料流程區塊。  
 下列範例會使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> 方法非同步給非同步讀取相同物件的 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 物件和 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> 方法寫入。  這個範例會使用 [非同步](../Topic/async%20\(C%23%20Reference\).md) 和 [等候](../Topic/await%20\(C%23%20Reference\).md) 運算子 \([Async](../Topic/Async%20\(Visual%20Basic\).md) 和 [等候](../Topic/Await%20Operator%20\(Visual%20Basic\).md) 在 Visual Basic 中為\) 以非同步方式傳送與讀取資料從目標區塊。  當您必須使資料流程區塊延後訊息時， <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> 方法會很有用。  <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> 方法會很有用，當您在資料可用時要對起作用。  如需 SOAP 訊息的詳細資訊在訊息區塊中傳送，請參閱 [資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)中的部分訊息傳遞。  
  
 [!code-csharp[TPLDataflow_ReadWrite#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#5)]
 [!code-vb[TPLDataflow_ReadWrite#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#5)]  
  
## 一個完整範例  
 下列範例顯示此文件的完整程式碼。  
  
 [!code-csharp[TPLDataflow_ReadWrite#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#1)]
 [!code-vb[TPLDataflow_ReadWrite#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#1)]  
  
## 編譯程式碼  
 請複製範例程式碼並將它貼在 Visual Studio 專案中，或是貼在名為  `DataflowReadWrite.cs`的檔案中 \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 的 `DataflowReadWrite.vb` \) ，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.vb**  
  
## 後續步驟  
 這個範例顯示如何讀取和寫入訊息區塊直接寫入。  您也可以連接資料流程區塊組成資料流程區塊線性序列： *管線*，或是資料流程區塊圖表：*網路*。  在管線或網路中，當資料可供使用時，來源非同步傳送資料至目標。  如需建立基本的資料流程管線的範例，請參閱 [Walkthrough: Creating a Dataflow Pipeline](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md)。  如需建立更複雜的資料流程網路的範例，請參閱 [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)。  
  
## 請參閱  
 [資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)