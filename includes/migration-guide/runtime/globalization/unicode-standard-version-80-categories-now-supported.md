---
ms.openlocfilehash: f389a9e9bcf4ac1777db66731a085d74889c4a98
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496926"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a>現在支援 Unicode 標準 8.0 版分類

#### <a name="details"></a>詳細資料

在 .NET Framework 4.6.2 中，Unicode 資料已從 Unicode 標準 6.3 版升級至 8.0 版。  在 .NET Framework 4.6.2 中要求 Unicode 字元分類時，某些結果可能不符合舊版 .NET Framework 中的結果。  這項變更主要會影響柴羅基文音節和新傣文母音符號和音調標記。

#### <a name="suggestion"></a>建議

請檢閱程式碼，並移除/變更仰賴硬式編碼的 Unicode 字元分類的邏輯。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Minor|
|版本|4.6.2|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType>
- <xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType>
- <xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Char.GetUnicodeCategory(System.Char)`
- `M:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)`
- `M:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)`

-->
