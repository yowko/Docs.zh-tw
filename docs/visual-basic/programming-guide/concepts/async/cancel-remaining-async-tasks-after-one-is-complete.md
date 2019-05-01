---
title: 當取消剩餘的非同步工作是完成 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
ms.openlocfilehash: 587c863ba110f035ace5207d8404fd70b3befe37
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63809117"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a>當取消剩餘的非同步工作是完成 (Visual Basic)

搭配使用 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> 方法與 <xref:System.Threading.CancellationToken>，即可在其中一個工作完成時取消所有剩餘的工作。 `WhenAny` 方法會接受本身為一組工作的引數。 這個方法會啟動所有工作，並傳回單一工作。 集合中的任何工作完成時，單一工作即完成。

這個範例示範如何搭配使用取消權杖與 `WhenAny` 以完成這組工作中的第一項工作，並取消其餘工作。 每一項工作都會下載網站的內容。 此範例顯示要完成的第一個下載內容的長度，並取消其他下載。

> [!NOTE]
> 若要執行範例，您必須在電腦上安裝 Visual Studio 2012 或更新版本以及 .NET Framework 4.5 或更新版本。

## <a name="downloading-the-example"></a>下載範例

您可以從 [Async Sample:Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (非同步範例：微調應用程式) 下載完整 Windows Presentation Foundation (WPF) 專案，然後遵循下列步驟。

1. 解壓縮您下載的檔案，然後啟動 Visual Studio。

2. 在功能表列上，依序選擇 [檔案] 、[開啟舊檔] 及 [專案/方案] 。

3. 在 [**開啟專案**] 對話方塊中，開啟您解壓縮之範例程式碼的資料夾，然後再開啟 AsyncFineTuningVB 的方案 (.sln) 檔案。

4. 在方案總管中，開啟 **CancelAfterOneTask** 專案的捷徑功能表，然後選擇 [設定為啟始專案]。

5. 選擇 F5 鍵以執行專案。

    選擇 CTRL+F5 鍵以執行專案，而不進行偵錯。

6. 執行程式數次，確認先完成不同的下載。

如果您不想要下載的專案，您可以檢閱本主題結尾的 MainWindow.xaml.vb 檔案。

## <a name="building-the-example"></a>建置範例

本主題中的範例將加入專案中所開發[取消一項非同步工作或工作清單](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)取消工作清單。 雖然未明確地使用 [取消] 按鈕，但是此範例會使用相同的 UI。

若要自行逐步建置範例，請遵循＜下載範例＞一節中的指示，但選擇 [CancelAListOfTasks] 作為 [啟始專案]。 將本主題中的變更新增至該專案。

中的 MainWindow.xaml.vb 檔案**CancelAListOfTasks**專案，以開始轉換，藉由移動每個網站的處理步驟中的迴圈從`AccessTheWebAsync`至下列非同步方法。

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

在 `AccessTheWebAsync` 中，這個範例會使用查詢、<xref:System.Linq.Enumerable.ToArray%2A> 方法和 `WhenAny` 方法來建立並啟動工作陣列。 將 `WhenAny` 套用至陣列，會傳回評估為在工作陣列中完成之第一個工作的等候中單一工作。

在 `AccessTheWebAsync` 中進行下列變更。 星號會標記程式碼檔中的變更。

1. 註解化或刪除迴圈。

2. 建立查詢，而查詢在執行時會產生一組泛型工作。 每個 `ProcessURLAsync` 呼叫都會傳回 `TResult` 為整數的 <xref:System.Threading.Tasks.Task%601>。

    ```vb
    ' ***Create a query that, when executed, returns a collection of tasks.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url, client, ct)
    ```

3. 呼叫 `ToArray` 來執行查詢，並開始工作。 在下一個步驟中套用 `WhenAny` 方法會執行查詢並啟動工作，而不使用 `ToArray`，但其他方法可能為否。 最安全的做法是明確地強制執行查詢。

    ```vb
    ' ***Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. 對這組工作呼叫 `WhenAny`。 `WhenAny` 會傳回 `Task(Of Task(Of Integer))` 或 `Task<Task<int>>`。  亦即，`WhenAny` 會傳回評估為單一 `Task(Of Integer)` 或 `Task<int>` 的等候中工作。 該單一工作是完成集合中的第一項工作。 先完成的工作會指派給 `firstFinishedTask`。 `firstFinishedTask` 的型別是 `TResult` 為整數的 <xref:System.Threading.Tasks.Task%601>，因為這是 `ProcessURLAsync` 的傳回型別。

    ```vb
    ' ***Call WhenAny and then await the result. The task that finishes
    ' first is assigned to firstFinishedTask.
    Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)
    ```

5. 在此範例中，您只想要知道先完成的工作。 因此，請使用 <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> 取消剩餘的工作。

    ```vb
    ' ***Cancel the rest of the downloads. You just want the first one.
    cts.Cancel()
    ```

6. 最後，等候 `firstFinishedTask` 擷取所下載內容的長度。

    ```vb
    Dim length = Await firstFinishedTask
    resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)
    ```

執行程式數次，確認先完成不同的下載。

## <a name="complete-example"></a>完整範例

下列程式碼是範例的完整 MainWindow.xaml.vb 或 MainWindow.xaml.cs 檔案。 星號會標記已針對此範例新增的項目。

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

' Length of the downloaded website:  158856

' Download complete.
```

## <a name="see-also"></a>另請參閱

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [微調非同步應用程式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [使用 Async 和 Await 進行非同步程式設計 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [非同步範例：微調您的應用程式](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
