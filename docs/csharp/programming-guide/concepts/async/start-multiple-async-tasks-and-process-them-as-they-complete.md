---
title: 在非同步工作完成時進行處理
ms.date: 09/12/2018
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: 9380be1dc24d7c147c22dbb1a362777f56a32358
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50202038"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a>啟動多項非同步工作並在它們完成時進行處理 (C#)

使用 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>，即可同時啟動多個工作，並在完成時逐一進行處理，而不是依啟動順序進行處理。

下列範例使用查詢來建立工作集合。 每項工作都會下載所指定網站的內容。 在 while 迴圈的的每個反覆運算中，等候的 `WhenAny` 呼叫會先傳回完成其下載的工作集合中的工作。 該工作會從集合中予以移除，並進行處理。 迴圈會重複進行，直到集合未包含其他工作為止。

> [!NOTE]
> 若要執行範例，您必須在電腦上安裝 Visual Studio (2012 或更新版本) 以及 .NET Framework 4.5 或更新版本。

## <a name="download-an-example-solution"></a>下載範例解決方案

您可以從 [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (非同步範例：微調應用程式) 下載完整 Windows Presentation Foundation (WPF) 專案，然後遵循下列步驟。

> [!TIP]
> 如果您不想要下載專案，可以檢閱本主題結尾的 MainWindow.xaml.cs 檔案。

1.  從 ZIP 檔案中解壓縮您下載的檔案，然後啟動 Visual Studio。

2.  在功能表列上選擇 [檔案] >  [開啟] > [專案/解決方案]。

3.  在 [開啟專案] 對話方塊中，開啟您已下載的範例程式碼所在的資料夾，然後開啟 AsyncFineTuningCS 的解決方案 (.sln) 檔案。

4.  在方案總管中，開啟 **ProcessTasksAsTheyFinish** 專案的捷徑功能表，然後選擇 [設定為啟始專案]。

5.  選擇 **F5** 鍵以執行程式 (或按 **Ctrl**+**F5** 鍵以執行程式而不進行偵錯)。

6.  執行專案數次，確認所下載的長度不一定會以相同的順序出現。

## <a name="create-the-program-yourself"></a>自行建立程式

此範例會新增至在[當其中一項工作完成時，取消剩餘的非同步工作 (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) 中開發的程式碼，並使用相同的 UI。

若要自行逐步建置範例，請遵循[下載範例](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md#downloading-the-example)一節中的指示，但將 [CancelAfterOneTask] 設定為啟始專案。 將本主題中的變更新增至該專案中的 `AccessTheWebAsync` 方法。 變更會標上星號。

**CancelAfterOneTask** 專案已經包含一個查詢，這個查詢在執行時，會建立一組工作。 下列程式碼中的每個 `ProcessURLAsync` 呼叫都會傳回 `TResult` 為整數的 <xref:System.Threading.Tasks.Task%601>：

```csharp
IEnumerable<Task<int>> downloadTasksQuery = from url in urlList select ProcessURL(url, client, ct);
```

在專案的 MainWindow.xaml.cs 檔案中，對 `AccessTheWebAsync` 方法進行下列變更。

-   套用 <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 來執行查詢，而非 <xref:System.Linq.Enumerable.ToArray%2A>。

    ```csharp
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
    ```

-   新增 `while` 迴圈，以對集合中的每個工作執行下列步驟：

    1.  等候 `WhenAny` 呼叫，識別集合中的第一個工作以完成其下載。

        ```csharp
        Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);
        ```

    2.  從集合中移除該工作。

        ```csharp
        downloadTasks.Remove(firstFinishedTask);
        ```

    3.  等候 `ProcessURLAsync` 呼叫所傳回的 `firstFinishedTask`。 `firstFinishedTask` 變數是 <xref:System.Threading.Tasks.Task%601>，其中 `TReturn` 是整數。 工作已完成，但您等候它擷取所下載網站的長度，如下列範例所示。

        ```csharp
        int length = await firstFinishedTask;
        resultsTextBox.Text += String.Format("\r\nLength of the download:  {0}", length);
        ```

執行程式數次，確認所下載的長度不一定會以相同的順序出現。

> [!CAUTION]
> 您可以如這個範例所述在迴圈中使用 `WhenAny`，以解決牽涉到少量工作的問題。 不過，如果您有大量的工作要處理，其他方法會更有效率。 如需詳細資訊和範例，請參閱 [Processing tasks as they complete](https://blogs.msdn.microsoft.com/pfxteam/2012/08/02/processing-tasks-as-they-complete/) (在工作完成時加以處理)。

## <a name="complete-example"></a>完整範例

下列程式碼是範例的 MainWindow.xaml.cs 檔案的完整文字。 星號會標記已針對此範例新增的項目。 同時請注意，您必須新增 <xref:System.Net.Http> 的參考。

您可以從 [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (非同步範例：微調應用程式) 下載專案。

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
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
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

## <a name="see-also"></a>另請參閱

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [微調非同步應用程式 (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [使用 async 和 await 進行非同步程式設計 (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
- [非同步範例：微調應用程式 (英文)](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)