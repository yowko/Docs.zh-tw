---
title: .NET Framework 協助工具的新功能
ms.custom: updateeachrelease
ms.date: 04/10/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 092b1cfc9350ea398eb18199f19a8eee7ea9f218
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675435"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a>.NET Framework 協助工具的新功能

.NET Framework 的目標在於讓使用者更容易存取應用程式。 協助工具功能可讓應用程式提供適當的輔助技術使用者體驗。 從 .NET Framework 4.7.1 開始，.NET Framework 包含大量協助工具改善，可讓開發人員建立可存取的應用程式。 

## <a name="accessibility-switches"></a>協助工具參數

您可以設定您的應用程式，以選擇加入協助工具功能，如果它以 .NET Framework 4.7 或較早版本為目標但是在 .NET Framework 4.7.1 或更新版本上執行的話。 您也可以設定應用程式以使用舊版的功能 (且不利用協助工具功能)，如果它以 .NET Framework 4.7.1 或更新版本為目標的話。 包含協助工具功能的每個 .NET Framework 版本都有版本特定的協助工具參數，您可以新增到應用程式組態檔 [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) 區段中的 [`<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 項目。 以下是支援的參數：

|版本|參數|
|---|---|
|.NET Framework 4.7.1|"Switch.UseLegacyAccessibilityFeatures"|
|.NET Framework 4.7.2|"Switch.UseLegacyAccessibilityFeatures.2"|

### <a name="taking-advantage-of-accessibility-enhancements"></a>利用協助工具增強功能

針對以 .NET Framework 4.7.1 或更新版本為目標的應用程式，預設會啟用新的協助工具功能。 此外，以舊版 .NET Framework 為目標但在 .NET Framework 4.7.1 或更新版本上執行的應用程式可以退出舊版協助工具行為 (進而利用協助工具增強功能)，方法是新增參數至應用程式組態檔之 [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) 區段中的 [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 項目，並將其值設定為 `false`。 以下顯示如何加入 .NET Framework 4.7.1 中引進的協助工具增強功能：

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

如果您選擇加入 .NET Framework 較新版本中的協助工具功能，您必須同時明確加入來自舊版 .NET Framework 的功能。 設定您的應用程式以同時利用 .NET Framework 4.7.1 和 4.7.2 的協助工具改善功能，需要下列 [`<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 項目：

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a>還原舊版行為

以從 4.7.1 開始的 .NET Framework 版本為目標的應用程式，可以停用協助工具功能，方法是新增參數至應用程式組態檔之 [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) 區段中的 [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 項目，並將其值設定為 `true`。 例如，下列組態會選擇退出 .NET Framework 4.7.2 中引進的協助工具功能：  

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-472"></a>.NET Framework 4.7.2 協助工具的新功能

.NET Framework 4.7.2 包含下列領域的新協助工具功能：

- [Windows Forms](#winforms472)

- [Windows Presentation Foundation (WPF)](#wpf472)

<a name="winforms472"></a>
### <a name="windows-forms"></a>Windows Forms

**高對比佈景主題中的作業系統定義色彩**

從 .NET Framework 4.7.2 開始，Windows Forms 在高對比佈景主題中使用作業系統所定義的色彩。 這會影響下列控制項：

- <xref:System.Windows.Forms.ToolStripDropDownButton> 控制項的下拉式箭號。

- <xref:System.Windows.Forms.ButtonBase.FlatStyle> 設成 <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> 或 <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType> 的 <xref:System.Windows.Forms.Button>、<xref:System.Windows.Forms.RadioButton> 和 <xref:System.Windows.Forms.CheckBox>。 以往，選取的文字和背景色彩不會呈現對比，因此難以閱讀。

- 包含在 <xref:System.Windows.Forms.GroupBox> 內的控制項，且其 <xref:System.Windows.Forms.Control.Enabled> 屬性設定為 `false`。
 
- <xref:System.Windows.Forms.ToolStripButton>、<xref:System.Windows.Forms.ToolStripComboBox> 和 <xref:System.Windows.Forms.ToolStripDropDownButton> 控制項，它們在高對比模式下有更高的亮度對比率。

- <xref:System.Windows.Forms.DataGridViewLinkCell> 的 <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> 屬性。

**朗讀程式增強功能**

從 .NET Framework 4.7.2 開始，朗讀程式的支援增強功能如下：

- 在播報 <xref:System.Windows.Forms.ToolStripMenuItem> 的文字時，現已會播報 <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> 屬性的值。 

- 當 <xref:System.Windows.Forms.ToolStripMenuItem> 的 <xref:System.Windows.Forms.Control.Enabled> 屬性設定為 `false` 時，會指明該情況。

- 當 <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> 屬性設定為 `true` 時，會提供核取方塊狀態的回應。

- 朗讀程式掃描模式的焦點順序，與 ClickOnce 下載對話視窗中所看見的控制項順序已一致。

**DataGridView 改善**

從 .NET Framework 4.7.2 開始，<xref:System.Windows.Forms.DataGridView> 控制項已經引進下列協助工具改善：

- 資料列可使用鍵盤排序。 使用者可使用 F3 鍵，依目前的資料行排序。

- 當 <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> 設定為 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> 時，資料行標頭會變更色彩，以在目前的資料列中指出使用者滑過儲存格時所在的資料行位置。

- <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> 的 <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> 屬性會傳回正確的父控制項。

**改善的視覺提示**

- <xref:System.Windows.Forms.ButtonBase.Text> 屬性為空白的控制項 <xref:System.Windows.Forms.RadioButton> 與 <xref:System.Windows.Forms.CheckBox>，會於接收到焦點時顯示焦點指標。

**已改進屬性方格支援**

- <xref:System.Windows.Forms.PropertyGrid> 控制項子項目現在只有在已啟用 PropertyGrid 項目的情況下，才會傳回 <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> 屬性的 `true`。

- <xref:System.Windows.Forms.PropertyGrid> 控制項子項目只有在使用者可變更 PropertyGrid 項目的情況下，才會傳回 <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> 屬性的 `false`。

**改善的鍵盤導覽**

- <xref:System.Windows.Forms.ToolStripPanel.TabStop> 屬性設定為 `true` 的 <xref:System.Windows.Forms.ToolStripPanel> 內含焦點時，<xref:System.Windows.Forms.ToolStripButton> 控制項允許焦點

<a name="wpf472"></a>
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**CheckBox 和 RadioButton 控制項的變更**

在 .NET Framework 4.7.1 和舊版的傳統和高對比佈景主題中，WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> 和 <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> 控制項的焦點視覺效果不一致且不正確。  當控制項沒有任何內容集時，會發生上述問題。  這可能會讓人混淆佈景主題之間的轉換，也看不清楚焦點視覺效果。

現在，.NET Framework 4.7.2 的這些視覺效果在各佈景主題之間會更一致；在傳統和高對比佈景主題中也可以看得更清楚。

**裝載於 WPF 應用程式的 WinForms 控制項**

對於 .NET Framework 4.7.1 和舊版中，裝載於 WPF 應用程式的 WinForms 控制項，使用者無法按 Tab 鍵移出 WinForms 層，如果該層的第一個或最後一個控制項是 WPF <xref:System.Windows.Forms.Integration.ElementHost> 控制項。 在 .NET Framework 4.7.2 中，使用者現在能按 Tab 鍵移出 WinForms 層。

不過，依賴焦點絕不會逸出 WinForms 層的自動化應用程式可能不再如預期運作。

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a>.NET Framework 4.7.1 協助工具的新功能

.NET Framework 4.7.1 包含下列領域的新協助工具功能：

- [Windows Presentation Foundation (WPF)](#wpf471)

- [Windows Forms](#winforms471)

- [ASP.NET Web 控制項](#aspnet471)

- [.NET SDK 工具](#tools471)

- [Windows Workflow Foundation (WF) 工作流程設計工具](#wf471)

<a name="wpf471"></a>
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**螢幕助讀程式改善**

如果啟用協助工具改善，則 .NET Framework 4.7.1 會包含下列影響螢幕助讀程式的改善：

- 在 .NET Framework 4.7 和舊版本中，螢幕助讀程式已將 <xref:System.Windows.Controls.Expander> 控制項公告為按鈕。 從 .NET Framework 4.7.1 開始，已將它們正確地宣告為可展開/可摺疊的群組。

- 在 .NET Framework 4.7 和舊版本中，螢幕助讀程式已將 <xref:System.Windows.Controls.DataGridCell> 控制項宣告為「自訂」。 從 .NET Framework 4.7.1 開始，現在已將它們正確地宣告為資料格 (已當地語系化)。
 
- 從 .NET Framework 4.7.1 開始，螢幕助讀程式會宣告可編輯 <xref:System.Windows.Controls.ComboBox> 的名稱。

- 在 .NET Framework 4.7 和舊版本中，<xref:System.Windows.Controls.PasswordBox> 控制項已宣告為「檢視中沒有項目」或具有不正確的行為。 從 .NET Framework 4.7.1 開始，已修正此問題。

**UIAutomation LiveRegion 支援**

朗讀程式這類螢幕助讀程式可協助人員讀取應用程式 UI 內容，通常是透過具有焦點之 UI 內容的文字轉換語音輸出。 不過，如果 UI 項目變更，而且沒有焦點，則使用者可能不會收到通知，並可能遺失重要資訊。 即時區域的目標在解決這個問題。 開發人員可以使用它們來通知螢幕助讀程式或任何其他 UIAutomation 用戶端，已對 UI 項目進行重要變更。 螢幕助讀程式接著可以決定如何和何時通知使用者已進行這項變更。 

為了支援即時區域，已將下列 API 新增至 WPF：

- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> 和 <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> 欄位，可識別 **LiveSetting** 屬性和 **LiveRegionChanged** 事件。 它們可以使用 XAML 進行設定。

- **AutomationProperties.LiveSetting** 附加屬性，可通知螢幕助讀程式有關 UI 變更對使用者的重要性。

- <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> 屬性，可識別 **AutomationProperties.LiveSetting** 附加屬性。
 
- <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> 方法，可以覆寫以提供 **LiveSetting** 值。

- <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> 和 <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> 方法，可以取得和設定 **LiveSetting** 值。
 
- <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> 列舉，可以定義下列可能的 **LiveSetting** 值：

   - <xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>. 如果即時區域的內容變更，項目不會傳送通知。   
   - <xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>. 如果即時區域的內容變更，項目會傳送不中斷通知。   

  - <xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>. 如果即時區域的內容變更，項目會傳送中斷通知。   

您可以在感興趣的項目上設定 **AutomationProperties.LiveSetting** 屬性，以建立 LiveRegion，如下列範例所示：   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

如果即時區域中的資料變更，而且您需要通知螢幕助讀程式，請明確地引發事件，如下列範例所示。

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

**高對比**

從 .NET Framework 4.7.1 開始，已對各種 WPF 控制項進行高對比改善。 現在，設定 <xref:System.Windows.SystemParameters.HighContrast%2A> 佈景主題時，可以看到它們。 它們包括：

- <xref:System.Windows.Controls.Expander> 控制項

    現在會顯示 <xref:System.Windows.Controls.Expander> 控制項的焦點視覺效果。 現在也會顯示 <xref:System.Windows.Controls.ComboBox>、<xref:System.Windows.Controls.ListBox> 和 <xref:System.Windows.Controls.RadioButton> 控制項的鍵盤視覺效果。 例如：

    之前： 
    
    ![協助工具改善之前的聚焦 Expander 控制項](media/expander-before.png)

    之後： 

    ![協助工具改善之後的聚焦 Expander 控制項](media/expander-after.png)

- <xref:System.Windows.Controls.CheckBox> 和 <xref:System.Windows.Controls.RadioButton> 控制項
 
    在高對比佈景主題中選取時，<xref:System.Windows.Controls.CheckBox> 和 <xref:System.Windows.Controls.RadioButton> 控制項中的文字現在更容易出現。 例如：

    之前： 

    ![協助工具改善之前的聚焦高對比選項按鈕](media/radio-button-before.png)
    
    之後： 

    ![協助工具改善之後的聚焦高對比選項按鈕](media/radio-button-after.png)

- <xref:System.Windows.Controls.ComboBox> 控制項
 
    從 .NET Framework 4.7.1 開始，已停用 <xref:System.Windows.Controls.ComboBox> 控制項的框線色彩與已停用文字的色彩相同。 例如：
    
    之前： 

     ![協助工具改善之前的 ComboBox 已停用框線和文字](media/combo-disabled-before.png)

    之後：   

     ![協助工具改善之後的 ComboBox 已停用框線和文字](media/combo-disabled-after.png)

    此外，已停用和聚焦按鈕會使用正確的佈景主題色彩。

    之前：

    ![協助工具改善之前的按鈕佈景主題色彩](media/button-themes-before.png) 
    
    之後： 

    ![協助工具改善之後的按鈕佈景主題色彩](media/button-themes-after.png) 

    最後，在 .NET Framework 4.7 和舊版本中，將 <xref:System.Windows.Controls.ComboBox> 控制項的樣式設定為 `Toolbar.ComboBoxStyleKey` 已導致下拉式箭號不可見。 從 .NET Framework 4.7.1 開始，已修正此問題。 例如：

    之前： 

    ![協助工具改善之前的 Toolbar.ComboBoxStyleKey](media/comboboxstylekey-before.png) 
    
    之後： 

    ![協助工具改善之後的 Toolbar.ComboBoxStyleKey](media/comboboxstylekey-after.png) 

- <xref:System.Windows.Controls.DataGrid> 控制項

    從 .NET Framework 4.7.1 開始，<xref:System.Windows.Controls.DataGrid> 控制項中的排序指標箭號現在會使用正確的佈景主題色彩。 例如：

    之前： 

    ![協助工具改善之前的排序指標箭號](media/sort-indicator-before.png) 
    
    之後：   
 
    ![協助工具改善之後的排序指標箭號](media/sort-indicator-after.png) 
    
    此外，在 .NET Framework 4.7 和舊版本中，高對比模式中滑鼠移至上方的預設連結樣式已變更為不正確的色彩。 從 .NET Framework 4.7.1 開始，已解決此問題。 同樣地，從 .NET Framework 4.7.1 開始，<xref:System.Windows.Controls.DataGrid> 核取方塊資料行會使用鍵盤焦點回饋的預期色彩。

    之前： 

    ![協助工具改善之前的 DataGrid 預設連結樣式](media/default-link-style-before.png) 
 
    之後：    
  
    ![協助工具改善之後的 DataGrid 預設連結樣式](media/default-link-style-after.png)  

如需 .NET Framework 4.7.1 中 WPF 協助工具改善的詳細資訊；請參閱 [WPF 中的協助工具改善](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf)。

<a name="winforms471"></a>
### <a name="windows-forms-accessibility-improvements"></a>Windows Forms 協助工具改善

在 .NET Framework 4.7.1 中，Windows Forms (WinForms) 包含下列領域的協助工具變更。

**高對比模式中改善的顯示**

從 .NET Framework 4.7.1 開始，各種 WinForms 控制項都提供作業系統中所提供高對比模式的呈現改善。 Windows 10 已變更某些高對比系統色彩的值，而且 Windows Forms 是以 Windows 10 Win32 架構為基礎。 為獲得最佳體驗，請在最新版的 Windows 上執行，並新增最新 OS 變更，方法是在測試應用程式中新增 app.manifest 檔案，並將 Windows 10 支援的 OS 列取消註解，使它看起來如下：

```xml
<!-- Windows 10 -->
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
一些高對比變更範例包含：

- <xref:System.Windows.Forms.MenuStrip> 項目中的核取記號較容易檢視。

- 選取時，已停用 <xref:System.Windows.Forms.MenuStrip> 項目較容易檢視。

- 所選取 <xref:System.Windows.Forms.Button> 控制項中的文字會與選取色彩成對比。

- 已停用的文字較容易閱讀。 例如：

    之前：

    ![協助工具改善之前的已停用文字](media/wf-disabled-before.png) 

    之後：

    ![協助工具改善之後的已停用文字](media/wf-disabled-after.png) 

- 執行緒例外狀況對話方塊中的高對比改善。

**改善的朗讀程式支援**

.NET Framework 4.7.1 中的 Windows Forms 包含朗讀程式的下列協助工具改善：

- 朗讀程式和其他 UI 自動化工具可以存取 <xref:System.Windows.Forms.MonthCalendar> 控制項。

- <xref:System.Windows.Forms.CheckedListBox> 控制項會在項目的核取狀態已經變更，因而通知使用者它們已變更清單項目值時通知 [朗讀程式]。
 
- <xref:System.Windows.Forms.DataGridViewCell> 控制項會向朗讀程式報告正確的唯讀狀態。
 
- 朗讀程式現在可以讀取已停用 <xref:System.Windows.Forms.ToolStripMenuItem> 文字，而之前它會略過已停用的功能表項目。

**UIAutomation 協助工具模式的增強支援**

從 .NET Framework 4.7.1 開始，協助工具技術工具開發人員可以利用數個 WinForms 控制項的一般 API 協助工具模式和屬性。 這些協助工具改善包含：

- <xref:System.Windows.Forms.ComboBox> 和 <xref:System.Windows.Forms.ToolStripSplitButton> 現在支援[展開/摺疊模式](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)。
 
- <xref:System.Windows.Forms.DataGridViewCheckBoxCell> 現在支援[切換模式](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md)。
 
- <xref:System.Windows.Forms.ToolStripItem> 控制項支援 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> 屬性和[展開/摺疊模式](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)。

- <xref:System.Windows.Forms.NumericUpDown> 和 <xref:System.Windows.Forms.DomainUpDown> 控制項支援 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> 屬性。

**改善的屬性瀏覽器體驗**

從 .NET Framework 4.7.1 開始，Windows Forms 包含：

- 透過各種下拉式選取視窗進行更佳的鍵盤導覽。
- 減少不必要的定位停駐點。
- 更適當地報告控制項類型。
- 改善的朗讀程式行為。
 
<a name="aspnet471"></a>
### <a name="aspnet-web-controls"></a>ASP.NET Web 控制項

從 .NET Framework 4.7.1 和 Visual Studio 2017 15.3 開始，ASP.NET 已經改善 ASP.NET Web 控制項如何搭配 Visual Studio 中的協助工具技術。 變更包括下列項目：

- 在控制項中，實作遺漏 UI 協助工具模式的變更，例如在 [詳細資料檢視精靈] 的 [新增欄位] 對話方塊或 [ListView 精靈] 的 [設定 ListView] 對話方塊。

- 改善高對比模式顯示的變更，例如**資料頁面巡覽區欄位編輯器**。

- 改善控制項鍵盤瀏覽體驗的變更，例如 DataPager 控制項 [編輯頁面巡覽區欄位精靈] 的 [欄位] 對話方塊、[設定 ObjectContext] 對話方塊，或 [設定資料來源精靈] 的 [設定資料選取項目] 對話方塊。

<a name="tools471"></a>
### <a name="net-sdk-tools"></a>.NET SDK 工具

[組態編輯器工具 (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) 和[服務追蹤檢視器工具 (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) 藉由修正各種協助工具問題來改善。 其中大部分是小問題，例如未定義名稱，或未正確實作某些 UI 自動化模式。 雖然許多使用者並未注意到這些不正確的值，但使用螢幕助讀程式等輔助技術的客戶會發現這些 SDK 工具更易於存取。 

這些增強功能變更一些先前的行為，例如鍵盤焦點的順序。

<a name="wf471"></a>
### <a name="windows-workflow-foundation-wf-workflow-designer"></a>Windows Workflow Foundation (WF) 工作流程設計工具

在工作流程設計工具中的協助工具變更包括下列各項：

- 在某些控制項中，定位順序變更為由左至右及由上至下：

  - 設定 <xref:System.ServiceModel.Activities.InitializeCorrelation> 活動之關聯性資料的初始化關聯性視窗。

  - <xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.SendReply> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 活動的內容定義視窗。

- 可透過鍵盤使用多個功能：

  - 編輯活動的屬性時，如果第一次將焦點放在屬性群組，可以透過鍵盤將其摺疊。

  - 可透過鍵盤存取警告圖示。

  - 可透過鍵盤存取 [屬性] 視窗中的 [其他屬性] 按鈕。

  - 鍵盤使用者可以存取工作流程設計工具之 [引數] 和 [變數] 窗格中的標頭項目。

- 在以下這類情況發生時，已改善具有焦點之項目的可見性：

  - 在工作流程設計工具與活動設計工具所使用的資料格中新增資料列。

  - 使用 Tab 鍵循環顯示 <xref:System.ServiceModel.Activities.ReceiveReply> 和 <xref:System.ServiceModel.Activities.SendReply> 活動的欄位。

  - 設定變數或引數的預設值

- 螢幕助讀程式現在可以正確辨識：

  - 工作流程設計工具中設定的中斷點。

  - <xref:System.Activities.Statements.FlowSwitch%601>、<xref:System.Activities.Statements.FlowDecision> 和 <xref:System.ServiceModel.Activities.CorrelationScope> 活動。
  - <xref:System.ServiceModel.Activities.Receive> 活動的內容。

  - <xref:System.Activities.Statements.InvokeMethod> 活動的目標類型。

  - <xref:System.Activities.Statements.TryCatch> 活動中的例外狀況下拉式方塊和 Finally 區段。

  - 傳訊活動 (<xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.SendReply> 和 <xref:System.ServiceModel.Activities.ReceiveReply>) 中的 [訊息類型] 下拉式方塊、[新增關聯性初始設定式] 視窗、[內容定義] 視窗和 [CorrelatesOn 定義] 視窗。

  - 狀態機器轉換和轉換目的地。

  - <xref:System.Activities.Statements.FlowDecision> 活動的註釋和連接器。

  - 活動的操作 (右鍵) 功能表。

  - 屬性方格中的屬性值編輯器、[清除搜尋] 按鈕、[依分類] 及 [字母順序] 排序按鈕和 [運算式編輯器] 對話方塊。

  - 工作流程設計工具中的顯示比例百分比。

  - <xref:System.Activities.Statements.Parallel> 和 <xref:System.Activities.Statements.Pick> 活動中的分隔符號。

  - <xref:System.Activities.Statements.InvokeDelegate> 活動。

  - 字典活動 (`Microsoft.Activities.AddToDictionary<TKey,TValue>`、`Microsoft.Activities.RemoveFromDictionary<TKey,TValue>` 等) 的 [選取類型] 視窗。

  - [瀏覽並選取 .NET 類型] 視窗。

  - 工作流程設計工具中的階層連結。

- 選擇高對比佈景主題的使用者會看到工作流程設計工具和其控制項在可見性方面的許多改善，例如項目之間的更佳對比比例以及用於焦點項目的更明顯選取方塊。

## <a name="see-also"></a>另請參閱

- [.NET Framework 的新功能](whats-new.md)

