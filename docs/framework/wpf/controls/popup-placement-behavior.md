---
title: 快顯功能表放置行為
description: 了解如何使用屬性來指定相對於控制項、滑鼠或畫面的 Windows Presentation Foundation 快顯位置。
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: 8184805518bc56693ead4c7d1f0e9a1bff9bff8f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167751"
---
# <a name="popup-placement-behavior"></a>快顯功能表放置行為
<xref:System.Windows.Controls.Primitives.Popup> 控制項會以在應用程式上浮動的個別視窗來顯示內容。 您可使用 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 與 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 屬性來指定相對於控制項、滑鼠或畫面的 <xref:System.Windows.Controls.Primitives.Popup> 位置。  這些屬性可共同作業，以提供在指定 <xref:System.Windows.Controls.Primitives.Popup>位置時的彈性。  
  
> [!NOTE]
> <xref:System.Windows.Controls.ToolTip> 與 <xref:System.Windows.Controls.ContextMenu> 類別也會定義這五個屬性，並以同樣的方式運作。  

<a name="Positioning"></a>
## <a name="positioning-the-popup"></a>設定快顯位置  
 <xref:System.Windows.Controls.Primitives.Popup> 的位置可相對於 <xref:System.Windows.UIElement> 或整個畫面。  下列範例建立四個相對於 <xref:System.Windows.UIElement> 的 <xref:System.Windows.Controls.Primitives.Popup> 控制項—此情況為影像。 所有 <xref:System.Windows.Controls.Primitives.Popup> 控制項都有設為 `image1` 的 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 屬性，但每個 <xref:System.Windows.Controls.Primitives.Popup>的位置屬性都有不同值。  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 下圖顯示影像與 <xref:System.Windows.Controls.Primitives.Popup> 控制項  
  
 ![搭配四個快顯控制項的影像](./media/popup-placement-behavior/popup-placement-intro.png "搭配四個快顯的影像")
  
 此簡單範例示範如何使用 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 與 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 屬性來設定 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 與 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 屬性，以讓您可更充分地控制 <xref:System.Windows.Controls.Primitives.Popup> 的位置。  
  
<a name="Definitions"></a>
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>字詞定義：快顯的剖析  
 下列字詞有助於了解 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 與 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 屬性，彼此與 <xref:System.Windows.Controls.Primitives.Popup> 關聯的程度為何：  
  
- 目標物件  
  
- 目標區域  
  
- 目標原點  
  
- 快顯對齊點  
  
 這些字詞可供方便地參考的 <xref:System.Windows.Controls.Primitives.Popup>各方面，以及與其建立關聯的控制項。  
  
### <a name="target-object"></a>目標物件  
 「目標物件」為與 <xref:System.Windows.Controls.Primitives.Popup> 建立關聯的元素。 如果已設定 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 屬性，其即會指定目標物件。  如果未設定 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>，且 <xref:System.Windows.Controls.Primitives.Popup> 具有父系，則父系為目標物件。  如果沒有 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 值且無父系，則沒有目標物件，且 <xref:System.Windows.Controls.Primitives.Popup> 的位置相對於畫面。  
  
 下列範例會建立 <xref:System.Windows.Controls.Primitives.Popup>，其為 <xref:System.Windows.Controls.Canvas> 的子系。  該範例不會設定 <xref:System.Windows.Controls.Primitives.Popup> 上的 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 屬性。 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 的預設值為 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>，所以 <xref:System.Windows.Controls.Primitives.Popup> 會出現在 <xref:System.Windows.Controls.Canvas> 下方。  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 下圖顯示 <xref:System.Windows.Controls.Primitives.Popup> 的位置相對於 <xref:System.Windows.Controls.Canvas>。  
  
 ![沒有 PlacementTarget 的快顯控制項](./media/popup-placement-behavior/popup-placement-no-placement-target.png "沒有 PlacementTarget 的快顯。")  

 下列範例會建立 <xref:System.Windows.Controls.Canvas> 其子系的 <xref:System.Windows.Controls.Primitives.Popup>，但 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 這次設為 `ellipse1`，所以快顯會出現在 <xref:System.Windows.Shapes.Ellipse> 下方。  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 下圖顯示 <xref:System.Windows.Controls.Primitives.Popup> 其位置與 <xref:System.Windows.Shapes.Ellipse> 相對。  
  
 ![相對於橢圓形置放的快顯](./media/popup-placement-behavior/popup-placement-with-placement-target.png "具有 PlacementTarget 的快顯")
  
