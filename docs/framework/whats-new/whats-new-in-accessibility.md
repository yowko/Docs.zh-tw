---
title: ".NET Framework 協助工具的新功能"
ms.custom: updateeachrelease
ms.date: 10/13/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: what's new [.NET Framework]
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e6a6759ae285f2dd101bddf71ea8e5ca792e87df
ms.sourcegitcommit: 957c696f25e39f923a827fc3ad5e8ab72768838c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2018
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a>.NET Framework 協助工具的新功能

.NET Framework 的目標在於讓使用者更容易存取應用程式。 協助工具功能可讓應用程式提供適當的輔助技術使用者體驗。 從 .NET Framework 4.7.1 開始，.NET Framework 包含大量協助工具改善，可讓開發人員建立可存取的應用程式。 

針對以 .NET Framework 4.7.1 或更新版本為目標的應用程式，預設會啟用新的協助工具功能。 此外，以舊版 .NET Framework 為目標但在 .NET Framework 4.7.1 或更新版本上執行的應用程式可以退出舊版協助工具行為 (進而加入 .NET Framework 4.7.1 中的協助工具改善)，方法是將下列參數新增至應用程式組態檔之 [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) 區段中的 [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 項目。 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

同樣地，以開頭為 4.7.1 的 .NET Framework 版本為目標的應用程式可以停用協助工具功能，方法是將下列參數新增至應用程式組態檔之 [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) 區段中的 [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 項目。 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a>.NET Framework 4.7.1 協助工具的新功能

.NET Framework 4.7.1 包含下列領域的新協助工具功能：

- [Windows Presentation Foundation (WPF)](#windows-presentation-foundation-wpf)

- [Windows Forms](#windows-forms-accessibility-improvements)

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

    現在會顯示 <xref:System.Windows.Controls.Expander> 控制項的焦點視覺效果。 現在也會顯示 <xref:System.Windows.Controls.ComboBox>、<xref:System.Windows.Controls.ListBox> 和 <xref:System.Windows.Controls.RadioButton> 控制項的鍵盤視覺效果。 例如: 

    之前： 
    
    ![協助工具改善之前的聚焦 Expander 控制項](media/expander-before.png)

    之後： 

    ![協助工具改善之後的聚焦 Expander 控制項](media/expander-after.png)

- <xref:System.Windows.Controls.CheckBox> 和 <xref:System.Windows.Controls.RadioButton> 控制項
 
    在高對比佈景主題中選取時，<xref:System.Windows.Controls.CheckBox> 和 <xref:System.Windows.Controls.RadioButton> 控制項中的文字現在更容易出現。 例如: 

    之前： 

    ![協助工具改善之前的聚焦高對比選項按鈕](media/radio-button-before.png)
    
    之後： 

    ![協助工具改善之後的聚焦高對比選項按鈕](media/radio-button-after.png)

- <xref:System.Windows.Controls.ComboBox> 控制項
 
    從 .NET Framework 4.7.1 開始，已停用 <xref:System.Windows.Controls.ComboBox> 控制項的框線色彩與已停用文字的色彩相同。 例如: 
    
    之前： 

     ![協助工具改善之前的 ComboBox 已停用框線和文字](media/combo-disabled-before.png)

    之後：   

     ![協助工具改善之後的 ComboBox 已停用框線和文字](media/combo-disabled-after.png)

    此外，已停用和聚焦按鈕會使用正確的佈景主題色彩。

    之前：

    ![協助工具改善之前的按鈕佈景主題色彩](media/button-themes-before.png) 
    
    之後： 

    ![協助工具改善之後的按鈕佈景主題色彩](media/button-themes-after.png) 

    最後，在 .NET Framework 4.7 和舊版本中，將 <xref:System.Windows.Controls.ComboBox> 控制項的樣式設定為 `Toolbar.ComboBoxStyleKey` 已導致下拉式箭號不可見。 從 .NET Framework 4.7.1 開始，已修正此問題。 例如: 

    之前： 

    ![協助工具改善之前的 Toolbar.ComboBoxStyleKey](media/comboboxstylekey-before.png) 
    
    之後： 

    ![協助工具改善之後的 Toolbar.ComboBoxStyleKey](media/comboboxstylekey-after.png) 

- <xref:System.Windows.Controls.DataGrid> 控制項

    從 .NET Framework 4.7.1 開始，<xref:System.Windows.Controls.DataGrid> 控制項中的排序指標箭號現在會使用正確的佈景主題色彩。 例如: 

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

## <a name="windows-forms-accessibility-improvements"></a>Windows Forms 協助工具改善

在 .NET Framework 4.7.1 中，Windows Forms (WinForms) 包含下列領域的協助工具變更。

**高對比模式中改善的顯示**

從 .NET Framework 4.7.1 開始，各種 WinForms 控制項都提供作業系統中所提供高對比模式的呈現改善。 Windows 10 已變更某些高對比系統色彩的值，而且 Windows Forms 是以 Windows 10 Win32 架構為基礎。 為獲得最佳體驗，在最新版的 Windows 上執行，並新增最新作業系統變更，方法是在測試應用程式中新增 app.manifest 檔案，並將 Windows 10 支援的作業系統列取消註解，使它看起來如下：

```xml
<!– Windows 10 –>
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
一些高對比變更範例包含：

- <xref:System.Windows.Forms.MenuStrip> 項目中的核取記號較容易檢視。

- 選取時，已停用 <xref:System.Windows.Forms.MenuStrip> 項目較容易檢視。

- 所選取 <xref:System.Windows.Forms.Button> 控制項中的文字會與選取色彩成對比。

- 已停用的文字較容易閱讀。 例如: 

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
 
## <a name="see-also"></a>請參閱
[.NET Framework 的新功能](whats-new.md)   
 