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
控制檔<xref:System.Windows.Controls.Primitives.Popup>在浮動在應用程式上的獨立視窗中顯示內容。 可以使用<xref:System.Windows.Controls.Primitives.Popup><xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>、 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>、<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>、 屬性指定相對於控制器、滑鼠或螢幕的位置。  這些屬性協同工作,讓您能夠靈活地指定的位置<xref:System.Windows.Controls.Primitives.Popup>。  
  
> [!NOTE]
> <xref:System.Windows.Controls.ToolTip>和<xref:System.Windows.Controls.ContextMenu>類還定義了這五個屬性,並且的行為類似。  

<a name="Positioning"></a>
## <a name="positioning-the-popup"></a>設定快顯位置  
 位置<xref:System.Windows.Controls.Primitives.Popup>可以相對於<xref:System.Windows.UIElement>或 相對於整個螢幕。  下面的範例創建四<xref:System.Windows.Controls.Primitives.Popup>個控制項,它們<xref:System.Windows.UIElement>與_,在本例中是圖像。 所有<xref:System.Windows.Controls.Primitives.Popup>控件的<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>屬性 都`image1`設置為<xref:System.Windows.Controls.Primitives.Popup>,但每個控制項都具有不同的放置屬性的值。  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 下圖顯示影像和<xref:System.Windows.Controls.Primitives.Popup>控制項  
  
 ![搭配四個快顯控制項的影像](./media/popup-placement-behavior/popup-placement-intro.png "帶四個彈出視窗的影像")
  
 此<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>簡單範例展示如何設定<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>和 屬性,<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>但<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A><xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>透過使用和屬性,您可以更<xref:System.Windows.Controls.Primitives.Popup>控制的位置。  
  
<a name="Definitions"></a>
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>詞彙定義︰快顯剖析  
 以下字語<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>有助於瞭解<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>、 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A><xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>、 與 屬性<xref:System.Windows.Controls.Primitives.Popup>如何相互關聯以及 :  
  
- 目標物件  
  
- 目標區域  
  
- 目標原點  
  
- 快顯對齊點  
  
 這些術語提供了一種方便的方式來引用<xref:System.Windows.Controls.Primitives.Popup>它 與之關聯的控制件的各個方面。  
  
### <a name="target-object"></a>目標物件  
 *目標物件*是與其關聯的<xref:System.Windows.Controls.Primitives.Popup>元素 。 如果設置了<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>該屬性,它將指定目標物件。  如果未<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>設置,<xref:System.Windows.Controls.Primitives.Popup>並且 有父級,則父對像是目標物件。  如果沒有<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>值,也沒有父物件,則沒有目標物件<xref:System.Windows.Controls.Primitives.Popup>, 並且相對於螢幕定位。  
  
 下面的範例建立<xref:System.Windows.Controls.Primitives.Popup>作為的子<xref:System.Windows.Controls.Canvas>級的 。  這個設定的屬性<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A><xref:System.Windows.Controls.Primitives.Popup>。 的<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>預設值<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>為<xref:System.Windows.Controls.Primitives.Popup>,因此<xref:System.Windows.Controls.Canvas>顯示在的下面。  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 下圖顯示 相<xref:System.Windows.Controls.Primitives.Popup>對於 定位<xref:System.Windows.Controls.Canvas>的 。  
  
 ![沒有 PlacementTarget 的快顯控制項](./media/popup-placement-behavior/popup-placement-no-placement-target.png "沒有放置目標的彈出視窗。")  

 下面的範例建立一<xref:System.Windows.Controls.Primitives.Popup>個,<xref:System.Windows.Controls.Canvas>是的子項目,但<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>您設定`ellipse1`為 , 因此彈出視窗<xref:System.Windows.Shapes.Ellipse>顯示在下面 。  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 下圖顯示 相<xref:System.Windows.Controls.Primitives.Popup>對於 定位<xref:System.Windows.Shapes.Ellipse>的 。  
  
 ![相對於橢圓形置放的快顯](./media/popup-placement-behavior/popup-placement-with-placement-target.png "具有 PlacementTarget 的快顯")
  
> [!NOTE]
> 對<xref:System.Windows.Controls.ToolTip>,<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>預設值為<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>。  對<xref:System.Windows.Controls.ContextMenu>,<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>預設值為<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>。 稍後在＜屬性如何一起運作＞中會說明這些值。  
  
