---
ms.openlocfilehash: b0e1d6d720a1c9b827fb4585606e64b545d395d7
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394375"
---
### <a name="kestrel-request-trailer-headers-moved-to-new-collection"></a>Kestrel：要求尾標頭已移至新的集合

在舊版中，Kestrel 會在要求主體讀取到結尾時，將 HTTP/1.1 區塊尾端標頭新增至要求標頭集合。 這種行為會造成標頭和結尾之間不明確的問題。 決定將結尾移至新的集合。

HTTP/2 要求結尾在 ASP.NET Core 2.2 中無法使用，但現在也可在 ASP.NET Core 3.0 的這個新集合中取得。

已加入新的要求擴充方法來存取這些結尾。

一旦讀取整個要求主體之後，就可以使用 HTTP/1.1 尾端。

從用戶端收到 HTTP/2 尾端後，就可以使用它。 用戶端將不會傳送結尾，直到伺服器至少已緩衝處理整個要求主體為止。 您可能需要讀取要求本文以釋放緩衝區空間。 如果您將要求主體讀取到結尾，一律可以使用尾端。 尾端會標示本文的結尾。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

要求尾端標頭會新增至 `HttpRequest.Headers` 集合。

#### <a name="new-behavior"></a>新的行為

@No__t-1 集合中**不存在**要求結尾標頭。 請使用下列 `HttpRequest` 的擴充方法來存取它們：

- `GetDeclaredTrailers()`-取得要求 "尾端" 標頭，以列出主體之後要預期的尾端。
- `SupportsTrailers()`-指出要求是否支援接收尾端標頭。
- `CheckTrailersAvailable()`-判斷要求是否支援尾端，以及是否可供讀取。
- `GetTrailer(string trailerName)`-從回應中取得要求的尾端標頭。

#### <a name="reason-for-change"></a>變更的原因

尾端是 gRPC 之類案例中的重要功能。 將中的尾端合併到要求標頭會對使用者造成混淆。

#### <a name="recommended-action"></a>建議的動作

使用 `HttpRequest` 上結尾相關的擴充方法來存取尾端。

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Http.HttpRequest.Headers?displayProperty=nameWithType>

<!--

#### Affected APIs

`P:Microsoft.AspNetCore.Http.HttpRequest.Headers`

-->
