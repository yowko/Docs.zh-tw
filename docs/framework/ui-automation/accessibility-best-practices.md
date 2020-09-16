---
title: 協助工具最佳作法
description: 瞭解 .NET 中的協助工具最佳做法。 探索程式設計存取、使用者設定、視覺 UI 設計、導覽和樣式介面。
ms.date: 03/30/2017
helpviewer_keywords:
- best practices for accessibility
- accessibility, best practices for
ms.assetid: e6d5cd98-21a3-4b01-999c-fb953556d0e6
ms.openlocfilehash: 1c01cfe8fdfb285ee5cbc586cc0c549365ef72ee
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543143"
---
# <a name="accessibility-best-practices"></a>協助工具最佳作法

> [!NOTE]
> 本文適用于想要使用在命名空間中定義之 managed 消費者介面自動化類別的 .NET Framework 開發人員 <xref:System.Windows.Automation> 。 如需消費者介面自動化的最新資訊，請參閱 [Windows AUTOMATION API：消費者介面自動化](/windows/win32/winauto/entry-uiauto-win32)。  
  
 在控制項或應用程式中執行下列最佳作法，可改善使用輔助技術裝置之人員的協助工具。 其中許多最佳作法都著重于良好的使用者介面 (UI) 設計。 每個最佳做法都包含 Windows Presentation Foundation (WPF) 控制項或應用程式的執行資訊。 在許多情況下，符合這些最佳做法的工作已包含在 WPF 控制項中。  
  
<a name="Programmatic_Access"></a>
## <a name="programmatic-access"></a>程式設計存取  
 以程式設計方式存取包括確保所有 UI 元素都會加上標籤、公開屬性值，以及引發適當的事件。 針對標準 WPF 控制項，這項工作大部分都已完成 <xref:System.Windows.Automation.Peers.AutomationPeer> 。 自訂控制項需要額外的工作，以確保正確實作程式設計方式的存取。  
  
<a name="Enable_Programmatic_Access_to_all_UI_Elements_and_Text"></a>
### <a name="enable-programmatic-access-to-all-ui-elements-and-text"></a>啟用以程式設計方式存取所有 UI 項目和文字  
 使用者介面 (UI) 元素應啟用以程式設計方式存取。 如果 UI 是標準 WPF 控制項，則控制項中包含程式設計存取的支援。 如果此控制項為自訂的控制項 (已從通用控制項子類別化或已從控制項子類別化)，則您必須檢查可能需要修改的區域之 <xref:System.Windows.Automation.Peers.AutomationPeer> 實作。  
  
 遵循此最佳做法可讓輔助技術廠商識別和操作您產品 UI 的元素。  
  
<a name="Place_Names__Titles_and_Descriptions_on_UI_Objects_"></a>
### <a name="place-names-titles-and-descriptions-on-ui-objects-frames-and-pages"></a>在 UI 物件、框架和頁面上放置名稱、標題和描述  
 輔助技術，尤其是螢幕助讀程式，會在巡覽配置中使用標題來了解框架、物件或頁面的位置。 因此，標題必須是描述性的。 例如若使用者已深入巡覽至某些特定的區域，則「Microsoft 網頁」的網頁標題毫無用處。 描述性的標題對於視力喪失而且依賴螢幕助讀程式的使用者相當重要。 同樣地，對於 WPF 控制項而言，對 <xref:System.Windows.Automation.AutomationProperties.NameProperty> <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> 輔助技術裝置而言很重要。  
  
 遵循這個最佳做法可讓輔助技術識別和操作範例控制項和應用程式中的 UI。  
  
<a name="Ensure_Programmatic_Events_are_Triggered_by_all_UI"></a>
### <a name="ensure-programmatic-events-are-triggered-by-all-ui-activities"></a>確定所有 UI 活動都會觸發程式設計事件  
 遵循此最佳做法可讓輔助技術接聽 UI 中的變更，並通知使用者這些變更。  
  
<a name="User_Settings"></a>
## <a name="user-settings"></a>使用者設定  
 本節中的最佳做法可確保該控制項或應用程式不會覆寫使用者設定。  
  
<a name="Respect_all_System_Wide_Settings_and_do_not_Interfere"></a>
### <a name="respect-all-system-wide-settings-and-do-not-interfere-with-accessibility-functions"></a>遵循所有系統範圍設定並不會干擾協助工具功能  
 使用者可以使用控制台來設定一些系統範圍的旗標；其他旗標則可透過程式設計方式設定。 不應該由控制項或應用程式變更這些設定。 此外，應用程式必須支援主機作業系統的協助工具設定。  
  
 遵循這個最佳做法可讓使用者設定協助工具設定，並了解這些設定不會由應用程式所變更。  
  
<a name="Visual_UI_Design"></a>
## <a name="visual-ui-design"></a>視覺 UI 設計  
 本節中的最佳做法可確保控制項或應用程式有效地使用色彩和影像，並可供輔助技術使用。  
  
<a name="Don_t_Hard_Code_Colors"></a>
### <a name="dont-hard-code-colors"></a>請勿對色彩硬式編碼  
 色盲、視力不佳或使用黑白螢幕的人可能無法使用色彩為硬式編碼的應用程式。  
  
 遵循這個最佳做法可讓使用者根據個人需求調整色彩組合。  
  
