---
ms.openlocfilehash: 22ef5d0f91a4f61ca75203f677bcc14e91d77dc1
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394033"
---
### <a name="http-response-body-infrastructure-changes"></a>HTTP：回應主體基礎結構變更

支援 HTTP 回應主體的基礎結構已變更。 如果您直接使用 `HttpResponse`，則不需要進行任何程式碼變更。 如果您要包裝或取代 `HttpResponse.Body` 或存取 `HttpContext.Features`，請進一步閱讀。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

有三個與 HTTP 回應主體相關聯的 Api：

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a>新的行為

如果您取代 `HttpResponse.Body`，則會使用 `StreamResponseBodyFeature`，以指定串流的包裝函式取代整個 `IHttpResponseBodyFeature`，以提供所有預期 Api 的預設執行。 將原始資料流程設回會還原此變更。

#### <a name="reason-for-change"></a>變更的原因

動機是將回應主體 Api 結合成單一的新功能介面。

#### <a name="recommended-action"></a>建議的動作

使用 `IHttpResponseBodyFeature`，您先前使用的是 `IHttpResponseFeature.Body`、`IHttpSendFileFeature` 或 `IHttpBufferingFeature`。

#### <a name="category"></a>分類

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
