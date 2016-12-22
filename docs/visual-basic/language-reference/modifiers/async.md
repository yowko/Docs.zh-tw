---
title: "Async (Visual Basic) | Microsoft Docs"
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
  - "vb.Async"
helpviewer_keywords: 
  - "Async [Visual Basic]"
  - "Async keyword [Visual Basic]"
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
caps.latest.revision: 37
caps.handback.revision: 37
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Async (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`Async` 修飾詞表示修改的方法或 [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) 是非同步的。  這種方法稱為 *非同步方法*。  
  
 非同步方法提供便利的方式進行可能需要長期執行的工作，而不封鎖呼叫端的執行緒。  非同步方法的呼叫端可以繼續其工作，而不需等待非同步方法。  
  
> [!NOTE]
>  `Async` 與 `Await` 關鍵字在 Visual Studio 2012 中引入。  如需非同步程式設計的簡介，請參閱[使用 Async 和 Await 設計非同步程式](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)。  
  
 以下範例顯示非同步方法的結構。  依照慣例，非同步方法名稱以「Async」結尾。  
  
```vb  
  
Public Async Function ExampleMethodAsync() As Task(Of Integer)  
    ' . . .  
  
    ' At the Await expression, execution in this method is suspended and,  
    ' if AwaitedProcessAsync has not already finished, control returns  
    ' to the caller of ExampleMethodAsync. When the awaited task is   
    ' completed, this method resumes execution.   
    Dim exampleInt As Integer = Await AwaitedProcessAsync()  
  
    ' . . .  
  
    ' The return statement completes the task. Any method that is   
    ' awaiting ExampleMethodAsync can now get the integer result.  
    Return exampleInt  
End Function  
```  
  
 `Async` 關鍵字修改的方法通常包含至少一個[Await](../../../visual-basic/language-reference/modifiers/async.md)運算式或陳述式。  此方法會以同步方式執行，直到到達第一個 `Await`，此時，它會暫止，直到等候的工作完成。  同時，控制權會返回非同步方法的呼叫端。  如果方法不包含 `Await` 運算式或陳述式，此方法不會逾時和並像一個同步方法一樣執行。  如果有任何非同步方法未包含 `Await`，編譯器會提出警告，因為這種情況可能表示錯誤。  如需更多詳細資訊，請參閱 [compiler error](../../../visual-basic/language-reference/error-messages/because-this-call-is-not-awaited-the-current-method-continues-to-run.md) 。  
  
 `Async` 是未保留的關鍵字。  它是修改方法或 Lambda 運算式時的關鍵字。  在所有其他內容中，將其解譯為識別碼。  
  
## 傳回類型  
 非同步方法是 [子函數](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) 程序或有 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601>的傳回型別 [函式](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) 的程序。  此方法不可以宣告任何 [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) 參數。  
  
 如果方法的 [Return](../../../visual-basic/language-reference/statements/return-statement.md) 陳述式指定 TResult 類型的運算元，您必須指定 `Task(Of TResult)` 做為非同步方法的傳回類型。  當方法完成時，如果未傳回有意義的值，您可以使用 `Task`。  也就是對方法的呼叫傳回，則為 `Task`，但是，當 `Task` 完成時，等候 `Task` 的任何 `Await` 陳述式不會產生結果值。  
  
 Async 副程式主要是用來定義需要 `Sub` 程序的事件處理常式。  非同步方法的呼叫端無法等候它，而且無法攔截方法擲回的例外狀況。  
  
 如需詳細資訊與範例，請參閱[非同步方法的傳回類型](../Topic/Async%20Return%20Types%20\(C%23%20and%20Visual%20Basic\).md)。  
  
## 範例  
 下列範例顯示一個非同步事件處理常式、非同步 Lambda 運算式和非同步方法。  如需使用類似項目的完整範例，請參閱[逐步解說：使用 Async 和 Await 存取 Web](../Topic/Walkthrough:%20Accessing%20the%20Web%20by%20Using%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)。  您可以從[開發人員程式碼範例](http://go.microsoft.com/fwlink/?LinkId=255191)下載逐步解說程式碼。  
  
```vb  
  
' An event handler must be a Sub procedure.  
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click  
    textBox1.Clear()  
    ' SumPageSizesAsync is a method that returns a Task.  
    Await SumPageSizesAsync()  
    textBox1.Text = vbCrLf & "Control returned to button1_Click."  
End Sub  
  
' The following async lambda expression creates an equivalent anonymous  
' event handler.  
AddHandler button1.Click, Async Sub(sender, e)  
                              textBox1.Clear()  
                              ' SumPageSizesAsync is a method that returns a Task.  
                              Await SumPageSizesAsync()  
                              textBox1.Text = vbCrLf & "Control returned to button1_Click."  
                          End Sub  
  
' The following async method returns a Task(Of T).  
' A typical call awaits the Byte array result:  
'      Dim result As Byte() = Await GetURLContents("http://msdn.com")  
Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
  
    ' The downloaded resource ends up in the variable named content.  
    Dim content = New MemoryStream()  
  
    ' Initialize an HttpWebRequest for the current URL.  
    Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
    ' Send the request to the Internet resource and wait for  
    ' the response.  
    Using response As WebResponse = Await webReq.GetResponseAsync()  
        ' Get the data stream that is associated with the specified URL.  
        Using responseStream As Stream = response.GetResponseStream()  
            ' Read the bytes in responseStream and copy them to content.    
            ' CopyToAsync returns a Task, not a Task<T>.  
            Await responseStream.CopyToAsync(content)  
        End Using  
    End Using  
  
    ' Return the result as a byte array.  
    Return content.ToArray()  
End Function  
  
```  
  
## 請參閱  
 <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>   
 [Await Operator](../../../visual-basic/language-reference/operators/await-operator.md)   
 [使用 Async 和 Await 設計非同步程式](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)   
 [逐步解說：使用 Async 和 Await 存取 Web](../Topic/Walkthrough:%20Accessing%20the%20Web%20by%20Using%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)