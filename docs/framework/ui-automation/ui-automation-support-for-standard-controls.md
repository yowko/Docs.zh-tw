---
title: 標準控制項的 UI 自動化支援
description: 取得針對 Windows Presentation Foundation （WPF）、Win32 和 Windows Forms 所開發的應用程式中，標準控制項的 UI 自動化支援的相關資訊。
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 17916a6978008439e91caae00d8b6f26045f9018
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166115"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="fe402-103">標準控制項的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="fe402-103">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="fe402-104">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="fe402-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="fe402-105">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="fe402-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="fe402-106">本主題包含針對 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 、Win32 和 Windows Forms 架構所開發之應用程式中的標準控制項支援的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fe402-106">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32, and Windows Forms frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="fe402-107">Windows Presentation Foundation 控制項</span><span class="sxs-lookup"><span data-stu-id="fe402-107">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="fe402-108">提供資訊或支援使用者互動的所有 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 控制項項目，都有 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的完整原生支援。</span><span class="sxs-lookup"><span data-stu-id="fe402-108">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="fe402-109">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]看不見其他如面板等的項目。</span><span class="sxs-lookup"><span data-stu-id="fe402-109">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>
## <a name="win32-controls"></a><span data-ttu-id="fe402-110">Win32 控制項</span><span class="sxs-lookup"><span data-stu-id="fe402-110">Win32 Controls</span></span>  
 <span data-ttu-id="fe402-111">大部分的 Win32 控制項都會 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 透過 UIAutomationClientsideProviders.dll 中的用戶端提供者公開至。</span><span class="sxs-lookup"><span data-stu-id="fe402-111">Most Win32 controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="fe402-112">此組件會自動註冊為用於使用者介面自動化用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="fe402-112">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="fe402-113">僅針對第6版*ComCtrl32.dll*的控制項提供完整支援。</span><span class="sxs-lookup"><span data-stu-id="fe402-113">Full support is provided only for controls from version 6 of *ComCtrl32.dll*.</span></span>  
  
 <span data-ttu-id="fe402-114">支援的控制項如下。</span><span class="sxs-lookup"><span data-stu-id="fe402-114">The following controls are supported.</span></span>  
  
