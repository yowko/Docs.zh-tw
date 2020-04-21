---
title: Windows 表單表單功能改進
description: 瞭解 .NET 核心 Windows 窗體嘗試與 .NET 框架 Windows 窗體相比提高可存取性的方式。
ms.date: 04/20/2020
helpviewer_keywords:
- Windows Forms accessibility
- accessibility
author: M-Lipin
ms.openlocfilehash: 30eb8b3bd0aaf646ea23f4f036e822f9bba78dc4
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739749"
---
# <a name="accessibility-improvements-in-windows-forms-controls-for-net-core-30"></a><span data-ttu-id="49027-103">.NET Core 3.0 的 Windows 表單元件中的輔助功能改進</span><span class="sxs-lookup"><span data-stu-id="49027-103">Accessibility improvements in Windows Forms controls for .NET Core 3.0</span></span>

<span data-ttu-id="49027-104">Windows 窗體正在繼續改進其使用輔助功能技術的方式,以便更好地支援 Windows 窗體客戶。</span><span class="sxs-lookup"><span data-stu-id="49027-104">Windows Forms is continuing to improve how it works with accessibility technologies to better support Windows Forms customers.</span></span> <span data-ttu-id="49027-105">這些改善包括下列變更：</span><span class="sxs-lookup"><span data-stu-id="49027-105">These improvements include the following changes:</span></span>

- <span data-ttu-id="49027-106">與輔助功能用戶端應用程式(包括講述人)互動的各個領域的更改。</span><span class="sxs-lookup"><span data-stu-id="49027-106">Changes in various areas of interaction with accessibility client applications, including Narrator.</span></span>
- <span data-ttu-id="49027-107">對可存取階層進行了變更 (改善 UI 自動化樹狀的瀏覽)。</span><span class="sxs-lookup"><span data-stu-id="49027-107">Changes in the Accessible hierarchy (improving navigation through the UI Automation tree).</span></span>
- <span data-ttu-id="49027-108">鍵盤導航中的更改。</span><span class="sxs-lookup"><span data-stu-id="49027-108">Changes in keyboard navigation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="49027-109">在 .NET 框架 4.7.1 到 .NET 框架 4.8 中所做的輔助功能更改包含在 .NET Core 3.0 及以上,默認情況下已啟用。</span><span class="sxs-lookup"><span data-stu-id="49027-109">Accessibility changes made in .NET Framework 4.7.1 through .NET Framework 4.8 are included in .NET Core 3.0 and above, and are enabled by default.</span></span> <span data-ttu-id="49027-110">. NET 框架支援相容換機,允許應用程式選擇退出新的輔助功能行為。</span><span class="sxs-lookup"><span data-stu-id="49027-110">The .NET Framework supported compatibility switches that allowed applications to opt out of the new accessibility behavior.</span></span> <span data-ttu-id="49027-111">另一方面,.NET Core 不支援這些設置,並且不允許應用程式選擇退出輔助功能行為。</span><span class="sxs-lookup"><span data-stu-id="49027-111">On the other hand, .NET Core doesn't support these settings and doesn't allow applications to opt out of accessibility behavior.</span></span>
  
<span data-ttu-id="49027-112">從 .NET Core 3.0 開始,Windows 窗體應用程式將受益於所有新的輔助功能(在 .NET 框架 4.7.1 - 4.8 中介紹),無需其他配置。</span><span class="sxs-lookup"><span data-stu-id="49027-112">Starting with .NET Core 3.0, Windows Forms applications benefit from all the new accessibility features (introduced in .NET Framework 4.7.1 - 4.8) without additional configuration.</span></span>

## <a name="listbox-accessibility-support"></a><span data-ttu-id="49027-113">清單框輔助功能支援</span><span class="sxs-lookup"><span data-stu-id="49027-113">ListBox Accessibility support</span></span>

<span data-ttu-id="49027-114">以下變更適用於<xref:System.Windows.Forms.ListBox>控制項:</span><span class="sxs-lookup"><span data-stu-id="49027-114">The following changes apply to the <xref:System.Windows.Forms.ListBox> control:</span></span>

