---
title: "How to: Use Components That Support the Event-based Asynchronous Pattern | Microsoft Docs"
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
  - "Event-based Asynchronous Pattern"
  - "ProgressChangedEventArgs class"
  - "BackgroundWorker component"
  - "events [.NET Framework], asynchronous"
  - "Asynchronous Pattern"
  - "AsyncOperationManager class"
  - "threading [.NET Framework], asynchronous features"
  - "components [.NET Framework], asynchronous"
  - "AsyncOperation class"
  - "threading [Windows Forms], asynchronous features"
  - "AsyncCompletedEventArgs class"
ms.assetid: 35e9549c-1568-4768-ad07-17cc6dff11e1
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# How to: Use Components That Support the Event-based Asynchronous Pattern
許多元件都會提供您以非同步的方式執行工作。  例如，<xref:System.Media.SoundPlayer> 和 <xref:System.Windows.Forms.PictureBox> 元件，就能讓您「從幕後」載入音效和影像，而不會中斷主執行緒同時繼續執行。  
  
 要對支援[Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)的類別使用非同步方法，就像處理其他任何事件一樣簡單，只要將事件處理常式附加到元件的 *MethodName*`Completed` 事件即可。  當您呼叫 *MethodName*`Async` 方法時，直到引發 *MethodName*`Completed` 事件為止，應用程式都會繼續執行而不中斷。  在事件處理常式中，您可以檢查 <xref:System.ComponentModel.AsyncCompletedEventArgs> 參數以判斷非同步作業 \(Asynchronous Operation\) 是否成功完成，或是已經取消。  
  
 如需使用事件處理常式的詳細資訊，請參閱[事件處理常式概觀](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)。  
  
 下列程序會示範如何使用 <xref:System.Windows.Forms.PictureBox> 控制項的非同步影像載入功能。  
  
### 若要啟用 PictureBox 控制項以非同步方式載入影像  
  
1.  在您的表單中建立 <xref:System.Windows.Forms.PictureBox> 元件的執行個體。  
  
2.  將事件處理常式指派給 <xref:System.Windows.Forms.PictureBox.LoadCompleted> 事件。  
  
     請在此檢查進行非同步下載時可能發生的任何錯誤。  這也是您檢查取消的地方。  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3.  將稱為 `loadButton` 和 `cancelLoadButton` 的兩個按鈕加入表單中。  加入 <xref:System.Windows.Forms.Control.Click> 事件處理常式以啟動和取消下載。  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4.  執行您的應用程式。  
  
     在進行影像下載時，您可以隨意移動表單、最小化表單，以及最大化表單。  
  
## 請參閱  
 [如何：在背景執行作業](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)   
 [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)   
 [NOT IN BUILD: Multithreading in Visual Basic](http://msdn.microsoft.com/zh-tw/c731a50c-09c1-4468-9646-54c86b75d269)