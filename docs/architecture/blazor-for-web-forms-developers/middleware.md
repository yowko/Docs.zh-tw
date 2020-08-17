---
title: 模組、處理常式和中介軟體
description: 瞭解如何使用模組、處理常式和中介軟體來處理 HTTP 要求。
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 10/11/2019
ms.openlocfilehash: 639755dd78892df1b70ea5245a9584e575fbf691
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267876"
---
# <a name="modules-handlers-and-middleware"></a>模組、處理常式和中介軟體

ASP.NET Core 的應用程式是以一系列 *中介軟體*為基礎。 中介軟體是排列成管線以處理要求和回應的處理常式。 在 Web Form 應用程式中，HTTP 處理常式和模組會解決類似的問題。 在 ASP.NET Core 中，模組、處理常式、 *Global.asax.cs*和應用程式生命週期會取代為中介軟體。 在本章中，您將瞭解應用程式內容中的中介軟體 Blazor 。

## <a name="overview"></a>概觀

ASP.NET Core 要求管線由要求委派序列組成，並會一個接著一個呼叫。 下圖說明此概念。 執行緒遵循黑色箭號執行。

![管線](media/middleware/request-delegate-pipeline.png)

上圖缺少生命週期事件的概念。 這是處理 ASP.NET Web Forms 要求的基礎概念。 此系統可讓您更輕鬆地瞭解正在發生的進程，並允許在任何時間點插入中介軟體。 中介軟體會依照將其新增至要求管線的順序來執行。 它們也會以程式碼（而非設定檔）的方式加入，通常是在 *Startup.cs*中。

## <a name="katana"></a>Katana

熟悉 Katana 的讀者會覺得 ASP.NET Core 的習慣。 事實上，Katana 是從中衍生 ASP.NET Core 的架構。 它導入了類似于 ASP.NET 4.x 的中介軟體和管線模式。 針對 Katana 而設計的中介軟體可以調整以搭配 ASP.NET Core 管線使用。

## <a name="common-middleware"></a>一般中介軟體

ASP.NET 4.x 包含許多模組。 同樣地，ASP.NET Core 也有許多中介軟體元件可用。 在某些情況下，IIS 模組可用於 ASP.NET Core。 在其他情況下，可以使用原生 ASP.NET Core 中介軟體。

下表列出 ASP.NET Core 中的更換中介軟體和元件。

|模組                 |ASP.NET 4.x 模組           |ASP.NET Core 選項|
|-----------------------|-----------------------------|-------------------|
|HTTP 錯誤            |`CustomErrorModule`          |[狀態碼頁面中介軟體](/aspnet/core/fundamentals/error-handling#usestatuscodepages)|
|預設文件       |`DefaultDocumentModule`      |[預設檔案中介軟體](/aspnet/core/fundamentals/static-files#serve-a-default-document)|
|瀏覽目錄     |`DirectoryListingModule`     |[目錄瀏覽中介軟體](/aspnet/core/fundamentals/static-files#enable-directory-browsing)|
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

這份清單並不完整，但應該要瞭解這兩個架構之間有何種對應存在。 如需更詳細的清單，請參閱 [具有 ASP.NET Core 的 IIS 模組](/aspnet/core/host-and-deploy/iis/modules)。

## <a name="custom-middleware"></a>自訂中介軟體

內建中介軟體可能不會處理應用程式所需的所有案例。 在這種情況下，建立您自己的中介軟體是合理的。 有多種方式可以定義中介軟體，最簡單的是簡單的委派。 請考慮下列中介軟體，其會接受來自查詢字串的文化要求：

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

中介軟體也可以藉由執行 `IMiddleware` 介面或依照中介軟體慣例，定義為類別。 如需詳細資訊，請參閱 [撰寫自訂 ASP.NET Core 中介軟體](/aspnet/core/fundamentals/middleware/write)。

>[!div class="step-by-step"]
>[上一個](data.md) 
>[下一步](config.md)
