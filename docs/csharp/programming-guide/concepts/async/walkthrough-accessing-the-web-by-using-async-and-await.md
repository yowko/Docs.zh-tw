---
title: 逐步解說：使用 async 和 await 存取 Web (C#)
ms.date: 07/20/2015
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
ms.openlocfilehash: 24ce1e405019ef83ff6bcbb61552d6fc5d911935
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2018
ms.locfileid: "47455745"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a>逐步解說：使用 async 和 await 存取 Web (C#)

您可以使用 async/await 功能，以更容易且直觀的方式撰寫非同步程式。 您可以撰寫非同步程式碼，使其看起來像是同步程式碼，讓編譯器處理困難的回呼函式和非同步程式碼通常需要的接續。

如需非同步功能的詳細資訊，請參閱[使用 async 和 await 進行非同步程式設計 (C#)](../../../../csharp/programming-guide/concepts/async/index.md)。

本逐步解說從同步化 Windows Presentation Foundation (WPF) 應用程式開始，該應用程式會加總網站清單中的位元組數目。 然後逐步解說會藉由使用新功能，將應用程式轉換為非同步解決方案。

如果您不想要自行建置應用程式，可以下載 [Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) (非同步範例：存取 Web 逐步解說 (C# 和 Visual Basic))。

> [!NOTE]
> 若要執行範例，您必須在電腦上安裝 Visual Studio 2012 或更新版本以及 .NET Framework 4.5 或更新版本。

## <a name="create-a-wpf-application"></a>建立 WPF 應用程式

1.  啟動 Visual Studio。

2.  在功能表列上，選擇 [檔案] > [新增] > [專案]。

     [ **新增專案** ] 對話方塊隨即開啟。

3.  在 [已安裝的範本] 窗格中，選擇 [Visual C#]，然後從專案類型清單中選擇 [WPF 應用程式]。

4.  在 [名稱] 文字方塊中，輸入 `AsyncExampleWPF`，然後選擇 [確定] 按鈕。

     新的專案隨即會出現在方案總管中。

## <a name="design-a-simple-wpf-mainwindow"></a>設計簡單的 WPF MainWindow

1.  在 Visual Studio 程式碼編輯器中，選擇 [ **MainWindow.xaml** ] 索引標籤。

2.  如果未顯示 [工具箱] 視窗，請選擇 [檢視] 功能表，然後選擇 [工具箱]。

3.  將 **Button** 控制項和 **TextBox** 控制項加入 [MainWindow] 視窗。

4.  反白顯示 **TextBox** 控制項，並在 [屬性] 視窗中，設定下列值：

    -   將 [名稱] 屬性設定為 `resultsTextBox`。

    -   將 [高度] 屬性設為 250。

    -   將 [寬度] 屬性設為 500。

    -   在 [文字] 索引標籤上，指定等寬字型，例如 Lucida Console 或全域等寬。

5.  反白顯示 **Button** 控制項，並在 [屬性] 視窗中，設定下列值：

    -   將 [名稱] 屬性設定為 `startButton`。

    -   將 [內容] 屬性的值從 **Button** 變更為 **Start**。

6.  放置文字方塊和按鈕，使兩者都出現在 [MainWindow] 視窗中。

     如需 WPF XAML 設計工具的詳細資訊，請參閱[使用 XAML 設計工具建立 UI](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio)。

## <a name="add-a-reference"></a>加入參考

1.  在方案總管中，反白顯示您的專案名稱。

2.  在功能表列上，選擇 [專案]  >  [加入參考]。

     [參考管理員] 對話方塊隨即顯示。

3.  在對話方塊上方，請確認專案的目標是 .NET Framework 4.5 或更新版本。

4.  在 [組件] 分類中，選擇 [Framework] (如果尚未選擇)。

5.  在名稱清單中，選取 [System.Net.Http] 核取方塊。

6.  選擇 [確定] 按鈕以關閉對話方塊。

## <a name="add-necessary-using-directives"></a>加入必要的 using 指示詞

1.  在方案總管中，開啟 MainWindow.xaml.cs 的捷徑功能表，然後選擇 [檢視程式碼]。

2.  如果尚未顯示，請將下列 `using` 指示詞加入程式碼檔案頂端。

    ```csharp
    using System.Net.Http;
    using System.Net;
    using System.IO;
    ```

## <a name="create-a-synchronous-app"></a>建立同步應用程式

1.  在設計視窗 MainWindow.xaml 中，按兩下 [開始] 按鈕，以在 MainWindow.xaml.cs 中建立 `startButton_Click` 事件處理常式。

2.  在 MainWindow.xaml.cs 中，將下列程式碼複製到 `startButton_Click` 的內文：

    ```csharp
    resultsTextBox.Clear();
    SumPageSizes();
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";
    ```

    程式碼會呼叫方法，該方法會驅動應用程式 `SumPageSizes`，並且在控制項返回 `startButton_Click` 時顯示訊息。

3.  同步方案的程式碼包含下列四種方法：

    -   `SumPageSizes`，會從 `SetUpURLList` 取得網頁 URL 的清單，然後呼叫 `GetURLContents` 和 `DisplayResults` 以處理每個 URL。

    -   `SetUpURLList`，會製作並傳回網址清單。

    -   `GetURLContents`，會下載每個網站的內容，並傳回內容做為位元組陣列。

    -   `DisplayResults`，會顯示每個 URL 的位元組陣列中的位元組數目。

    複製下列四種方法，然後貼在 MainWindow.xaml.cs 的 `startButton_Click` 事件處理常式下方：

    ```csharp
    private void SumPageSizes()
    {
        // Make a list of web addresses.
        List<string> urlList = SetUpURLList();

        var total = 0;
        foreach (var url in urlList)
        {
            // GetURLContents returns the contents of url as a byte array.
            byte[] urlContents = GetURLContents(url);

            DisplayResults(url, urlContents);

            // Update the total.
            total += urlContents.Length;
        }

        // Display the total count for all of the web addresses.
        resultsTextBox.Text +=
            string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);
    }

    private List<string> SetUpURLList()
    {
        var urls = new List<string>
        {
            "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",
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

    private byte[] GetURLContents(string url)
    {
        // The downloaded resource ends up in the variable named content.
        var content = new MemoryStream();

        // Initialize an HttpWebRequest for the current URL.
        var webReq = (HttpWebRequest)WebRequest.Create(url);

        // Send the request to the Internet resource and wait for
        // the response.
        // Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.
        using (WebResponse response = webReq.GetResponse())
        {
            // Get the data stream that is associated with the specified URL.
            using (Stream responseStream = response.GetResponseStream())
            {
                // Read the bytes in responseStream and copy them to content.
                responseStream.CopyTo(content);
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
    ```

## <a name="test-the-synchronous-solution"></a>測試同步解決方案

選擇 **F5** 鍵以執行程式，然後選擇 [開始] 按鈕。

應該會顯示如下列清單的輸出：

```text
msdn.microsoft.com/library/windows/apps/br211380.aspx        383832
msdn.microsoft.com                                            33964
msdn.microsoft.com/library/hh290136.aspx               225793
msdn.microsoft.com/library/ee256749.aspx               143577
msdn.microsoft.com/library/hh290138.aspx               237372
msdn.microsoft.com/library/hh290140.aspx               128279
msdn.microsoft.com/library/dd470362.aspx               157649
msdn.microsoft.com/library/aa578028.aspx               204457
msdn.microsoft.com/library/ms404677.aspx               176405
msdn.microsoft.com/library/ff730837.aspx               143474

Total bytes returned:  1834802

Control returned to startButton_Click.
```

請注意，需要花費幾秒鐘以顯示計數。 在這段期間，在等候下載要求資源的同時，會封鎖 UI 執行緒。 如此一來，您就無法在選擇 [開始] 按鈕之後，移動、最大化、最小化，或甚至關閉顯示視窗。 這些努力會失敗，直到位元組計數開始出現為止。 如果網站沒有回應，也不會指出失敗的站台。 甚至難以停止等候以及關閉程式。

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a>將 GetURLContents 轉換為非同步方法

1.  若要將同步方案轉換成非同步方案，最佳的起點是在 `GetURLContents`，因為呼叫 <xref:System.Net.HttpWebRequest> 方法 <xref:System.Net.HttpWebRequest.GetResponse%2A> 及 <xref:System.IO.Stream> 方法 <xref:System.IO.Stream.CopyTo%2A> 是應用程式存取 Web 的位置。 .NET Framework 會讓轉換變得簡單，方法是提供這兩種方法的非同步版本。

     如需 `GetURLContents` 中所用之方法的詳細資訊，請參閱 <xref:System.Net.WebRequest>。

    > [!NOTE]
    > 當您依照本逐步解說中的步驟時，會出現數個編譯器錯誤。 您可以略過它們，並繼續進行本逐步解說。

     將在 `GetURLContents` 的第三行呼叫的方法從 `GetResponse` 變更為非同步、以工作為基礎的 <xref:System.Net.WebRequest.GetResponseAsync%2A> 方法。

    ```csharp
    using (WebResponse response = webReq.GetResponseAsync())
    ```

2.  `GetResponseAsync` 會傳回 <xref:System.Threading.Tasks.Task%601>。 在此情況下，工作傳回變數 `TResult` 具有類型 <xref:System.Net.WebResponse>。 工作承諾會在已下載要求的資料及工作執行完成之後，產生實際 `WebResponse` 物件。

     若要從工作擷取 `WebResponse` 值，請將 [await](../../../../csharp/language-reference/keywords/await.md) 運算子套用至 `GetResponseAsync` 的呼叫，如下列程式碼所示。

    ```csharp
    using (WebResponse response = await webReq.GetResponseAsync())
    ```

     `await` 運算子會暫停執行目前的 `GetURLContents` 方法，直到等候的工作完成為止。 同時，控制項會返回非同步方法的呼叫端。 在此範例中，目前方法是 `GetURLContents`，呼叫端是 `SumPageSizes`。 當工作完成時，承諾的 `WebResponse` 物件會以等候工作之值的形式產生，而且會指派給變數 `response`。

     前一個陳述式可分成下列兩個陳述式，以釐清會發生什麼情況。

    ```csharp
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();
    //using (WebResponse response = await responseTask)
    ```

     對 `webReq.GetResponseAsync` 的呼叫會傳回 `Task(Of WebResponse)` 或 `Task<WebResponse>`。 await 運算子會套用至工作以擷取 `WebResponse` 值。

     如果非同步方法有不需要依賴工作完成的工作要執行，此方法可以在呼叫非同步方法之後，以及套用 `await` 運算子之前，繼續這兩個陳述式之間的工作。 如需範例，請參閱[如何：使用 Async 和 Await，同時發出多個 Web 要求 (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) 以及[如何：使用 Task.WhenAll 擴充非同步逐步解說的內容 (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)。

3.  由於您在上一個步驟中加入 `await` 運算子，所以發生編譯器錯誤。 此運算子只能用於以 [async](../../../../csharp/language-reference/keywords/async.md) 修飾詞標示的方法。 當您重複轉換步驟以將對 `CopyTo` 的呼叫取代為對 `CopyToAsync` 的呼叫時，略過錯誤。

    -   變更方法的名稱，該方法會呼叫 <xref:System.IO.Stream.CopyToAsync%2A>。

    -   `CopyTo` 或 `CopyToAsync` 方法會將位元組複製到其引數，`content`，並不會傳回有意義的值。 在同步版本中，呼叫 `CopyTo` 是簡單的陳述式，不會傳回值。 非同步版本，`CopyToAsync`，傳回 <xref:System.Threading.Tasks.Task>。 工作函式，例如 "Task(void)"，讓方法等候。 將 `Await` 或 `await` 套用至對 `CopyToAsync` 的呼叫，如下列程式碼所示。

        ```csharp
        await responseStream.CopyToAsync(content);
        ```

         前一個陳述式縮寫下列兩行程式碼。

        ```csharp
        // CopyToAsync returns a Task, not a Task<T>.
        //Task copyTask = responseStream.CopyToAsync(content);

        // When copyTask is completed, content contains a copy of
        // responseStream.
        //await copyTask;
        ```

4.  `GetURLContents` 中還需要完成的工作是調整方法簽章。 您只能在以 [async](../../../../csharp/language-reference/keywords/async.md) 修飾詞標示的方法中使用 `await` 運算子。 新增修飾詞以將方法標示為「非同步方法」，如下列程式碼所示。

    ```csharp
    private async byte[] GetURLContents(string url)
    ```

5.  非同步方法的傳回類型在 C# 中只能是 <xref:System.Threading.Tasks.Task>、<xref:System.Threading.Tasks.Task%601> 或 `void`。 一般而言，`void` 的傳回型別只適用於非同步事件處理常式，其中 `void` 為必要項目。 在其他情況下，如果完成的方法有 [return](../../../../csharp/language-reference/keywords/return.md) 陳述式，則會傳回類型 T 的值，請使用 `Task(T)`；如果完成的方法不會傳回有意義的值，則使用 `Task`。 您可以將 `Task` 傳回類型想成是有意義的 "Task(void)"。

     如需詳細資訊，請參閱[非同步方法的傳回型別 (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)。

     方法 `GetURLContents` 有 return 陳述式，陳述式會傳回位元組陣列。 因此，非同步版本的傳回類型是 Task(T)，其中 T 是位元組陣列。 在方法簽章中進行下列變更：

    -   將傳回型別變更為 `Task<byte[]>`。

    -   依照慣例，非同步方法的名稱會以 "Async" 結尾，所以重新命名方法 `GetURLContentsAsync`。

     下列程式碼會顯示這些變更。

    ```csharp
    private async Task<byte[]> GetURLContentsAsync(string url)
    ```

     只要這幾個變更，`GetURLContents` 至非同步方法的轉換就能完成。

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a>將 SumPageSizes 轉換為非同步方法

1.  針對 `SumPageSizes` 重複上述程序的步驟。 首先，將對 `GetURLContents` 的呼叫變更為非同步呼叫。

    -   如果您尚未這麼做，請變更方法的名稱，該方法是從 `GetURLContents` 呼叫至 `GetURLContentsAsync`。

    -   將 `await` 套用至工作，`GetURLContentsAsync` 會傳回該工作以取得位元組陣列值。

     下列程式碼會顯示這些變更。

    ```csharp
    byte[] urlContents = await GetURLContentsAsync(url);
    ```

     前一個指派縮寫下列兩行程式碼。

    ```csharp
    // GetURLContentsAsync returns a Task<T>. At completion, the task
    // produces a byte array.
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
    //byte[] urlContents = await getContentsTask;
    ```

2.  在方法簽章中進行下列變更：

    -   以 `async` 修飾詞來標示方法。

    -   將 "Async" 加入至方法名稱。

    -   這次沒有任何工作傳回變數，T，因為 `SumPageSizesAsync` 並未傳回 T 的值。(這個方法沒有任何 `return` 陳述式)。不過，方法必須傳回 `Task` 才可以等候。 因此，請將方法的傳回型別從 `void` 變更為 `Task`。

    下列程式碼會顯示這些變更。

    ```csharp
    private async Task SumPageSizesAsync()
    ```

     `SumPageSizes` 至 `SumPageSizesAsync` 的轉換完成。

## <a name="convert-startbuttonclick-to-an-asynchronous-method"></a>將 startButton_Click 轉換為非同步方法

1.  如果您尚未這麼做，請在事件處理常式中，將呼叫方法的名稱從 `SumPageSizes` 變更為 `SumPageSizesAsync`。

2.  因為 `SumPageSizesAsync` 是非同步方法，在事件處理常式中變更程式碼以等候結果。

     對 `SumPageSizesAsync` 的呼叫會鏡射 `GetURLContentsAsync` 中對 `CopyToAsync` 的呼叫。 呼叫會傳回 `Task`，而不是 `Task(T)`。

     如同先前的程序，您可以使用一個陳述式或兩個陳述式轉換呼叫。 下列程式碼會顯示這些變更。

    ```csharp
    // One-step async call.
    await SumPageSizesAsync();

    // Two-step async call.
    //Task sumTask = SumPageSizesAsync();
    //await sumTask;
    ```

3.  若要避免不小心重新進入作業，請在 `startButton_Click` 頂端加入下列陳述式以停用 [開始] 按鈕。

    ```csharp
    // Disable the button until the operation is complete.
    startButton.IsEnabled = false;
    ```

     您可以在事件處理常式結尾重新啟用按鈕。

    ```csharp
    // Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = true;
    ```

     如需重新進入的詳細資訊，請參閱[處理非同步應用程式中的重新進入 (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md)。

4.  最後，將 `async` 修飾詞加入宣告，讓事件處理常式可以等候 `SumPagSizesAsync`。

    ```csharp
    private async void startButton_Click(object sender, RoutedEventArgs e)
    ```

     一般而言，事件處理常式的名稱並沒有改變。 因為事件處理常式必須傳回 `void`，所以傳回型別不會變更為 `Task`。

     專案從同步到非同步處理的轉換已完成。

## <a name="test-the-asynchronous-solution"></a>測試非同步解決方案

1.  選擇 **F5** 鍵以執行程式，然後選擇 [開始] 按鈕。

2.  類似同步方案的輸出應該會顯示。 但是，請注意下列差異。

    -   處理完成之後，結果不會同時發生。 例如，這兩個程式在 `startButton_Click` 中都包含程式碼行，會清除文字方塊。 此用意是在顯示一個結果集之後、二度選擇 [開始] 按鈕時，清除執行之間的文字方塊。 在同步版本中，當下載完成且 UI 執行緒可以執行其他工作時，會在第二次顯示計數之前，清除文字方塊。 在非同步版本中，會在您選擇 [開始] 按鈕之後，立即清除文字方塊。

    -   最重要的是，不會在下載期間封鎖 UI 執行緒。 您可以移動視窗或調整其大小，同時下載、計算及顯示 Web 資源。 如果其中一個網站變慢或沒有回應，您可以選擇 [關閉] 按鈕 (右上角紅色欄位中的 x)，取消作業。

## <a name="replace-method-geturlcontentsasync-with-a-net-framework-method"></a>將方法 GetURLContentsAsync 取代為 .NET Framework 方法

1.  .NET Framework 4.5 提供許多您可以使用的非同步方法。 其中一個方法 (<xref:System.Net.Http.HttpClient> 方法 <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>) 會執行這個逐步解說所需的工作。 您可以使用這個方法，而不是 `GetURLContentsAsync` 方法，這是您在先前的程序中建立的方法。

     第一個步驟是在方法 `SumPageSizesAsync` 中建立 `HttpClient` 物件。 在方法的開頭，加入下列宣告。

    ```csharp
    // Declare an HttpClient object and increase the buffer size. The
    // default buffer size is 65,536.
    HttpClient client =
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };
    ```

2.  在 `SumPageSizesAsync,` 中將對 `GetURLContentsAsync` 方法的呼叫取代為對 `HttpClient` 方法的呼叫。

    ```csharp
    byte[] urlContents = await client.GetByteArrayAsync(url);
    ```

3.  移除或取消註解您撰寫的 `GetURLContentsAsync` 方法。

4.  選擇 **F5** 鍵以執行程式，然後選擇 [開始] 按鈕。

     此版本之專案的行為應該符合「測試非同步方案」程序描述的行為，而且您只需要投入較少的精力。

## <a name="example-code"></a>範例程式碼

下列程式碼包含使用您撰寫的 `GetURLContentsAsync` 方法，從同步轉換為非同步方案的完整範例。 請注意，它極為類似原始的同步方案。

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

// Add the following using directives, and add a reference for System.Net.Http.
using System.Net.Http;
using System.IO;
using System.Net;

namespace AsyncExampleWPF
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // Disable the button until the operation is complete.
            startButton.IsEnabled = false;

            resultsTextBox.Clear();

            // One-step async call.
            await SumPageSizesAsync();

            // Two-step async call.
            //Task sumTask = SumPageSizesAsync();
            //await sumTask;

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";

            // Reenable the button in case you want to run the operation again.
            startButton.IsEnabled = true;
        }

        private async Task SumPageSizesAsync()
        {
            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            var total = 0;

            foreach (var url in urlList)
            {
                byte[] urlContents = await GetURLContentsAsync(url);

                // The previous line abbreviates the following two assignment statements.

                // GetURLContentsAsync returns a Task<T>. At completion, the task
                // produces a byte array.
                //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
                //byte[] urlContents = await getContentsTask;

                DisplayResults(url, urlContents);

                // Update the total.
                total += urlContents.Length;
            }
            // Display the total count for all of the websites.
            resultsTextBox.Text +=
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",
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

        private async Task<byte[]> GetURLContentsAsync(string url)
        {
            // The downloaded resource ends up in the variable named content.
            var content = new MemoryStream();

            // Initialize an HttpWebRequest for the current URL.
            var webReq = (HttpWebRequest)WebRequest.Create(url);

            // Send the request to the Internet resource and wait for
            // the response.
            using (WebResponse response = await webReq.GetResponseAsync())

            // The previous statement abbreviates the following two statements.

            //Task<WebResponse> responseTask = webReq.GetResponseAsync();
            //using (WebResponse response = await responseTask)
            {
                // Get the data stream that is associated with the specified url.
                using (Stream responseStream = response.GetResponseStream())
                {
                    // Read the bytes in responseStream and copy them to content.
                    await responseStream.CopyToAsync(content);

                    // The previous statement abbreviates the following two statements.

                    // CopyToAsync returns a Task, not a Task<T>.
                    //Task copyTask = responseStream.CopyToAsync(content);

                    // When copyTask is completed, content contains a copy of
                    // responseStream.
                    //await copyTask;
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

下列程式碼包含使用 `HttpClient` 方法 `GetByteArrayAsync` 之方案的完整範例。

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

// Add the following using directives, and add a reference for System.Net.Http.
using System.Net.Http;
using System.IO;
using System.Net;

namespace AsyncExampleWPF
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

            // Disable the button until the operation is complete.
            startButton.IsEnabled = false;

            // One-step async call.
            await SumPageSizesAsync();

            //// Two-step async call.
            //Task sumTask = SumPageSizesAsync();
            //await sumTask;

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";

            // Reenable the button in case you want to run the operation again.
            startButton.IsEnabled = true;
        }

        private async Task SumPageSizesAsync()
        {
            // Declare an HttpClient object and increase the buffer size. The
            // default buffer size is 65,536.
            HttpClient client =
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };

            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            var total = 0;

            foreach (var url in urlList)
            {
                // GetByteArrayAsync returns a task. At completion, the task
                // produces a byte array.
                byte[] urlContents = await client.GetByteArrayAsync(url);

                // The following two lines can replace the previous assignment statement.
                //Task<byte[]> getContentsTask = client.GetByteArrayAsync(url);
                //byte[] urlContents = await getContentsTask;

                DisplayResults(url, urlContents);

                // Update the total.
                total += urlContents.Length;
            }

            // Display the total count for all of the websites.
            resultsTextBox.Text +=
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",
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

## <a name="see-also"></a>另請參閱

- [Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) (非同步範例：存取 Web 逐步解說 (C# 和 Visual Basic))
- [async](../../../../csharp/language-reference/keywords/async.md)
- [await](../../../../csharp/language-reference/keywords/await.md)
- [使用 async 和 await 進行非同步程式設計 (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
- [非同步方法的傳回型別 (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)
- [Task-based Asynchronous Programming (TAP)](https://www.microsoft.com/en-us/download/details.aspx?id=19957) (以工作為基礎的非同步程式設計 (TAP))
- [如何：使用 Task.WhenAll 擴充非同步逐步解說的內容 (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [如何：使用 async 和 await，同時發出多個 Web 要求 (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