> [!NOTE]
> 針對 <xref:System.Windows.Controls.ToolTip>，<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 的預設值為 <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>。  針對 <xref:System.Windows.Controls.ContextMenu>，<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 的預設值為 <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>。 稍後在＜屬性如何一起運作＞中會說明這些值。  
  
### <a name="target-area"></a>目標區域  
 *目標區域*為畫面上相對於 <xref:System.Windows.Controls.Primitives.Popup> 的區域。 在前一個範例中，<xref:System.Windows.Controls.Primitives.Popup> 對齊目標物件的繫結，但在某些情況下，即使 <xref:System.Windows.Controls.Primitives.Popup> 有目標物件，<xref:System.Windows.Controls.Primitives.Popup> 還是對齊其他的繫結。  如果已設定 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 屬性，則目標區域不同於目標物件的繫結。  
  
 下列範例建立兩個 <xref:System.Windows.Controls.Canvas> 物件，每一個都包含 <xref:System.Windows.Shapes.Rectangle> 與 <xref:System.Windows.Controls.Primitives.Popup>。  在這兩種狀況下，<xref:System.Windows.Controls.Primitives.Popup> 的目標物件為 <xref:System.Windows.Controls.Canvas>。 第一個 <xref:System.Windows.Controls.Canvas> 的 <xref:System.Windows.Controls.Primitives.Popup> 已設定 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>，且其 <xref:System.Windows.Rect.X%2A>、<xref:System.Windows.Rect.Y%2A>、<xref:System.Windows.Rect.Width%2A> 與 <xref:System.Windows.Rect.Height%2A> 屬性分別設為 50、50、50 與 100。 第二個 <xref:System.Windows.Controls.Canvas> 的 <xref:System.Windows.Controls.Primitives.Popup> 未設定 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  結果，第一個 <xref:System.Windows.Controls.Primitives.Popup> 的位置在 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 下方，而第二個 <xref:System.Windows.Controls.Primitives.Popup> 的位置在 <xref:System.Windows.Controls.Canvas> 下方。 每個 <xref:System.Windows.Controls.Canvas> 也包含 <xref:System.Windows.Shapes.Rectangle>，其 第一個 <xref:System.Windows.Controls.Primitives.Popup>具有與 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 相同的繫結。  請注意，<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 不會在應用程式中建立可見項目；該範例會建立 <xref:System.Windows.Shapes.Rectangle> 以代表 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 下圖顯示上述範例的結果。  
  
 ![具有和沒有 PlacementRectangle 的快顯](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "具有與沒有 PlacementRectangle 的快顯。")  

### <a name="target-origin-and-popup-alignment-point"></a>目標原點和快顯對齊點  
 「目標原點」和「快顯對齊點」分別是目標區域和快顯上的參考點，用來進行定位。 您可使用 <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 屬性以位移目標區域的快顯。  <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 與 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 相對於目標來源與快顯對齊點。 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 屬性值決定目標來源與快顯對齊點的位置。  
  
 下列範例建立 <xref:System.Windows.Controls.Primitives.Popup> 並將 <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 與 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 屬性設為 20。  <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 屬性設為 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> (預設)，所以目標來源位於目標區域的左下角，且快顯對齊點位於 <xref:System.Windows.Controls.Primitives.Popup> 的左上角。  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 下圖顯示上述範例的結果。  
  
 ![具有目標原點和對齊點的快顯位置](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "具有 HorizontalOffset 與 VerticalOffset 的快顯。")
  
<a name="How"></a>
## <a name="how-the-properties-work-together"></a>屬性如何一起運作  
 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 與 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 的值需要一起考慮，以找出正確目標區域、目標來源與快顯對齊點。  例如，如果 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 的值為 <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>，除了沒有目標物件之外，還會忽略 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>，且目標區域為滑鼠指標的繫結。 另一方面，如果 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 為 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>，則 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父系決定目標物件；且 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 會決定目標區域。  
  
 下表描述目標物件、目標區域、目標來源與快顯對齊點，並指出每個 <xref:System.Windows.Controls.Primitives.PlacementMode> 列舉值是否使用 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  
  
