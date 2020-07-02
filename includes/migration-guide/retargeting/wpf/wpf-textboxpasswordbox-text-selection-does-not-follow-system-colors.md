---
ms.openlocfilehash: 7c2e80669d9ef27f87cde9442d8eeab0ee31a524
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614623"
---
### <a name="wpf-textboxpasswordbox-text-selection-does-not-follow-system-colors"></a>WPF 文字方塊/PasswordBox 文字選取範圍不遵循系統色彩

#### <a name="details"></a>詳細資料

在 .NET Framework 4.7.1 和舊版中，WPF `System.Windows.Controls.TextBox` 和 `System.Windows.Controls.PasswordBox` 只能在 Adorner 圖層轉譯文字選取項目。 在某些系統佈景主題中，這會遮擋文字，讓它變得更難讀取。  在 .NET Framework 4.7.2 和更新版本中，開發人員可以選擇非 Adorner 型的選取項目轉譯配置來減輕這個問題。

#### <a name="suggestion"></a>建議

想要利用這項變更的開發人員必須適當設定下列 AppContext 旗標。  若要利用這項功能，已安裝的 .NET Framework 版本必須是 4.7.2 或更高。若要啟用非 Adorner 型的選取項目，請使用下列 AppContext 旗標。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Text.UseAdornerForTextboxSelectionRendering=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.7.2       |
| 類型    | 正在重定目標 |