### <a name="target-area"></a>目標區域  
 *目標區域*是<xref:System.Windows.Controls.Primitives.Popup>螢幕上 相對的區域。 在前面的範例中,<xref:System.Windows.Controls.Primitives.Popup>與目標物件的邊界對齊,但在某些情況下<xref:System.Windows.Controls.Primitives.Popup>,<xref:System.Windows.Controls.Primitives.Popup>即使具有目標物件,也會與其他邊界對齊。  如果設置了<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>該屬性,則目標區域與目標物件的邊界不同。  
  
 下面的範例建立兩<xref:System.Windows.Controls.Canvas>個物件,每個物件包含<xref:System.Windows.Shapes.Rectangle>與<xref:System.Windows.Controls.Primitives.Popup>。  在這兩種情況下,的目標物件<xref:System.Windows.Controls.Primitives.Popup>是<xref:System.Windows.Controls.Canvas>。 第<xref:System.Windows.Controls.Primitives.Popup><xref:System.Windows.Controls.Canvas><xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>一個集具有集,<xref:System.Windows.Rect.X%2A>其<xref:System.Windows.Rect.Y%2A><xref:System.Windows.Rect.Width%2A>、<xref:System.Windows.Rect.Height%2A>屬性分別設置為50、50、50和100。 第<xref:System.Windows.Controls.Primitives.Popup><xref:System.Windows.Controls.Canvas>二個沒有<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>集 。  因此,<xref:System.Windows.Controls.Primitives.Popup>第一個位於下方<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>,<xref:System.Windows.Controls.Primitives.Popup>第二<xref:System.Windows.Controls.Canvas>個位於的下方。 每個<xref:System.Windows.Controls.Canvas>還包含<xref:System.Windows.Shapes.Rectangle>與<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>第<xref:System.Windows.Controls.Primitives.Popup>一個具有相同的邊界。  請注意,<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>不會在應用程式中創建可見元素,此範例建立<xref:System.Windows.Shapes.Rectangle>表示<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>的 。  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 下圖顯示上述範例的結果。  
  
 ![具有和沒有 PlacementRectangle 的快顯](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "彈出視窗帶和沒有放置矩形。")  

### <a name="target-origin-and-popup-alignment-point"></a>目標原點和快顯對齊點  
 「目標原點」** 和「快顯對齊點」** 分別是目標區域和快顯上的參考點，用來進行定位。 可以使用和<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A><xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>屬性從目標區域偏移彈出視窗。  <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>相對於目標原點和彈出對齊<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>點。 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性的值確定目標原點和彈出對齊點的位置。  
  
 下面的範例建立和<xref:System.Windows.Controls.Primitives.Popup><xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>將和<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>屬性設定為 20。  屬性<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>設置<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>為 (預設值),因此目標原點是目標區域的左下角,彈出對齊點<xref:System.Windows.Controls.Primitives.Popup>是 的 左上角。  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 下圖顯示上述範例的結果。  
  
 ![具有目標原點和對齊點的快顯位置](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "帶水準偏移和垂直偏移的彈出視窗。")
  
<a name="How"></a>
## <a name="how-the-properties-work-together"></a>屬性如何一起運作  
 的值和 需要一起考慮,以找出正確的目標區域、目標原點<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>和彈出對齊點。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>  例如,如果值<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>為<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>,則沒有目標物件<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, 則忽略 ,並且目標區域是滑鼠指標的邊界。 另一<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>方面,如果為<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom><xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, 或父項確定<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>目標物件 並確定目標區域。  
  
 下表描述了目標物件、目標區域、目標原點和彈出對齊點,並指示是否<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A><xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>和用於每個<xref:System.Windows.Controls.Primitives.PlacementMode>枚舉值。  
  
|PlacementMode|目標物件|目標區域|目標原點|快顯對齊點|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|不適用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 會被忽略。|螢幕,或者如果<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設置了。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於螢幕的。|目標區域的左上角。|左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|不適用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 會被忽略。|螢幕,或者如果<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設置了。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於螢幕的。|目標區域的左上角。|左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父項。|目標物件,或者如果<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>已設置。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件的。|目標區域的左下角。|左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父項。|目標物件,或者如果<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>已設置。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件的。|目標區域的中央。|的中心<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父項。|目標物件,或者如果<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>已設置。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件的。|由定義<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>。|由定義<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父項。|目標物件,或者如果<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>已設置。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件的。|目標區域的左上角。|的右上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|不適用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 會被忽略。|滑鼠指標的範圍。 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 會被忽略。|目標區域的左下角。|左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|不適用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 會被忽略。|滑鼠指標的範圍。 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 會被忽略。|目標區域的左上角。|左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父項。|目標物件,或者如果<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>已設置。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件的。|目標區域的左上角。|左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父項。|目標物件,或者如果<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>已設置。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件的。|目標區域的左上角。|左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父項。|目標物件,或者如果<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>已設置。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件的。|目標區域的右上角。|左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父項。|目標物件,或者如果<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>已設置。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件的。|目標區域的左上角。|左下角<xref:System.Windows.Controls.Primitives.Popup>。|  
  
 下圖顯示了<xref:System.Windows.Controls.Primitives.Popup><xref:System.Windows.Controls.Primitives.PlacementMode>每個值的目標區域、目標原點和彈出對齊點。 在每個圖形中,目標區域為黃色,並且<xref:System.Windows.Controls.Primitives.Popup>為藍色。  
  
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
 出於安全原因,<xref:System.Windows.Controls.Primitives.Popup>無法隱藏在螢幕邊緣。 遇到螢幕邊緣時<xref:System.Windows.Controls.Primitives.Popup>會發生以下三種情況之一:  
  
