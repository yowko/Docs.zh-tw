---
ms.openlocfilehash: e528a41748d9353c96d443f68e15e7a98ee7f4ae
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617797"
---
### <a name="accessibility-improvements-in-windows-forms-controls-for-net-48"></a><span data-ttu-id="b4dc0-101">已改進 .NET 4.8 之 Windows Forms 控制項的協助工具</span><span class="sxs-lookup"><span data-stu-id="b4dc0-101">Accessibility improvements in Windows Forms controls for .NET 4.8</span></span>

#### <a name="details"></a><span data-ttu-id="b4dc0-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b4dc0-102">Details</span></span>

<span data-ttu-id="b4dc0-103">Windows Forms Framework 利用協助工具技術，持續改善運作方式，可為 Windows Forms 客戶提供更良好的支援。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-103">The Windows Forms Framework is continuing to improve how it works with accessibility technologies to better support Windows Forms customers.</span></span> <span data-ttu-id="b4dc0-104">這些包括下列變更：</span><span class="sxs-lookup"><span data-stu-id="b4dc0-104">These include the following changes:</span></span>

- <span data-ttu-id="b4dc0-105">改善高對比模式期間之顯示方式的變更。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-105">Changes to improve display during High Contrast mode.</span></span>
- <span data-ttu-id="b4dc0-106">對朗讀程式的互動進行了變更。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-106">Changes to interaction with Narrator.</span></span>
- <span data-ttu-id="b4dc0-107">對可存取階層進行了變更 (改善 UI 自動化樹狀的瀏覽)。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-107">Changes in the Accessible hierarchy (improving navigation through the UI Automation tree).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b4dc0-108">建議</span><span class="sxs-lookup"><span data-stu-id="b4dc0-108">Suggestion</span></span>

<span data-ttu-id="b4dc0-109">**如何加入宣告或退出這些變更**為了讓應用程式受益于這些變更，它必須在 .NET Framework 4.8 上執行。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-109">**How to opt in or out of these changes** In order for the application to benefit from these changes, it must run on the .NET Framework 4.8.</span></span> <span data-ttu-id="b4dc0-110">應用程式可以用下列任一種方式選擇使用這些變更：</span><span class="sxs-lookup"><span data-stu-id="b4dc0-110">The application can opt in into these changes in either of the following ways:</span></span>

- <span data-ttu-id="b4dc0-111">將其重新編譯為以 .NET Framework 4.8 為目標。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-111">It is recompiled to target the .NET Framework 4.8.</span></span> <span data-ttu-id="b4dc0-112">在以 .NET Framework 4.8 為目標的 Windows Forms 應用程式上，預設會啟用這些協助工具的變更。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-112">These accessibility changes are enabled by default on Windows Forms applications that target the .NET Framework 4.8.</span></span>
- <span data-ttu-id="b4dc0-113">其以 .NET Framework 4.7.2 或更早版本為目標，且藉由在應用程式組態檔的 `<runtime>` 區段中新增下列 [AppContext 參數](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element)，並設定為 `false`，選擇不使用舊版協助工具行為，如下範例所示。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-113">It targets the .NET Framework 4.7.2 or earlier version and opts out of the legacy accessibility behaviors by adding the following [AppContext switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the `<runtime>` section of the app config file and setting it to `false`, as the following example shows.</span></span>

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

