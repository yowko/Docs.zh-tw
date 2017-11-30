---
title: "對齊、邊界和填補概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- margins [WPF]
- padding [WPF]
- aligning [WPF]
ms.assetid: 9c6a2009-9b86-4e40-8605-0a2664dc3973
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0c0a57018959aedc72e0fa02befa1733f66f265b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="alignment-margins-and-padding-overview"></a>對齊、邊界和填補概觀
<xref:System.Windows.FrameworkElement>類別會公開數個屬性，可用來明確地說放置子項目。 本主題討論四個最重要的屬性： <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>， <xref:System.Windows.FrameworkElement.Margin%2A>， <xref:System.Windows.Controls.Border.Padding%2A>，和<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>。 一定要了解這些屬性的作用，因為它們提供控制 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式中項目位置的基礎。  
  
  
<a name="wcpsdk_layout_amp_introduction"></a>   
## <a name="introduction-to-element-positioning"></a>項目定位簡介  
 有許多種方式可以使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 定位項目。 不過，達到理想的配置超過只需選擇正確的<xref:System.Windows.Controls.Panel>項目。 微調控制位置必須先了解<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>， <xref:System.Windows.FrameworkElement.Margin%2A>， <xref:System.Windows.Controls.Border.Padding%2A>，和<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>屬性。  
  
 下圖顯示利用數個定位屬性的版面配置情節。  
  
 ![WPF 定位屬性範例](../../../../docs/framework/wpf/advanced/media/layout-margins-padding-alignment-graphic1.PNG "layout_margins_padding_alignment_graphic1")  
  
 第一眼<xref:System.Windows.Controls.Button>隨機放置可能會出現在此圖中的項目。 不過，實際上使用了邊界、對齊和邊框間距的組合精確地控制它們的位置。  
  
 下列範例說明如何建立上圖中的版面配置。 A<xref:System.Windows.Controls.Border>項目封裝的父代<xref:System.Windows.Controls.StackPanel>，與<xref:System.Windows.Controls.Border.Padding%2A>15 與裝置無關的像素的值。 這會負責窄<xref:System.Windows.Media.Brushes.LightBlue%2A>圍繞在子系的頻外<xref:System.Windows.Controls.StackPanel>。 子項目的<xref:System.Windows.Controls.StackPanel>用來說明每個本主題中詳述的各種定位屬性。 三個<xref:System.Windows.Controls.Button>元素用來示範同時<xref:System.Windows.FrameworkElement.Margin%2A>和<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性。  
  
 [!code-csharp[MPALayoutSampleIntro#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 下圖提供上述範例中使用之各種定位屬性的特寫檢視。 本主題中的後續各節會更詳細說明如何使用每個定位屬性。  
  
 ![定位屬性與畫面圖說](../../../../docs/framework/wpf/advanced/media/layout-margins-padding-alignment-graphic2.PNG "layout_margins_padding_alignment_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>   
## <a name="understanding-alignment-properties"></a>了解對齊屬性  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>和<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>屬性會描述如何應該放置子項目的父項目的配置空間內。 藉由一起使用這些屬性，您可以精確定位子項目。 例如，子項目的<xref:System.Windows.Controls.DockPanel>可以指定四個不同的水平對齊方式： <xref:System.Windows.HorizontalAlignment.Left>， <xref:System.Windows.HorizontalAlignment.Right>，或<xref:System.Windows.HorizontalAlignment.Center>，或<xref:System.Windows.HorizontalAlignment.Stretch>以填滿可用空間。 類似的值可供垂直定位之用。  
  
> [!NOTE]
>  明確地設定<xref:System.Windows.FrameworkElement.Height%2A>和<xref:System.Windows.FrameworkElement.Width%2A>項目上的屬性會優先於<xref:System.Windows.HorizontalAlignment.Stretch>屬性值。 嘗試設定<xref:System.Windows.FrameworkElement.Height%2A>， <xref:System.Windows.FrameworkElement.Width%2A>，和<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>值`Stretch`導致`Stretch`要求被忽略。  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>   
### <a name="horizontalalignment-property"></a>HorizontalAlignment 屬性  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性會宣告要套用至項目子系的水平對齊特性。 下表顯示每個可能的值<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性。  
  
|成員|說明|  
|------------|-----------------|  
|<xref:System.Windows.HorizontalAlignment.Left>|子項目對齊父項目的已配置版面配置空間的左側。|  
|<xref:System.Windows.HorizontalAlignment.Center>|子項目對齊父項目的已配置版面配置空間的中間。|  
|<xref:System.Windows.HorizontalAlignment.Right>|子項目對齊父項目的已配置版面配置空間的右側。|  
|<xref:System.Windows.HorizontalAlignment.Stretch>（預設值）|子項目會自動縮放以填滿父項目的已配置版面配置空間。 明確<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>值優先。|  
  
 下列範例示範如何套用<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性<xref:System.Windows.Controls.Button>項目。 為了更清楚說明各種不同的轉譯行為，會顯示每個屬性值。  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 上述程式碼會產生類似下圖的版面配置。 每個定位效果<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>值會顯示在圖例中。  
  
 ![HorizontalAlignment 範例](../../../../docs/framework/wpf/advanced/media/layout-horizontal-alignment-graphic.PNG "layout_horizontal_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>   
### <a name="verticalalignment-property"></a>VerticalAlignment 屬性  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>屬性會描述要套用至子元素的垂直對齊特性。 下表顯示每個可能的值為<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>屬性。  
  
|成員|說明|  
|------------|-----------------|  
|<xref:System.Windows.VerticalAlignment.Top>|子項目對齊父項目的已配置版面配置空間的頂端。|  
|<xref:System.Windows.VerticalAlignment.Center>|子項目對齊父項目的已配置版面配置空間的中間。|  
|<xref:System.Windows.VerticalAlignment.Bottom>|子項目對齊父項目的已配置版面配置空間的底部。|  
|<xref:System.Windows.VerticalAlignment.Stretch>（預設值）|子項目會自動縮放以填滿父項目的已配置版面配置空間。 明確<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>值優先。|  
  
 下列範例示範如何套用<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>屬性<xref:System.Windows.Controls.Button>項目。 為了更清楚說明各種不同的轉譯行為，會顯示每個屬性值。 此範例中，以利<xref:System.Windows.Controls.Grid>可見格線項目做為父代，更清楚說明每個屬性值的配置行為。  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xaml[MPALayoutVerticalAlignment#2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 上述程式碼會產生類似下圖的版面配置。 每個定位效果<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>值會顯示在圖例中。  
  
 ![VerticalAlignment 屬性範例](../../../../docs/framework/wpf/advanced/media/layout-vertical-alignment-graphic.PNG "layout_vertical_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>   
## <a name="understanding-margin-properties"></a>了解邊界屬性  
 <xref:System.Windows.FrameworkElement.Margin%2A>屬性描述項目及其子系或對等之間的距離。 <xref:System.Windows.FrameworkElement.Margin%2A>值可以使用類似下面的語法統一， `Margin="20"`。 使用此語法，統一<xref:System.Windows.FrameworkElement.Margin%2A>的 20 裝置無關的像素會套用至項目。 <xref:System.Windows.FrameworkElement.Margin%2A>值也可以採用四個相異值的形式每個值，描述要套用到左側、 頂端、 右側和下方 （依該順序），相異邊界像`Margin="0,10,5,25"`。 正確使用<xref:System.Windows.FrameworkElement.Margin%2A>屬性可讓其相鄰項目和子系呈現位置的項目呈現位置的非常精細的控制。  
  
> [!NOTE]
>  非零邊界適用於空間的項目之外<xref:System.Windows.FrameworkElement.ActualWidth%2A>和<xref:System.Windows.FrameworkElement.ActualHeight%2A>。  
  
 下列範例示範如何套用統一群組周圍的邊界<xref:System.Windows.Controls.Button>項目。 <xref:System.Windows.Controls.Button>項目會平均每個方向的十個像素邊界緩衝區。  
  
 [!code-cpp[MarginPaddingAlignmentSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#1)]
 [!code-csharp[MarginPaddingAlignmentSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#1)]
 [!code-vb[MarginPaddingAlignmentSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#1)]
 [!code-xaml[MarginPaddingAlignmentSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#1)]  
  
 在許多情況下，不適合統一的邊界。 在這些情況下，可以套用非統一的間距。 下列範例示範如何將非統一邊界間距套用至子項目。 邊界以下列順序描述︰左側、頂端、右側、底部。  
  
 [!code-cpp[MarginPaddingAlignmentSample#2](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#2)]
 [!code-csharp[MarginPaddingAlignmentSample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#2)]
 [!code-vb[MarginPaddingAlignmentSample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#2)]
 [!code-xaml[MarginPaddingAlignmentSample#2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#2)]  
  
<a name="wcpsdk_layout_amp_padding_properties"></a>   
## <a name="understanding-the-padding-property"></a>了解邊框間距屬性  
 填補會類似於<xref:System.Windows.FrameworkElement.Margin%2A>在大部分的方面。 Padding 屬性上公開只在幾個類別，主要是為了方便起見： <xref:System.Windows.Documents.Block>， <xref:System.Windows.Controls.Border>， <xref:System.Windows.Controls.Control>，和<xref:System.Windows.Controls.TextBlock>樣本數 Padding 屬性公開 （expose） 的類別。 <xref:System.Windows.Controls.Border.Padding%2A>屬性來指定放大子項目的大小<xref:System.Windows.Thickness>值。  
  
 下列範例示範如何套用<xref:System.Windows.Controls.Border.Padding%2A>至父代<xref:System.Windows.Controls.Border>項目。  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xaml[MarginPaddingAlignmentSample#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>   
## <a name="using-alignment-margins-and-padding-in-an-application"></a>在應用程式使用對齊、邊界和邊框間距  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A><xref:System.Windows.FrameworkElement.Margin%2A>， <xref:System.Windows.Controls.Border.Padding%2A>，和<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>提供定位控制項需要建立複雜[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]。 您可以使用每個屬性的效果來變更子項目定位，這樣可以在建立動態應用程式和使用者體驗時具有彈性。  
  
 下列範例示範本主題所述的每個概念。 本主題中的第一個範例中找到的基礎結構上建置，則這個範例會將<xref:System.Windows.Controls.Grid>做為子系的項目<xref:System.Windows.Controls.Border>中第一個範例。 <xref:System.Windows.Controls.Border.Padding%2A>套用至父<xref:System.Windows.Controls.Border>項目。 <xref:System.Windows.Controls.Grid>用來分割三個子系之間的空間<xref:System.Windows.Controls.StackPanel>項目。 <xref:System.Windows.Controls.Button>元素一次用來顯示不同效果<xref:System.Windows.FrameworkElement.Margin%2A>和<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>。 <xref:System.Windows.Controls.TextBlock>項目會加入至每個<xref:System.Windows.Controls.ColumnDefinition>更明確地定義套用到的各種屬性<xref:System.Windows.Controls.Button>每個資料行中的項目。  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xaml[MarginPaddingAlignmentSample#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 上述的應用程式在編譯時，會產生類似下圖的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 不同的屬性值的效果很容易看見的項目之間的間距和重要的屬性值的每個資料行中的項目內顯示<xref:System.Windows.Controls.TextBlock>項目。  
  
 ![數個定位屬性都在同一個應用程式中](../../../../docs/framework/wpf/advanced/media/layout-margins-padding-aligment-graphic3.PNG "layout_margins_padding_aligment_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>   
## <a name="whats-next"></a>後續步驟  
 位置所定義的內容<xref:System.Windows.FrameworkElement>類別啟用中的項目位置的良好控制[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。 現在您有數種技巧可使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 進一步使用位置項目。  
  
 有更詳細說明 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 版面配置的其他資源可供使用。 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)主題包含有關在各種詳細<xref:System.Windows.Controls.Panel>項目。 本主題[逐步解說： 第一個 WPF 桌面應用程式](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)導入了進階的技術，將元件，並將其動作繫結至資料來源使用版面配置項目。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>  
 <xref:System.Windows.FrameworkElement.Margin%2A>  
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [版面配置](../../../../docs/framework/wpf/advanced/layout.md)  
 [WPF 版面配置庫範例](http://go.microsoft.com/fwlink/?LinkID=160054)
