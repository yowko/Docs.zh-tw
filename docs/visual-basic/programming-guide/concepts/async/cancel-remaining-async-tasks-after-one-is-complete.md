---
title: "當取消剩餘的非同步工作是完整 (Visual Basic) |Microsoft 文件"
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
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
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
ms.openlocfilehash: 1b70822edd972ac33614ab49faad6ff50b0e80b7
ms.lasthandoff: 03/13/2017

---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a>當取消剩餘的非同步工作是完整 (Visual Basic)
使用<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>方法並搭配<xref:System.Threading.CancellationToken>，一個工作完成時，您可以取消所有其餘的工作。</xref:System.Threading.CancellationToken> </xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName> `WhenAny`方法會採用一組工作的引數。 這個方法會啟動所有工作，並傳回單一工作。 集合中的任何工作完成時，單一工作已完成。  
  
 這個範例示範如何搭配使用取消語彙基元`WhenAny`固守第一項工作完成的工作集合，以及取消其餘的工作。 每一項工作會下載網站的內容。 此範例顯示的第一個完成的下載內容的長度，並取消其他下載。  
  
> [!NOTE]
>  若要執行範例，您必須擁有 Visual Studio 2012 或較新和.NET Framework 4.5 或更新版本安裝在電腦上。  
  