|<span data-ttu-id="fe402-115">類別名稱</span><span class="sxs-lookup"><span data-stu-id="fe402-115">Class name</span></span>|<span data-ttu-id="fe402-116">控制項類型</span><span class="sxs-lookup"><span data-stu-id="fe402-116">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="fe402-117">Button</span><span class="sxs-lookup"><span data-stu-id="fe402-117">Button</span></span>|<span data-ttu-id="fe402-118">Button</span><span class="sxs-lookup"><span data-stu-id="fe402-118">Button</span></span>|  
|<span data-ttu-id="fe402-119">Button</span><span class="sxs-lookup"><span data-stu-id="fe402-119">Button</span></span>|<span data-ttu-id="fe402-120">RadioButton</span><span class="sxs-lookup"><span data-stu-id="fe402-120">RadioButton</span></span>|  
|<span data-ttu-id="fe402-121">按鈕</span><span class="sxs-lookup"><span data-stu-id="fe402-121">Button</span></span>|<span data-ttu-id="fe402-122">群組</span><span class="sxs-lookup"><span data-stu-id="fe402-122">Group</span></span>|  
|<span data-ttu-id="fe402-123">按鈕</span><span class="sxs-lookup"><span data-stu-id="fe402-123">Button</span></span>|<span data-ttu-id="fe402-124">CheckBox</span><span class="sxs-lookup"><span data-stu-id="fe402-124">CheckBox</span></span>|  
|<span data-ttu-id="fe402-125">按鈕</span><span class="sxs-lookup"><span data-stu-id="fe402-125">Button</span></span>|<span data-ttu-id="fe402-126">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="fe402-126">Hyperlink</span></span>|  
|<span data-ttu-id="fe402-127">按鈕</span><span class="sxs-lookup"><span data-stu-id="fe402-127">Button</span></span>|<span data-ttu-id="fe402-128">SplitButton</span><span class="sxs-lookup"><span data-stu-id="fe402-128">SplitButton</span></span>|  
|<span data-ttu-id="fe402-129">按鈕</span><span class="sxs-lookup"><span data-stu-id="fe402-129">Button</span></span>|<span data-ttu-id="fe402-130">CheckBox</span><span class="sxs-lookup"><span data-stu-id="fe402-130">CheckBox</span></span>|  
|<span data-ttu-id="fe402-131">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="fe402-131">ComboBoxEx32</span></span>|<span data-ttu-id="fe402-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="fe402-132">ComboBox</span></span>|  
|<span data-ttu-id="fe402-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="fe402-133">ComboBox</span></span>|<span data-ttu-id="fe402-134">ComboBox</span><span class="sxs-lookup"><span data-stu-id="fe402-134">ComboBox</span></span>|  
|<span data-ttu-id="fe402-135">編輯</span><span class="sxs-lookup"><span data-stu-id="fe402-135">Edit</span></span>|<span data-ttu-id="fe402-136">Document</span><span class="sxs-lookup"><span data-stu-id="fe402-136">Document</span></span>|  
|<span data-ttu-id="fe402-137">編輯</span><span class="sxs-lookup"><span data-stu-id="fe402-137">Edit</span></span>|<span data-ttu-id="fe402-138">編輯</span><span class="sxs-lookup"><span data-stu-id="fe402-138">Edit</span></span>|  
|<span data-ttu-id="fe402-139">SysLink</span><span class="sxs-lookup"><span data-stu-id="fe402-139">SysLink</span></span>|<span data-ttu-id="fe402-140">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="fe402-140">Hyperlink</span></span>|  
|<span data-ttu-id="fe402-141">靜態</span><span class="sxs-lookup"><span data-stu-id="fe402-141">Static</span></span>|<span data-ttu-id="fe402-142">Text</span><span class="sxs-lookup"><span data-stu-id="fe402-142">Text</span></span>|  
|<span data-ttu-id="fe402-143">靜態</span><span class="sxs-lookup"><span data-stu-id="fe402-143">Static</span></span>|<span data-ttu-id="fe402-144">映像</span><span class="sxs-lookup"><span data-stu-id="fe402-144">Image</span></span>|  
|<span data-ttu-id="fe402-145">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="fe402-145">SysIPAddress32</span></span>|<span data-ttu-id="fe402-146">自訂</span><span class="sxs-lookup"><span data-stu-id="fe402-146">Custom</span></span>|  
|<span data-ttu-id="fe402-147">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="fe402-147">SysHeader32</span></span>|<span data-ttu-id="fe402-148">Header/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="fe402-148">Header/HeaderItem</span></span>|  
|<span data-ttu-id="fe402-149">SysListView32</span><span class="sxs-lookup"><span data-stu-id="fe402-149">SysListView32</span></span>|<span data-ttu-id="fe402-150">DataGrid</span><span class="sxs-lookup"><span data-stu-id="fe402-150">DataGrid</span></span>|  
|<span data-ttu-id="fe402-151">SysListView32</span><span class="sxs-lookup"><span data-stu-id="fe402-151">SysListView32</span></span>|<span data-ttu-id="fe402-152">清單</span><span class="sxs-lookup"><span data-stu-id="fe402-152">List</span></span>|  
|<span data-ttu-id="fe402-153">ListBox</span><span class="sxs-lookup"><span data-stu-id="fe402-153">ListBox</span></span>|<span data-ttu-id="fe402-154">清單</span><span class="sxs-lookup"><span data-stu-id="fe402-154">List</span></span>|  
|<span data-ttu-id="fe402-155">ListBox</span><span class="sxs-lookup"><span data-stu-id="fe402-155">ListBox</span></span>|<span data-ttu-id="fe402-156">ListItem</span><span class="sxs-lookup"><span data-stu-id="fe402-156">ListItem</span></span>|  
|<span data-ttu-id="fe402-157">#32768</span><span class="sxs-lookup"><span data-stu-id="fe402-157">#32768</span></span>|<span data-ttu-id="fe402-158">功能表</span><span class="sxs-lookup"><span data-stu-id="fe402-158">Menu</span></span>|  
|<span data-ttu-id="fe402-159">#32768</span><span class="sxs-lookup"><span data-stu-id="fe402-159">#32768</span></span>|<span data-ttu-id="fe402-160">MenuItem</span><span class="sxs-lookup"><span data-stu-id="fe402-160">MenuItem</span></span>|  
|<span data-ttu-id="fe402-161">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="fe402-161">msctls_progress32</span></span>|<span data-ttu-id="fe402-162">進度列</span><span class="sxs-lookup"><span data-stu-id="fe402-162">ProgressBar</span></span>|  
|<span data-ttu-id="fe402-163">RichEdit</span><span class="sxs-lookup"><span data-stu-id="fe402-163">RichEdit</span></span>|<span data-ttu-id="fe402-164">文件。</span><span class="sxs-lookup"><span data-stu-id="fe402-164">Document.</span></span> <span data-ttu-id="fe402-165">請參閱附註。</span><span class="sxs-lookup"><span data-stu-id="fe402-165">See note.</span></span>|  
|<span data-ttu-id="fe402-166">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="fe402-166">RichEdit20A</span></span>|<span data-ttu-id="fe402-167">Document</span><span class="sxs-lookup"><span data-stu-id="fe402-167">Document</span></span>|  
|<span data-ttu-id="fe402-168">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="fe402-168">RichEdit20W</span></span>|<span data-ttu-id="fe402-169">Document</span><span class="sxs-lookup"><span data-stu-id="fe402-169">Document</span></span>|  
|<span data-ttu-id="fe402-170">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="fe402-170">RichEdit50W</span></span>|<span data-ttu-id="fe402-171">Document</span><span class="sxs-lookup"><span data-stu-id="fe402-171">Document</span></span>|  
|<span data-ttu-id="fe402-172">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="fe402-172">ScrollBar</span></span>|<span data-ttu-id="fe402-173">滑桿</span><span class="sxs-lookup"><span data-stu-id="fe402-173">Slider</span></span>|  
|<span data-ttu-id="fe402-174">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="fe402-174">msctls_trackbar32</span></span>|<span data-ttu-id="fe402-175">滑桿</span><span class="sxs-lookup"><span data-stu-id="fe402-175">Slider</span></span>|  
|<span data-ttu-id="fe402-176">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="fe402-176">msctls_updown32</span></span>|<span data-ttu-id="fe402-177">Spinner</span><span class="sxs-lookup"><span data-stu-id="fe402-177">Spinner</span></span>|  
|<span data-ttu-id="fe402-178">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="fe402-178">msctls_statusbar32</span></span>|<span data-ttu-id="fe402-179">StatusBar</span><span class="sxs-lookup"><span data-stu-id="fe402-179">StatusBar</span></span>|  
|<span data-ttu-id="fe402-180">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="fe402-180">SysTabControl32</span></span>|<span data-ttu-id="fe402-181">索引標籤</span><span class="sxs-lookup"><span data-stu-id="fe402-181">Tab</span></span>|  
|<span data-ttu-id="fe402-182">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="fe402-182">SysTabControl32</span></span>|<span data-ttu-id="fe402-183">TabItem</span><span class="sxs-lookup"><span data-stu-id="fe402-183">TabItem</span></span>|  
|<span data-ttu-id="fe402-184">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="fe402-184">ToolbarWindow32</span></span>|<span data-ttu-id="fe402-185">ToolBar</span><span class="sxs-lookup"><span data-stu-id="fe402-185">ToolBar</span></span>|  
|<span data-ttu-id="fe402-186">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="fe402-186">ToolbarWindow32</span></span>|<span data-ttu-id="fe402-187">MenuItem</span><span class="sxs-lookup"><span data-stu-id="fe402-187">MenuItem</span></span>|  
|<span data-ttu-id="fe402-188">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="fe402-188">ToolbarWindow32</span></span>|<span data-ttu-id="fe402-189">按鈕</span><span class="sxs-lookup"><span data-stu-id="fe402-189">Button</span></span>|  
|<span data-ttu-id="fe402-190">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="fe402-190">ToolbarWindow32</span></span>|<span data-ttu-id="fe402-191">CheckBox</span><span class="sxs-lookup"><span data-stu-id="fe402-191">CheckBox</span></span>|  
|<span data-ttu-id="fe402-192">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="fe402-192">ToolbarWindow32</span></span>|<span data-ttu-id="fe402-193">RadioButton</span><span class="sxs-lookup"><span data-stu-id="fe402-193">RadioButton</span></span>|  
|<span data-ttu-id="fe402-194">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="fe402-194">ToolbarWindow32</span></span>|<span data-ttu-id="fe402-195">Separator</span><span class="sxs-lookup"><span data-stu-id="fe402-195">Separator</span></span>|  
|<span data-ttu-id="fe402-196">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="fe402-196">tooltips_class32</span></span>|<span data-ttu-id="fe402-197">ToolTip</span><span class="sxs-lookup"><span data-stu-id="fe402-197">ToolTip</span></span>|  
|<span data-ttu-id="fe402-198">#32774</span><span class="sxs-lookup"><span data-stu-id="fe402-198">#32774</span></span>|<span data-ttu-id="fe402-199">ToolTip</span><span class="sxs-lookup"><span data-stu-id="fe402-199">ToolTip</span></span>|  
|<span data-ttu-id="fe402-200">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="fe402-200">ReBarWindow32</span></span>|<span data-ttu-id="fe402-201">工具列</span><span class="sxs-lookup"><span data-stu-id="fe402-201">Toolbar</span></span>|  
|<span data-ttu-id="fe402-202">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="fe402-202">SysTreeView32</span></span>|<span data-ttu-id="fe402-203">樹狀結構</span><span class="sxs-lookup"><span data-stu-id="fe402-203">Tree</span></span>|  
|<span data-ttu-id="fe402-204">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="fe402-204">SysTreeView32</span></span>|<span data-ttu-id="fe402-205">TreeItem</span><span class="sxs-lookup"><span data-stu-id="fe402-205">TreeItem</span></span>|  
  
 <span data-ttu-id="fe402-206">**注意**只有 Windows Vista 隨附的版本（RichEd20.dll 3.1 版和更新版本，以及 MsftEdit.dll 4.1 版和更新版本）才支援 RichEdit 控制項。</span><span class="sxs-lookup"><span data-stu-id="fe402-206">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="fe402-207">不支援的控制項如下。</span><span class="sxs-lookup"><span data-stu-id="fe402-207">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="fe402-208">類別名稱</span><span class="sxs-lookup"><span data-stu-id="fe402-208">Class name</span></span>|<span data-ttu-id="fe402-209">控制項類型</span><span class="sxs-lookup"><span data-stu-id="fe402-209">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="fe402-210">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="fe402-210">SysAnimate32</span></span>|<span data-ttu-id="fe402-211">映像</span><span class="sxs-lookup"><span data-stu-id="fe402-211">Image</span></span>|  
