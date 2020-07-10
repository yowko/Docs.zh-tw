---
title: 快顯功能表放置行為
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: 1c377e62ffd334638031baee4d4831ac5a31acf3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243254"
---
# <a name="popup-placement-behavior"></a>快顯功能表放置行為
<xref:System.Windows.Controls.Primitives.Popup>控制項會在應用程式浮動的另一個視窗中顯示內容。 您可以 <xref:System.Windows.Controls.Primitives.Popup> 使用、、、 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 屬性，指定相對於控制項、滑鼠或畫面的位置。  這些屬性會一起使用，讓您有彈性地指定的位置 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
> [!NOTE]
> <xref:System.Windows.Controls.ToolTip>和 <xref:System.Windows.Controls.ContextMenu> 類別也會定義這五個屬性，並以類似的方式運作。  

<a name="Positioning"></a>
## <a name="positioning-the-popup"></a>設定快顯位置  
 的位置 <xref:System.Windows.Controls.Primitives.Popup> 可以相對於 <xref:System.Windows.UIElement> 或整個螢幕。  下列範例會建立四個 <xref:System.Windows.Controls.Primitives.Popup> 相對於的控制項 <xref:System.Windows.UIElement> （在此案例中為影像）。 所有 <xref:System.Windows.Controls.Primitives.Popup> 控制項都將 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 屬性設定為 `image1` ，但每個都 <xref:System.Windows.Controls.Primitives.Popup> 有不同的位置屬性值。  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 下圖顯示影像和 <xref:System.Windows.Controls.Primitives.Popup> 控制項  
  
 ![搭配四個快顯控制項的影像](./media/popup-placement-behavior/popup-placement-intro.png "具有四個快顯視窗的影像")
  
 這個簡單的範例示範如何設定 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 屬性，但藉由使用 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 、 <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 屬性，您可以更充分掌控所在的位置 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
<a name="Definitions"></a>
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>詞彙定義︰快顯剖析  
 下列詞彙有助於瞭解 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 、、、和屬性如何與彼此 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 和相互 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 關聯 <xref:System.Windows.Controls.Primitives.Popup> ：  
  
- 目標物件  
  
- 目標區域  
  
- 目標原點  
  
- 快顯對齊點  
  
 這些詞彙提供一個便利的方式來參考的各個層面 <xref:System.Windows.Controls.Primitives.Popup> ，以及與它相關聯的控制項。  
  
### <a name="target-object"></a>目標物件  
 *目標物件*是 <xref:System.Windows.Controls.Primitives.Popup> 與相關聯的元素。 如果 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 已設定屬性，它會指定目標物件。  如果 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 未設定，且 <xref:System.Windows.Controls.Primitives.Popup> 具有父系，父系就是目標物件。  如果沒有任何 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 值，而且沒有父代，則不會有目標物件，且的 <xref:System.Windows.Controls.Primitives.Popup> 位置會相對於螢幕。  
  
 下列範例 <xref:System.Windows.Controls.Primitives.Popup> 會建立，它是的子系 <xref:System.Windows.Controls.Canvas> 。  此範例不會 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 在上設定屬性 <xref:System.Windows.Controls.Primitives.Popup> 。 的預設值 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 為 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType> ，因此 <xref:System.Windows.Controls.Primitives.Popup> 會出現在下方 <xref:System.Windows.Controls.Canvas> 。  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 下圖顯示 <xref:System.Windows.Controls.Primitives.Popup> 相對於的位置 <xref:System.Windows.Controls.Canvas> 。  
  
 ![沒有 PlacementTarget 的快顯控制項](./media/popup-placement-behavior/popup-placement-no-placement-target.png "沒有 System.windows.controls.primitives.popup.placementtarget 的快捷方式。")  

 下列範例會建立， <xref:System.Windows.Controls.Primitives.Popup> 它是的子系 <xref:System.Windows.Controls.Canvas> ，但這次 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 會將設定為 `ellipse1` ，因此快顯視窗會出現在下方 <xref:System.Windows.Shapes.Ellipse> 。  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 下圖顯示 <xref:System.Windows.Controls.Primitives.Popup> 相對於的位置 <xref:System.Windows.Shapes.Ellipse> 。  
  
 ![相對於橢圓形置放的快顯](./media/popup-placement-behavior/popup-placement-with-placement-target.png "具有 PlacementTarget 的快顯")
  
