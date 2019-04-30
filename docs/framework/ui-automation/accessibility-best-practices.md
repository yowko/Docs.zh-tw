---
title: 協助工具最佳作法
ms.date: 03/30/2017
helpviewer_keywords:
- best practices for accessibility
- accessibility, best practices for
ms.assetid: e6d5cd98-21a3-4b01-999c-fb953556d0e6
ms.openlocfilehash: a20ecb8fb8d2ea4efdd244c3460dc9c07e22b538
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033224"
---
# <a name="accessibility-best-practices"></a>協助工具最佳作法
> [!NOTE]
>  這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱[Windows Automation API:使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 在控制項或應用程式中實作下列最佳做法，可以改善 [!INCLUDE[TLA#tla_at](../../../includes/tlasharptla-at-md.md)] 裝置使用者的協助工具。 這些最佳做法有許多是著眼於良好的 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 設計。 每個最佳做法包含 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] 控制項或應用程式的實作資訊。 在許多情況下，符合這些最佳做法的工作已經包含在 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 控制項中。  
  
<a name="Programmatic_Access"></a>   
## <a name="programmatic-access"></a>以程式設計方式存取  
 以程式設計方式存取牽涉到要確保所有 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 項目為已標示，屬性值為已公開，且已引發適當的事件。 對於標準的 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 控制項而言，已透過 <xref:System.Windows.Automation.Peers.AutomationPeer>完成這項工作的絕大部分。 自訂控制項需要額外的工作，以確保正確實作程式設計方式的存取。  
  
<a name="Enable_Programmatic_Access_to_all_UI_Elements_and_Text"></a>   
### <a name="enable-programmatic-access-to-all-ui-elements-and-text"></a>啟用以程式設計方式存取所有 UI 項目和文字  
 應該以程式設計方式存取[!INCLUDE[TLA#tla_ui#initcap](../../../includes/tlasharptla-uisharpinitcap-md.md)] 項目。 如果 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 是一種標準的 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 控制項，則在控制項中包含以程式設計方式存取的支援。 如果此控制項為自訂的控制項 (已從通用控制項子類別化或已從控制項子類別化)，則您必須檢查可能需要修改的區域之 <xref:System.Windows.Automation.Peers.AutomationPeer> 實作。  
  
 遵循此最佳做法可讓 [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] 廠商來識別及管理您的 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]產品項目。  
  
<a name="Place_Names__Titles_and_Descriptions_on_UI_Objects_"></a>   
### <a name="place-names-titles-and-descriptions-on-ui-objects-frames-and-pages"></a>在 UI 物件、框架和頁面上放置名稱、標題和描述  
 輔助技術，尤其是螢幕助讀程式，會在巡覽配置中使用標題來了解框架、物件或頁面的位置。 因此，此標題必須具備相當的描述性。 例如若使用者已深入巡覽至某些特定的區域，則「Microsoft 網頁」的網頁標題毫無用處。 描述性的標題對於視力喪失而且依賴螢幕助讀程式的使用者相當重要。 同樣地，對於 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] 控制項而言， <xref:System.Windows.Automation.AutomationProperties.NameProperty> 和 <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> 對 [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] 裝置相當重要。  
  
 遵循此最佳做法可讓 [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)]在範例控制項和應用程式中識別及管理 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 。  
  
<a name="Ensure_Programmatic_Events_are_Triggered_by_all_UI"></a>   
### <a name="ensure-programmatic-events-are-triggered-by-all-ui-activities"></a>確定所有 UI 活動都會觸發程式設計事件  
 遵循此最佳做法可讓 [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)]接聽 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 中的變更，並通知使用者這些變更。  
  
<a name="User_Settings"></a>   
## <a name="user-settings"></a>使用者設定  
 本節中的最佳做法可確保該控制項或應用程式不會覆寫使用者設定。  
  
<a name="Respect_all_System_Wide_Settings_and_do_not_Interfere"></a>   
### <a name="respect-all-system-wide-settings-and-do-not-interfere-with-accessibility-functions"></a>遵循所有系統範圍設定並不會干擾協助工具功能  
 使用者可以使用控制台來設定一些系統範圍的旗標；其他旗標則可透過程式設計方式設定。 不應該由控制項或應用程式變更這些設定。 此外，應用程式必須支援主機作業系統的協助工具設定。  
  
 遵循這個最佳做法可讓使用者設定協助工具設定，並了解這些設定不會由應用程式所變更。  
  
<a name="Visual_UI_Design"></a>   
## <a name="visual-ui-design"></a>視覺 UI 設計  
 本節中的最佳做法確保控制項或應用程式有效率地使用色彩和影像，而且能夠由 [!INCLUDE[TLA2#tla_at#plural](../../../includes/tla2sharptla-atsharpplural-md.md)]所使用。  
  
<a name="Don_t_Hard_Code_Colors"></a>   
### <a name="dont-hard-code-colors"></a>請勿對色彩硬式編碼  
 色盲、視力不佳或使用黑白螢幕的人可能無法使用色彩為硬式編碼的應用程式。  
  
 遵循這個最佳做法可讓使用者根據個人需求調整色彩組合。  
  
<a name="Support_High_Contrast_and_all_System_Display_Attributes"></a>   
### <a name="support-high-contrast-and-all-system-display-attributes"></a>支援高對比和所有系統的顯示屬性  
 應用程式不應中斷或停用使用者選取的系統範圍對比設定、色彩選擇或其他系統範圍的顯示設定和屬性。 使用者採用的系統範圍設定可增強應用程式的可及性，所以應用程式不應停用或忽略它們。 應該在正確的前景背景組合中使用色彩，以提供適當的對比。 不應混用不相關的色彩，而且不應反轉色彩。  
  
 許多使用者需要特定的高對比組合，例如在黑色背景上的白色文字。 如在白色背景上的黑色文字一樣反轉繪製，會造成背景滲出到前景，可能會使某些使用者閱讀困難。  
  
<a name="Ensure_all_UI_Correctly_Scales_by_any_DPI_Setting"></a>   
### <a name="ensure-all-ui-correctly-scales-by-any-dpi-setting"></a>確定所有 UI 正確地依 DPI 設定值縮放比例  
 請確定所有 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 可以正確地依 [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)] 設定值縮放比例。 此外，請確定 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 項目能容納在具有 120 [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)]的 1024 x 768 螢幕中。  
  
<a name="Navigation"></a>   
## <a name="navigation"></a>巡覽  
 本節中的最佳做法可確保已處理控制項和應用程式的巡覽。  
  
<a name="Provide_Keyboard_Interface_for_all_UI_Elements"></a>   
### <a name="provide-keyboard-interface-for-all-ui-elements"></a>提供所有 UI 項目的鍵盤介面  
 特別是經過謹慎計劃的定位停駐點，能讓使用者以另一種方式巡覽 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]。  
  
 應用程式應該提供下列鍵盤介面：  
  
