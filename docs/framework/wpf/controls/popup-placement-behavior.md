---
title: 快顯功能表放置行為
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: 063b309ebaf0944787ce40725eed250e59f09dff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176756"
---
# <a name="popup-placement-behavior"></a>快顯功能表放置行為
控制項<xref:System.Windows.Controls.Primitives.Popup>在浮動在應用程式上的獨立視窗中顯示內容。 可以使用<xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>、 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>、 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>、 和<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>屬性指定相對於控制項、滑鼠或螢幕的位置。  這些屬性協同工作，使您能夠靈活地指定 的位置<xref:System.Windows.Controls.Primitives.Popup>。  
  
> [!NOTE]
> <xref:System.Windows.Controls.ToolTip>和<xref:System.Windows.Controls.ContextMenu>類還定義了這五個屬性，並且的行為類似。  

<a name="Positioning"></a>
## <a name="positioning-the-popup"></a>設定快顯位置  
 位置<xref:System.Windows.Controls.Primitives.Popup>可以相對於 或<xref:System.Windows.UIElement>相對於整個螢幕。  下面的示例創建四<xref:System.Windows.Controls.Primitives.Popup>個控制項，它們與<xref:System.Windows.UIElement>_，在本例中是圖像。 所有<xref:System.Windows.Controls.Primitives.Popup>控制項的屬性<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>都設置為`image1`，但每個<xref:System.Windows.Controls.Primitives.Popup>控制項都具有不同的放置屬性的值。  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 下圖顯示了圖像和<xref:System.Windows.Controls.Primitives.Popup>控制項  
  
 ![搭配四個快顯控制項的影像](./media/popup-placement-behavior/popup-placement-intro.png "帶四個快顯視窗的圖像")
  
 此<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>簡單示例演示如何設置 和<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性，但通過使用<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>和<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A><xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>屬性，您可以更控制 的位置。 <xref:System.Windows.Controls.Primitives.Popup>  
  
<a name="Definitions"></a>
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>詞彙定義︰快顯剖析  
 以下術語<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>有助於瞭解 、 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>、 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、 和<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A><xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>屬性如何相互關聯以及 ： <xref:System.Windows.Controls.Primitives.Popup>  
  
- 目標物件  
  
- 目標區域  
  
- 目標原點  
  
- 快顯對齊點  
  
 這些術語提供了一種方便的方式來引用 它<xref:System.Windows.Controls.Primitives.Popup>與之關聯的 控制項的各個方面。  
  
### <a name="target-object"></a>目標物件  
 *目標物件*是 與其關聯的元素<xref:System.Windows.Controls.Primitives.Popup>。 如果設置了<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>該屬性，它將指定目標物件。  如果未<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>設置，並且<xref:System.Windows.Controls.Primitives.Popup>有父級，則父物件是目標物件。  如果沒有<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>值，也沒有父物件，則沒有目標物件，<xref:System.Windows.Controls.Primitives.Popup>並且相對於螢幕定位。  
  
 下面的示例創建<xref:System.Windows.Controls.Primitives.Popup>作為 的 子級<xref:System.Windows.Controls.Canvas>的 。  該示例未在<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>上設置 屬性<xref:System.Windows.Controls.Primitives.Popup>。 的<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>預設值為<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>，因此<xref:System.Windows.Controls.Primitives.Popup>顯示在 的<xref:System.Windows.Controls.Canvas>下面。  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 下圖顯示 相對於<xref:System.Windows.Controls.Primitives.Popup>定位 的 。 <xref:System.Windows.Controls.Canvas>  
  
 ![沒有 PlacementTarget 的快顯控制項](./media/popup-placement-behavior/popup-placement-no-placement-target.png "沒有放置目標的快顯視窗。")  

 下面的示例創建 一<xref:System.Windows.Controls.Primitives.Popup>個 ， 是<xref:System.Windows.Controls.Canvas>的子項，但這次<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>設置為`ellipse1`， 因此快顯視窗顯示在 下面<xref:System.Windows.Shapes.Ellipse>。  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 下圖顯示 相對於<xref:System.Windows.Controls.Primitives.Popup>定位 的 。 <xref:System.Windows.Shapes.Ellipse>  
  
 ![相對於橢圓形置放的快顯](./media/popup-placement-behavior/popup-placement-with-placement-target.png "具有 PlacementTarget 的快顯")
  
