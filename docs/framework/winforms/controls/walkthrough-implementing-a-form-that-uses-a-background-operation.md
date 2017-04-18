---
title: "逐步解說：實作使用背景作業的表單 | Microsoft Docs"
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
  - "BackgroundWorker 元件"
  - "表單, 背景作業"
  - "表單, 多執行緒"
  - "執行緒處理 [Windows Form], 背景作業"
  - "執行緒處理 [Windows Form], 表單"
  - "執行緒處理 [Windows Form], 逐步解說"
ms.assetid: 4691b796-9200-471a-89c3-ba4c7cc78c03
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 25
---
# 逐步解說：實作使用背景作業的表單
如果您有必須花費長時間才能完成的作業，且不希望使用者介面 \(UI\) 停止回應或「無回應」\(hang\)，您可以使用 <xref:System.ComponentModel.BackgroundWorker> 類別在另一個執行緒上執行作業。  
  
 這個逐步解說會說明如何使用 <xref:System.ComponentModel.BackgroundWorker> 類別「於幕後」執行耗時的計算，讓使用者介面保持回應能力。  當您完成後，會擁有非同步計算費氏數的應用程式。  即使計算大的費氏數會耗費可觀的時間，主要的 UI 執行緒也不會受此延遲中斷，而表單在計算期間將具有回應能力。  
  
 逐步解說將說明的工作包括：  
  
-   建立 Windows 架構應用程式  
  
-   在表單上建立 <xref:System.ComponentModel.BackgroundWorker>  
  
-   加入非同步事件處理常式  
  
