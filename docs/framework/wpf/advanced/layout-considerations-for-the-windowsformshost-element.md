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
ms.openlocfilehash: 9f97639447284b792d52cf4aa25b81f584d7291a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76787897"
---
# <a name="layout-considerations-for-the-windowsformshost-element"></a>WindowsFormsHost 項目的配置考量
本主題描述 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素如何與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 版面配置系統互動。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 Windows Forms 支援在表單或頁面上調整大小和定位元素的不同但類似的邏輯。 當您建立在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中裝載 Windows Forms 控制項的混合式使用者介面（UI）時，<xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素會整合兩個配置配置。  
  
## <a name="differences-in-layout-between-wpf-and-windows-forms"></a>WPF 與 Windows Forms 之間的版面配置差異  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用與解析度無關的版面配置。 所有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的版面配置維度都是使用*與裝置無關的圖元*來指定。 與裝置無關的圖元是大小與解析度無關的 90-6，因此不論您是轉譯為 72 DPI 的監視器或 19200 DPI 的印表機，您都會得到類似的結果。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 也是以*動態版面*配置為基礎。 這表示 UI 元素會根據其內容、其父系版面配置容器和可用的螢幕大小，在表單或頁面上排列本身。 動態配置會在其包含的字串變更長度時，自動調整 UI 元素的大小和位置，藉此協助當地語系化。  
  
 Windows Forms 中的配置與裝置相關，而且較可能是靜態的。 一般來說，Windows Forms 控制項都是以硬體圖元中指定的維度，絕對放在表單上。 不過，Windows Forms 支援一些動態版面配置功能，如下表摘要所示。  
  
|版面配置功能|描述|  
|--------------------|-----------------|  
|自動調整大小|有些 Windows Forms 控制項會調整自己的大小，以適當地顯示其內容。 如需詳細資訊，請參閱[AutoSize 屬性總覽](../../winforms/controls/autosize-property-overview.md)。|  
|錨定和停駐|Windows Forms 控制項支援根據父容器的定位和調整大小。 如需詳細資訊，請參閱<xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>和<xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>。|  
|自動調整規模|容器控制項會根據輸出裝置的解析度或預設容器字型的大小（以圖元為單位），來調整自己及其子系的大小。 如需詳細資訊，請參閱[Windows Forms 中的自動縮放](../../winforms/automatic-scaling-in-windows-forms.md)。|  
|版面配置容器|<xref:System.Windows.Forms.FlowLayoutPanel> 和 <xref:System.Windows.Forms.TableLayoutPanel> 控制項會根據其內容，排列其子控制項和本身的大小。|  
  
## <a name="layout-limitations"></a>版面配置限制  
 一般來說，Windows Forms 控制項無法縮放並轉換成 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中的可能程度。 下列清單描述當 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素嘗試將其裝載的 Windows Forms 控制項整合到 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 版面配置系統時的已知限制。  
  
- 在某些情況下，Windows Forms 控制項無法調整大小，或只能調整為特定維度。 例如，Windows Forms <xref:System.Windows.Forms.ComboBox> 控制項僅支援單一高度，這是由控制項的字型大小所定義。 在專案可以垂直延展的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動態配置中，主控的 <xref:System.Windows.Forms.ComboBox> 控制項不會如預期般延展。  
  
- Windows Forms 控制項無法旋轉或扭曲。 如果您套用扭曲或旋轉轉換，<xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素會引發 <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> 事件。 如果您未處理 <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> 事件，則會引發 <xref:System.InvalidOperationException>。  
  
- 在大多數情況下，Windows Forms 控制項不支援比例調整。 雖然會縮放控制項的整體維度，但是可能無法如預期調整控制項的子控制項和元件大小。 這項限制取決於每個 Windows Forms 控制項支援調整的程度。 此外，您無法將 Windows Forms 控制項相應縮小為0圖元的大小。  
  
- Windows Forms 控制項支援自動調整，表單將會根據字型大小自動調整其本身及其控制項的大小。 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用者介面中，變更字型大小並不會調整整個版面配置大小，雖然可能會動態調整個別項目。  
  
### <a name="z-order"></a>迭置順序  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用者介面中，您可以變更項目的 Z 順序以控制重疊行為。 主控的 Windows Forms 控制項會在個別的 HWND 中繪製，因此一律會在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 元素的頂端繪製。  
  
 主控的 Windows Forms 控制項也會在任何 <xref:System.Windows.Documents.Adorner> 元素的上方繪製。  
  
## <a name="layout-behavior"></a>版面配置行為  
 下列各節說明在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中裝載 Windows Forms 控制項時的版面配置行為的特定層面。  
  