## <a name="downloading-the-example"></a>下載範例  
 您可以下載完整的 Windows Presentation Foundation (WPF) 專案，從[非同步範例︰ 順利微調您的應用程式](http://go.microsoft.com/fwlink/?LinkId=255046)，然後依照下列步驟。  
  
1.  解壓縮您下載的檔案，然後啟動 Visual Studio。  
  
2.  在功能表列上，依序選擇 [檔案] ****、[開啟舊檔] ****及 [專案/方案] ****。  
  
3.  在**開啟專案**對話方塊中，開啟保存在解壓縮時，範例程式碼的資料夾，並接著開啟 AsyncFineTuningVB 方案 (.sln) 檔案。  
  
4.  在**方案總管 中**，開啟捷徑功能表**CancelAfterOneTask**專案，然後再選擇**設定為啟始專案**。  
  
5.  選擇 F5 鍵以執行專案。  
  
     選擇 Ctrl + F5 鍵以執行專案，但不偵錯它。  
  
6.  若要確認不同的下載完成第一次執行程式數次。  
  
 如果您不想要下載的專案，您可以檢閱本主題結尾處的 MainWindow.xaml.vb 檔案。  
  
## <a name="building-the-example"></a>建置範例  
 本主題中的範例將加入專案中開發[取消一項非同步工作或工作清單](http://msdn.microsoft.com/library/d6e4e801-df64-4705-98fc-df725a577fb0)取消的工作清單。 雖然此範例會使用相同的 UI，**取消**按鈕不會明確地使用。  
  
 若要建置範例自行逐步解說，依照指示下載 「 範例 」 一節中的，但是選擇**CancelAListOfTasks**為**啟始專案**。 本主題中加入該專案所做的變更。  
  
 中的 MainWindow.xaml.vb 檔案**CancelAListOfTasks**專案中，從迴圈中移動的每個網站的處理步驟開始轉換`AccessTheWebAsync`下列非同步方法。  
  
```vb  
' ***Bundle the processing steps for a website into one async method.  
Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)  
  
    ' GetAsync returns a Task(Of HttpResponseMessage).   
    Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
    ' Retrieve the website contents from the HttpResponseMessage.  
    Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
    Return urlContents.Length  
End Function  
```  
  
 在`AccessTheWebAsync`，這個範例會使用查詢，<xref:System.Linq.Enumerable.ToArray%2A>方法，而`WhenAny`方法來建立並啟動工作的陣列。</xref:System.Linq.Enumerable.ToArray%2A> 應用程式的`WhenAny`陣列傳回的單一工作，當等候時，會評估為連線到陣列中的完成工作的第一個工作。  
  
 進行下列變更在`AccessTheWebAsync`。 星號標示的程式碼檔案中的變更。  
  
1.  註解化或刪除迴圈。  
  
2.  建立查詢，在執行時，會產生一組一般工作。 每次呼叫`ProcessURLAsync`傳回<xref:System.Threading.Tasks.Task%601>其中`TResult`是一個整數。</xref:System.Threading.Tasks.Task%601>  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
3.  呼叫`ToArray`來執行查詢，並開始工作。 應用程式的`WhenAny`下一個步驟中的方法會執行查詢，並啟動工作，而不使用`ToArray`，但不是可能的其他方法。 最安全的作法是明確地強制執行查詢。  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
4.  呼叫`WhenAny`上工作的集合。 `WhenAny`傳回`Task(Of Task(Of Integer))`或`Task<Task<int>>`。  也就是`WhenAny`傳回的工作，評估單一`Task(Of Integer)`或`Task<int>`時，它會等候。 該單一的工作會在完成集合中的第一項工作。 已完成第一次工作指派給`firstFinishedTask`。 型別`firstFinishedTask`是<xref:System.Threading.Tasks.Task%601>其中`TResult`是一個整數，因為這是傳回型別`ProcessURLAsync`。</xref:System.Threading.Tasks.Task%601>  
  
```vb  
' ***Call WhenAny and then await the result. The task that finishes   
' first is assigned to firstFinishedTask.  
Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
```  
  
5.  在此範例中，您想要知道只能在第一次完成的工作項目。 因此，使用<xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName>取消其餘的工作。</xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName>  
  
```vb  
' ***Cancel the rest of the downloads. You just want the first one.  
cts.Cancel()  
```  
  
6.  最後，等候`firstFinishedTask`擷取下載的內容長度。  
  
```vb  
Dim length = Await firstFinishedTask  
resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
```  
  
 若要確認不同的下載完成第一次執行程式數次。  
  
## <a name="complete-example"></a>完整範例  
 下列程式碼是完整的 MainWindow.xaml.vb 或 MainWindow.xaml.cs 檔案的範例。 星號標示此範例中所新增的項目。  
  
 請注意，您必須加入<xref:System.Net.Http>.</xref:System.Net.Http>的參考  
  
 您可以下載的專案[非同步範例︰ 順利微調您的應用程式](http://go.microsoft.com/fwlink/?LinkId=255046)。  
  
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
            Await AccessTheWebAsync(cts.Token)  
            resultsTextBox.Text &= vbCrLf & "Download complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf  
        End Try  
  
        ' Set the CancellationTokenSource to Nothing when the download is complete.  
        cts = Nothing  
    End Sub  
  
    ' You can still include a Cancel button if you want to.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
  
    ' Provide a parameter for the CancellationToken.  
    ' Change the return type to Task because the method has no return statement.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
  
        Dim client As HttpClient = New HttpClient()  
  
        ' Call SetUpURLList to make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        '' Comment out or delete the loop.  
        ''For Each url In urlList  
        ''    ' GetAsync returns a Task(Of HttpResponseMessage).   
        ''    ' Argument ct carries the message if the Cancel button is chosen.   
        ''    ' Note that the Cancel button can cancel all remaining downloads.  
        ''    Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ''    ' Retrieve the website contents from the HttpResponseMessage.  
        ''    Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ''    resultsTextBox.Text &=  
        ''        String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
        ''Next  
  
        ' ***Create a query that, when executed, returns a collection of tasks.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client, ct)  
  
        ' ***Use ToArray to execute the query and start the download tasks.   
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' ***Call WhenAny and then await the result. The task that finishes   
        ' first is assigned to firstFinishedTask.  
        Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
  
        ' ***Cancel the rest of the downloads. You just want the first one.  
        cts.Cancel()  
  
        ' ***Await the first completed task and display the results  
        ' Run the program several times to demonstrate that different  
        ' websites can finish first.  
        Dim length = Await firstFinishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
    End Function  
  
    ' ***Bundle the processing steps for a website into one async method.  
    Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)  
  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        Return urlContents.Length  
    End Function  
  
    ' Add a method that creates a list of web addresses.  
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
  
' Sample output:  
  
' Length of the downloaded website:  158856  
  
' Download complete.  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.Tasks.Task.WhenAny%2A></xref:System.Threading.Tasks.Task.WhenAny%2A>   
 [微調非同步應用程式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)   
 [非同步程式設計使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)   
 [非同步範例︰ 微調應用程式](http://go.microsoft.com/fwlink/?LinkId=255046)
