---
title: 如何：使用 Task.WhenAll 擴充非同步逐步解說的內容 (C#)
ms.date: 07/20/2015
ms.assetid: f6927ef2-dc6c-43f8-bc82-bbeac42de423
ms.openlocfilehash: 4bdd3f32d2fa502de8ada352c522198a89a17f97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339465"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-c"></a>如何：使用 Task.WhenAll 擴充非同步逐步解說的內容 (C#)
您可以使用 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 方法，來提升[逐步解說：使用 Async 和 Await 存取 Web (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) 中非同步方案的效能。 此方法會以非同步方式等候多個非同步作業進行，這些作業是以工作集合來表示。  
  
 您在此逐步解說中可能已注意到網站下載的速度各自不同。 有時其中一個網站的速度很慢，而導致所有其餘下載延後執行。 當您執行在此逐步解說中建立的非同步方案時，如果不想要等候，您可以輕鬆地結束程式；但更好的做法是同時啟動所有下載，並讓較快的下載繼續執行而不等候延遲的下載。  
  
 您可以將 `Task.WhenAll` 方法套用至工作集合。 套用 `WhenAll` 會傳回未完成的單一工作，直到集合中的所有工作都完成為止。 工作似乎會平行執行，但不會建立其他任何執行緒。 工作可以依任何順序完成。  
  
> [!IMPORTANT]
>  下列程序描述在[逐步解說：使用 Async 和 Await 存取 Web (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) 中開發之非同步應用程式的擴充。 您可以藉由完成此逐步解說，或從[開發人員程式碼範例](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)下載程式碼，來開發應用程式。  
>   
>  若要執行範例，您必須在電腦上安裝 Visual Studio 2012 或更新版本。  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a>將 Task.WhenAll 新增至您的 GetURLContentsAsync 方案  
  
1.  將 `ProcessURLAsync` 方法新增至在[逐步解說：使用 Async 和 Await 存取 Web (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) 中開發的第一個應用程式。  
  
    -   如果您已從[開發人員程式碼範例](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)下載程式碼，請開啟 AsyncWalkthrough 專案，然後將 `ProcessURLAsync` 新增至 MainWindow.xaml.cs 檔案。  
  
    -   如果您藉由完成此逐步解說來開發程式碼，請將 `ProcessURLAsync` 新增至包含 `GetURLContentsAsync` 方法的應用程式。 此應用程式的 MainWindow.xaml.cs 檔案是＜逐步解說中完整的程式碼範例＞一節的第一個範例。  
  
     `ProcessURLAsync` 方法會合併原始逐步解說中 `SumPageSizesAsync` 之 `foreach` 迴圈主體內的動作。 此方法會以非同步方式將指定網站的內容下載為位元組陣列，然後顯示並傳回位元組陣列的長度。  
  
    ```csharp  
    private async Task<int> ProcessURLAsync(string url)  
    {  
        var byteArray = await GetURLContentsAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
    ```  
  
2.  將 `SumPageSizesAsync` 中的 `foreach` 迴圈註解化或刪除，如下列程式碼所示。  
  
    ```csharp  
    //var total = 0;  
    //foreach (var url in urlList)  
    //{  
    //    byte[] urlContents = await GetURLContentsAsync(url);  
  
    //    // The previous line abbreviates the following two assignment statements.  
    //    // GetURLContentsAsync returns a Task<T>. At completion, the task  
    //    // produces a byte array.  
    //    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
    //    //byte[] urlContents = await getContentsTask;  
  
    //    DisplayResults(url, urlContents);  
  
    //    // Update the total.            
    //    total += urlContents.Length;  
    //}  
    ```  
  
3.  建立工作集合。 下列程式碼定義一個[查詢](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)，當 <xref:System.Linq.Enumerable.ToArray%2A> 方法執行此查詢時，會建立工作集合以下載每個網站的內容。 工作會在評估查詢之後啟動。  
  
     將下列程式碼新增至 `urlList` 宣告後面的 `SumPageSizesAsync` 方法。  
  
    ```csharp  
    // Create a query.   
    IEnumerable<Task<int>> downloadTasksQuery =   
        from url in urlList select ProcessURLAsync(url);  
  
    // Use ToArray to execute the query and start the download tasks.  
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4.  將 `Task.WhenAll` 套用至工作集合 `downloadTasks`。 `Task.WhenAll` 會傳回當工作集合中所有工作完成後才會完成的單一工作。  
  
     在下列範例中，`await` 運算式會等候 `WhenAll` 傳回的單一工作完成。 此運算式會評估為整數陣列，其中每個整數都是所下載網站的長度。 將下列程式碼新增至 `SumPageSizesAsync`，就在您於上一個步驟中新增的程式碼之後。  
  
    ```csharp  
    // Await the completion of all the running tasks.  
    int[] lengths = await Task.WhenAll(downloadTasks);  
  
    //// The previous line is equivalent to the following two statements.  
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
    //int[] lengths = await whenAllTask;  
    ```  
  
5.  最後，使用 <xref:System.Linq.Enumerable.Sum%2A> 方法來計算所有網站的長度總和。 將下列程式碼行新增至 `SumPageSizesAsync`。  
  
    ```csharp  
    int total = lengths.Sum();  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a>將 Task.WhenAll 新增至 HttpClient.GetByteArrayAsync 方案  
  
1.  將下列版本的 `ProcessURLAsync` 新增至在[逐步解說：使用 Async 和 Await 存取 Web (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) 中開發的第二個應用程式。  
  
    -   如果您已從[開發人員程式碼範例](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)下載程式碼，請開啟 AsyncWalkthrough_HttpClient 專案，然後將 `ProcessURLAsync` 新增至 MainWindow.xaml.cs 檔案。  
  
    -   如果您藉由完成此逐步解說來開發程式碼，請將 `ProcessURLAsync` 新增至使用 `HttpClient.GetByteArrayAsync` 方法的應用程式。 此應用程式的 MainWindow.xaml.cs 檔案是＜逐步解說中完整的程式碼範例＞一節的第二個範例。  
  
     `ProcessURLAsync` 方法會合併原始逐步解說中 `SumPageSizesAsync` 之 `foreach` 迴圈主體內的動作。 此方法會以非同步方式將指定網站的內容下載為位元組陣列，然後顯示並傳回位元組陣列的長度。  
  
     其與上一個步驟中 `ProcessURLAsync` 方法的唯一差別，在於使用了 <xref:System.Net.Http.HttpClient> 執行個體 `client`。  
  
    ```csharp  
    async Task<int> ProcessURL(string url, HttpClient client)  
    {  
        byte[] byteArray = await client.GetByteArrayAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
    ```  
  
2.  將 `SumPageSizesAsync` 中的 `For Each` 或 `foreach` 迴圈註解化或刪除，如下列程式碼所示。  
  
    ```csharp  
    //var total = 0;  
    //foreach (var url in urlList)  
    //{  
    //    // GetByteArrayAsync returns a Task<T>. At completion, the task  
    //    // produces a byte array.  
    //    byte[] urlContent = await client.GetByteArrayAsync(url);  
  
    //    // The previous line abbreviates the following two assignment  
    //    // statements.  
    //    Task<byte[]> getContentTask = client.GetByteArrayAsync(url);  
    //    byte[] urlContent = await getContentTask;  
  
    //    DisplayResults(url, urlContent);  
  
    //    // Update the total.  
    //    total += urlContent.Length;  
    //}  
    ```  
  
3.  定義一個[查詢](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)，當 <xref:System.Linq.Enumerable.ToArray%2A> 方法執行此查詢時，會建立工作集合以下載每個網站的內容。 工作會在評估查詢之後啟動。  
  
     將下列程式碼新增至 `client` 和 `urlList` 宣告後面的 `SumPageSizesAsync` 方法。  
  
    ```csharp  
    // Create a query.  
    IEnumerable<Task<int>> downloadTasksQuery =   
        from url in urlList select ProcessURL(url, client);  
  
    // Use ToArray to execute the query and start the download tasks.  
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4.  接下來，將 `Task.WhenAll` 套用至工作集合 `downloadTasks`。 `Task.WhenAll` 會傳回當工作集合中所有工作完成後才會完成的單一工作。  
  
     在下列範例中，`await` 運算式會等候 `WhenAll` 傳回的單一工作完成。 完成時，`await` 運算式會評估為整數陣列，其中每個整數都是所下載網站的長度。 將下列程式碼新增至 `SumPageSizesAsync`，就在您於上一個步驟中新增的程式碼之後。  
  
    ```csharp  
    // Await the completion of all the running tasks.  
    int[] lengths = await Task.WhenAll(downloadTasks);  
  
    //// The previous line is equivalent to the following two statements.  
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
    //int[] lengths = await whenAllTask;  
    ```  
  
5.  最後，使用 <xref:System.Linq.Enumerable.Sum%2A> 方法取得所有網站的長度總和。 將下列程式碼行新增至 `SumPageSizesAsync`。  
  
    ```csharp  
    int total = lengths.Sum();
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a>測試 Task.WhenAll 方案  
  
-   針對任一方案，選擇 F5 鍵以執行程式，然後選擇 [開始] 按鈕。 輸出應類似於[逐步解說：使用 Async 和 Await 存取 Web (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) 中的非同步方案輸出。 不過請注意，網站每次出現的順序都不同。  
  
## <a name="example"></a>範例  
 下列程式碼顯示專案擴充，其使用 `GetURLContentsAsync` 方法從 Web 下載內容。  
  
```csharp  
// Add the following using directives, and add a reference for System.Net.Http.  
using System.Net.Http;  
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF_WhenAll  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            resultsTextBox.Clear();  
  
            // Two-step async call.  
            Task sumTask = SumPageSizesAsync();  
            await sumTask;  
  
            // One-step async call.  
            //await SumPageSizesAsync();  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // Create a query.   
            IEnumerable<Task<int>> downloadTasksQuery =   
                from url in urlList select ProcessURLAsync(url);  
  
            // Use ToArray to execute the query and start the download tasks.  
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
  
            // You can do other work here before awaiting.  
  
            // Await the completion of all the running tasks.  
            int[] lengths = await Task.WhenAll(downloadTasks);  
  
            //// The previous line is equivalent to the following two statements.  
            //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
            //int[] lengths = await whenAllTask;  
  
            int total = lengths.Sum();  
  
            //var total = 0;  
            //foreach (var url in urlList)  
            //{  
            //    byte[] urlContents = await GetURLContentsAsync(url);  
  
            //    // The previous line abbreviates the following two assignment statements.  
            //    // GetURLContentsAsync returns a Task<T>. At completion, the task  
            //    // produces a byte array.  
            //    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
            //    //byte[] urlContents = await getContentsTask;  
  
            //    DisplayResults(url, urlContents);  
  
            //    // Update the total.            
            //    total += urlContents.Length;  
            //}  
  
            // Display the total count for all of the websites.  
            resultsTextBox.Text +=  
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        // The actions from the foreach loop are moved to this async method.  
        private async Task<int> ProcessURLAsync(string url)  
        {  
            var byteArray = await GetURLContentsAsync(url);  
            DisplayResults(url, byteArray);  
            return byteArray.Length;  
        }  
  
        private async Task<byte[]> GetURLContentsAsync(string url)  
        {  
            // The downloaded resource ends up in the variable named content.  
            var content = new MemoryStream();  
  
            // Initialize an HttpWebRequest for the current URL.  
            var webReq = (HttpWebRequest)WebRequest.Create(url);  
  
            // Send the request to the Internet resource and wait for  
            // the response.  
            using (WebResponse response = await webReq.GetResponseAsync())  
            {  
                // Get the data stream that is associated with the specified url.  
                using (Stream responseStream = response.GetResponseStream())  
                {  
                    await responseStream.CopyToAsync(content);  
                }  
            }  
  
            // Return the result as a byte array.  
            return content.ToArray();  
  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
  
        }  
    }  
}  
```  
  
## <a name="example"></a>範例  
 下列程式碼顯示專案擴充，其使用 `HttpClient.GetByteArrayAsync` 方法從 Web 下載內容。  
  
```csharp  
// Add the following using directives, and add a reference for System.Net.Http.  
using System.Net.Http;  
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF_HttpClient_WhenAll  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            resultsTextBox.Clear();  
  
            // One-step async call.  
            await SumPageSizesAsync();  
  
            // Two-step async call.  
            //Task sumTask = SumPageSizesAsync();  
            //await sumTask;  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // Declare an HttpClient object and increase the buffer size. The  
            // default buffer size is 65,536.  
            HttpClient client = new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
            // Create a query.  
            IEnumerable<Task<int>> downloadTasksQuery =   
                from url in urlList select ProcessURL(url, client);  
  
            // Use ToArray to execute the query and start the download tasks.  
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
  
            // You can do other work here before awaiting.  
  
            // Await the completion of all the running tasks.  
            int[] lengths = await Task.WhenAll(downloadTasks);  
  
            //// The previous line is equivalent to the following two statements.  
            //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
            //int[] lengths = await whenAllTask;  
  
            int total = lengths.Sum();  
  
            //var total = 0;  
            //foreach (var url in urlList)  
            //{  
            //    // GetByteArrayAsync returns a Task<T>. At completion, the task  
            //    // produces a byte array.  
            //    byte[] urlContent = await client.GetByteArrayAsync(url);  
  
            //    // The previous line abbreviates the following two assignment  
            //    // statements.  
            //    Task<byte[]> getContentTask = client.GetByteArrayAsync(url);  
            //    byte[] urlContent = await getContentTask;  
  
            //    DisplayResults(url, urlContent);  
  
            //    // Update the total.  
            //    total += urlContent.Length;  
            //}  
  
            // Display the total count for all of the web addresses.  
            resultsTextBox.Text +=  
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        // The actions from the foreach loop are moved to this async method.  
        async Task<int> ProcessURL(string url, HttpClient client)  
        {  
            byte[] byteArray = await client.GetByteArrayAsync(url);  
            DisplayResults(url, byteArray);  
            return byteArray.Length;  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each web site. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>  
 [逐步解說：使用 async 和 await 存取 Web (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
