---
title: 重大變更： IHttpClientFactory 記錄整數狀態碼所建立的 HTTP： HttpClient 實例
description: 瞭解 ASP.NET Core 5.0 的重大變更，標題為 HTTP： IHttpClientFactory 記錄檔整數狀態碼所建立的 HttpClient 實例
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 964c0a65a07816acea8016d42a66a6bf84aba7c4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760440"
---
# <a name="http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes"></a>HTTP： IHttpClientFactory 記錄整數狀態碼所建立的 HttpClient 實例

<xref:System.Net.Http.HttpClient><xref:System.Net.Http.IHttpClientFactory>記錄 HTTP 狀態碼做為整數而非狀態碼名稱所建立的實例。

## <a name="version-introduced"></a>引進的版本

5.0 Preview 1

## <a name="old-behavior"></a>舊的行為

記錄會使用 HTTP 狀態碼的文字描述。 請考慮下列記錄訊息：

```output
Received HTTP response after 56.0044ms - OK
End processing HTTP request after 70.0862ms - OK
```

## <a name="new-behavior"></a>新的行為

記錄會使用 HTTP 狀態碼的整數值。 請考慮下列記錄訊息：

```output
Received HTTP response after 56.0044ms - 200
End processing HTTP request after 70.0862ms - 200
```

## <a name="reason-for-change"></a>變更的原因

此記錄的原始行為與具有永遠使用之整數值的 ASP.NET Core 的其他部分不一致。 不一致會讓記錄難以透過結構化記錄系統（例如 [Elasticsearch](https://www.elastic.co/elasticsearch/)）進行查詢。 如需詳細資訊，請參閱 [dotnet/extensions # 1549](https://github.com/dotnet/extensions/issues/1549)。

使用整數值比文字更有彈性，因為它允許對值範圍進行查詢。

已考慮新增另一個記錄值來捕捉整數狀態碼。 可惜的是，這麼做會導致其他 ASP.NET Core 的不一致。 HttpClient 記錄和 HTTP 伺服器/裝載記錄已使用相同的 `StatusCode` 金鑰名稱。

## <a name="recommended-action"></a>建議的動作

最佳選項是更新記錄查詢，以使用狀態碼的整數值。 此選項可能會在多個 ASP.NET Core 版本之間撰寫查詢時遇到困難。 不過，針對此用途使用整數，對於查詢記錄會有更大的彈性。

如果您需要強制與舊有行為的相容性，並使用文字狀態碼，請 `IHttpClientFactory` 使用您自己的記錄來取代記錄：

1. 將下列類別的 .NET Core 3.1 版本複製到您的專案中：

    * [LoggingHttpMessageHandlerBuilderFilter](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandlerBuilderFilter.cs)
    * [LoggingHttpMessageHandler](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandler.cs)
    * [LoggingScopeHttpMessageHandler](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingScopeHttpMessageHandler.cs)
    * [HttpHeadersLogValue](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/HttpHeadersLogValue.cs)

1. 將類別重新命名，以避免與位於 [Http.sys](https://www.nuget.org/packages/Microsoft.Extensions.Http) NuGet 套件中的公用類型發生衝突。

1. 以 `LoggingHttpMessageHandlerBuilderFilter` 您自己在專案的方法中取代內建的實作為 `Startup.ConfigureServices` 。 例如：

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        // Other service registrations go first. Code omitted for brevity.

        // Place the following after all AddHttpClient registrations.
        services.RemoveAll<IHttpMessageHandlerBuilderFilter>();

        services.AddSingleton<IHttpMessageHandlerBuilderFilter,
                              MyLoggingHttpMessageHandlerBuilderFilter>();
    }
    ```

## <a name="affected-apis"></a>受影響的 API

<xref:System.Net.Http.HttpClient?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:System.Net.Http.HttpClient`

-->
