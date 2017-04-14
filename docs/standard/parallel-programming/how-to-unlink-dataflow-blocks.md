---
title: "How to: Unlink Dataflow Blocks | Microsoft Docs"
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
  - "dataflow blocks, unlinking in TPL"
  - "Task Parallel Library, dataflows"
  - "TPL dataflow library, unlinking dataflow blocks"
ms.assetid: 40f0208d-4618-47f7-85cf-4913d07d2d7d
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# How to: Unlink Dataflow Blocks
本文件說明如何取消來源其來源的目標資料流程區塊。  
  
> [!TIP]
>  TPL 資料流程式庫 \(<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName> 命名空間\) 並沒有和 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 配置在一起。  若要安裝 <xref:System.Threading.Tasks.Dataflow> 命名空間，請在 [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] 中開啟您的專案，從 \[專案\] 功能表中選擇 \[**管理 NuGet 封裝**\]，並且線上搜尋 `Microsoft.Tpl.Dataflow` 封裝。  
  
## 範例  
 下列範例會建立一個 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> 物件的陣列，每個呼叫 `TrySolution` 方法來計算值。  這個範例要求從第一次呼叫的結果為 `TrySolution` 完成。  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 要接收從第一個 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> 值會結束，此範例會定義 `ReceiveFromAny(T)` 方法。  `ReceiveFromAny(T)` 方法會接受 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> 物件的陣列並連接到 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> 物件的每一個物件。  當您使用 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> 方法與目標區塊時連結來源資料流程區塊，當資料可供使用時，來源傳播訊息到目標。  由於 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> 類別只接受第一個訊息提供它， `ReceiveFromAny(T)` 方法會呼叫 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> 方法來產生其結果。  這會導致為 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> 物件提供的第一個訊息。  <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> 方法會採用 <xref:System.Boolean> 參數之的多載版本，則為 `unlinkAfterOne` ，則設定為 `True`時，在目標接收來自來源之後的訊息時，指示來源區塊從目標回溯。  會從來源 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> 物件很重要，因為<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> 物件收到訊息之後，不再需要來源和 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> 物件之間的關聯性 。  
  
 讓剩餘的呼叫加入至 `TrySolution` 結尾，在其中一個計算值， 在對 `ReceiveFromAny(T)` 的呼叫傳回之後， `TrySolution` 方法接受已移除的 <xref:System.Threading.CancellationToken> 物件之後。  表示這個 <xref:System.Threading.CancellationToken> 物件中移除時， <xref:System.Threading.SpinWait.SpinUntil%2A> 方法會傳回。  
  
## 編譯程式碼  
 請複製範例程式碼並將它貼在 Visual Studio 專案中，或是貼在名為  `DataflowReceiveAny.cs`的檔案中 \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 的 `DataflowReceiveAny.vb` \) ，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**  
  
## 穩固程式設計  
  
## 請參閱  
 [資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)