---
title: 協助工具最佳作法
description: 瞭解 .NET 中的協助工具最佳做法。 探索程式設計存取、使用者設定、視覺 UI 設計、導覽和樣式介面。
ms.date: 03/30/2017
helpviewer_keywords:
- best practices for accessibility
- accessibility, best practices for
ms.assetid: e6d5cd98-21a3-4b01-999c-fb953556d0e6
ms.openlocfilehash: 30961c83bdacf816856205322ac2b627d0f2594c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235684"
---
# <a name="accessibility-best-practices"></a><span data-ttu-id="858d3-104">協助工具最佳作法</span><span class="sxs-lookup"><span data-stu-id="858d3-104">Accessibility best practices</span></span>

> [!NOTE]
> <span data-ttu-id="858d3-105">本文適用于想要使用在命名空間中定義之 managed 消費者介面自動化類別的 .NET Framework 開發人員 <xref:System.Windows.Automation> 。</span><span class="sxs-lookup"><span data-stu-id="858d3-105">This article is intended for .NET Framework developers who want to use the managed UI Automation classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="858d3-106">如需消費者介面自動化的最新資訊，請參閱 [Windows AUTOMATION API：消費者介面自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="858d3-106">For the latest information about UI Automation, see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="858d3-107">在控制項或應用程式中執行下列最佳作法，可改善使用輔助技術裝置之人員的協助工具。</span><span class="sxs-lookup"><span data-stu-id="858d3-107">Implementing the following best practices in controls or applications will improve their accessibility for people who use assistive technology devices.</span></span> <span data-ttu-id="858d3-108">其中許多最佳作法都著重于良好的使用者介面 (UI) 設計。</span><span class="sxs-lookup"><span data-stu-id="858d3-108">Many of these best practices focus on good user interface (UI) design.</span></span> <span data-ttu-id="858d3-109">每個最佳做法都包含 Windows Presentation Foundation (WPF) 控制項或應用程式的執行資訊。</span><span class="sxs-lookup"><span data-stu-id="858d3-109">Each best practice includes implementation information for Windows Presentation Foundation (WPF) controls or applications.</span></span> <span data-ttu-id="858d3-110">在許多情況下，符合這些最佳做法的工作已包含在 WPF 控制項中。</span><span class="sxs-lookup"><span data-stu-id="858d3-110">In many cases, the work to meet these best practices is already included in WPF controls.</span></span>  
  
<a name="Programmatic_Access"></a>

## <a name="programmatic-access"></a><span data-ttu-id="858d3-111">程式設計存取</span><span class="sxs-lookup"><span data-stu-id="858d3-111">Programmatic Access</span></span>  

 <span data-ttu-id="858d3-112">以程式設計方式存取包括確保所有 UI 元素都會加上標籤、公開屬性值，以及引發適當的事件。</span><span class="sxs-lookup"><span data-stu-id="858d3-112">Programmatic access involves ensuring that all UI elements are labeled, property values are exposed, and appropriate events are raised.</span></span> <span data-ttu-id="858d3-113">針對標準 WPF 控制項，這項工作大部分都已完成 <xref:System.Windows.Automation.Peers.AutomationPeer> 。</span><span class="sxs-lookup"><span data-stu-id="858d3-113">For standard WPF controls, most of this work is already done through <xref:System.Windows.Automation.Peers.AutomationPeer>.</span></span> <span data-ttu-id="858d3-114">自訂控制項需要額外的工作，以確保正確實作程式設計方式的存取。</span><span class="sxs-lookup"><span data-stu-id="858d3-114">Custom controls require additional work to ensure that programmatic access is correctly implemented.</span></span>  
  
<a name="Enable_Programmatic_Access_to_all_UI_Elements_and_Text"></a>

### <a name="enable-programmatic-access-to-all-ui-elements-and-text"></a><span data-ttu-id="858d3-115">啟用以程式設計方式存取所有 UI 項目和文字</span><span class="sxs-lookup"><span data-stu-id="858d3-115">Enable Programmatic Access to all UI Elements and Text</span></span>  

 <span data-ttu-id="858d3-116">使用者介面 (UI) 元素應啟用以程式設計方式存取。</span><span class="sxs-lookup"><span data-stu-id="858d3-116">User interface (UI) elements should enable programmatic access.</span></span> <span data-ttu-id="858d3-117">如果 UI 是標準 WPF 控制項，則控制項中包含程式設計存取的支援。</span><span class="sxs-lookup"><span data-stu-id="858d3-117">If the UI is a standard WPF control, support for programmatic access is included in the control.</span></span> <span data-ttu-id="858d3-118">如果此控制項為自訂的控制項 (已從通用控制項子類別化或已從控制項子類別化)，則您必須檢查可能需要修改的區域之 <xref:System.Windows.Automation.Peers.AutomationPeer> 實作。</span><span class="sxs-lookup"><span data-stu-id="858d3-118">If the control is a custom control – a control that has been subclassed from a common control or a control that has been subclassed from Control – then you must check the <xref:System.Windows.Automation.Peers.AutomationPeer> implementation for areas that may need modification.</span></span>  
  
 <span data-ttu-id="858d3-119">遵循此最佳做法可讓輔助技術廠商識別和操作您產品 UI 的元素。</span><span class="sxs-lookup"><span data-stu-id="858d3-119">Following this best practice allows assistive technology vendors to identify and manipulate elements of your product's UI.</span></span>  
  
<a name="Place_Names__Titles_and_Descriptions_on_UI_Objects_"></a>

### <a name="place-names-titles-and-descriptions-on-ui-objects-frames-and-pages"></a><span data-ttu-id="858d3-120">在 UI 物件、框架和頁面上放置名稱、標題和描述</span><span class="sxs-lookup"><span data-stu-id="858d3-120">Place Names, Titles, and Descriptions on UI Objects, Frames, and Pages</span></span>  

 <span data-ttu-id="858d3-121">輔助技術，尤其是螢幕助讀程式，會在巡覽配置中使用標題來了解框架、物件或頁面的位置。</span><span class="sxs-lookup"><span data-stu-id="858d3-121">Assistive technologies, especially screen readers, use the title to understand the location of the frame, object, or page in the navigation scheme.</span></span> <span data-ttu-id="858d3-122">因此，標題必須是描述性的。</span><span class="sxs-lookup"><span data-stu-id="858d3-122">Therefore, the title must be descriptive.</span></span> <span data-ttu-id="858d3-123">例如若使用者已深入巡覽至某些特定的區域，則「Microsoft 網頁」的網頁標題毫無用處。</span><span class="sxs-lookup"><span data-stu-id="858d3-123">For example, a Web page title of "Microsoft Web Page" is useless if the user has navigated deeply into some particular area.</span></span> <span data-ttu-id="858d3-124">描述性的標題對於視力喪失而且依賴螢幕助讀程式的使用者相當重要。</span><span class="sxs-lookup"><span data-stu-id="858d3-124">A descriptive title is critical for users who are blind and depend on screen readers.</span></span> <span data-ttu-id="858d3-125">同樣地，對於 WPF 控制項而言，對 <xref:System.Windows.Automation.AutomationProperties.NameProperty> <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> 輔助技術裝置而言很重要。</span><span class="sxs-lookup"><span data-stu-id="858d3-125">Similarly, for WPF controls, <xref:System.Windows.Automation.AutomationProperties.NameProperty> and <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> are important for assistive technology devices.</span></span>  
  
 <span data-ttu-id="858d3-126">遵循這個最佳做法可讓輔助技術識別和操作範例控制項和應用程式中的 UI。</span><span class="sxs-lookup"><span data-stu-id="858d3-126">Following this best practice allows assistive technologies to identify and manipulate UI in sample controls and applications.</span></span>  
  
<a name="Ensure_Programmatic_Events_are_Triggered_by_all_UI"></a>

### <a name="ensure-programmatic-events-are-triggered-by-all-ui-activities"></a><span data-ttu-id="858d3-127">確定所有 UI 活動都會觸發程式設計事件</span><span class="sxs-lookup"><span data-stu-id="858d3-127">Ensure Programmatic Events Are Triggered by All UI Activities</span></span>  

 <span data-ttu-id="858d3-128">遵循此最佳做法可讓輔助技術接聽 UI 中的變更，並通知使用者這些變更。</span><span class="sxs-lookup"><span data-stu-id="858d3-128">Following this best practice allows assistive technologies to listen for changes in the UI and notify the user about these changes.</span></span>  
  
<a name="User_Settings"></a>

## <a name="user-settings"></a><span data-ttu-id="858d3-129">使用者設定</span><span class="sxs-lookup"><span data-stu-id="858d3-129">User Settings</span></span>  

 <span data-ttu-id="858d3-130">本節中的最佳做法可確保該控制項或應用程式不會覆寫使用者設定。</span><span class="sxs-lookup"><span data-stu-id="858d3-130">The best practice in this section ensures that controls or applications do not override user settings.</span></span>  
  
<a name="Respect_all_System_Wide_Settings_and_do_not_Interfere"></a>

### <a name="respect-all-system-wide-settings-and-do-not-interfere-with-accessibility-functions"></a><span data-ttu-id="858d3-131">遵循所有系統範圍設定並不會干擾協助工具功能</span><span class="sxs-lookup"><span data-stu-id="858d3-131">Respect All System-Wide Settings and Do Not Interfere with Accessibility Functions</span></span>  

 <span data-ttu-id="858d3-132">使用者可以使用控制台來設定一些系統範圍的旗標；其他旗標則可透過程式設計方式設定。</span><span class="sxs-lookup"><span data-stu-id="858d3-132">Users can use the Control Panel to set some system-wide flags; other flags can be set programmatically.</span></span> <span data-ttu-id="858d3-133">不應該由控制項或應用程式變更這些設定。</span><span class="sxs-lookup"><span data-stu-id="858d3-133">These settings should not be changed by controls or applications.</span></span> <span data-ttu-id="858d3-134">此外，應用程式必須支援主機作業系統的協助工具設定。</span><span class="sxs-lookup"><span data-stu-id="858d3-134">Also, applications must support the accessibility settings of their host operating system.</span></span>  
  
 <span data-ttu-id="858d3-135">遵循這個最佳做法可讓使用者設定協助工具設定，並了解這些設定不會由應用程式所變更。</span><span class="sxs-lookup"><span data-stu-id="858d3-135">Following this best practice allows users to set accessibility settings and know that those settings will not be changed by applications.</span></span>  
  
<a name="Visual_UI_Design"></a>

## <a name="visual-ui-design"></a><span data-ttu-id="858d3-136">視覺 UI 設計</span><span class="sxs-lookup"><span data-stu-id="858d3-136">Visual UI Design</span></span>  

 <span data-ttu-id="858d3-137">本節中的最佳做法可確保控制項或應用程式有效地使用色彩和影像，並可供輔助技術使用。</span><span class="sxs-lookup"><span data-stu-id="858d3-137">Best Practices in this section ensure that controls or applications use color and images effectively and are able to be used by Assistive technologies.</span></span>  
  
<a name="Don_t_Hard_Code_Colors"></a>

### <a name="dont-hard-code-colors"></a><span data-ttu-id="858d3-138">請勿對色彩硬式編碼</span><span class="sxs-lookup"><span data-stu-id="858d3-138">Don't Hard-Code Colors</span></span>  

 <span data-ttu-id="858d3-139">色盲、視力不佳或使用黑白螢幕的人可能無法使用色彩為硬式編碼的應用程式。</span><span class="sxs-lookup"><span data-stu-id="858d3-139">People who are color blind, have low vision, or are using a black and white screen might not be able to use applications with hard-coded colors.</span></span>  
  
 <span data-ttu-id="858d3-140">遵循這個最佳做法可讓使用者根據個人需求調整色彩組合。</span><span class="sxs-lookup"><span data-stu-id="858d3-140">Following this best practice allows users to adjust color combinations based on individual needs.</span></span>  
  
<a name="Support_High_Contrast_and_all_System_Display_Attributes"></a>

### <a name="support-high-contrast-and-all-system-display-attributes"></a><span data-ttu-id="858d3-141">支援高對比和所有系統的顯示屬性</span><span class="sxs-lookup"><span data-stu-id="858d3-141">Support High Contrast and all System Display Attributes</span></span>  

 <span data-ttu-id="858d3-142">應用程式不應中斷或停用使用者選取的系統範圍對比設定、色彩選擇或其他系統範圍的顯示設定和屬性。</span><span class="sxs-lookup"><span data-stu-id="858d3-142">Applications should not disrupt or disable user-selected, system-wide contrast settings, color selections, or other system-wide display settings and attributes.</span></span> <span data-ttu-id="858d3-143">使用者採用的系統範圍設定可增強應用程式的可及性，所以應用程式不應停用或忽略它們。</span><span class="sxs-lookup"><span data-stu-id="858d3-143">System-wide settings adopted by a user enhance the accessibility of applications, so they should not be disabled or disregarded by applications.</span></span> <span data-ttu-id="858d3-144">應該在正確的前景背景組合中使用色彩，以提供適當的對比。</span><span class="sxs-lookup"><span data-stu-id="858d3-144">Color should be used in their correct foreground-on-background combination to provide proper contrast.</span></span> <span data-ttu-id="858d3-145">請勿混用不相關的色彩，也不要反轉色彩。</span><span class="sxs-lookup"><span data-stu-id="858d3-145">Don't mix unrelated colors, and don't reverse colors.</span></span>  
  
 <span data-ttu-id="858d3-146">許多使用者需要特定的高對比組合，例如在黑色背景上的白色文字。</span><span class="sxs-lookup"><span data-stu-id="858d3-146">Many users require specific high-contrast combinations, such as white text on a black background.</span></span> <span data-ttu-id="858d3-147">如在白色背景上的黑色文字一樣反轉繪製，會造成背景滲出到前景，可能會使某些使用者閱讀困難。</span><span class="sxs-lookup"><span data-stu-id="858d3-147">Drawing these reversed, as black text on a white background causes the background to bleed over the foreground and can make reading difficult for some users.</span></span>  
  
<a name="Ensure_all_UI_Correctly_Scales_by_any_DPI_Setting"></a>

### <a name="ensure-all-ui-correctly-scales-by-any-dpi-setting"></a><span data-ttu-id="858d3-148">確定所有 UI 正確地依 DPI 設定值縮放比例</span><span class="sxs-lookup"><span data-stu-id="858d3-148">Ensure All UI Correctly Scales by Any DPI Setting</span></span>  

 <span data-ttu-id="858d3-149">確定所有的 UI 都能以每英寸的任何點（ (DPI) 設定）正確地調整。</span><span class="sxs-lookup"><span data-stu-id="858d3-149">Ensure that all UI can correctly scale by any dots per inch (dpi) setting.</span></span> <span data-ttu-id="858d3-150">此外，請確定 UI 元素能容納在 1024 x 768 的螢幕中，每英寸都有120點 (DPI) 。</span><span class="sxs-lookup"><span data-stu-id="858d3-150">Also, ensure that UI elements fit in a screen of 1024 x 768 with 120 dots per inch (dpi).</span></span>  
  
<a name="Navigation"></a>

## <a name="navigation"></a><span data-ttu-id="858d3-151">導覽</span><span class="sxs-lookup"><span data-stu-id="858d3-151">Navigation</span></span>  

 <span data-ttu-id="858d3-152">本節中的最佳做法可確保已處理控制項和應用程式的巡覽。</span><span class="sxs-lookup"><span data-stu-id="858d3-152">Best Practices in this section ensure that navigation has been addressed for controls and applications.</span></span>  
  
<a name="Provide_Keyboard_Interface_for_all_UI_Elements"></a>

### <a name="provide-keyboard-interface-for-all-ui-elements"></a><span data-ttu-id="858d3-153">提供所有 UI 項目的鍵盤介面</span><span class="sxs-lookup"><span data-stu-id="858d3-153">Provide Keyboard Interface for All UI Elements</span></span>  

 <span data-ttu-id="858d3-154">Tab 鍵停止，特別是在仔細規劃時，讓使用者可以用另一種方式流覽 UI。</span><span class="sxs-lookup"><span data-stu-id="858d3-154">Tab stops, especially when carefully planned, give users another way to navigate the UI.</span></span>  
  
 <span data-ttu-id="858d3-155">應用程式應該提供下列鍵盤介面：</span><span class="sxs-lookup"><span data-stu-id="858d3-155">Applications should provide the following keyboard interfaces:</span></span>  
  
- <span data-ttu-id="858d3-156">使用者可與其互動的所有控制項之定位停駐點，例如按鈕、連結或清單方塊</span><span class="sxs-lookup"><span data-stu-id="858d3-156">tab stops for all controls that the user can interact with, such as buttons, links, or list boxes</span></span>  
  
- <span data-ttu-id="858d3-157">邏輯定位順序</span><span class="sxs-lookup"><span data-stu-id="858d3-157">logical tab order</span></span>  
  
<a name="Show_the_Keyboard_Focus"></a>

### <a name="show-the-keyboard-focus"></a><span data-ttu-id="858d3-158">顯示鍵盤焦點</span><span class="sxs-lookup"><span data-stu-id="858d3-158">Show the Keyboard Focus</span></span>  

 <span data-ttu-id="858d3-159">使用者需要知道哪個物件具有鍵盤焦點，這樣他們才可以預期按鍵的效果。</span><span class="sxs-lookup"><span data-stu-id="858d3-159">Users need to know which object has the keyboard focus so that they can anticipate the effect of their keystrokes.</span></span> <span data-ttu-id="858d3-160">若要醒目提示鍵盤焦點，請使用色彩、字型或圖形，例如矩形或縮放比例。</span><span class="sxs-lookup"><span data-stu-id="858d3-160">To highlight the keyboard focus, use colors, fonts, or graphics such as rectangles or magnification.</span></span> <span data-ttu-id="858d3-161">若要語音反白顯示鍵盤焦點，請變更音量、音調或色調品質。</span><span class="sxs-lookup"><span data-stu-id="858d3-161">To audibly highlight the keyboard focus, change the volume, pitch, or tonal quality.</span></span>  
  
 <span data-ttu-id="858d3-162">為了避免混淆，應用程式應隱藏所有視覺焦點指標，以及將位於非使用中視窗 (或窗格) 中的選取項目變暗。</span><span class="sxs-lookup"><span data-stu-id="858d3-162">To avoid confusion, applications should hide all visual focus indicators and dim selections that are located in inactive windows (or panes).</span></span>  
  
 <span data-ttu-id="858d3-163">應用程式應以鍵盤焦點執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="858d3-163">Applications should do the following with keyboard focus:</span></span>  
  
- <span data-ttu-id="858d3-164">項目應一律具有鍵盤焦點</span><span class="sxs-lookup"><span data-stu-id="858d3-164">one item should always have keyboard focus</span></span>  
  
- <span data-ttu-id="858d3-165">鍵盤焦點應為可見及明顯</span><span class="sxs-lookup"><span data-stu-id="858d3-165">keyboard focus should be visible and obvious</span></span>  
  
- <span data-ttu-id="858d3-166">選取項目及/或具有焦點的項目應該以視覺方式醒目提示</span><span class="sxs-lookup"><span data-stu-id="858d3-166">selections and/or focused items should be visually highlighted</span></span>  
  
<a name="Support_Navigation_Standards_and_Powerful_Navigation"></a>

### <a name="support-navigation-standards-and-powerful-navigation-schemes"></a><span data-ttu-id="858d3-167">支援巡覽標準和強大的巡覽配置</span><span class="sxs-lookup"><span data-stu-id="858d3-167">Support Navigation Standards and Powerful Navigation Schemes</span></span>  

 <span data-ttu-id="858d3-168">鍵盤導覽的不同層面提供不同的方式讓使用者流覽 UI。</span><span class="sxs-lookup"><span data-stu-id="858d3-168">Different aspects of keyboard navigation provide different ways for users to navigate the UI.</span></span>  
  
 <span data-ttu-id="858d3-169">應用程式應該提供下列鍵盤介面：</span><span class="sxs-lookup"><span data-stu-id="858d3-169">Applications should provide the following keyboard interfaces:</span></span>  
  
- <span data-ttu-id="858d3-170">所有命令、功能表和控制項的快速鍵和加底線的便捷鍵</span><span class="sxs-lookup"><span data-stu-id="858d3-170">shortcut keys and underlined access keys for all commands, menus, and controls</span></span>  
  
- <span data-ttu-id="858d3-171">重要連結的鍵盤快速鍵</span><span class="sxs-lookup"><span data-stu-id="858d3-171">keyboard shortcuts to important links</span></span>  
  
- <span data-ttu-id="858d3-172">所有功能表項目都有便捷鍵；所有的按鈕都有快速鍵，且所有命令都有快速鍵。</span><span class="sxs-lookup"><span data-stu-id="858d3-172">all menu items have an access key; all buttons have accelerator keys, all commands have an accelerator key.</span></span>  
  
<a name="Do_not_let_Mouse_Location_Interfere_with_Keyboard"></a>

### <a name="do-not-let-mouse-location-interfere-with-keyboard-navigation"></a><span data-ttu-id="858d3-173">不要讓滑鼠位置干擾鍵盤巡覽</span><span class="sxs-lookup"><span data-stu-id="858d3-173">Do Not Let Mouse Location Interfere with Keyboard Navigation</span></span>  

 <span data-ttu-id="858d3-174">滑鼠位置不應干擾鍵盤巡覽。</span><span class="sxs-lookup"><span data-stu-id="858d3-174">Mouse location should not interfere with keyboard navigation.</span></span> <span data-ttu-id="858d3-175">例如，如果滑鼠位於某個位置，而使用者正在使用鍵盤流覽，則除非使用者起始滑鼠，否則不應該進行滑鼠點擊。</span><span class="sxs-lookup"><span data-stu-id="858d3-175">For example, if the mouse is positioned some place and the user is navigating with the keyboard, a mouse click should not happen unless initiated by the user.</span></span>  
  
<a name="Multimodal_Interface"></a>

## <a name="multimodal-interface"></a><span data-ttu-id="858d3-176">多樣式介面</span><span class="sxs-lookup"><span data-stu-id="858d3-176">Multimodal Interface</span></span>  

 <span data-ttu-id="858d3-177">本節中的最佳做法可確保應用程式 UI 包含視覺元素的替代方案。</span><span class="sxs-lookup"><span data-stu-id="858d3-177">Best Practices in this section ensure that application UI includes alternatives for visual elements.</span></span>  
  
<a name="Provide_User_Selectable_Equivalents_for_Non_Text"></a>

### <a name="provide-user-selectable-equivalents-for-non-text-elements"></a><span data-ttu-id="858d3-178">對於非文字項目提供使用者可選取的對等項目</span><span class="sxs-lookup"><span data-stu-id="858d3-178">Provide User-Selectable Equivalents for Non-Text Elements</span></span>  

 <span data-ttu-id="858d3-179">對於每個非文字項目，提供文字、文字記錄或音訊描述之使用者可選取的對等項目，如替代文字、標題或視覺化回饋。</span><span class="sxs-lookup"><span data-stu-id="858d3-179">For each non-text element, provide a user-selectable equivalent for text, transcripts, or audio descriptions, such as alt text, captions, or visual feedback.</span></span>  
  
 <span data-ttu-id="858d3-180">非文字元素涵蓋範圍廣泛的 UI 元素，包括：影像、影像地圖區域、動畫、applet、框架、腳本、圖形按鈕、音效、獨立音訊檔案和影片。</span><span class="sxs-lookup"><span data-stu-id="858d3-180">Non-text elements cover a wide range of UI elements including: images, image map regions, animations, applets, frames, scripts, graphical buttons, sounds, stand-alone audio files, and video.</span></span> <span data-ttu-id="858d3-181">如果非文字元素包含使用者需要存取的視覺資訊、語音或一般音訊資訊，以瞭解 UI 的內容，就很重要。</span><span class="sxs-lookup"><span data-stu-id="858d3-181">Non-text elements are important when they contain visual information, speech, or general audio information that the user needs access to in order to understand the content of the UI.</span></span>  
  
<a name="Use_Color_but_also_Provide_Alternatives_to_Color"></a>

### <a name="use-color-but-also-provide-alternatives-to-color"></a><span data-ttu-id="858d3-182">使用色彩，但是也提供色彩的替代方案</span><span class="sxs-lookup"><span data-stu-id="858d3-182">Use Color but Also Provide Alternatives to Color</span></span>  

 <span data-ttu-id="858d3-183">請使用色彩來增強及強調，或再次提醒以其他方式顯示的資訊，但請勿單獨使用色彩傳達資訊。</span><span class="sxs-lookup"><span data-stu-id="858d3-183">Use color to enhance, emphasize, or reiterate information shown by other means, but do not communicate information by using color alone.</span></span> <span data-ttu-id="858d3-184">色盲或使用單色顯示器的使用者需要色彩的替代方案。</span><span class="sxs-lookup"><span data-stu-id="858d3-184">Users who are color blind or have a monochrome display need alternatives to color.</span></span>  
  
<a name="Use_Standard_Input_APIs_with_Devices_Independent"></a>

### <a name="use-standard-input-apis-with-device-independent-calls"></a><span data-ttu-id="858d3-185">藉由與裝置無關的呼叫使用標準輸入的 API</span><span class="sxs-lookup"><span data-stu-id="858d3-185">Use Standard Input APIs with Device-Independent Calls</span></span>  

 <span data-ttu-id="858d3-186">與裝置無關的呼叫會確保鍵盤和滑鼠功能是否相等，同時提供具有 UI 所需資訊的輔助技術。</span><span class="sxs-lookup"><span data-stu-id="858d3-186">Device-independent calls ensure keyboard and mouse feature equality, while providing assistive technology with needed information about the UI.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="858d3-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="858d3-187">See also</span></span>

- <xref:System.Windows.Automation.Peers>
- <span data-ttu-id="858d3-188">[具有佈景主題和 UI 自動化支援的 NumericUpDown 自訂控制項範例](/previous-versions/dotnet/netframework-3.5/ms771573(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="858d3-188">[NumericUpDown Custom Control with Theme and UI Automation Support Sample](/previous-versions/dotnet/netframework-3.5/ms771573(v=vs.90))</span></span>
- [<span data-ttu-id="858d3-189">鍵盤使用者介面設計指導方針</span><span class="sxs-lookup"><span data-stu-id="858d3-189">Guidelines for Keyboard User Interface Design</span></span>](/previous-versions/windows/desktop/dnacc/guidelines-for-keyboard-user-interface-design)
