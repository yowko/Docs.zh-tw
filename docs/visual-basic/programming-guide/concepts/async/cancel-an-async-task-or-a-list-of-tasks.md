---
title: "取消一項非同步工作或一份工作 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9ee1b71-5bec-4736-a1e9-448042dd7215
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 916577107bd65559aed71dc9bb2921969a117e90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-visual-basic"></a><span data-ttu-id="93b2f-102">取消一項非同步工作或一份工作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93b2f-102">Cancel an Async Task or a List of Tasks (Visual Basic)</span></span>
<span data-ttu-id="93b2f-103">如果您不想要等候非同步應用程式完成，則可以設定可用來取消非同步應用程式的按鈕。</span><span class="sxs-lookup"><span data-stu-id="93b2f-103">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="93b2f-104">遵循本主題中的範例，即可將取消按鈕新增至下載某個網站內容或網站清單的應用程式。</span><span class="sxs-lookup"><span data-stu-id="93b2f-104">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span></span>  
  
 <span data-ttu-id="93b2f-105">範例會使用 UI，[微調非同步應用程式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)描述。</span><span class="sxs-lookup"><span data-stu-id="93b2f-105">The examples use the UI that [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) describes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93b2f-106">若要執行範例，您必須在電腦上安裝 Visual Studio 2012 或更新版本以及 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="93b2f-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <a name="BKMK_CancelaTask"></a> <span data-ttu-id="93b2f-107">取消工作</span><span class="sxs-lookup"><span data-stu-id="93b2f-107">Cancel a Task</span></span>  
 <span data-ttu-id="93b2f-108">第一個範例會建立 [取消] 按鈕與單一下載工作的關聯。</span><span class="sxs-lookup"><span data-stu-id="93b2f-108">The first example associates the **Cancel** button with a single download task.</span></span> <span data-ttu-id="93b2f-109">如果您在應用程式下載內容時選擇該按鈕，則會取消下載。</span><span class="sxs-lookup"><span data-stu-id="93b2f-109">If you choose the button while the application is downloading content, the download is canceled.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="93b2f-110">下載範例</span><span class="sxs-lookup"><span data-stu-id="93b2f-110">Downloading the Example</span></span>  
 <span data-ttu-id="93b2f-111">您可以從 [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) (非同步範例：微調應用程式) 下載完整 Windows Presentation Foundation (WPF) 專案，然後遵循下列步驟。</span><span class="sxs-lookup"><span data-stu-id="93b2f-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="93b2f-112">解壓縮您下載的檔案，然後啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="93b2f-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="93b2f-113">在功能表列上，依序選擇 [檔案] 、[開啟舊檔] 及 [專案/方案] 。</span><span class="sxs-lookup"><span data-stu-id="93b2f-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="93b2f-114">在**開啟專案**對話方塊中，開啟保存您解壓縮範例程式碼的資料夾，然後再開啟進行 AsyncFineTuningVB 的 方案 (.sln) 檔案。</span><span class="sxs-lookup"><span data-stu-id="93b2f-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="93b2f-115">在方案總管中，開啟 **CancelATask** 專案的捷徑功能表，然後選擇 [設定為啟始專案]。</span><span class="sxs-lookup"><span data-stu-id="93b2f-115">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="93b2f-116">選擇 F5 鍵執行執行專案。</span><span class="sxs-lookup"><span data-stu-id="93b2f-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="93b2f-117">選擇 CTRL+F5 鍵以執行專案，而不進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="93b2f-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="93b2f-118">如果您不想要下載的專案，您可以檢閱本主題結尾處的 MainWindow.xaml.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="93b2f-118">If you don't want to download the project, you can review the MainWindow.xaml.vb files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="93b2f-119">建置範例</span><span class="sxs-lookup"><span data-stu-id="93b2f-119">Building the Example</span></span>  
 <span data-ttu-id="93b2f-120">下列變更會將 [取消] 按鈕新增至下載網站的應用程式。</span><span class="sxs-lookup"><span data-stu-id="93b2f-120">The following changes add a **Cancel** button to an application that downloads a website.</span></span> <span data-ttu-id="93b2f-121">如果您不想要下載或建置範例，則可以檢閱本主題結尾處的＜完整範例＞一節中的最終產品。</span><span class="sxs-lookup"><span data-stu-id="93b2f-121">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span></span> <span data-ttu-id="93b2f-122">星號會標記程式碼中的變更。</span><span class="sxs-lookup"><span data-stu-id="93b2f-122">Asterisks mark the changes in the code.</span></span>  
  
 <span data-ttu-id="93b2f-123">若要自行逐步建置範例，請遵循＜下載範例＞一節中的指示，但選擇 [StarterCode] 作為 [啟始專案]，而非 [CancelATask]。</span><span class="sxs-lookup"><span data-stu-id="93b2f-123">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span></span>  
  
 <span data-ttu-id="93b2f-124">MainWindow.xaml.vb 檔案中的該專案，然後新增下列變更。</span><span class="sxs-lookup"><span data-stu-id="93b2f-124">Then add the following changes to the MainWindow.xaml.vb file of that project.</span></span>  
  