<span data-ttu-id="b4dc0-114">請注意，選擇使用 .NET Framework 4.8 中新增的協助工具功能時，也必須選擇使用 .NET Framework 4.7.1 和 4.7.2 的協助工具功能。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-114">Note that to opt in to the accessibility features added in .NET Framework 4.8, you must also opt in to accessibility features of .NET Framework 4.7.1 and 4.7.2 as well.</span></span> <span data-ttu-id="b4dc0-115">以 .NET Framework 4.8 為目標，並且想要保留舊版協助工具行為的應用程式，可以藉由明確將此 AppContext 參數設為 `true`，選擇使用舊版的協助工具功能。如需啟用鍵盤工具提示引動過程支援，需要將 `Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false` 行新增至 AppContextSwitchOverrides 值：</span><span class="sxs-lookup"><span data-stu-id="b4dc0-115">Applications that target the .NET Framework 4.8 and want to preserve the legacy accessibility behavior can opt in to the use of legacy accessibility features by explicitly setting this AppContext switch to `true`.Enabling the keyboard ToolTip invocation support requires adding the `Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false` line to the AppContextSwitchOverrides value:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false" />
```

<span data-ttu-id="b4dc0-116">請注意，啟用這項功能需要選擇使用上述 .NET Framework 4.7.1 - 4.8 的協助工具功能。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-116">Note that enabling this feature requires opting in to the aforementioned accessibility features of .NET Framework 4.7.1 - 4.8.</span></span> <span data-ttu-id="b4dc0-117">此外，如果未選擇使用任何協助工具，但選擇使用了工具提示顯示功能，則在第一次存取這些功能時將擲回執行階段 <xref:System.NotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-117">Also, if any of the accessibility features are not opted in but the tooltip display feature is opted in, a runtime <xref:System.NotSupportedException> will be thrown on the first access to these features.</span></span> <span data-ttu-id="b4dc0-118">例外狀況訊息指出鍵盤工具提示需要啟用層級3的協助工具改善。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-118">The exception message indicates that keyboard ToolTips require accessibility improvements of level 3 to be enabled.</span></span>

<span data-ttu-id="b4dc0-119">**使用高對比佈景主題中作業系統定義的色彩**</span><span class="sxs-lookup"><span data-stu-id="b4dc0-119">**Use of OS-defined colors in High Contrast themes**</span></span>

- <span data-ttu-id="b4dc0-120">改善的高對比佈景主題。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-120">Improved high-contrast themes.</span></span>

<span data-ttu-id="b4dc0-121">**已改進朗讀程式支援**</span><span class="sxs-lookup"><span data-stu-id="b4dc0-121">**Improved Narrator support**</span></span>

- <span data-ttu-id="b4dc0-122">朗讀程式現在會在宣布 <xref:System.Windows.Forms.DataGridViewCell> 的可存取名稱時，宣布 <xref:System.Windows.Forms.DataGridViewColumn> 的排序方向。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-122">Narrator now announces the sort direction of the <xref:System.Windows.Forms.DataGridViewColumn> when announcing an accessible name of a <xref:System.Windows.Forms.DataGridViewCell>.</span></span>

<span data-ttu-id="b4dc0-123">**改善的 CheckedListBox 協助工具支援**</span><span class="sxs-lookup"><span data-stu-id="b4dc0-123">**Improved CheckedListBox Accessibility support**</span></span>

- <span data-ttu-id="b4dc0-124">已改善 <xref:System.Windows.Forms.CheckedListBox> 控制項的朗讀程式支援。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-124">Improved Narrator support for the <xref:System.Windows.Forms.CheckedListBox> control.</span></span> <span data-ttu-id="b4dc0-125">使用鍵盤瀏覽至 <xref:System.Windows.Forms.CheckedListBox> 控制項時，朗讀程式會專注於 <xref:System.Windows.Forms.CheckedListBox> 項目並宣布該項目。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-125">When navigating to the <xref:System.Windows.Forms.CheckedListBox> control using the keyboard, Narrator focuses the <xref:System.Windows.Forms.CheckedListBox> item and announces it.</span></span>
- <span data-ttu-id="b4dc0-126">當控制項變成焦點時，空白 CheckedListBox 控制項現在具有為虛擬第一個項目繪製的焦點矩形。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-126">An empty CheckedListBox control now has a focus rectangle drawn for a virtual first item when the control becomes focused.</span></span>

<span data-ttu-id="b4dc0-127">**改善的 ComboBox 協助工具支援**</span><span class="sxs-lookup"><span data-stu-id="b4dc0-127">**Improved ComboBox Accessibility support**</span></span>

- <span data-ttu-id="b4dc0-128">已啟用 <xref:System.Windows.Forms.ComboBox> 控制項的 UI 自動化支援，並可使用 UI 自動化通知和其他 UI 自動化功能。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-128">Enabled UI Automation support for the <xref:System.Windows.Forms.ComboBox> control, with the ability to use UI Automation notifications and other UI Automation features.</span></span>
<span data-ttu-id="b4dc0-129">**已改進 DataGridView 協助工具支援**</span><span class="sxs-lookup"><span data-stu-id="b4dc0-129">**Improved DataGridView Accessibility support**</span></span>

- <span data-ttu-id="b4dc0-130">已啟用 <xref:System.Windows.Forms.DataGridView> 控制項的 UI 自動化支援，並可使用 UI 自動化通知和其他 UI 自動化功能。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-130">Enabled UI Automation support for <xref:System.Windows.Forms.DataGridView> control with ability to use UI Automation notifications and other UI Automation features.</span></span>
- <span data-ttu-id="b4dc0-131">對應至 <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl> 或 <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl> 的 UI 自動化項目，現為對應編輯儲存格的子項目。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-131">The UI Automation element which corresponds to the <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl> or <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl> is now a child of corresponding editing cell.</span></span>

<span data-ttu-id="b4dc0-132">**改善的 LinkLabel 協助工具支援**</span><span class="sxs-lookup"><span data-stu-id="b4dc0-132">**Improved LinkLabel Accessibility support**</span></span>

- <span data-ttu-id="b4dc0-133">改良 <xref:System.Windows.Forms.LinkLabel> 的控制項協助工具：如果停用對應的控制項，朗讀程式會宣佈已停用的連結狀態 <xref:System.Windows.Forms.LinkLabel> 。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-133">Improved <xref:System.Windows.Forms.LinkLabel> control accessibility: Narrator announces the disabled state for the link if the corresponding <xref:System.Windows.Forms.LinkLabel> control is disabled.</span></span>

<span data-ttu-id="b4dc0-134">**改善的進度列協助工具支援**</span><span class="sxs-lookup"><span data-stu-id="b4dc0-134">**Improved ProgressBar Accessibility support**</span></span>

- <span data-ttu-id="b4dc0-135">已啟用 <xref:System.Windows.Forms.ProgressBar> 控制項的 UI 自動化支援，並可使用 UI 自動化通知和其他 UI 自動化功能。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-135">Enabled UI Automation support for the <xref:System.Windows.Forms.ProgressBar> control with the ability to use UI Automation notifications and other UI Automation features.</span></span> <span data-ttu-id="b4dc0-136">開發人員現在可以使用 UI 自動化通知，朗讀程式可以透過這些通知顯示進度。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-136">Developers are now able to use UI Automation notifications which Narrator can announce to indicate progress.</span></span>
<span data-ttu-id="b4dc0-137">如需 UI 自動化事件總覽（包括 UI 自動化通知事件）的總覽，請參閱[Ui 自動化事件總覽](https://docs.microsoft.com/windows/desktop/WinAuto/uiauto-eventsoverview)。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-137">For an overview of UI automation events overview, including UI automation notification events, see the [UI Automation Events Overview](https://docs.microsoft.com/windows/desktop/WinAuto/uiauto-eventsoverview).</span></span>

<span data-ttu-id="b4dc0-138">**改良的 PropertyGrid 協助工具支援**</span><span class="sxs-lookup"><span data-stu-id="b4dc0-138">**Improved PropertyGrid Accessibility support**</span></span>

- <span data-ttu-id="b4dc0-139">已啟用 <xref:System.Windows.Forms.PropertyGrid> 控制項的 UI 自動化支援，並可使用 UI 自動化通知和其他 UI 自動化功能。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-139">Enabled UI Automation support for the <xref:System.Windows.Forms.PropertyGrid> control, with the ability to use UI Automation notifications and other UI Automation features.</span></span>
- <span data-ttu-id="b4dc0-140">與當前已編輯屬性對應的 UI 自動化項目，現為對應屬性項目 UI 自動化項目的子項目。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-140">The UI Automation element which corresponds to the currently edited property is now a child of the corresponding property item UI Automation element.</span></span>
- <span data-ttu-id="b4dc0-141">如果父 <xref:System.Windows.Forms.PropertyGrid> 控制項設為類別檢視，則 UI 自動化屬性項目項目現為對應類別項目的子項目。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-141">The UI Automation property item element is now a child of the corresponding category element if the parent <xref:System.Windows.Forms.PropertyGrid> control is set to category view.</span></span>

<span data-ttu-id="b4dc0-142">**改善的 ToolStrip 支援**</span><span class="sxs-lookup"><span data-stu-id="b4dc0-142">**Improved ToolStrip support**</span></span>

- <span data-ttu-id="b4dc0-143">已啟用 <xref:System.Windows.Forms.ToolStrip> 控制項的 UI 自動化支援，並可使用 UI 自動化通知和其他 UI 自動化功能。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-143">Enabled UI Automation support for the <xref:System.Windows.Forms.ToolStrip> control, with the ability to use UI Automation notifications and other UI Automation features.</span></span>
- <span data-ttu-id="b4dc0-144">已改善 <xref:System.Windows.Forms.ToolStrip> 項目的瀏覽。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-144">Improved navigation through <xref:System.Windows.Forms.ToolStrip> items.</span></span>
- <span data-ttu-id="b4dc0-145">在項目模式中，朗讀程式的焦點未消失，且不會前往隱藏的項目。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-145">In items mode, Narrator focus does not disappear and does not go to hidden items.</span></span>

<span data-ttu-id="b4dc0-146">**已改進視覺提示**</span><span class="sxs-lookup"><span data-stu-id="b4dc0-146">**Improved Visual cues**</span></span>

- <span data-ttu-id="b4dc0-147">空白 <xref:System.Windows.Forms.CheckedListBox> 控制項現會在收到焦點時顯示焦點指標。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-147">An empty <xref:System.Windows.Forms.CheckedListBox> control now displays a focus indicator when it receives focus.</span></span>
<span data-ttu-id="b4dc0-148">注意：在執行時間中，控制項的 UI 自動化支援已啟用，但不會在設計階段中使用。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-148">Note: UI automation support is enabled for controls in runtime but is not used in design time.</span></span> <span data-ttu-id="b4dc0-149">如需 UI 自動化的概觀，請參閱 [UI 自動化概觀](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview)。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-149">For an overview of UI automation, see the [UI Automation Overview](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview).</span></span>

<span data-ttu-id="b4dc0-150">**使用鍵盤叫用控制項的工具提示**</span><span class="sxs-lookup"><span data-stu-id="b4dc0-150">**Invoking controls' ToolTips with a keyboard**</span></span>

- <span data-ttu-id="b4dc0-151">現在可以把焦點放在使用鍵盤控制，叫用控制項工具提示。</span><span class="sxs-lookup"><span data-stu-id="b4dc0-151">Control tooltip can now be invoked by focusing the control with keyboard.</span></span> <span data-ttu-id="b4dc0-152">應用程式必須明確啟用此功能（請參閱\*\* &quot; 如何加入宣告或退出這些變更 &quot; \*\*一節）</span><span class="sxs-lookup"><span data-stu-id="b4dc0-152">This feature needs to be enabled explicitly for the application (see section **&quot;How to opt in or out of these changes&quot;**)</span></span>

| <span data-ttu-id="b4dc0-153">名稱</span><span class="sxs-lookup"><span data-stu-id="b4dc0-153">Name</span></span>    | <span data-ttu-id="b4dc0-154">值</span><span class="sxs-lookup"><span data-stu-id="b4dc0-154">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b4dc0-155">影響範圍</span><span class="sxs-lookup"><span data-stu-id="b4dc0-155">Scope</span></span>   | <span data-ttu-id="b4dc0-156">主要</span><span class="sxs-lookup"><span data-stu-id="b4dc0-156">Major</span></span>       |
| <span data-ttu-id="b4dc0-157">版本</span><span class="sxs-lookup"><span data-stu-id="b4dc0-157">Version</span></span> | <span data-ttu-id="b4dc0-158">4.8</span><span class="sxs-lookup"><span data-stu-id="b4dc0-158">4.8</span></span>         |
| <span data-ttu-id="b4dc0-159">類型</span><span class="sxs-lookup"><span data-stu-id="b4dc0-159">Type</span></span>    | <span data-ttu-id="b4dc0-160">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="b4dc0-160">Retargeting</span></span> |
