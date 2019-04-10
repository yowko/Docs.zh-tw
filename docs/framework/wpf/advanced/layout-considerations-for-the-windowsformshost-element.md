---
title: WindowsFormsHost 項目的配置考量
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element layout considerations [WPF]
- dynamic layout [WPF interoperability]
- device-independent pixels
ms.assetid: 3c574597-bbde-440f-95cc-01371f1a5d9d
ms.openlocfilehash: 93aaa8e21ef483fc21297e29189d86f93fbe138a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59327850"
---
# <a name="layout-considerations-for-the-windowsformshost-element"></a>WindowsFormsHost 項目的配置考量
本主題描述如何<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目互動[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版面配置系統。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]支援不同但相似，邏輯大小及定位在表單或頁面上的項目。 當您建立混合式使用者介面 (UI) 裝載[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]中的控制項[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，則<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目整合的兩個版面配置。  
  
## <a name="differences-in-layout-between-wpf-and-windows-forms"></a>在配置中 WPF 與 Windows Form 之間的差異  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用版面配置的解析度無關。 所有[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用指定的配置維度*裝置無關的像素*。 與裝置無關的像素是一個有 90-六分之一英吋為單位的大小與解析度無關，因此取得類似的結果，不論您要轉譯 72 dpi 監視器或 19200 dpi 印表機。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 也依據*動態配置*。 這表示 UI 項目，在表單或根據其內容、 其父系版面配置容器中和可用的螢幕大小的頁面上排列本身。 動態配置其所包含的字串長度變更時，自動調整的大小和位置的 UI 項目，從而完成當地語系化。  
  
 在 版面配置[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]是裝置而異，更有可能是靜態。 一般而言，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項會使用硬體像素中指定的維度，將表單上絕對定位。 不過，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]並支援某些動態配置功能下, 表摘要說明。  
  
