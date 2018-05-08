---
title: 設定控制項中焦點的樣式和 FocusVisualStyle
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard focus [WPF]
- focus [WPF], visual styling
- styles [WPF], focus visual style
ms.assetid: 786ac576-011b-4d72-913b-558deccb9b35
ms.openlocfilehash: 6c73c8bbfcf7631094ddf89641de9af38f86f88e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="styling-for-focus-in-controls-and-focusvisualstyle"></a>設定控制項中焦點的樣式和 FocusVisualStyle
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供兩種平行機制，在控制項接收到鍵盤焦點時，用來變更它的視覺外觀。 第一種機制是使用屬性 setter 的屬性，例如<xref:System.Windows.UIElement.IsKeyboardFocused%2A>樣式或範本套用至控制項內。 第二種機制是要提供不同的樣式的值為<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>屬性;"專注視覺化樣式 」 建立個別的視覺化樹狀結構控制項，而不是變更或其他 UI 控制項的視覺化樹狀結構上方繪製到裝飾項藉由取代它的項目。 本主題將討論每一種機制的適用案例。  
   
  
<a name="Purpose"></a>   
## <a name="the-purpose-of-focus-visual-style"></a>焦點視覺化樣式的用途  
 焦點視覺化樣式功能提供常見的「物件模型」，以介紹根據鍵盤瀏覽至任何 UI 元素的視覺化使用者回饋。 即使不將新的範本套用至控制項，或是知道特定的範本組合，還是能夠達成此目的。  
  
 不過，正因為焦點視覺化樣式功能可以在不知道控制項範本的情況下運作，所以，一定要限制可使用焦點視覺化樣式，針對控制項顯示的視覺化回饋。 此功能真正的運作方式是，在視覺化樹狀結構上方重疊不同的視覺化樹狀結構 (提示)，如同由控制項透過其範本的轉譯來建立。 您定義這個個別的視覺化樹狀結構，以填滿的樣式<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>屬性。  
  
<a name="Default"></a>   
## <a name="default-focus-visual-style-behavior"></a>預設的焦點視覺化樣式行為  
 只有當焦點動作是由鍵盤所起始時，焦點視覺化樣式才會運作。 任何的滑鼠動作或程式設計焦點變更，都會停用焦點視覺化樣式的模式。 如需焦點模式之間差異的詳細資訊，請參閱[焦點概觀](../../../../docs/framework/wpf/advanced/focus-overview.md)。  
  
 控制項的佈景主題包括預設的焦點視覺化樣式行為，其會成為佈景主題中所有控制項的焦點視覺化樣式。 此佈景主題樣式由靜態的機碼值<xref:System.Windows.SystemParameters.FocusVisualStyleKey%2A>。 當您在應用程式層級宣告自己的焦點視覺化樣式時，會取代佈景主題的這個預設樣式行為。 或者，如果您定義整個佈景主題，則您應該使用這個相同的索引鍵，針對整個佈景主題定義預設行為的樣式。  
  
 在佈景主題中，預設的焦點視覺化樣式通常非常簡單。 以下是一種概略的方式：  
  
```  
<Style x:Key="{x:Static SystemParameters.FocusVisualStyleKey}">  
  <Setter Property="Control.Template">  
    <Setter.Value>  
      <ControlTemplate>  
        <Rectangle StrokeThickness="1"  
          Stroke="Black"  
          StrokeDashArray="1 2"  
          SnapsToDevicePixels="true"/>  
      </ControlTemplate>  
    </Setter.Value>  
  </Setter>  
</Style>  
```  
  
<a name="When"></a>   
## <a name="when-to-use-focus-visual-styles"></a>使用焦點視覺化樣式的時機  
 概念上，套用至控制項的焦點視覺化樣式外觀在各個控制項之間應該保持一致。 確保一致性的方法之一是，只有當您在撰寫整個佈景主題時，才能變更焦點視覺化樣式，而定義於該佈景主題中的每一個控制項都會取得完全相同的焦點視覺化樣式，或是控制項之間視覺上相關之樣式的一些變化。 另外，您可以使用相同的樣式 (或類似樣式)，為頁面上或 UI 中每一個可透過鍵盤取得焦點的元素設定樣式。  
  
 設定<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>上個別控制項的樣式不屬於佈景主題，不是焦點的預定使用方式視覺化樣式。 這是因為控制項之間不一致的視覺化行為，可導致使用者在關於鍵盤焦點方面得到令人困惑的體驗。 如果您打算是刻意不一致的佈景主題的控制項專屬行為的鍵盤焦點，更好的方法是使用觸發程序在樣式為個別的輸入的狀態的屬性，例如<xref:System.Windows.UIElement.IsFocused%2A>或<xref:System.Windows.UIElement.IsKeyboardFocused%2A>。  
  
 焦點視覺化樣式是鍵盤焦點專用的。 因此，焦點視覺化樣式是一種協助工具功能。 如果您想要針對任何類型的焦點進行 UI 變更 (不論是透過滑鼠、鍵盤或程式設計)，則您不應該使用焦點視覺化樣式，而應該在從一般焦點屬性 (例如 `IsFocused` 或 `IsFocusWithin`) 的值運作的樣式或範本中改用 setter 和觸發程序。  
  
