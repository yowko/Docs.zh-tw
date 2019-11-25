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
ms.openlocfilehash: f3cddcd6cd90e7e43ea6af67725e709673f7650f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978344"
---
# <a name="troubleshooting-hybrid-applications"></a>混合應用程式疑難排解
<a name="introduction"></a> 本主題列出一些會在撰寫混合式應用程式時發生的常見問題，這類應用程式同時使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 技術。  

<a name="overlapping_controls"></a>   
## <a name="overlapping-controls"></a>重疊控制項  
 控制項可能不會以您預期的方式重疊。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 會針對每個控制項使用不同的 HWND。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會針對頁面上的所有內容使用一個 HWND。 這個實作差異導致非預期的重疊行為。  
  
 裝載於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 上的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項一律會顯示在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容上方。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 裝載于 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中的內容會以 <xref:System.Windows.Forms.Integration.ElementHost> 控制項的迭置順序出現。 <xref:System.Windows.Forms.Integration.ElementHost> 控制項可能會重迭，但裝載的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容不會合並或互動。  
  
<a name="child_property"></a>   
## <a name="child-property"></a>子屬性  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 和 <xref:System.Windows.Forms.Integration.ElementHost> 類別只能裝載單一子控制項或元素。 若要裝載多個控制項或元素，您必須使用容器當做子內容。 例如，您可以將 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 按鈕和核取方塊控制項加入 <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> 控制項，然後將面板指派給 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項的 <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> 屬性。 不過，您無法將按鈕和核取方塊控制項分別新增至相同的 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項。  
  
<a name="scaling"></a>   
## <a name="scaling"></a>縮放  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 具有不同的縮放比例模型。 某些 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 縮放比例轉換對 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項深具意義，但其他則沒有。 例如，將 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項的縮放比例設為 0 是可行的，但如果您嘗試將同一個控制項的縮放比例調回非零的值，則控制項的大小會保持 0。 如需詳細資訊，請參閱 [WindowsFormsHost 元素的配置考量](layout-considerations-for-the-windowsformshost-element.md)。  
  
<a name="adapter"></a>   
## <a name="adapter"></a>配接器  
 使用 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 和 <xref:System.Windows.Forms.Integration.ElementHost> 類別時，可能會造成混淆，因為它們包含隱藏的容器。 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 和 <xref:System.Windows.Forms.Integration.ElementHost> 類別都有一個隱藏的容器，稱為*介面卡*，其用來裝載內容。 針對 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素，介面卡衍生自 <xref:System.Windows.Forms.ContainerControl?displayProperty=nameWithType> 類別。 針對 <xref:System.Windows.Forms.Integration.ElementHost> 控制項，介面卡衍生自 <xref:System.Windows.Controls.DockPanel> 元素。 當您在其他交互操作主題中看見對於配接器的參考資訊時，就是在討論此容器。  
  
<a name="nesting"></a>   
## <a name="nesting"></a>巢狀  
 不支援在 <xref:System.Windows.Forms.Integration.ElementHost> 控制項內嵌套 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素。 也不支援在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素內嵌套 <xref:System.Windows.Forms.Integration.ElementHost> 控制項。  
  
<a name="focus"></a>   
## <a name="focus"></a>焦點  
 焦點在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 中會以不同的方式運作，這表示焦點問題可能會發生在混合式應用程式中。 例如，如果您將焦點放在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 專案中，而您將頁面最小化和還原，或顯示模式對話方塊，則可能會遺失 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素內的焦點。 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 的元素仍然具有焦點，但它內部的控制項可能不是。  
  
 資料驗證也會受到焦點影響。 驗證可在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 專案中運作，但當您在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素或兩個不同的 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素之間進行 tab 鍵時，無法運作。  
  
<a name="property_mapping"></a>   
## <a name="property-mapping"></a>屬性對應  
 某些屬性對應需要大量解譯，以橋接 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 技術之間的不同實作。 屬性對應可讓您的程式碼回應字型、色彩和其他屬性的變更。 通常，屬性對應是透過接聽 *Property*Changed 事件或 On*Property*Changed 呼叫，並在子控制項或其介面卡上設定適當的屬性來運作。 如需詳細資訊，請參閱 [Windows Form 和 WPF 屬性對應](windows-forms-and-wpf-property-mapping.md)。  
  
