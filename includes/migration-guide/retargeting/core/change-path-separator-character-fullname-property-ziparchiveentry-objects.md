---
ms.openlocfilehash: e4860113f45d3b3466e01e5db61d355a8ea745df
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68235576"
---
### <a name="change-in-path-separator-character-in-fullname-property-of-ziparchiveentry-objects"></a>ZipArchiveEntry 物件的 FullName 屬性中路徑分隔符號字元變更

|   |   |
|---|---|
|詳細資料|若為以 .NET Framework 4.6.1 和更新版本為目標的應用程式，在由 <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A> 方法之多載所建立之 <xref:System.IO.Compression.ZipArchiveEntry> 物件的 <xref:System.IO.Compression.ZipArchiveEntry.FullName> 屬性中，路徑分隔符號字元已從反斜線 (&quot;\&quot;) 變更為斜線 (&quot;/&quot;)。 這項變更使得 .NET 實作遵守 [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) (.ZIP 檔案格式規格) 的 4.4.17.1 小節，並允許在非 Windows 系統上解壓縮 ZIP 封存。<br />在非 Windows 作業系統 (例如 Macintosh) 上解壓縮以舊版 .NET Framework 為目標的應用程式所建立的 ZIP 檔案，會無法保留目錄結構。 例如，在 Macintosh 上，它會建立一組檔案，其檔案名稱會串連目錄路徑，以及任何反斜線 (&quot;&quot;) 字元和檔案名稱。 因此，解壓縮檔案的目錄結構會無法保留。|
|建議|對於 Windows 作業系統上由 .NET Framework <xref:System.IO?displayProperty=nameWithType> 命名空間中 API 解壓縮的 .ZIP 檔案而言，此變更的影響應該很小，因為這些 API 可以將斜線 (&quot;/&quot;) 或反斜線 (&quot;\&quot;) 當做路徑分隔符號字元順利地處理。<br />如果不需要此變更，您可以在應用程式組態檔的 [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段新增組態設定，選擇退出。 下列範例顯示 <code>&lt;runtime&gt;</code> 區段及 <code>Switch.System.IO.Compression.ZipFile.UseBackslash</code> 選擇退出參數：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Compression.ZipFile.UseBackslash=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>此外，以舊版 .NET Framework 為目標但在 .NET Framework 4.6.1 和更新版本下執行的應用程式，可以藉由將組態設定新增到應用程式組態檔的 [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段，以選擇加入這項行為。 下圖顯示 <code>&lt;runtime&gt;</code> 區段及 <code>Switch.System.IO.Compression.ZipFile.UseBackslash</code> 選擇加入參數。<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Compression.ZipFile.UseBackslash=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|範圍|Edge|
|版本|4.6.1|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean)?displayProperty=nameWithType></li><li><xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean,System.Text.Encoding)?displayProperty=nameWithType></li></ul>|
