---
title: 標準控制項的 UI 自動化支援
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: cbfb640a068a2c1178d321480ee3a112db07b6ac
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463888"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="98070-102">標準控制項的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="98070-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="98070-103">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="98070-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="98070-104">如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱 < [Windows Automation API： 使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="98070-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="98070-105">本主題將說明針對 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 、 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]和 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]架構所開發的應用程式中，其標準控制項的 [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] 支援。</span><span class="sxs-lookup"><span data-stu-id="98070-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="98070-106">Windows Presentation Foundation 控制項</span><span class="sxs-lookup"><span data-stu-id="98070-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="98070-107">提供資訊或支援使用者互動的所有 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 控制項項目，都有 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的完整原生支援。</span><span class="sxs-lookup"><span data-stu-id="98070-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="98070-108">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]看不見其他如面板等的項目。</span><span class="sxs-lookup"><span data-stu-id="98070-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="98070-109">Win32 控制項</span><span class="sxs-lookup"><span data-stu-id="98070-109">Win32 Controls</span></span>  
 <span data-ttu-id="98070-110">大多數 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] 控制項都是透過 UIAutomationClientsideProviders.dll 中的用戶端提供者公開至 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="98070-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="98070-111">此組件會自動註冊為用於使用者介面自動化用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="98070-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="98070-112">完整支援只提供給 ComCtrl32.dll 第 6 版 (隨附於 [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] (含) 以後的版本) 以後的控制項。</span><span class="sxs-lookup"><span data-stu-id="98070-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="98070-113">支援的控制項如下。</span><span class="sxs-lookup"><span data-stu-id="98070-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="98070-114">類別名稱</span><span class="sxs-lookup"><span data-stu-id="98070-114">Class name</span></span>|<span data-ttu-id="98070-115">控制項類型</span><span class="sxs-lookup"><span data-stu-id="98070-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="98070-116">按鈕</span><span class="sxs-lookup"><span data-stu-id="98070-116">Button</span></span>|<span data-ttu-id="98070-117">按鈕</span><span class="sxs-lookup"><span data-stu-id="98070-117">Button</span></span>|  
