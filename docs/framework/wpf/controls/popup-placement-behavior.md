---
title: 快顯功能表放置行為
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: 99875de320d6728fdacb55c153064c5c1267efdf
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362921"
---
# <a name="popup-placement-behavior"></a>快顯功能表放置行為
A<xref:System.Windows.Controls.Primitives.Popup>控制項會顯示在不同的視窗會漂浮在應用程式的內容。 您可以指定的位置<xref:System.Windows.Controls.Primitives.Popup>相對於控制項、 滑鼠或使用螢幕<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>， <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>， <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>， <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>，和<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>屬性。  若要讓您靈活地指定的位置，這些屬性一起運作<xref:System.Windows.Controls.Primitives.Popup>。  
  
> [!NOTE]
>  <xref:System.Windows.Controls.ToolTip>和<xref:System.Windows.Controls.ContextMenu>類別也會定義這五個屬性，並具有類似的行為。  
  

  
<a name="Positioning"></a>   
## <a name="positioning-the-popup"></a>設定快顯位置  
 放置<xref:System.Windows.Controls.Primitives.Popup>可以是相對於<xref:System.Windows.UIElement>或整個螢幕。  下列範例會建立四個<xref:System.Windows.Controls.Primitives.Popup>控制項的相對<xref:System.Windows.UIElement>— 在此案例中，映像。 所有<xref:System.Windows.Controls.Primitives.Popup>控制項都<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>屬性設定為`image1`，但每個<xref:System.Windows.Controls.Primitives.Popup>有不同的位置屬性的值。  
  
 [!code-xaml[PopupPositionSnippet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 下圖顯示映像和<xref:System.Windows.Controls.Primitives.Popup>控制項  
  
 ![具有四個 popup 控制項的影像](../../../../docs/framework/wpf/controls/media/popupplacementintro.png "PopupPlacementIntro")  
搭配四個快顯的影像  
  
 這個簡單的範例示範如何設定<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>並<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性，但使用<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>， <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>，和<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>屬性，您可以更多控制的位置<xref:System.Windows.Controls.Primitives.Popup>位於。  
  
<a name="Definitions"></a>   
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>詞彙的定義：快顯剖析  
 下列詞彙可協助您了解如何<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>， <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>， <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>， <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>，並<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>相互關聯屬性和<xref:System.Windows.Controls.Primitives.Popup>:  
  
-   目標物件  
  
-   目標區域  
  
-   目標原點  
  
-   快顯對齊點  
  
 這些詞彙提供便利的方式來參考的各個層面<xref:System.Windows.Controls.Primitives.Popup>和其相關聯的控制項。  
  
### <a name="target-object"></a>目標物件  
 *目標物件*是項目，<xref:System.Windows.Controls.Primitives.Popup>相關聯。 如果<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>屬性設定，它會指定目標物件。  如果<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>未設定，而<xref:System.Windows.Controls.Primitives.Popup>具有父代，父代是目標物件。  如果沒有任何<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>值並沒有父代，沒有目標物件，而<xref:System.Windows.Controls.Primitives.Popup>相對於畫面。  
  
 下列範例會建立<xref:System.Windows.Controls.Primitives.Popup>也就是子系<xref:System.Windows.Controls.Canvas>。  此範例不會設定<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>屬性上的<xref:System.Windows.Controls.Primitives.Popup>。 預設值<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>已<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>，因此<xref:System.Windows.Controls.Primitives.Popup>請參閱下文<xref:System.Windows.Controls.Canvas>。  
  
 [!code-xaml[PopupPositionSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 下圖顯示<xref:System.Windows.Controls.Primitives.Popup>的相對位置<xref:System.Windows.Controls.Canvas>。  
  
 ![沒有 placementtarget 的快顯視窗控制項](../../../../docs/framework/wpf/controls/media/popupplacementnoplacementtarget.PNG "PopupPlacementNoPlacementTarget")  
沒有 PlacementTarget 的快顯  
  
 下列範例會建立<xref:System.Windows.Controls.Primitives.Popup>也就是子系<xref:System.Windows.Controls.Canvas>，但這次<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>設定為`ellipse1`，因此快顯視窗會出現下方<xref:System.Windows.Shapes.Ellipse>。  
  
 [!code-xaml[PopupPositionSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 下圖顯示<xref:System.Windows.Controls.Primitives.Popup>的相對位置<xref:System.Windows.Shapes.Ellipse>。  
  
 ![相對於橢圓形置放的快顯](../../../../docs/framework/wpf/controls/media/popupplacementwithplacementtarget.PNG "PopupPlacementWithPlacementTarget")  
具有 PlacementTarget 的快顯  
  
> [!NOTE]
>  針對<xref:System.Windows.Controls.ToolTip>，預設值<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>是<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>。  針對<xref:System.Windows.Controls.ContextMenu>，預設值<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>是<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>。 稍後在＜屬性如何一起運作＞中會說明這些值。  
  
### <a name="target-area"></a>目標區域  
 *目標區域*是在螢幕上的區域，<xref:System.Windows.Controls.Primitives.Popup>是相對於。 在上一個範例中，<xref:System.Windows.Controls.Primitives.Popup>界限的目標物件，但在某些情況下，與對齊<xref:System.Windows.Controls.Primitives.Popup>會配合其他範圍中，即使<xref:System.Windows.Controls.Primitives.Popup>已有目標物件。  如果<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>屬性設定、 目標區域是不同於目標物件的界限。  
  
 下列範例會建立兩個<xref:System.Windows.Controls.Canvas>物件，其中包含每個<xref:System.Windows.Shapes.Rectangle>和<xref:System.Windows.Controls.Primitives.Popup>。  在這兩種情況下，目標物件<xref:System.Windows.Controls.Primitives.Popup>是<xref:System.Windows.Controls.Canvas>。 <xref:System.Windows.Controls.Primitives.Popup>第一次<xref:System.Windows.Controls.Canvas>已<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定，以其<xref:System.Windows.Rect.X%2A>， <xref:System.Windows.Rect.Y%2A>， <xref:System.Windows.Rect.Width%2A>，和<xref:System.Windows.Rect.Height%2A>屬性分別設定為 50、 50、 50 和 100。 <xref:System.Windows.Controls.Primitives.Popup>中，第二個<xref:System.Windows.Controls.Canvas>沒有<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定。  如此一來，第一個<xref:System.Windows.Controls.Primitives.Popup>位於下面<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>，第二個<xref:System.Windows.Controls.Primitives.Popup>位於以下<xref:System.Windows.Controls.Canvas>。 每個<xref:System.Windows.Controls.Canvas>也包含<xref:System.Windows.Shapes.Rectangle>具有相同的範圍<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>前<xref:System.Windows.Controls.Primitives.Popup>。  請注意，<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>不會建立可見的項目中的應用程式; 此範例會建立<xref:System.Windows.Shapes.Rectangle>來代表<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  
  
 [!code-xaml[PopupPositionSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 下圖顯示上述範例的結果。  
  
 ![具有和沒有 PlacementRectangle 的快顯](../../../../docs/framework/wpf/controls/media/popupplacementplacementrectangle.PNG "PopupPlacementPlacementRectangle")  
具有和沒有 PlacementRectangle 的快顯  
  
### <a name="target-origin-and-popup-alignment-point"></a>目標原點和快顯對齊點  
 「目標原點」和「快顯對齊點」分別是目標區域和快顯上的參考點，用來進行定位。 您可以使用<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>和<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>位移設定快顯距離目標區域的屬性。  <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>和<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>相對於目標原點與快顯對齊點。 值<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性會決定目標原點和快顯對齊點的所在位置。  
  
 下列範例會建立<xref:System.Windows.Controls.Primitives.Popup>，並設定<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>和<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>屬性為 20。  <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性設定為<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>（預設值），因此目標原點會是目標區域的左下角和快顯對齊點則是左上角的<xref:System.Windows.Controls.Primitives.Popup>。  
  
 [!code-xaml[PopupPositionSnippet#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 下圖顯示上述範例的結果。  
  
 ![具有目標原始對齊點的快顯位置](../../../../docs/framework/wpf/controls/media/popupplacementtargetoriginalignmentpoint.PNG "PopupPlacementTargetOriginAlignmentPoint")  
具有 HorizontalOffset 和 VerticalOffset 的快顯  
  
<a name="How"></a>   
## <a name="how-the-properties-work-together"></a>屬性如何一起運作  
 值<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>， <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>，和<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>必須一起考量，才能找出正確的目標區域、 目標原點和快顯對齊點。  例如，如果的值<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>是<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>，沒有目標物件，<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>會被忽略，且目標區域為滑鼠指標的範圍。 相反地，如果<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>已<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>，則<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父代會決定目標物件和<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>會決定目標區域。  
  
 下表描述的目標物件、 目標區域、 目標原點和快顯對齊點，並指出是否<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>並<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>用於每個<xref:System.Windows.Controls.Primitives.PlacementMode>列舉值。  
  
|PlacementMode|目標物件|目標區域|目標原點|快顯對齊點|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|不適用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 會被忽略。|畫面上，或<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>如果設定。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於畫面。|目標區域的左上角。|左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|不適用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 會被忽略。|畫面上，或<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>如果設定。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於畫面。|目標區域的左上角。|左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父代。|目標物件或<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>如果設定。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件。|目標區域的左下角。|左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父代。|目標物件或<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>如果設定。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件。|目標區域的中央。|中心<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父代。|目標物件或<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>如果設定。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件。|藉由定義<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>。|藉由定義<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父代。|目標物件或<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>如果設定。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件。|目標區域的左上角。|右上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|不適用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 會被忽略。|滑鼠指標的範圍。 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 會被忽略。|目標區域的左下角。|左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|不適用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 會被忽略。|滑鼠指標的範圍。 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 會被忽略。|目標區域的左上角。|左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父代。|目標物件或<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>如果設定。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件。|目標區域的左上角。|左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父代。|目標物件或<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>如果設定。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件。|目標區域的左上角。|左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父代。|目標物件或<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>如果設定。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件。|目標區域的右上角。|左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父代。|目標物件或<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>如果設定。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相對於目標物件。|目標區域的左上角。|左下角<xref:System.Windows.Controls.Primitives.Popup>。|  
  
 下列圖例顯示<xref:System.Windows.Controls.Primitives.Popup>，目標區域、 目標原點及快顯對齊點針對每個<xref:System.Windows.Controls.Primitives.PlacementMode>值。 在每個圖中，目標區域是黃色，而<xref:System.Windows.Controls.Primitives.Popup>是藍色。  
  
 ![具有 Absolute 或 AbsolutePoint 位置的 popup](../../../../docs/framework/wpf/controls/media/popupplacementabsolute.png "PopupPlacementAbsolute")  
Placement 為 Absolute 或 AbsolutePoint  
  
 ![具有 Bottom 位置的快顯](../../../../docs/framework/wpf/controls/media/popupplacementbottom.png "PopupPlacementBottom")  
Placement 為 Bottom  
  
 ![具有 Center 位置的 popup](../../../../docs/framework/wpf/controls/media/popupplacementcenter.png "PopupPlacementCenter")  
Placement 為 Center  
  
 ![具有 Left 位置的快顯](../../../../docs/framework/wpf/controls/media/popupplacementleft.png "PopupPlacementLeft")  
Placement 為 Left  
  
 ![具有 Mouse 位置的快顯](../../../../docs/framework/wpf/controls/media/popupplacementmouse.png "PopupPlacementMouse")  
Placement 為 Mouse  
  
 ![具有 MousePoint 位置的 popup](../../../../docs/framework/wpf/controls/media/popupplacementmousepoint.png "PopupPlacementMousePoint")  
Placement 為 MousePoint  
  
 ![具有 Relative 或 RelativePoint 位置的 popup](../../../../docs/framework/wpf/controls/media/popupplacementrelative.png "PopupPlacementRelative")  
Placement 為 Relative 或 RelativePoint  
  
 ![具有 Right 位置的快顯](../../../../docs/framework/wpf/controls/media/popupplacementright.png "PopupPlacementRight")  
Placement 為 Right  
  
 ![具有 Top 位置的快顯](../../../../docs/framework/wpf/controls/media/popupplacementtop.png "PopupPlacementTop")  
Placement 為 Top  
  
<a name="When"></a>   
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>當快顯遇到畫面邊緣時  
 基於安全性理由，<xref:System.Windows.Controls.Primitives.Popup>無法螢幕的邊緣遮住。 下列三件事的其中一個發生時<xref:System.Windows.Controls.Primitives.Popup>遇到畫面邊緣：  
  
-   快顯視窗本身會遮蔽的畫面邊緣<xref:System.Windows.Controls.Primitives.Popup>。  
  
-   快顯會使用不同的快顯對齊點。  
  
-   快顯會使用不同的目標原點和快顯對齊點。  
  
 本節稍後會進一步說明這些選項。  
  
 行為<xref:System.Windows.Controls.Primitives.Popup>時遇到畫面邊緣取決於值<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性，以及哪些畫面快顯遇到的邊界。 下表摘要說明的行為時<xref:System.Windows.Controls.Primitives.Popup>遇到畫面邊緣，為每個<xref:System.Windows.Controls.Primitives.PlacementMode>值。  
  
|PlacementMode|上邊緣|下邊緣|左邊緣|右邊緣|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|對齊上邊緣。|對齊下邊緣。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|對齊上邊緣。|快顯對齊點會變更至左下角<xref:System.Windows.Controls.Primitives.Popup>。|對齊左邊緣。|快顯對齊點會變更至右上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|對齊上邊緣。|目標原點會變更至目標區域的左上角和快顯對齊點會變更至左下角<xref:System.Windows.Controls.Primitives.Popup>。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|對齊上邊緣。|對齊下邊緣。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|對齊上邊緣。|對齊下邊緣。|目標原點會變更至目標區域的右上角，並變更至左上角的快顯對齊點<xref:System.Windows.Controls.Primitives.Popup>。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|對齊上邊緣。|目標原點會變更至目標區域 （滑鼠指標的範圍） 的左上角和快顯對齊點會變更至左下角<xref:System.Windows.Controls.Primitives.Popup>。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|對齊上邊緣。|快顯對齊點會變更至左下角<xref:System.Windows.Controls.Primitives.Popup>。|對齊左邊緣。|快顯對齊點會變更至快顯的右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|對齊上邊緣。|對齊下邊緣。|對齊左邊緣。|對齊右邊緣。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|對齊上邊緣。|快顯對齊點會變更至左下角<xref:System.Windows.Controls.Primitives.Popup>。|對齊左邊緣。|快顯對齊點會變更至快顯的右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|對齊上邊緣。|對齊下邊緣。|對齊左邊緣。|目標原點會變更至目標區域的左上角和右上角的快顯對齊點變更<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|目標原點會變更至目標區域的左下角，並變更至左上角的快顯對齊點<xref:System.Windows.Controls.Primitives.Popup>。 實際上，這等同於何時<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>是<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>。|對齊下邊緣。|對齊左邊緣。|對齊右邊緣。|  
  
### <a name="aligning-to-the-screen-edge"></a>對齊畫面邊緣  
 A<xref:System.Windows.Controls.Primitives.Popup>可以對齊螢幕的邊緣調整自己的位置因此整個<xref:System.Windows.Controls.Primitives.Popup>會顯示在螢幕上。  當發生這種情況時，目標原點和快顯對齊點之間的距離可能會與不同的值從<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>和<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>。 當<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>已<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>， <xref:System.Windows.Controls.Primitives.PlacementMode.Center>，或<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>，則<xref:System.Windows.Controls.Primitives.Popup>本身會將每個畫面邊緣對齊。  例如，假設<xref:System.Windows.Controls.Primitives.Popup>已經<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>設為<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>和<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>設為 100。  如果畫面下的邊緣會隱藏所有或部分<xref:System.Windows.Controls.Primitives.Popup>，則<xref:System.Windows.Controls.Primitives.Popup>調整自己的位置的螢幕和目標原點與快顯視窗之間的垂直距離的下邊緣對齊點則是小於 100。 下圖示範這種情況。  
  
 ![對齊畫面邊緣的快顯](../../../../docs/framework/wpf/controls/media/popupplacementrelativescreenedge.png "PopupPlacementRelativeScreenEdge")  
快顯對齊畫面的邊緣  
  
### <a name="changing-the-popup-alignment-point"></a>變更快顯對齊點  
 如果<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>已<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>， <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>，或<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>，快顯對齊點變更時快顯遇到畫面右邊緣的底部。  
  
 下圖示範當畫面下邊緣會隱藏所有或部分<xref:System.Windows.Controls.Primitives.Popup>，快顯對齊點則是左下角的<xref:System.Windows.Controls.Primitives.Popup>。  
  
 ![因為底部畫面邊緣造成的新對齊點](../../../../docs/framework/wpf/controls/media/popupplacementrelativepointscreenedge.png "PopupPlacementRelativePointScreenEdge")  
快顯遇到畫面的下邊緣而變更快顯對齊點  
  
 下圖示範當<xref:System.Windows.Controls.Primitives.Popup>隱藏畫面右邊緣，快顯對齊點則是右上方的角<xref:System.Windows.Controls.Primitives.Popup>。  
  
 ![因為畫面邊緣造成的新快顯對齊點](../../../../docs/framework/wpf/controls/media/popupplacementrelativepointrightscreenedge.png "PopupPlacementRelativePointRightScreenEdge")  
快顯遇到畫面的右邊緣而變更快顯對齊點  
  
 如果<xref:System.Windows.Controls.Primitives.Popup>遇到下框線和畫面右邊緣，快顯對齊點則是右下角的<xref:System.Windows.Controls.Primitives.Popup>。  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>變更目標原點和快顯對齊點  
 當<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>已<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>， <xref:System.Windows.Controls.Primitives.PlacementMode.Left>， <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>， <xref:System.Windows.Controls.Primitives.PlacementMode.Right>，或<xref:System.Windows.Controls.Primitives.PlacementMode.Top>，目標原點和快顯對齊點的變更，如果遇到某個畫面邊緣。  會造成變更位置的畫面邊緣取決於<xref:System.Windows.Controls.Primitives.PlacementMode>值。  
  
 下圖示範當<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>已<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>而<xref:System.Windows.Controls.Primitives.Popup>遇到畫面下邊緣，目標原點會是目標區域的左上角和快顯對齊點則是左下角的<xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![因為底部畫面邊緣造成的新對齊點](../../../../docs/framework/wpf/controls/media/popupplacementbottomscreenedge.png "PopupPlacementBottomScreenEdge")  
Placement 為 Bottom 且快顯遇到畫面下邊緣  
  
 下圖示範當<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>已<xref:System.Windows.Controls.Primitives.PlacementMode.Left>而<xref:System.Windows.Controls.Primitives.Popup>遇到畫面左邊的緣，目標原點會是目標區域的右上角和快顯對齊點則是左上方的角<xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![因為左邊的畫面邊緣造成的新對齊點](../../../../docs/framework/wpf/controls/media/popupplacementleftscreenedge.png "PopupPlacementLeftScreenEdge")  
Placement 為 Left 且快顯遇到畫面左邊緣  
  
 下圖示範當<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>已<xref:System.Windows.Controls.Primitives.PlacementMode.Right>而<xref:System.Windows.Controls.Primitives.Popup>遇到畫面右邊緣，目標原點會是目標區域的左上角和快顯對齊點則是右上角的<xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![因畫面右邊緣而導致的新對齊點](../../../../docs/framework/wpf/controls/media/popupplacementrightscreenedge.png "PopupPlacementRightScreenEdge")  
Placement 為 Right 且快顯遇到畫面右邊緣  
  
 下圖示範當<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>已<xref:System.Windows.Controls.Primitives.PlacementMode.Top>而<xref:System.Windows.Controls.Primitives.Popup>遇到畫面邊緣，目標原點會是目標區域的左下角和快顯對齊點則是左上角的<xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![因為頂端畫面邊緣造成的新對齊點](../../../../docs/framework/wpf/controls/media/popupplacementtopscreenedge.png "PopupPlacementTopScreenEdge")  
Placement 為 Top 且快顯遇到畫面上邊緣  
  
 下圖示範當<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>已<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>而<xref:System.Windows.Controls.Primitives.Popup>遇到畫面下邊緣，目標原點會是目標區域 （滑鼠指標的範圍） 和快顯功能表對齊左上角點則是左下角的<xref:System.Windows.Controls.Primitives.Popup>。  
  
 ![因為滑鼠附近畫面邊緣造成的新對齊點](../../../../docs/framework/wpf/controls/media/popupplacementmousescreenedge.png "PopupPlacementMouseScreenEdge")  
Placement 為 Mouse 且快顯遇到畫面下邊緣  
  
### <a name="customizing-popup-placement"></a>自訂快顯位置  
 您可以設定連線，來自訂目標原點和快顯對齊點<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性設<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>。 然後定義<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>傳回一組可能的位置點和主要軸 （依偏好順序） 的委派<xref:System.Windows.Controls.Primitives.Popup>。 顯示的最大部分的點<xref:System.Windows.Controls.Primitives.Popup>已選取。  位置<xref:System.Windows.Controls.Primitives.Popup>會自動調整，如果<xref:System.Windows.Controls.Primitives.Popup>畫面邊緣遮住。 如需範例，請參閱[指定自訂快顯位置](../../../../docs/framework/wpf/controls/how-to-specify-a-custom-popup-position.md)。  
  
## <a name="see-also"></a>另請參閱  
 [快顯位置範例](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
