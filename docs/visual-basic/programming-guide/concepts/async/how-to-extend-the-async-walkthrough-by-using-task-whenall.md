---
title: "如何︰ 使用 Task.WhenAll (Visual Basic) 來擴充非同步逐步解說 |Microsoft 文件"
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
ms.assetid: c06d386d-e996-4da9-bf3d-05a3b6c0a258
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
ms.openlocfilehash: 46c5cb9328f2fa1a4ffc5116d318bc3286419e13
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-visual-basic"></a>如何︰ 使用 Task.WhenAll (Visual Basic) 來擴充非同步逐步解說
您可以改善效能的非同步方案中[逐步解說︰ 存取 Web 使用 Async 和 Await (Visual Basic) 的](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)使用<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>方法。</xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> 這個方法以非同步方式等候多個非同步作業，表示為工作的集合。  
  
 您可能已經注意到在這個逐步解說的網站下載不同的速率。 有時網站是非常緩慢，這會延遲所有剩餘的下載。 當您執行您建置的非同步方案逐步解說中，您可以結束程式輕鬆地如果不想等待，但更好的選項會啟動一次的所有下載並讓更快下載繼續而不需等待的延遲。  
  
 您套用`Task.WhenAll`的工作集合的方法。 應用程式的`WhenAll`傳回集合中的每項工作完成之前未完成的單一工作。 若要平行執行，就會出現的工作，但沒有其他執行緒會建立。 工作可以依任何順序完成。  
  
