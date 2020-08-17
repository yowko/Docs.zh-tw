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
# <a name="modules-handlers-and-middleware"></a><span data-ttu-id="2acec-103">模組、處理常式和中介軟體</span><span class="sxs-lookup"><span data-stu-id="2acec-103">Modules, handlers, and middleware</span></span>

<span data-ttu-id="2acec-104">ASP.NET Core 的應用程式是以一系列 *中介軟體*為基礎。</span><span class="sxs-lookup"><span data-stu-id="2acec-104">An ASP.NET Core app is built upon a series of *middleware*.</span></span> <span data-ttu-id="2acec-105">中介軟體是排列成管線以處理要求和回應的處理常式。</span><span class="sxs-lookup"><span data-stu-id="2acec-105">Middleware is handlers that are arranged into a pipeline to handle requests and responses.</span></span> <span data-ttu-id="2acec-106">在 Web Form 應用程式中，HTTP 處理常式和模組會解決類似的問題。</span><span class="sxs-lookup"><span data-stu-id="2acec-106">In a Web Forms app, HTTP handlers and modules solve similar problems.</span></span> <span data-ttu-id="2acec-107">在 ASP.NET Core 中，模組、處理常式、 *Global.asax.cs*和應用程式生命週期會取代為中介軟體。</span><span class="sxs-lookup"><span data-stu-id="2acec-107">In ASP.NET Core, modules, handlers, *Global.asax.cs*, and the app life cycle are replaced with middleware.</span></span> <span data-ttu-id="2acec-108">在本章中，您將瞭解應用程式內容中的中介軟體 Blazor 。</span><span class="sxs-lookup"><span data-stu-id="2acec-108">In this chapter, you'll learn what middleware in the context of a Blazor app.</span></span>

## <a name="overview"></a><span data-ttu-id="2acec-109">概觀</span><span class="sxs-lookup"><span data-stu-id="2acec-109">Overview</span></span>

<span data-ttu-id="2acec-110">ASP.NET Core 要求管線由要求委派序列組成，並會一個接著一個呼叫。</span><span class="sxs-lookup"><span data-stu-id="2acec-110">The ASP.NET Core request pipeline consists of a sequence of request delegates, called one after the other.</span></span> <span data-ttu-id="2acec-111">下圖說明此概念。</span><span class="sxs-lookup"><span data-stu-id="2acec-111">The following diagram demonstrates the concept.</span></span> <span data-ttu-id="2acec-112">執行緒遵循黑色箭號執行。</span><span class="sxs-lookup"><span data-stu-id="2acec-112">The thread of execution follows the black arrows.</span></span>

![管線](media/middleware/request-delegate-pipeline.png)

<span data-ttu-id="2acec-114">上圖缺少生命週期事件的概念。</span><span class="sxs-lookup"><span data-stu-id="2acec-114">The preceding diagram lacks a concept of lifecycle events.</span></span> <span data-ttu-id="2acec-115">這是處理 ASP.NET Web Forms 要求的基礎概念。</span><span class="sxs-lookup"><span data-stu-id="2acec-115">This concept is foundational to how ASP.NET Web Forms requests are handled.</span></span> <span data-ttu-id="2acec-116">此系統可讓您更輕鬆地瞭解正在發生的進程，並允許在任何時間點插入中介軟體。</span><span class="sxs-lookup"><span data-stu-id="2acec-116">This system makes it easier to reason about what process is occurring and allows middleware to be inserted at any point.</span></span> <span data-ttu-id="2acec-117">中介軟體會依照將其新增至要求管線的順序來執行。</span><span class="sxs-lookup"><span data-stu-id="2acec-117">Middleware executes in the order in which it's added to the request pipeline.</span></span> <span data-ttu-id="2acec-118">它們也會以程式碼（而非設定檔）的方式加入，通常是在 *Startup.cs*中。</span><span class="sxs-lookup"><span data-stu-id="2acec-118">They're also added in code instead of configuration files, usually in *Startup.cs*.</span></span>

## <a name="katana"></a><span data-ttu-id="2acec-119">Katana</span><span class="sxs-lookup"><span data-stu-id="2acec-119">Katana</span></span>

