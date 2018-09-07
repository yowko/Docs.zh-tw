---
title: 逐步解說：在背景執行作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 1b9a4e0a-f134-48ff-a1be-c461446a31ba
ms.openlocfilehash: 09019f24248985c0a1057873f0226ee69a30ca9d
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084688"
---
# <a name="walkthrough-running-an-operation-in-the-background"></a>逐步解說：在背景執行作業
如果您有要花費較長時間才能完成的作業，但您不想導致使用者介面發生延遲，就可以使用 <xref:System.ComponentModel.BackgroundWorker> 類別在另一個執行緒上執行該作業。  
  
 如需在此範例中使用的程式碼的完整清單，請參閱 <<c0> [ 如何： 在背景執行作業](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-run-an-operation-in-the-background"></a>若要在背景執行作業  
  
1.  與您在 Windows Form 設計工具中的表單，將兩個<xref:System.Windows.Forms.Button>控制項從**工具箱**到表單，並再把`Name`和<xref:System.Windows.Forms.Control.Text%2A>根據下表按鈕的屬性。  
  
    |按鈕|名稱|文字|  
    |------------|----------|----------|  
    |`button1`|`startBtn`|**Start**|  
    |`button2`|`cancelBtn`|**取消**|  
  
2.  開啟**工具箱**，按一下**元件**索引標籤，然後再拖曳<xref:System.ComponentModel.BackgroundWorker>元件拖曳至表單。  
  
     `backgroundWorker1`元件會出現在**元件匣**。  
  
3.  在 **屬性**視窗中，將<xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A>屬性設`true`。  
  
4.  在 **屬性**視窗中，按一下**事件**按鈕，然後再連按兩下<xref:System.ComponentModel.BackgroundWorker.DoWork>和<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件建立事件處理常式。  
  
5.  插入您耗費時間的程式碼插入<xref:System.ComponentModel.BackgroundWorker.DoWork>事件處理常式。  
  
6.  擷取作業所需的任何參數<xref:System.ComponentModel.DoWorkEventArgs.Argument%2A>屬性<xref:System.ComponentModel.DoWorkEventArgs>參數。  
  
7.  若要計算的結果指派<xref:System.ComponentModel.DoWorkEventArgs.Result%2A>屬性<xref:System.ComponentModel.DoWorkEventArgs>。  
  
     這是將可供<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件處理常式。  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#2)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#2)]  
  
8.  插入程式碼來擷取在您作業的結果<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件處理常式。  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#3)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#3)]  
  
9. 實作 `TimeConsumingOperation` 方法。  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#4)]  
  
10. 在 Windows Form 設計工具中，按兩下`startButton`來建立<xref:System.Windows.Forms.Control.Click>事件處理常式。  
  
11. 呼叫<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>方法中的<xref:System.Windows.Forms.Control.Click>事件處理常式`startButton`。  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#5)]  
  
12. 在 Windows Form 設計工具中，按兩下`cancelButton`來建立<xref:System.Windows.Forms.Control.Click>事件處理常式。  
  
13. 呼叫<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>方法中的<xref:System.Windows.Forms.Control.Click>事件處理常式`cancelButton`。  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#6)]  
  
14. 在檔案頂端，匯入 System.ComponentModel 和 System.Threading 命名空間。  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#7)]  
  
15. 按下 F6 以建置方案，，然後按 CTRL-F5 執行應用程式偵錯工具之外。  
  
> [!NOTE]
>  如果您按 F5 執行應用程式在偵錯工具，在引發例外狀況`TimeConsumingOperation`方法會攔截到並顯示偵錯工具。 當您執行偵錯工具中，外部應用程式時<xref:System.ComponentModel.BackgroundWorker>處理例外狀況，並快取中<xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>屬性<xref:System.ComponentModel.RunWorkerCompletedEventArgs>。  
  
1.  按一下 **開始**按鈕以執行非同步作業，，然後按一下**取消**按鈕以停止執行中的非同步作業。  
  
     每個作業的結果會顯示於 <xref:System.Windows.Forms.MessageBox>。  
  
## <a name="next-steps"></a>後續步驟  
  
-   實作非同步作業進行時，報告進度的表單。 如需詳細資訊，請參閱 <<c0> [ 如何： 實作使用背景作業的表單](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)。  
  
-   實作元件支援非同步模式的類別。 如需詳細資訊，請參閱 <<c0> [ 實作事件架構非同步模式](../../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [操作說明：實作使用背景作業的表單](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [操作說明：在背景執行作業](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [BackgroundWorker 元件](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
