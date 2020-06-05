---
title: Async
ms.date: 07/20/2015
f1_keywords:
- vb.Async
helpviewer_keywords:
- Async [Visual Basic]
- Async keyword [Visual Basic]
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
ms.openlocfilehash: 35df7a464937647c6d110142a3e2801cebbea505
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373150"
---
# <a name="async-visual-basic"></a>Async (Visual Basic)

`Async`修飾詞表示它修改的方法或[lambda 運算式](../../programming-guide/language-features/procedures/lambda-expressions.md)是非同步。 這類方法稱為「*非同步方法*」。

非同步方法提供了方便進行可能需要長時間執行之工作的方式，而不需封鎖呼叫端的執行緒。 非同步方法的呼叫端可以繼續其工作，而不需要等待非同步方法完成。

> [!NOTE]
> `Async` 和 `Await` 關鍵字是在 Visual Studio 2012 中引入。 如需非同步程式設計的簡介，請參閱[使用 async 和 Await 進行非同步程式設計](../../programming-guide/concepts/async/index.md)。

以下範例將示範非同步方法的結構。 依照慣例，非同步方法的名稱會以 "Async" 結尾。

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

通常，由關鍵字修改的方法 `Async` 至少包含一個[Await](async.md)運算式或語句。 方法會以同步方式執行，直到達到第一個 `Await`，此時它會暫止，直到等候的工作完成。 同時，控制權會返回方法的呼叫端。 如果方法不包含 `Await` 運算式或語句，則方法不會暫止，而且會以同步方法執行。 編譯器警告會對不包含的任何非同步方法發出警示， `Await` 因為這種情況可能表示發生錯誤。 如需詳細資訊，請參閱[編譯器錯誤](../error-messages/bc42358.md)。

`Async` 關鍵字是未保留的關鍵字。 它是修飾方法或 Lambda 運算式時的關鍵字。 在所有其他內容中，它會解譯為識別項。

## <a name="return-types"></a>傳回型別

非同步方法是[Sub](../../programming-guide/language-features/procedures/sub-procedures.md)程式，或傳回類型為或[的函](../../programming-guide/language-features/procedures/function-procedures.md)式程式 <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> 。 方法無法宣告任何[ByRef](byref.md)參數。

`Task(Of TResult)`如果方法的[return](../statements/return-statement.md)語句具有 TResult 類型的運算元，您可以指定非同步方法的傳回型別。 如果方法完成時未傳回任何有意義的值，則使用 `Task`。 也就是說，呼叫方法會傳回 `Task`，但是當 `Task` 完成時，任何等候 `Await` 的 `Task` 陳述式都不會產生結果值。

Async 副程式主要是用來定義需要 `Sub` 程序的事件處理常式。 非同步副程式的呼叫端無法等候它，而且無法攔截方法擲回的例外狀況。

如需詳細資訊和範例，請參閱[非同步方法的傳回型別](../../programming-guide/concepts/async/async-return-types.md)。

## <a name="example"></a>範例

下列範例將示範非同步事件處理常式、非同步 Lambda 運算式及非同步方法。 如需使用這些元素的完整範例，請參閱[逐步解說：使用 Async 和 Await 存取 Web](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。 您可以從[開發人員程式碼範例](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)下載逐步解說程式碼。

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
'      Dim result As Byte() = Await GetURLContents("https://msdn.com")
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

## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [Await 運算子](../operators/await-operator.md)
- [使用 Async 和 Await 進行非同步程式設計](../../programming-guide/concepts/async/index.md)
- [逐步解說：使用 Async 和 Await 存取 Web](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
