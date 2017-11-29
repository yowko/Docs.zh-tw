---
title: "ToolTip 概觀"
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
helpviewer_keywords:
- ToolTip control [WPF], about ToolTip control
- controls [WPF], ToolTip
ms.assetid: f06c1603-e9cb-4809-8a62-234607fc52f7
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31bd56323e90368f850ae54854e6f50b63d5f7fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="tooltip-overview"></a>ToolTip 概觀
工具提示是小型的快顯視窗出現時，使用者將滑鼠指標停留在項目，例如為 [過度] <xref:System.Windows.Controls.Button>。 本主題將介紹工具提示，並說明如何建立及自訂工具提示內容。  
  
 
  
<a name="what_is_a_tooltip"></a>   
## <a name="what-is-a-tooltip"></a>什麼是工具提示？  
 當使用者將滑鼠指標移到有工具提示的元素上時，包含工具提示內容 (例如，描述控制項功能的文字內容) 的視窗會出現並持續一段指定的時間。 如果使用者將滑鼠指標移離控制項，由於工具提示內容無法接收焦點，視窗便會消失。  
  
 工具提示的內容可包含一或多個文字行、影像、圖形或其他視覺內容。 您可以將下列其中一個屬性設為工具提示內容來定義控制項的工具提示。  
  
-   <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 您使用哪一個屬性，取決於定義工具提示控制項繼承自<xref:System.Windows.FrameworkContentElement>或<xref:System.Windows.FrameworkElement>類別。  
  
<a name="create_tooltip"></a>   
## <a name="creating-a-tooltip"></a>建立 ToolTip  
 下列範例示範如何建立簡單的工具提示，藉由設定<xref:System.Windows.FrameworkElement.ToolTip%2A>屬性<xref:System.Windows.Controls.Button>控制項的文字字串。  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 您也可以定義為工具提示<xref:System.Windows.Controls.ToolTip>物件。 下列範例會使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]指定<xref:System.Windows.Controls.ToolTip>物件的工具提示為<xref:System.Windows.Controls.TextBox>項目。 請注意，此範例會指定<xref:System.Windows.Controls.ToolTip>藉由設定<xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>屬性。  
  
 [!code-xaml[ToolTipSimple#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 下列範例會使用程式碼產生<xref:System.Windows.Controls.ToolTip>物件。 此範例會建立<xref:System.Windows.Controls.ToolTip>(`tt`) 並將它與相關聯<xref:System.Windows.Controls.Button>。  
  
 [!code-csharp[ToolTipSimple#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 您也可以建立為未定義的工具提示內容<xref:System.Windows.Controls.ToolTip>物件，只要將工具提示內容在版面配置項目，例如<xref:System.Windows.Controls.DockPanel>。 下列範例示範如何設定<xref:System.Windows.FrameworkElement.ToolTip%2A>屬性<xref:System.Windows.Controls.TextBox>內容是包含在<xref:System.Windows.Controls.DockPanel>控制項。  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>   
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a>使用 ToolTip 和 ToolTipService 類別的屬性  
 您可以透過設定視覺屬性並套用樣式，來自訂工具提示內容。 如果您定義的內容做為工具提示<xref:System.Windows.Controls.ToolTip>物件，您可以設定的視覺屬性<xref:System.Windows.Controls.ToolTip>物件。 否則，您必須設定對等的附加的屬性上<xref:System.Windows.Controls.ToolTipService>類別。  
  
 如需如何設定屬性來指定工具提示內容的位置使用的範例<xref:System.Windows.Controls.ToolTip>和<xref:System.Windows.Controls.ToolTipService>屬性，請參閱[放置工具提示](../../../../docs/framework/wpf/controls/how-to-position-a-tooltip.md)。  
  
<a name="StylingToolTip"></a>   
## <a name="styling-a-tooltip"></a>設定 ToolTip 樣式  
 您可以設定樣式<xref:System.Windows.Controls.ToolTip>藉由定義自訂<xref:System.Windows.Style>。 下列範例會定義<xref:System.Windows.Style>呼叫`Simple`，示範如何在位移位置的<xref:System.Windows.Controls.ToolTip>和設定以變更其外觀<xref:System.Windows.Controls.Control.Background%2A>， <xref:System.Windows.Controls.Control.Foreground%2A>， <xref:System.Windows.Controls.Control.FontSize%2A>，和<xref:System.Windows.Controls.Control.FontWeight%2A>。  
  
 [!code-xaml[ToolTipSimple#Style](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>   
## <a name="using-the-time-interval-properties-of-tooltipservice"></a>使用 ToolTipService 的時間間隔屬性  
 <xref:System.Windows.Controls.ToolTipService>類別會提供下列屬性，以設定工具提示顯示時間： <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>， <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>，和<xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>。  
  
 使用<xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>和<xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>屬性，以指定的延遲通常簡短，之前<xref:System.Windows.Controls.ToolTip>隨即出現，並且指定多久<xref:System.Windows.Controls.ToolTip>保持可見狀態。 如需詳細資訊，請參閱[操作說明：延遲 ToolTip 的顯示](http://msdn.microsoft.com/en-us/618e05ef-f2bf-4a53-a0f4-aacb49918bd7)。  
  
 <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>屬性會決定當您將滑鼠指標之間快速移動它們是否不同的控制項的工具提示顯示沒有初始的延遲。 如需有關<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>屬性，請參閱[使用 BetweenShowDelay 屬性](../../../../docs/framework/wpf/controls/how-to-use-the-betweenshowdelay-property.md)。  
  
 下列範例顯示如何為工具提示設定這些屬性。  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.ToolTipService>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipEventArgs>  
 <xref:System.Windows.Controls.ToolTipEventHandler>  
 [操作說明主題](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)
