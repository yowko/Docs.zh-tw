---
title: 使用指數輪詢來實作自訂 HTTP 呼叫重試
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 使用指數輪詢來實作自訂 HTTP 呼叫重試
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 77663f193b5f788ee07eba001306caed764ed253
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104775"
---
# <a name="implementing-custom-http-call-retries-with-exponential-backoff"></a><span data-ttu-id="f9db7-103">使用指數輪詢來實作自訂 HTTP 呼叫重試</span><span class="sxs-lookup"><span data-stu-id="f9db7-103">Implementing custom HTTP call retries with exponential backoff</span></span>

<span data-ttu-id="f9db7-104">若要建立具有恢復功能的微服務，您必須處理可能的 HTTP 失敗案例。</span><span class="sxs-lookup"><span data-stu-id="f9db7-104">In order to create resilient microservices, you need to handle possible HTTP failure scenarios.</span></span> <span data-ttu-id="f9db7-105">基於這個目的，您可以建立自己的實作來使用指數輪詢重試。</span><span class="sxs-lookup"><span data-stu-id="f9db7-105">For that purpose, you could create your own implementation of retries with exponential backoff.</span></span>

<span data-ttu-id="f9db7-106">除了處理時態性資源無法使用的情況，指數輪詢也必須考慮到雲端提供者可能會為了避免使用量超載，而對資源可用性進行節流處理。</span><span class="sxs-lookup"><span data-stu-id="f9db7-106">In addition to handling temporal resource unavailability, the exponential backoff also needs to take into account that the cloud provider might throttle availability of resources to prevent usage overload.</span></span> <span data-ttu-id="f9db7-107">例如，雲端提供者可能會將太快建立太多連接要求視為拒絕服務 ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) 的攻擊。</span><span class="sxs-lookup"><span data-stu-id="f9db7-107">For example, creating too many connection requests very quickly might be viewed as a Denial of Service ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) attack by the cloud provider.</span></span> <span data-ttu-id="f9db7-108">因此，您需要提供一個機制，在遇到容量閾值時相應減少連接要求。</span><span class="sxs-lookup"><span data-stu-id="f9db7-108">As a result, you need to provide a mechanism to scale back connection requests when a capacity threshold has been encountered.</span></span>

<span data-ttu-id="f9db7-109">一開始探索時，您可以實作自己的程式碼來包含指數輪詢的公用程式類別，如 [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260) 中所示，再加上類似如下的程式碼 ([GitHub 儲存機制](https://gist.github.com/CESARDELATORRE/d80c6423a1aebaffaf387469f5194f5b)中也有提供)。</span><span class="sxs-lookup"><span data-stu-id="f9db7-109">As an initial exploration, you could implement your own code with a utility class for exponential backoff as in [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260), plus code like the following (which is also available on a [GitHub repo](https://gist.github.com/CESARDELATORRE/d80c6423a1aebaffaf387469f5194f5b)).</span></span>

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

<span data-ttu-id="f9db7-110">在用戶端 C\# 應用程式 (另一個 Web API 用戶端微服務、ASP.NET MVC 應用程式或甚至 C\# Xamarin 應用程式) 中使用此程式碼相當簡單。</span><span class="sxs-lookup"><span data-stu-id="f9db7-110">Using this code in a client C\# application (another Web API client microservice, an ASP.NET MVC application, or even a C\# Xamarin application) is straightforward.</span></span> <span data-ttu-id="f9db7-111">下列範例示範如何使用 HttpClient 類別。</span><span class="sxs-lookup"><span data-stu-id="f9db7-111">The following example shows how, using the HttpClient class.</span></span>

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

<span data-ttu-id="f9db7-112">不過，此程式碼只適合作為概念證明。</span><span class="sxs-lookup"><span data-stu-id="f9db7-112">However, this code is suitable only as a proof of concept.</span></span> <span data-ttu-id="f9db7-113">下一個主題說明如何使用更複雜且經過實證的程式庫。</span><span class="sxs-lookup"><span data-stu-id="f9db7-113">The next topic explains how to use more sophisticated and proven libraries.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="f9db7-114">[上一頁](implement-resilient-entity-framework-core-sql-connections.md)
[下一頁](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="f9db7-114">[Previous](implement-resilient-entity-framework-core-sql-connections.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>
