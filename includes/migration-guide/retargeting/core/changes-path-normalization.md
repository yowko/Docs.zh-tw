---
ms.openlocfilehash: 994876457f9745de99be30e567f400f69a0192fa
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70259780"
---
### <a name="changes-in-path-normalization"></a>路徑正規化的變更

|   |   |
|---|---|
|詳細資料|從以 .NET Framework 4.6.2 為目標的應用程式開始，執行階段正規化路徑的方式已變更。正規化路徑涉及修改識別路徑或檔案的字串，使它符合目標作業系統上的有效路徑。 正規化通常牽涉到︰<ul><li>規範化元件和目錄分隔符號。</li><li>將目前的目錄套用到相對路徑。</li><li>評估路徑中的相對目錄 (.) 或上層目錄 (..)。</li><li>修剪指定的字元。</li></ul>從以 .NET Framework 4.6.2 為目標的應用程式開始，預設會啟用路徑正規化的下列變更：<ul><li>執行階段會延後至作業系統的 [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) 函式再進行路徑正規化。</li><li>正規化不再涉及修剪目錄區段的結尾 (例如目錄名稱結尾的空格)。</li><li>支援完全信任的裝置路徑語法，包括 `\\.\` 以及適用於 mscorlib.dll 中之檔案 I/O API 的 `\\?\`。</li><li>執行階段不會驗證裝置語法路徑。</li><li>支援使用裝置語法存取替代資料流。</li></ul>這些變更可改善效能，同時允許方法存取先前無法存取的路徑。 此變更不會影響以 .NET Framework 4.6.1 和舊版為目標但執行於 .NET Framework 4.6.2 或更新版本下的應用程式。|
|建議|以 .NET Framework 4.6.2 或更新版本為目標的應用程式可透過在應用程式設定檔的 <code>&lt;runtime&gt;</code> 區段中新增下列內容來選擇退出此變更，並使用舊版行為：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>以 .NET Framework 4.6.1 或更早版本為目標，但在 .NET Framework 4.6.2 或更新版本上執行的應用程式，可以藉由在應用程式設定檔的 <code>&lt;runtime&gt;</code> 區段新增下行，就能啟用路徑正規化的變更：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|範圍|次要|
|版本|4.6.2|
|類型|正在重定目標|