|<span data-ttu-id="fe402-212">SysPager</span><span class="sxs-lookup"><span data-stu-id="fe402-212">SysPager</span></span>|<span data-ttu-id="fe402-213">Spinner</span><span class="sxs-lookup"><span data-stu-id="fe402-213">Spinner</span></span>|  
|<span data-ttu-id="fe402-214">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="fe402-214">SysDateTimePick32</span></span>|<span data-ttu-id="fe402-215">自訂</span><span class="sxs-lookup"><span data-stu-id="fe402-215">Custom</span></span>|  
|<span data-ttu-id="fe402-216">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="fe402-216">SysMonthCal32</span></span>|<span data-ttu-id="fe402-217">行事曆</span><span class="sxs-lookup"><span data-stu-id="fe402-217">Calendar</span></span>|  
|<span data-ttu-id="fe402-218">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="fe402-218">MS_WINNOTE</span></span>|<span data-ttu-id="fe402-219">工具提示</span><span class="sxs-lookup"><span data-stu-id="fe402-219">Tooltip</span></span>|  
|<span data-ttu-id="fe402-220">VBBubble</span><span class="sxs-lookup"><span data-stu-id="fe402-220">VBBubble</span></span>|<span data-ttu-id="fe402-221">工具提示</span><span class="sxs-lookup"><span data-stu-id="fe402-221">Tooltip</span></span>|  
|<span data-ttu-id="fe402-222">ScrollBar (當做獨立控制項使用時)</span><span class="sxs-lookup"><span data-stu-id="fe402-222">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="fe402-223">滑桿</span><span class="sxs-lookup"><span data-stu-id="fe402-223">Slider</span></span>|  
|<span data-ttu-id="fe402-224">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="fe402-224">SuperGrid</span></span>|<span data-ttu-id="fe402-225">自訂</span><span class="sxs-lookup"><span data-stu-id="fe402-225">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>
## <a name="windows-forms-controls"></a><span data-ttu-id="fe402-226">Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="fe402-226">Windows Forms Controls</span></span>  
 <span data-ttu-id="fe402-227">Windows Forms 控制項會 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 透過 UIAutomationClientsideProviders.dll 中的用戶端提供者公開至。</span><span class="sxs-lookup"><span data-stu-id="fe402-227">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="fe402-228">此組件會自動註冊為用於使用者介面自動化用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="fe402-228">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="fe402-229">一般來說，支援 Win32 通用控制項的 managed 包裝函式 Windows Forms 控制項 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fe402-229">Typically, Windows Forms controls that are managed wrappers for Win32 common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="fe402-230">支援的控制項如下。</span><span class="sxs-lookup"><span data-stu-id="fe402-230">The following controls are supported.</span></span>  
  
