---
ms.openlocfilehash: 7344fddbc61d47d4ca735808f0b92f63e33e15a3
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760782"
---
### <a name="winforms-domain-upbutton-and-downbutton-actions-are-in-sync-now"></a>WinForm 的網域 upbutton 和 downbutton 動作現在會同步

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.7.1 和先前版本中，<xref:System.Windows.Forms.DomainUpDown> 控制項的 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 動作會在控制項文字存在時予以忽略，因此開發人員必須在控制項上使用 <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> 動作，才能使用 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 動作。 從 .NET Framework 4.7.2 開始，<xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 和 <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> 這兩個動作在此案例中會獨立工作，並保持同步。|
|建議|為了讓應用程式可受益於這些變更，它必須在 .NET Framework 4.7.2 或更新版本上執行。 應用程式可以用下列任一種方式受益於這些變更：<ul><li>將其重新編譯為以 .NET Framework 4.7.2 為目標。 在以 .NET Framework 4.7.2 或更新版本為目標的 Windows Forms 應用程式上，預設會啟用這項變更。</li><li>藉由在應用程式組態檔的 <code>&lt;runtime&gt;</code> 區段中新增下列 [AppContext 參數](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)，並將它設定為 <code>false</code>，選擇退出舊版捲動行為，如下列範例所示。</li></ul><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|範圍|Edge|
|版本|4.7.2|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType></li><li><xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType></li></ul>|

