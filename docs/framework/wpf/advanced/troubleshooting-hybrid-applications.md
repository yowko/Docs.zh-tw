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
ms.openlocfilehash: b85a607d2e44d6253359a81118f90e6ee05d2d3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187319"
---
# <a name="troubleshooting-hybrid-applications"></a>混合應用程式疑難排解
<a name="introduction"></a>本主題列出了創作混合應用程式時可能出現的一些常見問題，這些應用程式同時使用 Windows[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]表單技術。  

<a name="overlapping_controls"></a>
## <a name="overlapping-controls"></a>重疊控制項  
 控制項可能不會以您預期的方式重疊。 Windows 表單為每個控制項使用單獨的 HWND。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會針對頁面上的所有內容使用一個 HWND。 這個實作差異導致非預期的重疊行為。  
  
 託管中的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Windows 表單控制項始終顯示在內容的頂部[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]託管在控制項中<xref:System.Windows.Forms.Integration.ElementHost>的內容以<xref:System.Windows.Forms.Integration.ElementHost>控制項的 z 順序顯示。 可以重疊<xref:System.Windows.Forms.Integration.ElementHost>控制項，但託管[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容不組合或交互。  
  
<a name="child_property"></a>
## <a name="child-property"></a>子屬性  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>和<xref:System.Windows.Forms.Integration.ElementHost>類只能承載一個子控制項或元素。 若要裝載多個控制項或元素，您必須使用容器當做子內容。 例如，您可以將 Windows 表單按鈕和核取方塊控制項添加到<xref:System.Windows.Forms.Panel?displayProperty=nameWithType>控制項，然後將面板分配給<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項的屬性。 <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> 但是，您不能將按鈕和核取方塊控制項單獨添加到同一<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項。  
  
<a name="scaling"></a>
## <a name="scaling"></a>調整大小  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]和 Windows 表單具有不同的縮放模型。 某些[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]縮放轉換對 Windows 表單控制項有意義，但其他擴輾轉換則沒有意義。 例如，將 Windows 表單控制項縮放為 0 將起作用，但如果嘗試將同一控制項縮放回非零值，則控制項的大小仍為 0。 如需詳細資訊，請參閱 [WindowsFormsHost 元素的配置考量](layout-considerations-for-the-windowsformshost-element.md)。  
  
<a name="adapter"></a>
## <a name="adapter"></a>配接器  
 在 和<xref:System.Windows.Forms.Integration.WindowsFormsHost><xref:System.Windows.Forms.Integration.ElementHost>類工作時可能存在混淆，因為它們包含一個隱藏的容器。 和 類都有一個隱藏的容器，稱為配接器，它們用於承載內容。 *adapter* <xref:System.Windows.Forms.Integration.WindowsFormsHost> <xref:System.Windows.Forms.Integration.ElementHost> 對於元素<xref:System.Windows.Forms.Integration.WindowsFormsHost>，配接器派生自類<xref:System.Windows.Forms.ContainerControl?displayProperty=nameWithType>。 對於<xref:System.Windows.Forms.Integration.ElementHost>控制項，配接器派生自元素<xref:System.Windows.Controls.DockPanel>。 當您在其他交互操作主題中看見對於配接器的參考資訊時，就是在討論此容器。  
  
<a name="nesting"></a>
## <a name="nesting"></a>巢狀  
 不支援將<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素嵌套在<xref:System.Windows.Forms.Integration.ElementHost>控制項中。 不支援在<xref:System.Windows.Forms.Integration.ElementHost><xref:System.Windows.Forms.Integration.WindowsFormsHost>元素內嵌套控制項。  
  
<a name="focus"></a>
## <a name="focus"></a>Focus  
 焦點在 和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Windows 表單中的工作方式不同，這意味著焦點問題可能發生在混合應用程式中。 例如，如果<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素內部具有焦點，並且最小化並還原頁面或顯示模式對話方塊，則元素內部的焦點<xref:System.Windows.Forms.Integration.WindowsFormsHost>可能會丟失。 元素<xref:System.Windows.Forms.Integration.WindowsFormsHost>仍有焦點，但元素內的控制項可能沒有。  
  
 資料驗證也會受到焦點影響。 驗證在<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素中工作，但它不能像從<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素中選項卡出來或在兩個不同的<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素之間工作。  
  
<a name="property_mapping"></a>
## <a name="property-mapping"></a>屬性對應  
 某些屬性對應需要大量解釋，以在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]和 Windows 表單技術之間橋接不同的實現。 屬性對應可讓您的程式碼回應字型、色彩和其他屬性的變更。 通常，屬性對應是透過接聽 *Property*Changed 事件或 On*Property*Changed 呼叫，並在子控制項或其介面卡上設定適當的屬性來運作。 如需詳細資訊，請參閱 [Windows Form 和 WPF 屬性對應](windows-forms-and-wpf-property-mapping.md)。  
  
