---
ms.openlocfilehash: a21824862d6cad046b5d6186f9d6db9c20438304
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606732"
---
### <a name="accessibility-improvements-in-windows-forms-controls-for-net-472"></a><span data-ttu-id="22f75-101">已改進 .NET 4.7.2 之 Windows Forms 控制項的協助工具</span><span class="sxs-lookup"><span data-stu-id="22f75-101">Accessibility improvements in Windows Forms controls for .NET 4.7.2</span></span>

#### <a name="details"></a><span data-ttu-id="22f75-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="22f75-102">Details</span></span>

<span data-ttu-id="22f75-103">Windows Forms Framework 利用了協助工具技術改善其運作方式，可為 Windows Forms 客戶提供更良好的支援。</span><span class="sxs-lookup"><span data-stu-id="22f75-103">Windows Forms Framework is improving how it works with accessibility technologies to better support Windows Forms customers.</span></span> <span data-ttu-id="22f75-104">這些包括下列變更：</span><span class="sxs-lookup"><span data-stu-id="22f75-104">These include the following changes:</span></span>

- <span data-ttu-id="22f75-105">改善高對比模式期間之顯示方式的變更。</span><span class="sxs-lookup"><span data-stu-id="22f75-105">Changes to improve display during High Contrast mode.</span></span>
- <span data-ttu-id="22f75-106">在 DataGridView 與 MenuStrip 控制項中進行了改進鍵盤瀏覽的變更。</span><span class="sxs-lookup"><span data-stu-id="22f75-106">Changes to improve the keyboard navigation in the DataGridView and MenuStrip controls.</span></span>
- <span data-ttu-id="22f75-107">對朗讀程式的互動進行了變更。</span><span class="sxs-lookup"><span data-stu-id="22f75-107">Changes to interaction with Narrator.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="22f75-108">建議</span><span class="sxs-lookup"><span data-stu-id="22f75-108">Suggestion</span></span>

