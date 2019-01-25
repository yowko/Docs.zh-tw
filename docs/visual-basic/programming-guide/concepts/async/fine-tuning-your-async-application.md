---
title: 微調非同步應用程式 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: 0dc03e1063b16c96916d4cac9214ddfa3333620b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625152"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a>微調非同步應用程式 (Visual Basic)
您可以使用 <xref:System.Threading.Tasks.Task> 類型所提供的方法和屬性，來增加非同步應用程式的精確度和彈性。 本節的主題會示範使用 <xref:System.Threading.CancellationToken> 以及 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> 等重要 `Task` 方法的範例。  
  
 您可以使用 `WhenAny` 和 `WhenAll`，更輕鬆地啟動多個工作，並藉由監視單一工作等候其完成。  
  
-   `WhenAny` 會在集合中的任何工作完成時，傳回一個完成的工作。  
  
     如需範例，使用`WhenAny`，請參閱 <<c2> [ 後一個 Is Complete (Visual Basic) 取消剩餘的非同步工作](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)並[啟動多項非同步工作和程序它們完成時進行 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)。  
  
-   `WhenAll` 會在集合中的所有工作完成時，傳回一個完成的工作。  
  
     如需詳細資訊和範例會使用`WhenAll`，請參閱[How to:使用 Task.WhenAll (Visual Basic) 來擴充非同步逐步解說](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)。  
  
 本節包含下列範例。  
  
-   [取消一項非同步工作或一份工作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)。  
  
-   [一段時間 (Visual Basic) 後取消非同步工作](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [當取消剩餘的非同步工作是完成 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [啟動多項非同步工作並處理完成 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  若要執行範例，您必須在電腦上安裝 Visual Studio 2012 或更新版本以及 .NET Framework 4.5 或更新版本。  
  
 這些專案會建立 UI，其中包含一個啟動處理序的按鈕和一個取消處理序的按鈕，如下圖所示。 這兩個按鈕的名稱分別是 `startButton` 和 `cancelButton`。  
  
 ![具有 [取消] 按鈕的 WPF 視窗](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "取消")  
  
 您可以下載完整 Windows Presentation Foundation (WPF) 專案從[非同步範例：順利微調您的應用程式](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)。  
  
## <a name="see-also"></a>另請參閱
- [使用 Async 和 Await 進行非同步程式設計 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
