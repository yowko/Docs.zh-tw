---
ms.openlocfilehash: a20fad5f9c95e59c14ffd91f4921cf8bfab443cd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621072"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a>現在支援 Unicode 標準 8.0 版分類

#### <a name="details"></a>詳細資料

在 .NET Framework 4.6.2 中，Unicode 資料已從 Unicode 標準 6.3 版升級至 8.0 版。  在 .NET Framework 4.6.2 中要求 Unicode 字元分類時，某些結果可能不符合舊版 .NET Framework 中的結果。  這項變更主要會影響柴羅基文音節和新傣文母音符號和音調標記。

#### <a name="suggestion"></a>建議

請檢閱程式碼，並移除/變更仰賴硬式編碼的 Unicode 字元分類的邏輯。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Minor|
|版本|4.6.2|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|
