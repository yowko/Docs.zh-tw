---
ms.openlocfilehash: 47f42305f4106f5e05e555a859f13c41bb950519
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811254"
---
### <a name="http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes"></a><span data-ttu-id="c2412-101">HTTP： IHttpClientFactory 記錄整數狀態碼所建立的 HttpClient 實例</span><span class="sxs-lookup"><span data-stu-id="c2412-101">HTTP: HttpClient instances created by IHttpClientFactory log integer status codes</span></span>

<span data-ttu-id="c2412-102"><xref:System.Net.Http.HttpClient><xref:System.Net.Http.IHttpClientFactory>記錄 HTTP 狀態碼做為整數而非狀態碼名稱所建立的實例。</span><span class="sxs-lookup"><span data-stu-id="c2412-102"><xref:System.Net.Http.HttpClient> instances created by <xref:System.Net.Http.IHttpClientFactory> log HTTP status codes as integers instead of with status code names.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c2412-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="c2412-103">Version introduced</span></span>

<span data-ttu-id="c2412-104">5.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="c2412-104">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="c2412-105">舊的行為</span><span class="sxs-lookup"><span data-stu-id="c2412-105">Old behavior</span></span>

<span data-ttu-id="c2412-106">記錄會使用 HTTP 狀態碼的文字描述。</span><span class="sxs-lookup"><span data-stu-id="c2412-106">Logging uses the textual descriptions of HTTP status codes.</span></span> <span data-ttu-id="c2412-107">請考慮下列記錄訊息：</span><span class="sxs-lookup"><span data-stu-id="c2412-107">Consider the following log messages:</span></span>

```output
Received HTTP response after 56.0044ms - OK
End processing HTTP request after 70.0862ms - OK
```

#### <a name="new-behavior"></a><span data-ttu-id="c2412-108">新的行為</span><span class="sxs-lookup"><span data-stu-id="c2412-108">New behavior</span></span>

<span data-ttu-id="c2412-109">記錄會使用 HTTP 狀態碼的整數值。</span><span class="sxs-lookup"><span data-stu-id="c2412-109">Logging uses the integer values of HTTP status codes.</span></span> <span data-ttu-id="c2412-110">請考慮下列記錄訊息：</span><span class="sxs-lookup"><span data-stu-id="c2412-110">Consider the following log messages:</span></span>

```output
Received HTTP response after 56.0044ms - 200
End processing HTTP request after 70.0862ms - 200
```

#### <a name="reason-for-change"></a><span data-ttu-id="c2412-111">變更的原因</span><span class="sxs-lookup"><span data-stu-id="c2412-111">Reason for change</span></span>

