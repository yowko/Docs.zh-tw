---
title: 使用 Polly 以指數輪詢實作 HTTP 呼叫重試
description: 瞭解如何使用 Polly 和 IHttpClientFactory 處理 HTTP 失敗。
ms.date: 01/13/2021
ms.openlocfilehash: 8cffc644d73eaec5019e00c6a83de8635b569cde
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189046"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-ihttpclientfactory-and-polly-policies"></a>使用 IHttpClientFactory 和 Polly 原則以指數輪詢來執行 HTTP 呼叫重試

使用指數輪詢重試的建議方法是利用更進階的 .NET 程式庫，例如開放原始碼 [Polly 程式庫](https://github.com/App-vNext/Polly)。

Polly 是 .NET 程式庫，提供恢復功能和暫時性錯誤處理功能。 您可以藉由套用重試、斷路器、艙壁隔離 (Bulkhead Isolation)、逾時和後援等 Polly 原則，來實作這些功能。 Polly 目標 .NET Framework 4.x 和 .NET Standard 1.0、1.1 和 2.0 (可支援 .NET Core 和更新版本的) 。

下列步驟示範如何使用 Http 重試，並將 Polly 整合至 `IHttpClientFactory` ，這會在上一節中說明。

**參考 ASP.NET Core 3.1 套件**

`IHttpClientFactory` 自 .NET Core 2.1 起可供使用，但我們建議您在專案中使用 NuGet 的最新 ASP.NET Core 3.1 套件。 您通常也需要參考延伸模組套件 `Microsoft.Extensions.Http.Polly` 。

**在啟動時使用 Polly 的重試原則設定用戶端**

如先前章節所示，您必須在標準 Startup.ConfigureServices(...) 方法中定義具名或具類型的用戶端 HttpClient 組態，但現在您可以新增累加式程式碼，為使用指數輪詢的 Http 重試指定原則，如下所示：

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

**AddPolicyHandler()** 方法會將原則新增至您將使用的 `HttpClient` 物件。 在此情況下，它會使用指數輪詢來新增 Polly 的 Http 重試原則。

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

如果發生高並行和延展性以及高競爭的情況，定期重試原則可能會影響您的系統。 若要解決來自許多用戶端的類似重試因部分中斷而達到最高的問題，一個很好的解決方法是將 Jitter 策略新增至重試演算法/原則。 這可以透過將隨機性加入指數輪詢，來改善端對端系統的整體效能。 發生問題時，突然增加的情況會擴散。 下列範例將說明此原則：

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

Polly 透過專案網站提供可供生產的抖動演算法。

## <a name="additional-resources"></a>其他資源

- **重試模式**  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- **Polly 和 IHttpClientFactory**  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- **Polly (.NET 復原和暫時性錯誤處理程式庫)**  
  <https://github.com/App-vNext/Polly>

- **Polly：使用抖動重試**  
  <https://github.com/App-vNext/Polly/wiki/Retry-with-jitter>

- **Marc Brooker。抖動：利用隨機性讓事情更好**  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
>[上一個](use-httpclientfactory-to-implement-resilient-http-requests.md) 
>[下一步](implement-circuit-breaker-pattern.md)
