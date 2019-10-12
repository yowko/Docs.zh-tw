---
title: 模組、處理常式和中介軟體
description: 瞭解如何處理具有模組、處理常式和中介軟體的 HTTP 要求。
author: danroth27
ms.author: daroth
ms.date: 10/11/2019
ms.openlocfilehash: b0be6109b9226bddbb9cbe4cebf114fd2b2a6114
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291160"
---
# <a name="modules-handlers-and-middleware"></a>模組、處理常式和中介軟體

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

ASP.NET Core 應用程式是以一系列中介軟體為基礎所建立。 中介軟體是處理常式，會排列成管線來處理要求和回應。 在 Web Forms 應用程式中，HTTP 處理常式和模組會解決類似的問題。 在 ASP.NET Core 中，模組、處理常式、 *Global.asax.cs*和應用程式生命週期都會取代為中介軟體。 在本章中，您將瞭解 Blazor 應用程式內容中的中介軟體。

## <a name="overview"></a>總覽

ASP.NET Core 要求管線由要求委派序列組成，並會一個接著一個呼叫。 下圖說明此概念。 執行緒遵循黑色箭號執行。

![管線](media/middleware/request-delegate-pipeline.png)

上圖缺少生命週期事件的概念。 這個概念是如何處理 ASP.NET Web Forms 要求的基礎。 此系統可讓您更輕鬆地瞭解發生了哪個進程，並允許在任何時間點插入中介軟體。 中介軟體會依照其新增至要求管線的循序執行。 它們也會新增至程式碼，而不是設定檔中，通常是在*Startup.cs*中。

## <a name="katana"></a>Katana

熟悉 Katana 的讀者會在 ASP.NET Core 中感到滿意。 事實上，Katana 是 ASP.NET Core 衍生的架構。 它引進了類似的中介軟體和 ASP.NET 4.x 的管線模式。 針對 Katana 而設計的中介軟體可以調整以搭配 ASP.NET Core 管線使用。

## <a name="common-middleware"></a>一般中介軟體

ASP.NET 4.x 包含許多模組。 以類似的方式，ASP.NET Core 也有許多中介軟體元件可供使用。 在某些情況下，可能會使用 IIS 模組 ASP.NET Core。 在其他情況下，可能會有原生 ASP.NET Core 中介軟體。

下表列出 ASP.NET Core 中的取代中介軟體和元件。

|Module                 |ASP.NET 4.x 模組           |ASP.NET Core 選項|
|-----------------------|-----------------------------|-------------------|
|HTTP 錯誤            |`CustomErrorModule`          |[狀態碼頁面中介軟體](/aspnet/core/fundamentals/error-handling#usestatuscodepages)|
|預設檔       |`DefaultDocumentModule`      |[預設檔案中介軟體](/aspnet/core/fundamentals/static-files#serve-a-default-document)|
|流覽目錄     |`DirectoryListingModule`     |[目錄瀏覽中介軟體](/aspnet/core/fundamentals/static-files#enable-directory-browsing)|
|動態壓縮    |`DynamicCompressionModule`   |[回應壓縮中介軟體](/aspnet/core/performance/response-compression)|
|失敗的要求追蹤|`FailedRequestsTracingModule`|[ASP.NET Core 記錄](/aspnet/core/fundamentals/logging/index#tracesource-provider)|
|檔案快取           |`FileCacheModule`            |[回應快取中介軟體](/aspnet/core/performance/caching/middleware)|
|HTTP 快取           |`HttpCacheModule`            |[回應快取中介軟體](/aspnet/core/performance/caching/middleware)|
|HTTP 記錄           |`HttpLoggingModule`          |[ASP.NET Core 記錄](/aspnet/core/fundamentals/logging/index)|
|HTTP 重新導向       |`HttpRedirectionModule`      |[URL 重寫中介軟體](/aspnet/core/fundamentals/url-rewriting)|
|ISAPI 篩選器          |`IsapiFilterModule`          |[中介軟體](/aspnet/core/fundamentals/middleware/index)|
|ISAPI                  |`IsapiModule`                |[中介軟體](/aspnet/core/fundamentals/middleware/index)|
|要求篩選      |`RequestFilteringModule`     |[URL 重寫中介軟體 IRule](/aspnet/core/fundamentals/url-rewriting#irule-based-rule)|
|URL 重寫&#8224;   |`RewriteModule`              |[URL 重寫中介軟體](/aspnet/core/fundamentals/url-rewriting)|
|靜態壓縮     |`StaticCompressionModule`    |[回應壓縮中介軟體](/aspnet/core/performance/response-compression)|
|靜態內容         |`StaticFileModule`           |[靜態檔案中介軟體](/aspnet/core/fundamentals/static-files)|
|URL 授權      |`UrlAuthorizationModule`     |[ASP.NET Core 身分識別](/aspnet/core/security/authentication/identity)|

這份清單並不完整，但應該能讓您瞭解這兩個架構之間有何對應存在。 如需更詳細的清單，請參閱[具有 ASP.NET Core 的 IIS 模組](/aspnet/core/host-and-deploy/iis/modules)。

## <a name="custom-middleware"></a>自訂中介軟體

內建中介軟體可能無法處理應用程式所需的所有案例。 在這種情況下，建立您自己的中介軟體是合理的。 有多種方式可定義中介軟體，最簡單的是簡單的委派。 請考慮下列中介軟體，它會接受查詢字串中的文化特性要求：

```csharp
public class Startup
{
    public void Configure(IApplicationBuilder app)
    {
        app.Use(async (context, next) =>
        {
            var cultureQuery = context.Request.Query["culture"];

            if (!string.IsNullOrWhiteSpace(cultureQuery))
            {
                var culture = new CultureInfo(cultureQuery);

                CultureInfo.CurrentCulture = culture;
                CultureInfo.CurrentUICulture = culture;
            }

            // Call the next delegate/middleware in the pipeline
            await next();
        });

        app.Run(async (context) =>
            await context.Response.WriteAsync(
                $"Hello {CultureInfo.CurrentCulture.DisplayName}"));
    }
}
```

中介軟體也可以藉由執行 @no__t 0 介面或遵循中介軟體慣例，定義為類別。 如需詳細資訊，請參閱[撰寫自訂 ASP.NET Core 中介軟體](/aspnet/core/fundamentals/middleware/write)。

>[!div class="step-by-step"]
>[上一頁](data.md)
>[下一頁](config.md)
