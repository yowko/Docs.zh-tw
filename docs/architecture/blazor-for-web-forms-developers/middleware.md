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
# <a name="modules-handlers-and-middleware"></a><span data-ttu-id="6c3b8-103">模組、處理常式和中介軟體</span><span class="sxs-lookup"><span data-stu-id="6c3b8-103">Modules, handlers, and middleware</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="6c3b8-104">ASP.NET Core 應用程式是以一系列中介軟體為基礎所建立。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-104">An ASP.NET Core app is built upon a series of middleware.</span></span> <span data-ttu-id="6c3b8-105">中介軟體是處理常式，會排列成管線來處理要求和回應。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-105">Middlewares are handlers, which are arranged into a pipeline to handle requests and responses.</span></span> <span data-ttu-id="6c3b8-106">在 Web Forms 應用程式中，HTTP 處理常式和模組會解決類似的問題。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-106">In a Web Forms app, HTTP handlers and modules solve similar problems.</span></span> <span data-ttu-id="6c3b8-107">在 ASP.NET Core 中，模組、處理常式、 *Global.asax.cs*和應用程式生命週期都會取代為中介軟體。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-107">In ASP.NET Core, modules, handlers, *Global.asax.cs*, and the app life cycle are replaced with middleware.</span></span> <span data-ttu-id="6c3b8-108">在本章中，您將瞭解 Blazor 應用程式內容中的中介軟體。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-108">In this chapter, you'll learn what middleware in the context of a Blazor app.</span></span>

## <a name="overview"></a><span data-ttu-id="6c3b8-109">總覽</span><span class="sxs-lookup"><span data-stu-id="6c3b8-109">Overview</span></span>

<span data-ttu-id="6c3b8-110">ASP.NET Core 要求管線由要求委派序列組成，並會一個接著一個呼叫。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-110">The ASP.NET Core request pipeline consists of a sequence of request delegates, called one after the other.</span></span> <span data-ttu-id="6c3b8-111">下圖說明此概念。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-111">The following diagram demonstrates the concept.</span></span> <span data-ttu-id="6c3b8-112">執行緒遵循黑色箭號執行。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-112">The thread of execution follows the black arrows.</span></span>

![管線](media/middleware/request-delegate-pipeline.png)

<span data-ttu-id="6c3b8-114">上圖缺少生命週期事件的概念。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-114">The preceding diagram lacks a concept of lifecycle events.</span></span> <span data-ttu-id="6c3b8-115">這個概念是如何處理 ASP.NET Web Forms 要求的基礎。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-115">This concept is foundational to how ASP.NET Web Forms requests are handled.</span></span> <span data-ttu-id="6c3b8-116">此系統可讓您更輕鬆地瞭解發生了哪個進程，並允許在任何時間點插入中介軟體。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-116">This system makes it easier to reason about what process is occurring and allows middleware to be inserted at any point.</span></span> <span data-ttu-id="6c3b8-117">中介軟體會依照其新增至要求管線的循序執行。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-117">Middleware executes in the order in which it's added to the request pipeline.</span></span> <span data-ttu-id="6c3b8-118">它們也會新增至程式碼，而不是設定檔中，通常是在*Startup.cs*中。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-118">They're also added in code instead of configuration files, usually in *Startup.cs*.</span></span>

## <a name="katana"></a><span data-ttu-id="6c3b8-119">Katana</span><span class="sxs-lookup"><span data-stu-id="6c3b8-119">Katana</span></span>

<span data-ttu-id="6c3b8-120">熟悉 Katana 的讀者會在 ASP.NET Core 中感到滿意。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-120">Readers familiar with Katana will feel comfortable in ASP.NET Core.</span></span> <span data-ttu-id="6c3b8-121">事實上，Katana 是 ASP.NET Core 衍生的架構。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-121">In fact, Katana is a framework from which ASP.NET Core derives.</span></span> <span data-ttu-id="6c3b8-122">它引進了類似的中介軟體和 ASP.NET 4.x 的管線模式。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-122">It introduced similar middleware and pipeline patterns for ASP.NET 4.x.</span></span> <span data-ttu-id="6c3b8-123">針對 Katana 而設計的中介軟體可以調整以搭配 ASP.NET Core 管線使用。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-123">Middleware designed for Katana can be adapted to work with the ASP.NET Core pipeline.</span></span>

