---
ms.openlocfilehash: 948c83f49b703194ccfe932e53751e0bb2dde37c
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760780"
---
### <a name="contextmenustripsourcecontrol-property-contains-a-valid-control-in-the-case-of-nested-toolstripmenuitems"></a>在巢狀 ToolStripMenuItems 的情況下，ContextMenuStrip.SourceControl 屬性包含有效的控制項

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.7.1 和舊版本中，當使用者從巢狀 <xref:System.Windows.Forms.ToolStripMenuItem> 控制項開啟功能表時，<xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> 屬性會誤傳回 null。 在 .NET Framework 4.7.2 和更新版本中，一律會將 <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> 屬性設定為實際的來源控制項。|
|建議|<strong>如何選擇使用或不使用這些變更</strong>為了讓應用程式能受益於這些變更，您必須在 .NET Framework 4.7.2 或更新版本上執行應用程式。 應用程式可以用下列任一種方式受益於這些變更：<ul><li>以 .NET Framework 4.7.2 為目標。 在以 .NET Framework 4.7.2 或更新版本為目標的 Windows Forms 應用程式上，預設會啟用這項變更。</li><li>以 .NET Framework 4.7.1 或舊版為目標，並選擇不使用舊版協助工具行為；方法為在 app.config 檔的 <code>&lt;runtime&gt;</code> 區段中新增下列 [AppContext 參數](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)，並將其設定為 <code>false</code>，如下範例所示。</li></ul><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>如果應用程式是以 .NET Framework 4.7.2 或更新版本為目標，而您想要保留舊版的行為，則可以明確將此 AppContext 參數設為 <code>true</code>，選擇使用舊版的來源控制項。|
|範圍|Edge|
|版本|4.7.2|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType></li></ul>|

