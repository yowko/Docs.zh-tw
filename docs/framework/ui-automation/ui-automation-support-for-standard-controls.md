---
title: 標準控制項的 UI 自動化支援
description: 取得針對 Windows Presentation Foundation (WPF) 、Win32 和 Windows Forms 所開發的應用程式中，消費者介面自動化支援標準控制項的相關資訊。
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 0a5a0b61a6492d9efb62799fa610859b247cf26e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261068"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="57b0f-103">標準控制項的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="57b0f-103">UI Automation Support for Standard Controls</span></span>

> [!NOTE]
> <span data-ttu-id="57b0f-104">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="57b0f-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="57b0f-105">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="57b0f-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="57b0f-106">本主題包含針對 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 、Win32 和 Windows Forms 架構開發的應用程式中，標準控制項支援的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="57b0f-106">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32, and Windows Forms frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>

## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="57b0f-107">Windows Presentation Foundation 控制項</span><span class="sxs-lookup"><span data-stu-id="57b0f-107">Windows Presentation Foundation Controls</span></span>  

 <span data-ttu-id="57b0f-108">提供資訊或支援使用者互動的所有 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 控制項項目，都有 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的完整原生支援。</span><span class="sxs-lookup"><span data-stu-id="57b0f-108">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="57b0f-109">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]看不見其他如面板等的項目。</span><span class="sxs-lookup"><span data-stu-id="57b0f-109">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>

## <a name="win32-controls"></a><span data-ttu-id="57b0f-110">Win32 控制項</span><span class="sxs-lookup"><span data-stu-id="57b0f-110">Win32 Controls</span></span>  

 <span data-ttu-id="57b0f-111">大部分的 Win32 控制項都是 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 透過 UIAutomationClientsideProviders.dll 中的用戶端提供者來公開。</span><span class="sxs-lookup"><span data-stu-id="57b0f-111">Most Win32 controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="57b0f-112">此組件會自動註冊為用於使用者介面自動化用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="57b0f-112">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="57b0f-113">僅針對 *ComCtrl32.dll* 第6版的控制項提供完整的支援。</span><span class="sxs-lookup"><span data-stu-id="57b0f-113">Full support is provided only for controls from version 6 of *ComCtrl32.dll*.</span></span>  
  
 <span data-ttu-id="57b0f-114">支援的控制項如下。</span><span class="sxs-lookup"><span data-stu-id="57b0f-114">The following controls are supported.</span></span>  
  
