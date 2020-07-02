---
ms.openlocfilehash: 7e42a294b151d07a6fdc61308cdf92df7a31a1d6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614352"
---
### <a name="deflatestream-uses-native-apis-for-decompression"></a>DeflateStream 使用原生 API 解壓縮

#### <a name="details"></a>詳細資料

從 .NET Framework 4.7.2 開始，`T:System.IO.Compression.DeflateStream` 類別中的解壓縮實作已變更為預設使用原生 Windows API。 一般而言，這會導致顯著的效能改善。 所有以 .NET Framework 4.7.2 或更高版本為目標的 .NET 應用程式都會使用原生實作。這項變更可能會導致行為的某些差異，包括：

- 例外狀況訊息可能會不同。 不過，擲回的例外狀況類型維持不變。
- 某些特殊情況下，例如記憶體不足無法完成作業，可能會以不同的方式處理。
- 剖析 gzip 標頭的已知差異 (注意：只有針對解壓縮設定的 `GZipStream` 會受到影響)：
- 剖析無效標頭時的例外狀況，可能會在不同的時間擲回。
- 原生實作強制執行的 gzip 標頭內某些保留旗標值 (亦即 [FLG](http://www.zlib.org/rfc-gzip.html#header-trailer))，會根據規格設定，這可能會造成它擲回略過先前無效值的例外狀況。

#### <a name="suggestion"></a>建議

如果使用原生 API 解壓縮對您的應用程式行為有不良影響，您可以在 app.config 檔案的 `runtime` 區段中新增 `Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression` 參數，並將它設定為 `true`，選擇不使用這項功能：

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=true" />
  </runtime>
</configuration>
```

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.7.2       |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.IO.Compression.DeflateStream?displayProperty=nameWithType>
- <xref:System.IO.Compression.GZipStream?displayProperty=nameWithType>