|<span data-ttu-id="fe402-231">類別名稱</span><span class="sxs-lookup"><span data-stu-id="fe402-231">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="fe402-232">按鈕</span><span class="sxs-lookup"><span data-stu-id="fe402-232">Button</span></span>|  
|<span data-ttu-id="fe402-233">CheckBox</span><span class="sxs-lookup"><span data-stu-id="fe402-233">CheckBox</span></span>|  
|<span data-ttu-id="fe402-234">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="fe402-234">CheckedListBox</span></span>|  
|<span data-ttu-id="fe402-235">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="fe402-235">ColorDialog</span></span>|  
|<span data-ttu-id="fe402-236">ComboBox</span><span class="sxs-lookup"><span data-stu-id="fe402-236">ComboBox</span></span>|  
|<span data-ttu-id="fe402-237">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="fe402-237">FolderBrowser</span></span>|  
|<span data-ttu-id="fe402-238">FontDialog</span><span class="sxs-lookup"><span data-stu-id="fe402-238">FontDialog</span></span>|  
|<span data-ttu-id="fe402-239">GroupBox</span><span class="sxs-lookup"><span data-stu-id="fe402-239">GroupBox</span></span>|  
|<span data-ttu-id="fe402-240">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="fe402-240">HscrollBar</span></span>|  
|<span data-ttu-id="fe402-241">ImageList</span><span class="sxs-lookup"><span data-stu-id="fe402-241">ImageList</span></span>|  
|<span data-ttu-id="fe402-242">標籤</span><span class="sxs-lookup"><span data-stu-id="fe402-242">Label</span></span>|  
|<span data-ttu-id="fe402-243">ListBox</span><span class="sxs-lookup"><span data-stu-id="fe402-243">ListBox</span></span>|  
|<span data-ttu-id="fe402-244">ListView</span><span class="sxs-lookup"><span data-stu-id="fe402-244">ListView</span></span>|  
|<span data-ttu-id="fe402-245">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="fe402-245">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="fe402-246">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="fe402-246">MonthCalendar</span></span>|  
|<span data-ttu-id="fe402-247">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="fe402-247">NotifyIcon</span></span>|  
|<span data-ttu-id="fe402-248">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="fe402-248">OpenFileDialog</span></span>|  
|<span data-ttu-id="fe402-249">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="fe402-249">PageSetupDialog</span></span>|  
|<span data-ttu-id="fe402-250">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="fe402-250">PrintDialog</span></span>|  
|<span data-ttu-id="fe402-251">進度列</span><span class="sxs-lookup"><span data-stu-id="fe402-251">ProgressBar</span></span>|  
|<span data-ttu-id="fe402-252">RadioButton</span><span class="sxs-lookup"><span data-stu-id="fe402-252">RadioButton</span></span>|  
|<span data-ttu-id="fe402-253">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="fe402-253">RichTextBox</span></span>|  
|<span data-ttu-id="fe402-254">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="fe402-254">SaveFileDialog</span></span>|  
|<span data-ttu-id="fe402-255">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="fe402-255">ScrollableControl</span></span>|  
|<span data-ttu-id="fe402-256">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="fe402-256">SoundPlayer</span></span>|  
|<span data-ttu-id="fe402-257">StatusBar</span><span class="sxs-lookup"><span data-stu-id="fe402-257">StatusBar</span></span>|  
|<span data-ttu-id="fe402-258">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="fe402-258">TabControl/TabPage</span></span>|  
|<span data-ttu-id="fe402-259">TextBox</span><span class="sxs-lookup"><span data-stu-id="fe402-259">TextBox</span></span>|  
|<span data-ttu-id="fe402-260">計時器</span><span class="sxs-lookup"><span data-stu-id="fe402-260">Timer</span></span>|  
|<span data-ttu-id="fe402-261">工具列</span><span class="sxs-lookup"><span data-stu-id="fe402-261">Toolbar</span></span>|  
|<span data-ttu-id="fe402-262">ToolTip</span><span class="sxs-lookup"><span data-stu-id="fe402-262">ToolTip</span></span>|  
|<span data-ttu-id="fe402-263">TrackBar</span><span class="sxs-lookup"><span data-stu-id="fe402-263">TrackBar</span></span>|  
|<span data-ttu-id="fe402-264">TreeView</span><span class="sxs-lookup"><span data-stu-id="fe402-264">TreeView</span></span>|  
|<span data-ttu-id="fe402-265">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="fe402-265">VscrollBar</span></span>|  
|<span data-ttu-id="fe402-266">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="fe402-266">WebBrowser</span></span>|  
  
 <span data-ttu-id="fe402-267">下列控制項 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 只會透過其 Microsoft Active Accessibility 的支援來公開。</span><span class="sxs-lookup"><span data-stu-id="fe402-267">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="fe402-268">部分功能可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="fe402-268">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="fe402-269">控制項名稱</span><span class="sxs-lookup"><span data-stu-id="fe402-269">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="fe402-270">BindingSource</span><span class="sxs-lookup"><span data-stu-id="fe402-270">BindingSource</span></span>|  
