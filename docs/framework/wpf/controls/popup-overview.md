---
title: 快顯功能表概觀
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
ms.openlocfilehash: 370970c80221e371db5a97303ef2650d14300b14
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102774"
---
# <a name="popup-overview"></a>快顯功能表概觀
<xref:System.Windows.Controls.Primitives.Popup>控制項可用來顯示不同的視窗以漂浮在目前的應用程式視窗相對於指定的項目或螢幕座標中的內容。 本主題將介紹<xref:System.Windows.Controls.Primitives.Popup>控制項，並提供其用法的相關資訊。  

<a name="What_Is_a_Popup_"></a>   
## <a name="what-is-a-popup"></a>什麼是快顯？  
 A<xref:System.Windows.Controls.Primitives.Popup>控制項會顯示在相對於項目或在螢幕上的點分隔視窗的內容。 當<xref:System.Windows.Controls.Primitives.Popup>是可見的<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A>屬性設定為`true`。  
  
> [!NOTE]
>  A<xref:System.Windows.Controls.Primitives.Popup>不會自動開啟當滑鼠指標移至其父物件時。 如果您想<xref:System.Windows.Controls.Primitives.Popup>若要自動開啟，請使用<xref:System.Windows.Controls.ToolTip>或<xref:System.Windows.Controls.ToolTipService>類別。 如需詳細資訊，請參閱 [ToolTip 概觀](tooltip-overview.md)。  
  