> [!NOTE]
> 對於<xref:System.Windows.Controls.ToolTip>， 的<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>預設值為<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>。  對於<xref:System.Windows.Controls.ContextMenu>， 的<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>預設值為<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>。 稍後在＜屬性如何一起運作＞中會說明這些值。  
  
### <a name="target-area"></a>目標區域  
 *目的地區域*是 螢幕上<xref:System.Windows.Controls.Primitives.Popup>相對的區域。 在前面的示例中，<xref:System.Windows.Controls.Primitives.Popup>與目標物件的邊界對齊，但在某些情況下，<xref:System.Windows.Controls.Primitives.Popup>即使<xref:System.Windows.Controls.Primitives.Popup>具有目標物件，也會與其他邊界對齊。  如果設置了<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>該屬性，則目的地區域與目標物件的邊界不同。  
  
 下面的示例創建兩<xref:System.Windows.Controls.Canvas>個物件，每個物件包含<xref:System.Windows.Shapes.Rectangle>和<xref:System.Windows.Controls.Primitives.Popup>。  在這兩種情況下，的目標物件<xref:System.Windows.Controls.Primitives.Popup>是 。 <xref:System.Windows.Controls.Canvas> 第<xref:System.Windows.Controls.Primitives.Popup><xref:System.Windows.Controls.Canvas>一<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>個集具有集，其<xref:System.Windows.Rect.X%2A>、<xref:System.Windows.Rect.Y%2A><xref:System.Windows.Rect.Width%2A>和<xref:System.Windows.Rect.Height%2A>屬性分別設置為 50、50、50 和 100。 第<xref:System.Windows.Controls.Primitives.Popup>二<xref:System.Windows.Controls.Canvas>個沒有集<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  因此，<xref:System.Windows.Controls.Primitives.Popup>第一個位於 下方，<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>第二<xref:System.Windows.Controls.Primitives.Popup>個位于 的<xref:System.Windows.Controls.Canvas>下方。 每個<xref:System.Windows.Controls.Canvas>還包含與<xref:System.Windows.Shapes.Rectangle>第<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>一<xref:System.Windows.Controls.Primitives.Popup>個 具有相同的邊界。  請注意，<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>不會在應用程式中創建可見元素，該示例創建<xref:System.Windows.Shapes.Rectangle>表示 的<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 下圖顯示上述範例的結果。  
  
 ![具有和沒有 PlacementRectangle 的快顯](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "快顯視窗帶和沒有放置矩形。")  

### <a name="target-origin-and-popup-alignment-point"></a>目標原點和快顯對齊點  
 「目標原點」** 和「快顯對齊點」** 分別是目標區域和快顯上的參考點，用來進行定位。 可以使用 和<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A><xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>屬性從目的地區域偏移快顯視窗。  <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>相對於目標原點和彈出對齊<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>點。 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性的值確定目標原點和彈出對齊點的位置。  
  
 下面的示例創建 和<xref:System.Windows.Controls.Primitives.Popup><xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>將 和<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>屬性設置為 20。  屬性<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>設置為<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>（預設值），因此目標原點是目的地區域的左下角，彈出對齊點是 的<xref:System.Windows.Controls.Primitives.Popup>左上角。  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 下圖顯示上述範例的結果。  
  
 ![具有目標原點和對齊點的快顯位置](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "帶水平位移和垂直位移的快顯視窗。")
  
<a name="How"></a>
## <a name="how-the-properties-work-together"></a>屬性如何一起運作  
 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>的值和 需要一起考慮，以找出正確的目的地區域、目標原點和<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>彈出對齊點。  例如，如果 值<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>為<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>，則沒有目標物件，<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>則忽略 ，並且目的地區域是滑鼠指標的邊界。 另一<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>方面，如果 為<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>，<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或 父項確定目標物件<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>並確定目的地區域。  
  
 下表描述了目標物件、目的地區域、目標原點和彈出對齊點，並指示是否<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A><xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>和用於每個<xref:System.Windows.Controls.Primitives.PlacementMode>枚舉值。  
  
