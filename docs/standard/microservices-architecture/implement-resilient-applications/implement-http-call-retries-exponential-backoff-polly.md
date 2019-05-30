---
title: 使用 Polly 以指數輪詢實作 HTTP 呼叫重試
description: 了解如何使用 Polly 和 HttpClientFactory 處理 HTTP 失敗。
ms.date: 01/07/2019
ms.openlocfilehash: 9ffb0d918dc2efdc41d6c2db2e2141d14061b687
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053107"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a>使用 HttpClientFactory 和 Polly 原則以指數輪詢實作 HTTP 呼叫重試

使用指數輪詢重試的建議方法是利用更進階的 .NET 程式庫，例如開放原始碼 [Polly 程式庫](https://github.com/App-vNext/Polly)。

Polly 是 .NET 程式庫，提供恢復功能和暫時性錯誤處理功能。 您可以藉由套用重試、斷路器、艙壁隔離 (Bulkhead Isolation)、逾時和後援等 Polly 原則，來實作這些功能。 Polly 以 .NET 4.x 和 .NET Standard Library 1.0 (其支援 .NET Core) 為目標。

不過，使用 Polly 的程式庫搭配您自己的自訂程式碼和 HttpClient 可能相當複雜。 在 eShopOnContainers 的原始版本中，已有採用 Polly 的 [ResilientHttpClient 建置組塊](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10)。 但自從發行 [HttpClientFactory](use-httpclientfactory-to-implement-resilient-http-requests.md) 後，具復原性的 HTTP 通訊已變得更容易實作，因此 eShopOnContainers 中的建置組塊已遭淘汰。 

下列步驟示範如何透過整合到 HttpClientFactory 中的 Polly 使用 Http 重試，如上一節所述。

**參考 ASP.NET Core 2.2 套件**

自.NET Core 2.1 後提供 `HttpClientFactory`不過建議您在專案中使用 NuGet 中的最新 ASP.NET Core 2.2 套件。 您通常需要 `AspNetCore` 中繼套件，以及延伸模組套件 `Microsoft.Extensions.Http.Polly`。

**在啟動時，使用 Polly 的重試原則來設定用戶端**

如先前章節所示，您必須在標準 Startup.ConfigureServices(...) 方法中定義具名或具類型的用戶端 HttpClient 組態，但現在您可以新增累加式程式碼，為使用指數輪詢的 Http 重試指定原則，如下所示：

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

**AddPolicyHandler()** 方法會將原則新增至您將使用的 `HttpClient` 物件。 在此案例中，它會為使用指數輪詢的 HTTP 重試新增 Polly 原則。

為了有更模組化的方法，可在 `Startup.cs` 檔案內的個別方法中定義 Http 重試原則，如以下程式碼所示：

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

透過 Polly，您可以定義重試原則，其中包含重試次數、指數輪詢組態，以及發生 HTTP 例外狀況時所要採取的動作，例如記錄錯誤。 在本例中，會設定原則，以便使用指數重試嘗試六次，一開始每隔兩秒。 

因此，它會嘗試六次，而且每次重試的間隔秒數會是指數，一開始每隔兩秒。

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a>將 Jitter 策略新增至重試原則

如果發生高並行和延展性以及高競爭的情況，定期重試原則可能會影響您的系統。 若要解決來自許多用戶端的類似重試因部分中斷而達到最高的問題，一個很好的解決方法是將 Jitter 策略新增至重試演算法/原則。 這可以透過將隨機性加入指數輪詢，來改善端對端系統的整體效能。 發生問題時，突然增加的情況會擴散。 使用簡單的 Polly 原則時，要實作 Jitter 的程式碼可能會如下列範例所示：

```csharp
Random jitterer = new Random(); 
Policy
  .Handle<HttpResponseException>() // etc
  .WaitAndRetry(5,    // exponential back-off plus some jitter
      retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                    + TimeSpan.FromMilliseconds(jitterer.Next(0, 100)) 
  );
```

## <a name="additional-resources"></a>其他資源

- **重試模式**\
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- **Polly 和 HttpClientFactory**\
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- **Polly (.NET 復原和暫時性錯誤處理程式庫)**\
  <https://github.com/App-vNext/Polly>

- **Marc Brooker：Jitter:利用隨機性更臻完美**\
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
>[上一頁](explore-custom-http-call-retries-exponential-backoff.md)
>[下一頁](implement-circuit-breaker-pattern.md)
