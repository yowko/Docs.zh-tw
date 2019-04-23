---
title: 作法：取消資料流程區塊
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- dataflow blocks, canceling in TPL
- TPL dataflow library,canceling dataflow blocks
ms.assetid: fbddda0d-da3b-4ec8-a1d6-67ab8573fcd7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b95f0a3535716c4a01dae52abe38eb850f080cf0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59345192"
---
# <a name="how-to-cancel-a-dataflow-block"></a>作法：取消資料流程區塊
本文件示範如何在您的應用程式中啟用取消作業。 此範例會使用 Windows Forms 來顯示工作項目在資料流程管線中的作用位置，以及取消作業的效果。  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a>若要建立 Windows Forms 應用程式  
  
1. 建立 C# 或 Visual Basic **Windows Forms 應用程式**專案。 在下列步驟中，專案會命名為 `CancellationWinForms`。  
  
2. 在主要表單 Form1.cs (在 Visual Basic 中為 Form1.vb) 的表單設計工具上，新增 <xref:System.Windows.Forms.ToolStrip> 控制項。  
  
3. 將 <xref:System.Windows.Forms.ToolStripButton> 控制項加入 <xref:System.Windows.Forms.ToolStrip> 控制項。 將 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> 屬性設為 <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> 並將 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性設為**新增工作項目**。  
  
4. 將第二個 <xref:System.Windows.Forms.ToolStripButton> 控制項加入 <xref:System.Windows.Forms.ToolStrip> 控制項。 將 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> 屬性設為 <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>，將 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性設為 **Cancel**，然後將 <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> 屬性設為 `False`。  
  
5. 將四個 <xref:System.Windows.Forms.ToolStripProgressBar> 物件加入 <xref:System.Windows.Forms.ToolStrip> 控制項。  
  
## <a name="creating-the-dataflow-pipeline"></a>建立資料流程管線  
 本節說明如何建立資料流程管線，以處理工作項目並更新進度列。  
  
### <a name="to-create-the-dataflow-pipeline"></a>建立資料流程管線  
  
1. 在您的專案中，加入 System.Threading.Tasks.Dataflow.dll 的參考。  
  
2. 確定 Form1.cs (在 Visual Basic 中為 Form1.vb) 包含下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3. 將 `WorkItem` 類別新增為 `Form1` 類別的內部類別。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4. 將下列資料成員新增至 `Form1` 類別。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5. 將下列 `CreatePipeline` 方法新增至 `Form1` 類別。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 由於 `incrementProgress` 和 `decrementProgress`資料流程區塊會在使用者介面上進行處理，因此這個動作一定要在使用者介面執行緒上發生。 為了要完成這項作業，在建構時這些物件會提供 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> 物件，而且其 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> 屬性會設定為 <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>。 <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> 方法會建立 <xref:System.Threading.Tasks.TaskScheduler> 物件，該物件會在目前的同步處理內容上執行工作。 由於 `Form1` 建構函式是從使用者介面執行緒呼叫，因此 `incrementProgress` 和 `decrementProgress` 資料流程區塊的動作也會在使用者介面執行緒上執行。  
  
 此範例在它建構管線成員時會設定 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> 屬性。 因為 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> 屬性會永久取消資料流程區塊執行，所以必須在使用者取消此作業，而後想要將更多工作項目新增至管線之後，重新建立整個管線。 如需示範取消資料流程區塊的替代方式，以便在取消作業後執行其他工作的範例，請參閱[逐步解說︰在 Windows Forms 應用程式中使用資料流程](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)。  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a>將資料流程管線連接至使用者介面  
 本節說明如何將資料流程管線連接至使用者介面。 建立管線以及將工作項目新增至管線都是由 [新增工作項目] 按鈕的事件處理常式所控制。 取消作業是由 [取消] 按鈕所起始。 當使用者按一下任一個按鈕時，會以非同步方式起始適當的動作。  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a>將資料流程管線連接至使用者介面  
  
1. 在主要表單的表單設計工具上，為 [新增工作項目] 的 <xref:System.Windows.Forms.ToolStripItem.Click> 事件建立事件處理常式。  
  
2. 實作 [新增工作項目] 按鈕的 <xref:System.Windows.Forms.ToolStripItem.Click> 事件。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3. 在主要表單的表單設計工具上，為 [取消] 的 <xref:System.Windows.Forms.ToolStripItem.Click> 事件建立事件處理常式。  
  
4. 實作 [取消] 按鈕的 <xref:System.Windows.Forms.ToolStripItem.Click> 事件處理常式。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a>範例  
 下列範例顯示 Form1.cs (在 Visual Basic 中為 Form1.vb) 的完整程式碼。  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 下圖顯示執行的應用程式。  
  
 ![Windows Forms 應用程式](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")  

## <a name="see-also"></a>另請參閱

- [資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
