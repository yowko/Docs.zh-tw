---
ms.openlocfilehash: eb5c032a020799fa19cc0a8cfaabb56e01417ff4
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496829"
---
### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a>ContentDisposition DateTimes 會傳回稍微不同的字串

#### <a name="details"></a>詳細資料

<xref:System.Net.Mime.ContentDisposition?displayProperty=fullName> 的字串表示已更新，從 4.6 開始，一律會以兩個位數表示 <xref:System.DateTime?displayProperty=fullName> 的小時元件。 這是為了遵守 [RFC822](https://www.ietf.org/rfc/rfc0822.txt) 和 [RFC2822](https://www.ietf.org/rfc/rfc2822.txt)。 這會導致 <xref:System.Net.Mime.ContentDisposition.ToString> 在 4.6 中傳回稍微不同的字串，例如，當其中一個配置的時間項目早於上午 10:00 時。 請注意，ContentDispositions 有時會透過轉換成字串來進行序列化，因此應檢閱任何 <xref:System.Net.Mime.ContentDisposition.ToString> 作業、序列化或 GetHashCode 呼叫。

#### <a name="suggestion"></a>建議

在不同的 .NET Framework 版本中，ContentDispositions 的字串表示不會正確地相互比較。 如果可能的話，請將字串轉換回 ContentDispositions，再進行比較。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Minor|
|版本|4.6|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType>
- <xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Net.Mime.ContentDisposition.ToString`
- `M:System.Net.Mime.ContentDisposition.GetHashCode`

-->
