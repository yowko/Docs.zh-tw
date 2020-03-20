---
title: 快顯功能表概觀
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
ms.openlocfilehash: 911130d52744c5ba54750f214829a5d1900e083c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185946"
---
# <a name="popup-overview"></a>快顯功能表概觀
該<xref:System.Windows.Controls.Primitives.Popup>控制項提供了一種在單獨的視窗中顯示內容的方法，該視窗相對於指定的元素或螢幕座標浮動在當前應用程式視窗中。 本主題介紹控制項<xref:System.Windows.Controls.Primitives.Popup>，並提供有關其使用的資訊。  

<a name="What_Is_a_Popup_"></a>
## <a name="what-is-a-popup"></a>什麼是快顯？  
 控制項<xref:System.Windows.Controls.Primitives.Popup>顯示與螢幕上的元素或點相關的單獨視窗中的內容。 當<xref:System.Windows.Controls.Primitives.Popup>可見 時，<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A>屬性設置為`true`。  
  
> [!NOTE]
> 當<xref:System.Windows.Controls.Primitives.Popup>滑鼠指標在其父物件上移動時，不會自動打開。 如果要自動打開<xref:System.Windows.Controls.Primitives.Popup>， 請使用 或<xref:System.Windows.Controls.ToolTip><xref:System.Windows.Controls.ToolTipService>類。 如需詳細資訊，請參閱 [ToolTip 概觀](tooltip-overview.md)。  
  