<a name="layoutrelated_properties_on_hosted_content"></a>
## <a name="layout-related-properties-on-hosted-content"></a>裝載內容上配置相關的屬性  
 分配<xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=nameWithType>或<xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=nameWithType>屬性時，將自動設置託管內容上的多個與佈局相關的屬性。 變更這些內容屬性會導致未預期的配置行為。  
  
 託管內容停靠以填充<xref:System.Windows.Forms.Integration.WindowsFormsHost>和<xref:System.Windows.Forms.Integration.ElementHost>父內容。 若要啟用這個填滿行為，您需要在設定子屬性時設定數個屬性。 下表列出了 和<xref:System.Windows.Forms.Integration.ElementHost><xref:System.Windows.Forms.Integration.WindowsFormsHost>類設置的內容屬性。  
  
|裝載類別|內容屬性|  
|----------------|------------------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 請勿直接在裝載的內容上設定這些屬性。 如需詳細資訊，請參閱 [WindowsFormsHost 元素的配置考量](layout-considerations-for-the-windowsformshost-element.md)。  
  
<a name="navigation_applications"></a>
## <a name="navigation-applications"></a>瀏覽應用程式  
 瀏覽應用程式可能不會保留使用者狀態。 當<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素在導航應用程式中使用時，它重新創建其控制項。 當使用者從承載元素的頁面導航，然後返回到該元素時，<xref:System.Windows.Forms.Integration.WindowsFormsHost>將重新創建子控制項。 使用者已輸入的任何內容都將遺失。  
  
<a name="message_loop_interoperation"></a>
## <a name="message-loop-interoperation"></a>訊息迴圈交互操作  
 使用 Windows 表單消息迴圈時，郵件可能無法按預期方式處理。 該方法<xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>由<xref:System.Windows.Forms.Integration.WindowsFormsHost>建構函式調用。 這個方法會將訊息篩選器加入至 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 訊息迴圈。 如果 是消息<xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType>的目標，<xref:System.Windows.Forms.Control?displayProperty=nameWithType>則此篩選器調用 方法，並轉換/調度消息。  
  
 如果在 Windows<xref:System.Windows.Window>表單消息迴圈中顯示 ，<xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>則除非調用 方法，<xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>否則無法鍵入任何內容。 該方法<xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>採用 和<xref:System.Windows.Window>添加<xref:System.Windows.Forms.IMessageFilter?displayProperty=nameWithType>，將與鍵相關的消息重新路由到[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]消息迴圈。 如需詳細資訊，請參閱 [Windows Form 和 WPF 互通性輸入架構](windows-forms-and-wpf-interoperability-input-architecture.md)。  
  
<a name="opacity_and_layering"></a>
## <a name="opacity-and-layering"></a>不透明度與分層  
 類<xref:System.Windows.Interop.HwndHost>不支援分層。 <xref:System.Windows.UIElement.Opacity%2A>這意味著在<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素上設置屬性不起作用，並且不會與設置為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Window.AllowsTransparency%2A>`true`的其他視窗進行混合。  
  
<a name="dispose"></a>
## <a name="dispose"></a>處置  
 未正確處置類別可能造成流失資源。 在混合應用程式中，請確保 已釋放<xref:System.Windows.Forms.Integration.WindowsFormsHost>和<xref:System.Windows.Forms.Integration.ElementHost>類，否則可能會洩漏資源。 Windows 表單在其<xref:System.Windows.Forms.Integration.ElementHost>非模式<xref:System.Windows.Forms.Form>父表單關閉時釋放控制項。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]當應用程式<xref:System.Windows.Forms.Integration.WindowsFormsHost>關閉時釋放元素。 可以在 Windows 表單消息<xref:System.Windows.Forms.Integration.WindowsFormsHost>迴圈<xref:System.Windows.Window>中顯示 元素。 在此情況下，您的程式碼可能不會收到應用程式正在關閉的通知。  
  
