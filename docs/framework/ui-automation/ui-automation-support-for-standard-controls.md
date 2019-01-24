---
title: 標準控制項的 UI 自動化支援
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 9c5e4133a3bc1f019ada00299df929c2e3915880
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726581"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="4942e-102">標準控制項的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="4942e-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="4942e-103">這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="4942e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="4942e-104">如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱[Windows Automation API:使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="4942e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="4942e-105">本主題將說明針對 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 、 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]和 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]架構所開發的應用程式中，其標準控制項的 [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] 支援。</span><span class="sxs-lookup"><span data-stu-id="4942e-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="4942e-106">Windows Presentation Foundation 控制項</span><span class="sxs-lookup"><span data-stu-id="4942e-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="4942e-107">提供資訊或支援使用者互動的所有 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 控制項項目，都有 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的完整原生支援。</span><span class="sxs-lookup"><span data-stu-id="4942e-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="4942e-108">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]看不見其他如面板等的項目。</span><span class="sxs-lookup"><span data-stu-id="4942e-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="4942e-109">Win32 控制項</span><span class="sxs-lookup"><span data-stu-id="4942e-109">Win32 Controls</span></span>  
 <span data-ttu-id="4942e-110">大多數 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] 控制項都是透過 UIAutomationClientsideProviders.dll 中的用戶端提供者公開至 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4942e-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="4942e-111">此組件會自動註冊為用於使用者介面自動化用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="4942e-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="4942e-112">完整支援只提供給 ComCtrl32.dll 第 6 版 (隨附於 [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] (含) 以後的版本) 以後的控制項。</span><span class="sxs-lookup"><span data-stu-id="4942e-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="4942e-113">支援的控制項如下。</span><span class="sxs-lookup"><span data-stu-id="4942e-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="4942e-114">類別名稱</span><span class="sxs-lookup"><span data-stu-id="4942e-114">Class name</span></span>|<span data-ttu-id="4942e-115">控制項類型</span><span class="sxs-lookup"><span data-stu-id="4942e-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="4942e-116">按鈕</span><span class="sxs-lookup"><span data-stu-id="4942e-116">Button</span></span>|<span data-ttu-id="4942e-117">按鈕</span><span class="sxs-lookup"><span data-stu-id="4942e-117">Button</span></span>|  
