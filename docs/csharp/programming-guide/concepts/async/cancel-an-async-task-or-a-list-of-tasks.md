---
title: 取消一項非同步工作或工作清單 (C#)
ms.date: 07/20/2015
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 93526f772f79e993767fd8f29087b6caf4e29468
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595715"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-c"></a><span data-ttu-id="1822f-102">取消一項非同步工作或工作清單 (C#)</span><span class="sxs-lookup"><span data-stu-id="1822f-102">Cancel an async task or a list of tasks (C#)</span></span>

<span data-ttu-id="1822f-103">如果您不想要等候非同步應用程式完成，則可以設定可用來取消非同步應用程式的按鈕。</span><span class="sxs-lookup"><span data-stu-id="1822f-103">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="1822f-104">遵循本主題中的範例，即可將取消按鈕新增至下載某個網站內容或網站清單的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1822f-104">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span></span>

<span data-ttu-id="1822f-105">這些範例會使用[微調非同步應用程式 (C#)](./fine-tuning-your-async-application.md) 所描述的 UI。</span><span class="sxs-lookup"><span data-stu-id="1822f-105">The examples use the UI that [Fine-Tuning Your Async Application (C#)](./fine-tuning-your-async-application.md) describes.</span></span>

> [!NOTE]
> <span data-ttu-id="1822f-106">若要執行範例，您必須在電腦上安裝 Visual Studio 2012 或更新版本以及 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="1822f-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="cancel-a-task"></a><span data-ttu-id="1822f-107">取消工作</span><span class="sxs-lookup"><span data-stu-id="1822f-107">Cancel a task</span></span>

<span data-ttu-id="1822f-108">第一個範例會建立 [取消]  按鈕與單一下載工作的關聯。</span><span class="sxs-lookup"><span data-stu-id="1822f-108">The first example associates the **Cancel** button with a single download task.</span></span> <span data-ttu-id="1822f-109">如果您在應用程式下載內容時選擇該按鈕，則會取消下載。</span><span class="sxs-lookup"><span data-stu-id="1822f-109">If you choose the button while the application is downloading content, the download is canceled.</span></span>

### <a name="download-the-example"></a><span data-ttu-id="1822f-110">下載範例</span><span class="sxs-lookup"><span data-stu-id="1822f-110">Download the example</span></span>

<span data-ttu-id="1822f-111">您可以從 [Async Sample:Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (非同步範例：微調應用程式) 下載完整 Windows Presentation Foundation (WPF) 專案，然後遵循下列步驟。</span><span class="sxs-lookup"><span data-stu-id="1822f-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="1822f-112">解壓縮您下載的檔案，然後啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="1822f-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="1822f-113">在功能表列上選擇 [檔案]   >  [開啟]   > [專案/解決方案]  。</span><span class="sxs-lookup"><span data-stu-id="1822f-113">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="1822f-114">在 [開啟專案]  對話方塊中，開啟保存已解壓縮之範例程式碼的資料夾，然後開啟 AsyncFineTuningCS 的方案 (.sln) 檔案。</span><span class="sxs-lookup"><span data-stu-id="1822f-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="1822f-115">在方案總管  中，開啟 **CancelATask** 專案的捷徑功能表，然後選擇 [設定為啟始專案]  。</span><span class="sxs-lookup"><span data-stu-id="1822f-115">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="1822f-116">選擇 **F5** 鍵以執行專案 (或按 **Ctrl** + **F5** 以執行專案但不進行偵錯)。</span><span class="sxs-lookup"><span data-stu-id="1822f-116">Choose the **F5** key to run the project (or, press **Ctrl**+**F5** to run the project without debugging it).</span></span>

> [!TIP]
> <span data-ttu-id="1822f-117">如果您不想要下載專案，則可以檢閱本主題結尾的 MainWindow.xaml.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="1822f-117">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>

### <a name="build-the-example"></a><span data-ttu-id="1822f-118">建置範例</span><span class="sxs-lookup"><span data-stu-id="1822f-118">Build the example</span></span>
 <span data-ttu-id="1822f-119">下列變更會將 [取消]  按鈕新增至下載網站的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1822f-119">The following changes add a **Cancel** button to an application that downloads a website.</span></span> <span data-ttu-id="1822f-120">如果您不想要下載或建置範例，則可以檢閱本主題結尾處的＜完整範例＞一節中的最終產品。</span><span class="sxs-lookup"><span data-stu-id="1822f-120">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span></span> <span data-ttu-id="1822f-121">星號會標記程式碼中的變更。</span><span class="sxs-lookup"><span data-stu-id="1822f-121">Asterisks mark the changes in the code.</span></span>

 <span data-ttu-id="1822f-122">若要自行逐步建置範例，請遵循＜下載範例＞一節中的指示，但選擇 [StarterCode]  作為 [啟始專案]  ，而非 [CancelATask]  。</span><span class="sxs-lookup"><span data-stu-id="1822f-122">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span></span>

 <span data-ttu-id="1822f-123">然後將下列變更新增至該專案的 MainWindow.xaml.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="1822f-123">Then add the following changes to the MainWindow.xaml.cs file of that project.</span></span>

1. <span data-ttu-id="1822f-124">宣告 `CancellationTokenSource` 變數 `cts`，這是在存取它之所有方法的範圍內。</span><span class="sxs-lookup"><span data-stu-id="1822f-124">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span></span>

    ```csharp
    public partial class MainWindow : Window
    {
        // ***Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. <span data-ttu-id="1822f-125">針對 [取消]  按鈕新增下列事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1822f-125">Add the following event handler for the **Cancel** button.</span></span> <span data-ttu-id="1822f-126">事件處理常式會使用 <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> 方法，以在使用者要求取消時通知 `cts`。</span><span class="sxs-lookup"><span data-stu-id="1822f-126">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> method to notify `cts` when the user requests cancellation.</span></span>

    ```csharp
    // ***Add an event handler for the Cancel button.
    private void cancelButton_Click(object sender, RoutedEventArgs e)
    {
        if (cts != null)
        {
            cts.Cancel();
        }
    }
    ```

3. <span data-ttu-id="1822f-127">在 [開始]  按鈕 `startButton_Click` 的事件處理常式中進行下列變更。</span><span class="sxs-lookup"><span data-stu-id="1822f-127">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span></span>

    - <span data-ttu-id="1822f-128">具現化 `CancellationTokenSource`、`cts`。</span><span class="sxs-lookup"><span data-stu-id="1822f-128">Instantiate the `CancellationTokenSource`, `cts`.</span></span>

        ```csharp
        // ***Instantiate the CancellationTokenSource.
        cts = new CancellationTokenSource();
        ```

    - <span data-ttu-id="1822f-129">在下載所指定網站內容的 `AccessTheWebAsync` 呼叫中，傳送 `cts` 的 <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> 屬性作為引數。</span><span class="sxs-lookup"><span data-stu-id="1822f-129">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> property of `cts` as an argument.</span></span> <span data-ttu-id="1822f-130">如果要求取消，則 `Token` 屬性會傳播訊息。</span><span class="sxs-lookup"><span data-stu-id="1822f-130">The `Token` property propagates the message if cancellation is requested.</span></span> <span data-ttu-id="1822f-131">新增 catch 區塊，以在使用者選擇取消下載作業時顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="1822f-131">Add a catch block that displays a message if the user chooses to cancel the download operation.</span></span> <span data-ttu-id="1822f-132">下列程式碼示範這些變更。</span><span class="sxs-lookup"><span data-stu-id="1822f-132">The following code shows the changes.</span></span>

        ```csharp
        try
        {
            // ***Send a token to carry the message if cancellation is requested.
            int contentLength = await AccessTheWebAsync(cts.Token);
            resultsTextBox.Text += $"\r\nLength of the downloaded string: {contentLength}.\r\n";
        }
        // *** If cancellation is requested, an OperationCanceledException results.
        catch (OperationCanceledException)
        {
            resultsTextBox.Text += "\r\nDownload canceled.\r\n";
        }
        catch (Exception)
        {
            resultsTextBox.Text += "\r\nDownload failed.\r\n";
        }
        ```

4. <span data-ttu-id="1822f-133">在 `AccessTheWebAsync` 中，使用 <xref:System.Net.Http.HttpClient> 型別中 `GetAsync` 方法的 <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> 多載來下載網站的內容。</span><span class="sxs-lookup"><span data-stu-id="1822f-133">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span></span> <span data-ttu-id="1822f-134">將 `ct` (`AccessTheWebAsync` 的 <xref:System.Threading.CancellationToken> 參數) 傳遞為第二個引數。</span><span class="sxs-lookup"><span data-stu-id="1822f-134">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span></span> <span data-ttu-id="1822f-135">如果使用者選擇 [取消]  按鈕，則權杖會夾帶訊息。</span><span class="sxs-lookup"><span data-stu-id="1822f-135">The token carries the message if the user chooses the **Cancel** button.</span></span>

     <span data-ttu-id="1822f-136">下列程式碼示範 `AccessTheWebAsync` 中的變更。</span><span class="sxs-lookup"><span data-stu-id="1822f-136">The following code shows the changes in `AccessTheWebAsync`.</span></span>

    ```csharp
    // ***Provide a parameter for the CancellationToken.
    async Task<int> AccessTheWebAsync(CancellationToken ct)
    {
        HttpClient client = new HttpClient();

        resultsTextBox.Text += "\r\nReady to download.\r\n";

        // You might need to slow things down to have a chance to cancel.
        await Task.Delay(250);

        // GetAsync returns a Task<HttpResponseMessage>.
        // ***The ct argument carries the message if the Cancel button is chosen.
        HttpResponseMessage response = await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct);

        // Retrieve the website contents from the HttpResponseMessage.
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

        // The result of the method is the length of the downloaded website.
        return urlContents.Length;
    }
    ```

5. <span data-ttu-id="1822f-137">如果您未取消程式，則會產生下列輸出。</span><span class="sxs-lookup"><span data-stu-id="1822f-137">If you don’t cancel the program, it produces the following output.</span></span>

    ```text
    Ready to download.
    Length of the downloaded string: 158125.
    ```

     <span data-ttu-id="1822f-138">如果您在程式完成下載內容之前選擇 [取消]  按鈕，程式會產生下列輸出。</span><span class="sxs-lookup"><span data-stu-id="1822f-138">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output.</span></span>

    ```text
    Ready to download.
    Download canceled.
    ```

## <a name="cancel-a-list-of-tasks"></a><span data-ttu-id="1822f-139">取消工作清單</span><span class="sxs-lookup"><span data-stu-id="1822f-139">Cancel a list of tasks</span></span>

<span data-ttu-id="1822f-140">您可以將相同 `CancellationTokenSource` 執行個體與每項工作建立關聯，以擴充先前的範例來取消許多工作。</span><span class="sxs-lookup"><span data-stu-id="1822f-140">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span></span> <span data-ttu-id="1822f-141">如果您選擇 [取消]  按鈕，即會取消所有尚未完成的工作。</span><span class="sxs-lookup"><span data-stu-id="1822f-141">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span></span>

### <a name="download-the-example"></a><span data-ttu-id="1822f-142">下載範例</span><span class="sxs-lookup"><span data-stu-id="1822f-142">Download the example</span></span>

<span data-ttu-id="1822f-143">您可以從 [Async Sample:Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (非同步範例：微調應用程式) 下載完整 Windows Presentation Foundation (WPF) 專案，然後遵循下列步驟。</span><span class="sxs-lookup"><span data-stu-id="1822f-143">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="1822f-144">解壓縮您下載的檔案，然後啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="1822f-144">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="1822f-145">在功能表列上選擇 [檔案]   >  [開啟]   > [專案/解決方案]  。</span><span class="sxs-lookup"><span data-stu-id="1822f-145">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="1822f-146">在 [開啟專案]  對話方塊中，開啟保存已解壓縮之範例程式碼的資料夾，然後開啟 AsyncFineTuningCS 的方案 (.sln) 檔案。</span><span class="sxs-lookup"><span data-stu-id="1822f-146">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="1822f-147">在方案總管  中，開啟 **CancelAListOfTasks** 專案的捷徑功能表，然後選擇 [設定為啟始專案]  。</span><span class="sxs-lookup"><span data-stu-id="1822f-147">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="1822f-148">選擇 **F5** 鍵以執行專案。</span><span class="sxs-lookup"><span data-stu-id="1822f-148">Choose the **F5** key to run the project.</span></span>

     <span data-ttu-id="1822f-149">選擇 **Ctrl** + **F5** 鍵以執行專案，而不進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="1822f-149">Choose the **Ctrl**+**F5** keys to run the project without debugging it.</span></span>

<span data-ttu-id="1822f-150">如果您不想要下載專案，則可以檢閱本主題結尾的 MainWindow.xaml.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="1822f-150">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>

### <a name="build-the-example"></a><span data-ttu-id="1822f-151">建置範例</span><span class="sxs-lookup"><span data-stu-id="1822f-151">Build the example</span></span>

<span data-ttu-id="1822f-152">若要自行逐步擴充範例，請遵循＜下載範例＞一節中的指示，但選擇 [CancelATask]  作為 [啟始專案]  。</span><span class="sxs-lookup"><span data-stu-id="1822f-152">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span></span> <span data-ttu-id="1822f-153">將下列變更新增至該專案。</span><span class="sxs-lookup"><span data-stu-id="1822f-153">Add the following changes to that project.</span></span> <span data-ttu-id="1822f-154">星號會標記程式中的變更。</span><span class="sxs-lookup"><span data-stu-id="1822f-154">Asterisks mark the changes in the program.</span></span>

1. <span data-ttu-id="1822f-155">新增方法以建立網址清單。</span><span class="sxs-lookup"><span data-stu-id="1822f-155">Add a method to create a list of web addresses.</span></span>

    ```csharp
    // ***Add a method that creates a list of web addresses.
    private List<string> SetUpURLList()
    {
        List<string> urls = new List<string>
        {
            "https://msdn.microsoft.com",
            "https://msdn.microsoft.com/library/hh290138.aspx",
            "https://msdn.microsoft.com/library/hh290140.aspx",
            "https://msdn.microsoft.com/library/dd470362.aspx",
            "https://msdn.microsoft.com/library/aa578028.aspx",
            "https://msdn.microsoft.com/library/ms404677.aspx",
            "https://msdn.microsoft.com/library/ff730837.aspx"
        };
        return urls;
    }
    ```

2. <span data-ttu-id="1822f-156">在 `AccessTheWebAsync` 中呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="1822f-156">Call the method in `AccessTheWebAsync`.</span></span>

    ```csharp
    // ***Call SetUpURLList to make a list of web addresses.
    List<string> urlList = SetUpURLList();
    ```

3. <span data-ttu-id="1822f-157">在 `AccessTheWebAsync` 中新增下列迴圈，以處理清單中的每個網址。</span><span class="sxs-lookup"><span data-stu-id="1822f-157">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span></span>

    ```csharp
    // ***Add a loop to process the list of web addresses.
    foreach (var url in urlList)
    {
        // GetAsync returns a Task<HttpResponseMessage>.
        // Argument ct carries the message if the Cancel button is chosen.
        // ***Note that the Cancel button can cancel all remaining downloads.
        HttpResponseMessage response = await client.GetAsync(url, ct);

        // Retrieve the website contents from the HttpResponseMessage.
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

        resultsTextBox.Text +=
            $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
    }
    ```

4. <span data-ttu-id="1822f-158">因為 `AccessTheWebAsync` 顯示長度，所以此方法不需要傳回任何項目。</span><span class="sxs-lookup"><span data-stu-id="1822f-158">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span></span> <span data-ttu-id="1822f-159">請移除 return 陳述式，並將方法的傳回型別變更為 <xref:System.Threading.Tasks.Task>，而非 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="1822f-159">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span></span>

    ```csharp
    async Task AccessTheWebAsync(CancellationToken ct)
    ```

     <span data-ttu-id="1822f-160">使用陳述式，從 `startButton_Click` 呼叫方法，而不是使用運算式。</span><span class="sxs-lookup"><span data-stu-id="1822f-160">Call the method from `startButton_Click` by using a statement instead of an expression.</span></span>

    ```csharp
    await AccessTheWebAsync(cts.Token);
    ```

5. <span data-ttu-id="1822f-161">如果您未取消程式，則會產生下列輸出。</span><span class="sxs-lookup"><span data-stu-id="1822f-161">If you don’t cancel the program, it produces the following output.</span></span>

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Length of the downloaded string: 158124.

    Length of the downloaded string: 204890.

    Length of the downloaded string: 175488.

    Length of the downloaded string: 145790.

    Downloads complete.
    ```

     <span data-ttu-id="1822f-162">如果您在下載完成之前選擇 [取消]  按鈕，則輸出會包含在取消之前完成之下載的長度。</span><span class="sxs-lookup"><span data-stu-id="1822f-162">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span></span>

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Downloads canceled.
    ```

## <a name="complete-examples"></a><span data-ttu-id="1822f-163">完整範例</span><span class="sxs-lookup"><span data-stu-id="1822f-163">Complete examples</span></span>

<span data-ttu-id="1822f-164">下列各節包含每個先前範例的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1822f-164">The following sections contain the code for each of the previous examples.</span></span> <span data-ttu-id="1822f-165">請注意，您必須新增 <xref:System.Net.Http> 的參考。</span><span class="sxs-lookup"><span data-stu-id="1822f-165">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="1822f-166">您可以從 [Async Sample:Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (非同步範例：微調應用程式) 下載專案。</span><span class="sxs-lookup"><span data-stu-id="1822f-166">You can download the projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

### <a name="example---cancel-a-task"></a><span data-ttu-id="1822f-167">範例 - 取消工作</span><span class="sxs-lookup"><span data-stu-id="1822f-167">Example - Cancel a task</span></span>

<span data-ttu-id="1822f-168">下列程式碼是取消單一工作之範例的完整 MainWindow.xaml.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="1822f-168">The following code is the complete MainWindow.xaml.cs file for the example that cancels a single task.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;

// Add a using directive and a reference for System.Net.Http.
using System.Net.Http;

// Add the following using directive for System.Threading.

using System.Threading;
namespace CancelATask
{
    public partial class MainWindow : Window
    {
        // ***Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;

        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // ***Instantiate the CancellationTokenSource.
            cts = new CancellationTokenSource();

            resultsTextBox.Clear();

            try
            {
                // ***Send a token to carry the message if cancellation is requested.
                int contentLength = await AccessTheWebAsync(cts.Token);
                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {contentLength}.\r\n";
            }
            // *** If cancellation is requested, an OperationCanceledException results.
            catch (OperationCanceledException)
            {
                resultsTextBox.Text += "\r\nDownload canceled.\r\n";
            }
            catch (Exception)
            {
                resultsTextBox.Text += "\r\nDownload failed.\r\n";
            }

            // ***Set the CancellationTokenSource to null when the download is complete.
            cts = null;
        }

        // ***Add an event handler for the Cancel button.
        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        // ***Provide a parameter for the CancellationToken.
        async Task<int> AccessTheWebAsync(CancellationToken ct)
        {
            HttpClient client = new HttpClient();

            resultsTextBox.Text += "\r\nReady to download.\r\n";

            // You might need to slow things down to have a chance to cancel.
            await Task.Delay(250);

            // GetAsync returns a Task<HttpResponseMessage>.
            // ***The ct argument carries the message if the Cancel button is chosen.
            HttpResponseMessage response = await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct);

            // Retrieve the website contents from the HttpResponseMessage.
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

            // The result of the method is the length of the downloaded website.
            return urlContents.Length;
        }
    }

    // Output for a successful download:

    // Ready to download.

    // Length of the downloaded string: 158125.

    // Or, if you cancel:

    // Ready to download.

    // Download canceled.
}
```

### <a name="example---cancel-a-list-of-tasks"></a><span data-ttu-id="1822f-169">範例 - 取消工作清單</span><span class="sxs-lookup"><span data-stu-id="1822f-169">Example - Cancel a list of tasks</span></span>

<span data-ttu-id="1822f-170">下列程式碼是取消工作清單之範例的完整 MainWindow.xaml.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="1822f-170">The following code is the complete MainWindow.xaml.cs file for the example that cancels a list of tasks.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;

// Add a using directive and a reference for System.Net.Http.
using System.Net.Http;

// Add the following using directive for System.Threading.
using System.Threading;

namespace CancelAListOfTasks
{
    public partial class MainWindow : Window
    {
        // Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;

        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // Instantiate the CancellationTokenSource.
            cts = new CancellationTokenSource();

            resultsTextBox.Clear();

            try
            {
                await AccessTheWebAsync(cts.Token);
                // ***Small change in the display lines.
                resultsTextBox.Text += "\r\nDownloads complete.";
            }
            catch (OperationCanceledException)
            {
                resultsTextBox.Text += "\r\nDownloads canceled.";
            }
            catch (Exception)
            {
                resultsTextBox.Text += "\r\nDownloads failed.";
            }

            // Set the CancellationTokenSource to null when the download is complete.
            cts = null;
        }

        // Add an event handler for the Cancel button.
        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        // Provide a parameter for the CancellationToken.
        // ***Change the return type to Task because the method has no return statement.
        async Task AccessTheWebAsync(CancellationToken ct)
        {
            // Declare an HttpClient object.
            HttpClient client = new HttpClient();

            // ***Call SetUpURLList to make a list of web addresses.
            List<string> urlList = SetUpURLList();

            // ***Add a loop to process the list of web addresses.
            foreach (var url in urlList)
            {
                // GetAsync returns a Task<HttpResponseMessage>.
                // Argument ct carries the message if the Cancel button is chosen.
                // ***Note that the Cancel button can cancel all remaining downloads.
                HttpResponseMessage response = await client.GetAsync(url, ct);

                // Retrieve the website contents from the HttpResponseMessage.
                byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            }
        }

        // ***Add a method that creates a list of web addresses.
        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }
    }

    // Output if you do not choose to cancel:

    //Length of the downloaded string: 35939.

    //Length of the downloaded string: 237682.

    //Length of the downloaded string: 128607.

    //Length of the downloaded string: 158124.

    //Length of the downloaded string: 204890.

    //Length of the downloaded string: 175488.

    //Length of the downloaded string: 145790.

    //Downloads complete.

    // Sample output if you choose to cancel:

    //Length of the downloaded string: 35939.

    //Length of the downloaded string: 237682.

    //Length of the downloaded string: 128607.

    //Downloads canceled.
}
```

## <a name="see-also"></a><span data-ttu-id="1822f-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1822f-171">See also</span></span>

- <xref:System.Threading.CancellationTokenSource>
- <xref:System.Threading.CancellationToken>
- [<span data-ttu-id="1822f-172">使用 Async 和 Await 進行非同步程式設計 (C#)</span><span class="sxs-lookup"><span data-stu-id="1822f-172">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="1822f-173">微調非同步應用程式 (C#)</span><span class="sxs-lookup"><span data-stu-id="1822f-173">Fine-Tuning Your Async Application (C#)</span></span>](./fine-tuning-your-async-application.md)
- [<span data-ttu-id="1822f-174">非同步範例：微調您的應用程式</span><span class="sxs-lookup"><span data-stu-id="1822f-174">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
