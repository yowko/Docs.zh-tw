---
title: "對齊、邊界和填補概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "對齊"
  - "類別, FrameworkElement"
  - "FrameworkElement 類別"
  - "邊界"
  - "填補"
ms.assetid: 9c6a2009-9b86-4e40-8605-0a2664dc3973
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 對齊、邊界和填補概觀
<xref:System.Windows.FrameworkElement> 類別會公開數個可用來精確定位子項目的屬性。  本主題將討論四個最重要的屬性：<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、<xref:System.Windows.FrameworkElement.Margin%2A>、<xref:System.Windows.Controls.Border.Padding%2A> 和 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>。  請務必了解這些屬性的作用，因為它們是控制 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式中之項目位置的基礎。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="wcpsdk_layout_amp_introduction"></a>   
## 項目定位簡介  
 使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 定位項目的方式有很多種。  不過，若要達成理想的版面配置，只選擇正確的 <xref:System.Windows.Controls.Panel> 項目還不夠。  若要精細控制定位，就必須了解 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、<xref:System.Windows.FrameworkElement.Margin%2A>、<xref:System.Windows.Controls.Border.Padding%2A> 和 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 屬性。  
  
 下圖顯示使用數個定位屬性的版面配置案例。  
  
 ![WPF 定位屬性範例](../../../../docs/framework/wpf/advanced/media/layout-margins-padding-alignment-graphic1.png "layout\_margins\_padding\_alignment\_graphic1")  
  
 乍看之下，上圖中的 <xref:System.Windows.Controls.Button> 項目像是隨機放置的。  不過，這些項目的位置其實是搭配使用邊界、對齊和填補等方式精確控制的。  
  
 下列範例將說明如何建立上圖的版面配置。  <xref:System.Windows.Controls.Border> 項目封裝了一個父 <xref:System.Windows.Controls.StackPanel>，並將 <xref:System.Windows.Controls.Border.Padding%2A> 值設為 15 個[與裝置無關的像素](GTMT)。  這就是框住子 <xref:System.Windows.Controls.StackPanel> 的 <xref:System.Windows.Media.Brushes.LightBlue%2A> 細邊。  <xref:System.Windows.Controls.StackPanel> 的子項目是用來示範本主題所詳述的每一個定位屬性。  三個 <xref:System.Windows.Controls.Button> 項目是用來示範 <xref:System.Windows.FrameworkElement.Margin%2A> 和 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 屬性。  
  
 [!code-csharp[MPALayoutSampleIntro#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 下圖更進一步顯示上述範例所用的各種定位屬性。  本主題後面的章節將詳述如何使用每個定位屬性。  
  
 ![具有畫面圖說文字的定位屬性](../../../../docs/framework/wpf/advanced/media/layout-margins-padding-alignment-graphic2.png "layout\_margins\_padding\_alignment\_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>   
## 了解對齊屬性  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 和 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 屬性會描述子項目如何在父項目的配置版面空間內定位。  藉由一起使用這兩個屬性，您可以精確定位子項目。  例如，<xref:System.Windows.Controls.DockPanel> 的子項目可以指定四種不同的水平對齊方式：<xref:System.Windows.HorizontalAlignment>、<xref:System.Windows.HorizontalAlignment>、<xref:System.Windows.HorizontalAlignment>、<xref:System.Windows.HorizontalAlignment> 來填滿可用的空間。  垂直定位也有類似的值。  
  
> [!NOTE]
>  在項目上明確設定的 <xref:System.Windows.FrameworkElement.Height%2A> 和 <xref:System.Windows.FrameworkElement.Width%2A> 屬性會比 <xref:System.Windows.HorizontalAlignment> 屬性值優先考慮。  嘗試設定 `Stretch` 的 <xref:System.Windows.FrameworkElement.Height%2A>、<xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 值，會導致 `Stretch` 要求被忽略。  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>   
### HorizontalAlignment 屬性  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 屬性會宣告套用到子項目的水平對齊特性。  下表顯示每個可能的 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 屬性值。  
  
|成員|描述|  
|--------|--------|  
|<xref:System.Windows.HorizontalAlignment>|子項目對齊至父項目配置版面空間的左邊。|  
|<xref:System.Windows.HorizontalAlignment>|子項目對齊至父項目配置版面空間的中央。|  
|<xref:System.Windows.HorizontalAlignment>|子項目對齊至父項目配置版面空間的右邊。|  
|<xref:System.Windows.HorizontalAlignment> \(預設\)|子項目延伸填滿父項目配置版面空間。  明確的 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 值優先適用。|  
  
 下列範例顯示如何將 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 屬性套用至 <xref:System.Windows.Controls.Button> 項目。  每個屬性值都會顯示出來，以更清楚示範各種呈現行為。  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 以上程式碼會產生類似下圖的版面配置。  圖中顯示了每個 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 值的定位效果。  
  
 ![HorizontalAlignment 範例](../../../../docs/framework/wpf/advanced/media/layout-horizontal-alignment-graphic.png "layout\_horizontal\_alignment\_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>   
### VerticalAlignment 屬性  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 屬性會描述套用到子項目的垂直對齊特性。  下表顯示每個可能的 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 屬性值。  
  
|成員|描述|  
|--------|--------|  
|<xref:System.Windows.VerticalAlignment>|子項目對齊至父項目配置版面空間的上方。|  
|<xref:System.Windows.VerticalAlignment>|子項目對齊至父項目配置版面空間的中央。|  
|<xref:System.Windows.VerticalAlignment>|子項目對齊至父項目配置版面空間的下方。|  
|<xref:System.Windows.VerticalAlignment> \(預設\)|子項目延伸填滿父項目配置版面空間。  明確的 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 值優先適用。|  
  
 下列範例顯示如何將 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 屬性套用至 <xref:System.Windows.Controls.Button> 項目。  每個屬性值都會顯示出來，以更清楚示範各種呈現行為。  為方便示範，此範例會使用 <xref:System.Windows.Controls.Grid> 項目加上可見的格線做為父項目，以更清楚顯示每個屬性值的配置行為。  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xml[MPALayoutVerticalAlignment#2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 以上程式碼會產生類似下圖的版面配置。  圖中顯示了每個 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 值的定位效果。  
  
 ![VerticalAlignment 屬性範例](../../../../docs/framework/wpf/advanced/media/layout-vertical-alignment-graphic.png "layout\_vertical\_alignment\_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>   
## 了解邊界屬性  
 <xref:System.Windows.FrameworkElement.Margin%2A> 屬性會說明項目與其子項或對等個體之間的距離。  <xref:System.Windows.FrameworkElement.Margin%2A> 值可以使用 `Margin="20"` 這類語法統一設定。  使用此語法時，會將統一的 <xref:System.Windows.FrameworkElement.Margin%2A> 值 20 個[與裝置無關的像素](GTMT)套用至項目。  <xref:System.Windows.FrameworkElement.Margin%2A> 值也可以採用四個不同值的格式，其中每個值分別描述套用到左、上、右和下 \(依順序\) 方的不同邊界，例如 `Margin="0,10,5,25"`。  正確使用 <xref:System.Windows.FrameworkElement.Margin%2A> 屬性可以精細控制項目的呈現位置和相鄰項目及子項的呈現位置。  
  
> [!NOTE]
>  非零的邊界會套用到項目的 <xref:System.Windows.FrameworkElement.ActualWidth%2A> 和 <xref:System.Windows.FrameworkElement.ActualHeight%2A> 以外的空間。  
  
 下列範例顯示如何在一組 <xref:System.Windows.Controls.Button> 項目的周圍套用均等邊界。  <xref:System.Windows.Controls.Button> 項目的間距均等，每個方向的邊界設為 10 個像素。  
  
 [!code-cpp[MarginPaddingAlignmentSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#1)]
 [!code-csharp[MarginPaddingAlignmentSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#1)]
 [!code-vb[MarginPaddingAlignmentSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#1)]
 [!code-xml[MarginPaddingAlignmentSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#1)]  
  
 在許多情況下，均等邊界並不適用。  在這些情況下，就需要套用非均等間距。  下列範例顯示如何將非均等邊界間距套用到子項目。  邊界會照左、上、右、下的順序描述。  
  
 [!code-cpp[MarginPaddingAlignmentSample#2](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#2)]
 [!code-csharp[MarginPaddingAlignmentSample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#2)]
 [!code-vb[MarginPaddingAlignmentSample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#2)]
 [!code-xml[MarginPaddingAlignmentSample#2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#2)]  
  
<a name="wcpsdk_layout_amp_padding_properties"></a>   
## 了解填補屬性  
 填補在很多方面都類似於 <xref:System.Windows.FrameworkElement.Margin%2A>。  Padding 屬性只會在幾個類別上公開，主要是為了方便使用：<xref:System.Windows.Documents.Block>、<xref:System.Windows.Controls.Border>、<xref:System.Windows.Controls.Control> 和 <xref:System.Windows.Controls.TextBlock> 是公開 Padding 屬性的類別範例。  <xref:System.Windows.Controls.Border.Padding%2A> 會藉由 <xref:System.Windows.Thickness> 的指定值，放大子項目的有效大小。  
  
 下列範例顯示如何將 <xref:System.Windows.Controls.Border.Padding%2A> 套用到父 <xref:System.Windows.Controls.Border> 項目。  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xml[MarginPaddingAlignmentSample#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>   
## 在應用程式中使用對齊、邊界和填補  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、<xref:System.Windows.FrameworkElement.Margin%2A>、<xref:System.Windows.Controls.Border.Padding%2A> 和 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 提供建立複雜[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 所需的定位控制項。  您可以利用每個屬性的作用來變更子項目的定位，以彈性地建立動態應用程式和創造使用者體驗。  
  
 下列範例示範本主題所述的每一個概念。  這個範例以本主題的第一個範例為基礎，另外加入了 <xref:System.Windows.Controls.Grid> 項目做為第一個範例中 <xref:System.Windows.Controls.Border> 的子項。  <xref:System.Windows.Controls.Border.Padding%2A> 會套用至父 <xref:System.Windows.Controls.Border> 項目。  <xref:System.Windows.Controls.Grid> 可用來分割三個子 <xref:System.Windows.Controls.StackPanel> 項目之間的空間。  <xref:System.Windows.Controls.Button> 項目會再次用來顯示 <xref:System.Windows.FrameworkElement.Margin%2A> 和 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 的各種效果。  <xref:System.Windows.Controls.TextBlock> 項目會加入到每個 <xref:System.Windows.Controls.ColumnDefinition>，以進一步定義套用到每個資料行中 <xref:System.Windows.Controls.Button> 項目的各種屬性。  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xml[MarginPaddingAlignmentSample#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 編譯之後，上面的應用程式會產生如下圖的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  您可以從項目之間的間距明顯看出各種屬性值的效果，而每個資料行中項目的有效屬性值則會在 <xref:System.Windows.Controls.TextBlock> 內顯示。  
  
 ![數個定位屬性都在同一個應用程式中](../../../../docs/framework/wpf/advanced/media/layout-margins-padding-aligment-graphic3.png "layout\_margins\_padding\_aligment\_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>   
## 下一步  
 <xref:System.Windows.FrameworkElement> 類別定義的定位屬性可精細控制 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式中的項目定位。  您現在已經學會使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 進一步控制項目定位的幾種方法。  
  
 此外也有其他更詳細說明 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 版面配置的資源。  [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)主題詳述各種 <xref:System.Windows.Controls.Panel> 項目。  [逐步解說：WPF 使用者入門](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)主題則介紹進階的方法，說明如何使用版面配置項目定位元件，並將其動作繫結至資料來源。  
  
## 請參閱  
 <xref:System.Windows.FrameworkElement>   
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>   
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>   
 <xref:System.Windows.FrameworkElement.Margin%2A>   
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [配置](../../../../docs/framework/wpf/advanced/layout.md)   
 [WPF 配置圖庫範例](http://go.microsoft.com/fwlink/?LinkID=160054)