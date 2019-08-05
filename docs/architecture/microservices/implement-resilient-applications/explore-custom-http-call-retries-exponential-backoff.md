---
title: 使用指數輪詢探索自訂 HTTP 呼叫重試
description: 了解如何使用指數輪詢從頭開始實作 HTTP 呼叫重試，以處理可能發生的HTTP 失敗案例。
ms.date: 10/16/2018
ms.openlocfilehash: 2b40b73a014faa87d4eb42192c72b5a9b6c8d4fa
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68674705"
---
# <a name="explore-custom-http-call-retries-with-exponential-backoff"></a>使用指數輪詢探索自訂 HTTP 呼叫重試

若要建立具復原功能的微服務，您必須處理可能的 HTTP 失敗案例。 處理這些失敗的一種方式 (雖然不建議使用) 是使用指數輪詢建立您自己的重試實作。

**重要事項：** 此節將說明如何建立您自己的自訂程式碼來實作 HTTP 呼叫重試。 不過，不建議您自己做，而是使用功能更強大且可靠，同時使用方式更簡單的機制，例如，使用自 .NET Core 2.1 開始提供的 `HttpClientFactory` 搭配 Polly。 這些建議方法會在後續各節中說明。

一開始探索時，您可以使用指數輪詢的公用程式類別 (如 [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260) 中所示)，再加上如下程式碼，來實作自己的程式碼。

```csharp
public sealed class RetryWithExponentialBackoff
{
    private readonly int maxRetries, delayMilliseconds, maxDelayMilliseconds;

    public RetryWithExponentialBackoff(int maxRetries = 50,
        int delayMilliseconds = 200,
        int maxDelayMilliseconds = 2000)
    {
        this.maxRetries = maxRetries;
        this.delayMilliseconds = delayMilliseconds;
        this.maxDelayMilliseconds = maxDelayMilliseconds;
    }

    public async Task RunAsync(Func<Task> func)
    {
        ExponentialBackoff backoff = new ExponentialBackoff(this.maxRetries,
            this.delayMilliseconds,
            this.maxDelayMilliseconds);
        retry:
        try
        {
            await func();
        }
        catch (Exception ex) when (ex is TimeoutException ||
            ex is System.Net.Http.HttpRequestException)
        {
            Debug.WriteLine("Exception raised is: " +
                ex.GetType().ToString() +
                " –Message: " + ex.Message +
                " -- Inner Message: " +
                ex.InnerException.Message);
            await backoff.Delay();
            goto retry;
        }
    }
}

public struct ExponentialBackoff
{
    private readonly int m_maxRetries, m_delayMilliseconds, m_maxDelayMilliseconds;
    private int m_retries, m_pow;

    public ExponentialBackoff(int maxRetries, int delayMilliseconds,
        int maxDelayMilliseconds)
    {
        m_maxRetries = maxRetries;
        m_delayMilliseconds = delayMilliseconds;
        m_maxDelayMilliseconds = maxDelayMilliseconds;
        m_retries = 0;
        m_pow = 1;
    }

    public Task Delay()
    {
        if (m_retries == m_maxRetries)
        {
            throw new TimeoutException("Max retry attempts exceeded.");
        }
        ++m_retries;
        if (m_retries < 31)
        {
            m_pow = m_pow << 1; // m_pow = Pow(2, m_retries - 1)
        }
        int delay = Math.Min(m_delayMilliseconds * (m_pow - 1) / 2,
            m_maxDelayMilliseconds);
        return Task.Delay(delay);
    }
}
```

在用戶端 C\# 應用程式 (另一個 Web API 用戶端微服務、ASP.NET MVC 應用程式或甚至 C\# Xamarin 應用程式) 中使用此程式碼相當簡單。 下列範例示範如何使用 HttpClient 類別。

```csharp
public async Task<Catalog> GetCatalogItems(int page,int take, int? brand, int? type)
{
    _apiClient = new HttpClient();
    var itemsQs = $"items?pageIndex={page}&pageSize={take}";
    var filterQs = "";
    var catalogUrl = $"{_remoteServiceBaseUrl}items{filterQs}?pageIndex={page}&pageSize={take}";
    var dataString = "";
    //
    // Using HttpClient with Retry and Exponential Backoff
    //
    var retry = new RetryWithExponentialBackoff();
    await retry.RunAsync(async () =>
    {
        // work with HttpClient call
        dataString = await _apiClient.GetStringAsync(catalogUrl);
    });
    return JsonConvert.DeserializeObject<Catalog>(dataString);
}
```

請記住，此程式碼只適合作為概念證明。 後續各節說明如何使用 HttpClientFactory 這個縝密但使用方式更簡單的方法。 HttpClientFactory 自.NET Core 2.1 開始提供，它內含像 Polly 一樣經過實證的復原程式庫。

>[!div class="step-by-step"]
>[上一頁](implement-resilient-entity-framework-core-sql-connections.md)
>[下一頁](use-httpclientfactory-to-implement-resilient-http-requests.md)
