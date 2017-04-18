---
title: "How to: Perform Action When a Dataflow Block Receives Data | Microsoft Docs"
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
  - "TPL dataflow library, receiving data"
ms.assetid: fc2585dc-965e-4632-ace7-73dd02684ed3
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# How to: Perform Action When a Dataflow Block Receives Data
會在收到資料時，*執行資料流程區塊* 型別呼叫使用者提供的委派。  <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=fullName>、 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=fullName>和 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=fullName> 類別是執行資料流程區塊型別。  您可以使用 `delegate` 關鍵字 \(在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]中為`Sub` \)， <xref:System.Action%601>、 <xref:System.Func%602>或 Lambda 運算式，因為您提供給工作函式執行資料流程區塊時。  文件在執行區塊說明如何使用 <xref:System.Func%602> 和 Lambda 運算式來執行動作。  
  
> [!TIP]
>  TPL 資料流程式庫 \(<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName> 命名空間\) 並沒有和 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 配置在一起。  若要安裝 <xref:System.Threading.Tasks.Dataflow> 命名空間，請在 [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] 中開啟您的專案，從 \[專案\] 功能表中選擇 \[**管理 NuGet 封裝**\]，並且線上搜尋 `Microsoft.Tpl.Dataflow` 封裝。  
  
## 範例  
 下列範例使用資料流讀取檔案從磁碟並計算等於零的位元組數。在該檔案中。  它會使用 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> 讀取檔案和計算零位元組數目和 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 列印零位元組數目寫入主控台。  當區塊接收資料時， <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> 物件指定要執行工作的 <xref:System.Func%602> 物件。  <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件使用 Lambda 運算式列印到主控台讀取零位元組數目。  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#1)]
 [!code-vb[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#1)]  
  
 雖然您可以提供 Lambda 運算式給 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> 物件，這個範例會使用 <xref:System.Func%602> 可讓其他程式碼使用 `CountBytes` 方法。  因為工作會執行特定於這項工作並不能是有用的其他程式碼， <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件使用 Lambda 運算式。  如需 Lambda 運算式的方式提供較多有關工作平行程式庫中運作，請參閱 [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)。  
  
 委派部分抽象型別 [資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) 文件摘要說明您可以提供給 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>、 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>和 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> 物件的委派型別。  這個資料表也指定委派型別同步運作或非同步運作。  
  
## 編譯程式碼  
 請複製範例程式碼並將它貼在 Visual Studio 專案中，或是貼在名為  `DataflowExecutionBlocks.cs`的檔案中 \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 的 `DataflowExecutionBlocks.vb` \) ，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowExecutionBlocks.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowExecutionBlocks.vb**  
  
## 穩固程式設計  
 這個範例提供 <xref:System.Func%602> 型別的委派給 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> 物件同步執行資料流程區塊的工作。  若要讓資料流程區塊的行為非同步，請提供 <xref:System.Func%601> 型別的委派給資料流程區塊。  當資料流程區塊非同步行為時，資料流程區塊的工作完成，只有在傳回的 <xref:System.Threading.Tasks.Task%601> 物件完成時。  下列範例會修改 `CountBytes` 方法並使用 [非同步](../Topic/async%20\(C%23%20Reference\).md) ，而 \([Async](../Topic/Async%20\(Visual%20Basic\).md) 和 [等候](../Topic/Await%20Operator%20\(Visual%20Basic\).md) 在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]\) 非同步計算是的總位元組數的 [等候](../Topic/await%20\(C%23%20Reference\).md) 運算子右邊的參數為提供的檔案。  <xref:System.IO.FileStream.ReadAsync%2A> 方法會執行的非同步讀取作業。  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#2)]
 [!code-vb[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#2)]  
  
 您在執行資料流程區塊也可以使用非同步 Lambda 運算式來執行動作。  下列範例修改所使用的 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> 物件，讓它使用 Lambda 運算式執行非同步工作。  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#3)]
 [!code-vb[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#3)]  
  
## 請參閱  
 [資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)