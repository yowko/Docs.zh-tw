---
title: HOW TO：同時發出多個 Web 要求，使用 Async 和 Await (Visual Basic)
ms.date: 07/20/2015
ms.assetid: a894b99b-7cfd-4a38-adfb-20d24f986730
ms.openlocfilehash: e306722fca4e0215cf7b67d85763858d459a171a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642435"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-visual-basic"></a>HOW TO：同時發出多個 Web 要求，使用 Async 和 Await (Visual Basic)
在非同步方法中，工作會在建立後啟動。 [Await](../../../../visual-basic/language-reference/operators/await-operator.md)運算子會套用到在方法中無法繼續處理直到工作完成的工作。 通常，工作會在建立後等候完成，如下列範例所示。  
  
```vb  
Dim result = Await someWebAccessMethodAsync(url)  
```  
  
 不過，如果您的程式有其他要完成的工作不需要等候此工作完成，您可以將建立工作與等候工作分開進行。  
  
```vb  
' The following line creates and starts the task.  
Dim myTask = someWebAccessMethodAsync(url)  
  
' While the task is running, you can do other work that does not depend  
' on the results of the task.  
' . . . . .  
  
' The application of Await suspends the rest of this method until the task is   
' complete.  
Dim result = Await myTask  
```  
  
 從工作啟動到等候完成的這段期間，您可以啟動其他工作。 其他工作會以隱含方式平行執行，但不會建立其他任何執行緒。  
  
 下列程式會啟動三個非同步的網頁下載，然後依呼叫順序等候完成。 請注意，當您執行此程式時，這些工作不一定會依建立和等候順序完成。 這些工作會在建立後開始執行，而且其中一或多個工作可能會在此方法到達 await 運算式之前就已完成。  
  
> [!NOTE]
>  若要完成此專案，您必須在電腦上安裝 Visual Studio 2012 或更高版本以及 .NET Framework 4.5 或更高版本。  
  
 如需同時啟動多個工作的其他範例，請參閱[如何：使用 Task.WhenAll (Visual Basic) 來擴充非同步逐步解說](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)。  
  
 您可以從[開發人員程式碼範例](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)下載此範例的程式碼。  
  
### <a name="to-set-up-the-project"></a>若要設定專案  
  
1. 若要設定 WPF 應用程式，請完成下列步驟。 您可以在[逐步解說：存取 Web 使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。  
  
    - 建立 WPF 應用程式，其中包含一個文字方塊和一個按鈕。 將按鈕命名為 `startButton`，並將文字方塊命名為 `resultsTextBox`。  
  
    - 加入 <xref:System.Net.Http> 的參考。  
  
    - 在 MainWindow.xaml.vb 檔案中，新增`Imports`陳述式`System.Net.Http`。  
  
### <a name="to-add-the-code"></a>新增程式碼  
  
1. 在設計視窗 MainWindow.xaml 中，連按兩下按鈕，以建立`startButton_Click`MainWindow.xaml.vb 中的事件處理常式。  
  
2. 下列程式碼中，複製並貼到主體`startButton_Click`MainWindow.xaml.vb 中。  
  
    ```vb  
    resultsTextBox.Clear()  
    Await CreateMultipleTasksAsync()  
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    ```  
  
     此程式碼會呼叫非同步方法 `CreateMultipleTasksAsync` 來驅動應用程式。  
  
3. 將下列支援方法新增至專案：  
  
    - `ProcessURLAsync` 使用 <xref:System.Net.Http.HttpClient> 方法，將網站內容下載為位元組陣列。 然後，支援方法 `ProcessURLAsync` 會顯示並傳回陣列的長度。  
  
    - `DisplayResults` 會顯示每個 URL 的位元組陣列中的位元組數目。 當每個工作完成下載時，即會顯示此畫面。  
  
     將下列方法，複製並貼上它們之後`startButton_Click`MainWindow.xaml.vb 中的事件處理常式。  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "https://".  
        Dim displayURL = url.Replace("https://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
    ```  
  
4. 最後，定義 `CreateMultipleTasksAsync` 方法以執行下列步驟。  
  
    - 方法宣告 `HttpClient` 物件，需要存取 `ProcessURLAsync` 中的方法<xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>。  
  
    - 方法會建立並啟動三個 <xref:System.Threading.Tasks.Task%601> 類型的工作，其中 `TResult` 是整數。 當每個工作完成時，`DisplayResults` 會顯示工作的 URL 和下載內容的長度。 因為工作是以非同步方式執行，所以結果出現的順序可能會因宣告的順序而有所不同。  
  
    - 此方法會等候每個工作完成。 每個 `Await` 運算子會暫停執行 `CreateMultipleTasksAsync`，直到等候的工作完成為止。 此運算子也會從每個完成的工作擷取透過呼叫 `ProcessURLAsync` 傳回的值。  
  
    - 完成工作並擷取整數值之後，此方法會加總網站的長度並顯示結果。  
  
     將下列方法複製並貼到您的方案中。  
  
    ```vb  
    Private Async Function CreateMultipleTasksAsync() As Task  
  
        ' Declare an HttpClient object, and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Create and start the tasks. As each task finishes, DisplayResults   
        ' displays its length.  
        Dim download1 As Task(Of Integer) =  
            ProcessURLAsync("https://msdn.microsoft.com", client)  
        Dim download2 As Task(Of Integer) =  
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)  
        Dim download3 As Task(Of Integer) =  
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client)  
  
        ' Await each task.  
        Dim length1 As Integer = Await download1  
        Dim length2 As Integer = Await download2  
        Dim length3 As Integer = Await download3  
  
        Dim total As Integer = length1 + length2 + length3  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
    ```  
  
5. 選擇 F5 鍵以執行程式，然後選擇 [ **開始** ] 按鈕。  
  
     執行此程式幾次，確認這三個工作不一定會依相同順序完成，而且其完成順序不一定是建立和等候順序。  
  
## <a name="example"></a>範例  
 下列程式碼包含完整的範例。  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
        resultsTextBox.Clear()  
        Await CreateMultipleTasksAsync()  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Private Async Function CreateMultipleTasksAsync() As Task  
  
        ' Declare an HttpClient object, and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Create and start the tasks. As each task finishes, DisplayResults   
        ' displays its length.  
        Dim download1 As Task(Of Integer) =  
            ProcessURLAsync("https://msdn.microsoft.com", client)  
        Dim download2 As Task(Of Integer) =  
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)  
        Dim download3 As Task(Of Integer) =  
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client)  
  
        ' Await each task.  
        Dim length1 As Integer = Await download1  
        Dim length2 As Integer = Await download2  
        Dim length3 As Integer = Await download3  
  
        Dim total As Integer = length1 + length2 + length3  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "https://".  
        Dim displayURL = url.Replace("https://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
End Class  
```  
  
## <a name="see-also"></a>另請參閱

- [逐步解說：存取 Web 使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [使用 Async 和 Await 進行非同步程式設計 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [如何：擴充非同步逐步解說使用 Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
