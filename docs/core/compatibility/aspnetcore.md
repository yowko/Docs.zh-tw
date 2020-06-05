---
title: ASP.NET Core 的重大變更
titleSuffix: ''
description: 列出 ASP.NET Core 中的重大變更。
ms.date: 04/29/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: 2e89a14c948365da1e7a04fc8d5ca4008842f8d8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446963"
---
# <a name="aspnet-core-breaking-changes"></a><span data-ttu-id="aa2ea-103">ASP.NET Core 的重大變更</span><span class="sxs-lookup"><span data-stu-id="aa2ea-103">ASP.NET Core breaking changes</span></span>

<span data-ttu-id="aa2ea-104">ASP.NET Core 提供 .NET Core 所使用的 web 應用程式開發功能。</span><span class="sxs-lookup"><span data-stu-id="aa2ea-104">ASP.NET Core provides the web app development features used by .NET Core.</span></span>

<span data-ttu-id="aa2ea-105">下列重大變更記載于此頁面：</span><span class="sxs-lookup"><span data-stu-id="aa2ea-105">The following breaking changes are documented on this page:</span></span>

- [<span data-ttu-id="aa2ea-106">已移除過時的 Antiforgery、CORS、診斷、MVC 和路由 Api</span><span class="sxs-lookup"><span data-stu-id="aa2ea-106">Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed</span></span>](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [<span data-ttu-id="aa2ea-107">驗證： Google + 淘汰</span><span class="sxs-lookup"><span data-stu-id="aa2ea-107">Authentication: Google+ deprecation</span></span>](#authentication-google-deprecated-and-replaced)
- [<span data-ttu-id="aa2ea-108">驗證：已移除 HttpCoNtext 驗證屬性</span><span class="sxs-lookup"><span data-stu-id="aa2ea-108">Authentication: HttpContext.Authentication property removed</span></span>](#authentication-httpcontextauthentication-property-removed)
- [<span data-ttu-id="aa2ea-109">驗證： Newtonsoft 已取代的 Json 類型</span><span class="sxs-lookup"><span data-stu-id="aa2ea-109">Authentication: Newtonsoft.Json types replaced</span></span>](#authentication-newtonsoftjson-types-replaced)
- [<span data-ttu-id="aa2ea-110">驗證： OAuthHandler ExchangeCodeAsync 簽章已變更</span><span class="sxs-lookup"><span data-stu-id="aa2ea-110">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [<span data-ttu-id="aa2ea-111">授權： AddAuthorization 多載已移至不同的元件</span><span class="sxs-lookup"><span data-stu-id="aa2ea-111">Authorization: AddAuthorization overload moved to different assembly</span></span>](#authorization-addauthorization-overload-moved-to-different-assembly)
- [<span data-ttu-id="aa2ea-112">授權： IAllowAnonymous 已從 AuthorizationFilterCoNtext 移除。篩選</span><span class="sxs-lookup"><span data-stu-id="aa2ea-112">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [<span data-ttu-id="aa2ea-113">授權： IAuthorizationPolicyProvider 的部署需要新的方法</span><span class="sxs-lookup"><span data-stu-id="aa2ea-113">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [<span data-ttu-id="aa2ea-114">Azure：已移除 Microsoft 前面的 Azure 整合套件</span><span class="sxs-lookup"><span data-stu-id="aa2ea-114">Azure: Microsoft-prefixed Azure integration packages removed</span></span>](#azure-microsoft-prefixed-azure-integration-packages-removed)
- [<span data-ttu-id="aa2ea-115">Caching： CompactOnMemoryPressure 屬性已移除</span><span class="sxs-lookup"><span data-stu-id="aa2ea-115">Caching: CompactOnMemoryPressure property removed</span></span>](#caching-compactonmemorypressure-property-removed)
- [<span data-ttu-id="aa2ea-116">快取： SqlClient 使用新的封裝</span><span class="sxs-lookup"><span data-stu-id="aa2ea-116">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [<span data-ttu-id="aa2ea-117">Caching： ResponseCaching "pubternal" 類型已變更為 internal</span><span class="sxs-lookup"><span data-stu-id="aa2ea-117">Caching: ResponseCaching "pubternal" types changed to internal</span></span>](#caching-responsecaching-pubternal-types-changed-to-internal)
- [<span data-ttu-id="aa2ea-118">資料保護： DataProtection. AzureStorage 使用新的 Azure 儲存體 Api</span><span class="sxs-lookup"><span data-stu-id="aa2ea-118">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [<span data-ttu-id="aa2ea-119">延伸模組：套件參考變更會影響某些 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="aa2ea-119">Extensions: Package reference changes affecting some NuGet packages</span></span>](#extensions-package-reference-changes-affecting-some-nuget-packages)
- [<span data-ttu-id="aa2ea-120">裝載：已從 Windows 裝載套件組合中移除 AspNetCoreModule V1</span><span class="sxs-lookup"><span data-stu-id="aa2ea-120">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [<span data-ttu-id="aa2ea-121">裝載：泛型主機會限制啟動的函數插入</span><span class="sxs-lookup"><span data-stu-id="aa2ea-121">Hosting: Generic host restricts Startup constructor injection</span></span>](#hosting-generic-host-restricts-startup-constructor-injection)
- [<span data-ttu-id="aa2ea-122">裝載：已為 IIS 跨進程應用程式啟用 HTTPS 重新導向</span><span class="sxs-lookup"><span data-stu-id="aa2ea-122">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [<span data-ttu-id="aa2ea-123">裝載：已取代 IHostingEnvironment 和 IApplicationLifetime 類型</span><span class="sxs-lookup"><span data-stu-id="aa2ea-123">Hosting: IHostingEnvironment and IApplicationLifetime types replaced</span></span>](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="aa2ea-124">裝載：已從 WebHostBuilder 相依性移除 ObjectPoolProvider</span><span class="sxs-lookup"><span data-stu-id="aa2ea-124">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [<span data-ttu-id="aa2ea-125">HTTP： Kestrel 和 IIS BadHttpRequestException 類型已標記為過時並被取代</span><span class="sxs-lookup"><span data-stu-id="aa2ea-125">HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced</span></span>](#http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="aa2ea-126">HTTP：瀏覽器 SameSite 變更影響驗證</span><span class="sxs-lookup"><span data-stu-id="aa2ea-126">HTTP: Browser SameSite changes impact authentication</span></span>](#http-browser-samesite-changes-impact-authentication)
- [<span data-ttu-id="aa2ea-127">HTTP： DefaultHttpCoNtext 擴充性已移除</span><span class="sxs-lookup"><span data-stu-id="aa2ea-127">HTTP: DefaultHttpContext extensibility removed</span></span>](#http-defaulthttpcontext-extensibility-removed)
- [<span data-ttu-id="aa2ea-128">HTTP： HeaderNames 欄位已變更為靜態唯讀</span><span class="sxs-lookup"><span data-stu-id="aa2ea-128">HTTP: HeaderNames fields changed to static readonly</span></span>](#http-headernames-constants-changed-to-static-readonly)
- [<span data-ttu-id="aa2ea-129">HTTP： IHttpClientFactory 記錄整數狀態碼所建立的 HttpClient 實例</span><span class="sxs-lookup"><span data-stu-id="aa2ea-129">HTTP: HttpClient instances created by IHttpClientFactory log integer status codes</span></span>](#http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes)
- [<span data-ttu-id="aa2ea-130">HTTP：回應主體基礎結構變更</span><span class="sxs-lookup"><span data-stu-id="aa2ea-130">HTTP: Response body infrastructure changes</span></span>](#http-response-body-infrastructure-changes)
- [<span data-ttu-id="aa2ea-131">HTTP：某些 cookie SameSite 預設值已變更</span><span class="sxs-lookup"><span data-stu-id="aa2ea-131">HTTP: Some cookie SameSite default values changed</span></span>](#http-some-cookie-samesite-defaults-changed-to-none)
- [<span data-ttu-id="aa2ea-132">HTTP：預設停用同步 IO</span><span class="sxs-lookup"><span data-stu-id="aa2ea-132">HTTP: Synchronous IO disabled by default</span></span>](#http-synchronous-io-disabled-in-all-servers)
- [<span data-ttu-id="aa2ea-133">識別： AddDefaultUI 方法多載已移除</span><span class="sxs-lookup"><span data-stu-id="aa2ea-133">Identity: AddDefaultUI method overload removed</span></span>](#identity-adddefaultui-method-overload-removed)
- [<span data-ttu-id="aa2ea-134">身分識別： UI 啟動程式版本變更</span><span class="sxs-lookup"><span data-stu-id="aa2ea-134">Identity: UI Bootstrap version change</span></span>](#identity-default-bootstrap-version-of-ui-changed)
- [<span data-ttu-id="aa2ea-135">身分識別： SignInAsync 擲回未驗證身分識別的例外狀況</span><span class="sxs-lookup"><span data-stu-id="aa2ea-135">Identity: SignInAsync throws exception for unauthenticated identity</span></span>](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [<span data-ttu-id="aa2ea-136">身分識別：使用的函式接受新的參數</span><span class="sxs-lookup"><span data-stu-id="aa2ea-136">Identity: SignInManager constructor accepts new parameter</span></span>](#identity-signinmanager-constructor-accepts-new-parameter)
- [<span data-ttu-id="aa2ea-137">身分識別： UI 使用靜態 web 資產功能</span><span class="sxs-lookup"><span data-stu-id="aa2ea-137">Identity: UI uses static web assets feature</span></span>](#identity-ui-uses-static-web-assets-feature)
- [<span data-ttu-id="aa2ea-138">Kestrel：已移除連接介面卡</span><span class="sxs-lookup"><span data-stu-id="aa2ea-138">Kestrel: Connection adapters removed</span></span>](#kestrel-connection-adapters-removed)
- [<span data-ttu-id="aa2ea-139">Kestrel：已移除空的 HTTPS 元件</span><span class="sxs-lookup"><span data-stu-id="aa2ea-139">Kestrel: Empty HTTPS assembly removed</span></span>](#kestrel-empty-https-assembly-removed)
- [<span data-ttu-id="aa2ea-140">Kestrel：要求尾標頭已移至新的集合</span><span class="sxs-lookup"><span data-stu-id="aa2ea-140">Kestrel: Request trailer headers moved to new collection</span></span>](#kestrel-request-trailer-headers-moved-to-new-collection)
- [<span data-ttu-id="aa2ea-141">Kestrel：傳輸抽象層變更</span><span class="sxs-lookup"><span data-stu-id="aa2ea-141">Kestrel: Transport abstraction layer changes</span></span>](#kestrel-transport-abstractions-removed-and-made-public)
- [<span data-ttu-id="aa2ea-142">當地語系化：已標記為過時的 Api</span><span class="sxs-lookup"><span data-stu-id="aa2ea-142">Localization: APIs marked obsolete</span></span>](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [<span data-ttu-id="aa2ea-143">當地語系化：已移除 "Pubternal" Api</span><span class="sxs-lookup"><span data-stu-id="aa2ea-143">Localization: "Pubternal" APIs removed</span></span>](#localization-pubternal-apis-removed)
- [<span data-ttu-id="aa2ea-144">當地語系化：已移除 ResourceManagerWithCultureStringLocalizer 類別和 WithCulture 介面成員</span><span class="sxs-lookup"><span data-stu-id="aa2ea-144">Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed</span></span>](#localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed)
- [<span data-ttu-id="aa2ea-145">記錄： DebugLogger 類別已設為內部</span><span class="sxs-lookup"><span data-stu-id="aa2ea-145">Logging: DebugLogger class made internal</span></span>](#logging-debuglogger-class-made-internal)
- [<span data-ttu-id="aa2ea-146">MVC：已移除控制器動作非同步尾碼</span><span class="sxs-lookup"><span data-stu-id="aa2ea-146">MVC: Controller action Async suffix removed</span></span>](#mvc-async-suffix-trimmed-from-controller-action-names)
- [<span data-ttu-id="aa2ea-147">MVC： JsonResult 已移至 AspNetCore. Core</span><span class="sxs-lookup"><span data-stu-id="aa2ea-147">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [<span data-ttu-id="aa2ea-148">MVC：先行編譯工具已被取代</span><span class="sxs-lookup"><span data-stu-id="aa2ea-148">MVC: Precompilation tool deprecated</span></span>](#mvc-precompilation-tool-deprecated)
- [<span data-ttu-id="aa2ea-149">MVC：類型已變更為內部</span><span class="sxs-lookup"><span data-stu-id="aa2ea-149">MVC: Types changed to internal</span></span>](#mvc-pubternal-types-changed-to-internal)
- [<span data-ttu-id="aa2ea-150">MVC： Web API 相容性填充碼已移除</span><span class="sxs-lookup"><span data-stu-id="aa2ea-150">MVC: Web API compatibility shim removed</span></span>](#mvc-web-api-compatibility-shim-removed)
- [<span data-ttu-id="aa2ea-151">Razor：將執行時間編譯移至封裝</span><span class="sxs-lookup"><span data-stu-id="aa2ea-151">Razor: Runtime compilation moved to a package</span></span>](#razor-runtime-compilation-moved-to-a-package)
- [<span data-ttu-id="aa2ea-152">會話狀態：已移除已淘汰的 Api</span><span class="sxs-lookup"><span data-stu-id="aa2ea-152">Session state: Obsolete APIs removed</span></span>](#session-state-obsolete-apis-removed)
- [<span data-ttu-id="aa2ea-153">共用架構：從 AspNetCore 應用程式移除元件</span><span class="sxs-lookup"><span data-stu-id="aa2ea-153">Shared framework: Assembly removal from Microsoft.AspNetCore.App</span></span>](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [<span data-ttu-id="aa2ea-154">共用架構： AspNetCore 全部移除</span><span class="sxs-lookup"><span data-stu-id="aa2ea-154">Shared framework: Microsoft.AspNetCore.All removed</span></span>](#shared-framework-removed-microsoftaspnetcoreall)
- [<span data-ttu-id="aa2ea-155">SignalR： HandshakeProtocol. SuccessHandshakeData 已取代</span><span class="sxs-lookup"><span data-stu-id="aa2ea-155">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [<span data-ttu-id="aa2ea-156">SignalR：已移除 HubConnection 方法</span><span class="sxs-lookup"><span data-stu-id="aa2ea-156">SignalR: HubConnection methods removed</span></span>](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [<span data-ttu-id="aa2ea-157">SignalR： HubConnectionCoNtext 的函式已變更</span><span class="sxs-lookup"><span data-stu-id="aa2ea-157">SignalR: HubConnectionContext constructors changed</span></span>](#signalr-hubconnectioncontext-constructors-changed)
- [<span data-ttu-id="aa2ea-158">SignalR： JavaScript 用戶端封裝名稱變更</span><span class="sxs-lookup"><span data-stu-id="aa2ea-158">SignalR: JavaScript client package name change</span></span>](#signalr-javascript-client-package-name-changed)
- [<span data-ttu-id="aa2ea-159">SignalR： MessagePack 中樞通訊協定已移至 MessagePack 2.x 套件</span><span class="sxs-lookup"><span data-stu-id="aa2ea-159">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>](#signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package)
- [<span data-ttu-id="aa2ea-160">SignalR： MessagePack 中樞通訊協定選項類型已變更</span><span class="sxs-lookup"><span data-stu-id="aa2ea-160">SignalR: MessagePack Hub Protocol options type changed</span></span>](#signalr-messagepack-hub-protocol-options-type-changed)
- [<span data-ttu-id="aa2ea-161">SignalR：過時的 Api</span><span class="sxs-lookup"><span data-stu-id="aa2ea-161">SignalR: Obsolete APIs</span></span>](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [<span data-ttu-id="aa2ea-162">SignalR：已移除 UseSignalR 和 UseConnections 方法</span><span class="sxs-lookup"><span data-stu-id="aa2ea-162">SignalR: UseSignalR and UseConnections methods removed</span></span>](#signalr-usesignalr-and-useconnections-methods-removed)
- [<span data-ttu-id="aa2ea-163">Spa： SpaServices 和 NodeServices 主控台記錄器 fallback 預設變更</span><span class="sxs-lookup"><span data-stu-id="aa2ea-163">SPAs: SpaServices and NodeServices console logger fallback default change</span></span>](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [<span data-ttu-id="aa2ea-164">Spa：已標記為過時的 SpaServices 和 NodeServices</span><span class="sxs-lookup"><span data-stu-id="aa2ea-164">SPAs: SpaServices and NodeServices marked obsolete</span></span>](#spas-spaservices-and-nodeservices-marked-obsolete)
- [<span data-ttu-id="aa2ea-165">靜態檔案： CSV 內容類型已變更為標準相容</span><span class="sxs-lookup"><span data-stu-id="aa2ea-165">Static files: CSV content type changed to standards-compliant</span></span>](#static-files-csv-content-type-changed-to-standards-compliant)
- [<span data-ttu-id="aa2ea-166">目標 framework：不支援 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="aa2ea-166">Target framework: .NET Framework not supported</span></span>](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-50"></a><span data-ttu-id="aa2ea-167">ASP.NET Core 5。0</span><span class="sxs-lookup"><span data-stu-id="aa2ea-167">ASP.NET Core 5.0</span></span>

[!INCLUDE[Azure: Microsoft-prefixed Azure integration packages removed](~/includes/core-changes/aspnetcore/5.0/azure-integration-packages-removed.md)]

***

[!INCLUDE[Extensions: Package reference changes](~/includes/core-changes/aspnetcore/5.0/extensions-package-reference-changes.md)]

***

[!INCLUDE[HTTP: HttpClient instances created by IHttpClientFactory log integer status codes](~/includes/core-changes/aspnetcore/5.0/http-httpclient-instances-log-integer-status-codes.md)]

***

[!INCLUDE[HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced](~/includes/core-changes/aspnetcore/5.0/http-badhttprequestexception-obsolete.md)]

***

[!INCLUDE [Localization: "Pubternal" APIs removed](~/includes/core-changes/aspnetcore/5.0/localization-pubternal-apis-removed.md)]

***

[!INCLUDE[Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed](~/includes/core-changes/aspnetcore/5.0/localization-members-removed.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-package.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol options type changed](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-hub-protocol-options-changed.md)]

***

[!INCLUDE[SignalR: UseSignalR and UseConnections methods removed](~/includes/core-changes/aspnetcore/5.0/signalr-usesignalr-useconnections-removed.md)]

***

[!INCLUDE[Static files: CSV content type changed to standards-compliant](~/includes/core-changes/aspnetcore/5.0/static-files-csv-content-type-changed.md)]

***

## <a name="aspnet-core-31"></a><span data-ttu-id="aa2ea-168">ASP.NET Core 3。1</span><span class="sxs-lookup"><span data-stu-id="aa2ea-168">ASP.NET Core 3.1</span></span>

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a><span data-ttu-id="aa2ea-169">ASP.NET Core 3。0</span><span class="sxs-lookup"><span data-stu-id="aa2ea-169">ASP.NET Core 3.0</span></span>

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