> [!NOTE]
> 若為 <xref:System.Windows.Controls.ToolTip> ，的預設值 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 為 <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> 。  若為 <xref:System.Windows.Controls.ContextMenu> ，的預設值 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 為 <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint> 。 稍後在＜屬性如何一起運作＞中會說明這些值。  
  
### <a name="target-area"></a>目標區域  
 [*目的地區域*] 是螢幕上相對於的區域 <xref:System.Windows.Controls.Primitives.Popup> 。 在先前的範例中， <xref:System.Windows.Controls.Primitives.Popup> 會與目標物件的界限對齊，但在某些情況下， <xref:System.Windows.Controls.Primitives.Popup> 即使具有目標物件，也會對齊其他界限 <xref:System.Windows.Controls.Primitives.Popup> 。  如果 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 設定了屬性，則目的地區域會與目標物件的界限不同。  
  
 下列範例會建立兩個 <xref:System.Windows.Controls.Canvas> 物件，其中每一個都包含 <xref:System.Windows.Shapes.Rectangle> 和 <xref:System.Windows.Controls.Primitives.Popup> 。  在這兩種情況下，的目標物件 <xref:System.Windows.Controls.Primitives.Popup> 是 <xref:System.Windows.Controls.Canvas> 。 <xref:System.Windows.Controls.Primitives.Popup>第一個中的 <xref:System.Windows.Controls.Canvas> 具有 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 集合，其 <xref:System.Windows.Rect.X%2A> 、 <xref:System.Windows.Rect.Y%2A> 、 <xref:System.Windows.Rect.Width%2A> 和 <xref:System.Windows.Rect.Height%2A> 屬性分別設定為50、50、50和100。 <xref:System.Windows.Controls.Primitives.Popup>第二個中的沒有 <xref:System.Windows.Controls.Canvas> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 集合。  因此，第一個位置位於 <xref:System.Windows.Controls.Primitives.Popup> 底下， <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 第二個位于 <xref:System.Windows.Controls.Primitives.Popup> 底下 <xref:System.Windows.Controls.Canvas> 。 每個 <xref:System.Windows.Controls.Canvas> 也 <xref:System.Windows.Shapes.Rectangle> 會包含具有與第一個之相同界限的 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> <xref:System.Windows.Controls.Primitives.Popup> 。  請注意，不 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 會在應用程式中建立可見的元素; 此範例會建立 <xref:System.Windows.Shapes.Rectangle> 來表示 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 。  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 下圖顯示上述範例的結果。  
  
 ![具有和沒有 PlacementRectangle 的快顯](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "具有和但不含 System.windows.controls.primitives.popup.placementrectangle 的快顯。")  

### <a name="target-origin-and-popup-alignment-point"></a>目標原點和快顯對齊點  
 「目標原點」** 和「快顯對齊點」** 分別是目標區域和快顯上的參考點，用來進行定位。 您可以使用 <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 屬性，從目的地區域中位移快捷方式。  <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>和 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 會相對於目標原點和快顯對齊點。 屬性的值 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 會決定目標原點和快顯對齊點的所在位置。  
  
 下列範例會建立 <xref:System.Windows.Controls.Primitives.Popup> ，並將 <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 和屬性設定 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 為20。  <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性會設定為 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> (預設) ，因此目標原點是目的地區域的左下角，而快顯對齊點則是的左上角 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 下圖顯示上述範例的結果。  
  
 ![具有目標原點和對齊點的快顯位置](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "具有 System.windows.controls.primitives.popup.horizontaloffset 和 VerticalOffset 的 Popup。")
  