1.  <span data-ttu-id="93b2f-125">宣告 `CancellationTokenSource` 變數 `cts`，這是在存取它之所有方法的範圍內。</span><span class="sxs-lookup"><span data-stu-id="93b2f-125">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span></span>  
  
    ```vb  
    Class MainWindow  
  
        ' ***Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
    ```  
  
2.  <span data-ttu-id="93b2f-126">針對 [取消] 按鈕新增下列事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="93b2f-126">Add the following event handler for the **Cancel** button.</span></span> <span data-ttu-id="93b2f-127">事件處理常式會使用 <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> 方法，以在使用者要求取消時通知 `cts`。</span><span class="sxs-lookup"><span data-stu-id="93b2f-127">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> method to notify `cts` when the user requests cancellation.</span></span>  
  
    ```vb  
    ' ***Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
    ```  
  
3.  <span data-ttu-id="93b2f-128">在 [開始] 按鈕 `startButton_Click` 的事件處理常式中進行下列變更。</span><span class="sxs-lookup"><span data-stu-id="93b2f-128">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span></span>  
  
    -   <span data-ttu-id="93b2f-129">具現化 `CancellationTokenSource`、`cts`。</span><span class="sxs-lookup"><span data-stu-id="93b2f-129">Instantiate the `CancellationTokenSource`, `cts`.</span></span>  
  
        ```vb  
        ' ***Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
        ```  
  
    -   <span data-ttu-id="93b2f-130">在下載所指定網站內容的 `AccessTheWebAsync` 呼叫中，傳送 `cts` 的 <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> 屬性作為引數。</span><span class="sxs-lookup"><span data-stu-id="93b2f-130">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> property of `cts` as an argument.</span></span> <span data-ttu-id="93b2f-131">如果要求取消，則 `Token` 屬性會傳播訊息。</span><span class="sxs-lookup"><span data-stu-id="93b2f-131">The `Token` property propagates the message if cancellation is requested.</span></span> <span data-ttu-id="93b2f-132">新增 catch 區塊，以在使用者選擇取消下載作業時顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="93b2f-132">Add a catch block that displays a message if the user chooses to cancel the download operation.</span></span> <span data-ttu-id="93b2f-133">下列程式碼示範這些變更。</span><span class="sxs-lookup"><span data-stu-id="93b2f-133">The following code shows the changes.</span></span>  
  
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
  
4.  <span data-ttu-id="93b2f-134">在 `AccessTheWebAsync` 中，使用 <xref:System.Net.Http.HttpClient> 型別中 `GetAsync` 方法的 <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> 多載來下載網站的內容。</span><span class="sxs-lookup"><span data-stu-id="93b2f-134">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span></span> <span data-ttu-id="93b2f-135">將 `ct` (`AccessTheWebAsync` 的 <xref:System.Threading.CancellationToken> 參數) 傳遞為第二個引數。</span><span class="sxs-lookup"><span data-stu-id="93b2f-135">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span></span> <span data-ttu-id="93b2f-136">如果使用者選擇 [取消] 按鈕，則權杖會夾帶訊息。</span><span class="sxs-lookup"><span data-stu-id="93b2f-136">The token carries the message if the user chooses the **Cancel** button.</span></span>  
  
     <span data-ttu-id="93b2f-137">下列程式碼示範 `AccessTheWebAsync` 中的變更。</span><span class="sxs-lookup"><span data-stu-id="93b2f-137">The following code shows the changes in `AccessTheWebAsync`.</span></span>  
  
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
  
