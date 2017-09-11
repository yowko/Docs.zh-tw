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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6fbf4611ecd64abfd016963dff887d82aad333b7
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-visual-basic"></a><span data-ttu-id="1861a-102">啟動多項非同步工作並處理它們完成 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1861a-102">Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)</span></span>
<span data-ttu-id="1861a-103">使用<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>，您可以同時啟動多項工作，並在它們正在完成而不是要啟動的順序處理這些時，處理逐一。</xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="1861a-103">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>, you can start multiple tasks at the same time and process them one by one as they’re completed rather than process them in the order in which they're started.</span></span>  
  
 <span data-ttu-id="1861a-104">下列範例會使用查詢來建立工作的集合。</span><span class="sxs-lookup"><span data-stu-id="1861a-104">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="1861a-105">每一項工作會下載指定的網站的內容。</span><span class="sxs-lookup"><span data-stu-id="1861a-105">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="1861a-106">在一段時間的每個反覆項目執行迴圈，等候的呼叫`WhenAny`先完成其下載的工作集合中傳回的工作。</span><span class="sxs-lookup"><span data-stu-id="1861a-106">In each iteration of a while loop, an awaited call to `WhenAny` returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="1861a-107">這項工作是從集合中移除，並處理。</span><span class="sxs-lookup"><span data-stu-id="1861a-107">That task is removed from the collection and processed.</span></span> <span data-ttu-id="1861a-108">迴圈重複，直到集合包含沒有更多的工作。</span><span class="sxs-lookup"><span data-stu-id="1861a-108">The loop repeats until the collection contains no more tasks.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1861a-109">若要執行範例，您必須擁有 Visual Studio 2012 或較新和.NET Framework 4.5 或更新版本安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="1861a-109">To run the examples, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="1861a-110">下載範例</span><span class="sxs-lookup"><span data-stu-id="1861a-110">Downloading the Example</span></span>  
 <span data-ttu-id="1861a-111">您可以下載完整的 Windows Presentation Foundation (WPF) 專案，從[非同步範例︰ 順利微調您的應用程式](http://go.microsoft.com/fwlink/?LinkId=255046)，然後依照下列步驟。</span><span class="sxs-lookup"><span data-stu-id="1861a-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="1861a-112">解壓縮您下載的檔案，然後啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="1861a-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="1861a-113">在功能表列上，依序選擇 [檔案] ****、[開啟舊檔] ****及 [專案/方案] ****。</span><span class="sxs-lookup"><span data-stu-id="1861a-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="1861a-114">在**開啟專案**對話方塊中，開啟保存在解壓縮時，範例程式碼的資料夾，並接著開啟 AsyncFineTuningVB 方案 (.sln) 檔案。</span><span class="sxs-lookup"><span data-stu-id="1861a-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="1861a-115">在**方案總管 中**，開啟捷徑功能表**ProcessTasksAsTheyFinish**專案，然後再選擇**設定為啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="1861a-115">In **Solution Explorer**, open the shortcut menu for the **ProcessTasksAsTheyFinish** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="1861a-116">選擇 F5 鍵以執行專案。</span><span class="sxs-lookup"><span data-stu-id="1861a-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="1861a-117">選擇 Ctrl + F5 鍵以執行專案，但不偵錯它。</span><span class="sxs-lookup"><span data-stu-id="1861a-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="1861a-118">若要確認下載的長度不一定會出現在相同的順序執行專案數次。</span><span class="sxs-lookup"><span data-stu-id="1861a-118">Run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
 <span data-ttu-id="1861a-119">如果您不想要下載的專案，您可以檢閱本主題結尾處的 MainWindow.xaml.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="1861a-119">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="1861a-120">建置範例</span><span class="sxs-lookup"><span data-stu-id="1861a-120">Building the Example</span></span>  
 <span data-ttu-id="1861a-121">這個範例會將開發中的程式碼加入[後一個完整 (Visual Basic) 取消剩餘的非同步工作](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)，並使用相同的 UI。</span><span class="sxs-lookup"><span data-stu-id="1861a-121">This example adds to the code that’s developed in [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) and uses the same UI.</span></span>  
  
 <span data-ttu-id="1861a-122">若要建置範例自行逐步解說，依照指示下載 「 範例 」 一節中的，但是選擇**CancelAfterOneTask**為**啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="1861a-122">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAfterOneTask** as the **StartUp Project**.</span></span> <span data-ttu-id="1861a-123">本主題中加入變更`AccessTheWebAsync`該專案中的方法。</span><span class="sxs-lookup"><span data-stu-id="1861a-123">Add the changes in this topic to the `AccessTheWebAsync` method in that project.</span></span> <span data-ttu-id="1861a-124">所做的變更會以星號標示。</span><span class="sxs-lookup"><span data-stu-id="1861a-124">The changes are marked with asterisks.</span></span>  
  
 <span data-ttu-id="1861a-125">**CancelAfterOneTask**專案已經包含的查詢，在執行時，會建立一組工作。</span><span class="sxs-lookup"><span data-stu-id="1861a-125">The **CancelAfterOneTask** project already includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="1861a-126">每次呼叫`ProcessURLAsync`在下列程式碼會傳回<xref:System.Threading.Tasks.Task%601>其中`TResult`是一個整數。</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="1861a-126">Each call to `ProcessURLAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
<span data-ttu-id="1861a-127"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="1861a-127"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="1861a-128">在專案的 MainWindow.xaml.vb 檔案中，進行下列變更`AccessTheWebAsync`方法。</span><span class="sxs-lookup"><span data-stu-id="1861a-128">In the MainWindow.xaml.vb file of the  project, make the following changes to the `AccessTheWebAsync` method.</span></span>  
  
-   <span data-ttu-id="1861a-129">執行查詢，<xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>而不是<xref:System.Linq.Enumerable.ToArray%2A>。</xref:System.Linq.Enumerable.ToArray%2A></xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>套用</span><span class="sxs-lookup"><span data-stu-id="1861a-129">Execute the query by applying <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName> instead of <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
<span data-ttu-id="1861a-130"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="1861a-130"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
-   <span data-ttu-id="1861a-131">新增 while 迴圈，每個工作集合中執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="1861a-131">Add a while loop that performs the following steps for each task in the collection.</span></span>  
  
    1.  <span data-ttu-id="1861a-132">等候呼叫`WhenAny`來識別要完成其下載集合的第一個工作。</span><span class="sxs-lookup"><span data-stu-id="1861a-132">Awaits a call to `WhenAny` to identify the first task in the collection to finish its download.</span></span>  
  
<span data-ttu-id="1861a-133"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="1861a-133"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span></span>  
    2.  <span data-ttu-id="1861a-134">從集合中移除該工作。</span><span class="sxs-lookup"><span data-stu-id="1861a-134">Removes that task from the collection.</span></span>  
  
<span data-ttu-id="1861a-135"><CodeContentPlaceHolder>3</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="1861a-135"><CodeContentPlaceHolder>3</CodeContentPlaceHolder></span></span>  
    3.  <span data-ttu-id="1861a-136">等候`firstFinishedTask`，這由呼叫`ProcessURLAsync`。</span><span class="sxs-lookup"><span data-stu-id="1861a-136">Awaits `firstFinishedTask`, which is returned by a call to `ProcessURLAsync`.</span></span> <span data-ttu-id="1861a-137">`firstFinishedTask`變數是<xref:System.Threading.Tasks.Task%601>其中`TReturn`是一個整數。</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="1861a-137">The `firstFinishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TReturn` is an integer.</span></span> <span data-ttu-id="1861a-138">工作已完成，但您等候它擷取的長度已下載的網站，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1861a-138">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span>  
  
        ```vb  
        Dim length = Await firstFinishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        ```  
  
 <span data-ttu-id="1861a-139">您應該執行專案數次，以確認下載的長度不一定會出現在相同的順序。</span><span class="sxs-lookup"><span data-stu-id="1861a-139">You should run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="1861a-140">您可以使用`WhenAny`在迴圈中，此範例中，以解決問題牽涉到少量的工作中所述。</span><span class="sxs-lookup"><span data-stu-id="1861a-140">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="1861a-141">不過，如果您有大量的工作要處理，其他方法會更有效率。</span><span class="sxs-lookup"><span data-stu-id="1861a-141">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="1861a-142">如需詳細資訊和範例，請參閱[處理工作完成時加以](http://go.microsoft.com/fwlink/?LinkId=260810)。</span><span class="sxs-lookup"><span data-stu-id="1861a-142">For more information and examples, see [Processing Tasks as they complete](http://go.microsoft.com/fwlink/?LinkId=260810).</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="1861a-143">完整範例</span><span class="sxs-lookup"><span data-stu-id="1861a-143">Complete Example</span></span>  
 <span data-ttu-id="1861a-144">下列程式碼是範例的 MainWindow.xaml.vb 檔案的完整文字。</span><span class="sxs-lookup"><span data-stu-id="1861a-144">The following code is the complete text of the MainWindow.xaml.vb file for the example.</span></span> <span data-ttu-id="1861a-145">星號標示此範例中所新增的項目。</span><span class="sxs-lookup"><span data-stu-id="1861a-145">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="1861a-146">請注意，您必須加入<xref:System.Net.Http>.</xref:System.Net.Http>的參考</span><span class="sxs-lookup"><span data-stu-id="1861a-146">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="1861a-147">您可以下載的專案[非同步範例︰ 順利微調您的應用程式](http://go.microsoft.com/fwlink/?LinkId=255046)。</span><span class="sxs-lookup"><span data-stu-id="1861a-147">You can download the project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1861a-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1861a-148">See Also</span></span>  
 <span data-ttu-id="1861a-149"><xref:System.Threading.Tasks.Task.WhenAny%2A></xref:System.Threading.Tasks.Task.WhenAny%2A></span><span class="sxs-lookup"><span data-stu-id="1861a-149"><xref:System.Threading.Tasks.Task.WhenAny%2A></span></span>   
<span data-ttu-id="1861a-150"> [微調非同步應用程式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) </span><span class="sxs-lookup"><span data-stu-id="1861a-150"> [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) </span></span>  
<span data-ttu-id="1861a-151"> [非同步程式設計使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="1861a-151"> [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="1861a-152"> [非同步範例︰ 微調應用程式](http://go.microsoft.com/fwlink/?LinkId=255046)</span><span class="sxs-lookup"><span data-stu-id="1861a-152"> [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046)</span></span>
