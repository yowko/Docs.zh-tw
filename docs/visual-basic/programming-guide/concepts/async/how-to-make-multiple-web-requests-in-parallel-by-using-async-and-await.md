---
title: "如何︰ 同時發出多個 Web 要求使用 Async 和 Await (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: a894b99b-7cfd-4a38-adfb-20d24f986730
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e4c41cc3813a9f96d944d115c6aaa5c5842a629b
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-visual-basic"></a>如何︰ 同時發出多個 Web 要求使用 Async 和 Await (Visual Basic)
在非同步方法，在建立時即會啟動工作。 [Await](../../../../visual-basic/language-reference/operators/await-operator.md)運算子會套用至方法中的點，而無法繼續處理直到工作完成工作。 通常工作會等候由於它建立，如下列範例所示。  
  
```vb  
Dim result = Await someWebAccessMethodAsync(url)  
```  
  
 不過，您可以將建立不相關的工作完成從等候工作，如果您的程式有其他工作来完成工作。  
  
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
  
 啟動工作和之間等候它，您可以啟動其他工作。 以平行方式，以隱含方式執行的其他工作，但沒有其他執行緒會建立。  
  
 下列程式會啟動三個非同步 web 下載項目，然後等候它們在所呼叫的順序。 請注意，當您執行的程式，工作不一定都他們所建立，以及等候完成。 便會開始執行時建立的與之前的方法到達 await 運算式，則可能會完成一或多個工作。  
  
> [!NOTE]
>  若要完成此專案，您必須擁有 Visual Studio 2012 或更新版本和.NET Framework 4.5 或更新版本安裝在電腦上。  
  
 如需同時啟動多個工作的其他範例，請參閱[How to︰ 擴充非同步逐步解說使用 Task.WhenAll (Visual Basic) 的](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)。  
  
 您可以下載這個範例中的程式碼[開發人員程式碼範例](http://go.microsoft.com/fwlink/?LinkId=254906)。  
  
### <a name="to-set-up-the-project"></a>若要設定專案  
  
1.  若要設定 WPF 應用程式，請完成下列步驟。 您可以找到這些步驟的詳細的指示[逐步解說︰ 存取 Web 使用 Async 和 Await (Visual Basic) 的](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。  
  
    -   建立 WPF 應用程式，其中包含一個文字方塊和按鈕。 將按鈕`startButton`，並將文字方塊`resultsTextBox`。  
  
    -   加入<xref:System.Net.Http>.</xref:System.Net.Http>的參考  
  
    -   在 MainWindow.xaml.vb 檔案中，加入`Imports`陳述式`System.Net.Http`。  
  
### <a name="to-add-the-code"></a>若要加入程式碼  
  
1.  在 [設計] 視窗，MainWindow.xaml，連按兩下按鈕，以建立`startButton_Click`MainWindow.xaml.vb 中的事件處理常式。  
  
2.  下列程式碼中，複製並貼到主體`startButton_Click`MainWindow.xaml.vb 中。  
  
    ```vb  
    resultsTextBox.Clear()  
    Await CreateMultipleTasksAsync()  
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    ```  
  
     程式碼會呼叫非同步方法， `CreateMultipleTasksAsync`，哪些磁碟機的應用程式。  
  
3.  將下列的支援方法加入至專案︰  
  
    -   `ProcessURLAsync`使用<xref:System.Net.Http.HttpClient>方法，以下載網站，以做為位元組陣列的內容。</xref:System.Net.Http.HttpClient> 支援的方法，`ProcessURLAsync`然後顯示，並傳回陣列的長度。  
  
    -   `DisplayResults`顯示每個 URL 位元組陣列中的位元組數目。 每一項工作已下載完成時，這會顯示說明。  
  
     將下列方法中，複製並貼上它們之後`startButton_Click`MainWindow.xaml.vb 中的事件處理常式。  
  
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
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
    ```  
  
4.  最後，方法定義`CreateMultipleTasksAsync`，其可執行下列步驟。  
  
    -   方法宣告`HttpClient`物件，您需要存取方法<xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>中`ProcessURLAsync`。</xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>  
  
    -   此方法會建立並啟動三個類型的工作<xref:System.Threading.Tasks.Task%601>，其中`TResult`是一個整數。</xref:System.Threading.Tasks.Task%601> 隨著每個工作完成，`DisplayResults`會顯示工作的 URL 和下載內容的長度。 因為工作都以非同步方式執行，結果會出現的順序可能會因所宣告的順序。  
  
    -   此方法會等候每個工作的完成。 每個`Await`運算子暫停執行`CreateMultipleTasksAsync`直到等候的工作。 運算子也會擷取傳回值，呼叫`ProcessURLAsync`從每個已完成的工作。  
  
    -   當工作完成後，已擷取的整數值的方法加總長度的網站，並顯示結果。  
  
     複製下列的方法，並將它貼到您的方案。  
  
    ```vb  
    Private Async Function CreateMultipleTasksAsync() As Task  
  
        ' Declare an HttpClient object, and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Create and start the tasks. As each task finishes, DisplayResults   
        ' displays its length.  
        Dim download1 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com", client)  
        Dim download2 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)  
        Dim download3 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/library/67w7t67f.aspx", client)  
  
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
  
5.  選擇 F5 鍵以執行程式，然後選擇 [ **開始** ] 按鈕。  
  
     若要確認三項工作不一定完成相同的順序和它們完成的順序不一定就是建立及等候的順序執行程式數次。  
  
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
            ProcessURLAsync("http://msdn.microsoft.com", client)  
        Dim download2 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)  
        Dim download3 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/library/67w7t67f.aspx", client)  
  
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
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
End Class  
```  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說︰ 存取 Web 使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
 [非同步程式設計使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)   
 [如何︰ 使用 Task.WhenAll (Visual Basic) 來擴充非同步逐步解說](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
