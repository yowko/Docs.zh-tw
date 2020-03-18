---
title: 使用 Polly 以指數輪詢實作 HTTP 呼叫重試
description: 瞭解如何使用 Polly 和 IHttpClientFactory 處理 HTTP 故障。
ms.date: 03/03/2020
ms.openlocfilehash: 49396dd545a05699278254474c77acf1483e0e0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846792"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-ihttpclientfactory-and-polly-policies"></a><span data-ttu-id="9a2be-103">使用 IHttpClientFactory 和 Polly 策略實施具有指數級備份的 HTTP 調用重試</span><span class="sxs-lookup"><span data-stu-id="9a2be-103">Implement HTTP call retries with exponential backoff with IHttpClientFactory and Polly policies</span></span>

<span data-ttu-id="9a2be-104">使用指數輪詢重試的建議方法是利用更進階的 .NET 程式庫，例如開放原始碼 [Polly 程式庫](https://github.com/App-vNext/Polly)。</span><span class="sxs-lookup"><span data-stu-id="9a2be-104">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open-source [Polly library](https://github.com/App-vNext/Polly).</span></span>

<span data-ttu-id="9a2be-105">Polly 是 .NET 程式庫，提供恢復功能和暫時性錯誤處理功能。</span><span class="sxs-lookup"><span data-stu-id="9a2be-105">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="9a2be-106">您可以藉由套用重試、斷路器、艙壁隔離 (Bulkhead Isolation)、逾時和後援等 Polly 原則，來實作這些功能。</span><span class="sxs-lookup"><span data-stu-id="9a2be-106">You can implement those capabilities by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="9a2be-107">Polly 目標 .NET 框架 4.x 和 .NET 標準 1.0、1.1 和 2.0（支援 .NET Core）。</span><span class="sxs-lookup"><span data-stu-id="9a2be-107">Polly targets .NET Framework 4.x and .NET Standard 1.0, 1.1, and 2.0 (which supports .NET Core).</span></span>

<span data-ttu-id="9a2be-108">以下步驟演示如何使用與 集成到 的`IHttpClientFactory`Polly 中的 Http 重試，這在前面一節中進行了說明。</span><span class="sxs-lookup"><span data-stu-id="9a2be-108">The following steps show how you can use Http retries with Polly integrated into `IHttpClientFactory`, which is explained in the previous section.</span></span>

<span data-ttu-id="9a2be-109">**參考ASP.NET核心 3.1 套裝軟體**</span><span class="sxs-lookup"><span data-stu-id="9a2be-109">**Reference the ASP.NET Core 3.1 packages**</span></span>

<span data-ttu-id="9a2be-110">`IHttpClientFactory`自 .NET Core 2.1 以來，我們建議您在專案中使用 NuGet 的最新ASP.NET酷睿 3.1 包。</span><span class="sxs-lookup"><span data-stu-id="9a2be-110">`IHttpClientFactory` is available since .NET Core 2.1 however we recommend you to use the latest ASP.NET Core 3.1 packages from NuGet in your project.</span></span> <span data-ttu-id="9a2be-111">您通常還需要引用擴展包`Microsoft.Extensions.Http.Polly`。</span><span class="sxs-lookup"><span data-stu-id="9a2be-111">You typically also need to reference the extension package `Microsoft.Extensions.Http.Polly`.</span></span>

<span data-ttu-id="9a2be-112">**在啟動時使用 Polly 的重試策略配置用戶端**</span><span class="sxs-lookup"><span data-stu-id="9a2be-112">**Configure a client with Polly's Retry policy, in Startup**</span></span>

<span data-ttu-id="9a2be-113">如先前章節所示，您必須在標準 Startup.ConfigureServices(...) 方法中定義具名或具類型的用戶端 HttpClient 組態，但現在您可以新增累加式程式碼，為使用指數輪詢的 Http 重試指定原則，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9a2be-113">As shown in previous sections, you need to define a named or typed client HttpClient configuration in your standard Startup.ConfigureServices(...) method, but now, you add incremental code specifying the policy for the Http retries with exponential backoff, as below:</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

<span data-ttu-id="9a2be-114">**AddPolicyHandler()** 方法會將原則新增至您將使用的 `HttpClient` 物件。</span><span class="sxs-lookup"><span data-stu-id="9a2be-114">The **AddPolicyHandler()** method is what adds policies to the `HttpClient` objects you'll use.</span></span> <span data-ttu-id="9a2be-115">在這種情況下，它添加了 Polly 的 Http Retries 策略，該策略具有指數級回退。</span><span class="sxs-lookup"><span data-stu-id="9a2be-115">In this case, it's adding a Polly's policy for Http Retries with exponential backoff.</span></span>

<span data-ttu-id="9a2be-116">為了有更模組化的方法，可在 `Startup.cs` 檔案內的個別方法中定義 Http 重試原則，如以下程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="9a2be-116">To have a more modular approach, the Http Retry Policy can be defined in a separate method within the `Startup.cs` file, as shown in the following code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2,
                                                                    retryAttempt)));
}
```

<span data-ttu-id="9a2be-117">透過 Polly，您可以定義重試原則，其中包含重試次數、指數輪詢組態，以及發生 HTTP 例外狀況時所要採取的動作，例如記錄錯誤。</span><span class="sxs-lookup"><span data-stu-id="9a2be-117">With Polly, you can define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there's an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="9a2be-118">在本例中，會設定原則，以便使用指數重試嘗試六次，一開始每隔兩秒。</span><span class="sxs-lookup"><span data-stu-id="9a2be-118">In this case, the policy is configured to try six times with an exponential retry, starting at two seconds.</span></span>

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="9a2be-119">將 Jitter 策略新增至重試原則</span><span class="sxs-lookup"><span data-stu-id="9a2be-119">Add a jitter strategy to the retry policy</span></span>

<span data-ttu-id="9a2be-120">如果發生高並行和延展性以及高競爭的情況，定期重試原則可能會影響您的系統。</span><span class="sxs-lookup"><span data-stu-id="9a2be-120">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="9a2be-121">若要解決來自許多用戶端的類似重試因部分中斷而達到最高的問題，一個很好的解決方法是將 Jitter 策略新增至重試演算法/原則。</span><span class="sxs-lookup"><span data-stu-id="9a2be-121">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="9a2be-122">這可以透過將隨機性加入指數輪詢，來改善端對端系統的整體效能。</span><span class="sxs-lookup"><span data-stu-id="9a2be-122">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="9a2be-123">發生問題時，突然增加的情況會擴散。</span><span class="sxs-lookup"><span data-stu-id="9a2be-123">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="9a2be-124">以下示例說明了該原理：</span><span class="sxs-lookup"><span data-stu-id="9a2be-124">The principle is illustrated by the following example:</span></span>

```csharp
Random jitterer = new Random();
var retryWithJitterPolicy = HttpPolicyExtensions
    .HandleTransientHttpError()
    .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
    .WaitAndRetryAsync(6,    // exponential back-off plus some jitter
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                      + TimeSpan.FromMilliseconds(jitterer.Next(0, 100))
    );
