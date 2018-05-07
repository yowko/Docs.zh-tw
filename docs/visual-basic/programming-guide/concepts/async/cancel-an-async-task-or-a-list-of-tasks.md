---
title: 取消一項非同步工作或一份工作 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: a9ee1b71-5bec-4736-a1e9-448042dd7215
ms.openlocfilehash: 74f0c1c4653709497cb264aac18b49f4fee4eefa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-visual-basic"></a>取消一項非同步工作或一份工作 (Visual Basic)
如果您不想要等候非同步應用程式完成，則可以設定可用來取消非同步應用程式的按鈕。 遵循本主題中的範例，即可將取消按鈕新增至下載某個網站內容或網站清單的應用程式。  
  
 範例會使用 UI，[微調非同步應用程式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)描述。  
  
> [!NOTE]
>  若要執行範例，您必須在電腦上安裝 Visual Studio 2012 或更新版本以及 .NET Framework 4.5 或更新版本。  
  
##  <a name="BKMK_CancelaTask"></a> 取消工作  
 第一個範例會建立 [取消] 按鈕與單一下載工作的關聯。 如果您在應用程式下載內容時選擇該按鈕，則會取消下載。  
  
### <a name="downloading-the-example"></a>下載範例  
 您可以從 [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) (非同步範例：微調應用程式) 下載完整 Windows Presentation Foundation (WPF) 專案，然後遵循下列步驟。  
  
1.  解壓縮您下載的檔案，然後啟動 Visual Studio。  
  
2.  在功能表列上，依序選擇 [檔案] 、[開啟舊檔] 及 [專案/方案] 。  
  
3.  在**開啟專案**對話方塊中，開啟保存您解壓縮範例程式碼的資料夾，然後再開啟進行 AsyncFineTuningVB 的 方案 (.sln) 檔案。  
  
4.  在方案總管中，開啟 **CancelATask** 專案的捷徑功能表，然後選擇 [設定為啟始專案]。  
  
5.  選擇 F5 鍵執行執行專案。  
  
     選擇 CTRL+F5 鍵以執行專案，而不進行偵錯。  
  
 如果您不想要下載的專案，您可以檢閱本主題結尾處的 MainWindow.xaml.vb 檔案。  
  
### <a name="building-the-example"></a>建置範例  
 下列變更會將 [取消] 按鈕新增至下載網站的應用程式。 如果您不想要下載或建置範例，則可以檢閱本主題結尾處的＜完整範例＞一節中的最終產品。 星號會標記程式碼中的變更。  
  
 若要自行逐步建置範例，請遵循＜下載範例＞一節中的指示，但選擇 [StarterCode] 作為 [啟始專案]，而非 [CancelATask]。  
  
 MainWindow.xaml.vb 檔案中的該專案，然後新增下列變更。  
  
1.  宣告 `CancellationTokenSource` 變數 `cts`，這是在存取它之所有方法的範圍內。  
  
    ```vb  
    Class MainWindow  
  
        ' ***Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
    ```  
  
2.  針對 [取消] 按鈕新增下列事件處理常式。 事件處理常式會使用 <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> 方法，以在使用者要求取消時通知 `cts`。  
  
    ```vb  
    ' ***Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
    ```  
  
3.  在 [開始] 按鈕 `startButton_Click` 的事件處理常式中進行下列變更。  
  
    -   具現化 `CancellationTokenSource`、`cts`。  
  
        ```vb  
        ' ***Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
        ```  
  
    -   在下載所指定網站內容的 `AccessTheWebAsync` 呼叫中，傳送 `cts` 的 <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> 屬性作為引數。 如果要求取消，則 `Token` 屬性會傳播訊息。 新增 catch 區塊，以在使用者選擇取消下載作業時顯示訊息。 下列程式碼示範這些變更。  
  
        ```vb  
        Try  
            ' ***Send a token to carry the message if cancellation is requested.  
            Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
  
            ' *** If cancellation is requested, an OperationCanceledException results.  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf  
        End Try  
        ```  
  