- <span data-ttu-id="49027-115">啟用了用於`ListBox`控制的 UI 自動化支援。</span><span class="sxs-lookup"><span data-stu-id="49027-115">Enabled UI Automation support for `ListBox` control.</span></span>
- <span data-ttu-id="49027-116">通過將`ListBox`添加<xref:System.Windows.Automation.ScrollItemPattern>`ListBox`到 項以及通過增強輔助功能事件籌集和處理以及通過專案進行講述人導航(上限鎖定導航不正確,並且不會無意中將導航扔到控件之外),從而改進了輔助功能支援。</span><span class="sxs-lookup"><span data-stu-id="49027-116">Improved `ListBox` accessibility support by adding the <xref:System.Windows.Automation.ScrollItemPattern> to `ListBox` items and by enhancing the accessibility event raising and handling and Narrator navigation through the items (caps lock navigation isn't correct and doesn't throw the navigation outside the control unintentionally).</span></span>

## <a name="checkedlistbox-accessibility-support"></a><span data-ttu-id="49027-117">選取清單框輔助功能支援</span><span class="sxs-lookup"><span data-stu-id="49027-117">CheckedListBox Accessibility support</span></span>

<span data-ttu-id="49027-118">以下變更適用於<xref:System.Windows.Forms.CheckedListBox>控制項:</span><span class="sxs-lookup"><span data-stu-id="49027-118">The following changes apply to the <xref:System.Windows.Forms.CheckedListBox> control:</span></span>

- <span data-ttu-id="49027-119">由項目`CheckedListBox`的輔助功能屬性提供的更正邊界。</span><span class="sxs-lookup"><span data-stu-id="49027-119">Corrected `CheckedListBox` Bounds provided by accessibility properties for entries.</span></span>
- <span data-ttu-id="49027-120">改進了`ListBox``CheckedListBox`整體和可訪問性:更正了屬性值和事件模型。</span><span class="sxs-lookup"><span data-stu-id="49027-120">Improved overall `ListBox` and `CheckedListBox` accessibility: corrected property values and event model.</span></span>

## <a name="combobox-accessibility-support"></a><span data-ttu-id="49027-121">組合盒輔助功能支援</span><span class="sxs-lookup"><span data-stu-id="49027-121">ComboBox Accessibility support</span></span>

<span data-ttu-id="49027-122">以下變更適用於<xref:System.Windows.Forms.ComboBox>控制項:</span><span class="sxs-lookup"><span data-stu-id="49027-122">The following changes apply to the <xref:System.Windows.Forms.ComboBox> control:</span></span>

- <span data-ttu-id="49027-123">更新了獲取`ComboBox`項的輔助物件以啟用為專案生成I而不是從項獲取哈希代碼的過程,如果函數被覆蓋,<xref:System.Object.GetHashCode%2A>這可能不安全。</span><span class="sxs-lookup"><span data-stu-id="49027-123">Updated the process of getting `ComboBox` items' accessibility objects to enable generating IDs for items instead of getting hash codes from items, which may be unsafe in case the <xref:System.Object.GetHashCode%2A> function is overridden.</span></span>

## <a name="datagridview-accessibility-support"></a><span data-ttu-id="49027-124">資料格線檢視輔助功能支援</span><span class="sxs-lookup"><span data-stu-id="49027-124">DataGridView Accessibility support</span></span>

<span data-ttu-id="49027-125">以下變更適用於<xref:System.Windows.Forms.DataGridView>控制項:</span><span class="sxs-lookup"><span data-stu-id="49027-125">The following changes apply to the <xref:System.Windows.Forms.DataGridView> control:</span></span>

