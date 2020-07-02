---
ms.openlocfilehash: e528a41748d9353c96d443f68e15e7a98ee7f4ae
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617797"
---
### <a name="accessibility-improvements-in-windows-forms-controls-for-net-48"></a>已改進 .NET 4.8 之 Windows Forms 控制項的協助工具

#### <a name="details"></a>詳細資料

Windows Forms Framework 利用協助工具技術，持續改善運作方式，可為 Windows Forms 客戶提供更良好的支援。 這些包括下列變更：

- 改善高對比模式期間之顯示方式的變更。
- 對朗讀程式的互動進行了變更。
- 對可存取階層進行了變更 (改善 UI 自動化樹狀的瀏覽)。

#### <a name="suggestion"></a>建議

**如何加入宣告或退出這些變更**為了讓應用程式受益于這些變更，它必須在 .NET Framework 4.8 上執行。 應用程式可以用下列任一種方式選擇使用這些變更：

- 將其重新編譯為以 .NET Framework 4.8 為目標。 在以 .NET Framework 4.8 為目標的 Windows Forms 應用程式上，預設會啟用這些協助工具的變更。
- 其以 .NET Framework 4.7.2 或更早版本為目標，且藉由在應用程式組態檔的 `<runtime>` 區段中新增下列 [AppContext 參數](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element)，並設定為 `false`，選擇不使用舊版協助工具行為，如下範例所示。

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
  </runtime>
</configuration>
```

請注意，選擇使用 .NET Framework 4.8 中新增的協助工具功能時，也必須選擇使用 .NET Framework 4.7.1 和 4.7.2 的協助工具功能。 以 .NET Framework 4.8 為目標，並且想要保留舊版協助工具行為的應用程式，可以藉由明確將此 AppContext 參數設為 `true`，選擇使用舊版的協助工具功能。如需啟用鍵盤工具提示引動過程支援，需要將 `Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false` 行新增至 AppContextSwitchOverrides 值：

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false" />
```

請注意，啟用這項功能需要選擇使用上述 .NET Framework 4.7.1 - 4.8 的協助工具功能。 此外，如果未選擇使用任何協助工具，但選擇使用了工具提示顯示功能，則在第一次存取這些功能時將擲回執行階段 <xref:System.NotSupportedException>。 例外狀況訊息指出鍵盤工具提示需要啟用層級3的協助工具改善。

**使用高對比佈景主題中作業系統定義的色彩**

- 改善的高對比佈景主題。

**已改進朗讀程式支援**

- 朗讀程式現在會在宣布 <xref:System.Windows.Forms.DataGridViewCell> 的可存取名稱時，宣布 <xref:System.Windows.Forms.DataGridViewColumn> 的排序方向。

**改善的 CheckedListBox 協助工具支援**

- 已改善 <xref:System.Windows.Forms.CheckedListBox> 控制項的朗讀程式支援。 使用鍵盤瀏覽至 <xref:System.Windows.Forms.CheckedListBox> 控制項時，朗讀程式會專注於 <xref:System.Windows.Forms.CheckedListBox> 項目並宣布該項目。
- 當控制項變成焦點時，空白 CheckedListBox 控制項現在具有為虛擬第一個項目繪製的焦點矩形。

**改善的 ComboBox 協助工具支援**

- 已啟用 <xref:System.Windows.Forms.ComboBox> 控制項的 UI 自動化支援，並可使用 UI 自動化通知和其他 UI 自動化功能。
**已改進 DataGridView 協助工具支援**

- 已啟用 <xref:System.Windows.Forms.DataGridView> 控制項的 UI 自動化支援，並可使用 UI 自動化通知和其他 UI 自動化功能。
- 對應至 <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl> 或 <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl> 的 UI 自動化項目，現為對應編輯儲存格的子項目。

**改善的 LinkLabel 協助工具支援**

- 改良 <xref:System.Windows.Forms.LinkLabel> 的控制項協助工具：如果停用對應的控制項，朗讀程式會宣佈已停用的連結狀態 <xref:System.Windows.Forms.LinkLabel> 。

**改善的進度列協助工具支援**

- 已啟用 <xref:System.Windows.Forms.ProgressBar> 控制項的 UI 自動化支援，並可使用 UI 自動化通知和其他 UI 自動化功能。 開發人員現在可以使用 UI 自動化通知，朗讀程式可以透過這些通知顯示進度。
如需 UI 自動化事件總覽（包括 UI 自動化通知事件）的總覽，請參閱[Ui 自動化事件總覽](https://docs.microsoft.com/windows/desktop/WinAuto/uiauto-eventsoverview)。

**改良的 PropertyGrid 協助工具支援**

- 已啟用 <xref:System.Windows.Forms.PropertyGrid> 控制項的 UI 自動化支援，並可使用 UI 自動化通知和其他 UI 自動化功能。
- 與當前已編輯屬性對應的 UI 自動化項目，現為對應屬性項目 UI 自動化項目的子項目。
- 如果父 <xref:System.Windows.Forms.PropertyGrid> 控制項設為類別檢視，則 UI 自動化屬性項目項目現為對應類別項目的子項目。

**改善的 ToolStrip 支援**

- 已啟用 <xref:System.Windows.Forms.ToolStrip> 控制項的 UI 自動化支援，並可使用 UI 自動化通知和其他 UI 自動化功能。
- 已改善 <xref:System.Windows.Forms.ToolStrip> 項目的瀏覽。
- 在項目模式中，朗讀程式的焦點未消失，且不會前往隱藏的項目。

**已改進視覺提示**

- 空白 <xref:System.Windows.Forms.CheckedListBox> 控制項現會在收到焦點時顯示焦點指標。
注意：在執行時間中，控制項的 UI 自動化支援已啟用，但不會在設計階段中使用。 如需 UI 自動化的概觀，請參閱 [UI 自動化概觀](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview)。

**使用鍵盤叫用控制項的工具提示**

- 現在可以把焦點放在使用鍵盤控制，叫用控制項工具提示。 應用程式必須明確啟用此功能（請參閱** &quot; 如何加入宣告或退出這些變更 &quot; **一節）

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | 主要       |
| 版本 | 4.8         |
| 類型    | 正在重定目標 |
