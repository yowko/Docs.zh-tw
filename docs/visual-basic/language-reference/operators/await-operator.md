---
title: "Await 運算子 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
caps.latest.revision: 30
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b50b9c7283ddd4d3f8484854bdffff3d76181c9f
ms.lasthandoff: 03/13/2017

---
# <a name="await-operator-visual-basic"></a>Await 運算子 (Visual Basic)
您在非同步方法或 Lambda 運算式的運算元中套用 `Await` 運算子，讓方法暫停執行，直到等候的工作完成。 工作代表進行中的工作。  
  
 此方法用於`Await`用必須[非同步](../../../visual-basic/language-reference/modifiers/async.md)修飾詞。 這種方法，定義使用`Async`修飾詞，以及通常包含一或多個`Await`運算式中，稱為*非同步方法*。  
  
> [!NOTE]
>  `Async` 和 `Await` 關鍵字是在 Visual Studio 2012 中引入。 非同步程式設計的簡介，請參閱[使用 Async 和 Await 進行非同步程式設計](../../../visual-basic/programming-guide/concepts/async/index.md)。  
  
 一般而言，您要套用的工作`Await`運算子是實作的方法呼叫的傳回值[工作架構非同步模式](http://go.microsoft.com/fwlink/?LinkId=204847)，亦即，<xref:System.Threading.Tasks.Task>或<xref:System.Threading.Tasks.Task%601>。</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task>  
  
 下列程式碼，<xref:System.Net.Http.HttpClient>方法<xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>傳回`getContentsTask`、 `Task(Of Byte())`。</xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> </xref:System.Net.Http.HttpClient> 這個工作可保證作業完成時，一定會產生實際位元組陣列。 `Await` 運算子會套用至 `getContentsTask` 以暫停在 `SumPageSizesAsync` 中執行，直到 `getContentsTask` 完成。 同時，控制權會返回 `SumPageSizesAsync` 的呼叫端。 當 `getContentsTask` 完成之後，`Await` 運算式會評估為位元組陣列。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
> [!IMPORTANT]
>  完整的範例，請參閱[逐步解說︰ 存取 Web 使用 Async 和 Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。 您可以下載從範例[開發人員程式碼範例](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409)Microsoft 網站上。 此範例位於 AsyncWalkthrough_HttpClient 專案中。  
  
 如果將 `Await` 套用至傳回 `Task(Of TResult)` 之方法呼叫的結果，則 `Await` 運算式的類型為 TResult。 如果 `Await` 套用至傳回 `Task` 之方法呼叫的結果，則 `Await` 運算式不會傳回值。 下列範例會說明其間的差異。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 `Await` 運算式或陳述式不會封鎖其執行所在的執行緒。 但是它會造成編譯器將 `Await` 運算式之後的其餘非同步方法註冊為所等候工作的接續。 控制權接著會返回非同步方法的呼叫端。 當工作完成時，它會叫用其接續，並從中斷處繼續執行非同步方法。  
  
 `Await` 運算式可能只會在 `Async` 修飾詞所標示之立即封入方法或 Lambda 運算式主體中發生。 這個詞彙*Await*做為關鍵字只在該內容。 在其他內容中，它會解譯為識別項。 在非同步方法或 lambda 運算式`Await`運算式不能出現在查詢運算式中，在`catch`或`finally`區塊[試...Catch...最後](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)的迴圈控制變數運算式中的陳述式，`For`或`For Each`迴圈，或在本文中[SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md)陳述式。  
  
## <a name="exceptions"></a>例外狀況  
 大部分的非同步方法會傳回<xref:System.Threading.Tasks.Task>或<xref:System.Threading.Tasks.Task%601>。</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task> 傳回的工作屬性會隨附其狀態和記錄的相關資訊，例如工作是否完成、非同步方法是否造成例外狀況或已取消，以及最終結果為何。 `Await` 運算子存取這些屬性。  
  
 如果您在等候工作傳回非同步方法時導致例外狀況，`Await` 運算子會重新擲回例外狀況。  
  
 如果您等候已取消的工作傳回非同步方法`Await`運算子會重新擲回<xref:System.OperationCanceledException>.</xref:System.OperationCanceledException>  
  
 處於錯誤狀態的單一工作可能反映多個例外狀況。  例如，工作可能是<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>。</xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>呼叫的結果 當您等候這類工作時，await 作業只會重新擲回其中一個例外狀況。 不過，您無法預測重新擲回哪個例外狀況。  
  
 例如非同步方法中的錯誤處理的詳細資訊，請參閱[試...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
## <a name="example"></a>範例  
 下列 Windows Form 範例說明如何在非同步方法 `WaitAsynchronouslyAsync` 中使用 `Await`。 請對照該方法的行為與 `WaitSynchronously` 的行為。 不含`Await`運算子，`WaitSynchronously`會同步執行，就算使用`Async`修飾詞，在其定義，以及呼叫<xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName>其主體中。</xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName>  
  
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
 [非同步程式設計使用 Async 和 Await](../../../visual-basic/programming-guide/concepts/async/index.md)   
 [逐步解說︰ 存取 Web 使用 Async 和 Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
 [Async](../../../visual-basic/language-reference/modifiers/async.md)
