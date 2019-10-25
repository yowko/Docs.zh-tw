---
title: 快顯功能表放置行為
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: ca984aa724cf3f076d6073aa8b8179abfb91d26c
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "69951725"
---
# <a name="popup-placement-behavior"></a>快顯功能表放置行為
@No__t_0 控制項會在應用程式浮動的另一個視窗中顯示內容。 您可以使用 [<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>]、[<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>]、[<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>]、[<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>] 和 [<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>] 屬性，指定 <xref:System.Windows.Controls.Primitives.Popup> 相對於控制項、滑鼠或畫面的位置。  這些屬性會一起使用，讓您有彈性地指定 <xref:System.Windows.Controls.Primitives.Popup> 的位置。  
  
> [!NOTE]
> @No__t_0 和 <xref:System.Windows.Controls.ContextMenu> 類別也會定義這五個屬性，並以類似的方式運作。  

<a name="Positioning"></a>   
## <a name="positioning-the-popup"></a>設定快顯位置  
 @No__t_0 的位置可以相對於 <xref:System.Windows.UIElement> 或整個螢幕。  下列範例會建立四個相對於 <xref:System.Windows.UIElement> 的 <xref:System.Windows.Controls.Primitives.Popup> 控制項，在此案例中為影像。 所有的 <xref:System.Windows.Controls.Primitives.Popup> 控制項都會將 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 屬性設定為 `image1`，但每個 <xref:System.Windows.Controls.Primitives.Popup> 的位置屬性都有不同的值。  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 下圖顯示影像和 <xref:System.Windows.Controls.Primitives.Popup> 控制項  
  
 ![搭配四個快顯控制項的影像](./media/popup-placement-behavior/popup-placement-intro.png "具有四個快顯視窗的影像")    
  
 這個簡單的範例示範如何設定 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 屬性，但是藉由使用 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 屬性，您可以更充分掌控 <xref:System.Windows.Controls.Primitives.Popup> 所在的位置。  
  
<a name="Definitions"></a>   
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>詞彙定義︰快顯剖析  
 下列詞彙有助於瞭解 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 屬性如何與彼此和 <xref:System.Windows.Controls.Primitives.Popup> 相互關聯：  
  
- 目標物件  
  
- 目標區域  
  
- 目標原點  
  
- 快顯對齊點  
  
 這些詞彙提供一個便利的方式來參考 <xref:System.Windows.Controls.Primitives.Popup> 的各個層面，以及與它相關聯的控制項。  
  
### <a name="target-object"></a>目標物件  
 *目標物件*是與 <xref:System.Windows.Controls.Primitives.Popup> 相關聯的元素。 如果已設定 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 屬性，它會指定目標物件。  如果未設定 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>，且 <xref:System.Windows.Controls.Primitives.Popup> 具有父系，則父系會是目標物件。  如果沒有 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 值，而且沒有父代，則沒有目標物件，且 <xref:System.Windows.Controls.Primitives.Popup> 的位置相對於螢幕。  
  
 下列範例會建立 <xref:System.Windows.Controls.Canvas> 子系的 <xref:System.Windows.Controls.Primitives.Popup>。  此範例不會設定 <xref:System.Windows.Controls.Primitives.Popup> 上的 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 屬性。 @No__t_0 的預設值為 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>，因此 <xref:System.Windows.Controls.Primitives.Popup> 會出現在 <xref:System.Windows.Controls.Canvas> 之下。  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 下圖顯示 <xref:System.Windows.Controls.Primitives.Popup> 相對於 <xref:System.Windows.Controls.Canvas> 的位置。  
  
 ![沒有 PlacementTarget 的快顯控制項](./media/popup-placement-behavior/popup-placement-no-placement-target.png "沒有 System.windows.controls.primitives.popup.placementtarget 的快捷方式。")  

 下列範例會建立 <xref:System.Windows.Controls.Canvas> 子系的 <xref:System.Windows.Controls.Primitives.Popup>，但這次 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 設定為 `ellipse1`，因此快顯視窗會出現在 <xref:System.Windows.Shapes.Ellipse> 之下。  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 下圖顯示 <xref:System.Windows.Controls.Primitives.Popup> 相對於 <xref:System.Windows.Shapes.Ellipse> 的位置。  
  
 ![相對於橢圓形置放的快顯](./media/popup-placement-behavior/popup-placement-with-placement-target.png "具有 PlacementTarget 的快顯")    
  
