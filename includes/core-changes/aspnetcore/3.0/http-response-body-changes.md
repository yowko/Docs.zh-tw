---
ms.openlocfilehash: cd66317bc93343e03a73dec74dff534776ca42e4
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032364"
---
### <a name="http-response-body-infrastructure-changes"></a>HTTP：回應主體基礎結構變更

支援 HTTP 回應主體的基礎結構已變更。 如果您是 `HttpResponse` 直接使用，就不需要進行任何程式碼變更。 如果您要換行或取代 `HttpResponse.Body` 或存取，請進一步閱讀 `HttpContext.Features` 。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

HTTP 回應主體有三個相關聯的 Api：

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a>新的行為

如果您取代 `HttpResponse.Body` 了，則會使用指定的資料流程周圍的包裝函式來取代整個， `IHttpResponseBodyFeature` `StreamResponseBodyFeature` 以提供所有預期 api 的預設執行。 設定回原始資料流程會還原此變更。

#### <a name="reason-for-change"></a>變更的原因

動機是將回應內文 Api 合併成單一的新功能介面。

#### <a name="recommended-action"></a>建議的動作

使用 `IHttpResponseBodyFeature` 您先前使用 `IHttpResponseFeature.Body` 、或的位置 `IHttpSendFileFeature` `IHttpBufferingFeature` 。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature`
- `P:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body`
- `T:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature`

-->