|<span data-ttu-id="4942e-118">按鈕</span><span class="sxs-lookup"><span data-stu-id="4942e-118">Button</span></span>|<span data-ttu-id="4942e-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="4942e-119">RadioButton</span></span>|  
|<span data-ttu-id="4942e-120">按鈕</span><span class="sxs-lookup"><span data-stu-id="4942e-120">Button</span></span>|<span data-ttu-id="4942e-121">群組</span><span class="sxs-lookup"><span data-stu-id="4942e-121">Group</span></span>|  
|<span data-ttu-id="4942e-122">按鈕</span><span class="sxs-lookup"><span data-stu-id="4942e-122">Button</span></span>|<span data-ttu-id="4942e-123">核取方塊</span><span class="sxs-lookup"><span data-stu-id="4942e-123">CheckBox</span></span>|  
|<span data-ttu-id="4942e-124">按鈕</span><span class="sxs-lookup"><span data-stu-id="4942e-124">Button</span></span>|<span data-ttu-id="4942e-125">超連結</span><span class="sxs-lookup"><span data-stu-id="4942e-125">Hyperlink</span></span>|  
|<span data-ttu-id="4942e-126">按鈕</span><span class="sxs-lookup"><span data-stu-id="4942e-126">Button</span></span>|<span data-ttu-id="4942e-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="4942e-127">SplitButton</span></span>|  
|<span data-ttu-id="4942e-128">按鈕</span><span class="sxs-lookup"><span data-stu-id="4942e-128">Button</span></span>|<span data-ttu-id="4942e-129">核取方塊</span><span class="sxs-lookup"><span data-stu-id="4942e-129">CheckBox</span></span>|  
|<span data-ttu-id="4942e-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="4942e-130">ComboBoxEx32</span></span>|<span data-ttu-id="4942e-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="4942e-131">ComboBox</span></span>|  
|<span data-ttu-id="4942e-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="4942e-132">ComboBox</span></span>|<span data-ttu-id="4942e-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="4942e-133">ComboBox</span></span>|  
|<span data-ttu-id="4942e-134">編輯</span><span class="sxs-lookup"><span data-stu-id="4942e-134">Edit</span></span>|<span data-ttu-id="4942e-135">文件</span><span class="sxs-lookup"><span data-stu-id="4942e-135">Document</span></span>|  
|<span data-ttu-id="4942e-136">編輯</span><span class="sxs-lookup"><span data-stu-id="4942e-136">Edit</span></span>|<span data-ttu-id="4942e-137">編輯</span><span class="sxs-lookup"><span data-stu-id="4942e-137">Edit</span></span>|  
|<span data-ttu-id="4942e-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="4942e-138">SysLink</span></span>|<span data-ttu-id="4942e-139">超連結</span><span class="sxs-lookup"><span data-stu-id="4942e-139">Hyperlink</span></span>|  
|<span data-ttu-id="4942e-140">Static</span><span class="sxs-lookup"><span data-stu-id="4942e-140">Static</span></span>|<span data-ttu-id="4942e-141">文字</span><span class="sxs-lookup"><span data-stu-id="4942e-141">Text</span></span>|  
|<span data-ttu-id="4942e-142">Static</span><span class="sxs-lookup"><span data-stu-id="4942e-142">Static</span></span>|<span data-ttu-id="4942e-143">Image</span><span class="sxs-lookup"><span data-stu-id="4942e-143">Image</span></span>|  
|<span data-ttu-id="4942e-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="4942e-144">SysIPAddress32</span></span>|<span data-ttu-id="4942e-145">自訂</span><span class="sxs-lookup"><span data-stu-id="4942e-145">Custom</span></span>|  
|<span data-ttu-id="4942e-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="4942e-146">SysHeader32</span></span>|<span data-ttu-id="4942e-147">Header/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="4942e-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="4942e-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="4942e-148">SysListView32</span></span>|<span data-ttu-id="4942e-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="4942e-149">DataGrid</span></span>|  
|<span data-ttu-id="4942e-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="4942e-150">SysListView32</span></span>|<span data-ttu-id="4942e-151">清單</span><span class="sxs-lookup"><span data-stu-id="4942e-151">List</span></span>|  
|<span data-ttu-id="4942e-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="4942e-152">ListBox</span></span>|<span data-ttu-id="4942e-153">清單</span><span class="sxs-lookup"><span data-stu-id="4942e-153">List</span></span>|  
|<span data-ttu-id="4942e-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="4942e-154">ListBox</span></span>|<span data-ttu-id="4942e-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="4942e-155">ListItem</span></span>|  
|<span data-ttu-id="4942e-156">#32768</span><span class="sxs-lookup"><span data-stu-id="4942e-156">#32768</span></span>|<span data-ttu-id="4942e-157">功能表</span><span class="sxs-lookup"><span data-stu-id="4942e-157">Menu</span></span>|  
|<span data-ttu-id="4942e-158">#32768</span><span class="sxs-lookup"><span data-stu-id="4942e-158">#32768</span></span>|<span data-ttu-id="4942e-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="4942e-159">MenuItem</span></span>|  
|<span data-ttu-id="4942e-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="4942e-160">msctls_progress32</span></span>|<span data-ttu-id="4942e-161">進度列</span><span class="sxs-lookup"><span data-stu-id="4942e-161">ProgressBar</span></span>|  
|<span data-ttu-id="4942e-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="4942e-162">RichEdit</span></span>|<span data-ttu-id="4942e-163">Document.</span><span class="sxs-lookup"><span data-stu-id="4942e-163">Document.</span></span> <span data-ttu-id="4942e-164">請參閱「注意」。</span><span class="sxs-lookup"><span data-stu-id="4942e-164">See note.</span></span>|  
|<span data-ttu-id="4942e-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="4942e-165">RichEdit20A</span></span>|<span data-ttu-id="4942e-166">文件</span><span class="sxs-lookup"><span data-stu-id="4942e-166">Document</span></span>|  
|<span data-ttu-id="4942e-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="4942e-167">RichEdit20W</span></span>|<span data-ttu-id="4942e-168">文件</span><span class="sxs-lookup"><span data-stu-id="4942e-168">Document</span></span>|  
|<span data-ttu-id="4942e-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="4942e-169">RichEdit50W</span></span>|<span data-ttu-id="4942e-170">文件</span><span class="sxs-lookup"><span data-stu-id="4942e-170">Document</span></span>|  
|<span data-ttu-id="4942e-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="4942e-171">ScrollBar</span></span>|<span data-ttu-id="4942e-172">滑桿</span><span class="sxs-lookup"><span data-stu-id="4942e-172">Slider</span></span>|  
|<span data-ttu-id="4942e-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="4942e-173">msctls_trackbar32</span></span>|<span data-ttu-id="4942e-174">滑桿</span><span class="sxs-lookup"><span data-stu-id="4942e-174">Slider</span></span>|  
|<span data-ttu-id="4942e-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="4942e-175">msctls_updown32</span></span>|<span data-ttu-id="4942e-176">Spinner</span><span class="sxs-lookup"><span data-stu-id="4942e-176">Spinner</span></span>|  
|<span data-ttu-id="4942e-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="4942e-177">msctls_statusbar32</span></span>|<span data-ttu-id="4942e-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="4942e-178">StatusBar</span></span>|  
|<span data-ttu-id="4942e-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="4942e-179">SysTabControl32</span></span>|<span data-ttu-id="4942e-180">索引標籤</span><span class="sxs-lookup"><span data-stu-id="4942e-180">Tab</span></span>|  
|<span data-ttu-id="4942e-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="4942e-181">SysTabControl32</span></span>|<span data-ttu-id="4942e-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="4942e-182">TabItem</span></span>|  
|<span data-ttu-id="4942e-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="4942e-183">ToolbarWindow32</span></span>|<span data-ttu-id="4942e-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="4942e-184">ToolBar</span></span>|  
|<span data-ttu-id="4942e-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="4942e-185">ToolbarWindow32</span></span>|<span data-ttu-id="4942e-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="4942e-186">MenuItem</span></span>|  
|<span data-ttu-id="4942e-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="4942e-187">ToolbarWindow32</span></span>|<span data-ttu-id="4942e-188">按鈕</span><span class="sxs-lookup"><span data-stu-id="4942e-188">Button</span></span>|  
|<span data-ttu-id="4942e-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="4942e-189">ToolbarWindow32</span></span>|<span data-ttu-id="4942e-190">核取方塊</span><span class="sxs-lookup"><span data-stu-id="4942e-190">CheckBox</span></span>|  
|<span data-ttu-id="4942e-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="4942e-191">ToolbarWindow32</span></span>|<span data-ttu-id="4942e-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="4942e-192">RadioButton</span></span>|  
|<span data-ttu-id="4942e-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="4942e-193">ToolbarWindow32</span></span>|<span data-ttu-id="4942e-194">Separator</span><span class="sxs-lookup"><span data-stu-id="4942e-194">Separator</span></span>|  
|<span data-ttu-id="4942e-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="4942e-195">tooltips_class32</span></span>|<span data-ttu-id="4942e-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="4942e-196">ToolTip</span></span>|  
|<span data-ttu-id="4942e-197">#32774</span><span class="sxs-lookup"><span data-stu-id="4942e-197">#32774</span></span>|<span data-ttu-id="4942e-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="4942e-198">ToolTip</span></span>|  
|<span data-ttu-id="4942e-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="4942e-199">ReBarWindow32</span></span>|<span data-ttu-id="4942e-200">工具列</span><span class="sxs-lookup"><span data-stu-id="4942e-200">Toolbar</span></span>|  
|<span data-ttu-id="4942e-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="4942e-201">SysTreeView32</span></span>|<span data-ttu-id="4942e-202">樹狀結構</span><span class="sxs-lookup"><span data-stu-id="4942e-202">Tree</span></span>|  
|<span data-ttu-id="4942e-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="4942e-203">SysTreeView32</span></span>|<span data-ttu-id="4942e-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="4942e-204">TreeItem</span></span>|  
  
 <span data-ttu-id="4942e-205">**注意** 只有隨附於 [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] 的版本 (在 RichEd20.dll 3.1 版 (含) 以後版本以及 MsftEdit.dll 4.1 版 (含) 以後版本) 才支援 RichEdit 控制項。</span><span class="sxs-lookup"><span data-stu-id="4942e-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="4942e-206">不支援的控制項如下。</span><span class="sxs-lookup"><span data-stu-id="4942e-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="4942e-207">類別名稱</span><span class="sxs-lookup"><span data-stu-id="4942e-207">Class name</span></span>|<span data-ttu-id="4942e-208">控制項類型</span><span class="sxs-lookup"><span data-stu-id="4942e-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="4942e-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="4942e-209">SysAnimate32</span></span>|<span data-ttu-id="4942e-210">Image</span><span class="sxs-lookup"><span data-stu-id="4942e-210">Image</span></span>|  
