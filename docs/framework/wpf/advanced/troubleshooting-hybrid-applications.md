---
title: 混合應用程式疑難排解
ms.date: 03/30/2017
helpviewer_keywords:
- overlapping controls [WPF]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid applications [WPF interoperability]
- message loops [WPF]
ms.assetid: f440c23f-fa5d-4d5a-852f-ba61150e6405
ms.openlocfilehash: b43143fb3f27d127f93f5e8edd55b853ad604ef5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43562642"
---
# <a name="troubleshooting-hybrid-applications"></a>混合應用程式疑難排解
<a name="introduction"></a> 本主題列出一些會在撰寫混合式應用程式時發生的常見問題，這類應用程式同時使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 技術。  
  

  
<a name="overlapping_controls"></a>   
## <a name="overlapping-controls"></a>重疊控制項  
 控制項可能不會以您預期的方式重疊。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 會針對每個控制項使用不同的 HWND。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會針對頁面上的所有內容使用一個 HWND。 這個實作差異導致非預期的重疊行為。  
  
 裝載於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 上的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項一律會顯示在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容上方。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容裝載於<xref:System.Windows.Forms.Integration.ElementHost>控制項就會出現在疊置順序的<xref:System.Windows.Forms.Integration.ElementHost>控制項。 可以重疊<xref:System.Windows.Forms.Integration.ElementHost>控制項，但是裝載[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容不會結合或互動。  
  
<a name="child_property"></a>   
## <a name="child-property"></a>子屬性  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>和<xref:System.Windows.Forms.Integration.ElementHost>類別可以裝載只有單一子控制項或項目。 若要裝載多個控制項或元素，您必須使用容器當做子內容。 例如，您可以在其中加入[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 按鈕和核取方塊控制項，以<xref:System.Windows.Forms.Panel?displayProperty=nameWithType>控制項，並接著將指派到面板<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項的<xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A>屬性。 不過，您無法將按鈕和核取方塊控制項分別加入相同<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項。  
  
<a name="scaling"></a>   
## <a name="scaling"></a>縮放  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 具有不同的縮放比例模型。 某些 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 縮放比例轉換對 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項深具意義，但其他則沒有。 例如，將 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項的縮放比例設為 0 是可行的，但如果您嘗試將同一個控制項的縮放比例調回非零的值，則控制項的大小會保持 0。 如需詳細資訊，請參閱 [WindowsFormsHost 元素的配置考量](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)。  
  
<a name="adapter"></a>   
## <a name="adapter"></a>配接器  
 有可能會產生混淆處理時<xref:System.Windows.Forms.Integration.WindowsFormsHost>和<xref:System.Windows.Forms.Integration.ElementHost>類別，因為它們包含一個隱藏的容器。 同時<xref:System.Windows.Forms.Integration.WindowsFormsHost>並<xref:System.Windows.Forms.Integration.ElementHost>類別具有一個隱藏的容器，稱為*配接器*，他們使用主機內容。 針對<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目，配接器是衍生自<xref:System.Windows.Forms.ContainerControl?displayProperty=nameWithType>類別。 針對<xref:System.Windows.Forms.Integration.ElementHost>控制項，配接器是衍生自<xref:System.Windows.Controls.DockPanel>項目。 當您在其他交互操作主題中看見對於配接器的參考資訊時，就是在討論此容器。  
  
<a name="nesting"></a>   
## <a name="nesting"></a>巢狀  
 巢狀<xref:System.Windows.Forms.Integration.WindowsFormsHost>內的項目<xref:System.Windows.Forms.Integration.ElementHost>控制項不支援。 巢狀<xref:System.Windows.Forms.Integration.ElementHost>內控制<xref:System.Windows.Forms.Integration.WindowsFormsHost>也不支援項目。  
  
<a name="focus"></a>   
## <a name="focus"></a>焦點  
 焦點在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 中會以不同的方式運作，這表示焦點問題可能會發生在混合式應用程式中。 例如，如果您有內部的焦點<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目，而且您其中一個最小化和還原的頁面或顯示強制回應對話方塊，專注在<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目可能會遺失。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>元素仍具有焦點，但其內部的控制項可能不會。  
  
 資料驗證也會受到焦點影響。 驗證適用於<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目，但運作不如您按下 tab 鍵 out<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目，或不同的兩個<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目。  
  
<a name="property_mapping"></a>   
## <a name="property-mapping"></a>屬性對應  
 某些屬性對應需要大量解譯，以橋接 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 技術之間的不同實作。 屬性對應可讓您的程式碼回應字型、色彩和其他屬性的變更。 通常，屬性對應是透過接聽 *Property*Changed 事件或 On*Property*Changed 呼叫，並在子控制項或其介面卡上設定適當的屬性來運作。 如需詳細資訊，請參閱 [Windows Form 和 WPF 屬性對應](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)。  
  
<a name="layoutrelated_properties_on_hosted_content"></a>   
## <a name="layout-related-properties-on-hosted-content"></a>裝載內容上配置相關的屬性  
 當<xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=nameWithType>或<xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=nameWithType>屬性會被指派，會自動設定數個配置相關的屬性，在裝載的內容。 變更這些內容屬性會導致未預期的配置行為。  
  
 裝載的內容會停駐來填滿<xref:System.Windows.Forms.Integration.WindowsFormsHost>和<xref:System.Windows.Forms.Integration.ElementHost>父代。 若要啟用這個填滿行為，您需要在設定子屬性時設定數個屬性。 下表列出的內容屬性進行設定<xref:System.Windows.Forms.Integration.ElementHost>和<xref:System.Windows.Forms.Integration.WindowsFormsHost>類別。  
  
|裝載類別|內容屬性|  
|----------------|------------------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 請勿直接在裝載的內容上設定這些屬性。 如需詳細資訊，請參閱 [WindowsFormsHost 元素的配置考量](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)。  
  
<a name="navigation_applications"></a>   
## <a name="navigation-applications"></a>瀏覽應用程式  
 瀏覽應用程式可能不會保留使用者狀態。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>項目在瀏覽應用程式中使用時，會重新建立它的控制項。 當使用者瀏覽離開裝載的頁面重新建立子控制項時發生<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目，然後返回。 使用者已輸入的任何內容都將遺失。  
  
<a name="message_loop_interoperation"></a>   
## <a name="message-loop-interoperation"></a>訊息迴圈交互操作  
 使用 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 訊息迴圈時，可能無法如預期般處理訊息。 <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>方法會呼叫<xref:System.Windows.Forms.Integration.WindowsFormsHost>建構函式。 這個方法會將訊息篩選器加入至 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 訊息迴圈。 此篩選器會呼叫<xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType>方法如果<xref:System.Windows.Forms.Control?displayProperty=nameWithType>訊息的目標和轉譯/分派訊息。  
  
 如果您顯示<xref:System.Windows.Window>中[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]使用的訊息迴圈<xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>，您無法輸入任何項目除非您呼叫<xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>方法。 <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>方法會採用<xref:System.Windows.Window>，並將<xref:System.Windows.Forms.IMessageFilter?displayProperty=nameWithType>，其中 device-mapper 金鑰相關訊息[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]訊息迴圈。 如需詳細資訊，請參閱 [Windows Form 和 WPF 互通性輸入架構](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture.md)。  
  
<a name="opacity_and_layering"></a>   
## <a name="opacity-and-layering"></a>不透明度與分層  
 <xref:System.Windows.Interop.HwndHost>類別不支援分層。 這表示<xref:System.Windows.UIElement.Opacity%2A>上的屬性<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目具有任何作用，而不會發生混色其他[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]視窗已<xref:System.Windows.Window.AllowsTransparency%2A>設定為`true`。  
  
<a name="dispose"></a>   
## <a name="dispose"></a>Dispose  
 未正確處置類別可能造成流失資源。 在您的混合式應用程式，請確定<xref:System.Windows.Forms.Integration.WindowsFormsHost>和<xref:System.Windows.Forms.Integration.ElementHost>處置類別，或您可能會流失資源。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 處置<xref:System.Windows.Forms.Integration.ElementHost>控制於何時其非強制回應<xref:System.Windows.Forms.Form>父關閉。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 處置<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目，您的應用程式關閉時。 可顯示<xref:System.Windows.Forms.Integration.WindowsFormsHost>中的項目<xref:System.Windows.Window>在[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]訊息迴圈。 在此情況下，您的程式碼可能不會收到應用程式正在關閉的通知。  
  
<a name="enabling_visual_styles"></a>   
## <a name="enabling-visual-styles"></a>啟用視覺化樣式  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項上的 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] 視覺化樣式可能不會啟用。 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>方法呼叫中的範本[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]應用程式。 雖然預設不會呼叫此方法，但如果您使用 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 來建立專案，您將會取得控制項的 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] 視覺化樣式 (前提是可使用 Comctl32.dll 版本 6.0)。 您必須呼叫<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>方法之前執行緒上建立控制代碼。 如需詳細資訊，請參閱[如何：在混合應用程式中啟用視覺化樣式](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)。  
  
<a name="licensed_controls"></a>   
## <a name="licensed-controls"></a>授權的控制項  
 授權的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項會在訊息方塊中向使用者顯示授權資訊，而這類控制項可能導致混合式應用程式產生未預期的行為。 某些授權的控制項會顯示對話方塊，以回應控制代碼的建立。 例如，授權的控制項可能會通知使用者，必須具有授權，或者使用者還剩三次機會來試用控制項。  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>項目衍生自<xref:System.Windows.Interop.HwndHost>內建立的類別和子控制項的控制代碼<xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A>方法。 <xref:System.Windows.Interop.HwndHost>類別不允許在處理訊息<xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A>方法，但顯示對話方塊會造成要傳送的訊息。 若要啟用此授權案例，請呼叫<xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=nameWithType>方法，再將它做為指派控制項上的<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素的子系。  
  
<a name="wpf_designer"></a>   
## <a name="wpf-designer"></a>WPF 設計工具  
 您可以使用 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] 來設計 WPF 內容。 下列各節將列出一些會在使用 [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] 撰寫混合式應用程式時發生的常見問題。  
  
