---
title: "如何： 使用 Task.WhenAll (Visual Basic) 擴充非同步逐步解說"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c06d386d-e996-4da9-bf3d-05a3b6c0a258
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 49cca45336cb25850c888e3389e97b323c70d89d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-visual-basic"></a>如何： 使用 Task.WhenAll (Visual Basic) 擴充非同步逐步解說
您可以改善效能中的非同步方案[逐步解說： 存取使用 Async 和 Await (Visual Basic) 的 Web](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)使用<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>方法。 此方法會以非同步方式等候多個非同步作業進行，這些作業是以工作集合來表示。  
  
 您在此逐步解說中可能已注意到網站下載的速度各自不同。 有時其中一個網站的速度很慢，而導致所有其餘下載延後執行。 當您執行在此逐步解說中建立的非同步方案時，如果不想要等候，您可以輕鬆地結束程式；但更好的做法是同時啟動所有下載，並讓較快的下載繼續執行而不等候延遲的下載。  
  
 您可以將 `Task.WhenAll` 方法套用至工作集合。 套用 `WhenAll` 會傳回未完成的單一工作，直到集合中的所有工作都完成為止。 工作似乎會平行執行，但不會建立其他任何執行緒。 工作可以依任何順序完成。  
  
> [!IMPORTANT]
>  下列程序描述擴充功能的非同步應用程式都是以開發[逐步解說： 存取使用 Async 和 Await (Visual Basic) 的 Web](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。 您可以藉由完成此逐步解說，或從[開發人員程式碼範例](http://go.microsoft.com/fwlink/?LinkId=255191)下載程式碼，來開發應用程式。  
>   
>  若要執行範例，您必須在電腦上安裝 Visual Studio 2012 或更新版本。  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a>將 Task.WhenAll 新增至您的 GetURLContentsAsync 方案  
  
1.  新增`ProcessURLAsync`開發中的第一個應用程式的方法[逐步解說： 存取使用 Async 和 Await (Visual Basic) 的 Web](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。  
  
    -   如果您已下載的程式碼[開發人員程式碼範例](http://go.microsoft.com/fwlink/?LinkId=255191)、 開啟 AsyncWalkthrough 專案，然後再將`ProcessURLAsync`MainWindow.xaml.vb 檔案。  
  
    -   如果您藉由完成此逐步解說來開發程式碼，請將 `ProcessURLAsync` 新增至包含 `GetURLContentsAsync` 方法的應用程式。 此應用程式的 MainWindow.xaml.vb 檔是 「 完整程式碼範例從逐步解說 > 一節中的第一個範例。  
  
     `ProcessURLAsync` 方法會合併原始逐步解說中 `SumPageSizesAsync` 之 `For Each` 迴圈主體內的動作。 此方法會以非同步方式將指定網站的內容下載為位元組陣列，然後顯示並傳回位元組陣列的長度。  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  將 `SumPageSizesAsync` 中的 `For Each` 迴圈註解化或刪除，如下列程式碼所示。  
  
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
  
3.  建立工作集合。 下列程式碼定義一個[查詢](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)，當 <xref:System.Linq.Enumerable.ToArray%2A> 方法執行此查詢時，會建立工作集合以下載每個網站的內容。 工作會在評估查詢之後啟動。  
  
     將下列程式碼新增至 `urlList` 宣告後面的 `SumPageSizesAsync` 方法。  
  
    ```vb  
    ' Create a query.   
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  將 `Task.WhenAll` 套用至工作集合 `downloadTasks`。 `Task.WhenAll` 會傳回當工作集合中所有工作完成後才會完成的單一工作。  
  
     在下列範例中，`Await` 運算式會等候 `WhenAll` 傳回的單一工作完成。 此運算式會評估為整數陣列，其中每個整數都是所下載網站的長度。 將下列程式碼新增至 `SumPageSizesAsync`，就在您於上一個步驟中新增的程式碼之後。  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  最後，使用 <xref:System.Linq.Enumerable.Sum%2A> 方法來計算所有網站的長度總和。 將下列程式碼行新增至 `SumPageSizesAsync`。  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a>將 Task.WhenAll 新增至 HttpClient.GetByteArrayAsync 方案  
  
1.  加入下列版本`ProcessURLAsync`開發中的第二個應用程式[逐步解說： 存取使用 Async 和 Await (Visual Basic) 的 Web](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。  
  
    -   如果您已下載的程式碼[開發人員程式碼範例](http://go.microsoft.com/fwlink/?LinkId=255191)、 開啟位於 AsyncWalkthrough_HttpClient 專案，然後再將`ProcessURLAsync`MainWindow.xaml.vb 檔案。  
  
    -   如果您藉由完成此逐步解說來開發程式碼，請將 `ProcessURLAsync` 新增至使用 `HttpClient.GetByteArrayAsync` 方法的應用程式。 此應用程式的 MainWindow.xaml.vb 檔是 「 完整程式碼範例從逐步解說 > 一節中的第二個範例。  
  
     `ProcessURLAsync` 方法會合併原始逐步解說中 `SumPageSizesAsync` 之 `For Each` 迴圈主體內的動作。 此方法會以非同步方式將指定網站的內容下載為位元組陣列，然後顯示並傳回位元組陣列的長度。  
  
     其與上一個步驟中 `ProcessURLAsync` 方法的唯一差別，在於使用了 <xref:System.Net.Http.HttpClient> 執行個體 `client`。  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  將 `SumPageSizesAsync` 中的 `For Each` 迴圈註解化或刪除，如下列程式碼所示。  
  
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
  
3.  定義一個[查詢](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)，當 <xref:System.Linq.Enumerable.ToArray%2A> 方法執行此查詢時，會建立工作集合以下載每個網站的內容。 工作會在評估查詢之後啟動。  
  
     將下列程式碼新增至 `client` 和 `urlList` 宣告後面的 `SumPageSizesAsync` 方法。  
  
    ```vb  
    ' Create a query.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  接下來，將 `Task.WhenAll` 套用至工作集合 `downloadTasks`。 `Task.WhenAll` 會傳回當工作集合中所有工作完成後才會完成的單一工作。  
  
     在下列範例中，`Await` 運算式會等候 `WhenAll` 傳回的單一工作完成。 完成時，`Await` 運算式會評估為整數陣列，其中每個整數都是所下載網站的長度。 將下列程式碼新增至 `SumPageSizesAsync`，就在您於上一個步驟中新增的程式碼之後。  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  最後，使用 <xref:System.Linq.Enumerable.Sum%2A> 方法取得所有網站的長度總和。 將下列程式碼行新增至 `SumPageSizesAsync`。  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a>測試 Task.WhenAll 方案  
  
-   針對任一方案，選擇 F5 鍵以執行程式，然後選擇 [開始] 按鈕。 輸出看起來應該像中的非同步方案的輸出[逐步解說： 存取使用 Async 和 Await (Visual Basic) 的 Web](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。 不過請注意，網站每次出現的順序都不同。  
  
## <a name="example"></a>範例  
 下列程式碼顯示專案擴充，其使用 `GetURLContentsAsync` 方法從 Web 下載內容。  
  
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
 下列程式碼顯示專案擴充，其使用 `HttpClient.GetByteArrayAsync` 方法從 Web 下載內容。  
  
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
 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>  
 [逐步解說：使用 Async 和 Await 存取 Web (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
