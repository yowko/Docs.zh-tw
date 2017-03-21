---
title: "啟動多項非同步工作並處理它們完成 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 57ffb748-af40-4794-bedd-bdb7fea062de
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
ms.openlocfilehash: 6fbf4611ecd64abfd016963dff887d82aad333b7
ms.lasthandoff: 03/13/2017

---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-visual-basic"></a>啟動多項非同步工作並處理它們完成 (Visual Basic)
使用<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>，您可以同時啟動多項工作，並在它們正在完成而不是要啟動的順序處理這些時，處理逐一。</xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>  
  
 下列範例會使用查詢來建立工作的集合。 每一項工作會下載指定的網站的內容。 在一段時間的每個反覆項目執行迴圈，等候的呼叫`WhenAny`先完成其下載的工作集合中傳回的工作。 這項工作是從集合中移除，並處理。 迴圈重複，直到集合包含沒有更多的工作。  
  
> [!NOTE]
>  若要執行範例，您必須擁有 Visual Studio 2012 或較新和.NET Framework 4.5 或更新版本安裝在電腦上。  
  
## <a name="downloading-the-example"></a>下載範例  
 您可以下載完整的 Windows Presentation Foundation (WPF) 專案，從[非同步範例︰ 順利微調您的應用程式](http://go.microsoft.com/fwlink/?LinkId=255046)，然後依照下列步驟。  
  
1.  解壓縮您下載的檔案，然後啟動 Visual Studio。  
  
2.  在功能表列上，依序選擇 [檔案] ****、[開啟舊檔] ****及 [專案/方案] ****。  
  
3.  在**開啟專案**對話方塊中，開啟保存在解壓縮時，範例程式碼的資料夾，並接著開啟 AsyncFineTuningVB 方案 (.sln) 檔案。  
  
4.  在**方案總管 中**，開啟捷徑功能表**ProcessTasksAsTheyFinish**專案，然後再選擇**設定為啟始專案**。  
  
5.  選擇 F5 鍵以執行專案。  
  
     選擇 Ctrl + F5 鍵以執行專案，但不偵錯它。  
  
6.  若要確認下載的長度不一定會出現在相同的順序執行專案數次。  
  
 如果您不想要下載的專案，您可以檢閱本主題結尾處的 MainWindow.xaml.vb 檔案。  
  
## <a name="building-the-example"></a>建置範例  
 這個範例會將開發中的程式碼加入[後一個完整 (Visual Basic) 取消剩餘的非同步工作](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)，並使用相同的 UI。  
  
 若要建置範例自行逐步解說，依照指示下載 「 範例 」 一節中的，但是選擇**CancelAfterOneTask**為**啟始專案**。 本主題中加入變更`AccessTheWebAsync`該專案中的方法。 所做的變更會以星號標示。  
  
 **CancelAfterOneTask**專案已經包含的查詢，在執行時，會建立一組工作。 每次呼叫`ProcessURLAsync`在下列程式碼會傳回<xref:System.Threading.Tasks.Task%601>其中`TResult`是一個整數。</xref:System.Threading.Tasks.Task%601>  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 在專案的 MainWindow.xaml.vb 檔案中，進行下列變更`AccessTheWebAsync`方法。  
  
-   執行查詢，<xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>而不是<xref:System.Linq.Enumerable.ToArray%2A>。</xref:System.Linq.Enumerable.ToArray%2A></xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>套用  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
-   新增 while 迴圈，每個工作集合中執行下列步驟。  
  
    1.  等候呼叫`WhenAny`來識別要完成其下載集合的第一個工作。  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
    2.  從集合中移除該工作。  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
    3.  等候`firstFinishedTask`，這由呼叫`ProcessURLAsync`。 `firstFinishedTask`變數是<xref:System.Threading.Tasks.Task%601>其中`TReturn`是一個整數。</xref:System.Threading.Tasks.Task%601> 工作已完成，但您等候它擷取的長度已下載的網站，如下列範例所示。  
  
        ```vb  
        Dim length = Await firstFinishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        ```  
  
 您應該執行專案數次，以確認下載的長度不一定會出現在相同的順序。  
  
> [!CAUTION]
>  您可以使用`WhenAny`在迴圈中，此範例中，以解決問題牽涉到少量的工作中所述。 不過，如果您有大量的工作要處理，其他方法會更有效率。 如需詳細資訊和範例，請參閱[處理工作完成時加以](http://go.microsoft.com/fwlink/?LinkId=260810)。  
  
## <a name="complete-example"></a>完整範例  
 下列程式碼是範例的 MainWindow.xaml.vb 檔案的完整文字。 星號標示此範例中所新增的項目。  
  
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
            resultsTextBox.Text &= vbCrLf & "Downloads complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf  
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
  
        ' ***Create a query that, when executed, returns a collection of tasks.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client, ct)  
  
        ' ***Use ToList to execute the query and start the download tasks.   
        Dim downloadTasks As List(Of Task(Of Integer)) = downloadTasksQuery.ToList()  
  
        ' ***Add a loop to process the tasks one at a time until none remain.  
        While downloadTasks.Count > 0  
            ' ***Identify the first task that completes.  
            Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
  
            ' ***Remove the selected task from the list so that you don't  
            ' process it more than once.  
            downloadTasks.Remove(firstFinishedTask)  
  
            ' ***Await the first completed task and display the results.  
            Dim length = Await firstFinishedTask  
            resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        End While  
  
    End Function  
  
    ' Bundle the processing steps for a website into one async method.  
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
  
' Length of the download:  226093  
' Length of the download:  412588  
' Length of the download:  175490  
' Length of the download:  204890  
' Length of the download:  158855  
' Length of the download:  145790  
' Length of the download:  44908  
' Downloads complete.  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.Tasks.Task.WhenAny%2A></xref:System.Threading.Tasks.Task.WhenAny%2A>   
 [微調非同步應用程式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)   
 [非同步程式設計使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)   
 [非同步範例︰ 微調應用程式](http://go.microsoft.com/fwlink/?LinkId=255046)
