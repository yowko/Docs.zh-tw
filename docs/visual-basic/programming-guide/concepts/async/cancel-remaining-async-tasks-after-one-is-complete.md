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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1b70822edd972ac33614ab49faad6ff50b0e80b7
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a><span data-ttu-id="cd29a-102">當取消剩餘的非同步工作是完整 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd29a-102">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>
<span data-ttu-id="cd29a-103">使用<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>方法並搭配<xref:System.Threading.CancellationToken>，一個工作完成時，您可以取消所有其餘的工作。</xref:System.Threading.CancellationToken> </xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="cd29a-103">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="cd29a-104">`WhenAny`方法會採用一組工作的引數。</span><span class="sxs-lookup"><span data-stu-id="cd29a-104">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="cd29a-105">這個方法會啟動所有工作，並傳回單一工作。</span><span class="sxs-lookup"><span data-stu-id="cd29a-105">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="cd29a-106">集合中的任何工作完成時，單一工作已完成。</span><span class="sxs-lookup"><span data-stu-id="cd29a-106">The single task is complete when any task in the collection is complete.</span></span>  
  
 <span data-ttu-id="cd29a-107">這個範例示範如何搭配使用取消語彙基元`WhenAny`固守第一項工作完成的工作集合，以及取消其餘的工作。</span><span class="sxs-lookup"><span data-stu-id="cd29a-107">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="cd29a-108">每一項工作會下載網站的內容。</span><span class="sxs-lookup"><span data-stu-id="cd29a-108">Each task downloads the contents of a website.</span></span> <span data-ttu-id="cd29a-109">此範例顯示的第一個完成的下載內容的長度，並取消其他下載。</span><span class="sxs-lookup"><span data-stu-id="cd29a-109">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd29a-110">若要執行範例，您必須擁有 Visual Studio 2012 或較新和.NET Framework 4.5 或更新版本安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="cd29a-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="cd29a-111">下載範例</span><span class="sxs-lookup"><span data-stu-id="cd29a-111">Downloading the Example</span></span>  
 <span data-ttu-id="cd29a-112">您可以下載完整的 Windows Presentation Foundation (WPF) 專案，從[非同步範例︰ 順利微調您的應用程式](http://go.microsoft.com/fwlink/?LinkId=255046)，然後依照下列步驟。</span><span class="sxs-lookup"><span data-stu-id="cd29a-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="cd29a-113">解壓縮您下載的檔案，然後啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="cd29a-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="cd29a-114">在功能表列上，依序選擇 [檔案] ****、[開啟舊檔] ****及 [專案/方案] ****。</span><span class="sxs-lookup"><span data-stu-id="cd29a-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="cd29a-115">在**開啟專案**對話方塊中，開啟保存在解壓縮時，範例程式碼的資料夾，並接著開啟 AsyncFineTuningVB 方案 (.sln) 檔案。</span><span class="sxs-lookup"><span data-stu-id="cd29a-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="cd29a-116">在**方案總管 中**，開啟捷徑功能表**CancelAfterOneTask**專案，然後再選擇**設定為啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="cd29a-116">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="cd29a-117">選擇 F5 鍵以執行專案。</span><span class="sxs-lookup"><span data-stu-id="cd29a-117">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="cd29a-118">選擇 Ctrl + F5 鍵以執行專案，但不偵錯它。</span><span class="sxs-lookup"><span data-stu-id="cd29a-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="cd29a-119">若要確認不同的下載完成第一次執行程式數次。</span><span class="sxs-lookup"><span data-stu-id="cd29a-119">Run the program several times to verify that different downloads finish first.</span></span>  
  
 <span data-ttu-id="cd29a-120">如果您不想要下載的專案，您可以檢閱本主題結尾處的 MainWindow.xaml.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="cd29a-120">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="cd29a-121">建置範例</span><span class="sxs-lookup"><span data-stu-id="cd29a-121">Building the Example</span></span>  
 <span data-ttu-id="cd29a-122">本主題中的範例將加入專案中開發[取消一項非同步工作或工作清單](http://msdn.microsoft.com/library/d6e4e801-df64-4705-98fc-df725a577fb0)取消的工作清單。</span><span class="sxs-lookup"><span data-stu-id="cd29a-122">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks](http://msdn.microsoft.com/library/d6e4e801-df64-4705-98fc-df725a577fb0) to cancel a list of tasks.</span></span> <span data-ttu-id="cd29a-123">雖然此範例會使用相同的 UI，**取消**按鈕不會明確地使用。</span><span class="sxs-lookup"><span data-stu-id="cd29a-123">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="cd29a-124">若要建置範例自行逐步解說，依照指示下載 「 範例 」 一節中的，但是選擇**CancelAListOfTasks**為**啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="cd29a-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="cd29a-125">本主題中加入該專案所做的變更。</span><span class="sxs-lookup"><span data-stu-id="cd29a-125">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="cd29a-126">中的 MainWindow.xaml.vb 檔案**CancelAListOfTasks**專案中，從迴圈中移動的每個網站的處理步驟開始轉換`AccessTheWebAsync`下列非同步方法。</span><span class="sxs-lookup"><span data-stu-id="cd29a-126">In the MainWindow.xaml.vb file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>  
  
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
  
 <span data-ttu-id="cd29a-127">在`AccessTheWebAsync`，這個範例會使用查詢，<xref:System.Linq.Enumerable.ToArray%2A>方法，而`WhenAny`方法來建立並啟動工作的陣列。</xref:System.Linq.Enumerable.ToArray%2A></span><span class="sxs-lookup"><span data-stu-id="cd29a-127">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="cd29a-128">應用程式的`WhenAny`陣列傳回的單一工作，當等候時，會評估為連線到陣列中的完成工作的第一個工作。</span><span class="sxs-lookup"><span data-stu-id="cd29a-128">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>  
  
 <span data-ttu-id="cd29a-129">進行下列變更在`AccessTheWebAsync`。</span><span class="sxs-lookup"><span data-stu-id="cd29a-129">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="cd29a-130">星號標示的程式碼檔案中的變更。</span><span class="sxs-lookup"><span data-stu-id="cd29a-130">Asterisks mark the changes in the code file.</span></span>  
  
1.  <span data-ttu-id="cd29a-131">註解化或刪除迴圈。</span><span class="sxs-lookup"><span data-stu-id="cd29a-131">Comment out or delete the loop.</span></span>  
  
2.  <span data-ttu-id="cd29a-132">建立查詢，在執行時，會產生一組一般工作。</span><span class="sxs-lookup"><span data-stu-id="cd29a-132">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="cd29a-133">每次呼叫`ProcessURLAsync`傳回<xref:System.Threading.Tasks.Task%601>其中`TResult`是一個整數。</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="cd29a-133">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
<span data-ttu-id="cd29a-134"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="cd29a-134"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
3.  <span data-ttu-id="cd29a-135">呼叫`ToArray`來執行查詢，並開始工作。</span><span class="sxs-lookup"><span data-stu-id="cd29a-135">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="cd29a-136">應用程式的`WhenAny`下一個步驟中的方法會執行查詢，並啟動工作，而不使用`ToArray`，但不是可能的其他方法。</span><span class="sxs-lookup"><span data-stu-id="cd29a-136">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="cd29a-137">最安全的作法是明確地強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="cd29a-137">The safest practice is to force execution of the query explicitly.</span></span>  
  
<span data-ttu-id="cd29a-138"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="cd29a-138"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span></span>  
4.  <span data-ttu-id="cd29a-139">呼叫`WhenAny`上工作的集合。</span><span class="sxs-lookup"><span data-stu-id="cd29a-139">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="cd29a-140">`WhenAny`傳回`Task(Of Task(Of Integer))`或`Task<Task<int>>`。</span><span class="sxs-lookup"><span data-stu-id="cd29a-140">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="cd29a-141">也就是`WhenAny`傳回的工作，評估單一`Task(Of Integer)`或`Task<int>`時，它會等候。</span><span class="sxs-lookup"><span data-stu-id="cd29a-141">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="cd29a-142">該單一的工作會在完成集合中的第一項工作。</span><span class="sxs-lookup"><span data-stu-id="cd29a-142">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="cd29a-143">已完成第一次工作指派給`firstFinishedTask`。</span><span class="sxs-lookup"><span data-stu-id="cd29a-143">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="cd29a-144">型別`firstFinishedTask`是<xref:System.Threading.Tasks.Task%601>其中`TResult`是一個整數，因為這是傳回型別`ProcessURLAsync`。</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="cd29a-144">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>  
  
```vb  
' ***Call WhenAny and then await the result. The task that finishes   
' first is assigned to firstFinishedTask.  
Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
```  
  
5.  <span data-ttu-id="cd29a-145">在此範例中，您想要知道只能在第一次完成的工作項目。</span><span class="sxs-lookup"><span data-stu-id="cd29a-145">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="cd29a-146">因此，使用<xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName>取消其餘的工作。</xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="cd29a-146">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName> to cancel the remaining tasks.</span></span>  
  
```vb  
' ***Cancel the rest of the downloads. You just want the first one.  
cts.Cancel()  
```  
  
6.  <span data-ttu-id="cd29a-147">最後，等候`firstFinishedTask`擷取下載的內容長度。</span><span class="sxs-lookup"><span data-stu-id="cd29a-147">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>  
  
```vb  
Dim length = Await firstFinishedTask  
resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
```  
  
 <span data-ttu-id="cd29a-148">若要確認不同的下載完成第一次執行程式數次。</span><span class="sxs-lookup"><span data-stu-id="cd29a-148">Run the program several times to verify that different downloads finish first.</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="cd29a-149">完整範例</span><span class="sxs-lookup"><span data-stu-id="cd29a-149">Complete Example</span></span>  
 <span data-ttu-id="cd29a-150">下列程式碼是完整的 MainWindow.xaml.vb 或 MainWindow.xaml.cs 檔案的範例。</span><span class="sxs-lookup"><span data-stu-id="cd29a-150">The following code is the complete MainWindow.xaml.vb or MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="cd29a-151">星號標示此範例中所新增的項目。</span><span class="sxs-lookup"><span data-stu-id="cd29a-151">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="cd29a-152">請注意，您必須加入<xref:System.Net.Http>.</xref:System.Net.Http>的參考</span><span class="sxs-lookup"><span data-stu-id="cd29a-152">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="cd29a-153">您可以下載的專案[非同步範例︰ 順利微調您的應用程式](http://go.microsoft.com/fwlink/?LinkId=255046)。</span><span class="sxs-lookup"><span data-stu-id="cd29a-153">You can download the project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cd29a-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd29a-154">See Also</span></span>  
 <span data-ttu-id="cd29a-155"><xref:System.Threading.Tasks.Task.WhenAny%2A></xref:System.Threading.Tasks.Task.WhenAny%2A></span><span class="sxs-lookup"><span data-stu-id="cd29a-155"><xref:System.Threading.Tasks.Task.WhenAny%2A></span></span>   
<span data-ttu-id="cd29a-156"> [微調非同步應用程式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) </span><span class="sxs-lookup"><span data-stu-id="cd29a-156"> [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) </span></span>  
<span data-ttu-id="cd29a-157"> [非同步程式設計使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="cd29a-157"> [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="cd29a-158"> [非同步範例︰ 微調應用程式](http://go.microsoft.com/fwlink/?LinkId=255046)</span><span class="sxs-lookup"><span data-stu-id="cd29a-158"> [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046)</span></span>
