---
ms.openlocfilehash: b0e1d6d720a1c9b827fb4585606e64b545d395d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394375"
---
### <a name="kestrel-request-trailer-headers-moved-to-new-collection"></a>Kestrel：要求尾端標頭移至新集合

在舊版中，Kestrel 會在要求主體讀取至結尾時，將 HTTP/1.1 區塊尾端標頭新增至要求標頭集合。 此行為會造成標頭和結尾之間的不明確問題。 決定將尾端移至新的集合。

HTTP/2 要求結尾在 ASP.NET Core 2.2 中無法使用，但現在也可在 ASP.NET Core 3.0 的這個新集合中取得。

已新增新的要求延伸方法，以存取這些結尾。

讀取整個要求主體後，就可以使用 HTTP/1.1 尾端。

從用戶端收到 HTTP/2 結尾時，就可以使用它。 用戶端將不會傳送結尾，直到整個要求主體至少經過伺服器的緩衝處理。 您可能需要讀取要求主體以釋出緩衝區空間。 如果您已將要求主體讀取至結尾，一律可使用尾端。 尾端標記主體結尾。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

要求尾端標頭會新增至 `HttpRequest.Headers` 集合。

#### <a name="new-behavior"></a>新的行為

集合中 **不存在** 要求尾端標頭 `HttpRequest.Headers` 。 使用下列擴充方法 `HttpRequest` 來存取它們：

- `GetDeclaredTrailers()` -取得要求 "尾端" 標頭，列出主體之後要預期的尾端。
- `SupportsTrailers()` -表示要求是否支援接收尾端標頭。
- `CheckTrailersAvailable()` -判斷要求是否支援尾端，以及是否可供讀取。
- `GetTrailer(string trailerName)` -從回應取得要求的尾端標頭。

#### <a name="reason-for-change"></a>變更的原因

尾端是 gRPC 案例中的重要功能。 將結尾合併到要求標頭會對使用者造成混淆。

#### <a name="recommended-action"></a>建議的動作

使用尾端相關的擴充方法 `HttpRequest` 來存取尾端。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Http.HttpRequest.Headers?displayProperty=nameWithType>

<!--

#### Affected APIs

`P:Microsoft.AspNetCore.Http.HttpRequest.Headers`

-->