<a name="layoutrelated_properties_on_hosted_content"></a>   
## <a name="layout-related-properties-on-hosted-content"></a>裝載內容上配置相關的屬性  
 指派 <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=nameWithType> 或 <xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=nameWithType> 屬性時，會自動設定裝載內容上的數個版面配置相關屬性。 變更這些內容屬性會導致未預期的配置行為。  
  
 裝載的內容會停駐，以填滿 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 並 <xref:System.Windows.Forms.Integration.ElementHost> 父系。 若要啟用這個填滿行為，您需要在設定子屬性時設定數個屬性。 下表列出 <xref:System.Windows.Forms.Integration.ElementHost> 和 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 類別所設定的內容屬性。  
  
|裝載類別|內容屬性|  
|----------------|------------------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 請勿直接在裝載的內容上設定這些屬性。 如需詳細資訊，請參閱 [WindowsFormsHost 元素的配置考量](layout-considerations-for-the-windowsformshost-element.md)。  
  
<a name="navigation_applications"></a>   
## <a name="navigation-applications"></a>瀏覽應用程式  
 瀏覽應用程式可能不會保留使用者狀態。 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素用於導覽應用程式時，會重新建立其控制項。 當使用者流覽離開主控 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 專案的頁面，然後返回該專案時，就會重新建立子控制項。 使用者已輸入的任何內容都將遺失。  
  
<a name="message_loop_interoperation"></a>   
## <a name="message-loop-interoperation"></a>訊息迴圈交互操作  
 使用 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 訊息迴圈時，可能無法如預期般處理訊息。 <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> 方法是由 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 的「函式」呼叫。 這個方法會將訊息篩選器加入至 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 訊息迴圈。 如果 <xref:System.Windows.Forms.Control?displayProperty=nameWithType> 是訊息的目標，且轉譯/分派訊息，此篩選準則會呼叫 <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType> 方法。  
  
 如果您在具有 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 訊息迴圈中顯示 <xref:System.Windows.Window>，除非您呼叫 <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> 方法，否則無法輸入任何專案。 <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> 方法會接受 <xref:System.Windows.Window> 並加入 <xref:System.Windows.Forms.IMessageFilter?displayProperty=nameWithType>，這會將索引鍵相關訊息重排到 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 訊息迴圈。 如需詳細資訊，請參閱 [Windows Form 和 WPF 互通性輸入架構](windows-forms-and-wpf-interoperability-input-architecture.md)。  
  
<a name="opacity_and_layering"></a>   
## <a name="opacity-and-layering"></a>不透明度與分層  
 <xref:System.Windows.Interop.HwndHost> 類別不支援分層。 這表示在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素上設定 <xref:System.Windows.UIElement.Opacity%2A> 屬性不會有任何作用，而且在 <xref:System.Windows.Window.AllowsTransparency%2A> 設定為 [`true`] 的其他 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 視窗中不會進行任何混合。  
  
<a name="dispose"></a>   
## <a name="dispose"></a>Dispose  
 未正確處置類別可能造成流失資源。 在您的混合式應用程式中，請確定已處置 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 和 <xref:System.Windows.Forms.Integration.ElementHost> 類別，否則您可能會洩漏資源。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 在其非強制回應 <xref:System.Windows.Forms.Form> 父系關閉時處置 <xref:System.Windows.Forms.Integration.ElementHost> 控制項。 當您的應用程式關閉時，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 處置 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素。 您可以在 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 訊息迴圈的 <xref:System.Windows.Window> 中顯示 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素。 在此情況下，您的程式碼可能不會收到應用程式正在關閉的通知。  
  
