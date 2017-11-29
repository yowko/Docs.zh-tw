---
title: "WindowsFormsHost 項目的配置考量"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element layout considerations [WPF]
- dynamic layout [WPF interoperability]
- device-independent pixels
ms.assetid: 3c574597-bbde-440f-95cc-01371f1a5d9d
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d21077e6012f8e48a1418f67e8f0d156d82003c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="layout-considerations-for-the-windowsformshost-element"></a>WindowsFormsHost 項目的配置考量
本主題描述如何<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目互動[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版面配置系統。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]和[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]支援不同但相似，邏輯大小及定位到表單或頁面上的項目。 當您建立混合式使用者介面 (UI) 的主控件[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目整合兩個配置。  
  
## <a name="differences-in-layout-between-wpf-and-windows-forms"></a>版面配置 WPF 和 Windows Form 之間的差異  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用解析度獨立版面配置。 所有[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用指定的配置維度*裝置無關的像素*。 與裝置無關的像素是一個 90-第六個英吋的大小與解析度無關，因此會發生類似的結果，不論您是否呈現 72 dpi 監視器或 19200 dpi 印表機。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]此外亦根據*動態配置*。 這表示 UI 項目，在表單或頁面根據其內容、 其父版面配置容器和可用的螢幕大小來排列本身。 動態版面配置包含的字串長度變更時，自動調整的大小和位置的 UI 項目，從而完成當地語系化。  
  
 在 版面配置[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]是裝置而異，更容易為靜態。 一般而言，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]使用硬體像素為單位指定維度的表單上控制項絕對定位。 不過，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]並支援某些動態配置功能，在下表將摘要說明。  
  
