---
title: 在非同步工作完成時進行處理
description: '這個範例會示範如何使用 c # 中的 System.threading.tasks.task.whenany 來啟動多個工作，並在其完成時處理其結果，而不是在開始順序中處理它們。'
ms.date: 08/19/2020
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: 520953eaf851dc82440e39b348aa4b246255e126
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557303"
---
# <a name="process-asynchronous-tasks-as-they-complete-c"></a><span data-ttu-id="4c3a1-103">在非同步工作完成時加以處理 (c # ) </span><span class="sxs-lookup"><span data-stu-id="4c3a1-103">Process asynchronous tasks as they complete (C#)</span></span>

<span data-ttu-id="4c3a1-104">藉由使用 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> ，您可以同時啟動多個工作，並在完成時逐一處理這些工作，而不是依照啟動的順序進行處理。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-104">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, you can start multiple tasks at the same time and process them one by one as they're completed rather than process them in the order in which they're started.</span></span>

<span data-ttu-id="4c3a1-105">下列範例使用查詢來建立工作集合。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-105">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="4c3a1-106">每項工作都會下載所指定網站的內容。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-106">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="4c3a1-107">在 while 迴圈的的每個反覆運算中，等候的 <xref:System.Threading.Tasks.Task.WhenAny%2A> 呼叫會先傳回完成其下載的工作集合中的工作。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-107">In each iteration of a while loop, an awaited call to <xref:System.Threading.Tasks.Task.WhenAny%2A> returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="4c3a1-108">該工作會從集合中予以移除，並進行處理。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-108">That task is removed from the collection and processed.</span></span> <span data-ttu-id="4c3a1-109">迴圈會重複進行，直到集合未包含其他工作為止。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-109">The loop repeats until the collection contains no more tasks.</span></span>

## <a name="create-example-application"></a><span data-ttu-id="4c3a1-110">建立範例應用程式</span><span class="sxs-lookup"><span data-stu-id="4c3a1-110">Create example application</span></span>

