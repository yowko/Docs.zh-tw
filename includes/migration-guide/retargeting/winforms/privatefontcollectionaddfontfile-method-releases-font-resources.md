---
ms.openlocfilehash: 53ded5ae6e5a025fc7992da099c3481587bb6f31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614578"
---
### <a name="privatefontcollectionaddfontfile-method-releases-font-resources"></a>PrivateFontCollection.AddFontFile 方法會釋放字型資源

#### <a name="details"></a>詳細資料

在 .NET Framework 4.7.1 和舊版本中，如果 <xref:System.Drawing.Font> 物件是使用 <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)> 方法新增至這個集合，則 <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> 類別不會在處置物件的 <xref:System.Drawing.Text.PrivateFontCollection> 之後釋放 GDI+ 字型資源。 在 .NET Framework 4.7.2 和更新版本中，<xref:System.Drawing.Text.FontCollection.Dispose%2A> 會釋放已藉由檔案形式新增至集合中的 GDI+ 字型。

#### <a name="suggestion"></a>建議

**如何加入宣告或退出這些變更**為了讓應用程式受益于這些變更，它必須在 .NET Framework 4.7.2 或更新版本上執行。 應用程式可以用下列任一種方式受益於這些變更：

- 將其重新編譯為以 .NET Framework 4.7.2 為目標。 在以 .NET Framework 4.7.2 或更新版本為目標的 Windows Forms 應用程式上，預設會啟用這項變更。
- 以 .NET Framework 4.7.1 或舊版為目標，並選擇不使用舊版協助工具行為；方法為在 app.config 檔的 `<runtime>` 區段中新增下列 [AppContext 參數](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element)，並將其設定為 `false`，如下範例所示。

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Drawing.Text.DoNotRemoveGdiFontsResourcesFromFontCollection=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

如果應用程式是以 .NET Framework 4.7.2 或更新版本為目標，而您想要保留舊版本的行為，則可以明確將此 AppContext 參數設為 `true`，選擇不要釋放字型資源。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.7.2       |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType>
- <xref:System.Drawing.Text.FontCollection.Dispose?displayProperty=nameWithType>
