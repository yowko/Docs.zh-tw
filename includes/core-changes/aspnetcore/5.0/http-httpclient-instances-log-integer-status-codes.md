---
ms.openlocfilehash: 44d33fb28e66e590e4604c6dd2c73616e4c5e943
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728277"
---
### <a name="http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes"></a>HTTP： IHttpClientFactory 記錄整數狀態碼所建立的 HttpClient 實例

<xref:System.Net.Http.HttpClient>以整數而<xref:System.Net.Http.IHttpClientFactory>不是狀態碼名稱所建立的實例。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 1

#### <a name="old-behavior"></a>舊的行為

記錄會使用 HTTP 狀態碼的文字描述。 請考慮下列記錄檔訊息：

```
Received HTTP response after 56.0044ms - OK
End processing HTTP request after 70.0862ms - OK
```

#### <a name="new-behavior"></a>新的行為

記錄會使用 HTTP 狀態碼的整數值。 請考慮下列記錄檔訊息：

```
Received HTTP response after 56.0044ms - 200
End processing HTTP request after 70.0862ms - 200
```

#### <a name="reason-for-change"></a>變更的原因

這項記錄的原始行為與具有一律使用之整數值的 ASP.NET Core 的其他部分不一致。 不一致會使記錄檔難以透過結構化記錄系統（例如[Elasticsearch](https://www.elastic.co/elasticsearch/)）進行查詢。 如需詳細內容，請參閱[dotnet/extensions # 1549](https://github.com/dotnet/extensions/issues/1549)。

使用整數值比文字更有彈性，因為它允許對值範圍進行查詢。

已考慮加入另一個記錄值來捕捉整數狀態碼。 可惜的是，這樣做會導致其他 ASP.NET Core 的其他不一致。 HttpClient 記錄和 HTTP 伺服器/裝載記錄使用相同`StatusCode`的索引鍵名稱。

#### <a name="recommended-action"></a>建議的動作

最佳選項是更新記錄查詢，以使用狀態碼的整數值。 此選項可能會導致在多個 ASP.NET Core 版本中撰寫查詢時遇到一些困難。 不過，針對此用途使用整數，對於查詢記錄會有更大的彈性。

如果您需要強制相容于舊的行為，並使用文字狀態碼，請將`IHttpClientFactory`記錄取代成您自己的：

1. 將下列類別的 .NET Core 3.1 版本複製到您的專案中：

    * [LoggingHttpMessageHandlerBuilderFilter](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandlerBuilderFilter.cs)
    * [LoggingHttpMessageHandler](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandler.cs)
    * [LoggingScopeHttpMessageHandler](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingScopeHttpMessageHandler.cs)
    * [HttpHeadersLogValue](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/HttpHeadersLogValue.cs)

1. 將類別重新命名，以避免與[Microsoft Extensions. Http](https://www.nuget.org/packages/Microsoft.Extensions.Http) NuGet 封裝中的公用類型發生衝突。

1. 在專案的`Startup.ConfigureServices`方法中，將`LoggingHttpMessageHandlerBuilderFilter`內建的實取代為您自己的。 例如：

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

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:System.Net.Http.HttpClient?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:System.Net.Http.HttpClient`

-->
