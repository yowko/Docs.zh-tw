---
ms.openlocfilehash: b0e1d6d720a1c9b827fb4585606e64b545d395d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394375"
---
### <a name="kestrel-request-trailer-headers-moved-to-new-collection"></a>Kestrel：請求將拖車頭移動到新集合

在以前的版本中，Kestrel 在讀取請求正文到末尾時，將 HTTP/1.1 塊塊的掛頁標頭添加到請求標頭集合中。 此行為引起了對標頭和尾部之間歧義的擔憂。 決定把拖車移到一個新的收藏。

HTTP/2 請求預告片在 ASP.NET 酷 2.2 中不可用，但現在在 ASP.NET Core 3.0 中，此新集合中也提供了該請求預告片。

添加了新的請求擴充方法來訪問這些拖車。

HTTP/1.1 預告片在讀取整個請求正文後可用。

HTTP/2 預告片一旦從用戶端收到，即可用。 在整個請求正文至少由伺服器緩衝之前，用戶端不會發送預告片。 您可能需要讀取請求正文以釋放緩衝區空間。 如果您將請求正文讀到末尾，則始終可用拖車。 拖車標誌著身體的盡頭。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

請求將拖車標頭添加到集合中`HttpRequest.Headers`。

#### <a name="new-behavior"></a>新的行為

請求拖車標頭**不在**集合中`HttpRequest.Headers`。 使用以下擴充方法`HttpRequest`訪問它們：

- `GetDeclaredTrailers()`- 獲取請求"Trailer"標頭，列出在正文之後要期待的預告片。
- `SupportsTrailers()`- 指示請求是否支援接收拖車頭。
- `CheckTrailersAvailable()`- 確定請求是否支援預告片，以及它們是否可用於閱讀。
- `GetTrailer(string trailerName)`- 從回應獲取請求的尾隨標頭。

#### <a name="reason-for-change"></a>更改原因

在 gRPC 等方案中，拖車是一個關鍵功能。 將預告片合併到請求標頭中會令使用者感到困惑。

#### <a name="recommended-action"></a>建議的動作

使用與拖車相關的擴充方法`HttpRequest`訪問拖車。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Http.HttpRequest.Headers?displayProperty=nameWithType>

<!--

#### Affected APIs

`P:Microsoft.AspNetCore.Http.HttpRequest.Headers`

-->