### <a name="scaling-unit-conversion-and-device-independence"></a>縮放、單位轉換和裝置獨立性  
 每當 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素執行涉及 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 Windows Forms 維度的作業時，就會牽涉到兩個座標系統： Windows Forms 的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和硬體圖元的裝置獨立圖元。 因此，您必須套用適當的單位和縮放轉換，以達成一致的版面配置。  
  
 座標系統之間的轉換取決於目前的裝置解析，以及套用至 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 專案或其祖系的任何版面配置或轉譯轉換。  
  
 如果輸出裝置為 96 DPI，而且未將縮放比例套用至 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素，則一個裝置獨立圖元等於一個硬體圖元。  
  
 所有其他情況都需要座標系統調整。 裝載的控制項不會調整大小。 相反地，<xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素會嘗試調整裝載的控制項及其所有子控制項。 因為 Windows Forms 不完全支援縮放，所以 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素會調整為特定控制項所支援的程度。  
  
 覆寫 <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A> 方法，為裝載的 Windows Forms 控制項提供自訂調整行為。  
  
 除了調整之外，<xref:System.Windows.Forms.Integration.WindowsFormsHost> 專案也會處理進位和溢位案例，如下表所述。  
  
|轉換問題|描述|  
|----------------------|-----------------|  
|捨入|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 裝置獨立圖元維度會指定為 `double`，Windows Forms 硬體圖元維度則指定為 `int`。 在以 `double`為基礎的維度轉換成 `int`型維度的情況下，<xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素會使用標準舍入，因此小於0.5 的小數值會四捨五入為0。|  
|溢位|當 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素從 `double` 值轉換成 `int` 值時，可能會發生溢位。 大於 <xref:System.Int32.MaxValue> 的值會設定為 <xref:System.Int32.MaxValue>。|  
  
### <a name="layout-related-properties"></a>版面配置相關屬性  
 控制 Windows Forms 控制項和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 專案之配置行為的屬性會由 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素適當地對應。 如需詳細資訊，請參閱 [Windows Form 和 WPF 屬性對應](windows-forms-and-wpf-property-mapping.md)。  
  
### <a name="layout-changes-in-the-hosted-control"></a>裝載控制項中的版面配置變更  
 主控的 Windows Forms 控制項中的配置變更會傳播至 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 以觸發版面配置更新。 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 上的 <xref:System.Windows.UIElement.InvalidateMeasure%2A> 方法可確保主控控制項中的版面配置變更會導致 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 配置引擎執行。  
  
### <a name="continuously-sized-windows-forms-controls"></a>持續調整 Windows Forms 控制項的大小  
 支援連續調整的 Windows Forms 控制項，與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 版面配置系統完全互動。 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 專案會如往常般使用 <xref:System.Windows.FrameworkElement.MeasureOverride%2A> 和 <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> 方法來調整主控 Windows Forms 控制項的大小並加以排列。  
  
### <a name="sizing-algorithm"></a>調整大小演算法  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素會使用下列程式來調整裝載控制項的大小：  
  
1. <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素會覆寫 <xref:System.Windows.FrameworkElement.MeasureOverride%2A> 和 <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> 方法。  
  
2. 為了判斷裝載控制項的大小，<xref:System.Windows.FrameworkElement.MeasureOverride%2A> 方法會呼叫裝載控制項的 <xref:System.Windows.Forms.Control.GetPreferredSize%2A> 方法，並將條件約束從傳遞給 <xref:System.Windows.FrameworkElement.MeasureOverride%2A> 方法的條件約束轉譯。  
  
3. <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> 方法會嘗試將主控的控制項設定為指定的大小條件約束。  
  
4. 如果裝載控制項的 <xref:System.Windows.Forms.Control.Size%2A> 屬性符合指定的條件約束，則裝載控制項的大小會調整為條件約束。  
  
 如果 <xref:System.Windows.Forms.Control.Size%2A> 屬性不符合指定的條件約束，裝載的控制項就不支援連續調整大小。 例如，<xref:System.Windows.Forms.MonthCalendar> 控制項只允許離散大小。 此控制項允許的大小是由整數（代表月數）的高度和寬度所組成。 在這種情況下，<xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素的行為如下所示：  
  
- 如果 <xref:System.Windows.Forms.Control.Size%2A> 屬性傳回的大小大於指定的條件約束，則 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素會裁剪裝載的控制項。 高度和寬度會分別處理，因此裝載的控制項可能會以任一方向裁剪。  
  
- 如果 <xref:System.Windows.Forms.Control.Size%2A> 屬性傳回的大小小於指定的條件約束，<xref:System.Windows.Forms.Integration.WindowsFormsHost> 會接受此大小值，並將值傳回至 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 配置系統。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [逐步解說：在 WPF 中排列 Windows Forms 控制項](walkthrough-arranging-windows-forms-controls-in-wpf.md)
- [在 WPF 範例中排列 Windows Forms 控制項](https://go.microsoft.com/fwlink/?LinkID=159971)
- [Windows Forms 和 WPF 屬性對應](windows-forms-and-wpf-property-mapping.md)
- [移轉和互通性](migration-and-interoperability.md)
