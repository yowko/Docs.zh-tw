---
ms.openlocfilehash: 9c2a8eca3f4498906cf703ff3b8ffb7336ff7a1b
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804462"
---
### <a name="icontobitmap-successfully-converts-icons-with-png-frames-into-bitmap-objects"></a>Icon.ToBitmap 成功將具有 PNG 畫面格的圖示轉換成點陣圖物件

|   |   |
|---|---|
|詳細資料|從以 .NET Framework 4.6 為目標的應用程式開始，<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> 方法可將具有 PNG 框架的圖示成功轉換成點陣圖物件。<p/>在以 .NET Framework 4.5.2 (含) 之前版本為目標的應用程式中，如果圖示物件具有 PNG 框架，則 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> 方法會擲回 <xref:System.ArgumentOutOfRangeException> 例外狀況。<p/>這項變更會影響重新撰寫之以 .NET Framework 4.6 為目標的應用程式，以及針對圖示物件具有 PNG 框架時所擲回的 <xref:System.ArgumentOutOfRangeException> 實作特殊處理的應用程式。 以 .NET Framework 4.6 執行時，轉換會成功，且不再擲回 <xref:System.ArgumentOutOfRangeException> ，因此不會再叫用例外狀況處理常式。|
|建議|如果不需要這項行為，您可以在 app.config 檔案的 <code>&lt;runtime&gt;</code> 區段中新增下列項目，以保留舊版行為：<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true&quot; /&gt;&#13;&#10;</code></pre>如果 app.config 檔案已經包含 <code>AppContextSwitchOverrides</code> 項目，則應以下列程式碼將新值與值屬性合併：<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true;&lt;previous key&gt;=&lt;previous value&gt;&quot; /&gt;&#13;&#10;</code></pre>|
|範圍|次要|
|版本|4.6|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Drawing.Icon.ToBitmap?displayProperty=nameWithType></li></ul>|