> [!NOTE]
> 針對 <xref:System.Windows.Controls.ToolTip>，<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 的預設值為 <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>。  針對 <xref:System.Windows.Controls.ContextMenu>，<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 的預設值為 <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>。 稍後在＜屬性如何一起運作＞中會說明這些值。  
  
### <a name="target-area"></a>目標區域  
 [*目標] 區域*是螢幕上 <xref:System.Windows.Controls.Primitives.Popup> 相對的區域。 在先前的範例中，<xref:System.Windows.Controls.Primitives.Popup> 與目標物件的界限對齊，但在某些情況下，即使 <xref:System.Windows.Controls.Primitives.Popup> 具有目標物件，<xref:System.Windows.Controls.Primitives.Popup> 還是會對齊其他界限。  如果已設定 [<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>] 屬性，則目的地區域會與目標物件的界限不同。  
  
 下列範例會建立兩個 <xref:System.Windows.Controls.Canvas> 物件，每一個都包含一個 <xref:System.Windows.Shapes.Rectangle> 和一個 <xref:System.Windows.Controls.Primitives.Popup>。  在這兩種情況下，<xref:System.Windows.Controls.Primitives.Popup> 的目標物件都是 <xref:System.Windows.Controls.Canvas>。 第一個 <xref:System.Windows.Controls.Canvas> 中的 <xref:System.Windows.Controls.Primitives.Popup> 已設定 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>，其 <xref:System.Windows.Rect.X%2A>、<xref:System.Windows.Rect.Y%2A>、<xref:System.Windows.Rect.Width%2A> 和 <xref:System.Windows.Rect.Height%2A> 屬性分別設定為50、50、50和100。 第二個 <xref:System.Windows.Controls.Canvas> 中的 <xref:System.Windows.Controls.Primitives.Popup> 沒有 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 設定。  因此，第一個 <xref:System.Windows.Controls.Primitives.Popup> 位於 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 下方，而第二個 <xref:System.Windows.Controls.Primitives.Popup> 位於 <xref:System.Windows.Controls.Canvas> 之下。 每個 <xref:System.Windows.Controls.Canvas> 也包含與第一個 <xref:System.Windows.Controls.Primitives.Popup> 的 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 具有相同界限的 <xref:System.Windows.Shapes.Rectangle>。  請注意，<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 不會在應用程式中建立可見的元素;此範例會建立代表 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 的 <xref:System.Windows.Shapes.Rectangle>。  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 下圖顯示上述範例的結果。  
  
 ![具有和沒有 PlacementRectangle 的快顯](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "具有和但不含 System.windows.controls.primitives.popup.placementrectangle 的快顯。")  

### <a name="target-origin-and-popup-alignment-point"></a>目標原點和快顯對齊點  
 「目標原點」和「快顯對齊點」分別是目標區域和快顯上的參考點，用來進行定位。 您可以使用 <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 屬性，從目的地區域中位移快捷方式。  @No__t_0 和 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 是相對於目標原點和快顯對齊點。 [@No__t_0] 屬性的值會決定目標原點和快顯對齊點的所在位置。  
  
 下列範例會建立 <xref:System.Windows.Controls.Primitives.Popup>，並將 <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 屬性設定為20。  @No__t_0 屬性會設定為 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> （預設值），因此目標原點是目的地區域的左下角，而快顯對齊點則是 <xref:System.Windows.Controls.Primitives.Popup> 的左上角。  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 下圖顯示上述範例的結果。  
  
 ![具有目標原點和對齊點的快顯位置](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "具有 System.windows.controls.primitives.popup.horizontaloffset 和 VerticalOffset 的 Popup。")    
  
<a name="How"></a>   
## <a name="how-the-properties-work-together"></a>屬性如何一起運作  
 @No__t_0、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 的值必須一起考慮，才能找出正確的目的地區域、目標原點和快顯對齊點。  例如，如果 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 的值為 <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>、沒有目標物件，則會忽略 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>，而目的地區域則是滑鼠指標的範圍。 另一方面，如果 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>，則 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父代會決定目標物件，而 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 會決定目的地區域。  
  
 下表描述 [目標物件]、[目的地區域]、[目標原點] 和 [快顯對齊點]，並指出每個 <xref:System.Windows.Controls.Primitives.PlacementMode> 列舉值是否都使用 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  
  
