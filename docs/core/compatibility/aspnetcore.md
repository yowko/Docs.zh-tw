---
title: ASP.NET核心突破性更改
titleSuffix: ''
description: 列出ASP.NET核心中的重大更改。
ms.date: 03/25/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: eb80be54da8ac0b15d854304e53a7ade7f42da1b
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291722"
---
# <a name="aspnet-core-breaking-changes"></a>ASP.NET核心突破性更改

ASP.NET核心提供 .NET Core 使用的 Web 應用開發功能。

此頁面將記錄以下重大更改：

- [已刪除的過期反偽造、CORS、診斷、MVC 和路由 API](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [身份驗證：Google+ 棄用](#authentication-google-deprecated-and-replaced)
- [身份驗證：HTTPCoNtext.身份驗證屬性已刪除](#authentication-httpcontextauthentication-property-removed)
- [身份驗證：牛頓軟.Json 類型替換](#authentication-newtonsoftjson-types-replaced)
- [身份驗證：OAuthHandler 交換代碼同步簽名已更改](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [授權：將授權重載移動到不同的程式集](#authorization-addauthorization-overload-moved-to-different-assembly)
- [授權：從授權篩選器上下文中刪除 IAllowAnonymous。篩檢程式](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [授權：I授權策略提供程式實現需要新方法](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [Azure：已刪除 Microsoft 預固定的 Azure 集成包](#azure-microsoft-prefixed-azure-integration-packages-removed)
- [緩存：已刪除 CompactOn 記憶體壓力屬性](#caching-compactonmemorypressure-property-removed)
- [緩存：微軟.擴展.緩存.SqlServer 使用新的 SqlClient 包](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [緩存：回應緩存"公共"類型更改為內部](#caching-responsecaching-pubternal-types-changed-to-internal)
- [資料保護：資料保護.Azure 存儲使用新的 Azure 存儲 API](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [託管：從 Windows 託管捆綁包中刪除的 AspNetCore 模組 V1](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [託管：通用主機限制啟動建構函式注入](#hosting-generic-host-restricts-startup-constructor-injection)
- [託管：為 IIS 進程外應用啟用 HTTPS 重定向](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [託管：已替換 IHosting 環境和 I應用程式生命週期類型](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [託管：從 WebHostBuilder 依賴項中刪除物件集區提供程式](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [HTTP： 瀏覽器同網站更改影響身份驗證](#http-browser-samesite-changes-impact-authentication)
- [HTTP： 預設 HttpCoNtext 擴充性已被刪除](#http-defaulthttpcontext-extensibility-removed)
- [HTTP：標題名稱欄位更改為靜態唯讀](#http-headernames-constants-changed-to-static-readonly)
- [HTTP：回應正文基礎結構更改](#http-response-body-infrastructure-changes)
- [HTTP： 某些 Cookie 同網站預設值已更改](#http-some-cookie-samesite-defaults-changed-to-none)
- [HTTP：預設情況下禁用同步 IO](#http-synchronous-io-disabled-in-all-servers)
- [標識：刪除添加 DefaultUI 方法重載](#identity-adddefaultui-method-overload-removed)
- [標識：UI 引導版本更改](#identity-default-bootstrap-version-of-ui-changed)
- [標識：SignInAsync 為未身份驗證的標識引發異常](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [標識：SignInManager 建構函式接受新參數](#identity-signinmanager-constructor-accepts-new-parameter)
- [標識：UI 使用靜態 Web 資產功能](#identity-ui-uses-static-web-assets-feature)
- [Kestrel：連接配接器已移除](#kestrel-connection-adapters-removed)
- [Kestrel： 空 HTTPS 程式集已刪除](#kestrel-empty-https-assembly-removed)
- [Kestrel：請求將拖車頭移動到新集合](#kestrel-request-trailer-headers-moved-to-new-collection)
- [Kestrel：傳輸抽象層更改](#kestrel-transport-abstractions-removed-and-made-public)
- [當地語系化：標記為過時的 API](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [日誌記錄：調試記錄器類是內部製作的](#logging-debuglogger-class-made-internal)
- [MVC：已刪除控制器操作非同步尾碼](#mvc-async-suffix-trimmed-from-controller-action-names)
- [MVC： JsonResult 移動到微軟.AspNetCore.Mvc.Core](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [MVC：預編譯工具已棄用](#mvc-precompilation-tool-deprecated)
- [MVC：類型更改為內部](#mvc-pubternal-types-changed-to-internal)
- [MVC：已刪除 Web API 相容性](#mvc-web-api-compatibility-shim-removed)
- [Razor：運行時編譯移動到包](#razor-runtime-compilation-moved-to-a-package)
- [會話狀態：已刪除的已過期 API](#session-state-obsolete-apis-removed)
- [共用框架：從 Microsoft 中刪除程式集.AspNetCore.App](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [共用框架：微軟.AspNetCore.全部刪除](#shared-framework-removed-microsoftaspnetcoreall)
- [信號R：握手協定.成功握手資料被替換](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [信號R：已刪除集線器連接方法](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [信號R：中心連接上下文建構函式已更改](#signalr-hubconnectioncontext-constructors-changed)
- [信號R：JavaScript用戶端包名稱更改](#signalr-javascript-client-package-name-changed)
- [信號R：過時的 API](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [信號R：使用信號R和使用連接方法被刪除](#signalr-usesignalr-and-useconnections-methods-removed)
- [Spa 服務：標記為過時的 Spa 服務和節點服務](#spas-spaservices-and-nodeservices-marked-obsolete)
- [Spa服務和節點服務主控台記錄器回退預設更改](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [目標框架： .NET 框架不支援](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-50"></a>ASP.NET核心 5.0

[!INCLUDE[Azure: Microsoft-prefixed Azure integration packages removed](~/includes/core-changes/aspnetcore/5.0/azure-integration-packages-removed.md)]

***

[!INCLUDE[SignalR: UseSignalR and UseConnections methods removed](~/includes/core-changes/aspnetcore/5.0/signalr-usesignalr-useconnections-removed.md)]

***

## <a name="aspnet-core-31"></a>ASP.NET核心 3.1

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a>ASP.NET核心 3.0

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
