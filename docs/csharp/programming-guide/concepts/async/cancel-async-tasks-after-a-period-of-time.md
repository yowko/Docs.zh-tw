---
title: 在一段時間後取消非同步工作 (C#)
ms.date: 07/20/2015
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: 55cf6b960752b36a1bfbd8ede25d7693225fbb20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325704"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a>在一段時間後取消非同步工作 (C#)
如果不想等候作業完成，則可以使用 <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> 方法，在一段時間之後取消非同步作業。 這個方法排定取消未在 `CancelAfter` 運算式所指定之2期間內完成的任何相關工作。  
  
 這個範例會新增至[取消一項非同步工作或工作清單 (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) 中所開發的程式碼來下載網站清單，以及顯示每個網站內容的長度。  
  
> [!NOTE]
>  若要執行範例，您必須在電腦上安裝 Visual Studio 2012 或更新版本以及 .NET Framework 4.5 或更新版本。  
  
## <a name="downloading-the-example"></a>下載範例  
 您可以從 [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (非同步範例：微調應用程式) 下載完整 Windows Presentation Foundation (WPF) 專案，然後遵循下列步驟。  
  
1.  解壓縮您下載的檔案，然後啟動 Visual Studio。  
  
2.  在功能表列上，依序選擇 [檔案] 、[開啟舊檔] 及 [專案/方案] 。  
  
3.  在 [開啟專案] 對話方塊中，開啟保存已解壓縮之範例程式碼的資料夾，然後開啟 AsyncFineTuningCS 的方案 (.sln) 檔案。  
  
4.  在方案總管中，開啟 **CancelAfterTime** 專案的捷徑功能表，然後選擇 [設定為啟始專案]。  
  
5.  選擇 F5 鍵執行執行專案。  
  
     選擇 CTRL+F5 鍵以執行專案，而不進行偵錯。  
  
6.  執行程式數次，確認輸出可能會顯示所有網站、沒有網站或某些網站的輸出。  
  
 如果您不想要下載專案，則可以檢閱本主題結尾的 MainWindow.xaml.cs 檔案。  
  
## <a name="building-the-example"></a>建置範例  
 本主題中的範例會新增至[取消一項非同步工作或工作清單 (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) 中所開發的專案來取消工作清單。 雖然未明確地使用 [取消] 按鈕，但是此範例會使用相同的 UI。  
  
 若要自行逐步建置範例，請遵循＜下載範例＞一節中的指示，但選擇 [CancelAListOfTasks] 作為 [啟始專案]。 將本主題中的變更新增至該專案。  
  
 若要指定將工作標記為取消之前的最長時間，請將 `CancelAfter` 呼叫新增至 `startButton_Click`，如下列範例所示。 新增的項目會以星號標記。  
  
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
  
 執行程式數次，確認輸出可能會顯示所有網站、沒有網站或某些網站的輸出。 下列輸出是範例。  
  
```  
Length of the downloaded string: 35990.  
  
Length of the downloaded string: 407399.  
  
Length of the downloaded string: 226091.  
  
Downloads canceled.  
```  
  
## <a name="complete-example"></a>完整範例  
 下列程式碼是範例的 MainWindow.xaml.cs 檔案的完整文字。 星號會標記已針對此範例新增的項目。  
  
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
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);  
            }  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
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
  
## <a name="see-also"></a>請參閱  
 [使用 async 和 await 進行非同步程式設計 (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
 [逐步解說：使用 async 和 await 存取 Web (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [取消一項非同步工作或工作清單 (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)  
 [微調非同步應用程式 (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [非同步範例：微調應用程式 (英文)](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