4.  在 `AccessTheWebAsync` 中，使用 <xref:System.Net.Http.HttpClient> 型別中 `GetAsync` 方法的 <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> 多載來下載網站的內容。 將 `ct` (`AccessTheWebAsync` 的 <xref:System.Threading.CancellationToken> 參數) 傳遞為第二個引數。 如果使用者選擇 [取消] 按鈕，則權杖會夾帶訊息。  
  
     下列程式碼示範 `AccessTheWebAsync` 中的變更。  
  
    ```vb  
    ' ***Provide a parameter for the CancellationToken.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)  
  
        Dim client As HttpClient = New HttpClient()  
  
        resultsTextBox.Text &=  
            String.Format(vbCrLf & "Ready to download." & vbCrLf)  
  
        ' You might need to slow things down to have a chance to cancel.  
        Await Task.Delay(250)  
  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        ' ***The ct argument carries the message if the Cancel button is chosen.  
        Dim response As HttpResponseMessage = Await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' The result of the method is the length of the downloaded website.  
        Return urlContents.Length  
    End Function  
    ```  
  
5.  如果您未取消程式，則會產生下列輸出。  
  
    ```  
    Ready to download.  
    Length of the downloaded string: 158125.  
    ```  
  
     如果您在程式完成下載內容之前選擇 [取消] 按鈕，程式會產生下列輸出。  
  
    ```  
    Ready to download.  
    Download canceled.  
    ```  
  
##  <a name="BKMK_CancelaListofTasks"></a> 取消工作清單  
 您可以將相同 `CancellationTokenSource` 執行個體與每項工作建立關聯，以擴充先前的範例來取消許多工作。 如果您選擇 [取消] 按鈕，即會取消所有尚未完成的工作。  
  
### <a name="downloading-the-example"></a>下載範例  
 您可以從 [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) (非同步範例：微調應用程式) 下載完整 Windows Presentation Foundation (WPF) 專案，然後遵循下列步驟。  
  
1.  解壓縮您下載的檔案，然後啟動 Visual Studio。  
  
2.  在功能表列上，依序選擇 [檔案] 、[開啟舊檔] 及 [專案/方案] 。  
  
3.  在**開啟專案**對話方塊中，開啟保存您解壓縮範例程式碼的資料夾，然後再開啟進行 AsyncFineTuningVB 的 方案 (.sln) 檔案。  
  
4.  在方案總管中，開啟 **CancelAListOfTasks** 專案的捷徑功能表，然後選擇 [設定為啟始專案]。  
  
5.  選擇 F5 鍵執行執行專案。  
  
     選擇 CTRL+F5 鍵以執行專案，而不進行偵錯。  
  
 如果您不想要下載的專案，您可以檢閱本主題結尾處的 MainWindow.xaml.vb 檔案。  
  
### <a name="building-the-example"></a>建置範例  
 若要自行逐步擴充範例，請遵循＜下載範例＞一節中的指示，但選擇 [CancelATask] 作為 [啟始專案]。 將下列變更新增至該專案。 星號會標記程式中的變更。  
  
1.  新增方法以建立網址清單。  
  
    ```vb  
    ' ***Add a method that creates a list of web addresses.  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
    ```  
  
2.  在 `AccessTheWebAsync` 中呼叫方法。  
  
    ```vb  
    ' ***Call SetUpURLList to make a list of web addresses.  
    Dim urlList As List(Of String) = SetUpURLList()  
    ```  
  
3.  在 `AccessTheWebAsync` 中新增下列迴圈，以處理清單中的每個網址。  
  
    ```vb  
    ' ***Add a loop to process the list of web addresses.  
    For Each url In urlList  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        ' Argument ct carries the message if the Cancel button is chosen.   
        ' ***Note that the Cancel button can cancel all remaining downloads.  
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        resultsTextBox.Text &=  
            String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
    Next  
    ```  
  
4.  因為 `AccessTheWebAsync` 顯示長度，所以此方法不需要傳回任何項目。 請移除 return 陳述式，並將方法的傳回型別變更為 <xref:System.Threading.Tasks.Task>，而非 <xref:System.Threading.Tasks.Task%601>。  
  
    ```vb  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
    ```  
  
     使用陳述式，從 `startButton_Click` 呼叫方法，而不是使用運算式。  
  
    ```vb  
    Await AccessTheWebAsync(cts.Token)  
    ```  
  
5.  如果您未取消程式，則會產生下列輸出。  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Length of the downloaded string: 158124.  
  
    Length of the downloaded string: 204890.  
  
    Length of the downloaded string: 175488.  
  
    Length of the downloaded string: 145790.  
  
    Downloads complete.  
    ```  
  
     如果您在下載完成之前選擇 [取消] 按鈕，則輸出會包含在取消之前完成之下載的長度。  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Downloads canceled.  
    ```  
  