> [!IMPORTANT]
>  下列程序說明中的非同步應用程式的擴充功能[逐步解說︰ 存取 Web 使用 Async 和 Await (Visual Basic) 的](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。 您可以開發應用程式以完成這個逐步解說，或下載的程式碼來[開發人員程式碼範例](http://go.microsoft.com/fwlink/?LinkId=255191)。  
>   
>  若要執行此範例，您必須安裝 Visual Studio 2012 或更新版本安裝在電腦上。  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a>若要新增 Task.WhenAll GetURLContentsAsync 解決方案  
  
1.  新增`ProcessURLAsync`開發中的第一個應用程式的方法[逐步解說︰ 存取 Web 使用 Async 和 Await (Visual Basic) 的](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。  
  
    -   如果您已下載的程式碼[開發人員程式碼範例](http://go.microsoft.com/fwlink/?LinkId=255191)，開啟 AsyncWalkthrough 專案，然後再新增`ProcessURLAsync`MainWindow.xaml.vb 檔案。  
  
    -   如果您完成逐步解說開發的程式碼，加入`ProcessURLAsync`應用程式，其中包含`GetURLContentsAsync`方法。 此應用程式的 MainWindow.xaml.vb 檔是 「 完整程式碼範例從逐步解說 > 一節的第一個範例。  
  
     `ProcessURLAsync`方法會彙總的主體中的動作`For Each`迴圈`SumPageSizesAsync`在原始的逐步解說。 此方法以非同步方式為位元組陣列，指定網站的內容下載然後並顯示傳回的位元組陣列的長度。  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  註解化或刪除`For Each`迴圈`SumPageSizesAsync`，如下列程式碼所示。  
  
    ```vb  
    'Dim total = 0  
    'For Each url In urlList  
  
    '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
    '    ' The previous line abbreviates the following two assignment statements.  
  
    '    ' GetURLContentsAsync returns a task. At completion, the task  
    '    ' produces a byte array.  
    '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
    '    'Dim urlContents As Byte() = Await getContentsTask  
  
    '    DisplayResults(url, urlContents)  
  
    '    ' Update the total.  
    '    total += urlContents.Length  
    'Next  
    ```  
  
3.  建立工作的集合。 下列程式碼定義[查詢](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)，程式執行時<xref:System.Linq.Enumerable.ToArray%2A>方法建立的每個網站的內容下載工作的集合。</xref:System.Linq.Enumerable.ToArray%2A> 當評估查詢時，會啟動工作。  
  
     將下列程式碼加入至方法`SumPageSizesAsync`宣告後`urlList`。  
  
    ```vb  
    ' Create a query.   
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  套用`Task.WhenAll`至集合的工作， `downloadTasks`。 `Task.WhenAll`傳回已完成的工作集合中的所有工作完成的單一工作。  
  
     在下列範例中，`Await`運算式等候完成的單一工作`WhenAll`傳回。 運算式評估為整數，其中每個整數是下載網站的長度的陣列。 加入下列程式碼以`SumPageSizesAsync`，只是您在上一個步驟中加入的程式碼後面。  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  最後，使用<xref:System.Linq.Enumerable.Sum%2A>方法，以計算所有網站的長度總和。</xref:System.Linq.Enumerable.Sum%2A> 將下列行加入`SumPageSizesAsync`。  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a>若要新增 Task.WhenAll HttpClient.GetByteArrayAsync 解決方案  
  
1.  加入下列版本`ProcessURLAsync`開發中的第二個應用程式[逐步解說︰ 存取 Web 使用 Async 和 Await (Visual Basic) 的](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。  
  
    -   如果您已下載的程式碼[開發人員程式碼範例](http://go.microsoft.com/fwlink/?LinkId=255191)，開啟 AsyncWalkthrough_HttpClient 專案，然後再新增`ProcessURLAsync`MainWindow.xaml.vb 檔案。  
  
    -   如果您完成逐步解說開發的程式碼，加入`ProcessURLAsync`應用程式使用`HttpClient.GetByteArrayAsync`方法。 此應用程式的 MainWindow.xaml.vb 檔是 「 完整程式碼範例從逐步解說 > 一節中的第二個範例。  
  
     `ProcessURLAsync`方法會彙總的主體中的動作`For Each`迴圈`SumPageSizesAsync`在原始的逐步解說。 此方法以非同步方式為位元組陣列，指定網站的內容下載然後並顯示傳回的位元組陣列的長度。  
  
     唯一差別`ProcessURLAsync`在先前程序中的方法是使用<xref:System.Net.Http.HttpClient>執行個體， `client`。</xref:System.Net.Http.HttpClient>  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  註解化或刪除`For Each`迴圈`SumPageSizesAsync`，如下列程式碼所示。  
  
    ```vb  
    'Dim total = 0   
    'For Each url In urlList   
    '    ' GetByteArrayAsync returns a task. At completion, the task   
    '    ' produces a byte array.   
    '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)   
  
    '    ' The following two lines can replace the previous assignment statement.   
    '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)   
    '    'Dim urlContents As Byte() = Await getContentsTask   
  
    '    DisplayResults(url, urlContents)   
  
    '    ' Update the total.   
    '    total += urlContents.Length   
    'Next  
  
    ```  
  
3.  定義[查詢](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)，程式執行時<xref:System.Linq.Enumerable.ToArray%2A>方法建立的每個網站的內容下載工作的集合。</xref:System.Linq.Enumerable.ToArray%2A> 當評估查詢時，會啟動工作。  
  
     將下列程式碼加入至方法`SumPageSizesAsync`宣告後`client`和`urlList`。  
  
    ```vb  
    ' Create a query.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  接下來，套用`Task.WhenAll`至集合的工作， `downloadTasks`。 `Task.WhenAll`傳回已完成的工作集合中的所有工作完成的單一工作。  
  
     在下列範例中，`Await`運算式等候完成的單一工作`WhenAll`傳回。 完成時，`Await`運算式評估為整數，其中每個整數是下載網站的長度的陣列。 加入下列程式碼以`SumPageSizesAsync`，只是您在上一個步驟中加入的程式碼後面。  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  最後，使用<xref:System.Linq.Enumerable.Sum%2A>方法來取得所有網站的長度總和。</xref:System.Linq.Enumerable.Sum%2A> 將下列行加入`SumPageSizesAsync`。  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a>若要測試 Task.WhenAll 解決方案  
  
-   其中一個解決方案中，選擇 F5 鍵以執行程式，然後選擇**啟動** 按鈕。 輸出應該類似的輸出中的非同步方案[逐步解說︰ 存取 Web 使用 Async 和 Await (Visual Basic) 的](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。 但是請注意，網站會出現在不同的順序每次。  
  
## <a name="example"></a>範例  
 下列程式碼顯示使用專案的擴充`GetURLContentsAsync`方法，從 web 下載內容。  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        ' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' Create a query.   
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url)  
  
        ' Use ToArray to execute the query and start the download tasks.  
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' You can do other work here before awaiting.  
  
        ' Await the completion of all the running tasks.  
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
        '' The previous line is equivalent to the following two statements.  
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
        'Dim lengths As Integer() = Await whenAllTask  
  
        Dim total = lengths.Sum()  
  
        'Dim total = 0  
        'For Each url In urlList  
  
        '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
        '    ' The previous line abbreviates the following two assignment statements.  
  
        '    ' GetURLContentsAsync returns a task. At completion, the task  
        '    ' produces a byte array.  
        '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
        '    'Dim urlContents As Byte() = Await getContentsTask  
  
        '    DisplayResults(url, urlContents)  
  
        '    ' Update the total.  
        '    total += urlContents.Length  
        'NextNext  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    ' The actions from the foreach loop are moved to this async method.  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
  
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
  
## <a name="example"></a>範例  
 下列程式碼顯示擴充方法會使用專案`HttpClient.GetByteArrayAsync`從 web 下載內容。  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        '' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Declare an HttpClient object and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' Create a query.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client)  
  
        ' Use ToArray to execute the query and start the download tasks.  
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' You can do other work here before awaiting.  
  
        ' Await the completion of all the running tasks.  
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
        '' The previous line is equivalent to the following two statements.  
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
        'Dim lengths As Integer() = Await whenAllTask  
  
        Dim total = lengths.Sum()  
  
        ''<snippet7>  
        'Dim total = 0  
        'For Each url In urlList  
        '    ' GetByteArrayAsync returns a task. At completion, the task  
        '    ' produces a byte array.  
        '    '<snippet31>  
        '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
        '    '</snippet31>  
  
        '    ' The following two lines can replace the previous assignment statement.  
        '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
        '    'Dim urlContents As Byte() = Await getContentsTask  
  
        '    DisplayResults(url, urlContents)  
  
        '    ' Update the total.  
        '    total += urlContents.Length  
        'NextNext  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://www.msdn.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
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
 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName></xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>   
 [逐步解說︰ 存取 Web 使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
