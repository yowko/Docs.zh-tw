---
title: Windows Form 和 WPF 屬性對應
ms.date: 03/30/2017
helpviewer_keywords:
- property mapping [WPF interoperability]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 999d8298-9c04-467d-a453-86e41002057d
ms.openlocfilehash: ae4a97bc96a4f9e93942b4995f488c427fda3134
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917504"
---
# <a name="windows-forms-and-wpf-property-mapping"></a>Windows Form 和 WPF 屬性對應
[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]技術有兩個相似但不同的屬性模型。 *屬性對應*支援兩種架構之間的互通性, 並提供下列功能:  
  
- 可讓您輕鬆地將主機環境中相關的屬性變更對應至裝載的控制項或元素。  
  
- 提供預設處理, 以便對應最常使用的屬性。  
  
- 允許輕鬆移除、覆寫或擴充預設屬性。  
  
- 確保會自動偵測主機上的屬性值變更, 並將其轉譯為裝載的控制項或元素。  
  
> [!NOTE]
> 屬性變更事件不會在裝載控制項或元素階層中向上傳播。 如果屬性的本機值因為直接設定、樣式、繼承、資料系結或其他變更屬性值的機制而不會變更, 則不會執行屬性轉譯。  
  
 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> <xref:System.Windows.Forms.Integration.ElementHost>使用專案<xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> <xref:System.Windows.Forms.Integration.WindowsFormsHost>上的屬性和控制項上的屬性來存取屬性對應。  
  
## <a name="property-mapping-with-the-windowsformshost-element"></a>具有 WindowsFormsHost 元素的屬性對應  
 元素會使用下列[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]轉譯表, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]將預設屬性轉換為其對等專案。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
  