<a name="How"></a>   
## <a name="how-to-create-a-focus-visual-style"></a>建立焦點視覺化樣式的方式  
 樣式針對您建立應該永遠具有焦點的視覺化樣式<xref:System.Windows.Style.TargetType%2A>的<xref:System.Windows.Controls.Control>。 樣式應該包含主要<xref:System.Windows.Controls.ControlTemplate>。 未指定目標類型是類型焦點視覺化樣式已指派給<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>。  
  
 因為目標類型一律為<xref:System.Windows.Controls.Control>，您必須藉由使用屬性通用於所有控制項樣式 (使用屬性的<xref:System.Windows.Controls.Control>類別和其基底類別)。 您應該建立將正常運作的範本來與 UI 元素重疊，而且將不會混淆控制項的功能區域。 一般而言，這表示視覺化回饋應該出現在控制項邊界外部，或者做為暫時性或不引人注目的效果，這類效果將不會在套用焦點視覺化樣式的控制項上封鎖點擊測試。 您可以使用範本繫結中的可用來判斷調整大小和位置的重疊範本的內容包括<xref:System.Windows.FrameworkElement.ActualHeight%2A>， <xref:System.Windows.FrameworkElement.ActualWidth%2A>， <xref:System.Windows.FrameworkElement.Margin%2A>，和<xref:System.Windows.Controls.Control.Padding%2A>。  
  
<a name="Alternatives"></a>   
## <a name="alternatives-to-using-a-focus-visual-style"></a>使用焦點視覺化樣式的替代方案  
 針對不適合使用焦點視覺化樣式的情況 (可能是因為您只設定單一控制項的樣式，或因為您想要對控制項範本有更大的控制權)，有許多其他可存取的屬性和技術可用於建立視覺化行為來回應焦點的變更。  
  
 如需所有對觸發程序、setter 及事件 setter 的詳細討論，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)中則會討論如何處理路由事件。  
  
### <a name="iskeyboardfocused"></a>IsKeyboardFocused  
 如果您特別想要在鍵盤焦點<xref:System.Windows.UIElement.IsKeyboardFocused%2A>相依性屬性可用於屬性<xref:System.Windows.Trigger>。 若要定義非常專屬於單一控制項的鍵盤焦點行為，樣式或範本中的屬性觸發程序是更為合適的技術，而這可能不會以視覺化方式符合其他控制項的鍵盤焦點行為。  
  
 另一個類似的相依性屬性是<xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>，可能適合使用，如果您想要以視覺化方式呼叫該鍵盤焦點位於複合或控制項的功能區域中。 例如，您可能會放置<xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>觸發程序群組在數個控制項的面板也會出現以不同的鍵盤焦點可能更明確地說，是在該面板中的個別項目。  
  
 您也可以使用事件<xref:System.Windows.UIElement.GotKeyboardFocus>和<xref:System.Windows.UIElement.LostKeyboardFocus>（以及其預覽對等項目）。 您可以使用這些事件為基礎<xref:System.Windows.EventSetter>，或您可以撰寫程式碼後置事件的處理常式。  
  
### <a name="other-focus-properties"></a>其他焦點屬性  
 如果您希望所有的可能原因變更焦點以產生視覺化的行為，您應該基底 setter 或觸發程序上<xref:System.Windows.UIElement.IsFocused%2A>相依性屬性，或者在<xref:System.Windows.UIElement.GotFocus>或<xref:System.Windows.UIElement.LostFocus>用於事件<xref:System.Windows.EventSetter>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>  
 [樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [焦點概觀](../../../../docs/framework/wpf/advanced/focus-overview.md)  
 [輸入概觀](../../../../docs/framework/wpf/advanced/input-overview.md)
