---
title: 相依性屬性值優先順序
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], classes as owners
- dependency properties [WPF], metadata
- classes [WPF], owners of dependency properties
- metadata [WPF], dependency properties
ms.assetid: 1fbada8e-4867-4ed1-8d97-62c07dad7ebc
ms.openlocfilehash: 7719c39c82b69421477cadf9ae5caf9f9f55b457
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="dependency-property-value-precedence"></a>相依性屬性值優先順序
<a name="introduction"></a> 本主題說明 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 屬性系統的運作方式如何影響相依性屬性的值，並描述屬性系統套用到屬性有效值的優先順序。  
    
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 本主題假設您已從 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類別的現有相依性屬性消費者角度了解相依性屬性，並已閱讀[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。 為遵循本主題中的範例，您也應該了解 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 並知道如何撰寫 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。  
  
<a name="intro"></a>   
## <a name="the-wpf-property-system"></a>WPF 屬性系統  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統提供一個強大的方法，透過各種因素來決定相依性屬性的值，並啟用即時屬性驗證、晚期繫結，以及將其他屬性的值變更通知相關屬性等功能。 用來決定相依性屬性值的實際順序和邏輯相當複雜。 不過，知道此順序將有助於避免不必要的屬性設定，也可釐清試圖影響或預測相依性屬性值，為何最後並未產生所預期的值。  
  
<a name="multiple_sets"></a>   
## <a name="dependency-properties-might-be-set-in-multiple-places"></a>相依性屬性可能在多處「設定」  
 以下是範例[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]所在相同的屬性 (<xref:System.Windows.Controls.Control.Background%2A>) 有三種不同 「 設定 」 可能會影響該值的作業。  
  
 [!code-xaml[PropertiesOvwSupport#DPPrecedence](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#dpprecedence)]  
  
 在此，您預期會套用哪個色彩 - 紅色、綠色，還是藍色？  
  
 除了動畫值和強制型轉之外，區域屬性集會設為最高優先順序。 如果您在本機設定值，可預期該值將會被接受，甚至優先於任何樣式或控制項範本。 在範例中，這裡<xref:System.Windows.Controls.Control.Background%2A>區域設定為紅色。 因此，即使它是隱含樣式，原本套用於在該範圍內，該類型的所有項目，在此範圍中，定義的樣式不提供最高優先順序<xref:System.Windows.Controls.Control.Background%2A>屬性及其值。  如果從該 Button 執行個體移除區域數值 Red，則樣式會具有優先順序，因此按鈕會從樣式取得 Background 值。  在樣式內，觸發程序具有較高的優先順序，因此如果將滑鼠移至按鈕上方，按鈕會變成藍色，否則就會是綠色的。  
  
<a name="listing"></a>   
## <a name="dependency-property-setting-precedence-list"></a>相依性屬性設定優先順序清單  
 以下是屬性系統在指派相依性屬性的執行階段值時，所使用的決定順序。 最高優先順序會先列出。 此清單更進一步說明了[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)中所述的部分概要。  
  
1.  **屬性系統強制型轉**： 如需強制型轉的詳細資訊，請參閱本主題稍後的[強制型轉、動畫和基底值](#animations)。  
  
2.  **作用中動畫或具有 Hold 行為的動畫**： 屬性的動畫必須優先於基底 (非動畫) 值，才能有任何實際效果，即使該值是在本機設定也一樣。 如需詳細資訊，請參閱本主題稍後的[強制型轉、動畫和基底值](#animations)。  
  
3.  **區域數值**： 為區域數值可能會設定 「 包裝函式 」 屬性，也等於中的屬性或屬性項目設定的方便性，不論透過[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，或藉由呼叫<xref:System.Windows.DependencyObject.SetValue%2A>[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]使用特定的執行個體的屬性。 如果使用繫結或資源來設定區域數值，其在優先順序中的作用就如同設定直接值。  
  
4.  **TemplatedParent 範本屬性**： 項目有<xref:System.Windows.FrameworkElement.TemplatedParent%2A>是建立為範本的一部分 (<xref:System.Windows.Controls.ControlTemplate>或<xref:System.Windows.DataTemplate>)。 如需何時套用此屬性的詳細資訊，請參閱本主題稍後的 [TemplatedParent](#templatedparent)。 在範本內，優先順序如下：  
  
    1.  從觸發程序<xref:System.Windows.FrameworkElement.TemplatedParent%2A>範本。  
  
    2.  屬性集 (通常透過[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]屬性) 在<xref:System.Windows.FrameworkElement.TemplatedParent%2A>範本。  
  
5.  **隱含樣式**： 僅適用於 `Style` 屬性。 `Style` 屬性是由具有符合項目類型之索引鍵的任何樣式資源所填入。 該樣式資源必須位於頁面或應用程式中；查閱隱含樣式資源不會進行到主題中。  
  
6.  **樣式觸發程序**： 來自於頁面或應用程式之樣式內的觸發程序 (這些樣式可為明確或隱含樣式，但不能來自於預設樣式，預設樣式的優先順序較低)。  
  
7.  **樣板觸發程序**： 樣式內之範本或直接套用之範本中的任何觸發程序。  
  
8.  **樣式 setter**： 從數值<xref:System.Windows.Setter>樣式頁面或應用程式內。  
  
9. **預設 (主題) 樣式**： 如需何時套用此樣式，以及主題樣式與主題樣式內範本之關聯的詳細資訊，請參閱本主題稍後的[預設 (主題) 樣式](#themestyles)。 在預設樣式內，優先順序如下：  
  
    1.  主題樣式中的作用中觸發程序。  
  
    2.  主題樣式中的 setter。  
  
10. **繼承**： 有幾個相依性屬性會從父項目繼承值到子項目，因此無須在整個應用程式的每一個項目上特別設定。 如需詳細資訊，請參閱[屬性值繼承](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)。  
  
11. **來自相依性屬性中繼資料的預設值**： 任何指定的相依性屬性都可能會有屬性系統註冊為該特定屬性建立的預設值。 此外，繼承相依性屬性的衍生類別可選擇根據類型覆寫該中繼資料 (包括預設值)。 如需詳細資訊，請參閱[相依性屬性中繼資料](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)。 因為會在預設值之前檢查繼承，所以對繼承的屬性而言，父項目的預設值會優先於子項目。  因此，如果未在任何位置設定可繼承的屬性，就會使用在根項目或父項目上指定的預設值，而不是子項目的預設值。  
  
<a name="templatedparent"></a>   
## <a name="templatedparent"></a>TemplatedParent  
 作為優先順序項目的 TemplatedParent 不會套用到您直接在標準應用程式標記中宣告之項目的任何屬性。 TemplatedParent 概念只對視覺化樹狀結構內因套用範本而產生的子項目有效。 對屬性系統的搜尋時<xref:System.Windows.FrameworkElement.TemplatedParent%2A>值的範本，它會搜尋建立該元素的範本。 屬性值從<xref:System.Windows.FrameworkElement.TemplatedParent%2A>範本通常當做已設定為本機值在子元素，但此較低的優先順序與本機值存在的原因可能共用的範本。 如需詳細資訊，請參閱 <xref:System.Windows.FrameworkElement.TemplatedParent%2A>。  
  
<a name="style_property"></a>   
## <a name="the-style-property"></a>Style 屬性  
 查閱稍早所述的順序套用至所有可能的相依性屬性，但有一個例外：<xref:System.Windows.FrameworkElement.Style%2A>屬性。 <xref:System.Windows.FrameworkElement.Style%2A>屬性是唯一的它無法自行設計，因此不會套用優先順序項目 5 到 8。 此外，顯示動畫，或強制型轉<xref:System.Windows.FrameworkElement.Style%2A>不建議您 (和動畫<xref:System.Windows.FrameworkElement.Style%2A>需要自訂動畫類別)。 這會保留三種方式，<xref:System.Windows.FrameworkElement.Style%2A>可能設定屬性：  
  
-   **明確樣式**： <xref:System.Windows.FrameworkElement.Style%2A>屬性直接設定。 在大多數情況下，樣式不會內嵌定義，而是使用明確索引鍵將它當做資源參考。 在此情況下，Style 屬性本身就會當做區域數值，也就是優先順序項目 3。  
  
-   **隱含樣式**： <xref:System.Windows.FrameworkElement.Style%2A>未直接設定屬性。 不過，<xref:System.Windows.FrameworkElement.Style%2A>存在資源查閱序列 （頁面、 應用程式） 中某個層級，而且做為索引鍵使用的樣式會套用至型別對應的資源索引鍵。 在此情況下，<xref:System.Windows.FrameworkElement.Style%2A>屬性本身做為 5 的項目序列中識別優先順序。 使用偵測到此狀況<xref:System.Windows.DependencyPropertyHelper>針對<xref:System.Windows.FrameworkElement.Style%2A>屬性，並尋找<xref:System.Windows.BaseValueSource.ImplicitStyleReference>結果中。  
  
-   **預設樣式**也稱為**主題樣式**。 <xref:System.Windows.FrameworkElement.Style%2A>屬性不會直接設定，而且事實上會為讀取`null`執行階段為止。 在此情況下，樣式會來自屬於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 展示引擎一部分的執行階段主題評估。  
  
 對於不在主題中的隱含樣式，類型必須完全相符 - `MyButton``Button` 衍生的類別不會隱含使用 `Button` 的樣式。  
  
<a name="themestyles"></a>   
## <a name="default-theme-styles"></a>預設 (主題) 樣式  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 隨附的每個控制項都有預設樣式。 該預設樣式可能會視主題而不同，因此預設樣式有時也稱為主題樣式。  
  
 最重要的資訊控制項為其控制項範本，存在於佈景主題樣式的 setter 稱為預設樣式中找到其<xref:System.Windows.Controls.Control.Template%2A>屬性。 如果預設樣式沒有範本，則沒有自訂範本作為自訂樣式一部分的控制項將完全沒有視覺外觀。 預設樣式中的範本會為每個控制項的視覺外觀提供基本結構，而且也會定義在範本視覺化樹狀結構中定義的屬性與相對應控制項類別之間的連接。 每個控制項會公開一組屬性，這些屬性可影響控制項的視覺外觀，但不會完全取代範本。 例如，請考慮預設視覺外觀的<xref:System.Windows.Controls.Primitives.Thumb>控制項，這是元件的<xref:System.Windows.Controls.Primitives.ScrollBar>。  
  
 A<xref:System.Windows.Controls.Primitives.Thumb>有特定的自訂屬性。 預設範本<xref:System.Windows.Controls.Primitives.Thumb>建立基本結構 / 視覺化樹狀結構有數個巢狀<xref:System.Windows.Controls.Border>元件，以建立斜面的外觀。 如果此屬性是範本的一部分，要公開的自訂<xref:System.Windows.Controls.Primitives.Thumb>類別，則該屬性必須公開[TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)，範本中。 如果是<xref:System.Windows.Controls.Primitives.Thumb>，這些框線的各種屬性這類共用範本繫結至屬性<xref:System.Windows.Controls.Border.Background%2A>或<xref:System.Windows.Controls.Border.BorderThickness%2A>。 但特定其他屬性或視覺化排列方式是用硬式編碼加入控制項範本，或繫結至直接來自於主題的值，除了取代整個範本之外，無法以其他方式變更。 一般而言，如果屬性來自於樣板化父項目且不由範本繫結公開，就無法使用樣式調整，因為沒有簡單的方式可將它設為目標。 但該屬性仍會受到所套用範本中的屬性值繼承所影響，或受到預設值所影響。  
  
 主題樣式在其定義中使用類型作為索引鍵。 不過，當佈景主題套用至指定的項目執行個體後，佈景主題此類型執行查閱藉由檢查<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>在控制項上的屬性。 這與隱含樣式使用常值 Type 的方式相反。 值<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>即使實作器不會變更它 （預期的方式變更的屬性是不覆寫它，在屬性層級，但若要改為其預設值屬性中繼資料中的變更），讓衍生類別會繼承。 這種間接方式可讓基底類別為沒有樣式 (或者更重要的是，在該樣式內沒有範本，因此完全沒有預設視覺外觀) 的衍生項目定義主題樣式。 因此，您也可以衍生`MyButton`從<xref:System.Windows.Controls.Button>，仍然會出現<xref:System.Windows.Controls.Button>預設範本。 如果您的控制項作者`MyButton`和您想要不同的行為，您無法覆寫的相依性屬性中繼資料<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>上`MyButton`傳回不同的索引鍵，並接著定義包括範本相關的佈景主題樣式如`MyButton`，您必須封裝與您`MyButton`控制項。 如需主題、樣式和控制項撰寫的詳細資訊，請參閱[控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)。  
  
<a name="resources"></a>   
## <a name="dynamic-resource-references-and-binding"></a>動態資源參考和繫結  
 動態資源參考和繫結作業會採用其設定位置的優先順序。 例如，套用到區域數值的動態資源會依優先順序項目 3 作用，主題樣式內屬性 setter 的繫結會依優先順序項目 9 套用，依此類推。 由於動態資源參考和繫結必須能夠從應用程式的執行階段狀態取得值，因此決定任何指定屬性之屬性值優先順序的實際程序也會延伸至執行階段。  
  
 嚴格來說，動態資源參考不是屬性系統的一部分，但它們有自己的查閱順序，會與上面所列的順序互動。 該優先順序在 [XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)中有更詳細的說明。 基本上來說，該優先順序就是：項目優先於頁面根項目、應用程式、主題和系統。  
  
 動態資源和繫結具有其設定位置的優先順序，但會受到其值影響。 因此，如果您將動態資源或繫結設定為區域數值，區域數值的任何變更都會取代整個動態資源或繫結。 即使您呼叫<xref:System.Windows.DependencyObject.ClearValue%2A>方法，以清除本機設定值，動態資源或繫結不會還原。 事實上，如果您呼叫<xref:System.Windows.DependencyObject.ClearValue%2A>屬性具有動態資源或繫結 （與任何常值的本機值），它們會依清除<xref:System.Windows.DependencyObject.ClearValue%2A>太呼叫。  
  
<a name="setcurrentvalue"></a>   
## <a name="setcurrentvalue"></a>SetCurrentValue  
 <xref:System.Windows.DependencyObject.SetCurrentValue%2A>方法為另一種方式來設定屬性，但是並不依照優先權順序。 相反地，<xref:System.Windows.DependencyObject.SetCurrentValue%2A>可讓您變更屬性的值，而不覆寫先前的值的來源。 您可以使用<xref:System.Windows.DependencyObject.SetCurrentValue%2A>任何您想要設定值，而不需給予該值的優先順序為區域數值的時間。 例如，如果屬性是觸發程序來設定，然後指派另一個透過<xref:System.Windows.DependencyObject.SetCurrentValue%2A>、 對屬性系統仍尊重觸發程序和觸發程序的動作發生時，會變更屬性。 <xref:System.Windows.DependencyObject.SetCurrentValue%2A> 可讓您變更屬性的值沒有任何具有較高優先順序的來源。 同樣地，您可以使用<xref:System.Windows.DependencyObject.SetCurrentValue%2A>若要變更屬性的值，而不覆寫繫結。  
  
<a name="animations"></a>   
## <a name="coercion-animations-and-base-value"></a>強制型轉、動畫和基底值  
 在這個 [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] 中，強制型轉和動畫都會在名為「基底值」的值上作用。 因此，基底值是透過在項目中往上評估，直到達到第 2 個項目來決定的值。  
  
 對動畫而言，如果動畫未同時指定特定行為的 "From" 和 "To"，或是動畫刻意在完成後還原成基底值，則基底值可能會對動畫值造成影響。 若要了解實際的情形，請執行 [From、To 和 By 動畫目標值範例](http://go.microsoft.com/fwlink/?LinkID=159988)。 請試著設定此範例中矩形高度的區域數值，讓初始區域數值與動畫中的任何 "From" 不同。 您會發現，動畫會立即使用 "From" 值啟動，並在啟動後取代基底值。 動畫可能會指定一旦完成藉由指定 停止動畫之前找到的值傳回<xref:System.Windows.Media.Animation.FillBehavior>。 在此之後，就會使用正常優先順序來決定基底值。  
  
 您可將多個動畫套用到單一屬性，每個動畫可能已透過值優先順序的不同點定義。 不過，這些動畫可能會將值結合起來，而不是只從較高的優先順序套用動畫。 這完全取決於動畫的定義方式，以及要顯示為動畫之值的類型。 如需將屬性顯示為動畫的詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
 強制型轉的套用層級最高。 即使是已在執行中的應用程式也受值強制型轉的限制。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的某些現有相依性屬性有內建強制型轉。 您可以自訂相依性屬性，定義自訂相依性屬性的強制型轉行為來撰寫<xref:System.Windows.CoerceValueCallback>和中繼資料的一部分傳遞回呼，當您建立屬性。 您也可以覆寫現有屬性的強制型轉行為，方式是在衍生類別中覆寫該屬性上的中繼資料。 強制型轉與基底值互動的方式是，強制型轉上的條件約束會以當時存在的條件約束套用，但仍保留基底值。 因此，如果強制型轉中的條件約束稍後放寬，強制型轉就會傳回最接近該基底值的值，而且強制型轉對屬性的影響有可能會在所有條件約束都放寬之後停止。 如需強制型轉行為的詳細資訊，請參閱[相依性屬性回呼和驗證](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)。  
  
<a name="triggers"></a>   
## <a name="trigger-behaviors"></a>觸發程序行為  
 控制項通常會將觸發程序行為定義為其在主題中之預設樣式的一部分。 在控制項上設定區域屬性，可能會使觸發程序無法從視覺或行為上回應使用者驅動的事件。 屬性觸發程序的常見用法是針對控制項或狀態屬性例如<xref:System.Windows.Controls.Primitives.Selector.IsSelected%2A>。 例如，根據預設時<xref:System.Windows.Controls.Button>已停用 (針對觸發<xref:System.Windows.UIElement.IsEnabled%2A>是`false`) 則<xref:System.Windows.Controls.Control.Foreground%2A>佈景主題樣式的值是什麼情況會讓控制項出現 「 灰色 」。 但是，如果您已設定本機<xref:System.Windows.Controls.Control.Foreground%2A>值正常的灰色外色彩將取消的優先順序，根據您的本機屬性集，即使在這個屬性觸發案例。 當您為具有主題層級觸發程序行為的屬性設定值時，請特別小心，並確保不會不當干擾該控制項的預期使用者體驗。  
  
<a name="clearvalue"></a>   
## <a name="clearvalue-and-value-precedence"></a>ClearValue 和值優先順序  
 <xref:System.Windows.DependencyObject.ClearValue%2A>方法提供代替品表示若要清除的設定項目的相依性屬性的任何本機套用的值。 不過，呼叫<xref:System.Windows.DependencyObject.ClearValue%2A>並不保證，如同在屬性註冊期間所建立中繼資料中的預設值是新生效的值。 值優先順序中的所有其他參與者仍在作用中。 只有在本機設定的值會從優先順序移除。 例如，如果您呼叫<xref:System.Windows.DependencyObject.ClearValue%2A>從中佈景主題樣式，也會設定該屬性，然後再佈景主題會套用的值為新的值，而不是中繼資料為基礎的預設屬性。 如果您想要採用跨處理序的所有屬性值參與者，並將值設為預設的已註冊的中繼資料，您可以取得預設值，肯定是藉由查詢相依性屬性中繼資料，然後可以在本機使用的預設值設定屬性，藉由呼叫<xref:System.Windows.DependencyObject.SetValue%2A>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.DependencyObject>  
 <xref:System.Windows.DependencyProperty>  
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [相依性屬性回呼和驗證](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)
