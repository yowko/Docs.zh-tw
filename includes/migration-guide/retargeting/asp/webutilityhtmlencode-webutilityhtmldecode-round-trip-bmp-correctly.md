---
ms.openlocfilehash: ca662b57fae9b1d0d41290f3052f71bca66e9bf3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774377"
---
### <a name="webutilityhtmlencode-and-webutilityhtmldecode-round-trip-bmp-correctly"></a>WebUtility.HtmlEncode 和 WebUtility.HtmlDecode 正確地反覆存取 BMP

|   |   |
|---|---|
|詳細資料|若是目標為 .NET Framework 4.5 的應用程式，當 Basic Multilingual Plane (BMP) 以外的字元傳遞至 <xref:System.Net.WebUtility.HtmlDecode(System.String)> 方法時，會正確地來回轉譯。|
|建議|這項變更應該不會影響目前的應用程式，但若要還原原始行為，請將 <code>&lt;httpRuntime&gt;</code> 項目的 <code>targetFramework</code> 屬性設為非 &quot;4.5&quot; 的字串。 您也可以設定 <code>unicodeEncodingConformance</code> 組態項目的 <code>unicodeDecodingConformance</code> 和 <code>&lt;webUtility&gt;</code> 屬性，以與目標 .NET Framework 版本不相關的方式控制這個行為。|
|範圍|Edge|
|版本|4.5|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Net.WebUtility.HtmlEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlEncode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li></ul>|