- <span data-ttu-id="49027-126">由列`DataGridView.Bounds`、行、單元格和相應標頭的輔助功能屬性更正,提高了邊界矩形計算的性能。</span><span class="sxs-lookup"><span data-stu-id="49027-126">Corrected `DataGridView.Bounds` provided by accessibility properties for columns, rows, cells and corresponding headers, improved performance of bounding rectangle calculation.</span></span> <span data-ttu-id="49027-127">考慮到整個控制項的邊界及其視口,將正確表示所有可訪問邊界。</span><span class="sxs-lookup"><span data-stu-id="49027-127">All accessibility bounds are represented correctly taking into account the bounds of entire control, along with its viewport.</span></span>
- <span data-ttu-id="49027-128">為可`Value.IsReadOnly`存取的用戶端應用程式提供更正的屬性值。</span><span class="sxs-lookup"><span data-stu-id="49027-128">Corrected `Value.IsReadOnly` property value providing for accessible client applications.</span></span> <span data-ttu-id="49027-129">該屬性現在顯示單元格`IsReadOnly`的正確狀態。</span><span class="sxs-lookup"><span data-stu-id="49027-129">The property now shows correct `IsReadOnly` status for cells.</span></span>
- <span data-ttu-id="49027-130">修復了第一次<xref:System.Windows.Forms.DataGridView.CellParsing>單元格更改的事件引發問題。</span><span class="sxs-lookup"><span data-stu-id="49027-130">Fixed the issue with <xref:System.Windows.Forms.DataGridView.CellParsing> event raising for the first cell change.</span></span> <span data-ttu-id="49027-131">單元格值可以更改,沒有任何問題,包括第一`DataGridView`個控制交互。</span><span class="sxs-lookup"><span data-stu-id="49027-131">Cell value can be changed without any issues including the first `DataGridView` control interaction.</span></span>
- <span data-ttu-id="49027-132">使用`DataGridView`Windows 高對比度主題時,改進了背景顏色對比度。</span><span class="sxs-lookup"><span data-stu-id="49027-132">Improved `DataGridView` background color contrast when using Windows High Contrast themes.</span></span> <span data-ttu-id="49027-133">使用`DataGridView`HC#1、HC+2 和 HC 黑色主題時更改預設回顏色。</span><span class="sxs-lookup"><span data-stu-id="49027-133">Changed `DataGridView` default back color when using HC#1, HC#2, and HC Black themes.</span></span>

## <a name="propertygrid-accessibility-support"></a><span data-ttu-id="49027-134">屬性格格輔助功能支援</span><span class="sxs-lookup"><span data-stu-id="49027-134">PropertyGrid Accessibility support</span></span>

<span data-ttu-id="49027-135">以下變更適用於<xref:System.Windows.Forms.PropertyGrid>控制項:</span><span class="sxs-lookup"><span data-stu-id="49027-135">The following changes apply to the <xref:System.Windows.Forms.PropertyGrid> control:</span></span>

- <span data-ttu-id="49027-136">網格`PropertyGrid.Bounds`條目的輔助功能屬性已更正,提高了邊界矩形計算的性能。</span><span class="sxs-lookup"><span data-stu-id="49027-136">Corrected `PropertyGrid.Bounds` provided by accessibility properties for grid entries, improved performance of bounding rectangle calculation.</span></span> <span data-ttu-id="49027-137">現在,考慮到整個控件的邊界及其視口,所有可訪問性邊界都正確表示。</span><span class="sxs-lookup"><span data-stu-id="49027-137">For now all accessibility bounds are represented correctly taking into account the bounds of entire control, along with its viewport.</span></span>
- <span data-ttu-id="49027-138">更正了輔助控制項的可存取名稱和說明,以不包含控制項類型名稱,並避免對控制項類型名稱進行雙重通知。</span><span class="sxs-lookup"><span data-stu-id="49027-138">Corrected accessible names and descriptions of subcontrols to not include control type names and to avoid double announcement for control type names.</span></span>

## <a name="toolstrip-accessibility-support"></a><span data-ttu-id="49027-139">工具條輔助功能支援</span><span class="sxs-lookup"><span data-stu-id="49027-139">ToolStrip Accessibility support</span></span>

<span data-ttu-id="49027-140">以下變更適用於<xref:System.Windows.Forms.ToolStrip>控制項:</span><span class="sxs-lookup"><span data-stu-id="49027-140">The following changes apply to the <xref:System.Windows.Forms.ToolStrip> control:</span></span>

