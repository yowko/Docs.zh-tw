---
ms.openlocfilehash: eb3fa768a491f6c0ff4b15479beabd71b0670338
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937266"
---
### <a name="hosting-https-redirection-enabled-for-iis-out-of-process-apps"></a><span data-ttu-id="d4e83-101">託管：為 IIS 進程外應用啟用 HTTPS 重定向</span><span class="sxs-lookup"><span data-stu-id="d4e83-101">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>

<span data-ttu-id="d4e83-102">[ASP.NET核心模組 （ANCM）](/aspnet/core/host-and-deploy/aspnet-core-module)的 13.0.19218.0 版本通過 IIS 進程外託管，可為 ASP.NET Core 3.0 和 2.2 應用提供現有的 HTTPS 重定向功能。</span><span class="sxs-lookup"><span data-stu-id="d4e83-102">Version 13.0.19218.0 of the [ASP.NET Core Module (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) for hosting via IIS out-of-process enables an existing HTTPS redirection feature for ASP.NET Core 3.0 and 2.2 apps.</span></span>

<span data-ttu-id="d4e83-103">有關討論，請參閱[點網/阿斯普內科#15243](https://github.com/dotnet/AspNetCore/issues/15243)。</span><span class="sxs-lookup"><span data-stu-id="d4e83-103">For discussion, see [dotnet/AspNetCore#15243](https://github.com/dotnet/AspNetCore/issues/15243).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d4e83-104">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="d4e83-104">Version introduced</span></span>

<span data-ttu-id="d4e83-105">3.0</span><span class="sxs-lookup"><span data-stu-id="d4e83-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d4e83-106">舊的行為</span><span class="sxs-lookup"><span data-stu-id="d4e83-106">Old behavior</span></span>

<span data-ttu-id="d4e83-107">ASP.NET Core 2.1 專案範本首先引入了對 HTTPS 中間<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A>件<xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>方法（如 和） 的支援。</span><span class="sxs-lookup"><span data-stu-id="d4e83-107">The ASP.NET Core 2.1 project template first introduced support for HTTPS middleware methods like <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> and <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>.</span></span> <span data-ttu-id="d4e83-108">啟用 HTTPS 重定向需要添加配置，因為開發中的應用不使用預設埠 443。</span><span class="sxs-lookup"><span data-stu-id="d4e83-108">Enabling HTTPS redirection required the addition of configuration, since apps in development don't use the default port of 443.</span></span> <span data-ttu-id="d4e83-109">[HTTP 嚴格傳輸安全 （HSTS）](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html)僅在請求已在使用 HTTPS 時才處於活動狀態。</span><span class="sxs-lookup"><span data-stu-id="d4e83-109">[HTTP Strict Transport Security (HSTS)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) is active only if the request is already using HTTPS.</span></span> <span data-ttu-id="d4e83-110">預設情況下，將跳過本地主機。</span><span class="sxs-lookup"><span data-stu-id="d4e83-110">Localhost is skipped by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d4e83-111">新的行為</span><span class="sxs-lookup"><span data-stu-id="d4e83-111">New behavior</span></span>

<span data-ttu-id="d4e83-112">在 ASP.NET 核心 3.0 中，IIS HTTPS 方案[得到了增強](https://github.com/dotnet/AspNetCore/pull/4685)。</span><span class="sxs-lookup"><span data-stu-id="d4e83-112">In ASP.NET Core 3.0, the IIS HTTPS scenario was [enhanced](https://github.com/dotnet/AspNetCore/pull/4685).</span></span> <span data-ttu-id="d4e83-113">通過增強功能，應用可以發現伺服器的 HTTPS 埠，並在預設情況下`UseHttpsRedirection`工作時正常工作。</span><span class="sxs-lookup"><span data-stu-id="d4e83-113">With the enhancement, an app could discover the server's HTTPS ports and make `UseHttpsRedirection` work by default.</span></span> <span data-ttu-id="d4e83-114">進程內元件使用`IServerAddresses`該功能完成了埠發現，該功能僅影響 ASP.NET Core 3.0 應用，因為進程內庫使用框架進行版本控制。</span><span class="sxs-lookup"><span data-stu-id="d4e83-114">The in-process component accomplished port discovery with the `IServerAddresses` feature, which only affects ASP.NET Core 3.0 apps because the in-process library is versioned with the framework.</span></span> <span data-ttu-id="d4e83-115">進程外元件更改為自動添加`ASPNETCORE_HTTPS_PORT`環境變數。</span><span class="sxs-lookup"><span data-stu-id="d4e83-115">The out-of-process component changed to automatically add the `ASPNETCORE_HTTPS_PORT` environment variable.</span></span> <span data-ttu-id="d4e83-116">此更改ASP.NET酷睿 2.2 和 3.0 應用都受到影響，因為進程外元件全域共用。</span><span class="sxs-lookup"><span data-stu-id="d4e83-116">This change affected both ASP.NET Core 2.2 and 3.0 apps because the out-of-process component is shared globally.</span></span> <span data-ttu-id="d4e83-117">ASP.NET Core 2.1 應用不受影響，因為它們預設使用以前的 ANCM 版本。</span><span class="sxs-lookup"><span data-stu-id="d4e83-117">ASP.NET Core 2.1 apps aren't affected because they use a prior version of ANCM by default.</span></span>

<span data-ttu-id="d4e83-118">ASP.NET Core 3.0.1 和 3.1.0 預覽 3 中修改了上述行為，以反轉 ASP.NET Core 2.x 中的行為更改。</span><span class="sxs-lookup"><span data-stu-id="d4e83-118">The preceding behavior was modified in ASP.NET Core 3.0.1 and 3.1.0 Preview 3 to reverse the behavior changes in ASP.NET Core 2.x.</span></span> <span data-ttu-id="d4e83-119">這些更改僅影響 IIS 進程外應用。</span><span class="sxs-lookup"><span data-stu-id="d4e83-119">These changes only affect IIS out-of-process apps.</span></span>

<span data-ttu-id="d4e83-120">如上所述，安裝ASP.NET Core 3.0.0 具有啟動ASP.NET Core 2.x 應用程式中`UseHttpsRedirection`的中介軟體的副作用。</span><span class="sxs-lookup"><span data-stu-id="d4e83-120">As detailed above, installing ASP.NET Core 3.0.0 had the side effect of also activating the `UseHttpsRedirection` middleware in ASP.NET Core 2.x apps.</span></span> <span data-ttu-id="d4e83-121">ASP.NET酷睿 3.0.1 和 3.1.0 預覽 3 中對 ANCM 進行了更改，以便安裝它們不再對 ASP.NET 酷睿 2.x 應用產生此影響。</span><span class="sxs-lookup"><span data-stu-id="d4e83-121">A change was made to ANCM in ASP.NET Core 3.0.1 and 3.1.0 Preview 3 such that installing them no longer has this effect on ASP.NET Core 2.x apps.</span></span> <span data-ttu-id="d4e83-122">ASP.NET `ASPNETCORE_HTTPS_PORT` Core 3.0.0 中填充的 ANCM 的環境`ASPNETCORE_ANCM_HTTPS_PORT`變數在 ASP.NET 酷 3.0.1 和 3.1.0 預覽 3 中更改為。</span><span class="sxs-lookup"><span data-stu-id="d4e83-122">The `ASPNETCORE_HTTPS_PORT` environment variable that ANCM populated in ASP.NET Core 3.0.0 was changed to `ASPNETCORE_ANCM_HTTPS_PORT` in ASP.NET Core 3.0.1 and 3.1.0 Preview 3.</span></span> <span data-ttu-id="d4e83-123">`UseHttpsRedirection`也在這些版本中更新，以瞭解新舊變數。</span><span class="sxs-lookup"><span data-stu-id="d4e83-123">`UseHttpsRedirection` was also updated in these releases to understand both the new and old variables.</span></span> <span data-ttu-id="d4e83-124">ASP.NET核心 2.x 不會更新。</span><span class="sxs-lookup"><span data-stu-id="d4e83-124">ASP.NET Core 2.x won't be updated.</span></span> <span data-ttu-id="d4e83-125">因此，它將恢復為預設情況下禁用的前一個行為。</span><span class="sxs-lookup"><span data-stu-id="d4e83-125">As a result, it reverts to the previous behavior of being disabled by default.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d4e83-126">更改原因</span><span class="sxs-lookup"><span data-stu-id="d4e83-126">Reason for change</span></span>

<span data-ttu-id="d4e83-127">改進了ASP.NET核心 3.0 功能。</span><span class="sxs-lookup"><span data-stu-id="d4e83-127">Improved ASP.NET Core 3.0 functionality.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d4e83-128">建議的動作</span><span class="sxs-lookup"><span data-stu-id="d4e83-128">Recommended action</span></span>

<span data-ttu-id="d4e83-129">如果希望所有用戶端都使用 HTTPS，則無需執行任何操作。</span><span class="sxs-lookup"><span data-stu-id="d4e83-129">No action is required if you want all clients to use HTTPS.</span></span> <span data-ttu-id="d4e83-130">要允許某些用戶端使用 HTTP，請執行以下步驟之一：</span><span class="sxs-lookup"><span data-stu-id="d4e83-130">To allow some clients to use HTTP, take one of the following steps:</span></span>

* <span data-ttu-id="d4e83-131">刪除對`UseHttpsRedirection`專案`UseHsts``Startup.Configure`方法的調用，然後重新部署應用。</span><span class="sxs-lookup"><span data-stu-id="d4e83-131">Remove the calls to `UseHttpsRedirection` and `UseHsts` from your project's `Startup.Configure` method, and redeploy the app.</span></span>
* <span data-ttu-id="d4e83-132">在*Web.config 檔中*，將`ASPNETCORE_HTTPS_PORT`環境變數設置為空字串。</span><span class="sxs-lookup"><span data-stu-id="d4e83-132">In your *web.config* file, set the `ASPNETCORE_HTTPS_PORT` environment variable to an empty string.</span></span> <span data-ttu-id="d4e83-133">此更改可以直接在伺服器上發生，而無需重新部署應用。</span><span class="sxs-lookup"><span data-stu-id="d4e83-133">This change can occur directly on the server without redeploying the app.</span></span> <span data-ttu-id="d4e83-134">例如：</span><span class="sxs-lookup"><span data-stu-id="d4e83-134">For example:</span></span>

    ```xml
    <aspNetCore processPath="dotnet" arguments=".\WebApplication3.dll" stdoutLogEnabled="false" stdoutLogFile="\\?\%home%\LogFiles\stdout" >
        <environmentVariables>
        <environmentVariable name="ASPNETCORE_HTTPS_PORT" value="" />
        </environmentVariables>
    </aspNetCore>
    ```

<span data-ttu-id="d4e83-135">`UseHttpsRedirection`仍然可以：</span><span class="sxs-lookup"><span data-stu-id="d4e83-135">`UseHttpsRedirection` can still be:</span></span>

* <span data-ttu-id="d4e83-136">通過將`ASPNETCORE_HTTPS_PORT`環境變數設置為相應的埠號（在大多數生產方案中為 443），在 ASP.NET Core 2.x 中手動啟動。</span><span class="sxs-lookup"><span data-stu-id="d4e83-136">Activated manually in ASP.NET Core 2.x by setting the `ASPNETCORE_HTTPS_PORT` environment variable to the appropriate port number (443 in most production scenarios).</span></span>
* <span data-ttu-id="d4e83-137">使用空字串值定義`ASPNETCORE_ANCM_HTTPS_PORT`ASP.NET Core 3.x 中停用。</span><span class="sxs-lookup"><span data-stu-id="d4e83-137">Deactivated in ASP.NET Core 3.x by defining `ASPNETCORE_ANCM_HTTPS_PORT` with an empty string value.</span></span> <span data-ttu-id="d4e83-138">此值的設置方式與前面的`ASPNETCORE_HTTPS_PORT`示例相同。</span><span class="sxs-lookup"><span data-stu-id="d4e83-138">This value is set in the same fashion as the preceding `ASPNETCORE_HTTPS_PORT` example.</span></span>

<span data-ttu-id="d4e83-139">運行ASP.NET酷睿 3.0.0 應用的電腦在安裝 ASP.NET 酷睿 3.1.0 預覽 3 ANCM 之前，應安裝ASP.NET酷睿 3.0.1 運行時。</span><span class="sxs-lookup"><span data-stu-id="d4e83-139">Machines running ASP.NET Core 3.0.0 apps should install the ASP.NET Core 3.0.1 runtime before installing the ASP.NET Core 3.1.0 Preview 3 ANCM.</span></span> <span data-ttu-id="d4e83-140">這樣做可確保`UseHttpsRedirection`繼續按預期運行ASP.NET酷睿 3.0 應用。</span><span class="sxs-lookup"><span data-stu-id="d4e83-140">Doing so ensures that `UseHttpsRedirection` continues to operate as expected for the ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="d4e83-141">在 Azure 應用服務中，ANCM 由於其全域性，在獨立于運行時的計畫中部署。</span><span class="sxs-lookup"><span data-stu-id="d4e83-141">In Azure App Service, ANCM deploys on a separate schedule from the runtime because of its global nature.</span></span> <span data-ttu-id="d4e83-142">在部署了ASP.NET Core 3.0.1 和 3.1.0 之後，ANCM 已部署到 Azure 中。</span><span class="sxs-lookup"><span data-stu-id="d4e83-142">ANCM was deployed to Azure with these changes after ASP.NET Core 3.0.1 and 3.1.0 were deployed.</span></span>

#### <a name="category"></a><span data-ttu-id="d4e83-143">類別</span><span class="sxs-lookup"><span data-stu-id="d4e83-143">Category</span></span>

<span data-ttu-id="d4e83-144">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d4e83-144">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d4e83-145">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d4e83-145">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)`

-->
