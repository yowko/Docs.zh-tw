---
title: 當其中一項非同步工作完成時，取消剩餘的非同步工作
ms.date: 07/20/2015
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
ms.openlocfilehash: a0a04c62378ddf70ab3dee9a522e490b0a73b83e
ms.sourcegitcommit: 632818f4b527e5bf3c48fc04e0c7f3b4bdb8a248
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98615954"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a><span data-ttu-id="22768-102">當其中一項工作完成時，取消剩餘的非同步工作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22768-102">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>

<span data-ttu-id="22768-103">搭配使用 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> 方法與 <xref:System.Threading.CancellationToken>，即可在其中一個工作完成時取消所有剩餘的工作。</span><span class="sxs-lookup"><span data-stu-id="22768-103">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="22768-104">`WhenAny` 方法會接受本身為一組工作的引數。</span><span class="sxs-lookup"><span data-stu-id="22768-104">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="22768-105">這個方法會啟動所有工作，並傳回單一工作。</span><span class="sxs-lookup"><span data-stu-id="22768-105">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="22768-106">集合中的任何工作完成時，單一工作即完成。</span><span class="sxs-lookup"><span data-stu-id="22768-106">The single task is complete when any task in the collection is complete.</span></span>

<span data-ttu-id="22768-107">這個範例示範如何搭配使用取消權杖與 `WhenAny` 以完成這組工作中的第一項工作，並取消其餘工作。</span><span class="sxs-lookup"><span data-stu-id="22768-107">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="22768-108">每一項工作都會下載網站的內容。</span><span class="sxs-lookup"><span data-stu-id="22768-108">Each task downloads the contents of a website.</span></span> <span data-ttu-id="22768-109">此範例顯示要完成的第一個下載內容的長度，並取消其他下載。</span><span class="sxs-lookup"><span data-stu-id="22768-109">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>

> [!NOTE]
> <span data-ttu-id="22768-110">若要執行範例，您必須在電腦上安裝 Visual Studio 2012 或更新版本以及 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="22768-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="downloading-the-example"></a><span data-ttu-id="22768-111">下載範例</span><span class="sxs-lookup"><span data-stu-id="22768-111">Downloading the Example</span></span>

