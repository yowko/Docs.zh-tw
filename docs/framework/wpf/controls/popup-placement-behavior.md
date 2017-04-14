---
title: "快顯功能表放置行為 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "快顯功能表"
  - "Popup 控制項放置"
  - "放置快顯功能表"
  - "定位快顯功能表"
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 快顯功能表放置行為
A<xref:System.Windows.Controls.Primitives.Popup>控制項會漂浮在應用程式的另一個視窗中顯示內容。 您可以指定的位置<xref:System.Windows.Controls.Primitives.Popup>相對於控制項、 滑鼠或使用螢幕<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>，<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>，<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>， <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>，和<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>屬性。  這些屬性一起工作，以讓您彈性地指定位置的<xref:System.Windows.Controls.Primitives.Popup>。  
  
> [!NOTE]
>  <xref:System.Windows.Controls.ToolTip>和<xref:System.Windows.Controls.ContextMenu>類別也定義這五個屬性，並具有類似的行為。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Positioning"></a>   
## <a name="positioning-the-popup"></a>定位快顯視窗  
 位置的<xref:System.Windows.Controls.Primitives.Popup>可以是相對於<xref:System.Windows.UIElement>或整個螢幕。  下列範例會建立四個<xref:System.Windows.Controls.Primitives.Popup>控制項的相對<xref:System.Windows.UIElement>— 在此情況下，映像。 所有的<xref:System.Windows.Controls.Primitives.Popup>控制項具有<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>屬性設定為`image1`，但每個<xref:System.Windows.Controls.Primitives.Popup>具有放置屬性不同的值。  
  
 [!code-xml[PopupPositionSnippet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 下圖顯示的影像和<xref:System.Windows.Controls.Primitives.Popup>控制項  
  
 ![具有四個 popup 控制項的影像](../../../../docs/framework/wpf/controls/media/popupplacementintro.png "PopupPlacementIntro")  
具有四個快顯功能表的影像  
  
 這個簡單的範例示範如何設定<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>和<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性，但若使用<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>， <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>，和<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>屬性，您有更多控制的位置<xref:System.Windows.Controls.Primitives.Popup>位於。  
  
<a name="Definitions"></a>   
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>詞彙的定義︰ 快顯視窗的剖析  
 下列詞彙可用於了解如何<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>，<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>，<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>， <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>，和<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>屬性相互關聯和<xref:System.Windows.Controls.Primitives.Popup>:  
  
-   目標物件  
  
-   目標區域  
  
-   目標原點  
  
-   快顯對齊點  
  
 這些條款提供便利的方式來參考的各種層面<xref:System.Windows.Controls.Primitives.Popup>以及與其相關聯的控制項。  
  
### <a name="target-object"></a>目標物件  
 *目標物件*是項目，<xref:System.Windows.Controls.Primitives.Popup>相關聯。 如果<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>屬性設定，它會指定目標物件。  如果<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>未設定，而<xref:System.Windows.Controls.Primitives.Popup>有父代，父代是目標物件。  如果沒有任何<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>值並沒有父代，沒有目標的物件，而<xref:System.Windows.Controls.Primitives.Popup>位於螢幕。  
  
 下列範例會建立<xref:System.Windows.Controls.Primitives.Popup>也就是子系<xref:System.Windows.Controls.Canvas>。  此範例不會設定<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>屬性<xref:System.Windows.Controls.Primitives.Popup>。 預設值為<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>是<xref:System.Windows.Controls.Primitives.PlacementMode?displayProperty=fullName>，因此<xref:System.Windows.Controls.Primitives.Popup>下方出現<xref:System.Windows.Controls.Canvas>。  
  
 [!code-xml[PopupPositionSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 下圖顯示<xref:System.Windows.Controls.Primitives.Popup>的相對位置<xref:System.Windows.Controls.Canvas>。  
  
 ![不含 PlacementTarget 的 popup 控制項](../../../../docs/framework/wpf/controls/media/popupplacementnoplacementtarget.png "PopupPlacementNoPlacementTarget")  
不含 PlacementTarget 的 popup  
  
 下列範例會建立<xref:System.Windows.Controls.Primitives.Popup>也就是子系<xref:System.Windows.Controls.Canvas>，但這次<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>設為`ellipse1`，因此快顯視窗會出現下方<xref:System.Windows.Shapes.Ellipse>。  
  
 [!code-xml[PopupPositionSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 下圖顯示<xref:System.Windows.Controls.Primitives.Popup>的相對位置<xref:System.Windows.Shapes.Ellipse>。  
  
 ![相對於橢圓形置放的 popup](../../../../docs/framework/wpf/controls/media/popupplacementwithplacementtarget.png "PopupPlacementWithPlacementTarget")  
含 PlacementTarget 的 popup  
  
> [!NOTE]
>  如<xref:System.Windows.Controls.ToolTip>，預設值的<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>是<xref:System.Windows.Controls.Primitives.PlacementMode>。  如<xref:System.Windows.Controls.ContextMenu>，預設值的<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>是<xref:System.Windows.Controls.Primitives.PlacementMode>。 這些值會說明更新版本中，「 如何屬性工作一起 」。  
  
### <a name="target-area"></a>目標區域  
 *目標區域*是在螢幕上的區域，<xref:System.Windows.Controls.Primitives.Popup>是相對於。 在上一個範例中，<xref:System.Windows.Controls.Primitives.Popup>對齊界限的目標物件，但在某些情況下，<xref:System.Windows.Controls.Primitives.Popup>對齊其他範圍中，即使<xref:System.Windows.Controls.Primitives.Popup>都有一個目標物件。  如果<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>屬性設定，則目標區域是不同於目標物件的界限。  
  
 下列範例會建立兩個<xref:System.Windows.Controls.Canvas>物件，其中包含每個<xref:System.Windows.Shapes.Rectangle>和<xref:System.Windows.Controls.Primitives.Popup>。  在這兩種情況下，目標物件<xref:System.Windows.Controls.Primitives.Popup>是<xref:System.Windows.Controls.Canvas>。 <xref:System.Windows.Controls.Primitives.Popup>第一次<xref:System.Windows.Controls.Canvas>有<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定，以其<xref:System.Windows.Rect.X%2A>， <xref:System.Windows.Rect.Y%2A>，<xref:System.Windows.Rect.Width%2A>，和<xref:System.Windows.Rect.Height%2A>屬性分別設定為 50，50，50，100。 <xref:System.Windows.Controls.Primitives.Popup>，第二個<xref:System.Windows.Controls.Canvas>沒有<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定。  如此一來，第一個<xref:System.Windows.Controls.Primitives.Popup>位於以下<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ，第二個<xref:System.Windows.Controls.Primitives.Popup>位於以下<xref:System.Windows.Controls.Canvas>。 每個<xref:System.Windows.Controls.Canvas>也包含<xref:System.Windows.Shapes.Rectangle>具有相同的範圍為<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>前<xref:System.Windows.Controls.Primitives.Popup>。  請注意，<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>不會建立可見的項目在應用程式; 此範例會建立<xref:System.Windows.Shapes.Rectangle>來代表<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  
  
 [!code-xml[PopupPositionSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 下圖顯示先前範例的結果。  
  
 ![與不含 PlacementRectangle 的 popup](../../../../docs/framework/wpf/controls/media/popupplacementplacementrectangle.png "PopupPlacementPlacementRectangle")  
包含與不含 PlacementRectangle 的 Popup  
  
### <a name="target-origin-and-popup-alignment-point"></a>目標原點與快顯對齊點  
 *目標原點*和*快顯對齊點*分別參考點上的目標區域和快顯視窗中，所使用的位置。 您可以使用<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>和<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>位移快顯視窗中的從目標區域的屬性。  <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>和<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>相對於目標原點與快顯對齊點。 值<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性會決定目標原點，並且快顯對齊點的位置。  
  
 下列範例會建立<xref:System.Windows.Controls.Primitives.Popup>，並設定<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>和<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>屬性為 20。  <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性設定為<xref:System.Windows.Controls.Primitives.PlacementMode>（預設值），因此目標原點是目標區域的左下角，且快顯對齊點的左上角<xref:System.Windows.Controls.Primitives.Popup>。  
  
 [!code-xml[PopupPositionSnippet#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 下圖顯示先前範例的結果。  
  
 ![具有目標原始對齊點的 popup 位置](../../../../docs/framework/wpf/controls/media/popupplacementtargetoriginalignmentpoint.PNG "PopupPlacementTargetOriginAlignmentPoint")  
HorizontalOffset 與 VerticalOffset 快顯視窗  
  
<a name="How"></a>   
## <a name="how-the-properties-work-together"></a>屬性如何搭配運作  
 值<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>，<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>，和<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>需要一併考慮，找出正確的目標區域、 目標原點和快顯對齊點。  比方說，如果值<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>是<xref:System.Windows.Controls.Primitives.PlacementMode>，沒有目標的物件，<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>會被忽略，而且目標區域滑鼠指標的範圍。 相反地，如果<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>是<xref:System.Windows.Controls.Primitives.PlacementMode>、 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父決定目標物件和<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>判斷目標區域。  
  
 下表描述的目標物件、 目標區域、 目標原點和快顯對齊點，並指出是否<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>和<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>用於每個<xref:System.Windows.Controls.Primitives.PlacementMode>列舉值。  
  
|PlacementMode|目標物件|目標區域|目標原點|快顯對齊點|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|不適用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>會被忽略。|畫面上，或<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>如果設定。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>相對於螢幕。|目標區域的左上角。|左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|不適用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>會被忽略。|畫面上，或<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>如果設定。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>相對於螢幕。|目標區域的左上角。|左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父代。|目標物件，或<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>如果設定。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>相對於目標物件。|目標區域的左下角。|左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父代。|目標物件，或<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>如果設定。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>相對於目標物件。|目標區域的中央。|中央<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父代。|目標物件，或<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>如果設定。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>相對於目標物件。|定義由<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>。|定義由<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父代。|目標物件，或<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>如果設定。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>相對於目標物件。|目標區域的左上角。|右上角的<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|不適用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>會被忽略。|滑鼠指標的範圍。 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>會被忽略。|目標區域的左下角。|左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|不適用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>會被忽略。|滑鼠指標的範圍。 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>會被忽略。|目標區域的左上角。|左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父代。|目標物件，或<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>如果設定。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>相對於目標物件。|目標區域的左上角。|左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父代。|目標物件，或<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>如果設定。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>相對於目標物件。|目標區域的左上角。|左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父代。|目標物件，或<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>如果設定。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>相對於目標物件。|目標區域右上角。|左上角<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父代。|目標物件，或<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>如果設定。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>相對於目標物件。|目標區域的左上角。|左下角<xref:System.Windows.Controls.Primitives.Popup>。|  
  
 下列圖例顯示<xref:System.Windows.Controls.Primitives.Popup>，每個點的目標區域、 目標原點和快顯功能表對齊<xref:System.Windows.Controls.Primitives.PlacementMode>值。 在每個圖中，目標區域是黃色，而<xref:System.Windows.Controls.Primitives.Popup>是藍色。  
  
 ![具有 Absolute 或 AbsolutePoint 位置的 popup](../../../../docs/framework/wpf/controls/media/popupplacementabsolute.png "PopupPlacementAbsolute")  
位置是 Absolute 或 AbsolutePoint  
  
 ![具有 Bottom 位置的 popup](../../../../docs/framework/wpf/controls/media/popupplacementbottom.png "PopupPlacementBottom")  
位置是下  
  
 ![具有 Center 位置的 popup](../../../../docs/framework/wpf/controls/media/popupplacementcenter.png "PopupPlacementCenter")  
為置中位置  
  
 ![具有 Left 位置的 popup](../../../../docs/framework/wpf/controls/media/popupplacementleft.png "PopupPlacementLeft")  
位置是左邊  
  
 ![具有 Mouse 位置的 popup](../../../../docs/framework/wpf/controls/media/popupplacementmouse.png "PopupPlacementMouse")  
位置是滑鼠  
  
 ![具有 MousePoint 位置的 popup](../../../../docs/framework/wpf/controls/media/popupplacementmousepoint.png "PopupPlacementMousePoint")  
位置是 MousePoint  
  
 ![具有 Relative 或 RelativePoint 位置的 popup](../../../../docs/framework/wpf/controls/media/popupplacementrelative.png "PopupPlacementRelative")  
位置是 Relative 或 RelativePoint  
  
 ![具有 Right 位置的 popup](../../../../docs/framework/wpf/controls/media/popupplacementright.png "PopupPlacementRight")  
位置是權限  
  
 ![具有 Top 位置的 popup](../../../../docs/framework/wpf/controls/media/popupplacementtop.png "PopupPlacementTop")  
定位為 Top  
  
<a name="When"></a>   
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>當快顯視窗在螢幕的邊緣  
 基於安全性理由，<xref:System.Windows.Controls.Primitives.Popup>不可處於隱藏狀態螢幕的邊緣。 發生下列三個項目的其中之一時<xref:System.Windows.Controls.Primitives.Popup>遇到螢幕邊緣︰  
  
-   快顯視窗方向上重新對齊本身會遮蔽螢幕邊緣<xref:System.Windows.Controls.Primitives.Popup>。  
  
-   快顯視窗中會使用不同的快顯對齊點。  
  
-   快顯視窗中會使用不同的目標原點，並且快顯對齊點。  
  
 這些選項是進一步說明稍後在本章節中。  
  
 行為<xref:System.Windows.Controls.Primitives.Popup>螢幕邊緣時遇到而定的值<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性而螢幕快顯視窗中遇到的邊緣。 下表摘要說明的行為時<xref:System.Windows.Controls.Primitives.Popup>遇到每個畫面邊緣<xref:System.Windows.Controls.Primitives.PlacementMode>值。  
  
|PlacementMode|上邊緣|下邊緣|左邊的緣|右邊緣|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|上邊緣對齊。|下邊緣對齊。|左邊緣對齊。|右邊緣對齊。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|上邊緣對齊。|變更的左下角的快顯對齊點<xref:System.Windows.Controls.Primitives.Popup>。|左邊緣對齊。|變更的右上角的快顯對齊點<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|上邊緣對齊。|目標原點變更目標區域的左上角，然後快顯對齊點變成的左下角<xref:System.Windows.Controls.Primitives.Popup>。|左邊緣對齊。|右邊緣對齊。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|上邊緣對齊。|下邊緣對齊。|左邊緣對齊。|右邊緣對齊。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|上邊緣對齊。|下邊緣對齊。|目標原點變更的目標區域右上角，然後快顯對齊點變成的左上角<xref:System.Windows.Controls.Primitives.Popup>。|右邊緣對齊。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|上邊緣對齊。|目標原點變更為目標的區域 （滑鼠指標的範圍） 的左上角，然後快顯對齊點變成的左下角<xref:System.Windows.Controls.Primitives.Popup>。|左邊緣對齊。|右邊緣對齊。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|上邊緣對齊。|變更的左下角的快顯對齊點<xref:System.Windows.Controls.Primitives.Popup>。|左邊緣對齊。|快顯對齊點變更的快顯視窗右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|上邊緣對齊。|下邊緣對齊。|左邊緣對齊。|右邊緣對齊。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|上邊緣對齊。|變更的左下角的快顯對齊點<xref:System.Windows.Controls.Primitives.Popup>。|左邊緣對齊。|快顯對齊點變更的快顯視窗右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|上邊緣對齊。|下邊緣對齊。|左邊緣對齊。|目標原點變更目標區域的左上角，然後快顯對齊點變成右上角的<xref:System.Windows.Controls.Primitives.Popup>。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|目標原點變更目標區域的左下角，然後快顯對齊點變成的左上角<xref:System.Windows.Controls.Primitives.Popup>。 實際上，這是當相同<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>是<xref:System.Windows.Controls.Primitives.PlacementMode>。|下邊緣對齊。|左邊緣對齊。|右邊緣對齊。|  
  
### <a name="aligning-to-the-screen-edge"></a>畫面邊緣對齊  
 A<xref:System.Windows.Controls.Primitives.Popup>可以對齊螢幕的邊緣以調整本身的位置，整個<xref:System.Windows.Controls.Primitives.Popup>會顯示在螢幕上。  當發生這種情況時，目標原點，並且快顯對齊點之間的距離可能的值會與不同<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>和<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>。 當<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>是<xref:System.Windows.Controls.Primitives.PlacementMode>， <xref:System.Windows.Controls.Primitives.PlacementMode>，或<xref:System.Windows.Controls.Primitives.PlacementMode>、<xref:System.Windows.Controls.Primitives.Popup>本身的每個畫面邊緣對齊。  例如，假設<xref:System.Windows.Controls.Primitives.Popup>有<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>設<xref:System.Windows.Controls.Primitives.PlacementMode>和<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>設為 100。  如果螢幕的邊緣會隱藏所有或部分<xref:System.Windows.Controls.Primitives.Popup>、<xref:System.Windows.Controls.Primitives.Popup>重新定位本身沿著螢幕和目標原點與快顯視窗的垂直距離的下邊緣對齊點是小於 100。 下圖示範這個情況。  
  
 ![快顯畫面邊緣對齊](../../../../docs/framework/wpf/controls/media/popupplacementrelativescreenedge.png "PopupPlacementRelativeScreenEdge")  
快顯對齊螢幕的邊緣  
  
### <a name="changing-the-popup-alignment-point"></a>變更快顯對齊點  
 如果<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>是<xref:System.Windows.Controls.Primitives.PlacementMode>， <xref:System.Windows.Controls.Primitives.PlacementMode>，或<xref:System.Windows.Controls.Primitives.PlacementMode>，快顯對齊點變更時快顯視窗中遇到下或右邊畫面邊緣。  
  
 下圖示範當底部畫面邊緣會隱藏所有或部分<xref:System.Windows.Controls.Primitives.Popup>，快顯對齊點為的左下角<xref:System.Windows.Controls.Primitives.Popup>。  
  
 ![因為底部畫面邊緣造成的新對齊點](../../../../docs/framework/wpf/controls/media/popupplacementrelativepointscreenedge.png "PopupPlacementRelativePointScreenEdge")  
快顯功能表接觸螢幕的邊緣，而變更快顯對齊點  
  
 下圖示範當<xref:System.Windows.Controls.Primitives.Popup>隱藏右邊畫面邊緣，快顯對齊點是右上角的<xref:System.Windows.Controls.Primitives.Popup>。  
  
 ![因為畫面邊緣造成的新快顯對齊點](../../../../docs/framework/wpf/controls/media/popupplacementrelativepointrightscreenedge.png "PopupPlacementRelativePointRightScreenEdge")  
快顯功能表接觸螢幕的右邊緣，而變更快顯對齊點  
  
 如果<xref:System.Windows.Controls.Primitives.Popup>遇到下框線和右螢幕邊緣，快顯對齊點為的右下角<xref:System.Windows.Controls.Primitives.Popup>。  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>變更目標原點和快顯對齊點  
 當<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>是<xref:System.Windows.Controls.Primitives.PlacementMode>，<xref:System.Windows.Controls.Primitives.PlacementMode>，<xref:System.Windows.Controls.Primitives.PlacementMode>，<xref:System.Windows.Controls.Primitives.PlacementMode>，或<xref:System.Windows.Controls.Primitives.PlacementMode>，目標原點，並且快顯對齊點的變更，如果遇到某些畫面邊緣。  畫面邊緣造成變更的位置取決於<xref:System.Windows.Controls.Primitives.PlacementMode>值。  
  
 下圖示範當<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>是<xref:System.Windows.Controls.Primitives.PlacementMode>和<xref:System.Windows.Controls.Primitives.Popup>遇到螢幕邊緣，目標原點是目標區域的左上角，且快顯對齊點的左下角<xref:System.Windows.Controls.Primitives.Popup>。  
  
 ![因為底部畫面邊緣造成的新對齊點](../../../../docs/framework/wpf/controls/media/popupplacementbottomscreenedge.png "PopupPlacementBottomScreenEdge")  
位置是下，若快顯視窗中碰到螢幕的邊緣  
  
 下圖示範當<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>是<xref:System.Windows.Controls.Primitives.PlacementMode>和<xref:System.Windows.Controls.Primitives.Popup>遇到左的螢幕邊緣，目標原點是目標區域右上角，且快顯對齊點的左上角<xref:System.Windows.Controls.Primitives.Popup>。  
  
 ![因為左邊的畫面邊緣造成的新對齊點](../../../../docs/framework/wpf/controls/media/popupplacementleftscreenedge.png "PopupPlacementLeftScreenEdge")  
位置是左和快顯視窗中遇到螢幕的左邊的緣  
  
 下圖示範當<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>是<xref:System.Windows.Controls.Primitives.PlacementMode>和<xref:System.Windows.Controls.Primitives.Popup>遇到右螢幕邊緣，目標原點是目標區域的左上角，且快顯對齊點的右上角<xref:System.Windows.Controls.Primitives.Popup>。  
  
 ![因為右邊畫面邊緣造成的新對齊點](../../../../docs/framework/wpf/controls/media/popupplacementrightscreenedge.png "PopupPlacementRightScreenEdge")  
位置是權限，且快顯視窗中遇到螢幕的右邊緣  
  
 下圖示範當<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>是<xref:System.Windows.Controls.Primitives.PlacementMode>和<xref:System.Windows.Controls.Primitives.Popup>遇到頂端畫面邊緣，目標原點是目標區域的左下角，且快顯對齊點的左上角<xref:System.Windows.Controls.Primitives.Popup>。  
  
 ![因為頂端畫面邊緣造成的新對齊點](../../../../docs/framework/wpf/controls/media/popupplacementtopscreenedge.png "PopupPlacementTopScreenEdge")  
定位為 Top 和快顯視窗中遇到螢幕的頂端  
  
 下圖示範當<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>是<xref:System.Windows.Controls.Primitives.PlacementMode>和<xref:System.Windows.Controls.Primitives.Popup>遇到螢幕邊緣，目標原點是目標區域 （滑鼠指標的範圍） 的左上角，且快顯對齊點的左下角<xref:System.Windows.Controls.Primitives.Popup>。  
  
 ![因為滑鼠附近畫面邊緣造成的新對齊點](../../../../docs/framework/wpf/controls/media/popupplacementmousescreenedge.png "PopupPlacementMouseScreenEdge")  
位置是滑鼠，而且快顯視窗會遇到螢幕的邊緣  
  
### <a name="customizing-popup-placement"></a>自訂的 Popup 位置  
 您可以藉由設定自訂目標原點，並且快顯對齊點<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性<xref:System.Windows.Controls.Primitives.PlacementMode>。 然後定義<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>委派，會傳回一組可能的定位點和主座標軸 （依喜好設定順序） 的<xref:System.Windows.Controls.Primitives.Popup>。 顯示的最大的一部分，但卻<xref:System.Windows.Controls.Primitives.Popup>已選取。  位置<xref:System.Windows.Controls.Primitives.Popup>會自動調整大小，如果<xref:System.Windows.Controls.Primitives.Popup>隱藏螢幕的邊緣。 如需範例，請參閱[指定自訂 Popup 的位置](../../../../docs/framework/wpf/controls/how-to-specify-a-custom-popup-position.md)。  
  
## <a name="see-also"></a>另請參閱  
 [快顯功能表放置範例](http://go.microsoft.com/fwlink/?LinkID=160032)