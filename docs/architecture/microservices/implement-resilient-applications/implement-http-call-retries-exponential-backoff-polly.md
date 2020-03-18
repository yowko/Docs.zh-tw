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
# <a name="implement-http-call-retries-with-exponential-backoff-with-ihttpclientfactory-and-polly-policies"></a>使用 IHttpClientFactory 和 Polly 策略實施具有指數級備份的 HTTP 調用重試

使用指數輪詢重試的建議方法是利用更進階的 .NET 程式庫，例如開放原始碼 [Polly 程式庫](https://github.com/App-vNext/Polly)。

Polly 是 .NET 程式庫，提供恢復功能和暫時性錯誤處理功能。 您可以藉由套用重試、斷路器、艙壁隔離 (Bulkhead Isolation)、逾時和後援等 Polly 原則，來實作這些功能。 Polly 目標 .NET 框架 4.x 和 .NET 標準 1.0、1.1 和 2.0（支援 .NET Core）。

以下步驟演示如何使用與 集成到 的`IHttpClientFactory`Polly 中的 Http 重試，這在前面一節中進行了說明。

**參考ASP.NET核心 3.1 套裝軟體**

`IHttpClientFactory`自 .NET Core 2.1 以來，我們建議您在專案中使用 NuGet 的最新ASP.NET酷睿 3.1 包。 您通常還需要引用擴展包`Microsoft.Extensions.Http.Polly`。

**在啟動時使用 Polly 的重試策略配置用戶端**

如先前章節所示，您必須在標準 Startup.ConfigureServices(...) 方法中定義具名或具類型的用戶端 HttpClient 組態，但現在您可以新增累加式程式碼，為使用指數輪詢的 Http 重試指定原則，如下所示：

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

**AddPolicyHandler()** 方法會將原則新增至您將使用的 `HttpClient` 物件。 在這種情況下，它添加了 Polly 的 Http Retries 策略，該策略具有指數級回退。

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

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a>將 Jitter 策略新增至重試原則

如果發生高並行和延展性以及高競爭的情況，定期重試原則可能會影響您的系統。 若要解決來自許多用戶端的類似重試因部分中斷而達到最高的問題，一個很好的解決方法是將 Jitter 策略新增至重試演算法/原則。 這可以透過將隨機性加入指數輪詢，來改善端對端系統的整體效能。 發生問題時，突然增加的情況會擴散。 以下示例說明了該原理：

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

Polly 通過專案網站提供生產就緒抖動演算法。

## <a name="additional-resources"></a>其他資源

- **重試模式**  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- **波利和IHttpClientFactory**  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- **Polly (.NET 復原和暫時性錯誤處理程式庫)**  
  <https://github.com/App-vNext/Polly>

- **波利：用抖動重試**  
  <https://github.com/App-vNext/Polly/wiki/Retry-with-jitter>

- **馬克·布魯克抖動：通過隨機性使事情變得更好**  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
>[上一個](use-httpclientfactory-to-implement-resilient-http-requests.md)
>[下一個](implement-circuit-breaker-pattern.md)
