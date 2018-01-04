---
title: "快顯功能表概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0cb20895b5af35fec7274ca4c747740390104355
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="popup-overview"></a>快顯功能表概觀
<xref:System.Windows.Controls.Primitives.Popup>控制項可用來在漂浮在目前應用程式視窗相對於指定的項目或螢幕座標的另一個視窗中顯示內容。 本主題將介紹<xref:System.Windows.Controls.Primitives.Popup>控制項，並提供其用途的相關資訊。  
  
 
  
<a name="What_Is_a_Popup_"></a>   
## <a name="what-is-a-popup"></a>什麼是快顯？  
 A<xref:System.Windows.Controls.Primitives.Popup>控制項相對於項目或在螢幕上的點個別視窗中顯示內容。 當<xref:System.Windows.Controls.Primitives.Popup>就會顯示<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A>屬性設定為`true`。  
  
> [!NOTE]
>  A<xref:System.Windows.Controls.Primitives.Popup>不會自動開啟時滑鼠指標移到其父物件。 如果您想<xref:System.Windows.Controls.Primitives.Popup>若要自動開啟，請使用<xref:System.Windows.Controls.ToolTip>或<xref:System.Windows.Controls.ToolTipService>類別。 如需詳細資訊，請參閱 [ToolTip 概觀](../../../../docs/framework/wpf/controls/tooltip-overview.md)。  
  
