---
title: Windows Form 和 WPF 屬性對應
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- property mapping [WPF interoperability]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 999d8298-9c04-467d-a453-86e41002057d
ms.openlocfilehash: 45d86ac1b65306c8f404f9cea1e663b67128ebc4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794066"
---
# <a name="windows-forms-and-wpf-property-mapping"></a>Windows Form 和 WPF 屬性對應
Windows Forms 和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 技術有兩個相似但不同的屬性模型。 *屬性對應*支援兩種架構之間的互通性，並提供下列功能：  
  
- 可讓您輕鬆地將主機環境中相關的屬性變更對應至裝載的控制項或元素。  
  
- 提供預設處理，以便對應最常使用的屬性。  
  
- 允許輕鬆移除、覆寫或擴充預設屬性。  
  
- 確保會自動偵測主機上的屬性值變更，並將其轉譯為裝載的控制項或元素。  
  
> [!NOTE]
> 屬性變更事件不會在裝載控制項或元素階層中向上傳播。 如果屬性的本機值因為直接設定、樣式、繼承、資料系結或其他變更屬性值的機制而不會變更，則不會執行屬性轉譯。  
  
 請使用 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素上的 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> 屬性和 <xref:System.Windows.Forms.Integration.ElementHost> 控制項上的 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> 屬性來存取屬性對應。  
  
## <a name="property-mapping-with-the-windowsformshost-element"></a>具有 WindowsFormsHost 元素的屬性對應  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素會使用下列轉譯表，將預設 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性轉譯為其 Windows Forms 對等專案。  
  
