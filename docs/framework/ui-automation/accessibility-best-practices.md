---
title: 協助工具最佳作法
ms.date: 03/30/2017
helpviewer_keywords:
- best practices for accessibility
- accessibility, best practices for
ms.assetid: e6d5cd98-21a3-4b01-999c-fb953556d0e6
ms.openlocfilehash: a20ecb8fb8d2ea4efdd244c3460dc9c07e22b538
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074231"
---
# <a name="accessibility-best-practices"></a><span data-ttu-id="ac699-102">協助工具最佳作法</span><span class="sxs-lookup"><span data-stu-id="ac699-102">Accessibility Best Practices</span></span>
> [!NOTE]
>  <span data-ttu-id="ac699-103">這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="ac699-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="ac699-104">如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱[Windows Automation API:使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="ac699-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="ac699-105">在控制項或應用程式中實作下列最佳做法，可以改善 [!INCLUDE[TLA#tla_at](../../../includes/tlasharptla-at-md.md)] 裝置使用者的協助工具。</span><span class="sxs-lookup"><span data-stu-id="ac699-105">Implementing the following best practices in controls or applications will improve their accessibility for people who use [!INCLUDE[TLA#tla_at](../../../includes/tlasharptla-at-md.md)] devices.</span></span> <span data-ttu-id="ac699-106">這些最佳做法有許多是著眼於良好的 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 設計。</span><span class="sxs-lookup"><span data-stu-id="ac699-106">Many of these best practices focus on good [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] design.</span></span> <span data-ttu-id="ac699-107">每個最佳做法包含 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] 控制項或應用程式的實作資訊。</span><span class="sxs-lookup"><span data-stu-id="ac699-107">Each best practice includes implementation information for [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] controls or applications.</span></span> <span data-ttu-id="ac699-108">在許多情況下，符合這些最佳做法的工作已經包含在 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 控制項中。</span><span class="sxs-lookup"><span data-stu-id="ac699-108">In many cases, the work to meet these best practices is already included in [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] controls.</span></span>  
  
<a name="Programmatic_Access"></a>   
## <a name="programmatic-access"></a><span data-ttu-id="ac699-109">以程式設計方式存取</span><span class="sxs-lookup"><span data-stu-id="ac699-109">Programmatic Access</span></span>  
 <span data-ttu-id="ac699-110">以程式設計方式存取牽涉到要確保所有 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 項目為已標示，屬性值為已公開，且已引發適當的事件。</span><span class="sxs-lookup"><span data-stu-id="ac699-110">Programmatic access involves ensuring that all [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elements are labeled, property values are exposed, and appropriate events are raised.</span></span> <span data-ttu-id="ac699-111">對於標準的 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 控制項而言，已透過 <xref:System.Windows.Automation.Peers.AutomationPeer>完成這項工作的絕大部分。</span><span class="sxs-lookup"><span data-stu-id="ac699-111">For standard [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] controls, most of this work is already done through <xref:System.Windows.Automation.Peers.AutomationPeer>.</span></span> <span data-ttu-id="ac699-112">自訂控制項需要額外的工作，以確保正確實作程式設計方式的存取。</span><span class="sxs-lookup"><span data-stu-id="ac699-112">Custom controls require additional work to ensure that programmatic access is correctly implemented.</span></span>  
  
<a name="Enable_Programmatic_Access_to_all_UI_Elements_and_Text"></a>   
### <a name="enable-programmatic-access-to-all-ui-elements-and-text"></a><span data-ttu-id="ac699-113">啟用以程式設計方式存取所有 UI 項目和文字</span><span class="sxs-lookup"><span data-stu-id="ac699-113">Enable Programmatic Access to all UI Elements and Text</span></span>  
 [!INCLUDE[TLA#tla_ui#initcap](../../../includes/tlasharptla-uisharpinitcap-md.md)] <span data-ttu-id="ac699-114">項目應該以程式設計方式存取。</span><span class="sxs-lookup"><span data-stu-id="ac699-114">elements should enable programmatic access.</span></span> <span data-ttu-id="ac699-115">如果 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 是一種標準的 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 控制項，則在控制項中包含以程式設計方式存取的支援。</span><span class="sxs-lookup"><span data-stu-id="ac699-115">If the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] is a standard [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control, support for programmatic access is included in the control.</span></span> <span data-ttu-id="ac699-116">如果此控制項為自訂的控制項 (已從通用控制項子類別化或已從控制項子類別化)，則您必須檢查可能需要修改的區域之 <xref:System.Windows.Automation.Peers.AutomationPeer> 實作。</span><span class="sxs-lookup"><span data-stu-id="ac699-116">If the control is a custom control – a control that has been subclassed from a common control or a control that has been subclassed from Control – then you must check the <xref:System.Windows.Automation.Peers.AutomationPeer> implementation for areas that may need modification.</span></span>  
  
 <span data-ttu-id="ac699-117">遵循此最佳做法可讓 [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] 廠商來識別及管理您的 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]產品項目。</span><span class="sxs-lookup"><span data-stu-id="ac699-117">Following this best practice allows [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] vendors to identify and manipulate elements of your product's [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].</span></span>  
  
<a name="Place_Names__Titles_and_Descriptions_on_UI_Objects_"></a>   
### <a name="place-names-titles-and-descriptions-on-ui-objects-frames-and-pages"></a><span data-ttu-id="ac699-118">在 UI 物件、框架和頁面上放置名稱、標題和描述</span><span class="sxs-lookup"><span data-stu-id="ac699-118">Place Names, Titles, and Descriptions on UI Objects, Frames, and Pages</span></span>  
 <span data-ttu-id="ac699-119">輔助技術，尤其是螢幕助讀程式，會在巡覽配置中使用標題來了解框架、物件或頁面的位置。</span><span class="sxs-lookup"><span data-stu-id="ac699-119">Assistive technologies, especially screen readers, use the title to understand the location of the frame, object, or page in the navigation scheme.</span></span> <span data-ttu-id="ac699-120">因此，此標題必須具備相當的描述性。</span><span class="sxs-lookup"><span data-stu-id="ac699-120">Therefore, the title must be very descriptive.</span></span> <span data-ttu-id="ac699-121">例如若使用者已深入巡覽至某些特定的區域，則「Microsoft 網頁」的網頁標題毫無用處。</span><span class="sxs-lookup"><span data-stu-id="ac699-121">For example, a Web page title of "Microsoft Web Page" is useless if the user has navigated deeply into some particular area.</span></span> <span data-ttu-id="ac699-122">描述性的標題對於視力喪失而且依賴螢幕助讀程式的使用者相當重要。</span><span class="sxs-lookup"><span data-stu-id="ac699-122">A descriptive title is critical for users who are blind and depend on screen readers.</span></span> <span data-ttu-id="ac699-123">同樣地，對於 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] 控制項而言， <xref:System.Windows.Automation.AutomationProperties.NameProperty> 和 <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> 對 [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] 裝置相當重要。</span><span class="sxs-lookup"><span data-stu-id="ac699-123">Similarly, for [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] controls, <xref:System.Windows.Automation.AutomationProperties.NameProperty> and <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> are important for [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] devices.</span></span>  
  
 <span data-ttu-id="ac699-124">遵循此最佳做法可讓 [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)]在範例控制項和應用程式中識別及管理 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ac699-124">Following this best practice allows [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)]s to identify and manipulate [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] in sample controls and applications.</span></span>  
  
<a name="Ensure_Programmatic_Events_are_Triggered_by_all_UI"></a>   
### <a name="ensure-programmatic-events-are-triggered-by-all-ui-activities"></a><span data-ttu-id="ac699-125">確定所有 UI 活動都會觸發程式設計事件</span><span class="sxs-lookup"><span data-stu-id="ac699-125">Ensure Programmatic Events Are Triggered by All UI Activities</span></span>  
 <span data-ttu-id="ac699-126">遵循此最佳做法可讓 [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)]接聽 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 中的變更，並通知使用者這些變更。</span><span class="sxs-lookup"><span data-stu-id="ac699-126">Following this best practice allows [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)]s to listen for changes in the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] and notify the user about these changes.</span></span>  
  