<a name="APopupExample"></a>   
## <a name="creating-a-popup"></a>建立快顯  
 下列範例示範如何定義<xref:System.Windows.Controls.Primitives.Popup>控制項的子元素<xref:System.Windows.Controls.Button>控制項。 因為<xref:System.Windows.Controls.Button>可以有只有一個子項目，這個範例會將文字<xref:System.Windows.Controls.Button>和<xref:System.Windows.Controls.Primitives.Popup>控制項<xref:System.Windows.Controls.StackPanel>。 內容<xref:System.Windows.Controls.Primitives.Popup>會出現在<xref:System.Windows.Controls.TextBlock>控制項，它會漂浮在附近相關應用程式視窗的另一個視窗中顯示其文字<xref:System.Windows.Controls.Button>控制項。  
  
 [!code-xaml[PopupSimple#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>   
## <a name="controls-that-implement-a-popup"></a>實作快顯的控制項  
 您可以建置<xref:System.Windows.Controls.Primitives.Popup>到其他控制項的控制項。 下列控制項實作<xref:System.Windows.Controls.Primitives.Popup>控制針對特定用途：  
  
-   <xref:System.Windows.Controls.ToolTip>. 如果您想要建立項目的工具提示，使用<xref:System.Windows.Controls.ToolTip>和<xref:System.Windows.Controls.ToolTipService>類別。 如需詳細資訊，請參閱 [ToolTip 概觀](../../../../docs/framework/wpf/controls/tooltip-overview.md)。  
  
-   <xref:System.Windows.Controls.ContextMenu>. 如果您想要建立的項目內容功能表，使用<xref:System.Windows.Controls.ContextMenu>控制項。 如需詳細資訊，請參閱 [ContextMenu 概觀](../../../../docs/framework/wpf/controls/contextmenu-overview.md)。  
  
-   <xref:System.Windows.Controls.ComboBox>. 如果您想要建立具有可顯示或隱藏，請使用下拉式清單方塊的選取控制項<xref:System.Windows.Controls.ComboBox>控制項。  
  
-   <xref:System.Windows.Controls.Expander>. 如果您想要建立控制項，以顯示具有可摺疊的區域的標頭會顯示內容，請使用<xref:System.Windows.Controls.Expander>控制項。 如需詳細資訊，請參閱 [Expander 概觀](../../../../docs/framework/wpf/controls/expander-overview.md)。  
  
<a name="PopupBehaviorandAppearance"></a>   
## <a name="popup-behavior-and-appearance"></a>快顯行為和外觀  
 <xref:System.Windows.Controls.Primitives.Popup>控制項提供可讓您自訂其行為和外觀的功能。 例如，您可以設定開啟和關閉行為、 動畫、 不透明和點陣圖效果和<xref:System.Windows.Controls.Primitives.Popup>大小和位置。  
  
<a name="OpenandCloseBehavior"></a>   
### <a name="open-and-close-behavior"></a>開啟和關閉行為  
 A<xref:System.Windows.Controls.Primitives.Popup>控制項會顯示其內容時<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A>屬性設定為`true`。 根據預設，<xref:System.Windows.Controls.Primitives.Popup>維持開啟直到<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A>屬性設定為`false`。 不過，您可以變更預設行為，藉由設定<xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A>屬性`false`。 當您將此屬性設定為`false`、<xref:System.Windows.Controls.Primitives.Popup>內容視窗具有滑鼠擷取。 <xref:System.Windows.Controls.Primitives.Popup>失去滑鼠擷取和視窗關閉時滑鼠事件之外，就會發生<xref:System.Windows.Controls.Primitives.Popup>視窗。  
  
 <xref:System.Windows.Controls.Primitives.Popup.Opened>和<xref:System.Windows.Controls.Primitives.Popup.Closed>引發事件時<xref:System.Windows.Controls.Primitives.Popup>內容視窗已開啟還是關閉。  
  
<a name="Animation"></a>   
### <a name="animation"></a>動畫  
 <xref:System.Windows.Controls.Primitives.Popup>控制項具有內建支援通常淡入與投影片中類似的行為與相關聯的動畫。 您可以藉由設定開啟這些動畫<xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A>屬性<xref:System.Windows.Controls.Primitives.PopupAnimation>列舉值。 如<xref:System.Windows.Controls.Primitives.Popup>動畫正常運作，您必須設定<xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A>屬性`true`。  
  
 您也可以套用類似的動畫<xref:System.Windows.Media.Animation.Storyboard>至<xref:System.Windows.Controls.Primitives.Popup>控制項。  
  
<a name="OpacityandBitmapEffects"></a>   
### <a name="opacity-and-bitmap-effects"></a>不透明度和點陣圖效果  
 <xref:System.Windows.UIElement.Opacity%2A>屬性<xref:System.Windows.Controls.Primitives.Popup>控制項有不會影響其內容。 根據預設，<xref:System.Windows.Controls.Primitives.Popup>內容的視窗是不透明。 若要建立透明<xref:System.Windows.Controls.Primitives.Popup>，將<xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A>屬性`true`。  
  
 內容<xref:System.Windows.Controls.Primitives.Popup>不是繼承的點陣圖效果，例如<xref:System.Windows.Media.Effects.DropShadowBitmapEffect>，您直接上設定<xref:System.Windows.Controls.Primitives.Popup>控制項或其他任何元素的父視窗中。 要顯示的內容上的點陣圖效果<xref:System.Windows.Controls.Primitives.Popup>，您必須設定直接在其內容的點陣圖效果。 例如，如果子系<xref:System.Windows.Controls.Primitives.Popup>是<xref:System.Windows.Controls.StackPanel>上, 設定的點陣圖效果<xref:System.Windows.Controls.StackPanel>。  
  
<a name="PopupSize"></a>   
### <a name="popup-size"></a>快顯大小  
 根據預設，<xref:System.Windows.Controls.Primitives.Popup>其內容會自動調整大小。 自動調整時，某些點陣圖效果可能會因為隱藏的螢幕區域定義的預設大小<xref:System.Windows.Controls.Primitives.Popup>內容未提供足夠的空間顯示點陣圖效果。  
  
 <xref:System.Windows.Controls.Primitives.Popup>當您設定時，可能也模糊內容<xref:System.Windows.UIElement.RenderTransform%2A>的內容。 在此案例中，某些內容可能已經被隱藏如果已轉換的內容<xref:System.Windows.Controls.Primitives.Popup>超出原始區域<xref:System.Windows.Controls.Primitives.Popup>。 如果點陣圖效果或轉換需要更多空間，您可以定義周圍的邊界<xref:System.Windows.Controls.Primitives.Popup>為了提供更多區域控制項的內容。  
  
<a name="DefiningPopupPosition"></a>   
## <a name="defining-the-popup-position"></a>定義快顯位置  
 您可以藉由設定放置在快顯<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>， <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>， <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>， <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>，和<xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty>屬性。 如需詳細資訊，請參閱[快顯放置行為](../../../../docs/framework/wpf/controls/popup-placement-behavior.md)。 當<xref:System.Windows.Controls.Primitives.Popup>會顯示在畫面上，它不會不重新定位本身如果其父代重新調整位置。  
  
<a name="CustomizingPopupPlacement"></a>   
### <a name="customizing-popup-placement"></a>自訂快顯位置  
 您可以自訂的放置<xref:System.Windows.Controls.Primitives.Popup>藉由指定的相對座標的一組控制項<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>想<xref:System.Windows.Controls.Primitives.Popup>才會出現。  
  
 若要自訂位置，設定<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>。 然後定義<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>委派，會傳回一組可能的定位點和 （依喜好設定順序） 的主座標軸的<xref:System.Windows.Controls.Primitives.Popup>。 顯示的最大一部分的點<xref:System.Windows.Controls.Primitives.Popup>自動選取。 如需範例，請參閱[指定自訂快顯位置](../../../../docs/framework/wpf/controls/how-to-specify-a-custom-popup-position.md)。  
  
<a name="PopupandtheVisualTree"></a>   
## <a name="popup-and-the-visual-tree"></a>快顯和視覺化樹狀結構  
 A<xref:System.Windows.Controls.Primitives.Popup>控制項沒有自己的視覺化樹狀結構，會改為傳回大小為 0 （零） 時<xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A>方法<xref:System.Windows.Controls.Primitives.Popup>呼叫。 不過，當您將<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A>屬性<xref:System.Windows.Controls.Primitives.Popup>至`true`，建立新的視窗有它自己的視覺化樹狀結構。 新視窗包含<xref:System.Windows.Controls.Primitives.Popup.Child%2A>內容的<xref:System.Windows.Controls.Primitives.Popup>。 新視窗的寬度和高度不可超過畫面寬度或高度的 75%。  
  
 <xref:System.Windows.Controls.Primitives.Popup>控制維護參考其<xref:System.Windows.Controls.Primitives.Popup.Child%2A>內容做為邏輯的子系。 當建立新的視窗，內容<xref:System.Windows.Controls.Primitives.Popup>變成視窗的視覺子項的邏輯子系，並且<xref:System.Windows.Controls.Primitives.Popup>。 相反地，<xref:System.Windows.Controls.Primitives.Popup>維持的邏輯父系其<xref:System.Windows.Controls.Primitives.Popup.Child%2A>內容。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Controls.Primitives.Popup>  
 <xref:System.Windows.Controls.Primitives.PopupPrimaryAxis>  
 <xref:System.Windows.Controls.Primitives.PlacementMode>  
 <xref:System.Windows.Controls.Primitives.CustomPopupPlacement>  
 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [HOW-TO 主題](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)