|<span data-ttu-id="98070-118">按鈕</span><span class="sxs-lookup"><span data-stu-id="98070-118">Button</span></span>|<span data-ttu-id="98070-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="98070-119">RadioButton</span></span>|  
|<span data-ttu-id="98070-120">按鈕</span><span class="sxs-lookup"><span data-stu-id="98070-120">Button</span></span>|<span data-ttu-id="98070-121">群組</span><span class="sxs-lookup"><span data-stu-id="98070-121">Group</span></span>|  
|<span data-ttu-id="98070-122">按鈕</span><span class="sxs-lookup"><span data-stu-id="98070-122">Button</span></span>|<span data-ttu-id="98070-123">核取方塊</span><span class="sxs-lookup"><span data-stu-id="98070-123">CheckBox</span></span>|  
|<span data-ttu-id="98070-124">按鈕</span><span class="sxs-lookup"><span data-stu-id="98070-124">Button</span></span>|<span data-ttu-id="98070-125">超連結</span><span class="sxs-lookup"><span data-stu-id="98070-125">Hyperlink</span></span>|  
|<span data-ttu-id="98070-126">按鈕</span><span class="sxs-lookup"><span data-stu-id="98070-126">Button</span></span>|<span data-ttu-id="98070-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="98070-127">SplitButton</span></span>|  
|<span data-ttu-id="98070-128">按鈕</span><span class="sxs-lookup"><span data-stu-id="98070-128">Button</span></span>|<span data-ttu-id="98070-129">核取方塊</span><span class="sxs-lookup"><span data-stu-id="98070-129">CheckBox</span></span>|  
|<span data-ttu-id="98070-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="98070-130">ComboBoxEx32</span></span>|<span data-ttu-id="98070-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="98070-131">ComboBox</span></span>|  
|<span data-ttu-id="98070-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="98070-132">ComboBox</span></span>|<span data-ttu-id="98070-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="98070-133">ComboBox</span></span>|  
|<span data-ttu-id="98070-134">Edit</span><span class="sxs-lookup"><span data-stu-id="98070-134">Edit</span></span>|<span data-ttu-id="98070-135">文件</span><span class="sxs-lookup"><span data-stu-id="98070-135">Document</span></span>|  
|<span data-ttu-id="98070-136">Edit</span><span class="sxs-lookup"><span data-stu-id="98070-136">Edit</span></span>|<span data-ttu-id="98070-137">Edit</span><span class="sxs-lookup"><span data-stu-id="98070-137">Edit</span></span>|  
|<span data-ttu-id="98070-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="98070-138">SysLink</span></span>|<span data-ttu-id="98070-139">超連結</span><span class="sxs-lookup"><span data-stu-id="98070-139">Hyperlink</span></span>|  
|<span data-ttu-id="98070-140">Static</span><span class="sxs-lookup"><span data-stu-id="98070-140">Static</span></span>|<span data-ttu-id="98070-141">Text</span><span class="sxs-lookup"><span data-stu-id="98070-141">Text</span></span>|  
|<span data-ttu-id="98070-142">Static</span><span class="sxs-lookup"><span data-stu-id="98070-142">Static</span></span>|<span data-ttu-id="98070-143">Image</span><span class="sxs-lookup"><span data-stu-id="98070-143">Image</span></span>|  
|<span data-ttu-id="98070-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="98070-144">SysIPAddress32</span></span>|<span data-ttu-id="98070-145">自訂</span><span class="sxs-lookup"><span data-stu-id="98070-145">Custom</span></span>|  
|<span data-ttu-id="98070-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="98070-146">SysHeader32</span></span>|<span data-ttu-id="98070-147">Header/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="98070-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="98070-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="98070-148">SysListView32</span></span>|<span data-ttu-id="98070-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="98070-149">DataGrid</span></span>|  
|<span data-ttu-id="98070-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="98070-150">SysListView32</span></span>|<span data-ttu-id="98070-151">清單</span><span class="sxs-lookup"><span data-stu-id="98070-151">List</span></span>|  
|<span data-ttu-id="98070-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="98070-152">ListBox</span></span>|<span data-ttu-id="98070-153">清單</span><span class="sxs-lookup"><span data-stu-id="98070-153">List</span></span>|  
|<span data-ttu-id="98070-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="98070-154">ListBox</span></span>|<span data-ttu-id="98070-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="98070-155">ListItem</span></span>|  
|<span data-ttu-id="98070-156">#32768</span><span class="sxs-lookup"><span data-stu-id="98070-156">#32768</span></span>|<span data-ttu-id="98070-157">功能表</span><span class="sxs-lookup"><span data-stu-id="98070-157">Menu</span></span>|  
|<span data-ttu-id="98070-158">#32768</span><span class="sxs-lookup"><span data-stu-id="98070-158">#32768</span></span>|<span data-ttu-id="98070-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="98070-159">MenuItem</span></span>|  
|<span data-ttu-id="98070-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="98070-160">msctls_progress32</span></span>|<span data-ttu-id="98070-161">進度列</span><span class="sxs-lookup"><span data-stu-id="98070-161">ProgressBar</span></span>|  
|<span data-ttu-id="98070-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="98070-162">RichEdit</span></span>|<span data-ttu-id="98070-163">Document.</span><span class="sxs-lookup"><span data-stu-id="98070-163">Document.</span></span> <span data-ttu-id="98070-164">請參閱「注意」。</span><span class="sxs-lookup"><span data-stu-id="98070-164">See note.</span></span>|  
|<span data-ttu-id="98070-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="98070-165">RichEdit20A</span></span>|<span data-ttu-id="98070-166">文件</span><span class="sxs-lookup"><span data-stu-id="98070-166">Document</span></span>|  
|<span data-ttu-id="98070-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="98070-167">RichEdit20W</span></span>|<span data-ttu-id="98070-168">文件</span><span class="sxs-lookup"><span data-stu-id="98070-168">Document</span></span>|  
|<span data-ttu-id="98070-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="98070-169">RichEdit50W</span></span>|<span data-ttu-id="98070-170">文件</span><span class="sxs-lookup"><span data-stu-id="98070-170">Document</span></span>|  
|<span data-ttu-id="98070-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="98070-171">ScrollBar</span></span>|<span data-ttu-id="98070-172">滑桿</span><span class="sxs-lookup"><span data-stu-id="98070-172">Slider</span></span>|  
|<span data-ttu-id="98070-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="98070-173">msctls_trackbar32</span></span>|<span data-ttu-id="98070-174">滑桿</span><span class="sxs-lookup"><span data-stu-id="98070-174">Slider</span></span>|  
|<span data-ttu-id="98070-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="98070-175">msctls_updown32</span></span>|<span data-ttu-id="98070-176">Spinner</span><span class="sxs-lookup"><span data-stu-id="98070-176">Spinner</span></span>|  
|<span data-ttu-id="98070-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="98070-177">msctls_statusbar32</span></span>|<span data-ttu-id="98070-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="98070-178">StatusBar</span></span>|  
|<span data-ttu-id="98070-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="98070-179">SysTabControl32</span></span>|<span data-ttu-id="98070-180">索引標籤</span><span class="sxs-lookup"><span data-stu-id="98070-180">Tab</span></span>|  
|<span data-ttu-id="98070-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="98070-181">SysTabControl32</span></span>|<span data-ttu-id="98070-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="98070-182">TabItem</span></span>|  
|<span data-ttu-id="98070-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="98070-183">ToolbarWindow32</span></span>|<span data-ttu-id="98070-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="98070-184">ToolBar</span></span>|  
|<span data-ttu-id="98070-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="98070-185">ToolbarWindow32</span></span>|<span data-ttu-id="98070-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="98070-186">MenuItem</span></span>|  
|<span data-ttu-id="98070-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="98070-187">ToolbarWindow32</span></span>|<span data-ttu-id="98070-188">按鈕</span><span class="sxs-lookup"><span data-stu-id="98070-188">Button</span></span>|  
|<span data-ttu-id="98070-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="98070-189">ToolbarWindow32</span></span>|<span data-ttu-id="98070-190">核取方塊</span><span class="sxs-lookup"><span data-stu-id="98070-190">CheckBox</span></span>|  
|<span data-ttu-id="98070-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="98070-191">ToolbarWindow32</span></span>|<span data-ttu-id="98070-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="98070-192">RadioButton</span></span>|  
|<span data-ttu-id="98070-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="98070-193">ToolbarWindow32</span></span>|<span data-ttu-id="98070-194">Separator</span><span class="sxs-lookup"><span data-stu-id="98070-194">Separator</span></span>|  
|<span data-ttu-id="98070-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="98070-195">tooltips_class32</span></span>|<span data-ttu-id="98070-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="98070-196">ToolTip</span></span>|  
|<span data-ttu-id="98070-197">#32774</span><span class="sxs-lookup"><span data-stu-id="98070-197">#32774</span></span>|<span data-ttu-id="98070-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="98070-198">ToolTip</span></span>|  
|<span data-ttu-id="98070-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="98070-199">ReBarWindow32</span></span>|<span data-ttu-id="98070-200">工具列</span><span class="sxs-lookup"><span data-stu-id="98070-200">Toolbar</span></span>|  
|<span data-ttu-id="98070-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="98070-201">SysTreeView32</span></span>|<span data-ttu-id="98070-202">樹狀結構</span><span class="sxs-lookup"><span data-stu-id="98070-202">Tree</span></span>|  
|<span data-ttu-id="98070-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="98070-203">SysTreeView32</span></span>|<span data-ttu-id="98070-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="98070-204">TreeItem</span></span>|  
  
 <span data-ttu-id="98070-205">**注意** 只有隨附於 [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] 的版本 (在 RichEd20.dll 3.1 版 (含) 以後版本以及 MsftEdit.dll 4.1 版 (含) 以後版本) 才支援 RichEdit 控制項。</span><span class="sxs-lookup"><span data-stu-id="98070-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="98070-206">不支援的控制項如下。</span><span class="sxs-lookup"><span data-stu-id="98070-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="98070-207">類別名稱</span><span class="sxs-lookup"><span data-stu-id="98070-207">Class name</span></span>|<span data-ttu-id="98070-208">控制項類型</span><span class="sxs-lookup"><span data-stu-id="98070-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="98070-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="98070-209">SysAnimate32</span></span>|<span data-ttu-id="98070-210">Image</span><span class="sxs-lookup"><span data-stu-id="98070-210">Image</span></span>|  
