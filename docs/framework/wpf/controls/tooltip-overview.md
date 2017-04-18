---
title: "工具提示概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "控制項, ToolTip"
  - "ToolTip 控制項, 關於 ToolTip 控制項"
ms.assetid: f06c1603-e9cb-4809-8a62-234607fc52f7
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# 工具提示概觀
工具提示是一個小型快顯視窗，會在使用者將滑鼠指標暫停在某個項目 \(如 <xref:System.Windows.Controls.Button>\) 上時出現。  本主題將介紹工具提示，並說明如何建立和自訂工具提示內容。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="what_is_a_tooltip"></a>   
## 什麼是工具提示？  
 當使用者將滑鼠指標移到有工具提示的項目上時，包含工具提示內容 \(例如，描述控制項功能的文字內容\) 的視窗會出現並持續一段指定的時間。  如果使用者將滑鼠指標移離控制項，視窗就會消失，因為工具提示內容不再接收焦點。  
  
 工具提示的內容可包含一或多行文字、一個或多個影像、圖案或其他視覺內容。  要定義控制項的工具提示，可以將下列其中一個屬性設為工具提示內容。  
  
-   <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=fullName>  
  
 要使用哪個屬性，會視定義工具提示的控制項是繼承自 <xref:System.Windows.FrameworkContentElement> 或 <xref:System.Windows.FrameworkElement> 類別而定。  
  
<a name="create_tooltip"></a>   
## 建立工具提示  
 下列範例顯示如何藉由將 <xref:System.Windows.Controls.Button> 控制項的 <xref:System.Windows.FrameworkElement.ToolTip%2A> 屬性設為文字字串，以建立簡單的工具提示。  
  
 [!code-xml[GroupBoxSnippet#ToolTipString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 您也可以將工具提示定義為 <xref:System.Windows.Controls.ToolTip> 物件。  下列範例會使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，將 <xref:System.Windows.Controls.ToolTip> 物件指定為 <xref:System.Windows.Controls.TextBox> 項目的工具提示。  請注意，此範例是藉由設定 <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=fullName> 屬性來指定 <xref:System.Windows.Controls.ToolTip>。  
  
 [!code-xml[ToolTipSimple#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 下列範例使用程式碼產生 <xref:System.Windows.Controls.ToolTip> 物件。  此範例會建立 <xref:System.Windows.Controls.ToolTip> \(`tt`\)，然後將它與 <xref:System.Windows.Controls.Button> 建立關聯。  
  
 [!code-csharp[ToolTipSimple#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 您也可以建立不是定義為 <xref:System.Windows.Controls.ToolTip> 物件的工具提示內容，方式是將工具提示內容封入版面配置項目，例如 <xref:System.Windows.Controls.DockPanel>。  下列範例顯示如何將 <xref:System.Windows.Controls.TextBox> 的 <xref:System.Windows.FrameworkElement.ToolTip%2A> 屬性設為封入 <xref:System.Windows.Controls.DockPanel> 控制項的內容。  
  
 [!code-xml[GroupBoxSnippet#ToolTipDockPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>   
## 使用工具提示的屬性和 ToolTipService 類別  
 您可以藉由設定視覺屬性和套用樣式，來自訂工具提示內容。  如果您將工具提示內容定義為 <xref:System.Windows.Controls.ToolTip> 物件，可以設定 <xref:System.Windows.Controls.ToolTip> 物件的視覺屬性。  否則，就必須在 <xref:System.Windows.Controls.ToolTipService> 類別上設定對等的[附加屬性](GTMT)。  
  
 如需範例示範如何使用 <xref:System.Windows.Controls.ToolTip> 和 <xref:System.Windows.Controls.ToolTipService> 屬性，以設定屬性來指定工具提示內容的位置，請參閱 [置放工具提示](../../../../docs/framework/wpf/controls/how-to-position-a-tooltip.md)。  
  
<a name="StylingToolTip"></a>   
## 設定工具提示樣式  
 您可以定義自訂 <xref:System.Windows.Style>，來設定 <xref:System.Windows.Controls.ToolTip> 的樣式。  下列範例會定義一個名為 `Simple` 的 <xref:System.Windows.Style>，顯示如何藉由設定 <xref:System.Windows.Controls.Control.Background%2A>、<xref:System.Windows.Controls.Control.Foreground%2A>、<xref:System.Windows.Controls.Control.FontSize%2A> 和 <xref:System.Windows.Controls.Control.FontWeight%2A>，來位移 <xref:System.Windows.Controls.ToolTip> 的位置並變更其外觀。  
  
 [!code-xml[ToolTipSimple#Style](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>   
## 使用 ToolTipService 的時間間隔屬性  
 <xref:System.Windows.Controls.ToolTipService> 類別提供下列屬性來設定工具提示的顯示時間：<xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>、<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> 和 <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>。  
  
 使用 <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> 和 <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> 屬性，可以指定一段短暫的延遲時間，讓 <xref:System.Windows.Controls.ToolTip> 在這段時間過後顯示，並可設定 <xref:System.Windows.Controls.ToolTip> 要顯示多久的時間。  如需詳細資訊，請參閱 [How to: Delay the Display of a ToolTip](http://msdn.microsoft.com/zh-tw/618e05ef-f2bf-4a53-a0f4-aacb49918bd7)。  
  
 <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> 屬性會決定滑鼠指標在不同控制項之間快速移動時，工具提示是否會在沒有初始延遲的情況下出現。  如需 <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> 屬性的詳細資訊，請參閱 [使用 BetweenShowDelay 屬性](../../../../docs/framework/wpf/controls/how-to-use-the-betweenshowdelay-property.md)。  
  
 下列範例顯示如何設定工具提示的這些屬性。  
  
 [!code-xml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## 請參閱  
 <xref:System.Windows.Controls.ToolTipService>   
 <xref:System.Windows.Controls.ToolTip>   
 <xref:System.Windows.Controls.ToolTipEventArgs>   
 <xref:System.Windows.Controls.ToolTipEventHandler>   
 [HOW TO 主題](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)