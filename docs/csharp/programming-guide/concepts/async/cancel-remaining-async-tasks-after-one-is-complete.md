---
title: 當其中一項工作完成時，取消剩餘的非同步工作 (C#)
ms.date: 07/20/2015
ms.assetid: d3cebc74-c392-497b-b1e6-62a262eabe05
ms.openlocfilehash: 40f010c4e1d84e6378334c826c58514f83b84657
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2018
ms.locfileid: "49349039"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a>當其中一項工作完成時，取消剩餘的非同步工作 (C#)
搭配使用 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> 方法與 <xref:System.Threading.CancellationToken>，即可在其中一個工作完成時取消所有剩餘的工作。 `WhenAny` 方法會接受本身為一組工作的引數。 這個方法會啟動所有工作，並傳回單一工作。 集合中的任何工作完成時，單一工作即完成。  
  
 這個範例示範如何搭配使用取消權杖與 `WhenAny` 以完成這組工作中的第一項工作，並取消其餘工作。 每一項工作都會下載網站的內容。 此範例顯示要完成的第一個下載內容的長度，並取消其他下載。  
  
> [!NOTE]
>  若要執行範例，您必須在電腦上安裝 Visual Studio 2012 或更新版本以及 .NET Framework 4.5 或更新版本。  
  
## <a name="downloading-the-example"></a>下載範例  
 您可以從 [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (非同步範例：微調應用程式) 下載完整 Windows Presentation Foundation (WPF) 專案，然後遵循下列步驟。  
  
1.  解壓縮您下載的檔案，然後啟動 Visual Studio。  
  
2.  在功能表列上，依序選擇 [檔案] 、[開啟舊檔] 及 [專案/方案] 。  
  
3.  在 [開啟專案] 對話方塊中，開啟保存已解壓縮之範例程式碼的資料夾，然後開啟 AsyncFineTuningCS 的方案 (.sln) 檔案。  
  
4.  在方案總管中，開啟 **CancelAfterOneTask** 專案的捷徑功能表，然後選擇 [設定為啟始專案]。  
  
5.  選擇 F5 鍵以執行專案。  
  
     選擇 CTRL+F5 鍵以執行專案，而不進行偵錯。  
  
6.  執行程式數次，確認先完成不同的下載。  
  
 如果您不想要下載專案，則可以檢閱本主題結尾的 MainWindow.xaml.cs 檔案。  
  
## <a name="building-the-example"></a>建置範例  
 本主題中的範例會新增至[取消一項非同步工作或工作清單 (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) 中所開發的專案來取消工作清單。 雖然未明確地使用 [取消] 按鈕，但是此範例會使用相同的 UI。  
  
 若要自行逐步建置範例，請遵循＜下載範例＞一節中的指示，但選擇 [CancelAListOfTasks] 作為 [啟始專案]。 將本主題中的變更新增至該專案。  
  
 在 **CancelAListOfTasks** 專案的 MainWindow.xaml.cs 檔案中，將每個網站的處理步驟從 `AccessTheWebAsync` 中的迴圈移至下列非同步方法即可開始轉換。  
  
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
  
 在 `AccessTheWebAsync` 中，這個範例會使用查詢、<xref:System.Linq.Enumerable.ToArray%2A> 方法和 `WhenAny` 方法來建立並啟動工作陣列。 將 `WhenAny` 套用至陣列，會傳回評估為在工作陣列中完成之第一個工作的等候中單一工作。  
  
 在 `AccessTheWebAsync` 中進行下列變更。 星號會標記程式碼檔中的變更。  
  
1.  註解化或刪除迴圈。  
  
2.  建立查詢，而查詢在執行時會產生一組泛型工作。 每個 `ProcessURLAsync` 呼叫都會傳回 `TResult` 為整數的 <xref:System.Threading.Tasks.Task%601>。  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3.  呼叫 `ToArray` 來執行查詢，並開始工作。 在下一個步驟中套用 `WhenAny` 方法會執行查詢並啟動工作，而不使用 `ToArray`，但其他方法可能為否。 最安全的做法是明確地強制執行查詢。  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.   
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4.  對這組工作呼叫 `WhenAny`。 `WhenAny` 會傳回 `Task(Of Task(Of Integer))` 或 `Task<Task<int>>`。  亦即，`WhenAny` 會傳回評估為單一 `Task(Of Integer)` 或 `Task<int>` 的等候中工作。 該單一工作是完成集合中的第一項工作。 先完成的工作會指派給 `firstFinishedTask`。 `firstFinishedTask` 的型別是 `TResult` 為整數的 <xref:System.Threading.Tasks.Task%601>，因為這是 `ProcessURLAsync` 的傳回型別。  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes   
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5.  在此範例中，您只想要知道先完成的工作。 因此，請使用 <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> 取消剩餘的工作。  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6.  最後，等候 `firstFinishedTask` 擷取所下載內容的長度。  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += String.Format("\r\nLength of the downloaded website:  {0}\r\n", length);  
    ```  
  
 執行程式數次，確認先完成不同的下載。  
  
## <a name="complete-example"></a>完整範例  
 下列程式碼是範例的完整 MainWindow.xaml.cs 檔案。 星號會標記已針對此範例新增的項目。  
  
 請注意，您必須新增 <xref:System.Net.Http> 的參考。  
  
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
            //        String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);  
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
            resultsTextBox.Text += String.Format("\r\nLength of the downloaded website:  {0}\r\n", length);  
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
  
## <a name="see-also"></a>請參閱

- <xref:System.Threading.Tasks.Task.WhenAny%2A>  
- [微調非同步應用程式 (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
- [使用 async 和 await 進行非同步程式設計 (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
- [非同步範例：微調應用程式 (英文)](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