-   加入進度報表和取消支援  
  
 如需在此範例中使用的完整程式碼清單，請參閱 [如何：實作使用背景作業的表單](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 建立專案  
 第一個步驟是建立專案並設定表單。  
  
#### 若要建立使用背景作業的表單  
  
1.  建立名為 `BackgroundWorkerExample` 的 Windows 架構應用程式專案。  如需詳細資訊，請參閱[How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
2.  在 \[**方案總管**\] 中以滑鼠右鍵按一下 \[**Form1**\]，並從捷徑功能表中選取 \[**重新命名**\]。  將檔案名稱變更為 `FibonacciCalculator`。  當詢問您是否要重新命名對程式碼項目「`Form1`」的所有參考時，請按一下 \[**是**\] 按鈕。  
  
3.  將 <xref:System.Windows.Forms.NumericUpDown> 控制項從 \[**工具箱**\] 拖曳到表單上。  將 <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> 屬性設定為 `1`，並將 <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> 屬性設定為 `91`。  
  
4.  加入兩個 <xref:System.Windows.Forms.Button> 控制項至表單。  
  
5.  重新命名第一個 <xref:System.Windows.Forms.Button> 控制項 `startAsyncButton`，並將 <xref:System.Windows.Forms.Control.Text%2A> 屬性設定為 `Start Async`。  重新命名第二個 <xref:System.Windows.Forms.Button> 控制項 `cancelAsyncButton`，並將 <xref:System.Windows.Forms.Control.Text%2A> 屬性設定為 `Cancel Async`。  將 <xref:System.Windows.Forms.Control.Enabled%2A> 屬性設定為 `false`。  
  
6.  為 <xref:System.Windows.Forms.Button> 控制項的兩個 <xref:System.Windows.Forms.Control.Click> 事件建立事件處理常式。  如需詳細資訊，請參閱[How to: Create Event Handlers Using the Designer](http://msdn.microsoft.com/zh-tw/8461e9b8-14e8-406f-936e-3726732b23d2)。  
  
7.  將 <xref:System.Windows.Forms.Label> 控制項從 \[**工具箱**\] 拖曳到表單上，並將其重新命名為 `resultLabel`。  
  
8.  將 <xref:System.Windows.Forms.ProgressBar> 控制項從 \[**工具箱**\] 拖曳到表單上。  
  
## 在表單中建立 BackgroundWorker  
 您可以使用 \[**Windows Forms 設計工具**\] 建立非同步作業的 <xref:System.ComponentModel.BackgroundWorker>。  
  
#### 若要使用設計工具建立 BackgroundWorker  
  
-   從 \[**工具箱**\] 的 \[**元件**\] 索引標籤中，將 <xref:System.ComponentModel.BackgroundWorker> 拖曳至表單上。  
  
## 加入非同步事件處理常式  
 您現在已準備好要為 <xref:System.ComponentModel.BackgroundWorker> 元件的非同步事件加入事件處理常式。  將於幕後執行的耗時作業 \(用來計算費氏數\)，會由這些事件處理常式的其中一個進行呼叫。  
  
#### 若要實作非同步事件處理常式  
  
1.  在 \[**屬性**\] 視窗中，在仍選取 <xref:System.ComponentModel.BackgroundWorker> 元件的情況下，按一下 \[**事件**\] 按鈕。  按兩下 <xref:System.ComponentModel.BackgroundWorker.DoWork> 和 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 事件以建立事件處理常式。  如需如何使用事件處理常式的詳細資訊，請參閱[How to: Create Event Handlers Using the Designer](http://msdn.microsoft.com/zh-tw/8461e9b8-14e8-406f-936e-3726732b23d2)。  
  
2.  在表單中建立名為 `ComputeFibonacci` 的新方法。  這個方法負責實際的執行作業，將於幕後執行。  此程式碼示範極無效率的費氏演算法遞迴實作，對於較大的數目要耗費更長的時間才能完成。  在這裡是做為說明用途，以示範在應用程式中可能引入冗長延遲的作業。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#10)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#10)]
     [!code-vb[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#10)]  
  
3.  在 <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件處理常式中加入對 `ComputeFibonacci` 方法的呼叫。  使用 <xref:System.ComponentModel.DoWorkEventArgs> 的 <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> 屬性做為 `ComputeFibonacci` 的第一個參數。  <xref:System.ComponentModel.BackgroundWorker> 和 <xref:System.ComponentModel.DoWorkEventArgs> 參數稍後將會用來做為進度報表和取消支援。  將 `ComputeFibonacci` 的傳回值指派給 <xref:System.ComponentModel.DoWorkEventArgs> 的 <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> 屬性。  <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 事件處理常式將可以使用這個結果。  
  
    > [!NOTE]
    >  <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件處理常式並未直接參考 `backgroundWorker1` 執行個體，因為這會讓此事件處理常式與 <xref:System.ComponentModel.BackgroundWorker> 的特定執行個體結合。  請以引發這個事件的 <xref:System.ComponentModel.BackgroundWorker> 參考代替，此參考會從 `sender` 參數還原。  當表單裝載了一個以上的 <xref:System.ComponentModel.BackgroundWorker> 時，這點非常重要。  另外您還必須注意，不要在 <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件處理常式中操作任何使用者介面物件。  相反地，請透過 <xref:System.ComponentModel.BackgroundWorker> 事件，與使用者介面通訊。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
4.  在 `startAsyncButton` 控制項的 <xref:System.Windows.Forms.Control.Click> 事件處理常式中，加入會啟動非同步作業的程式碼。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#13)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#13)]
     [!code-vb[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#13)]  
  
5.  在 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 事件處理常式中，將計算結果指派給 `resultLabel` 控制項。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#6)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#6)]  
  
## 加入進度報表和取消支援  
 對於花費長時間的非同步作業，通常會向使用者報告進度，並允許使用者取消作業。  <xref:System.ComponentModel.BackgroundWorker> 類別提供了事件，可讓您在背景作業進行時張貼進度。  同時也提供旗標，讓您的工作程式碼可偵測對 <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> 的呼叫並加以中斷。  
  
#### 若要實作進度報表  
  
1.  在 \[**屬性**\] 視窗中選取 `backgroundWorker1`。  將 <xref:System.ComponentModel.BackgroundWorker.WorkerReportsProgress%2A> 和 <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> 屬性設定為 `true`。  
  
2.  在 `FibonacciCalculator` 表單中宣告兩個變數，  這些將用來追蹤進度。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#14)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#14)]
     [!code-vb[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#14)]  
  
3.  加入 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件的事件處理常式。  在 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件處理常式中，使用 <xref:System.ComponentModel.ProgressChangedEventArgs> 參數的 <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> 屬性更新 <xref:System.Windows.Forms.ProgressBar>。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#7)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#7)]  
  
#### 若要實作取消的支援  
  
1.  在 `cancelAsyncButton` 控制項的 <xref:System.Windows.Forms.Control.Click> 事件處理常式中，加入會取消非同步作業的程式碼。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#4)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#4)]  
  
2.  下列 `ComputeFibonacci` 方法中的程式碼片段會報告進度並支援取消。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#11)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#11)]
     [!code-vb[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#11)]  
    [!code-cpp[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#12)]
    [!code-csharp[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#12)]
    [!code-vb[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#12)]  
  
## 檢查點  
 在這個檢查點時，可以編譯並執行費氏計算機應用程式。  
  
#### 若要測試您的專案  
  
-   按 F5 編譯和執行應用程式。  
  
     當計算在幕後執行時，您會看見 <xref:System.Windows.Forms.ProgressBar> 顯示計算逐漸完成的進度。  您也可以取消暫止的作業。  
  
     對於小數目，計算速度應該很快，但對於大數目，您會看見明顯的延遲。  如果您輸入等於或大於 30 的值，就應該看見數秒鐘的延遲，延遲時間依據電腦速度而定。  對於大於 40 的值，可能會花上數分鐘或數小時以完成計算。  當計算機正忙著計算大費氏數時，請注意，您可以自由移動表單，對表單進行最小化、最大化，甚至加以關閉。  這是因為主要的 UI 執行緒並不在等待計算結束。  
  
## 後續步驟  
 您已實作了使用 <xref:System.ComponentModel.BackgroundWorker> 元件在幕後執行計算的表單，現在可以探索非同步作業的其他可能性：  
  
-   為數個同時作業使用多個 <xref:System.ComponentModel.BackgroundWorker> 物件。  
  
-   若要偵錯您的多執行緒應用程式，請參閱 [如何：使用執行緒視窗](../Topic/How%20to:%20Use%20the%20Threads%20Window.md)。  
  
-   實作支援非同步程式撰寫模型 \(Programming Model\) 的元件。  如需詳細資訊，請參閱 [Event\-based Asynchronous Pattern Overview](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)。  
  
    > [!CAUTION]
    >  在使用任何類型的多執行緒時，很可能會接觸到極嚴重且複雜的錯誤。  在實作任何使用多執行緒處理的方案之前，請參閱 [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md)。  
  
## 請參閱  
 <xref:System.ComponentModel.BackgroundWorker>   
 [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md)   
 [元件中的多執行緒](../Topic/Multithreading%20in%20Components.md)   
 [NOT IN BUILD: Multithreading in Visual Basic](http://msdn.microsoft.com/zh-tw/c731a50c-09c1-4468-9646-54c86b75d269)   
 [如何：實作使用背景作業的表單](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)   
 [逐步解說：在背景執行作業](../../../../docs/framework/winforms/controls/walkthrough-running-an-operation-in-the-background.md)   
 [BackgroundWorker 元件](../../../../docs/framework/winforms/controls/backgroundworker-component.md)