|<span data-ttu-id="57b0f-115">類別名稱</span><span class="sxs-lookup"><span data-stu-id="57b0f-115">Class name</span></span>|<span data-ttu-id="57b0f-116">控制項類型</span><span class="sxs-lookup"><span data-stu-id="57b0f-116">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="57b0f-117">Button</span><span class="sxs-lookup"><span data-stu-id="57b0f-117">Button</span></span>|<span data-ttu-id="57b0f-118">Button</span><span class="sxs-lookup"><span data-stu-id="57b0f-118">Button</span></span>|  
|<span data-ttu-id="57b0f-119">Button</span><span class="sxs-lookup"><span data-stu-id="57b0f-119">Button</span></span>|<span data-ttu-id="57b0f-120">RadioButton</span><span class="sxs-lookup"><span data-stu-id="57b0f-120">RadioButton</span></span>|  
|<span data-ttu-id="57b0f-121">按鈕</span><span class="sxs-lookup"><span data-stu-id="57b0f-121">Button</span></span>|<span data-ttu-id="57b0f-122">群組</span><span class="sxs-lookup"><span data-stu-id="57b0f-122">Group</span></span>|  
|<span data-ttu-id="57b0f-123">按鈕</span><span class="sxs-lookup"><span data-stu-id="57b0f-123">Button</span></span>|<span data-ttu-id="57b0f-124">CheckBox</span><span class="sxs-lookup"><span data-stu-id="57b0f-124">CheckBox</span></span>|  
|<span data-ttu-id="57b0f-125">按鈕</span><span class="sxs-lookup"><span data-stu-id="57b0f-125">Button</span></span>|<span data-ttu-id="57b0f-126">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="57b0f-126">Hyperlink</span></span>|  
|<span data-ttu-id="57b0f-127">按鈕</span><span class="sxs-lookup"><span data-stu-id="57b0f-127">Button</span></span>|<span data-ttu-id="57b0f-128">SplitButton</span><span class="sxs-lookup"><span data-stu-id="57b0f-128">SplitButton</span></span>|  
|<span data-ttu-id="57b0f-129">按鈕</span><span class="sxs-lookup"><span data-stu-id="57b0f-129">Button</span></span>|<span data-ttu-id="57b0f-130">CheckBox</span><span class="sxs-lookup"><span data-stu-id="57b0f-130">CheckBox</span></span>|  
|<span data-ttu-id="57b0f-131">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="57b0f-131">ComboBoxEx32</span></span>|<span data-ttu-id="57b0f-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="57b0f-132">ComboBox</span></span>|  
|<span data-ttu-id="57b0f-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="57b0f-133">ComboBox</span></span>|<span data-ttu-id="57b0f-134">ComboBox</span><span class="sxs-lookup"><span data-stu-id="57b0f-134">ComboBox</span></span>|  
|<span data-ttu-id="57b0f-135">編輯</span><span class="sxs-lookup"><span data-stu-id="57b0f-135">Edit</span></span>|<span data-ttu-id="57b0f-136">文件</span><span class="sxs-lookup"><span data-stu-id="57b0f-136">Document</span></span>|  
|<span data-ttu-id="57b0f-137">編輯</span><span class="sxs-lookup"><span data-stu-id="57b0f-137">Edit</span></span>|<span data-ttu-id="57b0f-138">編輯</span><span class="sxs-lookup"><span data-stu-id="57b0f-138">Edit</span></span>|  
|<span data-ttu-id="57b0f-139">SysLink</span><span class="sxs-lookup"><span data-stu-id="57b0f-139">SysLink</span></span>|<span data-ttu-id="57b0f-140">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="57b0f-140">Hyperlink</span></span>|  
|<span data-ttu-id="57b0f-141">靜態</span><span class="sxs-lookup"><span data-stu-id="57b0f-141">Static</span></span>|<span data-ttu-id="57b0f-142">文字</span><span class="sxs-lookup"><span data-stu-id="57b0f-142">Text</span></span>|  
|<span data-ttu-id="57b0f-143">靜態</span><span class="sxs-lookup"><span data-stu-id="57b0f-143">Static</span></span>|<span data-ttu-id="57b0f-144">映像</span><span class="sxs-lookup"><span data-stu-id="57b0f-144">Image</span></span>|  
|<span data-ttu-id="57b0f-145">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="57b0f-145">SysIPAddress32</span></span>|<span data-ttu-id="57b0f-146">自訂</span><span class="sxs-lookup"><span data-stu-id="57b0f-146">Custom</span></span>|  
|<span data-ttu-id="57b0f-147">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="57b0f-147">SysHeader32</span></span>|<span data-ttu-id="57b0f-148">Header/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="57b0f-148">Header/HeaderItem</span></span>|  
|<span data-ttu-id="57b0f-149">SysListView32</span><span class="sxs-lookup"><span data-stu-id="57b0f-149">SysListView32</span></span>|<span data-ttu-id="57b0f-150">DataGrid</span><span class="sxs-lookup"><span data-stu-id="57b0f-150">DataGrid</span></span>|  
|<span data-ttu-id="57b0f-151">SysListView32</span><span class="sxs-lookup"><span data-stu-id="57b0f-151">SysListView32</span></span>|<span data-ttu-id="57b0f-152">清單</span><span class="sxs-lookup"><span data-stu-id="57b0f-152">List</span></span>|  
|<span data-ttu-id="57b0f-153">ListBox</span><span class="sxs-lookup"><span data-stu-id="57b0f-153">ListBox</span></span>|<span data-ttu-id="57b0f-154">清單</span><span class="sxs-lookup"><span data-stu-id="57b0f-154">List</span></span>|  
|<span data-ttu-id="57b0f-155">ListBox</span><span class="sxs-lookup"><span data-stu-id="57b0f-155">ListBox</span></span>|<span data-ttu-id="57b0f-156">ListItem</span><span class="sxs-lookup"><span data-stu-id="57b0f-156">ListItem</span></span>|  
|<span data-ttu-id="57b0f-157">#32768</span><span class="sxs-lookup"><span data-stu-id="57b0f-157">#32768</span></span>|<span data-ttu-id="57b0f-158">功能表</span><span class="sxs-lookup"><span data-stu-id="57b0f-158">Menu</span></span>|  
|<span data-ttu-id="57b0f-159">#32768</span><span class="sxs-lookup"><span data-stu-id="57b0f-159">#32768</span></span>|<span data-ttu-id="57b0f-160">MenuItem</span><span class="sxs-lookup"><span data-stu-id="57b0f-160">MenuItem</span></span>|  
|<span data-ttu-id="57b0f-161">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="57b0f-161">msctls_progress32</span></span>|<span data-ttu-id="57b0f-162">進度列</span><span class="sxs-lookup"><span data-stu-id="57b0f-162">ProgressBar</span></span>|  
|<span data-ttu-id="57b0f-163">RichEdit</span><span class="sxs-lookup"><span data-stu-id="57b0f-163">RichEdit</span></span>|<span data-ttu-id="57b0f-164">文件。</span><span class="sxs-lookup"><span data-stu-id="57b0f-164">Document.</span></span> <span data-ttu-id="57b0f-165">請參閱附註。</span><span class="sxs-lookup"><span data-stu-id="57b0f-165">See note.</span></span>|  
|<span data-ttu-id="57b0f-166">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="57b0f-166">RichEdit20A</span></span>|<span data-ttu-id="57b0f-167">文件</span><span class="sxs-lookup"><span data-stu-id="57b0f-167">Document</span></span>|  
|<span data-ttu-id="57b0f-168">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="57b0f-168">RichEdit20W</span></span>|<span data-ttu-id="57b0f-169">文件</span><span class="sxs-lookup"><span data-stu-id="57b0f-169">Document</span></span>|  
|<span data-ttu-id="57b0f-170">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="57b0f-170">RichEdit50W</span></span>|<span data-ttu-id="57b0f-171">文件</span><span class="sxs-lookup"><span data-stu-id="57b0f-171">Document</span></span>|  
|<span data-ttu-id="57b0f-172">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="57b0f-172">ScrollBar</span></span>|<span data-ttu-id="57b0f-173">滑桿</span><span class="sxs-lookup"><span data-stu-id="57b0f-173">Slider</span></span>|  
|<span data-ttu-id="57b0f-174">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="57b0f-174">msctls_trackbar32</span></span>|<span data-ttu-id="57b0f-175">滑桿</span><span class="sxs-lookup"><span data-stu-id="57b0f-175">Slider</span></span>|  
|<span data-ttu-id="57b0f-176">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="57b0f-176">msctls_updown32</span></span>|<span data-ttu-id="57b0f-177">微調按鈕</span><span class="sxs-lookup"><span data-stu-id="57b0f-177">Spinner</span></span>|  
|<span data-ttu-id="57b0f-178">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="57b0f-178">msctls_statusbar32</span></span>|<span data-ttu-id="57b0f-179">StatusBar</span><span class="sxs-lookup"><span data-stu-id="57b0f-179">StatusBar</span></span>|  
|<span data-ttu-id="57b0f-180">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="57b0f-180">SysTabControl32</span></span>|<span data-ttu-id="57b0f-181">索引標籤</span><span class="sxs-lookup"><span data-stu-id="57b0f-181">Tab</span></span>|  
|<span data-ttu-id="57b0f-182">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="57b0f-182">SysTabControl32</span></span>|<span data-ttu-id="57b0f-183">TabItem</span><span class="sxs-lookup"><span data-stu-id="57b0f-183">TabItem</span></span>|  
|<span data-ttu-id="57b0f-184">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="57b0f-184">ToolbarWindow32</span></span>|<span data-ttu-id="57b0f-185">ToolBar</span><span class="sxs-lookup"><span data-stu-id="57b0f-185">ToolBar</span></span>|  
|<span data-ttu-id="57b0f-186">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="57b0f-186">ToolbarWindow32</span></span>|<span data-ttu-id="57b0f-187">MenuItem</span><span class="sxs-lookup"><span data-stu-id="57b0f-187">MenuItem</span></span>|  
|<span data-ttu-id="57b0f-188">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="57b0f-188">ToolbarWindow32</span></span>|<span data-ttu-id="57b0f-189">按鈕</span><span class="sxs-lookup"><span data-stu-id="57b0f-189">Button</span></span>|  
|<span data-ttu-id="57b0f-190">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="57b0f-190">ToolbarWindow32</span></span>|<span data-ttu-id="57b0f-191">CheckBox</span><span class="sxs-lookup"><span data-stu-id="57b0f-191">CheckBox</span></span>|  
|<span data-ttu-id="57b0f-192">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="57b0f-192">ToolbarWindow32</span></span>|<span data-ttu-id="57b0f-193">RadioButton</span><span class="sxs-lookup"><span data-stu-id="57b0f-193">RadioButton</span></span>|  
|<span data-ttu-id="57b0f-194">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="57b0f-194">ToolbarWindow32</span></span>|<span data-ttu-id="57b0f-195">Separator</span><span class="sxs-lookup"><span data-stu-id="57b0f-195">Separator</span></span>|  
|<span data-ttu-id="57b0f-196">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="57b0f-196">tooltips_class32</span></span>|<span data-ttu-id="57b0f-197">ToolTip</span><span class="sxs-lookup"><span data-stu-id="57b0f-197">ToolTip</span></span>|  
|<span data-ttu-id="57b0f-198">#32774</span><span class="sxs-lookup"><span data-stu-id="57b0f-198">#32774</span></span>|<span data-ttu-id="57b0f-199">ToolTip</span><span class="sxs-lookup"><span data-stu-id="57b0f-199">ToolTip</span></span>|  
|<span data-ttu-id="57b0f-200">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="57b0f-200">ReBarWindow32</span></span>|<span data-ttu-id="57b0f-201">工具列</span><span class="sxs-lookup"><span data-stu-id="57b0f-201">Toolbar</span></span>|  
|<span data-ttu-id="57b0f-202">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="57b0f-202">SysTreeView32</span></span>|<span data-ttu-id="57b0f-203">樹狀結構</span><span class="sxs-lookup"><span data-stu-id="57b0f-203">Tree</span></span>|  
|<span data-ttu-id="57b0f-204">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="57b0f-204">SysTreeView32</span></span>|<span data-ttu-id="57b0f-205">TreeItem</span><span class="sxs-lookup"><span data-stu-id="57b0f-205">TreeItem</span></span>|  
  
 <span data-ttu-id="57b0f-206">**注意** RichEdit 控制項僅支援 Windows Vista (RichEd20.dll 3.1 版和更新版本中隨附的版本，以及 MsftEdit.dll 4.1 版和更新版本的) 。</span><span class="sxs-lookup"><span data-stu-id="57b0f-206">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="57b0f-207">不支援的控制項如下。</span><span class="sxs-lookup"><span data-stu-id="57b0f-207">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="57b0f-208">類別名稱</span><span class="sxs-lookup"><span data-stu-id="57b0f-208">Class name</span></span>|<span data-ttu-id="57b0f-209">控制項類型</span><span class="sxs-lookup"><span data-stu-id="57b0f-209">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="57b0f-210">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="57b0f-210">SysAnimate32</span></span>|<span data-ttu-id="57b0f-211">映像</span><span class="sxs-lookup"><span data-stu-id="57b0f-211">Image</span></span>|  