## <a name="common-middleware"></a><span data-ttu-id="6c3b8-124">一般中介軟體</span><span class="sxs-lookup"><span data-stu-id="6c3b8-124">Common middleware</span></span>

<span data-ttu-id="6c3b8-125">ASP.NET 4.x 包含許多模組。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-125">ASP.NET 4.x includes many modules.</span></span> <span data-ttu-id="6c3b8-126">以類似的方式，ASP.NET Core 也有許多中介軟體元件可供使用。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-126">In a similar fashion, ASP.NET Core has many middleware components available as well.</span></span> <span data-ttu-id="6c3b8-127">在某些情況下，可能會使用 IIS 模組 ASP.NET Core。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-127">IIS modules may be used in some cases with ASP.NET Core.</span></span> <span data-ttu-id="6c3b8-128">在其他情況下，可能會有原生 ASP.NET Core 中介軟體。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-128">In other cases, native ASP.NET Core middleware may be available.</span></span>

<span data-ttu-id="6c3b8-129">下表列出 ASP.NET Core 中的取代中介軟體和元件。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-129">The following table lists replacement middleware and components in ASP.NET Core.</span></span>

|<span data-ttu-id="6c3b8-130">Module</span><span class="sxs-lookup"><span data-stu-id="6c3b8-130">Module</span></span>                 |<span data-ttu-id="6c3b8-131">ASP.NET 4.x 模組</span><span class="sxs-lookup"><span data-stu-id="6c3b8-131">ASP.NET 4.x module</span></span>           |<span data-ttu-id="6c3b8-132">ASP.NET Core 選項</span><span class="sxs-lookup"><span data-stu-id="6c3b8-132">ASP.NET Core option</span></span>|
|-----------------------|-----------------------------|-------------------|
|<span data-ttu-id="6c3b8-133">HTTP 錯誤</span><span class="sxs-lookup"><span data-stu-id="6c3b8-133">HTTP errors</span></span>            |`CustomErrorModule`          |[<span data-ttu-id="6c3b8-134">狀態碼頁面中介軟體</span><span class="sxs-lookup"><span data-stu-id="6c3b8-134">Status Code Pages Middleware</span></span>](/aspnet/core/fundamentals/error-handling#usestatuscodepages)|
|<span data-ttu-id="6c3b8-135">預設檔</span><span class="sxs-lookup"><span data-stu-id="6c3b8-135">Default document</span></span>       |`DefaultDocumentModule`      |[<span data-ttu-id="6c3b8-136">預設檔案中介軟體</span><span class="sxs-lookup"><span data-stu-id="6c3b8-136">Default Files Middleware</span></span>](/aspnet/core/fundamentals/static-files#serve-a-default-document)|
|<span data-ttu-id="6c3b8-137">流覽目錄</span><span class="sxs-lookup"><span data-stu-id="6c3b8-137">Directory browsing</span></span>     |`DirectoryListingModule`     |[<span data-ttu-id="6c3b8-138">目錄瀏覽中介軟體</span><span class="sxs-lookup"><span data-stu-id="6c3b8-138">Directory Browsing Middleware</span></span>](/aspnet/core/fundamentals/static-files#enable-directory-browsing)|
|<span data-ttu-id="6c3b8-139">動態壓縮</span><span class="sxs-lookup"><span data-stu-id="6c3b8-139">Dynamic compression</span></span>    |`DynamicCompressionModule`   |[<span data-ttu-id="6c3b8-140">回應壓縮中介軟體</span><span class="sxs-lookup"><span data-stu-id="6c3b8-140">Response Compression Middleware</span></span>](/aspnet/core/performance/response-compression)|
|<span data-ttu-id="6c3b8-141">失敗的要求追蹤</span><span class="sxs-lookup"><span data-stu-id="6c3b8-141">Failed requests tracing</span></span>|`FailedRequestsTracingModule`|[<span data-ttu-id="6c3b8-142">ASP.NET Core 記錄</span><span class="sxs-lookup"><span data-stu-id="6c3b8-142">ASP.NET Core Logging</span></span>](/aspnet/core/fundamentals/logging/index#tracesource-provider)|
|<span data-ttu-id="6c3b8-143">檔案快取</span><span class="sxs-lookup"><span data-stu-id="6c3b8-143">File caching</span></span>           |`FileCacheModule`            |[<span data-ttu-id="6c3b8-144">回應快取中介軟體</span><span class="sxs-lookup"><span data-stu-id="6c3b8-144">Response Caching Middleware</span></span>](/aspnet/core/performance/caching/middleware)|
|<span data-ttu-id="6c3b8-145">HTTP 快取</span><span class="sxs-lookup"><span data-stu-id="6c3b8-145">HTTP caching</span></span>           |`HttpCacheModule`            |[<span data-ttu-id="6c3b8-146">回應快取中介軟體</span><span class="sxs-lookup"><span data-stu-id="6c3b8-146">Response Caching Middleware</span></span>](/aspnet/core/performance/caching/middleware)|
|<span data-ttu-id="6c3b8-147">HTTP 記錄</span><span class="sxs-lookup"><span data-stu-id="6c3b8-147">HTTP logging</span></span>           |`HttpLoggingModule`          |[<span data-ttu-id="6c3b8-148">ASP.NET Core 記錄</span><span class="sxs-lookup"><span data-stu-id="6c3b8-148">ASP.NET Core Logging</span></span>](/aspnet/core/fundamentals/logging/index)|
|<span data-ttu-id="6c3b8-149">HTTP 重新導向</span><span class="sxs-lookup"><span data-stu-id="6c3b8-149">HTTP redirection</span></span>       |`HttpRedirectionModule`      |[<span data-ttu-id="6c3b8-150">URL 重寫中介軟體</span><span class="sxs-lookup"><span data-stu-id="6c3b8-150">URL Rewriting Middleware</span></span>](/aspnet/core/fundamentals/url-rewriting)|
|<span data-ttu-id="6c3b8-151">ISAPI 篩選器</span><span class="sxs-lookup"><span data-stu-id="6c3b8-151">ISAPI filters</span></span>          |`IsapiFilterModule`          |[<span data-ttu-id="6c3b8-152">中介軟體</span><span class="sxs-lookup"><span data-stu-id="6c3b8-152">Middleware</span></span>](/aspnet/core/fundamentals/middleware/index)|
|<span data-ttu-id="6c3b8-153">ISAPI</span><span class="sxs-lookup"><span data-stu-id="6c3b8-153">ISAPI</span></span>                  |`IsapiModule`                |[<span data-ttu-id="6c3b8-154">中介軟體</span><span class="sxs-lookup"><span data-stu-id="6c3b8-154">Middleware</span></span>](/aspnet/core/fundamentals/middleware/index)|
|<span data-ttu-id="6c3b8-155">要求篩選</span><span class="sxs-lookup"><span data-stu-id="6c3b8-155">Request filtering</span></span>      |`RequestFilteringModule`     |[<span data-ttu-id="6c3b8-156">URL 重寫中介軟體 IRule</span><span class="sxs-lookup"><span data-stu-id="6c3b8-156">URL Rewriting Middleware IRule</span></span>](/aspnet/core/fundamentals/url-rewriting#irule-based-rule)|
|<span data-ttu-id="6c3b8-157">URL 重寫&#8224;</span><span class="sxs-lookup"><span data-stu-id="6c3b8-157">URL rewriting&#8224;</span></span>   |`RewriteModule`              |[<span data-ttu-id="6c3b8-158">URL 重寫中介軟體</span><span class="sxs-lookup"><span data-stu-id="6c3b8-158">URL Rewriting Middleware</span></span>](/aspnet/core/fundamentals/url-rewriting)|
|<span data-ttu-id="6c3b8-159">靜態壓縮</span><span class="sxs-lookup"><span data-stu-id="6c3b8-159">Static compression</span></span>     |`StaticCompressionModule`    |[<span data-ttu-id="6c3b8-160">回應壓縮中介軟體</span><span class="sxs-lookup"><span data-stu-id="6c3b8-160">Response Compression Middleware</span></span>](/aspnet/core/performance/response-compression)|
|<span data-ttu-id="6c3b8-161">靜態內容</span><span class="sxs-lookup"><span data-stu-id="6c3b8-161">Static content</span></span>         |`StaticFileModule`           |[<span data-ttu-id="6c3b8-162">靜態檔案中介軟體</span><span class="sxs-lookup"><span data-stu-id="6c3b8-162">Static File Middleware</span></span>](/aspnet/core/fundamentals/static-files)|
|<span data-ttu-id="6c3b8-163">URL 授權</span><span class="sxs-lookup"><span data-stu-id="6c3b8-163">URL authorization</span></span>      |`UrlAuthorizationModule`     |[<span data-ttu-id="6c3b8-164">ASP.NET Core 身分識別</span><span class="sxs-lookup"><span data-stu-id="6c3b8-164">ASP.NET Core Identity</span></span>](/aspnet/core/security/authentication/identity)|

<span data-ttu-id="6c3b8-165">這份清單並不完整，但應該能讓您瞭解這兩個架構之間有何對應存在。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-165">This list isn't exhaustive but should give an idea of what mapping exists between the two frameworks.</span></span> <span data-ttu-id="6c3b8-166">如需更詳細的清單，請參閱[具有 ASP.NET Core 的 IIS 模組](/aspnet/core/host-and-deploy/iis/modules)。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-166">For a more detailed list, see [IIS modules with ASP.NET Core](/aspnet/core/host-and-deploy/iis/modules).</span></span>

## <a name="custom-middleware"></a><span data-ttu-id="6c3b8-167">自訂中介軟體</span><span class="sxs-lookup"><span data-stu-id="6c3b8-167">Custom middleware</span></span>

<span data-ttu-id="6c3b8-168">內建中介軟體可能無法處理應用程式所需的所有案例。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-168">Built-in middleware may not handle all scenarios needed for an app.</span></span> <span data-ttu-id="6c3b8-169">在這種情況下，建立您自己的中介軟體是合理的。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-169">In such cases, it makes sense to create your own middleware.</span></span> <span data-ttu-id="6c3b8-170">有多種方式可定義中介軟體，最簡單的是簡單的委派。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-170">There are multiple ways of defining middleware, with the simplest being a simple delegate.</span></span> <span data-ttu-id="6c3b8-171">請考慮下列中介軟體，它會接受查詢字串中的文化特性要求：</span><span class="sxs-lookup"><span data-stu-id="6c3b8-171">Consider the following middleware, which accepts a culture request from a query string:</span></span>

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

<span data-ttu-id="6c3b8-172">中介軟體也可以藉由執行 @no__t 0 介面或遵循中介軟體慣例，定義為類別。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-172">Middleware can also be defined as class, either by implementing the `IMiddleware` interface or by following middleware convention.</span></span> <span data-ttu-id="6c3b8-173">如需詳細資訊，請參閱[撰寫自訂 ASP.NET Core 中介軟體](/aspnet/core/fundamentals/middleware/write)。</span><span class="sxs-lookup"><span data-stu-id="6c3b8-173">For more information, see [Write custom ASP.NET Core middleware](/aspnet/core/fundamentals/middleware/write).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6c3b8-174">[上一頁](data.md)
>[下一頁](config.md)</span><span class="sxs-lookup"><span data-stu-id="6c3b8-174">[Previous](data.md)
[Next](config.md)</span></span>
