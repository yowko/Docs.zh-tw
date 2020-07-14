---
ms.openlocfilehash: b1d4b69b7a8ed68cd688dfd0249d5107b80e67c4
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281331"
---
### <a name="localization-obsolete-constructor-removed-in-request-localization-middleware"></a>當地語系化：已在要求當地語系化中介軟體中移除過時的函式

<xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware> <xref:Microsoft.Extensions.Logging.ILoggerFactory> [在此認可中](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0)，缺少參數的函式已標示為過時。 在 ASP.NET Core 5.0 中，已移除過時的函式。 如需討論，請參閱[dotnet/aspnetcore # 23785](https://github.com/dotnet/aspnetcore/issues/23785)。

#### <a name="version-introduced"></a>引進的版本

5.0

#### <a name="old-behavior"></a>舊的行為

已過時的函式 `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` 存在。

#### <a name="new-behavior"></a>新的行為

過時的函式 `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` 不存在。

#### <a name="reason-for-change"></a>變更的原因

這種變更可確保要求當地語系化中介軟體一律具有記錄器的存取權。

#### <a name="recommended-action"></a>建議的動作

當您手動建立的實例時 `RequestLocalizationMiddleware` ，請 `ILoggerFactory` 在此函式中傳遞實例。 如果 `ILoggerFactory` 在該內容中無法使用有效的實例，請考慮將中介軟體的函式傳遞給 <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> 實例。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

[RequestLocalizationMiddleware (RequestDelegate，Microsoft.extensions.options.ioptions \<RequestLocalizationOptions>) ](/dotnet/api/microsoft.aspnetcore.localization.requestlocalizationmiddleware.-ctor?view=aspnetcore-3.1#Microsoft_AspNetCore_Localization_RequestLocalizationMiddleware__ctor_Microsoft_AspNetCore_Http_RequestDelegate_Microsoft_Extensions_Options_IOptions_Microsoft_AspNetCore_Builder_RequestLocalizationOptions__)

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Builder.RequestLocalizationOptions})`

-->
