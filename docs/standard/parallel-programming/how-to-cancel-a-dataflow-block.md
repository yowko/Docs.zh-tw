---
title: "如何：取消資料流程區塊"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- dataflow blocks, canceling in TPL
- TPL dataflow library,canceling dataflow blocks
ms.assetid: fbddda0d-da3b-4ec8-a1d6-67ab8573fcd7
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4d6fbde31cd4b4b5d0c6404b8baf23230f2bda77
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-cancel-a-dataflow-block"></a>如何：取消資料流程區塊
本文件示範如何在您的應用程式中啟用取消作業。 此範例會使用 Windows Forms 來顯示工作項目在資料流程管線中的作用位置，以及取消作業的效果。  
  
> [!TIP]
>  TPL 資料流程程式庫 (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> 命名空間) 並未隨附於 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]。 若要安裝<xref:System.Threading.Tasks.Dataflow>命名空間中，開啟您的專案中[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]，選擇**管理 NuGet 封裝**從 [專案] 功能表中，並在搜尋線上`Microsoft.Tpl.Dataflow`封裝。  
  
### <a name="to-create-the-windows-forms-application"></a>若要建立 Windows Forms 應用程式  
  
1.  建立 C# 或 Visual Basic **Windows Forms 應用程式**專案。 在下列步驟中，專案會命名為 `CancellationWinForms`。  
  
2.  在主要表單 Form1.cs 的表單設計工具 (為 Form1.vb [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)])，新增<xref:System.Windows.Forms.ToolStrip>控制項。  
  
3.  新增<xref:System.Windows.Forms.ToolStripButton>控制權傳輸至<xref:System.Windows.Forms.ToolStrip>控制項。 設定<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>屬性<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>和<xref:System.Windows.Forms.ToolStripItem.Text%2A>屬性**加入工作項目**。  
  
4.  新增第二個<xref:System.Windows.Forms.ToolStripButton>控制權傳輸至<xref:System.Windows.Forms.ToolStrip>控制項。 設定<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>屬性<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>、<xref:System.Windows.Forms.ToolStripItem.Text%2A>屬性**取消**，而<xref:System.Windows.Forms.ToolStripItem.Enabled%2A>屬性`False`。  
  
5.  加入四個<xref:System.Windows.Forms.ToolStripProgressBar>物件加入至<xref:System.Windows.Forms.ToolStrip>控制項。  
  
## <a name="creating-the-dataflow-pipeline"></a>建立資料流程管線  
 本節說明如何建立資料流程管線，以處理工作項目並更新進度列。  
  
#### <a name="to-create-the-dataflow-pipeline"></a>建立資料流程管線  
  
1.  在您的專案中，加入 System.Threading.Tasks.Dataflow.dll 的參考。  
  
2.  確定 Form1.cs (在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 中為 Form1.vb) 包含下列 `using` 陳述式 (在 `Imports` 中為 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)])。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3.  將 `WorkItem` 類別新增為 `Form1` 類別的內部類別。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4.  將下列資料成員新增至 `Form1` 類別。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5.  將下列 `CreatePipeline` 方法新增至 `Form1` 類別。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 由於 `incrementProgress` 和 `decrementProgress`資料流程區塊會在使用者介面上進行處理，因此這個動作一定要在使用者介面執行緒上發生。 若要達成此目的，在建構期間每個提供這些物件<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>具有物件<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A>屬性設定為<xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>。 <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> 方法會建立 <xref:System.Threading.Tasks.TaskScheduler> 物件，該物件會在目前的同步處理內容上執行工作。 由於 `Form1` 建構函式是從使用者介面執行緒呼叫，因此 `incrementProgress` 和 `decrementProgress` 資料流程區塊的動作也會在使用者介面執行緒上執行。  
  
 此範例會設定<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A>屬性時就會建構管線的成員。 因為<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A>屬性永遠會取消資料流程區塊執行，必須重新建立整個管線之後使用者取消作業，並要將多個工作項目新增至管線。 如需示範取消資料流程區塊的替代方式，以便在取消作業後執行其他工作的範例，請參閱[逐步解說︰在 Windows Forms 應用程式中使用資料流程](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)。  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a>將資料流程管線連接至使用者介面  
 本節說明如何將資料流程管線連接至使用者介面。 建立管線以及將工作項目新增至管線都是由 [新增工作項目] 按鈕的事件處理常式所控制。 取消作業是由 [取消] 按鈕所起始。 當使用者按一下任一個按鈕時，會以非同步方式起始適當的動作。  
  
#### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a>將資料流程管線連接至使用者介面  
  
1.  在主要表單的表單設計工具，建立事件處理常式<xref:System.Windows.Forms.ToolStripItem.Click>事件**加入工作項目** 按鈕。  
  
2.  實作<xref:System.Windows.Forms.ToolStripItem.Click>事件**加入工作項目** 按鈕。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3.  在主要表單的表單設計工具，建立事件處理常式<xref:System.Windows.Forms.ToolStripItem.Click>事件處理常式**取消** 按鈕。  
  
4.  實作<xref:System.Windows.Forms.ToolStripItem.Click>事件處理常式**取消** 按鈕。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a>範例  
 下列範例顯示 Form1.cs (在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 中為 Form1.vb) 的完整程式碼。  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 下圖顯示執行的應用程式。  
  
 ![Windows Forms 應用程式](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")  
  
## <a name="robust-programming"></a>穩固程式設計  
  
## <a name="see-also"></a>另請參閱  
 [資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