<a name="Support_High_Contrast_and_all_System_Display_Attributes"></a>
### <a name="support-high-contrast-and-all-system-display-attributes"></a>支援高對比和所有系統的顯示屬性  
 應用程式不應中斷或停用使用者選取的系統範圍對比設定、色彩選擇或其他系統範圍的顯示設定和屬性。 使用者採用的系統範圍設定可增強應用程式的可及性，所以應用程式不應停用或忽略它們。 應該在正確的前景背景組合中使用色彩，以提供適當的對比。 請勿混用不相關的色彩，也不要反轉色彩。  
  
 許多使用者需要特定的高對比組合，例如在黑色背景上的白色文字。 如在白色背景上的黑色文字一樣反轉繪製，會造成背景滲出到前景，可能會使某些使用者閱讀困難。  
  
<a name="Ensure_all_UI_Correctly_Scales_by_any_DPI_Setting"></a>
### <a name="ensure-all-ui-correctly-scales-by-any-dpi-setting"></a>確定所有 UI 正確地依 DPI 設定值縮放比例  
 確定所有的 UI 都能以每英寸的任何點（ (DPI) 設定）正確地調整。 此外，請確定 UI 元素能容納在 1024 x 768 的螢幕中，每英寸都有120點 (DPI) 。  
  
<a name="Navigation"></a>
## <a name="navigation"></a>導覽  
 本節中的最佳做法可確保已處理控制項和應用程式的巡覽。  
  
<a name="Provide_Keyboard_Interface_for_all_UI_Elements"></a>
### <a name="provide-keyboard-interface-for-all-ui-elements"></a>提供所有 UI 項目的鍵盤介面  
 Tab 鍵停止，特別是在仔細規劃時，讓使用者可以用另一種方式流覽 UI。  
  
 應用程式應該提供下列鍵盤介面：  
  
- 使用者可與其互動的所有控制項之定位停駐點，例如按鈕、連結或清單方塊  
  
- 邏輯定位順序  
  
<a name="Show_the_Keyboard_Focus"></a>
### <a name="show-the-keyboard-focus"></a>顯示鍵盤焦點  
 使用者需要知道哪個物件具有鍵盤焦點，這樣他們才可以預期按鍵的效果。 若要醒目提示鍵盤焦點，請使用色彩、字型或圖形，例如矩形或縮放比例。 若要語音反白顯示鍵盤焦點，請變更音量、音調或色調品質。  
  
 為了避免混淆，應用程式應隱藏所有視覺焦點指標，以及將位於非使用中視窗 (或窗格) 中的選取項目變暗。  
  
 應用程式應以鍵盤焦點執行下列動作：  
  
- 項目應一律具有鍵盤焦點  
  
- 鍵盤焦點應為可見及明顯  
  
- 選取項目及/或具有焦點的項目應該以視覺方式醒目提示  
  
<a name="Support_Navigation_Standards_and_Powerful_Navigation"></a>
### <a name="support-navigation-standards-and-powerful-navigation-schemes"></a>支援巡覽標準和強大的巡覽配置  
 鍵盤導覽的不同層面提供不同的方式讓使用者流覽 UI。  
  
 應用程式應該提供下列鍵盤介面：  
  
- 所有命令、功能表和控制項的快速鍵和加底線的便捷鍵  
  
- 重要連結的鍵盤快速鍵  
  
- 所有功能表項目都有便捷鍵；所有的按鈕都有快速鍵，且所有命令都有快速鍵。  
  
<a name="Do_not_let_Mouse_Location_Interfere_with_Keyboard"></a>
### <a name="do-not-let-mouse-location-interfere-with-keyboard-navigation"></a>不要讓滑鼠位置干擾鍵盤巡覽  
 滑鼠位置不應干擾鍵盤巡覽。 例如，如果滑鼠位於某個位置，而使用者正在使用鍵盤流覽，則除非使用者起始滑鼠，否則不應該進行滑鼠點擊。  
  
<a name="Multimodal_Interface"></a>
## <a name="multimodal-interface"></a>多樣式介面  
 本節中的最佳做法可確保應用程式 UI 包含視覺元素的替代方案。  
  
<a name="Provide_User_Selectable_Equivalents_for_Non_Text"></a>
### <a name="provide-user-selectable-equivalents-for-non-text-elements"></a>對於非文字項目提供使用者可選取的對等項目  
 對於每個非文字項目，提供文字、文字記錄或音訊描述之使用者可選取的對等項目，如替代文字、標題或視覺化回饋。  
  
 非文字元素涵蓋範圍廣泛的 UI 元素，包括：影像、影像地圖區域、動畫、applet、框架、腳本、圖形按鈕、音效、獨立音訊檔案和影片。 如果非文字元素包含使用者需要存取的視覺資訊、語音或一般音訊資訊，以瞭解 UI 的內容，就很重要。  
  
<a name="Use_Color_but_also_Provide_Alternatives_to_Color"></a>
### <a name="use-color-but-also-provide-alternatives-to-color"></a>使用色彩，但是也提供色彩的替代方案  
 請使用色彩來增強及強調，或再次提醒以其他方式顯示的資訊，但請勿單獨使用色彩傳達資訊。 色盲或使用單色顯示器的使用者需要色彩的替代方案。  
  
<a name="Use_Standard_Input_APIs_with_Devices_Independent"></a>
### <a name="use-standard-input-apis-with-device-independent-calls"></a>藉由與裝置無關的呼叫使用標準輸入的 API  
 與裝置無關的呼叫會確保鍵盤和滑鼠功能是否相等，同時提供具有 UI 所需資訊的輔助技術。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Automation.Peers>
- [具有佈景主題和 UI 自動化支援的 NumericUpDown 自訂控制項範例](/previous-versions/dotnet/netframework-3.5/ms771573(v=vs.90))
- [鍵盤使用者介面設計指導方針](/previous-versions/windows/desktop/dnacc/guidelines-for-keyboard-user-interface-design)
