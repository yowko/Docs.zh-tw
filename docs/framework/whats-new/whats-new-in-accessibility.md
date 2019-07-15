---
title: .NET Framework 協助工具的新功能
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da73df97524b9e394fac795daf14a3f0fb1f4e3d
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661378"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a>.NET Framework 協助工具的新功能

.NET Framework 的目標在於讓使用者更容易存取應用程式。 協助工具功能可讓應用程式提供適當的輔助技術使用者體驗。 從 .NET Framework 4.7.1 開始，.NET Framework 包含大量協助工具改善，可讓開發人員建立無障礙應用程式。

## <a name="accessibility-switches"></a>協助工具參數

如果您的應用程式是以 .NET Framework 4.7 或較早版本為目標，但是在 .NET Framework 4.7.1 或更新版本上執行，您可以將其設定為選擇加入協助工具功能。 如果您的應用程式是以 .NET Framework 4.7.1 或更新版本為目標，您也可以將其設定為使用舊版的功能 (且不利用協助工具功能)。 包含協助工具功能的每個 .NET Framework 版本都有版本特定的協助工具參數，您可以新增到應用程式組態檔 [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) 區段中的 [`<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 項目。 以下是支援的參數：

|版本|參數|
|---|---|
|.NET Framework 4.7.1|"Switch.UseLegacyAccessibilityFeatures"|
|.NET Framework 4.7.2|"Switch.UseLegacyAccessibilityFeatures.2"|
|.NET Framework 4.8|"Switch.UseLegacyAccessibilityFeatures.3"|

### <a name="taking-advantage-of-accessibility-enhancements"></a>利用協助工具增強功能

針對以 .NET Framework 4.7.1 或更新版本為目標的應用程式，預設會啟用新的協助工具功能。 此外，如果應用程式是以舊版 .NET Framework 為目標但在 .NET Framework 4.7.1 或更新版本上執行，您可以新增參數至應用程式組態檔 [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) 區段中的 [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 項目，並將其值設定為 `false`，使其退出舊版協助工具行為 (進而利用協助工具改善)。 下列顯示如何選擇加入 .NET Framework 4.7.1 中引進的協助工具增強功能：

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

如果您選擇加入 .NET Framework 較新版本中的協助工具功能，您必須同時明確加入來自舊版 .NET Framework 的功能。 若要將應用程式設定為同時利用 .NET Framework 4.7.1 和 4.7.2 的協助工具改善，您必須使用下列 [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 項目：

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

若要將應用程式設定為利用 .NET Framework 4.7.1、4.7.2 和 4.8 的協助工具改善，您必須使用下列 [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 項目：

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
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

## <a name="whats-new-in-accessibility-in-net-framework-48"></a>.NET Framework 4.8 協助工具的新功能

.NET Framework 4.8 包含下列領域的新協助工具功能：

- [Windows Forms](#winforms48)

- [Windows Presentation Foundation (WPF)](#wpf48)

- [Windows Workflow Foundation (WF) 工作流程設計工具](#wf48)

<a name="winforms48" />

### <a name="windows-forms"></a>Windows Forms

在 .NET Framework 4.8 中，Windows Forms 已新增對許多常用控制項的 LiveRegions 和通知事件支援。 它也新增當使用者利用鍵盤巡覽至控制項時的工具提示支援。

**標籤與 StatusStrips 中的 UIA LiveRegions 支援**

UIA LiveRegions 可讓應用程式開發人員將控制項中的文字變更 (位於使用者正在處理的位置以外) 通知螢幕助讀程式。 例如，對於顯示連線狀態的 <xref:System.Windows.Forms.StatusStrip> 控制項，這非常有用。 當連線中斷且狀態變更時，開發人員可能需要通知螢幕助讀程式。

從 .NET Framework 4.8 開始，Windows Forms 即針對 <xref:System.Windows.Forms.Label> 和 <xref:System.Windows.Forms.StatusStrip> 這兩個控制項實作 UIA LiveRegions。 例如，下列程式碼會在名為 `label1` 的 <xref:System.Windows.Forms.Label> 控制項中使用 LiveRegion：

```csharp
public Form1()
{
   InitializeComponent();
   label1.AutomationLiveSetting = AutomationLiveSetting.Polite;
}

…
Label1.Text = “Ready!”;
```

不論使用者與應用程式互動的位置為何，朗讀程式均會播報「就緒」。

您也可以將您的 <xref:System.Windows.Forms.UserControl> 實作為 LiveRegion：

```csharp
using System;
using System.Windows.Forms;
using System.Windows.Forms.Automation;

namespace WindowsFormsApplication
{
   public partial class UserControl1 : UserControl, IAutomationLiveRegion
   {
      public UserControl1()
      {
         InitializeComponent();
      }

      public AutomationLiveSetting AutomationLiveSetting { get; set; }
      private AutomationLiveSetting IAutomationLiveRegion.GetLiveSetting()
      {
         return this.AutomationLiveSetting;
      }

      protected override void OnTextChanged(EventArgs e)
      {
         base.OnTextChanged(e);
         AutomationNotifications.UiaRaiseLiveRegionChangedEvent(this.AccessibilityObject);
      }
   }
}
```

**UIA 通知事件**

Windows 10 Fall Creators Update 中引進了 UIA 通知事件，其可讓您的應用程式引發 UIA 事件，並讓朗讀程式只依據您提供的事件文字來播報，而不需要在 UI 中具備對應的控制項。 在某些情況下，這是大幅改善應用程式協助工具的直接方法。 它也可以用來通知可能需要長時間處理的程序進度。 如需 UIA 通知事件的詳細資訊，請參閱 [Can your desktop app leverage the new UI Notification event?](https://blogs.msdn.microsoft.com/winuiautomation/2017/11/08/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need/) (傳統型應用程式可以利用新的 UI 通知事件嗎？)

下列範例會引發[通知事件](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A)：

```csharp
MethodInfo raiseMethod = typeof(AccessibleObject).GetMethod("RaiseAutomationNotification");
if (raiseMethod != null) {
   raiseMethod.Invoke(progressBar1.AccessibilityObject, new object[3] {/*Other*/ 4, /*All*/ 2, "The progress is 50%." });
}
```

**鍵盤存取的工具提示**

在目標為 .NET Framework 4.7.2 和更早版本的應用程式中，只有將滑鼠指標移到控制項中才會觸發跳出該控制項的[工具提示](xref:System.Windows.Forms.ToolTip)。 從 .NET Framework 4.8 開始，不論有無輔助按鍵，鍵盤使用者均可使用 Tab 鍵或方向鍵把焦點放在控制項上，藉此觸發控制項的工具提示。 這個特定協助工具增強功能需要額外的 [AppContext 參數](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)：

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1"/>
   </startup>
   <runtime>
      <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false  -->
      <!-- Please note that disabling Switch.UseLegacyAccessibilityFeatures, Switch.UseLegacyAccessibilityFeatures.2 and Switch.UseLegacyAccessibilityFeatures.3 is required to disable Switch.System.Windows.Forms.UseLegacyToolTipDisplay -->
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false"/>
   </runtime>
</configuration>
```

下圖顯示當使用者以鍵盤選取按鈕時的工具提示。

![當使用者以鍵盤巡覽至按鈕時的工具提示](media/tooltip.png)

<a name="wpf48" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

從 .NET Framework 4.8 開始，WPF 包含許多協助工具改善。

**螢幕朗讀程式不再播報含摺疊或隱藏可見度的項目**

螢幕朗讀程式不會再播報含摺疊或隱藏可見度的項目。 如果使用者介面包含的項目可見度為 <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> 或 <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType>，則螢幕助讀程式向使用者播報時可能會表達錯誤。 從 .NET Framework 4.8 開始，WPF 的 UIAutomation 樹狀結構控制項檢視中不會再包含摺疊或隱藏項目，因此螢幕助讀程式即無法再播報這些項目。

**搭配使用非 Adorner 文字選取範圍的 SelectionTextBrush 屬性**

在 .NET Framework 4.7.2 中，WPF 新增了繪製 <xref:System.Windows.Controls.TextBox> 和 <xref:System.Windows.Controls.PasswordBox> 文字選取範圍的功能，而不需使用 Adorner 圖層。 在此案例中，選取文字的前景色彩取決於 <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>。

.NET Framework 4.8 新增 `SelectionTextBrush` 屬性，可讓開發人員在使用非 Adorner 文字選取範圍時，針對選取的文字選取特定筆刷。 此屬性僅適用於 WPF 應用程式 (已啟用非 Adorner 文字選取範圍) 中 <xref:System.Windows.Controls.Primitives.TextBoxBase> 衍生的控制項和 <xref:System.Windows.Controls.PasswordBox> 控制項。 此屬性不適用於 <xref:System.Windows.Controls.RichTextBox> 控制項。 如果未啟用非 Adorner 文字選取範圍，則會忽略這個屬性。

若要使用這個屬性，只要將它新增至您的 XAML 程式碼，並使用適當的筆刷或繫結即可。 產生的文字選取範圍看起來像這樣：

![當使用者以鍵盤巡覽至按鈕時的工具提示](media/selectiontextbrush-property.png)

您可以結合 `SelectionBrush` 和 `SelectionTextBrush` 屬性的用法，視需要產生任何背景和前景色彩的組合。

**支援 UIAutomation ControllerFor 屬性**

UIAutomation 的 `ControllerFor` 屬性會傳回自動化項目的陣列，而這些項目是由支援此屬性的自動化項目所操作。 此屬性通常用於自動建議的協助工具。 當自動化項目會影響應用程式 UI 或桌面的一或多個區段時，請使用 `ControllerFor`。 否則，您很難將控制作業的影響與 UI 項目建立關聯。 這項功能讓控制項能夠提供 `ControllerFor` 屬性值。

.NET Framework 4.8 新增新的虛擬方法 <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>。 若要提供 `ControllerFor` 屬性值，只要覆寫這個方法，並傳回控制項 (由此 <xref:System.Windows.Automation.Peers.AutomationPeer> 操作) 的 `List<AutomationPeer>` 即可：

```csharp
public class AutoSuggestTextBox: TextBox
{
   protected override AutomationPeer OnCreateAutomationPeer()
   {
      return new AutoSuggestTextBoxAutomationPeer(this);
   }

   public ListBox SuggestionListBox;
}

internal class AutoSuggestTextBoxAutomationPeer : TextBoxAutomationPeer
{
   public AutoSuggestTextBoxAutomationPeer(AutoSuggestTextBox owner) : base(owner)
   {
   }

   protected override List<AutomationPeer> GetControlledPeersCore()
   {
      List<AutomationPeer> controlledPeers = new List<AutomationPeer>();
      AutoSuggestTextBox owner = Owner as AutoSuggestTextBox;
      controlledPeers.Add(UIElementAutomationPeer.CreatePeerForElement(owner.SuggestionListBox));
      return controlledPeers;
   }
}
```

**鍵盤存取的工具提示**

在 .NET Framework 4.7.2 和更早版本中，只有當使用者將滑鼠游標停留在控制項上方時會顯示工具提示。 在 .NET Framework 4.8 中，工具提示也會在鍵盤焦點上顯示，以及透過鍵盤快速鍵顯示。

若要啟用這項功能，應用程式需要以 .NET Framework 4.8 為目標，或使用 `Switch.UseLegacyAccessibilityFeatures.3` 和 `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 參數選擇加入。 下列是範例應用程式組態檔：

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />
   </startup>
   <runtime>
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.UseLegacyToolTipDisplay=false" />
   </runtime>
</configuration>
```

啟用之後，一旦控制項取得鍵盤焦點時，所有包含工具提示的控制項會都顯示工具提示。 工具提示可能會隨著時間或鍵盤焦點變更而關閉。 使用者也可以使用新的鍵盤快速鍵 Ctrl + Shift + F10，手動關閉工具提示。 工具提示關閉之後，您可以使用相同的鍵盤快速鍵使其再次顯示。

> [!NOTE]
> <xref:System.Windows.Controls.Ribbon.Ribbon> 控制項上的[功能區工具提示](xref:System.Windows.Controls.Ribbon.RibbonToolTip)不會顯示在鍵盤焦點上；而只能透過鍵盤快速鍵顯示。

**新增支援 SizeOfSet 和 PositionInSet UIAutomation 屬性**

Windows 10 引進 `SizeOfSet` 和 `PositionInSet` 這兩個新的 UIAutomation 屬性；應用程式會使用該屬性來描述集合中的項目計數。 UIAutomation 用戶端應用程式 (例如螢幕助讀程式) 可以查詢應用程式的這些屬性，並播報應用程式 UI 的精確呈現。

從 .NET Framework 4.8 開始，WPF 會將這兩個屬性公開至 WPF 應用程式中的 UIAutomation。 這可由下列兩種方法來完成：

- 藉由使用相依性屬性。

  WPF 新增 <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> 和 <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType> 這兩個新的相依性屬性。 開發人員可以使用 XAML 來設定其值：

  ```xaml
  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="1">Button 1</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="2">Button 2</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="3">Button 3</Button>
  ```

- 藉由覆寫 AutomationPeer 虛擬方法。

  AutomationPeer 類別已新增 <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> 和 <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> 虛擬方法。 開發人員可以覆寫這些方法來提供 `SizeOfSet` 和 `PositionInSet` 的值，如下列範例所示：

  ```csharp
  public class MyButtonAutomationPeer : ButtonAutomationPeer
  {
    protected override int GetSizeOfSetCore()
    {
        // Call into your own logic to provide a value for SizeOfSet
        return CalculateSizeOfSet();
    }

    protected override int GetPositionInSetCore()
    {
        // Call into your own logic to provide a value for PositionInSet
        return CalculatePositionInSet();
    }
  }
  ```

此外，<xref:System.Windows.Controls.ItemsControl> 執行個體中的項目可自動提供這些屬性值，而不需要開發人員的額外動作。 如果 <xref:System.Windows.Controls.ItemsControl> 是分組形式，即會以各組來表示群組的集合，並將每個群組計算為個別的一組，而該群組內每個項目均提供其在該群組內的位置及群組大小。 虛擬化不會影響自動值。 即使某個項目未具現化，系統仍會將其計入集合的總大小，並會影響其同層級項目集合的位置。

只有在應用程式的目標為 .NET Framework 4.8 時，系統才會提供自動值。 若是以舊版 .NET Framework 為目標的應用程式，您可以設定 `Switch.UseLegacyAccessibilityFeatures.3` [AppContext 參數](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)，如下列 App.config 檔案中所示：

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />
   </startup>
   <runtime>
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
   </runtime>
</configuration>
```

<a name="wf48" />

### <a name="windows-workflow-foundation-wf-workflow-designer"></a>Windows Workflow Foundation (WF) 工作流程設計工具

工作流程設計工具包括下列各項 .NET Framework 4.8 的變更：

- 使用朗讀程式的使用者會看到 FlowSwitch 案例標籤方面的改善。

- 使用朗讀程式的使用者會看到按鈕描述方面的改善。

- 選擇高對比佈景主題之使用者會看到工作流程設計工具和其控制項在可見度方面的改善，例如項目之間的更佳對比比例，以及用於焦點項目的更明顯選取方塊。

如果應用程式是以 .NET Framework 4.7.2 或更早的版本為目標，您可以將應用程式組態檔中的 `Switch.UseLegacyAccessibilityFeatures.3` [AppContext 參數](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 設為 `false` 來選擇加入這些變更。 如需詳細資訊，請參閱本文的[利用協助工具增強功能](#taking-advantage-of-accessibility-enhancements)一節。

## <a name="whats-new-in-accessibility-in-net-framework-472"></a>.NET Framework 4.7.2 協助工具的新功能

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

從 .NET Framework 4.7.2 開始，朗讀程式支援的增強功能如下：

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

針對 .NET Framework 4.7.1 和舊版中裝載於 WPF 應用程式的 WinForms 控制項，如果 WinForms 層的第一個或最後一個控制項是 WPF <xref:System.Windows.Forms.Integration.ElementHost> 控制項，則使用者無法按 Tab 鍵移出該 WinForms 層。 在 .NET Framework 4.7.2 中，使用者現在能按 Tab 鍵移出 WinForms 層。

不過，依賴焦點絕不會逸出 WinForms 層的自動化應用程式可能不再如預期運作。

## <a name="whats-new-in-accessibility-in-net-framework-471"></a>.NET Framework 4.7.1 協助工具的新功能

.NET Framework 4.7.1 包含下列領域的新協助工具功能：

- [Windows Presentation Foundation (WPF)](#wpf471)

- [Windows Forms](#winforms471)

- [ASP.NET Web 控制項](#aspnet471)

- [.NET SDK 工具](#tools471)

- [Windows Workflow Foundation (WF) 工作流程設計工具](#wf471)

<a name="wpf471"></a>

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**螢幕助讀程式改善**

如果啟用協助工具改善，則 .NET Framework 4.7.1 會包含下列影響螢幕助讀程式的增強功能：

- 在 .NET Framework 4.7 和舊版本中，螢幕助讀程式會將 <xref:System.Windows.Controls.Expander> 控制項宣告為按鈕。 從 .NET Framework 4.7.1 開始，螢幕助讀程式已將它們正確地宣告為可展開/可摺疊的群組。

- 在 .NET Framework 4.7 和舊版本中，螢幕助讀程式會將 <xref:System.Windows.Controls.DataGridCell> 控制項宣告為「自訂」。 從 .NET Framework 4.7.1 開始，螢幕助讀程式現在已將它們正確地宣告為資料格儲存格 (當地語系化)。

- 從 .NET Framework 4.7.1 開始，螢幕助讀程式會宣告可編輯 <xref:System.Windows.Controls.ComboBox> 的名稱。

- 在 .NET Framework 4.7 和舊版本中，螢幕助讀程式會將 <xref:System.Windows.Controls.PasswordBox> 控制項宣告為「檢視中沒有項目」或具有不正確的行為。 從 .NET Framework 4.7.1 開始，已修正此問題。

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

  從 .NET Framework 4.7.1 開始，已停用的 <xref:System.Windows.Controls.ComboBox> 控制項框線色彩與已停用的文字色彩相同。 例如：

  之前： 

  ![協助工具改善之前的 ComboBox 已停用框線和文字](media/combo-disabled-before.png)

  之後：   

  ![協助工具改善之後的 ComboBox 已停用框線和文字](media/combo-disabled-after.png)

  此外，已停用和聚焦按鈕會使用正確的佈景主題色彩。

  之前：

  ![協助工具改善之前的按鈕佈景主題色彩](media/button-themes-before.png) 

  之後： 

  ![協助工具改善之後的按鈕佈景主題色彩](media/button-themes-after.png) 

  最後，在 .NET Framework 4.7 和舊版本中將 <xref:System.Windows.Controls.ComboBox> 控制項的樣式設定為 `Toolbar.ComboBoxStyleKey` 會導致無法看到下拉式箭號。 從 .NET Framework 4.7.1 開始已修正此問題。 例如：

  之前： 

  ![協助工具改善之前的 Toolbar.ComboBoxStyleKey](media/comboboxstylekey-before.png) 

  之後： 

  ![協助工具改善之後的 Toolbar.ComboBoxStyleKey](media/comboboxstylekey-after.png) 

- <xref:System.Windows.Controls.DataGrid> 控制項

  從 .NET Framework 4.7.1 開始，<xref:System.Windows.Controls.DataGrid> 控制項中的排序指標箭號現在會使用正確佈景主題色彩。 例如：

  之前： 

  ![協助工具改善之前的排序指標箭號](media/sort-indicator-before.png) 

  之後：   

  ![協助工具改善之後的排序指標箭號](media/sort-indicator-after.png) 

  此外，在 .NET Framework 4.7 和舊版本的高對比模式中，預設連結樣式會在滑鼠移至上方時變更為不正確的色彩。 從 .NET Framework 4.7.1 開始已解決此問題。 同樣地，從 .NET Framework 4.7.1 開始，<xref:System.Windows.Controls.DataGrid> 核取方塊資料行會使用鍵盤焦點回饋的預期色彩。

  之前： 

  ![協助工具改善之前的 DataGrid 預設連結樣式](media/default-link-style-before.png) 

  之後：    

  ![協助工具改善之後的 DataGrid 預設連結樣式](media/default-link-style-after.png) 

如需 .NET Framework 4.7.1 中的 WPF 協助工具改善詳細資訊；請參閱 [WPF 的協助工具改善](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf)。

<a name="winforms471"></a>

### <a name="windows-forms-accessibility-improvements"></a>Windows Forms 協助工具改善

在 .NET Framework 4.7.1 中，Windows Forms (WinForms) 包含下列領域的協助工具變更。

**高對比模式中改善的顯示**

從 .NET Framework 4.7.1 開始，各種 WinForms 控制項都提供作業系統適用的高對比模式呈現改善。 Windows 10 已變更某些高對比系統色彩的值，而且 Windows Forms 是以 Windows 10 Win32 架構為基礎。 為獲得最佳體驗，請在最新版的 Windows 上執行，並新增最新 OS 變更，方法是在測試應用程式中新增 app.manifest 檔案，並將 Windows 10 支援的 OS 列取消註解，使它看起來如下：

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

從 .NET Framework 4.7.1 開始，協助工具技術工具開發人員可以利用許多 WinForms 控制項的一般 API 協助工具模式和屬性。 這些協助工具改善包含：

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

從 .NET Framework 4.7.1 和 Visual Studio 2017 15.3 開始，ASP.NET 改善 ASP.NET Web 控制項搭配 Visual Studio 協助工具技術的方式。 變更包括下列項目：

- 在控制項中，實作遺漏 UI 協助工具模式的變更，例如在 [詳細資料檢視精靈]  的 [新增欄位]  對話方塊或 [ListView 精靈]  的 [設定 ListView]  對話方塊。

- 改善高對比模式顯示的變更，例如**資料頁面巡覽區欄位編輯器**。

- 改善控制項鍵盤瀏覽體驗的變更，例如 DataPager 控制項 [編輯頁面巡覽區欄位精靈]  的 [欄位]  對話方塊、[設定 ObjectContext]  對話方塊，或 [設定資料來源精靈]  的 [設定資料選取項目]  對話方塊。

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

  - 可透過鍵盤存取 [屬性]  視窗中的 [其他屬性]  按鈕。

  - 鍵盤使用者可以存取工作流程設計工具之 [引數]  和 [變數]  窗格中的標頭項目。

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
