---
ms.openlocfilehash: 47d3829748deef2c7c3610816b8941bf88da7ec6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614591"
---
### <a name="accessibility-improvements-in-wpf"></a>WPF 的協助工具改善

#### <a name="details"></a>詳細資料

**高對比改善**
<ul><li>現在會顯示 <xref:System.Windows.Controls.Expander> 控制項的焦點。 在舊版 .NET Framework 中並非如此。
-和中的文字會在 <xref:System.Windows.Controls.CheckBox> <xref:System.Windows.Controls.RadioButton> 選取時進行控制，現在比先前的 .NET Framework 版本更容易看到。
-已停用的框線 <xref:System.Windows.Controls.ComboBox> 現在與已停用文字的色彩相同。 在舊版 .NET Framework 中並非如此。
-[已停用] 和 [焦點] 按鈕現在會使用正確的主題色彩。 在舊版 .NET Framework 中並非如此。
-當 <xref:System.Windows.Controls.ComboBox> 控制項的樣式設定為時，現在會顯示下拉式按鈕 <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey?displayProperty=nameWithType> ，在舊版的 .NET Framework 中則不會。
-控制項中的排序指標箭號 <xref:System.Windows.Controls.DataGrid> 現在會使用主題色彩。 在舊版 .NET Framework 中並非如此。
-預設的超連結樣式現在會在滑鼠停留時變更為正確的主題色彩。 在舊版 .NET Framework 中並非如此。
-現在可以看到鍵盤焦點在選項按鈕上。 在舊版 .NET Framework 中並非如此。
-<xref:System.Windows.Controls.DataGrid>控制項的 checkbox 資料行現在會使用鍵盤焦點回饋的預期色彩。 在舊版 .NET Framework 中並非如此。
-鍵盤焦點視覺效果現在會顯示在 <xref:System.Windows.Controls.ComboBox> 和 <xref:System.Windows.Controls.ListBox> 控制項上。 在舊版 .NET Framework 中並非如此。</p>
**螢幕閱讀程式互動改善**
<ul><li>螢幕助讀程式現在會將 <xref:System.Windows.Controls.Expander> 控制項正確宣告為群組 (展開/摺疊)。
螢幕助讀程式現在會將 - <xref:System.Windows.Controls.DataGridCell> 控制項正確宣告為資料儲存格 (展開/摺疊)。
-螢幕閱讀程式現在會宣告可編輯的名稱 <xref:System.Windows.Controls.ComboBox> 。
螢幕助讀程式不會再將 - <xref:System.Windows.Controls.PasswordBox> 控制項宣告為「檢視中無任何項目」。</p>
**LiveRegion 支援**[朗讀程式] 之類的螢幕讀取器可協助人們知道應用程式的 UI 內容，通常是透過描述目前焦點所在 UI 的相關專案，因為這可能是使用者最感關注的元素。 不過，如果螢幕某處的 UI 項目變更，而且沒有焦點，則使用者可能不會收到通知，並且可能會遺失重要資訊。 LiveRegions 旨在用來解決這個問題。 開發人員可以使用它們來通知螢幕助讀程式或任何其他 [UI 自動化](~/docs/framework/ui-automation/ui-automation-overview.md)用戶端，已對 UI 項目進行重要變更。 螢幕助讀程式接著可以決定如何和何時通知使用者已進行這項變更。 LiveSetting 屬性還可讓螢幕助讀程式知道通知使用者 UI 所做變更的重要性。

#### <a name="suggestion"></a>建議

**如何加入宣告或退出這些變更**為了讓應用程式受益于這些變更，它必須在 .NET Framework 4.7.1 或更新版本上執行。 應用程式可以用下列任一種方式受益於這些變更：

- 以 .NET Framework 4.7.1 為目標。 這是建議的方法。 在以 .NET Framework 4.7.1 或更新版本為目標的 WPF 應用程式上，預設會啟用這些協助工具變更。
- 藉由在 app config 檔案的 `<runtime>` 區段中新增下列 [AppContext 參數](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)，並將它設定為 `false`，選擇退出舊版協助工具行為，如下列範例所示。

<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

以 .NET Framework 4.7.1 或更新版本為目標，並且想要保留舊版協助工具行為的應用程式，可以藉由明確將此 AppContext 參數設為 `true`，選擇加入舊版的協助工具功能。
如需 UI 自動化的概觀，請參閱 [UI 自動化概觀](~/docs/framework/ui-automation/ui-automation-overview.md)。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | 主要       |
| 版本 | 4.7.1       |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting(System.Windows.DependencyObject,System.Windows.Automation.AutomationLiveSetting)?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting(System.Windows.DependencyObject)?displayProperty=nameWithType>
- <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore?displayProperty=nameWithType>