<span data-ttu-id="22768-112">您可以從 [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (非同步範例：微調應用程式) 下載完整 Windows Presentation Foundation (WPF) 專案，然後遵循下列步驟。</span><span class="sxs-lookup"><span data-stu-id="22768-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="22768-113">解壓縮您下載的檔案，然後啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="22768-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="22768-114">在功能表列上，依序選擇 [檔案] 、[開啟舊檔] 及 [專案/方案] 。</span><span class="sxs-lookup"><span data-stu-id="22768-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

3. <span data-ttu-id="22768-115">在 [ **開啟專案** ] 對話方塊中，開啟保存您解壓縮之範例程式碼的資料夾，然後開啟 AsyncFineTuningVB 的方案 ( .sln) 檔。</span><span class="sxs-lookup"><span data-stu-id="22768-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>

4. <span data-ttu-id="22768-116">在方案總管中，開啟 **CancelAfterOneTask** 專案的捷徑功能表，然後選擇 [設定為啟始專案]。</span><span class="sxs-lookup"><span data-stu-id="22768-116">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="22768-117">選擇 F5 鍵以執行專案。</span><span class="sxs-lookup"><span data-stu-id="22768-117">Choose the F5 key to run the project.</span></span>

    <span data-ttu-id="22768-118">選擇 CTRL+F5 鍵以執行專案，而不進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="22768-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>

6. <span data-ttu-id="22768-119">執行程式數次，確認先完成不同的下載。</span><span class="sxs-lookup"><span data-stu-id="22768-119">Run the program several times to verify that different downloads finish first.</span></span>

<span data-ttu-id="22768-120">如果您不想要下載專案，可以參閱本主題結尾處的 MainWindow。</span><span class="sxs-lookup"><span data-stu-id="22768-120">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>

## <a name="building-the-example"></a><span data-ttu-id="22768-121">建置範例</span><span class="sxs-lookup"><span data-stu-id="22768-121">Building the Example</span></span>

<span data-ttu-id="22768-122">本主題中的範例會新增至在中開發的專案，以取消非同步工作或取消工作清單 [的工作清單](cancel-an-async-task-or-a-list-of-tasks.md) 。</span><span class="sxs-lookup"><span data-stu-id="22768-122">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks](cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="22768-123">雖然未明確地使用 [取消] 按鈕，但是此範例會使用相同的 UI。</span><span class="sxs-lookup"><span data-stu-id="22768-123">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>

<span data-ttu-id="22768-124">若要自行逐步建置範例，請遵循＜下載範例＞一節中的指示，但選擇 [CancelAListOfTasks] 作為 [啟始專案]。</span><span class="sxs-lookup"><span data-stu-id="22768-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="22768-125">將本主題中的變更新增至該專案。</span><span class="sxs-lookup"><span data-stu-id="22768-125">Add the changes in this topic to that project.</span></span>

<span data-ttu-id="22768-126">在 **>cancelalistoftasks** 專案的 MainWindow 檔案中，將每個網站的處理步驟從迴圈移 `AccessTheWebAsync` 至下列非同步方法，以開始進行轉換。</span><span class="sxs-lookup"><span data-stu-id="22768-126">In the MainWindow.xaml.vb file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>

```vb
' **_Bundle the processing steps for a website into one async method.
Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)

    ' GetAsync returns a Task(Of HttpResponseMessage).
    Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

    ' Retrieve the website contents from the HttpResponseMessage.
    Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

    Return urlContents.Length
End Function
```

<span data-ttu-id="22768-127">在 `AccessTheWebAsync` 中，這個範例會使用查詢、<xref:System.Linq.Enumerable.ToArray%2A> 方法和 `WhenAny` 方法來建立並啟動工作陣列。</span><span class="sxs-lookup"><span data-stu-id="22768-127">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="22768-128">將 `WhenAny` 套用至陣列，會傳回評估為在工作陣列中完成之第一個工作的等候中單一工作。</span><span class="sxs-lookup"><span data-stu-id="22768-128">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>

<span data-ttu-id="22768-129">在 `AccessTheWebAsync` 中進行下列變更。</span><span class="sxs-lookup"><span data-stu-id="22768-129">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="22768-130">星號會標記程式碼檔中的變更。</span><span class="sxs-lookup"><span data-stu-id="22768-130">Asterisks mark the changes in the code file.</span></span>

1. <span data-ttu-id="22768-131">註解化或刪除迴圈。</span><span class="sxs-lookup"><span data-stu-id="22768-131">Comment out or delete the loop.</span></span>

2. <span data-ttu-id="22768-132">建立查詢，而查詢在執行時會產生一組泛型工作。</span><span class="sxs-lookup"><span data-stu-id="22768-132">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="22768-133">每個 `ProcessURLAsync` 呼叫都會傳回 `TResult` 為整數的 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="22768-133">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>

    ```vb
    ' _*_Create a query that, when executed, returns a collection of tasks.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url, client, ct)
    ```

3. <span data-ttu-id="22768-134">呼叫 `ToArray` 來執行查詢，並開始工作。</span><span class="sxs-lookup"><span data-stu-id="22768-134">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="22768-135">在下一個步驟中套用 `WhenAny` 方法會執行查詢並啟動工作，而不使用 `ToArray`，但其他方法可能為否。</span><span class="sxs-lookup"><span data-stu-id="22768-135">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="22768-136">最安全的做法是明確地強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="22768-136">The safest practice is to force execution of the query explicitly.</span></span>

    ```vb
    ' _*_Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. <span data-ttu-id="22768-137">對這組工作呼叫 `WhenAny`。</span><span class="sxs-lookup"><span data-stu-id="22768-137">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="22768-138">`WhenAny` 會傳回 `Task(Of Task(Of Integer))` 或 `Task<Task<int>>`。</span><span class="sxs-lookup"><span data-stu-id="22768-138">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="22768-139">亦即，`WhenAny` 會傳回評估為單一 `Task(Of Integer)` 或 `Task<int>` 的等候中工作。</span><span class="sxs-lookup"><span data-stu-id="22768-139">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="22768-140">該單一工作是完成集合中的第一項工作。</span><span class="sxs-lookup"><span data-stu-id="22768-140">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="22768-141">先完成的工作會指派給 `finishedTask`。</span><span class="sxs-lookup"><span data-stu-id="22768-141">The task that finished first is assigned to `finishedTask`.</span></span> <span data-ttu-id="22768-142">`finishedTask` 的型別是 `TResult` 為整數的 <xref:System.Threading.Tasks.Task%601>，因為這是 `ProcessURLAsync` 的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="22768-142">The type of `finishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>

    ```vb
    ' _*_Call WhenAny and then await the result. The task that finishes
    ' first is assigned to finishedTask.
    Dim finishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)
    ```

5. <span data-ttu-id="22768-143">在此範例中，您只想要知道先完成的工作。</span><span class="sxs-lookup"><span data-stu-id="22768-143">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="22768-144">因此，請使用 <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> 取消剩餘的工作。</span><span class="sxs-lookup"><span data-stu-id="22768-144">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>

    ```vb
    ' _*_Cancel the rest of the downloads. You just want the first one.
    cts.Cancel()
    ```

6. <span data-ttu-id="22768-145">最後，等候 `finishedTask` 擷取所下載內容的長度。</span><span class="sxs-lookup"><span data-stu-id="22768-145">Finally, await `finishedTask` to retrieve the length of the downloaded content.</span></span>

    ```vb
    Dim length = Await finishedTask
    resultsTextBox.Text &= vbCrLf & $"Length of the downloaded website:  {length}" & vbCrLf
    ```

<span data-ttu-id="22768-146">執行程式數次，確認先完成不同的下載。</span><span class="sxs-lookup"><span data-stu-id="22768-146">Run the program several times to verify that different downloads finish first.</span></span>

## <a name="complete-example"></a><span data-ttu-id="22768-147">完整範例</span><span class="sxs-lookup"><span data-stu-id="22768-147">Complete Example</span></span>

<span data-ttu-id="22768-148">下列程式碼是範例的完整 MainWindow 或 MainWindow.xaml.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="22768-148">The following code is the complete MainWindow.xaml.vb or MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="22768-149">星號會標記已針對此範例新增的項目。</span><span class="sxs-lookup"><span data-stu-id="22768-149">Asterisks mark the elements that were added for this example.</span></span>

<span data-ttu-id="22768-150">請注意，您必須新增 <xref:System.Net.Http> 的參考。</span><span class="sxs-lookup"><span data-stu-id="22768-150">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="22768-151">您可以從 [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (非同步範例：微調應用程式) 下載專案。</span><span class="sxs-lookup"><span data-stu-id="22768-151">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

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
        ''        vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
        ''Next

        ' _*_Create a query that, when executed, returns a collection of tasks.
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
            From url In urlList Select ProcessURLAsync(url, client, ct)

        ' _*_Use ToArray to execute the query and start the download tasks.
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()

        ' _*_Call WhenAny and then await the result. The task that finishes
        ' first is assigned to finishedTask.
        Dim finishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)

        ' _*_Cancel the rest of the downloads. You just want the first one.
        cts.Cancel()

        ' _*_Await the first completed task and display the results
        ' Run the program several times to demonstrate that different
        ' websites can finish first.
        Dim length = Await finishedTask
        resultsTextBox.Text &= vbCrLf & $"Length of the downloaded website:  {length}" & vbCrLf
    End Function

    ' _**Bundle the processing steps for a website into one async method.
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

## <a name="see-also"></a><span data-ttu-id="22768-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22768-152">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="22768-153">微調非同步應用程式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22768-153">Fine-Tuning Your Async Application (Visual Basic)</span></span>](fine-tuning-your-async-application.md)
- [<span data-ttu-id="22768-154">使用 Async 和 Await 進行非同步程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22768-154">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- <span data-ttu-id="22768-155">[Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (非同步範例：微調應用程式)</span><span class="sxs-lookup"><span data-stu-id="22768-155">[Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)</span></span>