|PlacementMode|目標物件|目標區域|目標原點|快顯對齊點|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|不適用。 已忽略 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>。|畫面，如果已設定，則為 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  @No__t_0 相對於螢幕。|目標區域的左上角。|@No__t_0 的左上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|不適用。 已忽略 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>。|畫面，如果已設定，則為 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  @No__t_0 相對於螢幕。|目標區域的左上角。|@No__t_0 的左上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父系。|目標物件，如果已設定，則為 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  @No__t_0 是相對於目標物件。|目標區域的左下角。|@No__t_0 的左上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父系。|目標物件，如果已設定，則為 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  @No__t_0 是相對於目標物件。|目標區域的中央。|@No__t_0 的中心。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父系。|目標物件，如果已設定，則為 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  @No__t_0 是相對於目標物件。|由 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> 定義。|由 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> 定義。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父系。|目標物件，如果已設定，則為 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  @No__t_0 是相對於目標物件。|目標區域的左上角。|@No__t_0 的右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|不適用。 已忽略 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>。|滑鼠指標的範圍。 已忽略 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。|目標區域的左下角。|@No__t_0 的左上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|不適用。 已忽略 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>。|滑鼠指標的範圍。 已忽略 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。|目標區域的左上角。|@No__t_0 的左上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父系。|目標物件，如果已設定，則為 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  @No__t_0 是相對於目標物件。|目標區域的左上角。|@No__t_0 的左上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父系。|目標物件，如果已設定，則為 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  @No__t_0 是相對於目標物件。|目標區域的左上角。|@No__t_0 的左上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父系。|目標物件，如果已設定，則為 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  @No__t_0 是相對於目標物件。|目標區域的右上角。|@No__t_0 的左上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父系。|目標物件，如果已設定，則為 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  @No__t_0 是相對於目標物件。|目標區域的左上角。|@No__t_0 的左下角。|  
  
 下圖顯示每個 <xref:System.Windows.Controls.Primitives.PlacementMode> 值的 <xref:System.Windows.Controls.Primitives.Popup>、目的地區域、目標原點和快顯對齊點。 在每個圖中，目的地區域都是黃色，而 <xref:System.Windows.Controls.Primitives.Popup> 是藍色。  
  
 ![具有 Absolute 或 AbsolutePoint 位置的快顯](./media/popup-placement-behavior/popup-placement-absolute.png "位置為絕對或 AbsolutePoint。")    
  
 ![具有 Bottom 位置的快顯](./media/popup-placement-behavior/popup-placement-bottom.png "放置為底端。")   
  
 ![具有 Center 位置的快顯](./media/popup-placement-behavior/popup-placement-center.png "位置為 Center。")    
  
 ![具有 Left 位置的快顯](./media/popup-placement-behavior/popup-placement-left.png "位置為 Left。")   
  
 ![具有 Mouse 位置的快顯](./media/popup-placement-behavior/popup-placement-mouse.png "放置是滑鼠。")  
  
 ![具有 MousePoint 位置的快顯](./media/popup-placement-behavior/popup-placement-mousepoint.png "位置為 MousePoint。")  
  
 ![具有 Relative 或 RelativePoint 位置的快顯](./media/popup-placement-behavior/popup-placement-relative.png "位置為相對或 RelativePoint。")    
  
 ![具有 Right 位置的快顯](./media/popup-placement-behavior/popup-placement-right.png "位置正確。")    
  
 ![具有 Top 位置的快顯](./media/popup-placement-behavior/popup-placement-top.png "Placement 是 Top。")    
  
<a name="When"></a>   
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>當快顯遇到畫面邊緣時  
 基於安全性理由，螢幕邊緣無法隱藏 <xref:System.Windows.Controls.Primitives.Popup>。 當 <xref:System.Windows.Controls.Primitives.Popup> 遇到螢幕邊緣時，就會發生下列三種情況之一：  
  
