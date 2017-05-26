---
title: "相依性屬性值優先順序 | Microsoft Docs"
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
  - "類別, 相依性屬性的擁有者"
  - "相依性屬性, 做為擁有者的類別"
  - "相依性屬性, 中繼資料"
  - "中繼資料, 相依性屬性"
ms.assetid: 1fbada8e-4867-4ed1-8d97-62c07dad7ebc
caps.latest.revision: 27
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 26
---
# 相依性屬性值優先順序
<a name="introduction"></a> 本主題將說明 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 屬性系統的運作方式如何影響[相依性屬性](GTMT)的值，並描述屬性系統套用到屬性有效值的優先順序。  
  
   
  
<a name="prerequisites"></a>   
## 必要條件  
 本主題假設您已了解相依性屬性，知道如何使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類別上的現有相依性屬性，而且已閱讀過[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。  為了能夠理解本主題中的範例，您也應該了解[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，並知道如何撰寫 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。  
  
<a name="intro"></a>   
## WPF 屬性系統  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統提供了強大的方法，可讓相依性屬性的值由各種不同因素決定，以提供像是即時屬性驗證、晚期繫結，以及將其他屬性的值變更通知相關屬性等功能。  用來決定相依性屬性值的順序和邏輯相當複雜。  不過，知道此順序將有助於避免不必要的屬性設定，也可釐清為什麼試圖影響或預測的相依性屬性值，最後並未產生所預期的值。  
  
<a name="multiple_sets"></a>   
## 相依性屬性可在多處「設定」  
 以下是範例 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，其中同一個屬性 \(<xref:System.Windows.Controls.Control.Background%2A>\) 有三個可能會影響值的不同 "set" 作業。  
  
 [!code-xml[PropertiesOvwSupport#DPPrecedence](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#dpprecedence)]  
  
 在此例中，您認為會套用哪個色彩 \- 紅色、綠色還是藍色？  
  
 除了動畫值和強制型轉 \(Coercion\)，區域屬性集會設為最高優先順序。  如果您在區域設定值，可預期該值將會被接受，甚至優先於任何樣式或控制項樣板。  在此例中，<xref:System.Windows.Controls.Control.Background%2A> 在區域是設為 Red。  因此，在此範圍中定義的樣式雖是隱含樣式，且原本應套用到該範圍中屬於該型別的所有項目，也沒有提供 <xref:System.Windows.Controls.Control.Background%2A> 屬性其值的最高優先順序。  如果從該 Button 執行個體移除區域值 Red，那麼樣式就具有優先權，按鈕會從樣式取得 Background 值。  在樣式內，觸發程序具有優先權，因此如果滑鼠移至按鈕上方，按鈕會變成藍色，否則就會是綠色的。  
  
<a name="listing"></a>   
## 相依性屬性設定優先順序清單  
 以下是屬性系統在指派相依性屬性的執行階段值時，所使用的決定順序。  最高優先順序會最先列出。  此清單更進一步說明了[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)中所述的部分概要。  
  
1.  **屬性系統強制型轉**： 如需強制型轉的詳細資訊，請參閱本主題稍後的[強制型轉、動畫和基底值](#animations)。  
  
2.  **作用中動畫或有 Hold 行為的動畫**： 為能產生實際效用，屬性的動畫必須優先於基底 \(非動畫\) 值，即使該值是在區域設定的。  如需詳細資訊，請參閱本主題稍後的[強制型轉、動畫和基底值](#animations)。  
  
3.  **區域值**： 區域值可透過「包裝函式」屬性之便設定，這也等於是設定為 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 的屬性 \(Attribute\) 或屬性 \(Property\) 項目，或者，可使用特定執行個體的屬性，透過呼叫 <xref:System.Windows.DependencyObject.SetValue%2A> [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] 方法來設定。  如果使用繫結或資源來設定區域值，其在優先順序中的作用就如同設定直接值。  
  
4.  **TemplatedParent 樣板屬性**： 如果項目是做為樣板 \(<xref:System.Windows.Controls.ControlTemplate> 或 <xref:System.Windows.DataTemplate>\) 的一部分建立的，它會具有 <xref:System.Windows.FrameworkElement.TemplatedParent%2A>。  如需此屬性何時套用的詳細資訊，請參閱本主題稍後的 [TemplatedParent](#templatedparent)。  在樣板內，優先順序如下：  
  
    1.  來自於 <xref:System.Windows.FrameworkElement.TemplatedParent%2A> 樣板的觸發程序。  
  
    2.  <xref:System.Windows.FrameworkElement.TemplatedParent%2A> 樣板中的屬性 \(Property\) 集 \(通常是透過 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 屬性 \(Attribute\)\)。  
  
5.  **隱含樣式**： 僅適用於 `Style` 屬性。  `Style` 屬性會由索引鍵符合該項目型別的任何樣式資源填入。  該樣式資源必須位於頁面或應用程式；查閱隱含樣式資源不會進行到主題中。  
  
6.  **樣式觸發程序**： 來自頁面或應用程式的樣式內的觸發程序 \(這些樣式可為明確或隱含樣式，但不能來自於預設樣式，預設樣式的優先順序較低\)。  
  
7.  **樣板觸發程序**： 來自於樣式內樣板或直接套用樣板的任何觸發程序。  
  
8.  **樣式 setter**： 此值來自頁面或應用程式的樣式內的 <xref:System.Windows.Setter>。  
  
9. **預設 \(主題\) 樣式**： 如需此樣式何時套用，以及主題樣式如何與主題樣式內的樣板相關，請參閱本主題稍後的[預設 \(主題\) 樣式](#themestyles)。  在預設樣式內，優先順序如下：  
  
    1.  主題樣式中的作用中觸發程序。  
  
    2.  主題樣式中的 Setter。  
  
10. **繼承** ：有幾個相依性屬性會從父項目繼承值到子項目，因此無須在整個應用程式的每一個項目上特別設定。  如需詳細資訊，請參閱[屬性值繼承](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)。  
  
11. **來自相依性屬性中繼資料的預設值。** 任何指定的相依性屬性都可能會有屬性系統註冊為該屬性建立的預設值。  此外，繼承相依性屬性的衍生類別可選擇根據型別覆寫該中繼資料 \(包括預設值\)。  如需詳細資訊，請參閱[相依性屬性中繼資料](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)。  由於繼承會在預設值之前檢查，所以對繼承的屬性來說，父項目的預設值會優先於子項目。  因此，如果沒有在任何位置設定可繼承的屬性，就會使用在根項目或父項目上指定的預設值，而非子項目的預設值。  
  
<a name="templatedparent"></a>   
## TemplatedParent  
 TemplatedParent 當做優先順序項目時，不會套用到您直接在標準應用程式標記中宣告之項目的任何屬性。  TemplatedParent 概念只對視覺化樹狀結構內因套用樣板而產生的子項目有效。  當屬性系統搜尋 <xref:System.Windows.FrameworkElement.TemplatedParent%2A> 樣板中的值時，它會搜尋建立該項目的樣板。  來自 <xref:System.Windows.FrameworkElement.TemplatedParent%2A> 樣板的屬性值通常會當成在子項目上設定的區域值，但其優先順序會比存在的區域值低，因為樣板有可能共用。  如需詳細資訊，請參閱<xref:System.Windows.FrameworkElement.TemplatedParent%2A>。  
  
<a name="style_property"></a>   
## Style 屬性  
 上述查閱順序適用於所有可能的相依性屬性，但有一個除外，那就是：<xref:System.Windows.FrameworkElement.Style%2A> 屬性。  <xref:System.Windows.FrameworkElement.Style%2A> 屬性之所以獨特，是因為它本身無法設計樣式，因此優先順序項目 5 至 8 並不適用。  此外，也不建議將 <xref:System.Windows.FrameworkElement.Style%2A> 顯示為動畫或強制型轉 \(將 <xref:System.Windows.FrameworkElement.Style%2A> 顯示為動畫需要自訂動畫類別\)。  如此一來，就只有三種方式可設定 <xref:System.Windows.FrameworkElement.Style%2A> 屬性：  
  
-   **明確樣式**： <xref:System.Windows.FrameworkElement.Style%2A> 屬性直接設定。  在大多數情況下，樣式不會內嵌定義，而是使用明確索引鍵，將它當做資源參考。  在此情況下，Style 屬性本身就會當做區域值，即為優先順序項目 3。  
  
-   **隱含樣式**： <xref:System.Windows.FrameworkElement.Style%2A> 屬性不直接設定。  不過，<xref:System.Windows.FrameworkElement.Style%2A> 會存在於資源查閱順序的某個層級 \(頁面、應用程式\)，而且會使用與套用樣式的型別相符的資源索引鍵加上索引鍵。  在此情況下，<xref:System.Windows.FrameworkElement.Style%2A> 屬性本身會根據序列中定義的優先順序做為項目 5。  此條件可藉由對 <xref:System.Windows.FrameworkElement.Style%2A> 屬性使用 <xref:System.Windows.DependencyPropertyHelper>，然後在結果中尋找 <xref:System.Windows.BaseValueSource> 的方式進行偵測。  
  
-   **預設樣式**，也稱為**主題樣式**： <xref:System.Windows.FrameworkElement.Style%2A> 屬性不會直接設定，實際上，它會讀取為 `null`，直到執行階段為止。  在此情況下，樣式會來自屬於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 展示引擎一部分的執行階段主題評估。  
  
 對於不在主題中的隱含樣式，型別必須完全相符 \- `MyButton` `Button` 衍生的類別不會隱含使用 `Button` 的樣式。  
  
<a name="themestyles"></a>   
## 預設 \(主題\) 樣式  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 隨附的每個控制項都有預設樣式。  該預設樣式可能會視主題而不同，因此預設樣式有時也稱為主題樣式。  
  
 對控制項來說，在預設樣式內找到的最重要資訊就是其控制項樣板，這在主題樣式中會以其 <xref:System.Windows.Controls.Control.Template%2A> 屬性的 setter 存在。  如果預設樣式沒有樣板，則沒有自訂樣板做為自訂樣式一部分的控制項將完全沒有視覺外觀。  來自預設樣式的樣板會為每個控制項的視覺外觀提供基本結構，而且也會定義在樣板視覺化樹狀結構中定義的屬性與相對應控制項類別之間的連接。  每個控制項會公開一組屬性，這些屬性可影響控制項的視覺外觀，但不會完全取代樣板。  例如，以 <xref:System.Windows.Controls.Primitives.Thumb> 控制項的預設視覺外觀來說明，這個控制項是 <xref:System.Windows.Controls.Primitives.ScrollBar> 的元件。  
  
 <xref:System.Windows.Controls.Primitives.Thumb> 有幾個可自訂的屬性。  <xref:System.Windows.Controls.Primitives.Thumb> 的預設樣板會建立基礎結構\/視覺化樹狀結構，其中有幾個巢狀 <xref:System.Windows.Controls.Border> 元件，以產生斜邊外觀。  如果屬於樣板一部分的屬性不打算公開供 <xref:System.Windows.Controls.Primitives.Thumb> 類別自訂，那麼該屬性就必須由 [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) 在樣板內公開。  在 <xref:System.Windows.Controls.Primitives.Thumb> 的情況中，這些框線的各種屬性共用如 <xref:System.Windows.Controls.Border.Background%2A> 或 <xref:System.Windows.Controls.Border.BorderThickness%2A> 等屬性的樣板繫結。  但特定其他屬性或視覺化排列方式是用硬式編碼加入控制項樣板，或繫結至直接來自於主題的值，除了取代整個樣板之外，無法以其他方式變更。  一般來說，如果屬性來自於樣板化父項目且不由樣板繫結公開，就無法使用樣式調整，因為沒有簡單的方式可將它設為目標。  但是，該屬性仍可由所套用樣板中的屬性值繼承影響，或為預設值所影響。  
  
 主題樣式在其定義中使用型別做為索引鍵。  不過，當主題套用到指定的項目執行個體時，此型別的主題查閱會藉由檢查控制項上的 <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> 屬性來執行。  這與隱含樣式使用常值 Type 的方式相反。  <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> 的值會繼承給衍生類別，即使實作器並未變更它也一樣 \(變更屬性的方式不是要在屬性層級覆寫它，而是要變更其在屬性中繼資料中的預設值\)。  這種間接方式可讓基底類別為沒有樣式 \(或者更重要的是，在該樣式內沒有樣板，因此完全沒有預設視覺外觀\) 的衍生項目定義主題樣式。  因此，您可以從 <xref:System.Windows.Controls.Button> 衍生 `MyButton`，而仍然取得 <xref:System.Windows.Controls.Button> 預設樣板。  如果您是 `MyButton` 的控制項作者，而想要不同的行為，可以覆寫 `MyButton` 上之 <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> 的相依性屬性中繼資料，以傳回不同的索引鍵，然後再定義相關的主題樣式，包括您必須與 `MyButton` 控制項一起封裝的 `MyButton` 樣板。  如需主題、樣式和控制項撰寫的詳細資訊，請參閱[控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)。  
  
<a name="resources"></a>   
## 動態資源參考和繫結  
 動態資源參考和繫結作業會尊重其設定位置的優先順序。  例如，套用到區域值的動態資源會依優先順序項目 3 作用，主題樣式內屬性 setter 的繫結就會依優先順序項目 9 套用，以此類推。  由於動態資源參考和繫結都必須能夠從應用程式的執行階段狀態取得值，因此，決定任何指定屬性的屬性值優先順序的實際程序也會延伸至執行階段。  
  
 嚴格上來說，動態資源參考不是屬性系統的一部分，但它們有自己的查閱順序，會與上面所列的順序互動。  該優先順序在[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)中有詳細說明。  該優先順序的基本總結就是：項目優先於頁面根項目、應用程式、主題和系統。  
  
 動態資源和繫結具有其設定位置的優先順序，但值會延後。  這樣一來，如果您將動態資源或繫結設定為區域值，則區域值的任何變更會取代整個動態資源或繫結。  即使您呼叫 <xref:System.Windows.DependencyObject.ClearValue%2A> 方法來清除區域設定的值，也無法還原動態資源或繫結。  事實上，如果您在設有動態資源或繫結 \(而無常值區域值\) 的屬性上呼叫 <xref:System.Windows.DependencyObject.ClearValue%2A>，它們也會被 <xref:System.Windows.DependencyObject.ClearValue%2A> 呼叫清除。  
  
<a name="setcurrentvalue"></a>   
## SetCurrentValue  
 <xref:System.Windows.DependencyObject.SetCurrentValue%2A> 方法是另一種設定屬性的方式，但不會依優先順序。  相反地，<xref:System.Windows.DependencyObject.SetCurrentValue%2A> 可讓您變更屬性的值，而不需要覆寫先前值的來源。  任何時候您想要設定值但不想要讓該值享有區域值的優先順序，都可以使用 <xref:System.Windows.DependencyObject.SetCurrentValue%2A>。  例如，如果觸發程序設定了某個屬性，然後有其他值透過 <xref:System.Windows.DependencyObject.SetCurrentValue%2A> 指派給這個屬性，則屬性系統仍然會尊重觸發程序，而屬性會在觸發程序的動作發生時變更。  <xref:System.Windows.DependencyObject.SetCurrentValue%2A> 可讓您變更屬性的值，而不需要提供更高優先順序的來源給它。  同樣地，您可以使用 <xref:System.Windows.DependencyObject.SetCurrentValue%2A> 變更屬性的值，而不需要覆寫繫結。  
  
<a name="animations"></a>   
## 強制型轉、動畫和基底值  
 在這個 [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] 中，強制型轉和動畫都會在名為「基底值」的值上作用。  因此，基底值是透過在項目中往上評估，直到達到第 2 個項目來決定的值。  
  
 對動畫來說，如果動畫沒有指定特定行為的 "From" 和 "To"，或如果動畫刻意在完成後還原成基底值，那麼基底值就可能會對動畫值造成影響。  若要了解實際的情形，請執行 [From、To 和 By 動畫目標值範例](http://go.microsoft.com/fwlink/?LinkID=159988) \(英文\)。  請試著設定此範例中矩形高度的區域值，讓初始區域值與動畫中的任何 "From" 不同。  您會發現，動畫會立即使用 "From" 值啟動，而且一旦啟動就取代了基底值。  動畫可以藉由指定停止 <xref:System.Windows.Media.Animation.FillBehavior>，等到一旦完成，就回到動畫之前找到的值。  在此之後，就會使用正常優先順序來判斷基底值。  
  
 您可將多個動畫套用到單一屬性，而且可能已從值優先順序的不同點定義每個動畫。  不過，這些動畫可能會將值結合起來，而不是只從較高的優先順序套用動畫。  這取決於動畫的定義方式，以及要顯示為動畫之值的型別而定。  如需將屬性顯示為動畫的詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
 強制型轉的套用層級最高。  即使是已在執行中的應用程式也受值強制型轉的限制。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的某些現有相依性屬性有內建強制型轉。  對於自訂相依性屬性，您可以在建立屬性時撰寫 <xref:System.Windows.CoerceValueCallback>，並將回呼當做中繼資料的一部分傳遞，以定義自訂相依性屬性的強制型轉行為。  您也可以覆寫現有屬性的強制型轉行為，方式是在衍生類別中覆寫該屬性上的中繼資料。  強制型轉與基底值互動的方式是，強制型轉上的條件約束會以當時存在的條件約束套用，但基底值仍保留。  因此，如果強制型轉中的條件約束稍後放寬，強制型轉就會傳回最接近該基底值的值，而一旦所有條件約束都放寬，強制型轉對屬性的影響就會停止。  如需強制型轉行為的詳細資訊，請參閱[相依性屬性回呼和驗證](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)。  
  
<a name="triggers"></a>   
## 觸發程序行為  
 控制項通常會將觸發程序行為定義為其在主題中的預設樣式的一部分。  在控制項上設定區域屬性，可能會使觸發程序無法從視覺或行為上回應使用者所引發的事件。  屬性觸發程序的最常見用法是提供給控制項或狀態屬性 \(如 <xref:System.Windows.Controls.Primitives.Selector.IsSelected%2A>\) 使用。  例如，根據預設，當 <xref:System.Windows.Controls.Button> 停用 \(<xref:System.Windows.UIElement.IsEnabled%2A> 的觸發程序為 `false`\) 時，主題樣式中的 <xref:System.Windows.Controls.Control.Foreground%2A> 值就會使控制項「變成灰色」。  但如果已設定區域 <xref:System.Windows.Controls.Control.Foreground%2A> 值，那麼區域屬性集在順序上就會優先於一般灰色色彩，即使在此屬性觸發的情形也一樣。  當您為具有主題層級觸發程序行為的屬性設定值時請特別小心，確定不會不當干擾到該控制項原本的使用者操作。  
  
<a name="clearvalue"></a>   
## ClearValue 和值優先順序  
 <xref:System.Windows.DependencyObject.ClearValue%2A> 方法可快速從項目上設定的[相依性屬性](GTMT)清除任何區域套用的值。  不過，呼叫 <xref:System.Windows.DependencyObject.ClearValue%2A> 並不能保證在屬性註冊時於中繼資料建立的預設值是新的有效值。  值優先順序中的所有其他參與者仍在作用中。  只有區域設定的值會從優先順序移除。  例如，如果您在屬性上呼叫 <xref:System.Windows.DependencyObject.ClearValue%2A>，而該屬性也由主題樣式設定，那麼就會套用主題值成為新值，而非中繼資料的預設值。  如果您要將所有屬性值參與者都從優先順序移除，並將值設為註冊的中繼資料預設值，可以藉由查詢相依性屬性中繼資料來取得正確的預設值，然後再使用 <xref:System.Windows.DependencyObject.SetValue%2A> 的呼叫，用預設值設定屬性的區域值。  
  
## 請參閱  
 <xref:System.Windows.DependencyObject>   
 <xref:System.Windows.DependencyProperty>   
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [相依性屬性回呼和驗證](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)