<a name="How"></a>
## <a name="how-the-properties-work-together"></a>屬性如何一起運作  
 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>、和的值 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 必須一起考慮，才能找出正確的目的地區域、目標原點和快顯對齊點。  例如，如果的值 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 是 <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> ，則沒有目標物件， <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 會忽略，而目的地區域則是滑鼠指標的範圍。 另一方面，如果 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 是 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> ， <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父代會決定目標物件並 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 決定目的地區域。  
  
 下表描述 [目標物件]、[目的地區域]、[目標原點] 和 [快顯對齊點]，並指出是否 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 要將和用於每個 <xref:System.Windows.Controls.Primitives.PlacementMode> 列舉值。  
  
|PlacementMode|目標物件|目標區域|目標原點|快顯對齊點|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|不適用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 會被忽略。|畫面， <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 如果已設定，則為。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>相對於螢幕。|目標區域的左上角。|的左上角 <xref:System.Windows.Controls.Primitives.Popup> 。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|不適用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 會被忽略。|畫面， <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 如果已設定，則為。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>相對於螢幕。|目標區域的左上角。|的左上角 <xref:System.Windows.Controls.Primitives.Popup> 。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父系。|目標物件; <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 如果已設定，則為。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件。|目標區域的左下角。|的左上角 <xref:System.Windows.Controls.Primitives.Popup> 。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父系。|目標物件; <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 如果已設定，則為。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件。|目標區域的中央。|的中央 <xref:System.Windows.Controls.Primitives.Popup> 。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父系。|目標物件; <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 如果已設定，則為。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件。|由定義 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> 。|由定義 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> 。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父系。|目標物件; <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 如果已設定，則為。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件。|目標區域的左上角。|的右上角 <xref:System.Windows.Controls.Primitives.Popup> 。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|不適用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 會被忽略。|滑鼠指標的範圍。 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 會被忽略。|目標區域的左下角。|的左上角 <xref:System.Windows.Controls.Primitives.Popup> 。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|不適用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 會被忽略。|滑鼠指標的範圍。 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 會被忽略。|目標區域的左上角。|的左上角 <xref:System.Windows.Controls.Primitives.Popup> 。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父系。|目標物件; <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 如果已設定，則為。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件。|目標區域的左上角。|的左上角 <xref:System.Windows.Controls.Primitives.Popup> 。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父系。|目標物件; <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 如果已設定，則為。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件。|目標區域的左上角。|的左上角 <xref:System.Windows.Controls.Primitives.Popup> 。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父系。|目標物件; <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 如果已設定，則為。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件。|目標區域的右上角。|的左上角 <xref:System.Windows.Controls.Primitives.Popup> 。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父系。|目標物件; <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 如果已設定，則為。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件。|目標區域的左上角。|的左下角 <xref:System.Windows.Controls.Primitives.Popup> 。|  
  
 下圖顯示 <xref:System.Windows.Controls.Primitives.Popup> 每個值的、目的地區域、目標原點和快顯對齊點 <xref:System.Windows.Controls.Primitives.PlacementMode> 。 在每個圖中，目的地區域都是黃色，而 <xref:System.Windows.Controls.Primitives.Popup> 是藍色。  
  
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
 基於安全性理由， <xref:System.Windows.Controls.Primitives.Popup> 畫面的邊緣無法隱藏。 當遇到螢幕邊緣時，就會發生下列三種情況之一 <xref:System.Windows.Controls.Primitives.Popup> ：  
  
- 快顯視窗會沿著會遮蔽的螢幕邊緣 realigns 本身 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
- 快顯會使用不同的快顯對齊點。  
  
