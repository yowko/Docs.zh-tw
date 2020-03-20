---
title: ToolTip 概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], about ToolTip control
- controls [WPF], ToolTip
ms.assetid: f06c1603-e9cb-4809-8a62-234607fc52f7
ms.openlocfilehash: 0fec31b28a21c2e17986210c852b3d630087842d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181941"
---
# <a name="tooltip-overview"></a>ToolTip 概觀
工具提示是當使用者將滑鼠指標懸停在元素（如 在 上）時出現的一個小快顯視窗<xref:System.Windows.Controls.Button>。 本主題將介紹工具提示，並說明如何建立及自訂工具提示內容。  

<a name="what_is_a_tooltip"></a>
## <a name="what-is-a-tooltip"></a>什麼是工具提示？  
 當使用者將滑鼠指標移到有工具提示的元素上時，包含工具提示內容 (例如，描述控制項功能的文字內容) 的視窗會出現並持續一段指定的時間。 如果使用者將滑鼠指標移離控制項，由於工具提示內容無法接收焦點，視窗便會消失。  
  
 工具提示的內容可包含一或多個文字行、影像、圖形或其他視覺內容。 您可以將下列其中一個屬性設為工具提示內容來定義控制項的工具提示。  
  
- <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 您使用的屬性取決於定義工具提示的控制項是否從<xref:System.Windows.FrameworkContentElement>或<xref:System.Windows.FrameworkElement>類繼承。  
  
<a name="create_tooltip"></a>
## <a name="creating-a-tooltip"></a>建立 ToolTip  
 下面的示例演示如何通過將<xref:System.Windows.FrameworkElement.ToolTip%2A><xref:System.Windows.Controls.Button>控制項的屬性設置為文本字串來創建簡單的工具提示。  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 您還可以將工具提示定義為<xref:System.Windows.Controls.ToolTip>物件。 下面的示例用於[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]指定<xref:System.Windows.Controls.ToolTip>物件作為<xref:System.Windows.Controls.TextBox>元素的工具提示。 請注意，該示例<xref:System.Windows.Controls.ToolTip>通過設置 屬性指定<xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>。  
  
 [!code-xaml[ToolTipSimple#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 下面的示例使用代碼生成<xref:System.Windows.Controls.ToolTip>物件。 該示例創建<xref:System.Windows.Controls.ToolTip>一`tt`個 （ ，<xref:System.Windows.Controls.Button>並將其與 關聯它與 。  
  
 [!code-csharp[ToolTipSimple#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 還可以通過將工具提示內容封閉在佈局元素（如<xref:System.Windows.Controls.ToolTip><xref:System.Windows.Controls.DockPanel>中）來創建未定義為物件的工具提示內容。 下面的示例演示如何將<xref:System.Windows.FrameworkElement.ToolTip%2A>中的 屬性<xref:System.Windows.Controls.TextBox>設置為包含在<xref:System.Windows.Controls.DockPanel>控制項中的內容。  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a>使用 ToolTip 和 ToolTipService 類別的屬性  
 您可以透過設定視覺屬性並套用樣式，來自訂工具提示內容。 如果將工具提示內容定義為<xref:System.Windows.Controls.ToolTip>物件，則可以設置<xref:System.Windows.Controls.ToolTip>物件的可視屬性。 否則，必須在<xref:System.Windows.Controls.ToolTipService>類上設置等效的附加屬性。  
  
 有關如何設置屬性以便使用<xref:System.Windows.Controls.ToolTip>和<xref:System.Windows.Controls.ToolTipService>屬性指定工具提示內容的位置的示例，請參閱[定位工具提示](how-to-position-a-tooltip.md)。  
  
<a name="StylingToolTip"></a>
## <a name="styling-a-tooltip"></a>設定 ToolTip 樣式  
 您可以通過定義自訂<xref:System.Windows.Style><xref:System.Windows.Controls.ToolTip>來設置 樣式 。 下面的<xref:System.Windows.Style>示例定義一個調用`Simple`，它演示如何通過設置<xref:System.Windows.Controls.ToolTip><xref:System.Windows.Controls.Control.Background%2A>、<xref:System.Windows.Controls.Control.Foreground%2A>和<xref:System.Windows.Controls.Control.FontSize%2A>來抵消 的位置並更改其外觀。 <xref:System.Windows.Controls.Control.FontWeight%2A>  
  
 [!code-xaml[ToolTipSimple#Style](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>
## <a name="using-the-time-interval-properties-of-tooltipservice"></a>使用 ToolTipService 的時間間隔屬性  
 該<xref:System.Windows.Controls.ToolTipService>類提供以下屬性，用於設置工具提示顯示時間：<xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>和<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>。 <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>  
  
 使用<xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>和<xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>屬性指定<xref:System.Windows.Controls.ToolTip>出現之前的延遲（通常簡短），並指定<xref:System.Windows.Controls.ToolTip>保留的可見時間。 如需詳細資訊，請參閱[操作說明：延遲 ToolTip 的顯示](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms747264(v=vs.90))。  
  
 該<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>屬性確定在滑鼠指標之間快速移動滑鼠指標時，不同控制項的工具提示是否不會出現初始延遲。 有關該<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>屬性的詳細資訊，請參閱[使用"ShowDelay 之間"屬性](how-to-use-the-betweenshowdelay-property.md)。  
  
 下列範例顯示如何為工具提示設定這些屬性。  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.ToolTipService>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipEventArgs>
- <xref:System.Windows.Controls.ToolTipEventHandler>
- [如何使用主題](tooltip-how-to-topics.md)