<a name="APopupExample"></a>   
## <a name="creating-a-popup"></a>建立快顯  
 下列範例示範如何定義<xref:System.Windows.Controls.Primitives.Popup>控制項的子項目<xref:System.Windows.Controls.Button>控制項。 因為<xref:System.Windows.Controls.Button>可以有只有一個子項目，此範例會針對文字<xref:System.Windows.Controls.Button>並<xref:System.Windows.Controls.Primitives.Popup>中的控制項<xref:System.Windows.Controls.StackPanel>。 內容<xref:System.Windows.Controls.Primitives.Popup>會出現在<xref:System.Windows.Controls.TextBlock>控制項，其中會漂浮在應用程式視窗上靠近相關的另一個視窗中顯示其文字<xref:System.Windows.Controls.Button>控制項。  
  
 [!code-xaml[PopupSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>   
## <a name="controls-that-implement-a-popup"></a>實作快顯的控制項  
 您可以建置<xref:System.Windows.Controls.Primitives.Popup>到其他控制項的控制項。 下列控制項會實作<xref:System.Windows.Controls.Primitives.Popup>適用於特定用途的控制項：  
  
-   <xref:System.Windows.Controls.ToolTip>。 如果您想要建立項目的工具提示，使用<xref:System.Windows.Controls.ToolTip>和<xref:System.Windows.Controls.ToolTipService>類別。 如需詳細資訊，請參閱 [ToolTip 概觀](tooltip-overview.md)。  
  
-   <xref:System.Windows.Controls.ContextMenu>。 如果您想要建立項目的內容功能表中，使用<xref:System.Windows.Controls.ContextMenu>控制項。 如需詳細資訊，請參閱 [ContextMenu 概觀](contextmenu-overview.md)。  
  
-   <xref:System.Windows.Controls.ComboBox>。 如果您想要建立具有可顯示或隱藏的使用下拉式清單方塊的選取項目控制項<xref:System.Windows.Controls.ComboBox>控制項。  
  
-   <xref:System.Windows.Controls.Expander>。 如果您想要建立顯示具有可摺疊區域的標頭的控制項，會顯示內容，請使用<xref:System.Windows.Controls.Expander>控制項。 如需詳細資訊，請參閱 [Expander 概觀](expander-overview.md)。  
  
<a name="PopupBehaviorandAppearance"></a>   
## <a name="popup-behavior-and-appearance"></a>快顯行為和外觀  
 <xref:System.Windows.Controls.Primitives.Popup>控制項提供可讓您自訂其行為和外觀的功能。 例如，您可以在其中設定開啟和關閉行為、 動畫、 不透明度和點陣圖效果，以及<xref:System.Windows.Controls.Primitives.Popup>大小和位置。  
  
<a name="OpenandCloseBehavior"></a>   
### <a name="open-and-close-behavior"></a>開啟和關閉行為  
 A<xref:System.Windows.Controls.Primitives.Popup>控制項會顯示其內容時<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A>屬性設定為`true`。 根據預設，<xref:System.Windows.Controls.Primitives.Popup>保持開啟，直到<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A>屬性設定為`false`。 不過，您可以變更預設行為，藉由設定<xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A>屬性設`false`。 當您將此屬性設定為`false`，則<xref:System.Windows.Controls.Primitives.Popup>內容視窗具有滑鼠擷取。 <xref:System.Windows.Controls.Primitives.Popup>失去滑鼠擷取，且視窗會關閉外部的滑鼠事件發生時<xref:System.Windows.Controls.Primitives.Popup>視窗。  
  
 <xref:System.Windows.Controls.Primitives.Popup.Opened>並<xref:System.Windows.Controls.Primitives.Popup.Closed>引發事件時<xref:System.Windows.Controls.Primitives.Popup>內容視窗已開啟還是關閉。  
  
<a name="Animation"></a>   
### <a name="animation"></a>動畫  
 <xref:System.Windows.Controls.Primitives.Popup>控制項有內建支援通常淡入和滑入之類的行為與相關聯的動畫。 您可以藉由設定開啟這些動畫<xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A>屬性設<xref:System.Windows.Controls.Primitives.PopupAnimation>列舉值。 針對<xref:System.Windows.Controls.Primitives.Popup>動畫可以正常運作，您必須設定<xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A>屬性設`true`。  
  
 您也可以套用之類的動畫<xref:System.Windows.Media.Animation.Storyboard>至<xref:System.Windows.Controls.Primitives.Popup>控制項。  
  
<a name="OpacityandBitmapEffects"></a>   
### <a name="opacity-and-bitmap-effects"></a>不透明度和點陣圖效果  
 <xref:System.Windows.UIElement.Opacity%2A>屬性<xref:System.Windows.Controls.Primitives.Popup>控制項有不會影響其內容。 根據預設，<xref:System.Windows.Controls.Primitives.Popup>是不透明的內容視窗。 若要建立透明<xref:System.Windows.Controls.Primitives.Popup>，將<xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A>屬性設`true`。  
  
 內容<xref:System.Windows.Controls.Primitives.Popup>不是繼承的點陣圖效果，例如<xref:System.Windows.Media.Effects.DropShadowBitmapEffect>，，直接設定在<xref:System.Windows.Controls.Primitives.Popup>控制項或其他任何元素的父視窗中。 要顯示的內容上的點陣圖效果<xref:System.Windows.Controls.Primitives.Popup>，您必須設定直接對其內容的點陣圖效果。 比方說，如果子系<xref:System.Windows.Controls.Primitives.Popup>是<xref:System.Windows.Controls.StackPanel>，在上設定點陣圖效果<xref:System.Windows.Controls.StackPanel>。  
  
<a name="PopupSize"></a>   
### <a name="popup-size"></a>快顯大小  
 根據預設，<xref:System.Windows.Controls.Primitives.Popup>其內容會自動調整大小。 因為自動調整時，可能隱藏部分點陣圖效果畫面區域中所定義的預設大小<xref:System.Windows.Controls.Primitives.Popup>內容不會提供足夠的空間，以顯示那些點陣圖效果。  
  
 <xref:System.Windows.Controls.Primitives.Popup> 內容也可能會遮蔽當您設定<xref:System.Windows.UIElement.RenderTransform%2A>的內容。 在此案例中，部分內容可能會隱藏如果已轉換的內容<xref:System.Windows.Controls.Primitives.Popup>超出原始區域<xref:System.Windows.Controls.Primitives.Popup>。 如果點陣圖效果或轉換需要更多空間，您可以定義周圍的邊界<xref:System.Windows.Controls.Primitives.Popup>以提供更多區域控制項的內容。  
  
<a name="DefiningPopupPosition"></a>   
## <a name="defining-the-popup-position"></a>定義快顯位置  
 您可以藉由設定定位快顯<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>， <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>， <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>， <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>，和<xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty>屬性。 如需詳細資訊，請參閱[快顯放置行為](popup-placement-behavior.md)。 當<xref:System.Windows.Controls.Primitives.Popup>會顯示在畫面上，它不會因為其父代重新調整位置。  
  
<a name="CustomizingPopupPlacement"></a>   
### <a name="customizing-popup-placement"></a>自訂快顯位置  
 您可以自訂的位置<xref:System.Windows.Controls.Primitives.Popup>控制項，藉由指定一組座標的相對<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>所在<xref:System.Windows.Controls.Primitives.Popup>才會出現。  
  
 若要自訂位置，請設定<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性設<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>。 然後定義<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>傳回一組可能的位置點和主要軸 （依偏好順序） 的委派<xref:System.Windows.Controls.Primitives.Popup>。 顯示的最大一部分的點<xref:System.Windows.Controls.Primitives.Popup>會自動選取。 如需範例，請參閱[指定自訂快顯位置](how-to-specify-a-custom-popup-position.md)。  
  
<a name="PopupandtheVisualTree"></a>   
## <a name="popup-and-the-visual-tree"></a>快顯和視覺化樹狀結構  
 A<xref:System.Windows.Controls.Primitives.Popup>控制項沒有自己的視覺化樹狀結構; 相反地會傳回大小為 0 （零） 時，<xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A>方法<xref:System.Windows.Controls.Primitives.Popup>呼叫。 但是，當您設定<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A>的屬性<xref:System.Windows.Controls.Primitives.Popup>到`true`，建立新的視窗具有自己視覺化樹狀結構。 新的視窗會包含<xref:System.Windows.Controls.Primitives.Popup.Child%2A>內容的<xref:System.Windows.Controls.Primitives.Popup>。 新視窗的寬度和高度不可超過畫面寬度或高度的 75%。  
  
 <xref:System.Windows.Controls.Primitives.Popup>控制項會維護指向其<xref:System.Windows.Controls.Primitives.Popup.Child%2A>內容做為邏輯的子系。 當建立新的視窗的內容<xref:System.Windows.Controls.Primitives.Popup>變成視覺化視窗的子系，並維持的邏輯子系<xref:System.Windows.Controls.Primitives.Popup>。 相反地，<xref:System.Windows.Controls.Primitives.Popup>保持邏輯父代及其<xref:System.Windows.Controls.Primitives.Popup.Child%2A>內容。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.Primitives.Popup>
- <xref:System.Windows.Controls.Primitives.PopupPrimaryAxis>
- <xref:System.Windows.Controls.Primitives.PlacementMode>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacement>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [HOW TO 主題](popup-how-to-topics.md)
- [HOW TO 主題](tooltip-how-to-topics.md)