|PlacementMode|目標物件|目標區域|目標原點|快顯對齊點|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|不適用。 已忽略 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>。|畫面，或在設定時為 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 相對於畫面。|目標區域的左上角。|<xref:System.Windows.Controls.Primitives.Popup> 的左上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|不適用。 已忽略 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>。|畫面，或在設定時為 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 相對於畫面。|目標區域的左上角。|<xref:System.Windows.Controls.Primitives.Popup> 的左上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父系。|目標物件，或在設定時為 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 相對於目標物件。|目標區域的左下角。|<xref:System.Windows.Controls.Primitives.Popup> 的左上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父系。|目標物件，或在設定時為 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 相對於目標物件。|目標區域的中央。|<xref:System.Windows.Controls.Primitives.Popup> 的中心。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父系。|目標物件，或在設定時為 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 相對於目標物件。|由 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> 所定義。|由 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> 所定義。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父系。|目標物件，或在設定時為 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 相對於目標物件。|目標區域的左上角。|<xref:System.Windows.Controls.Primitives.Popup> 的右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|不適用。 已忽略 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>。|滑鼠指標的範圍。 已忽略 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。|目標區域的左下角。|<xref:System.Windows.Controls.Primitives.Popup> 的左上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|不適用。 已忽略 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>。|滑鼠指標的範圍。 已忽略 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。|目標區域的左上角。|<xref:System.Windows.Controls.Primitives.Popup> 的左上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父系。|目標物件，或在設定時為 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 相對於目標物件。|目標區域的左上角。|<xref:System.Windows.Controls.Primitives.Popup> 的左上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父系。|目標物件，或在設定時為 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 相對於目標物件。|目標區域的左上角。|<xref:System.Windows.Controls.Primitives.Popup> 的左上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父系。|目標物件，或在設定時為 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 相對於目標物件。|目標區域的右上角。|<xref:System.Windows.Controls.Primitives.Popup> 的左上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父系。|目標物件，或在設定時為 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 相對於目標物件。|目標區域的左上角。|<xref:System.Windows.Controls.Primitives.Popup> 的左下角。|  
  
 下圖顯示每個 <xref:System.Windows.Controls.Primitives.PlacementMode> 值的 <xref:System.Windows.Controls.Primitives.Popup>、目標區域、目標來源與快顯對齊點。 在每張圖中，目標區域為黃色且 <xref:System.Windows.Controls.Primitives.Popup> 為藍色。  
  
 ![具有 Absolute 或 AbsolutePoint 位置的快顯](./media/popup-placement-behavior/popup-placement-absolute.png "Placement 為 Absolute 或 AbsolutePoint。")
  
 ![具有 Bottom 位置的快顯](./media/popup-placement-behavior/popup-placement-bottom.png "Placement 為 Bottom。")
  
 ![具有 Center 位置的快顯](./media/popup-placement-behavior/popup-placement-center.png "Placement 為 Center。")
  
 ![具有 Left 位置的快顯](./media/popup-placement-behavior/popup-placement-left.png "Placement 為 Left。")
  
 ![具有 Mouse 位置的快顯](./media/popup-placement-behavior/popup-placement-mouse.png "Placement 為 Mouse。")  
  
 ![具有 MousePoint 位置的快顯](./media/popup-placement-behavior/popup-placement-mousepoint.png "Placement 為 MousePoint。")  
  
 ![具有 Relative 或 RelativePoint 位置的快顯](./media/popup-placement-behavior/popup-placement-relative.png "Placement 為 Relative 或 RelativePoint。")
  
 ![具有 Right 位置的快顯](./media/popup-placement-behavior/popup-placement-right.png "Placement 為 Right。")
  
 ![具有 Top 位置的快顯](./media/popup-placement-behavior/popup-placement-top.png "Placement 為 Top。")
  
<a name="When"></a>
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>當快顯遇到畫面邊緣時  
 為了安全起見，畫面邊緣無法隱藏 <xref:System.Windows.Controls.Primitives.Popup>。 當 <xref:System.Windows.Controls.Primitives.Popup> 遇到畫面邊緣時，即會發生下列三種情況的其中一種：  
  