|<span data-ttu-id="4942e-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="4942e-211">SysPager</span></span>|<span data-ttu-id="4942e-212">Spinner</span><span class="sxs-lookup"><span data-stu-id="4942e-212">Spinner</span></span>|  
|<span data-ttu-id="4942e-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="4942e-213">SysDateTimePick32</span></span>|<span data-ttu-id="4942e-214">自訂</span><span class="sxs-lookup"><span data-stu-id="4942e-214">Custom</span></span>|  
|<span data-ttu-id="4942e-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="4942e-215">SysMonthCal32</span></span>|<span data-ttu-id="4942e-216">行事曆</span><span class="sxs-lookup"><span data-stu-id="4942e-216">Calendar</span></span>|  
|<span data-ttu-id="4942e-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="4942e-217">MS_WINNOTE</span></span>|<span data-ttu-id="4942e-218">ToolTip</span><span class="sxs-lookup"><span data-stu-id="4942e-218">Tooltip</span></span>|  
|<span data-ttu-id="4942e-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="4942e-219">VBBubble</span></span>|<span data-ttu-id="4942e-220">ToolTip</span><span class="sxs-lookup"><span data-stu-id="4942e-220">Tooltip</span></span>|  
|<span data-ttu-id="4942e-221">ScrollBar (當做獨立控制項使用時)</span><span class="sxs-lookup"><span data-stu-id="4942e-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="4942e-222">滑桿</span><span class="sxs-lookup"><span data-stu-id="4942e-222">Slider</span></span>|  
|<span data-ttu-id="4942e-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="4942e-223">SuperGrid</span></span>|<span data-ttu-id="4942e-224">自訂</span><span class="sxs-lookup"><span data-stu-id="4942e-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="4942e-225">Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="4942e-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="4942e-226">Windows Forms 控制項都會公開至[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]透過 UIAutomationClientsideProviders.dll 中的用戶端提供者。</span><span class="sxs-lookup"><span data-stu-id="4942e-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="4942e-227">此組件會自動註冊為用於使用者介面自動化用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="4942e-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="4942e-228">一般而言，Windows Form 的 managed 包裝函式[!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]通用控制項都受到[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4942e-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="4942e-229">支援的控制項如下。</span><span class="sxs-lookup"><span data-stu-id="4942e-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="4942e-230">類別名稱</span><span class="sxs-lookup"><span data-stu-id="4942e-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="4942e-231">按鈕</span><span class="sxs-lookup"><span data-stu-id="4942e-231">Button</span></span>|  
|<span data-ttu-id="4942e-232">核取方塊</span><span class="sxs-lookup"><span data-stu-id="4942e-232">CheckBox</span></span>|  
|<span data-ttu-id="4942e-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="4942e-233">CheckedListBox</span></span>|  
|<span data-ttu-id="4942e-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="4942e-234">ColorDialog</span></span>|  
|<span data-ttu-id="4942e-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="4942e-235">ComboBox</span></span>|  
|<span data-ttu-id="4942e-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="4942e-236">FolderBrowser</span></span>|  
|<span data-ttu-id="4942e-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="4942e-237">FontDialog</span></span>|  
|<span data-ttu-id="4942e-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="4942e-238">GroupBox</span></span>|  
|<span data-ttu-id="4942e-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="4942e-239">HscrollBar</span></span>|  
|<span data-ttu-id="4942e-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="4942e-240">ImageList</span></span>|  
|<span data-ttu-id="4942e-241">ThisAddIn</span><span class="sxs-lookup"><span data-stu-id="4942e-241">Label</span></span>|  
|<span data-ttu-id="4942e-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="4942e-242">ListBox</span></span>|  
|<span data-ttu-id="4942e-243">ListView</span><span class="sxs-lookup"><span data-stu-id="4942e-243">ListView</span></span>|  
|<span data-ttu-id="4942e-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="4942e-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="4942e-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="4942e-245">MonthCalendar</span></span>|  
|<span data-ttu-id="4942e-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="4942e-246">NotifyIcon</span></span>|  
|<span data-ttu-id="4942e-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="4942e-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="4942e-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="4942e-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="4942e-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="4942e-249">PrintDialog</span></span>|  
|<span data-ttu-id="4942e-250">進度列</span><span class="sxs-lookup"><span data-stu-id="4942e-250">ProgressBar</span></span>|  
|<span data-ttu-id="4942e-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="4942e-251">RadioButton</span></span>|  
|<span data-ttu-id="4942e-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="4942e-252">RichTextBox</span></span>|  
|<span data-ttu-id="4942e-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="4942e-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="4942e-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="4942e-254">ScrollableControl</span></span>|  
|<span data-ttu-id="4942e-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="4942e-255">SoundPlayer</span></span>|  
|<span data-ttu-id="4942e-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="4942e-256">StatusBar</span></span>|  
|<span data-ttu-id="4942e-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="4942e-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="4942e-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="4942e-258">TextBox</span></span>|  
|<span data-ttu-id="4942e-259">計時器</span><span class="sxs-lookup"><span data-stu-id="4942e-259">Timer</span></span>|  
|<span data-ttu-id="4942e-260">ToolBar</span><span class="sxs-lookup"><span data-stu-id="4942e-260">Toolbar</span></span>|  
|<span data-ttu-id="4942e-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="4942e-261">ToolTip</span></span>|  
|<span data-ttu-id="4942e-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="4942e-262">TrackBar</span></span>|  
|<span data-ttu-id="4942e-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="4942e-263">TreeView</span></span>|  
|<span data-ttu-id="4942e-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="4942e-264">VscrollBar</span></span>|  
|<span data-ttu-id="4942e-265">Web 瀏覽器</span><span class="sxs-lookup"><span data-stu-id="4942e-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="4942e-266">下列控制項只透過其 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 支援公開至 [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4942e-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="4942e-267">部分功能可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="4942e-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="4942e-268">控制項名稱</span><span class="sxs-lookup"><span data-stu-id="4942e-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="4942e-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="4942e-269">BindingSource</span></span>|  
|<span data-ttu-id="4942e-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="4942e-270">DataGrid</span></span>|  
|<span data-ttu-id="4942e-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="4942e-271">DataGridView</span></span>|  
|<span data-ttu-id="4942e-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="4942e-272">DataNavigator</span></span>|  
|<span data-ttu-id="4942e-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="4942e-273">DomainUpDown</span></span>|  
|<span data-ttu-id="4942e-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="4942e-274">ErrorProvider</span></span>|  
|<span data-ttu-id="4942e-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="4942e-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="4942e-276">表單</span><span class="sxs-lookup"><span data-stu-id="4942e-276">Form</span></span>|  
|<span data-ttu-id="4942e-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="4942e-277">LinkLabel</span></span>|  
|<span data-ttu-id="4942e-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="4942e-278">HelpProvider</span></span>|  
|<span data-ttu-id="4942e-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="4942e-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="4942e-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="4942e-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="4942e-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="4942e-281">NumericUpDown</span></span>|  
|<span data-ttu-id="4942e-282">面板</span><span class="sxs-lookup"><span data-stu-id="4942e-282">Panel</span></span>|  
|<span data-ttu-id="4942e-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="4942e-283">PictureBox</span></span>|  
|<span data-ttu-id="4942e-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="4942e-284">PrintDocument</span></span>|  
|<span data-ttu-id="4942e-285">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="4942e-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="4942e-286">PrintPreview-Dialog</span><span class="sxs-lookup"><span data-stu-id="4942e-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="4942e-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="4942e-287">PropertyGrid</span></span>|  
|<span data-ttu-id="4942e-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="4942e-288">UserControl</span></span>|  
|<span data-ttu-id="4942e-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="4942e-289">ToolStrip</span></span>|  
|<span data-ttu-id="4942e-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="4942e-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="4942e-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="4942e-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="4942e-292">Splitter</span><span class="sxs-lookup"><span data-stu-id="4942e-292">Splitter</span></span>|  
|<span data-ttu-id="4942e-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="4942e-293">RaftingContainer</span></span>|  
|<span data-ttu-id="4942e-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="4942e-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4942e-295">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4942e-295">See also</span></span>
- [<span data-ttu-id="4942e-296">UI 自動化控制項類型</span><span class="sxs-lookup"><span data-stu-id="4942e-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
