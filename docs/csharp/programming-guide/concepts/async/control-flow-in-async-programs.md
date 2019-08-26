---
title: 非同步程式中的控制流程 (C#)
ms.date: 07/20/2015
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
ms.openlocfilehash: 8adf4bcf193d9fa8d7335996539933ce71282bac
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595857"
---
# <a name="control-flow-in-async-programs-c"></a>非同步程式中的控制流程 (C#)

您可以使用 `async` 和 `await` 關鍵字更輕鬆地撰寫和維護非同步程式。 不過，如果您不了解程式的運作方式，則結果可能會讓您大吃一驚。 本主題透過簡單非同步程式來追蹤控制流程，以顯示控制何時從某個方法移至另一個方法以及每次傳輸的資訊。

一般而言，您可以使用 [async (C#)](../../../language-reference/keywords/async.md) 修飾詞來標記包含非同步程式碼的方法。 在使用 async 修飾詞所標記的方法中，您可以使用 [await (C#)](../../../language-reference/keywords/await.md) 運算子來指定方法會暫停以等候被呼叫的非同步處理程序完成的位置。 如需詳細資訊，請參閱[使用 async 和 await 進行非同步程式設計 (C#)](./index.md)。

下列範例會使用非同步方法，將所指定網站的內容下載為字串，以及顯示字串的長度。 這個範例包含下列兩個方法。

- `startButton_Click`，其呼叫 `AccessTheWebAsync` 並顯示結果。

- `AccessTheWebAsync`，會將網站的內容下載為字串，並傳回字串的長度。 `AccessTheWebAsync`使用非同步的 <xref:System.Net.Http.HttpClient> 方法 <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> 來下載內容。

編號的顯示行會出現在程式中的策略點，協助您了解程式的執行方式，以及說明每個標記點所發生的情況。 顯示行會標上 "ONE" 到 "SIX"。 標籤代表程式到達這些程式碼行的順序。

下列程式碼示範程式的大綱。

```csharp
public partial class MainWindow : Window
{
    // . . .
    private async void startButton_Click(object sender, RoutedEventArgs e)
    {
        // ONE
        Task<int> getLengthTask = AccessTheWebAsync();

        // FOUR
        int contentLength = await getLengthTask;

        // SIX
        resultsTextBox.Text +=
            $"\r\nLength of the downloaded string: {contentLength}.\r\n";
    }

    async Task<int> AccessTheWebAsync()
    {
        // TWO
        HttpClient client = new HttpClient();
        Task<string> getStringTask =
            client.GetStringAsync("https://msdn.microsoft.com");

        // THREE
        string urlContents = await getStringTask;

        // FIVE
        return urlContents.Length;
    }
}
```

每個標記位置 "ONE" 到 "SIX" 都會顯示程式目前狀態的資訊。 會產生下列輸出：

```text
ONE:   Entering startButton_Click.
           Calling AccessTheWebAsync.

TWO:   Entering AccessTheWebAsync.
           Calling HttpClient.GetStringAsync.

THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.

FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.

FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.

SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.

Length of the downloaded string: 33946.
```

## <a name="set-up-the-program"></a>設定程式

您可以從 MSDN 下載本主題所使用的程式碼，也可以自行建置。

> [!NOTE]
> 若要執行範例，您必須在電腦上安裝 Visual Studio 2012 或更新版本以及 .NET Framework 4.5 或更新版本。

### <a name="download-the-program"></a>下載程式

您可以從[非同步範例：非同步程式中的控制流程](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)下載本主題的應用程式。 下列步驟會開啟和執行程式。

1. 解壓縮下載的檔案，然後啟動 Visual Studio。

2. 在功能表列上選擇 [檔案]   >  [開啟]   > [專案/解決方案]  。

3. 巡覽至保存解壓縮之範例程式碼的資料夾，並開啟方案 (.sln) 檔案，然後選擇 **F5** 鍵來建置和執行專案。

### <a name="create-the-program-yourself"></a>自行建立程式

下列 Windows Presentation Foundation (WPF) 專案包含本主題的程式碼範例。

若要執行專案，請執行下列步驟：

1. 啟動 Visual Studio。

2. 在功能表列上，選擇 [檔案]   > [新增]   > [專案]  。

     [ **新增專案** ] 對話方塊隨即開啟。

3. 選擇 [已安裝]   >  [Visual C#]   >  [Windows Desktop]  類別，然後從專案範本的清單中選擇 [WPF 應用程式]  。

4. 輸入 `AsyncTracer` 作為專案的名稱，然後選擇 [確定]  按鈕。

     新的專案隨即出現在方案總管  中。

5. 在 Visual Studio 程式碼編輯器中，選擇 [ **MainWindow.xaml** ] 索引標籤。

     如未顯示索引標籤，請在方案總管  中開啟 MainWindow.xaml 的捷徑功能表，然後選擇 [檢視程式碼]  。

6. 在 MainWindow.xaml 的 [XAML]  檢視中，以下列程式碼取代程式碼。

    ```csharp
    <Window
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" mc:Ignorable="d" x:Class="AsyncTracer.MainWindow"
            Title="Control Flow Trace" Height="350" Width="592">
        <Grid>
            <Button x:Name="startButton" Content="Start
    " HorizontalAlignment="Left" Margin="250,10,0,0" VerticalAlignment="Top" Width="75" Height="24"  Click="startButton_Click" d:LayoutOverrides="GridBox"/>
            <TextBox x:Name="resultsTextBox" HorizontalAlignment="Left" TextWrapping="Wrap" VerticalAlignment="Bottom" Width="576" Height="265" FontFamily="Lucida Console" FontSize="10" VerticalScrollBarVisibility="Visible" Grid.ColumnSpan="3"/>
        </Grid>
    </Window>
    ```

     包含文字方塊和按鈕的簡易視窗會出現在 MainWindow.xaml 的 [設計]  檢視中。

7. 加入 <xref:System.Net.Http> 的參考。

8. 在方案總管  中，開啟 MainWindow.xaml.cs 的捷徑功能表，然後選擇 [檢視程式碼]  。

9. 將 MainWindow.xaml.cs 中的程式碼更換為下列程式碼。

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

    // Add a using directive and a reference for System.Net.Http;
    using System.Net.Http;

    namespace AsyncTracer
    {
        public partial class MainWindow : Window
        {
            public MainWindow()
            {
                InitializeComponent();
            }

            private async void startButton_Click(object sender, RoutedEventArgs e)
            {
                // The display lines in the example lead you through the control shifts.
                resultsTextBox.Text += "ONE:   Entering startButton_Click.\r\n" +
                    "           Calling AccessTheWebAsync.\r\n";

                Task<int> getLengthTask = AccessTheWebAsync();

                resultsTextBox.Text += "\r\nFOUR:  Back in startButton_Click.\r\n" +
                    "           Task getLengthTask is started.\r\n" +
                    "           About to await getLengthTask -- no caller to return to.\r\n";

                int contentLength = await getLengthTask;

                resultsTextBox.Text += "\r\nSIX:   Back in startButton_Click.\r\n" +
                    "           Task getLengthTask is finished.\r\n" +
                    "           Result from AccessTheWebAsync is stored in contentLength.\r\n" +
                    "           About to display contentLength and exit.\r\n";

                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {contentLength}.\r\n";
            }

            async Task<int> AccessTheWebAsync()
            {
                resultsTextBox.Text += "\r\nTWO:   Entering AccessTheWebAsync.";

                // Declare an HttpClient object.
                HttpClient client = new HttpClient();

                resultsTextBox.Text += "\r\n           Calling HttpClient.GetStringAsync.\r\n";

                // GetStringAsync returns a Task<string>.
                Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");

                resultsTextBox.Text += "\r\nTHREE: Back in AccessTheWebAsync.\r\n" +
                    "           Task getStringTask is started.";

                // AccessTheWebAsync can continue to work until getStringTask is awaited.

                resultsTextBox.Text +=
                    "\r\n           About to await getStringTask and return a Task<int> to startButton_Click.\r\n";

                // Retrieve the website contents when task is complete.
                string urlContents = await getStringTask;

                resultsTextBox.Text += "\r\nFIVE:  Back in AccessTheWebAsync." +
                    "\r\n           Task getStringTask is complete." +
                    "\r\n           Processing the return statement." +
                    "\r\n           Exiting from AccessTheWebAsync.\r\n";

                return urlContents.Length;
            }
        }
    }
    ```

10. 選擇 **F5** 鍵以執行程式，然後選擇 [開始]  按鈕。

    即會出現下列輸出：

    ```text
    ONE:   Entering startButton_Click.
               Calling AccessTheWebAsync.

    TWO:   Entering AccessTheWebAsync.
               Calling HttpClient.GetStringAsync.

    THREE: Back in AccessTheWebAsync.
               Task getStringTask is started.
               About to await getStringTask & return a Task<int> to startButton_Click.

    FOUR:  Back in startButton_Click.
               Task getLengthTask is started.
               About to await getLengthTask -- no caller to return to.

    FIVE:  Back in AccessTheWebAsync.
               Task getStringTask is complete.
               Processing the return statement.
               Exiting from AccessTheWebAsync.

    SIX:   Back in startButton_Click.
               Task getLengthTask is finished.
               Result from AccessTheWebAsync is stored in contentLength.
               About to display contentLength and exit.

    Length of the downloaded string: 33946.
    ```

## <a name="trace-the-program"></a>追蹤程式

### <a name="steps-one-and-two"></a>步驟一和二

前兩個顯示當 `startButton_Click` 呼叫 `AccessTheWebAsync`，以及 `AccessTheWebAsync` 呼叫非同步 <xref:System.Net.Http.HttpClient> 方法 <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> 時，追蹤路徑的程式碼行。 下圖概述不同方法的呼叫。

![步驟一和二](./media/asynctrace-onetwo.png "AsyncTrace-ONETWO")

`AccessTheWebAsync` 和 `client.GetStringAsync` 傳回的類型都是 <xref:System.Threading.Tasks.Task%601>。 針對 `AccessTheWebAsync`，TResult 是整數。 針對 `GetStringAsync`，TResult 是字串。 如需非同步方法傳回型別的詳細資訊，請參閱[非同步方法的傳回型別 (C#)](./async-return-types.md)。

控制權返回呼叫端時，工作傳回非同步方法會傳回工作執行個體。 在被呼叫的方法中發現 `await` 運算子時，或被呼叫的方法結束時，控制權會從非同步方法返回其呼叫端。 標上 "THREE" 到 "SIX" 的顯示行會追蹤處理程序的這個部分。

### <a name="step-three"></a>步驟三

在 `AccessTheWebAsync` 中，呼叫非同步方法 <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> 以下載目標網頁的內容。 傳回 `client.GetStringAsync` 時，控制項會從 `client.GetStringAsync` 返回 `AccessTheWebAsync`。

 `client.GetStringAsync` 方法會傳回指派給 `AccessTheWebAsync` 中 `getStringTask` 變數的字串工作。 範例程式中的下行示範 `client.GetStringAsync` 呼叫和指派。

```csharp
Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");
```

 您可以透過 `client.GetStringAsync` 將工作視為承諾，最後產生實際字串。 同時，如果 `AccessTheWebAsync` 的工作未依存於來自 `client.GetStringAsync` 的承諾字串，則該工作可以在 `client.GetStringAsync` 等候時繼續進行。 在此範例中，下列數行的輸出 (標上 "THREE”) 代表執行獨立工作的機會。

```
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 下列陳述式會在等候 `getStringTask` 時暫止 `AccessTheWebAsync` 中的進度。

```csharp
string urlContents = await getStringTask;
```

 下圖顯示從 `client.GetStringAsync` 到指派給 `getStringTask` 以及從建立 `getStringTask` 到套用 await 運算子的控制流程。

 ![步驟三](./media/asynctrace-three.png "AsyncTrace-Three")

 除非傳回 `client.GetStringAsync`，否則 await 運算式會暫止 `AccessTheWebAsync`。 同時，控制項會返回 `AccessTheWebAsync` 的呼叫端 `startButton_Click`。

> [!NOTE]
> 一般而言，您會立即等候非同步方法呼叫。 例如，下列指派可以取代可建立後等候 `getStringTask` 的先前程式碼：`string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`
>
> 在本主題中，稍後會套用 await 運算子，以容納透過程式標記控制流程的輸出行。

### <a name="step-four"></a>步驟四

`AccessTheWebAsync` 的已宣告傳回型別為 `Task<int>`。 因此，暫止 `AccessTheWebAsync` 時，會將整數工作傳回給 `startButton_Click`。 您應該了解所傳回的工作不是 `getStringTask`。 傳回的工作是新整數工作，代表仍要在已暫止方法 `AccessTheWebAsync` 中執行的作業。 這個工作是來自 `AccessTheWebAsync` 的承諾，可在工作完成時產生整數。

下列陳述式會將這個工作指派給 `getLengthTask` 變數。

```csharp
Task<int> getLengthTask = AccessTheWebAsync();
```

 如同 `AccessTheWebAsync`，除非等候非同步工作 (`getLengthTask`)，否則 `startButton_Click` 可以繼續執行未依存於該工作結果的工作。 下列輸出行代表該工作。

```
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

 等候 `getLengthTask` 時，會暫止 `startButton_Click` 中的進度。 除非 `AccessTheWebAsync` 完成，否則下列指派陳述式會暫止 `startButton_Click`。

```csharp
int contentLength = await getLengthTask;
```

 在下圖中，除非等候 `getLengthTask`，否則箭頭會顯示從 `AccessTheWebAsync` 中的 await 運算式到將值指派給 `getLengthTask` (後接 `startButton_Click` 中的正常處理) 的控制流程。

 ![步驟四](./media/asynctrace-four.png "AsyncTrace-FOUR")

### <a name="step-five"></a>步驟五

`client.GetStringAsync` 指出完成時，會取消暫止 `AccessTheWebAsync` 中的處理，而且可以繼續略過 await 陳述式。 下列數行的輸出代表繼續處理。

```
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

 return 陳述式的運算元 `urlContents.Length` 儲存在 `AccessTheWebAsync` 所傳回的工作中。 await 運算式會從 `startButton_Click` 中的 `getLengthTask` 擷取該值。

 下圖顯示 `client.GetStringAsync` (和 `getStringTask`) 完成後的控制權轉移。

 ![步驟五](./media/asynctrace-five.png "AsyncTrace-FIVE")

 `AccessTheWebAsync` 會執行直到完成，而且控制項會返回正在等待完成的 `startButton_Click`。

### <a name="step-six"></a>步驟六

`AccessTheWebAsync` 指出完成時，會繼續略過 `startButton_Async` 中 await 陳述式的處理。 事實上，程式不需要再執行任何動作。

下列數行的輸出代表在 `startButton_Async` 中繼續處理：

```
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

 await 運算式會從 `getLengthTask` 擷取整數值，而整數值是 `AccessTheWebAsync` 中 return 陳述式的運算元。 下列陳述式會將該值指派給 `contentLength` 變數。

```csharp
int contentLength = await getLengthTask;
```

 下圖顯示從 `AccessTheWebAsync` 到 `startButton_Click` 的控制項返回。

 ![步驟六](./media/asynctrace-six.png "AsyncTrace-SIX")

## <a name="see-also"></a>另請參閱

- [使用 Async 和 Await 進行非同步程式設計 (C#)](./index.md)
- [非同步方法的傳回型別 (C#)](./async-return-types.md)
- [逐步解說：使用 Async 和 Await 存取 Web (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [非同步範例：非同步程式中的控制流程 (C# 和 Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
