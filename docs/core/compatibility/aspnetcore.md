---
title: ASP.NET Core 重大變更
titleSuffix: ''
description: 列出 ASP.NET Core 中的重大變更。
ms.date: 09/09/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: 2af0cc6721b66b1d07b196e4ba330f8425c14752
ms.sourcegitcommit: 6d4ee46871deb9ea1e45bb5f3784474e240bbc26
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2020
ms.locfileid: "90022983"
---
# <a name="aspnet-core-breaking-changes"></a><span data-ttu-id="bf222-103">ASP.NET Core 重大變更</span><span class="sxs-lookup"><span data-stu-id="bf222-103">ASP.NET Core breaking changes</span></span>

<span data-ttu-id="bf222-104">ASP.NET Core 提供 .NET Core 所使用的 web 應用程式開發功能。</span><span class="sxs-lookup"><span data-stu-id="bf222-104">ASP.NET Core provides the web app development features used by .NET Core.</span></span>

<span data-ttu-id="bf222-105">針對特定版本中的重大變更，請選取下列其中一個連結：</span><span class="sxs-lookup"><span data-stu-id="bf222-105">Select one of the following links for breaking changes in a specific version:</span></span>

* [<span data-ttu-id="bf222-106">ASP.NET Core 5。0</span><span class="sxs-lookup"><span data-stu-id="bf222-106">ASP.NET Core 5.0</span></span>](#aspnet-core-50)
* [<span data-ttu-id="bf222-107">ASP.NET Core 3。1</span><span class="sxs-lookup"><span data-stu-id="bf222-107">ASP.NET Core 3.1</span></span>](#aspnet-core-31)
* [<span data-ttu-id="bf222-108">ASP.NET Core 3。0</span><span class="sxs-lookup"><span data-stu-id="bf222-108">ASP.NET Core 3.0</span></span>](#aspnet-core-30)

<span data-ttu-id="bf222-109">下列 ASP.NET Core 3.0、3.1 和5.0 的重大變更記載于此頁面：</span><span class="sxs-lookup"><span data-stu-id="bf222-109">The following breaking changes in ASP.NET Core 3.0, 3.1, and 5.0 are documented on this page:</span></span>

- [<span data-ttu-id="bf222-110">已移除過時的 Antiforgery、CORS、診斷、MVC 和路由 Api</span><span class="sxs-lookup"><span data-stu-id="bf222-110">Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed</span></span>](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [<span data-ttu-id="bf222-111">驗證： Google + 淘汰</span><span class="sxs-lookup"><span data-stu-id="bf222-111">Authentication: Google+ deprecation</span></span>](#authentication-google-deprecated-and-replaced)
- [<span data-ttu-id="bf222-112">驗證：已移除 HttpCoNtext 驗證屬性</span><span class="sxs-lookup"><span data-stu-id="bf222-112">Authentication: HttpContext.Authentication property removed</span></span>](#authentication-httpcontextauthentication-property-removed)
- [<span data-ttu-id="bf222-113">驗證：已取代類型上的 Newtonsoft.Js</span><span class="sxs-lookup"><span data-stu-id="bf222-113">Authentication: Newtonsoft.Json types replaced</span></span>](#authentication-newtonsoftjson-types-replaced)
- [<span data-ttu-id="bf222-114">驗證： OAuthHandler ExchangeCodeAsync 簽章已變更</span><span class="sxs-lookup"><span data-stu-id="bf222-114">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [<span data-ttu-id="bf222-115">授權： AddAuthorization 多載移至不同的元件</span><span class="sxs-lookup"><span data-stu-id="bf222-115">Authorization: AddAuthorization overload moved to different assembly</span></span>](#authorization-addauthorization-overload-moved-to-different-assembly)
- [<span data-ttu-id="bf222-116">授權： IAllowAnonymous 已從 AuthorizationFilterCoNtext 中移除。篩選器</span><span class="sxs-lookup"><span data-stu-id="bf222-116">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [<span data-ttu-id="bf222-117">授權： IAuthorizationPolicyProvider 執行需要新的方法</span><span class="sxs-lookup"><span data-stu-id="bf222-117">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [<span data-ttu-id="bf222-118">授權：端點路由中的資源為 HttpCoNtext</span><span class="sxs-lookup"><span data-stu-id="bf222-118">Authorization: Resource in endpoint routing is HttpContext</span></span>](#authorization-resource-in-endpoint-routing-is-httpcontext)
- [<span data-ttu-id="bf222-119">Azure：已移除的 Microsoft 首碼 Azure 整合套件</span><span class="sxs-lookup"><span data-stu-id="bf222-119">Azure: Microsoft-prefixed Azure integration packages removed</span></span>](#azure-microsoft-prefixed-azure-integration-packages-removed)
- [<span data-ttu-id="bf222-120">ASP.NET apps 已淘汰且禁止 BinaryFormatter 序列化方法</span><span class="sxs-lookup"><span data-stu-id="bf222-120">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps)
- [<span data-ttu-id="bf222-121">Blazor：在編譯時期從元件中修剪的無意義空白</span><span class="sxs-lookup"><span data-stu-id="bf222-121">Blazor: Insignificant whitespace trimmed from components at compile time</span></span>](#blazor-insignificant-whitespace-trimmed-from-components-at-compile-time)
- [<span data-ttu-id="bf222-122">Blazor： NuGet 套件的目標 framework 已變更</span><span class="sxs-lookup"><span data-stu-id="bf222-122">Blazor: Target framework of NuGet packages changed</span></span>](#blazor-target-framework-of-nuget-packages-changed)
- [<span data-ttu-id="bf222-123">快取：已移除 CompactOnMemoryPressure 屬性</span><span class="sxs-lookup"><span data-stu-id="bf222-123">Caching: CompactOnMemoryPressure property removed</span></span>](#caching-compactonmemorypressure-property-removed)
- [<span data-ttu-id="bf222-124">Caching： SqlClient 使用新的套件</span><span class="sxs-lookup"><span data-stu-id="bf222-124">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [<span data-ttu-id="bf222-125">快取： ResponseCaching "pubternal" 類型已變更為內部</span><span class="sxs-lookup"><span data-stu-id="bf222-125">Caching: ResponseCaching "pubternal" types changed to internal</span></span>](#caching-responsecaching-pubternal-types-changed-to-internal)
- [<span data-ttu-id="bf222-126">資料保護： DataProtection. AzureStorage 使用新的 Azure 儲存體 Api</span><span class="sxs-lookup"><span data-stu-id="bf222-126">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [<span data-ttu-id="bf222-127">擴充功能：套件參考變更會影響某些 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="bf222-127">Extensions: Package reference changes affecting some NuGet packages</span></span>](#extensions-package-reference-changes-affecting-some-nuget-packages)
- [<span data-ttu-id="bf222-128">裝載：已從 Windows 裝載套件組合移除 AspNetCoreModule V1</span><span class="sxs-lookup"><span data-stu-id="bf222-128">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [<span data-ttu-id="bf222-129">裝載：泛型主機限制啟動的函式插入</span><span class="sxs-lookup"><span data-stu-id="bf222-129">Hosting: Generic host restricts Startup constructor injection</span></span>](#hosting-generic-host-restricts-startup-constructor-injection)
- [<span data-ttu-id="bf222-130">裝載：針對 IIS 跨進程應用程式啟用 HTTPS 重新導向</span><span class="sxs-lookup"><span data-stu-id="bf222-130">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [<span data-ttu-id="bf222-131">裝載：已取代 IHostingEnvironment 和 IApplicationLifetime 類型</span><span class="sxs-lookup"><span data-stu-id="bf222-131">Hosting: IHostingEnvironment and IApplicationLifetime types replaced</span></span>](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="bf222-132">裝載： ObjectPoolProvider 已從 >webhostbuilder 相依性中移除</span><span class="sxs-lookup"><span data-stu-id="bf222-132">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [<span data-ttu-id="bf222-133">HTTP： Kestrel 和 IIS BadHttpRequestException 類型標示為已淘汰和已取代</span><span class="sxs-lookup"><span data-stu-id="bf222-133">HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced</span></span>](#http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="bf222-134">HTTP：瀏覽器 SameSite 變更會影響驗證</span><span class="sxs-lookup"><span data-stu-id="bf222-134">HTTP: Browser SameSite changes impact authentication</span></span>](#http-browser-samesite-changes-impact-authentication)
- [<span data-ttu-id="bf222-135">HTTP：已移除 DefaultHttpCoNtext 擴充性</span><span class="sxs-lookup"><span data-stu-id="bf222-135">HTTP: DefaultHttpContext extensibility removed</span></span>](#http-defaulthttpcontext-extensibility-removed)
- [<span data-ttu-id="bf222-136">HTTP： HeaderNames 欄位已變更為靜態 readonly</span><span class="sxs-lookup"><span data-stu-id="bf222-136">HTTP: HeaderNames fields changed to static readonly</span></span>](#http-headernames-constants-changed-to-static-readonly)
- [<span data-ttu-id="bf222-137">HTTP： IHttpClientFactory 記錄整數狀態碼所建立的 HttpClient 實例</span><span class="sxs-lookup"><span data-stu-id="bf222-137">HTTP: HttpClient instances created by IHttpClientFactory log integer status codes</span></span>](#http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes)
- [<span data-ttu-id="bf222-138">HTTP：回應主體基礎結構變更</span><span class="sxs-lookup"><span data-stu-id="bf222-138">HTTP: Response body infrastructure changes</span></span>](#http-response-body-infrastructure-changes)
- [<span data-ttu-id="bf222-139">HTTP：某些 cookie SameSite 預設值已變更</span><span class="sxs-lookup"><span data-stu-id="bf222-139">HTTP: Some cookie SameSite default values changed</span></span>](#http-some-cookie-samesite-defaults-changed-to-none)
- [<span data-ttu-id="bf222-140">HTTP：同步 IO 預設為停用</span><span class="sxs-lookup"><span data-stu-id="bf222-140">HTTP: Synchronous IO disabled by default</span></span>](#http-synchronous-io-disabled-in-all-servers)
- [<span data-ttu-id="bf222-141">HttpSys：用戶端憑證重新協商預設為停用</span><span class="sxs-lookup"><span data-stu-id="bf222-141">HttpSys: Client certificate renegotiation disabled by default</span></span>](#httpsys-client-certificate-renegotiation-disabled-by-default)
- [<span data-ttu-id="bf222-142">Identity： AddDefaultUI 方法多載已移除</span><span class="sxs-lookup"><span data-stu-id="bf222-142">Identity: AddDefaultUI method overload removed</span></span>](#identity-adddefaultui-method-overload-removed)
- [<span data-ttu-id="bf222-143">身分識別： UI 啟動程式版本變更</span><span class="sxs-lookup"><span data-stu-id="bf222-143">Identity: UI Bootstrap version change</span></span>](#identity-default-bootstrap-version-of-ui-changed)
- [<span data-ttu-id="bf222-144">Identity： SignInAsync 會針對未驗證的身分識別擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="bf222-144">Identity: SignInAsync throws exception for unauthenticated identity</span></span>](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [<span data-ttu-id="bf222-145">Identity：使用函式接受新的參數</span><span class="sxs-lookup"><span data-stu-id="bf222-145">Identity: SignInManager constructor accepts new parameter</span></span>](#identity-signinmanager-constructor-accepts-new-parameter)
- [<span data-ttu-id="bf222-146">身分識別： UI 使用靜態 web 資產功能</span><span class="sxs-lookup"><span data-stu-id="bf222-146">Identity: UI uses static web assets feature</span></span>](#identity-ui-uses-static-web-assets-feature)
- [<span data-ttu-id="bf222-147">IIS：保留 UrlRewrite 中介軟體查詢字串</span><span class="sxs-lookup"><span data-stu-id="bf222-147">IIS: UrlRewrite middleware query strings are preserved</span></span>](#iis-urlrewrite-middleware-query-strings-are-preserved)
- [<span data-ttu-id="bf222-148">Kestrel：預設會偵測到執行時間的設定變更</span><span class="sxs-lookup"><span data-stu-id="bf222-148">Kestrel: Configuration changes at run time detected by default</span></span>](#kestrel-configuration-changes-at-run-time-detected-by-default)
- [<span data-ttu-id="bf222-149">Kestrel：已移除連接配接器</span><span class="sxs-lookup"><span data-stu-id="bf222-149">Kestrel: Connection adapters removed</span></span>](#kestrel-connection-adapters-removed)
- [<span data-ttu-id="bf222-150">Kestrel：預設支援的 TLS 通訊協定版本已變更</span><span class="sxs-lookup"><span data-stu-id="bf222-150">Kestrel: Default supported TLS protocol versions changed</span></span>](#kestrel-default-supported-tls-protocol-versions-changed)
- [<span data-ttu-id="bf222-151">Kestrel：已移除空白的 HTTPS 元件</span><span class="sxs-lookup"><span data-stu-id="bf222-151">Kestrel: Empty HTTPS assembly removed</span></span>](#kestrel-empty-https-assembly-removed)
- [<span data-ttu-id="bf222-152">Kestrel：在不相容的 Windows 版本上，透過 TLS 停用 HTTP/2</span><span class="sxs-lookup"><span data-stu-id="bf222-152">Kestrel: HTTP/2 disabled over TLS on incompatible Windows versions</span></span>](#kestrel-http2-disabled-over-tls-on-incompatible-windows-versions)
- [<span data-ttu-id="bf222-153">Kestrel： Libuv 傳輸標示為已淘汰</span><span class="sxs-lookup"><span data-stu-id="bf222-153">Kestrel: Libuv transport marked as obsolete</span></span>](#kestrel-libuv-transport-marked-as-obsolete)
- [<span data-ttu-id="bf222-154">Kestrel：要求尾端標頭移至新集合</span><span class="sxs-lookup"><span data-stu-id="bf222-154">Kestrel: Request trailer headers moved to new collection</span></span>](#kestrel-request-trailer-headers-moved-to-new-collection)
- [<span data-ttu-id="bf222-155">Kestrel：傳輸抽象層變更</span><span class="sxs-lookup"><span data-stu-id="bf222-155">Kestrel: Transport abstraction layer changes</span></span>](#kestrel-transport-abstractions-removed-and-made-public)
- [<span data-ttu-id="bf222-156">當地語系化： Api 已標記為過時</span><span class="sxs-lookup"><span data-stu-id="bf222-156">Localization: APIs marked obsolete</span></span>](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [<span data-ttu-id="bf222-157">當地語系化：已移除 "Pubternal" Api</span><span class="sxs-lookup"><span data-stu-id="bf222-157">Localization: "Pubternal" APIs removed</span></span>](#localization-pubternal-apis-removed)
- [<span data-ttu-id="bf222-158">當地語系化：在要求當地語系化中介軟體中移除過時的函式</span><span class="sxs-lookup"><span data-stu-id="bf222-158">Localization: Obsolete constructor removed in request localization middleware</span></span>](#localization-obsolete-constructor-removed-in-request-localization-middleware)
- [<span data-ttu-id="bf222-159">當地語系化：已移除 ResourceManagerWithCultureStringLocalizer 類別和 WithCulture 介面成員</span><span class="sxs-lookup"><span data-stu-id="bf222-159">Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed</span></span>](#localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed)
- [<span data-ttu-id="bf222-160">記錄： DebugLogger 類別設為內部</span><span class="sxs-lookup"><span data-stu-id="bf222-160">Logging: DebugLogger class made internal</span></span>](#logging-debuglogger-class-made-internal)
- [<span data-ttu-id="bf222-161">中介軟體：資料庫錯誤頁面標示為已淘汰</span><span class="sxs-lookup"><span data-stu-id="bf222-161">Middleware: Database error page marked as obsolete</span></span>](#middleware-database-error-page-marked-as-obsolete)
- [<span data-ttu-id="bf222-162">中介軟體：如果找不到處理程式，中介軟體會擲回原始例外狀況</span><span class="sxs-lookup"><span data-stu-id="bf222-162">Middleware: Exception Handler Middleware throws original exception if handler not found</span></span>](#middleware-exception-handler-middleware-throws-original-exception-if-handler-not-found)
- [<span data-ttu-id="bf222-163">MVC：已移除控制器動作非同步尾碼</span><span class="sxs-lookup"><span data-stu-id="bf222-163">MVC: Controller action Async suffix removed</span></span>](#mvc-async-suffix-trimmed-from-controller-action-names)
- [<span data-ttu-id="bf222-164">MVC： JsonResult 已移至 AspNetCore</span><span class="sxs-lookup"><span data-stu-id="bf222-164">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [<span data-ttu-id="bf222-165">MVC：先行編譯工具已淘汰</span><span class="sxs-lookup"><span data-stu-id="bf222-165">MVC: Precompilation tool deprecated</span></span>](#mvc-precompilation-tool-deprecated)
- [<span data-ttu-id="bf222-166">MVC：類型已變更為內部</span><span class="sxs-lookup"><span data-stu-id="bf222-166">MVC: Types changed to internal</span></span>](#mvc-pubternal-types-changed-to-internal)
- [<span data-ttu-id="bf222-167">MVC：已移除 Web API 相容性填充碼</span><span class="sxs-lookup"><span data-stu-id="bf222-167">MVC: Web API compatibility shim removed</span></span>](#mvc-web-api-compatibility-shim-removed)
- [<span data-ttu-id="bf222-168">Razor：已移除 RazorTemplateEngine API</span><span class="sxs-lookup"><span data-stu-id="bf222-168">Razor: RazorTemplateEngine API removed</span></span>](#razor-razortemplateengine-api-removed)
- [<span data-ttu-id="bf222-169">Razor：執行時間編譯已移至封裝</span><span class="sxs-lookup"><span data-stu-id="bf222-169">Razor: Runtime compilation moved to a package</span></span>](#razor-runtime-compilation-moved-to-a-package)
- [<span data-ttu-id="bf222-170">安全性：已移除 Cookie 名稱編碼</span><span class="sxs-lookup"><span data-stu-id="bf222-170">Security: Cookie name encoding removed</span></span>](#security-cookie-name-encoding-removed)
- [<span data-ttu-id="bf222-171">安全性：已更新 Microsoft.identitymodel NuGet 套件版本</span><span class="sxs-lookup"><span data-stu-id="bf222-171">Security: IdentityModel NuGet package versions updated</span></span>](#security-identitymodel-nuget-package-versions-updated)
- [<span data-ttu-id="bf222-172">會話狀態：已移除淘汰的 Api</span><span class="sxs-lookup"><span data-stu-id="bf222-172">Session state: Obsolete APIs removed</span></span>](#session-state-obsolete-apis-removed)
- [<span data-ttu-id="bf222-173">共用架構：從 AspNetCore 移除元件</span><span class="sxs-lookup"><span data-stu-id="bf222-173">Shared framework: Assembly removal from Microsoft.AspNetCore.App</span></span>](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [<span data-ttu-id="bf222-174">共用架構： Microsoft. AspNetCore. 全部移除</span><span class="sxs-lookup"><span data-stu-id="bf222-174">Shared framework: Microsoft.AspNetCore.All removed</span></span>](#shared-framework-removed-microsoftaspnetcoreall)
- [<span data-ttu-id="bf222-175">SignalR：已取代 HandshakeProtocol SuccessHandshakeData</span><span class="sxs-lookup"><span data-stu-id="bf222-175">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [<span data-ttu-id="bf222-176">SignalR：已移除 HubConnection 方法</span><span class="sxs-lookup"><span data-stu-id="bf222-176">SignalR: HubConnection methods removed</span></span>](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [<span data-ttu-id="bf222-177">SignalR： HubConnectionCoNtext 的函式已變更</span><span class="sxs-lookup"><span data-stu-id="bf222-177">SignalR: HubConnectionContext constructors changed</span></span>](#signalr-hubconnectioncontext-constructors-changed)
- [<span data-ttu-id="bf222-178">SignalR： JavaScript 用戶端套件名稱變更</span><span class="sxs-lookup"><span data-stu-id="bf222-178">SignalR: JavaScript client package name change</span></span>](#signalr-javascript-client-package-name-changed)
- [<span data-ttu-id="bf222-179">SignalR： MessagePack Hub 通訊協定已移至 MessagePack 2.x 套件</span><span class="sxs-lookup"><span data-stu-id="bf222-179">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>](#signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package)
- [<span data-ttu-id="bf222-180">SignalR： MessagePack Hub 通訊協定選項類型已變更</span><span class="sxs-lookup"><span data-stu-id="bf222-180">SignalR: MessagePack Hub Protocol options type changed</span></span>](#signalr-messagepack-hub-protocol-options-type-changed)
- [<span data-ttu-id="bf222-181">SignalR：淘汰的 Api</span><span class="sxs-lookup"><span data-stu-id="bf222-181">SignalR: Obsolete APIs</span></span>](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [<span data-ttu-id="bf222-182">SignalR：已移除 UseSignalR 和 UseConnections 方法</span><span class="sxs-lookup"><span data-stu-id="bf222-182">SignalR: UseSignalR and UseConnections methods removed</span></span>](#signalr-usesignalr-and-useconnections-methods-removed)
- [<span data-ttu-id="bf222-183">Spa： SpaServices 和 NodeServices 主控台記錄器 fallback 預設變更</span><span class="sxs-lookup"><span data-stu-id="bf222-183">SPAs: SpaServices and NodeServices console logger fallback default change</span></span>](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [<span data-ttu-id="bf222-184">Spa： SpaServices 和 NodeServices 已標示為過時</span><span class="sxs-lookup"><span data-stu-id="bf222-184">SPAs: SpaServices and NodeServices marked obsolete</span></span>](#spas-spaservices-and-nodeservices-marked-obsolete)
- [<span data-ttu-id="bf222-185">靜態檔案： CSV 內容類型已變更為符合標準</span><span class="sxs-lookup"><span data-stu-id="bf222-185">Static files: CSV content type changed to standards-compliant</span></span>](#static-files-csv-content-type-changed-to-standards-compliant)
- [<span data-ttu-id="bf222-186">目標 framework：不支援 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bf222-186">Target framework: .NET Framework not supported</span></span>](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-50"></a><span data-ttu-id="bf222-187">ASP.NET Core 5。0</span><span class="sxs-lookup"><span data-stu-id="bf222-187">ASP.NET Core 5.0</span></span>

[!INCLUDE[Authorization: Resource in endpoint routing is HttpContext](~/includes/core-changes/aspnetcore/5.0/authorization-resource-in-endpoint-routing.md)]

***

[!INCLUDE[Azure: Microsoft-prefixed Azure integration packages removed](~/includes/core-changes/aspnetcore/5.0/azure-integration-packages-removed.md)]

***

[!INCLUDE [binaryformatter-serialization-obsolete](../../../includes/core-changes/corefx/5.0/binaryformatter-serialization-obsolete.md)]

***

[!INCLUDE[Blazor: Insignificant whitespace trimmed from components at compile time](~/includes/core-changes/aspnetcore/5.0/blazor-components-trim-insignificant-whitespace.md)]

***

[!INCLUDE[Blazor: Target framework of NuGet packages changed](~/includes/core-changes/aspnetcore/5.0/blazor-packages-target-framework-changed.md)]

***

[!INCLUDE[Extensions: Package reference changes](~/includes/core-changes/aspnetcore/5.0/extensions-package-reference-changes.md)]

***

[!INCLUDE[HTTP: HttpClient instances created by IHttpClientFactory log integer status codes](~/includes/core-changes/aspnetcore/5.0/http-httpclient-instances-log-integer-status-codes.md)]

***

[!INCLUDE[HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced](~/includes/core-changes/aspnetcore/5.0/http-badhttprequestexception-obsolete.md)]

***

[!INCLUDE[HttpSys: Client certificate renegotiation disabled by default](~/includes/core-changes/aspnetcore/5.0/httpsys-client-certificate-renegotiation-disabled-by-default.md)]

***

[!INCLUDE[IIS: UrlRewrite middleware query strings are preserved](~/includes/core-changes/aspnetcore/5.0/iis-urlrewrite-middleware-query-strings-are-preserved.md)]

***

[!INCLUDE[Kestrel: Configuration changes at run time detected by default](~/includes/core-changes/aspnetcore/5.0/kestrel-configuration-changes-at-run-time-detected-by-default.md)]

***
[!INCLUDE[Kestrel: Default supported TLS protocol versions changed](~/includes/core-changes/aspnetcore/5.0/kestrel-default-supported-tls-protocol-versions-changed.md)]

***

[!INCLUDE[Kestrel: HTTP/2 disabled over TLS on incompatible Windows versions](~/includes/core-changes/aspnetcore/5.0/kestrel-disables-http2-over-tls.md)]

***

[!INCLUDE[Kestrel: Libuv transport marked as obsolete](~/includes/core-changes/aspnetcore/5.0/kestrel-libuv-transport-obsolete.md)]

***

[!INCLUDE[Localization: "Pubternal" APIs removed](~/includes/core-changes/aspnetcore/5.0/localization-pubternal-apis-removed.md)]

***

[!INCLUDE[Localization: Obsolete constructor removed in request localization middleware](~/includes/core-changes/aspnetcore/5.0/localization-requestlocalizationmiddleware-constructor-removed.md)]

***

[!INCLUDE[Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed](~/includes/core-changes/aspnetcore/5.0/localization-members-removed.md)]

***

[!INCLUDE[Middleware: Database error page marked as obsolete](~/includes/core-changes/aspnetcore/5.0/middleware-database-error-page-obsolete.md)]

***

[!INCLUDE[Middleware: Exception Handler Middleware throws original exception if handler not found](~/includes/core-changes/aspnetcore/5.0/middleware-exception-handler-throws-original-exception.md)]

***

[!INCLUDE[Security: Cookie name encoding removed](~/includes/core-changes/aspnetcore/5.0/security-cookie-name-encoding-removed.md)]

***

[!INCLUDE[Security: IdentityModel NuGet package versions updated](~/includes/core-changes/aspnetcore/5.0/security-identitymodel-nuget-package-versions-updated.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-package.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol options type changed](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-hub-protocol-options-changed.md)]

***

[!INCLUDE[SignalR: UseSignalR and UseConnections methods removed](~/includes/core-changes/aspnetcore/5.0/signalr-usesignalr-useconnections-removed.md)]

***

[!INCLUDE[Static files: CSV content type changed to standards-compliant](~/includes/core-changes/aspnetcore/5.0/static-files-csv-content-type-changed.md)]

***

## <a name="aspnet-core-31"></a><span data-ttu-id="bf222-188">ASP.NET Core 3。1</span><span class="sxs-lookup"><span data-stu-id="bf222-188">ASP.NET Core 3.1</span></span>

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a><span data-ttu-id="bf222-189">ASP.NET Core 3。0</span><span class="sxs-lookup"><span data-stu-id="bf222-189">ASP.NET Core 3.0</span></span>

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

[!INCLUDE[Razor: RazorTemplatEengine API removed](~/includes/core-changes/aspnetcore/3.0/razor-razortemplateengine-api-removed.md)]

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
