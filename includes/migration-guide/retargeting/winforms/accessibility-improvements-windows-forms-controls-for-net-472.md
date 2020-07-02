---
ms.openlocfilehash: cc3c2c2be179842f87be8892d057a6c4138086cb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614397"
---
### <a name="accessibility-improvements-in-windows-forms-controls-for-net-472"></a>已改進 .NET 4.7.2 之 Windows Forms 控制項的協助工具

#### <a name="details"></a>詳細資料

Windows Forms Framework 利用了協助工具技術改善其運作方式，可為 Windows Forms 客戶提供更良好的支援。 這些包括下列變更：

- 改善高對比模式期間之顯示方式的變更。
- 在 DataGridView 與 MenuStrip 控制項中進行了改進鍵盤瀏覽的變更。
- 對朗讀程式的互動進行了變更。

#### <a name="suggestion"></a>建議

**如何加入宣告或退出這些變更**為了讓應用程式受益于這些變更，它必須在 .NET Framework 4.7.2 或更新版本上執行。 應用程式可以用下列任一種方式受益於這些變更：

- 將其重新編譯為以 .NET Framework 4.7.2 為目標。 在以 .NET Framework 4.7.2 或更新版本為目標的 Windows Forms 應用程式上，預設會啟用這些協助工具的變更。
- 其以 .NET Framework 4.7.1 或更新版本為目標，且藉由在應用程式組態檔的 `<runtime>` 區段中新增下列 [AppContext 參數](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element)，並將其設定為 `false`，選擇不使用舊版協助工具行為，如下範例所示。

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
  </runtime>
</configuration>
```

請注意，選擇使用 .NET Framework 4.7.2 中新增的協助工具功能時，也必須選擇使用 .NET Framework 4.7.1 的協助工具功能。 以 .NET Framework 4.7.2 或更新版本為目標，而且想要保留舊版協助工具行為的應用程式，可以藉由明確地將此 AppCoNtext 參數設定為，選擇使用舊版協助工具功能 `true` 。

**使用高對比佈景主題中作業系統定義的色彩**

- <xref:System.Windows.Forms.ToolStripDropDownButton> 的下拉式箭號現在會於高對比佈景主題中使用 OS 所定義的色彩。
- 若有選取時，其 <xref:System.Windows.Forms.ButtonBase.FlatStyle> 設定為 <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> 或 <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType> 的 <xref:System.Windows.Forms.Button>、<xref:System.Windows.Forms.RadioButton> 及 <xref:System.Windows.Forms.CheckBox> 控制項，現已會於高對比佈景主題中使用 OS 所定義的色彩。 以往，文字和背景色彩不會呈現對比，因此難以閱讀。
- 在 <xref:System.Windows.Forms.GroupBox> 中其 <xref:System.Windows.Forms.Control.Enabled> 屬性設定為 `false` 的控制項，現已會於高對比佈景主題中使用 OS 所定義的色彩。
- 控制項 <xref:System.Windows.Forms.ToolStripButton>、<xref:System.Windows.Forms.ToolStripComboBox> 和 <xref:System.Windows.Forms.ToolStripDropDownButton> 在高對比模式下有更高的亮度對比率。
- <xref:System.Windows.Forms.DataGridViewLinkCell> 預設會為 <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor?displayProperty=nameWithType> 屬性在高對比模式下使用 OS 所定義的色彩。
注意：Windows 10 已變更某些高對比系統色彩的值。 Windows Forms 架構是以 Win32 架構為基礎。 若要獲得最佳體驗，請在最新版本的 Windows 上執行，並在測試應用程式中新增 app.config 檔案並取消批註下列程式碼，以加入宣告最新的 OS 變更：

```xml
<!-- Windows 10 -->
<supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
```

**已改進朗讀程式支援**

- 朗讀程式在播報 <xref:System.Windows.Forms.ToolStripMenuItem> 的文字時，現已會播報 <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType>屬性的值。
- 當 <xref:System.Windows.Forms.ToolStripMenuItem> 的 <xref:System.Windows.Forms.Control.Enabled> 屬性設定為 `false` 時，朗讀程式現在會指明該情況。
- 當 <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> 屬性設定為 `true` 時，朗讀程式現已會提供核取方塊狀態的回應。
- 朗讀程式掃描模式的焦點順序，與 ClickOnce 下載對話視窗中所看見的控制項順序現已一致。

**已改進 DataGridView 協助工具支援**

- <xref:System.Windows.Forms.DataGridView> 中的資料列現已可使用鍵盤排序。 使用者現已可使用 F3 鍵，依目前的資料行排序。
- 當 <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> 設定為 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> 時，資料行標頭會變更色彩，以在目前的資料列中指出使用者滑過儲存格時所在的資料行位置。
- <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Parent?displayProperty=nameWithType> 屬性現已會傳回正確的父控制項。

**已改進視覺提示**

- <xref:System.Windows.Forms.ButtonBase.Text> 屬性為空白的控制項 <xref:System.Windows.Forms.RadioButton> 與 <xref:System.Windows.Forms.CheckBox>，現已會於接收到焦點時顯示焦點指標。

**已改進屬性方格支援**

- <xref:System.Windows.Forms.PropertyGrid> 控制項子項目現在只有在已啟用 PropertyGrid 項目的情況下，才會傳回 <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> 屬性的 `true`。
- <xref:System.Windows.Forms.PropertyGrid> 控制項子項目現在只有在使用者可變更 PropertyGrid 項目的情況下，才會傳回 <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> 屬性的 `false`。
如需 UI 自動化的概觀，請參閱 [UI 自動化概觀](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview)。</p>**改善的鍵盤導覽**

- <xref:System.Windows.Forms.ToolStripButton>當包含在的 <xref:System.Windows.Forms.ToolStripPanel> <xref:System.Windows.Forms.ToolStripPanel.TabStop> 屬性設定為時，現在允許焦點 `true` 。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | 主要       |
| 版本 | 4.7.2       |
| 類型    | 正在重定目標 |
