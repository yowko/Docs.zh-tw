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
ms.openlocfilehash: e9b9d1c8a059a85f2b5137e568ec6ad562ca0eb9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680291"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="3f028-102">.NET Framework 協助工具的新功能</span><span class="sxs-lookup"><span data-stu-id="3f028-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="3f028-103">.NET Framework 的目標在於讓使用者更容易存取應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f028-103">The .NET Framework aims at making applications more accessible for your users.</span></span> <span data-ttu-id="3f028-104">協助工具功能可讓應用程式提供適當的輔助技術使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="3f028-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="3f028-105">從 .NET Framework 4.7.1 開始，.NET Framework 包含大量協助工具改善，可讓開發人員建立可存取的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f028-105">Starting with the .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span> 

## <a name="accessibility-switches"></a><span data-ttu-id="3f028-106">協助工具參數</span><span class="sxs-lookup"><span data-stu-id="3f028-106">Accessibility switches</span></span>

<span data-ttu-id="3f028-107">您可以設定您的應用程式，以選擇加入協助工具功能，如果它以 .NET Framework 4.7 或較早版本為目標但是在 .NET Framework 4.7.1 或更新版本上執行的話。</span><span class="sxs-lookup"><span data-stu-id="3f028-107">You can configure your app to opt into accessibility features if it targets the .NET Framework 4.7 or an earlier version but is running on the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="3f028-108">您也可以設定應用程式以使用舊版的功能 (且不利用協助工具功能)，如果它以 .NET Framework 4.7.1 或更新版本為目標的話。</span><span class="sxs-lookup"><span data-stu-id="3f028-108">You can also configure your app to use legacy features (and not take advantage of accessibility features) if it targets the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="3f028-109">包含協助工具功能的每個 .NET Framework 版本都有版本特定的協助工具參數，您可以新增到應用程式組態檔 [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) 區段中的 [`<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 項目。</span><span class="sxs-lookup"><span data-stu-id="3f028-109">Each version of the .NET Framework that includes accessibility features has a version-specific accessibility switch, which you add to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> <span data-ttu-id="3f028-110">以下是支援的參數：</span><span class="sxs-lookup"><span data-stu-id="3f028-110">The following are the supported switches:</span></span>

|<span data-ttu-id="3f028-111">版本</span><span class="sxs-lookup"><span data-stu-id="3f028-111">Version</span></span>|<span data-ttu-id="3f028-112">參數</span><span class="sxs-lookup"><span data-stu-id="3f028-112">Switch</span></span>|
|---|---|
|<span data-ttu-id="3f028-113">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="3f028-113">.NET Framework 4.7.1</span></span>|<span data-ttu-id="3f028-114">"Switch.UseLegacyAccessibilityFeatures"</span><span class="sxs-lookup"><span data-stu-id="3f028-114">"Switch.UseLegacyAccessibilityFeatures"</span></span>|
|<span data-ttu-id="3f028-115">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="3f028-115">.NET Framework 4.7.2</span></span>|<span data-ttu-id="3f028-116">"Switch.UseLegacyAccessibilityFeatures.2"</span><span class="sxs-lookup"><span data-stu-id="3f028-116">"Switch.UseLegacyAccessibilityFeatures.2"</span></span>|

### <a name="taking-advantage-of-accessibility-enhancements"></a><span data-ttu-id="3f028-117">利用協助工具增強功能</span><span class="sxs-lookup"><span data-stu-id="3f028-117">Taking advantage of accessibility enhancements</span></span>

<span data-ttu-id="3f028-118">針對以 .NET Framework 4.7.1 或更新版本為目標的應用程式，預設會啟用新的協助工具功能。</span><span class="sxs-lookup"><span data-stu-id="3f028-118">The new accessibility features are enabled by default for applications that target the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="3f028-119">此外，以舊版 .NET Framework 為目標但在 .NET Framework 4.7.1 或更新版本上執行的應用程式可以退出舊版協助工具行為 (進而利用協助工具增強功能)，方法是新增參數至應用程式組態檔之 [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) 區段中的 [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 項目，並將其值設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="3f028-119">In addition, applications that target an earlier version of the .NET Framework but are running on the .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby take advantage of accessibility improvements) by adding switches to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `false`.</span></span> <span data-ttu-id="3f028-120">以下顯示如何加入 .NET Framework 4.7.1 中引進的協助工具增強功能：</span><span class="sxs-lookup"><span data-stu-id="3f028-120">The following shows how to opt in to accessibility enhancements introduced in the .NET Framework 4.7.1:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="3f028-121">如果您選擇加入 .NET Framework 較新版本中的協助工具功能，您必須同時明確加入來自舊版 .NET Framework 的功能。</span><span class="sxs-lookup"><span data-stu-id="3f028-121">If you choose to opt in to accessibility features in a later version of the .NET Framework, you must also explicitly opt in to the features from earlier versions of the .NET Framework.</span></span> <span data-ttu-id="3f028-122">設定您的應用程式以同時利用 .NET Framework 4.7.1 和 4.7.2 的協助工具改善功能，需要下列 [`<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 項目：</span><span class="sxs-lookup"><span data-stu-id="3f028-122">Configuring your app to take advantage of accessibility improvements in both the .NET Framework 4.7.1 and 4.7.2 requires the following [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a><span data-ttu-id="3f028-123">還原舊版行為</span><span class="sxs-lookup"><span data-stu-id="3f028-123">Restoring legacy behavior</span></span>

<span data-ttu-id="3f028-124">以從 4.7.1 開始的 .NET Framework 版本為目標的應用程式，可以停用協助工具功能，方法是新增參數至應用程式組態檔之 [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) 區段中的 [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 項目，並將其值設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="3f028-124">Applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding switches to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `true`.</span></span> <span data-ttu-id="3f028-125">例如，下列組態會選擇退出 .NET Framework 4.7.2 中引進的協助工具功能：</span><span class="sxs-lookup"><span data-stu-id="3f028-125">For example, the following configuration opts out of accessibility features introduced in .NET Framework 4.7.2:</span></span>  

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-472"></a><span data-ttu-id="3f028-126">.NET Framework 4.7.2 協助工具的新功能</span><span class="sxs-lookup"><span data-stu-id="3f028-126">What's new in accessibility in the .NET Framework 4.7.2</span></span>

<span data-ttu-id="3f028-127">.NET Framework 4.7.2 包含下列領域的新協助工具功能：</span><span class="sxs-lookup"><span data-stu-id="3f028-127">The .NET Framework 4.7.2 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="3f028-128">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3f028-128">Windows Forms</span></span>](#winforms472)

- [<span data-ttu-id="3f028-129">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="3f028-129">Windows Presentation Foundation (WPF)</span></span>](#wpf472)

<a name="winforms472"></a>
### <a name="windows-forms"></a><span data-ttu-id="3f028-130">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3f028-130">Windows Forms</span></span>

<span data-ttu-id="3f028-131">**高對比佈景主題中的作業系統定義色彩**</span><span class="sxs-lookup"><span data-stu-id="3f028-131">**OS-defined colors in High Contrast themes**</span></span>

<span data-ttu-id="3f028-132">從 .NET Framework 4.7.2 開始，Windows Forms 在高對比佈景主題中使用作業系統所定義的色彩。</span><span class="sxs-lookup"><span data-stu-id="3f028-132">Starting with .NET Framework 4.7.2, Windows Forms uses colors defined by the operating system in High Contrast themes.</span></span> <span data-ttu-id="3f028-133">這會影響下列控制項：</span><span class="sxs-lookup"><span data-stu-id="3f028-133">This affects the following controls:</span></span>

- <span data-ttu-id="3f028-134"><xref:System.Windows.Forms.ToolStripDropDownButton> 控制項的下拉式箭號。</span><span class="sxs-lookup"><span data-stu-id="3f028-134">The drop-down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> control.</span></span>

- <span data-ttu-id="3f028-135"><xref:System.Windows.Forms.ButtonBase.FlatStyle> 設成 <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> 或 <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType> 的 <xref:System.Windows.Forms.Button>、<xref:System.Windows.Forms.RadioButton> 和 <xref:System.Windows.Forms.CheckBox>。</span><span class="sxs-lookup"><span data-stu-id="3f028-135">The <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3f028-136">以往，選取的文字和背景色彩不會呈現對比，因此難以閱讀。</span><span class="sxs-lookup"><span data-stu-id="3f028-136">Previously, selected text and background colors were not contrasting and were hard to read.</span></span>

- <span data-ttu-id="3f028-137">包含在 <xref:System.Windows.Forms.GroupBox> 內的控制項，且其 <xref:System.Windows.Forms.Control.Enabled> 屬性設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="3f028-137">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>
 
- <span data-ttu-id="3f028-138"><xref:System.Windows.Forms.ToolStripButton>、<xref:System.Windows.Forms.ToolStripComboBox> 和 <xref:System.Windows.Forms.ToolStripDropDownButton> 控制項，它們在高對比模式下有更高的亮度對比率。</span><span class="sxs-lookup"><span data-stu-id="3f028-138">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls, which have an increased luminosity contrast ratio in High Contrast Mode.</span></span>

- <span data-ttu-id="3f028-139"><xref:System.Windows.Forms.DataGridViewLinkCell> 的 <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> 屬性。</span><span class="sxs-lookup"><span data-stu-id="3f028-139">The <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> property of the <xref:System.Windows.Forms.DataGridViewLinkCell>.</span></span>

<span data-ttu-id="3f028-140">**朗讀程式增強功能**</span><span class="sxs-lookup"><span data-stu-id="3f028-140">**Narrator improvements**</span></span>

<span data-ttu-id="3f028-141">從 .NET Framework 4.7.2 開始，朗讀程式的支援增強功能如下：</span><span class="sxs-lookup"><span data-stu-id="3f028-141">Starting with the .NET Framework 4.7.2, Narrator support is enhanced as follows:</span></span>

- <span data-ttu-id="3f028-142">在播報 <xref:System.Windows.Forms.ToolStripMenuItem> 的文字時，現已會播報 <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="3f028-142">It announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span> 

- <span data-ttu-id="3f028-143">當 <xref:System.Windows.Forms.ToolStripMenuItem> 的 <xref:System.Windows.Forms.Control.Enabled> 屬性設定為 `false` 時，會指明該情況。</span><span class="sxs-lookup"><span data-stu-id="3f028-143">It indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="3f028-144">當 <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> 屬性設定為 `true` 時，會提供核取方塊狀態的回應。</span><span class="sxs-lookup"><span data-stu-id="3f028-144">It gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span></span>

- <span data-ttu-id="3f028-145">朗讀程式掃描模式的焦點順序，與 ClickOnce 下載對話視窗中所看見的控制項順序已一致。</span><span class="sxs-lookup"><span data-stu-id="3f028-145">Narrator's Scan Mode focus order is consistent with the visual order of the controls on the ClickOnce download dialog window.</span></span>

<span data-ttu-id="3f028-146">**DataGridView 改善**</span><span class="sxs-lookup"><span data-stu-id="3f028-146">**DataGridView improvements**</span></span>

<span data-ttu-id="3f028-147">從 .NET Framework 4.7.2 開始，<xref:System.Windows.Forms.DataGridView> 控制項已經引進下列協助工具改善：</span><span class="sxs-lookup"><span data-stu-id="3f028-147">Starting with the .NET Framework 4.7.2, the <xref:System.Windows.Forms.DataGridView> control has introduced the following accessibility improvements:</span></span>

- <span data-ttu-id="3f028-148">資料列可使用鍵盤排序。</span><span class="sxs-lookup"><span data-stu-id="3f028-148">Rows can be sorted using the keyboard.</span></span> <span data-ttu-id="3f028-149">使用者可使用 F3 鍵，依目前的資料行排序。</span><span class="sxs-lookup"><span data-stu-id="3f028-149">A user can use the F3 key in order to sort by the current column.</span></span>

- <span data-ttu-id="3f028-150">當 <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> 設定為 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> 時，資料行標頭會變更色彩，以在目前的資料列中指出使用者滑過儲存格時所在的資料行位置。</span><span class="sxs-lookup"><span data-stu-id="3f028-150">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header changes color to indicate the current column as the user tabs through the cells in the current row.</span></span>

- <span data-ttu-id="3f028-151"><xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> 的 <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> 屬性會傳回正確的父控制項。</span><span class="sxs-lookup"><span data-stu-id="3f028-151">The <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> property of a  <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> returns the correct parent control.</span></span>

<span data-ttu-id="3f028-152">**改善的視覺提示**</span><span class="sxs-lookup"><span data-stu-id="3f028-152">**Improved visual cues**</span></span>

- <span data-ttu-id="3f028-153"><xref:System.Windows.Forms.ButtonBase.Text> 屬性為空白的控制項 <xref:System.Windows.Forms.RadioButton> 與 <xref:System.Windows.Forms.CheckBox>，會於接收到焦點時顯示焦點指標。</span><span class="sxs-lookup"><span data-stu-id="3f028-153">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property  display a focus indicator when they receive the focus.</span></span>

<span data-ttu-id="3f028-154">**已改進屬性方格支援**</span><span class="sxs-lookup"><span data-stu-id="3f028-154">**Improved Property Grid Support**</span></span>

- <span data-ttu-id="3f028-155"><xref:System.Windows.Forms.PropertyGrid> 控制項子項目現在只有在已啟用 PropertyGrid 項目的情況下，才會傳回 <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> 屬性的 `true`。</span><span class="sxs-lookup"><span data-stu-id="3f028-155">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span></span>

- <span data-ttu-id="3f028-156"><xref:System.Windows.Forms.PropertyGrid> 控制項子項目只有在使用者可變更 PropertyGrid 項目的情況下，才會傳回 <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> 屬性的 `false`。</span><span class="sxs-lookup"><span data-stu-id="3f028-156">The <xref:System.Windows.Forms.PropertyGrid> control child elements return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span></span>

<span data-ttu-id="3f028-157">**改善的鍵盤導覽**</span><span class="sxs-lookup"><span data-stu-id="3f028-157">**Improved keyboard navigation**</span></span>

- <span data-ttu-id="3f028-158"><xref:System.Windows.Forms.ToolStripPanel.TabStop> 屬性設定為 `true` 的 <xref:System.Windows.Forms.ToolStripPanel> 內含焦點時，<xref:System.Windows.Forms.ToolStripButton> 控制項允許焦點</span><span class="sxs-lookup"><span data-stu-id="3f028-158">The <xref:System.Windows.Forms.ToolStripButton> control allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`</span></span>

<a name="wpf472"></a>
### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="3f028-159">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="3f028-159">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="3f028-160">**CheckBox 和 RadioButton 控制項的變更**</span><span class="sxs-lookup"><span data-stu-id="3f028-160">**Changes to the CheckBox and RadioButton controls**</span></span>

<span data-ttu-id="3f028-161">在 .NET Framework 4.7.1 和舊版的傳統和高對比佈景主題中，WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> 和 <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> 控制項的焦點視覺效果不一致且不正確。</span><span class="sxs-lookup"><span data-stu-id="3f028-161">In the .NET Framework 4.7.1 and earlier versions, the WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> controls have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="3f028-162">當控制項沒有任何內容集時，會發生上述問題。</span><span class="sxs-lookup"><span data-stu-id="3f028-162">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="3f028-163">這可能會讓人混淆佈景主題之間的轉換，也看不清楚焦點視覺效果。</span><span class="sxs-lookup"><span data-stu-id="3f028-163">This can make the transition between themes confusing and the focus visual hard to see.</span></span>

<span data-ttu-id="3f028-164">現在，.NET Framework 4.7.2 的這些視覺效果在各佈景主題之間會更一致；在傳統和高對比佈景主題中也可以看得更清楚。</span><span class="sxs-lookup"><span data-stu-id="3f028-164">In the .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

<span data-ttu-id="3f028-165">**裝載於 WPF 應用程式的 WinForms 控制項**</span><span class="sxs-lookup"><span data-stu-id="3f028-165">**WinForms controls hosted in a WPF application**</span></span>

<span data-ttu-id="3f028-166">對於 .NET Framework 4.7.1 和舊版中，裝載於 WPF 應用程式的 WinForms 控制項，使用者無法按 Tab 鍵移出 WinForms 層，如果該層的第一個或最後一個控制項是 WPF <xref:System.Windows.Forms.Integration.ElementHost> 控制項。</span><span class="sxs-lookup"><span data-stu-id="3f028-166">For WinForms control hosted in a WPF application in the .NET Framework 4.7.1 and earlier versions, users couldn't tab out of the WinForms layer if the first or last control in that layer is the WPF <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span> <span data-ttu-id="3f028-167">在 .NET Framework 4.7.2 中，使用者現在能按 Tab 鍵移出 WinForms 層。</span><span class="sxs-lookup"><span data-stu-id="3f028-167">In the .NET Framework 4.7.2, users are now able to tab out of the WinForms layer.</span></span>

<span data-ttu-id="3f028-168">不過，依賴焦點絕不會逸出 WinForms 層的自動化應用程式可能不再如預期運作。</span><span class="sxs-lookup"><span data-stu-id="3f028-168">However, automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a><span data-ttu-id="3f028-169">.NET Framework 4.7.1 協助工具的新功能</span><span class="sxs-lookup"><span data-stu-id="3f028-169">What's new in accessibility in the .NET Framework 4.7.1</span></span>

<span data-ttu-id="3f028-170">.NET Framework 4.7.1 包含下列領域的新協助工具功能：</span><span class="sxs-lookup"><span data-stu-id="3f028-170">The .NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="3f028-171">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="3f028-171">Windows Presentation Foundation (WPF)</span></span>](#wpf471)

- [<span data-ttu-id="3f028-172">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3f028-172">Windows Forms</span></span>](#winforms471)

- [<span data-ttu-id="3f028-173">ASP.NET Web 控制項</span><span class="sxs-lookup"><span data-stu-id="3f028-173">ASP.NET web controls</span></span>](#aspnet471)

- [<span data-ttu-id="3f028-174">.NET SDK 工具</span><span class="sxs-lookup"><span data-stu-id="3f028-174">.NET SDK Tools</span></span>](#tools471)

- [<span data-ttu-id="3f028-175">Windows Workflow Foundation (WF) 工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="3f028-175">Windows Workflow Foundation (WF) Workflow Designer</span></span>](#wf471)

<a name="wpf471"></a>
### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="3f028-176">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="3f028-176">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="3f028-177">**螢幕助讀程式改善**</span><span class="sxs-lookup"><span data-stu-id="3f028-177">**Screen reader improvements**</span></span>

<span data-ttu-id="3f028-178">如果啟用協助工具改善，則 .NET Framework 4.7.1 會包含下列影響螢幕助讀程式的改善：</span><span class="sxs-lookup"><span data-stu-id="3f028-178">If accessibility improvements are enabled, the .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="3f028-179">在 .NET Framework 4.7 和舊版本中，螢幕助讀程式已將 <xref:System.Windows.Controls.Expander> 控制項公告為按鈕。</span><span class="sxs-lookup"><span data-stu-id="3f028-179">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="3f028-180">從 .NET Framework 4.7.1 開始，已將它們正確地宣告為可展開/可摺疊的群組。</span><span class="sxs-lookup"><span data-stu-id="3f028-180">Starting with the .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="3f028-181">在 .NET Framework 4.7 和舊版本中，螢幕助讀程式已將 <xref:System.Windows.Controls.DataGridCell> 控制項宣告為「自訂」。</span><span class="sxs-lookup"><span data-stu-id="3f028-181">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="3f028-182">從 .NET Framework 4.7.1 開始，現在已將它們正確地宣告為資料格 (已當地語系化)。</span><span class="sxs-lookup"><span data-stu-id="3f028-182">Starting with the .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>
 
- <span data-ttu-id="3f028-183">從 .NET Framework 4.7.1 開始，螢幕助讀程式會宣告可編輯 <xref:System.Windows.Controls.ComboBox> 的名稱。</span><span class="sxs-lookup"><span data-stu-id="3f028-183">Starting with the .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="3f028-184">在 .NET Framework 4.7 和舊版本中，<xref:System.Windows.Controls.PasswordBox> 控制項已宣告為「檢視中沒有項目」或具有不正確的行為。</span><span class="sxs-lookup"><span data-stu-id="3f028-184">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="3f028-185">從 .NET Framework 4.7.1 開始，已修正此問題。</span><span class="sxs-lookup"><span data-stu-id="3f028-185">This issue is fixed starting with the .NET Framework 4.7.1.</span></span>

<span data-ttu-id="3f028-186">**UIAutomation LiveRegion 支援**</span><span class="sxs-lookup"><span data-stu-id="3f028-186">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="3f028-187">朗讀程式這類螢幕助讀程式可協助人員讀取應用程式 UI 內容，通常是透過具有焦點之 UI 內容的文字轉換語音輸出。</span><span class="sxs-lookup"><span data-stu-id="3f028-187">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="3f028-188">不過，如果 UI 項目變更，而且沒有焦點，則使用者可能不會收到通知，並可能遺失重要資訊。</span><span class="sxs-lookup"><span data-stu-id="3f028-188">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="3f028-189">即時區域的目標在解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="3f028-189">Live regions aim at solving this problem.</span></span> <span data-ttu-id="3f028-190">開發人員可以使用它們來通知螢幕助讀程式或任何其他 UIAutomation 用戶端，已對 UI 項目進行重要變更。</span><span class="sxs-lookup"><span data-stu-id="3f028-190">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="3f028-191">螢幕助讀程式接著可以決定如何和何時通知使用者已進行這項變更。</span><span class="sxs-lookup"><span data-stu-id="3f028-191">The screen reader can then decide how and when to inform the user of this change.</span></span> 

<span data-ttu-id="3f028-192">為了支援即時區域，已將下列 API 新增至 WPF：</span><span class="sxs-lookup"><span data-stu-id="3f028-192">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="3f028-193"><xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> 和 <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> 欄位，可識別 **LiveSetting** 屬性和 **LiveRegionChanged** 事件。</span><span class="sxs-lookup"><span data-stu-id="3f028-193">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="3f028-194">它們可以使用 XAML 進行設定。</span><span class="sxs-lookup"><span data-stu-id="3f028-194">They can be set by using XAML.</span></span>

- <span data-ttu-id="3f028-195">**AutomationProperties.LiveSetting** 附加屬性，可通知螢幕助讀程式有關 UI 變更對使用者的重要性。</span><span class="sxs-lookup"><span data-stu-id="3f028-195">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="3f028-196"><xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> 屬性，可識別 **AutomationProperties.LiveSetting** 附加屬性。</span><span class="sxs-lookup"><span data-stu-id="3f028-196">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>
 
- <span data-ttu-id="3f028-197"><xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> 方法，可以覆寫以提供 **LiveSetting** 值。</span><span class="sxs-lookup"><span data-stu-id="3f028-197">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="3f028-198"><xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> 和 <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> 方法，可以取得和設定 **LiveSetting** 值。</span><span class="sxs-lookup"><span data-stu-id="3f028-198">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>
 
- <span data-ttu-id="3f028-199"><xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> 列舉，可以定義下列可能的 **LiveSetting** 值：</span><span class="sxs-lookup"><span data-stu-id="3f028-199">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

   - <span data-ttu-id="3f028-200"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3f028-200"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3f028-201">如果即時區域的內容變更，項目不會傳送通知。</span><span class="sxs-lookup"><span data-stu-id="3f028-201">The element does not send notifications if the content of the live region has changed.</span></span>   
   - <span data-ttu-id="3f028-202"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3f028-202"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3f028-203">如果即時區域的內容變更，項目會傳送不中斷通知。</span><span class="sxs-lookup"><span data-stu-id="3f028-203">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>   

  - <span data-ttu-id="3f028-204"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3f028-204"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3f028-205">如果即時區域的內容變更，項目會傳送中斷通知。</span><span class="sxs-lookup"><span data-stu-id="3f028-205">The element sends interruptive notifications if the content of the live region has changed.</span></span>   

<span data-ttu-id="3f028-206">您可以在感興趣的項目上設定 **AutomationProperties.LiveSetting** 屬性，以建立 LiveRegion，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="3f028-206">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="3f028-207">如果即時區域中的資料變更，而且您需要通知螢幕助讀程式，請明確地引發事件，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="3f028-207">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="3f028-208">**高對比**</span><span class="sxs-lookup"><span data-stu-id="3f028-208">**High contrast**</span></span>

<span data-ttu-id="3f028-209">從 .NET Framework 4.7.1 開始，已對各種 WPF 控制項進行高對比改善。</span><span class="sxs-lookup"><span data-stu-id="3f028-209">Starting with the .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="3f028-210">現在，設定 <xref:System.Windows.SystemParameters.HighContrast%2A> 佈景主題時，可以看到它們。</span><span class="sxs-lookup"><span data-stu-id="3f028-210">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="3f028-211">它們包括：</span><span class="sxs-lookup"><span data-stu-id="3f028-211">These include:</span></span>

- <span data-ttu-id="3f028-212"><xref:System.Windows.Controls.Expander> 控制項</span><span class="sxs-lookup"><span data-stu-id="3f028-212"><xref:System.Windows.Controls.Expander> control</span></span>

    <span data-ttu-id="3f028-213">現在會顯示 <xref:System.Windows.Controls.Expander> 控制項的焦點視覺效果。</span><span class="sxs-lookup"><span data-stu-id="3f028-213">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="3f028-214">現在也會顯示 <xref:System.Windows.Controls.ComboBox>、<xref:System.Windows.Controls.ListBox> 和 <xref:System.Windows.Controls.RadioButton> 控制項的鍵盤視覺效果。</span><span class="sxs-lookup"><span data-stu-id="3f028-214">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="3f028-215">例如：</span><span class="sxs-lookup"><span data-stu-id="3f028-215">For example:</span></span>

    <span data-ttu-id="3f028-216">之前：</span><span class="sxs-lookup"><span data-stu-id="3f028-216">Before:</span></span> 
    
    ![協助工具改善之前的聚焦 Expander 控制項](media/expander-before.png)

    <span data-ttu-id="3f028-218">之後：</span><span class="sxs-lookup"><span data-stu-id="3f028-218">After:</span></span> 

    ![協助工具改善之後的聚焦 Expander 控制項](media/expander-after.png)

- <span data-ttu-id="3f028-220"><xref:System.Windows.Controls.CheckBox> 和 <xref:System.Windows.Controls.RadioButton> 控制項</span><span class="sxs-lookup"><span data-stu-id="3f028-220"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>
 
    <span data-ttu-id="3f028-221">在高對比佈景主題中選取時，<xref:System.Windows.Controls.CheckBox> 和 <xref:System.Windows.Controls.RadioButton> 控制項中的文字現在更容易出現。</span><span class="sxs-lookup"><span data-stu-id="3f028-221">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="3f028-222">例如：</span><span class="sxs-lookup"><span data-stu-id="3f028-222">For example:</span></span>

    <span data-ttu-id="3f028-223">之前：</span><span class="sxs-lookup"><span data-stu-id="3f028-223">Before:</span></span> 

    ![協助工具改善之前的聚焦高對比選項按鈕](media/radio-button-before.png)
    
    <span data-ttu-id="3f028-225">之後：</span><span class="sxs-lookup"><span data-stu-id="3f028-225">After:</span></span> 

    ![協助工具改善之後的聚焦高對比選項按鈕](media/radio-button-after.png)

- <span data-ttu-id="3f028-227"><xref:System.Windows.Controls.ComboBox> 控制項</span><span class="sxs-lookup"><span data-stu-id="3f028-227"><xref:System.Windows.Controls.ComboBox> control</span></span>
 
    <span data-ttu-id="3f028-228">從 .NET Framework 4.7.1 開始，已停用 <xref:System.Windows.Controls.ComboBox> 控制項的框線色彩與已停用文字的色彩相同。</span><span class="sxs-lookup"><span data-stu-id="3f028-228">Starting with the .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="3f028-229">例如：</span><span class="sxs-lookup"><span data-stu-id="3f028-229">For example:</span></span>
    
    <span data-ttu-id="3f028-230">之前：</span><span class="sxs-lookup"><span data-stu-id="3f028-230">Before:</span></span> 

     ![協助工具改善之前的 ComboBox 已停用框線和文字](media/combo-disabled-before.png)

    <span data-ttu-id="3f028-232">之後：</span><span class="sxs-lookup"><span data-stu-id="3f028-232">After:</span></span>   

     ![協助工具改善之後的 ComboBox 已停用框線和文字](media/combo-disabled-after.png)

    <span data-ttu-id="3f028-234">此外，已停用和聚焦按鈕會使用正確的佈景主題色彩。</span><span class="sxs-lookup"><span data-stu-id="3f028-234">In addition, disabled and focused buttons use the correct theme color.</span></span>

    <span data-ttu-id="3f028-235">之前：</span><span class="sxs-lookup"><span data-stu-id="3f028-235">Before:</span></span>

    ![協助工具改善之前的按鈕佈景主題色彩](media/button-themes-before.png) 
    
    <span data-ttu-id="3f028-237">之後：</span><span class="sxs-lookup"><span data-stu-id="3f028-237">After:</span></span> 

    ![協助工具改善之後的按鈕佈景主題色彩](media/button-themes-after.png) 

    <span data-ttu-id="3f028-239">最後，在 .NET Framework 4.7 和舊版本中，將 <xref:System.Windows.Controls.ComboBox> 控制項的樣式設定為 `Toolbar.ComboBoxStyleKey` 已導致下拉式箭號不可見。</span><span class="sxs-lookup"><span data-stu-id="3f028-239">Finally, in the .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="3f028-240">從 .NET Framework 4.7.1 開始，已修正此問題。</span><span class="sxs-lookup"><span data-stu-id="3f028-240">This issue is fixed starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="3f028-241">例如：</span><span class="sxs-lookup"><span data-stu-id="3f028-241">For example:</span></span>

    <span data-ttu-id="3f028-242">之前：</span><span class="sxs-lookup"><span data-stu-id="3f028-242">Before:</span></span> 

    ![協助工具改善之前的 Toolbar.ComboBoxStyleKey](media/comboboxstylekey-before.png) 
    
    <span data-ttu-id="3f028-244">之後：</span><span class="sxs-lookup"><span data-stu-id="3f028-244">After:</span></span> 

    ![協助工具改善之後的 Toolbar.ComboBoxStyleKey](media/comboboxstylekey-after.png) 

- <span data-ttu-id="3f028-246"><xref:System.Windows.Controls.DataGrid> 控制項</span><span class="sxs-lookup"><span data-stu-id="3f028-246"><xref:System.Windows.Controls.DataGrid> control</span></span>

    <span data-ttu-id="3f028-247">從 .NET Framework 4.7.1 開始，<xref:System.Windows.Controls.DataGrid> 控制項中的排序指標箭號現在會使用正確的佈景主題色彩。</span><span class="sxs-lookup"><span data-stu-id="3f028-247">Starting with the .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="3f028-248">例如：</span><span class="sxs-lookup"><span data-stu-id="3f028-248">For example:</span></span>

    <span data-ttu-id="3f028-249">之前：</span><span class="sxs-lookup"><span data-stu-id="3f028-249">Before:</span></span> 

    ![協助工具改善之前的排序指標箭號](media/sort-indicator-before.png) 
    
    <span data-ttu-id="3f028-251">之後：</span><span class="sxs-lookup"><span data-stu-id="3f028-251">After:</span></span>   
 
    ![協助工具改善之後的排序指標箭號](media/sort-indicator-after.png) 
    
    <span data-ttu-id="3f028-253">此外，在 .NET Framework 4.7 和舊版本中，高對比模式中滑鼠移至上方的預設連結樣式已變更為不正確的色彩。</span><span class="sxs-lookup"><span data-stu-id="3f028-253">In addition, in the .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="3f028-254">從 .NET Framework 4.7.1 開始，已解決此問題。</span><span class="sxs-lookup"><span data-stu-id="3f028-254">This is resolved starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="3f028-255">同樣地，從 .NET Framework 4.7.1 開始，<xref:System.Windows.Controls.DataGrid> 核取方塊資料行會使用鍵盤焦點回饋的預期色彩。</span><span class="sxs-lookup"><span data-stu-id="3f028-255">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with the .NET Framework 4.7.1.</span></span>

    <span data-ttu-id="3f028-256">之前：</span><span class="sxs-lookup"><span data-stu-id="3f028-256">Before:</span></span> 

    ![協助工具改善之前的 DataGrid 預設連結樣式](media/default-link-style-before.png) 
 
    <span data-ttu-id="3f028-258">之後：</span><span class="sxs-lookup"><span data-stu-id="3f028-258">After:</span></span>    
  
    ![協助工具改善之後的 DataGrid 預設連結樣式](media/default-link-style-after.png)  

<span data-ttu-id="3f028-260">如需 .NET Framework 4.7.1 中 WPF 協助工具改善的詳細資訊；請參閱 [WPF 中的協助工具改善](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf)。</span><span class="sxs-lookup"><span data-stu-id="3f028-260">For more information on WPF accessibility improvements in the .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

<a name="winforms471"></a>
## <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="3f028-261">Windows Forms 協助工具改善</span><span class="sxs-lookup"><span data-stu-id="3f028-261">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="3f028-262">在 .NET Framework 4.7.1 中，Windows Forms (WinForms) 包含下列領域的協助工具變更。</span><span class="sxs-lookup"><span data-stu-id="3f028-262">In the .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="3f028-263">**高對比模式中改善的顯示**</span><span class="sxs-lookup"><span data-stu-id="3f028-263">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="3f028-264">從 .NET Framework 4.7.1 開始，各種 WinForms 控制項都提供作業系統中所提供高對比模式的呈現改善。</span><span class="sxs-lookup"><span data-stu-id="3f028-264">Starting with the .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="3f028-265">Windows 10 已變更某些高對比系統色彩的值，而且 Windows Forms 是以 Windows 10 Win32 架構為基礎。</span><span class="sxs-lookup"><span data-stu-id="3f028-265">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="3f028-266">為獲得最佳體驗，請在最新版的 Windows 上執行，並新增最新 OS 變更，方法是在測試應用程式中新增 app.manifest 檔案，並將 Windows 10 支援的 OS 列取消註解，使它看起來如下：</span><span class="sxs-lookup"><span data-stu-id="3f028-266">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!-- Windows 10 -->
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
<span data-ttu-id="3f028-267">一些高對比變更範例包含：</span><span class="sxs-lookup"><span data-stu-id="3f028-267">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="3f028-268"><xref:System.Windows.Forms.MenuStrip> 項目中的核取記號較容易檢視。</span><span class="sxs-lookup"><span data-stu-id="3f028-268">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="3f028-269">選取時，已停用 <xref:System.Windows.Forms.MenuStrip> 項目較容易檢視。</span><span class="sxs-lookup"><span data-stu-id="3f028-269">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="3f028-270">所選取 <xref:System.Windows.Forms.Button> 控制項中的文字會與選取色彩成對比。</span><span class="sxs-lookup"><span data-stu-id="3f028-270">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="3f028-271">已停用的文字較容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="3f028-271">Disabled text is easier to read.</span></span> <span data-ttu-id="3f028-272">例如：</span><span class="sxs-lookup"><span data-stu-id="3f028-272">For example:</span></span>

    <span data-ttu-id="3f028-273">之前：</span><span class="sxs-lookup"><span data-stu-id="3f028-273">Before:</span></span>

    ![協助工具改善之前的已停用文字](media/wf-disabled-before.png) 

    <span data-ttu-id="3f028-275">之後：</span><span class="sxs-lookup"><span data-stu-id="3f028-275">After:</span></span>

    ![協助工具改善之後的已停用文字](media/wf-disabled-after.png) 

- <span data-ttu-id="3f028-277">執行緒例外狀況對話方塊中的高對比改善。</span><span class="sxs-lookup"><span data-stu-id="3f028-277">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="3f028-278">**改善的朗讀程式支援**</span><span class="sxs-lookup"><span data-stu-id="3f028-278">**Improved Narrator support**</span></span>

<span data-ttu-id="3f028-279">.NET Framework 4.7.1 中的 Windows Forms 包含朗讀程式的下列協助工具改善：</span><span class="sxs-lookup"><span data-stu-id="3f028-279">Windows Forms in the .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="3f028-280">朗讀程式和其他 UI 自動化工具可以存取 <xref:System.Windows.Forms.MonthCalendar> 控制項。</span><span class="sxs-lookup"><span data-stu-id="3f028-280">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="3f028-281"><xref:System.Windows.Forms.CheckedListBox> 控制項會在項目的核取狀態已經變更，因而通知使用者它們已變更清單項目值時通知 [朗讀程式]。</span><span class="sxs-lookup"><span data-stu-id="3f028-281">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>
 
- <span data-ttu-id="3f028-282"><xref:System.Windows.Forms.DataGridViewCell> 控制項會向朗讀程式報告正確的唯讀狀態。</span><span class="sxs-lookup"><span data-stu-id="3f028-282">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>
 
- <span data-ttu-id="3f028-283">朗讀程式現在可以讀取已停用 <xref:System.Windows.Forms.ToolStripMenuItem> 文字，而之前它會略過已停用的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="3f028-283">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="3f028-284">**UIAutomation 協助工具模式的增強支援**</span><span class="sxs-lookup"><span data-stu-id="3f028-284">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="3f028-285">從 .NET Framework 4.7.1 開始，協助工具技術工具開發人員可以利用數個 WinForms 控制項的一般 API 協助工具模式和屬性。</span><span class="sxs-lookup"><span data-stu-id="3f028-285">Starting with the .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="3f028-286">這些協助工具改善包含：</span><span class="sxs-lookup"><span data-stu-id="3f028-286">These accessibility improvements include:</span></span>

- <span data-ttu-id="3f028-287"><xref:System.Windows.Forms.ComboBox> 和 <xref:System.Windows.Forms.ToolStripSplitButton> 現在支援[展開/摺疊模式](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="3f028-287">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>
 
- <span data-ttu-id="3f028-288"><xref:System.Windows.Forms.DataGridViewCheckBoxCell> 現在支援[切換模式](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="3f028-288">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>
 
- <span data-ttu-id="3f028-289"><xref:System.Windows.Forms.ToolStripItem> 控制項支援 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> 屬性和[展開/摺疊模式](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="3f028-289">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="3f028-290"><xref:System.Windows.Forms.NumericUpDown> 和 <xref:System.Windows.Forms.DomainUpDown> 控制項支援 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> 屬性。</span><span class="sxs-lookup"><span data-stu-id="3f028-290">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="3f028-291">**改善的屬性瀏覽器體驗**</span><span class="sxs-lookup"><span data-stu-id="3f028-291">**Improved property browser experience**</span></span>

<span data-ttu-id="3f028-292">從 .NET Framework 4.7.1 開始，Windows Forms 包含：</span><span class="sxs-lookup"><span data-stu-id="3f028-292">Starting with the .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="3f028-293">透過各種下拉式選取視窗進行更佳的鍵盤導覽。</span><span class="sxs-lookup"><span data-stu-id="3f028-293">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="3f028-294">減少不必要的定位停駐點。</span><span class="sxs-lookup"><span data-stu-id="3f028-294">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="3f028-295">更適當地報告控制項類型。</span><span class="sxs-lookup"><span data-stu-id="3f028-295">Better reporting of control types.</span></span>
- <span data-ttu-id="3f028-296">改善的朗讀程式行為。</span><span class="sxs-lookup"><span data-stu-id="3f028-296">Improved narrator behavior.</span></span>
 
<a name="aspnet471"></a>
## <a name="aspnet-web-controls"></a><span data-ttu-id="3f028-297">ASP.NET Web 控制項</span><span class="sxs-lookup"><span data-stu-id="3f028-297">ASP.NET web controls</span></span>

<span data-ttu-id="3f028-298">從 .NET Framework 4.7.1 和 Visual Studio 2017 15.3 開始，ASP.NET 已經改善 ASP.NET Web 控制項如何搭配 Visual Studio 中的協助工具技術。</span><span class="sxs-lookup"><span data-stu-id="3f028-298">Starting with the .NET Framework 4.7.1 and Visual Studio 2017 15.3, ASP.NET improves how ASP.NET web controls work with accessibility technology in Visual Studio.</span></span> <span data-ttu-id="3f028-299">變更包括下列項目：</span><span class="sxs-lookup"><span data-stu-id="3f028-299">Changes include the following:</span></span>

- <span data-ttu-id="3f028-300">在控制項中，實作遺漏 UI 協助工具模式的變更，例如在 [詳細資料檢視精靈] 的 [新增欄位] 對話方塊或 [ListView 精靈] 的 [設定 ListView] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3f028-300">Changes to implement missing UI accessibility patterns in controls, like the **Add Field** dialog in the **Details View** wizard, or the **Configure ListView** dialog of the **ListView** wizard.</span></span>

- <span data-ttu-id="3f028-301">改善高對比模式顯示的變更，例如**資料頁面巡覽區欄位編輯器**。</span><span class="sxs-lookup"><span data-stu-id="3f028-301">Changes to improve the display in High Contrast mode, like the **Data Pager Fields Editor**.</span></span>

- <span data-ttu-id="3f028-302">改善控制項鍵盤瀏覽體驗的變更，例如 DataPager 控制項 [編輯頁面巡覽區欄位精靈] 的 [欄位] 對話方塊、[設定 ObjectContext] 對話方塊，或 [設定資料來源精靈] 的 [設定資料選取項目] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3f028-302">Changes to improve the keyboard navigation experiences for controls, like the **Fields** dialog in the **Edit Pager Fields** wizard of the DataPager control, the **Configure ObjectContext** dialog, or the **Configure Data Selection** dialog of the **Configure Data Source** wizard.</span></span>

<a name="tools471"></a>
## <a name="net-sdk-tools"></a><span data-ttu-id="3f028-303">.NET SDK 工具</span><span class="sxs-lookup"><span data-stu-id="3f028-303">.NET SDK Tools</span></span>

<span data-ttu-id="3f028-304">[組態編輯器工具 (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) 和[服務追蹤檢視器工具 (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) 藉由修正各種協助工具問題來改善。</span><span class="sxs-lookup"><span data-stu-id="3f028-304">The [Configuration Editor Tool (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) and [Service Trace Viewer Tool (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="3f028-305">其中大部分是小問題，例如未定義名稱，或未正確實作某些 UI 自動化模式。</span><span class="sxs-lookup"><span data-stu-id="3f028-305">Most of these were small issues, like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="3f028-306">雖然許多使用者並未注意到這些不正確的值，但使用螢幕助讀程式等輔助技術的客戶會發現這些 SDK 工具更易於存取。</span><span class="sxs-lookup"><span data-stu-id="3f028-306">While many users won’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span> 

<span data-ttu-id="3f028-307">這些增強功能變更一些先前的行為，例如鍵盤焦點的順序。</span><span class="sxs-lookup"><span data-stu-id="3f028-307">These enhancements change some previous behaviors, such as keyboard focus order.</span></span>

<a name="wf471"></a>
## <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="3f028-308">Windows Workflow Foundation (WF) 工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="3f028-308">Windows Workflow Foundation (WF) Workflow Designer</span></span>

<span data-ttu-id="3f028-309">在工作流程設計工具中的協助工具變更包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="3f028-309">Accessibility changes in the Workflow Designer include the following:</span></span>

- <span data-ttu-id="3f028-310">在某些控制項中，定位順序變更為由左至右及由上至下：</span><span class="sxs-lookup"><span data-stu-id="3f028-310">The tab order changes to left to right and top to bottom in some controls:</span></span>

  - <span data-ttu-id="3f028-311">設定 <xref:System.ServiceModel.Activities.InitializeCorrelation> 活動之關聯性資料的初始化關聯性視窗。</span><span class="sxs-lookup"><span data-stu-id="3f028-311">The initialize correlation window for setting correlation data for the <xref:System.ServiceModel.Activities.InitializeCorrelation> activity.</span></span>

  - <span data-ttu-id="3f028-312"><xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.SendReply> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 活動的內容定義視窗。</span><span class="sxs-lookup"><span data-stu-id="3f028-312">The content definition window for the <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply> activities.</span></span>

- <span data-ttu-id="3f028-313">可透過鍵盤使用多個功能：</span><span class="sxs-lookup"><span data-stu-id="3f028-313">More functions are available via the keyboard:</span></span>

  - <span data-ttu-id="3f028-314">編輯活動的屬性時，如果第一次將焦點放在屬性群組，可以透過鍵盤將其摺疊。</span><span class="sxs-lookup"><span data-stu-id="3f028-314">When editing the properties of an activity, property groups can be collapsed by keyboard the first time they are focused.</span></span>

  - <span data-ttu-id="3f028-315">可透過鍵盤存取警告圖示。</span><span class="sxs-lookup"><span data-stu-id="3f028-315">Warning icons are accessible by keyboard.</span></span>

  - <span data-ttu-id="3f028-316">可透過鍵盤存取 [屬性] 視窗中的 [其他屬性] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3f028-316">The **More Properties** button in the **Properties** window is accessible by keyboard.</span></span>

  - <span data-ttu-id="3f028-317">鍵盤使用者可以存取工作流程設計工具之 [引數] 和 [變數] 窗格中的標頭項目。</span><span class="sxs-lookup"><span data-stu-id="3f028-317">Keyboard users can access the header items in the **Arguments** and **Variables** panes of the Workflow Designer.</span></span>

- <span data-ttu-id="3f028-318">在以下這類情況發生時，已改善具有焦點之項目的可見性：</span><span class="sxs-lookup"><span data-stu-id="3f028-318">Improved visibility of items with focus, such as when:</span></span>

  - <span data-ttu-id="3f028-319">在工作流程設計工具與活動設計工具所使用的資料格中新增資料列。</span><span class="sxs-lookup"><span data-stu-id="3f028-319">Adding rows to data grids used by the Workflow Designer and activity designers.</span></span>

  - <span data-ttu-id="3f028-320">使用 Tab 鍵循環顯示 <xref:System.ServiceModel.Activities.ReceiveReply> 和 <xref:System.ServiceModel.Activities.SendReply> 活動的欄位。</span><span class="sxs-lookup"><span data-stu-id="3f028-320">Tabbing through fields in the <xref:System.ServiceModel.Activities.ReceiveReply> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>

  - <span data-ttu-id="3f028-321">設定變數或引數的預設值</span><span class="sxs-lookup"><span data-stu-id="3f028-321">Setting default values for variables or arguments</span></span>

- <span data-ttu-id="3f028-322">螢幕助讀程式現在可以正確辨識：</span><span class="sxs-lookup"><span data-stu-id="3f028-322">Screen readers can now correctly recognize:</span></span>

  - <span data-ttu-id="3f028-323">工作流程設計工具中設定的中斷點。</span><span class="sxs-lookup"><span data-stu-id="3f028-323">Breakpoints set in the workflow designer.</span></span>

  - <span data-ttu-id="3f028-324"><xref:System.Activities.Statements.FlowSwitch%601>、<xref:System.Activities.Statements.FlowDecision> 和 <xref:System.ServiceModel.Activities.CorrelationScope> 活動。</span><span class="sxs-lookup"><span data-stu-id="3f028-324">The <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, and <xref:System.ServiceModel.Activities.CorrelationScope> activities.</span></span>
  - <span data-ttu-id="3f028-325"><xref:System.ServiceModel.Activities.Receive> 活動的內容。</span><span class="sxs-lookup"><span data-stu-id="3f028-325">The contents of the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

  - <span data-ttu-id="3f028-326"><xref:System.Activities.Statements.InvokeMethod> 活動的目標類型。</span><span class="sxs-lookup"><span data-stu-id="3f028-326">The Target Type for the <xref:System.Activities.Statements.InvokeMethod> activity.</span></span>

  - <span data-ttu-id="3f028-327"><xref:System.Activities.Statements.TryCatch> 活動中的例外狀況下拉式方塊和 Finally 區段。</span><span class="sxs-lookup"><span data-stu-id="3f028-327">The Exception combo box and the Finally section in the <xref:System.Activities.Statements.TryCatch> activity.</span></span>

  - <span data-ttu-id="3f028-328">傳訊活動 (<xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.SendReply> 和 <xref:System.ServiceModel.Activities.ReceiveReply>) 中的 [訊息類型] 下拉式方塊、[新增關聯性初始設定式] 視窗、[內容定義] 視窗和 [CorrelatesOn 定義] 視窗。</span><span class="sxs-lookup"><span data-stu-id="3f028-328">The Message Type combo box, the splitter in the Add Correlation Initializers window, the Content Definition window, and the CorrelatesOn Definition window in the messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>

  - <span data-ttu-id="3f028-329">狀態機器轉換和轉換目的地。</span><span class="sxs-lookup"><span data-stu-id="3f028-329">State machine transitions and transitions destinations.</span></span>

  - <span data-ttu-id="3f028-330"><xref:System.Activities.Statements.FlowDecision> 活動的註釋和連接器。</span><span class="sxs-lookup"><span data-stu-id="3f028-330">Annotations and connectors on <xref:System.Activities.Statements.FlowDecision> activities.</span></span>

  - <span data-ttu-id="3f028-331">活動的操作 (右鍵) 功能表。</span><span class="sxs-lookup"><span data-stu-id="3f028-331">The context (right-click) menus for activities.</span></span>

  - <span data-ttu-id="3f028-332">屬性方格中的屬性值編輯器、[清除搜尋] 按鈕、[依分類] 及 [字母順序] 排序按鈕和 [運算式編輯器] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3f028-332">The property value editors, the Clear Search button, the By Category and Alphabetical sort buttons, and the Expression Editor dialog in the properties grid.</span></span>

  - <span data-ttu-id="3f028-333">工作流程設計工具中的顯示比例百分比。</span><span class="sxs-lookup"><span data-stu-id="3f028-333">The zoom percentage in the Workflow Designer.</span></span>

  - <span data-ttu-id="3f028-334"><xref:System.Activities.Statements.Parallel> 和 <xref:System.Activities.Statements.Pick> 活動中的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="3f028-334">The separator in <xref:System.Activities.Statements.Parallel> and <xref:System.Activities.Statements.Pick> activities.</span></span>

  - <span data-ttu-id="3f028-335"><xref:System.Activities.Statements.InvokeDelegate> 活動。</span><span class="sxs-lookup"><span data-stu-id="3f028-335">The <xref:System.Activities.Statements.InvokeDelegate> activity.</span></span>

  - <span data-ttu-id="3f028-336">字典活動 (`Microsoft.Activities.AddToDictionary<TKey,TValue>`、`Microsoft.Activities.RemoveFromDictionary<TKey,TValue>` 等) 的 [選取類型] 視窗。</span><span class="sxs-lookup"><span data-stu-id="3f028-336">The Select Types window for dictionary activities (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, etc.).</span></span>

  - <span data-ttu-id="3f028-337">[瀏覽並選取 .NET 類型] 視窗。</span><span class="sxs-lookup"><span data-stu-id="3f028-337">The Browse and Select .NET Type window.</span></span>

  - <span data-ttu-id="3f028-338">工作流程設計工具中的階層連結。</span><span class="sxs-lookup"><span data-stu-id="3f028-338">Breadcrumbs in the Workflow Designer.</span></span>

- <span data-ttu-id="3f028-339">選擇高對比佈景主題的使用者會看到工作流程設計工具和其控制項在可見性方面的許多改善，例如項目之間的更佳對比比例以及用於焦點項目的更明顯選取方塊。</span><span class="sxs-lookup"><span data-stu-id="3f028-339">Users who choose High Contrast themes will see many improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="3f028-340">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f028-340">See also</span></span>

- [<span data-ttu-id="3f028-341">.NET Framework 的新功能</span><span class="sxs-lookup"><span data-stu-id="3f028-341">What's new in the .NET Framework</span></span>](whats-new.md)