- <span data-ttu-id="49027-141">改進了通過`ToolStrip``MenuStrip`和`StatusStrip`和項的導航。</span><span class="sxs-lookup"><span data-stu-id="49027-141">Improved navigation through `ToolStrip`, `MenuStrip`, and `StatusStrip` items.</span></span> <span data-ttu-id="49027-142">更正`ToolStrip`和`MenuStrip`移位選項卡導航,在按下移位選項卡上箭頭時回迴圈功能表項,該箭頭將導航到底部功能表元素。</span><span class="sxs-lookup"><span data-stu-id="49027-142">Corrected `ToolStrip` and `MenuStrip` shift-tab navigation, back-looping the menu items when shift-tab up-arrow is pressed, which navigates to the bottom menu element.</span></span>
- <span data-ttu-id="49027-143">改進`MenuStrip`了可訪問導航、更正的功能表可存取控制類型,可為子功能表製作類型為"菜單"而不是"菜單專案"的子功能表。</span><span class="sxs-lookup"><span data-stu-id="49027-143">Improved `MenuStrip` accessible navigation, corrected menu accessible control types for submenus to make submenus of type 'Menu' instead of 'MenuItem'.</span></span>

## <a name="printpreviewcontrol-and-printpreviewdialog-accessibility-support"></a><span data-ttu-id="49027-144">預覽控制並列印預覽對話輔助功能支援</span><span class="sxs-lookup"><span data-stu-id="49027-144">PrintPreviewControl and PrintPreviewDialog Accessibility support</span></span>

<span data-ttu-id="49027-145">以下變更適用於列印控制項:</span><span class="sxs-lookup"><span data-stu-id="49027-145">The following changes apply to the print controls:</span></span>

- <span data-ttu-id="49027-146">通過功能表項改進了可訪問導航(包括講述人導航)。</span><span class="sxs-lookup"><span data-stu-id="49027-146">Improved accessible navigation (including Narrator navigation) through menu items.</span></span>
- <span data-ttu-id="49027-147">改進了高對比度主題支援,使控制元素更加對比。</span><span class="sxs-lookup"><span data-stu-id="49027-147">Improved High Contrast themes support and made the control element more contrasted.</span></span>

## <a name="stringcollectioneditor-accessibility-support"></a><span data-ttu-id="49027-148">字串收集編輯器輔助功能支援</span><span class="sxs-lookup"><span data-stu-id="49027-148">StringCollectionEditor Accessibility support</span></span>

<span data-ttu-id="49027-149">Windows 表單表設計器現在使用具有改進的輔助功能支援的字串集合編輯器。</span><span class="sxs-lookup"><span data-stu-id="49027-149">Windows Forms designer now uses the string collection editor with improved accessibility support.</span></span>

## <a name="monthcalendar-accessibility-support-available-in-net-core-31"></a><span data-ttu-id="49027-150">月曆輔助功能支援(在 .NET 核心 3.1 中提供)</span><span class="sxs-lookup"><span data-stu-id="49027-150">MonthCalendar Accessibility support (available in .NET Core 3.1)</span></span>

<span data-ttu-id="49027-151">以下變更適用於<xref:System.Windows.Forms.MonthCalendar>控制項:</span><span class="sxs-lookup"><span data-stu-id="49027-151">The following changes apply to the <xref:System.Windows.Forms.MonthCalendar> control:</span></span>

