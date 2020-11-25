---
title: ASP.NET Core 重大變更
titleSuffix: ''
description: 列出 ASP.NET Core 3.0 和3.1 中的重大變更。
ms.date: 11/03/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: 40dfda77dd51ed46366ec6cd8f6598070e8ce846
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "96032316"
---
# <a name="aspnet-core-breaking-changes-for-versions-30-and-31"></a><span data-ttu-id="3c8e7-103">版本3.0 和3.1 的 ASP.NET Core 重大變更</span><span class="sxs-lookup"><span data-stu-id="3c8e7-103">ASP.NET Core breaking changes for versions 3.0 and 3.1</span></span>

<span data-ttu-id="3c8e7-104">ASP.NET Core 提供 .NET Core 所使用的 web 應用程式開發功能。</span><span class="sxs-lookup"><span data-stu-id="3c8e7-104">ASP.NET Core provides the web app development features used by .NET Core.</span></span>

<span data-ttu-id="3c8e7-105">針對特定版本中的重大變更，請選取下列其中一個連結：</span><span class="sxs-lookup"><span data-stu-id="3c8e7-105">Select one of the following links for breaking changes in a specific version:</span></span>

* [<span data-ttu-id="3c8e7-106">ASP.NET Core 3。1</span><span class="sxs-lookup"><span data-stu-id="3c8e7-106">ASP.NET Core 3.1</span></span>](#aspnet-core-31)
* [<span data-ttu-id="3c8e7-107">ASP.NET Core 3。0</span><span class="sxs-lookup"><span data-stu-id="3c8e7-107">ASP.NET Core 3.0</span></span>](#aspnet-core-30)

<span data-ttu-id="3c8e7-108">下列 ASP.NET Core 3.0 和3.1 的重大變更記載于此頁面：</span><span class="sxs-lookup"><span data-stu-id="3c8e7-108">The following breaking changes in ASP.NET Core 3.0 and 3.1 are documented on this page:</span></span>

- [<span data-ttu-id="3c8e7-109">已移除過時的 Antiforgery、CORS、診斷、MVC 和路由 Api</span><span class="sxs-lookup"><span data-stu-id="3c8e7-109">Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed</span></span>](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [<span data-ttu-id="3c8e7-110">驗證： Google + 淘汰</span><span class="sxs-lookup"><span data-stu-id="3c8e7-110">Authentication: Google+ deprecation</span></span>](#authentication-google-deprecated-and-replaced)
- [<span data-ttu-id="3c8e7-111">驗證：已移除 HttpCoNtext 驗證屬性</span><span class="sxs-lookup"><span data-stu-id="3c8e7-111">Authentication: HttpContext.Authentication property removed</span></span>](#authentication-httpcontextauthentication-property-removed)
- [<span data-ttu-id="3c8e7-112">驗證：已取代類型上的 Newtonsoft.Js</span><span class="sxs-lookup"><span data-stu-id="3c8e7-112">Authentication: Newtonsoft.Json types replaced</span></span>](#authentication-newtonsoftjson-types-replaced)
- [<span data-ttu-id="3c8e7-113">驗證： OAuthHandler ExchangeCodeAsync 簽章已變更</span><span class="sxs-lookup"><span data-stu-id="3c8e7-113">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [<span data-ttu-id="3c8e7-114">授權： AddAuthorization 多載移至不同的元件</span><span class="sxs-lookup"><span data-stu-id="3c8e7-114">Authorization: AddAuthorization overload moved to different assembly</span></span>](#authorization-addauthorization-overload-moved-to-different-assembly)
- [<span data-ttu-id="3c8e7-115">授權： IAllowAnonymous 已從 AuthorizationFilterCoNtext 中移除。篩選器</span><span class="sxs-lookup"><span data-stu-id="3c8e7-115">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [<span data-ttu-id="3c8e7-116">授權： IAuthorizationPolicyProvider 執行需要新的方法</span><span class="sxs-lookup"><span data-stu-id="3c8e7-116">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [<span data-ttu-id="3c8e7-117">快取：已移除 CompactOnMemoryPressure 屬性</span><span class="sxs-lookup"><span data-stu-id="3c8e7-117">Caching: CompactOnMemoryPressure property removed</span></span>](#caching-compactonmemorypressure-property-removed)
- [<span data-ttu-id="3c8e7-118">Caching： SqlClient 使用新的套件</span><span class="sxs-lookup"><span data-stu-id="3c8e7-118">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [<span data-ttu-id="3c8e7-119">資料保護： DataProtection 會使用新的 Azure 儲存體 Api</span><span class="sxs-lookup"><span data-stu-id="3c8e7-119">Data Protection: DataProtection.Blobs uses new Azure Storage APIs</span></span>](#data-protection-dataprotectionblobs-uses-new-azure-storage-apis)
- [<span data-ttu-id="3c8e7-120">裝載：已從 Windows 裝載套件組合移除 AspNetCoreModule V1</span><span class="sxs-lookup"><span data-stu-id="3c8e7-120">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [<span data-ttu-id="3c8e7-121">裝載：泛型主機限制啟動的函式插入</span><span class="sxs-lookup"><span data-stu-id="3c8e7-121">Hosting: Generic host restricts Startup constructor injection</span></span>](#hosting-generic-host-restricts-startup-constructor-injection)
- [<span data-ttu-id="3c8e7-122">裝載：針對 IIS 跨進程應用程式啟用 HTTPS 重新導向</span><span class="sxs-lookup"><span data-stu-id="3c8e7-122">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [<span data-ttu-id="3c8e7-123">裝載：已取代 IHostingEnvironment 和 IApplicationLifetime 類型</span><span class="sxs-lookup"><span data-stu-id="3c8e7-123">Hosting: IHostingEnvironment and IApplicationLifetime types replaced</span></span>](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="3c8e7-124">裝載： ObjectPoolProvider 已從 >webhostbuilder 相依性中移除</span><span class="sxs-lookup"><span data-stu-id="3c8e7-124">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [<span data-ttu-id="3c8e7-125">HTTP：瀏覽器 SameSite 變更會影響驗證</span><span class="sxs-lookup"><span data-stu-id="3c8e7-125">HTTP: Browser SameSite changes impact authentication</span></span>](#http-browser-samesite-changes-impact-authentication)
- [<span data-ttu-id="3c8e7-126">HTTP：已移除 DefaultHttpCoNtext 擴充性</span><span class="sxs-lookup"><span data-stu-id="3c8e7-126">HTTP: DefaultHttpContext extensibility removed</span></span>](#http-defaulthttpcontext-extensibility-removed)
- [<span data-ttu-id="3c8e7-127">HTTP： HeaderNames 欄位已變更為靜態 readonly</span><span class="sxs-lookup"><span data-stu-id="3c8e7-127">HTTP: HeaderNames fields changed to static readonly</span></span>](#http-headernames-constants-changed-to-static-readonly)
- [<span data-ttu-id="3c8e7-128">HTTP：回應主體基礎結構變更</span><span class="sxs-lookup"><span data-stu-id="3c8e7-128">HTTP: Response body infrastructure changes</span></span>](#http-response-body-infrastructure-changes)
- [<span data-ttu-id="3c8e7-129">HTTP：某些 cookie SameSite 預設值已變更</span><span class="sxs-lookup"><span data-stu-id="3c8e7-129">HTTP: Some cookie SameSite default values changed</span></span>](#http-some-cookie-samesite-defaults-changed-to-none)
- [<span data-ttu-id="3c8e7-130">HTTP：同步 IO 預設為停用</span><span class="sxs-lookup"><span data-stu-id="3c8e7-130">HTTP: Synchronous IO disabled by default</span></span>](#http-synchronous-io-disabled-in-all-servers)
- [<span data-ttu-id="3c8e7-131">Identity： AddDefaultUI 方法多載已移除</span><span class="sxs-lookup"><span data-stu-id="3c8e7-131">Identity: AddDefaultUI method overload removed</span></span>](#identity-adddefaultui-method-overload-removed)
- [<span data-ttu-id="3c8e7-132">身分識別： UI 啟動程式版本變更</span><span class="sxs-lookup"><span data-stu-id="3c8e7-132">Identity: UI Bootstrap version change</span></span>](#identity-default-bootstrap-version-of-ui-changed)
- [<span data-ttu-id="3c8e7-133">Identity： SignInAsync 會針對未驗證的身分識別擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="3c8e7-133">Identity: SignInAsync throws exception for unauthenticated identity</span></span>](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [<span data-ttu-id="3c8e7-134">Identity：使用函式接受新的參數</span><span class="sxs-lookup"><span data-stu-id="3c8e7-134">Identity: SignInManager constructor accepts new parameter</span></span>](#identity-signinmanager-constructor-accepts-new-parameter)
- [<span data-ttu-id="3c8e7-135">身分識別： UI 使用靜態 web 資產功能</span><span class="sxs-lookup"><span data-stu-id="3c8e7-135">Identity: UI uses static web assets feature</span></span>](#identity-ui-uses-static-web-assets-feature)
- [<span data-ttu-id="3c8e7-136">Kestrel：已移除連接配接器</span><span class="sxs-lookup"><span data-stu-id="3c8e7-136">Kestrel: Connection adapters removed</span></span>](#kestrel-connection-adapters-removed)
- [<span data-ttu-id="3c8e7-137">Kestrel：已移除空白的 HTTPS 元件</span><span class="sxs-lookup"><span data-stu-id="3c8e7-137">Kestrel: Empty HTTPS assembly removed</span></span>](#kestrel-empty-https-assembly-removed)
- [<span data-ttu-id="3c8e7-138">Kestrel：要求尾端標頭移至新集合</span><span class="sxs-lookup"><span data-stu-id="3c8e7-138">Kestrel: Request trailer headers moved to new collection</span></span>](#kestrel-request-trailer-headers-moved-to-new-collection)
- [<span data-ttu-id="3c8e7-139">Kestrel：傳輸抽象層變更</span><span class="sxs-lookup"><span data-stu-id="3c8e7-139">Kestrel: Transport abstraction layer changes</span></span>](#kestrel-transport-abstractions-removed-and-made-public)
- [<span data-ttu-id="3c8e7-140">當地語系化： Api 已標記為過時</span><span class="sxs-lookup"><span data-stu-id="3c8e7-140">Localization: APIs marked obsolete</span></span>](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [<span data-ttu-id="3c8e7-141">記錄： DebugLogger 類別設為內部</span><span class="sxs-lookup"><span data-stu-id="3c8e7-141">Logging: DebugLogger class made internal</span></span>](#logging-debuglogger-class-made-internal)
- [<span data-ttu-id="3c8e7-142">MVC：已移除控制器動作非同步尾碼</span><span class="sxs-lookup"><span data-stu-id="3c8e7-142">MVC: Controller action Async suffix removed</span></span>](#mvc-async-suffix-trimmed-from-controller-action-names)
- [<span data-ttu-id="3c8e7-143">MVC： JsonResult 已移至 AspNetCore</span><span class="sxs-lookup"><span data-stu-id="3c8e7-143">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [<span data-ttu-id="3c8e7-144">MVC：先行編譯工具已淘汰</span><span class="sxs-lookup"><span data-stu-id="3c8e7-144">MVC: Precompilation tool deprecated</span></span>](#mvc-precompilation-tool-deprecated)
- [<span data-ttu-id="3c8e7-145">MVC：類型已變更為內部</span><span class="sxs-lookup"><span data-stu-id="3c8e7-145">MVC: Types changed to internal</span></span>](#mvc-pubternal-types-changed-to-internal)
- [<span data-ttu-id="3c8e7-146">MVC：已移除 Web API 相容性填充碼</span><span class="sxs-lookup"><span data-stu-id="3c8e7-146">MVC: Web API compatibility shim removed</span></span>](#mvc-web-api-compatibility-shim-removed)
- [<span data-ttu-id="3c8e7-147">Razor：已移除 RazorTemplateEngine API</span><span class="sxs-lookup"><span data-stu-id="3c8e7-147">Razor: RazorTemplateEngine API removed</span></span>](#razor-razortemplateengine-api-removed)
- [<span data-ttu-id="3c8e7-148">Razor：執行時間編譯已移至封裝</span><span class="sxs-lookup"><span data-stu-id="3c8e7-148">Razor: Runtime compilation moved to a package</span></span>](#razor-runtime-compilation-moved-to-a-package)
- [<span data-ttu-id="3c8e7-149">會話狀態：已移除淘汰的 Api</span><span class="sxs-lookup"><span data-stu-id="3c8e7-149">Session state: Obsolete APIs removed</span></span>](#session-state-obsolete-apis-removed)
- [<span data-ttu-id="3c8e7-150">共用架構：從 AspNetCore 移除元件</span><span class="sxs-lookup"><span data-stu-id="3c8e7-150">Shared framework: Assembly removal from Microsoft.AspNetCore.App</span></span>](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [<span data-ttu-id="3c8e7-151">共用架構： Microsoft. AspNetCore. 全部移除</span><span class="sxs-lookup"><span data-stu-id="3c8e7-151">Shared framework: Microsoft.AspNetCore.All removed</span></span>](#shared-framework-removed-microsoftaspnetcoreall)
- [<span data-ttu-id="3c8e7-152">SignalR：已取代 HandshakeProtocol SuccessHandshakeData</span><span class="sxs-lookup"><span data-stu-id="3c8e7-152">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [<span data-ttu-id="3c8e7-153">SignalR：已移除 HubConnection 方法</span><span class="sxs-lookup"><span data-stu-id="3c8e7-153">SignalR: HubConnection methods removed</span></span>](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [<span data-ttu-id="3c8e7-154">SignalR： HubConnectionCoNtext 的函式已變更</span><span class="sxs-lookup"><span data-stu-id="3c8e7-154">SignalR: HubConnectionContext constructors changed</span></span>](#signalr-hubconnectioncontext-constructors-changed)
- [<span data-ttu-id="3c8e7-155">SignalR： JavaScript 用戶端套件名稱變更</span><span class="sxs-lookup"><span data-stu-id="3c8e7-155">SignalR: JavaScript client package name change</span></span>](#signalr-javascript-client-package-name-changed)
- [<span data-ttu-id="3c8e7-156">SignalR：淘汰的 Api</span><span class="sxs-lookup"><span data-stu-id="3c8e7-156">SignalR: Obsolete APIs</span></span>](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [<span data-ttu-id="3c8e7-157">Spa： SpaServices 和 NodeServices 主控台記錄器 fallback 預設變更</span><span class="sxs-lookup"><span data-stu-id="3c8e7-157">SPAs: SpaServices and NodeServices console logger fallback default change</span></span>](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [<span data-ttu-id="3c8e7-158">Spa： SpaServices 和 NodeServices 已標示為過時</span><span class="sxs-lookup"><span data-stu-id="3c8e7-158">SPAs: SpaServices and NodeServices marked obsolete</span></span>](#spas-spaservices-and-nodeservices-marked-obsolete)
- [<span data-ttu-id="3c8e7-159">目標 framework：不支援 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3c8e7-159">Target framework: .NET Framework not supported</span></span>](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-31"></a><span data-ttu-id="3c8e7-160">ASP.NET Core 3。1</span><span class="sxs-lookup"><span data-stu-id="3c8e7-160">ASP.NET Core 3.1</span></span>

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a><span data-ttu-id="3c8e7-161">ASP.NET Core 3。0</span><span class="sxs-lookup"><span data-stu-id="3c8e7-161">ASP.NET Core 3.0</span></span>

[!INCLUDE[Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed](~/includes/core-changes/aspnetcore/3.0/obsolete-apis-removed.md)]

<span data-ttu-id="3c8e7-162">\*\*_</span><span class="sxs-lookup"><span data-stu-id="3c8e7-162">\*\*_</span></span>

[!INCLUDE[Authentication: Google+ deprecation](~/includes/core-changes/aspnetcore/3.0/authn-google-plus-authn-changes.md)]

_*_

[!INCLUDE[Authentication: HttpContext.Authentication property removed](~/includes/core-changes/aspnetcore/3.0/authn-httpcontext-property-removed.md)]

_*_

[!INCLUDE[Authentication: Newtonsoft.Json types replaced](~/includes/core-changes/aspnetcore/3.0/authn-apis-json-types.md)]

_*_

[!INCLUDE[Authentication: OAuthHandler ExchangeCodeAsync signature changed](~/includes/core-changes/aspnetcore/3.0/authn-exchangecodeasync-signature-change.md)]

_*_

[!INCLUDE[Authorization: AddAuthorization overload assembly change](~/includes/core-changes/aspnetcore/3.0/authz-assembly-change.md)]

_*_

[!INCLUDE[Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters](~/includes/core-changes/aspnetcore/3.0/authz-iallowanonymous-removed-from-collection.md)]

_*_

[!INCLUDE[Authorization: IAuthorizationPolicyProvider implementations require new method](~/includes/core-changes/aspnetcore/3.0/authz-iauthzpolicyprovider-new-method.md)]

_*_

[!INCLUDE[Caching: CompactOnMemoryPressure property removed](~/includes/core-changes/aspnetcore/3.0/caching-memory-property-removed.md)]

_*_

[!INCLUDE[Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package](~/includes/core-changes/aspnetcore/3.0/caching-new-sqlclient-package.md)]

_*_

[!INCLUDE[Caching: ResponseCaching types changed to internal](~/includes/core-changes/aspnetcore/3.0/caching-response-pubternal-to-internal.md)]

_*_

[!INCLUDE[Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs](~/includes/core-changes/aspnetcore/3.0/dataprotection-azstorage-using-azstorage-apis.md)]

_*_

[!INCLUDE[Hosting: ANCM version 1 removed from hosting bundle](~/includes/core-changes/aspnetcore/3.0/hosting-ancmv1-hosting-bundle-removal.md)]

_*_

[!INCLUDE[Hosting: Generic host restriction on Startup constructor injection](~/includes/core-changes/aspnetcore/3.0/hosting-generic-host-startup-ctor-restriction.md)]

_*_

[!INCLUDE[Hosting: HTTPS redirection enabled for IIS OutOfProcess](~/includes/core-changes/aspnetcore/3.0/hosting-https-redirection-iis-outofprocess.md)]

_*_

[!INCLUDE[Hosting: IHostingEnvironment and IApplicationLifetime types replaced](~/includes/core-changes/aspnetcore/3.0/hosting-ihostingenv-iapplifetime-types-replaced.md)]

_*_

[!INCLUDE[Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies](~/includes/core-changes/aspnetcore/3.0/hosting-objectpoolprovider-webhostbuilder-dependencies.md)]

_*_

[!INCLUDE[HTTP: DefaultHttpContext extensibility removed](~/includes/core-changes/aspnetcore/3.0/http-defaulthttpcontext-extensibility-removed.md)]

_*_

[!INCLUDE[HTTP: HeaderNames fields changed to static readonly](~/includes/core-changes/aspnetcore/3.0/http-headernames-constants-staticreadonly.md)]

_*_

[!INCLUDE[HTTP: Response body infrastructure changes](~/includes/core-changes/aspnetcore/3.0/http-response-body-changes.md)]

_*_

[!INCLUDE[HTTP: Some cookie SameSite default values changed](~/includes/core-changes/aspnetcore/3.0/http-cookie-samesite-defaults-change.md)]

_*_

[!INCLUDE[HTTP: Synchronous IO disabled by default](~/includes/core-changes/aspnetcore/3.0/http-synchronous-io-disabled.md)]

_*_

[!INCLUDE[Identity: AddDefaultUI method overload removed](~/includes/core-changes/aspnetcore/3.0/identity-ui-adddefaultui-overload-removed.md)]

_*_

[!INCLUDE[Identity: UI Bootstrap version change](~/includes/core-changes/aspnetcore/3.0/identity-ui-bootstrap-version.md)]

_*_

[!INCLUDE[Identity: SignInAsync throws exception for unauthenticated identity](~/includes/core-changes/aspnetcore/3.0/identity-signinasync-throws-exception.md)]

_*_

[!INCLUDE[Identity: SignInManager constructor accepts new parameter](~/includes/core-changes/aspnetcore/3.0/identity-signinmanager-ctor-parameter.md)]

_*_

[!INCLUDE[Identity: UI uses static web assets feature](~/includes/core-changes/aspnetcore/3.0/identity-ui-static-web-assets.md)]

_*_

[!INCLUDE[Kestrel: Connection adapters removed](~/includes/core-changes/aspnetcore/3.0/kestrel-connection-adapters-removed.md)]

_*_

[!INCLUDE[Kestrel: Empty HTTPS assembly removed](~/includes/core-changes/aspnetcore/3.0/kestrel-empty-assembly-removed.md)]

_*_

[!INCLUDE[Kestrel: Request trailer headers moved to new collection](~/includes/core-changes/aspnetcore/3.0/kestrel-request-trailer-headers.md)]

_*_

[!INCLUDE[Kestrel: Transport abstraction layer changes](~/includes/core-changes/aspnetcore/3.0/kestrel-transport-abstractions.md)]

_*_

[!INCLUDE[Localization: APIs marked obsolete](~/includes/core-changes/aspnetcore/3.0/localization-apis-marked-obsolete.md)]

_*_

[!INCLUDE[Logging: DebugLogger class made internal](~/includes/core-changes/aspnetcore/3.0/logging-debuglogger-to-internal.md)]

_*_

[!INCLUDE[MVC: Controller action Async suffix removed](~/includes/core-changes/aspnetcore/3.0/mvc-action-async-suffix-trimmed.md)]

_*_

[!INCLUDE[MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core](~/includes/core-changes/aspnetcore/3.0/mvc-jsonresult-moved.md)]

_*_

[!INCLUDE[MVC: Precompilation tool deprecated](~/includes/core-changes/aspnetcore/3.0/mvc-precompilation-tool-deprecated.md)]

_*_

[!INCLUDE[MVC: Types changed to internal](~/includes/core-changes/aspnetcore/3.0/mvc-pubternal-to-internal.md)]

_*_

[!INCLUDE[MVC: Web API compatibility shim removed](~/includes/core-changes/aspnetcore/3.0/mvc-webapi-compat-shim-removed.md)]

_*_

[!INCLUDE[Razor: RazorTemplatEengine API removed](~/includes/core-changes/aspnetcore/3.0/razor-razortemplateengine-api-removed.md)]

_*_

[!INCLUDE[Razor: Runtime compilation moved to a package](~/includes/core-changes/aspnetcore/3.0/razor-runtime-compilation-package.md)]

_*_

[!INCLUDE[Session state: Obsolete APIs removed](~/includes/core-changes/aspnetcore/3.0/session-obsolete-apis-removed.md)]

_*_

[!INCLUDE[Shared framework: Assembly removal from Microsoft.AspNetCore.App](~/includes/core-changes/aspnetcore/3.0/sharedfx-app-shared-framework-assemblies.md)]

_*_

[!INCLUDE[Shared framework: Microsoft.AspNetCore.All removed](~/includes/core-changes/aspnetcore/3.0/sharedfx-all-framework-removed.md)]

_*_

[!INCLUDE[SignalR: HandshakeProtocol.SuccessHandshakeData replaced](~/includes/core-changes/aspnetcore/3.0/signalr-successhandshakedata-replaced.md)]

_*_

[!INCLUDE[SignalR: HubConnection methods removed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnection-methods-removed.md)]

_*_

[!INCLUDE[SignalR: HubConnectionContext constructors changed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnectioncontext-ctors.md)]

_*_

[!INCLUDE[SignalR: JavaScript client package name change](~/includes/core-changes/aspnetcore/3.0/signalr-js-client-package-name.md)]

_*_

[!INCLUDE[SignalR: Obsolete APIs](~/includes/core-changes/aspnetcore/3.0/signalr-obsolete-apis.md)]

_*_

[!INCLUDE[SPAs: SpaServices and NodeServices marked obsolete](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-obsolete.md)]

_*_

[!INCLUDE[SPAs: SpaServices and NodeServices console logger fallback default change](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-fallback.md)]

_*_

[!INCLUDE[Target framework: .NET Framework not supported](~/includes/core-changes/aspnetcore/3.0/targetfx-netfx-tfm-support.md)]

<span data-ttu-id="3c8e7-163">_\*\*</span><span class="sxs-lookup"><span data-stu-id="3c8e7-163">_\*\*</span></span>