<a name="User_Settings"></a>   
## <a name="user-settings"></a><span data-ttu-id="ac699-127">使用者設定</span><span class="sxs-lookup"><span data-stu-id="ac699-127">User Settings</span></span>  
 <span data-ttu-id="ac699-128">本節中的最佳做法可確保該控制項或應用程式不會覆寫使用者設定。</span><span class="sxs-lookup"><span data-stu-id="ac699-128">The best practice in this section ensures that controls or applications do not override user settings.</span></span>  
  
<a name="Respect_all_System_Wide_Settings_and_do_not_Interfere"></a>   
### <a name="respect-all-system-wide-settings-and-do-not-interfere-with-accessibility-functions"></a><span data-ttu-id="ac699-129">遵循所有系統範圍設定並不會干擾協助工具功能</span><span class="sxs-lookup"><span data-stu-id="ac699-129">Respect All System-Wide Settings and Do Not Interfere with Accessibility Functions</span></span>  
 <span data-ttu-id="ac699-130">使用者可以使用控制台來設定一些系統範圍的旗標；其他旗標則可透過程式設計方式設定。</span><span class="sxs-lookup"><span data-stu-id="ac699-130">Users can use the Control Panel to set some system-wide flags; other flags can be set programmatically.</span></span> <span data-ttu-id="ac699-131">不應該由控制項或應用程式變更這些設定。</span><span class="sxs-lookup"><span data-stu-id="ac699-131">These settings should not be changed by controls or applications.</span></span> <span data-ttu-id="ac699-132">此外，應用程式必須支援主機作業系統的協助工具設定。</span><span class="sxs-lookup"><span data-stu-id="ac699-132">Also, applications must support the accessibility settings of their host operating system.</span></span>  
  
 <span data-ttu-id="ac699-133">遵循這個最佳做法可讓使用者設定協助工具設定，並了解這些設定不會由應用程式所變更。</span><span class="sxs-lookup"><span data-stu-id="ac699-133">Following this best practice allows users to set accessibility settings and know that those settings will not be changed by applications.</span></span>  
  
