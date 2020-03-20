---
title: 標準控制項的 UI 自動化支援
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 36028d589e98177f6a0e83092edd656860b1a8d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179856"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="f0a48-102">標準控制項的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="f0a48-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="f0a48-103">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="f0a48-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f0a48-104">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="f0a48-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="f0a48-105">本主題包含有關支援為[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)][!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]Win32 和 Windows 表單框架開發的應用程式中的標準控制項的資訊。</span><span class="sxs-lookup"><span data-stu-id="f0a48-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32, and Windows Forms frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="f0a48-106">Windows Presentation Foundation 控制項</span><span class="sxs-lookup"><span data-stu-id="f0a48-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="f0a48-107">提供資訊或支援使用者互動的所有 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 控制項項目，都有 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的完整原生支援。</span><span class="sxs-lookup"><span data-stu-id="f0a48-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="f0a48-108">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]看不見其他如面板等的項目。</span><span class="sxs-lookup"><span data-stu-id="f0a48-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>
## <a name="win32-controls"></a><span data-ttu-id="f0a48-109">Win32 控制項</span><span class="sxs-lookup"><span data-stu-id="f0a48-109">Win32 Controls</span></span>  
 <span data-ttu-id="f0a48-110">大多數 Win32 控制項[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]通過 UIAutomationClientside 提供程式.dll 中的用戶端提供程式公開。</span><span class="sxs-lookup"><span data-stu-id="f0a48-110">Most Win32 controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="f0a48-111">此組件會自動註冊為用於使用者介面自動化用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="f0a48-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="f0a48-112">完全支援僅為*ComCtrl32.dll*版本 6 中的控制項提供。</span><span class="sxs-lookup"><span data-stu-id="f0a48-112">Full support is provided only for controls from version 6 of *ComCtrl32.dll*.</span></span>  
  
 <span data-ttu-id="f0a48-113">支援的控制項如下。</span><span class="sxs-lookup"><span data-stu-id="f0a48-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="f0a48-114">類別名稱</span><span class="sxs-lookup"><span data-stu-id="f0a48-114">Class name</span></span>|<span data-ttu-id="f0a48-115">控制項類型</span><span class="sxs-lookup"><span data-stu-id="f0a48-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="f0a48-116">按鈕</span><span class="sxs-lookup"><span data-stu-id="f0a48-116">Button</span></span>|<span data-ttu-id="f0a48-117">按鈕</span><span class="sxs-lookup"><span data-stu-id="f0a48-117">Button</span></span>|  