- <span data-ttu-id="49027-152">添加了 UI 自動化伺服器`MonthCalendar`提供者 來控制、添加了 UI 自動化網格模式和表模式提供程式。</span><span class="sxs-lookup"><span data-stu-id="49027-152">Added UI Automation server providers to `MonthCalendar` control, added UI Automation Grid pattern and Table pattern providers.</span></span>
- <span data-ttu-id="49027-153">變更_的表_可存取控制項類型到_行事曆_可存`MonthCalendar`取 控制項類型`MonthCalendar`,除非控制項具有定義 控制項可存取名稱的上述標籤控制項的情況,在此特定情況下,可存取控制項類型將成為_表_格 。</span><span class="sxs-lookup"><span data-stu-id="49027-153">Changed _table_ accessible control type to _calendar_ accessible control type for `MonthCalendar` except the case when the control has a preceding label control that defines `MonthCalendar` control accessible name, in this specific case accessible control type becomes _table_.</span></span>
- <span data-ttu-id="49027-154">改進了所選控制日期的`MonthCalendar`公告。</span><span class="sxs-lookup"><span data-stu-id="49027-154">Improved announcement of selected date for `MonthCalendar` control.</span></span>
- <span data-ttu-id="49027-155">改進`MonthCalendar`了對螢幕閱讀器和其他輔助功能工具的控制支援。</span><span class="sxs-lookup"><span data-stu-id="49027-155">Improved `MonthCalendar` control support for screen readers and other accessibility tools.</span></span> <span data-ttu-id="49027-156">此時,用戶可以導航控制件元素並使用僅鍵盤輸入與這些元素進行交互。</span><span class="sxs-lookup"><span data-stu-id="49027-156">At this moment, users can navigate the control elements and interact with these elements using keyboard-only input.</span></span> <span data-ttu-id="49027-157">使用「講述人」,使用 CAPS + 箭頭鍵通過控制元素導航,然後使用 CAPS = 輸入以調用元素預設操作。</span><span class="sxs-lookup"><span data-stu-id="49027-157">With Narrator, use CAPS + arrow keys to navigation through the control elements and CAPS + Enter to invoke element default action.</span></span>
- <span data-ttu-id="49027-158">使用對焦矩形改進`MonthCalendar`了子元素的箭頭鍵導航:講述人的藍色焦點矩形。</span><span class="sxs-lookup"><span data-stu-id="49027-158">Improved arrow key navigation across `MonthCalendar` child elements with a focusing rectangle: blue focus rectangle for Narrator.</span></span>
- <span data-ttu-id="49027-159">改進了控制項元素抓測操作`MonthCalendar`的可存取性`MonthCalendar`, 以便透過提供的座標獲取子可存取元素。</span><span class="sxs-lookup"><span data-stu-id="49027-159">Improved accessibility for hit test action for `MonthCalendar` control elements to allow getting `MonthCalendar` child accessible element by provided coordinates.</span></span>

## <a name="tooltips-accessibility-available-in-net-core-31"></a><span data-ttu-id="49027-160">工具提示輔助功能(在 .NET 核心 3.1 中提供)</span><span class="sxs-lookup"><span data-stu-id="49027-160">ToolTips accessibility (available in .NET Core 3.1)</span></span>

- <span data-ttu-id="49027-161">增加了通過螢幕閱讀器應用程式(如 NVDA 和講述人)宣佈工具提示文本的能力。</span><span class="sxs-lookup"><span data-stu-id="49027-161">Added ability to announce a tooltip text by screen reader applications such as NVDA and Narrator.</span></span> <span data-ttu-id="49027-162">螢幕閱讀器應用程式現在可以宣佈任何 Windows 窗體控制項的鍵盤或滑鼠工具提示的文本,該控制項配置為顯示工具提示。</span><span class="sxs-lookup"><span data-stu-id="49027-162">Screen reader application can now announce the text of keyboard or mouse tooltip of any Windows Forms control that configured to show tooltips.</span></span>

## <a name="ui-automation-support-for-datagridview-propertygrid-listbox-combobox-toolstrip-and-other-controls"></a><span data-ttu-id="49027-163">對 DataGridView、屬性網格、清單框、組合盒、工具條和其他控制項的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="49027-163">UI automation support for DataGridView, PropertyGrid, ListBox, ComboBox, ToolStrip, and other controls</span></span>

<span data-ttu-id="49027-164">在運行時為控件啟用 UI 自動化支援,但在設計期間不使用。</span><span class="sxs-lookup"><span data-stu-id="49027-164">UI Automation support is enabled for controls at runtime but isn't used during design time.</span></span> <span data-ttu-id="49027-165">如需 UI 自動化的概觀，請參閱 [UI 自動化概觀](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview)。</span><span class="sxs-lookup"><span data-stu-id="49027-165">For an overview of UI automation, see the [UI Automation Overview](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview).</span></span>

## <a name="see-also"></a><span data-ttu-id="49027-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49027-166">See also</span></span>

- <span data-ttu-id="49027-167">[協助功能最佳實作](../ui-automation/accessibility-best-practices.md)。</span><span class="sxs-lookup"><span data-stu-id="49027-167">[Accessibility Best Practices](../ui-automation/accessibility-best-practices.md).</span></span>
