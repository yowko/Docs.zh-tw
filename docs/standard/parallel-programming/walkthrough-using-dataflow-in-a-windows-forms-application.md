---
title: 逐步解說：在 Windows Forms 應用程式中使用資料流程
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- TPL dataflow library, in Windows Forms
- Task Parallel Library, dataflows
- Windows Forms, and TPL
ms.assetid: 9c65cdf7-660c-409f-89ea-59d7ec8e127c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6d27500332c59f24e121c9c15ac27a36ed93d07
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2019
ms.locfileid: "58465798"
---
# <a name="walkthrough-using-dataflow-in-a-windows-forms-application"></a>逐步解說：在 Windows Forms 應用程式中使用資料流程
此文件示範如何建立資料流程區塊網路，其可以在 Windows Forms 應用程式中執行映像處理。  
  
 這個範例會從指定的資料夾載入映像檔案、建立複合映像，以及顯示結果。 這個範例會使用資料流程模型，透過網路路由映像。 在資料流程模型中，程式的獨立元件會透過傳送訊息，彼此進行通訊。 當元件收到訊息時，它會執行某些動作，然後將結果傳遞給另一個元件。 比較資料流程模型與控制流程模型，在其中應用程式會使用控制項結構，例如，條件陳述式、迴圈等等，來控制程式中作業的順序。  
  
## <a name="prerequisites"></a>必要條件  
 在開始進行這個逐步解說之前，請先閱讀[資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)。  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="sections"></a>章節  
 本逐步解說包含下列各節：  
  
