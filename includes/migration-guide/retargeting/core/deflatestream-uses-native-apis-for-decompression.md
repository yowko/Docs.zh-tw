---
ms.openlocfilehash: ed0dde302e30ae0cf3c7a8d0985f2314d91cab66
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760792"
---
### <a name="deflatestream-uses-native-apis-for-decompression"></a>DeflateStream 使用原生 API 解壓縮

|   |   |
|---|---|
|詳細資料|從 .NET Framework 4.7.2 開始，<code>T:System.IO.Compression.DeflateStream</code> 類別中的解壓縮實作已變更為預設使用原生 Windows API。 一般而言，這會導致顯著的效能改善。 所有以 .NET Framework 4.7.2 或更高版本為目標的 .NET 應用程式都會使用原生實作。這項變更可能會導致行為的某些差異，包括：<ul><li>例外狀況訊息可能會不同。 不過，擲回的例外狀況類型維持不變。</li><li>某些特殊情況下，例如記憶體不足無法完成作業，可能會以不同的方式處理。</li><li>剖析 gzip 標頭的已知差異 (注意：只有針對解壓縮設定的 <code>GZipStream</code> 會受到影響)：</li><li>剖析無效標頭時的例外狀況，可能會在不同的時間擲回。</li><li>原生實作強制執行的 gzip 標頭內某些保留旗標值 (亦即 [FLG](http://www.zlib.org/rfc-gzip.html#header-trailer))，會根據規格設定，這可能會造成它擲回略過先前無效值的例外狀況。</li></ul>|
|建議|如果使用原生 API 解壓縮對您的應用程式行為有不良影響，您可以在 app.config 檔案的 <code>runtime</code> 區段中新增 <code>Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression</code> 參數，並將它設定為 <code>true</code>，選擇不使用這項功能：<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot; ?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|範圍|次要|
|版本|4.7.2|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.IO.Compression.DeflateStream?displayProperty=nameWithType></li><li><xref:System.IO.Compression.GZipStream?displayProperty=nameWithType></li></ul>|

