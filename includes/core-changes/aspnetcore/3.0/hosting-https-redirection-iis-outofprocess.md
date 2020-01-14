---
ms.openlocfilehash: eb3fa768a491f6c0ff4b15479beabd71b0670338
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937266"
---
### <a name="hosting-https-redirection-enabled-for-iis-out-of-process-apps"></a><span data-ttu-id="80bef-101">裝載：已為 IIS 跨進程應用程式啟用 HTTPS 重新導向</span><span class="sxs-lookup"><span data-stu-id="80bef-101">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>

<span data-ttu-id="80bef-102">透過 IIS 跨進程裝載之[ASP.NET Core 模組（ANCM）](/aspnet/core/host-and-deploy/aspnet-core-module)的版本13.0.19218.0，可讓 ASP.NET Core 3.0 和2.2 應用程式使用現有的 HTTPS 重新導向功能。</span><span class="sxs-lookup"><span data-stu-id="80bef-102">Version 13.0.19218.0 of the [ASP.NET Core Module (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) for hosting via IIS out-of-process enables an existing HTTPS redirection feature for ASP.NET Core 3.0 and 2.2 apps.</span></span>

<span data-ttu-id="80bef-103">如需討論，請參閱[dotnet/AspNetCore # 15243](https://github.com/dotnet/AspNetCore/issues/15243)。</span><span class="sxs-lookup"><span data-stu-id="80bef-103">For discussion, see [dotnet/AspNetCore#15243](https://github.com/dotnet/AspNetCore/issues/15243).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="80bef-104">引進的版本</span><span class="sxs-lookup"><span data-stu-id="80bef-104">Version introduced</span></span>

<span data-ttu-id="80bef-105">3.0</span><span class="sxs-lookup"><span data-stu-id="80bef-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="80bef-106">舊的行為</span><span class="sxs-lookup"><span data-stu-id="80bef-106">Old behavior</span></span>

<span data-ttu-id="80bef-107">ASP.NET Core 2.1 專案範本會先引進 HTTPS 中介軟體方法（例如 <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> 和 <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>）的支援。</span><span class="sxs-lookup"><span data-stu-id="80bef-107">The ASP.NET Core 2.1 project template first introduced support for HTTPS middleware methods like <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> and <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>.</span></span> <span data-ttu-id="80bef-108">因為開發中的應用程式不會使用預設通訊埠443，所以啟用 HTTPS 重新導向需要新增設定。</span><span class="sxs-lookup"><span data-stu-id="80bef-108">Enabling HTTPS redirection required the addition of configuration, since apps in development don't use the default port of 443.</span></span> <span data-ttu-id="80bef-109">只有在要求已在使用 HTTPS 時， [HTTP Strict Transport Security （HSTS）](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html)才會處於作用中狀態。</span><span class="sxs-lookup"><span data-stu-id="80bef-109">[HTTP Strict Transport Security (HSTS)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) is active only if the request is already using HTTPS.</span></span> <span data-ttu-id="80bef-110">預設會略過 Localhost。</span><span class="sxs-lookup"><span data-stu-id="80bef-110">Localhost is skipped by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="80bef-111">新的行為</span><span class="sxs-lookup"><span data-stu-id="80bef-111">New behavior</span></span>

<span data-ttu-id="80bef-112">在 ASP.NET Core 3.0 中，已[增強](https://github.com/dotnet/AspNetCore/pull/4685)IIS HTTPS 案例。</span><span class="sxs-lookup"><span data-stu-id="80bef-112">In ASP.NET Core 3.0, the IIS HTTPS scenario was [enhanced](https://github.com/dotnet/AspNetCore/pull/4685).</span></span> <span data-ttu-id="80bef-113">有了增強功能，應用程式就可以探索伺服器的 HTTPS 埠，並根據預設讓 `UseHttpsRedirection` 的工作。</span><span class="sxs-lookup"><span data-stu-id="80bef-113">With the enhancement, an app could discover the server's HTTPS ports and make `UseHttpsRedirection` work by default.</span></span> <span data-ttu-id="80bef-114">同進程元件使用 `IServerAddresses` 功能完成埠探索，這只會影響 ASP.NET Core 3.0 應用程式，因為同進程程式庫是以架構建立版本。</span><span class="sxs-lookup"><span data-stu-id="80bef-114">The in-process component accomplished port discovery with the `IServerAddresses` feature, which only affects ASP.NET Core 3.0 apps because the in-process library is versioned with the framework.</span></span> <span data-ttu-id="80bef-115">跨進程元件已變更為自動新增 `ASPNETCORE_HTTPS_PORT` 環境變數。</span><span class="sxs-lookup"><span data-stu-id="80bef-115">The out-of-process component changed to automatically add the `ASPNETCORE_HTTPS_PORT` environment variable.</span></span> <span data-ttu-id="80bef-116">這項變更會影響 ASP.NET Core 2.2 和3.0 應用程式，因為跨進程元件會全域共用。</span><span class="sxs-lookup"><span data-stu-id="80bef-116">This change affected both ASP.NET Core 2.2 and 3.0 apps because the out-of-process component is shared globally.</span></span> <span data-ttu-id="80bef-117">ASP.NET Core 2.1 應用程式不會受到影響，因為預設會使用舊版的 ANCM。</span><span class="sxs-lookup"><span data-stu-id="80bef-117">ASP.NET Core 2.1 apps aren't affected because they use a prior version of ANCM by default.</span></span>

<span data-ttu-id="80bef-118">先前的行為已在 ASP.NET Core 3.0.1 和 3.1.0 Preview 3 中修改，以反轉 ASP.NET Core 2.x 中的行為變更。</span><span class="sxs-lookup"><span data-stu-id="80bef-118">The preceding behavior was modified in ASP.NET Core 3.0.1 and 3.1.0 Preview 3 to reverse the behavior changes in ASP.NET Core 2.x.</span></span> <span data-ttu-id="80bef-119">這些變更只會影響 IIS 跨進程應用程式。</span><span class="sxs-lookup"><span data-stu-id="80bef-119">These changes only affect IIS out-of-process apps.</span></span>

<span data-ttu-id="80bef-120">如上所述，安裝 ASP.NET Core 3.0.0，其副作用也是在 ASP.NET Core 2.x 應用程式中啟用 `UseHttpsRedirection` 中介軟體。</span><span class="sxs-lookup"><span data-stu-id="80bef-120">As detailed above, installing ASP.NET Core 3.0.0 had the side effect of also activating the `UseHttpsRedirection` middleware in ASP.NET Core 2.x apps.</span></span> <span data-ttu-id="80bef-121">已對 ASP.NET Core 3.0.1 和 3.1.0 Preview 3 中的 ANCM 進行變更，因此安裝它們不再對 ASP.NET Core 2.x 應用程式造成影響。</span><span class="sxs-lookup"><span data-stu-id="80bef-121">A change was made to ANCM in ASP.NET Core 3.0.1 and 3.1.0 Preview 3 such that installing them no longer has this effect on ASP.NET Core 2.x apps.</span></span> <span data-ttu-id="80bef-122">ANCM 填入 ASP.NET Core 3.0.0 中的 `ASPNETCORE_HTTPS_PORT` 環境變數，已變更為 ASP.NET Core 3.0.1 和 3.1.0 Preview 3 中的 `ASPNETCORE_ANCM_HTTPS_PORT`。</span><span class="sxs-lookup"><span data-stu-id="80bef-122">The `ASPNETCORE_HTTPS_PORT` environment variable that ANCM populated in ASP.NET Core 3.0.0 was changed to `ASPNETCORE_ANCM_HTTPS_PORT` in ASP.NET Core 3.0.1 and 3.1.0 Preview 3.</span></span> <span data-ttu-id="80bef-123">這些版本中的 `UseHttpsRedirection` 也會更新，以瞭解新的和舊的變數。</span><span class="sxs-lookup"><span data-stu-id="80bef-123">`UseHttpsRedirection` was also updated in these releases to understand both the new and old variables.</span></span> <span data-ttu-id="80bef-124">ASP.NET Core 2.x 不會更新。</span><span class="sxs-lookup"><span data-stu-id="80bef-124">ASP.NET Core 2.x won't be updated.</span></span> <span data-ttu-id="80bef-125">因此，它會還原成預設為停用的先前行為。</span><span class="sxs-lookup"><span data-stu-id="80bef-125">As a result, it reverts to the previous behavior of being disabled by default.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="80bef-126">變更的原因</span><span class="sxs-lookup"><span data-stu-id="80bef-126">Reason for change</span></span>

<span data-ttu-id="80bef-127">改良的 ASP.NET Core 3.0 功能。</span><span class="sxs-lookup"><span data-stu-id="80bef-127">Improved ASP.NET Core 3.0 functionality.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="80bef-128">建議的動作</span><span class="sxs-lookup"><span data-stu-id="80bef-128">Recommended action</span></span>

<span data-ttu-id="80bef-129">如果您想要讓所有用戶端使用 HTTPS，則不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="80bef-129">No action is required if you want all clients to use HTTPS.</span></span> <span data-ttu-id="80bef-130">若要允許某些用戶端使用 HTTP，請採取下列其中一個步驟：</span><span class="sxs-lookup"><span data-stu-id="80bef-130">To allow some clients to use HTTP, take one of the following steps:</span></span>

* <span data-ttu-id="80bef-131">從專案的 `Startup.Configure` 方法中，移除 `UseHttpsRedirection` 和 `UseHsts` 的呼叫，然後重新部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="80bef-131">Remove the calls to `UseHttpsRedirection` and `UseHsts` from your project's `Startup.Configure` method, and redeploy the app.</span></span>
* <span data-ttu-id="80bef-132">在 web.config*檔案*中，將 `ASPNETCORE_HTTPS_PORT` 環境變數設定為空字串。</span><span class="sxs-lookup"><span data-stu-id="80bef-132">In your *web.config* file, set the `ASPNETCORE_HTTPS_PORT` environment variable to an empty string.</span></span> <span data-ttu-id="80bef-133">這種變更可以直接在伺服器上進行，而不需要重新部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="80bef-133">This change can occur directly on the server without redeploying the app.</span></span> <span data-ttu-id="80bef-134">例如：</span><span class="sxs-lookup"><span data-stu-id="80bef-134">For example:</span></span>

    ```xml
    <aspNetCore processPath="dotnet" arguments=".\WebApplication3.dll" stdoutLogEnabled="false" stdoutLogFile="\\?\%home%\LogFiles\stdout" >
        <environmentVariables>
        <environmentVariable name="ASPNETCORE_HTTPS_PORT" value="" />
        </environmentVariables>
    </aspNetCore>
    ```

<span data-ttu-id="80bef-135">`UseHttpsRedirection` 仍然可以是：</span><span class="sxs-lookup"><span data-stu-id="80bef-135">`UseHttpsRedirection` can still be:</span></span>

* <span data-ttu-id="80bef-136">將 `ASPNETCORE_HTTPS_PORT` 環境變數設定為適當的埠號碼（在大部分的生產案例中為443），以手動方式在 ASP.NET Core 2.x 中啟用。</span><span class="sxs-lookup"><span data-stu-id="80bef-136">Activated manually in ASP.NET Core 2.x by setting the `ASPNETCORE_HTTPS_PORT` environment variable to the appropriate port number (443 in most production scenarios).</span></span>
* <span data-ttu-id="80bef-137">已在 ASP.NET Core 3.x 中停用，方法是定義具有空字串值的 `ASPNETCORE_ANCM_HTTPS_PORT`。</span><span class="sxs-lookup"><span data-stu-id="80bef-137">Deactivated in ASP.NET Core 3.x by defining `ASPNETCORE_ANCM_HTTPS_PORT` with an empty string value.</span></span> <span data-ttu-id="80bef-138">此值的設定方式與上述 `ASPNETCORE_HTTPS_PORT` 範例相同。</span><span class="sxs-lookup"><span data-stu-id="80bef-138">This value is set in the same fashion as the preceding `ASPNETCORE_HTTPS_PORT` example.</span></span>

<span data-ttu-id="80bef-139">執行 ASP.NET Core 3.0.0 應用程式的電腦應該先安裝 ASP.NET Core 3.0.1 執行時間，再安裝 ASP.NET Core 3.1.0 Preview 3 ANCM。</span><span class="sxs-lookup"><span data-stu-id="80bef-139">Machines running ASP.NET Core 3.0.0 apps should install the ASP.NET Core 3.0.1 runtime before installing the ASP.NET Core 3.1.0 Preview 3 ANCM.</span></span> <span data-ttu-id="80bef-140">這麼做可確保 ASP.NET Core 3.0 應用程式的 `UseHttpsRedirection` 繼續如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="80bef-140">Doing so ensures that `UseHttpsRedirection` continues to operate as expected for the ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="80bef-141">在 Azure App Service 中，ANCM 會根據其全域性質，從執行時間部署成獨立的排程。</span><span class="sxs-lookup"><span data-stu-id="80bef-141">In Azure App Service, ANCM deploys on a separate schedule from the runtime because of its global nature.</span></span> <span data-ttu-id="80bef-142">ANCM 已部署至 Azure，並在部署 ASP.NET Core 3.0.1 和3.1.0 之後進行這些變更。</span><span class="sxs-lookup"><span data-stu-id="80bef-142">ANCM was deployed to Azure with these changes after ASP.NET Core 3.0.1 and 3.1.0 were deployed.</span></span>

#### <a name="category"></a><span data-ttu-id="80bef-143">分類</span><span class="sxs-lookup"><span data-stu-id="80bef-143">Category</span></span>

<span data-ttu-id="80bef-144">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="80bef-144">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="80bef-145">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="80bef-145">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)`

-->