|版面配置功能|說明|  
|--------------------|-----------------|  
|自動調整大小|某些[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項調整大小，才能夠正確顯示其內容。 如需詳細資訊，請參閱[AutoSize 屬性概觀](../../../../docs/framework/winforms/controls/autosize-property-overview.md)。|  
|錨定和停駐|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項支援定位和調整大小基礎的父容器。 如需詳細資訊，請參閱 <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType> 與 <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>。|  
|自動調整|容器控制項調整大小本身和其子系根據輸出裝置或大小，單位為像素的預設容器字型的解析度。 如需詳細資訊，請參閱[Windows Form 中的自動調整](../../../../docs/framework/winforms/automatic-scaling-in-windows-forms.md)。|  
|版面配置容器|<xref:System.Windows.Forms.FlowLayoutPanel>和<xref:System.Windows.Forms.TableLayoutPanel>控制項排列其子控制項，並根據其內容調整本身的大小。|  
  
## <a name="layout-limitations"></a>版面配置限制  
 一般情況下，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項無法調整及轉換為範圍中可能有[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。 下列清單描述已知的限制時<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目會嘗試將其裝載整合[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項放入[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版面配置系統。  
  
-   在某些情況下，無法調整 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項大小，或只能將它調整為特定維度。 例如， [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox>控制項支援只有單一高度定義控制項的字型大小。 在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]其中項目可以垂直延伸，裝載的動態配置<xref:System.Windows.Forms.ComboBox>控制項將會自動縮放如預期般。  
  
-   無法旋轉或扭曲 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>項目引發<xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>事件，如果您將會套用傾斜或旋轉轉換。 如果您沒有處理<xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>事件， <xref:System.InvalidOperationException> ，就會引發。  
  
-   在大部分情況下，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項不支援等比例縮放。 雖然會縮放控制項的整體維度，但是可能無法如預期調整控制項的子控制項和元件大小。 這項限制取決於每個 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項支援縮放比例的程度。 此外，您無法擴充[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]向 0 像素大小的控制項。  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項支援自動調整，以表單將自動調整大小本身和字型大小，依據其控制項。 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用者介面中，變更字型大小並不會調整整個版面配置大小，雖然可能會動態調整個別項目。  
  
### <a name="z-order"></a>疊置順序  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用者介面中，您可以變更項目的 Z 順序以控制重疊行為。 裝載的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項會以不同的 HWND 進行繪製，因此一律會將它繪製在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 項目頂端。  
  
 裝載[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]之上任何也繪製控制項<xref:System.Windows.Documents.Adorner>項目。  
  
## <a name="layout-behavior"></a>配置行為  
 下列章節說明特定層面的配置行為，當裝載[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。  
  
### <a name="scaling-unit-conversion-and-device-independence"></a>縮放比例單位轉換與裝置獨立  
 每當<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目執行作業[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]和[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]所涉及的維度，這兩個座標系統： 與裝置無關像素[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]和硬體像素[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]。 因此，您必須套用適當的單位和縮放轉換，以達到一致的版面配置。  
  
 座標系統之間的轉換取決於目前的裝置解析度和任何配置或呈現轉換套用至<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目或其祖系。  
  
 如果輸出裝置是 96 dpi，沒有縮放已套用至<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目，一個與裝置無關的像素等於一個硬體像素。  
  
 所有其他情況下需要調整座標系統。 裝載的控制項不會重新調整。 相反地，<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目會嘗試調整裝載的控制項和所有子控制項。 因為[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]不完全支援縮放比例，<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目會調整為特定控制項所支援的程度。  
  
 覆寫<xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A>方法以提供自訂的縮放行為的裝載[!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)]控制項。  
  
 除了擴充之外，<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目會處理捨入和溢位的情況下下, 表中所述。  
  
|轉換問題|說明|  
|----------------------|-----------------|  
|四捨五入|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]裝置獨立畫素維度已指定為`double`，和[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]硬體像素維度已指定為`int`。 萬一其中`double`-根據的維度會轉換成`int`-基礎維度<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目使用標準的捨入，以便小於 0.5 小數的值會無條件捨去至 0。|  
|溢位|當<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素將從轉換`double`值`int`值，可能會溢位。 值大於<xref:System.Int32.MaxValue>設為<xref:System.Int32.MaxValue>。|  
  
### <a name="layout-related-properties"></a>與配置有關的屬性  
 屬性可控制中的配置行為[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]項目適當地對應<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目。 如需詳細資訊，請參閱 [Windows Form 和 WPF 屬性對應](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)。  
  
### <a name="layout-changes-in-the-hosted-control"></a>裝載控制項的配置變更  
 中主控的版面配置變更[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制會傳播至[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]觸發配置更新。 <xref:System.Windows.UIElement.InvalidateMeasure%2A>方法<xref:System.Windows.Forms.Integration.WindowsFormsHost>可確保裝載控制項的配置變更，導致[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版面配置引擎來執行。  
  
### <a name="continuously-sized-windows-forms-controls"></a>持續的大小調整 Windows Form 控制項  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項支援連續調整完整互動[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版面配置系統。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>項目使用<xref:System.Windows.FrameworkElement.MeasureOverride%2A>和<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>方法，如往常般以調整大小和排列託管[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項。  
  
### <a name="sizing-algorithm"></a>調整大小演算法  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>項目使用下列程序來裝載的控制項的大小：  
  
1.  <xref:System.Windows.Forms.Integration.WindowsFormsHost>元素會覆寫<xref:System.Windows.FrameworkElement.MeasureOverride%2A>和<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>方法。  
  
2.  若要判斷與裝載的控制項的大小<xref:System.Windows.FrameworkElement.MeasureOverride%2A>方法會呼叫裝載的控制項的<xref:System.Windows.Forms.Control.GetPreferredSize%2A>從條件約束傳遞至轉譯方法具有條件約束<xref:System.Windows.FrameworkElement.MeasureOverride%2A>方法。  
  
3.  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>方法嘗試將指定的大小條件約束設定裝載的控制項。  
  
4.  如果裝載的控制項<xref:System.Windows.Forms.Control.Size%2A>屬性符合指定的條件約束，裝載的控制項的大小調整成條件約束。  
  
 如果<xref:System.Windows.Forms.Control.Size%2A>屬性不符合指定的條件約束，裝載的控制項不支援連續的調整大小。 例如，<xref:System.Windows.Forms.MonthCalendar>控制項可讓不連續的大小。 對這個控制項允許的大小會組成高度和寬度的整數 （表示的月份數）。 在此情況下<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素的行為，如下所示：  
  
-   如果<xref:System.Windows.Forms.Control.Size%2A>屬性會傳回與指定的條件約束，較大的大小<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素裁剪裝載的控制項。 高度和寬度會個別處理，讓裝載的控制項可能會裁剪任一方向。  
  
-   如果<xref:System.Windows.Forms.Control.Size%2A>屬性會傳回與指定的條件約束，較小的大小<xref:System.Windows.Forms.Integration.WindowsFormsHost>接受這個大小值，並傳回值，以[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版面配置系統。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [逐步解說：在 WPF 中排列 Windows Forms 控制項](../../../../docs/framework/wpf/advanced/walkthrough-arranging-windows-forms-controls-in-wpf.md)  
 [排列 Windows Form 控制項中的 WPF 範例](http://go.microsoft.com/fwlink/?LinkID=159971)  
 [Windows Forms 和 WPF 屬性對應](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [移轉和互通性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