|<span data-ttu-id="57b0f-212">SysPager</span><span class="sxs-lookup"><span data-stu-id="57b0f-212">SysPager</span></span>|<span data-ttu-id="57b0f-213">微調按鈕</span><span class="sxs-lookup"><span data-stu-id="57b0f-213">Spinner</span></span>|  
|<span data-ttu-id="57b0f-214">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="57b0f-214">SysDateTimePick32</span></span>|<span data-ttu-id="57b0f-215">自訂</span><span class="sxs-lookup"><span data-stu-id="57b0f-215">Custom</span></span>|  
|<span data-ttu-id="57b0f-216">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="57b0f-216">SysMonthCal32</span></span>|<span data-ttu-id="57b0f-217">Calendar</span><span class="sxs-lookup"><span data-stu-id="57b0f-217">Calendar</span></span>|  
|<span data-ttu-id="57b0f-218">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="57b0f-218">MS_WINNOTE</span></span>|<span data-ttu-id="57b0f-219">工具提示</span><span class="sxs-lookup"><span data-stu-id="57b0f-219">Tooltip</span></span>|  
|<span data-ttu-id="57b0f-220">VBBubble</span><span class="sxs-lookup"><span data-stu-id="57b0f-220">VBBubble</span></span>|<span data-ttu-id="57b0f-221">工具提示</span><span class="sxs-lookup"><span data-stu-id="57b0f-221">Tooltip</span></span>|  
|<span data-ttu-id="57b0f-222">ScrollBar (當做獨立控制項使用時)</span><span class="sxs-lookup"><span data-stu-id="57b0f-222">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="57b0f-223">滑桿</span><span class="sxs-lookup"><span data-stu-id="57b0f-223">Slider</span></span>|  
|<span data-ttu-id="57b0f-224">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="57b0f-224">SuperGrid</span></span>|<span data-ttu-id="57b0f-225">自訂</span><span class="sxs-lookup"><span data-stu-id="57b0f-225">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>

