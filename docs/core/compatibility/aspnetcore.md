---
title: ASP.NET Core 的重大變更
titleSuffix: ''
description: 列出 ASP.NET Core 中的重大變更。
ms.date: 01/10/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: c54735cd53fb9cb48eb84045791ccc559fe683cd
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093171"
---
# <a name="aspnet-core-breaking-changes"></a><span data-ttu-id="6f900-103">ASP.NET Core 的重大變更</span><span class="sxs-lookup"><span data-stu-id="6f900-103">ASP.NET Core breaking changes</span></span>

<span data-ttu-id="6f900-104">ASP.NET Core 提供 .NET Core 所使用的 web 應用程式開發功能。</span><span class="sxs-lookup"><span data-stu-id="6f900-104">ASP.NET Core provides the web app development features used by .NET Core.</span></span>

<span data-ttu-id="6f900-105">下列重大變更記載于此頁面：</span><span class="sxs-lookup"><span data-stu-id="6f900-105">The following breaking changes are documented on this page:</span></span>

- [<span data-ttu-id="6f900-106">HTTP：瀏覽器 SameSite 變更影響驗證</span><span class="sxs-lookup"><span data-stu-id="6f900-106">HTTP: Browser SameSite changes impact authentication</span></span>](#http-browser-samesite-changes-impact-authentication)
- [<span data-ttu-id="6f900-107">已移除過時的 Antiforgery、CORS、診斷、MVC 和路由 Api</span><span class="sxs-lookup"><span data-stu-id="6f900-107">Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed</span></span>](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [<span data-ttu-id="6f900-108">驗證： Google + 淘汰</span><span class="sxs-lookup"><span data-stu-id="6f900-108">Authentication: Google+ deprecation</span></span>](#authentication-google-deprecated-and-replaced)
- [<span data-ttu-id="6f900-109">驗證：已移除 HttpCoNtext 驗證屬性</span><span class="sxs-lookup"><span data-stu-id="6f900-109">Authentication: HttpContext.Authentication property removed</span></span>](#authentication-httpcontextauthentication-property-removed)
- [<span data-ttu-id="6f900-110">驗證： Newtonsoft 已取代的 Json 類型</span><span class="sxs-lookup"><span data-stu-id="6f900-110">Authentication: Newtonsoft.Json types replaced</span></span>](#authentication-newtonsoftjson-types-replaced)
- [<span data-ttu-id="6f900-111">驗證： OAuthHandler ExchangeCodeAsync 簽章已變更</span><span class="sxs-lookup"><span data-stu-id="6f900-111">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [<span data-ttu-id="6f900-112">授權： AddAuthorization 多載已移至不同的元件</span><span class="sxs-lookup"><span data-stu-id="6f900-112">Authorization: AddAuthorization overload moved to different assembly</span></span>](#authorization-addauthorization-overload-moved-to-different-assembly)
- [<span data-ttu-id="6f900-113">授權： IAllowAnonymous 已從 AuthorizationFilterCoNtext 移除。篩選</span><span class="sxs-lookup"><span data-stu-id="6f900-113">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [<span data-ttu-id="6f900-114">授權： IAuthorizationPolicyProvider 的部署需要新的方法</span><span class="sxs-lookup"><span data-stu-id="6f900-114">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [<span data-ttu-id="6f900-115">Caching： CompactOnMemoryPressure 屬性已移除</span><span class="sxs-lookup"><span data-stu-id="6f900-115">Caching: CompactOnMemoryPressure property removed</span></span>](#caching-compactonmemorypressure-property-removed)
- [<span data-ttu-id="6f900-116">快取： SqlClient 使用新的封裝</span><span class="sxs-lookup"><span data-stu-id="6f900-116">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [<span data-ttu-id="6f900-117">Caching： ResponseCaching "pubternal" 類型已變更為 internal</span><span class="sxs-lookup"><span data-stu-id="6f900-117">Caching: ResponseCaching "pubternal" types changed to internal</span></span>](#caching-responsecaching-pubternal-types-changed-to-internal)
- [<span data-ttu-id="6f900-118">資料保護： DataProtection. AzureStorage 使用新的 Azure 儲存體 Api</span><span class="sxs-lookup"><span data-stu-id="6f900-118">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [<span data-ttu-id="6f900-119">裝載：已從 Windows 裝載套件組合中移除 AspNetCoreModule V1</span><span class="sxs-lookup"><span data-stu-id="6f900-119">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [<span data-ttu-id="6f900-120">裝載：泛型主機會限制啟動的函數插入</span><span class="sxs-lookup"><span data-stu-id="6f900-120">Hosting: Generic host restricts Startup constructor injection</span></span>](#hosting-generic-host-restricts-startup-constructor-injection)
- [<span data-ttu-id="6f900-121">裝載：已為 IIS 跨進程應用程式啟用 HTTPS 重新導向</span><span class="sxs-lookup"><span data-stu-id="6f900-121">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [<span data-ttu-id="6f900-122">裝載：已取代 IHostingEnvironment 和 IApplicationLifetime 類型</span><span class="sxs-lookup"><span data-stu-id="6f900-122">Hosting: IHostingEnvironment and IApplicationLifetime types replaced</span></span>](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="6f900-123">裝載：已從 WebHostBuilder 相依性移除 ObjectPoolProvider</span><span class="sxs-lookup"><span data-stu-id="6f900-123">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [<span data-ttu-id="6f900-124">HTTP： DefaultHttpCoNtext 擴充性已移除</span><span class="sxs-lookup"><span data-stu-id="6f900-124">HTTP: DefaultHttpContext extensibility removed</span></span>](#http-defaulthttpcontext-extensibility-removed)
- [<span data-ttu-id="6f900-125">HTTP： HeaderNames 欄位已變更為靜態唯讀</span><span class="sxs-lookup"><span data-stu-id="6f900-125">HTTP: HeaderNames fields changed to static readonly</span></span>](#http-headernames-constants-changed-to-static-readonly)
- [<span data-ttu-id="6f900-126">HTTP：回應主體基礎結構變更</span><span class="sxs-lookup"><span data-stu-id="6f900-126">HTTP: Response body infrastructure changes</span></span>](#http-response-body-infrastructure-changes)
- [<span data-ttu-id="6f900-127">HTTP：某些 cookie SameSite 預設值已變更</span><span class="sxs-lookup"><span data-stu-id="6f900-127">HTTP: Some cookie SameSite default values changed</span></span>](#http-some-cookie-samesite-defaults-changed-to-none)
- [<span data-ttu-id="6f900-128">HTTP：預設停用同步 IO</span><span class="sxs-lookup"><span data-stu-id="6f900-128">HTTP: Synchronous IO disabled by default</span></span>](#http-synchronous-io-disabled-in-all-servers)
- [<span data-ttu-id="6f900-129">識別： AddDefaultUI 方法多載已移除</span><span class="sxs-lookup"><span data-stu-id="6f900-129">Identity: AddDefaultUI method overload removed</span></span>](#identity-adddefaultui-method-overload-removed)
- [<span data-ttu-id="6f900-130">身分識別： UI 啟動程式版本變更</span><span class="sxs-lookup"><span data-stu-id="6f900-130">Identity: UI Bootstrap version change</span></span>](#identity-default-bootstrap-version-of-ui-changed)
- [<span data-ttu-id="6f900-131">身分識別： SignInAsync 擲回未驗證身分識別的例外狀況</span><span class="sxs-lookup"><span data-stu-id="6f900-131">Identity: SignInAsync throws exception for unauthenticated identity</span></span>](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [<span data-ttu-id="6f900-132">身分識別：使用的函式接受新的參數</span><span class="sxs-lookup"><span data-stu-id="6f900-132">Identity: SignInManager constructor accepts new parameter</span></span>](#identity-signinmanager-constructor-accepts-new-parameter)
- [<span data-ttu-id="6f900-133">身分識別： UI 使用靜態 web 資產功能</span><span class="sxs-lookup"><span data-stu-id="6f900-133">Identity: UI uses static web assets feature</span></span>](#identity-ui-uses-static-web-assets-feature)
- [<span data-ttu-id="6f900-134">Kestrel：已移除連接介面卡</span><span class="sxs-lookup"><span data-stu-id="6f900-134">Kestrel: Connection adapters removed</span></span>](#kestrel-connection-adapters-removed)
- [<span data-ttu-id="6f900-135">Kestrel：已移除空的 HTTPS 元件</span><span class="sxs-lookup"><span data-stu-id="6f900-135">Kestrel: Empty HTTPS assembly removed</span></span>](#kestrel-empty-https-assembly-removed)
- [<span data-ttu-id="6f900-136">Kestrel：要求尾標頭已移至新的集合</span><span class="sxs-lookup"><span data-stu-id="6f900-136">Kestrel: Request trailer headers moved to new collection</span></span>](#kestrel-request-trailer-headers-moved-to-new-collection)
- [<span data-ttu-id="6f900-137">Kestrel：傳輸抽象層變更</span><span class="sxs-lookup"><span data-stu-id="6f900-137">Kestrel: Transport abstraction layer changes</span></span>](#kestrel-transport-abstractions-removed-and-made-public)
- [<span data-ttu-id="6f900-138">當地語系化：已標記為過時的 Api</span><span class="sxs-lookup"><span data-stu-id="6f900-138">Localization: APIs marked obsolete</span></span>](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [<span data-ttu-id="6f900-139">記錄： DebugLogger 類別已設為內部</span><span class="sxs-lookup"><span data-stu-id="6f900-139">Logging: DebugLogger class made internal</span></span>](#logging-debuglogger-class-made-internal)
- [<span data-ttu-id="6f900-140">MVC：已移除控制器動作非同步尾碼</span><span class="sxs-lookup"><span data-stu-id="6f900-140">MVC: Controller action Async suffix removed</span></span>](#mvc-async-suffix-trimmed-from-controller-action-names)
- [<span data-ttu-id="6f900-141">MVC： JsonResult 已移至 AspNetCore. Core</span><span class="sxs-lookup"><span data-stu-id="6f900-141">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [<span data-ttu-id="6f900-142">MVC：先行編譯工具已被取代</span><span class="sxs-lookup"><span data-stu-id="6f900-142">MVC: Precompilation tool deprecated</span></span>](#mvc-precompilation-tool-deprecated)
- [<span data-ttu-id="6f900-143">MVC：類型已變更為內部</span><span class="sxs-lookup"><span data-stu-id="6f900-143">MVC: Types changed to internal</span></span>](#mvc-pubternal-types-changed-to-internal)
- [<span data-ttu-id="6f900-144">MVC： Web API 相容性填充碼已移除</span><span class="sxs-lookup"><span data-stu-id="6f900-144">MVC: Web API compatibility shim removed</span></span>](#mvc-web-api-compatibility-shim-removed)
- [<span data-ttu-id="6f900-145">Razor：將執行時間編譯移至封裝</span><span class="sxs-lookup"><span data-stu-id="6f900-145">Razor: Runtime compilation moved to a package</span></span>](#razor-runtime-compilation-moved-to-a-package)
- [<span data-ttu-id="6f900-146">會話狀態：已移除已淘汰的 Api</span><span class="sxs-lookup"><span data-stu-id="6f900-146">Session state: Obsolete APIs removed</span></span>](#session-state-obsolete-apis-removed)
- [<span data-ttu-id="6f900-147">共用架構：從 AspNetCore 應用程式移除元件</span><span class="sxs-lookup"><span data-stu-id="6f900-147">Shared framework: Assembly removal from Microsoft.AspNetCore.App</span></span>](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [<span data-ttu-id="6f900-148">共用架構： AspNetCore 全部移除</span><span class="sxs-lookup"><span data-stu-id="6f900-148">Shared framework: Microsoft.AspNetCore.All removed</span></span>](#shared-framework-removed-microsoftaspnetcoreall)
- [<span data-ttu-id="6f900-149">SignalR： HandshakeProtocol. SuccessHandshakeData 已取代</span><span class="sxs-lookup"><span data-stu-id="6f900-149">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [<span data-ttu-id="6f900-150">SignalR：已移除 HubConnection 方法</span><span class="sxs-lookup"><span data-stu-id="6f900-150">SignalR: HubConnection methods removed</span></span>](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [<span data-ttu-id="6f900-151">SignalR： HubConnectionCoNtext 的函式已變更</span><span class="sxs-lookup"><span data-stu-id="6f900-151">SignalR: HubConnectionContext constructors changed</span></span>](#signalr-hubconnectioncontext-constructors-changed)
- [<span data-ttu-id="6f900-152">SignalR： JavaScript 用戶端封裝名稱變更</span><span class="sxs-lookup"><span data-stu-id="6f900-152">SignalR: JavaScript client package name change</span></span>](#signalr-javascript-client-package-name-changed)
- [<span data-ttu-id="6f900-153">SignalR：過時的 Api</span><span class="sxs-lookup"><span data-stu-id="6f900-153">SignalR: Obsolete APIs</span></span>](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [<span data-ttu-id="6f900-154">Spa：已標記為過時的 SpaServices 和 NodeServices</span><span class="sxs-lookup"><span data-stu-id="6f900-154">SPAs: SpaServices and NodeServices marked obsolete</span></span>](#spas-spaservices-and-nodeservices-marked-obsolete)
- [<span data-ttu-id="6f900-155">Spa： SpaServices 和 NodeServices 主控台記錄器 fallback 預設變更</span><span class="sxs-lookup"><span data-stu-id="6f900-155">SPAs: SpaServices and NodeServices console logger fallback default change</span></span>](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [<span data-ttu-id="6f900-156">目標 framework：不支援 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6f900-156">Target framework: .NET Framework not supported</span></span>](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-31"></a><span data-ttu-id="6f900-157">ASP.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="6f900-157">ASP.NET Core 3.1</span></span>

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a><span data-ttu-id="6f900-158">ASP.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6f900-158">ASP.NET Core 3.0</span></span>

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