- 彈出視窗沿螢幕邊緣重新調整自身,這會遮蓋<xref:System.Windows.Controls.Primitives.Popup>。  
  
- 快顯會使用不同的快顯對齊點。  
  
- 快顯會使用不同的目標原點和快顯對齊點。  
  
 本節稍後會進一步說明這些選項。  
  
 遇到螢幕邊緣<xref:System.Windows.Controls.Primitives.Popup>時的行為<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>取決於 屬性的值以及彈出視窗遇到的屏幕邊緣。 下表總結了當<xref:System.Windows.Controls.Primitives.Popup>遇到<xref:System.Windows.Controls.Primitives.PlacementMode>每個 值的屏幕邊緣時的行為。  
  
|PlacementMode|上邊緣|下邊緣|左邊緣|右邊緣|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|對齊上邊緣。|對齊下邊緣。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|對齊上邊緣。|彈出對齊點將更改為<xref:System.Windows.Controls.Primitives.Popup>的 左下角。|對齊左邊緣。|彈出對齊點將更改為<xref:System.Windows.Controls.Primitives.Popup>的 右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|對齊上邊緣。|目標原點更改為目標區域的左上角,彈出對齊點將更改為<xref:System.Windows.Controls.Primitives.Popup>的 左下角。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|對齊上邊緣。|對齊下邊緣。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|對齊上邊緣。|對齊下邊緣。|目標原點更改為目標區域的右上角,彈出對齊點將更改為<xref:System.Windows.Controls.Primitives.Popup>的 左上角。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|對齊上邊緣。|目標原點更改為目標區域的左上角(滑鼠指標的邊界),彈出對齊點將更改為 的<xref:System.Windows.Controls.Primitives.Popup>左下角。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|對齊上邊緣。|彈出對齊點將更改為<xref:System.Windows.Controls.Primitives.Popup>的 左下角。|對齊左邊緣。|快顯對齊點會變更至快顯的右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|對齊上邊緣。|對齊下邊緣。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|對齊上邊緣。|彈出對齊點將更改為<xref:System.Windows.Controls.Primitives.Popup>的 左下角。|對齊左邊緣。|快顯對齊點會變更至快顯的右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|對齊上邊緣。|對齊下邊緣。|對齊左邊緣。|目標原點更改為目標區域的左上角,彈出對齊點將更改為<xref:System.Windows.Controls.Primitives.Popup>的 右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|目標原點更改為目標區域的左下角,彈出對齊點將更改為<xref:System.Windows.Controls.Primitives.Popup>的 左上角。 實際上,這與時<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>相同。 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|對齊下邊緣。|對齊左邊緣。|對齊右邊緣。|  
  
### <a name="aligning-to-the-screen-edge"></a>對齊畫面邊緣  
 A<xref:System.Windows.Controls.Primitives.Popup>可以通過重新置放自身來與螢幕邊緣對齊,<xref:System.Windows.Controls.Primitives.Popup>以便整個螢幕 可見。  發生這種情況時,目標原點和彈出對齊點之間的距離可能與<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A><xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>和的值不同。 當<xref:System.Windows.Controls.Primitives.Popup.Placement%2A><xref:System.Windows.Controls.Primitives.PlacementMode.Absolute><xref:System.Windows.Controls.Primitives.PlacementMode.Center>是<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>、<xref:System.Windows.Controls.Primitives.Popup>或時,將自身與每個螢幕邊緣對齊。  例如,<xref:System.Windows.Controls.Primitives.Popup>假設<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>a<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>已設定<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>為設定為 100。  如果螢幕的下邊緣隱藏 全部或<xref:System.Windows.Controls.Primitives.Popup>部分 ,則沿螢幕底部<xref:System.Windows.Controls.Primitives.Popup>邊緣的 重新置放自身,目標原點和彈出對齊點之間的垂直距離小於 100。 下圖示範這種情況。  
  
 ![與畫面邊緣對齊的快顯](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "彈出視窗與屏幕邊緣對齊。")
  
