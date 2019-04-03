---
title: Await 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
ms.openlocfilehash: d9d50433e3bc24df7cda137a145ab3f0f0302a1f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841975"
---
# <a name="await-operator-visual-basic"></a>Await 運算子 (Visual Basic)
您在非同步方法或 Lambda 運算式的運算元中套用 `Await` 運算子，讓方法暫停執行，直到等候的工作完成。 工作代表進行中的工作。  
  
 此方法用於`Await`會使用必須要有[非同步](../../../visual-basic/language-reference/modifiers/async.md)修飾詞。 這種方法是使用 `Async` 修飾詞所定義，且通常包含一或多個 `Await` 運算式，我們稱之為「非同步方法」。  
  
> [!NOTE]
>  `Async` 和 `Await` 關鍵字是在 Visual Studio 2012 中引入。 如需非同步程式設計的簡介，請參閱[使用 Async 和 Await 進行非同步程式設計](../../../visual-basic/programming-guide/concepts/async/index.md)。  
  
 一般而言，您要套用工作`Await`運算子會實作的方法呼叫的傳回值[工作架構非同步模式](https://go.microsoft.com/fwlink/?LinkId=204847)，也就是<xref:System.Threading.Tasks.Task>或<xref:System.Threading.Tasks.Task%601>。  
  
 在下列程式碼中，<xref:System.Net.Http.HttpClient> 方法 <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> 會傳回 `getContentsTask`，也就是 `Task(Of Byte())`。 這個工作可保證作業完成時，一定會產生實際位元組陣列。 `Await` 運算子會套用至 `getContentsTask` 以暫停在 `SumPageSizesAsync` 中執行，直到 `getContentsTask` 完成。 同時，控制權會返回 `SumPageSizesAsync` 的呼叫端。 當 `getContentsTask` 完成之後，`Await` 運算式會評估為位元組陣列。  
  
```vb  
Private Async Function SumPageSizesAsync() As Task  
  
    ' To use the HttpClient type in desktop apps, you must include a using directive and add a   
    ' reference for the System.Net.Http namespace.  
    Dim client As HttpClient = New HttpClient()   
    ' . . .   
    Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
    Dim urlContents As Byte() = Await getContentsTask  
  
    ' Equivalently, now that you see how it works, you can write the same thing in a single line.  
    'Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
    ' . . .  
End Function  
```  
  
> [!IMPORTANT]
>  如需完整的範例，請參閱[逐步解說：使用 Async 和 Await 存取 Web](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。 您可以從 Microsoft 網站的[開發人員程式碼範例](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) 下載此範例。 此範例位於 AsyncWalkthrough_HttpClient 專案中。  
  
 如果將 `Await` 套用至傳回 `Task(Of TResult)` 之方法呼叫的結果，則 `Await` 運算式的類型為 TResult。 如果 `Await` 套用至傳回 `Task` 之方法呼叫的結果，則 `Await` 運算式不會傳回值。 下列範例會說明其間的差異。  
  
```vb  
' Await used with a method that returns a Task(Of TResult).  
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()  
  
' Await used with a method that returns a Task.  
Await AsyncMethodThatReturnsTask()  
```  
  
 `Await` 運算式或陳述式不會封鎖其執行所在的執行緒。 但是它會造成編譯器將 `Await` 運算式之後的其餘非同步方法註冊為所等候工作的接續。 控制權接著會返回非同步方法的呼叫端。 當工作完成時，它會叫用其接續，並從中斷處繼續執行非同步方法。  
  
 `Await` 運算式可能只會在 `Async` 修飾詞所標示之立即封入方法或 Lambda 運算式主體中發生。 詞彙*Await*做為關鍵字只在該內容中。 在其他內容中，它會解譯為識別項。 在非同步方法或 lambda 運算式中，`Await`運算式不能出現在查詢運算式中，`catch`或是`finally`區塊[試...Catch...最後](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)中的迴圈控制變數運算式的陳述式，`For`或是`For Each`迴圈，或主體中[SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md)陳述式。  
  
## <a name="exceptions"></a>例外狀況  
 大部分的非同步方法會傳回 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601>。 傳回的工作屬性會隨附其狀態和記錄的相關資訊，例如工作是否完成、非同步方法是否造成例外狀況或已取消，以及最終結果為何。 `Await` 運算子存取這些屬性。  
  
 如果您在等候工作傳回非同步方法時導致例外狀況，`Await` 運算子會重新擲回例外狀況。  
  
 如果您等候已取消的工作傳回非同步方法，則 `Await` 運算子會重新擲回 <xref:System.OperationCanceledException>。  
  
 處於錯誤狀態的單一工作可能反映多個例外狀況。  例如，工作可能是對 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 呼叫的結果。 當您等候這類工作時，await 作業只會重新擲回其中一個例外狀況。 不過，您無法預測重新擲回哪個例外狀況。  
  
 如需非同步方法中的錯誤處理的範例，請參閱[試...Catch...Try...catch...finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
## <a name="example"></a>範例  
 下列 Windows Form 範例說明如何在非同步方法 `WaitAsynchronouslyAsync` 中使用 `Await`。 請對照該方法的行為與 `WaitSynchronously` 的行為。 若沒有 `Await` 運算子，儘管在定義中使用 `WaitSynchronously` 修飾詞並在主體中呼叫 `Async`，<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> 仍會以同步方式執行。  
  
```vb  
Private Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
    ' Call the method that runs asynchronously.  
    Dim result As String = Await WaitAsynchronouslyAsync()  
  
    ' Call the method that runs synchronously.  
    'Dim result As String = Await WaitSynchronously()  
  
    ' Display the result.  
    TextBox1.Text &= result  
End Sub  
  
' The following method runs asynchronously. The UI thread is not  
' blocked during the delay. You can move or resize the Form1 window   
' while Task.Delay is running.  
Public Async Function WaitAsynchronouslyAsync() As Task(Of String)  
    Await Task.Delay(10000)  
    Return "Finished"  
End Function  
  
' The following method runs synchronously, despite the use of Async.  
' You cannot move or resize the Form1 window while Thread.Sleep  
' is running because the UI thread is blocked.  
Public Async Function WaitSynchronously() As Task(Of String)  
    ' Import System.Threading for the Sleep method.  
    Thread.Sleep(10000)  
    Return "Finished"  
End Function  
```  
  
## <a name="see-also"></a>另請參閱

- [使用 Async 和 Await 進行非同步程式設計](../../../visual-basic/programming-guide/concepts/async/index.md)
- [逐步解說：使用 Async 和 Await 存取 Web](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Async](../../../visual-basic/language-reference/modifiers/async.md)