```

<span data-ttu-id="9a2be-125">Polly 通過專案網站提供生產就緒抖動演算法。</span><span class="sxs-lookup"><span data-stu-id="9a2be-125">Polly provides production-ready jitter algorithms via the project website.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="9a2be-126">其他資源</span><span class="sxs-lookup"><span data-stu-id="9a2be-126">Additional resources</span></span>

- <span data-ttu-id="9a2be-127">**重試模式**</span><span class="sxs-lookup"><span data-stu-id="9a2be-127">**Retry pattern**</span></span>  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- <span data-ttu-id="9a2be-128">**波利和IHttpClientFactory**</span><span class="sxs-lookup"><span data-stu-id="9a2be-128">**Polly and IHttpClientFactory**</span></span>  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- <span data-ttu-id="9a2be-129">**Polly (.NET 復原和暫時性錯誤處理程式庫)**</span><span class="sxs-lookup"><span data-stu-id="9a2be-129">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <https://github.com/App-vNext/Polly>

- <span data-ttu-id="9a2be-130">**波利：用抖動重試**</span><span class="sxs-lookup"><span data-stu-id="9a2be-130">**Polly: Retry with Jitter**</span></span>  
  <https://github.com/App-vNext/Polly/wiki/Retry-with-jitter>

- <span data-ttu-id="9a2be-131">**馬克·布魯克抖動：通過隨機性使事情變得更好**</span><span class="sxs-lookup"><span data-stu-id="9a2be-131">**Marc Brooker. Jitter: Making Things Better With Randomness**</span></span>  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
><span data-ttu-id="9a2be-132">[上一個](use-httpclientfactory-to-implement-resilient-http-requests.md)
>[下一個](implement-circuit-breaker-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="9a2be-132">[Previous](use-httpclientfactory-to-implement-resilient-http-requests.md)
[Next](implement-circuit-breaker-pattern.md)</span></span>