<span data-ttu-id="22f75-109">**如何加入宣告或退出這些變更** 為了讓應用程式受益于這些變更，它必須在 .NET Framework 4.7.2 或更新版本上執行。</span><span class="sxs-lookup"><span data-stu-id="22f75-109">**How to opt in or out of these changes** In order for the application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="22f75-110">應用程式可以用下列任一種方式受益於這些變更：</span><span class="sxs-lookup"><span data-stu-id="22f75-110">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="22f75-111">將其重新編譯為以 .NET Framework 4.7.2 為目標。</span><span class="sxs-lookup"><span data-stu-id="22f75-111">It is recompiled to target the .NET Framework 4.7.2.</span></span> <span data-ttu-id="22f75-112">在以 .NET Framework 4.7.2 或更新版本為目標的 Windows Forms 應用程式上，預設會啟用這些協助工具的變更。</span><span class="sxs-lookup"><span data-stu-id="22f75-112">These accessibility changes are enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="22f75-113">其以 .NET Framework 4.7.1 或更新版本為目標，且藉由在應用程式組態檔的 `<runtime>` 區段中新增下列 [AppContext 參數](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)，並將其設定為 `false`，選擇不使用舊版協助工具行為，如下範例所示。</span><span class="sxs-lookup"><span data-stu-id="22f75-113">It targets the .NET Framework 4.7.1 or earlier version and opts out of the legacy accessibility behaviors by adding the following [AppContext Switch](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the `<runtime>` section of the app config file and setting it to `false`, as the following example shows.</span></span>

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

<span data-ttu-id="22f75-114">請注意，選擇使用 .NET Framework 4.7.2 中新增的協助工具功能時，也必須選擇使用 .NET Framework 4.7.1 的協助工具功能。</span><span class="sxs-lookup"><span data-stu-id="22f75-114">Note that to opt in to the accessibility features added in .NET Framework 4.7.2, you must also opt in to accessibility features of .NET Framework 4.7.1 as well.</span></span> <span data-ttu-id="22f75-115">以 .NET Framework 4.7.2 或更新版本為目標，而且想要保留舊版協助工具行為的應用程式，可以藉由明確地將此 AppCoNtext 參數設定為，選擇使用舊版的協助工具功能 `true` 。</span><span class="sxs-lookup"><span data-stu-id="22f75-115">Applications that target the .NET Framework 4.7.2 or later and want to preserve the legacy accessibility behavior can opt in to the use of legacy accessibility features by explicitly setting this AppContext switch to `true`.</span></span>

<span data-ttu-id="22f75-116">**使用高對比佈景主題中作業系統定義的色彩**</span><span class="sxs-lookup"><span data-stu-id="22f75-116">**Use of OS-defined colors in High Contrast themes**</span></span>

- <span data-ttu-id="22f75-117"><xref:System.Windows.Forms.ToolStripDropDownButton> 的下拉式箭號現在會於高對比佈景主題中使用 OS 所定義的色彩。</span><span class="sxs-lookup"><span data-stu-id="22f75-117">The drop down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> now uses OS-defined colors in High Contrast theme.</span></span>
- <span data-ttu-id="22f75-118">若有選取時，其 <xref:System.Windows.Forms.ButtonBase.FlatStyle> 設定為 <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> 或 <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType> 的 <xref:System.Windows.Forms.Button>、<xref:System.Windows.Forms.RadioButton> 及 <xref:System.Windows.Forms.CheckBox> 控制項，現已會於高對比佈景主題中使用 OS 所定義的色彩。</span><span class="sxs-lookup"><span data-stu-id="22f75-118"><xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType> now use OS-defined colors in High Contrast theme when selected.</span></span> <span data-ttu-id="22f75-119">以往，文字和背景色彩不會呈現對比，因此難以閱讀。</span><span class="sxs-lookup"><span data-stu-id="22f75-119">Previously, text and background colors were not contrasting and were hard to read.</span></span>
- <span data-ttu-id="22f75-120">在 <xref:System.Windows.Forms.GroupBox> 中其 <xref:System.Windows.Forms.Control.Enabled> 屬性設定為 `false` 的控制項，現已會於高對比佈景主題中使用 OS 所定義的色彩。</span><span class="sxs-lookup"><span data-stu-id="22f75-120">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false` will now use OS-defined colors in High Contrast theme.</span></span>
- <span data-ttu-id="22f75-121">控制項 <xref:System.Windows.Forms.ToolStripButton>、<xref:System.Windows.Forms.ToolStripComboBox> 和 <xref:System.Windows.Forms.ToolStripDropDownButton> 在高對比模式下有更高的亮度對比率。</span><span class="sxs-lookup"><span data-stu-id="22f75-121">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls have an increased luminosity contrast ratio in High Contrast Mode.</span></span>
- <span data-ttu-id="22f75-122"><xref:System.Windows.Forms.DataGridViewLinkCell> 預設會為 <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor?displayProperty=nameWithType> 屬性在高對比模式下使用 OS 所定義的色彩。</span><span class="sxs-lookup"><span data-stu-id="22f75-122"><xref:System.Windows.Forms.DataGridViewLinkCell> will by default use OS-defined colors in High Contrast mode for the <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor?displayProperty=nameWithType> property.</span></span>
<span data-ttu-id="22f75-123">注意：Windows 10 已變更某些高對比系統色彩的值。</span><span class="sxs-lookup"><span data-stu-id="22f75-123">NOTE: Windows 10 has changed values for some high contrast system colors.</span></span> <span data-ttu-id="22f75-124">Windows Forms 架構是以 Win32 架構為基礎。</span><span class="sxs-lookup"><span data-stu-id="22f75-124">Windows Forms Framework is based on the Win32 framework.</span></span> <span data-ttu-id="22f75-125">為了獲得最佳體驗，請在最新版本的 Windows 上執行，並藉由在測試應用程式中新增 app.config 檔案並取消批註下列程式碼，加入宣告最新的 OS 變更：</span><span class="sxs-lookup"><span data-stu-id="22f75-125">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-commenting the following code:</span></span>

```xml
<!-- Windows 10 -->
<supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
```

<span data-ttu-id="22f75-126">**已改進朗讀程式支援**</span><span class="sxs-lookup"><span data-stu-id="22f75-126">**Improved Narrator support**</span></span>

- <span data-ttu-id="22f75-127">朗讀程式在播報 <xref:System.Windows.Forms.ToolStripMenuItem> 的文字時，現已會播報 <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType>屬性的值。</span><span class="sxs-lookup"><span data-stu-id="22f75-127">Narrator now announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>
- <span data-ttu-id="22f75-128">當 <xref:System.Windows.Forms.ToolStripMenuItem> 的 <xref:System.Windows.Forms.Control.Enabled> 屬性設定為 `false` 時，朗讀程式現在會指明該情況。</span><span class="sxs-lookup"><span data-stu-id="22f75-128">Narrator now indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>
- <span data-ttu-id="22f75-129">當 <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> 屬性設定為 `true` 時，朗讀程式現已會提供核取方塊狀態的回應。</span><span class="sxs-lookup"><span data-stu-id="22f75-129">Narrator now gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span></span>
- <span data-ttu-id="22f75-130">朗讀程式掃描模式的焦點順序，與 ClickOnce 下載對話視窗中所看見的控制項順序現已一致。</span><span class="sxs-lookup"><span data-stu-id="22f75-130">Narrator Scan Mode focus order is now consistent with the visual order of the controls on the ClickOnce download dialog window.</span></span>

<span data-ttu-id="22f75-131">**已改進 DataGridView 協助工具支援**</span><span class="sxs-lookup"><span data-stu-id="22f75-131">**Improved DataGridView Accessibility support**</span></span>

- <span data-ttu-id="22f75-132"><xref:System.Windows.Forms.DataGridView> 中的資料列現已可使用鍵盤排序。</span><span class="sxs-lookup"><span data-stu-id="22f75-132">Rows in a <xref:System.Windows.Forms.DataGridView> can now be sorted using the keyboard.</span></span> <span data-ttu-id="22f75-133">使用者現已可使用 F3 鍵，依目前的資料行排序。</span><span class="sxs-lookup"><span data-stu-id="22f75-133">Now a user can use the F3 key in order to sort by the current column.</span></span>
- <span data-ttu-id="22f75-134">當 <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> 設定為 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> 時，資料行標頭會變更色彩，以在目前的資料列中指出使用者滑過儲存格時所在的資料行位置。</span><span class="sxs-lookup"><span data-stu-id="22f75-134">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header will change color to indicate the current column as the user tabs through the cells in the current row.</span></span>
- <span data-ttu-id="22f75-135"><xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Parent?displayProperty=nameWithType> 屬性現已會傳回正確的父控制項。</span><span class="sxs-lookup"><span data-stu-id="22f75-135">The <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Parent?displayProperty=nameWithType> property now returns the correct parent control.</span></span>

<span data-ttu-id="22f75-136">**已改進視覺提示**</span><span class="sxs-lookup"><span data-stu-id="22f75-136">**Improved Visual cues**</span></span>

- <span data-ttu-id="22f75-137"><xref:System.Windows.Forms.ButtonBase.Text> 屬性為空白的控制項 <xref:System.Windows.Forms.RadioButton> 與 <xref:System.Windows.Forms.CheckBox>，現已會於接收到焦點時顯示焦點指標。</span><span class="sxs-lookup"><span data-stu-id="22f75-137">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property will now display a focus indicator when they receive focus.</span></span>

<span data-ttu-id="22f75-138">**已改進屬性方格支援**</span><span class="sxs-lookup"><span data-stu-id="22f75-138">**Improved Property Grid Support**</span></span>

- <span data-ttu-id="22f75-139"><xref:System.Windows.Forms.PropertyGrid> 控制項子項目現在只有在已啟用 PropertyGrid 項目的情況下，才會傳回 <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> 屬性的 `true`。</span><span class="sxs-lookup"><span data-stu-id="22f75-139">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span></span>
- <span data-ttu-id="22f75-140"><xref:System.Windows.Forms.PropertyGrid> 控制項子項目現在只有在使用者可變更 PropertyGrid 項目的情況下，才會傳回 <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> 屬性的 `false`。</span><span class="sxs-lookup"><span data-stu-id="22f75-140">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span></span>
<span data-ttu-id="22f75-141">如需 UI 自動化的概觀，請參閱 [UI 自動化概觀](../../../../docs/framework/ui-automation/ui-automation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="22f75-141">For an overview of UI automation, see the [UI Automation Overview](../../../../docs/framework/ui-automation/ui-automation-overview.md).</span></span></p><span data-ttu-id="22f75-142">**改善的鍵盤導覽**</span><span class="sxs-lookup"><span data-stu-id="22f75-142">**Improved keyboard navigation**</span></span>

- <span data-ttu-id="22f75-143"><xref:System.Windows.Forms.ToolStripButton> 當包含在 <xref:System.Windows.Forms.ToolStripPanel> <xref:System.Windows.Forms.ToolStripPanel.TabStop> 屬性設為的的中時，現在允許焦點 `true` 。</span><span class="sxs-lookup"><span data-stu-id="22f75-143"><xref:System.Windows.Forms.ToolStripButton> now allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`.</span></span>

| <span data-ttu-id="22f75-144">名稱</span><span class="sxs-lookup"><span data-stu-id="22f75-144">Name</span></span>    | <span data-ttu-id="22f75-145">值</span><span class="sxs-lookup"><span data-stu-id="22f75-145">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="22f75-146">範圍</span><span class="sxs-lookup"><span data-stu-id="22f75-146">Scope</span></span>   | <span data-ttu-id="22f75-147">主要</span><span class="sxs-lookup"><span data-stu-id="22f75-147">Major</span></span>       |
| <span data-ttu-id="22f75-148">版本</span><span class="sxs-lookup"><span data-stu-id="22f75-148">Version</span></span> | <span data-ttu-id="22f75-149">4.7.2</span><span class="sxs-lookup"><span data-stu-id="22f75-149">4.7.2</span></span>       |
| <span data-ttu-id="22f75-150">類型</span><span class="sxs-lookup"><span data-stu-id="22f75-150">Type</span></span>    | <span data-ttu-id="22f75-151">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="22f75-151">Retargeting</span></span> |