## <a name="windows-forms-controls"></a><span data-ttu-id="57b0f-226">Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="57b0f-226">Windows Forms Controls</span></span>  

 <span data-ttu-id="57b0f-227">Windows Forms 的控制項會 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 透過 UIAutomationClientsideProviders.dll 中的用戶端提供者來公開。</span><span class="sxs-lookup"><span data-stu-id="57b0f-227">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="57b0f-228">此組件會自動註冊為用於使用者介面自動化用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="57b0f-228">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="57b0f-229">一般而言，支援 Win32 通用控制項的 managed 包裝函式 Windows Forms 控制項 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="57b0f-229">Typically, Windows Forms controls that are managed wrappers for Win32 common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="57b0f-230">支援的控制項如下。</span><span class="sxs-lookup"><span data-stu-id="57b0f-230">The following controls are supported.</span></span>  
  
|<span data-ttu-id="57b0f-231">類別名稱</span><span class="sxs-lookup"><span data-stu-id="57b0f-231">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="57b0f-232">按鈕</span><span class="sxs-lookup"><span data-stu-id="57b0f-232">Button</span></span>|  
|<span data-ttu-id="57b0f-233">CheckBox</span><span class="sxs-lookup"><span data-stu-id="57b0f-233">CheckBox</span></span>|  
|<span data-ttu-id="57b0f-234">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="57b0f-234">CheckedListBox</span></span>|  
|<span data-ttu-id="57b0f-235">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="57b0f-235">ColorDialog</span></span>|  
|<span data-ttu-id="57b0f-236">ComboBox</span><span class="sxs-lookup"><span data-stu-id="57b0f-236">ComboBox</span></span>|  
|<span data-ttu-id="57b0f-237">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="57b0f-237">FolderBrowser</span></span>|  
|<span data-ttu-id="57b0f-238">FontDialog</span><span class="sxs-lookup"><span data-stu-id="57b0f-238">FontDialog</span></span>|  
|<span data-ttu-id="57b0f-239">GroupBox</span><span class="sxs-lookup"><span data-stu-id="57b0f-239">GroupBox</span></span>|  
|<span data-ttu-id="57b0f-240">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="57b0f-240">HscrollBar</span></span>|  
|<span data-ttu-id="57b0f-241">ImageList</span><span class="sxs-lookup"><span data-stu-id="57b0f-241">ImageList</span></span>|  
|<span data-ttu-id="57b0f-242">標籤</span><span class="sxs-lookup"><span data-stu-id="57b0f-242">Label</span></span>|  
|<span data-ttu-id="57b0f-243">ListBox</span><span class="sxs-lookup"><span data-stu-id="57b0f-243">ListBox</span></span>|  
|<span data-ttu-id="57b0f-244">ListView</span><span class="sxs-lookup"><span data-stu-id="57b0f-244">ListView</span></span>|  
|<span data-ttu-id="57b0f-245">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="57b0f-245">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="57b0f-246">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="57b0f-246">MonthCalendar</span></span>|  
|<span data-ttu-id="57b0f-247">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="57b0f-247">NotifyIcon</span></span>|  
|<span data-ttu-id="57b0f-248">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="57b0f-248">OpenFileDialog</span></span>|  
|<span data-ttu-id="57b0f-249">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="57b0f-249">PageSetupDialog</span></span>|  
|<span data-ttu-id="57b0f-250">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="57b0f-250">PrintDialog</span></span>|  
|<span data-ttu-id="57b0f-251">進度列</span><span class="sxs-lookup"><span data-stu-id="57b0f-251">ProgressBar</span></span>|  
|<span data-ttu-id="57b0f-252">RadioButton</span><span class="sxs-lookup"><span data-stu-id="57b0f-252">RadioButton</span></span>|  
|<span data-ttu-id="57b0f-253">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="57b0f-253">RichTextBox</span></span>|  
|<span data-ttu-id="57b0f-254">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="57b0f-254">SaveFileDialog</span></span>|  
|<span data-ttu-id="57b0f-255">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="57b0f-255">ScrollableControl</span></span>|  
|<span data-ttu-id="57b0f-256">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="57b0f-256">SoundPlayer</span></span>|  
|<span data-ttu-id="57b0f-257">StatusBar</span><span class="sxs-lookup"><span data-stu-id="57b0f-257">StatusBar</span></span>|  
|<span data-ttu-id="57b0f-258">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="57b0f-258">TabControl/TabPage</span></span>|  
|<span data-ttu-id="57b0f-259">TextBox</span><span class="sxs-lookup"><span data-stu-id="57b0f-259">TextBox</span></span>|  
|<span data-ttu-id="57b0f-260">計時器</span><span class="sxs-lookup"><span data-stu-id="57b0f-260">Timer</span></span>|  
|<span data-ttu-id="57b0f-261">工具列</span><span class="sxs-lookup"><span data-stu-id="57b0f-261">Toolbar</span></span>|  
|<span data-ttu-id="57b0f-262">ToolTip</span><span class="sxs-lookup"><span data-stu-id="57b0f-262">ToolTip</span></span>|  
|<span data-ttu-id="57b0f-263">TrackBar</span><span class="sxs-lookup"><span data-stu-id="57b0f-263">TrackBar</span></span>|  
|<span data-ttu-id="57b0f-264">TreeView</span><span class="sxs-lookup"><span data-stu-id="57b0f-264">TreeView</span></span>|  
|<span data-ttu-id="57b0f-265">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="57b0f-265">VscrollBar</span></span>|  
|<span data-ttu-id="57b0f-266">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="57b0f-266">WebBrowser</span></span>|  
  
 <span data-ttu-id="57b0f-267">下列控制項 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 只會透過其對 Microsoft Active Accessibility 的支援公開。</span><span class="sxs-lookup"><span data-stu-id="57b0f-267">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="57b0f-268">部分功能可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="57b0f-268">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="57b0f-269">控制項名稱</span><span class="sxs-lookup"><span data-stu-id="57b0f-269">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="57b0f-270">BindingSource</span><span class="sxs-lookup"><span data-stu-id="57b0f-270">BindingSource</span></span>|  
