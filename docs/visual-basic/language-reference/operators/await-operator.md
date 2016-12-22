---
title: "Await Operator (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Await"
helpviewer_keywords: 
  - "Await operator [Visual Basic]"
  - "Await [Visual Basic]"
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Await Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

您在非同步方法或 Lambda 運算式的運算域中使用 `Await` 運算子以擱置方法的執行，直到等候的工作完成。  工作代表進行中的工作。  
  
 `Await` 所使用的方法必須有 [Async](../../../visual-basic/language-reference/modifiers/async.md) 修飾詞。  這種方法，透過使用 `Async` 修飾詞來定義和通常包含一或多個 `Await` 運算式，稱為「*非同步方法*」\(async method\)。  
  
> [!NOTE]
>  `Async` 與 `Await` 關鍵字在 Visual Studio 2012 中引入。  如需非同步程式設計的簡介，請參閱[使用 Async 和 Await 設計非同步程式](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)。  
  
 `Await` 運算子套用的工作通常是實作[以工作為基礎的非同步模式](http://go.microsoft.com/fwlink/?LinkId=204847)的方法呼叫之傳回值，也就是說是 <xref:System.Threading.Tasks.Task> 或是 <xref:System.Threading.Tasks.Task%601>。  
  
 在下列程式碼中，<xref:System.Net.Http.HttpClient> 方法 <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> 會傳回 `getContentsTask`、`Task(Of Byte())`。  這個工作保證作業完成時，一定會產生實際位元組陣列。  `Await` 運算子套用至 `getContentsTask` 以暫停 `SumPageSizesAsync` 中的執行，直到 `getContentsTask` 完成。  同時，控制項會返回 `SumPageSizesAsync` 的呼叫端。  當 `getContentsTask` 完成時，`Await` 運算式評估為位元組陣列。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
> [!IMPORTANT]
>  如需完整的範例，請參閱 [逐步解說：使用 Async 和 Await 存取 Web](../Topic/Walkthrough:%20Accessing%20the%20Web%20by%20Using%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)。  您可以從Microsoft 網站上的[開發人員程式碼範例](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409)下載範例。  這個範例是在 AsyncWalkthrough\_HttpClient 專案中。  
  
 如果將 `Await` 套用至傳回 `Task(Of TResult)` 之方法呼叫的結果，則 `Await` 運算式的類型為 TResult。  如果 `Await` 套用至傳回 `Task` 之方法呼叫的結果，則 `Await` 運算式不會傳回值。  下列範例說明差異。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 `Await` 運算式或陳述式不會封鎖其執行所在的執行緒。  相反地，它會造成編譯器將在運算式之後其餘的非同步方法\(在 `Await` 運算式之後的\)註冊為被等候工作的接續。  控制權會返回非同步方法的呼叫端。  當工作完成時，它會叫用其接續，而且非同步方法的執行會從先前暫停的地方繼續。  
  
 `Await` 運算式可能只會在 `Async` 修飾詞所標示之立即封入方法或Lambda 運算式的主體中發生。  「*等候*」\(await\) 這個詞彙只在該內容中做為關鍵字。  在其他位置，則會將它解譯為識別碼。  在非同步方法或 Lambda 運算式中， `Await` 運算式不能出現在查詢運算式、 [Try…Catch…Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) 陳述式中的 `catch` 或 `finally` 區塊、 `For` 或 `For Each` 迴圈中的迴圈控制變數運算式中、或在 [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) 陳述式的主體中。  
  
## 例外狀況  
 大部分非同步方法會傳回 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601>。  傳回的工作屬性含有其狀態和記錄的資訊，例如工作是否完成，非同步方法是否造成例外狀況或被取消，以及最後結果。  `Await` 運算子存取這些屬性。  
  
 如果等候造成例外狀況的工作傳回非同步方法，則 `Await` 運算子會重新擲回例外狀況。  
  
 如果您等候已取消之工作傳回非同步方法，則 `Await` 運算子會重新擲回 <xref:System.OperationCanceledException>。  
  
 處於錯誤狀態的單一工作可能反映多個例外狀況。例如，工作可能是呼叫 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> 的結果。  當您等候這類工作時，等候作業只擲回其中一個例外狀況。  不過，您無法預測會重新擲回哪一個例外狀況。  
  
 如需非同步方法錯誤處理的範例，請參閱 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
## 範例  
 下列 Windows Form 範例示範在非同步方法 `WaitAsynchronouslyAsync` 中 `Await` 的用法。  將該方法的表現方式對照 `WaitSynchronously` 的表現方式。  若`WaitSynchronously` 沒有 `Await` 運算子，儘管其定義使用 `Async` 修飾詞並在主體呼叫 <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName>，它仍會同步執行。  
  
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
  
## 請參閱  
 [使用 Async 和 Await 設計非同步程式](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)   
 [逐步解說：使用 Async 和 Await 存取 Web](../Topic/Walkthrough:%20Accessing%20the%20Web%20by%20Using%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)   
 [Async](../../../visual-basic/language-reference/modifiers/async.md)