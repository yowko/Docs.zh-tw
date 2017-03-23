---
title: "取消一項非同步工作或一份工作 (Visual Basic) |Microsoft 文件"
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
ms.assetid: a9ee1b71-5bec-4736-a1e9-448042dd7215
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fe2df73aaf49f1b61dafcad9a6c6e0f3d014f8ec
ms.lasthandoff: 03/13/2017

---
# <a name="cancel-an-async-task-or-a-list-of-tasks-visual-basic"></a>取消一項非同步工作或一份工作 (Visual Basic)
您可以設定按鈕可讓您取消非同步應用程式，如果您不想等候它完成。 依照本主題中的範例，您可以取消按鈕加入的應用程式，下載網站的內容或網站的清單。  
  
 範例會使用 UI，[微調非同步應用程式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)描述。  
  
> [!NOTE]
>  若要執行範例，您必須擁有 Visual Studio 2012 或較新和.NET Framework 4.5 或更新版本安裝在電腦上。  
  
##  <a name="BKMK_CancelaTask"></a>取消工作  
 第一個範例將**取消**具有單一的下載工作的按鈕。 如果應用程式會下載內容時，您可以選擇該按鈕，則會取消下載。  
  
### <a name="downloading-the-example"></a>下載範例  
 您可以下載完整的 Windows Presentation Foundation (WPF) 專案，從[非同步範例︰ 順利微調您的應用程式](http://go.microsoft.com/fwlink/?LinkId=255046)，然後依照下列步驟。  
  
1.  解壓縮您下載的檔案，然後啟動 Visual Studio。  
  
2.  在功能表列上，依序選擇 [檔案] ****、[開啟舊檔] ****及 [專案/方案] ****。  
  
3.  在**開啟專案**對話方塊中，開啟保存在解壓縮時，範例程式碼的資料夾，並接著開啟 AsyncFineTuningVB 方案 (.sln) 檔案。  
  
4.  在**方案總管 中**，開啟捷徑功能表**CancelATask**專案，然後再選擇**設定為啟始專案**。  
  
5.  選擇 F5 鍵以執行專案。  
  
     選擇 Ctrl + F5 鍵以執行專案，但不偵錯它。  
  
 如果您不想要下載的專案，您可以檢閱本主題結尾處的 MainWindow.xaml.vb 檔案。  
  
### <a name="building-the-example"></a>建置範例  
 加入下列變更**取消** 按鈕，下載網站的應用程式。 如果您不想要下載或建置範例，您可以檢閱本主題結尾處的 「 完整的範例 」 一節中最終產品。 星號標示的程式碼變更。  
  
 若要建置範例自行逐步解說，依照指示下載 「 範例 」 一節中的，但是選擇**StarterCode**為**啟始專案**而不是**CancelATask**。  
  
 該專案的 MainWindow.xaml.vb 檔案，然後加入下列變更。  
  
1.  宣告`CancellationTokenSource`變數`cts`，這是所有的方法來存取該範圍內。  
  
    ```vb  
    Class MainWindow  
  
        ' ***Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
    ```  
  
2.  新增下列事件處理常式**取消** 按鈕。 事件處理常式會使用<xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName>方法來通知`cts`當使用者要求取消。</xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName>  
  
    ```vb  
    ' ***Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
    ```  
  
3.  進行下列變更在事件處理常式**啟動** 按鈕， `startButton_Click`。  
  
    -   具現化`CancellationTokenSource`， `cts`。  
  
        ```vb  
        ' ***Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
        ```  
  
    -   在呼叫`AccessTheWebAsync`、 下載指定的網站內容、 傳送<xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=fullName>屬性`cts`做為引數。</xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=fullName> `Token`屬性會傳播訊息，如果已要求取消。 新增會顯示訊息，如果使用者選擇取消下載作業的 catch 區塊。 下列程式碼顯示的變更。  
  
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
  
4.  在`AccessTheWebAsync`，使用<xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=fullName>多載`GetAsync`方法中的<xref:System.Net.Http.HttpClient>下載網站的內容類型。</xref:System.Net.Http.HttpClient> </xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=fullName> 傳遞`ct`、<xref:System.Threading.CancellationToken>參數`AccessTheWebAsync`，做為第二個引數。</xref:System.Threading.CancellationToken> 如果使用者選擇權杖夾帶了訊息**取消** 按鈕。  
  
     下列程式碼將示範在變更`AccessTheWebAsync`。  
  
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
  
5.  如果您沒有取消程式，便會產生下列輸出。  
  
    ```  
    Ready to download.  
    Length of the downloaded string: 158125.  
    ```  
  
     如果您選擇**取消**按鈕，然後再程式完成之後下載內容，此程式會產生下列輸出。  
  
    ```  
    Ready to download.  
    Download canceled.  
    ```  
  
##  <a name="BKMK_CancelaListofTasks"></a>取消工作的清單  
 您可以擴充先前的範例，若要取消產生關聯，以相同的許多工作`CancellationTokenSource`與每個工作的執行個體。 如果您選擇**取消** 按鈕，取消尚無完整的所有工作。  
  
### <a name="downloading-the-example"></a>下載範例  
 您可以下載完整的 Windows Presentation Foundation (WPF) 專案，從[非同步範例︰ 順利微調您的應用程式](http://go.microsoft.com/fwlink/?LinkId=255046)，然後依照下列步驟。  
  
1.  解壓縮您下載的檔案，然後啟動 Visual Studio。  
  
2.  在功能表列上，依序選擇 [檔案] ****、[開啟舊檔] ****及 [專案/方案] ****。  
  
3.  在**開啟專案**對話方塊中，開啟保存在解壓縮時，範例程式碼的資料夾，並接著開啟 AsyncFineTuningVB 方案 (.sln) 檔案。  
  
4.  在**方案總管 中**，開啟捷徑功能表**CancelAListOfTasks**專案，然後再選擇**設定為啟始專案**。  
  
5.  選擇 F5 鍵以執行專案。  
  
     選擇 Ctrl + F5 鍵以執行專案，但不偵錯它。  
  
 如果您不想要下載的專案，您可以檢閱本主題結尾處的 MainWindow.xaml.vb 檔案。  
  
### <a name="building-the-example"></a>建置範例  
 若要擴充範例自行逐步解說，依照指示下載 「 範例 」 一節中的，但是選擇**CancelATask**為**啟始專案**。 專案中加入下列變更。 星號標示的程式中的變更。  
  
1.  加入方法以建立一份 web 位址。  
  
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
  
2.  在呼叫方法`AccessTheWebAsync`。  
  
    ```vb  
    ' ***Call SetUpURLList to make a list of web addresses.  
    Dim urlList As List(Of String) = SetUpURLList()  
    ```  
  
3.  將下列的迴圈中加入`AccessTheWebAsync`處理每個清單中的網址。  
  
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
  
4.  因為`AccessTheWebAsync`顯示長度，此方法不需傳回任何項目。 移除 return 陳述式，並將方法的傳回型別變更為 <xref:System.Threading.Tasks.Task>而不是<xref:System.Threading.Tasks.Task%601>。</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task>  
  
<CodeContentPlaceHolder>10</CodeContentPlaceHolder>  
     呼叫這個方法從`startButton_Click`使用陳述式，而不是運算式。  
  
    ```vb  
    Await AccessTheWebAsync(cts.Token)  
    ```  
  
5.  如果您沒有取消程式，便會產生下列輸出。  
  
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
  
     如果您選擇**取消**之前會完整下載 按鈕，輸出會包含完成之前取消下載的長度。  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Downloads canceled.  
  
    ```  
  
##  <a name="BKMK_CompleteExamples"></a>完整範例  
 下列各節包含的程式碼，為每個先前的範例。 請注意，您必須加入<xref:System.Net.Http>.</xref:System.Net.Http>的參考  
  
 您可以下載的專案[非同步範例︰ 順利微調您的應用程式](http://go.microsoft.com/fwlink/?LinkId=255046)。  
  
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
  
### <a name="cancel-a-list-of-tasks-example"></a>取消工作範例的清單  
 下列程式碼是完整的 MainWindow.xaml.vb 檔案，例如取消的工作清單。  
  
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
 <xref:System.Threading.CancellationTokenSource></xref:System.Threading.CancellationTokenSource>   
 <xref:System.Threading.CancellationToken></xref:System.Threading.CancellationToken>   
 [非同步程式設計使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)   
 [微調非同步應用程式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)   
 [非同步範例︰ 微調應用程式](http://go.microsoft.com/fwlink/?LinkId=255046)
