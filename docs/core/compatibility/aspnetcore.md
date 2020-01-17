---
title: ASP.NET Core 的重大變更-.NET Core
description: 列出 ASP.NET Core 中的重大變更。
ms.date: 01/10/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: 261788722e09a6fa5b9427b5a220b69a2367b751
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116582"
---
# <a name="aspnet-core-breaking-changes"></a>ASP.NET Core 的重大變更

ASP.NET Core 提供 .NET Core 所使用的 web 應用程式開發功能。

下列重大變更記載于此頁面：

- [HTTP：瀏覽器 SameSite 變更影響驗證](#http-browser-samesite-changes-impact-authentication)
- [已移除過時的 Antiforgery、CORS、診斷、MVC 和路由 Api](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [驗證： Google + 淘汰](#authentication-google-deprecated-and-replaced)
- [驗證：已移除 HttpCoNtext 驗證屬性](#authentication-httpcontextauthentication-property-removed)
- [驗證： Newtonsoft 已取代的 Json 類型](#authentication-newtonsoftjson-types-replaced)
- [驗證： OAuthHandler ExchangeCodeAsync 簽章已變更](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [授權： AddAuthorization 多載已移至不同的元件](#authorization-addauthorization-overload-moved-to-different-assembly)
- [授權： IAllowAnonymous 已從 AuthorizationFilterCoNtext 移除。篩選](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [授權： IAuthorizationPolicyProvider 的部署需要新的方法](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [Caching： CompactOnMemoryPressure 屬性已移除](#caching-compactonmemorypressure-property-removed)
- [快取： SqlClient 使用新的封裝](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [Caching： ResponseCaching "pubternal" 類型已變更為 internal](#caching-responsecaching-pubternal-types-changed-to-internal)
- [資料保護： DataProtection. AzureStorage 使用新的 Azure 儲存體 Api](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [裝載：已從 Windows 裝載套件組合中移除 AspNetCoreModule V1](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [裝載：泛型主機會限制啟動的函數插入](#hosting-generic-host-restricts-startup-constructor-injection)
- [裝載：已為 IIS 跨進程應用程式啟用 HTTPS 重新導向](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [裝載：已取代 IHostingEnvironment 和 IApplicationLifetime 類型](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [裝載：已從 WebHostBuilder 相依性移除 ObjectPoolProvider](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [HTTP： DefaultHttpCoNtext 擴充性已移除](#http-defaulthttpcontext-extensibility-removed)
- [HTTP： HeaderNames 欄位已變更為靜態唯讀](#http-headernames-constants-changed-to-static-readonly)
- [HTTP：回應主體基礎結構變更](#http-response-body-infrastructure-changes)
- [HTTP：某些 cookie SameSite 預設值已變更](#http-some-cookie-samesite-defaults-changed-to-none)
- [HTTP：預設停用同步 IO](#http-synchronous-io-disabled-in-all-servers)
- [識別： AddDefaultUI 方法多載已移除](#identity-adddefaultui-method-overload-removed)
- [身分識別： UI 啟動程式版本變更](#identity-default-bootstrap-version-of-ui-changed)
- [身分識別： SignInAsync 擲回未驗證身分識別的例外狀況](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [身分識別：使用的函式接受新的參數](#identity-signinmanager-constructor-accepts-new-parameter)
- [身分識別： UI 使用靜態 web 資產功能](#identity-ui-uses-static-web-assets-feature)
- [Kestrel：已移除連接介面卡](#kestrel-connection-adapters-removed)
- [Kestrel：已移除空的 HTTPS 元件](#kestrel-empty-https-assembly-removed)
- [Kestrel：要求尾標頭已移至新的集合](#kestrel-request-trailer-headers-moved-to-new-collection)
- [Kestrel：傳輸抽象層變更](#kestrel-transport-abstractions-removed-and-made-public)
- [當地語系化：已標記為過時的 Api](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [記錄： DebugLogger 類別已設為內部](#logging-debuglogger-class-made-internal)
- [MVC：已移除控制器動作非同步尾碼](#mvc-async-suffix-trimmed-from-controller-action-names)
- [MVC： JsonResult 已移至 AspNetCore. Core](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [MVC：先行編譯工具已被取代](#mvc-precompilation-tool-deprecated)
- [MVC：類型已變更為內部](#mvc-pubternal-types-changed-to-internal)
- [MVC： Web API 相容性填充碼已移除](#mvc-web-api-compatibility-shim-removed)
- [Razor：將執行時間編譯移至封裝](#razor-runtime-compilation-moved-to-a-package)
- [會話狀態：已移除已淘汰的 Api](#session-state-obsolete-apis-removed)
- [共用架構：從 AspNetCore 應用程式移除元件](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [共用架構： AspNetCore 全部移除](#shared-framework-removed-microsoftaspnetcoreall)
- [SignalR： HandshakeProtocol. SuccessHandshakeData 已取代](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [SignalR：已移除 HubConnection 方法](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [SignalR： HubConnectionCoNtext 的函式已變更](#signalr-hubconnectioncontext-constructors-changed)
- [SignalR： JavaScript 用戶端封裝名稱變更](#signalr-javascript-client-package-name-changed)
- [SignalR：過時的 Api](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [Spa：已標記為過時的 SpaServices 和 NodeServices](#spas-spaservices-and-nodeservices-marked-obsolete)
- [Spa： SpaServices 和 NodeServices 主控台記錄器 fallback 預設變更](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [目標 framework：不支援 .NET Framework](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-31"></a>ASP.NET Core 3.1

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a>ASP.NET Core 3.0

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