<a name="APopupExample"></a>
## <a name="creating-a-popup"></a>建立快顯  
 下面的示例演示如何定義作為<xref:System.Windows.Controls.Primitives.Popup><xref:System.Windows.Controls.Button>控制項的子項目的控制項。 由於<xref:System.Windows.Controls.Button>只能有一個子項目，因此此示例將 和<xref:System.Windows.Controls.Button><xref:System.Windows.Controls.Primitives.Popup>控制項的文本放在 中。 <xref:System.Windows.Controls.StackPanel> 的內容<xref:System.Windows.Controls.Primitives.Popup>顯示在<xref:System.Windows.Controls.TextBlock>控制項中，該控制項在單獨的視窗中顯示其文本，該視窗浮動在相關<xref:System.Windows.Controls.Button>控制項附近的應用程式視窗上。  
  
 [!code-xaml[PopupSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>
## <a name="controls-that-implement-a-popup"></a>實作快顯的控制項  
 可以將控制項構建<xref:System.Windows.Controls.Primitives.Popup>到其他控制項中。 以下控制項為<xref:System.Windows.Controls.Primitives.Popup>特定用途實現控制項：  
  
- <xref:System.Windows.Controls.ToolTip>. 如果要為元素創建工具提示，請使用 和<xref:System.Windows.Controls.ToolTip><xref:System.Windows.Controls.ToolTipService>類。 如需詳細資訊，請參閱 [ToolTip 概觀](tooltip-overview.md)。  
  
- <xref:System.Windows.Controls.ContextMenu>. 如果要為元素創建內容功能表，請使用 控制項<xref:System.Windows.Controls.ContextMenu>。 如需詳細資訊，請參閱 [ContextMenu 概觀](contextmenu-overview.md)。  
  
- <xref:System.Windows.Controls.ComboBox>. 如果要創建具有可顯示或隱藏的下拉式清單方塊的選擇控制項，請使用 該<xref:System.Windows.Controls.ComboBox>控制項。  
  
- <xref:System.Windows.Controls.Expander>. 如果要創建顯示具有可折疊區域顯示內容的標頭的控制項，請使用 該<xref:System.Windows.Controls.Expander>控制項。 如需詳細資訊，請參閱 [Expander 概觀](expander-overview.md)。  
  
<a name="PopupBehaviorandAppearance"></a>
## <a name="popup-behavior-and-appearance"></a>快顯行為和外觀  
 該<xref:System.Windows.Controls.Primitives.Popup>控制項提供的功能使您能夠自訂其行為和外觀。 例如，您可以設置打開和關閉行為、動畫、不一公開性和點陣圖效果以及<xref:System.Windows.Controls.Primitives.Popup>大小和位置。  
  
<a name="OpenandCloseBehavior"></a>
### <a name="open-and-close-behavior"></a>開啟和關閉行為  
 當<xref:System.Windows.Controls.Primitives.Popup>屬性設置為<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A>`true`時，控制項將顯示其內容。 預設情況下，<xref:System.Windows.Controls.Primitives.Popup>保持打開狀態，<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A>直到屬性設置為`false`。 但是，您可以通過將<xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A>屬性設置為`false`來更改預設行為。 將此屬性設置為`false`時，<xref:System.Windows.Controls.Primitives.Popup>內容視窗具有滑鼠捕獲。 當<xref:System.Windows.Controls.Primitives.Popup>滑鼠事件發生在<xref:System.Windows.Controls.Primitives.Popup>視窗外部時，丟失滑鼠捕獲和視窗關閉。  
  
 當<xref:System.Windows.Controls.Primitives.Popup.Opened><xref:System.Windows.Controls.Primitives.Popup>內容<xref:System.Windows.Controls.Primitives.Popup.Closed>視窗打開或關閉時，將引發 和 事件。  
  
<a name="Animation"></a>
### <a name="animation"></a>動畫  
 該<xref:System.Windows.Controls.Primitives.Popup>控制項具有內置支援通常與淡入和滑入等行為關聯的動畫。 通過將屬性設置為<xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A><xref:System.Windows.Controls.Primitives.PopupAnimation>枚舉值，可以打開這些動畫。 要<xref:System.Windows.Controls.Primitives.Popup>使動畫正常工作，必須將<xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A>屬性設置為`true`。  
  
 您還可以將控制項等<xref:System.Windows.Media.Animation.Storyboard>動畫應用於<xref:System.Windows.Controls.Primitives.Popup>控制項。  
  
<a name="OpacityandBitmapEffects"></a>
### <a name="opacity-and-bitmap-effects"></a>不透明度和點陣圖效果  
 <xref:System.Windows.Controls.Primitives.Popup>控制項<xref:System.Windows.UIElement.Opacity%2A>的屬性對其內容沒有影響。 預設情況下，<xref:System.Windows.Controls.Primitives.Popup>內容視窗不透明。 要創建透明<xref:System.Windows.Controls.Primitives.Popup>，請將<xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A>屬性設置為`true`。  
  
 的內容<xref:System.Windows.Controls.Primitives.Popup>不繼承點陣圖效果，例如<xref:System.Windows.Media.Effects.DropShadowBitmapEffect>，您直接在<xref:System.Windows.Controls.Primitives.Popup>控制項或父視窗中的任何其他元素上設置。 要將點陣圖效果顯示在 的內容上<xref:System.Windows.Controls.Primitives.Popup>，必須直接在其內容上設置點陣圖效果。 例如，如果 的<xref:System.Windows.Controls.Primitives.Popup>子級為<xref:System.Windows.Controls.StackPanel>， 在 上設置點陣圖效果<xref:System.Windows.Controls.StackPanel>。  
  
<a name="PopupSize"></a>
### <a name="popup-size"></a>快顯大小  
 預設情況下，應<xref:System.Windows.Controls.Primitives.Popup>自動調整其內容的大小。 發生自動大小調整時，可能會隱藏某些點陣圖效果，因為為<xref:System.Windows.Controls.Primitives.Popup>內容定義的螢幕區域的預設大小無法為點陣圖效果提供足夠的空間來顯示。  
  
 <xref:System.Windows.Controls.Primitives.Popup>在內容上設置 時<xref:System.Windows.UIElement.RenderTransform%2A>，內容也會被遮蓋。 在這種情況下，如果轉換的內容<xref:System.Windows.Controls.Primitives.Popup>超出原始<xref:System.Windows.Controls.Primitives.Popup>區域的範圍，則某些內容可能會隱藏。 如果點陣圖效果或變換需要更多空間，則可以在<xref:System.Windows.Controls.Primitives.Popup>內容周圍定義邊距，以便為控制項提供更多區域。  
  
<a name="DefiningPopupPosition"></a>
## <a name="defining-the-popup-position"></a>定義快顯位置  
 您可以通過設置<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>、 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>和<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A><xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty>屬性來定位快顯視窗。 如需詳細資訊，請參閱[快顯放置行為](popup-placement-behavior.md)。 當<xref:System.Windows.Controls.Primitives.Popup>顯示在螢幕上時，如果重新置放其父級，它不會重新置放自身。  
  
<a name="CustomizingPopupPlacement"></a>
### <a name="customizing-popup-placement"></a>自訂快顯位置  
 可以通過指定一組相對於要<xref:System.Windows.Controls.Primitives.Popup><xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A><xref:System.Windows.Controls.Primitives.Popup>顯示的位置的座標來自訂控制項的位置。  
  
 要自訂放置，請將<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>屬性<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>設置為 。 然後定義一<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>個委託，該委託返回 一<xref:System.Windows.Controls.Primitives.Popup>組可能的放置點和主軸（按首選項順序排列） 。 顯示 的最大部分<xref:System.Windows.Controls.Primitives.Popup>的點將自動選擇。 如需範例，請參閱[指定自訂快顯位置](how-to-specify-a-custom-popup-position.md)。  
  
<a name="PopupandtheVisualTree"></a>
## <a name="popup-and-the-visual-tree"></a>快顯和視覺化樹狀結構  
 控制項<xref:System.Windows.Controls.Primitives.Popup>沒有自己的可視樹;因此，控制項沒有自己的可視樹。相反，當調用 方法<xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A><xref:System.Windows.Controls.Primitives.Popup>時，它返回大小 0（零）。 但是，當您將 屬性<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A><xref:System.Windows.Controls.Primitives.Popup>設置為`true`時，將創建具有其自身可視樹的新視窗。 新視窗包含<xref:System.Windows.Controls.Primitives.Popup.Child%2A>的內容<xref:System.Windows.Controls.Primitives.Popup>。 新視窗的寬度和高度不可超過畫面寬度或高度的 75%。  
  
 控制項<xref:System.Windows.Controls.Primitives.Popup>將引用內容<xref:System.Windows.Controls.Primitives.Popup.Child%2A>作為邏輯子級。 創建新視窗時，的內容<xref:System.Windows.Controls.Primitives.Popup>將成為視窗的視覺子級，並且仍然是<xref:System.Windows.Controls.Primitives.Popup>的邏輯子級。 相反，<xref:System.Windows.Controls.Primitives.Popup>仍然是其內容<xref:System.Windows.Controls.Primitives.Popup.Child%2A>的邏輯父級。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.Primitives.Popup>
- <xref:System.Windows.Controls.Primitives.PopupPrimaryAxis>
- <xref:System.Windows.Controls.Primitives.PlacementMode>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacement>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [如何使用主題](popup-how-to-topics.md)
- [如何使用主題](tooltip-how-to-topics.md)