|<span data-ttu-id="f0a48-118">按鈕</span><span class="sxs-lookup"><span data-stu-id="f0a48-118">Button</span></span>|<span data-ttu-id="f0a48-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="f0a48-119">RadioButton</span></span>|  
|<span data-ttu-id="f0a48-120">按鈕</span><span class="sxs-lookup"><span data-stu-id="f0a48-120">Button</span></span>|<span data-ttu-id="f0a48-121">群組</span><span class="sxs-lookup"><span data-stu-id="f0a48-121">Group</span></span>|  
|<span data-ttu-id="f0a48-122">按鈕</span><span class="sxs-lookup"><span data-stu-id="f0a48-122">Button</span></span>|<span data-ttu-id="f0a48-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="f0a48-123">CheckBox</span></span>|  
|<span data-ttu-id="f0a48-124">按鈕</span><span class="sxs-lookup"><span data-stu-id="f0a48-124">Button</span></span>|<span data-ttu-id="f0a48-125">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="f0a48-125">Hyperlink</span></span>|  
|<span data-ttu-id="f0a48-126">按鈕</span><span class="sxs-lookup"><span data-stu-id="f0a48-126">Button</span></span>|<span data-ttu-id="f0a48-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="f0a48-127">SplitButton</span></span>|  
|<span data-ttu-id="f0a48-128">按鈕</span><span class="sxs-lookup"><span data-stu-id="f0a48-128">Button</span></span>|<span data-ttu-id="f0a48-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="f0a48-129">CheckBox</span></span>|  
|<span data-ttu-id="f0a48-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="f0a48-130">ComboBoxEx32</span></span>|<span data-ttu-id="f0a48-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="f0a48-131">ComboBox</span></span>|  
|<span data-ttu-id="f0a48-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="f0a48-132">ComboBox</span></span>|<span data-ttu-id="f0a48-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="f0a48-133">ComboBox</span></span>|  
|<span data-ttu-id="f0a48-134">編輯</span><span class="sxs-lookup"><span data-stu-id="f0a48-134">Edit</span></span>|<span data-ttu-id="f0a48-135">Document</span><span class="sxs-lookup"><span data-stu-id="f0a48-135">Document</span></span>|  
|<span data-ttu-id="f0a48-136">編輯</span><span class="sxs-lookup"><span data-stu-id="f0a48-136">Edit</span></span>|<span data-ttu-id="f0a48-137">編輯</span><span class="sxs-lookup"><span data-stu-id="f0a48-137">Edit</span></span>|  
|<span data-ttu-id="f0a48-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="f0a48-138">SysLink</span></span>|<span data-ttu-id="f0a48-139">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="f0a48-139">Hyperlink</span></span>|  
|<span data-ttu-id="f0a48-140">靜態</span><span class="sxs-lookup"><span data-stu-id="f0a48-140">Static</span></span>|<span data-ttu-id="f0a48-141">Text</span><span class="sxs-lookup"><span data-stu-id="f0a48-141">Text</span></span>|  
|<span data-ttu-id="f0a48-142">靜態</span><span class="sxs-lookup"><span data-stu-id="f0a48-142">Static</span></span>|<span data-ttu-id="f0a48-143">映像</span><span class="sxs-lookup"><span data-stu-id="f0a48-143">Image</span></span>|  
|<span data-ttu-id="f0a48-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="f0a48-144">SysIPAddress32</span></span>|<span data-ttu-id="f0a48-145">Custom</span><span class="sxs-lookup"><span data-stu-id="f0a48-145">Custom</span></span>|  
|<span data-ttu-id="f0a48-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="f0a48-146">SysHeader32</span></span>|<span data-ttu-id="f0a48-147">Header/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="f0a48-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="f0a48-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="f0a48-148">SysListView32</span></span>|<span data-ttu-id="f0a48-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="f0a48-149">DataGrid</span></span>|  
|<span data-ttu-id="f0a48-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="f0a48-150">SysListView32</span></span>|<span data-ttu-id="f0a48-151">清單</span><span class="sxs-lookup"><span data-stu-id="f0a48-151">List</span></span>|  
|<span data-ttu-id="f0a48-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="f0a48-152">ListBox</span></span>|<span data-ttu-id="f0a48-153">清單</span><span class="sxs-lookup"><span data-stu-id="f0a48-153">List</span></span>|  
|<span data-ttu-id="f0a48-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="f0a48-154">ListBox</span></span>|<span data-ttu-id="f0a48-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="f0a48-155">ListItem</span></span>|  
|<span data-ttu-id="f0a48-156">#32768</span><span class="sxs-lookup"><span data-stu-id="f0a48-156">#32768</span></span>|<span data-ttu-id="f0a48-157">功能表</span><span class="sxs-lookup"><span data-stu-id="f0a48-157">Menu</span></span>|  
|<span data-ttu-id="f0a48-158">#32768</span><span class="sxs-lookup"><span data-stu-id="f0a48-158">#32768</span></span>|<span data-ttu-id="f0a48-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="f0a48-159">MenuItem</span></span>|  
|<span data-ttu-id="f0a48-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="f0a48-160">msctls_progress32</span></span>|<span data-ttu-id="f0a48-161">進度列</span><span class="sxs-lookup"><span data-stu-id="f0a48-161">ProgressBar</span></span>|  
|<span data-ttu-id="f0a48-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="f0a48-162">RichEdit</span></span>|<span data-ttu-id="f0a48-163">文件。</span><span class="sxs-lookup"><span data-stu-id="f0a48-163">Document.</span></span> <span data-ttu-id="f0a48-164">請參閱「注意」。</span><span class="sxs-lookup"><span data-stu-id="f0a48-164">See note.</span></span>|  
|<span data-ttu-id="f0a48-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="f0a48-165">RichEdit20A</span></span>|<span data-ttu-id="f0a48-166">Document</span><span class="sxs-lookup"><span data-stu-id="f0a48-166">Document</span></span>|  
|<span data-ttu-id="f0a48-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="f0a48-167">RichEdit20W</span></span>|<span data-ttu-id="f0a48-168">Document</span><span class="sxs-lookup"><span data-stu-id="f0a48-168">Document</span></span>|  
|<span data-ttu-id="f0a48-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="f0a48-169">RichEdit50W</span></span>|<span data-ttu-id="f0a48-170">Document</span><span class="sxs-lookup"><span data-stu-id="f0a48-170">Document</span></span>|  
|<span data-ttu-id="f0a48-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="f0a48-171">ScrollBar</span></span>|<span data-ttu-id="f0a48-172">滑桿</span><span class="sxs-lookup"><span data-stu-id="f0a48-172">Slider</span></span>|  
|<span data-ttu-id="f0a48-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="f0a48-173">msctls_trackbar32</span></span>|<span data-ttu-id="f0a48-174">滑桿</span><span class="sxs-lookup"><span data-stu-id="f0a48-174">Slider</span></span>|  
|<span data-ttu-id="f0a48-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="f0a48-175">msctls_updown32</span></span>|<span data-ttu-id="f0a48-176">Spinner</span><span class="sxs-lookup"><span data-stu-id="f0a48-176">Spinner</span></span>|  
|<span data-ttu-id="f0a48-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="f0a48-177">msctls_statusbar32</span></span>|<span data-ttu-id="f0a48-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="f0a48-178">StatusBar</span></span>|  
|<span data-ttu-id="f0a48-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="f0a48-179">SysTabControl32</span></span>|<span data-ttu-id="f0a48-180">索引標籤</span><span class="sxs-lookup"><span data-stu-id="f0a48-180">Tab</span></span>|  
|<span data-ttu-id="f0a48-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="f0a48-181">SysTabControl32</span></span>|<span data-ttu-id="f0a48-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="f0a48-182">TabItem</span></span>|  
|<span data-ttu-id="f0a48-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="f0a48-183">ToolbarWindow32</span></span>|<span data-ttu-id="f0a48-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="f0a48-184">ToolBar</span></span>|  
|<span data-ttu-id="f0a48-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="f0a48-185">ToolbarWindow32</span></span>|<span data-ttu-id="f0a48-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="f0a48-186">MenuItem</span></span>|  
|<span data-ttu-id="f0a48-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="f0a48-187">ToolbarWindow32</span></span>|<span data-ttu-id="f0a48-188">按鈕</span><span class="sxs-lookup"><span data-stu-id="f0a48-188">Button</span></span>|  
|<span data-ttu-id="f0a48-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="f0a48-189">ToolbarWindow32</span></span>|<span data-ttu-id="f0a48-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="f0a48-190">CheckBox</span></span>|  
|<span data-ttu-id="f0a48-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="f0a48-191">ToolbarWindow32</span></span>|<span data-ttu-id="f0a48-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="f0a48-192">RadioButton</span></span>|  
|<span data-ttu-id="f0a48-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="f0a48-193">ToolbarWindow32</span></span>|<span data-ttu-id="f0a48-194">分隔符號</span><span class="sxs-lookup"><span data-stu-id="f0a48-194">Separator</span></span>|  
|<span data-ttu-id="f0a48-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="f0a48-195">tooltips_class32</span></span>|<span data-ttu-id="f0a48-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="f0a48-196">ToolTip</span></span>|  
|<span data-ttu-id="f0a48-197">#32774</span><span class="sxs-lookup"><span data-stu-id="f0a48-197">#32774</span></span>|<span data-ttu-id="f0a48-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="f0a48-198">ToolTip</span></span>|  
|<span data-ttu-id="f0a48-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="f0a48-199">ReBarWindow32</span></span>|<span data-ttu-id="f0a48-200">工具列</span><span class="sxs-lookup"><span data-stu-id="f0a48-200">Toolbar</span></span>|  
|<span data-ttu-id="f0a48-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="f0a48-201">SysTreeView32</span></span>|<span data-ttu-id="f0a48-202">樹狀結構</span><span class="sxs-lookup"><span data-stu-id="f0a48-202">Tree</span></span>|  
|<span data-ttu-id="f0a48-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="f0a48-203">SysTreeView32</span></span>|<span data-ttu-id="f0a48-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="f0a48-204">TreeItem</span></span>|  
  
 <span data-ttu-id="f0a48-205">**注意**僅支援與 Windows Vista 一起附帶的版本（在 RichEd20.dll 版本 3.1 及更高版本以及 MsftEdit.dll 版本 4.1 及更高版本）中支援 RichEdit 控制項。</span><span class="sxs-lookup"><span data-stu-id="f0a48-205">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="f0a48-206">不支援的控制項如下。</span><span class="sxs-lookup"><span data-stu-id="f0a48-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="f0a48-207">類別名稱</span><span class="sxs-lookup"><span data-stu-id="f0a48-207">Class name</span></span>|<span data-ttu-id="f0a48-208">控制項類型</span><span class="sxs-lookup"><span data-stu-id="f0a48-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="f0a48-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="f0a48-209">SysAnimate32</span></span>|<span data-ttu-id="f0a48-210">映像</span><span class="sxs-lookup"><span data-stu-id="f0a48-210">Image</span></span>|  