- 快顯本身會重新對齊將遮蔽 <xref:System.Windows.Controls.Primitives.Popup> 的畫面邊緣。  
  
- 快顯會使用不同的快顯對齊點。  
  
- 快顯會使用不同的目標原點和快顯對齊點。  
  
 本節稍後會進一步說明這些選項。  
  
 當遇到畫面邊緣時，<xref:System.Windows.Controls.Primitives.Popup> 的行為取決於 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 屬性的值，以及快顯遇到的畫面邊緣。 下表摘述 <xref:System.Windows.Controls.Primitives.Popup> 遇到每個 <xref:System.Windows.Controls.Primitives.PlacementMode> 值其畫面邊緣時的行為。  
  
|PlacementMode|上邊緣|下邊緣|左邊緣|右邊緣|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|對齊上邊緣。|對齊下邊緣。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|對齊上邊緣。|快顯對齊點變更至 <xref:System.Windows.Controls.Primitives.Popup> 的左下角。|對齊左邊緣。|快顯對齊點變更至 <xref:System.Windows.Controls.Primitives.Popup> 的右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|對齊上邊緣。|目標來源變更至目標區域的左上角，且快顯對齊點變更至 <xref:System.Windows.Controls.Primitives.Popup> 的左下角。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|對齊上邊緣。|對齊下邊緣。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|對齊上邊緣。|對齊下邊緣。|目標來源變更至目標區域的右上角，且快顯對齊點變更至 <xref:System.Windows.Controls.Primitives.Popup> 的左上角。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|對齊上邊緣。|目標來源變更至目標區域的左上角 (滑鼠指標的繫結)，且快顯對齊點變更至 <xref:System.Windows.Controls.Primitives.Popup> 的左下角。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|對齊上邊緣。|快顯對齊點變更至 <xref:System.Windows.Controls.Primitives.Popup> 的左下角。|對齊左邊緣。|快顯對齊點會變更至快顯的右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|對齊上邊緣。|對齊下邊緣。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|對齊上邊緣。|快顯對齊點變更至 <xref:System.Windows.Controls.Primitives.Popup> 的左下角。|對齊左邊緣。|快顯對齊點會變更至快顯的右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|對齊上邊緣。|對齊下邊緣。|對齊左邊緣。|目標來源變更至目標區域的左上角，且快顯對齊點變更至 <xref:System.Windows.Controls.Primitives.Popup> 的右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|目標來源變更至目標區域的左下角，且快顯對齊點變更至 <xref:System.Windows.Controls.Primitives.Popup> 的左上角。 實際上，這與 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 為 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> 時相同。|對齊下邊緣。|對齊左邊緣。|對齊右邊緣。|  
  
### <a name="aligning-to-the-screen-edge"></a>對齊畫面邊緣  
 <xref:System.Windows.Controls.Primitives.Popup> 本身可重新置放以對齊畫面邊緣，這樣畫面上即可看到整個 <xref:System.Windows.Controls.Primitives.Popup>。  當發生此情況時，目標來源與快顯對齊點之間距離可能會不同於 <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 的值。 當 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 為 <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>、<xref:System.Windows.Controls.Primitives.PlacementMode.Center> 或 <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> 時，<xref:System.Windows.Controls.Primitives.Popup> 本身會對齊每個畫面邊緣。  例如，假設 <xref:System.Windows.Controls.Primitives.Popup> 將 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 設為 <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> 且 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 設為 100。  如果畫面下邊緣隱藏全部或部分 <xref:System.Windows.Controls.Primitives.Popup>，則 <xref:System.Windows.Controls.Primitives.Popup> 本身會沿著畫面下邊緣重新置放，且目標來源與快顯對齊點之間的垂直距離少於 100。 下圖示範這種情況。  
  
 ![與畫面邊緣對齊的快顯](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "快顯對齊畫面邊緣。")
  
