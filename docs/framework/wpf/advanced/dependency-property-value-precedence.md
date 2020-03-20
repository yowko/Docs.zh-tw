---
title: 相依性屬性值優先順序
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], classes as owners
- dependency properties [WPF], metadata
- classes [WPF], owners of dependency properties
- metadata [WPF], dependency properties
ms.assetid: 1fbada8e-4867-4ed1-8d97-62c07dad7ebc
ms.openlocfilehash: 1d7c644c7f7581a96ffff1a0fe1fcf2adfe071e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186152"
---
# <a name="dependency-property-value-precedence"></a>相依性屬性值優先順序
<a name="introduction"></a> 本主題說明 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 屬性系統的運作方式如何影響相依性屬性的值，並描述屬性系統套用到屬性有效值的優先順序。  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>必要條件  
 本主題假設您已從 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類別的現有相依性屬性消費者角度了解相依性屬性，並已閱讀[相依性屬性概觀](dependency-properties-overview.md)。 為遵循本主題中的範例，您也應該了解 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 並知道如何撰寫 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。  
  
<a name="intro"></a>
## <a name="the-wpf-property-system"></a>WPF 屬性系統  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統提供一個強大的方法，透過各種因素來決定相依性屬性的值，並啟用即時屬性驗證、晚期繫結，以及將其他屬性的值變更通知相關屬性等功能。 用來決定相依性屬性值的實際順序和邏輯相當複雜。 不過，知道此順序將有助於避免不必要的屬性設定，也可釐清試圖影響或預測相依性屬性值，為何最後並未產生所預期的值。  
  
