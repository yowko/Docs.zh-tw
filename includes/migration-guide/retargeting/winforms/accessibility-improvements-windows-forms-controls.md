---
ms.openlocfilehash: fa24c664e9f7cf6da78d0703c7ebb52c8ebbec20
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606944"
---
### <a name="accessibility-improvements-in-windows-forms-controls"></a>Windows Forms 控制項的協助工具改善

#### <a name="details"></a>詳細資料

Windows Forms 正在使用協助工具技術改善其運作方式，以便為 Windows Forms 客戶提供更好的支援。 包括自 .NET Framework 4.7.1 開始的下列變更：

- 改善高對比模式期間之顯示方式的變更。
- 改善屬性瀏覽器體驗的變更。 屬性瀏覽器改善包括：
- 透過各種下拉式選取視窗進行更佳的鍵盤導覽。
- 減少不必要的定位停駐點。
- 更適當地報告控制項類型。
- 改善的朗讀程式行為。
- 在控制項中實作遺漏的 UI 協助工具模式的變更。

#### <a name="suggestion"></a>建議

**如何加入宣告或退出這些變更** 為了讓應用程式受益于這些變更，它必須在 .NET Framework 4.7.1 或更新版本上執行。 應用程式可以用下列任一種方式受益於這些變更：

- 它已重新編譯為以 .NET Framework 4.7.1 為目標。 在以 .NET Framework 4.7.1 或更新版本為目標的 Windows Forms 應用程式上，預設會啟用這些協助工具變更。
- 藉由在 app config 檔案的 `<runtime>` 區段中新增下列 [AppContext 參數](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)，並將它設定為 `false`，選擇退出舊版協助工具行為，如下列範例所示。

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
  </runtime>
