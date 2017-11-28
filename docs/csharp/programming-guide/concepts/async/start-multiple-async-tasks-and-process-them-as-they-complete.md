---
title: "啟動多項非同步工作並在它們完成時進行處理 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bf70bd5e79e962d8edaea2dc037f191707f4e047
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a><span data-ttu-id="a4335-102">啟動多項非同步工作並在它們完成時進行處理 (C#)</span><span class="sxs-lookup"><span data-stu-id="a4335-102">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>
<span data-ttu-id="a4335-103">使用 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>，即可同時啟動多個工作，並在完成時逐一進行處理，而不是依啟動順序進行處理。</span><span class="sxs-lookup"><span data-stu-id="a4335-103">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, you can start multiple tasks at the same time and process them one by one as they’re completed rather than process them in the order in which they're started.</span></span>  
  
 <span data-ttu-id="a4335-104">下列範例使用查詢來建立工作集合。</span><span class="sxs-lookup"><span data-stu-id="a4335-104">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="a4335-105">每項工作都會下載所指定網站的內容。</span><span class="sxs-lookup"><span data-stu-id="a4335-105">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="a4335-106">在 while 迴圈的的每個反覆運算中，等候的 `WhenAny` 呼叫會先傳回完成其下載的工作集合中的工作。</span><span class="sxs-lookup"><span data-stu-id="a4335-106">In each iteration of a while loop, an awaited call to `WhenAny` returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="a4335-107">該工作會從集合中予以移除，並進行處理。</span><span class="sxs-lookup"><span data-stu-id="a4335-107">That task is removed from the collection and processed.</span></span> <span data-ttu-id="a4335-108">迴圈會重複進行，直到集合未包含其他工作為止。</span><span class="sxs-lookup"><span data-stu-id="a4335-108">The loop repeats until the collection contains no more tasks.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4335-109">若要執行範例，您必須在電腦上安裝 Visual Studio 2012 或更新版本以及 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="a4335-109">To run the examples, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="a4335-110">下載範例</span><span class="sxs-lookup"><span data-stu-id="a4335-110">Downloading the Example</span></span>  
 <span data-ttu-id="a4335-111">您可以從 [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) (非同步範例：微調應用程式) 下載完整 Windows Presentation Foundation (WPF) 專案，然後遵循下列步驟。</span><span class="sxs-lookup"><span data-stu-id="a4335-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="a4335-112">解壓縮您下載的檔案，然後啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="a4335-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="a4335-113">在功能表列上，依序選擇 [檔案] 、[開啟舊檔] 及 [專案/方案] 。</span><span class="sxs-lookup"><span data-stu-id="a4335-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="a4335-114">在 [開啟專案] 對話方塊中，開啟保存已解壓縮之範例程式碼的資料夾，然後開啟 AsyncFineTuningCS 的方案 (.sln) 檔案。</span><span class="sxs-lookup"><span data-stu-id="a4335-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4.  <span data-ttu-id="a4335-115">在方案總管中，開啟 **ProcessTasksAsTheyFinish** 專案的捷徑功能表，然後選擇 [設定為啟始專案]。</span><span class="sxs-lookup"><span data-stu-id="a4335-115">In **Solution Explorer**, open the shortcut menu for the **ProcessTasksAsTheyFinish** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="a4335-116">選擇 F5 鍵以執行專案。</span><span class="sxs-lookup"><span data-stu-id="a4335-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="a4335-117">選擇 CTRL+F5 鍵以執行專案，而不進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="a4335-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="a4335-118">執行專案數次，確認所下載的長度不一定會以相同的順序出現。</span><span class="sxs-lookup"><span data-stu-id="a4335-118">Run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
 <span data-ttu-id="a4335-119">如果您不想要下載專案，則可以檢閱本主題結尾的 MainWindow.xaml.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="a4335-119">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="a4335-120">建置範例</span><span class="sxs-lookup"><span data-stu-id="a4335-120">Building the Example</span></span>  
 <span data-ttu-id="a4335-121">這個範例會新增至在[當其中一項工作完成時，取消剩餘的非同步工作 (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)[當其中一項工作完成時，取消剩餘的非同步工作](http://msdn.microsoft.com/library/8e800b58-235a-44b7-a02c-fa4375591d76)中開發的程式碼，並使用相同的 UI。</span><span class="sxs-lookup"><span data-stu-id="a4335-121">This example adds to the code that’s developed in [Cancel Remaining Async Tasks after One Is Complete (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)[Cancel Remaining Async Tasks after One Is Complete](http://msdn.microsoft.com/library/8e800b58-235a-44b7-a02c-fa4375591d76) and uses the same UI.</span></span>  
  
 <span data-ttu-id="a4335-122">若要自行逐步建置範例，請遵循＜下載範例＞一節中的指示，但選擇 [CancelAfterOneTask] 作為 [啟始專案]。</span><span class="sxs-lookup"><span data-stu-id="a4335-122">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAfterOneTask** as the **StartUp Project**.</span></span> <span data-ttu-id="a4335-123">將本主題中的變更新增至該專案中的 `AccessTheWebAsync` 方法。</span><span class="sxs-lookup"><span data-stu-id="a4335-123">Add the changes in this topic to the `AccessTheWebAsync` method in that project.</span></span> <span data-ttu-id="a4335-124">變更會標上星號。</span><span class="sxs-lookup"><span data-stu-id="a4335-124">The changes are marked with asterisks.</span></span>  
  
 <span data-ttu-id="a4335-125">**CancelAfterOneTask** 專案已經包含一個查詢，這個查詢在執行時，會建立一組工作。</span><span class="sxs-lookup"><span data-stu-id="a4335-125">The **CancelAfterOneTask** project already includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="a4335-126">下列程式碼中的每個 `ProcessURLAsync` 呼叫都會傳回 `TResult` 為整數的 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="a4335-126">Each call to `ProcessURLAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
```csharp  
IEnumerable<Task<int>> downloadTasksQuery =  
    from url in urlList select ProcessURL(url, client, ct);  
```  
  
 <span data-ttu-id="a4335-127">在專案的 MainWindow.xaml.cs 檔案中，對 `AccessTheWebAsync` 方法進行下列變更。</span><span class="sxs-lookup"><span data-stu-id="a4335-127">In the MainWindow.xaml.cs file of the  project, make the following changes to the `AccessTheWebAsync` method.</span></span>  
  
-   <span data-ttu-id="a4335-128">套用 <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 來執行查詢，而非 <xref:System.Linq.Enumerable.ToArray%2A>。</span><span class="sxs-lookup"><span data-stu-id="a4335-128">Execute the query by applying <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> instead of <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
    ```csharp  
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();  
    ```  
  
-   <span data-ttu-id="a4335-129">新增 while 迴圈，以對集合中的每個工作執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="a4335-129">Add a while loop that performs the following steps for each task in the collection.</span></span>  
  
    1.  <span data-ttu-id="a4335-130">等候 `WhenAny` 呼叫，識別集合中的第一個工作以完成其下載。</span><span class="sxs-lookup"><span data-stu-id="a4335-130">Awaits a call to `WhenAny` to identify the first task in the collection to finish its download.</span></span>  
  
        ```csharp  
        Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
        ```  
  
    2.  <span data-ttu-id="a4335-131">從集合中移除該工作。</span><span class="sxs-lookup"><span data-stu-id="a4335-131">Removes that task from the collection.</span></span>  
  
        ```csharp  
        downloadTasks.Remove(firstFinishedTask);  
        ```  
  
    3.  <span data-ttu-id="a4335-132">等候 `ProcessURLAsync` 呼叫所傳回的 `firstFinishedTask`。</span><span class="sxs-lookup"><span data-stu-id="a4335-132">Awaits `firstFinishedTask`, which is returned by a call to `ProcessURLAsync`.</span></span> <span data-ttu-id="a4335-133">`firstFinishedTask` 變數是 <xref:System.Threading.Tasks.Task%601>，其中 `TReturn` 是整數。</span><span class="sxs-lookup"><span data-stu-id="a4335-133">The `firstFinishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TReturn` is an integer.</span></span> <span data-ttu-id="a4335-134">工作已完成，但您等候它擷取所下載網站的長度，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a4335-134">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span>  
  
        ```csharp  
        int length = await firstFinishedTask;  
        resultsTextBox.Text += String.Format("\r\nLength of the download:  {0}", length);  
        ```  
  
 <span data-ttu-id="a4335-135">您應該執行專案數次，確認所下載的長度不一定會以相同的順序出現。</span><span class="sxs-lookup"><span data-stu-id="a4335-135">You should run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="a4335-136">您可以如這個範例所述在迴圈中使用 `WhenAny`，以解決牽涉到少量工作的問題。</span><span class="sxs-lookup"><span data-stu-id="a4335-136">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="a4335-137">不過，如果您有大量的工作要處理，其他方法會更有效率。</span><span class="sxs-lookup"><span data-stu-id="a4335-137">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="a4335-138">如需詳細資訊和範例，請參閱[Processing Tasks as they complete](http://go.microsoft.com/fwlink/?LinkId=260810)(在工作完成時加以處理)。</span><span class="sxs-lookup"><span data-stu-id="a4335-138">For more information and examples, see [Processing Tasks as they complete](http://go.microsoft.com/fwlink/?LinkId=260810).</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="a4335-139">完整範例</span><span class="sxs-lookup"><span data-stu-id="a4335-139">Complete Example</span></span>  
 <span data-ttu-id="a4335-140">下列程式碼是範例的 MainWindow.xaml.cs 檔案的完整文字。</span><span class="sxs-lookup"><span data-stu-id="a4335-140">The following code is the complete text of the MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="a4335-141">星號會標記已針對此範例新增的項目。</span><span class="sxs-lookup"><span data-stu-id="a4335-141">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="a4335-142">請注意，您必須新增 <xref:System.Net.Http> 的參考。</span><span class="sxs-lookup"><span data-stu-id="a4335-142">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="a4335-143">您可以從 [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) (非同步範例：微調應用程式) 下載專案。</span><span class="sxs-lookup"><span data-stu-id="a4335-143">You can download the project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
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
  
namespace ProcessTasksAsTheyFinish  
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
            resultsTextBox.Clear();  
  
            // Instantiate the CancellationTokenSource.  
            cts = new CancellationTokenSource();  
  
            try  
            {  
                await AccessTheWebAsync(cts.Token);  
                resultsTextBox.Text += "\r\nDownloads complete.";  
            }  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownloads canceled.\r\n";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownloads failed.\r\n";  
            }  
  
            cts = null;  
        }  
  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        async Task AccessTheWebAsync(CancellationToken ct)  
        {  
            HttpClient client = new HttpClient();  
  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // ***Create a query that, when executed, returns a collection of tasks.  
            IEnumerable<Task<int>> downloadTasksQuery =  
                from url in urlList select ProcessURL(url, client, ct);  
  
            // ***Use ToList to execute the query and start the tasks.   
            List<Task<int>> downloadTasks = downloadTasksQuery.ToList();  
  
            // ***Add a loop to process the tasks one at a time until none remain.  
            while (downloadTasks.Count > 0)  
            {  
                    // Identify the first task that completes.  
                    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
  
                    // ***Remove the selected task from the list so that you don't  
                    // process it more than once.  
                    downloadTasks.Remove(firstFinishedTask);  
  
                    // Await the completed task.  
                    int length = await firstFinishedTask;  
                    resultsTextBox.Text += String.Format("\r\nLength of the download:  {0}", length);  
            }  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        async Task<int> ProcessURL(string url, HttpClient client, CancellationToken ct)  
        {  
            // GetAsync returns a Task<HttpResponseMessage>.   
            HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            // Retrieve the website contents from the HttpResponseMessage.  
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            return urlContents.Length;  
        }  
    }  
}  
  
// Sample Output:  
  
// Length of the download:  226093  
// Length of the download:  412588  
// Length of the download:  175490  
// Length of the download:  204890  
// Length of the download:  158855  
// Length of the download:  145790  
// Length of the download:  44908  
// Downloads complete.  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4335-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4335-144">See Also</span></span>  
 <xref:System.Threading.Tasks.Task.WhenAny%2A>  
 [<span data-ttu-id="a4335-145">微調非同步應用程式 (C#)</span><span class="sxs-lookup"><span data-stu-id="a4335-145">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [<span data-ttu-id="a4335-146">使用 async 和 await 進行非同步程式設計 (C#)</span><span class="sxs-lookup"><span data-stu-id="a4335-146">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="a4335-147">非同步範例：微調應用程式 (英文)</span><span class="sxs-lookup"><span data-stu-id="a4335-147">Async Sample: Fine Tuning Your Application</span></span>](http://go.microsoft.com/fwlink/?LinkId=255046)
