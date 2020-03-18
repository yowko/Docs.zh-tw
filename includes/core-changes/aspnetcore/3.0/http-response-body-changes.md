---
ms.openlocfilehash: cd66317bc93343e03a73dec74dff534776ca42e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198379"
---
### <a name="http-response-body-infrastructure-changes"></a>HTTP：回應正文基礎結構更改

支援 HTTP 回應正文的基礎結構已更改。 如果您直接使用`HttpResponse`，則不需要進行任何代碼更改。 如果要包裝、替換`HttpResponse.Body`或訪問`HttpContext.Features`，請進一步閱讀。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

有三個 API 與 HTTP 回應正文相關聯：

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a>新的行為

如果替換`HttpResponse.Body`，它將用給定流周圍的`IHttpResponseBodyFeature`包裝器替換整個物件，用於`StreamResponseBodyFeature`為所有預期的 API 提供預設實現。 設置回原始流將恢復此更改。

#### <a name="reason-for-change"></a>更改原因

動機是將回應體 API 合併到單個新功能介面中。

#### <a name="recommended-action"></a>建議的動作

使用`IHttpResponseBodyFeature`以前使用`IHttpResponseFeature.Body`或`IHttpSendFileFeature``IHttpBufferingFeature`的位置。

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
