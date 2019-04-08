---
ms.openlocfilehash: c923d9b341bbf0a21d73ac75cc6cb1a037f37826
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760781"
---
### <a name="privatefontcollectionaddfontfile-method-releases-font-resources"></a>PrivateFontCollection.AddFontFile 方法會釋放字型資源

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.7.1 和舊版本中，如果 <xref:System.Drawing.Font> 物件是使用 <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)> 方法新增至這個集合，則 <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> 類別不會在處置物件的 <xref:System.Drawing.Text.PrivateFontCollection> 之後釋放 GDI+ 字型資源。 在 .NET Framework 4.7.2 和更新版本中，<xref:System.Drawing.Text.FontCollection.Dispose%2A> 會釋放已藉由檔案形式新增至集合中的 GDI+ 字型。|
|建議|<strong>如何選擇使用或不使用這些變更</strong>為了讓應用程式能受益於這些變更，您必須在 .NET Framework 4.7.2 或更新版本上執行應用程式。 應用程式可以用下列任一種方式受益於這些變更：<ul><li>將其重新編譯為以 .NET Framework 4.7.2 為目標。 在以 .NET Framework 4.7.2 或更新版本為目標的 Windows Forms 應用程式上，預設會啟用這項變更。</li><li>以 .NET Framework 4.7.1 或舊版為目標，並選擇不使用舊版協助工具行為；方法為在 app.config 檔的 <code>&lt;runtime&gt;</code> 區段中新增下列 [AppContext 參數](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)，並將其設定為 <code>false</code>，如下範例所示。</li></ul><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Drawing.Text.DoNotRemoveGdiFontsResourcesFromFontCollection=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>如果應用程式是以 .NET Framework 4.7.2 或更新版本為目標，而您想要保留舊版本的行為，則可以明確將此 AppContext 參數設為 <code>true</code>，選擇不要釋放字型資源。|
|範圍|Edge|
|版本|4.7.2|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType></li><li><xref:System.Drawing.Text.FontCollection.Dispose?displayProperty=nameWithType></li></ul>|

