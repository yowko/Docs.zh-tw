---
title: '取消 (c # ) 的工作清單'
description: 瞭解如何使用解除標記將取消要求告知工作清單。
ms.date: 08/19/2020
ms.topic: tutorial
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 84cd1bb413d20b6c13be8415c13c72b57873b1cf
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654701"
---
# <a name="cancel-a-list-of-tasks-c"></a><span data-ttu-id="3eb5c-103">取消 (c # ) 的工作清單</span><span class="sxs-lookup"><span data-stu-id="3eb5c-103">Cancel a list of tasks (C#)</span></span>

<span data-ttu-id="3eb5c-104">如果您不想等候它完成，您可以取消非同步主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="3eb5c-104">You can cancel an async console application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="3eb5c-105">依照本主題中的範例，您可以將取消新增至下載網站清單內容的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3eb5c-105">By following the example in this topic, you can add a cancellation to an application that downloads the contents of a list of websites.</span></span> <span data-ttu-id="3eb5c-106">您可以藉由將實例與每項工作產生關聯，來取消許多工 <xref:System.Threading.CancellationTokenSource> 具。</span><span class="sxs-lookup"><span data-stu-id="3eb5c-106">You can cancel many tasks by associating the <xref:System.Threading.CancellationTokenSource> instance with each task.</span></span> <span data-ttu-id="3eb5c-107">如果您選取 <kbd>Enter</kbd> 鍵，則會取消尚未完成的所有工作。</span><span class="sxs-lookup"><span data-stu-id="3eb5c-107">If you select the <kbd>Enter</kbd> key, you cancel all tasks that aren't yet complete.</span></span>

<span data-ttu-id="3eb5c-108">本教學課程涵蓋下列項目：</span><span class="sxs-lookup"><span data-stu-id="3eb5c-108">This tutorial covers:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="3eb5c-109">建立 .NET 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="3eb5c-109">Creating a .NET console application</span></span>
> - <span data-ttu-id="3eb5c-110">撰寫支援取消的非同步應用程式</span><span class="sxs-lookup"><span data-stu-id="3eb5c-110">Writing an async application that supports cancellation</span></span>
> - <span data-ttu-id="3eb5c-111">示範信號取消</span><span class="sxs-lookup"><span data-stu-id="3eb5c-111">Demonstrating signaling cancellation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3eb5c-112">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="3eb5c-112">Prerequisites</span></span>

<span data-ttu-id="3eb5c-113">本教學課程需要下列各項：</span><span class="sxs-lookup"><span data-stu-id="3eb5c-113">This tutorial requires the following:</span></span>