</configuration>
```

以 .NET Framework 4.7.1 或更新版本為目標，並且想要保留舊版協助工具行為的應用程式，可以藉由明確將此 AppContext 參數設為 `true`，選擇加入舊版的協助工具功能。<p/>如需 UI 自動化的概觀，請參閱 [UI 自動化概觀](~/docs/framework/ui-automation/ui-automation-overview.md)。<p/>**為 UI 自動化模式和屬性新增的支援**<br/>協助工具用戶端可以使用通用的公開描述叫用模式，利用新的 WinForms 協助工具功能。 這些不是 WinForms 特有模式。 例如，協助工具用戶端可以在 IAccessible 介面 (MAAS) 上呼叫 QueryInterface 方法，以取得 IServiceProvider 介面。 如果此介面可供使用，用戶端可以使用其 QueryService 方法來要求 IAccessibleEx 介面。 如需詳細資訊，請參閱[從用戶端使用 IAccessibleEx](/windows/desktop/WinAuto/using-iaccessibleex-from-a-client)。 從 .NET Framework 4.7.1 開始，IServiceProvider 和 [IAccessibleEx](/windows/desktop/WinAuto/iaccessibleex) (若適用) 可供 WinForms 協助工具物件使用。<p/>.NET Framework 4.7.1 為下列 UI 自動化模式和屬性新增支援：

- <xref:System.Windows.Forms.ToolStripSplitButton> 和 <xref:System.Windows.Forms.ComboBox> 控制項支援[展開/摺疊模式](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)。
- <xref:System.Windows.Forms.ToolStripMenuItem> 控制項有 [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) 屬性值 <xref:System.Windows.Automation.ControlType.MenuItem?displayProperty=nameWithType>。
- <xref:System.Windows.Forms.ToolStripItem> 控制項支援 <xref:System.Windows.Automation.AutomationElement.NameProperty> 屬性和[展開/摺疊模式](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)。
- <xref:System.Windows.Forms.ToolStripDropDownItem> 控制項支援 <xref:System.Windows.Forms.AccessibleEvents>表示展開或摺疊下拉式清單時的 StateChange 和 NameChange。
- <xref:System.Windows.Forms.ToolStripDropDownButton> 控制項具有 [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) 屬性值 <xref:System.Windows.Automation.ControlType.MenuItem?displayProperty=nameWithType>。
- <xref:System.Windows.Forms.DataGridViewCheckBoxCell> 控制項支援 <xref:System.Windows.Automation.TogglePattern>。
- <xref:System.Windows.Forms.NumericUpDown> 和 <xref:System.Windows.Forms.DomainUpDown> 控制項支援 <xref:System.Windows.Automation.AutomationElement.NameProperty> 屬性，而且具有 <xref:System.Windows.Automation.ControlType.Spinner?displayProperty=nameWithType> 的 [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md)。</p>
**PropertyGrid 控制項的改進** .NET Framework 4.7.1 會將下列改良功能新增至 PropertyBrowser 控制項：

- 使用者在 <xref:System.Windows.Forms.PropertyGrid> 控制項中輸入不正確的值時所顯示之 [錯誤] 對話方塊中的 [詳細資料]**** 按鈕，支援[展開/摺疊模式](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)、狀態與名稱變更通知，以及值為 <xref:System.Windows.Automation.ControlType.MenuItem?displayProperty=nameWithType> 的 [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) 屬性。
- 展開 [錯誤] 對話方塊的 [詳細資料]**** 按鈕時所顯示的 [訊息] 窗格，現在可透過鍵盤存取，並可讓朗讀程式宣告錯誤訊息的內容。
- <xref:System.Windows.Forms.PropertyGrid> 控制項中資料列的 <xref:System.Windows.Forms.AccessibleRole> 已從 &quot;Row&quot; 變更為 &quot;Cell&quot;。 此資料格會對應至 UIA ControlType &quot;DataItem&quot;，讓它支援適當的鍵盤快速鍵和朗讀程式宣告。
- <xref:System.Windows.Forms.PropertyGrid> 控制項將 <xref:System.Windows.Forms.PropertyGrid.PropertySort> 屬性設定為 <xref:System.Windows.Forms.PropertySort.Categorized?displayProperty=nameWithType> 時代表標頭項目的 <xref:System.Windows.Forms.PropertyGrid> 控制項資料列，具有 [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) 屬性值 <xref:System.Windows.Automation.ControlType.Button?displayProperty=nameWithType>。
- <xref:System.Windows.Forms.PropertyGrid> 控制項將 <xref:System.Windows.Forms.PropertyGrid.PropertySort> 屬性設定為 <xref:System.Windows.Forms.PropertySort.Categorized?displayProperty=nameWithType> 時代表標頭項目的 <xref:System.Windows.Forms.PropertyGrid> 控制項資料列，支援[展開/摺疊模式](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)。
- 改善了方格與其上工具列之間的鍵盤導覽。 按下 &quot;Shift-Tab&quot; 現在會選取第一個工具列按鈕，而不是整個工具列。
- 在高對比模式中顯示的 <xref:System.Windows.Forms.PropertyGrid> 控制項，現在會圍繞對應於目前 <xref:System.Windows.Forms.PropertyGrid.PropertySort> 屬性值的工具列按鈕繪製焦點矩形。
- 在高對比模式中顯示且 <xref:System.Windows.Forms.PropertyGrid.PropertySort> 屬性設定為 <xref:System.Windows.Forms.PropertySort.Categorized?displayProperty=nameWithType> 的 <xref:System.Windows.Forms.PropertyGrid> 控制項，現在將以高對比的色彩顯示分類標頭的背景。
- <xref:System.Windows.Forms.PropertyGrid> 控制項可以更好地區別具有焦點的工具列項目與表示 <xref:System.Windows.Forms.PropertyGrid.PropertySort> 屬性目前值的工具列項目。 此修正包含高對比變更及非高對比案例的變更。
- 表示 <xref:System.Windows.Forms.PropertyGrid.PropertySort> 屬性目前值的 <xref:System.Windows.Forms.PropertyGrid> 控制項工具列項目支援 <xref:System.Windows.Automation.TogglePattern>。
- 改善了朗讀程式對區分對齊選擇器中所選取對齊方式的支援。
- 在表單上顯示空的 <xref:System.Windows.Forms.PropertyGrid> 控制項時，它現在會接收焦點，而之前並不會。

**使用高對比佈景主題中作業系統定義的色彩**

- <xref:System.Windows.Forms.ButtonBase.FlatStyle> 屬性設定為 <xref:System.Windows.Forms.FlatStyle.System?displayProperty=nameWithType> (這是預設樣式) 的 <xref:System.Windows.Forms.Button> 和 <xref:System.Windows.Forms.CheckBox> 控制項，現在使用選取的高對比佈景主題中作業系統定義的色彩。 以往，文字和背景色彩不會呈現對比，因此難以閱讀。
- <xref:System.Windows.Forms.Control.Enabled> 屬性設定為 **false** 的 <xref:System.Windows.Forms.Button>、<xref:System.Windows.Forms.CheckBox>、<xref:System.Windows.Forms.RadioButton>、<xref:System.Windows.Forms.Label>、<xref:System.Windows.Forms.LinkLabel> 和 <xref:System.Windows.Forms.GroupBox> 控制項，使用陰影色彩呈現高對比佈景主題中的文字，導致與背景的對比過低。 現在，這些控制項使用作業系統所定義的「已停用文字」色彩。 此修正套用至 `FlatStyle` 屬性設定為非 <xref:System.Windows.Forms.FlatStyle.System?displayProperty=nameWithType> 值的控制項。 後者的控制項是由作業系統呈現。
- <xref:System.Windows.Forms.DataGridView> 現在會於目前焦點所在的儲存格內容周圍呈現可見的矩形。 之前，這不會顯示在特定的高對比佈景主題中。
- <xref:System.Windows.Forms.ToolStripMenuItem><xref:System.Windows.Forms.ToolStripMenuItem.Enabled>屬性設為**false**的控制項現在會使用 &quot; 作業系統所定義的停用文字 &quot; 色彩。
- <xref:System.Windows.Forms.ToolStripMenuItem.Checked> 屬性設定為 **true** 的 <xref:System.Windows.Forms.ToolStripMenuItem> 控制項，現在以對比的系統色彩呈現相關聯的核取記號。  先前的核取記號色彩對比不足，無法在高對比佈景主題中顯示。
注意：Windows 10 已變更某些高對比系統色彩的值。 Windows Forms 架構是以 Win32 架構為基礎。 為了獲得最佳體驗，請在最新版本的 Windows 上執行，並藉由在測試應用程式中新增 app.config 檔案並取消批註下列程式碼，加入宣告最新的 OS 變更：

```xml
<!-- Windows 10 -->
<supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
```

**改善的鍵盤導覽**

- 當 <xref:System.Windows.Forms.ComboBox> 控制項將其 <xref:System.Windows.Forms.ComboBox.DropDownStyle> 屬性設定為 <xref:System.Windows.Forms.ComboBoxStyle.DropDownList?displayProperty=nameWithType>，且它是表單中定位順序的第一個控制項時，如果使用鍵盤來開啟父表單，它現在會顯示焦點矩形。 在這項變更之前，鍵盤焦點是在這個控制項上，但不會呈現焦點指標。

**已改進朗讀程式支援**

- <xref:System.Windows.Forms.MonthCalendar> 控制項已針對輔助技術新增存取控制項的支援，包括讓朗讀程式可以讀取先前無法讀取的控制項值。

- <xref:System.Windows.Forms.CheckedListBox> 控制項現在會於 <xref:System.Windows.Forms.CheckBox.CheckState?displayProperty=nameWithType> 屬性已變更時通知朗讀程式。 之前，朗讀程式不會收到通知，因此使用者不會被告知 <xref:System.Windows.Forms.CheckBox.CheckState> 屬性已更新。
- <xref:System.Windows.Forms.LinkLabel> 控制項已變更其告知朗讀程式有關控制項文字的方式。 之前，朗讀程式會宣告這段文字兩次，並將 &quot;&amp;&quot; 符號讀取為實際文字，即使使用者看不到這些文字也一樣。 已從朗讀程式宣告中移除重複的文字，以及不必要的 &quot;&amp;&quot; 符號。
- <xref:System.Windows.Forms.DataGridViewCell> 控制項類型現在會正確地向朗讀程式和其他輔助技術報告唯讀狀態。
- 朗讀程式現在可以讀取 [Multiple-Document Interface]~/docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md) 應用程式中的子視窗系統功能表。
- 朗讀程式現在可以讀取 <xref:System.Windows.Forms.ToolStripItem.Enabled?displayProperty=nameWithType> 屬性設定為 **false** 的 <xref:System.Windows.Forms.ToolStripMenuItem> 控制項。 之前，朗讀程式無法將焦點放在已停用的功能表項目來讀取內容。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   | 主要       |
| 版本 | 4.8         |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Forms.ToolStripDropDownButton.CreateAccessibilityInstance?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownAccessibleObject.Name?displayProperty=nameWithType>
- [MonthCalendar.AccessibilityObject](xref:System.Windows.Forms.Control.AccessibilityObject)
