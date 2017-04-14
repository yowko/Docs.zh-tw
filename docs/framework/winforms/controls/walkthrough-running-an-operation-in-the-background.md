---
title: "逐步解說：在背景執行作業 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "背景作業"
  - "背景工作"
  - "背景執行緒"
  - "BackgroundWorker 類別, 範例"
  - "表單, 背景作業"
  - "表單, 多執行緒"
  - "執行緒處理 [Windows Form], 背景作業"
ms.assetid: 1b9a4e0a-f134-48ff-a1be-c461446a31ba
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 逐步解說：在背景執行作業
如果您有要花費較長時間才能完成的作業，但您不想導致使用者介面發生延遲，就可以使用 <xref:System.ComponentModel.BackgroundWorker> 類別在另一個執行緒上執行該作業。  
  
 如需在此範例中使用的完整程式碼清單，請參閱 [如何：在背景執行作業](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要在背景執行作業  
  
1.  使您的表單成為 \[Windows Form 設計工具\] 中的現用表單，從 \[**工具箱**\] 拖曳兩個 <xref:System.Windows.Forms.Button> 控制項到表單中，然後根據下表設定按鈕的 `Name` 和 <xref:System.Windows.Forms.Control.Text%2A> 屬性。  
  
    |Button|名稱|文字|  
    |------------|--------|--------|  
    |`button1`|`startBtn`|Start|  
    |`button2`|`cancelBtn`|Cancel|  
  
2.  開啟 \[**工具箱**\]，按一下 \[**元件**\] 索引標籤，然後將 <xref:System.ComponentModel.BackgroundWorker> 元件拖曳到表單上。  
  
     `backgroundWorker1` 元件隨即出現在 \[**元件匣**\] 上。  
  
3.  在 \[**屬性**\] 視窗中，將 <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> 屬性設定為 `true`。  
  
4.  在 \[**屬性**\] 視窗中，按一下 \[**事件**\] 按鈕，再按兩下 <xref:System.ComponentModel.BackgroundWorker.DoWork> 和 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 事件以建立事件處理常式。  
  
5.  在 <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件處理常式中插入會耗費許多時間的程式碼。  
  
6.  從 <xref:System.ComponentModel.DoWorkEventArgs> 參數的 <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> 屬性中擷取這項作業所需的任何參數。  
  
7.  將計算的結果指派至 <xref:System.ComponentModel.DoWorkEventArgs> 的 <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> 屬性。  
  
     <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 事件處理常式將可以使用這個結果。  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#2)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#2)]  
  
8.  在 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 事件處理常式中插入擷取結果的程式碼。  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#3)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#3)]  
  
9. 實作 `TimeConsumingOperation` 方法。  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#4)]  
  
10. 在 \[Windows Form 設計工具\] 中按兩下 `startButton` 以建立 <xref:System.Windows.Forms.Control.Click> 事件處理常式。  
  
11. 為  `startButton` 呼叫 <xref:System.Windows.Forms.Control.Click> 事件處理常式中的 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 方法。  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#5)]  
  
12. 在 \[Windows Form 設計工具\] 中按兩下 `cancelButton` 以建立 <xref:System.Windows.Forms.Control.Click> 事件處理常式。  
  
13. 為  `cancelButton` 呼叫 <xref:System.Windows.Forms.Control.Click> 事件處理常式中的 <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> 方法。  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#6)]  
  
14. 在檔案的頂端，匯入 System.ComponentModel 和 System.Threading 命名空間。  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#7)]  
  
15. 按 F6 建置方案，然後按 CTRL\-F5 在偵錯工具外部執行應用程式。  
  
> [!NOTE]
>  如果您按 F5 在偵錯工具內部執行應用程式，偵錯工具會攔截並顯示在 `TimeConsumingOperation` 方法中所引發的例外狀況。  當您在偵錯工具內部執行應用程式時，<xref:System.ComponentModel.BackgroundWorker> 會處理例外狀況，並在 <xref:System.ComponentModel.RunWorkerCompletedEventArgs> 的 <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> 屬性中將其攔截。  
  
1.  按一下 \[**開始**\] 按鈕以執行非同步作業，然後按一下 \[**取消**\] 按鈕以停止執行中的非同步作業。  
  
     每個作業的結果會顯示於 <xref:System.Windows.Forms.MessageBox>。  
  
## 後續步驟  
  
-   實作一個可以回報非同步作業進度的表單。  如需詳細資訊，請參閱 [如何：實作使用背景作業的表單](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)。  
  
-   實作一個支援元件非同步模式的類別。  如需詳細資訊，請參閱[Implementing the Event\-based Asynchronous Pattern](../../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)。  
  
## 請參閱  
 <xref:System.ComponentModel.BackgroundWorker>   
 <xref:System.ComponentModel.DoWorkEventArgs>   
 [如何：實作使用背景作業的表單](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)   
 [如何：在背景執行作業](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)   
 [BackgroundWorker 元件](../../../../docs/framework/winforms/controls/backgroundworker-component.md)