### <a name="changing-the-popup-alignment-point"></a>變更快顯對齊點  
 如果 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 為 <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>、<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint> 或 <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>，則當快顯遇到畫面下邊緣或右邊緣時，快顯對齊點即會產生變化。  
  
 下圖示範當畫面下邊緣隱藏全部或部分 <xref:System.Windows.Controls.Primitives.Popup> 時，則快顯對齊點位於 <xref:System.Windows.Controls.Primitives.Popup> 的左下角。  
  
 ![因畫面下邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "快顯遇到畫面下邊緣而變更快顯對齊點。")  

 下圖示範當畫面右邊緣隱藏 <xref:System.Windows.Controls.Primitives.Popup> 時，則快顯對齊點位於 <xref:System.Windows.Controls.Primitives.Popup> 的右上角。  
  
 ![因畫面邊緣而導致的新快顯對齊點](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "快顯遇到畫面右邊緣而變更快顯對齊點。")
  
 如果 <xref:System.Windows.Controls.Primitives.Popup> 遇到畫面下邊緣與右邊緣時，則快顯對齊點位於 <xref:System.Windows.Controls.Primitives.Popup> 的右下角。  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>變更目標原點和快顯對齊點  
 當 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 為 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>、<xref:System.Windows.Controls.Primitives.PlacementMode.Left>、<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>、<xref:System.Windows.Controls.Primitives.PlacementMode.Right> 或 <xref:System.Windows.Controls.Primitives.PlacementMode.Top> 時，如果遇到特定的畫面邊緣，目標來源與快顯對齊點即會產生變化。  造成位置產生變化的畫面邊緣取決於 <xref:System.Windows.Controls.Primitives.PlacementMode> 值。  
  
 下圖示範當 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 為 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> 且 <xref:System.Windows.Controls.Primitives.Popup> 遇到畫面下邊緣時，則目標來源位於目標區域的右上角，且快顯對齊點位於 <xref:System.Windows.Controls.Primitives.Popup> 的左下角。  
  
 ![因畫面下邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "Placement 為 Bottom 且快顯遇到畫面下邊緣。")
  
 下圖示範當 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 為 <xref:System.Windows.Controls.Primitives.PlacementMode.Left> 且 <xref:System.Windows.Controls.Primitives.Popup> 遇到畫面下邊緣時，則目標來源位於目標區域的上角，且快顯對齊點位於 <xref:System.Windows.Controls.Primitives.Popup> 的左上角。  
  
 ![因畫面左邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "Placement 為 Left 且快顯遇到畫面左邊緣。")  
  
 下圖示範當 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 為 <xref:System.Windows.Controls.Primitives.PlacementMode.Right> 且 <xref:System.Windows.Controls.Primitives.Popup> 遇到畫面下邊緣時，則目標來源位於目標區域的左上角，且快顯對齊點位於 <xref:System.Windows.Controls.Primitives.Popup> 的右上角。  
  
 ![因畫面右邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "Placement 為 Right 且快顯遇到畫面右邊緣。")  

 下圖示範當 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 為 <xref:System.Windows.Controls.Primitives.PlacementMode.Top> 且 <xref:System.Windows.Controls.Primitives.Popup> 遇到畫面下邊緣時，則目標來源位於目標區域的左下角，且快顯對齊點位於 <xref:System.Windows.Controls.Primitives.Popup> 的左角。  
  
 ![因畫面上邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "Placement 為 Top 且快顯遇到畫面上邊緣。")  
  
 下圖示範當 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 為 <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> 且 <xref:System.Windows.Controls.Primitives.Popup> 遇到畫面下邊緣時，則目標來源位於目標區域 (滑鼠指標範圍) 的左上角，且快顯對齊點位於 <xref:System.Windows.Controls.Primitives.Popup> 的左下角。  
  
 ![因滑鼠靠近畫面邊緣而導致的新對齊點](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "Placement 為 Mouse 且快顯遇到畫面下邊緣。")
  
### <a name="customizing-popup-placement"></a>自訂快顯位置  
 您可透過將 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 屬性設為 <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>，以自訂目標來源與快顯對齊點。 然後定義 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> 委派，其傳回一組 <xref:System.Windows.Controls.Primitives.Popup>可能的放置點與主軸 (以偏好順序)。 顯示已選取 <xref:System.Windows.Controls.Primitives.Popup> 最大部分的點。  如果畫面邊緣隱藏 <xref:System.Windows.Controls.Primitives.Popup>，則會自動調整 <xref:System.Windows.Controls.Primitives.Popup> 的位置。 如需範例，請參閱[指定自訂快顯位置](how-to-specify-a-custom-popup-position.md)。  
  
## <a name="see-also"></a>另請參閱

- [快顯位置範例](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