##  <a name="BKMK_CompleteExamples"></a> 完整範例  
 下列各節包含每個先前範例的程式碼。 請注意，您必須新增 <xref:System.Net.Http> 的參考。  
  
 您可以從 [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) (非同步範例：微調應用程式) 下載專案。  
  
### <a name="cancel-a-task-example"></a>取消工作範例  
 下列程式碼是完整的 MainWindow.xaml.vb 檔案，例如取消單一工作。  
  
```vb  
' Add an Imports directive and a reference for System.Net.Http.  
Imports System.Net.Http  
  
' Add the following Imports directive for System.Threading.  
Imports System.Threading  
  
Class MainWindow  
  
    ' ***Declare a System.Threading.CancellationTokenSource.  
    Dim cts As CancellationTokenSource  
  
    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
        ' ***Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
  
        resultsTextBox.Clear()  
  
        Try  
            ' ***Send a token to carry the message if cancellation is requested.  
            Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
  
            ' *** If cancellation is requested, an OperationCanceledException results.  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf  
        End Try  
  
        ' ***Set the CancellationTokenSource to Nothing when the download is complete.  
        cts = Nothing  
    End Sub  
  
    ' ***Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
  
    ' ***Provide a parameter for the CancellationToken.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)  
  
        Dim client As HttpClient = New HttpClient()  
  
        resultsTextBox.Text &=  
            String.Format(vbCrLf & "Ready to download." & vbCrLf)  
  
        ' You might need to slow things down to have a chance to cancel.  
        Await Task.Delay(250)  
  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        ' ***The ct argument carries the message if the Cancel button is chosen.  
        Dim response As HttpResponseMessage = Await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' The result of the method is the length of the downloaded website.  
        Return urlContents.Length  
    End Function  
End Class  
  
' Output for a successful download:  
  
' Ready to download.  
  
' Length of the downloaded string: 158125.  
  
' Or, if you cancel:  
  
' Ready to download.  
  
' Download canceled.  
```  
  
### <a name="cancel-a-list-of-tasks-example"></a>取消工作清單範例  
 下列程式碼是完整的 MainWindow.xaml.vb 檔案，如需取消的工作清單的範例。  
  
```vb  
' Add an Imports directive and a reference for System.Net.Http.  
Imports System.Net.Http  
  
' Add the following Imports directive for System.Threading.  
Imports System.Threading  
  
Class MainWindow  
  
    ' Declare a System.Threading.CancellationTokenSource.  
    Dim cts As CancellationTokenSource  
  
    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
  
        ' Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
  
        resultsTextBox.Clear()  
  
        Try  
            ' ***AccessTheWebAsync returns a Task, not a Task(Of Integer).  
            Await AccessTheWebAsync(cts.Token)  
            '  ***Small change in the display lines.  
            resultsTextBox.Text &= vbCrLf & "Downloads complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf  
        End Try  
  
        ' Set the CancellationTokenSource to Nothing when the download is complete.  
        cts = Nothing  
    End Sub  
  
    ' Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
  
    ' Provide a parameter for the CancellationToken.  
    ' ***Change the return type to Task because the method has no return statement.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
  
        Dim client As HttpClient = New HttpClient()  
  
        ' ***Call SetUpURLList to make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' ***Add a loop to process the list of web addresses.  
        For Each url In urlList  
            ' GetAsync returns a Task(Of HttpResponseMessage).   
            ' Argument ct carries the message if the Cancel button is chosen.   
            ' ***Note that the Cancel button can cancel all remaining downloads.  
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
            ' Retrieve the website contents from the HttpResponseMessage.  
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
        Next  
    End Function  
  
    ' ***Add a method that creates a list of web addresses.  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
End Class  
  
' Output if you do not choose to cancel:  
  
' Length of the downloaded string: 35939.  
  
' Length of the downloaded string: 237682.  
  
' Length of the downloaded string: 128607.  
  
' Length of the downloaded string: 158124.  
  
' Length of the downloaded string: 204890.  
  
' Length of the downloaded string: 175488.  
  
' Length of the downloaded string: 145790.  
  
' Downloads complete.  
  
'  Sample output if you choose to cancel:  
  
' Length of the downloaded string: 35939.  
  
' Length of the downloaded string: 237682.  
  
' Length of the downloaded string: 128607.  
  
' Downloads canceled.  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.CancellationTokenSource>  
 <xref:System.Threading.CancellationToken>  
 [使用 Async 和 Await 進行非同步程式設計 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [微調非同步應用程式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [非同步範例：微調應用程式 (英文)](http://go.microsoft.com/fwlink/?LinkId=255046)
