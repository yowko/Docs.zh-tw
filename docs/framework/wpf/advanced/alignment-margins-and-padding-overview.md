---
title: 對齊、邊界和填補概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- margins [WPF]
- padding [WPF]
- aligning [WPF]
ms.assetid: 9c6a2009-9b86-4e40-8605-0a2664dc3973
ms.openlocfilehash: bf351b6df972dc992f214ddfe899bfa808d0cd53
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963641"
---
# <a name="alignment-margins-and-padding-overview"></a>對齊、邊界和填補概觀
<xref:System.Windows.FrameworkElement>類別會公開數個用來精確定位子項目的屬性。 本主題討論四個最重要的屬性: <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、 <xref:System.Windows.FrameworkElement.Margin%2A>、 <xref:System.Windows.Controls.Border.Padding%2A>和<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>。 一定要了解這些屬性的作用，因為它們提供控制 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式中項目位置的基礎。  

<a name="wcpsdk_layout_amp_introduction"></a>   
## <a name="introduction-to-element-positioning"></a>項目定位簡介  
 有許多種方式可以使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 定位項目。 不過, 達到理想的版面配置不僅僅是選擇正確<xref:System.Windows.Controls.Panel>的元素。 您必須<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>先瞭解、、 <xref:System.Windows.Controls.Border.Padding%2A>和<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>屬性, <xref:System.Windows.FrameworkElement.Margin%2A>才能精確控制定位。  
  
 下圖顯示利用數個定位屬性的版面配置情節。  
  
 ![WPF 定位屬性範例](./media/layout-margins-padding-alignment-graphic1.PNG "layout_margins_padding_alignment_graphic1")  
  
 乍看之下, 此圖<xref:System.Windows.Controls.Button>中的元素可能會以隨機方式放置。 不過，實際上使用了邊界、對齊和邊框間距的組合精確地控制它們的位置。  
  
 下列範例說明如何建立上圖中的版面配置。 元素會封裝父系<xref:System.Windows.Controls.StackPanel>, 其<xref:System.Windows.Controls.Border.Padding%2A>值為15個與裝置無關的圖元。 <xref:System.Windows.Controls.Border> 此帳戶適用于括<xref:System.Windows.Media.Brushes.LightBlue%2A>住子<xref:System.Windows.Controls.StackPanel>系的窄寬線。 的子項目<xref:System.Windows.Controls.StackPanel>是用來說明本主題中詳述的各種位置屬性。 有<xref:System.Windows.Controls.Button>三個元素用來示範<xref:System.Windows.FrameworkElement.Margin%2A>和<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性。  
  
 [!code-csharp[MPALayoutSampleIntro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 下圖提供上述範例中使用之各種定位屬性的特寫檢視。 本主題中的後續各節會更詳細說明如何使用每個定位屬性。  
  
 ![定位屬性與畫面圖說](./media/layout-margins-padding-alignment-graphic2.PNG "layout_margins_padding_alignment_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>   
## <a name="understanding-alignment-properties"></a>了解對齊屬性  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 和<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>屬性會描述子專案應如何放在父項目的已配置版面配置空間內。 藉由一起使用這些屬性，您可以精確定位子項目。 <xref:System.Windows.Controls.DockPanel>例如, 的子專案可以指定四種不同的水準對齊方式<xref:System.Windows.HorizontalAlignment.Left>: <xref:System.Windows.HorizontalAlignment.Right>、或<xref:System.Windows.HorizontalAlignment.Center>, 或<xref:System.Windows.HorizontalAlignment.Stretch>以填滿可用空間。 類似的值可供垂直定位之用。  
  
> [!NOTE]
> 明確設定<xref:System.Windows.FrameworkElement.Height%2A>專案上<xref:System.Windows.FrameworkElement.Width%2A>的和屬性會優先于<xref:System.Windows.HorizontalAlignment.Stretch>屬性值。 嘗試設定<xref:System.Windows.FrameworkElement.Height%2A>、和<xref:System.Windows.FrameworkElement.Width%2A> `Stretch`的值, 會導致忽略要求。 `Stretch` <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>   
### <a name="horizontalalignment-property"></a>HorizontalAlignment 屬性  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性會宣告要套用至子專案的水準對齊特性。 下表顯示<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性的每個可能值。  
  
|成員|描述|  
|------------|-----------------|  
|<xref:System.Windows.HorizontalAlignment.Left>|子項目對齊父項目的已配置版面配置空間的左側。|  
|<xref:System.Windows.HorizontalAlignment.Center>|子項目對齊父項目的已配置版面配置空間的中間。|  
|<xref:System.Windows.HorizontalAlignment.Right>|子項目對齊父項目的已配置版面配置空間的右側。|  
|<xref:System.Windows.HorizontalAlignment.Stretch>預設|子項目會自動縮放以填滿父項目的已配置版面配置空間。 明確<xref:System.Windows.FrameworkElement.Width%2A> 和<xref:System.Windows.FrameworkElement.Height%2A>值的優先順序較高。|  
  
 下列範例顯示如何將<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性套用至<xref:System.Windows.Controls.Button>專案。 為了更清楚說明各種不同的轉譯行為，會顯示每個屬性值。  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 上述程式碼會產生類似下圖的版面配置。 每個<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>值的定位效果都會顯示在圖例中。  
  
 ![HorizontalAlignment 範例](./media/layout-horizontal-alignment-graphic.PNG "layout_horizontal_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>   
### <a name="verticalalignment-property"></a>VerticalAlignment 屬性  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>屬性會描述要套用至子項目的垂直對齊特性。 下表顯示<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>屬性的每個可能值。  
  
|成員|描述|  
|------------|-----------------|  
|<xref:System.Windows.VerticalAlignment.Top>|子項目對齊父項目的已配置版面配置空間的頂端。|  
|<xref:System.Windows.VerticalAlignment.Center>|子項目對齊父項目的已配置版面配置空間的中間。|  
|<xref:System.Windows.VerticalAlignment.Bottom>|子項目對齊父項目的已配置版面配置空間的底部。|  
|<xref:System.Windows.VerticalAlignment.Stretch>預設|子項目會自動縮放以填滿父項目的已配置版面配置空間。 明確<xref:System.Windows.FrameworkElement.Width%2A> 和<xref:System.Windows.FrameworkElement.Height%2A>值的優先順序較高。|  
  
 下列範例顯示如何將<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>屬性套用至<xref:System.Windows.Controls.Button>專案。 為了更清楚說明各種不同的轉譯行為，會顯示每個屬性值。 基於此範例的目的, <xref:System.Windows.Controls.Grid>具有可見格線的元素會當做父系使用, 以更清楚地說明每個屬性值的配置行為。  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xaml[MPALayoutVerticalAlignment#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 上述程式碼會產生類似下圖的版面配置。 每個<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>值的定位效果都會顯示在圖例中。  
  
 ![VerticalAlignment 屬性範例](./media/layout-vertical-alignment-graphic.PNG "layout_vertical_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>   
## <a name="understanding-margin-properties"></a>了解邊界屬性  
 <xref:System.Windows.FrameworkElement.Margin%2A>屬性會描述元素及其子系或對等之間的距離。 <xref:System.Windows.FrameworkElement.Margin%2A>值可以是統一的, 方法是使用`Margin="20"`類似的語法。 使用此語法時, 會<xref:System.Windows.FrameworkElement.Margin%2A>將20個裝置獨立圖元的統一套用至元素。 <xref:System.Windows.FrameworkElement.Margin%2A>值也可以採用四個相異值的形式, 每個值都會描述不同的邊界, 以套用至左側、頂端、右側和底部 (依該順序), `Margin="0,10,5,25"`例如。 適當地使用<xref:System.Windows.FrameworkElement.Margin%2A>屬性, 可讓您非常精確地控制元素的轉譯位置, 以及其鄰近專案和子系的呈現位置。  
  
> [!NOTE]
> 非零的邊界會在專案的<xref:System.Windows.FrameworkElement.ActualWidth%2A>和<xref:System.Windows.FrameworkElement.ActualHeight%2A>之外套用空間。  
  
 下列範例顯示如何在專案群組<xref:System.Windows.Controls.Button>周圍套用統一邊界。 <xref:System.Windows.Controls.Button>元素會以每個方向的十圖元邊界緩衝區平均隔開。  
  
 [!code-cpp[MarginPaddingAlignmentSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#1)]
 [!code-csharp[MarginPaddingAlignmentSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#1)]
 [!code-vb[MarginPaddingAlignmentSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#1)]
 [!code-xaml[MarginPaddingAlignmentSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#1)]  
  
 在許多情況下，不適合統一的邊界。 在這些情況下，可以套用非統一的間距。 下列範例示範如何將非統一邊界間距套用至子項目。 邊界以下列順序描述︰左側、頂端、右側、底部。  
  
 [!code-cpp[MarginPaddingAlignmentSample#2](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#2)]
 [!code-csharp[MarginPaddingAlignmentSample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#2)]
 [!code-vb[MarginPaddingAlignmentSample#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#2)]
 [!code-xaml[MarginPaddingAlignmentSample#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#2)]  
  
<a name="wcpsdk_layout_amp_padding_properties"></a>   
## <a name="understanding-the-padding-property"></a>了解邊框間距屬性  
 填補<xref:System.Windows.FrameworkElement.Margin%2A>在大部分方面都很類似。 填補屬性只會在少數類別上公開, 主要是為了方便<xref:System.Windows.Documents.Block>:、 <xref:System.Windows.Controls.Border>、 <xref:System.Windows.Controls.Control>和<xref:System.Windows.Controls.TextBlock>是公開填補屬性之類別的範例。 屬性會以指定<xref:System.Windows.Thickness>的值來放大子項目的有效大小。 <xref:System.Windows.Controls.Border.Padding%2A>  
  
 下列範例顯示如何將<xref:System.Windows.Controls.Border.Padding%2A>套用至父<xref:System.Windows.Controls.Border>元素。  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xaml[MarginPaddingAlignmentSample#3](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>   
## <a name="using-alignment-margins-and-padding-in-an-application"></a>在應用程式使用對齊、邊界和邊框間距  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、 <xref:System.Windows.FrameworkElement.Margin%2A>、 <xref:System.Windows.Controls.Border.Padding%2A>和[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]提供建立複雜的必要位置控制項。 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 您可以使用每個屬性的效果來變更子項目定位，這樣可以在建立動態應用程式和使用者體驗時具有彈性。  
  
 下列範例示範本主題所述的每個概念。 根據在本主題第一個範例中找到的基礎結構來建立, 此範例<xref:System.Windows.Controls.Grid>會在第一個範例中<xref:System.Windows.Controls.Border>加入一個專案做為的子系。 <xref:System.Windows.Controls.Border.Padding%2A>會套用至父<xref:System.Windows.Controls.Border>元素。 是<xref:System.Windows.Controls.Grid>用來分割三個子<xref:System.Windows.Controls.StackPanel>元素之間的空間。 <xref:System.Windows.Controls.Button>元素會再次用來顯示<xref:System.Windows.FrameworkElement.Margin%2A>和<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>的各種效果。 <xref:System.Windows.Controls.TextBlock>專案會加入至每<xref:System.Windows.Controls.ColumnDefinition>個專案, 以進一步定義套用<xref:System.Windows.Controls.Button>至每個資料行中專案的各種屬性。  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xaml[MarginPaddingAlignmentSample#4](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 上述的應用程式在編譯時，會產生類似下圖的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 各種屬性值的效果會明顯出現在專案之間的間距, 而且每個資料行中專案的重要屬性值會顯示<xref:System.Windows.Controls.TextBlock>在專案中。  
  
 ![數個定位屬性都在同一個應用程式中](./media/layout-margins-padding-aligment-graphic3.PNG "layout_margins_padding_aligment_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>   
## <a name="whats-next"></a>後續步驟  
 定位類別所<xref:System.Windows.FrameworkElement>定義的屬性, 可讓您對應用程式[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內的專案位置進行精細的控制。 現在您有數種技巧可使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 進一步使用位置項目。  
  
 有更詳細說明 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 版面配置的其他資源可供使用。 [面板總覽](../controls/panels-overview.md)主題包含各種<xref:System.Windows.Controls.Panel>元素的詳細資料。 本主題[逐步解說:我的第一個 WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)桌面應用程式引進了使用版面設定項目來放置元件, 並將其動作系結至資料來源的先進技術。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- <xref:System.Windows.FrameworkElement.Margin%2A>
- [面板概觀](../controls/panels-overview.md)
- [版面配置](layout.md)
- [WPF 版面配置庫範例](https://go.microsoft.com/fwlink/?LinkID=160054)