5.  <span data-ttu-id="93b2f-138">如果您未取消程式，則會產生下列輸出。</span><span class="sxs-lookup"><span data-stu-id="93b2f-138">If you don’t cancel the program, it produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Length of the downloaded string: 158125.  
    ```  
  
     <span data-ttu-id="93b2f-139">如果您在程式完成下載內容之前選擇 [取消] 按鈕，程式會產生下列輸出。</span><span class="sxs-lookup"><span data-stu-id="93b2f-139">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Download canceled.  
    ```  
  
##  <a name="BKMK_CancelaListofTasks"></a> <span data-ttu-id="93b2f-140">取消工作清單</span><span class="sxs-lookup"><span data-stu-id="93b2f-140">Cancel a List of Tasks</span></span>  
 <span data-ttu-id="93b2f-141">您可以將相同 `CancellationTokenSource` 執行個體與每項工作建立關聯，以擴充先前的範例來取消許多工作。</span><span class="sxs-lookup"><span data-stu-id="93b2f-141">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span></span> <span data-ttu-id="93b2f-142">如果您選擇 [取消] 按鈕，即會取消所有尚未完成的工作。</span><span class="sxs-lookup"><span data-stu-id="93b2f-142">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="93b2f-143">下載範例</span><span class="sxs-lookup"><span data-stu-id="93b2f-143">Downloading the Example</span></span>  
 <span data-ttu-id="93b2f-144">您可以從 [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) (非同步範例：微調應用程式) 下載完整 Windows Presentation Foundation (WPF) 專案，然後遵循下列步驟。</span><span class="sxs-lookup"><span data-stu-id="93b2f-144">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="93b2f-145">解壓縮您下載的檔案，然後啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="93b2f-145">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="93b2f-146">在功能表列上，依序選擇 [檔案] 、[開啟舊檔] 及 [專案/方案] 。</span><span class="sxs-lookup"><span data-stu-id="93b2f-146">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="93b2f-147">在**開啟專案**對話方塊中，開啟保存您解壓縮範例程式碼的資料夾，然後再開啟進行 AsyncFineTuningVB 的 方案 (.sln) 檔案。</span><span class="sxs-lookup"><span data-stu-id="93b2f-147">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="93b2f-148">在方案總管中，開啟 **CancelAListOfTasks** 專案的捷徑功能表，然後選擇 [設定為啟始專案]。</span><span class="sxs-lookup"><span data-stu-id="93b2f-148">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="93b2f-149">選擇 F5 鍵執行執行專案。</span><span class="sxs-lookup"><span data-stu-id="93b2f-149">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="93b2f-150">選擇 CTRL+F5 鍵以執行專案，而不進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="93b2f-150">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="93b2f-151">如果您不想要下載的專案，您可以檢閱本主題結尾處的 MainWindow.xaml.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="93b2f-151">If you don't want to download the project, you can review the MainWindow.xaml.vb files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="93b2f-152">建置範例</span><span class="sxs-lookup"><span data-stu-id="93b2f-152">Building the Example</span></span>  
 <span data-ttu-id="93b2f-153">若要自行逐步擴充範例，請遵循＜下載範例＞一節中的指示，但選擇 [CancelATask] 作為 [啟始專案]。</span><span class="sxs-lookup"><span data-stu-id="93b2f-153">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span></span> <span data-ttu-id="93b2f-154">將下列變更新增至該專案。</span><span class="sxs-lookup"><span data-stu-id="93b2f-154">Add the following changes to that project.</span></span> <span data-ttu-id="93b2f-155">星號會標記程式中的變更。</span><span class="sxs-lookup"><span data-stu-id="93b2f-155">Asterisks mark the changes in the program.</span></span>  
  
1.  <span data-ttu-id="93b2f-156">新增方法以建立網址清單。</span><span class="sxs-lookup"><span data-stu-id="93b2f-156">Add a method to create a list of web addresses.</span></span>  
  
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
  
2.  <span data-ttu-id="93b2f-157">在 `AccessTheWebAsync` 中呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="93b2f-157">Call the method in `AccessTheWebAsync`.</span></span>  
  
    ```vb  
    ' ***Call SetUpURLList to make a list of web addresses.  
    Dim urlList As List(Of String) = SetUpURLList()  
    ```  
  
