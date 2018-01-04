---
title: "如何：在背景中下載檔案"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9b7bc5ae-051c-4904-9720-18f6667388bd
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 875ad9a17078865c526770587d36b1db1adf378c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-download-a-file-in-the-background"></a>如何：在背景中下載檔案
下載檔案是常見的工作，在不同執行緒上執行這種可能很耗時的作業通常會相當實用。 使用 <xref:System.ComponentModel.BackgroundWorker> 元件，以非常少的程式碼來完成這項工作。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用 <xref:System.ComponentModel.BackgroundWorker> 元件從 URL 載入 XML 檔案。 當使用者按一下**下載** 按鈕，<xref:System.Windows.Forms.Control.Click>事件處理常式呼叫<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>方法<xref:System.ComponentModel.BackgroundWorker>元件來啟動下載作業。 按鈕會在下載期間停用，然後當下載完成時再啟用。 <xref:System.Windows.Forms.MessageBox> 會顯示檔案的內容。  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#1)]  
  
 **下載檔案**  
  
 檔案會在 <xref:System.ComponentModel.BackgroundWorker> 元件的背景工作執行緒上下載，該執行緒會執行 <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件處理常式。 當您的程式碼呼叫 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 方法時，會啟動此執行緒。  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#3)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#3)]  
  
 **等候 BackgroundWorker 完成**  
  
 `downloadButton_Click` 事件處理常式會示範如何等候 <xref:System.ComponentModel.BackgroundWorker> 元件完成其非同步工作。  
  
 如果您只想要讓應用程式回應事件，並不想要在等候背景執行緒完成時，於主執行緒中執行任何工作，則直接結束這個處理常式即可。  
  
 如果您想要繼續進行主執行緒中的工作，請使用 <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> 屬性來判斷 <xref:System.ComponentModel.BackgroundWorker> 執行緒是否仍在執行中。 在本範例中，當正在處理下載時，會更新進度列。 請確定呼叫 <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> 方法，以保留 UI 回應性。  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#2)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#2)]  
  
 **顯示結果**  
  
 `backgroundWorker1_RunWorkerCompleted` 方法會處理 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 事件，會在背景作業完成時被呼叫。 這個方法會先檢查 <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> 屬性。 如果 <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> 是 `null`，則這個方法會顯示檔案的內容。 然後會啟用開始下載時被停用的下載按鈕，並重設其進度列。  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#4)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System.Drawing、System.Windows.Forms 和 System.Xml 組件的參考。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置命令列](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Forms 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## <a name="robust-programming"></a>穩固程式設計  
 請務必檢查您 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 事件處理常式中的 <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> 屬性，再嘗試存取可能會受 <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件處理常式影響的 <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> 屬性或任何其他物件。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.ComponentModel.BackgroundWorker>  
 [操作說明：在背景執行作業](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [操作說明：實作使用背景作業的表單](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
