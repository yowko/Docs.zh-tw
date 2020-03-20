---
title: Expander 概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Expander
- Expander control [WPF], about Expander control
ms.assetid: 877bf425-0e54-49ec-8fd2-13a211377abb
ms.openlocfilehash: 892d972a5704d50e91d04e05d6fdea7180a3155d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187116"
---
# <a name="expander-overview"></a>Expander 概觀
控制項<xref:System.Windows.Controls.Expander>提供了一種在類似于視窗且包含標頭的可擴展區域中提供內容的方法。  

<a name="CreatinganExpanderinXAML"></a>
## <a name="creating-a-simple-expander"></a>建立簡單的展開器  
 下面的示例演示如何創建簡單的<xref:System.Windows.Controls.Expander>控制項。 此示例創建一個<xref:System.Windows.Controls.Expander>類似于上一個插圖的圖。  
  
 [!code-xaml[ExpanderExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderExample/CSharp/Page1.xaml#2)]  
  
 的<xref:System.Windows.Controls.ContentControl.Content%2A><xref:System.Windows.Controls.HeaderedContentControl.Header%2A>和<xref:System.Windows.Controls.Expander>也可以包含複雜的內容，如<xref:System.Windows.Controls.RadioButton>和<xref:System.Windows.Controls.Image>物件。  
  
<a name="SettingtheDirectionoftheExpandingWindow"></a>
## <a name="setting-the-direction-of-the-expanding-content-area"></a>設定展開內容區域的方向  
 可以使用 屬性將<xref:System.Windows.Controls.Expander>控制項的內容地區設定為以四個方向之一 （、<xref:System.Windows.Controls.ExpandDirection.Down> <xref:System.Windows.Controls.ExpandDirection.Up>、<xref:System.Windows.Controls.ExpandDirection.Left>或<xref:System.Windows.Controls.ExpandDirection.Right>） 展開。 <xref:System.Windows.Controls.ExpandDirection> 當內容區域折疊時，僅顯示<xref:System.Windows.Controls.Expander><xref:System.Windows.Controls.HeaderedContentControl.Header%2A>及其切換按鈕。 顯示<xref:System.Windows.Controls.Button>方向箭頭的控制項用作切換按鈕，用於展開或折疊內容區域。 展開時，<xref:System.Windows.Controls.Expander>將嘗試在類似視窗的區域中顯示其所有內容。  
  
<a name="SettingSizeDimensionsonanExpanderinaPanel"></a>
## <a name="controlling-the-size-of-an-expander-in-a-panel"></a>控制面板中展開器的大小  
 如果<xref:System.Windows.Controls.Expander><xref:System.Windows.Controls.Panel>控制項位於繼承于 （如<xref:System.Windows.Controls.StackPanel>） 的佈局控制項內，則在 屬性<xref:System.Windows.FrameworkElement.Height%2A>設置為<xref:System.Windows.Controls.Expander><xref:System.Windows.Controls.ExpandDirection.Down>或<xref:System.Windows.Controls.ExpandDirection.Up><xref:System.Windows.Controls.Expander.ExpandDirection%2A>時，不要在 上指定 。 同樣，在<xref:System.Windows.FrameworkElement.Width%2A><xref:System.Windows.Controls.Expander><xref:System.Windows.Controls.Expander.ExpandDirection%2A>將屬性設置為<xref:System.Windows.Controls.ExpandDirection.Left>或<xref:System.Windows.Controls.ExpandDirection.Right>時，不要在 上指定 。  
  
 在<xref:System.Windows.Controls.Expander>控制項上按展開內容的顯示方向設置大小尺寸時，<xref:System.Windows.Controls.Expander>將控制內容使用的區域並在其周圍顯示邊框。 該框線即使在內容摺疊時也會顯示。 要設置展開內容區域的大小，請設置 在 的內容上<xref:System.Windows.Controls.Expander>的大小尺寸，或者如果希望滾動功能，請設置<xref:System.Windows.Controls.ScrollViewer>包含內容的內容的大小尺寸。  
  
 <xref:System.Windows.Controls.Expander>當控制項是 中的最後一個<xref:System.Windows.Controls.DockPanel>元素時[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]，將自動將<xref:System.Windows.Controls.Expander>維度設置為等於 的<xref:System.Windows.Controls.DockPanel>其餘區域。 要<xref:System.Windows.Controls.DockPanel.LastChildFill%2A>防止此預設行為，將<xref:System.Windows.Controls.DockPanel>物件上的屬性設置為`false`， 或確保<xref:System.Windows.Controls.Expander>不是 中的最後一個<xref:System.Windows.Controls.DockPanel>元素。  
  
<a name="CreatingScrollableContent"></a>
## <a name="creating-scrollable-content"></a>建立可捲動的內容  
 如果內容太大，無法減小內容區域的大小，則可以將 的內容包裝<xref:System.Windows.Controls.Expander>在 中<xref:System.Windows.Controls.ScrollViewer>，以便提供可滾動的內容。 該<xref:System.Windows.Controls.Expander>控制項不會自動提供滾動功能。 下圖顯示了包含控制項的<xref:System.Windows.Controls.Expander><xref:System.Windows.Controls.ScrollViewer>控制項。  
  
 **ScrollViewer 中的展開器**  
  
 ![顯示帶有捲軸的擴展器的螢幕截圖。](./media/expander-overview/expander-scrollbar-control.jpg)  
  
 <xref:System.Windows.Controls.Expander>將控制項<xref:System.Windows.Controls.ScrollViewer>放置在 中 時，設置與<xref:System.Windows.Controls.ScrollViewer><xref:System.Windows.Controls.Expander>內容打開的方向對應<xref:System.Windows.Controls.Expander>內容區域大小的維度屬性。 例如，如果將<xref:System.Windows.Controls.Expander.ExpandDirection%2A>屬性設置為<xref:System.Windows.Controls.Expander> <xref:System.Windows.Controls.ExpandDirection.Down> <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Controls.ScrollViewer> 如果改為在內容本身上設置高度維度，<xref:System.Windows.Controls.ScrollViewer>則無法識別此設置，因此不提供可滾動的內容。  
  
 下面的示例演示如何創建<xref:System.Windows.Controls.Expander>包含複雜內容且包含<xref:System.Windows.Controls.ScrollViewer>控制項的控制項。 此示例創建類似于<xref:System.Windows.Controls.Expander>本節開頭的插圖的 。  
  
 [!code-csharp[ExpanderRichContent#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ExpanderRichContent#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpanderRichContent/VisualBasic/Window1.xaml.vb#1)]
 [!code-xaml[ExpanderRichContent#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#1)]  
  
<a name="UsingtheAlignmentProperties"></a>
## <a name="using-the-alignment-properties"></a>使用對齊屬性  
 您可以通過在控制項上設置 和<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A><xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>屬性來<xref:System.Windows.Controls.Expander>對齊內容。 當您設定這些屬性時，對齊方式會套用到標頭，也會套用到所展開的內容。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.Expander>
- <xref:System.Windows.Controls.ExpandDirection>
- [如何使用主題](expander-how-to-topics.md)
