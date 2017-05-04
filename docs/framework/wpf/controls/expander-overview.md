---
title: "Expander 概觀 | Microsoft Docs"
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
  - "控制項, 展開工具"
  - "Expander 控制項, 關於 Expander 控制項"
ms.assetid: 877bf425-0e54-49ec-8fd2-13a211377abb
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Expander 概觀
<xref:System.Windows.Controls.Expander> 控制項這個方法可以在可展開的區域中提供內容，而這個區域類似視窗且會包含標頭。  
  
   
  
<a name="CreatinganExpanderinXAML"></a>   
## 建立簡單的 Expander  
 下列範例示範如何建立簡單的 <xref:System.Windows.Controls.Expander> 控制項。  本範例會建立外觀類似於前一個範例的 <xref:System.Windows.Controls.Expander>。  
  
 [!code-xml[ExpanderExample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderExample/CSharp/Page1.xaml#2)]  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A> 和 <xref:System.Windows.Controls.Expander> 的 <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> 也會包含複雜的內容，例如，<xref:System.Windows.Controls.RadioButton> 和 <xref:System.Windows.Controls.Image> 物件。  
  
<a name="SettingtheDirectionoftheExpandingWindow"></a>   
## 設定展開內容區域的方向  
 您可以設定<xref:System.Windows.Controls.Expander> 控制項的內容區域，使用 <xref:System.Windows.Controls.ExpandDirection> 屬性，往任一個方向展開 \(包括 <xref:System.Windows.Controls.ExpandDirection>、<xref:System.Windows.Controls.ExpandDirection>、<xref:System.Windows.Controls.ExpandDirection> 或 <xref:System.Windows.Controls.ExpandDirection>\)。  摺疊內容區域時，則只會顯示 <xref:System.Windows.Controls.Expander> <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> 以及它的切換按鈕。  會顯示方向箭號的 <xref:System.Windows.Controls.Button> 控制項，可以做為展開或折疊內容區域的切換按鈕之用。  在展開時，<xref:System.Windows.Controls.Expander> 會嘗試以類似視窗的區域中顯示所有內容。  
  
<a name="SettingSizeDimensionsonanExpanderinaPanel"></a>   
## 控制面板中 Expander 的大小  
 如果 <xref:System.Windows.Controls.Expander> 控制項位於版面配置控制項內部，且此控制項繼承自 <xref:System.Windows.Controls.Panel> \(例如 <xref:System.Windows.Controls.StackPanel>\)，則當 <xref:System.Windows.Controls.Expander.ExpandDirection%2A> 屬性設定為 <xref:System.Windows.Controls.ExpandDirection> 或 <xref:System.Windows.Controls.ExpandDirection> 時，請勿在 <xref:System.Windows.Controls.Expander> 上指定 <xref:System.Windows.FrameworkElement.Height%2A>。  同樣地，當 <xref:System.Windows.Controls.Expander.ExpandDirection%2A> 屬性設定為 <xref:System.Windows.Controls.ExpandDirection> 或 <xref:System.Windows.Controls.ExpandDirection> 時，請勿在 <xref:System.Windows.Controls.Expander> 上指定 <xref:System.Windows.FrameworkElement.Width%2A>。  
  
 當您以展開內容顯示的方向，來設定 <xref:System.Windows.Controls.Expander> 控制項上的大小維度時，<xref:System.Windows.Controls.Expander> 會控制內容所使用的區域並在區域周圍顯示框線。  即時摺疊內容時，也會顯示框線。  若要設定展開區域的大小，請設定 <xref:System.Windows.Controls.Expander> 內容的大小維度，或者，如果您需要捲動功能，則對包含該內容的 <xref:System.Windows.Controls.ScrollViewer> 進行設定。  
  
 如果 <xref:System.Windows.Controls.Expander> 控制項是 <xref:System.Windows.Controls.DockPanel> 中的最後一個項目，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 便會自動將  <xref:System.Windows.Controls.Expander> 維度設定為與 <xref:System.Windows.Controls.DockPanel> 其餘區域相同。  如果不要使用這個預設行為，請將 <xref:System.Windows.Controls.DockPanel> 物件上的 <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> 屬性設定為 `false`，或確定 <xref:System.Windows.Controls.Expander> 不是 <xref:System.Windows.Controls.DockPanel> 中的最後一個項目。  
  
<a name="CreatingScrollableContent"></a>   
## 建立可捲動的內容  
 如果內容大於內容區域的大小，則可以將 <xref:System.Windows.Controls.Expander> 的內容換行到 <xref:System.Windows.Controls.ScrollViewer>，才能提供可捲動的內容。  <xref:System.Windows.Controls.Expander> 控制項不會自動提供捲動功能。  以下範例示範包含 <xref:System.Windows.Controls.ScrollViewer> 控制項的 <xref:System.Windows.Controls.Expander> 控制項。  
  
 **ScrollViewer 的 Expander**  
  
 ![具有 ScrollBar 的 Expander](../../../../docs/framework/wpf/controls/media/expanderwithscrollbar.JPG "ExpanderWithScrollBar")  
  
 當您將 <xref:System.Windows.Controls.Expander> 控制項置於 <xref:System.Windows.Controls.ScrollViewer>，請設定與方向相對應的 <xref:System.Windows.Controls.ScrollViewer> 維度屬性，此方向就是 <xref:System.Windows.Controls.Expander> 內容開啟至<xref:System.Windows.Controls.Expander> 內容區域的大小。  例如，如果您將 <xref:System.Windows.Controls.Expander> 上的 <xref:System.Windows.Controls.Expander.ExpandDirection%2A> 屬性設定為 <xref:System.Windows.Controls.ExpandDirection> \(內容區域向下開啟\)，則請將 <xref:System.Windows.Controls.ScrollViewer> 控制項上的 <xref:System.Windows.FrameworkElement.Height%2A> 屬性設定為內容區域的所需高度。  如果您改為在內容本身上設定高度維度，<xref:System.Windows.Controls.ScrollViewer> 則無法辨識此設定，因此，無法提供可捲動的內容。  
  
 下列範例示範如何建立具有複雜內容的 <xref:System.Windows.Controls.Expander> 控制項，且該控制項包含 <xref:System.Windows.Controls.ScrollViewer> 控制項。  本範例會建立與本節開頭範例類似的 <xref:System.Windows.Controls.Expander>。  
  
 [!code-csharp[ExpanderRichContent#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ExpanderRichContent#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpanderRichContent/VisualBasic/Window1.xaml.vb#1)]
 [!code-xml[ExpanderRichContent#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#1)]  
  
<a name="UsingtheAlignmentProperties"></a>   
## 使用對齊屬性  
 您可以設定 <xref:System.Windows.Controls.Expander> 控制項上的 <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> 和 <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> 屬性來對齊內容。  當您設定這些屬性時，標頭和展開的內容便會套用對齊格式。  
  
## 請參閱  
 <xref:System.Windows.Controls.Expander>   
 <xref:System.Windows.Controls.ExpandDirection>   
 [HOW TO 主題](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)