|PlacementMode|目標物件|目標區域|目標原點|快顯對齊點|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|不適用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 會被忽略。|螢幕，或者如果<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設置了。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於螢幕的。|目標區域的左上角。|的左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|不適用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 會被忽略。|螢幕，或者如果<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設置了。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於螢幕的。|目標區域的左上角。|的左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父項。|目標物件，或者如果<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>已設置。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件的。|目標區域的左下角。|的左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父項。|目標物件，或者如果<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>已設置。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件的。|目標區域的中央。|的中心<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父項。|目標物件，或者如果<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>已設置。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件的。|由 定義<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>。|由 定義<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父項。|目標物件，或者如果<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>已設置。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件的。|目標區域的左上角。|的右上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|不適用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 會被忽略。|滑鼠指標的範圍。 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 會被忽略。|目標區域的左下角。|的左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|不適用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 會被忽略。|滑鼠指標的範圍。 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 會被忽略。|目標區域的左上角。|的左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父項。|目標物件，或者如果<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>已設置。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件的。|目標區域的左上角。|的左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父項。|目標物件，或者如果<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>已設置。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件的。|目標區域的左上角。|的左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父項。|目標物件，或者如果<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>已設置。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件的。|目標區域的右上角。|的左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父項。|目標物件，或者如果<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>已設置。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件的。|目標區域的左上角。|的左下角<xref:System.Windows.Controls.Primitives.Popup>。|  
  
 下圖顯示了 每個<xref:System.Windows.Controls.Primitives.Popup><xref:System.Windows.Controls.Primitives.PlacementMode>值的目的地區域、目標原點和彈出對齊點。 在每個圖形中，目的地區域為黃色，並且<xref:System.Windows.Controls.Primitives.Popup>為藍色。  
  
 ![具有 Absolute 或 AbsolutePoint 位置的快顯](./media/popup-placement-behavior/popup-placement-absolute.png "放置是絕對或絕對點。")
  
 ![具有 Bottom 位置的快顯](./media/popup-placement-behavior/popup-placement-bottom.png "放置是底部。")
  
 ![具有 Center 位置的快顯](./media/popup-placement-behavior/popup-placement-center.png "放置是中心。")
  
 ![具有 Left 位置的快顯](./media/popup-placement-behavior/popup-placement-left.png "放置為"左"。")
  
 ![具有 Mouse 位置的快顯](./media/popup-placement-behavior/popup-placement-mouse.png "放置是滑鼠。")  
  
 ![具有 MousePoint 位置的快顯](./media/popup-placement-behavior/popup-placement-mousepoint.png "放置是滑鼠點。")  
  
 ![具有 Relative 或 RelativePoint 位置的快顯](./media/popup-placement-behavior/popup-placement-relative.png "放置是相對點或相對點。")
  
 ![具有 Right 位置的快顯](./media/popup-placement-behavior/popup-placement-right.png "放置是正確的。")
  
 ![具有 Top 位置的快顯](./media/popup-placement-behavior/popup-placement-top.png "位置是頂部。")
  
<a name="When"></a>
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>當快顯遇到畫面邊緣時  
 出於安全原因，<xref:System.Windows.Controls.Primitives.Popup>無法隱藏在螢幕邊緣。 遇到螢幕邊緣時<xref:System.Windows.Controls.Primitives.Popup>會發生以下三種情況之一：  
  
- 快顯視窗沿螢幕邊緣重新調整自身，這將遮蓋 。 <xref:System.Windows.Controls.Primitives.Popup>  
  
- 快顯會使用不同的快顯對齊點。  
  
