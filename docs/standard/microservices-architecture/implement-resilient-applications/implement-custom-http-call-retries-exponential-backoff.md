---
title: "實作自訂的 HTTP 呼叫重試，使用指數型輪詢"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |實作自訂的 HTTP 呼叫重試，使用指數型輪詢"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 4449e5d7e0ca3c81aead26fac653de3ba2187a92
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-custom-http-call-retries-with-exponential-backoff"></a><span data-ttu-id="9d8f4-104">實作自訂的 HTTP 呼叫重試，使用指數型輪詢</span><span class="sxs-lookup"><span data-stu-id="9d8f4-104">Implementing custom HTTP call retries with exponential backoff</span></span>

<span data-ttu-id="9d8f4-105">若要建立具有恢復功能 microservices，您必須處理可能的 HTTP 故障案例。</span><span class="sxs-lookup"><span data-stu-id="9d8f4-105">In order to create resilient microservices, you need to handle possible HTTP failure scenarios.</span></span> <span data-ttu-id="9d8f4-106">基於這個目的，您可以建立您自己的重試次數的實作使用指數型輪詢。</span><span class="sxs-lookup"><span data-stu-id="9d8f4-106">For that purpose, you could create your own implementation of retries with exponential backoff.</span></span>

<span data-ttu-id="9d8f4-107">除了處理時態資源無法使用，指數型輪詢也必須考慮雲端提供者可能會進行節流處理以避免使用量超載的資源的可用性。</span><span class="sxs-lookup"><span data-stu-id="9d8f4-107">In addition to handling temporal resource unavailability, the exponential backoff also needs to take into account that the cloud provider might throttle availability of resources to prevent usage overload.</span></span> <span data-ttu-id="9d8f4-108">例如，非常快速地建立太多連線要求可能會被視為阻絕服務 ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) 雲端提供者的攻擊。</span><span class="sxs-lookup"><span data-stu-id="9d8f4-108">For example, creating too many connection requests very quickly might be viewed as a Denial of Service ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) attack by the cloud provider.</span></span> <span data-ttu-id="9d8f4-109">如此一來，您需要提供一個機制，在遇到的容量閾值時，調整連接要求。</span><span class="sxs-lookup"><span data-stu-id="9d8f4-109">As a result, you need to provide a mechanism to scale back connection requests when a capacity threshold has been encountered.</span></span>

<span data-ttu-id="9d8f4-110">為最初的探索，您可以實作自己的程式碼以指數型輪詢中的公用程式類別[RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260)，再加上類似下列程式碼 (這也是用於[GitHub 儲存機制](https://gist.github.com/CESARDELATORRE/d80c6423a1aebaffaf387469f5194f5b)).</span><span class="sxs-lookup"><span data-stu-id="9d8f4-110">As an initial exploration, you could implement your own code with a utility class for exponential backoff as in [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260), plus code like the following (which is also available on a [GitHub repo](https://gist.github.com/CESARDELATORRE/d80c6423a1aebaffaf387469f5194f5b)).</span></span>

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

<span data-ttu-id="9d8f4-111">使用此程式碼中的用戶端 C\#應用程式 (另一個 Web API 用戶端微服務、 ASP.NET MVC 應用程式或甚至 C\# Xamarin 應用程式) 相當簡單。</span><span class="sxs-lookup"><span data-stu-id="9d8f4-111">Using this code in a client C\# application (another Web API client microservice, an ASP.NET MVC application, or even a C\# Xamarin application) is straightforward.</span></span> <span data-ttu-id="9d8f4-112">下列範例會示範如何使用 HttpClient 類別。</span><span class="sxs-lookup"><span data-stu-id="9d8f4-112">The following example shows how, using the HttpClient class.</span></span>

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

<span data-ttu-id="9d8f4-113">不過，這段程式碼很適合僅做概念證明。</span><span class="sxs-lookup"><span data-stu-id="9d8f4-113">However, this code is suitable only as a proof of concept.</span></span> <span data-ttu-id="9d8f4-114">下一個主題說明如何使用更高性能且經過實證的程式庫。</span><span class="sxs-lookup"><span data-stu-id="9d8f4-114">The next topic explains how to use more sophisticated and proven libraries.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="9d8f4-115">[上一個](implement-resilient-entity-framework-core-sql-connections.md) [下一步] (implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="9d8f4-115">[Previous] (implement-resilient-entity-framework-core-sql-connections.md) [Next] (implement-http-call-retries-exponential-backoff-polly.md)</span></span>