<a name="Visual_UI_Design"></a>   
## <a name="visual-ui-design"></a><span data-ttu-id="ac699-134">視覺 UI 設計</span><span class="sxs-lookup"><span data-stu-id="ac699-134">Visual UI Design</span></span>  
 <span data-ttu-id="ac699-135">本節中的最佳做法確保控制項或應用程式有效率地使用色彩和影像，而且能夠由 [!INCLUDE[TLA2#tla_at#plural](../../../includes/tla2sharptla-atsharpplural-md.md)]所使用。</span><span class="sxs-lookup"><span data-stu-id="ac699-135">Best Practices in this section ensure that controls or applications use color and images effectively and are able to be used by [!INCLUDE[TLA2#tla_at#plural](../../../includes/tla2sharptla-atsharpplural-md.md)].</span></span>  
  
<a name="Don_t_Hard_Code_Colors"></a>   
### <a name="dont-hard-code-colors"></a><span data-ttu-id="ac699-136">請勿對色彩硬式編碼</span><span class="sxs-lookup"><span data-stu-id="ac699-136">Don't Hard-Code Colors</span></span>  
 <span data-ttu-id="ac699-137">色盲、視力不佳或使用黑白螢幕的人可能無法使用色彩為硬式編碼的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ac699-137">People who are color blind, have low vision, or are using a black and white screen might not be able to use applications with hard-coded colors.</span></span>  
  
 <span data-ttu-id="ac699-138">遵循這個最佳做法可讓使用者根據個人需求調整色彩組合。</span><span class="sxs-lookup"><span data-stu-id="ac699-138">Following this best practice allows users to adjust color combinations based on individual needs.</span></span>  
  
<a name="Support_High_Contrast_and_all_System_Display_Attributes"></a>   
### <a name="support-high-contrast-and-all-system-display-attributes"></a><span data-ttu-id="ac699-139">支援高對比和所有系統的顯示屬性</span><span class="sxs-lookup"><span data-stu-id="ac699-139">Support High Contrast and all System Display Attributes</span></span>  
 <span data-ttu-id="ac699-140">應用程式不應中斷或停用使用者選取的系統範圍對比設定、色彩選擇或其他系統範圍的顯示設定和屬性。</span><span class="sxs-lookup"><span data-stu-id="ac699-140">Applications should not disrupt or disable user-selected, system-wide contrast settings, color selections, or other system-wide display settings and attributes.</span></span> <span data-ttu-id="ac699-141">使用者採用的系統範圍設定可增強應用程式的可及性，所以應用程式不應停用或忽略它們。</span><span class="sxs-lookup"><span data-stu-id="ac699-141">System-wide settings adopted by a user enhance the accessibility of applications, so they should not be disabled or disregarded by applications.</span></span> <span data-ttu-id="ac699-142">應該在正確的前景背景組合中使用色彩，以提供適當的對比。</span><span class="sxs-lookup"><span data-stu-id="ac699-142">Color should be used in their correct foreground-on-background combination to provide proper contrast.</span></span> <span data-ttu-id="ac699-143">不應混用不相關的色彩，而且不應反轉色彩。</span><span class="sxs-lookup"><span data-stu-id="ac699-143">Unrelated colors should not be mixed, and colors should not be reversed.</span></span>  
  
 <span data-ttu-id="ac699-144">許多使用者需要特定的高對比組合，例如在黑色背景上的白色文字。</span><span class="sxs-lookup"><span data-stu-id="ac699-144">Many users require specific high-contrast combinations, such as white text on a black background.</span></span> <span data-ttu-id="ac699-145">如在白色背景上的黑色文字一樣反轉繪製，會造成背景滲出到前景，可能會使某些使用者閱讀困難。</span><span class="sxs-lookup"><span data-stu-id="ac699-145">Drawing these reversed, as black text on a white background causes the background to bleed over the foreground and can make reading difficult for some users.</span></span>  
  
<a name="Ensure_all_UI_Correctly_Scales_by_any_DPI_Setting"></a>   
### <a name="ensure-all-ui-correctly-scales-by-any-dpi-setting"></a><span data-ttu-id="ac699-146">確定所有 UI 正確地依 DPI 設定值縮放比例</span><span class="sxs-lookup"><span data-stu-id="ac699-146">Ensure All UI Correctly Scales by Any DPI Setting</span></span>  
 <span data-ttu-id="ac699-147">請確定所有 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 可以正確地依 [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)] 設定值縮放比例。</span><span class="sxs-lookup"><span data-stu-id="ac699-147">Ensure that all [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] can correctly scale by any [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)] setting.</span></span> <span data-ttu-id="ac699-148">此外，請確定 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 項目能容納在具有 120 [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)]的 1024 x 768 螢幕中。</span><span class="sxs-lookup"><span data-stu-id="ac699-148">Also, ensure that [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elements fit in a screen of 1024 x 768 with 120 [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)].</span></span>  
  