<span data-ttu-id="4c3a1-111">建立新的 .NET Core 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-111">Create a new .NET Core console application.</span></span> <span data-ttu-id="4c3a1-112">您可以使用 [ [dotnet 新主控台](../../../../core/tools/dotnet-new.md#console) ] 命令或從 [Visual Studio](/visualstudio/install/install-visual-studio)建立一個。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-112">You can create one by using the [dotnet new console](../../../../core/tools/dotnet-new.md#console) command or from [Visual Studio](/visualstudio/install/install-visual-studio).</span></span> <span data-ttu-id="4c3a1-113">在您最愛的程式碼編輯器中開啟 *Program.cs* 檔案。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-113">Open the *Program.cs* file in your favorite code editor.</span></span>

### <a name="replace-using-statements"></a><span data-ttu-id="4c3a1-114">取代 using 語句</span><span class="sxs-lookup"><span data-stu-id="4c3a1-114">Replace using statements</span></span>

<span data-ttu-id="4c3a1-115">將現有的 using 語句取代為這些宣告：</span><span class="sxs-lookup"><span data-stu-id="4c3a1-115">Replace the existing using statements with these declarations:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Linq;
using System.Net.Http;
using System.Threading.Tasks;
```

## <a name="add-fields"></a><span data-ttu-id="4c3a1-116">新增欄位</span><span class="sxs-lookup"><span data-stu-id="4c3a1-116">Add fields</span></span>

<span data-ttu-id="4c3a1-117">在 `Program` 類別定義中，新增下列兩個欄位：</span><span class="sxs-lookup"><span data-stu-id="4c3a1-117">In the `Program` class definition, add the following two fields:</span></span>

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

<span data-ttu-id="4c3a1-118">`HttpClient`會公開傳送 HTTP 要求和接收 HTTP 回應的能力。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-118">The `HttpClient` exposes the ability to send HTTP requests and receive HTTP responses.</span></span> <span data-ttu-id="4c3a1-119">`s_urlList`會保存應用程式計畫處理的所有 url。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-119">The `s_urlList` holds all of the URLs that the application plans to process.</span></span>

## <a name="update-application-entry-point"></a><span data-ttu-id="4c3a1-120">更新應用程式進入點</span><span class="sxs-lookup"><span data-stu-id="4c3a1-120">Update application entry point</span></span>

<span data-ttu-id="4c3a1-121">主控台應用程式的主要進入點是 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-121">The main entry point into the console application is the `Main` method.</span></span> <span data-ttu-id="4c3a1-122">以下列內容取代現有的方法：</span><span class="sxs-lookup"><span data-stu-id="4c3a1-122">Replace the existing method with the following:</span></span>

```csharp
static Task Main() => SumPageSizesAsync();
```

<span data-ttu-id="4c3a1-123">更新後的 `Main` 方法現在會被視為 [非同步 main](../../../whats-new/csharp-7-1.md#async-main)，以允許進入可執行檔的非同步進入點。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-123">The updated `Main` method is now considered an [Async main](../../../whats-new/csharp-7-1.md#async-main), which allows for an asynchronous entry point into the executable.</span></span> <span data-ttu-id="4c3a1-124">它是以的呼叫表示 `SumPageSizesAsync` 。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-124">It is expressed a call to `SumPageSizesAsync`.</span></span>

## <a name="create-the-asynchronous-sum-page-sizes-method"></a><span data-ttu-id="4c3a1-125">建立異步總和頁面大小方法</span><span class="sxs-lookup"><span data-stu-id="4c3a1-125">Create the asynchronous sum page sizes method</span></span>

<span data-ttu-id="4c3a1-126">在 `Main` 方法下方，新增 `SumPageSizesAsync` 方法：</span><span class="sxs-lookup"><span data-stu-id="4c3a1-126">Below the `Main` method, add the `SumPageSizesAsync` method:</span></span>

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

<span data-ttu-id="4c3a1-127">方法會從具現化和啟動開始 <xref:System.Diagnostics.Stopwatch> 。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-127">The method starts by instantiating and starting a <xref:System.Diagnostics.Stopwatch>.</span></span> <span data-ttu-id="4c3a1-128">然後，它會包含一個查詢，該查詢會在執行時建立一組工作。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-128">It then includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="4c3a1-129">下列程式碼中的每個 `ProcessUrlAsync` 呼叫都會傳回 `TResult` 為整數的 <xref:System.Threading.Tasks.Task%601>：</span><span class="sxs-lookup"><span data-stu-id="4c3a1-129">Each call to `ProcessUrlAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer:</span></span>

```csharp
IEnumerable<Task<int>> downloadTasksQuery =
    from url in s_urlList
    select ProcessUrlAsync(url, s_client);
```

<span data-ttu-id="4c3a1-130">由於使用 LINQ [延後執行](../../../../standard/linq/deferred-execution-example.md) ，因此您會呼叫 <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 以啟動每項工作。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-130">Due to [deferred execution](../../../../standard/linq/deferred-execution-example.md) with the LINQ, you call <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> to start each task.</span></span>

```csharp
List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
```

<span data-ttu-id="4c3a1-131">`while`迴圈會針對集合中的每個工作執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="4c3a1-131">The `while` loop performs the following steps for each task in the collection:</span></span>

1. <span data-ttu-id="4c3a1-132">等候的呼叫， `WhenAny` 以識別集合中已完成其下載的第一個工作。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-132">Awaits a call to `WhenAny` to identify the first task in the collection that has finished its download.</span></span>

    ```csharp
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);
    ```

1. <span data-ttu-id="4c3a1-133">從集合中移除該工作。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-133">Removes that task from the collection.</span></span>

    ```csharp
    downloadTasks.Remove(firstFinishedTask);
    ```

1. <span data-ttu-id="4c3a1-134">等候 `ProcessUrlAsync` 呼叫所傳回的 `finishedTask`。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-134">Awaits `finishedTask`, which is returned by a call to `ProcessUrlAsync`.</span></span> <span data-ttu-id="4c3a1-135">`finishedTask` 變數是 <xref:System.Threading.Tasks.Task%601>，其中 `TResult` 是整數。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-135">The `finishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span> <span data-ttu-id="4c3a1-136">工作已完成，但您等候它擷取所下載網站的長度，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-136">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span> <span data-ttu-id="4c3a1-137">如果工作發生錯誤， `await` 將會擲回儲存在中的第一個子例外狀況，而不 `AggregateException` 像讀取 <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> 屬性，它會擲回 `AggregateException` 。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-137">If the task is faulted, `await` will throw the first child exception stored in the `AggregateException`, unlike reading the <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> property, which would throw the `AggregateException`.</span></span>

    ```csharp
    total += await finishedTask;
    ```

## <a name="add-process-method"></a><span data-ttu-id="4c3a1-138">新增處理方法</span><span class="sxs-lookup"><span data-stu-id="4c3a1-138">Add process method</span></span>

<span data-ttu-id="4c3a1-139">`ProcessUrlAsync`在方法下方新增下列方法 `SumPageSizesAsync` ：</span><span class="sxs-lookup"><span data-stu-id="4c3a1-139">Add the following `ProcessUrlAsync` method below the `SumPageSizesAsync` method:</span></span>

```csharp
static async Task<int> ProcessUrlAsync(string url, HttpClient client)
{
    byte[] content = await client.GetByteArrayAsync(url);
    Console.WriteLine($"{url,-60} {content.Length,10:#,#}");

    return content.Length;
}
```

<span data-ttu-id="4c3a1-140">針對任何指定的 URL，方法會使用提供的實例，將 `client` 回應取得為 `byte[]` 。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-140">For any given URL, the method will use the `client` instance provided to get the response as a `byte[]`.</span></span> <span data-ttu-id="4c3a1-141">將 URL 和長度寫入主控台之後，會傳回長度。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-141">The length is returned after the URL and length is written to the console.</span></span>

<span data-ttu-id="4c3a1-142">執行程式數次，確認所下載的長度不一定會以相同的順序出現。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-142">Run the program several times to verify that the downloaded lengths don't always appear in the same order.</span></span>

> [!CAUTION]
> <span data-ttu-id="4c3a1-143">您可以如這個範例所述在迴圈中使用 `WhenAny`，以解決牽涉到少量工作的問題。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-143">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="4c3a1-144">不過，如果您有大量的工作要處理，其他方法會更有效率。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-144">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="4c3a1-145">如需詳細資訊和範例，請參閱 [Processing tasks as they complete](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete) (在工作完成時加以處理)。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-145">For more information and examples, see [Processing tasks as they complete](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete).</span></span>

## <a name="complete-example"></a><span data-ttu-id="4c3a1-146">完整範例</span><span class="sxs-lookup"><span data-stu-id="4c3a1-146">Complete example</span></span>

<span data-ttu-id="4c3a1-147">下列程式碼是範例 *Program.cs* 檔的完整文字。</span><span class="sxs-lookup"><span data-stu-id="4c3a1-147">The following code is the complete text of the *Program.cs* file for the example.</span></span>

:::code language="csharp" source="snippets/multiple-tasks/Program.cs":::

## <a name="see-also"></a><span data-ttu-id="4c3a1-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c3a1-148">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="4c3a1-149">使用 async 和 await 進行非同步程式設計 (c # ) </span><span class="sxs-lookup"><span data-stu-id="4c3a1-149">Asynchronous programming with async and await (C#)</span></span>](index.md)
