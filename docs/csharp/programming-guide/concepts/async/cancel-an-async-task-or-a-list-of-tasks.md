---
title: "取消一項非同步工作或工作清單 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 9fbfa3602766b51c4be5078b793139501802a90c
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017

---
# <a name="cancel-an-async-task-or-a-list-of-tasks-c"></a>取消一項非同步工作或工作清單 (C#)
如果您不想要等候非同步應用程式完成，則可以設定可用來取消非同步應用程式的按鈕。 遵循本主題中的範例，即可將取消按鈕新增至下載某個網站內容或網站清單的應用程式。  
  
 這些範例會使用[微調非同步應用程式 (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) 所描述的 UI。  
  
> [!NOTE]
>  若要執行範例，您必須在電腦上安裝 Visual Studio 2012 或更新版本以及 .NET Framework 4.5 或更新版本。  
  
##  <a name="BKMK_CancelaTask"></a> 取消工作  
 第一個範例會建立 [取消] 按鈕與單一下載工作的關聯。 如果您在應用程式下載內容時選擇該按鈕，則會取消下載。  
  
### <a name="downloading-the-example"></a>下載範例  
 您可以從 [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) (非同步範例：微調應用程式) 下載完整 Windows Presentation Foundation (WPF) 專案，然後遵循下列步驟。  
  
1.  解壓縮您下載的檔案，然後啟動 Visual Studio。  
  
2.  在功能表列上，依序選擇 [檔案] 、[開啟舊檔] 及 [專案/方案] 。  
  
3.  在 [開啟專案] 對話方塊中，開啟保存已解壓縮之範例程式碼的資料夾，然後開啟 AsyncFineTuningCS 的方案 (.sln) 檔案。  
  
4.  在方案總管中，開啟 **CancelATask** 專案的捷徑功能表，然後選擇 [設定為啟始專案]。  
  
5.  選擇 F5 鍵執行執行專案。  
  
     選擇 CTRL+F5 鍵以執行專案，而不進行偵錯。  
  
 如果您不想要下載專案，則可以檢閱本主題結尾的 MainWindow.xaml.cs 檔案。  
  
### <a name="building-the-example"></a>建置範例  
 下列變更會將 [取消] 按鈕新增至下載網站的應用程式。 如果您不想要下載或建置範例，則可以檢閱本主題結尾處的＜完整範例＞一節中的最終產品。 星號會標記程式碼中的變更。  
  
 若要自行逐步建置範例，請遵循＜下載範例＞一節中的指示，但選擇 [StarterCode] 作為 [啟始專案]，而非 [CancelATask]。  
  
 然後將下列變更新增至該專案的 MainWindow.xaml.cs 檔案。  
  
1.  宣告 `CancellationTokenSource` 變數 `cts`，這是在存取它之所有方法的範圍內。  
  
    ```csharp  
    public partial class MainWindow : Window  
    {  
        // ***Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
    ```  
  
2.  針對 [取消] 按鈕新增下列事件處理常式。 事件處理常式會使用 <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName> 方法，以在使用者要求取消時通知 `cts`。  
  
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
  
3.  在 [開始] 按鈕 `startButton_Click` 的事件處理常式中進行下列變更。  
  
    -   具現化 `CancellationTokenSource`、`cts`。  
  
        ```csharp  
        // ***Instantiate the CancellationTokenSource.  
        cts = new CancellationTokenSource();  
        ```  
  
    -   在下載所指定網站內容的 `AccessTheWebAsync` 呼叫中，傳送 `cts` 的 <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=fullName> 屬性作為引數。 如果要求取消，則 `Token` 屬性會傳播訊息。 新增 catch 區塊，以在使用者選擇取消下載作業時顯示訊息。 下列程式碼示範這些變更。  
  
        ```csharp  
        try  
        {  
            // ***Send a token to carry the message if cancellation is requested.  
            int contentLength = await AccessTheWebAsync(cts.Token);  
            resultsTextBox.Text +=  
                String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
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
  
4.  在 `AccessTheWebAsync` 中，使用 <xref:System.Net.Http.HttpClient> 類型中 `GetAsync` 方法的 <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=fullName> 多載來下載網站的內容。 將 `ct` (`AccessTheWebAsync` 的 <xref:System.Threading.CancellationToken> 參數) 傳遞為第二個引數。 如果使用者選擇 [取消] 按鈕，則權杖會夾帶訊息。  
  
     下列程式碼示範 `AccessTheWebAsync` 中的變更。  
  
    ```csharp  
    // ***Provide a parameter for the CancellationToken.  
    async Task<int> AccessTheWebAsync(CancellationToken ct)  
    {  
        HttpClient client = new HttpClient();  
  
        resultsTextBox.Text +=  
            String.Format("\r\nReady to download.\r\n");  
  
        // You might need to slow things down to have a chance to cancel.  
        await Task.Delay(250);  
  
        // GetAsync returns a Task<HttpResponseMessage>.   
        // ***The ct argument carries the message if the Cancel button is chosen.  
        HttpResponseMessage response = await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct);  
  
        // Retrieve the website contents from the HttpResponseMessage.  
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
        // The result of the method is the length of the downloaded website.  
        return urlContents.Length;  
    }  
    ```  
  
5.  如果您未取消程式，則會產生下列輸出。  
  
    ```  
    Ready to download.  
    Length of the downloaded string: 158125.  
    ```  
  
     如果您在程式完成下載內容之前選擇 [取消] 按鈕，程式會產生下列輸出。  
  
    ```  
    Ready to download.  
    Download canceled.  
    ```  
  
##  <a name="BKMK_CancelaListofTasks"></a> 取消工作清單  
 您可以將相同 `CancellationTokenSource` 執行個體與每項工作建立關聯，以擴充先前的範例來取消許多工作。 如果您選擇 [取消] 按鈕，即會取消所有尚未完成的工作。  
  
### <a name="downloading-the-example"></a>下載範例  
 您可以從 [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) (非同步範例：微調應用程式) 下載完整 Windows Presentation Foundation (WPF) 專案，然後遵循下列步驟。  
  
1.  解壓縮您下載的檔案，然後啟動 Visual Studio。  
  
2.  在功能表列上，依序選擇 [檔案] 、[開啟舊檔] 及 [專案/方案] 。  
  
3.  在 [開啟專案] 對話方塊中，開啟保存已解壓縮之範例程式碼的資料夾，然後開啟 AsyncFineTuningCS 的方案 (.sln) 檔案。  
  
4.  在方案總管中，開啟 **CancelAListOfTasks** 專案的捷徑功能表，然後選擇 [設定為啟始專案]。  
  
5.  選擇 F5 鍵執行執行專案。  
  
     選擇 CTRL+F5 鍵以執行專案，而不進行偵錯。  
  
 如果您不想要下載專案，則可以檢閱本主題結尾的 MainWindow.xaml.cs 檔案。  
  
### <a name="building-the-example"></a>建置範例  
 若要自行逐步擴充範例，請遵循＜下載範例＞一節中的指示，但選擇 [CancelATask] 作為 [啟始專案]。 將下列變更新增至該專案。 星號會標記程式中的變更。  
  
1.  新增方法以建立網址清單。  
  
    ```csharp  
    // ***Add a method that creates a list of web addresses.  
    private List<string> SetUpURLList()  
    {  
        List<string> urls = new List<string>   
        {   
            "http://msdn.microsoft.com",  
            "http://msdn.microsoft.com/library/hh290138.aspx",  
            "http://msdn.microsoft.com/library/hh290140.aspx",  
            "http://msdn.microsoft.com/library/dd470362.aspx",  
            "http://msdn.microsoft.com/library/aa578028.aspx",  
            "http://msdn.microsoft.com/library/ms404677.aspx",  
            "http://msdn.microsoft.com/library/ff730837.aspx"  
        };  
        return urls;  
    }  
    ```  
  
2.  在 `AccessTheWebAsync` 中呼叫方法。  
  
    ```csharp  
    // ***Call SetUpURLList to make a list of web addresses.  
    List<string> urlList = SetUpURLList();  
    ```  
  
3.  在 `AccessTheWebAsync` 中新增下列迴圈，以處理清單中的每個網址。  
  
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
            String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);  
    }  
    ```  
  
