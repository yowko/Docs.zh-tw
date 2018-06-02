---
title: 一段時間 (Visual Basic) 後取消非同步工作
ms.date: 07/20/2015
ms.assetid: a48045a3-6a99-42af-b824-af340f0b9a5d
ms.openlocfilehash: f91fffd9bfcd66833ca3233251914868bf3b84de
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728689"
---
# <a name="cancel-async-tasks-after-a-period-of-time-visual-basic"></a>一段時間 (Visual Basic) 後取消非同步工作
如果不想等候作業完成，則可以使用 <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> 方法，在一段時間之後取消非同步作業。 這個方法排定取消未在 `CancelAfter` 運算式所指定之2期間內完成的任何相關工作。  
  
 這個範例會將開發中的程式碼加入[取消一項非同步工作或清單的工作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)下載的網站清單，並顯示每個內容的長度。  
  
> [!NOTE]
>  若要執行範例，您必須有 Visual Studio 2012 或更新版本和.NET Framework 4.5 或更新版本安裝在電腦上。  
  
## <a name="downloading-the-example"></a>下載範例  
 您可以從 [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (非同步範例：微調應用程式) 下載完整 Windows Presentation Foundation (WPF) 專案，然後遵循下列步驟。  
  
1.  解壓縮您下載的檔案，然後啟動 Visual Studio。  
  
2.  在功能表列上，依序選擇 [檔案] 、[開啟舊檔] 及 [專案/方案] 。  
  
3.  在**開啟專案**對話方塊中，開啟保存您解壓縮範例程式碼的資料夾，然後再開啟進行 AsyncFineTuningVB 的 方案 (.sln) 檔案。  
  
4.  在方案總管中，開啟 **CancelAfterTime** 專案的捷徑功能表，然後選擇 [設定為啟始專案]。  
  
5.  選擇 F5 鍵執行執行專案。  
  
     選擇 CTRL+F5 鍵以執行專案，而不進行偵錯。  
  
6.  執行程式數次，確認輸出可能會顯示所有網站、沒有網站或某些網站的輸出。  
  
 如果您不想要下載的專案，您可以檢閱本主題結尾處 MainWindow.xaml.vb 檔案。  
  
## <a name="building-the-example"></a>建置範例  
 本主題中的範例將加入專案中開發時，[取消一項非同步工作或清單的工作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)取消的工作清單。 雖然未明確地使用 [取消] 按鈕，但是此範例會使用相同的 UI。  
  
 若要自行逐步建置範例，請遵循＜下載範例＞一節中的指示，但選擇 [CancelAListOfTasks] 作為 [啟始專案]。 將本主題中的變更新增至該專案。  
  
 若要指定將工作標記為取消之前的最長時間，請將 `CancelAfter` 呼叫新增至 `startButton_Click`，如下列範例所示。 新增的項目會以星號標記。  
  
```vb  
Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
  
    ' Instantiate the CancellationTokenSource.  
    cts = New CancellationTokenSource()  
  
    resultsTextBox.Clear()  
  
    Try  
        ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You   
        ' can adjust the time.)  
        cts.CancelAfter(2500)  
  
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
```  
  
 執行程式數次，確認輸出可能會顯示所有網站、沒有網站或某些網站的輸出。 下列輸出是範例。  
  
```  
Length of the downloaded string: 35990.  
  
Length of the downloaded string: 407399.  
  
Length of the downloaded string: 226091.  
  
Downloads canceled.  
```  
  
## <a name="complete-example"></a>完整範例  
 下列程式碼是範例的 MainWindow.xaml.vb 檔案的完整文字。 星號會標記已針對此範例新增的項目。  
  
 請注意，您必須新增 <xref:System.Net.Http> 的參考。  
  
 您可以從 [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (非同步範例：微調應用程式) 下載專案。  
  
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
            ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You   
            ' can adjust the time.)  
            cts.CancelAfter(2500)  
  
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
  
        ' Process each element in the list of web addresses.  
        For Each url In urlList  
            ' GetAsync returns a Task(Of HttpResponseMessage).   
            ' Argument ct carries the message if the Cancel button is chosen.   
            ' Note that the Cancel button can cancel all remaining downloads.  
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
            ' Retrieve the website contents from the HttpResponseMessage.  
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
        Next  
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
  
' Length of the downloaded string: 35990.  
  
' Length of the downloaded string: 407399.  
  
' Length of the downloaded string: 226091.  
  
' Downloads canceled.  
```  
  
## <a name="see-also"></a>另請參閱  
 [使用 Async 和 Await 進行非同步程式設計 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [逐步解說：使用 Async 和 Await 存取 Web (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [取消一項非同步工作或一份工作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)  
 [微調非同步應用程式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [非同步範例：微調應用程式 (英文)](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
