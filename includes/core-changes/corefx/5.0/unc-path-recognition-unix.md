---
ms.openlocfilehash: 0246f325a6274082b7fb0d5590cec7c80687ae85
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720178"
---
### <a name="uri-recognition-of-unc-paths-on-unix"></a>Unix 上 UNC 路徑的 Uri 識別

<xref:System.Uri>類別現在會辨識開頭為兩個正斜線的字串 (`//`) 為 Unix 作業系統上 (UNC) 路徑的通用命名慣例。 這種變更讓這類字串在所有平臺上都是一致的。

#### <a name="change-description"></a>變更描述

在舊版的 .NET 中， <xref:System.Uri> 類別會辨識開頭為兩個正斜線（例如，）的字串， `//contoso` 做為 Unix 作業系統的絕對檔案路徑。 不過，在 Windows 上，這類字串會被辨識為 UNC 路徑。

從 .NET 5.0 開始，此 <xref:System.Uri> 類別會辨識以兩個正斜線作為所有平臺（包括 Unix）上之 UNC 路徑開頭的字串。 此外，屬性會根據 UNC 語義而行為：

- <xref:System.Uri.IsUnc?displayProperty=nameWithType> 會傳回 `true`。
- 路徑中的反斜線會以正斜線取代。 例如，`//first\second` 會成為 `//first/second`。
- <xref:System.Uri.LocalPath?displayProperty=nameWithType> 不以百分比編碼的字元。 例如， `//first/\uFFF0` *不* 會轉換成 `//first/%EF%BF%B0` 。

#### <a name="version-introduced"></a>引進的版本

5.0

#### <a name="recommended-action"></a>建議的動作

開發人員不需要採取任何動作。

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Uri`

-->
