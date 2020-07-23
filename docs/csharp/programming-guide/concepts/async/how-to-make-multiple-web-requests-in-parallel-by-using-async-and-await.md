---
title: '如何使用 async 和 await，同時發出多個 web 要求（c #）'
description: '瞭解如何在 c # 中使用 await 運算子分隔建立工作，而不是在工作建立時套用。'
ms.date: 07/20/2015
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
ms.openlocfilehash: 899dfd9165d199a67a5178bb351081ee544b231f
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925159"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a>如何使用 async 和 await，同時發出多個 web 要求（c #）
在非同步方法中，工作會在建立時啟動。 [Await](../../../language-reference/operators/await.md)運算子會套用至方法中的工作點，在此情況下無法繼續處理，直到工作完成為止。 通常會在建立工作時立即等待，如下列範例所示。  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 不過，如果您的程式有其他工作要完成，而不是相依于工作完成，您可以區分建立工作，使其無法等候工作。  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 從工作啟動到等候完成的這段期間，您可以啟動其他工作。 其他工作會以隱含方式平行執行，但不會建立其他任何執行緒。  
  
 下列程式會啟動三個非同步 web 下載，然後依照呼叫的順序來等候它們。 請注意，當您執行程式時，工作不一定會依其建立和等候的順序完成。 它們會在建立時開始執行，而且一或多個工作可能會在方法到達 await 運算式之前完成。  
  
> [!NOTE]
> 若要完成此專案，您必須在電腦上安裝 Visual Studio 2012 或更高版本以及 .NET Framework 4.5 或更高版本。  
  
 如需同時啟動多個工作的另一個範例，請參閱[如何使用 system.threading.tasks.task.whenall 擴充非同步逐步解說（c #）](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)。
  
 您可以從[開發人員程式碼範例](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)下載此範例的程式碼。  
  
### <a name="to-set-up-the-project"></a>若要設定專案  
  
1. 若要設定 WPF 應用程式，請完成下列步驟。 您可以在[逐步解說：使用 Async 和 Await 存取 Web (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md) 中，找到這些步驟的詳細指示。  
  
    - 建立 WPF 應用程式，其中包含一個文字方塊和一個按鈕。 將按鈕命名為 `startButton`，並將文字方塊命名為 `resultsTextBox`。  
  
    - 加入 <xref:System.Net.Http> 的參考。  
  
    - 在 MainWindow.xaml.cs 檔案中，新增 `System.Net.Http` 的 `using` 指示詞。  
  
### <a name="to-add-the-code"></a>新增程式碼  
  
1. 在設計視窗 MainWindow.xaml 中，按兩下此按鈕以在 MainWindow.xaml.cs 中建立 `startButton_Click` 事件處理常式。  
  
2. 將下列程式碼複製並貼到 MainWindow.xaml.cs 中的 `startButton_Click` 主體。  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     此程式碼會呼叫非同步方法 `CreateMultipleTasksAsync` 來驅動應用程式。  
  
3. 將下列支援方法新增至專案：  
  
    - `ProcessURLAsync` 使用 <xref:System.Net.Http.HttpClient> 方法，將網站內容下載為位元組陣列。 然後，支援方法 `ProcessURLAsync` 會顯示並傳回陣列的長度。  
  
    - `DisplayResults` 會顯示每個 URL 的位元組陣列中的位元組數目。 當每個工作完成下載時，即會顯示此畫面。  
  
     將下列方法複製並貼到 MainWindow.xaml.cs 中的 `startButton_Click` 事件處理常式之後。  
  
    ```csharp  
    async Task<int> ProcessURLAsync(string url, HttpClient client)  
    {  
        var byteArray = await client.GetByteArrayAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
  
    private void DisplayResults(string url, byte[] content)  
    {  
        // Display the length of each website. The string format
        // is designed to be used with a monospaced font, such as  
        // Lucida Console or Global Monospace.  
        var bytes = content.Length;  
        // Strip off the "https://".  
        var displayURL = url.Replace("https://", "");  
        resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
    }  
    ```  
  
4. 最後，定義 `CreateMultipleTasksAsync` 方法以執行下列步驟。  
  
    - 方法宣告 `HttpClient` 物件，需要存取 `ProcessURLAsync` 中的方法<xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>。  
  
    - 方法會建立並啟動三個 <xref:System.Threading.Tasks.Task%601> 類型的工作，其中 `TResult` 是整數。 當每個工作完成時，`DisplayResults` 會顯示工作的 URL 和下載內容的長度。 因為工作是以非同步方式執行，所以結果出現的順序可能會因宣告的順序而有所不同。  
  
    - 此方法會等候每個工作完成。 每個 `await` 運算子會暫停執行 `CreateMultipleTasksAsync`，直到等候的工作完成為止。 此運算子也會從每個完成的工作擷取透過呼叫 `ProcessURLAsync` 傳回的值。  
  
    - 完成工作並擷取整數值之後，此方法會加總網站的長度並顯示結果。  
  
     將下列方法複製並貼到您的方案中。  
  
    ```csharp  
    private async Task CreateMultipleTasksAsync()  
    {  
        // Declare an HttpClient object, and increase the buffer size. The  
        // default buffer size is 65,536.  
        HttpClient client =  
            new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
        // Create and start the tasks. As each task finishes, DisplayResults
        // displays its length.  
        Task<int> download1 =
            ProcessURLAsync("https://msdn.microsoft.com", client);  
        Task<int> download2 =
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
        Task<int> download3 =
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
        // Await each task.  
        int length1 = await download1;  
        int length2 = await download2;  
        int length3 = await download3;  
  
        int total = length1 + length2 + length3;  
  
        // Display the total count for the downloaded websites.  
        resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
    }  
    ```  
  
5. 選擇 F5 鍵以執行程式，然後選擇 [開始]**** 按鈕。  
  
     執行程式數次，以確認三個工作不一定會以相同的順序完成，而且它們的完成順序不一定是建立和等候的順序。  
  
## <a name="example"></a>範例  
 下列程式碼包含完整的範例。  
  
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
  
// Add the following using directive, and add a reference for System.Net.Http.  
using System.Net.Http;  
  
namespace AsyncExample_MultipleTasks  
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
            await CreateMultipleTasksAsync();  
            resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
        }  
  
        private async Task CreateMultipleTasksAsync()  
        {  
            // Declare an HttpClient object, and increase the buffer size. The  
            // default buffer size is 65,536.  
            HttpClient client =  
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
            // Create and start the tasks. As each task finishes, DisplayResults
            // displays its length.  
            Task<int> download1 =
                ProcessURLAsync("https://msdn.microsoft.com", client);  
            Task<int> download2 =
                ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
            Task<int> download3 =
                ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
            // Await each task.  
            int length1 = await download1;  
            int length2 = await download2;  
            int length3 = await download3;  
  
            int total = length1 + length2 + length3;  
  
            // Display the total count for the downloaded websites.  
            resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }  
  
        async Task<int> ProcessURLAsync(string url, HttpClient client)  
        {  
            var byteArray = await client.GetByteArrayAsync(url);  
            DisplayResults(url, byteArray);  
            return byteArray.Length;  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "https://".  
            var displayURL = url.Replace("https://", "");  
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱

- [逐步解說：使用 async 和 await 存取 Web (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [使用 Async 和 Await 進行非同步程式設計 (C#)](./index.md)
- [如何使用 System.threading.tasks.task.whenall 擴充非同步逐步解說（c #）](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
