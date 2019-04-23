---
title: 使用 Polly 以指數輪詢實作 HTTP 呼叫重試
description: 了解如何使用 Polly 和 HttpClientFactory 處理 HTTP 失敗。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: d031ca9b7c46f02cd9e22ae91fb20f281ebb47a2
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612052"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a><span data-ttu-id="6876b-103">使用 HttpClientFactory 和 Polly 原則以指數輪詢實作 HTTP 呼叫重試</span><span class="sxs-lookup"><span data-stu-id="6876b-103">Implement HTTP call retries with exponential backoff with HttpClientFactory and Polly policies</span></span>

<span data-ttu-id="6876b-104">使用指數輪詢重試的建議方法是利用更進階的 .NET 程式庫，例如開放原始碼 [Polly 程式庫](https://github.com/App-vNext/Polly)。</span><span class="sxs-lookup"><span data-stu-id="6876b-104">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open-source [Polly library](https://github.com/App-vNext/Polly).</span></span>

<span data-ttu-id="6876b-105">Polly 是 .NET 程式庫，提供恢復功能和暫時性錯誤處理功能。</span><span class="sxs-lookup"><span data-stu-id="6876b-105">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="6876b-106">您可以藉由套用重試、斷路器、艙壁隔離 (Bulkhead Isolation)、逾時和後援等 Polly 原則，來實作這些功能。</span><span class="sxs-lookup"><span data-stu-id="6876b-106">You can implement those capabilities by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="6876b-107">Polly 以 .NET 4.x 和 .NET Standard Library 1.0 (其支援 .NET Core) 為目標。</span><span class="sxs-lookup"><span data-stu-id="6876b-107">Polly targets .NET 4.x and the .NET Standard Library 1.0 (which supports .NET Core).</span></span>

<span data-ttu-id="6876b-108">不過，使用 Polly 的程式庫搭配您自己的自訂程式碼和 HttpClient 可能相當複雜。</span><span class="sxs-lookup"><span data-stu-id="6876b-108">However, using Polly’s library with your own custom code with HttpClient can be significantly complex.</span></span> <span data-ttu-id="6876b-109">在 eShopOnContainers 的原始版本中，已有採用 Polly 的 [ResilientHttpClient 建置組塊](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/Resilience/Resilience.Http/ResilientHttpClient.cs)。</span><span class="sxs-lookup"><span data-stu-id="6876b-109">In the original version of eShopOnContainers, there was a [ResilientHttpClient building-block](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/Resilience/Resilience.Http/ResilientHttpClient.cs) based on Polly.</span></span> <span data-ttu-id="6876b-110">但發行 HttpClientFactory 之後，具復原功能的 Http 通訊已變得更容易實作，因此 eShopOnContainers 中的建置組塊已被取代。</span><span class="sxs-lookup"><span data-stu-id="6876b-110">But with the release of HttpClientFactory, resilient Http communication has become much simpler to implement, so that building-block was deprecated from eShopOnContainers.</span></span> 

<span data-ttu-id="6876b-111">下列步驟示範如何透過整合到 HttpClientFactory 中的 Polly 使用 Http 重試，如上一節所述。</span><span class="sxs-lookup"><span data-stu-id="6876b-111">The following steps show how you can use Http retries with Polly integrated into HttpClientFactory, which is explained in the previous section.</span></span>

<span data-ttu-id="6876b-112">**參考 ASP.NET Core 2.2 套件**</span><span class="sxs-lookup"><span data-stu-id="6876b-112">**Reference the ASP.NET Core 2.2 packages**</span></span>

<span data-ttu-id="6876b-113">自.NET Core 2.1 後提供 `HttpClientFactory`不過建議您在專案中使用 NuGet 中的最新 ASP.NET Core 2.2 套件。</span><span class="sxs-lookup"><span data-stu-id="6876b-113">`HttpClientFactory` is available since .NET Core 2.1 however we recommend you to use the latest ASP.NET Core 2.2 packages from NuGet in your project.</span></span> <span data-ttu-id="6876b-114">您通常需要 `AspNetCore` 中繼套件，以及延伸模組套件 `Microsoft.Extensions.Http.Polly`。</span><span class="sxs-lookup"><span data-stu-id="6876b-114">You typically need the `AspNetCore` metapackage, and the extension package `Microsoft.Extensions.Http.Polly`.</span></span>

<span data-ttu-id="6876b-115">**在啟動時，使用 Polly 的重試原則來設定用戶端**</span><span class="sxs-lookup"><span data-stu-id="6876b-115">**Configure a client with Polly’s Retry policy, in Startup**</span></span>

<span data-ttu-id="6876b-116">如先前章節所示，您必須在標準 Startup.ConfigureServices(...) 方法中定義具名或具類型的用戶端 HttpClient 組態，但現在您可以新增累加式程式碼，為使用指數輪詢的 Http 重試指定原則，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6876b-116">As shown in previous sections, you need to define a named or typed client HttpClient configuration in your standard Startup.ConfigureServices(...) method, but now, you add incremental code specifying the policy for the Http retries with exponential backoff, as below:</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

<span data-ttu-id="6876b-117">**AddPolicyHandler()** 方法會將原則新增至您將使用的 `HttpClient` 物件。</span><span class="sxs-lookup"><span data-stu-id="6876b-117">The **AddPolicyHandler()** method is what adds policies to the `HttpClient` objects you'll use.</span></span> <span data-ttu-id="6876b-118">在此案例中，它會為使用指數輪詢的 HTTP 重試新增 Polly 原則。</span><span class="sxs-lookup"><span data-stu-id="6876b-118">In this case, it's adding a Polly’s policy for Http Retries with exponential backoff.</span></span>

<span data-ttu-id="6876b-119">為了有更模組化的方法，可在 `Startup.cs` 檔案內的個別方法中定義 Http 重試原則，如以下程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="6876b-119">To have a more modular approach, the Http Retry Policy can be defined in a separate method within the `Startup.cs` file, as shown in the following code:</span></span>

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

<span data-ttu-id="6876b-120">透過 Polly，您可以定義重試原則，其中包含重試次數、指數輪詢組態，以及發生 HTTP 例外狀況時所要採取的動作，例如記錄錯誤。</span><span class="sxs-lookup"><span data-stu-id="6876b-120">With Polly, you can define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there's an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="6876b-121">在本例中，會設定原則，以便使用指數重試嘗試六次，一開始每隔兩秒。</span><span class="sxs-lookup"><span data-stu-id="6876b-121">In this case, the policy is configured to try six times with an exponential retry, starting at two seconds.</span></span> 

<span data-ttu-id="6876b-122">因此，它會嘗試六次，而且每次重試的間隔秒數會是指數，一開始每隔兩秒。</span><span class="sxs-lookup"><span data-stu-id="6876b-122">so it will try six times and the seconds between each retry will be exponential, starting on two seconds.</span></span>

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="6876b-123">將 Jitter 策略新增至重試原則</span><span class="sxs-lookup"><span data-stu-id="6876b-123">Add a jitter strategy to the retry policy</span></span>

<span data-ttu-id="6876b-124">如果發生高並行和延展性以及高競爭的情況，定期重試原則可能會影響您的系統。</span><span class="sxs-lookup"><span data-stu-id="6876b-124">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="6876b-125">若要解決來自許多用戶端的類似重試因部分中斷而達到最高的問題，一個很好的解決方法是將 Jitter 策略新增至重試演算法/原則。</span><span class="sxs-lookup"><span data-stu-id="6876b-125">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="6876b-126">這可以透過將隨機性加入指數輪詢，來改善端對端系統的整體效能。</span><span class="sxs-lookup"><span data-stu-id="6876b-126">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="6876b-127">發生問題時，突然增加的情況會擴散。</span><span class="sxs-lookup"><span data-stu-id="6876b-127">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="6876b-128">使用簡單的 Polly 原則時，要實作 Jitter 的程式碼可能會如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="6876b-128">When you use a plain Polly policy, code to implement jitter could look like the following example:</span></span>

```csharp
Random jitterer = new Random(); 
Policy
  .Handle<HttpResponseException>() // etc
  .WaitAndRetry(5,    // exponential back-off plus some jitter
      retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                    + TimeSpan.FromMilliseconds(jitterer.Next(0, 100)) 
  );
```

## <a name="additional-resources"></a><span data-ttu-id="6876b-129">其他資源</span><span class="sxs-lookup"><span data-stu-id="6876b-129">Additional resources</span></span>

- <span data-ttu-id="6876b-130">**重試模式**\\</span><span class="sxs-lookup"><span data-stu-id="6876b-130">**Retry pattern**\\</span></span>
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- <span data-ttu-id="6876b-131">**Polly 和 HttpClientFactory**\\</span><span class="sxs-lookup"><span data-stu-id="6876b-131">**Polly and HttpClientFactory**\\</span></span>
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- <span data-ttu-id="6876b-132">**Polly (.NET 復原和暫時性錯誤處理程式庫)**\\</span><span class="sxs-lookup"><span data-stu-id="6876b-132">**Polly (.NET resilience and transient-fault-handling library)**\\</span></span>
  <https://github.com/App-vNext/Polly>

- <span data-ttu-id="6876b-133">**Marc Brooker：Jitter:利用隨機性更臻完美**\\</span><span class="sxs-lookup"><span data-stu-id="6876b-133">**Marc Brooker. Jitter: Making Things Better With Randomness**\\</span></span>
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
><span data-ttu-id="6876b-134">[上一頁](explore-custom-http-call-retries-exponential-backoff.md)
>[下一頁](implement-circuit-breaker-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="6876b-134">[Previous](explore-custom-http-call-retries-exponential-backoff.md)
[Next](implement-circuit-breaker-pattern.md)</span></span>
