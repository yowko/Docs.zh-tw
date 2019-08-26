---
title: 在一段時間後取消非同步工作 (C#)
ms.date: 07/20/2015
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: e00ff51e987275c6c84822f7095c82ed03b53176
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595753"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a><span data-ttu-id="4583b-102">在一段時間後取消非同步工作 (C#)</span><span class="sxs-lookup"><span data-stu-id="4583b-102">Cancel async tasks after a period of time (C#)</span></span>

<span data-ttu-id="4583b-103">如果不想等候作業完成，則可以使用 <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> 方法，在一段時間之後取消非同步作業。</span><span class="sxs-lookup"><span data-stu-id="4583b-103">You can cancel an asynchronous operation after a period of time by using the  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="4583b-104">這個方法排定取消未在 `CancelAfter` 運算式所指定之2期間內完成的任何相關工作。</span><span class="sxs-lookup"><span data-stu-id="4583b-104">This method schedules the cancellation of any associated tasks that aren’t complete within the period of time that’s designated by the `CancelAfter` expression.</span></span>

<span data-ttu-id="4583b-105">這個範例會新增至[取消一項非同步工作或工作清單 (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) 中所開發的程式碼來下載網站清單，以及顯示每個網站內容的長度。</span><span class="sxs-lookup"><span data-stu-id="4583b-105">This example adds to the code that’s developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>

> [!NOTE]
> <span data-ttu-id="4583b-106">若要執行範例，您必須在電腦上安裝 Visual Studio 2012 或更新版本以及 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="4583b-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="download-the-example"></a><span data-ttu-id="4583b-107">下載範例</span><span class="sxs-lookup"><span data-stu-id="4583b-107">Download the example</span></span>

<span data-ttu-id="4583b-108">您可以從 [Async Sample:Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (非同步範例：微調應用程式) 下載完整 Windows Presentation Foundation (WPF) 專案，然後遵循下列步驟。</span><span class="sxs-lookup"><span data-stu-id="4583b-108">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="4583b-109">解壓縮您下載的檔案，然後啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="4583b-109">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="4583b-110">在功能表列上選擇 [檔案]   >  [開啟]   > [專案/解決方案]  。</span><span class="sxs-lookup"><span data-stu-id="4583b-110">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="4583b-111">在 [開啟專案]  對話方塊中，開啟保存已解壓縮之範例程式碼的資料夾，然後開啟 AsyncFineTuningCS 的方案 (.sln) 檔案。</span><span class="sxs-lookup"><span data-stu-id="4583b-111">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="4583b-112">在方案總管  中，開啟 **CancelAfterTime** 專案的捷徑功能表，然後選擇 [設定為啟始專案]  。</span><span class="sxs-lookup"><span data-stu-id="4583b-112">In **Solution Explorer**, open the shortcut menu for the **CancelAfterTime** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="4583b-113">選擇 **F5** 鍵以執行專案。</span><span class="sxs-lookup"><span data-stu-id="4583b-113">Choose the **F5** key to run the project.</span></span> <span data-ttu-id="4583b-114">(或者，按 **Ctrl** + **F5** 鍵以執行專案，而不進行偵錯)。</span><span class="sxs-lookup"><span data-stu-id="4583b-114">(Or, press **Ctrl**+**F5** to run the project without debugging it).</span></span>

6. <span data-ttu-id="4583b-115">執行程式數次，確認輸出可能會顯示所有網站、沒有網站或某些網站的輸出。</span><span class="sxs-lookup"><span data-stu-id="4583b-115">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span>

<span data-ttu-id="4583b-116">如果您不想要下載專案，則可以檢閱本主題結尾的 MainWindow.xaml.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="4583b-116">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>

## <a name="build-the-example"></a><span data-ttu-id="4583b-117">建置範例</span><span class="sxs-lookup"><span data-stu-id="4583b-117">Build the example</span></span>

<span data-ttu-id="4583b-118">本主題中的範例會新增至[取消一項非同步工作或工作清單 (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) 中所開發的專案來取消工作清單。</span><span class="sxs-lookup"><span data-stu-id="4583b-118">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="4583b-119">雖然未明確地使用 [取消]  按鈕，但是此範例會使用相同的 UI。</span><span class="sxs-lookup"><span data-stu-id="4583b-119">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>

<span data-ttu-id="4583b-120">若要自行逐步建置範例，請遵循＜下載範例＞一節中的指示，但選擇 [CancelAListOfTasks]  作為 [啟始專案]  。</span><span class="sxs-lookup"><span data-stu-id="4583b-120">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="4583b-121">將本主題中的變更新增至該專案。</span><span class="sxs-lookup"><span data-stu-id="4583b-121">Add the changes in this topic to that project.</span></span>

<span data-ttu-id="4583b-122">若要指定將工作標記為取消之前的最長時間，請將 `CancelAfter` 呼叫新增至 `startButton_Click`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4583b-122">To specify a maximum time before the tasks are marked as canceled, add a call to `CancelAfter` to `startButton_Click`, as the following example shows.</span></span> <span data-ttu-id="4583b-123">新增的項目會以星號標記。</span><span class="sxs-lookup"><span data-stu-id="4583b-123">The addition is marked with asterisks.</span></span>

```csharp
private async void startButton_Click(object sender, RoutedEventArgs e)
{
    // Instantiate the CancellationTokenSource.
    cts = new CancellationTokenSource();

    resultsTextBox.Clear();

    try
    {
        // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
        // can adjust the time.)
        cts.CancelAfter(2500);

        await AccessTheWebAsync(cts.Token);
        resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";
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
```

 <span data-ttu-id="4583b-124">執行程式數次，確認輸出可能會顯示所有網站、沒有網站或某些網站的輸出。</span><span class="sxs-lookup"><span data-stu-id="4583b-124">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span> <span data-ttu-id="4583b-125">下列輸出是範例。</span><span class="sxs-lookup"><span data-stu-id="4583b-125">The following output is a sample.</span></span>

```
Length of the downloaded string: 35990.

Length of the downloaded string: 407399.

Length of the downloaded string: 226091.

Downloads canceled.
```

## <a name="complete-example"></a><span data-ttu-id="4583b-126">完整範例</span><span class="sxs-lookup"><span data-stu-id="4583b-126">Complete example</span></span>

<span data-ttu-id="4583b-127">下列程式碼是範例的 MainWindow.xaml.cs 檔案的完整文字。</span><span class="sxs-lookup"><span data-stu-id="4583b-127">The following code is the complete text of the MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="4583b-128">星號會標記已針對此範例新增的項目。</span><span class="sxs-lookup"><span data-stu-id="4583b-128">Asterisks mark the elements that were added for this example.</span></span>

<span data-ttu-id="4583b-129">請注意，您必須新增 <xref:System.Net.Http> 的參考。</span><span class="sxs-lookup"><span data-stu-id="4583b-129">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="4583b-130">您可以從 [Async Sample:Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (非同步範例：微調應用程式) 下載專案。</span><span class="sxs-lookup"><span data-stu-id="4583b-130">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

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

namespace CancelAfterTime
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
                // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
                // can adjust the time.)
                cts.CancelAfter(2500);

                await AccessTheWebAsync(cts.Token);
                resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";
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

        // You can still include a Cancel button if you want to.
        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        async Task AccessTheWebAsync(CancellationToken ct)
        {
            // Declare an HttpClient object.
            HttpClient client = new HttpClient();

            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            foreach (var url in urlList)
            {
                // GetAsync returns a Task<HttpResponseMessage>.
                // Argument ct carries the message if the Cancel button is chosen.
                // Note that the Cancel button cancels all remaining downloads.
                HttpResponseMessage response = await client.GetAsync(url, ct);

                // Retrieve the website contents from the HttpResponseMessage.
                byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            }
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }
    }

    // Sample Output:

    // Length of the downloaded string: 35990.

    // Length of the downloaded string: 407399.

    // Length of the downloaded string: 226091.

    // Downloads canceled.
}
```

## <a name="see-also"></a><span data-ttu-id="4583b-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4583b-131">See also</span></span>

- [<span data-ttu-id="4583b-132">使用 Async 和 Await 進行非同步程式設計 (C#)</span><span class="sxs-lookup"><span data-stu-id="4583b-132">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="4583b-133">逐步解說：使用 Async 和 Await 存取 Web (C#)</span><span class="sxs-lookup"><span data-stu-id="4583b-133">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="4583b-134">取消一項非同步工作或工作清單 (C#)</span><span class="sxs-lookup"><span data-stu-id="4583b-134">Cancel an Async Task or a List of Tasks (C#)</span></span>](./cancel-an-async-task-or-a-list-of-tasks.md)
- [<span data-ttu-id="4583b-135">微調非同步應用程式 (C#)</span><span class="sxs-lookup"><span data-stu-id="4583b-135">Fine-Tuning Your Async Application (C#)</span></span>](./fine-tuning-your-async-application.md)
- [<span data-ttu-id="4583b-136">非同步範例：微調您的應用程式</span><span class="sxs-lookup"><span data-stu-id="4583b-136">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