<a name="Navigation"></a>   
## <a name="navigation"></a><span data-ttu-id="ac699-149">巡覽</span><span class="sxs-lookup"><span data-stu-id="ac699-149">Navigation</span></span>  
 <span data-ttu-id="ac699-150">本節中的最佳做法可確保已處理控制項和應用程式的巡覽。</span><span class="sxs-lookup"><span data-stu-id="ac699-150">Best Practices in this section ensure that navigation has been addressed for controls and applications.</span></span>  
  
<a name="Provide_Keyboard_Interface_for_all_UI_Elements"></a>   
### <a name="provide-keyboard-interface-for-all-ui-elements"></a><span data-ttu-id="ac699-151">提供所有 UI 項目的鍵盤介面</span><span class="sxs-lookup"><span data-stu-id="ac699-151">Provide Keyboard Interface for All UI Elements</span></span>  
 <span data-ttu-id="ac699-152">特別是經過謹慎計劃的定位停駐點，能讓使用者以另一種方式巡覽 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ac699-152">Tab stops, especially when carefully planned, give users another way to navigate the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="ac699-153">應用程式應該提供下列鍵盤介面：</span><span class="sxs-lookup"><span data-stu-id="ac699-153">Applications should provide the following keyboard interfaces:</span></span>  
  
-   <span data-ttu-id="ac699-154">使用者可與其互動的所有控制項之定位停駐點，例如按鈕、連結或清單方塊</span><span class="sxs-lookup"><span data-stu-id="ac699-154">tab stops for all controls that the user can interact with, such as buttons, links, or list boxes</span></span>  
  
-   <span data-ttu-id="ac699-155">邏輯定位順序</span><span class="sxs-lookup"><span data-stu-id="ac699-155">logical tab order</span></span>  
  