<a name="enabling_visual_styles"></a>   
## <a name="enabling-visual-styles"></a>啟用視覺化樣式  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項上的 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] 視覺化樣式可能不會啟用。 在 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 應用程式的範本中，會呼叫 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> 方法。 雖然預設不會呼叫這個方法，但如果您使用 Visual Studio 來建立專案，則會取得控制項的 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] 視覺化樣式（如果有6.0 版的 Comctl32.dll 可用）。 線上程上建立控制碼之前，您必須先呼叫 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> 方法。 如需詳細資訊，請參閱[如何：在混合應用程式中啟用視覺化樣式](how-to-enable-visual-styles-in-a-hybrid-application.md)。  
  
<a name="licensed_controls"></a>   
## <a name="licensed-controls"></a>授權的控制項  
 授權的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項會在訊息方塊中向使用者顯示授權資訊，而這類控制項可能導致混合式應用程式產生未預期的行為。 某些授權的控制項會顯示對話方塊，以回應控制代碼的建立。 例如，授權的控制項可能會通知使用者，必須具有授權，或者使用者還剩三次機會來試用控制項。  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 專案衍生自 <xref:System.Windows.Interop.HwndHost> 類別，而子控制項的控制碼是在 <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> 方法內建立。 <xref:System.Windows.Interop.HwndHost> 類別不允許在 <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> 方法中處理訊息，但顯示對話方塊會導致傳送訊息。 若要啟用此授權案例，請先在控制項上呼叫 <xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=nameWithType> 方法，再將它指派為 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素的子系。  
  
<a name="wpf_designer"></a>   
## <a name="wpf-designer"></a>WPF 設計工具  
 您可以使用適用于 Visual Studio 的 WPF 設計工具來設計 WPF 內容。 下列各節列出使用 WPF 設計工具撰寫混合式應用程式時可能會發生的一些常見問題。  
  
### <a name="backcolortransparent-is-ignored-at-design-time"></a>BackColorTransparent 會在設計階段被略過  
 在設計階段，<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> 屬性可能無法如預期般運作。  
  
 如果 WPF 控制項不在可見的父系上，WPF 執行時間會忽略 <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> 值。 可能會忽略 <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> 的原因是因為 <xref:System.Windows.Forms.Integration.ElementHost> 物件是在不同的 <xref:System.AppDomain>中建立的。 不過，當您執行應用程式時，<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> 會如預期般運作。  
  
### <a name="design-time-error-list-appears-when-the-obj-folder-is-deleted"></a>刪除 obj 資料夾時，出現設計階段錯誤清單  
 如果刪除了 obj 資料夾，就會出現設計階段錯誤清單。  
  
 當您使用 <xref:System.Windows.Forms.Integration.ElementHost>進行設計時，Windows Form 設計工具會在專案的 [obj] 資料夾內，使用 [Debug] 或 [Release] 資料夾中產生的檔案。 如果您刪除這些檔案，就會出現設計階段錯誤清單。 若要修正此問題，請重建專案。 如需詳細資訊，請參閱 [Windows Forms 設計工具的設計階段錯誤](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md)。  
  
<a name="elementhost_and_ime"></a>   
## <a name="elementhost-and-ime"></a>ElementHost 和 IME  
 <xref:System.Windows.Forms.Integration.ElementHost> 中裝載的 WPF 控制項目前不支援 <xref:System.Windows.Forms.Control.ImeMode%2A> 屬性。 對 <xref:System.Windows.Forms.Control.ImeMode%2A> 所做的變更將會被裝載的控制項忽略。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [WPF 設計工具中的互通性](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628658(v=vs.100))
- [Windows Forms 和 WPF 互通性輸入架構](windows-forms-and-wpf-interoperability-input-architecture.md)
- [操作說明：在混合應用程式中啟用視覺化樣式](how-to-enable-visual-styles-in-a-hybrid-application.md)
- [WindowsFormsHost 元素的配置考量](layout-considerations-for-the-windowsformshost-element.md)
- [Windows Forms 和 WPF 屬性對應](windows-forms-and-wpf-property-mapping.md)
- [Windows Forms 設計工具的設計階段錯誤](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md)
- [移轉和互通性](migration-and-interoperability.md)