-   [建立 Windows Forms 應用程式](#winforms)  
  
-   [建立資料流程網路](#network)  
  
-   [連接資料流程網路與使用者介面](#ui)  
  
-   [完整範例](#complete)  
  
<a name="winforms"></a>   
## <a name="creating-the-windows-forms-application"></a>建立 Windows Forms 應用程式  
 本節描述如何建立基本 Windows Forms 應用程式，並且將控制項新增至主要表單。  
  
#### <a name="to-create-the-windows-forms-application"></a>若要建立 Windows Forms 應用程式  
  
1.  在 Visual Studio 中，建立 Visual C# 或 Visual Basic **Windows Forms 應用程式**專案。 在此文件中，專案命名為 `CompositeImages`。  
  
2.  在主要表單 Form1.cs (在 Visual Basic 中為 Form1.vb) 的表單設計工具上，新增 <xref:System.Windows.Forms.ToolStrip> 控制項。  
  
3.  將 <xref:System.Windows.Forms.ToolStripButton> 控制項加入 <xref:System.Windows.Forms.ToolStrip> 控制項。 將 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> 屬性設為 <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>，並將 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性設為 **Choose Folder**。  
  
4.  將第二個 <xref:System.Windows.Forms.ToolStripButton> 控制項加入 <xref:System.Windows.Forms.ToolStrip> 控制項。 將 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> 屬性設為 <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>，將 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性設為 **Cancel**，然後將 <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> 屬性設為 `False`。  
  
5.  將 <xref:System.Windows.Forms.PictureBox> 物件加入主要表單。 將 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設定為 <xref:System.Windows.Forms.DockStyle.Fill>。  
  
<a name="network"></a>   
## <a name="creating-the-dataflow-network"></a>建立資料流程網路  
 本節描述如何建立會執行映像處理的資料流程網路。  
  
#### <a name="to-create-the-dataflow-network"></a>若要建立資料流程網路  
  
1.  將 System.Threading.Tasks.Dataflow.dll 參考新增至您的專案。  
  
2.  確定 Form1.cs (在 Visual Basic 中為 Form1.vb) 包含下列 `using` (在 Visual Basic 中為 `Using`) 陳述式：  
  
     [!code-csharp[TPLDataflow_CompositeImages#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#1)]  
  
3.  將下列資料成員新增至 `Form1` 類別：  
  
     [!code-csharp[TPLDataflow_CompositeImages#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#2)]  
  
4.  將下列 `CreateImageProcessingNetwork` 方法新增至 `Form1` 類別。 這個方法會建立映像處理網路。  
  
     [!code-csharp[TPLDataflow_CompositeImages#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#3)]  
  
5.  實作 `LoadBitmaps` 方法。  
  
     [!code-csharp[TPLDataflow_CompositeImages#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#4)]  
  
6.  實作 `CreateCompositeBitmap` 方法。  
  
     [!code-csharp[TPLDataflow_CompositeImages#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#5)]  
  
    > [!NOTE]
    >  C# 版本的 `CreateCompositeBitmap` 方法會使用指標，以便有效處理 <xref:System.Drawing.Bitmap?displayProperty=nameWithType> 物件。 因此，您必須在專案中啟用 [容許 Unsafe 程式碼] 選項，以便使用 [unsafe](~/docs/csharp/language-reference/keywords/unsafe.md) 關鍵字。 如需如何在 Visual C# 專案中啟用不安全程式碼的詳細資訊，請參閱[專案設計工具、建置頁 (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)。  
  
 下表描述網路的成員。  
  
|成員|類型|說明|  
|------------|----------|-----------------|  
|`loadBitmaps`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|採用資料夾路徑做為輸入，並且產生 <xref:System.Drawing.Bitmap> 物件的集合作為輸出。|  
|`createCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|採用 <xref:System.Drawing.Bitmap> 物件的集合做為輸入，並且產生複合點陣圖做為輸出。|  
|`displayCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|在表單上顯示複合點陣圖。|  
|`operationCancelled`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|顯示映像以表示作業已取消，讓使用者選取另一個資料夾。|  
  
 為了連線資料流程區塊以形成網路，此範例會使用 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> 方法。 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> 方法包含採用 <xref:System.Predicate%601> 物件的多載版本，該物件會判斷目標區塊是否接受或拒絕訊息。 這個篩選機制可讓訊息區塊僅接收特定的值。 在此範例中，網路可以使用兩種方式之一進行分支。 主要分支會從磁碟載入映像、建立複合映像，以及在表單上顯示該映像。 替代分支會取消目前的作業。 <xref:System.Predicate%601> 物件會啟用主要分支上的資料流程區塊，以藉由拒絕特定訊息來切換至替代分支。 例如，如果使用者取消作業，資料流程區塊 `createCompositeBitmap` 會產生 `null` (在 Visual Basic 中為 `Nothing`) 作為其輸出。 資料流程區塊 `displayCompositeBitmap` 會拒絕 `null` 輸入值，因此，訊息會提供給 `operationCancelled`。 資料流程區塊 `operationCancelled` 接受所有訊息，因此，會顯示映像表示作業取消。  
  
 下圖顯示影像處理網路：  
  
 ![顯示影像處理網路的圖例。](./media/walkthrough-using-dataflow-in-a-windows-forms-application/dataflow-winforms-image-processing.png)  
  
 由於 `displayCompositeBitmap` 和 `operationCancelled`資料流程區塊會在使用者介面上進行處理，因此這個動作一定要在使用者介面執行緒上發生。 為了要完成這項作業，這些物件在建構時會提供 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> 物件，而且其 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> 屬性會設定為 <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>。 <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> 方法會建立 <xref:System.Threading.Tasks.TaskScheduler> 物件，該物件會在目前的同步處理內容上執行工作。 因為 `CreateImageProcessingNetwork` 方法是從 [選擇資料夾] 按鈕的處理常式呼叫，它會在使用者介面執行緒上執行，`displayCompositeBitmap` 和 `operationCancelled` 資料流程區塊的動作也會在使用者介面執行緒上執行。  
  
 此範例使用共用取消權杖，而非設定 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> 屬性，因為 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> 屬性會永久取消資料流程區塊的執行。 取消語彙基元可讓此範例重複使用相同的資料流程網路多次，即使使用者取消一或多個作業。 如需使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> 以永久取消資料流程區塊執行的範例，請參閱[如何：取消資料流程區塊](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md)。  
  
<a name="ui"></a>   
## <a name="connecting-the-dataflow-network-to-the-user-interface"></a>連接資料流程網路與使用者介面  
 本節描述如何連接資料流程網路與使用者介面。 建立複合映像和取消作業是從 [選擇資料夾] 和 [取消] 按鈕起始。 當使用者選擇任一個按鈕時，會以非同步方式起始適當的動作。  
  
#### <a name="to-connect-the-dataflow-network-to-the-user-interface"></a>若要連接資料流程網路與使用者介面  
  
1.  在主要表單的表單設計工具上，為 **Choose Folder** 按鈕的 <xref:System.Windows.Forms.ToolStripItem.Click> 事件建立事件處理常式。  
  
2.  實作 **Choose Folder** 按鈕的 <xref:System.Windows.Forms.ToolStripItem.Click> 事件。  
  
     [!code-csharp[TPLDataflow_CompositeImages#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#6)]  
  
3.  在主要表單的表單設計工具上，為 **Cancel** 按鈕的 <xref:System.Windows.Forms.ToolStripItem.Click> 事件建立事件處理常式。  
  
4.  實作 **Cancel** 按鈕的 <xref:System.Windows.Forms.ToolStripItem.Click> 事件。  
  
     [!code-csharp[TPLDataflow_CompositeImages#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#7)]  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a>完整範例  
 下列範例將示範本逐步解說的完整程式碼。  
  
 [!code-csharp[TPLDataflow_CompositeImages#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#100)]  
  
 下圖顯示通用 \Sample Pictures\ 資料夾的一般輸出。  
  
 ![Windows Forms 應用程式](../../../docs/standard/parallel-programming/media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")  

## <a name="see-also"></a>另請參閱

- [資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
