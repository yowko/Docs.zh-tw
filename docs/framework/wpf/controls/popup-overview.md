---
title: 快顯功能表概觀
description: 瞭解 Windows Presentation Foundation Popup 控制項，其提供在浮動于目前應用程式的視窗中顯示內容的方式。
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
ms.openlocfilehash: 84eaddc53366df6d1da1a0a005d3618268f8cce2
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167543"
---
# <a name="popup-overview"></a>快顯功能表概觀
<xref:System.Windows.Controls.Primitives.Popup>控制項提供一種方式，可以將內容顯示在另一個視窗中，以浮動在相對於指定專案或螢幕座標的目前應用程式視窗。 本主題將介紹 <xref:System.Windows.Controls.Primitives.Popup> 控制項，並提供其用法的相關資訊。  

<a name="What_Is_a_Popup_"></a>
## <a name="what-is-a-popup"></a>什麼是快顯？  
 <xref:System.Windows.Controls.Primitives.Popup>控制項會在與螢幕上的專案或點相對的個別視窗中顯示內容。 當 <xref:System.Windows.Controls.Primitives.Popup> 為可見時， <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> 屬性會設定為 `true` 。  
  
> [!NOTE]
> <xref:System.Windows.Controls.Primitives.Popup>當滑鼠指標移到其父物件上方時，不會自動開啟。 如果您想要 <xref:System.Windows.Controls.Primitives.Popup> 自動開啟，請使用 <xref:System.Windows.Controls.ToolTip> 或 <xref:System.Windows.Controls.ToolTipService> 類別。 如需詳細資訊，請參閱 [ToolTip 概觀](tooltip-overview.md)。  
  