|版面配置功能|描述|  
|--------------------|-----------------|  
|自動調整大小|某些[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項調整大小本身無法正確顯示其內容。 如需詳細資訊，請參閱 < [AutoSize 屬性概觀](../../winforms/controls/autosize-property-overview.md)。|  
|錨定和停駐|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項支援定位和調整大小為基礎的父容器。 如需詳細資訊，請參閱 <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType> 與 <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>。|  
|自動調整|容器控制項調整大小本身與其子系根據解析度的輸出裝置或大小，單位為像素的預設容器的字型。 如需詳細資訊，請參閱 <<c0> [ 在 Windows Form 中的自動調整](../../winforms/automatic-scaling-in-windows-forms.md)。|  
|版面配置容器|<xref:System.Windows.Forms.FlowLayoutPanel>和<xref:System.Windows.Forms.TableLayoutPanel>控制項排列其子控制項，並根據其內容調整本身的大小。|  
  
## <a name="layout-limitations"></a>版面配置限制  
 一般情況下，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項無法調整，而且範圍在轉換[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。 下列清單描述已知的限制時<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目會嘗試將其裝載的整合[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項放入[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版面配置系統。  
  
-   在某些情況下，無法調整 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項大小，或只能將它調整為特定維度。 例如， [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox>控制項支援只有單一高度由控制項字型大小所定義。 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]其中項目可以垂直延伸，裝載的動態配置<xref:System.Windows.Forms.ComboBox>控制項將不會如預期延伸。  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項無法旋轉或扭曲。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>項目引發<xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>事件，如果您套用扭曲或旋轉轉換。 如果您不會處理<xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>事件， <xref:System.InvalidOperationException> ，就會引發。  
  
-   在大部分情況下，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項不支援等比例縮放。 雖然會縮放控制項的整體維度，但是可能無法如預期調整控制項的子控制項和元件大小。 這項限制取決於每個 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項支援縮放比例的程度。 此外，您無法調整[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項到 0 像素的大小。  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項支援自動調整，以表單將自動調整大小本身和它的字型大小為基礎的控制項。 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用者介面中，變更字型大小並不會調整整個版面配置大小，雖然可能會動態調整個別項目。  
  
### <a name="z-order"></a>疊置順序  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用者介面中，您可以變更項目的 Z 順序以控制重疊行為。 裝載的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項會以不同的 HWND 進行繪製，因此一律會將它繪製在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 項目頂端。  
  
 託管[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項也會繪製上方任何<xref:System.Windows.Documents.Adorner>項目。  
  
## <a name="layout-behavior"></a>版面配置行為  
 下列各節描述的版面配置行為的特定層面，裝載時[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]中的控制項[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。  
  
### <a name="scaling-unit-conversion-and-device-independence"></a>調整大小、 單位轉換和裝置獨立性  
 每當<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目執行的作業涉及[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]並[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]牽涉到兩個座標系統的維度： 裝置獨立像素[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]和硬體像素[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]。 因此，您必須套用適當的單位和縮放轉換，以達到一致的版面配置。  
  
 座標系統之間的轉換取決於目前的裝置解析度和任何配置或轉譯轉換套用至<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目或其祖系。  
  
 如果在輸出裝置是 96 dpi，且無縮放已套用至<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目，一個以與裝置無關的像素等於一個硬體像素。  
  
 所有其他情況下需要座標系統中調整。 裝載的控制項不會重新調整。 相反地，<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目會嘗試調整裝載的控制項及其所有子控制項。 因為[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]不完全支援縮放比例、<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目調整為特定的控制項支援的程度。  
  
 覆寫<xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A>方法，以提供裝載 Windows Forms 控制項的自訂的調整行為。  
  
 除了調整<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目處理捨入和溢位的情況下下, 表中所述。  
  
|轉換問題|描述|  
|----------------------|-----------------|  
|四捨五入|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 指定為與裝置無關的像素尺寸`double`，並[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]硬體像素尺寸會指定為`int`。 萬一其中`double`-根據的維度會轉換成`int`-基礎維度<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目使用標準的圓弧半徑，以便小於 0.5 的小數的值會無條件捨去為 0。|  
|溢位|當<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目將從轉換`double`值來`int`值，可能會溢位。 值大於<xref:System.Int32.MaxValue>設定為<xref:System.Int32.MaxValue>。|  
  
### <a name="layout-related-properties"></a>配置相關的屬性  
 控制項中的版面配置行為的屬性[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]項目會適當地藉由對應<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目。 如需詳細資訊，請參閱 [Windows Form 和 WPF 屬性對應](windows-forms-and-wpf-property-mapping.md)。  
  
### <a name="layout-changes-in-the-hosted-control"></a>裝載控制項中的配置變更  
 中所裝載的版面配置變更[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項都會傳播到[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]觸發版面配置更新。 <xref:System.Windows.UIElement.InvalidateMeasure%2A>方法<xref:System.Windows.Forms.Integration.WindowsFormsHost>可確保裝載控制項中的配置變更會造成[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版面配置引擎來執行。  
  
### <a name="continuously-sized-windows-forms-controls"></a>持續調整 Windows Form 控制項  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 支援完整連續的縮放比例的控制項互動[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版面配置系統。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>項目會使用<xref:System.Windows.FrameworkElement.MeasureOverride%2A>並<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>方法，如往常般以調整大小和排列裝載[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項。  
  
### <a name="sizing-algorithm"></a>調整大小演算法  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>項目使用下列程序來裝載的控制項的大小：  
  
1. <xref:System.Windows.Forms.Integration.WindowsFormsHost>元素會覆寫<xref:System.Windows.FrameworkElement.MeasureOverride%2A>和<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>方法。  
  
2. 若要判斷所裝載的控制項的大小<xref:System.Windows.FrameworkElement.MeasureOverride%2A>方法會呼叫裝載的控制項<xref:System.Windows.Forms.Control.GetPreferredSize%2A>含有條件約束的方法會轉譯從傳遞給條件約束<xref:System.Windows.FrameworkElement.MeasureOverride%2A>方法。  
  
3. <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>方法會嘗試將指定的大小條件約束來設定裝載的控制項。  
  
4. 如果裝載的控制項<xref:System.Windows.Forms.Control.Size%2A>屬性符合指定的條件約束，裝載的控制項大小為條件約束。  
  
 如果<xref:System.Windows.Forms.Control.Size%2A>屬性不符合指定的條件約束，裝載的控制項不支援連續的調整大小。 比方說，<xref:System.Windows.Forms.MonthCalendar>控制項可讓只有離散的大小。 這個控制項允許的大小會組成高度和寬度的整數 （表示的月數）。 在此情況下<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目行為，如下所示：  
  
-   如果<xref:System.Windows.Forms.Control.Size%2A>屬性會傳回與指定的條件約束，較大的大小<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素裁剪裝載的控制項。 高度和寬度會分開處理，因此可能會裁剪裝載的控制項，在任一方向。  
  
-   如果<xref:System.Windows.Forms.Control.Size%2A>屬性會傳回與指定的條件約束，較小的大小<xref:System.Windows.Forms.Integration.WindowsFormsHost>接受這個大小值，並傳回值，以[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版面配置系統。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [逐步解說：在 WPF 中排列 Windows Forms 控制項](walkthrough-arranging-windows-forms-controls-in-wpf.md)
- [排列 Windows Form 控制項，在 WPF 範例](https://go.microsoft.com/fwlink/?LinkID=159971)
- [Windows Form 和 WPF 屬性對應](windows-forms-and-wpf-property-mapping.md)
- [移轉和互通性](migration-and-interoperability.md)
