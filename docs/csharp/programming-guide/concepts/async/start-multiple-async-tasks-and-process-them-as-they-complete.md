---
title: 在非同步工作完成時進行處理
description: '這個範例會示範如何使用 c # 中的 System.threading.tasks.task.whenany 來啟動多個工作，並在其完成時處理其結果，而不是在開始順序中處理它們。'
ms.date: 08/19/2020
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: 860e94a9c3973ce56e7321741a1136f752aa3d18
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2020
ms.locfileid: "91805235"
---
# <a name="process-asynchronous-tasks-as-they-complete-c"></a>在非同步工作完成時加以處理 (c # ) 

藉由使用 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> ，您可以同時啟動多個工作，並在完成時逐一處理這些工作，而不是依照啟動的順序進行處理。

下列範例使用查詢來建立工作集合。 每項工作都會下載所指定網站的內容。 在 while 迴圈的的每個反覆運算中，等候的 <xref:System.Threading.Tasks.Task.WhenAny%2A> 呼叫會先傳回完成其下載的工作集合中的工作。 該工作會從集合中予以移除，並進行處理。 迴圈會重複進行，直到集合未包含其他工作為止。

## <a name="create-example-application"></a>建立範例應用程式

建立新的 .NET Core 主控台應用程式。 您可以使用 [ [dotnet 新主控台](../../../../core/tools/dotnet-new.md#console) ] 命令或從 [Visual Studio](/visualstudio/install/install-visual-studio)建立一個。 在您最愛的程式碼編輯器中開啟 *Program.cs* 檔案。

### <a name="replace-using-statements"></a>取代 using 語句

將現有的 using 語句取代為這些宣告：

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Linq;
using System.Net.Http;
using System.Threading.Tasks;
```

## <a name="add-fields"></a>新增欄位

在 `Program` 類別定義中，新增下列兩個欄位：

```csharp
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

`HttpClient`會公開傳送 HTTP 要求和接收 HTTP 回應的能力。 `s_urlList`會保存應用程式計畫處理的所有 url。

## <a name="update-application-entry-point"></a>更新應用程式進入點

主控台應用程式的主要進入點是 `Main` 方法。 以下列內容取代現有的方法：

```csharp
static Task Main() => SumPageSizesAsync();
```

更新後的 `Main` 方法現在會被視為 [非同步 main](../../../whats-new/csharp-7.md#async-main)，以允許進入可執行檔的非同步進入點。 它是以的呼叫表示 `SumPageSizesAsync` 。

## <a name="create-the-asynchronous-sum-page-sizes-method"></a>建立異步總和頁面大小方法

在 `Main` 方法下方，新增 `SumPageSizesAsync` 方法：

```csharp
static async Task SumPageSizesAsync()
{
    var stopwatch = Stopwatch.StartNew();

    IEnumerable<Task<int>> downloadTasksQuery =
        from url in s_urlList
        select ProcessUrlAsync(url, s_client);

    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();

    int total = 0;
    while (downloadTasks.Any())
    {
        Task<int> finishedTask = await Task.WhenAny(downloadTasks);
        downloadTasks.Remove(finishedTask);
        total += await finishedTask;
    }

    stopwatch.Stop();

    Console.WriteLine($"\nTotal bytes returned:  {total:#,#}");
    Console.WriteLine($"Elapsed time:          {stopwatch.Elapsed}\n");
}
```

方法會從具現化和啟動開始 <xref:System.Diagnostics.Stopwatch> 。 然後，它會包含一個查詢，該查詢會在執行時建立一組工作。 下列程式碼中的每個 `ProcessUrlAsync` 呼叫都會傳回 `TResult` 為整數的 <xref:System.Threading.Tasks.Task%601>：

```csharp
IEnumerable<Task<int>> downloadTasksQuery =
    from url in s_urlList
    select ProcessUrlAsync(url, s_client);
```

由於使用 LINQ [延後執行](../../../../standard/linq/deferred-execution-example.md) ，因此您會呼叫 <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 以啟動每項工作。

```csharp
List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
```

`while`迴圈會針對集合中的每個工作執行下列步驟：

1. 等候的呼叫， `WhenAny` 以識別集合中已完成其下載的第一個工作。

    ```csharp
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);
    ```

1. 從集合中移除該工作。

    ```csharp
    downloadTasks.Remove(firstFinishedTask);
    ```

1. 等候 `ProcessUrlAsync` 呼叫所傳回的 `finishedTask`。 `finishedTask` 變數是 <xref:System.Threading.Tasks.Task%601>，其中 `TResult` 是整數。 工作已完成，但您等候它擷取所下載網站的長度，如下列範例所示。 如果工作發生錯誤， `await` 將會擲回儲存在中的第一個子例外狀況，而不 `AggregateException` 像讀取 <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> 屬性，它會擲回 `AggregateException` 。

    ```csharp
    total += await finishedTask;
    ```

## <a name="add-process-method"></a>新增處理方法

`ProcessUrlAsync`在方法下方新增下列方法 `SumPageSizesAsync` ：

```csharp
static async Task<int> ProcessUrlAsync(string url, HttpClient client)
{
    byte[] content = await client.GetByteArrayAsync(url);
    Console.WriteLine($"{url,-60} {content.Length,10:#,#}");

    return content.Length;
}
```

針對任何指定的 URL，方法會使用提供的實例，將 `client` 回應取得為 `byte[]` 。 將 URL 和長度寫入主控台之後，會傳回長度。

執行程式數次，確認所下載的長度不一定會以相同的順序出現。

> [!CAUTION]
> 您可以如這個範例所述在迴圈中使用 `WhenAny`，以解決牽涉到少量工作的問題。 不過，如果您有大量的工作要處理，其他方法會更有效率。 如需詳細資訊和範例，請參閱 [Processing tasks as they complete](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete) (在工作完成時加以處理)。

## <a name="complete-example"></a>完整範例

下列程式碼是範例 *Program.cs* 檔的完整文字。

:::code language="csharp" source="snippets/multiple-tasks/Program.cs":::

## <a name="see-also"></a>請參閱

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [使用 async 和 await 進行非同步程式設計 (c # ) ](index.md)
