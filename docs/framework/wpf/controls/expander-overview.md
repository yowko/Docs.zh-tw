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
ms.openlocfilehash: ddf6ee550e0eb6af5af44d032e85ecd5b735b951
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130399"
---
# <a name="expander-overview"></a>Expander 概觀
<xref:System.Windows.Controls.Expander>控制項提供一個可展開區域類似於視窗並且包含標頭中提供內容的方式。  

<a name="CreatinganExpanderinXAML"></a>   
## <a name="creating-a-simple-expander"></a>建立簡單的展開器  
 下列範例示範如何建立簡單<xref:System.Windows.Controls.Expander>控制項。 這個範例會建立<xref:System.Windows.Controls.Expander>看起來像上圖。  
  
 [!code-xaml[ExpanderExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderExample/CSharp/Page1.xaml#2)]  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A>並<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>的<xref:System.Windows.Controls.Expander>可以也包含複雜內容，例如<xref:System.Windows.Controls.RadioButton>和<xref:System.Windows.Controls.Image>物件。  
  
<a name="SettingtheDirectionoftheExpandingWindow"></a>   
## <a name="setting-the-direction-of-the-expanding-content-area"></a>設定展開內容區域的方向  
 您可以設定的內容區域<xref:System.Windows.Controls.Expander>展開其中一個四個方向的控制項 (<xref:System.Windows.Controls.ExpandDirection.Down>， <xref:System.Windows.Controls.ExpandDirection.Up>， <xref:System.Windows.Controls.ExpandDirection.Left>，或<xref:System.Windows.Controls.ExpandDirection.Right>) 使用<xref:System.Windows.Controls.ExpandDirection>屬性。 當內容區域摺疊，只<xref:System.Windows.Controls.Expander><xref:System.Windows.Controls.HeaderedContentControl.Header%2A>和它的切換按鈕出現。 A<xref:System.Windows.Controls.Button>控制項顯示的方向性箭號來作為切換按鈕展開或摺疊內容區域。 展開時會<xref:System.Windows.Controls.Expander>嘗試在類似視窗的區域中顯示其所有內容。  
  
<a name="SettingSizeDimensionsonanExpanderinaPanel"></a>   
## <a name="controlling-the-size-of-an-expander-in-a-panel"></a>控制面板中展開器的大小  
 如果<xref:System.Windows.Controls.Expander>控制項是繼承自的版面配置控制項內<xref:System.Windows.Controls.Panel>，例如<xref:System.Windows.Controls.StackPanel>，沒有指定<xref:System.Windows.FrameworkElement.Height%2A>上<xref:System.Windows.Controls.Expander>當<xref:System.Windows.Controls.Expander.ExpandDirection%2A>屬性設定為<xref:System.Windows.Controls.ExpandDirection.Down>或<xref:System.Windows.Controls.ExpandDirection.Up>。 同樣地，未指定<xref:System.Windows.FrameworkElement.Width%2A>上<xref:System.Windows.Controls.Expander>當<xref:System.Windows.Controls.Expander.ExpandDirection%2A>屬性設定為<xref:System.Windows.Controls.ExpandDirection.Left>或<xref:System.Windows.Controls.ExpandDirection.Right>。  
  
 當您在上設定大小維度時<xref:System.Windows.Controls.Expander>控制項的方向，則會顯示展開的內容，<xref:System.Windows.Controls.Expander>接管由內容，並顯示其周圍的框線的區域。 該框線即使在內容摺疊時也會顯示。 若要設定所展開內容區域的大小，請設定大小維度上的內容<xref:System.Windows.Controls.Expander>，或如果您想要在捲動功能，<xref:System.Windows.Controls.ScrollViewer>包含內容。  
  
 當<xref:System.Windows.Controls.Expander>控制項是中的最後一個項目<xref:System.Windows.Controls.DockPanel>，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]會自動設定<xref:System.Windows.Controls.Expander>等於的剩餘區域的維度<xref:System.Windows.Controls.DockPanel>。 若要防止這個預設行為，將<xref:System.Windows.Controls.DockPanel.LastChildFill%2A>上的屬性<xref:System.Windows.Controls.DockPanel>物件`false`，或請確定<xref:System.Windows.Controls.Expander>不是中的最後一個項目<xref:System.Windows.Controls.DockPanel>。  
  
<a name="CreatingScrollableContent"></a>   
## <a name="creating-scrollable-content"></a>建立可捲動的內容  
 如果內容對內容區域的大小而言太大，您可以將包裝的內容<xref:System.Windows.Controls.Expander>在<xref:System.Windows.Controls.ScrollViewer>以提供可捲動的內容。 <xref:System.Windows.Controls.Expander>控制項不會自動提供捲動功能。 如下圖所示<xref:System.Windows.Controls.Expander>控制項，其中包含<xref:System.Windows.Controls.ScrollViewer>控制項。  
  
 **ScrollViewer 中的展開器**  
  
 ![如果螢幕擷取畫面顯示具有 ScrollBar 的 expander。](./media/expander-overview/expander-scrollbar-control.jpg)  
  
 當您將<xref:System.Windows.Controls.Expander>在中控制可<xref:System.Windows.Controls.ScrollViewer>，將<xref:System.Windows.Controls.ScrollViewer>維度屬性對應至的方向<xref:System.Windows.Controls.Expander>內容的大小將會開啟<xref:System.Windows.Controls.Expander>內容區域。 比方說，如果您設定<xref:System.Windows.Controls.Expander.ExpandDirection%2A>上的屬性<xref:System.Windows.Controls.Expander>要<xref:System.Windows.Controls.ExpandDirection.Down>（內容區域向下開啟），設定<xref:System.Windows.FrameworkElement.Height%2A>屬性<xref:System.Windows.Controls.ScrollViewer>控制項內容區域所需的高度。 如果您在內容本身，改為設定高度維度<xref:System.Windows.Controls.ScrollViewer>無法辨識此設定，因此，無法提供可捲動的內容。  
  
 下列範例示範如何建立<xref:System.Windows.Controls.Expander>控制項具有複雜內容，且其中包含<xref:System.Windows.Controls.ScrollViewer>控制項。 這個範例會建立<xref:System.Windows.Controls.Expander>，就像是本節開頭圖例。  
  
 [!code-csharp[ExpanderRichContent#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ExpanderRichContent#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpanderRichContent/VisualBasic/Window1.xaml.vb#1)]
 [!code-xaml[ExpanderRichContent#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#1)]  
  
<a name="UsingtheAlignmentProperties"></a>   
## <a name="using-the-alignment-properties"></a>使用對齊屬性  
 您可以藉由設定對齊內容<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>並<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>上的屬性<xref:System.Windows.Controls.Expander>控制項。 當您設定這些屬性時，對齊方式會套用到標頭，也會套用到所展開的內容。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.Expander>
- <xref:System.Windows.Controls.ExpandDirection>
- [HOW TO 主題](expander-how-to-topics.md)