### <a name="backcolortransparent-is-ignored-at-design-time"></a>BackColorTransparent 會在設計階段被略過  
 <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>如預期般在設計階段屬性可能無法運作。  
  
 如果 WPF 控制項不是可見的父代上，WPF 執行階段會略過<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>值。 原因，<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>可能會遭到忽略，所以<xref:System.Windows.Forms.Integration.ElementHost>物件建立於個別的<xref:System.AppDomain>。 不過，當您執行應用程式，<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>如預期般運作。  
  
### <a name="design-time-error-list-appears-when-the-obj-folder-is-deleted"></a>刪除 obj 資料夾時，出現設計階段錯誤清單  
 如果刪除了 obj 資料夾，就會出現設計階段錯誤清單。  
  
 當您設計使用<xref:System.Windows.Forms.Integration.ElementHost>，Windows Form 設計工具專案的 obj 資料夾內的 [偵錯或發行] 資料夾中使用產生的檔案。 如果您刪除這些檔案，就會出現設計階段錯誤清單。 若要修正此問題，請重建專案。 如需詳細資訊，請參閱 [Windows Forms 設計工具的設計階段錯誤](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)。  
  
<a name="elementhost_and_ime"></a>   
## <a name="elementhost-and-ime"></a>ElementHost 和 IME  
 WPF 控制項裝載於<xref:System.Windows.Forms.Integration.ElementHost>目前不支援<xref:System.Windows.Forms.Control.ImeMode%2A>屬性。 若要變更<xref:System.Windows.Forms.Control.ImeMode%2A>將會忽略裝載的控制項。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF 設計工具中的互通性](https://msdn.microsoft.com/library/2cb7c1ca-2a75-463b-8801-fba81e2b7042)  
 [Windows Forms 和 WPF 互通性輸入架構](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture.md)  
 [操作說明：在混合應用程式中啟用視覺化樣式](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)  
 [WindowsFormsHost 元素的配置考量](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [Windows Forms 和 WPF 屬性對應](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [Windows Forms 設計工具的設計階段錯誤](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)  
 [移轉和互通性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
