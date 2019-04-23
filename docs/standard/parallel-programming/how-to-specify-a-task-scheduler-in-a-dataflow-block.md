---
title: HOW TO：在資料流程區塊中指定工作排程器
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TPL dataflow library, linking to task scheduler in TPL
- Task Parallel Library, dataflows
- task scheduler, linking from TPL
ms.assetid: 27ece374-ed5b-49ef-9cec-b20db34a65e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 681c0f1f918c8991ed2544189488d1ea25547834
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59345842"
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a>HOW TO：在資料流程區塊中指定工作排程器
此文件將示範當您在應用程式中使用資料流程時，如何與特定工作排程器產生關聯。 這個範例會使用 Windows Form 應用程式中的 <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> 類別顯示讀取器工作何時為使用中，以及寫入器工作何時為使用中。 另外還會使用 <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> 方法讓資料流程區塊在使用者介面執行緒上執行。

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a>若要建立 Windows Forms 應用程式  
  
1. 建立 Visual C# 或 Visual Basic **Windows Forms 應用程式**專案。 在下列步驟中，專案會命名為 `WriterReadersWinForms`。  
  
2. 在主要表單 Form1.cs (在 Visual Basic 中為 Form1.vb) 的表單設計工具上，新增四個 <xref:System.Windows.Forms.CheckBox> 控制項。 將 `checkBox1` 的 <xref:System.Windows.Forms.Control.Text%2A> 屬性設定為**讀取器 1**、`checkBox2` 的該屬性設為**讀取器 2**、`checkBox3` 的該屬性設為**讀取器 3**，以及 `checkBox4` 的該屬性設為**寫入器**。 將每個控制項的 <xref:System.Windows.Forms.Control.Enabled%2A> 屬性設為 `False`。  
  
3. 將 <xref:System.Windows.Forms.Timer> 控制項加入表單。 將 <xref:System.Windows.Forms.Timer.Interval%2A> 屬性設定為 `2500`。  
  
## <a name="adding-dataflow-functionality"></a>加入資料流程功能  
 本節將說明如何建立參與應用程式的資料流程區塊，以及如何將每個區塊與工作排程器產生關聯。  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a>若要將資料流程功能加入至應用程式  
  
1. 在您的專案中，加入 System.Threading.Tasks.Dataflow.dll 的參考。  
  
2. 確定 Form1.cs (在 Visual Basic 中為 Form1.vb) 包含下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)。  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3. 將 <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> 資料成員加入至 `Form1` 類別。  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4. 在 `Form1` 建構函式中，於呼叫 `InitializeComponent` 之後建立 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件，用於切換 <xref:System.Windows.Forms.CheckBox> 物件的狀態。  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5. 在 `Form1` 建構函式中，建立 <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> 物件和四個 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件，每個 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件都有一個 <xref:System.Windows.Forms.CheckBox> 物件。 針對每個 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件指定 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> 物件，並將其 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> 屬性設定為讀取器的 <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> 屬性，以及寫入器的 <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> 屬性。  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6. 在 `Form1` 建構函式中，啟動 <xref:System.Windows.Forms.Timer> 物件。  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7. 在主要表單的表單設計工具上，為計時器的 <xref:System.Windows.Forms.Timer.Tick> 事件建立事件處理常式。  
  
8. 實作計時器的 <xref:System.Windows.Forms.Timer.Tick> 事件。  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 由於 `toggleCheckBox` 資料流程區塊會在使用者介面上進行處理，因此這個動作一定要在使用者介面執行緒上發生。 為了要完成這項作業，在建構時這個物件會提供 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> 物件，而且其 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> 屬性會設定為 <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>。 <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> 方法會建立 <xref:System.Threading.Tasks.TaskScheduler> 物件，該物件會在目前的同步處理內容上執行工作。 由於 `Form1` 建構函式是從使用者介面執行緒呼叫，因此 `toggleCheckBox` 資料流程區塊的動作也會在使用者介面執行緒上執行。  
  
 這個範例也會使用 <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> 類別讓某些資料流程區塊同時執行，以及讓另一個資料流程區塊相對於同一個 <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> 物件上執行的所有資料流程區塊獨佔執行。 當多個資料流程區塊共用某一項資源，而其中有些區塊需要獨佔存取該資源時，這項技術會很有用，因為它能讓您不必手動同步處理該資源的存取權。 不必手動同步處理可讓程式碼更有效率。  
  
## <a name="example"></a>範例  
 下列範例顯示 Form1.cs (在 Visual Basic 中為 Form1.vb) 的完整程式碼。  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a>另請參閱

- [資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