<a name="Show_the_Keyboard_Focus"></a>   
### <a name="show-the-keyboard-focus"></a><span data-ttu-id="ac699-156">顯示鍵盤焦點</span><span class="sxs-lookup"><span data-stu-id="ac699-156">Show the Keyboard Focus</span></span>  
 <span data-ttu-id="ac699-157">使用者需要知道哪個物件具有鍵盤焦點，這樣他們才可以預期按鍵的效果。</span><span class="sxs-lookup"><span data-stu-id="ac699-157">Users need to know which object has the keyboard focus so that they can anticipate the effect of their keystrokes.</span></span> <span data-ttu-id="ac699-158">若要醒目提示鍵盤焦點，請使用色彩、字型或圖形，例如矩形或縮放比例。</span><span class="sxs-lookup"><span data-stu-id="ac699-158">To highlight the keyboard focus, use colors, fonts, or graphics such as rectangles or magnification.</span></span> <span data-ttu-id="ac699-159">若要以可聽見的方式提示鍵盤焦點，請變更音量、音高或音調品質。</span><span class="sxs-lookup"><span data-stu-id="ac699-159">To audibly highlight the keyboard focus, change the volume, pitch or tonal quality.</span></span>  
  
 <span data-ttu-id="ac699-160">為了避免混淆，應用程式應隱藏所有視覺焦點指標，以及將位於非使用中視窗 (或窗格) 中的選取項目變暗。</span><span class="sxs-lookup"><span data-stu-id="ac699-160">To avoid confusion, applications should hide all visual focus indicators and dim selections that are located in inactive windows (or panes).</span></span>  
  
 <span data-ttu-id="ac699-161">應用程式應以鍵盤焦點執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ac699-161">Applications should do the following with keyboard focus:</span></span>  
  
-   <span data-ttu-id="ac699-162">項目應一律具有鍵盤焦點</span><span class="sxs-lookup"><span data-stu-id="ac699-162">one item should always have keyboard focus</span></span>  
  
-   <span data-ttu-id="ac699-163">鍵盤焦點應為可見及明顯</span><span class="sxs-lookup"><span data-stu-id="ac699-163">keyboard focus should be visible and obvious</span></span>  
  
-   <span data-ttu-id="ac699-164">選取項目及/或具有焦點的項目應該以視覺方式醒目提示</span><span class="sxs-lookup"><span data-stu-id="ac699-164">selections and/or focused items should be visually highlighted</span></span>  
  
<a name="Support_Navigation_Standards_and_Powerful_Navigation"></a>   
### <a name="support-navigation-standards-and-powerful-navigation-schemes"></a><span data-ttu-id="ac699-165">支援巡覽標準和強大的巡覽配置</span><span class="sxs-lookup"><span data-stu-id="ac699-165">Support Navigation Standards and Powerful Navigation Schemes</span></span>  
 <span data-ttu-id="ac699-166">不同層面的鍵盤巡覽提供不同的方式，讓使用者巡覽 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ac699-166">Different aspects of keyboard navigation provide different ways for users to navigate the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="ac699-167">應用程式應該提供下列鍵盤介面：</span><span class="sxs-lookup"><span data-stu-id="ac699-167">Applications should provide the following keyboard interfaces:</span></span>  
  
-   <span data-ttu-id="ac699-168">快速鍵以及所有命令、功能表和控制項之加上底線的便捷鍵</span><span class="sxs-lookup"><span data-stu-id="ac699-168">shortcut keys and underlined access keys for all commands, menus and controls</span></span>  
  
-   <span data-ttu-id="ac699-169">重要連結的鍵盤快速鍵</span><span class="sxs-lookup"><span data-stu-id="ac699-169">keyboard shortcuts to important links</span></span>  
  
-   <span data-ttu-id="ac699-170">所有功能表項目都有便捷鍵；所有的按鈕都有快速鍵，且所有命令都有快速鍵。</span><span class="sxs-lookup"><span data-stu-id="ac699-170">all menu items have an access key; all buttons have accelerator keys, all commands have an accelerator key.</span></span>  
  
<a name="Do_not_let_Mouse_Location_Interfere_with_Keyboard"></a>   
### <a name="do-not-let-mouse-location-interfere-with-keyboard-navigation"></a><span data-ttu-id="ac699-171">不要讓滑鼠位置干擾鍵盤巡覽</span><span class="sxs-lookup"><span data-stu-id="ac699-171">Do Not Let Mouse Location Interfere with Keyboard Navigation</span></span>  
 <span data-ttu-id="ac699-172">滑鼠位置不應干擾鍵盤巡覽。</span><span class="sxs-lookup"><span data-stu-id="ac699-172">Mouse location should not interfere with keyboard navigation.</span></span> <span data-ttu-id="ac699-173">例如，如果滑鼠置於某個位置，而且使用者正在以鍵盤巡覽，則不應發生滑鼠點選，除非這是由使用者啟始的。</span><span class="sxs-lookup"><span data-stu-id="ac699-173">For example, if the mouse is positioned someplace and the user is navigating with the keyboard, a mouse click should not happen unless initiated by the user.</span></span>  
  
