---
title: "新功能 .NET Framework 中的協助工具"
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
ms.openlocfilehash: 4886dad94d3a67e78525241a1538c06b9fe4b0be
ms.sourcegitcommit: 6f49c973f62855ffd6c4a322903e7dd50c5c1b50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2017
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a>新功能 .NET Framework 中的協助工具

.NET Framework 的目標是讓應用程式的多個可存取您的使用者。 協助工具功能可讓應用程式提供適當的體驗輔助技術的使用者。 從.NET Framework 4.7.1 開始，.NET Framework 包含大量的協助工具增強功能可讓開發人員建立可存取的應用程式。 

新的協助工具功能會啟用.NET Framework 4.7.1 為目標的應用程式的預設或更新版本。 此外，以舊版.NET Framework 為目標但在.NET Framework 4.7.1 上正在執行或稍後可以選擇應用程式的舊版的協助工具的行為 （和藉此加入.NET Framework 4.7.1 的協助工具增強功能） 的加入下列參數： 要[ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)中的項目[ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md)應用程式的組態檔區段。 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

同樣地，開頭 4.7.1 的.NET Framework 版本為目標的應用程式可以停用協助工具功能加入至下列參數[ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)中的項目[ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md)應用程式的組態檔區段。 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a>新功能 .NET Framework 4.7.1 中的協助工具

.NET Framework 4.7.1 包含下列領域的新協助工具功能：

