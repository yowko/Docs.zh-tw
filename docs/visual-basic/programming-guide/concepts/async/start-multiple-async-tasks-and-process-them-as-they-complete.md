---
title: 啟動多項非同步工作並處理完成 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 57ffb748-af40-4794-bedd-bdb7fea062de
ms.openlocfilehash: a9a41c354993e0d362c344d523d6c4c4b6f61f10
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59309650"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-visual-basic"></a>啟動多項非同步工作並處理完成 (Visual Basic)
使用 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>，即可同時啟動多個工作，並在完成時逐一進行處理，而不是依啟動順序進行處理。  
  
 下列範例使用查詢來建立工作集合。 每項工作都會下載所指定網站的內容。 在 while 迴圈的的每個反覆運算中，等候的 `WhenAny` 呼叫會先傳回完成其下載的工作集合中的工作。 該工作會從集合中予以移除，並進行處理。 迴圈會重複進行，直到集合未包含其他工作為止。  
  
> [!NOTE]
>  若要執行範例，您必須在電腦上安裝 Visual Studio 2012 或更新版本以及 .NET Framework 4.5 或更新版本。  
  
## <a name="downloading-the-example"></a>下載範例  
 您可以從 [Async Sample:Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (非同步範例：微調應用程式) 下載完整 Windows Presentation Foundation (WPF) 專案，然後遵循下列步驟。  
  
1. 解壓縮您下載的檔案，然後啟動 Visual Studio。  
  
2. 在功能表列上，依序選擇 [檔案] 、[開啟舊檔] 及 [專案/方案] 。  
  
3. 在 [**開啟專案**] 對話方塊中，開啟您解壓縮之範例程式碼的資料夾，然後再開啟 AsyncFineTuningVB 的方案 (.sln) 檔案。  
  
4. 在方案總管中，開啟 **ProcessTasksAsTheyFinish** 專案的捷徑功能表，然後選擇 [設定為啟始專案]。  
  
5. 選擇 F5 鍵以執行專案。  
  
     選擇 CTRL+F5 鍵以執行專案，而不進行偵錯。  
  
6. 執行專案數次，確認所下載的長度不一定會以相同的順序出現。  
  
 如果您不想要下載的專案，您可以檢閱本主題結尾的 MainWindow.xaml.vb 檔案。  
  
## <a name="building-the-example"></a>建置範例  
 此範例會將開發中的程式碼加入[一個是完成 (Visual Basic) 之後取消剩餘的非同步工作](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)並使用相同的 UI。  
  
 若要自行逐步建置範例，請遵循＜下載範例＞一節中的指示，但選擇 [CancelAfterOneTask] 作為 [啟始專案]。 將本主題中的變更新增至該專案中的 `AccessTheWebAsync` 方法。 變更會標上星號。  
  
 **CancelAfterOneTask** 專案已經包含一個查詢，這個查詢在執行時，會建立一組工作。 下列程式碼中的每個 `ProcessURLAsync` 呼叫都會傳回 `TResult` 為整數的 <xref:System.Threading.Tasks.Task%601>。  
  
```vb  
Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
    From url In urlList Select ProcessURLAsync(url, client, ct)  
```  
  
 在專案的 MainWindow.xaml.vb 檔案中，進行下列變更`AccessTheWebAsync`方法。  
  
-   套用 <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 來執行查詢，而非 <xref:System.Linq.Enumerable.ToArray%2A>。  
  
    ```vb  
    Dim downloadTasks As List(Of Task(Of Integer)) = downloadTasksQuery.ToList()  
    ```  
  
-   新增 while 迴圈，以對集合中的每個工作執行下列步驟。  
  
    1.  等候 `WhenAny` 呼叫，識別集合中的第一個工作以完成其下載。  
  
        ```vb  
        Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
        ```  
  
    2.  從集合中移除該工作。  
  
        ```vb  
        downloadTasks.Remove(firstFinishedTask)  
        ```  
  
    3.  等候 `ProcessURLAsync` 呼叫所傳回的 `firstFinishedTask`。 `firstFinishedTask` 變數是 <xref:System.Threading.Tasks.Task%601>，其中 `TReturn` 是整數。 工作已完成，但您等候它擷取所下載網站的長度，如下列範例所示。  
  
        ```vb  
        Dim length = Await firstFinishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        ```  
  
 您應該執行專案數次，確認所下載的長度不一定會以相同的順序出現。  
  
> [!CAUTION]
>  您可以如這個範例所述在迴圈中使用 `WhenAny`，以解決牽涉到少量工作的問題。 不過，如果您有大量的工作要處理，其他方法會更有效率。 如需詳細資訊和範例，請參閱[Processing Tasks as they complete](https://blogs.msdn.microsoft.com/pfxteam/2012/08/02/processing-tasks-as-they-complete)(在工作完成時加以處理)。  
  
## <a name="complete-example"></a>完整範例  
 下列程式碼是範例的 MainWindow.xaml.vb 檔案的完整文字。 星號會標記已針對此範例新增的項目。  
  
 請注意，您必須新增 <xref:System.Net.Http> 的參考。  
  
 您可以從 [Async Sample:Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (非同步範例：微調應用程式) 下載專案。  
  
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
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
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

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [微調非同步應用程式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [使用 Async 和 Await 進行非同步程式設計 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [非同步範例：微調您的應用程式](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