<a name="Multimodal_Interface"></a>   
## <a name="multimodal-interface"></a><span data-ttu-id="ac699-174">多樣式介面</span><span class="sxs-lookup"><span data-stu-id="ac699-174">Multimodal Interface</span></span>  
 <span data-ttu-id="ac699-175">本節中的最佳做法確保應用程式 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 包含視覺項目的替代方案。</span><span class="sxs-lookup"><span data-stu-id="ac699-175">Best Practices in this section ensure that application [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] includes alternatives for visual elements.</span></span>  
  
<a name="Provide_User_Selectable_Equivalents_for_Non_Text"></a>   
### <a name="provide-user-selectable-equivalents-for-non-text-elements"></a><span data-ttu-id="ac699-176">對於非文字項目提供使用者可選取的對等項目</span><span class="sxs-lookup"><span data-stu-id="ac699-176">Provide User-Selectable Equivalents for Non-Text Elements</span></span>  
 <span data-ttu-id="ac699-177">對於每個非文字項目，提供文字、文字記錄或音訊描述之使用者可選取的對等項目，如替代文字、標題或視覺化回饋。</span><span class="sxs-lookup"><span data-stu-id="ac699-177">For each non-text element, provide a user-selectable equivalent for text, transcripts, or audio descriptions, such as alt text, captions, or visual feedback.</span></span>  
  
 <span data-ttu-id="ac699-178">非文字項目涵蓋廣泛的 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 項目，包含：影像、 影像地圖區域、動畫、Applet、框架、指令碼、圖形按鈕、聲音、獨立的音訊檔及視訊。</span><span class="sxs-lookup"><span data-stu-id="ac699-178">Non-text elements cover a wide range of [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elements including: images, image map regions, animations, applets, frames, scripts, graphical buttons, sounds, stand-alone audio files and video.</span></span> <span data-ttu-id="ac699-179">當非文字項目包含使用者為了解 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]內容而需存取的視覺資訊、語音或一般音訊資訊時，非文字項目會很重要。</span><span class="sxs-lookup"><span data-stu-id="ac699-179">Non-text elements are important when they contain visual information, speech, or general audio information that the user needs access to in order to understand the content of the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].</span></span>  
  
<a name="Use_Color_but_also_Provide_Alternatives_to_Color"></a>   
### <a name="use-color-but-also-provide-alternatives-to-color"></a><span data-ttu-id="ac699-180">使用色彩，但是也提供色彩的替代方案</span><span class="sxs-lookup"><span data-stu-id="ac699-180">Use Color but Also Provide Alternatives to Color</span></span>  
 <span data-ttu-id="ac699-181">請使用色彩來增強及強調，或再次提醒以其他方式顯示的資訊，但請勿單獨使用色彩傳達資訊。</span><span class="sxs-lookup"><span data-stu-id="ac699-181">Use color to enhance, emphasize, or reiterate information shown by other means, but do not communicate information by using color alone.</span></span> <span data-ttu-id="ac699-182">色盲或使用單色顯示器的使用者需要色彩的替代方案。</span><span class="sxs-lookup"><span data-stu-id="ac699-182">Users who are color blind or have a monochrome display need alternatives to color.</span></span>  
  
<a name="Use_Standard_Input_APIs_with_Devices_Independent"></a>   
### <a name="use-standard-input-apis-with-device-independent-calls"></a><span data-ttu-id="ac699-183">藉由與裝置無關的呼叫使用標準輸入的 API</span><span class="sxs-lookup"><span data-stu-id="ac699-183">Use Standard Input APIs with Device-Independent Calls</span></span>  
 <span data-ttu-id="ac699-184">與裝置無關的呼叫會確保鍵盤和滑鼠功能是否相等，同時提供 [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] 關於 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]必要的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ac699-184">Device-independent calls ensure keyboard and mouse feature equality, while providing [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] with needed information about the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac699-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac699-185">See also</span></span>

- <xref:System.Windows.Automation.Peers>
- [<span data-ttu-id="ac699-186">具有佈景主題和 UI 自動化支援範例的 NumericUpDown 自訂控制項</span><span class="sxs-lookup"><span data-stu-id="ac699-186">NumericUpDown Custom Control with Theme and UI Automation Support Sample</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771573(v=vs.90))
- [<span data-ttu-id="ac699-187">鍵盤使用者介面設計指導方針</span><span class="sxs-lookup"><span data-stu-id="ac699-187">Guidelines for Keyboard User Interface Design</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/dnacc/guidelines-for-keyboard-user-interface-design)