|<span data-ttu-id="f0a48-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="f0a48-211">SysPager</span></span>|<span data-ttu-id="f0a48-212">Spinner</span><span class="sxs-lookup"><span data-stu-id="f0a48-212">Spinner</span></span>|  
|<span data-ttu-id="f0a48-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="f0a48-213">SysDateTimePick32</span></span>|<span data-ttu-id="f0a48-214">Custom</span><span class="sxs-lookup"><span data-stu-id="f0a48-214">Custom</span></span>|  
|<span data-ttu-id="f0a48-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="f0a48-215">SysMonthCal32</span></span>|<span data-ttu-id="f0a48-216">Calendar</span><span class="sxs-lookup"><span data-stu-id="f0a48-216">Calendar</span></span>|  
|<span data-ttu-id="f0a48-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="f0a48-217">MS_WINNOTE</span></span>|<span data-ttu-id="f0a48-218">工具提示</span><span class="sxs-lookup"><span data-stu-id="f0a48-218">Tooltip</span></span>|  
|<span data-ttu-id="f0a48-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="f0a48-219">VBBubble</span></span>|<span data-ttu-id="f0a48-220">工具提示</span><span class="sxs-lookup"><span data-stu-id="f0a48-220">Tooltip</span></span>|  
|<span data-ttu-id="f0a48-221">ScrollBar (當做獨立控制項使用時)</span><span class="sxs-lookup"><span data-stu-id="f0a48-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="f0a48-222">滑桿</span><span class="sxs-lookup"><span data-stu-id="f0a48-222">Slider</span></span>|  
|<span data-ttu-id="f0a48-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="f0a48-223">SuperGrid</span></span>|<span data-ttu-id="f0a48-224">Custom</span><span class="sxs-lookup"><span data-stu-id="f0a48-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>
## <a name="windows-forms-controls"></a><span data-ttu-id="f0a48-225">Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="f0a48-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="f0a48-226">Windows 表單控制項通過[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]UIAutomationClientside 提供程式.dll 中的用戶端提供程式公開。</span><span class="sxs-lookup"><span data-stu-id="f0a48-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="f0a48-227">此組件會自動註冊為用於使用者介面自動化用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="f0a48-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="f0a48-228">通常，Win32 公共控制項的託管包裝器的 Windows 表單控制項受[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]支援。</span><span class="sxs-lookup"><span data-stu-id="f0a48-228">Typically, Windows Forms controls that are managed wrappers for Win32 common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="f0a48-229">支援的控制項如下。</span><span class="sxs-lookup"><span data-stu-id="f0a48-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="f0a48-230">類別名稱</span><span class="sxs-lookup"><span data-stu-id="f0a48-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="f0a48-231">按鈕</span><span class="sxs-lookup"><span data-stu-id="f0a48-231">Button</span></span>|  
|<span data-ttu-id="f0a48-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="f0a48-232">CheckBox</span></span>|  
|<span data-ttu-id="f0a48-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="f0a48-233">CheckedListBox</span></span>|  
|<span data-ttu-id="f0a48-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="f0a48-234">ColorDialog</span></span>|  
|<span data-ttu-id="f0a48-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="f0a48-235">ComboBox</span></span>|  
|<span data-ttu-id="f0a48-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="f0a48-236">FolderBrowser</span></span>|  
|<span data-ttu-id="f0a48-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="f0a48-237">FontDialog</span></span>|  
|<span data-ttu-id="f0a48-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="f0a48-238">GroupBox</span></span>|  
|<span data-ttu-id="f0a48-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="f0a48-239">HscrollBar</span></span>|  
|<span data-ttu-id="f0a48-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="f0a48-240">ImageList</span></span>|  
|<span data-ttu-id="f0a48-241">標籤</span><span class="sxs-lookup"><span data-stu-id="f0a48-241">Label</span></span>|  
|<span data-ttu-id="f0a48-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="f0a48-242">ListBox</span></span>|  
|<span data-ttu-id="f0a48-243">ListView</span><span class="sxs-lookup"><span data-stu-id="f0a48-243">ListView</span></span>|  
|<span data-ttu-id="f0a48-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="f0a48-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="f0a48-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="f0a48-245">MonthCalendar</span></span>|  
|<span data-ttu-id="f0a48-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="f0a48-246">NotifyIcon</span></span>|  
|<span data-ttu-id="f0a48-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="f0a48-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="f0a48-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="f0a48-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="f0a48-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="f0a48-249">PrintDialog</span></span>|  
|<span data-ttu-id="f0a48-250">進度列</span><span class="sxs-lookup"><span data-stu-id="f0a48-250">ProgressBar</span></span>|  
|<span data-ttu-id="f0a48-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="f0a48-251">RadioButton</span></span>|  
|<span data-ttu-id="f0a48-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="f0a48-252">RichTextBox</span></span>|  
|<span data-ttu-id="f0a48-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="f0a48-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="f0a48-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="f0a48-254">ScrollableControl</span></span>|  
|<span data-ttu-id="f0a48-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="f0a48-255">SoundPlayer</span></span>|  
|<span data-ttu-id="f0a48-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="f0a48-256">StatusBar</span></span>|  
|<span data-ttu-id="f0a48-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="f0a48-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="f0a48-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="f0a48-258">TextBox</span></span>|  
|<span data-ttu-id="f0a48-259">計時器</span><span class="sxs-lookup"><span data-stu-id="f0a48-259">Timer</span></span>|  
|<span data-ttu-id="f0a48-260">工具列</span><span class="sxs-lookup"><span data-stu-id="f0a48-260">Toolbar</span></span>|  
|<span data-ttu-id="f0a48-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="f0a48-261">ToolTip</span></span>|  
|<span data-ttu-id="f0a48-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="f0a48-262">TrackBar</span></span>|  
|<span data-ttu-id="f0a48-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="f0a48-263">TreeView</span></span>|  
|<span data-ttu-id="f0a48-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="f0a48-264">VscrollBar</span></span>|  
|<span data-ttu-id="f0a48-265">Web 瀏覽器</span><span class="sxs-lookup"><span data-stu-id="f0a48-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="f0a48-266">以下控制項[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]僅通過支援 Microsoft 活動協助工具而公開。</span><span class="sxs-lookup"><span data-stu-id="f0a48-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="f0a48-267">部分功能可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="f0a48-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="f0a48-268">控制項名稱</span><span class="sxs-lookup"><span data-stu-id="f0a48-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="f0a48-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="f0a48-269">BindingSource</span></span>|  
|<span data-ttu-id="f0a48-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="f0a48-270">DataGrid</span></span>|  
|<span data-ttu-id="f0a48-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="f0a48-271">DataGridView</span></span>|  
|<span data-ttu-id="f0a48-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="f0a48-272">DataNavigator</span></span>|  
|<span data-ttu-id="f0a48-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="f0a48-273">DomainUpDown</span></span>|  
|<span data-ttu-id="f0a48-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="f0a48-274">ErrorProvider</span></span>|  
|<span data-ttu-id="f0a48-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f0a48-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="f0a48-276">表單</span><span class="sxs-lookup"><span data-stu-id="f0a48-276">Form</span></span>|  
|<span data-ttu-id="f0a48-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="f0a48-277">LinkLabel</span></span>|  
|<span data-ttu-id="f0a48-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="f0a48-278">HelpProvider</span></span>|  
|<span data-ttu-id="f0a48-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="f0a48-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="f0a48-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="f0a48-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="f0a48-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="f0a48-281">NumericUpDown</span></span>|  
|<span data-ttu-id="f0a48-282">面板</span><span class="sxs-lookup"><span data-stu-id="f0a48-282">Panel</span></span>|  
|<span data-ttu-id="f0a48-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="f0a48-283">PictureBox</span></span>|  
|<span data-ttu-id="f0a48-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="f0a48-284">PrintDocument</span></span>|  
|<span data-ttu-id="f0a48-285">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="f0a48-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="f0a48-286">PrintPreview-Dialog</span><span class="sxs-lookup"><span data-stu-id="f0a48-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="f0a48-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="f0a48-287">PropertyGrid</span></span>|  
|<span data-ttu-id="f0a48-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="f0a48-288">UserControl</span></span>|  
|<span data-ttu-id="f0a48-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="f0a48-289">ToolStrip</span></span>|  
|<span data-ttu-id="f0a48-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f0a48-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="f0a48-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="f0a48-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="f0a48-292">Splitter</span><span class="sxs-lookup"><span data-stu-id="f0a48-292">Splitter</span></span>|  
|<span data-ttu-id="f0a48-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="f0a48-293">RaftingContainer</span></span>|  
|<span data-ttu-id="f0a48-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="f0a48-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f0a48-295">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0a48-295">See also</span></span>

- [<span data-ttu-id="f0a48-296">UI 自動化控制項類型</span><span class="sxs-lookup"><span data-stu-id="f0a48-296">UI Automation Control Types</span></span>](ui-automation-control-types.md)