- 快顯視窗邊緣的 realigns 會遮蔽 <xref:System.Windows.Controls.Primitives.Popup>。  
  
- 快顯會使用不同的快顯對齊點。  
  
- 快顯會使用不同的目標原點和快顯對齊點。  
  
 本節稍後會進一步說明這些選項。  
  
 當遇到螢幕邊緣時，<xref:System.Windows.Controls.Primitives.Popup> 的行為，取決於 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 屬性的值和快顯所遇到的畫面邊緣。 下表摘要說明 <xref:System.Windows.Controls.Primitives.Popup> 遇到每個 <xref:System.Windows.Controls.Primitives.PlacementMode> 值的螢幕邊緣時的行為。  
  
|PlacementMode|上邊緣|下邊緣|左邊緣|右邊緣|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|對齊上邊緣。|對齊下邊緣。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|對齊上邊緣。|快顯對齊點會變更為 <xref:System.Windows.Controls.Primitives.Popup> 的左下角。|對齊左邊緣。|快顯對齊點會變更為 <xref:System.Windows.Controls.Primitives.Popup> 的右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|對齊上邊緣。|目標原點會變更為目的地區域的左上角，而快顯對齊點會變更為 <xref:System.Windows.Controls.Primitives.Popup> 的左下角。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|對齊上邊緣。|對齊下邊緣。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|對齊上邊緣。|對齊下邊緣。|目標原點會變更為目的地區域的右上角，而快顯對齊點會變更為 <xref:System.Windows.Controls.Primitives.Popup> 的左上角。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|對齊上邊緣。|目標原點會變更為目的地區域的左上角（滑鼠指標的界限），而快顯對齊點會變更為 <xref:System.Windows.Controls.Primitives.Popup> 的左下角。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|對齊上邊緣。|快顯對齊點會變更為 <xref:System.Windows.Controls.Primitives.Popup> 的左下角。|對齊左邊緣。|快顯對齊點會變更至快顯的右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|對齊上邊緣。|對齊下邊緣。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|對齊上邊緣。|快顯對齊點會變更為 <xref:System.Windows.Controls.Primitives.Popup> 的左下角。|對齊左邊緣。|快顯對齊點會變更至快顯的右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|對齊上邊緣。|對齊下邊緣。|對齊左邊緣。|目標原點會變更為目的地區域的左上角，而快顯對齊點會變更為 <xref:System.Windows.Controls.Primitives.Popup> 的右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|目標原點會變更為目的地區域的左下角，而快顯對齊點會變更為 <xref:System.Windows.Controls.Primitives.Popup> 的左上角。 實際上，這與 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 時相同。|對齊下邊緣。|對齊左邊緣。|對齊右邊緣。|  
  
### <a name="aligning-to-the-screen-edge"></a>對齊畫面邊緣  
 @No__t_0 可以藉由重新置放來與畫面邊緣對齊，讓整個 <xref:System.Windows.Controls.Primitives.Popup> 顯示在螢幕上。  發生這種情況時，目標原點和快顯對齊點之間的距離可能會與 <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 的值不同。 當 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>、<xref:System.Windows.Controls.Primitives.PlacementMode.Center> 或 <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> 時，<xref:System.Windows.Controls.Primitives.Popup> 會將其本身對應到每個螢幕邊緣。  例如，假設 <xref:System.Windows.Controls.Primitives.Popup> 的 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 設定為 <xref:System.Windows.Controls.Primitives.PlacementMode.Relative>，<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 設定為100。  如果畫面的下邊緣隱藏了全部或部分的 <xref:System.Windows.Controls.Primitives.Popup>，<xref:System.Windows.Controls.Primitives.Popup> 會沿著畫面的下邊緣自動重新置放，而目標原點和快顯對齊點之間的垂直距離則小於100。 下圖示範這種情況。  
  
 ![與畫面邊緣對齊的快顯](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "快顯與畫面邊緣對齊。")    
  