|<span data-ttu-id="98070-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="98070-211">SysPager</span></span>|<span data-ttu-id="98070-212">Spinner</span><span class="sxs-lookup"><span data-stu-id="98070-212">Spinner</span></span>|  
|<span data-ttu-id="98070-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="98070-213">SysDateTimePick32</span></span>|<span data-ttu-id="98070-214">自訂</span><span class="sxs-lookup"><span data-stu-id="98070-214">Custom</span></span>|  
|<span data-ttu-id="98070-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="98070-215">SysMonthCal32</span></span>|<span data-ttu-id="98070-216">行事曆</span><span class="sxs-lookup"><span data-stu-id="98070-216">Calendar</span></span>|  
|<span data-ttu-id="98070-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="98070-217">MS_WINNOTE</span></span>|<span data-ttu-id="98070-218">ToolTip</span><span class="sxs-lookup"><span data-stu-id="98070-218">Tooltip</span></span>|  
|<span data-ttu-id="98070-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="98070-219">VBBubble</span></span>|<span data-ttu-id="98070-220">ToolTip</span><span class="sxs-lookup"><span data-stu-id="98070-220">Tooltip</span></span>|  
|<span data-ttu-id="98070-221">ScrollBar (當做獨立控制項使用時)</span><span class="sxs-lookup"><span data-stu-id="98070-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="98070-222">滑桿</span><span class="sxs-lookup"><span data-stu-id="98070-222">Slider</span></span>|  
|<span data-ttu-id="98070-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="98070-223">SuperGrid</span></span>|<span data-ttu-id="98070-224">自訂</span><span class="sxs-lookup"><span data-stu-id="98070-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="98070-225">Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="98070-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="98070-226">Windows Forms 控制項都會公開至[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]透過 UIAutomationClientsideProviders.dll 中的用戶端提供者。</span><span class="sxs-lookup"><span data-stu-id="98070-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="98070-227">此組件會自動註冊為用於使用者介面自動化用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="98070-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="98070-228">一般而言，Windows Form 的 managed 包裝函式[!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]通用控制項都受到[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="98070-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="98070-229">支援的控制項如下。</span><span class="sxs-lookup"><span data-stu-id="98070-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="98070-230">類別名稱</span><span class="sxs-lookup"><span data-stu-id="98070-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="98070-231">按鈕</span><span class="sxs-lookup"><span data-stu-id="98070-231">Button</span></span>|  
|<span data-ttu-id="98070-232">核取方塊</span><span class="sxs-lookup"><span data-stu-id="98070-232">CheckBox</span></span>|  
|<span data-ttu-id="98070-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="98070-233">CheckedListBox</span></span>|  
|<span data-ttu-id="98070-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="98070-234">ColorDialog</span></span>|  
|<span data-ttu-id="98070-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="98070-235">ComboBox</span></span>|  
|<span data-ttu-id="98070-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="98070-236">FolderBrowser</span></span>|  
|<span data-ttu-id="98070-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="98070-237">FontDialog</span></span>|  
|<span data-ttu-id="98070-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="98070-238">GroupBox</span></span>|  
|<span data-ttu-id="98070-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="98070-239">HscrollBar</span></span>|  
|<span data-ttu-id="98070-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="98070-240">ImageList</span></span>|  
|<span data-ttu-id="98070-241">ThisAddIn</span><span class="sxs-lookup"><span data-stu-id="98070-241">Label</span></span>|  
|<span data-ttu-id="98070-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="98070-242">ListBox</span></span>|  
|<span data-ttu-id="98070-243">ListView</span><span class="sxs-lookup"><span data-stu-id="98070-243">ListView</span></span>|  
|<span data-ttu-id="98070-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="98070-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="98070-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="98070-245">MonthCalendar</span></span>|  
|<span data-ttu-id="98070-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="98070-246">NotifyIcon</span></span>|  
|<span data-ttu-id="98070-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="98070-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="98070-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="98070-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="98070-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="98070-249">PrintDialog</span></span>|  
|<span data-ttu-id="98070-250">進度列</span><span class="sxs-lookup"><span data-stu-id="98070-250">ProgressBar</span></span>|  
|<span data-ttu-id="98070-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="98070-251">RadioButton</span></span>|  
|<span data-ttu-id="98070-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="98070-252">RichTextBox</span></span>|  
|<span data-ttu-id="98070-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="98070-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="98070-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="98070-254">ScrollableControl</span></span>|  
|<span data-ttu-id="98070-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="98070-255">SoundPlayer</span></span>|  
|<span data-ttu-id="98070-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="98070-256">StatusBar</span></span>|  
|<span data-ttu-id="98070-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="98070-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="98070-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="98070-258">TextBox</span></span>|  
|<span data-ttu-id="98070-259">計時器</span><span class="sxs-lookup"><span data-stu-id="98070-259">Timer</span></span>|  
|<span data-ttu-id="98070-260">ToolBar</span><span class="sxs-lookup"><span data-stu-id="98070-260">Toolbar</span></span>|  
|<span data-ttu-id="98070-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="98070-261">ToolTip</span></span>|  
|<span data-ttu-id="98070-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="98070-262">TrackBar</span></span>|  
|<span data-ttu-id="98070-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="98070-263">TreeView</span></span>|  
|<span data-ttu-id="98070-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="98070-264">VscrollBar</span></span>|  
|<span data-ttu-id="98070-265">Web 瀏覽器</span><span class="sxs-lookup"><span data-stu-id="98070-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="98070-266">下列控制項只透過其 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 支援公開至 [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="98070-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="98070-267">部分功能可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="98070-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="98070-268">控制項名稱</span><span class="sxs-lookup"><span data-stu-id="98070-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="98070-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="98070-269">BindingSource</span></span>|  
|<span data-ttu-id="98070-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="98070-270">DataGrid</span></span>|  
|<span data-ttu-id="98070-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="98070-271">DataGridView</span></span>|  
|<span data-ttu-id="98070-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="98070-272">DataNavigator</span></span>|  
|<span data-ttu-id="98070-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="98070-273">DomainUpDown</span></span>|  
|<span data-ttu-id="98070-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="98070-274">ErrorProvider</span></span>|  
|<span data-ttu-id="98070-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="98070-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="98070-276">表單</span><span class="sxs-lookup"><span data-stu-id="98070-276">Form</span></span>|  
|<span data-ttu-id="98070-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="98070-277">LinkLabel</span></span>|  
|<span data-ttu-id="98070-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="98070-278">HelpProvider</span></span>|  
|<span data-ttu-id="98070-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="98070-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="98070-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="98070-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="98070-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="98070-281">NumericUpDown</span></span>|  
|<span data-ttu-id="98070-282">面板</span><span class="sxs-lookup"><span data-stu-id="98070-282">Panel</span></span>|  
|<span data-ttu-id="98070-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="98070-283">PictureBox</span></span>|  
|<span data-ttu-id="98070-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="98070-284">PrintDocument</span></span>|  
|<span data-ttu-id="98070-285">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="98070-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="98070-286">PrintPreview-Dialog</span><span class="sxs-lookup"><span data-stu-id="98070-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="98070-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="98070-287">PropertyGrid</span></span>|  
|<span data-ttu-id="98070-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="98070-288">UserControl</span></span>|  
|<span data-ttu-id="98070-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="98070-289">ToolStrip</span></span>|  
|<span data-ttu-id="98070-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="98070-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="98070-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="98070-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="98070-292">Splitter</span><span class="sxs-lookup"><span data-stu-id="98070-292">Splitter</span></span>|  
|<span data-ttu-id="98070-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="98070-293">RaftingContainer</span></span>|  
|<span data-ttu-id="98070-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="98070-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="98070-295">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98070-295">See Also</span></span>  
 [<span data-ttu-id="98070-296">UI 自動化控制項類型</span><span class="sxs-lookup"><span data-stu-id="98070-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