<span data-ttu-id="2acec-120">熟悉 Katana 的讀者會覺得 ASP.NET Core 的習慣。</span><span class="sxs-lookup"><span data-stu-id="2acec-120">Readers familiar with Katana will feel comfortable in ASP.NET Core.</span></span> <span data-ttu-id="2acec-121">事實上，Katana 是從中衍生 ASP.NET Core 的架構。</span><span class="sxs-lookup"><span data-stu-id="2acec-121">In fact, Katana is a framework from which ASP.NET Core derives.</span></span> <span data-ttu-id="2acec-122">它導入了類似于 ASP.NET 4.x 的中介軟體和管線模式。</span><span class="sxs-lookup"><span data-stu-id="2acec-122">It introduced similar middleware and pipeline patterns for ASP.NET 4.x.</span></span> <span data-ttu-id="2acec-123">針對 Katana 而設計的中介軟體可以調整以搭配 ASP.NET Core 管線使用。</span><span class="sxs-lookup"><span data-stu-id="2acec-123">Middleware designed for Katana can be adapted to work with the ASP.NET Core pipeline.</span></span>

## <a name="common-middleware"></a><span data-ttu-id="2acec-124">一般中介軟體</span><span class="sxs-lookup"><span data-stu-id="2acec-124">Common middleware</span></span>

<span data-ttu-id="2acec-125">ASP.NET 4.x 包含許多模組。</span><span class="sxs-lookup"><span data-stu-id="2acec-125">ASP.NET 4.x includes many modules.</span></span> <span data-ttu-id="2acec-126">同樣地，ASP.NET Core 也有許多中介軟體元件可用。</span><span class="sxs-lookup"><span data-stu-id="2acec-126">In a similar fashion, ASP.NET Core has many middleware components available as well.</span></span> <span data-ttu-id="2acec-127">在某些情況下，IIS 模組可用於 ASP.NET Core。</span><span class="sxs-lookup"><span data-stu-id="2acec-127">IIS modules may be used in some cases with ASP.NET Core.</span></span> <span data-ttu-id="2acec-128">在其他情況下，可以使用原生 ASP.NET Core 中介軟體。</span><span class="sxs-lookup"><span data-stu-id="2acec-128">In other cases, native ASP.NET Core middleware may be available.</span></span>

<span data-ttu-id="2acec-129">下表列出 ASP.NET Core 中的更換中介軟體和元件。</span><span class="sxs-lookup"><span data-stu-id="2acec-129">The following table lists replacement middleware and components in ASP.NET Core.</span></span>

