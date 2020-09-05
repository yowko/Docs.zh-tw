---
ms.openlocfilehash: 895d09e4ec39bd4a92ed1f4910da80474334d99b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497471"
---
### <a name="accessibility-improvements-in-wpf"></a>WPF 的協助工具改善

#### <a name="details"></a>詳細資料

**高對比改善**

- 現在會顯示 <xref:System.Windows.Controls.Expander> 控制項的焦點。 在舊版 .NET Framework 中，則不是。
- <xref:System.Windows.Controls.CheckBox> 和 <xref:System.Windows.Controls.RadioButton> 控制項在選取時，其中的文字現在比起舊版 .NET Framework 更容易查看。
- 已停用 <xref:System.Windows.Controls.ComboBox> 的框線現在與已停用文字的色彩相同。 在舊版 .NET Framework 中，則不是。
- 已停用和聚焦按鈕現在會使用正確的佈景主題色彩。 在舊版 .NET Framework 中，它們沒有。
- 當 <xref:System.Windows.Controls.ComboBox> 控制項的樣式設定為時，現在會顯示下拉式按鈕 <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey?displayProperty=nameWithType> 。 在舊版 .NET Framework 中，則不是。
- <xref:System.Windows.Controls.DataGrid> 控制項中的排序指標箭號現在會使用佈景主題色彩。 在舊版的 .NET Framework 中，它不是。
- 預設的超連結樣式現在會在滑鼠移至上方時變更為正確的佈景主題色彩。 在舊版的 .NET Framework 中，它不是。
- 現在會顯示選項按鈕上的鍵盤焦點。 在舊版 .NET Framework 中，則不是。
- <xref:System.Windows.Controls.DataGrid> 控制項的核取方塊資料行現在會使用鍵盤焦點回饋的預期色彩。 在舊版的 .NET Framework 中，它不是。
- 鍵盤焦點視覺效果現在會顯示在 <xref:System.Windows.Controls.ComboBox> 和 <xref:System.Windows.Controls.ListBox> 控制項上。 在舊版 .NET Framework 中，則不是。

**螢幕助讀程式互動改善**

- 螢幕助讀程式現在會將 <xref:System.Windows.Controls.Expander> 控制項正確宣告為群組 (展開/摺疊)。
- 螢幕助讀程式現在會將 <xref:System.Windows.Controls.DataGridCell> 控制項正確宣告為資料儲存格 (展開/摺疊)。
- 螢幕助讀程式現在會宣告可編輯 <xref:System.Windows.Controls.ComboBox> 的名稱。
- <xref:System.Windows.Controls.PasswordBox> 螢幕讀取器不再將控制項宣告為「沒有專案在視野中」。

**LiveRegion 支援**

螢幕閱讀程式（例如朗讀程式）可協助人員瞭解應用程式的使用者介面 (UI) ，通常是透過描述目前擁有焦點的 UI 元素。 不過，如果螢幕某處的 UI 項目變更，而且沒有焦點，則使用者可能不會收到通知，並且可能會遺失重要資訊。 LiveRegions 旨在用來解決這個問題。 開發人員可以使用它們來通知螢幕助讀程式或任何其他 [UI 自動化](~/docs/framework/ui-automation/ui-automation-overview.md)用戶端，已對 UI 項目進行重要變更。 螢幕助讀程式接著可以決定如何和何時通知使用者已進行這項變更。 LiveSetting 屬性還可讓螢幕助讀程式知道通知使用者 UI 所做變更的重要性。

#### <a name="suggestion"></a>建議

**如何選擇加入或退出這些變更**

為了讓應用程式受益于這些變更，它必須在 .NET Framework 4.7.1 或更新版本上執行。 應用程式可以用下列任一種方式受益於這些變更：

- 目標 .NET Framework 4.7.1。 這是建議的方法。 在以 .NET Framework 4.7.1 或更新版本為目標的 WPF 應用程式上，預設會啟用這些協助工具變更。
- 藉由在 app config 檔案的 `<runtime>` 區段中新增下列 [AppContext 參數](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)，並將它設定為 `false`，選擇退出舊版協助工具行為，如下列範例所示。

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
    </startup>
    <runtime>
      <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false'  -->
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
    </runtime>
  </configuration>
  ```

以 .NET Framework 4.7.1 或更新版本為目標，而且想要保留舊版協助工具行為的應用程式，可以藉由明確地將此 AppCoNtext 參數設定為，選擇使用舊版的協助工具功能 `true` 。
如需 UI 自動化的總覽，請參閱 [消費者介面自動化總覽](~/docs/framework/ui-automation/ui-automation-overview.md)。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   | 主要       |
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