- [<span data-ttu-id="3eb5c-114">.NET 5.0 或更新版本的 SDK</span><span class="sxs-lookup"><span data-stu-id="3eb5c-114">.NET 5.0 or later SDK</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
- <span data-ttu-id="3eb5c-115">整合式開發環境 (IDE) </span><span class="sxs-lookup"><span data-stu-id="3eb5c-115">Integrated development environment (IDE)</span></span>
  - [<span data-ttu-id="3eb5c-116">建議 Visual Studio、Visual Studio Code 或 Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="3eb5c-116">We recommend Visual Studio, Visual Studio Code, or Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com)

### <a name="create-example-application"></a><span data-ttu-id="3eb5c-117">建立範例應用程式</span><span class="sxs-lookup"><span data-stu-id="3eb5c-117">Create example application</span></span>

<span data-ttu-id="3eb5c-118">建立新的 .NET Core 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="3eb5c-118">Create a new .NET Core console application.</span></span> <span data-ttu-id="3eb5c-119">您可以使用 [`dotnet new console`](../../../../core/tools/dotnet-new.md#console) 命令或從 [Visual Studio](/visualstudio/install/install-visual-studio)建立一個。</span><span class="sxs-lookup"><span data-stu-id="3eb5c-119">You can create one by using the [`dotnet new console`](../../../../core/tools/dotnet-new.md#console) command or from [Visual Studio](/visualstudio/install/install-visual-studio).</span></span> <span data-ttu-id="3eb5c-120">在您最愛的程式碼編輯器中開啟 *Program.cs* 檔案。</span><span class="sxs-lookup"><span data-stu-id="3eb5c-120">Open the *Program.cs* file in your favorite code editor.</span></span>

### <a name="replace-using-statements"></a><span data-ttu-id="3eb5c-121">取代 using 語句</span><span class="sxs-lookup"><span data-stu-id="3eb5c-121">Replace using statements</span></span>

<span data-ttu-id="3eb5c-122">將現有的 using 語句取代為這些宣告：</span><span class="sxs-lookup"><span data-stu-id="3eb5c-122">Replace the existing using statements with these declarations:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using System.Threading;
using System.Threading.Tasks;
```

## <a name="add-fields"></a><span data-ttu-id="3eb5c-123">新增欄位</span><span class="sxs-lookup"><span data-stu-id="3eb5c-123">Add fields</span></span>

<span data-ttu-id="3eb5c-124">在 `Program` 類別定義中，加入下列三個欄位：</span><span class="sxs-lookup"><span data-stu-id="3eb5c-124">In the `Program` class definition, add these three fields:</span></span>

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

<span data-ttu-id="3eb5c-125"><xref:System.Threading.CancellationTokenSource>用來向要求的取消發出信號 <xref:System.Threading.CancellationToken> 。</span><span class="sxs-lookup"><span data-stu-id="3eb5c-125">The <xref:System.Threading.CancellationTokenSource> is used to signal a requested cancellation to a <xref:System.Threading.CancellationToken>.</span></span> <span data-ttu-id="3eb5c-126">`HttpClient`會公開傳送 HTTP 要求和接收 HTTP 回應的能力。</span><span class="sxs-lookup"><span data-stu-id="3eb5c-126">The `HttpClient` exposes the ability to send HTTP requests and receive HTTP responses.</span></span> <span data-ttu-id="3eb5c-127">`s_urlList`會保存應用程式計畫處理的所有 url。</span><span class="sxs-lookup"><span data-stu-id="3eb5c-127">The `s_urlList` holds all of the URLs that the application plans to process.</span></span>

## <a name="update-application-entry-point"></a><span data-ttu-id="3eb5c-128">更新應用程式進入點</span><span class="sxs-lookup"><span data-stu-id="3eb5c-128">Update application entry point</span></span>

<span data-ttu-id="3eb5c-129">主控台應用程式的主要進入點是 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="3eb5c-129">The main entry point into the console application is the `Main` method.</span></span> <span data-ttu-id="3eb5c-130">以下列內容取代現有的方法：</span><span class="sxs-lookup"><span data-stu-id="3eb5c-130">Replace the existing method with the following:</span></span>

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

<span data-ttu-id="3eb5c-131">更新後的 `Main` 方法現在會被視為 [非同步 main](../../../whats-new/csharp-7-1.md#async-main)，以允許進入可執行檔的非同步進入點。</span><span class="sxs-lookup"><span data-stu-id="3eb5c-131">The updated `Main` method is now considered an [Async main](../../../whats-new/csharp-7-1.md#async-main), which allows for an asynchronous entry point into the executable.</span></span> <span data-ttu-id="3eb5c-132">它會將幾個教學訊息寫入主控台，然後宣告 <xref:System.Threading.Tasks.Task> 名為的實例 `cancelTask` ，以讀取主控台按鍵筆劃。</span><span class="sxs-lookup"><span data-stu-id="3eb5c-132">It writes a few instructional messages to the console, then declares a <xref:System.Threading.Tasks.Task> instance named `cancelTask`, which will read console key strokes.</span></span> <span data-ttu-id="3eb5c-133">如果按下 <kbd>Enter</kbd> 鍵， <xref:System.Threading.CancellationTokenSource.Cancel?displayProperty=nameWithType> 則會進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="3eb5c-133">If the <kbd>Enter</kbd> key is pressed, a call to <xref:System.Threading.CancellationTokenSource.Cancel?displayProperty=nameWithType> is made.</span></span> <span data-ttu-id="3eb5c-134">這會通知取消。</span><span class="sxs-lookup"><span data-stu-id="3eb5c-134">This will signal cancellation.</span></span> <span data-ttu-id="3eb5c-135">接下來， `sumPageSizesTask` 會從方法指派變數 `SumPageSizesAsync` 。</span><span class="sxs-lookup"><span data-stu-id="3eb5c-135">Next, the `sumPageSizesTask` variable is assigned from the `SumPageSizesAsync` method.</span></span> <span data-ttu-id="3eb5c-136">這兩項工作都會傳遞至 <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])?displayProperty=nameWithType> ，這兩項工作都已完成時，將會繼續進行。</span><span class="sxs-lookup"><span data-stu-id="3eb5c-136">Both tasks are then passed to <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])?displayProperty=nameWithType>, which will continue when any of the two tasks have completed.</span></span>

## <a name="create-the-asynchronous-sum-page-sizes-method"></a><span data-ttu-id="3eb5c-137">建立異步總和頁面大小方法</span><span class="sxs-lookup"><span data-stu-id="3eb5c-137">Create the asynchronous sum page sizes method</span></span>

<span data-ttu-id="3eb5c-138">在 `Main` 方法下方，新增 `SumPageSizesAsync` 方法：</span><span class="sxs-lookup"><span data-stu-id="3eb5c-138">Below the `Main` method, add the `SumPageSizesAsync` method:</span></span>

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

<span data-ttu-id="3eb5c-139">方法會從具現化和啟動開始 <xref:System.Diagnostics.Stopwatch> 。</span><span class="sxs-lookup"><span data-stu-id="3eb5c-139">The method starts by instantiating and starting a <xref:System.Diagnostics.Stopwatch>.</span></span> <span data-ttu-id="3eb5c-140">然後，它會在中的每個 URL 執行迴圈 `s_urlList` ，並呼叫 `ProcessUrlAsync` 。</span><span class="sxs-lookup"><span data-stu-id="3eb5c-140">It then loops through each URL in the `s_urlList` and calls `ProcessUrlAsync`.</span></span> <span data-ttu-id="3eb5c-141">在每個反復專案中， `s_cts.Token` 都會傳遞至方法，而程式碼會傳回 `ProcessUrlAsync` <xref:System.Threading.Tasks.Task%601> ，其中 `TResult` 是整數：</span><span class="sxs-lookup"><span data-stu-id="3eb5c-141">With each iteration, the `s_cts.Token` is passed into the `ProcessUrlAsync` method and the code returns a <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer:</span></span>

```csharp
int total = 0;
foreach (string url in s_urlList)
{
    int contentLength = await ProcessUrlAsync(url, s_client, s_cts.Token);
    total += contentLength;
}
```

## <a name="add-process-method"></a><span data-ttu-id="3eb5c-142">新增處理方法</span><span class="sxs-lookup"><span data-stu-id="3eb5c-142">Add process method</span></span>

<span data-ttu-id="3eb5c-143">`ProcessUrlAsync`在方法下方新增下列方法 `SumPageSizesAsync` ：</span><span class="sxs-lookup"><span data-stu-id="3eb5c-143">Add the following `ProcessUrlAsync` method below the `SumPageSizesAsync` method:</span></span>

```csharp
static async Task<int> ProcessUrlAsync(string url, HttpClient client, CancellationToken token)
{
    HttpResponseMessage response = await client.GetAsync(url, token);
    byte[] content = await response.Content.ReadAsByteArrayAsync();
    Console.WriteLine($"{url,-60} {content.Length,10:#,#}");

    return content.Length;
}
```

<span data-ttu-id="3eb5c-144">針對任何指定的 URL，方法會使用提供的實例，將 `client` 回應取得為 `byte[]` 。</span><span class="sxs-lookup"><span data-stu-id="3eb5c-144">For any given URL, the method will use the `client` instance provided to get the response as a `byte[]`.</span></span> <span data-ttu-id="3eb5c-145"><xref:System.Threading.CancellationToken>實例會傳遞至 <xref:System.Net.Http.HttpClient.GetAsync(System.String,System.Threading.CancellationToken)?displayProperty=nameWithType> 和 <xref:System.Net.Http.HttpContent.ReadAsByteArrayAsync?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="3eb5c-145">The <xref:System.Threading.CancellationToken> instance is passed into the <xref:System.Net.Http.HttpClient.GetAsync(System.String,System.Threading.CancellationToken)?displayProperty=nameWithType> and <xref:System.Net.Http.HttpContent.ReadAsByteArrayAsync?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="3eb5c-146">`token`用來註冊要求的取消。</span><span class="sxs-lookup"><span data-stu-id="3eb5c-146">The `token` is used to register for requested cancellation.</span></span> <span data-ttu-id="3eb5c-147">將 URL 和長度寫入主控台之後，會傳回長度。</span><span class="sxs-lookup"><span data-stu-id="3eb5c-147">The length is returned after the URL and length is written to the console.</span></span>

### <a name="example-application-output"></a><span data-ttu-id="3eb5c-148">範例應用程式輸出</span><span class="sxs-lookup"><span data-stu-id="3eb5c-148">Example application output</span></span>

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

## <a name="complete-example"></a><span data-ttu-id="3eb5c-149">完整範例</span><span class="sxs-lookup"><span data-stu-id="3eb5c-149">Complete example</span></span>

<span data-ttu-id="3eb5c-150">下列程式碼是範例 *Program.cs* 檔的完整文字。</span><span class="sxs-lookup"><span data-stu-id="3eb5c-150">The following code is the complete text of the *Program.cs* file for the example.</span></span>

:::code language="csharp" source="snippets/cancel-tasks/cancel-tasks/Program.cs":::

## <a name="see-also"></a><span data-ttu-id="3eb5c-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3eb5c-151">See also</span></span>

- <xref:System.Threading.CancellationToken>
- <xref:System.Threading.CancellationTokenSource>
- [<span data-ttu-id="3eb5c-152">使用 async 和 await 進行非同步程式設計 (c # ) </span><span class="sxs-lookup"><span data-stu-id="3eb5c-152">Asynchronous programming with async and await (C#)</span></span>](index.md)

## <a name="next-steps"></a><span data-ttu-id="3eb5c-153">後續步驟</span><span class="sxs-lookup"><span data-stu-id="3eb5c-153">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3eb5c-154">在一段時間後取消非同步工作 (C#)</span><span class="sxs-lookup"><span data-stu-id="3eb5c-154">Cancel async tasks after a period of time (C#)</span></span>](cancel-async-tasks-after-a-period-of-time.md)
