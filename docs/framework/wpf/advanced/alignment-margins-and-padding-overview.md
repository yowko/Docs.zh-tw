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
ms.openlocfilehash: bec2d9cd224febb650e2de67bb7406365d075963
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145471"
---
# <a name="alignment-margins-and-padding-overview"></a>對齊、邊界和填補概觀
類<xref:System.Windows.FrameworkElement>公開幾個用於精確定位子項目的屬性。 本主題<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>討論四個最重要的屬性： 、<xref:System.Windows.FrameworkElement.Margin%2A><xref:System.Windows.Controls.Border.Padding%2A>和<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>。 一定要了解這些屬性的作用，因為它們提供控制 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式中項目位置的基礎。  

<a name="wcpsdk_layout_amp_introduction"></a>
## <a name="introduction-to-element-positioning"></a>項目定位簡介  
 有許多種方式可以使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 定位項目。 但是，實現理想的佈局不僅僅是簡單地選擇正確的<xref:System.Windows.Controls.Panel>元素。 精細地控制定位需要瞭解<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、<xref:System.Windows.FrameworkElement.Margin%2A><xref:System.Windows.Controls.Border.Padding%2A>和<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>屬性。  
  
 下圖顯示利用數個定位屬性的版面配置情節。  
  
 ![WPF 定位屬性範例](./media/layout-margins-padding-alignment-graphic1.PNG "layout_margins_padding_alignment_graphic1")  
  
 乍一看，<xref:System.Windows.Controls.Button>此圖中的元素可能看起來是隨機放置的。 不過，實際上使用了邊界、對齊和邊框間距的組合精確地控制它們的位置。  
  
 下列範例說明如何建立上圖中的版面配置。 元素<xref:System.Windows.Controls.Border>封裝父<xref:System.Windows.Controls.StackPanel>級 ，<xref:System.Windows.Controls.Border.Padding%2A>值為 15 個與設備無關的圖元。 這說明了圍繞孩子<xref:System.Windows.Media.Brushes.LightBlue%2A><xref:System.Windows.Controls.StackPanel>周圍的狹窄帶。 子<xref:System.Windows.Controls.StackPanel>元素用於說明本主題中詳述的每個定位屬性。 三<xref:System.Windows.Controls.Button>個元素用於演示 和<xref:System.Windows.FrameworkElement.Margin%2A><xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性。  
  
 [!code-csharp[MPALayoutSampleIntro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 下圖提供上述範例中使用之各種定位屬性的特寫檢視。 本主題中的後續各節會更詳細說明如何使用每個定位屬性。  
  
 ![使用螢幕呼叫&#45;外定位屬性](./media/layout-margins-padding-alignment-graphic2.PNG "layout_margins_padding_alignment_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>
## <a name="understanding-alignment-properties"></a>了解對齊屬性  
 和<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A><xref:System.Windows.FrameworkElement.VerticalAlignment%2A>屬性描述子項目應如何定位到父元素分配的佈局空間中。 藉由一起使用這些屬性，您可以精確定位子項目。 例如，<xref:System.Windows.Controls.DockPanel>子項目可以指定四種不同的水準對齊：、<xref:System.Windows.HorizontalAlignment.Left><xref:System.Windows.HorizontalAlignment.Right>或<xref:System.Windows.HorizontalAlignment.Center>，或以<xref:System.Windows.HorizontalAlignment.Stretch>填充可用空間。 類似的值可供垂直定位之用。  
  
> [!NOTE]
> 元素上的顯式設置<xref:System.Windows.FrameworkElement.Height%2A>和<xref:System.Windows.FrameworkElement.Width%2A>屬性優先于<xref:System.Windows.HorizontalAlignment.Stretch>屬性值。 <xref:System.Windows.FrameworkElement.Height%2A>嘗試設置<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>的值`Stretch`會導致`Stretch`請求被忽略。  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>
### <a name="horizontalalignment-property"></a>HorizontalAlignment 屬性  
 屬性<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>聲明要應用於子項目的水準對齊特徵。 下表顯示了<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>該屬性的每個可能值。  
  
|member|描述|  
|------------|-----------------|  
|<xref:System.Windows.HorizontalAlignment.Left>|子項目對齊父項目的已配置版面配置空間的左側。|  
|<xref:System.Windows.HorizontalAlignment.Center>|子項目對齊父項目的已配置版面配置空間的中間。|  
|<xref:System.Windows.HorizontalAlignment.Right>|子項目對齊父項目的已配置版面配置空間的右側。|  
|<xref:System.Windows.HorizontalAlignment.Stretch> (預設值)|子項目會自動縮放以填滿父項目的已配置版面配置空間。 顯式<xref:System.Windows.FrameworkElement.Width%2A>值<xref:System.Windows.FrameworkElement.Height%2A>和值優先。|  
  
 下面的示例演示如何將<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性應用於<xref:System.Windows.Controls.Button>元素。 為了更清楚說明各種不同的轉譯行為，會顯示每個屬性值。  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 上述程式碼會產生類似下圖的版面配置。 每個<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>值的定位效果在圖中可見。  
  
 ![HorizontalAlignment 範例](./media/layout-horizontal-alignment-graphic.PNG "layout_horizontal_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>
### <a name="verticalalignment-property"></a>VerticalAlignment 屬性  
 該<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>屬性描述要應用於子項目的垂直對齊特徵。 下表顯示了<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>該屬性的每個可能值。  
  
|member|描述|  
|------------|-----------------|  
|<xref:System.Windows.VerticalAlignment.Top>|子項目對齊父項目的已配置版面配置空間的頂端。|  
|<xref:System.Windows.VerticalAlignment.Center>|子項目對齊父項目的已配置版面配置空間的中間。|  
|<xref:System.Windows.VerticalAlignment.Bottom>|子項目對齊父項目的已配置版面配置空間的底部。|  
|<xref:System.Windows.VerticalAlignment.Stretch> (預設值)|子項目會自動縮放以填滿父項目的已配置版面配置空間。 顯式<xref:System.Windows.FrameworkElement.Width%2A>值<xref:System.Windows.FrameworkElement.Height%2A>和值優先。|  
  
 下面的示例演示如何將<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>屬性應用於<xref:System.Windows.Controls.Button>元素。 為了更清楚說明各種不同的轉譯行為，會顯示每個屬性值。 出於此示例的目的，<xref:System.Windows.Controls.Grid>使用具有可見格線的元素作為父元素，以便更好地說明每個屬性值的佈局行為。  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xaml[MPALayoutVerticalAlignment#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 上述程式碼會產生類似下圖的版面配置。 每個<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>值的定位效果在圖中可見。  
  
 ![VerticalAlignment 屬性範例](./media/layout-vertical-alignment-graphic.PNG "layout_vertical_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>
## <a name="understanding-margin-properties"></a>了解邊界屬性  
 屬性<xref:System.Windows.FrameworkElement.Margin%2A>描述元素與其子項或對等體之間的距離。 <xref:System.Windows.FrameworkElement.Margin%2A>通過使用 語法（如`Margin="20"`） 可以統一值。 使用此語法，將應用於元素<xref:System.Windows.FrameworkElement.Margin%2A>的 20 個獨立于設備的圖元的統一。 <xref:System.Windows.FrameworkElement.Margin%2A>值還可以採用四個不同的值的形式，每個值描述一個不同的邊距以應用於左側、頂部、右側和底部（按該順序），如`Margin="0,10,5,25"`。 正確使用 該<xref:System.Windows.FrameworkElement.Margin%2A>屬性可以非常精細地控制元素的呈現位置及其相鄰元素和子項目的渲染位置。  
  
> [!NOTE]
> 非零邊距應用元素<xref:System.Windows.FrameworkElement.ActualWidth%2A>和<xref:System.Windows.FrameworkElement.ActualHeight%2A>以外的空間。  
  
 下面的示例演示如何在一組<xref:System.Windows.Controls.Button>元素周圍應用統一邊距。 元素<xref:System.Windows.Controls.Button>以每個方向上的 10 圖元邊距緩衝區均勻間隔。  
  
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
 填充在大多數方面都類似<xref:System.Windows.FrameworkElement.Margin%2A>。 Padding<xref:System.Windows.Documents.Block>屬性僅在幾個類上公開，這主要為方便： 、<xref:System.Windows.Controls.Border><xref:System.Windows.Controls.Control>和<xref:System.Windows.Controls.TextBlock>是公開填充屬性的類的示例。 屬性<xref:System.Windows.Controls.Border.Padding%2A>按指定<xref:System.Windows.Thickness>值放大子項目的有效大小。  
  
 下面的示例演示如何應用於<xref:System.Windows.Controls.Border.Padding%2A>父<xref:System.Windows.Controls.Border>元素。  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xaml[MarginPaddingAlignmentSample#3](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>
## <a name="using-alignment-margins-and-padding-in-an-application"></a>在應用程式使用對齊、邊界和邊框間距  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>，<xref:System.Windows.FrameworkElement.Margin%2A><xref:System.Windows.Controls.Border.Padding%2A>並提供<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>創建複雜[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]複雜所需的定位控制。 您可以使用每個屬性的效果來變更子項目定位，這樣可以在建立動態應用程式和使用者體驗時具有彈性。  
  
 下列範例示範本主題所述的每個概念。 在本主題中的第一個示例中找到的基礎結構的基礎上，本示例將元素添加<xref:System.Windows.Controls.Grid>為第一個示例中的<xref:System.Windows.Controls.Border>子項目。 <xref:System.Windows.Controls.Border.Padding%2A>應用於父<xref:System.Windows.Controls.Border>元素。 <xref:System.Windows.Controls.Grid>用於在三個子<xref:System.Windows.Controls.StackPanel>元素之間劃分空間。 <xref:System.Windows.Controls.Button>元素再次用於顯示<xref:System.Windows.FrameworkElement.Margin%2A>和<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>的各種效果。 <xref:System.Windows.Controls.TextBlock>元素將添加到每個<xref:System.Windows.Controls.ColumnDefinition>元素中，以便更好地定義應用於每列中<xref:System.Windows.Controls.Button>元素的各種屬性。  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xaml[MarginPaddingAlignmentSample#4](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 上述的應用程式在編譯時，會產生類似下圖的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 各種屬性值的效果在元素之間的間距中很明顯，並且每個列中元素的重要屬性值顯示在元素中<xref:System.Windows.Controls.TextBlock>。  
  
 ![數個定位屬性都在同一個應用程式中](./media/layout-margins-padding-aligment-graphic3.PNG "layout_margins_padding_aligment_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>
## <a name="whats-next"></a>接下來  
 <xref:System.Windows.FrameworkElement>類定義的定位屬性可精細控制[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式中的元素放置。 現在您有數種技巧可使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 進一步使用位置項目。  
  
 有更詳細說明 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 版面配置的其他資源可供使用。 "[面板概述](../controls/panels-overview.md)"主題包含有關各種<xref:System.Windows.Controls.Panel>元素的更多詳細資訊。 主題[演練：我的第一個 WPF 桌面應用程式](../getting-started/walkthrough-my-first-wpf-desktop-application.md)引入了使用佈局元素定位元件並將其操作綁定到資料來源的高級技術。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- <xref:System.Windows.FrameworkElement.Margin%2A>
- [面板概觀](../controls/panels-overview.md)
- [版面配置](layout.md)
- [WPF 版面配置庫範例 (英文)](https://go.microsoft.com/fwlink/?LinkID=160054)