|Windows Presentation Foundation 裝載|Windows 表單|交互操作行為|  
|---------------------------------------------|-------------------|-----------------------------|  
|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素會設定裝載控制項的 <xref:System.Windows.Forms.Control.BackColor%2A> 屬性和裝載控制項的 <xref:System.Windows.Forms.Control.BackgroundImage%2A> 屬性。 對應是使用下列規則來執行：<br /><br /> -如果 <xref:System.Windows.Controls.Control.Background%2A> 是純色，則會轉換並用來設定裝載控制項的 <xref:System.Windows.Forms.Control.BackColor%2A> 屬性。 未在裝載的控制項上設定 <xref:System.Windows.Forms.Control.BackColor%2A> 屬性，因為裝載的控制項可以繼承 <xref:System.Windows.Forms.Control.BackColor%2A> 屬性的值。 **注意：** 裝載的控制項不支援透明度。 指派給 <xref:System.Windows.Forms.Control.BackColor%2A> 的任何色彩都必須是完全不透明的，且 Alpha 值是0xFF。 <br /><br /> -如果 <xref:System.Windows.Controls.Control.Background%2A> 不是純色，則 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項會從 <xref:System.Windows.Controls.Control.Background%2A> 屬性建立點陣圖。 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項會將這個點陣圖指派給裝載控制項的 <xref:System.Windows.Forms.Control.BackgroundImage%2A> 屬性。 這會提供類似于透明度的效果。 **注意：** 您可以覆寫此行為，也可以移除 <xref:System.Windows.Controls.Control.Background%2A> 屬性對應。|  
|<xref:System.Windows.FrameworkElement.Cursor%2A>|<xref:System.Windows.Forms.Control.Cursor%2A>|如果尚未重新指派預設的對應，<xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項就會遍歷其上階階層，直到找到其 <xref:System.Windows.FrameworkElement.Cursor%2A> 屬性集的上階為止。 這個值會轉譯為最接近的對應 Windows Forms 資料指標。<br /><br /> 如果 <xref:System.Windows.FrameworkElement.ForceCursor%2A> 屬性的預設對應尚未重新指派，則會在具有 <xref:System.Windows.FrameworkElement.ForceCursor%2A> 設定為 `true`的第一個上階上停止遍歷。|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FlowDirection.LeftToRight> 對應至 <xref:System.Windows.Forms.RightToLeft.No>。<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft> 對應至 <xref:System.Windows.Forms.RightToLeft.Yes>。<br /><br /> <xref:System.Windows.Forms.RightToLeft.Inherit> 未對應。<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> 對應至 <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType>。|  
|<xref:System.Windows.Controls.Control.FontStyle%2A>|主控控制項的 <xref:System.Drawing.Font?displayProperty=nameWithType> 上的 <xref:System.Drawing.Font.Style%2A>|這組 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性會轉譯成對應的 <xref:System.Drawing.Font>。 當其中一個屬性變更時，就會建立新的 <xref:System.Drawing.Font>。 針對 <xref:System.Windows.FontStyles.Normal%2A>： <xref:System.Drawing.FontStyle.Italic> 已停用。 若為 <xref:System.Windows.FontStyles.Italic%2A> 或 <xref:System.Windows.FontStyles.Oblique%2A>： <xref:System.Drawing.FontStyle.Italic> 已啟用。|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|主控控制項的 <xref:System.Drawing.Font?displayProperty=nameWithType> 上的 <xref:System.Drawing.Font.Style%2A>|這組 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性會轉譯成對應的 <xref:System.Drawing.Font>。 當其中一個屬性變更時，就會建立新的 <xref:System.Drawing.Font>。 針對 <xref:System.Windows.FontWeights.Black%2A>、<xref:System.Windows.FontWeights.Bold%2A>、<xref:System.Windows.FontWeights.DemiBold%2A>、<xref:System.Windows.FontWeights.ExtraBold%2A>、<xref:System.Windows.FontWeights.Heavy%2A>、<xref:System.Windows.FontWeights.Medium%2A>、<xref:System.Windows.FontWeights.SemiBold%2A>或 <xref:System.Windows.FontWeights.UltraBold%2A>：已啟用 <xref:System.Drawing.FontStyle.Bold>。 針對 <xref:System.Windows.FontWeights.ExtraLight%2A>、<xref:System.Windows.FontWeights.Light%2A>、<xref:System.Windows.FontWeights.Normal%2A>、<xref:System.Windows.FontWeights.Regular%2A>、<xref:System.Windows.FontWeights.Thin%2A>或 <xref:System.Windows.FontWeights.UltraLight%2A>：已停用 <xref:System.Drawing.FontStyle.Bold>。|  
|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|這組 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性會轉譯成對應的 <xref:System.Drawing.Font>。 當其中一個屬性變更時，就會建立新的 <xref:System.Drawing.Font>。 主控的 Windows Forms 控制項會根據字型大小調整大小。<br /><br /> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的字型大小是以一英寸的 90-6 表示，而在 Windows Forms 中是以一英寸的七十為單位。 對應的轉換如下：<br /><br /> Windows Forms 字型大小 = [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 字型大小 * 72.0/96.0。|  
|<xref:System.Windows.Controls.Control.Foreground%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.ForeColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Foreground%2A> 屬性對應是使用下列規則來執行：<br /><br /> -如果 <xref:System.Windows.Controls.Control.Foreground%2A> 是 <xref:System.Windows.Media.SolidColorBrush>，請使用 <xref:System.Windows.Forms.Control.ForeColor%2A>的 <xref:System.Windows.Media.SolidColorBrush.Color%2A>。<br />-如果 <xref:System.Windows.Controls.Control.Foreground%2A> 是 <xref:System.Windows.Media.GradientBrush>，請使用 <xref:System.Windows.Forms.Control.ForeColor%2A>的最低位移值 <xref:System.Windows.Media.GradientStop> 的色彩。<br />-若為任何其他 <xref:System.Windows.Media.Brush> 類型，保持 <xref:System.Windows.Forms.Control.ForeColor%2A> 不變。 這表示會使用預設值。|  
|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A>|設定 <xref:System.Windows.UIElement.IsEnabled%2A> 時，<xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素會在裝載的控制項上設定 <xref:System.Windows.Forms.Control.Enabled%2A> 屬性。|  
|<xref:System.Windows.Controls.Control.Padding%2A>|<xref:System.Windows.Forms.Control.Padding%2A>|在裝載的 Windows Forms 控制項上，<xref:System.Windows.Forms.Control.Padding%2A> 屬性的全部四個值都會設定為相同的 <xref:System.Windows.Thickness> 值。<br /><br /> -大於 <xref:System.Int32.MaxValue> 的值會設定為 <xref:System.Int32.MaxValue>。<br />-小於 <xref:System.Int32.MinValue> 的值會設定為 <xref:System.Int32.MinValue>。|  
|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Control.Visible%2A>|-   <xref:System.Windows.Visibility.Visible> 對應至 <xref:System.Windows.Forms.Control.Visible%2A> = `true`。 主控的 Windows Forms 控制項是可見的。 不建議將裝載控制項上的 <xref:System.Windows.Forms.Control.Visible%2A> 屬性明確設定為 [`false`]。<br />-   <xref:System.Windows.Visibility.Collapsed> 對應至 <xref:System.Windows.Forms.Control.Visible%2A> = `true` 或 `false`。 主控的 Windows Forms 控制項不會繪製，而且其區域會折迭。<br />-   <xref:System.Windows.Visibility.Hidden>：主控的 Windows Forms 控制項佔用配置中的空間，但看不到。 在此情況下，<xref:System.Windows.Forms.Control.Visible%2A> 屬性會設定為 `true`。 不建議將裝載控制項上的 <xref:System.Windows.Forms.Control.Visible%2A> 屬性明確設定為 [`false`]。|  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素完全支援容器元素上的附加屬性。  
  
 如需詳細資訊，請參閱[逐步解說：使用 WindowsFormsHost 元素對應屬性](walkthrough-mapping-properties-using-the-windowsformshost-element.md)。  
  
## <a name="updates-to-parent-properties"></a>父屬性的更新  
 對大部分的父系屬性所做的變更，會使通知裝載于主控的子控制項。 下列清單描述在其值變更時不會造成通知的屬性。  
  
- <xref:System.Windows.Controls.Control.Background%2A>  
  
- <xref:System.Windows.FrameworkElement.Cursor%2A>  
  
- <xref:System.Windows.FrameworkElement.ForceCursor%2A>  
  
- <xref:System.Windows.UIElement.Visibility%2A>  
  
 例如，如果您變更 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素的 <xref:System.Windows.Controls.Control.Background%2A> 屬性值，則裝載控制項的 <xref:System.Windows.Forms.Control.BackColor%2A> 屬性不會變更。  
  
## <a name="property-mapping-with-the-elementhost-control"></a>使用 ElementHost 控制項的屬性對應  
 下列屬性會提供內建的變更通知。 當您對應這些屬性時，請勿呼叫 <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> 方法：  
  
- 自動調整大小  
  
- BackColor  
  
- BackgroundImage  
  
- BackgroundImageLayout  
  
- BindingCoNtext  
  
- CausesValidation  
  
- ContextMenu  
  
- ContextMenuStrip  
  
- Cursor  
  
- 停駐  
  
- Enabled  
  
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
  
 <xref:System.Windows.Forms.Integration.ElementHost> 控制項會使用下列翻譯表，將預設 Windows Forms 屬性轉譯為其 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 對等專案。  
  
 如需詳細資訊，請參閱[逐步解說：使用 ElementHost 控制項對應屬性](walkthrough-mapping-properties-using-the-elementhost-control.md)。  
  
|Windows Forms 裝載|Windows Presentation Foundation|交互操作行為|  
|---------------------------|-------------------------------------|-----------------------------|  
|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> 託管元素上的（<xref:System.Windows.Media.Brush?displayProperty=nameWithType>）|設定此屬性會強制重新繪製 <xref:System.Windows.Media.ImageBrush>。 如果 <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> 屬性設為 `false` （預設值），則此 <xref:System.Windows.Media.ImageBrush> 是以 <xref:System.Windows.Forms.Integration.ElementHost> 控制項的外觀為基礎，包括其 <xref:System.Windows.Forms.Control.BackColor%2A>、<xref:System.Windows.Forms.Control.BackgroundImage%2A>、<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> 屬性和任何附加的繪製處理常式。<br /><br /> 如果 [<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>] 屬性設定為 [`true`]，則 <xref:System.Windows.Media.ImageBrush> 是根據 <xref:System.Windows.Forms.Integration.ElementHost> 控制項的父系外觀，包括父系的 <xref:System.Windows.Forms.Control.BackColor%2A>、<xref:System.Windows.Forms.Control.BackgroundImage%2A>、<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> 屬性和任何附加的繪製處理常式。|  
|<xref:System.Windows.Forms.Control.BackgroundImage%2A><br /><br /> (<xref:System.Drawing.Image?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> 託管元素上的（<xref:System.Windows.Media.Brush?displayProperty=nameWithType>）|設定此屬性會導致 <xref:System.Windows.Forms.Control.BackColor%2A> 對應所述的相同行為。|  
|<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> 託管元素上的（<xref:System.Windows.Media.Brush?displayProperty=nameWithType>）|設定此屬性會導致 <xref:System.Windows.Forms.Control.BackColor%2A> 對應所述的相同行為。|  
|<xref:System.Windows.Forms.Control.Cursor%2A><br /><br /> (<xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.Cursor%2A><br /><br /> (<xref:System.Windows.Input.Cursor?displayProperty=nameWithType>)|Windows Forms 標準資料指標會轉譯成對應的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 標準資料指標。 如果 Windows Forms 不是標準資料指標，則會指派預設值。|  
|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A>|設定 <xref:System.Windows.Forms.Control.Enabled%2A> 時，<xref:System.Windows.Forms.Integration.ElementHost> 控制項會在裝載的元素上設定 <xref:System.Windows.UIElement.IsEnabled%2A> 屬性。|  
|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A> 值會轉譯成一組對應的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 字型屬性。|  
|<xref:System.Drawing.Font.Bold%2A>|裝載元素上的 <xref:System.Windows.Controls.Control.FontWeight%2A>|如果 <xref:System.Drawing.Font.Bold%2A> 為 `true`，則會將 <xref:System.Windows.Controls.Control.FontWeight%2A> 設為 <xref:System.Windows.FontWeights.Bold%2A>。<br /><br /> 如果 <xref:System.Drawing.Font.Bold%2A> 為 `false`，則會將 <xref:System.Windows.Controls.Control.FontWeight%2A> 設為 <xref:System.Windows.FontWeights.Normal%2A>。|  
|<xref:System.Drawing.Font.Italic%2A>|裝載元素上的 <xref:System.Windows.Controls.Control.FontStyle%2A>|如果 <xref:System.Drawing.Font.Italic%2A> 為 `true`，則會將 <xref:System.Windows.Controls.Control.FontStyle%2A> 設為 <xref:System.Windows.FontStyles.Italic%2A>。<br /><br /> 如果 <xref:System.Drawing.Font.Italic%2A> 為 `false`，則會將 <xref:System.Windows.Controls.Control.FontStyle%2A> 設為 <xref:System.Windows.FontStyles.Normal%2A>。|  
|<xref:System.Drawing.Font.Strikeout%2A>|裝載元素上的 <xref:System.Windows.TextDecorations>|只有在裝載 <xref:System.Windows.Controls.TextBlock> 控制項時才適用。|  
|<xref:System.Drawing.Font.Underline%2A>|裝載元素上的 <xref:System.Windows.TextDecorations>|只有在裝載 <xref:System.Windows.Controls.TextBlock> 控制項時才適用。|  
|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection>)|<xref:System.Windows.Forms.RightToLeft.No> 對應至 <xref:System.Windows.FlowDirection.LeftToRight>。<br /><br /> <xref:System.Windows.Forms.RightToLeft.Yes> 對應至 <xref:System.Windows.FlowDirection.RightToLeft>。|  
|<xref:System.Windows.Forms.Control.Visible%2A>|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Integration.ElementHost> 控制項會使用下列規則，在裝載的元素上設定 <xref:System.Windows.UIElement.Visibility%2A> 屬性：<br /><br /> -   <xref:System.Windows.Forms.Control.Visible%2A> = `true` 對應至 <xref:System.Windows.Visibility.Visible>。<br />-   <xref:System.Windows.Forms.Control.Visible%2A> = `false` 對應至 <xref:System.Windows.Visibility.Hidden>。|  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [WPF 和 Win32 交互操作](wpf-and-win32-interoperation.md)
- [WPF 和 Windows Forms 互通](wpf-and-windows-forms-interoperation.md)
- [逐步解說：使用 WindowsFormsHost 元素對應屬性](walkthrough-mapping-properties-using-the-windowsformshost-element.md)
- [逐步解說：使用 ElementHost 控制項對應屬性](walkthrough-mapping-properties-using-the-elementhost-control.md)