### <a name="changing-the-popup-alignment-point"></a>變更快顯對齊點  
 如果 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 是 <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>、<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint> 或 <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>，快顯對齊點會在快顯視窗遇到底部或右邊畫面邊緣時變更。  
  
 下圖顯示當底部畫面邊緣隱藏全部或部分的 <xref:System.Windows.Controls.Primitives.Popup> 時，快顯對齊點是 <xref:System.Windows.Controls.Primitives.Popup> 的左下角。  
  
 ![因畫面下邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "Popup 會遇到畫面的下邊緣，並變更快顯對齊點。")  

 下圖顯示當右螢幕邊緣隱藏了 <xref:System.Windows.Controls.Primitives.Popup> 時，快顯對齊點是 <xref:System.Windows.Controls.Primitives.Popup> 的右上角。  
  
 ![因畫面邊緣而導致的新快顯對齊點](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "Popup 會遇到畫面的右邊緣，並變更快顯對齊點。")    
  
 如果 <xref:System.Windows.Controls.Primitives.Popup> 遇到底部和右側畫面邊緣，則快顯對齊點是 <xref:System.Windows.Controls.Primitives.Popup> 的右下角。  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>變更目標原點和快顯對齊點  
 當 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>、<xref:System.Windows.Controls.Primitives.PlacementMode.Left>、<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>、<xref:System.Windows.Controls.Primitives.PlacementMode.Right> 或 <xref:System.Windows.Controls.Primitives.PlacementMode.Top> 時，如果遇到特定的螢幕邊緣，目標原點和快顯對齊點就會變更。  造成位置變更的螢幕邊緣取決於 <xref:System.Windows.Controls.Primitives.PlacementMode> 值。  
  
 下圖顯示當 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> 而且 <xref:System.Windows.Controls.Primitives.Popup> 遇到底部畫面邊緣時，目標原點是目的地區域的左上角，而快顯對齊點則是 <xref:System.Windows.Controls.Primitives.Popup> 的左下角。  
  
 ![因畫面下邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "放置為底部，而快顯視窗則會遇到畫面的下邊緣。")    
  
 下圖顯示當 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Left> 而且 <xref:System.Windows.Controls.Primitives.Popup> 遇到左畫面邊緣時，目標原點是目的地區域的右上角，而快顯對齊點則是 <xref:System.Windows.Controls.Primitives.Popup> 的左上角。  
  
 ![因畫面左邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "[位置] 是 Left，而快顯視窗則會遇到螢幕的左邊緣。")  
  
 下圖顯示當 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Right> 而且 <xref:System.Windows.Controls.Primitives.Popup> 遇到正確的畫面邊緣時，目標原點是目的地區域的左上角，而快顯對齊點則是 <xref:System.Windows.Controls.Primitives.Popup> 的右上角。  
  
 ![因畫面右邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "Placement 是 Right，而 popup 會遇到畫面的右邊緣。")  

 下圖顯示當 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Top> 而且 <xref:System.Windows.Controls.Primitives.Popup> 遇到頂端畫面邊緣時，目標原點是目的地區域的左下角，而快顯對齊點則是 <xref:System.Windows.Controls.Primitives.Popup> 的左上角。  
  
 ![因畫面上邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "Placement 是 Top，而快顯視窗則會遇到畫面的上邊緣。")  
  
 下圖顯示當 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> 而且 <xref:System.Windows.Controls.Primitives.Popup> 遇到底部畫面邊緣時，目標原點是目的地區域的左上角（滑鼠指標的界限），而快顯對齊點則是左下方<xref:System.Windows.Controls.Primitives.Popup> 的角落。  
  
 ![因滑鼠靠近畫面邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "放置是滑鼠，而快顯視窗會遇到畫面的下邊緣。")    
  
### <a name="customizing-popup-placement"></a>自訂快顯位置  
 您可以將 [<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>] 屬性設定為 [<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>]，以自訂目標原點和快顯對齊點。 然後定義 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> 委派，以傳回 <xref:System.Windows.Controls.Primitives.Popup> 的一組可能的放置點和主要軸（依照喜好設定的順序）。 已選取顯示 <xref:System.Windows.Controls.Primitives.Popup> 最大部分的點。  如果畫面的邊緣隱藏 <xref:System.Windows.Controls.Primitives.Popup>，則會自動調整 <xref:System.Windows.Controls.Primitives.Popup> 的位置。 如需範例，請參閱[指定自訂快顯位置](how-to-specify-a-custom-popup-position.md)。  
  
## <a name="see-also"></a>請參閱

- [快顯位置範例](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
