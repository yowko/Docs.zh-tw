---
title: 如何：使用支援事件架構非同步模式的元件
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 35e9549c-1568-4768-ad07-17cc6dff11e1
ms.openlocfilehash: e11bf8af6f56cbdcdcc920cafe145edcf744efed
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003395"
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a>如何：使用支援事件架構非同步模式的元件
許多元件可讓您選擇以非同步方式執行其工作。 例如，<xref:System.Media.SoundPlayer> 和 <xref:System.Windows.Forms.PictureBox> 元件可讓您「在背景」載入音效和影像，同時主執行緒會繼續執行而不中斷。  
  
 對支援[事件架構非同步模式概觀](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)的類別使用非同步方法，就像處理其他任何事件一樣簡單，只要將事件處理常式附加到元件的 _MethodName_**Completed** 事件即可。 當您呼叫 _MethodName_**Async** 方法時，應用程式將會繼續執行而不中斷，直到引發 _MethodName_**Completed** 事件為止。 在事件處理常式中，您可以檢查 <xref:System.ComponentModel.AsyncCompletedEventArgs> 參數來判斷非同步作業已成功完成或已取消。  
  
 如需使用事件處理常式的詳細資訊，請參閱[事件處理常式概觀](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)。  
  
 下列程序示範如何使用 <xref:System.Windows.Forms.PictureBox> 控制項的非同步影像載入功能。  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a>啟用 PictureBox 控制項以非同步方式載入影像  
  
1.  建立表單中 <xref:System.Windows.Forms.PictureBox> 元件的執行個體。  
  
2.  將事件處理常式指派給 <xref:System.Windows.Forms.PictureBox.LoadCompleted>。  
  
     請檢查非同步下載期間是否發生任何任何錯誤。 您也可在此時檢查取消。  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3.  將稱為 `loadButton` 和 `cancelLoadButton` 的兩個按鈕加入至表單。 新增 <xref:System.Windows.Forms.Control.Click> 事件處理常式，以啟動和取消下載。  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4.  執行應用程式。  
  
     在進行影像下載時，您可以隨意移動表單、將它縮至最小以及最大化。  
  
## <a name="see-also"></a>另請參閱

- [操作說明：在背景執行作業](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
- [事件架構非同步模式概觀](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
