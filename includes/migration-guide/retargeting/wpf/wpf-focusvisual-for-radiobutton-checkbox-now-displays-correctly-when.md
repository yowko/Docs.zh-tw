---
ms.openlocfilehash: 4eac93d5cfea19cb83c66cd3fe35c1b0703c0cc0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59233927"
---
### <a name="wpf-focusvisual-for-radiobutton-and-checkbox-now-displays-correctly-when-the-controls-have-no-content"></a>現在，當控制項沒有內容時，RadioButton 和 CheckBox 的 WPF 焦點視覺效果會正確顯示

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.7.1 和舊版的傳統和高對比佈景主題中，WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> 和 <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> 的焦點視覺效果不一致且不正確。  當控制項沒有任何內容集時，會發生上述問題。  這可能會讓人混淆佈景主題之間的轉換，也看不清楚焦點視覺效果。 現在，.NET Framework 4.7.2 的這些視覺效果在各佈景主題之間會更一致；在傳統和高對比佈景主題中也可以看得更清楚。|
|建議|如果開發人員是以 .NET Framework 4.7.2 為目標，並想要還原為 .NET 4.7.1 的行為，則必須設定下列 AppContext 旗標。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true;&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>如果開發人員想要利用這項變更，同時以 .NET 4.7.2 以下的 Framework 版本為目標，則必須設定下列 AppContext 旗標。請注意，所有旗標都必須正確設定，而且安裝的 .NET Framework 版本必須為 4.7.2 或更新版本。您必須具備 WPF 應用程式，才能選擇使用所有舊版的協助工具改進功能，並取得最新的改進功能。 若要這樣做，請確認 'Switch.UseLegacyAccessibilityFeatures' 和 'Switch.UseLegacyAccessibilityFeatures.2' 這兩個 AppContext 參數均設為 false。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|範圍|Edge|
|版本|4.7.2|
|類型|正在重定目標|
