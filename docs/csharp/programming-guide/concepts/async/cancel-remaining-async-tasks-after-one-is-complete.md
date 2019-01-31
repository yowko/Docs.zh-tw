---
title: 當其中一項工作完成時，取消剩餘的非同步工作 (C#)
ms.date: 07/20/2015
ms.assetid: d3cebc74-c392-497b-b1e6-62a262eabe05
ms.openlocfilehash: c4998733fbfe4cdc6730d2433828f5ea996ff6a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529420"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a><span data-ttu-id="3b062-102">當其中一項工作完成時，取消剩餘的非同步工作 (C#)</span><span class="sxs-lookup"><span data-stu-id="3b062-102">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>
<span data-ttu-id="3b062-103">搭配使用 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> 方法與 <xref:System.Threading.CancellationToken>，即可在其中一個工作完成時取消所有剩餘的工作。</span><span class="sxs-lookup"><span data-stu-id="3b062-103">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="3b062-104">`WhenAny` 方法會接受本身為一組工作的引數。</span><span class="sxs-lookup"><span data-stu-id="3b062-104">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="3b062-105">這個方法會啟動所有工作，並傳回單一工作。</span><span class="sxs-lookup"><span data-stu-id="3b062-105">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="3b062-106">集合中的任何工作完成時，單一工作即完成。</span><span class="sxs-lookup"><span data-stu-id="3b062-106">The single task is complete when any task in the collection is complete.</span></span>  
  
 <span data-ttu-id="3b062-107">這個範例示範如何搭配使用取消權杖與 `WhenAny` 以完成這組工作中的第一項工作，並取消其餘工作。</span><span class="sxs-lookup"><span data-stu-id="3b062-107">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="3b062-108">每一項工作都會下載網站的內容。</span><span class="sxs-lookup"><span data-stu-id="3b062-108">Each task downloads the contents of a website.</span></span> <span data-ttu-id="3b062-109">此範例顯示要完成的第一個下載內容的長度，並取消其他下載。</span><span class="sxs-lookup"><span data-stu-id="3b062-109">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b062-110">若要執行範例，您必須在電腦上安裝 Visual Studio 2012 或更新版本以及 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="3b062-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="3b062-111">下載範例</span><span class="sxs-lookup"><span data-stu-id="3b062-111">Downloading the Example</span></span>  
 <span data-ttu-id="3b062-112">您可以從 [Async Sample:Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (非同步範例：微調應用程式) 下載完整 Windows Presentation Foundation (WPF) 專案，然後遵循下列步驟。</span><span class="sxs-lookup"><span data-stu-id="3b062-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="3b062-113">解壓縮您下載的檔案，然後啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="3b062-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="3b062-114">在功能表列上，依序選擇 [檔案] 、[開啟舊檔] 及 [專案/方案] 。</span><span class="sxs-lookup"><span data-stu-id="3b062-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="3b062-115">在 [開啟專案] 對話方塊中，開啟保存已解壓縮之範例程式碼的資料夾，然後開啟 AsyncFineTuningCS 的方案 (.sln) 檔案。</span><span class="sxs-lookup"><span data-stu-id="3b062-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4.  <span data-ttu-id="3b062-116">在方案總管中，開啟 **CancelAfterOneTask** 專案的捷徑功能表，然後選擇 [設定為啟始專案]。</span><span class="sxs-lookup"><span data-stu-id="3b062-116">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="3b062-117">選擇 F5 鍵以執行專案。</span><span class="sxs-lookup"><span data-stu-id="3b062-117">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="3b062-118">選擇 CTRL+F5 鍵以執行專案，而不進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="3b062-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="3b062-119">執行程式數次，確認先完成不同的下載。</span><span class="sxs-lookup"><span data-stu-id="3b062-119">Run the program several times to verify that different downloads finish first.</span></span>  
  
 <span data-ttu-id="3b062-120">如果您不想要下載專案，則可以檢閱本主題結尾的 MainWindow.xaml.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="3b062-120">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="3b062-121">建置範例</span><span class="sxs-lookup"><span data-stu-id="3b062-121">Building the Example</span></span>  
 <span data-ttu-id="3b062-122">本主題中的範例會新增至[取消一項非同步工作或工作清單 (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) 中所開發的專案來取消工作清單。</span><span class="sxs-lookup"><span data-stu-id="3b062-122">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="3b062-123">雖然未明確地使用 [取消] 按鈕，但是此範例會使用相同的 UI。</span><span class="sxs-lookup"><span data-stu-id="3b062-123">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="3b062-124">若要自行逐步建置範例，請遵循＜下載範例＞一節中的指示，但選擇 [CancelAListOfTasks] 作為 [啟始專案]。</span><span class="sxs-lookup"><span data-stu-id="3b062-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="3b062-125">將本主題中的變更新增至該專案。</span><span class="sxs-lookup"><span data-stu-id="3b062-125">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="3b062-126">在 **CancelAListOfTasks** 專案的 MainWindow.xaml.cs 檔案中，將每個網站的處理步驟從 `AccessTheWebAsync` 中的迴圈移至下列非同步方法即可開始轉換。</span><span class="sxs-lookup"><span data-stu-id="3b062-126">In the MainWindow.xaml.cs file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>  
  
```csharp  
/ ***Bundle the processing steps for a website into one async method.  
async Task<int> ProcessURLAsync(string url, HttpClient client, CancellationToken ct)  
{  
    // GetAsync returns a Task<HttpResponseMessage>.   
    HttpResponseMessage response = await client.GetAsync(url, ct);  
  
    // Retrieve the website contents from the HttpResponseMessage.  
    byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
    return urlContents.Length;  
}  
```  
  
 <span data-ttu-id="3b062-127">在 `AccessTheWebAsync` 中，這個範例會使用查詢、<xref:System.Linq.Enumerable.ToArray%2A> 方法和 `WhenAny` 方法來建立並啟動工作陣列。</span><span class="sxs-lookup"><span data-stu-id="3b062-127">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="3b062-128">將 `WhenAny` 套用至陣列，會傳回評估為在工作陣列中完成之第一個工作的等候中單一工作。</span><span class="sxs-lookup"><span data-stu-id="3b062-128">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>  
  
 <span data-ttu-id="3b062-129">在 `AccessTheWebAsync` 中進行下列變更。</span><span class="sxs-lookup"><span data-stu-id="3b062-129">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="3b062-130">星號會標記程式碼檔中的變更。</span><span class="sxs-lookup"><span data-stu-id="3b062-130">Asterisks mark the changes in the code file.</span></span>  
  
1.  <span data-ttu-id="3b062-131">註解化或刪除迴圈。</span><span class="sxs-lookup"><span data-stu-id="3b062-131">Comment out or delete the loop.</span></span>  
  
2.  <span data-ttu-id="3b062-132">建立查詢，而查詢在執行時會產生一組泛型工作。</span><span class="sxs-lookup"><span data-stu-id="3b062-132">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="3b062-133">每個 `ProcessURLAsync` 呼叫都會傳回 `TResult` 為整數的 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="3b062-133">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3.  <span data-ttu-id="3b062-134">呼叫 `ToArray` 來執行查詢，並開始工作。</span><span class="sxs-lookup"><span data-stu-id="3b062-134">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="3b062-135">在下一個步驟中套用 `WhenAny` 方法會執行查詢並啟動工作，而不使用 `ToArray`，但其他方法可能為否。</span><span class="sxs-lookup"><span data-stu-id="3b062-135">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="3b062-136">最安全的做法是明確地強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="3b062-136">The safest practice is to force execution of the query explicitly.</span></span>  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.   
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4.  <span data-ttu-id="3b062-137">對這組工作呼叫 `WhenAny`。</span><span class="sxs-lookup"><span data-stu-id="3b062-137">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="3b062-138">`WhenAny` 會傳回 `Task(Of Task(Of Integer))` 或 `Task<Task<int>>`。</span><span class="sxs-lookup"><span data-stu-id="3b062-138">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="3b062-139">亦即，`WhenAny` 會傳回評估為單一 `Task(Of Integer)` 或 `Task<int>` 的等候中工作。</span><span class="sxs-lookup"><span data-stu-id="3b062-139">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="3b062-140">該單一工作是完成集合中的第一項工作。</span><span class="sxs-lookup"><span data-stu-id="3b062-140">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="3b062-141">先完成的工作會指派給 `firstFinishedTask`。</span><span class="sxs-lookup"><span data-stu-id="3b062-141">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="3b062-142">`firstFinishedTask` 的型別是 `TResult` 為整數的 <xref:System.Threading.Tasks.Task%601>，因為這是 `ProcessURLAsync` 的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="3b062-142">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes   
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5.  <span data-ttu-id="3b062-143">在此範例中，您只想要知道先完成的工作。</span><span class="sxs-lookup"><span data-stu-id="3b062-143">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="3b062-144">因此，請使用 <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> 取消剩餘的工作。</span><span class="sxs-lookup"><span data-stu-id="3b062-144">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6.  <span data-ttu-id="3b062-145">最後，等候 `firstFinishedTask` 擷取所下載內容的長度。</span><span class="sxs-lookup"><span data-stu-id="3b062-145">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
    ```  
  
 <span data-ttu-id="3b062-146">執行程式數次，確認先完成不同的下載。</span><span class="sxs-lookup"><span data-stu-id="3b062-146">Run the program several times to verify that different downloads finish first.</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="3b062-147">完整範例</span><span class="sxs-lookup"><span data-stu-id="3b062-147">Complete Example</span></span>  
 <span data-ttu-id="3b062-148">下列程式碼是範例的完整 MainWindow.xaml.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="3b062-148">The following code is the complete MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="3b062-149">星號會標記已針對此範例新增的項目。</span><span class="sxs-lookup"><span data-stu-id="3b062-149">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="3b062-150">請注意，您必須新增 <xref:System.Net.Http> 的參考。</span><span class="sxs-lookup"><span data-stu-id="3b062-150">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="3b062-151">您可以從 [Async Sample:Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (非同步範例：微調應用程式) 下載專案。</span><span class="sxs-lookup"><span data-stu-id="3b062-151">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
  
// Add the following using directive.  
using System.Threading;  
  
namespace CancelAfterOneTask  
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
                resultsTextBox.Text += "\r\nDownload complete.";  
            }  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownload canceled.";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownload failed.";  
            }  
  
            // Set the CancellationTokenSource to null when the download is complete.  
            cts = null;  
        }  
  
        // You can still include a Cancel button if you want to.  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        // Provide a parameter for the CancellationToken.  
        async Task AccessTheWebAsync(CancellationToken ct)  
        {  
            HttpClient client = new HttpClient();  
  
            // Call SetUpURLList to make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // ***Comment out or delete the loop.  
            //foreach (var url in urlList)  
            //{  
            //    // GetAsync returns a Task<HttpResponseMessage>.   
            //    // Argument ct carries the message if the Cancel button is chosen.   
            //    // ***Note that the Cancel button can cancel all remaining downloads.  
            //    HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            //    // Retrieve the website contents from the HttpResponseMessage.  
            //    byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            //    resultsTextBox.Text +=  
            //        $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            //}  
  
            // ***Create a query that, when executed, returns a collection of tasks.  
            IEnumerable<Task<int>> downloadTasksQuery =  
                from url in urlList select ProcessURLAsync(url, client, ct);  
  
            // ***Use ToArray to execute the query and start the download tasks.   
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
  
            // ***Call WhenAny and then await the result. The task that finishes   
            // first is assigned to firstFinishedTask.  
            Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
  
            // ***Cancel the rest of the downloads. You just want the first one.  
            cts.Cancel();  
  
            // ***Await the first completed task and display the results.   
            // Run the program several times to demonstrate that different  
            // websites can finish first.  
            var length = await firstFinishedTask;  
            resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
        }  
  
        // ***Bundle the processing steps for a website into one async method.  
        async Task<int> ProcessURLAsync(string url, HttpClient client, CancellationToken ct)  
        {  
            // GetAsync returns a Task<HttpResponseMessage>.   
            HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            // Retrieve the website contents from the HttpResponseMessage.  
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            return urlContents.Length;  
        }  
  
        // Add a method that creates a list of web addresses.  
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
    // Sample output:  
  
    // Length of the downloaded website:  158856  
  
    // Download complete.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b062-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b062-152">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="3b062-153">微調非同步應用程式 (C#)</span><span class="sxs-lookup"><span data-stu-id="3b062-153">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [<span data-ttu-id="3b062-154">使用 Async 和 Await 進行非同步程式設計 (C#)</span><span class="sxs-lookup"><span data-stu-id="3b062-154">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="3b062-155">非同步範例：微調您的應用程式</span><span class="sxs-lookup"><span data-stu-id="3b062-155">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
