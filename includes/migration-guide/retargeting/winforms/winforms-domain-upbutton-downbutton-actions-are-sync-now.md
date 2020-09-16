---
ms.openlocfilehash: c64431fd651fd7d53fb46231c6acc10c5cb43fff
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606833"
---
### <a name="winforms-domain-upbutton-and-downbutton-actions-are-in-sync-now"></a>WinForm 的網域 upbutton 和 downbutton 動作現在會同步

#### <a name="details"></a>詳細資料

在 .NET Framework 4.7.1 和先前版本中，<xref:System.Windows.Forms.DomainUpDown> 控制項的 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 動作會在控制項文字存在時予以忽略，因此開發人員必須在控制項上使用 <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> 動作，才能使用 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 動作。 從 .NET Framework 4.7.2 開始，<xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 和 <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> 這兩個動作在此案例中會獨立工作，並保持同步。

#### <a name="suggestion"></a>建議

為了讓應用程式可受益於這些變更，它必須在 .NET Framework 4.7.2 或更新版本上執行。 應用程式可以用下列任一種方式受益於這些變更：

- 將其重新編譯為以 .NET Framework 4.7.2 為目標。 在以 .NET Framework 4.7.2 或更新版本為目標的 Windows Forms 應用程式上，預設會啟用這項變更。
- 藉由在應用程式組態檔的 `<runtime>` 區段中新增下列 [AppContext 參數](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)，並將它設定為 `false`，選擇退出舊版捲動行為，如下列範例所示。

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| 名稱    | 值       |
|:--------|:------------|
| 範圍   | Edge        |
| 版本 | 4.7.2       |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