<a name="enabling_visual_styles"></a>
## <a name="enabling-visual-styles"></a>啟用視覺化樣式  
 可能無法啟用 Windows 表單控制項上的 Microsoft Windows XP 可視樣式。 該方法<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>在 Windows 表單應用程式的範本中調用。 儘管預設情況下不調用此方法，但如果使用 Visual Studio 創建專案，如果 Comctl32.dll 的版本 6.0 可用，則將為控制項獲取 Microsoft Windows XP 可視樣式。 線上程上創建<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>控制碼之前，必須調用 方法。 如需詳細資訊，請參閱[如何：在混合應用程式中啟用視覺化樣式](how-to-enable-visual-styles-in-a-hybrid-application.md)。  
  
<a name="licensed_controls"></a>
## <a name="licensed-controls"></a>授權的控制項  
 向使用者顯示訊息方塊中許可資訊的許可 Windows 表單控制項可能會導致混合應用程式的意外行為。 某些授權的控制項會顯示對話方塊，以回應控制代碼的建立。 例如，授權的控制項可能會通知使用者，必須具有授權，或者使用者還剩三次機會來試用控制項。  
  
 元素<xref:System.Windows.Forms.Integration.WindowsFormsHost>派生自 類<xref:System.Windows.Interop.HwndHost>，並在<xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A>方法內創建子控制項的控制碼。 類<xref:System.Windows.Interop.HwndHost>不允許在<xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A>方法中處理消息，但顯示對話方塊會導致發送消息。 要啟用此許可方案，請<xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=nameWithType>先調用控制項上的方法，然後再將其指定為<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素的子級。  
  
<a name="wpf_designer"></a>
## <a name="wpf-designer"></a>WPF 設計工具  
 您可以使用視覺化工作室的 WPF 設計器來設計 WPF 內容。 以下各節列出了使用 WPF 設計器創作混合應用程式時可能出現的一些常見問題。  
  
### <a name="backcolortransparent-is-ignored-at-design-time"></a>BackColorTransparent 會在設計階段被略過  
 在<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>設計時，該屬性可能無法按預期工作。  
  
 如果 WPF 控制項不在可見的父級上，則 WPF 運行時將忽略<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>該值。 <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>可能忽略的原因是物件<xref:System.Windows.Forms.Integration.ElementHost>是在單獨的<xref:System.AppDomain>中創建的。 但是，當您運行應用程式時，<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>確實按預期工作。  
  
### <a name="design-time-error-list-appears-when-the-obj-folder-is-deleted"></a>刪除 obj 資料夾時，出現設計階段錯誤清單  
 如果刪除了 obj 資料夾，就會出現設計階段錯誤清單。  
  
 使用 時，Windows<xref:System.Windows.Forms.Integration.ElementHost>表單設計器使用專案 obj 資料夾中的"調試"或"釋放"資料夾中生成的檔。 如果您刪除這些檔案，就會出現設計階段錯誤清單。 若要修正此問題，請重建專案。 如需詳細資訊，請參閱 [Windows Forms 設計工具的設計階段錯誤](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md)。  
  
<a name="elementhost_and_ime"></a>
## <a name="elementhost-and-ime"></a>ElementHost 和 IME  
 當前託管在 的<xref:System.Windows.Forms.Integration.ElementHost>WPF 控制項不支援<xref:System.Windows.Forms.Control.ImeMode%2A>該屬性。 託管控制項<xref:System.Windows.Forms.Control.ImeMode%2A>將忽略 對 的更改。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [WPF 設計工具中的互通性](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628658(v=vs.100))
- [Windows Form 和 WPF 互通性輸入架構](windows-forms-and-wpf-interoperability-input-architecture.md)
- [如何：在混合應用程式中啟用視覺化樣式](how-to-enable-visual-styles-in-a-hybrid-application.md)
- [WindowsFormsHost 元素的配置考量](layout-considerations-for-the-windowsformshost-element.md)
- [Windows Form 和 WPF 屬性對應](windows-forms-and-wpf-property-mapping.md)
- [Windows Forms 設計工具的設計階段錯誤](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md)
- [移轉和互通性](migration-and-interoperability.md)