<a name="multiple_sets"></a>
## <a name="dependency-properties-might-be-set-in-multiple-places"></a>相依性屬性可能在多處「設定」  
 下面是同一屬性[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]（<xref:System.Windows.Controls.Control.Background%2A>） 具有可能影響該值的三個不同的"設置"操作的示例。  
  
 [!code-xaml[PropertiesOvwSupport#DPPrecedence](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#dpprecedence)]  
  
 在此，您預期會套用哪個色彩 - 紅色、綠色，還是藍色？  
  
 除了動畫值和強制型轉之外，區域屬性集會設為最高優先順序。 如果您在本機設定值，可預期該值將會被接受，甚至優先於任何樣式或控制項範本。 在此示例中，<xref:System.Windows.Controls.Control.Background%2A>在本地設置為紅色。 因此，在此作用域中定義的樣式（即使它是隱式樣式，否則將應用於該作用域中該類型的所有元素）不是給予<xref:System.Windows.Controls.Control.Background%2A>屬性其值的最高優先順序。  如果從該 Button 執行個體移除區域數值 Red，則樣式會具有優先順序，因此按鈕會從樣式取得 Background 值。  在樣式內，觸發程序具有較高的優先順序，因此如果將滑鼠移至按鈕上方，按鈕會變成藍色，否則就會是綠色的。  
  
<a name="listing"></a>
## <a name="dependency-property-setting-precedence-list"></a>相依性屬性設定優先順序清單  
 以下是屬性系統在指派相依性屬性的執行階段值時，所使用的決定順序。 最高優先順序會先列出。 此清單更進一步說明了[相依性屬性概觀](dependency-properties-overview.md)中所述的部分概要。  
  
1. **屬性系統強制型轉**： 如需強制型轉的詳細資訊，請參閱本主題稍後的[強制型轉、動畫和基底值](#animations)。  
  
2. **作用中動畫或具有 Hold 行為的動畫**： 屬性的動畫必須優先於基底 (非動畫) 值，才能有任何實際效果，即使該值是在本機設定也一樣。 如需詳細資訊，請參閱本主題稍後的[強制型轉、動畫和基底值](#animations)。  
  
3. **區域數值**： 本地值可以通過"wrapper"屬性的便利性進行設置，該屬性也等同于在 中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]設置為屬性或屬性元素，或者通過使用特定實例的屬性調用<xref:System.Windows.DependencyObject.SetValue%2A>API。 如果使用繫結或資源來設定區域數值，其在優先順序中的作用就如同設定直接值。  
  
4. **TemplatedParent 範本屬性**： <xref:System.Windows.FrameworkElement.TemplatedParent%2A> <xref:System.Windows.Controls.ControlTemplate>元素<xref:System.Windows.DataTemplate>具有 如需何時套用此屬性的詳細資訊，請參閱本主題稍後的 [TemplatedParent](#templatedparent)。 在範本內，優先順序如下：  
  
    1. 來自範本的<xref:System.Windows.FrameworkElement.TemplatedParent%2A>觸發器。  
  
    2. 範本中的屬性集（[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]通常通過屬性）。 <xref:System.Windows.FrameworkElement.TemplatedParent%2A>  
  
5. **隱含樣式**： 僅適用於 `Style` 屬性。 `Style` 屬性是由具有符合項目類型之索引鍵的任何樣式資源所填入。 該樣式資源必須位於頁面或應用程式中；查閱隱含樣式資源不會進行到主題中。  
  
6. **樣式觸發程序**： 來自於頁面或應用程式之樣式內的觸發程序 (這些樣式可為明確或隱含樣式，但不能來自於預設樣式，預設樣式的優先順序較低)。  
  
7. **樣板觸發程序**： 樣式內之範本或直接套用之範本中的任何觸發程序。  
  
8. **樣式 setter**： 來自頁面或<xref:System.Windows.Setter>應用程式中的樣式內的值。  
  
9. **預設 (主題) 樣式**： 如需何時套用此樣式，以及主題樣式與主題樣式內範本之關聯的詳細資訊，請參閱本主題稍後的[預設 (主題) 樣式](#themestyles)。 在預設樣式內，優先順序如下：  
  
    1. 主題樣式中的作用中觸發程序。  
  
    2. 主題樣式中的 setter。  
  
10. **繼承。** 有幾個相依性屬性會從父項目繼承值到子項目，因此無須在整個應用程式的每一個項目上特別設定。 有關詳細資訊，請參閱[屬性值繼承](property-value-inheritance.md)。  
  
11. **來自相依性屬性中繼資料的預設值**： 任何指定的相依性屬性都可能會有屬性系統註冊為該特定屬性建立的預設值。 此外，繼承相依性屬性的衍生類別可選擇根據類型覆寫該中繼資料 (包括預設值)。 如需詳細資訊，請參閱[相依性屬性中繼資料](dependency-property-metadata.md)。 因為會在預設值之前檢查繼承，所以對繼承的屬性而言，父項目的預設值會優先於子項目。  因此，如果未在任何位置設定可繼承的屬性，就會使用在根項目或父項目上指定的預設值，而不是子項目的預設值。  
  
<a name="templatedparent"></a>
## <a name="templatedparent"></a>TemplatedParent  
 作為優先順序項目的 TemplatedParent 不會套用到您直接在標準應用程式標記中宣告之項目的任何屬性。 TemplatedParent 概念只對視覺化樹狀結構內因套用範本而產生的子項目有效。 當屬性系統搜索<xref:System.Windows.FrameworkElement.TemplatedParent%2A>範本查找值時，它將搜索創建該元素的範本。 範本中<xref:System.Windows.FrameworkElement.TemplatedParent%2A>的屬性值通常充當子項目上的本地值，但相對於本地值存在此較小的優先順序，因為範本可能共用。 如需詳細資訊，請參閱<xref:System.Windows.FrameworkElement.TemplatedParent%2A>。  
  
<a name="style_property"></a>
## <a name="the-style-property"></a>Style 屬性  
 前面描述的查找順序適用于所有可能的依賴項屬性，但屬性<xref:System.Windows.FrameworkElement.Style%2A>除外。 該<xref:System.Windows.FrameworkElement.Style%2A>屬性是唯一的，因為它本身無法設置樣式，因此優先順序項 5 到 8 不適用。 此外，不建議進行動畫或強制<xref:System.Windows.FrameworkElement.Style%2A>（動畫<xref:System.Windows.FrameworkElement.Style%2A>需要自訂動畫類）。 這留下了三種設置<xref:System.Windows.FrameworkElement.Style%2A>屬性的方法：  
  
- **明確樣式**： 屬性<xref:System.Windows.FrameworkElement.Style%2A>是直接設置的。 在大多數情況下，樣式不會內嵌定義，而是使用明確索引鍵將它當做資源參考。 在此情況下，Style 屬性本身就會當做區域數值，也就是優先順序項目 3。  
  
- **隱含樣式**： 屬性<xref:System.Windows.FrameworkElement.Style%2A>不是直接設置的。 但是，資源<xref:System.Windows.FrameworkElement.Style%2A>查找序列（頁面、應用程式）中的某個級別存在 ，並使用與要應用於樣式的類型匹配的資源鍵進行鍵控。 在這種情況下，<xref:System.Windows.FrameworkElement.Style%2A>屬性本身按序列中標識為專案 5 的優先順序執行。 可以通過對<xref:System.Windows.DependencyPropertyHelper><xref:System.Windows.FrameworkElement.Style%2A>屬性使用並在結果中查找<xref:System.Windows.BaseValueSource.ImplicitStyleReference>來檢測此情況。  
  
- **預設樣式**也稱為**主題樣式**。 屬性<xref:System.Windows.FrameworkElement.Style%2A>不是直接設置的，實際上將讀取為`null`運行時。 在此情況下，樣式會來自屬於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 展示引擎一部分的執行階段主題評估。  
  
 對於不在主題中的隱式樣式，類型必須完全符合 -`MyButton``Button`派生類不會隱式使用 樣式`Button`。  
  
<a name="themestyles"></a>
## <a name="default-theme-styles"></a>預設 (主題) 樣式  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 隨附的每個控制項都有預設樣式。 該預設樣式可能會視主題而不同，因此預設樣式有時也稱為主題樣式。  
  
 控制項的預設樣式中找到的最重要資訊是控制項範本，該範本作為其<xref:System.Windows.Controls.Control.Template%2A>屬性的 setter 存在於主題樣式中。 如果預設樣式沒有範本，則沒有自訂範本作為自訂樣式一部分的控制項將完全沒有視覺外觀。 預設樣式中的範本會為每個控制項的視覺外觀提供基本結構，而且也會定義在範本視覺化樹狀結構中定義的屬性與相對應控制項類別之間的連接。 每個控制項會公開一組屬性，這些屬性可影響控制項的視覺外觀，但不會完全取代範本。 例如，請考慮<xref:System.Windows.Controls.Primitives.Thumb>控制項的預設可視外觀，該外觀是 的<xref:System.Windows.Controls.Primitives.ScrollBar>元件。  
  
 A<xref:System.Windows.Controls.Primitives.Thumb>具有某些可自訂的屬性。 的預設範本<xref:System.Windows.Controls.Primitives.Thumb>創建一個基本結構/視覺化樹，其中有多個嵌套<xref:System.Windows.Controls.Border>元件，以創建斜面外觀。 如果作為範本一部分的屬性打算公開以供<xref:System.Windows.Controls.Primitives.Thumb>類自訂，則該屬性必須由範本中的[範本繫結](templatebinding-markup-extension.md)公開。 在 中<xref:System.Windows.Controls.Primitives.Thumb>，這些邊框的各種屬性共用綁定到 屬性（如 或<xref:System.Windows.Controls.Border.Background%2A><xref:System.Windows.Controls.Border.BorderThickness%2A>） 的範本。 但特定其他屬性或視覺化排列方式是用硬式編碼加入控制項範本，或繫結至直接來自於主題的值，除了取代整個範本之外，無法以其他方式變更。 一般而言，如果屬性來自於樣板化父項目且不由範本繫結公開，就無法使用樣式調整，因為沒有簡單的方式可將它設為目標。 但該屬性仍會受到所套用範本中的屬性值繼承所影響，或受到預設值所影響。  
  
 主題樣式在其定義中使用類型作為索引鍵。 但是，當主題應用於給定元素實例時，通過檢查控制項上的屬性<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>來執行此類型的主題查找。 這與隱含樣式使用常值 Type 的方式相反。 即使實現者<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>未更改該屬性，也會繼承到派生類的值（更改屬性的預定方式不是在屬性級別重寫該屬性，而是更改屬性中繼資料中的預設值）。 這種間接方式可讓基底類別為沒有樣式 (或者更重要的是，在該樣式內沒有範本，因此完全沒有預設視覺外觀) 的衍生項目定義主題樣式。 因此，您可以派生`MyButton`，<xref:System.Windows.Controls.Button>並且仍將獲取<xref:System.Windows.Controls.Button>預設範本。 如果您是 的`MyButton`控制項作者，並且需要其他行為，則可以重寫<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>依賴`MyButton`項屬性中繼資料以返回其他鍵，然後定義相關主題樣式，包括必須隨`MyButton``MyButton`控制項打包的範本。 如需主題、樣式和控制項撰寫的詳細資訊，請參閱[控制項撰寫概觀](../controls/control-authoring-overview.md)。  
  
<a name="resources"></a>
## <a name="dynamic-resource-references-and-binding"></a>動態資源參考和繫結  
 動態資源參考和繫結作業會採用其設定位置的優先順序。 例如，套用到區域數值的動態資源會依優先順序項目 3 作用，主題樣式內屬性 setter 的繫結會依優先順序項目 9 套用，依此類推。 由於動態資源參考和繫結必須能夠從應用程式的執行階段狀態取得值，因此決定任何指定屬性之屬性值優先順序的實際程序也會延伸至執行階段。  
  
 嚴格來說，動態資源參考不是屬性系統的一部分，但它們有自己的查閱順序，會與上面所列的順序互動。 該優先順序在 [XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)中有更詳細的說明。 基本上來說，該優先順序就是：項目優先於頁面根項目、應用程式、主題和系統。  
  
 動態資源和繫結具有其設定位置的優先順序，但會受到其值影響。 因此，如果您將動態資源或繫結設定為區域數值，區域數值的任何變更都會取代整個動態資源或繫結。 即使您調用<xref:System.Windows.DependencyObject.ClearValue%2A>方法以清除本地設置的值，也不會還原動態資源或綁定。 實際上，如果調用<xref:System.Windows.DependencyObject.ClearValue%2A>具有動態資源或綁定的屬性（沒有文本本地值），則<xref:System.Windows.DependencyObject.ClearValue%2A>調用也會清除它們。  
  
<a name="setcurrentvalue"></a>
## <a name="setcurrentvalue"></a>SetCurrentValue  
 該方法<xref:System.Windows.DependencyObject.SetCurrentValue%2A>是設置屬性的另一種方法，但它的優先順序順序不一。 相反，<xref:System.Windows.DependencyObject.SetCurrentValue%2A>使您能夠更改屬性的值，而無需覆蓋前一個值的源。 您可以使用<xref:System.Windows.DependencyObject.SetCurrentValue%2A>任何時間設置值，而不給予該值本地值的優先順序。 例如，如果屬性由觸發器設置，然後通過<xref:System.Windows.DependencyObject.SetCurrentValue%2A>分配另一個值，則屬性系統仍尊重觸發器，如果觸發器的操作發生，該屬性將更改。 <xref:System.Windows.DependencyObject.SetCurrentValue%2A>使您能夠更改屬性的值，而不為屬性提供具有更高優先順序的源。 同樣，可以使用<xref:System.Windows.DependencyObject.SetCurrentValue%2A>更改屬性的值而不覆蓋綁定。  
  
<a name="animations"></a>
## <a name="coercion-animations-and-base-value"></a>強制型轉、動畫和基底值  
 強制和動畫都作用於此 SDK 中稱為"基值"的值。 因此，基底值是透過在項目中往上評估，直到達到第 2 個項目來決定的值。  
  
 對動畫而言，如果動畫未同時指定特定行為的 "From" 和 "To"，或是動畫刻意在完成後還原成基底值，則基底值可能會對動畫值造成影響。 若要了解實際的情形，請執行 [From、To 和 By 動畫目標值範例](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/TargetValues)。 請試著設定此範例中矩形高度的區域數值，讓初始區域數值與動畫中的任何 "From" 不同。 您會發現，動畫會立即使用 "From" 值啟動，並在啟動後取代基底值。 動畫可能指定在動畫完成後通過指定 Stop<xref:System.Windows.Media.Animation.FillBehavior>返回到動畫之前找到的值。 在此之後，就會使用正常優先順序來決定基底值。  
  
 您可將多個動畫套用到單一屬性，每個動畫可能已透過值優先順序的不同點定義。 不過，這些動畫可能會將值結合起來，而不是只從較高的優先順序套用動畫。 這完全取決於動畫的定義方式，以及要顯示為動畫之值的類型。 如需將屬性顯示為動畫的詳細資訊，請參閱[動畫概觀](../graphics-multimedia/animation-overview.md)。  
  
 強制型轉的套用層級最高。 即使是已在執行中的應用程式也受值強制型轉的限制。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的某些現有相依性屬性有內建強制型轉。 對於自訂依賴項屬性，通過在創建屬性時編寫 和<xref:System.Windows.CoerceValueCallback>傳遞回檔作為中繼資料的一部分來定義自訂依賴項屬性的強制行為。 您也可以覆寫現有屬性的強制型轉行為，方式是在衍生類別中覆寫該屬性上的中繼資料。 強制型轉與基底值互動的方式是，強制型轉上的條件約束會以當時存在的條件約束套用，但仍保留基底值。 因此，如果強制型轉中的條件約束稍後放寬，強制型轉就會傳回最接近該基底值的值，而且強制型轉對屬性的影響有可能會在所有條件約束都放寬之後停止。 如需強制型轉行為的詳細資訊，請參閱[相依性屬性回呼和驗證](dependency-property-callbacks-and-validation.md)。  
  
<a name="triggers"></a>
## <a name="trigger-behaviors"></a>觸發程序行為  
 控制項通常會將觸發程序行為定義為其在主題中之預設樣式的一部分。 在控制項上設定區域屬性，可能會使觸發程序無法從視覺或行為上回應使用者驅動的事件。 屬性觸發器的最常見用途是控制項或狀態屬性（如<xref:System.Windows.Controls.Primitives.Selector.IsSelected%2A>） 例如，預設情況下，當禁用<xref:System.Windows.Controls.Button>（為<xref:System.Windows.UIElement.IsEnabled%2A>is`false`的觸發器）<xref:System.Windows.Controls.Control.Foreground%2A>時，主題樣式中的值是導致控制項顯示為"灰顯"的原因。 但是，如果您設置了本地<xref:System.Windows.Controls.Control.Foreground%2A>值，則即使在此屬性觸發的方案中，該正常的灰出顏色也會優先于本地屬性集來否決。 當您為具有主題層級觸發程序行為的屬性設定值時，請特別小心，並確保不會不當干擾該控制項的預期使用者體驗。  
  
<a name="clearvalue"></a>
## <a name="clearvalue-and-value-precedence"></a>ClearValue 和值優先順序  
 該方法<xref:System.Windows.DependencyObject.ClearValue%2A>提供了一個權宜之計，用於清除在元素上設置的依賴項屬性中的任何本地應用值。 但是，調用<xref:System.Windows.DependencyObject.ClearValue%2A>並不保證在屬性註冊期間在中繼資料中建立的預設值是新的有效值。 值優先順序中的所有其他參與者仍在作用中。 只有在本機設定的值會從優先順序移除。 例如，如果調用<xref:System.Windows.DependencyObject.ClearValue%2A>由主題樣式設置該屬性的屬性，則主題值將應用為新值，而不是基於中繼資料的預設值。 如果要將所有屬性值參與者從流程中拉出，並將該值設置為已註冊的中繼資料預設值，則可以通過查詢依賴項屬性中繼資料最終獲取該預設值，然後可以使用預設值在本地設置具有 調用 的屬性<xref:System.Windows.DependencyObject.SetValue%2A>。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.DependencyObject>
- <xref:System.Windows.DependencyProperty>
- [相依性屬性概觀](dependency-properties-overview.md)
- [自訂相依性屬性](custom-dependency-properties.md)
- [相依性屬性回呼和驗證](dependency-property-callbacks-and-validation.md)