|<span data-ttu-id="2acec-130">模組</span><span class="sxs-lookup"><span data-stu-id="2acec-130">Module</span></span>                 |<span data-ttu-id="2acec-131">ASP.NET 4.x 模組</span><span class="sxs-lookup"><span data-stu-id="2acec-131">ASP.NET 4.x module</span></span>           |<span data-ttu-id="2acec-132">ASP.NET Core 選項</span><span class="sxs-lookup"><span data-stu-id="2acec-132">ASP.NET Core option</span></span>|
|-----------------------|-----------------------------|-------------------|
|<span data-ttu-id="2acec-133">HTTP 錯誤</span><span class="sxs-lookup"><span data-stu-id="2acec-133">HTTP errors</span></span>            |`CustomErrorModule`          |[<span data-ttu-id="2acec-134">狀態碼頁面中介軟體</span><span class="sxs-lookup"><span data-stu-id="2acec-134">Status Code Pages Middleware</span></span>](/aspnet/core/fundamentals/error-handling#usestatuscodepages)|
|<span data-ttu-id="2acec-135">預設文件</span><span class="sxs-lookup"><span data-stu-id="2acec-135">Default document</span></span>       |`DefaultDocumentModule`      |[<span data-ttu-id="2acec-136">預設檔案中介軟體</span><span class="sxs-lookup"><span data-stu-id="2acec-136">Default Files Middleware</span></span>](/aspnet/core/fundamentals/static-files#serve-a-default-document)|
|<span data-ttu-id="2acec-137">瀏覽目錄</span><span class="sxs-lookup"><span data-stu-id="2acec-137">Directory browsing</span></span>     |`DirectoryListingModule`     |[<span data-ttu-id="2acec-138">目錄瀏覽中介軟體</span><span class="sxs-lookup"><span data-stu-id="2acec-138">Directory Browsing Middleware</span></span>](/aspnet/core/fundamentals/static-files#enable-directory-browsing)|
|<span data-ttu-id="2acec-139">動態壓縮</span><span class="sxs-lookup"><span data-stu-id="2acec-139">Dynamic compression</span></span>    |`DynamicCompressionModule`   |[<span data-ttu-id="2acec-140">回應壓縮中介軟體</span><span class="sxs-lookup"><span data-stu-id="2acec-140">Response Compression Middleware</span></span>](/aspnet/core/performance/response-compression)|
|<span data-ttu-id="2acec-141">失敗的要求追蹤</span><span class="sxs-lookup"><span data-stu-id="2acec-141">Failed requests tracing</span></span>|`FailedRequestsTracingModule`|[<span data-ttu-id="2acec-142">ASP.NET Core 記錄</span><span class="sxs-lookup"><span data-stu-id="2acec-142">ASP.NET Core Logging</span></span>](/aspnet/core/fundamentals/logging/index#tracesource-provider)|
|<span data-ttu-id="2acec-143">檔案快取</span><span class="sxs-lookup"><span data-stu-id="2acec-143">File caching</span></span>           |`FileCacheModule`            |[<span data-ttu-id="2acec-144">回應快取中介軟體</span><span class="sxs-lookup"><span data-stu-id="2acec-144">Response Caching Middleware</span></span>](/aspnet/core/performance/caching/middleware)|
|<span data-ttu-id="2acec-145">HTTP 快取</span><span class="sxs-lookup"><span data-stu-id="2acec-145">HTTP caching</span></span>           |`HttpCacheModule`            |[<span data-ttu-id="2acec-146">回應快取中介軟體</span><span class="sxs-lookup"><span data-stu-id="2acec-146">Response Caching Middleware</span></span>](/aspnet/core/performance/caching/middleware)|
|<span data-ttu-id="2acec-147">HTTP 記錄</span><span class="sxs-lookup"><span data-stu-id="2acec-147">HTTP logging</span></span>           |`HttpLoggingModule`          |[<span data-ttu-id="2acec-148">ASP.NET Core 記錄</span><span class="sxs-lookup"><span data-stu-id="2acec-148">ASP.NET Core Logging</span></span>](/aspnet/core/fundamentals/logging/index)|
|<span data-ttu-id="2acec-149">HTTP 重新導向</span><span class="sxs-lookup"><span data-stu-id="2acec-149">HTTP redirection</span></span>       |`HttpRedirectionModule`      |[<span data-ttu-id="2acec-150">URL 重寫中介軟體</span><span class="sxs-lookup"><span data-stu-id="2acec-150">URL Rewriting Middleware</span></span>](/aspnet/core/fundamentals/url-rewriting)|
|<span data-ttu-id="2acec-151">ISAPI 篩選器</span><span class="sxs-lookup"><span data-stu-id="2acec-151">ISAPI filters</span></span>          |`IsapiFilterModule`          |[<span data-ttu-id="2acec-152">中介軟體</span><span class="sxs-lookup"><span data-stu-id="2acec-152">Middleware</span></span>](/aspnet/core/fundamentals/middleware/index)|
|<span data-ttu-id="2acec-153">ISAPI</span><span class="sxs-lookup"><span data-stu-id="2acec-153">ISAPI</span></span>                  |`IsapiModule`                |[<span data-ttu-id="2acec-154">中介軟體</span><span class="sxs-lookup"><span data-stu-id="2acec-154">Middleware</span></span>](/aspnet/core/fundamentals/middleware/index)|
|<span data-ttu-id="2acec-155">要求篩選</span><span class="sxs-lookup"><span data-stu-id="2acec-155">Request filtering</span></span>      |`RequestFilteringModule`     |[<span data-ttu-id="2acec-156">URL 重寫中介軟體 IRule</span><span class="sxs-lookup"><span data-stu-id="2acec-156">URL Rewriting Middleware IRule</span></span>](/aspnet/core/fundamentals/url-rewriting#irule-based-rule)|
|<span data-ttu-id="2acec-157">URL 重寫&#8224;</span><span class="sxs-lookup"><span data-stu-id="2acec-157">URL rewriting&#8224;</span></span>   |`RewriteModule`              |[<span data-ttu-id="2acec-158">URL 重寫中介軟體</span><span class="sxs-lookup"><span data-stu-id="2acec-158">URL Rewriting Middleware</span></span>](/aspnet/core/fundamentals/url-rewriting)|
|<span data-ttu-id="2acec-159">靜態壓縮</span><span class="sxs-lookup"><span data-stu-id="2acec-159">Static compression</span></span>     |`StaticCompressionModule`    |[<span data-ttu-id="2acec-160">回應壓縮中介軟體</span><span class="sxs-lookup"><span data-stu-id="2acec-160">Response Compression Middleware</span></span>](/aspnet/core/performance/response-compression)|
|<span data-ttu-id="2acec-161">靜態內容</span><span class="sxs-lookup"><span data-stu-id="2acec-161">Static content</span></span>         |`StaticFileModule`           |[<span data-ttu-id="2acec-162">靜態檔案中介軟體</span><span class="sxs-lookup"><span data-stu-id="2acec-162">Static File Middleware</span></span>](/aspnet/core/fundamentals/static-files)|
|<span data-ttu-id="2acec-163">URL 授權</span><span class="sxs-lookup"><span data-stu-id="2acec-163">URL authorization</span></span>      |`UrlAuthorizationModule`     |[<span data-ttu-id="2acec-164">ASP.NET Core 身分識別</span><span class="sxs-lookup"><span data-stu-id="2acec-164">ASP.NET Core Identity</span></span>](/aspnet/core/security/authentication/identity)|

<span data-ttu-id="2acec-165">這份清單並不完整，但應該要瞭解這兩個架構之間有何種對應存在。</span><span class="sxs-lookup"><span data-stu-id="2acec-165">This list isn't exhaustive but should give an idea of what mapping exists between the two frameworks.</span></span> <span data-ttu-id="2acec-166">如需更詳細的清單，請參閱 [具有 ASP.NET Core 的 IIS 模組](/aspnet/core/host-and-deploy/iis/modules)。</span><span class="sxs-lookup"><span data-stu-id="2acec-166">For a more detailed list, see [IIS modules with ASP.NET Core](/aspnet/core/host-and-deploy/iis/modules).</span></span>

## <a name="custom-middleware"></a><span data-ttu-id="2acec-167">自訂中介軟體</span><span class="sxs-lookup"><span data-stu-id="2acec-167">Custom middleware</span></span>

<span data-ttu-id="2acec-168">內建中介軟體可能不會處理應用程式所需的所有案例。</span><span class="sxs-lookup"><span data-stu-id="2acec-168">Built-in middleware may not handle all scenarios needed for an app.</span></span> <span data-ttu-id="2acec-169">在這種情況下，建立您自己的中介軟體是合理的。</span><span class="sxs-lookup"><span data-stu-id="2acec-169">In such cases, it makes sense to create your own middleware.</span></span> <span data-ttu-id="2acec-170">有多種方式可以定義中介軟體，最簡單的是簡單的委派。</span><span class="sxs-lookup"><span data-stu-id="2acec-170">There are multiple ways of defining middleware, with the simplest being a simple delegate.</span></span> <span data-ttu-id="2acec-171">請考慮下列中介軟體，其會接受來自查詢字串的文化要求：</span><span class="sxs-lookup"><span data-stu-id="2acec-171">Consider the following middleware, which accepts a culture request from a query string:</span></span>

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

<span data-ttu-id="2acec-172">中介軟體也可以藉由執行 `IMiddleware` 介面或依照中介軟體慣例，定義為類別。</span><span class="sxs-lookup"><span data-stu-id="2acec-172">Middleware can also be defined as class, either by implementing the `IMiddleware` interface or by following middleware convention.</span></span> <span data-ttu-id="2acec-173">如需詳細資訊，請參閱 [撰寫自訂 ASP.NET Core 中介軟體](/aspnet/core/fundamentals/middleware/write)。</span><span class="sxs-lookup"><span data-stu-id="2acec-173">For more information, see [Write custom ASP.NET Core middleware](/aspnet/core/fundamentals/middleware/write).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2acec-174">[上一個](data.md) 
>[下一步](config.md)</span><span class="sxs-lookup"><span data-stu-id="2acec-174">[Previous](data.md)
[Next](config.md)</span></span>
