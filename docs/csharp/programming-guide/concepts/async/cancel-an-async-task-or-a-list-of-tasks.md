---
title: '取消 (c # ) 的工作清單'
description: 瞭解如何使用解除標記將取消要求告知工作清單。
ms.date: 08/19/2020
ms.topic: tutorial
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 30bef5d1a5082fbd3757377dbedb8f9b9d17e218
ms.sourcegitcommit: 2560a355c76b0a04cba0d34da870df9ad94ceca3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2020
ms.locfileid: "89053089"
---
# <a name="cancel-a-list-of-tasks-c"></a>取消 (c # ) 的工作清單

如果您不想等候它完成，您可以取消非同步主控台應用程式。 依照本主題中的範例，您可以將取消新增至下載網站清單內容的應用程式。 您可以藉由將實例與每項工作產生關聯，來取消許多工 <xref:System.Threading.CancellationTokenSource> 具。 如果您選取 <kbd>Enter</kbd> 鍵，則會取消尚未完成的所有工作。

本教學課程涵蓋下列項目：

> [!div class="checklist"]
>
> - 建立 .NET 主控台應用程式
> - 撰寫支援取消的非同步應用程式
> - 示範信號取消

## <a name="prerequisites"></a>必要條件

本教學課程需要下列各項：

- [.NET 5.0 或更新版本的 SDK](https://dotnet.microsoft.com/download/dotnet/5.0)
- 整合式開發環境 (IDE) 
  - [建議 Visual Studio、Visual Studio Code 或 Visual Studio for Mac](https://visualstudio.microsoft.com)

### <a name="create-example-application"></a>建立範例應用程式

建立新的 .NET Core 主控台應用程式。 您可以使用 [`dotnet new console`](../../../../core/tools/dotnet-new.md#console) 命令或從 [Visual Studio](/visualstudio/install/install-visual-studio)建立一個。 在您最愛的程式碼編輯器中開啟 *Program.cs* 檔案。

### <a name="replace-using-statements"></a>取代 using 語句

將現有的 using 語句取代為這些宣告：

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using System.Threading;
using System.Threading.Tasks;
```

## <a name="add-fields"></a>新增欄位

在 `Program` 類別定義中，加入下列三個欄位：

```csharp
static readonly CancellationTokenSource s_cts = new CancellationTokenSource();

static readonly HttpClient s_client = new HttpClient
{
    MaxResponseContentBufferSize = 1_000_000
};

static readonly IEnumerable<string> s_urlList = new string[]
{
    "https://docs.microsoft.com",
    "https://docs.microsoft.com/aspnet/core",
    "https://docs.microsoft.com/azure",
    "https://docs.microsoft.com/azure/devops",
    "https://docs.microsoft.com/dotnet",
    "https://docs.microsoft.com/dynamics365",
    "https://docs.microsoft.com/education",
    "https://docs.microsoft.com/enterprise-mobility-security",
    "https://docs.microsoft.com/gaming",
    "https://docs.microsoft.com/graph",
    "https://docs.microsoft.com/microsoft-365",
    "https://docs.microsoft.com/office",
    "https://docs.microsoft.com/powershell",
    "https://docs.microsoft.com/sql",
    "https://docs.microsoft.com/surface",
    "https://docs.microsoft.com/system-center",
    "https://docs.microsoft.com/visualstudio",
    "https://docs.microsoft.com/windows",
    "https://docs.microsoft.com/xamarin"
};
```

<xref:System.Threading.CancellationTokenSource>用來向要求的取消發出信號 <xref:System.Threading.CancellationToken> 。 `HttpClient`會公開傳送 HTTP 要求和接收 HTTP 回應的能力。 `s_urlList`會保存應用程式計畫處理的所有 url。

## <a name="update-application-entry-point"></a>更新應用程式進入點

主控台應用程式的主要進入點是 `Main` 方法。 以下列內容取代現有的方法：

```csharp
static async Task Main()
{
    Console.WriteLine("Application started.");
    Console.WriteLine("Press the ENTER key to cancel...\n");

    Task cancelTask = Task.Run(() =>
    {
        while (Console.ReadKey().Key != ConsoleKey.Enter)
        {
            Console.WriteLine("Press the ENTER key to cancel...");
        }

        Console.WriteLine("\nENTER key pressed: cancelling downloads.\n");
        s_cts.Cancel();
    });

    Task sumPageSizesTask = SumPageSizesAsync();

    await Task.WhenAny(new[] { cancelTask, sumPageSizesTask });

    Console.WriteLine("Application ending.");
}
```

更新後的 `Main` 方法現在會被視為 [非同步 main](../../../whats-new/csharp-7-1.md#async-main)，以允許進入可執行檔的非同步進入點。 它會將幾個教學訊息寫入主控台，然後宣告 <xref:System.Threading.Tasks.Task> 名為的實例 `cancelTask` ，以讀取主控台按鍵筆劃。 如果按下 <kbd>Enter</kbd> 鍵， <xref:System.Threading.CancellationTokenSource.Cancel?displayProperty=nameWithType> 則會進行呼叫。 這會通知取消。 接下來， `sumPageSizesTask` 會從方法指派變數 `SumPageSizesAsync` 。 這兩項工作都會傳遞至 <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])?displayProperty=nameWithType> ，這兩項工作都已完成時，將會繼續進行。

## <a name="create-the-asynchronous-sum-page-sizes-method"></a>建立異步總和頁面大小方法

在 `Main` 方法下方，新增 `SumPageSizesAsync` 方法：

```csharp
static async Task SumPageSizesAsync()
{
    var stopwatch = Stopwatch.StartNew();

    int total = 0;
    foreach (string url in s_urlList)
    {
        int contentLength = await ProcessUrlAsync(url, s_client, s_cts.Token);
        total += contentLength;
    }

    stopwatch.Stop();

    Console.WriteLine($"\nTotal bytes returned:  {total:#,#}");
    Console.WriteLine($"Elapsed time:          {stopwatch.Elapsed}\n");
}
```

方法會從具現化和啟動開始 <xref:System.Diagnostics.Stopwatch> 。 然後，它會在中的每個 URL 執行迴圈 `s_urlList` ，並呼叫 `ProcessUrlAsync` 。 在每個反復專案中， `s_cts.Token` 都會傳遞至方法，而程式碼會傳回 `ProcessUrlAsync` <xref:System.Threading.Tasks.Task%601> ，其中 `TResult` 是整數：

```csharp
int total = 0;
foreach (string url in s_urlList)
{
    int contentLength = await ProcessUrlAsync(url, s_client, s_cts.Token);
    total += contentLength;
}
```

## <a name="add-process-method"></a>新增處理方法

`ProcessUrlAsync`在方法下方新增下列方法 `SumPageSizesAsync` ：

```csharp
static async Task<int> ProcessUrlAsync(string url, HttpClient client, CancellationToken token)
{
    HttpResponseMessage response = await client.GetAsync(url, token);
    byte[] content = await response.Content.ReadAsByteArrayAsync(token);
    Console.WriteLine($"{url,-60} {content.Length,10:#,#}");

    return content.Length;
}
```

針對任何指定的 URL，方法會使用提供的實例，將 `client` 回應取得為 `byte[]` 。 <xref:System.Threading.CancellationToken>實例會傳遞至 <xref:System.Net.Http.HttpClient.GetAsync(System.String,System.Threading.CancellationToken)?displayProperty=nameWithType> 和 <xref:System.Net.Http.HttpContent.ReadAsByteArrayAsync(System.Threading.CancellationToken)?displayProperty=nameWithType> 方法。 `token`用來註冊要求的取消。 將 URL 和長度寫入主控台之後，會傳回長度。

### <a name="example-application-output"></a>範例應用程式輸出

```console
Application started.
Press the ENTER key to cancel...

https://docs.microsoft.com                                       37,357
https://docs.microsoft.com/aspnet/core                           85,589
https://docs.microsoft.com/azure                                398,939
https://docs.microsoft.com/azure/devops                          73,663
https://docs.microsoft.com/dotnet                                67,452
https://docs.microsoft.com/dynamics365                           48,582
https://docs.microsoft.com/education                             22,924

ENTER key pressed: cancelling downloads.

Application ending.
```

## <a name="complete-example"></a>完整範例

下列程式碼是範例 *Program.cs* 檔的完整文字。

:::code language="csharp" source="snippets/cancel-tasks/cancel-tasks/Program.cs":::

## <a name="see-also"></a>另請參閱

- <xref:System.Threading.CancellationToken>
- <xref:System.Threading.CancellationTokenSource>
- [使用 async 和 await 進行非同步程式設計 (c # ) ](index.md)

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [在一段時間後取消非同步工作 (C#)](cancel-async-tasks-after-a-period-of-time.md)