- 快顯會使用不同的目標原點和快顯對齊點。  
  
 本節稍後會進一步說明這些選項。  
  
 遇到螢幕邊緣<xref:System.Windows.Controls.Primitives.Popup>時的行為取決於<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性的值以及快顯視窗遇到的螢幕邊緣。 下表總結了當<xref:System.Windows.Controls.Primitives.Popup>遇到每個<xref:System.Windows.Controls.Primitives.PlacementMode>值的螢幕邊緣時的行為。  
  
|PlacementMode|上邊緣|下邊緣|左邊緣|右邊緣|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|對齊上邊緣。|對齊下邊緣。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|對齊上邊緣。|彈出對齊點將更改為 的<xref:System.Windows.Controls.Primitives.Popup>左下角。|對齊左邊緣。|彈出對齊點將更改為 的<xref:System.Windows.Controls.Primitives.Popup>右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|對齊上邊緣。|目標原點更改為目的地區域的左上角，彈出對齊點將更改為 的<xref:System.Windows.Controls.Primitives.Popup>左下角。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|對齊上邊緣。|對齊下邊緣。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|對齊上邊緣。|對齊下邊緣。|目標原點更改為目的地區域的右上角，彈出對齊點將更改為 的<xref:System.Windows.Controls.Primitives.Popup>左上角。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|對齊上邊緣。|目標原點更改為目的地區域的左上角（滑鼠指標的邊界），彈出對齊點將更改為 的<xref:System.Windows.Controls.Primitives.Popup>左下角。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|對齊上邊緣。|彈出對齊點將更改為 的<xref:System.Windows.Controls.Primitives.Popup>左下角。|對齊左邊緣。|快顯對齊點會變更至快顯的右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|對齊上邊緣。|對齊下邊緣。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|對齊上邊緣。|彈出對齊點將更改為 的<xref:System.Windows.Controls.Primitives.Popup>左下角。|對齊左邊緣。|快顯對齊點會變更至快顯的右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|對齊上邊緣。|對齊下邊緣。|對齊左邊緣。|目標原點更改為目的地區域的左上角，彈出對齊點將更改為 的<xref:System.Windows.Controls.Primitives.Popup>右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|目標原點更改為目的地區域的左下角，彈出對齊點將更改為 的<xref:System.Windows.Controls.Primitives.Popup>左上角。 實際上，這與 時<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>相同。 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|對齊下邊緣。|對齊左邊緣。|對齊右邊緣。|  
  
### <a name="aligning-to-the-screen-edge"></a>對齊畫面邊緣  
 A<xref:System.Windows.Controls.Primitives.Popup>可以通過重新置放自身來與螢幕邊緣對齊，以便整個螢幕<xref:System.Windows.Controls.Primitives.Popup>可見。  發生這種情況時，目標原點和彈出對齊點之間的距離可能與 和<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A><xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>的值不同。 當<xref:System.Windows.Controls.Primitives.Popup.Placement%2A><xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>是<xref:System.Windows.Controls.Primitives.PlacementMode.Center>、<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>或<xref:System.Windows.Controls.Primitives.Popup>時，將自身與每個螢幕邊緣對齊。  例如，<xref:System.Windows.Controls.Primitives.Popup>假設 a 已<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>設置為<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>設置為<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>100。  如果螢幕的下邊緣隱藏 全部或部分<xref:System.Windows.Controls.Primitives.Popup>，則沿螢幕底部邊緣的<xref:System.Windows.Controls.Primitives.Popup>重新置放自身，目標原點和彈出對齊點之間的垂直距離小於 100。 下圖示範這種情況。  
  
 ![與畫面邊緣對齊的快顯](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "快顯視窗與螢幕邊緣對齊。")
  