|<span data-ttu-id="fe402-271">DataGrid</span><span class="sxs-lookup"><span data-stu-id="fe402-271">DataGrid</span></span>|  
|<span data-ttu-id="fe402-272">DataGridView</span><span class="sxs-lookup"><span data-stu-id="fe402-272">DataGridView</span></span>|  
|<span data-ttu-id="fe402-273">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="fe402-273">DataNavigator</span></span>|  
|<span data-ttu-id="fe402-274">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="fe402-274">DomainUpDown</span></span>|  
|<span data-ttu-id="fe402-275">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="fe402-275">ErrorProvider</span></span>|  
|<span data-ttu-id="fe402-276">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="fe402-276">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="fe402-277">表單</span><span class="sxs-lookup"><span data-stu-id="fe402-277">Form</span></span>|  
|<span data-ttu-id="fe402-278">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="fe402-278">LinkLabel</span></span>|  
|<span data-ttu-id="fe402-279">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="fe402-279">HelpProvider</span></span>|  
|<span data-ttu-id="fe402-280">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="fe402-280">MaskedTextBox</span></span>|  
|<span data-ttu-id="fe402-281">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="fe402-281">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="fe402-282">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="fe402-282">NumericUpDown</span></span>|  
|<span data-ttu-id="fe402-283">面板</span><span class="sxs-lookup"><span data-stu-id="fe402-283">Panel</span></span>|  
|<span data-ttu-id="fe402-284">PictureBox</span><span class="sxs-lookup"><span data-stu-id="fe402-284">PictureBox</span></span>|  
|<span data-ttu-id="fe402-285">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="fe402-285">PrintDocument</span></span>|  
|<span data-ttu-id="fe402-286">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="fe402-286">PrintPreview-Control</span></span>|  
|<span data-ttu-id="fe402-287">PrintPreview-Dialog</span><span class="sxs-lookup"><span data-stu-id="fe402-287">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="fe402-288">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="fe402-288">PropertyGrid</span></span>|  
|<span data-ttu-id="fe402-289">UserControl</span><span class="sxs-lookup"><span data-stu-id="fe402-289">UserControl</span></span>|  
|<span data-ttu-id="fe402-290">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="fe402-290">ToolStrip</span></span>|  
|<span data-ttu-id="fe402-291">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="fe402-291">TableLayoutPanel</span></span>|  
|<span data-ttu-id="fe402-292">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="fe402-292">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="fe402-293">Splitter</span><span class="sxs-lookup"><span data-stu-id="fe402-293">Splitter</span></span>|  
|<span data-ttu-id="fe402-294">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="fe402-294">RaftingContainer</span></span>|  
|<span data-ttu-id="fe402-295">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="fe402-295">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fe402-296">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe402-296">See also</span></span>

- [<span data-ttu-id="fe402-297">UI 自動化控制項類型</span><span class="sxs-lookup"><span data-stu-id="fe402-297">UI Automation Control Types</span></span>](ui-automation-control-types.md)