4.  因為 `AccessTheWebAsync` 顯示長度，所以此方法不需要傳回任何項目。 移除 return 陳述式，並將方法的傳回型別變更為 <xref:System.Threading.Tasks.Task>，而非 <xref:System.Threading.Tasks.Task%601>。  
  
    ```csharp  
    async Task AccessTheWebAsync(CancellationToken ct)  
    ```  
  
     使用陳述式，從 `startButton_Click` 呼叫方法，而不是使用運算式。  
  
    ```csharp  
    await AccessTheWebAsync(cts.Token);  
    ```  
  
5.  如果您未取消程式，則會產生下列輸出。  
  
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
  
     如果您在下載完成之前選擇 [取消] 按鈕，則輸出會包含在取消之前完成之下載的長度。  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Downloads canceled.  
  
    ```  
  
##  <a name="BKMK_CompleteExamples"></a> 完整範例  
 下列各節包含每個先前範例的程式碼。 請注意，您必須新增 <xref:System.Net.Http> 的參考。  
  
 您可以從 [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) (非同步範例：微調應用程式) 下載專案。  
  
### <a name="cancel-a-task-example"></a>取消工作範例  
 下列程式碼是取消單一工作之範例的完整 MainWindow.xaml.cs 檔案。  
  
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
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
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
  
            resultsTextBox.Text +=  
                String.Format("\r\nReady to download.\r\n");  
  
            // You might need to slow things down to have a chance to cancel.  
            await Task.Delay(250);  
  
            // GetAsync returns a Task<HttpResponseMessage>.   
            // ***The ct argument carries the message if the Cancel button is chosen.  
            HttpResponseMessage response = await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct);  
  
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
  
### <a name="cancel-a-list-of-tasks-example"></a>取消工作清單範例  
 下列程式碼是取消工作清單之範例的完整 MainWindow.xaml.cs 檔案。  
  
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
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);  
            }  
        }  
  
        // ***Add a method that creates a list of web addresses.  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
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
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.CancellationTokenSource>   
 <xref:System.Threading.CancellationToken>   
 [使用 async 和 await 進行非同步程式設計 (C#)](../../../../csharp/programming-guide/concepts/async/index.md)   
 [微調非同步應用程式 (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)   
 [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) (非同步範例：微調應用程式)