- 快顯會使用不同的目標原點和快顯對齊點。  
  
 本節稍後會進一步說明這些選項。  
  
 <xref:System.Windows.Controls.Primitives.Popup>當它遇到螢幕邊緣時的行為，取決於屬性的值和快顯 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 所遇到的畫面邊緣。 下表摘要說明 <xref:System.Windows.Controls.Primitives.Popup> 遇到每個值的螢幕邊緣時的行為 <xref:System.Windows.Controls.Primitives.PlacementMode> 。  
  
|PlacementMode|上邊緣|下邊緣|左邊緣|右邊緣|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|對齊上邊緣。|對齊下邊緣。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|對齊上邊緣。|快顯對齊點會變更為的左下角 <xref:System.Windows.Controls.Primitives.Popup> 。|對齊左邊緣。|快顯對齊點會變更為的右上角 <xref:System.Windows.Controls.Primitives.Popup> 。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|對齊上邊緣。|目標原點會變更為目的地區域的左上角，而快顯對齊點會變更為的左下角 <xref:System.Windows.Controls.Primitives.Popup> 。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|對齊上邊緣。|對齊下邊緣。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|對齊上邊緣。|對齊下邊緣。|目標原點會變更為目的地區域的右上角，而快顯對齊點會變更為的左上角 <xref:System.Windows.Controls.Primitives.Popup> 。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|對齊上邊緣。|目標原點會變更為目的地區域的左上角 (滑鼠指標的範圍) 而快顯對齊點則會變更為的左下角 <xref:System.Windows.Controls.Primitives.Popup> 。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|對齊上邊緣。|快顯對齊點會變更為的左下角 <xref:System.Windows.Controls.Primitives.Popup> 。|對齊左邊緣。|快顯對齊點會變更至快顯的右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|對齊上邊緣。|對齊下邊緣。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|對齊上邊緣。|快顯對齊點會變更為的左下角 <xref:System.Windows.Controls.Primitives.Popup> 。|對齊左邊緣。|快顯對齊點會變更至快顯的右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|對齊上邊緣。|對齊下邊緣。|對齊左邊緣。|目標原點會變更為目的地區域的左上角，而快顯對齊點會變更為的右上角 <xref:System.Windows.Controls.Primitives.Popup> 。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|目標原點會變更為目的地區域的左下角，而快顯對齊點會變更為的左上角 <xref:System.Windows.Controls.Primitives.Popup> 。 實際上，這與為時相同 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> 。|對齊下邊緣。|對齊左邊緣。|對齊右邊緣。|  
  
### <a name="aligning-to-the-screen-edge"></a>對齊畫面邊緣  
 <xref:System.Windows.Controls.Primitives.Popup>可以藉由重新置放來對齊畫面的邊緣，讓整個 <xref:System.Windows.Controls.Primitives.Popup> 畫面顯示在螢幕上。  發生這種情況時，目標原點和快顯對齊點之間的距離可能會與和的值不同 <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 。 當 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 為 <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute> 、 <xref:System.Windows.Controls.Primitives.PlacementMode.Center> 或時 <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> ，會將 <xref:System.Windows.Controls.Primitives.Popup> 其本身對齊每個螢幕邊緣。  例如，假設 a <xref:System.Windows.Controls.Primitives.Popup> 已 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 將設為 <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> ，並 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 將設定為100。  如果畫面的下邊緣隱藏了的全部或部分 <xref:System.Windows.Controls.Primitives.Popup> ， <xref:System.Windows.Controls.Primitives.Popup> 會將其本身沿著畫面的下邊緣重新置放，而目標原點和快顯對齊點之間的垂直距離則小於100。 下圖示範這種情況。  
  
 ![與畫面邊緣對齊的快顯](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "快顯與畫面邊緣對齊。")
  