### <a name="changing-the-popup-alignment-point"></a>變更快顯對齊點  
 如果<xref:System.Windows.Controls.Primitives.Popup.Placement%2A><xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint><xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>是<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>、 或,則彈出視窗遇到底部或右螢幕邊緣時,彈出視窗對齊點將發生變化。  
  
 下圖演示了當底部屏幕邊緣隱藏 的全部或<xref:System.Windows.Controls.Primitives.Popup>部分 時,彈出對齊點<xref:System.Windows.Controls.Primitives.Popup>是 的 左下角。  
  
 ![因畫面下邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "彈出視窗遇到螢幕的下邊緣並更改彈出對齊點。")  

 下圖演示了當 被隱藏<xref:System.Windows.Controls.Primitives.Popup>在 右屏幕邊緣時,彈出對齊點<xref:System.Windows.Controls.Primitives.Popup>是 的 右上角。  
  
 ![因畫面邊緣而導致的新快顯對齊點](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "彈出視窗遇到螢幕的右邊緣並更改彈出對齊點。")
  
 如果<xref:System.Windows.Controls.Primitives.Popup>遇到螢幕底部和右側邊緣,則彈出對齊點是<xref:System.Windows.Controls.Primitives.Popup>的 右下角。  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>變更目標原點和快顯對齊點  
 如果<xref:System.Windows.Controls.Primitives.Popup.Placement%2A><xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>遇到<xref:System.Windows.Controls.Primitives.PlacementMode.Left><xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>特定<xref:System.Windows.Controls.Primitives.PlacementMode.Right>螢幕<xref:System.Windows.Controls.Primitives.PlacementMode.Top>邊緣 , 則目標原點和彈出對齊點何時更改。  導致位置更改的屏幕邊緣取決於該<xref:System.Windows.Controls.Primitives.PlacementMode>值。  
  
 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>下圖演示了當和<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom><xref:System.Windows.Controls.Primitives.Popup>遇到下屏邊緣時,目標原點是目標區域的左上角,彈出對齊點是<xref:System.Windows.Controls.Primitives.Popup>的 左下角。  
  
 ![因畫面下邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "放置是底部,彈出視窗遇到螢幕的底部邊緣。")
  
 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>下圖演示了當和<xref:System.Windows.Controls.Primitives.PlacementMode.Left><xref:System.Windows.Controls.Primitives.Popup>遇到左屏幕邊緣時,目標原點是目標區域的右上角,彈出對齊點是<xref:System.Windows.Controls.Primitives.Popup>的 左上角。  
  
 ![因畫面左邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "放置是「左」,彈出視窗遇到螢幕的左邊緣。")  
  
 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>下圖演示了當和<xref:System.Windows.Controls.Primitives.PlacementMode.Right><xref:System.Windows.Controls.Primitives.Popup>遇到右屏幕邊緣時,目標原點是目標區域的左上角,彈出對齊點是<xref:System.Windows.Controls.Primitives.Popup>的 右上角。  
  
 ![因畫面右邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "放置正確,彈出視窗遇到螢幕的右邊緣。")  

 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>下圖演示了當和<xref:System.Windows.Controls.Primitives.PlacementMode.Top><xref:System.Windows.Controls.Primitives.Popup>遇到頂部屏幕邊緣時,目標原點是目標區域的左下角,彈出對齊點是<xref:System.Windows.Controls.Primitives.Popup>的 左上角。  
  
 ![因畫面上邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "放置是頂部,彈出視窗遇到螢幕的上邊緣。")  
  
 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>下圖演示了當和<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse><xref:System.Windows.Controls.Primitives.Popup>遇到底部屏幕邊緣時,目標原點是目標區域的左上角(滑鼠指標的邊界),彈出對齊點是<xref:System.Windows.Controls.Primitives.Popup>的左下角。  
  
 ![因滑鼠靠近畫面邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "放置是滑鼠,彈出視窗遇到螢幕的底部邊緣。")
  
### <a name="customizing-popup-placement"></a>自訂快顯位置  
 通過將<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性設置<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>為 ,可以自定義目標原點和彈出對齊點。 然後定義一<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>個委託,該委託傳回<xref:System.Windows.Controls.Primitives.Popup>一組可能的放置點和主軸(按首選項順序排列) 。 所選顯示<xref:System.Windows.Controls.Primitives.Popup>的最大 部分的點。  <xref:System.Windows.Controls.Primitives.Popup>如果<xref:System.Windows.Controls.Primitives.Popup>隱藏在螢幕邊緣, 會自動調整的位置。 如需範例，請參閱[指定自訂快顯位置](how-to-specify-a-custom-popup-position.md)。  
  
## <a name="see-also"></a>另請參閱

- [快顯位置範例](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