### <a name="changing-the-popup-alignment-point"></a>變更快顯對齊點  
 如果<xref:System.Windows.Controls.Primitives.Popup.Placement%2A><xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>是<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>、<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>或 ，則快顯視窗遇到底部或右螢幕邊緣時，快顯視窗對齊點將發生變化。  
  
 下圖演示了當底部螢幕邊緣隱藏 的全部或部分<xref:System.Windows.Controls.Primitives.Popup>時，彈出對齊點是 的<xref:System.Windows.Controls.Primitives.Popup>左下角。  
  
 ![因畫面下邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "快顯視窗遇到螢幕的下邊緣並更改彈出對齊點。")  

 下圖演示了當 被隱藏在<xref:System.Windows.Controls.Primitives.Popup>右螢幕邊緣時，彈出對齊點是 的<xref:System.Windows.Controls.Primitives.Popup>右上角。  
  
 ![因畫面邊緣而導致的新快顯對齊點](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "快顯視窗遇到螢幕的右邊緣並更改彈出對齊點。")
  
 如果<xref:System.Windows.Controls.Primitives.Popup>遇到螢幕底部和右側邊緣，則彈出對齊點是 的<xref:System.Windows.Controls.Primitives.Popup>右下角。  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>變更目標原點和快顯對齊點  
 如果<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>遇到<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>特定<xref:System.Windows.Controls.Primitives.PlacementMode.Left>螢幕<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>邊緣<xref:System.Windows.Controls.Primitives.PlacementMode.Right>，<xref:System.Windows.Controls.Primitives.PlacementMode.Top>則目標原點和彈出對齊點何時更改。  導致位置更改的螢幕邊緣取決於該<xref:System.Windows.Controls.Primitives.PlacementMode>值。  
  
 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>下圖演示了當和<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom><xref:System.Windows.Controls.Primitives.Popup>遇到下屏邊緣時，目標原點是目的地區域的左上角，彈出對齊點是 的<xref:System.Windows.Controls.Primitives.Popup>左下角。  
  
 ![因畫面下邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "放置是底部，快顯視窗遇到螢幕的底部邊緣。")
  
 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>下圖演示了當和<xref:System.Windows.Controls.Primitives.PlacementMode.Left><xref:System.Windows.Controls.Primitives.Popup>遇到左螢幕邊緣時，目標原點是目的地區域的右上角，彈出對齊點是 的<xref:System.Windows.Controls.Primitives.Popup>左上角。  
  
 ![因畫面左邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "放置是"左"，快顯視窗遇到螢幕的左邊緣。")  
  
 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>下圖演示了當和<xref:System.Windows.Controls.Primitives.PlacementMode.Right><xref:System.Windows.Controls.Primitives.Popup>遇到右螢幕邊緣時，目標原點是目的地區域的左上角，彈出對齊點是 的<xref:System.Windows.Controls.Primitives.Popup>右上角。  
  
 ![因畫面右邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "放置正確，快顯視窗遇到螢幕的右邊緣。")  

 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>下圖演示了當和<xref:System.Windows.Controls.Primitives.PlacementMode.Top><xref:System.Windows.Controls.Primitives.Popup>遇到頂部螢幕邊緣時，目標原點是目的地區域的左下角，彈出對齊點是 的<xref:System.Windows.Controls.Primitives.Popup>左上角。  
  
 ![因畫面上邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "放置是頂部，快顯視窗遇到螢幕的上邊緣。")  
  
 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>下圖演示了當和<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse><xref:System.Windows.Controls.Primitives.Popup>遇到底部螢幕邊緣時，目標原點是目的地區域的左上角（滑鼠指標的邊界），彈出對齊點是 的<xref:System.Windows.Controls.Primitives.Popup>左下角。  
  
 ![因滑鼠靠近畫面邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "放置是滑鼠，快顯視窗遇到螢幕的底部邊緣。")
  
### <a name="customizing-popup-placement"></a>自訂快顯位置  
 通過將<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性設置為<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>，可以自訂目標原點和彈出對齊點。 然後定義一<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>個委託，該委託返回 一<xref:System.Windows.Controls.Primitives.Popup>組可能的放置點和主軸（按首選項順序排列） 。 所選顯示 的最大<xref:System.Windows.Controls.Primitives.Popup>部分的點。  <xref:System.Windows.Controls.Primitives.Popup>如果<xref:System.Windows.Controls.Primitives.Popup>隱藏在螢幕邊緣， 則 會自動調整 的位置。 如需範例，請參閱[指定自訂快顯位置](how-to-specify-a-custom-popup-position.md)。  
  
## <a name="see-also"></a>另請參閱

- [快顯位置範例](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