<span data-ttu-id="c2412-112">此記錄的原始行為與具有永遠使用之整數值的 ASP.NET Core 的其他部分不一致。</span><span class="sxs-lookup"><span data-stu-id="c2412-112">The original behavior of this logging is inconsistent with other parts of ASP.NET Core that have always used integer values.</span></span> <span data-ttu-id="c2412-113">不一致會讓記錄難以透過結構化記錄系統（例如 [Elasticsearch](https://www.elastic.co/elasticsearch/)）進行查詢。</span><span class="sxs-lookup"><span data-stu-id="c2412-113">The inconsistency makes logs difficult to query via structured logging systems such as [Elasticsearch](https://www.elastic.co/elasticsearch/).</span></span> <span data-ttu-id="c2412-114">如需詳細資訊，請參閱 [dotnet/extensions # 1549](https://github.com/dotnet/extensions/issues/1549)。</span><span class="sxs-lookup"><span data-stu-id="c2412-114">For more context, see [dotnet/extensions#1549](https://github.com/dotnet/extensions/issues/1549).</span></span>

<span data-ttu-id="c2412-115">使用整數值比文字更有彈性，因為它允許對值範圍進行查詢。</span><span class="sxs-lookup"><span data-stu-id="c2412-115">Using integer values is more flexible than text because it allows queries on ranges of values.</span></span>

<span data-ttu-id="c2412-116">已考慮新增另一個記錄值來捕捉整數狀態碼。</span><span class="sxs-lookup"><span data-stu-id="c2412-116">Adding another log value to capture the integer status code was considered.</span></span> <span data-ttu-id="c2412-117">可惜的是，這麼做會導致其他 ASP.NET Core 的不一致。</span><span class="sxs-lookup"><span data-stu-id="c2412-117">Unfortunately, doing so would introduce another inconsistency with the rest of ASP.NET Core.</span></span> <span data-ttu-id="c2412-118">HttpClient 記錄和 HTTP 伺服器/裝載記錄已使用相同的 `StatusCode` 金鑰名稱。</span><span class="sxs-lookup"><span data-stu-id="c2412-118">HttpClient logging and HTTP server/hosting logging use the same `StatusCode` key name already.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c2412-119">建議的動作</span><span class="sxs-lookup"><span data-stu-id="c2412-119">Recommended action</span></span>

<span data-ttu-id="c2412-120">最佳選項是更新記錄查詢，以使用狀態碼的整數值。</span><span class="sxs-lookup"><span data-stu-id="c2412-120">The best option is to update logging queries to use the integer values of status codes.</span></span> <span data-ttu-id="c2412-121">此選項可能會在多個 ASP.NET Core 版本之間撰寫查詢時遇到困難。</span><span class="sxs-lookup"><span data-stu-id="c2412-121">This option may cause some difficulty writing queries across multiple ASP.NET Core versions.</span></span> <span data-ttu-id="c2412-122">不過，針對此用途使用整數，對於查詢記錄會有更大的彈性。</span><span class="sxs-lookup"><span data-stu-id="c2412-122">However, using integers for this purpose is much more flexible for querying logs.</span></span>

<span data-ttu-id="c2412-123">如果您需要強制與舊有行為的相容性，並使用文字狀態碼，請 `IHttpClientFactory` 使用您自己的記錄來取代記錄：</span><span class="sxs-lookup"><span data-stu-id="c2412-123">If you need to force compatibility with the old behavior and use textual status codes, replace the `IHttpClientFactory` logging with your own:</span></span>

1. <span data-ttu-id="c2412-124">將下列類別的 .NET Core 3.1 版本複製到您的專案中：</span><span class="sxs-lookup"><span data-stu-id="c2412-124">Copy the .NET Core 3.1 versions of the following classes into your project:</span></span>

    * [<span data-ttu-id="c2412-125">LoggingHttpMessageHandlerBuilderFilter</span><span class="sxs-lookup"><span data-stu-id="c2412-125">LoggingHttpMessageHandlerBuilderFilter</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandlerBuilderFilter.cs)
    * [<span data-ttu-id="c2412-126">LoggingHttpMessageHandler</span><span class="sxs-lookup"><span data-stu-id="c2412-126">LoggingHttpMessageHandler</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandler.cs)
    * [<span data-ttu-id="c2412-127">LoggingScopeHttpMessageHandler</span><span class="sxs-lookup"><span data-stu-id="c2412-127">LoggingScopeHttpMessageHandler</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingScopeHttpMessageHandler.cs)
    * [<span data-ttu-id="c2412-128">HttpHeadersLogValue</span><span class="sxs-lookup"><span data-stu-id="c2412-128">HttpHeadersLogValue</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/HttpHeadersLogValue.cs)

1. <span data-ttu-id="c2412-129">將類別重新命名，以避免與位於 [Http.sys](https://www.nuget.org/packages/Microsoft.Extensions.Http) NuGet 套件中的公用類型發生衝突。</span><span class="sxs-lookup"><span data-stu-id="c2412-129">Rename the classes to avoid conflicts with public types in the [Microsoft.Extensions.Http](https://www.nuget.org/packages/Microsoft.Extensions.Http) NuGet package.</span></span>

1. <span data-ttu-id="c2412-130">以 `LoggingHttpMessageHandlerBuilderFilter` 您自己在專案的方法中取代內建的實作為 `Startup.ConfigureServices` 。</span><span class="sxs-lookup"><span data-stu-id="c2412-130">Replace the built-in implementation of `LoggingHttpMessageHandlerBuilderFilter` with your own in the project's `Startup.ConfigureServices` method.</span></span> <span data-ttu-id="c2412-131">例如：</span><span class="sxs-lookup"><span data-stu-id="c2412-131">For example:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        // Other service registrations go first. Code omitted for brevity.

        // Place the following after all AddHttpClient registrations.
        var descriptors = services.Where(
            s => s.ServiceType == typeof(IHttpMessageHandlerBuilderFilter));
        foreach (var descriptor in descriptors)
        {
            services.Remove(descriptor);
        }

        services.AddSingleton<IHttpMessageHandlerBuilderFilter,
                              MyLoggingHttpMessageHandlerBuilderFilter>();
    }
    ```

#### <a name="category"></a><span data-ttu-id="c2412-132">類別</span><span class="sxs-lookup"><span data-stu-id="c2412-132">Category</span></span>

<span data-ttu-id="c2412-133">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c2412-133">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c2412-134">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="c2412-134">Affected APIs</span></span>

<xref:System.Net.Http.HttpClient?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:System.Net.Http.HttpClient`

-->