3.  <span data-ttu-id="93b2f-158">在 `AccessTheWebAsync` 中新增下列迴圈，以處理清單中的每個網址。</span><span class="sxs-lookup"><span data-stu-id="93b2f-158">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span></span>  
  
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
  
4.  <span data-ttu-id="93b2f-159">因為 `AccessTheWebAsync` 顯示長度，所以此方法不需要傳回任何項目。</span><span class="sxs-lookup"><span data-stu-id="93b2f-159">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span></span> <span data-ttu-id="93b2f-160">請移除 return 陳述式，並將方法的傳回型別變更為 <xref:System.Threading.Tasks.Task>，而非 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="93b2f-160">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
    ```vb  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
    ```  
  
     <span data-ttu-id="93b2f-161">使用陳述式，從 `startButton_Click` 呼叫方法，而不是使用運算式。</span><span class="sxs-lookup"><span data-stu-id="93b2f-161">Call the method from `startButton_Click` by using a statement instead of an expression.</span></span>  
  
    ```vb  
    Await AccessTheWebAsync(cts.Token)  
    ```  
  
5.  <span data-ttu-id="93b2f-162">如果您未取消程式，則會產生下列輸出。</span><span class="sxs-lookup"><span data-stu-id="93b2f-162">If you don’t cancel the program, it produces the following output.</span></span>  
  
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
  
     <span data-ttu-id="93b2f-163">如果您在下載完成之前選擇 [取消] 按鈕，則輸出會包含在取消之前完成之下載的長度。</span><span class="sxs-lookup"><span data-stu-id="93b2f-163">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span></span>  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Downloads canceled.  
    ```  
  
##  <a name="BKMK_CompleteExamples"></a> <span data-ttu-id="93b2f-164">完整範例</span><span class="sxs-lookup"><span data-stu-id="93b2f-164">Complete Examples</span></span>  
 <span data-ttu-id="93b2f-165">下列各節包含每個先前範例的程式碼。</span><span class="sxs-lookup"><span data-stu-id="93b2f-165">The following sections contain the code for each of the previous examples.</span></span> <span data-ttu-id="93b2f-166">請注意，您必須新增 <xref:System.Net.Http> 的參考。</span><span class="sxs-lookup"><span data-stu-id="93b2f-166">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="93b2f-167">您可以從 [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) (非同步範例：微調應用程式) 下載專案。</span><span class="sxs-lookup"><span data-stu-id="93b2f-167">You can download the projects from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
### <a name="cancel-a-task-example"></a><span data-ttu-id="93b2f-168">取消工作範例</span><span class="sxs-lookup"><span data-stu-id="93b2f-168">Cancel a Task Example</span></span>  
 <span data-ttu-id="93b2f-169">下列程式碼是完整的 MainWindow.xaml.vb 檔案，例如取消單一工作。</span><span class="sxs-lookup"><span data-stu-id="93b2f-169">The following code is the complete MainWindow.xaml.vb file for the example that cancels a single task.</span></span>  
  
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
  
### <a name="cancel-a-list-of-tasks-example"></a><span data-ttu-id="93b2f-170">取消工作清單範例</span><span class="sxs-lookup"><span data-stu-id="93b2f-170">Cancel a List of Tasks Example</span></span>  
 <span data-ttu-id="93b2f-171">下列程式碼是完整的 MainWindow.xaml.vb 檔案，如需取消的工作清單的範例。</span><span class="sxs-lookup"><span data-stu-id="93b2f-171">The following code is the complete MainWindow.xaml.vb file for the example that cancels a list of tasks.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="93b2f-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93b2f-172">See Also</span></span>  
 <xref:System.Threading.CancellationTokenSource>  
 <xref:System.Threading.CancellationToken>  
 [<span data-ttu-id="93b2f-173">使用 Async 和 Await 進行非同步程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93b2f-173">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="93b2f-174">微調非同步應用程式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93b2f-174">Fine-Tuning Your Async Application (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [<span data-ttu-id="93b2f-175">非同步範例：微調應用程式 (英文)</span><span class="sxs-lookup"><span data-stu-id="93b2f-175">Async Sample: Fine Tuning Your Application</span></span>](http://go.microsoft.com/fwlink/?LinkId=255046)
