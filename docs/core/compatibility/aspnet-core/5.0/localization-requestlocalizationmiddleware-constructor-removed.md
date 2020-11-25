---
title: 重大變更：當地語系化：在要求當地語系化中介軟體中移除已淘汰的函式
description: 瞭解 ASP.NET Core 5.0 的重大變更，其標題為當地語系化：在要求當地語系化中介軟體中移除已淘汰的函式
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 53dd0f25078dae140d34d6d21d66983f78b8bdb0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760763"
---
# <a name="localization-obsolete-constructor-removed-in-request-localization-middleware"></a>當地語系化：在要求當地語系化中介軟體中移除過時的函式

<xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware>缺少參數的函式 <xref:Microsoft.Extensions.Logging.ILoggerFactory> [在此認可中](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0)標示為已淘汰。 在 ASP.NET Core 5.0 中，已移除過時的函式。 如需討論，請參閱 [dotnet/aspnetcore # 23785](https://github.com/dotnet/aspnetcore/issues/23785)。

## <a name="version-introduced"></a>引進的版本

5.0 Preview 8

## <a name="old-behavior"></a>舊的行為

已淘汰的函式 `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` 存在。

## <a name="new-behavior"></a>新的行為

過時的函式 `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` 不存在。

## <a name="reason-for-change"></a>變更的原因

這種變更可確保要求當地語系化中介軟體一律具有記錄器的存取權。

## <a name="recommended-action"></a>建議的動作

當您手動建立的實例時 `RequestLocalizationMiddleware` ，會在函式 `ILoggerFactory` 中傳遞實例。 如果 `ILoggerFactory` 該內容中未提供有效的實例，請考慮將中介軟體函式傳遞給 <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> 實例。

## <a name="affected-apis"></a>受影響的 API

[RequestLocalizationMiddleware .ctor (RequestDelegate、Microsoft.extensions.options.ioptions \<RequestLocalizationOptions>) ](/dotnet/api/microsoft.aspnetcore.localization.requestlocalizationmiddleware.-ctor?view=aspnetcore-3.1#Microsoft_AspNetCore_Localization_RequestLocalizationMiddleware__ctor_Microsoft_AspNetCore_Http_RequestDelegate_Microsoft_Extensions_Options_IOptions_Microsoft_AspNetCore_Builder_RequestLocalizationOptions__)

<!--

### Category

ASP.NET Core

### Affected APIs

`M:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Builder.RequestLocalizationOptions})`

-->