### <a name="changing-the-popup-alignment-point"></a>變更快顯對齊點  
 如果 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 為 <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint> 、 <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint> 或，快顯 <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint> 對齊點會在快顯視窗遇到底部或右邊畫面邊緣時變更。  
  
 下圖顯示當底部螢幕邊緣隱藏的全部或部分時，快顯 <xref:System.Windows.Controls.Primitives.Popup> 對齊點是的左下角 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
 ![因畫面下邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "Popup 會遇到畫面的下邊緣，並變更快顯對齊點。")  

 下圖說明當 <xref:System.Windows.Controls.Primitives.Popup> 右畫面邊緣隱藏時，快顯對齊點是的右上角 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
 ![因畫面邊緣而導致的新快顯對齊點](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "Popup 會遇到畫面的右邊緣，並變更快顯對齊點。")
  
 如果 <xref:System.Windows.Controls.Primitives.Popup> 遇到底部和右側畫面邊緣，則快顯對齊點就是的右下角 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>變更目標原點和快顯對齊點  
 當 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 是 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> 、 <xref:System.Windows.Controls.Primitives.PlacementMode.Left> 、 <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> 、 <xref:System.Windows.Controls.Primitives.PlacementMode.Right> 或時 <xref:System.Windows.Controls.Primitives.PlacementMode.Top> ，如果遇到特定螢幕邊緣，目標原點和快顯對齊點就會變更。  造成位置變更的螢幕邊緣取決於 <xref:System.Windows.Controls.Primitives.PlacementMode> 值。  
  
 下圖顯示當 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 是 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> ，而 <xref:System.Windows.Controls.Primitives.Popup> 遇到底部畫面邊緣時，目標原點是目的地區域的左上角，而快顯對齊點則是的左下角 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
 ![因畫面下邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "放置為底部，而快顯視窗則會遇到畫面的下邊緣。")
  
 下圖顯示當 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 是 <xref:System.Windows.Controls.Primitives.PlacementMode.Left> ，而 <xref:System.Windows.Controls.Primitives.Popup> 遇到左畫面邊緣時，目標原點是目的地區域的右上角，而快顯對齊點是的左上角 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
 ![因畫面左邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "[位置] 是 Left，而快顯視窗則會遇到螢幕的左邊緣。")  
  
 下圖顯示當 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 是 <xref:System.Windows.Controls.Primitives.PlacementMode.Right> ，而 <xref:System.Windows.Controls.Primitives.Popup> 遇到了右畫面邊緣時，目標原點是目的地區域的左上角，而快顯對齊點是的右上角 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
 ![因畫面右邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "Placement 是 Right，而 popup 會遇到畫面的右邊緣。")  

 下圖顯示當 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 是 <xref:System.Windows.Controls.Primitives.PlacementMode.Top> ，而 <xref:System.Windows.Controls.Primitives.Popup> 遇到頂端畫面邊緣時，目標原點是目的地區域的左下角，而快顯對齊點則是的左上角 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
 ![因畫面上邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "Placement 是 Top，而快顯視窗則會遇到畫面的上邊緣。")  
  
 下圖顯示當 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 是 <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> ，而 <xref:System.Windows.Controls.Primitives.Popup> 遇到底部畫面邊緣時，目標原點是目的地區域的左上角， (滑鼠指標的邊界) 而快顯對齊點則是的左下角 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
 ![因滑鼠靠近畫面邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "放置是滑鼠，而快顯視窗會遇到畫面的下邊緣。")
  
### <a name="customizing-popup-placement"></a>自訂快顯位置  
 您可以藉由將屬性設定為，來自訂目標原點和快顯對齊點 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Custom> 。 然後定義一個 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> 委派，以傳回一組可能的放置點和主要軸， (的喜好設定) 順序 <xref:System.Windows.Controls.Primitives.Popup> 。 會選取顯示最大部分的點 <xref:System.Windows.Controls.Primitives.Popup> 。  如果畫面的邊緣隱藏了，的位置 <xref:System.Windows.Controls.Primitives.Popup> 就會自動調整 <xref:System.Windows.Controls.Primitives.Popup> 。 如需範例，請參閱[指定自訂快顯位置](how-to-specify-a-custom-popup-position.md)。  
  
## <a name="see-also"></a>另請參閱

- [快顯位置範例](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