- 使用者可與其互動的所有控制項之定位停駐點，例如按鈕、連結或清單方塊  
  
- 邏輯定位順序  
  
<a name="Show_the_Keyboard_Focus"></a>   
### <a name="show-the-keyboard-focus"></a>顯示鍵盤焦點  
 使用者需要知道哪個物件具有鍵盤焦點，這樣他們才可以預期按鍵的效果。 若要醒目提示鍵盤焦點，請使用色彩、字型或圖形，例如矩形或縮放比例。 若要以可聽見的方式提示鍵盤焦點，請變更音量、音高或音調品質。  
  
 為了避免混淆，應用程式應隱藏所有視覺焦點指標，以及將位於非使用中視窗 (或窗格) 中的選取項目變暗。  
  
 應用程式應以鍵盤焦點執行下列動作：  
  
- 項目應一律具有鍵盤焦點  
  
- 鍵盤焦點應為可見及明顯  
  
- 選取項目及/或具有焦點的項目應該以視覺方式醒目提示  
  
<a name="Support_Navigation_Standards_and_Powerful_Navigation"></a>   
### <a name="support-navigation-standards-and-powerful-navigation-schemes"></a>支援巡覽標準和強大的巡覽配置  
 不同層面的鍵盤巡覽提供不同的方式，讓使用者巡覽 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]。  
  
 應用程式應該提供下列鍵盤介面：  
  
- 快速鍵以及所有命令、功能表和控制項之加上底線的便捷鍵  
  
- 重要連結的鍵盤快速鍵  
  
- 所有功能表項目都有便捷鍵；所有的按鈕都有快速鍵，且所有命令都有快速鍵。  
  
<a name="Do_not_let_Mouse_Location_Interfere_with_Keyboard"></a>   
### <a name="do-not-let-mouse-location-interfere-with-keyboard-navigation"></a>不要讓滑鼠位置干擾鍵盤巡覽  
 滑鼠位置不應干擾鍵盤巡覽。 例如，如果滑鼠置於某個位置，而且使用者正在以鍵盤巡覽，則不應發生滑鼠點選，除非這是由使用者啟始的。  
  
<a name="Multimodal_Interface"></a>   
## <a name="multimodal-interface"></a>多樣式介面  
 本節中的最佳做法確保應用程式 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 包含視覺項目的替代方案。  
  
<a name="Provide_User_Selectable_Equivalents_for_Non_Text"></a>   
### <a name="provide-user-selectable-equivalents-for-non-text-elements"></a>對於非文字項目提供使用者可選取的對等項目  
 對於每個非文字項目，提供文字、文字記錄或音訊描述之使用者可選取的對等項目，如替代文字、標題或視覺化回饋。  
  
 非文字項目涵蓋廣泛的 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 項目，包含：影像、 影像地圖區域、動畫、Applet、框架、指令碼、圖形按鈕、聲音、獨立的音訊檔及視訊。 當非文字項目包含使用者為了解 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]內容而需存取的視覺資訊、語音或一般音訊資訊時，非文字項目會很重要。  
  
<a name="Use_Color_but_also_Provide_Alternatives_to_Color"></a>   
### <a name="use-color-but-also-provide-alternatives-to-color"></a>使用色彩，但是也提供色彩的替代方案  
 請使用色彩來增強及強調，或再次提醒以其他方式顯示的資訊，但請勿單獨使用色彩傳達資訊。 色盲或使用單色顯示器的使用者需要色彩的替代方案。  
  
<a name="Use_Standard_Input_APIs_with_Devices_Independent"></a>   
### <a name="use-standard-input-apis-with-device-independent-calls"></a>藉由與裝置無關的呼叫使用標準輸入的 API  
 與裝置無關的呼叫會確保鍵盤和滑鼠功能是否相等，同時提供 [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] 關於 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]必要的相關資訊。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Automation.Peers>
- [具有佈景主題和 UI 自動化支援範例的 NumericUpDown 自訂控制項](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771573(v=vs.90))
- [鍵盤使用者介面設計指導方針](https://docs.microsoft.com/previous-versions/windows/desktop/dnacc/guidelines-for-keyboard-user-interface-design)