<a name="APopupExample"></a>
## <a name="creating-a-popup"></a>建立快顯  
 下列範例示範如何定義控制項 <xref:System.Windows.Controls.Primitives.Popup> 的子項目 <xref:System.Windows.Controls.Button> 。 因為只能 <xref:System.Windows.Controls.Button> 有一個子專案，所以這個範例會將和控制項的文字放 <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.Popup> 在中 <xref:System.Windows.Controls.StackPanel> 。 的內容 <xref:System.Windows.Controls.Primitives.Popup> 會出現在控制項中 <xref:System.Windows.Controls.TextBlock> ，它會在另一個視窗中顯示其文字，並將其浮動在相關控制項附近的應用程式視窗中 <xref:System.Windows.Controls.Button> 。  
  
 [!code-xaml[PopupSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>
## <a name="controls-that-implement-a-popup"></a>實作快顯的控制項  
 您可以將 <xref:System.Windows.Controls.Primitives.Popup> 控制項建立在其他控制項中。 下列控制項會 <xref:System.Windows.Controls.Primitives.Popup> 針對特定用途來執行控制項：  
  
- <xref:System.Windows.Controls.ToolTip>. 如果您想要建立元素的工具提示，請使用 <xref:System.Windows.Controls.ToolTip> 和 <xref:System.Windows.Controls.ToolTipService> 類別。 如需詳細資訊，請參閱 [ToolTip 概觀](tooltip-overview.md)。  
  
- <xref:System.Windows.Controls.ContextMenu>. 如果您想要建立元素的內容功能表，請使用 <xref:System.Windows.Controls.ContextMenu> 控制項。 如需詳細資訊，請參閱 [ContextMenu 概觀](contextmenu-overview.md)。  
  
- <xref:System.Windows.Controls.ComboBox>. 如果您想要建立具有可顯示或隱藏之下拉式清單方塊的選取控制項，請使用 <xref:System.Windows.Controls.ComboBox> 控制項。  
  
- <xref:System.Windows.Controls.Expander>. 如果您想要建立一個顯示標題的控制項，其中包含顯示內容的可折迭區域，請使用 <xref:System.Windows.Controls.Expander> 控制項。 如需詳細資訊，請參閱 [Expander 概觀](expander-overview.md)。  
  
<a name="PopupBehaviorandAppearance"></a>
## <a name="popup-behavior-and-appearance"></a>快顯行為和外觀  
 <xref:System.Windows.Controls.Primitives.Popup>控制項提供的功能可讓您自訂其行為和外觀。 例如，您可以設定開啟和關閉行為、動畫、不透明度和點陣圖效果，以及 <xref:System.Windows.Controls.Primitives.Popup> 大小和位置。  
  
<a name="OpenandCloseBehavior"></a>
### <a name="open-and-close-behavior"></a>開啟和關閉行為  
 <xref:System.Windows.Controls.Primitives.Popup>當 <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> 屬性設定為時，控制項會顯示其內容 `true` 。 根據預設， <xref:System.Windows.Controls.Primitives.Popup> 會保持開啟狀態，直到 <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> 屬性設定為為止 `false` 。 不過，您可以藉由將屬性設定為，來變更預設行為 <xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A> `false` 。 當您將此屬性設定為時 `false` ， <xref:System.Windows.Controls.Primitives.Popup> 內容視窗會有滑鼠捕捉。 <xref:System.Windows.Controls.Primitives.Popup>當滑鼠事件在視窗外發生時，失去滑鼠捕捉和視窗會關閉 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
 <xref:System.Windows.Controls.Primitives.Popup.Opened> <xref:System.Windows.Controls.Primitives.Popup.Closed> 當 <xref:System.Windows.Controls.Primitives.Popup> 內容視窗開啟或關閉時，會引發和事件。  
  
<a name="Animation"></a>
### <a name="animation"></a>動畫  
 <xref:System.Windows.Controls.Primitives.Popup>控制項內建的動畫支援通常與淡入和滑入等行為相關聯。 您可以藉由將 <xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A> 屬性設定為列舉值來開啟這些動畫 <xref:System.Windows.Controls.Primitives.PopupAnimation> 。 <xref:System.Windows.Controls.Primitives.Popup>若要讓動畫正常運作，您必須將 <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> 屬性設定為 `true` 。  
  
 您也可以將像 <xref:System.Windows.Media.Animation.Storyboard> 是的動畫套用至 <xref:System.Windows.Controls.Primitives.Popup> 控制項。  
  
<a name="OpacityandBitmapEffects"></a>
### <a name="opacity-and-bitmap-effects"></a>不透明度和點陣圖效果  
 <xref:System.Windows.UIElement.Opacity%2A>控制項的屬性對 <xref:System.Windows.Controls.Primitives.Popup> 其內容不會有任何影響。 根據預設， <xref:System.Windows.Controls.Primitives.Popup> 內容視窗是不透明的。 若要建立透明的 <xref:System.Windows.Controls.Primitives.Popup> ，請將 <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> 屬性設定為 `true` 。  
  
 的內容 <xref:System.Windows.Controls.Primitives.Popup> 不會繼承點陣圖效果（例如 <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> ），您可以直接在控制項上或在 <xref:System.Windows.Controls.Primitives.Popup> 父視窗中的任何其他專案上設定。 若要讓點陣圖效果出現在的內容上 <xref:System.Windows.Controls.Primitives.Popup> ，您必須直接在其內容上設定點陣圖效果。 例如，如果的子系 <xref:System.Windows.Controls.Primitives.Popup> 為 <xref:System.Windows.Controls.StackPanel> ，請在上設定點陣圖效果 <xref:System.Windows.Controls.StackPanel> 。  
  
<a name="PopupSize"></a>
### <a name="popup-size"></a>快顯大小  
 根據預設， <xref:System.Windows.Controls.Primitives.Popup> 會自動調整為其內容的大小。 當自動調整大小時，可能會隱藏某些點陣圖效果，因為針對內容定義的螢幕區域預設大小 <xref:System.Windows.Controls.Primitives.Popup> 未提供足夠的空間來顯示點陣圖效果。  
  
 <xref:System.Windows.Controls.Primitives.Popup>當您在內容上設定時，內容也可能會遮蔽 <xref:System.Windows.UIElement.RenderTransform%2A> 。 在此案例中，如果已轉換的內容 <xref:System.Windows.Controls.Primitives.Popup> 延伸至原始區域之外，某些內容可能會隱藏 <xref:System.Windows.Controls.Primitives.Popup> 。 如果點陣圖效果或轉換需要更多空間，您可以在內容周圍定義邊界， <xref:System.Windows.Controls.Primitives.Popup> 以便為控制項提供更多區域。  
  
<a name="DefiningPopupPosition"></a>
## <a name="defining-the-popup-position"></a>定義快顯位置  
 您可以藉由設定 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 、 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 、 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 、 <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty> 屬性來定位快顯功能表。 如需詳細資訊，請參閱[快顯放置行為](popup-placement-behavior.md)。 當 <xref:System.Windows.Controls.Primitives.Popup> 螢幕上顯示時，如果其父系已重新置放，則不會重新調整其本身的位置。  
  
<a name="CustomizingPopupPlacement"></a>
### <a name="customizing-popup-placement"></a>自訂快顯位置  
 您可以 <xref:System.Windows.Controls.Primitives.Popup> 指定相對於您想要顯示之位置的一組座標，以自訂控制項的位置 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Primitives.Popup> 。  
  
 若要自訂位置，請將 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 屬性設定為 <xref:System.Windows.Controls.Primitives.PlacementMode.Custom> 。 然後定義委派，以傳回的 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> 一組可能的放置點和主要軸（依照喜好設定的順序） <xref:System.Windows.Controls.Primitives.Popup> 。 會自動選取顯示最大部分的點 <xref:System.Windows.Controls.Primitives.Popup> 。 如需範例，請參閱[指定自訂快顯位置](how-to-specify-a-custom-popup-position.md)。  
  
<a name="PopupandtheVisualTree"></a>
## <a name="popup-and-the-visual-tree"></a>快顯和視覺化樹狀結構  
 <xref:System.Windows.Controls.Primitives.Popup>控制項沒有自己的視覺化樹狀結構; 當呼叫的方法時，它會改為傳回0（零）的大小 <xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A> <xref:System.Windows.Controls.Primitives.Popup> 。 不過，當您將的 <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> 屬性設定 <xref:System.Windows.Controls.Primitives.Popup> 為時 `true` ，會建立具有自己的視覺化樹狀結構的新視窗。 新視窗包含的 <xref:System.Windows.Controls.Primitives.Popup.Child%2A> 內容 <xref:System.Windows.Controls.Primitives.Popup> 。 新視窗的寬度和高度不可超過畫面寬度或高度的 75%。  
  
 <xref:System.Windows.Controls.Primitives.Popup>控制項會將其內容的參考維護 <xref:System.Windows.Controls.Primitives.Popup.Child%2A> 為邏輯子系。 建立新視窗時，的內容 <xref:System.Windows.Controls.Primitives.Popup> 會成為視窗的視覺子系，而且會維持的邏輯子系 <xref:System.Windows.Controls.Primitives.Popup> 。 相反地，會 <xref:System.Windows.Controls.Primitives.Popup> 維持其內容的邏輯父系 <xref:System.Windows.Controls.Primitives.Popup.Child%2A> 。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.Primitives.Popup>
- <xref:System.Windows.Controls.Primitives.PopupPrimaryAxis>
- <xref:System.Windows.Controls.Primitives.PlacementMode>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacement>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [操作說明主題](popup-how-to-topics.md)
- [操作說明主題](tooltip-how-to-topics.md)