|Windows Presentation Foundation 裝載|Windows Forms|交互操作行為|  
|---------------------------------------------|-------------------|-----------------------------|  
|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|元素會設定裝載控制項的<xref:System.Windows.Forms.Control.BackgroundImage%2A> 屬性,以及裝載控制項的屬性。<xref:System.Windows.Forms.Control.BackColor%2A> <xref:System.Windows.Forms.Integration.WindowsFormsHost> 對應是使用下列規則來執行:<br /><br /> -如果<xref:System.Windows.Controls.Control.Background%2A>是純色, 則會轉換並用來設定裝載控制項的<xref:System.Windows.Forms.Control.BackColor%2A>屬性。 未在裝載的控制項上設定<xref:System.Windows.Forms.Control.BackColor%2A> 屬性,因為裝載的控制項可以繼承屬性的值。<xref:System.Windows.Forms.Control.BackColor%2A> **注意：** 裝載的控制項不支援透明度。 指派給<xref:System.Windows.Forms.Control.BackColor%2A>的任何色彩都必須是完全不透明的, 且 Alpha 值為0xff。 <br /><br /> -如果<xref:System.Windows.Controls.Control.Background%2A>不是純色<xref:System.Windows.Forms.Integration.WindowsFormsHost> , 控制項會從<xref:System.Windows.Controls.Control.Background%2A>屬性建立點陣圖。 控制項會將這個點陣圖指派給裝載<xref:System.Windows.Forms.Control.BackgroundImage%2A>控制項的屬性。 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 這會提供類似于透明度的效果。 **注意：** 您可以覆寫此行為, 也可以移除<xref:System.Windows.Controls.Control.Background%2A>屬性對應。|  
|<xref:System.Windows.FrameworkElement.Cursor%2A>|<xref:System.Windows.Forms.Control.Cursor%2A>|如果尚未重新指派預設的對應, 控制權<xref:System.Windows.Forms.Integration.WindowsFormsHost>就會遍歷其上階階層, 直到找到其<xref:System.Windows.FrameworkElement.Cursor%2A>屬性設定的上階為止。 這個值會轉譯為最接近的[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]對應資料指標。<br /><br /> 如果尚未重新指派<xref:System.Windows.FrameworkElement.ForceCursor%2A>屬性的預設對應, 則會在<xref:System.Windows.FrameworkElement.ForceCursor%2A>設定為`true`的第一個上階上停止遍歷。|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FlowDirection.LeftToRight>對應至<xref:System.Windows.Forms.RightToLeft.No>。<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft>對應至<xref:System.Windows.Forms.RightToLeft.Yes>。<br /><br /> <xref:System.Windows.Forms.RightToLeft.Inherit>未對應。<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType>對應至<xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType>。|  
|<xref:System.Windows.Controls.Control.FontStyle%2A>|<xref:System.Drawing.Font.Style%2A>在主控控制項的<xref:System.Drawing.Font?displayProperty=nameWithType>|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]屬性集會轉譯成對應<xref:System.Drawing.Font>的。 當其中一個屬性變更時, 就會<xref:System.Drawing.Font>建立新的。 針對<xref:System.Windows.FontStyles.Normal%2A> :<xref:System.Drawing.FontStyle.Italic>已停用。 針對<xref:System.Windows.FontStyles.Italic%2A>或<xref:System.Windows.FontStyles.Oblique%2A> :<xref:System.Drawing.FontStyle.Italic>已啟用。|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Drawing.Font.Style%2A>在主控控制項的<xref:System.Drawing.Font?displayProperty=nameWithType>|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]屬性集會轉譯成對應<xref:System.Drawing.Font>的。 當其中一個屬性變更時, 就會<xref:System.Drawing.Font>建立新的。 對於<xref:System.Windows.FontWeights.Black%2A>、 <xref:System.Windows.FontWeights.Bold%2A> 、<xref:System.Windows.FontWeights.DemiBold%2A>、、 、<xref:System.Windows.FontWeights.Medium%2A>、或:<xref:System.Windows.FontWeights.UltraBold%2A>已啟用<xref:System.Drawing.FontStyle.Bold> 。 <xref:System.Windows.FontWeights.ExtraBold%2A> <xref:System.Windows.FontWeights.Heavy%2A> <xref:System.Windows.FontWeights.SemiBold%2A> 對於<xref:System.Windows.FontWeights.ExtraLight%2A>、 <xref:System.Windows.FontWeights.Light%2A>、 、、<xref:System.Windows.FontWeights.UltraLight%2A>或:已<xref:System.Drawing.FontStyle.Bold>停用。 <xref:System.Windows.FontWeights.Regular%2A> <xref:System.Windows.FontWeights.Normal%2A> <xref:System.Windows.FontWeights.Thin%2A>|  
|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]屬性集會轉譯成對應<xref:System.Drawing.Font>的。 當其中一個屬性變更時, 就會<xref:System.Drawing.Font>建立新的。 裝載的[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項會根據字型大小調整大小。<br /><br /> 中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的字型大小會表示為一英寸的 90-6, 而在中[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]則會以一英寸的一到1個。 對應的轉換如下:<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]字型大小 = [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]字型大小 * 72.0/96.0。|  
|<xref:System.Windows.Controls.Control.Foreground%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.ForeColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Foreground%2A>屬性對應是使用下列規則來執行:<br /><br /> -如果<xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Media.SolidColorBrush.Color%2A>是, 請使用做<xref:System.Windows.Forms.Control.ForeColor%2A>為。 <xref:System.Windows.Media.SolidColorBrush><br />-如果<xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Media.GradientStop>是, 請使用具有最低位移值<xref:System.Windows.Forms.Control.ForeColor%2A>的色彩。 <xref:System.Windows.Media.GradientBrush><br />-若為任何<xref:System.Windows.Media.Brush>其他類型, <xref:System.Windows.Forms.Control.ForeColor%2A>請保持不變。 這表示會使用預設值。|  
|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A>|當<xref:System.Windows.UIElement.IsEnabled%2A>設定時, <xref:System.Windows.Forms.Integration.WindowsFormsHost>元素會在<xref:System.Windows.Forms.Control.Enabled%2A>裝載的控制項上設定屬性。|  
|<xref:System.Windows.Controls.Control.Padding%2A>|<xref:System.Windows.Forms.Control.Padding%2A>|裝載<xref:System.Windows.Forms.Control.Padding%2A> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項上屬性的四個值都會設定為相同<xref:System.Windows.Thickness>的值。<br /><br /> -大於<xref:System.Int32.MaxValue>的值會設定為<xref:System.Int32.MaxValue>。<br />-小於<xref:System.Int32.MinValue>的值會設定為<xref:System.Int32.MinValue>。|  
|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Control.Visible%2A>|-   <xref:System.Windows.Visibility.Visible>對應至<xref:System.Windows.Forms.Control.Visible%2A>。  =  `true` 裝載的[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項是可見的。 不建議將<xref:System.Windows.Forms.Control.Visible%2A>裝載控制項上的屬性明確`false`設定為。<br />-   <xref:System.Windows.Visibility.Collapsed>對應至<xref:System.Windows.Forms.Control.Visible%2A>  =  或。`true` `false` 裝載的[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項不會繪製, 而且其區域會折迭。<br />-   <xref:System.Windows.Visibility.Hidden>:裝載的[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項會佔用配置中的空間, 但看不到。 在此情況下, <xref:System.Windows.Forms.Control.Visible%2A>屬性會設定為`true`。 不建議將<xref:System.Windows.Forms.Control.Visible%2A>裝載控制項上的屬性明確`false`設定為。|  
  
 元素會完全支援容器元素上的<xref:System.Windows.Forms.Integration.WindowsFormsHost>附加屬性。  
  
 如需詳細資訊，請參閱[逐步解說：使用 WindowsFormsHost 元素](walkthrough-mapping-properties-using-the-windowsformshost-element.md)對應屬性。  
  
## <a name="updates-to-parent-properties"></a>父屬性的更新  
 對大部分的父系屬性所做的變更, 會使通知裝載于主控的子控制項。 下列清單描述在其值變更時不會造成通知的屬性。  
  
- <xref:System.Windows.Controls.Control.Background%2A>  
  
- <xref:System.Windows.FrameworkElement.Cursor%2A>  
  
- <xref:System.Windows.FrameworkElement.ForceCursor%2A>  
  
- <xref:System.Windows.UIElement.Visibility%2A>  
  
 例如, 如果您變更<xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Forms.Integration.WindowsFormsHost>元素的屬性值, <xref:System.Windows.Forms.Control.BackColor%2A>則裝載控制項的屬性不會變更。  
  
## <a name="property-mapping-with-the-elementhost-control"></a>使用 ElementHost 控制項的屬性對應  
 下列屬性會提供內建的變更通知。 當您對應這些<xref:System.Windows.FrameworkElement.OnPropertyChanged%2A>屬性時, 請勿呼叫方法:  
  
- AutoSize  
  
- BackColor  
  
- BackgroundImage  
  
- BackgroundImageLayout  
  
- BindingContext  
  
- CausesValidation  
  
- ContextMenu  
  
- ContextMenuStrip  
  
- 資料指標  
  
- 停駐  
  
- 已啟用  
  
- 字型  
  
- ForeColor  
  
- 位置  
  
- 邊界  
  
- 與邊框距離  
  
- 父代  
  
- 區域  
  
- RightToLeft  
  
- 大小  
  
- TabIndex  
  
- TabStop  
  
- 文字  
  
- Visible  
  
 控制項會使用下列翻譯[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]表, 將[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]預設屬性轉換為其對等專案。 <xref:System.Windows.Forms.Integration.ElementHost>  
  
 如需詳細資訊，請參閱[逐步解說：使用 ElementHost 控制項](walkthrough-mapping-properties-using-the-elementhost-control.md)對應屬性。  
  
|Windows Forms 裝載|Windows Presentation Foundation|交互操作行為|  
|---------------------------|-------------------------------------|-----------------------------|  
|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) 在託管元素上|設定此屬性會強制重新繪製<xref:System.Windows.Media.ImageBrush>。 <xref:System.Windows.Forms.Integration.ElementHost> <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Forms.Control.BackgroundImage%2A> <xref:System.Windows.Forms.Control.BackColor%2A> <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>如果屬性設為`false` (預設值), 則這是根據控制項的外觀, 包括其、、屬性和任何附加的繪製<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>處理常式.<br /><br /> <xref:System.Windows.Forms.Integration.ElementHost> `true` <xref:System.Windows.Forms.Control.BackColor%2A> <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> <xref:System.Windows.Forms.Control.BackgroundImage%2A>如果屬性設定為, <xref:System.Windows.Media.ImageBrush>則會以控制項父系的外觀為基礎, 包括父系的、、屬性和任何附加的繪製<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>處理常式.|  
|<xref:System.Windows.Forms.Control.BackgroundImage%2A><br /><br /> (<xref:System.Drawing.Image?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) 在託管元素上|設定此屬性會導致<xref:System.Windows.Forms.Control.BackColor%2A>對應所述的相同行為。|  
|<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) 在託管元素上|設定此屬性會導致<xref:System.Windows.Forms.Control.BackColor%2A>對應所述的相同行為。|  
|<xref:System.Windows.Forms.Control.Cursor%2A><br /><br /> (<xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.Cursor%2A><br /><br /> (<xref:System.Windows.Input.Cursor?displayProperty=nameWithType>)|標準資料指標會轉譯成對應[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的標準資料指標。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]如果不是標準資料指標, 則會指派預設值。|  
|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A>|當<xref:System.Windows.Forms.Control.Enabled%2A>設定時<xref:System.Windows.Forms.Integration.ElementHost> , 控制項會在裝載的<xref:System.Windows.UIElement.IsEnabled%2A>元素上設定屬性。|  
|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|此<xref:System.Windows.Forms.Control.Font%2A>值會轉譯成一組對應的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]字型屬性。|  
|<xref:System.Drawing.Font.Bold%2A>|<xref:System.Windows.Controls.Control.FontWeight%2A>在託管元素上|如果 <xref:System.Drawing.Font.Bold%2A> 為 `true`，則會將 <xref:System.Windows.Controls.Control.FontWeight%2A> 設為 <xref:System.Windows.FontWeights.Bold%2A>。<br /><br /> 如果 <xref:System.Drawing.Font.Bold%2A> 為 `false`，則會將 <xref:System.Windows.Controls.Control.FontWeight%2A> 設為 <xref:System.Windows.FontWeights.Normal%2A>。|  
|<xref:System.Drawing.Font.Italic%2A>|<xref:System.Windows.Controls.Control.FontStyle%2A>在託管元素上|如果 <xref:System.Drawing.Font.Italic%2A> 為 `true`，則會將 <xref:System.Windows.Controls.Control.FontStyle%2A> 設為 <xref:System.Windows.FontStyles.Italic%2A>。<br /><br /> 如果 <xref:System.Drawing.Font.Italic%2A> 為 `false`，則會將 <xref:System.Windows.Controls.Control.FontStyle%2A> 設為 <xref:System.Windows.FontStyles.Normal%2A>。|  
|<xref:System.Drawing.Font.Strikeout%2A>|<xref:System.Windows.TextDecorations>在託管元素上|僅適用于裝載<xref:System.Windows.Controls.TextBlock>控制項時。|  
|<xref:System.Drawing.Font.Underline%2A>|<xref:System.Windows.TextDecorations>在託管元素上|僅適用于裝載<xref:System.Windows.Controls.TextBlock>控制項時。|  
|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection>)|<xref:System.Windows.Forms.RightToLeft.No>對應至<xref:System.Windows.FlowDirection.LeftToRight>。<br /><br /> <xref:System.Windows.Forms.RightToLeft.Yes>對應至<xref:System.Windows.FlowDirection.RightToLeft>。|  
|<xref:System.Windows.Forms.Control.Visible%2A>|<xref:System.Windows.UIElement.Visibility%2A>|控制項會使用下列規則<xref:System.Windows.UIElement.Visibility%2A> , 在裝載的元素上設定屬性: <xref:System.Windows.Forms.Integration.ElementHost><br /><br /> -   <xref:System.Windows.Forms.Control.Visible%2A> = `true`對應至<xref:System.Windows.Visibility.Visible>。<br />-   <xref:System.Windows.Forms.Control.Visible%2A> = `false`對應至<xref:System.Windows.Visibility.Hidden>。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [WPF 和 Win32 交互操作](wpf-and-win32-interoperation.md)
- [WPF 和 Windows Forms 互通](wpf-and-windows-forms-interoperation.md)
- [逐步解說：使用 WindowsFormsHost 元素對應屬性](walkthrough-mapping-properties-using-the-windowsformshost-element.md)
- [逐步解說：使用 ElementHost 控制項對應屬性](walkthrough-mapping-properties-using-the-elementhost-control.md)
