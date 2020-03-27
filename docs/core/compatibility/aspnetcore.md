---
title: ASP.NET核心突破性更改
titleSuffix: ''
description: 列出ASP.NET核心中的重大更改。
ms.date: 03/26/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: 05272032f2b93c8ae89377a20e6fdafc2ff0eb7b
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345332"
---
# <a name="aspnet-core-breaking-changes"></a><span data-ttu-id="c9dcb-103">ASP.NET核心突破性更改</span><span class="sxs-lookup"><span data-stu-id="c9dcb-103">ASP.NET Core breaking changes</span></span>

<span data-ttu-id="c9dcb-104">ASP.NET核心提供 .NET Core 使用的 Web 應用開發功能。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-104">ASP.NET Core provides the web app development features used by .NET Core.</span></span>

<span data-ttu-id="c9dcb-105">此頁面將記錄以下重大更改：</span><span class="sxs-lookup"><span data-stu-id="c9dcb-105">The following breaking changes are documented on this page:</span></span>

- [<span data-ttu-id="c9dcb-106">已刪除的過期反偽造、CORS、診斷、MVC 和路由 API</span><span class="sxs-lookup"><span data-stu-id="c9dcb-106">Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed</span></span>](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [<span data-ttu-id="c9dcb-107">身份驗證：Google+ 棄用</span><span class="sxs-lookup"><span data-stu-id="c9dcb-107">Authentication: Google+ deprecation</span></span>](#authentication-google-deprecated-and-replaced)
- [<span data-ttu-id="c9dcb-108">身份驗證：HTTPCoNtext.身份驗證屬性已刪除</span><span class="sxs-lookup"><span data-stu-id="c9dcb-108">Authentication: HttpContext.Authentication property removed</span></span>](#authentication-httpcontextauthentication-property-removed)
- [<span data-ttu-id="c9dcb-109">身份驗證：牛頓軟.Json 類型替換</span><span class="sxs-lookup"><span data-stu-id="c9dcb-109">Authentication: Newtonsoft.Json types replaced</span></span>](#authentication-newtonsoftjson-types-replaced)
- [<span data-ttu-id="c9dcb-110">身份驗證：OAuthHandler 交換代碼同步簽名已更改</span><span class="sxs-lookup"><span data-stu-id="c9dcb-110">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [<span data-ttu-id="c9dcb-111">授權：將授權重載移動到不同的程式集</span><span class="sxs-lookup"><span data-stu-id="c9dcb-111">Authorization: AddAuthorization overload moved to different assembly</span></span>](#authorization-addauthorization-overload-moved-to-different-assembly)
- [<span data-ttu-id="c9dcb-112">授權：從授權篩選器上下文中刪除 IAllowAnonymous。篩檢程式</span><span class="sxs-lookup"><span data-stu-id="c9dcb-112">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [<span data-ttu-id="c9dcb-113">授權：I授權策略提供程式實現需要新方法</span><span class="sxs-lookup"><span data-stu-id="c9dcb-113">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [<span data-ttu-id="c9dcb-114">Azure：已刪除 Microsoft 預固定的 Azure 集成包</span><span class="sxs-lookup"><span data-stu-id="c9dcb-114">Azure: Microsoft-prefixed Azure integration packages removed</span></span>](#azure-microsoft-prefixed-azure-integration-packages-removed)
- [<span data-ttu-id="c9dcb-115">緩存：已刪除 CompactOn 記憶體壓力屬性</span><span class="sxs-lookup"><span data-stu-id="c9dcb-115">Caching: CompactOnMemoryPressure property removed</span></span>](#caching-compactonmemorypressure-property-removed)
- [<span data-ttu-id="c9dcb-116">緩存：微軟.擴展.緩存.SqlServer 使用新的 SqlClient 包</span><span class="sxs-lookup"><span data-stu-id="c9dcb-116">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [<span data-ttu-id="c9dcb-117">緩存：回應緩存"公共"類型更改為內部</span><span class="sxs-lookup"><span data-stu-id="c9dcb-117">Caching: ResponseCaching "pubternal" types changed to internal</span></span>](#caching-responsecaching-pubternal-types-changed-to-internal)
- [<span data-ttu-id="c9dcb-118">資料保護：資料保護.Azure 存儲使用新的 Azure 存儲 API</span><span class="sxs-lookup"><span data-stu-id="c9dcb-118">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [<span data-ttu-id="c9dcb-119">託管：從 Windows 託管捆綁包中刪除的 AspNetCore 模組 V1</span><span class="sxs-lookup"><span data-stu-id="c9dcb-119">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [<span data-ttu-id="c9dcb-120">託管：通用主機限制啟動建構函式注入</span><span class="sxs-lookup"><span data-stu-id="c9dcb-120">Hosting: Generic host restricts Startup constructor injection</span></span>](#hosting-generic-host-restricts-startup-constructor-injection)
- [<span data-ttu-id="c9dcb-121">託管：為 IIS 進程外應用啟用 HTTPS 重定向</span><span class="sxs-lookup"><span data-stu-id="c9dcb-121">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [<span data-ttu-id="c9dcb-122">託管：已替換 IHosting 環境和 I應用程式生命週期類型</span><span class="sxs-lookup"><span data-stu-id="c9dcb-122">Hosting: IHostingEnvironment and IApplicationLifetime types replaced</span></span>](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="c9dcb-123">託管：從 WebHostBuilder 依賴項中刪除物件集區提供程式</span><span class="sxs-lookup"><span data-stu-id="c9dcb-123">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [<span data-ttu-id="c9dcb-124">HTTP： 瀏覽器同網站更改影響身份驗證</span><span class="sxs-lookup"><span data-stu-id="c9dcb-124">HTTP: Browser SameSite changes impact authentication</span></span>](#http-browser-samesite-changes-impact-authentication)
- [<span data-ttu-id="c9dcb-125">HTTP： 預設 HttpCoNtext 擴充性已被刪除</span><span class="sxs-lookup"><span data-stu-id="c9dcb-125">HTTP: DefaultHttpContext extensibility removed</span></span>](#http-defaulthttpcontext-extensibility-removed)
- [<span data-ttu-id="c9dcb-126">HTTP：標題名稱欄位更改為靜態唯讀</span><span class="sxs-lookup"><span data-stu-id="c9dcb-126">HTTP: HeaderNames fields changed to static readonly</span></span>](#http-headernames-constants-changed-to-static-readonly)
- [<span data-ttu-id="c9dcb-127">HTTP：回應正文基礎結構更改</span><span class="sxs-lookup"><span data-stu-id="c9dcb-127">HTTP: Response body infrastructure changes</span></span>](#http-response-body-infrastructure-changes)
- [<span data-ttu-id="c9dcb-128">HTTP： 某些 Cookie 同網站預設值已更改</span><span class="sxs-lookup"><span data-stu-id="c9dcb-128">HTTP: Some cookie SameSite default values changed</span></span>](#http-some-cookie-samesite-defaults-changed-to-none)
- [<span data-ttu-id="c9dcb-129">HTTP：預設情況下禁用同步 IO</span><span class="sxs-lookup"><span data-stu-id="c9dcb-129">HTTP: Synchronous IO disabled by default</span></span>](#http-synchronous-io-disabled-in-all-servers)
- [<span data-ttu-id="c9dcb-130">標識：刪除添加 DefaultUI 方法重載</span><span class="sxs-lookup"><span data-stu-id="c9dcb-130">Identity: AddDefaultUI method overload removed</span></span>](#identity-adddefaultui-method-overload-removed)
- [<span data-ttu-id="c9dcb-131">標識：UI 引導版本更改</span><span class="sxs-lookup"><span data-stu-id="c9dcb-131">Identity: UI Bootstrap version change</span></span>](#identity-default-bootstrap-version-of-ui-changed)
- [<span data-ttu-id="c9dcb-132">標識：SignInAsync 為未身份驗證的標識引發異常</span><span class="sxs-lookup"><span data-stu-id="c9dcb-132">Identity: SignInAsync throws exception for unauthenticated identity</span></span>](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [<span data-ttu-id="c9dcb-133">標識：SignInManager 建構函式接受新參數</span><span class="sxs-lookup"><span data-stu-id="c9dcb-133">Identity: SignInManager constructor accepts new parameter</span></span>](#identity-signinmanager-constructor-accepts-new-parameter)
- [<span data-ttu-id="c9dcb-134">標識：UI 使用靜態 Web 資產功能</span><span class="sxs-lookup"><span data-stu-id="c9dcb-134">Identity: UI uses static web assets feature</span></span>](#identity-ui-uses-static-web-assets-feature)
- [<span data-ttu-id="c9dcb-135">Kestrel：連接配接器已移除</span><span class="sxs-lookup"><span data-stu-id="c9dcb-135">Kestrel: Connection adapters removed</span></span>](#kestrel-connection-adapters-removed)
- [<span data-ttu-id="c9dcb-136">Kestrel： 空 HTTPS 程式集已刪除</span><span class="sxs-lookup"><span data-stu-id="c9dcb-136">Kestrel: Empty HTTPS assembly removed</span></span>](#kestrel-empty-https-assembly-removed)
- [<span data-ttu-id="c9dcb-137">Kestrel：請求將拖車頭移動到新集合</span><span class="sxs-lookup"><span data-stu-id="c9dcb-137">Kestrel: Request trailer headers moved to new collection</span></span>](#kestrel-request-trailer-headers-moved-to-new-collection)
- [<span data-ttu-id="c9dcb-138">Kestrel：傳輸抽象層更改</span><span class="sxs-lookup"><span data-stu-id="c9dcb-138">Kestrel: Transport abstraction layer changes</span></span>](#kestrel-transport-abstractions-removed-and-made-public)
- [<span data-ttu-id="c9dcb-139">當地語系化：標記為過時的 API</span><span class="sxs-lookup"><span data-stu-id="c9dcb-139">Localization: APIs marked obsolete</span></span>](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [<span data-ttu-id="c9dcb-140">日誌記錄：調試記錄器類是內部製作的</span><span class="sxs-lookup"><span data-stu-id="c9dcb-140">Logging: DebugLogger class made internal</span></span>](#logging-debuglogger-class-made-internal)
- [<span data-ttu-id="c9dcb-141">MVC：已刪除控制器操作非同步尾碼</span><span class="sxs-lookup"><span data-stu-id="c9dcb-141">MVC: Controller action Async suffix removed</span></span>](#mvc-async-suffix-trimmed-from-controller-action-names)
- [<span data-ttu-id="c9dcb-142">MVC： JsonResult 移動到微軟.AspNetCore.Mvc.Core</span><span class="sxs-lookup"><span data-stu-id="c9dcb-142">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [<span data-ttu-id="c9dcb-143">MVC：預編譯工具已棄用</span><span class="sxs-lookup"><span data-stu-id="c9dcb-143">MVC: Precompilation tool deprecated</span></span>](#mvc-precompilation-tool-deprecated)
- [<span data-ttu-id="c9dcb-144">MVC：類型更改為內部</span><span class="sxs-lookup"><span data-stu-id="c9dcb-144">MVC: Types changed to internal</span></span>](#mvc-pubternal-types-changed-to-internal)
- [<span data-ttu-id="c9dcb-145">MVC：已刪除 Web API 相容性</span><span class="sxs-lookup"><span data-stu-id="c9dcb-145">MVC: Web API compatibility shim removed</span></span>](#mvc-web-api-compatibility-shim-removed)
- [<span data-ttu-id="c9dcb-146">Razor：運行時編譯移動到包</span><span class="sxs-lookup"><span data-stu-id="c9dcb-146">Razor: Runtime compilation moved to a package</span></span>](#razor-runtime-compilation-moved-to-a-package)
- [<span data-ttu-id="c9dcb-147">會話狀態：已刪除的已過期 API</span><span class="sxs-lookup"><span data-stu-id="c9dcb-147">Session state: Obsolete APIs removed</span></span>](#session-state-obsolete-apis-removed)
- [<span data-ttu-id="c9dcb-148">共用框架：從 Microsoft 中刪除程式集.AspNetCore.App</span><span class="sxs-lookup"><span data-stu-id="c9dcb-148">Shared framework: Assembly removal from Microsoft.AspNetCore.App</span></span>](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [<span data-ttu-id="c9dcb-149">共用框架：微軟.AspNetCore.全部刪除</span><span class="sxs-lookup"><span data-stu-id="c9dcb-149">Shared framework: Microsoft.AspNetCore.All removed</span></span>](#shared-framework-removed-microsoftaspnetcoreall)
- [<span data-ttu-id="c9dcb-150">信號R：握手協定.成功握手資料被替換</span><span class="sxs-lookup"><span data-stu-id="c9dcb-150">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [<span data-ttu-id="c9dcb-151">信號R：已刪除集線器連接方法</span><span class="sxs-lookup"><span data-stu-id="c9dcb-151">SignalR: HubConnection methods removed</span></span>](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [<span data-ttu-id="c9dcb-152">信號R：中心連接上下文建構函式已更改</span><span class="sxs-lookup"><span data-stu-id="c9dcb-152">SignalR: HubConnectionContext constructors changed</span></span>](#signalr-hubconnectioncontext-constructors-changed)
- [<span data-ttu-id="c9dcb-153">信號R：JavaScript用戶端包名稱更改</span><span class="sxs-lookup"><span data-stu-id="c9dcb-153">SignalR: JavaScript client package name change</span></span>](#signalr-javascript-client-package-name-changed)
- [<span data-ttu-id="c9dcb-154">信號R：MessagePack集線器協定移動到消息包 2.x 包</span><span class="sxs-lookup"><span data-stu-id="c9dcb-154">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>](#signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package)
- [<span data-ttu-id="c9dcb-155">信號R：過時的 API</span><span class="sxs-lookup"><span data-stu-id="c9dcb-155">SignalR: Obsolete APIs</span></span>](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [<span data-ttu-id="c9dcb-156">信號R：使用信號R和使用連接方法被刪除</span><span class="sxs-lookup"><span data-stu-id="c9dcb-156">SignalR: UseSignalR and UseConnections methods removed</span></span>](#signalr-usesignalr-and-useconnections-methods-removed)
- [<span data-ttu-id="c9dcb-157">Spa服務和節點服務主控台記錄器回退預設更改</span><span class="sxs-lookup"><span data-stu-id="c9dcb-157">SPAs: SpaServices and NodeServices console logger fallback default change</span></span>](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [<span data-ttu-id="c9dcb-158">Spa 服務：標記為過時的 Spa 服務和節點服務</span><span class="sxs-lookup"><span data-stu-id="c9dcb-158">SPAs: SpaServices and NodeServices marked obsolete</span></span>](#spas-spaservices-and-nodeservices-marked-obsolete)
- [<span data-ttu-id="c9dcb-159">目標框架： .NET 框架不支援</span><span class="sxs-lookup"><span data-stu-id="c9dcb-159">Target framework: .NET Framework not supported</span></span>](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-50"></a><span data-ttu-id="c9dcb-160">ASP.NET核心 5.0</span><span class="sxs-lookup"><span data-stu-id="c9dcb-160">ASP.NET Core 5.0</span></span>

[!INCLUDE[Azure: Microsoft-prefixed Azure integration packages removed](~/includes/core-changes/aspnetcore/5.0/azure-integration-packages-removed.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-package.md)]

***

[!INCLUDE[SignalR: UseSignalR and UseConnections methods removed](~/includes/core-changes/aspnetcore/5.0/signalr-usesignalr-useconnections-removed.md)]

***

## <a name="aspnet-core-31"></a><span data-ttu-id="c9dcb-161">ASP.NET核心 3.1</span><span class="sxs-lookup"><span data-stu-id="c9dcb-161">ASP.NET Core 3.1</span></span>

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a><span data-ttu-id="c9dcb-162">ASP.NET核心 3.0</span><span class="sxs-lookup"><span data-stu-id="c9dcb-162">ASP.NET Core 3.0</span></span>

[!INCLUDE[Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed](~/includes/core-changes/aspnetcore/3.0/obsolete-apis-removed.md)]

***

[!INCLUDE[Authentication: Google+ deprecation](~/includes/core-changes/aspnetcore/3.0/authn-google-plus-authn-changes.md)]

***

[!INCLUDE[Authentication: HttpContext.Authentication property removed](~/includes/core-changes/aspnetcore/3.0/authn-httpcontext-property-removed.md)]

***

[!INCLUDE[Authentication: Newtonsoft.Json types replaced](~/includes/core-changes/aspnetcore/3.0/authn-apis-json-types.md)]

***

[!INCLUDE[Authentication: OAuthHandler ExchangeCodeAsync signature changed](~/includes/core-changes/aspnetcore/3.0/authn-exchangecodeasync-signature-change.md)]

***

[!INCLUDE[Authorization: AddAuthorization overload assembly change](~/includes/core-changes/aspnetcore/3.0/authz-assembly-change.md)]

***

[!INCLUDE[Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters](~/includes/core-changes/aspnetcore/3.0/authz-iallowanonymous-removed-from-collection.md)]

***

[!INCLUDE[Authorization: IAuthorizationPolicyProvider implementations require new method](~/includes/core-changes/aspnetcore/3.0/authz-iauthzpolicyprovider-new-method.md)]

***

[!INCLUDE[Caching: CompactOnMemoryPressure property removed](~/includes/core-changes/aspnetcore/3.0/caching-memory-property-removed.md)]

***

[!INCLUDE[Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package](~/includes/core-changes/aspnetcore/3.0/caching-new-sqlclient-package.md)]

***

[!INCLUDE[Caching: ResponseCaching types changed to internal](~/includes/core-changes/aspnetcore/3.0/caching-response-pubternal-to-internal.md)]

***

[!INCLUDE[Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs](~/includes/core-changes/aspnetcore/3.0/dataprotection-azstorage-using-azstorage-apis.md)]

***

[!INCLUDE[Hosting: ANCM version 1 removed from hosting bundle](~/includes/core-changes/aspnetcore/3.0/hosting-ancmv1-hosting-bundle-removal.md)]

***

[!INCLUDE[Hosting: Generic host restriction on Startup constructor injection](~/includes/core-changes/aspnetcore/3.0/hosting-generic-host-startup-ctor-restriction.md)]

***

[!INCLUDE[Hosting: HTTPS redirection enabled for IIS OutOfProcess](~/includes/core-changes/aspnetcore/3.0/hosting-https-redirection-iis-outofprocess.md)]

***

[!INCLUDE[Hosting: IHostingEnvironment and IApplicationLifetime types replaced](~/includes/core-changes/aspnetcore/3.0/hosting-ihostingenv-iapplifetime-types-replaced.md)]

***

[!INCLUDE[Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies](~/includes/core-changes/aspnetcore/3.0/hosting-objectpoolprovider-webhostbuilder-dependencies.md)]

***

[!INCLUDE[HTTP: DefaultHttpContext extensibility removed](~/includes/core-changes/aspnetcore/3.0/http-defaulthttpcontext-extensibility-removed.md)]

***

[!INCLUDE[HTTP: HeaderNames fields changed to static readonly](~/includes/core-changes/aspnetcore/3.0/http-headernames-constants-staticreadonly.md)]

***

[!INCLUDE[HTTP: Response body infrastructure changes](~/includes/core-changes/aspnetcore/3.0/http-response-body-changes.md)]

***

[!INCLUDE[HTTP: Some cookie SameSite default values changed](~/includes/core-changes/aspnetcore/3.0/http-cookie-samesite-defaults-change.md)]

***

[!INCLUDE[HTTP: Synchronous IO disabled by default](~/includes/core-changes/aspnetcore/3.0/http-synchronous-io-disabled.md)]

***

[!INCLUDE[Identity: AddDefaultUI method overload removed](~/includes/core-changes/aspnetcore/3.0/identity-ui-adddefaultui-overload-removed.md)]

***

[!INCLUDE[Identity: UI Bootstrap version change](~/includes/core-changes/aspnetcore/3.0/identity-ui-bootstrap-version.md)]

***

[!INCLUDE[Identity: SignInAsync throws exception for unauthenticated identity](~/includes/core-changes/aspnetcore/3.0/identity-signinasync-throws-exception.md)]

***

[!INCLUDE[Identity: SignInManager constructor accepts new parameter](~/includes/core-changes/aspnetcore/3.0/identity-signinmanager-ctor-parameter.md)]

***

[!INCLUDE[Identity: UI uses static web assets feature](~/includes/core-changes/aspnetcore/3.0/identity-ui-static-web-assets.md)]

***

[!INCLUDE[Kestrel: Connection adapters removed](~/includes/core-changes/aspnetcore/3.0/kestrel-connection-adapters-removed.md)]

***

[!INCLUDE[Kestrel: Empty HTTPS assembly removed](~/includes/core-changes/aspnetcore/3.0/kestrel-empty-assembly-removed.md)]

***

[!INCLUDE[Kestrel: Request trailer headers moved to new collection](~/includes/core-changes/aspnetcore/3.0/kestrel-request-trailer-headers.md)]

***

[!INCLUDE[Kestrel: Transport abstraction layer changes](~/includes/core-changes/aspnetcore/3.0/kestrel-transport-abstractions.md)]

***

[!INCLUDE[Localization: APIs marked obsolete](~/includes/core-changes/aspnetcore/3.0/localization-apis-marked-obsolete.md)]

***

[!INCLUDE[Logging: DebugLogger class made internal](~/includes/core-changes/aspnetcore/3.0/logging-debuglogger-to-internal.md)]

***

[!INCLUDE[MVC: Controller action Async suffix removed](~/includes/core-changes/aspnetcore/3.0/mvc-action-async-suffix-trimmed.md)]

***

[!INCLUDE[MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core](~/includes/core-changes/aspnetcore/3.0/mvc-jsonresult-moved.md)]

***

[!INCLUDE[MVC: Precompilation tool deprecated](~/includes/core-changes/aspnetcore/3.0/mvc-precompilation-tool-deprecated.md)]

***

[!INCLUDE[MVC: Types changed to internal](~/includes/core-changes/aspnetcore/3.0/mvc-pubternal-to-internal.md)]

***

[!INCLUDE[MVC: Web API compatibility shim removed](~/includes/core-changes/aspnetcore/3.0/mvc-webapi-compat-shim-removed.md)]

***

[!INCLUDE[Razor: Runtime compilation moved to a package](~/includes/core-changes/aspnetcore/3.0/razor-runtime-compilation-package.md)]

***

[!INCLUDE[Session state: Obsolete APIs removed](~/includes/core-changes/aspnetcore/3.0/session-obsolete-apis-removed.md)]

***

[!INCLUDE[Shared framework: Assembly removal from Microsoft.AspNetCore.App](~/includes/core-changes/aspnetcore/3.0/sharedfx-app-shared-framework-assemblies.md)]

***

[!INCLUDE[Shared framework: Microsoft.AspNetCore.All removed](~/includes/core-changes/aspnetcore/3.0/sharedfx-all-framework-removed.md)]

***

[!INCLUDE[SignalR: HandshakeProtocol.SuccessHandshakeData replaced](~/includes/core-changes/aspnetcore/3.0/signalr-successhandshakedata-replaced.md)]

***

[!INCLUDE[SignalR: HubConnection methods removed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnection-methods-removed.md)]

***

[!INCLUDE[SignalR: HubConnectionContext constructors changed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnectioncontext-ctors.md)]

***

[!INCLUDE[SignalR: JavaScript client package name change](~/includes/core-changes/aspnetcore/3.0/signalr-js-client-package-name.md)]

***

[!INCLUDE[SignalR: Obsolete APIs](~/includes/core-changes/aspnetcore/3.0/signalr-obsolete-apis.md)]

***

[!INCLUDE[SPAs: SpaServices and NodeServices marked obsolete](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-obsolete.md)]

***

[!INCLUDE[SPAs: SpaServices and NodeServices console logger fallback default change](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-fallback.md)]

***

[!INCLUDE[Target framework: .NET Framework not supported](~/includes/core-changes/aspnetcore/3.0/targetfx-netfx-tfm-support.md)]

***