- [Windows Presentation Foundation (WPF)](#windows-presentation-foundation-wpf)

- [Windows Forms](#windows-forms-accessibility-improvements)

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**螢幕讀取器的增強功能**

如果已啟用協助工具增強功能，.NET Framework 4.7.1 包含會影響到螢幕助讀程式的下列增強功能：

- 在.NET Framework 4.7 及更新版本、<xref:System.Windows.Controls.Expander>控制項已被為按鈕的螢幕助讀程式。 從.NET Framework 4.7.1 開始，經過正確地宣布為可展開/摺疊的群組。

- 在.NET Framework 4.7 及更新版本、<xref:System.Windows.Controls.DataGridCell>控制項已被螢幕助讀程式，為"custom"。 從.NET Framework 4.7.1 開始，經過現在正確地宣布為資料方格資料格 （已當地語系化）。
 
- 從.NET Framework 4.7.1 開始，螢幕助讀程式宣告名稱的可編輯<xref:System.Windows.Controls.ComboBox>。

- 在.NET Framework 4.7 及更新版本、<xref:System.Windows.Controls.PasswordBox>控制項已推出，「 在檢視中沒有項目 」，或有否則不正確的行為。 從.NET Framework 4.7.1 開始來修正此問題。     

**UIAutomation LiveRegion 支援**

螢幕助讀程式，例如 [朗讀程式] 說明人員 UI 的內容讀取應用程式，通常由文字轉換語音輸出具有焦點的 UI 內容。 不過，如果 UI 項目變更並沒有焦點時，使用者可能不會收到通知，並可能會遺失重要資訊。 在解決這個問題，目標是即時的區域。 開發人員可以使用它們來通知螢幕助讀程式或任何其他 UIAutomation 用戶端的 UI 元素已成為一項重要變更。 螢幕助讀程式可以決定如何及何時來通知使用者這項變更。 

若要支援即時的區域，WPF 已加入下列 Api:

- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType>和<xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType>欄位會識別**LiveSetting**屬性和**LiveRegionChanged**事件。 他們可以使用 XAML 設定。

- **AutomationProperties.LiveSetting**附加屬性，會通知使用者的 UI 變更的重要性螢幕助讀程式。

- <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType>屬性，其可識別**AutomationProperties.LiveSetting**附加屬性。
 
- <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType>方法，可以覆寫，以提供**LiveSetting**值。

- <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType>和<xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType>方法取得和設定**LiveSetting**值。
 
- <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType>列舉型別，它會定義下列**LiveSetting**值：

   - <xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>. 如果即時區域的內容已變更的項目不會傳送通知。   
   - <xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>. 如果即時區域的內容變更，項目會傳送不中斷通知。   

  - <xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>. 如果即時區域的內容變更，項目會傳送中斷通知。   

您可以設定來建立 LiveRegion **AutomationProperties.LiveSetting**感興趣，如下列範例所示的項目上的屬性：   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

當即時區域中的資料變更，您需要告知螢幕助讀程式，您明確地引發事件，如下列範例所示。

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

**高對比**

從.NET Framework 4.7.1 開始，在高對比的增強功能已對不同的 WPF 控制項。 它們現在是可見時<xref:System.Windows.SystemParameters.HighContrast%2A>主題設定。 這些活動包括：

- <xref:System.Windows.Controls.Expander> 控制項

    焦點視覺<xref:System.Windows.Controls.Expander>控制項現在會顯示。 鍵盤視覺效果的<xref:System.Windows.Controls.ComboBox>，<xref:System.Windows.Controls.ListBox>，和<xref:System.Windows.Controls.RadioButton>控制項也會顯示。 例如: 

    之前： 
    
    ![Expander 控制項具有焦點之前協助工具增強功能](media/expander-before.png)

    之後： 

    ![Expander 控制項具有焦點後協助工具增強功能](media/expander-after.png)

- <xref:System.Windows.Controls.CheckBox>和<xref:System.Windows.Controls.RadioButton>控制項
 
    中的文字<xref:System.Windows.Controls.CheckBox>和<xref:System.Windows.Controls.RadioButton>控制項現在是看得更清楚時選取 高對比佈景主題。 例如: 

    之前： 

    ![高對比選項按鈕具有焦點之前協助工具增強功能](media/radio-button-before.png)
    
    之後： 

    ![高對比選項按鈕具有焦點後協助工具增強功能](media/radio-button-after.png)

- <xref:System.Windows.Controls.ComboBox> 控制項
 
    從.NET Framework 4.7.1，已停用的框線開始<xref:System.Windows.Controls.ComboBox>控制項是相同的已停用文字色彩。 例如: 
    
    之前： 

     ![框線與文字協助工具增強功能之前，已停用下拉式方塊](media/combo-disabled-before.png)

    之後：   

     ![下拉式方塊框線與文字在之後停用協助工具增強功能](media/combo-disabled-after.png)

    此外，停用，已取得焦點的按鈕會使用正確的佈景主題色彩。

    之前：

    ![協助工具增強功能之前按鈕佈景主題色彩](media/button-themes-before.png) 
    
    之後： 

    ![協助改進之後按鈕佈景主題色彩](media/button-themes-after.png) 

    最後，在舊版本中，設定與.NET Framework 4.7<xref:System.Windows.Controls.ComboBox>控制項的樣式`Toolbar.ComboBoxStyleKey`造成不可見的下拉式箭號。 從.NET Framework 4.7.1 開始來修正此問題。 例如: 

    之前： 

    ![Toolbar.ComboBoxStyleKey 之前協助工具增強功能](media/comboboxstylekey-before.png) 
    
    之後： 

    ![Toolbar.ComboBoxStyleKey 之後協助工具增強功能](media/comboboxstylekey-after.png) 

- <xref:System.Windows.Controls.DataGrid> 控制項

    從.NET Framework 4.7.1，排序指標箭號，在開始<xref:System.Windows.Controls.DataGrid>控制項現在會使用更正佈景主題色彩。 例如: 

    之前： 

    ![排序指標箭號之前存取範圍的增強功能](media/sort-indicator-before.png) 
    
    之後：   
 
    ![排序標記箭號，協助改進之後](media/sort-indicator-after.png) 
    
    此外，在.NET Framework 4.7 和更早版本中，預設連結樣式變更為不正確的色彩在滑鼠在高對比模式。 這是以.NET Framework 4.7.1 啟動已解決。 同樣地，<xref:System.Windows.Controls.DataGrid>核取方塊資料行使用的鍵盤焦點回函從.NET Framework 4.7.1 開始的預期的色彩。

    之前： 

    ![DataGrid 的預設連結樣式之前協助工具增強功能](media/default-link-style-before.png) 
 
    之後：    
  
    ![DataGrid 的預設連結樣式之後協助工具增強功能](media/default-link-style-after.png)  

如需 WPF 在.NET Framework 4.7.1 的協助工具改良功能的詳細資訊，請參閱[WPF 中的協助工具改進](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf)。

## <a name="windows-forms-accessibility-improvements"></a>Windows Form 協助工具增強功能

在.NET Framework 4.7.1 中，Windows Forms (WinForms) 包含下列領域中的存取範圍變更。

**改善的顯示高對比模式**

從.NET Framework 4.7.1 開始，各種 WinForms 控制項提供改善的呈現在作業系統中提供的高對比模式。 Windows 10 已變更的某些系統高對比的色彩，值和 Windows Form 為基礎的 Windows 10 Win32 架構。 獲得最佳的體驗，在最新的 Windows 版本上執行，並選擇加入最新的 OS 變更 app.manifest 檔案測試應用程式後取消註解的 Windows 10 支援的 OS 列，使它看起來下列新增：

```xml
<!– Windows 10 –>
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
高對比變更的一些範例包括：

- 中的核取記號<xref:System.Windows.Forms.MenuStrip>項目較容易檢視。

- 選取時，停用<xref:System.Windows.Forms.MenuStrip>項目較容易檢視。

- 在選取的文字<xref:System.Windows.Forms.Button>控制使用選取範圍的色彩對比。

- 已停用的文字是容易讀取。 例如: 

    之前：

    ![已停用協助工具增強功能之前的文字](media/wf-disabled-before.png) 

    之後：

    ![已停用協助工具改進之後的文字](media/wf-disabled-after.png) 

- 高對比改善執行緒例外狀況對話方塊。

**改良的 [朗讀程式] 支援**

.NET Framework 4.7.1 中的 Windows Form 包含以下的協助工具改良，用於 [朗讀程式]:

- <xref:System.Windows.Forms.MonthCalendar>由 [朗讀程式]，以及其他 UI 自動化工具，可以存取控制項。

- <xref:System.Windows.Forms.CheckedListBox>控制項項目的核取狀態已經變更，則會通知使用者他們已變更的清單項目值時，通知 [朗讀程式]。
 
- <xref:System.Windows.Forms.DataGridViewCell>控制 [朗讀程式] 來報告正確的唯讀狀態。
 
- [朗讀程式] 現在可以讀取已停用<xref:System.Windows.Forms.ToolStripMenuItem>文字，而之前它會略過停用的功能表項目。

**UIAutomation 協助工具模式的增強的支援**

從.NET Framework 4.7.1 開始，開發人員的協助工具技術工具可以利用一般的應用程式開發介面協助工具模式和數個 WinForms 控制項的屬性。 這些協助工具增強功能包括：

- <xref:System.Windows.Forms.ComboBox>和<xref:System.Windows.Forms.ToolStripSplitButton>現在支援[展開/摺疊模式](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)。
 
- <xref:System.Windows.Forms.DataGridViewCheckBoxCell>現在支援[切換模式](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md)。
 
- <xref:System.Windows.Forms.ToolStripItem>支援<xref:System.Windows.Automation.AutomationElement.Name>屬性和[展開/摺疊模式](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)。

- <xref:System.Windows.Forms.NumericUpDown>和<xref:System.Windows.Forms.DomainUpDown>控制支援<xref:System.Windows.Automation.automationElement.Name>屬性。

**提升的屬性瀏覽器體驗**

從.NET Framework 4.7.1 開始，Windows Form 包含：

- 透過各種不同的下拉式清單選取 windows 的更佳的鍵盤巡覽。
- 減少不必要的定位停駐點。
- 更好的控制項類型的報告。
- 改善 [朗讀程式] 行為。
 
## <a name="see-also"></a>另請參閱
[什麼是.NET Framework 的新功能](whats-new.md)   
 