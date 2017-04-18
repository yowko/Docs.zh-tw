---
title: "如何：進行對 Windows Form 控制項的安全執行緒呼叫 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHInvalidOperation.WinForms.IllegalCrossThreadCall"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "執行緒安全, 呼叫控制項 [Windows Forms]"
  - "呼叫控制項, 執行緒安全 [Windows Forms]"
  - "CheckForIllegalCrossThreadCalls 屬性 [Windows Form]"
  - "Windows Forms 控制項, 多執行緒"
  - "BackgroundWorker 類別, 範例"
  - "執行緒處理 [Windows Forms], 跨執行緒呼叫"
  - "控制項 [Windows Forms], 多執行緒"
ms.assetid: 138f38b6-1099-4fd5-910c-390b41cbad35
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 如何：進行對 Windows Form 控制項的安全執行緒呼叫
如果您使用多執行緒處理來改善 Windows Forms 應用程式的效能，您必須確定以安全執行緒的方式呼叫控制項。  
  
 Windows Forms 控制項的存取並非原本就是安全執行緒。 如果您有兩個以上的執行緒在管理控制項狀態，則可能會強制控制項進入不一致的狀態。 也可能發生其他與執行緒相關的錯誤，例如競爭情況和死結 \(deadlock\)。 請務必確定您的控制項存取是以安全執行緒的方式執行。  
  
 從非建立控制項的執行緒呼叫控制項，而不使用 <xref:System.Windows.Forms.Control.Invoke%2A> 方法，是不安全的作法。 以下是非安全執行緒的呼叫範例。  
  
 [!code-cpp[System.Windows.Forms.CrossThreadCalls#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/cpp/Form1.cpp#6)]
 [!code-csharp[System.Windows.Forms.CrossThreadCalls#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/CS/Form1.cs#6)]
 [!code-vb[System.Windows.Forms.CrossThreadCalls#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/VB/Form1.vb#6)]  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 可幫助您偵測正在以不安全執行緒的方式存取控制項。 當您在偵錯工具執行應用程式時，如果非建立控制項的執行緒嘗試呼叫該控制項，則偵錯工具會引發 <xref:System.InvalidOperationException>，並且會有訊息：「控制項 *控制項名稱* 已從建立它的執行緒以外的執行緒進行存取。」  
  
 這個例外狀況一般發生在偵錯期間，並且在某些情況下會發生在執行階段。 當您在偵錯使用 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 之前的 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] 所撰寫的應用程式時，可能會看到這個例外狀況。 強烈建議您在看到時修正這個問題，但您可以藉由將 <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A> 屬性設定為 `false` 來停用它。 這會使您的控制項像是在 Visual Studio.NET 2003 及 [!INCLUDE[net_v11_short](../../../../includes/net-v11-short-md.md)] 之下執行。  
  
> [!NOTE]
>  如果您在表單上使用 ActiveX 控制項，當您在偵錯工具下執行時，可能會收到跨執行緒的 <xref:System.InvalidOperationException>。 發生這種情況時，ActiveX 控制項不支援多執行緒處理。 如需如何搭配使用 ActiveX 控制項與 Windows Forms 的詳細資訊，請參閱 [Windows Form 和 Unmanaged 應用程式](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)。 如果您使用 Visual Studio，可以停用 Visual Studio 的裝載處理序，以避免這個例外狀況，請參閱 [如何：停用裝載處理序](../Topic/How%20to:%20Disable%20the%20Hosting%20Process.md)。  
  
## 對 Windows Forms 控制項進行安全執行緒呼叫  
  
#### 對 Windows Forms 控制項進行安全執行緒呼叫  
  
1.  查詢控制項的 <xref:System.Windows.Forms.Control.InvokeRequired%2A> 屬性。  
  
2.  如果 <xref:System.Windows.Forms.Control.InvokeRequired%2A> 傳回 `true`，請使用對控制項進行實際呼叫的委派呼叫 <xref:System.Windows.Forms.Control.Invoke%2A>。  
  
3.  如果 <xref:System.Windows.Forms.Control.InvokeRequired%2A> 傳回 `false`，請直接呼叫控制項。  
  
 下列程式碼範例中，會在 `ThreadProcSafe` 方法中實作安全執行緒的呼叫，此方法是由背景執行緒執行。 如果 <xref:System.Windows.Forms.TextBox> 控制項的 <xref:System.Windows.Forms.Control.InvokeRequired%2A> 傳回 `true`，則 `ThreadProcSafe` 方法會建立 `SetTextCallback` 的執行個體，並將它傳遞給表單的 <xref:System.Windows.Forms.Control.Invoke%2A> 方法。 這會導致在建立 `SetText` 控制項的執行緒上呼叫 <xref:System.Windows.Forms.TextBox> 方法，並在這個執行緒內容中直接設定 <xref:System.Windows.Forms.Control.Text%2A> 屬性。  
  
 [!code-cpp[System.Windows.Forms.CrossThreadCalls#7](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/cpp/Form1.cpp#7)]
 [!code-csharp[System.Windows.Forms.CrossThreadCalls#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.CrossThreadCalls#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/VB/Form1.vb#7)]  
  
 [!code-cpp[System.Windows.Forms.CrossThreadCalls#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/cpp/Form1.cpp#3)]
 [!code-csharp[System.Windows.Forms.CrossThreadCalls#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.CrossThreadCalls#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/VB/Form1.vb#3)]  
  
 [!code-cpp[System.Windows.Forms.CrossThreadCalls#8](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/cpp/Form1.cpp#8)]
 [!code-csharp[System.Windows.Forms.CrossThreadCalls#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/CS/Form1.cs#8)]
 [!code-vb[System.Windows.Forms.CrossThreadCalls#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/VB/Form1.vb#8)]  
  
## 使用 BackgroundWorker 進行安全執行緒呼叫  
 在應用程式中實作多執行緒的慣用方法是使用 <xref:System.ComponentModel.BackgroundWorker> 元件。<xref:System.ComponentModel.BackgroundWorker> 元件使用事件驅動的模型來進行多執行緒處理。 背景執行緒會執行您的 <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件處理常式，而建立控制項的執行緒會執行您的 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 和 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 事件處理常式。 您可以從 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 和 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 事件處理常式呼叫控制項。  
  
#### 使用 BackgroundWorker 進行安全執行緒呼叫  
  
1.  建立方法來執行您想要在背景執行緒完成的工作。 請勿在這個方法中呼叫主執行緒所建立的控制項。  
  
2.  建立在背景工作完成後報告其結果之方法。 您可以在這個方法中呼叫主執行緒所建立的控制項。  
  
3.  將步驟 1 中建立的方法繫結到 <xref:System.ComponentModel.BackgroundWorker.DoWork> 執行個體的 <xref:System.ComponentModel.BackgroundWorker> 事件，並將步驟 2 中建立的方法繫結至相同執行個體的 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 事件。  
  
4.  若要啟動背景執行緒，請呼叫 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 執行個體的 <xref:System.ComponentModel.BackgroundWorker> 方法。  
  
 在下列程式碼範例中，<xref:System.ComponentModel.BackgroundWorker.DoWork> 事件處理常式會使用 <xref:System.Threading.Thread.Sleep%2A> 來模擬耗費時間的工作。 它不會呼叫表單的 <xref:System.Windows.Forms.TextBox> 控制項。<xref:System.Windows.Forms.TextBox> 控制項的 <xref:System.Windows.Forms.Control.Text%2A> 屬性直接設定在 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 事件處理常式中。  
  
 [!code-cpp[System.Windows.Forms.CrossThreadCalls#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/cpp/Form1.cpp#5)]
 [!code-csharp[System.Windows.Forms.CrossThreadCalls#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/CS/Form1.cs#5)]
 [!code-vb[System.Windows.Forms.CrossThreadCalls#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/VB/Form1.vb#5)]  
  
 [!code-cpp[System.Windows.Forms.CrossThreadCalls#9](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/cpp/Form1.cpp#9)]
 [!code-csharp[System.Windows.Forms.CrossThreadCalls#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/CS/Form1.cs#9)]
 [!code-vb[System.Windows.Forms.CrossThreadCalls#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/VB/Form1.vb#9)]  
  
 您也可以使用 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件報告背景工作的進度。 如需包含該事件的範例，請參閱 <xref:System.ComponentModel.BackgroundWorker>。  
  
## 範例  
 下列程式碼範例是完整的 Windows Forms 應用程式，此應用程式由具有三個按鈕和一個文字方塊的表單所組成。 第一個按鈕示範不安全的跨執行緒存取，第二個按鈕示範使用 <xref:System.Windows.Forms.Control.Invoke%2A> 的安全存取，第三個按鈕示範使用 <xref:System.ComponentModel.BackgroundWorker> 的安全存取。  
  
> [!NOTE]
>  如需如何執行範例的指示，請參閱 [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/zh-tw/cc447f7e-4c3b-4397-9d05-aeba3ca49416)。 此範例必須參考 System.Drawing 和 System.Windows.Forms 組件。  
  
 [!code-cpp[System.Windows.Forms.CrossThreadCalls#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/cpp/Form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.CrossThreadCalls#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.CrossThreadCalls#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/VB/Form1.vb#1)]  
  
 當您執行應用程式，並按一下 \[不安全的呼叫\] 按鈕時，您會立即在文字方塊中看到「由主執行緒寫入」。 兩秒之後，嘗試不安全的呼叫時，Visual Studio 偵錯工具會指出發生例外狀況。 偵錯工具會停止在背景執行緒嘗試直接寫入文字方塊的那行。 您必須重新啟動應用程式來測試其他兩個按鈕。 當您按下 \[安全呼叫\] 按鈕時，文字方塊中會出現「由主執行緒寫入」。 兩秒之後，文字方塊會設定為「由背景執行緒 \(Invoke\) 寫入」，這表示呼叫了 <xref:System.Windows.Forms.Control.Invoke%2A> 方法。 當您按下 \[安全 BW 呼叫\] 按鈕時，文字方塊中會出現「由主執行緒寫入」。 兩秒之後，文字方塊設定為「由主執行緒在背景執行緒完成後寫入」，這表示呼叫了 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 的 <xref:System.ComponentModel.BackgroundWorker> 事件的處理常式。  
  
## 穩固程式設計  
  
> [!CAUTION]
>  當您使用任何類型的多執行緒處理時，您的程式碼很有可能會暴露在非常嚴重且複雜的錯誤下。 如需詳細資訊，請參閱 [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md)，再實作使用多執行緒處理的任何解決方案。  
  
## 請參閱  
 <xref:System.ComponentModel.BackgroundWorker>   
 [如何：在背景執行作業](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)   
 [如何：實作使用背景作業的表單](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)   
 [使用 .NET Framework 開發自訂的 Windows Form 控制項](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)   
 [Windows Form 和 Unmanaged 應用程式](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)