|<span data-ttu-id="57b0f-271">DataGrid</span><span class="sxs-lookup"><span data-stu-id="57b0f-271">DataGrid</span></span>|  
|<span data-ttu-id="57b0f-272">DataGridView</span><span class="sxs-lookup"><span data-stu-id="57b0f-272">DataGridView</span></span>|  
|<span data-ttu-id="57b0f-273">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="57b0f-273">DataNavigator</span></span>|  
|<span data-ttu-id="57b0f-274">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="57b0f-274">DomainUpDown</span></span>|  
|<span data-ttu-id="57b0f-275">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="57b0f-275">ErrorProvider</span></span>|  
|<span data-ttu-id="57b0f-276">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="57b0f-276">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="57b0f-277">表單</span><span class="sxs-lookup"><span data-stu-id="57b0f-277">Form</span></span>|  
|<span data-ttu-id="57b0f-278">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="57b0f-278">LinkLabel</span></span>|  
|<span data-ttu-id="57b0f-279">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="57b0f-279">HelpProvider</span></span>|  
|<span data-ttu-id="57b0f-280">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="57b0f-280">MaskedTextBox</span></span>|  
|<span data-ttu-id="57b0f-281">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="57b0f-281">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="57b0f-282">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="57b0f-282">NumericUpDown</span></span>|  
|<span data-ttu-id="57b0f-283">面板</span><span class="sxs-lookup"><span data-stu-id="57b0f-283">Panel</span></span>|  
|<span data-ttu-id="57b0f-284">PictureBox</span><span class="sxs-lookup"><span data-stu-id="57b0f-284">PictureBox</span></span>|  
|<span data-ttu-id="57b0f-285">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="57b0f-285">PrintDocument</span></span>|  
|<span data-ttu-id="57b0f-286">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="57b0f-286">PrintPreview-Control</span></span>|  
|<span data-ttu-id="57b0f-287">PrintPreview-Dialog</span><span class="sxs-lookup"><span data-stu-id="57b0f-287">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="57b0f-288">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="57b0f-288">PropertyGrid</span></span>|  
|<span data-ttu-id="57b0f-289">UserControl</span><span class="sxs-lookup"><span data-stu-id="57b0f-289">UserControl</span></span>|  
|<span data-ttu-id="57b0f-290">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="57b0f-290">ToolStrip</span></span>|  
|<span data-ttu-id="57b0f-291">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="57b0f-291">TableLayoutPanel</span></span>|  
|<span data-ttu-id="57b0f-292">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="57b0f-292">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="57b0f-293">Splitter</span><span class="sxs-lookup"><span data-stu-id="57b0f-293">Splitter</span></span>|  
|<span data-ttu-id="57b0f-294">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="57b0f-294">RaftingContainer</span></span>|  
|<span data-ttu-id="57b0f-295">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="57b0f-295">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57b0f-296">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57b0f-296">See also</span></span>

- [<span data-ttu-id="57b0f-297">UI 自動化控制項類型</span><span class="sxs-lookup"><span data-stu-id="57b0f-297">UI Automation Control Types</span></span>](ui-automation-control-types.md)
