---
ms.openlocfilehash: acb5b467fc8f0692d8fa1b3b8263fd27308cc124
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617134"
---
### <a name="webutilityhtmlencode-and-webutilityhtmldecode-round-trip-bmp-correctly"></a>WebUtility.HtmlEncode 和 WebUtility.HtmlDecode 正確地反覆存取 BMP

#### <a name="details"></a>詳細資料

若是目標為 .NET Framework 4.5 的應用程式，當 Basic Multilingual Plane (BMP) 以外的字元傳遞至 <xref:System.Net.WebUtility.HtmlDecode(System.String)> 方法時，會正確地來回轉譯。

#### <a name="suggestion"></a>建議

這項變更應該不會影響目前的應用程式，但若要還原原始行為，請將 `targetFramework` 元素的屬性設定 `<httpRuntime>` 為 "4.5" 以外的字串。 您也可以設定 `unicodeEncodingConformance` 組態項目的 `unicodeDecodingConformance` 和 `<webUtility>` 屬性，以與目標 .NET Framework 版本不相關的方式控制這個行為。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.5         |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Net.WebUtility.HtmlEncode(System.String)?displayProperty=nameWithType>
- <xref:System.Net.WebUtility.HtmlEncode(System.String,System.IO.TextWriter)?displayProperty=nameWithType>
