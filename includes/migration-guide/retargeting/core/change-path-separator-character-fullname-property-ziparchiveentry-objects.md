---
ms.openlocfilehash: f87d0dbeda6094bd745f5b580772b1161f30d0d5
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86218278"
---
### <a name="change-in-path-separator-character-in-fullname-property-of-ziparchiveentry-objects"></a>ZipArchiveEntry 物件的 FullName 屬性中路徑分隔符號字元變更

#### <a name="details"></a>詳細資料

針對以 .NET Framework 4.6.1 和更新版本為目標的應用程式，在方法的多載所建立之物件的屬性中，路徑分隔符號已從反斜線 ( " \\ " ) 變更為正斜線 ( "/" ) <xref:System.IO.Compression.ZipArchiveEntry.FullName> <xref:System.IO.Compression.ZipArchiveEntry> <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A> 。 這項變更使得 .NET 實作遵守 [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) (.ZIP 檔案格式規格) 的 4.4.17.1 小節，並允許在非 Windows 系統上解壓縮 ZIP 封存。<br />在非 Windows 作業系統 (例如 Macintosh) 上解壓縮以舊版 .NET Framework 為目標的應用程式所建立的 ZIP 檔案，會無法保留目錄結構。 例如，在 Macintosh 上，它會建立一組檔案，其檔案名稱會串連目錄路徑，以及任何反斜線 (\\) 字元和檔案名稱。 因此，解壓縮檔案的目錄結構會無法保留。

#### <a name="suggestion"></a>建議

這項變更對的影響。在 Windows 作業系統上，由 .NET Framework 命名空間中的 Api 解壓縮的 ZIP 檔案 <xref:System.IO?displayProperty=nameWithType> 應該是最小的，因為這些 api 可以順暢地處理正斜線 ( "/" ) 或反斜線 ( " \\ " ) 做為路徑分隔字元。<br />如果不需要這項變更，您可以新增設定至 [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 應用程式佈建檔的區段，以退出宣告。 下列範例顯示 `<runtime>` 區段及 `Switch.System.IO.Compression.ZipFile.UseBackslash` 選擇退出參數：

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />
</runtime>
```

此外，以舊版 .NET Framework 為目標但在 .NET Framework 4.6.1 和更新版本上執行的應用程式，可以藉由新增設定至 [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 應用程式佈建檔的區段，來加入宣告此行為。 下圖顯示 `<runtime>` 區段及 `Switch.System.IO.Compression.ZipFile.UseBackslash` 選擇加入參數。

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />
</runtime>
```

| 名稱    | 值       |
|:--------|:------------|
| 範圍   | Edge        |
| 版本 | 4.6.1       |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean)?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean,System.Text.Encoding)?displayProperty=nameWithType>
