---
title: "How to: Cancel a Dataflow Block | Microsoft Docs"
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
  - "dataflow blocks, canceling in TPL"
  - "TPL dataflow library,canceling dataflow blocks"
ms.assetid: fbddda0d-da3b-4ec8-a1d6-67ab8573fcd7
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# How to: Cancel a Dataflow Block
本文件示範如何啟用應用程式的移除。  這個範例會使用 Windows Form 顯示工作項目位置是現用的資料流程管線同時移除效果。  
  
> [!TIP]
>  TPL 資料流程式庫 \(<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName> 命名空間\) 並沒有和 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 配置在一起。  若要安裝 <xref:System.Threading.Tasks.Dataflow> 命名空間，請在 [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] 中開啟您的專案，從 \[專案\] 功能表中選擇 \[**管理 NuGet 封裝**\]，並且線上搜尋 `Microsoft.Tpl.Dataflow` 封裝。  
  
### 若要建立新的 Windows Form 應用程式  
  
1.  建立 C\# 或 **Visual Basic Windows Forms Application** 專案。  在下列步驟中，專案命名為 `CancellationWinForms`。  
  
2.  在主要表單的表單設計工具上， Form1.cs \( [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]中的 Form1.vb\)，將一個 <xref:System.Windows.Forms.ToolStrip> 控制項。  
  
3.  將 <xref:System.Windows.Forms.ToolStripButton> 控制項加入至 <xref:System.Windows.Forms.ToolStrip> 控制項。  將 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> 屬性設定為 <xref:System.Windows.Forms.ToolStripItemDisplayStyle> 和 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性加入工作項目。  
  
4.  將 <xref:System.Windows.Forms.ToolStripButton> 控制項加入至<xref:System.Windows.Forms.ToolStrip>控制項。  設定 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> 屬性為 <xref:System.Windows.Forms.ToolStripItemDisplayStyle>， <xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性取消和 <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> 屬性設定為 `False`。  
  
5.  加入至 <xref:System.Windows.Forms.ToolStrip> 控制項的 <xref:> System.Windows.Forms.ToolStripProgressBar?qualifyHint=False&autoUpgrade=True 物件。  
  
## 建立資料流程管線  
 本節說明如何建立處理工作項目並更新進度列的資料流程管線。  
  
#### 若要建立方案管線  
  
1.  在您的專案中，加入 System.Threading.Tasks.Dataflow.dll 的參考。  
  
2.  確定 Form1.cs \( [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]中的 Form1.vb\) 包含下列 `using` 陳述式 \(在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]中為`Imports` \) 。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3.  將 `WorkItem` 類別和 `Form1` 類別中的內部型別。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4.  加入下列資料成員至 `Form1` 類別中：  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5.  將下列方法 `CreatePipeline` 加入至 `Form1` 類別。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 由於 `incrementProgress` 和 `decrementProgress` 資料流程區塊動作在使用者介面 \(UI\) ，則這個動作會在使用者介面執行緒上發生。  在建構時要達到這個目的，，這些物件都提供有 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> 屬性設定為 <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=fullName>的 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> 物件。  <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=fullName> 方法會建立 <xref:System.Threading.Tasks.TaskScheduler> 物件會在目前的同步處理內容運作。  由於 `Form1` 建構函式會從使用者介面執行緒呼叫 `incrementProgress` and `decrementProgress` ，資料流程區塊的動作在使用者介面執行緒中執行。  
  
 會在建構成員管線時，這個範例會設定 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> 屬性。  因為 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> 屬性永久地移除資料流程區塊執行，必須重新建立整體管線，在使用者取消作業會想要加入多個工作項目到管線之後。  如需示範一種取消資料流程區塊的範例，以便其他工作可以執行，作業已取消之後，請參閱 [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)。  
  
## 連接使用者介面 \(UI\) 的資料流程管線  
 本節說明如何連接資料流程管線到使用者介面。  建立管線和將工作項目加入至管線由加入工作項目按鈕的事件處理常式的控制項。  取消按鈕啟始取消。  當使用者點擊其中一個按鈕時，適當的動作已開始以非同步方式。  
  
#### 連接使用者介面 \(UI\) 的資料流程管線  
  
1.  在主要表單的表單設計工具上，建立 <xref:System.Windows.Forms.ToolStripItem.Click> 事件的事件處理常式加入工作項目按鈕的。  
  
2.  實作加入工作項目按鈕的 <xref:System.Windows.Forms.ToolStripItem.Click> 事件。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3.  在主要表單的表單設計工具上，替取消按鈕建立 <xref:System.Windows.Forms.ToolStripItem.Click> 事件處理常式。  
  
4.  實作取消按鈕的 <xref:System.Windows.Forms.ToolStripItem.Click> 事件處理常式。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## 範例  
 下列範例顯示 Form1.cs \( [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]中的 Form1.vb 完整的程式碼\)。  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 下圖顯示的是執行中的應用程式。  
  
 ![Windows Form 應用程式](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow\_Cancellation")  
  
## 穩固程式設計  
  
## 請參閱  
 [資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)