---
title: "控制項撰寫概觀 | Microsoft Docs"
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
  - "控制項撰寫概觀"
  - "控制項, 撰寫概觀"
ms.assetid: 3d864748-cff0-4e63-9b23-d8e5a635b28f
caps.latest.revision: 32
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 29
---
# 控制項撰寫概觀
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 控制項模型由於具有擴充性，大幅減少了建立新控制項的需求。  不過，在某些情況下，您可能還是需要建立自訂控制項。  本主題將說明一些功能使建立自訂控制項的需求減至最少，以及 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的不同控制項撰寫模型。  本主題也將示範如何建立新的控制項。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="when_to_write_a_new_control"></a>   
## 撰寫新控制項的替代方案  
 在過去，如果要從現有控制項自訂控制項，只能變更控制項的標準屬性，例如背景色彩、框線寬度和字型大小。  除了這些預先定義的參數外，如果還想擴充控制項的外觀或行為，就需要建立新的控制項，建立的方式通常是藉由繼承現有控制項並覆寫負責繪製控制項的方法。  雖然您現在還是可以使用前述方式，但 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可以讓您藉由使用其豐富的內容模型、樣式、樣板和觸發程序來自訂現有控制項。  下列清單提供的範例示範如何在不建立新控制項的情況下，即可以使用這些功能來建立自訂且一致的控制項。  
  
-   **豐富內容** 許多標準 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項都支援豐富內容 \(Rich Content\) 樣式的功能。  例如，<xref:System.Windows.Controls.Button> 的內容屬性的型別是 <xref:System.Object>，所以理論上可以在 <xref:System.Windows.Controls.Button> 上顯示任何東西。  若要讓按鈕顯示影像和文字，您可以在 <xref:System.Windows.Controls.StackPanel> 上加入影像和 <xref:System.Windows.Controls.TextBlock>，並指派 <xref:System.Windows.Controls.StackPanel> 到 <xref:System.Windows.Controls.ContentControl.Content%2A> 屬性。  因為控制項可以顯示 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 視覺化項目和任意資料，就比較不需要建立新控制項或修改現有控制項來支援複雜的視覺效果。  如需 <xref:System.Windows.Controls.Button> 內容模型及 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中其他內容模型的詳細資訊，請參閱 [WPF 內容模型](../../../../docs/framework/wpf/controls/wpf-content-model.md)。  
  
-   **樣式** <xref:System.Windows.Style> 是代表控制項屬性的值集合。  藉由使用樣式，您可以針對所要的控制項外觀和行為，建立可重複使用的表示，而不需要撰寫新的控制項。  例如，假設您想要所有 <xref:System.Windows.Controls.TextBlock> 控制項都具有紅色新細明體且大小為 14 的字型。  您可以建立樣式做為資源，並對應地設定適當的屬性。  那麼，加入至您應用程式的每個 <xref:System.Windows.Controls.TextBlock>，都會具有相同的外觀。  
  
-   **資料樣板** <xref:System.Windows.DataTemplate> 可以讓您自訂控制項上資料的顯示方式。  例如，<xref:System.Windows.DataTemplate> 可以用來指定資料在 <xref:System.Windows.Controls.ListBox> 中的顯示方式。  如需範例，請參閱[資料範本化概觀](../../../../docs/framework/wpf/data/data-templating-overview.md)。  除了自訂資料外觀之外，<xref:System.Windows.DataTemplate> 可以包含 UI 項目 \(Element\)，帶給您在自訂 UI 方面許多的彈性。  例如，藉由使用 <xref:System.Windows.DataTemplate>，您可以建立其中每個項目 \(Item\) 都包含核取方塊的 <xref:System.Windows.Controls.ComboBox>。  
  
-   **控制項樣板** 許多 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項使用 <xref:System.Windows.Controls.ControlTemplate> 定義控制項的結構和外觀，這樣會將控制項外觀和控制項功能加以分隔開來。藉由重新定義控制項的 <xref:System.Windows.Controls.ControlTemplate>，即可以大幅變更控制項的外觀。  例如，假設您希望控制項看起來像號誌燈。  這個控制項具有簡單的使用者介面和功能。  控制項是三個圓圈，每次只會亮其中一個。  在一番對照之後，您會發現 <xref:System.Windows.Controls.RadioButton> 提供的功能會讓每次只能選取一個選項按鈕，但 <xref:System.Windows.Controls.RadioButton> 的預設外觀看起來就像號誌燈的亮燈。  因為 <xref:System.Windows.Controls.RadioButton> 使用控制項樣板定義其外觀，很容易可以重新定義 <xref:System.Windows.Controls.ControlTemplate> 以滿足控制項需求，並使用選項按鈕製作號誌燈。  
  
    > [!NOTE]
    >  雖然 <xref:System.Windows.Controls.RadioButton> 可以使用 <xref:System.Windows.DataTemplate>，但一個 <xref:System.Windows.DataTemplate> 對本範例來說並不足夠。  <xref:System.Windows.DataTemplate> 會定義控制項內容的外觀。  在 <xref:System.Windows.Controls.RadioButton> 的案例中，內容是出現在代表是否有選取的 <xref:System.Windows.Controls.RadioButton> 的圓圈右邊的任何項目。  在號誌燈的範例中，選項按鈕只需要是可以發亮的圓圈。 因為號誌燈的外觀需求跟 <xref:System.Windows.Controls.RadioButton> 的預設外觀是如此的不同，所以有必要重新定義 <xref:System.Windows.Controls.ControlTemplate>。  一般而言，<xref:System.Windows.DataTemplate> 是用於定義控制項的內容 \(或資料\)，而 <xref:System.Windows.Controls.ControlTemplate> 則用於定義控制項的結構排列方式。  
  
-   **觸發程序** <xref:System.Windows.Trigger> 可以讓您動態變更控制項的外觀和行為，而不需要建立新的控制項。  例如，假設應用程式中具有多個 <xref:System.Windows.Controls.ListBox> 控制項，並希望每個 <xref:System.Windows.Controls.ListBox> 中的項目在選取時呈現紅色粗體。  您的第一個想法可能是建立繼承自 <xref:System.Windows.Controls.ListBox> 的類別，並覆寫 <xref:System.Windows.Controls.Primitives.Selector.OnSelectionChanged%2A> 方法以變更選取項目的外觀，但有個較好的方式是為 <xref:System.Windows.Controls.ListBoxItem> 樣式加入觸發程序，以變更選取項目的外觀。  觸發程序可以讓您變更屬性值，或是依據屬性值採取動作。  <xref:System.Windows.EventTrigger> 則可以讓您在發生事件時採取動作。  
  
 如需樣式、樣板和觸發程序的詳細資訊，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。  
  
 一般而言，如果您的控制項可以對應到現有控制項的功能，但您希望控制項看起來不太一樣，則應該先考慮是否能使用本節所討論的任何方法來變更現有控制項的外觀。  
  
<a name="models_for_control_authoring"></a>   
## 控制項撰寫模型  
 豐富的內容模型、樣式、樣板和觸發程序，可以讓您建立新控制項的需求降到最低。  然而，如果有必要建立新的控制項，最好能先了解 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的不同控制項撰寫模型。[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供三種建立控制項的常用模型，每種模型都提供不同的功能集和不同程度的彈性。  三種模型的基底類別為 <xref:System.Windows.Controls.UserControl>、<xref:System.Windows.Controls.Control> 和 <xref:System.Windows.FrameworkElement>。  
  
### 衍生自 UserControl  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中建立控制項最簡單的方式，是衍生自 <xref:System.Windows.Controls.UserControl>。  在建置繼承自 <xref:System.Windows.Controls.UserControl> 的控制項時，您要加入現有的元件至 <xref:System.Windows.Controls.UserControl>、為元件命名，並參考[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中的事件處理常式。  您接著可以在程式碼中參考該具名項目並定義事件處理常式。  這個開發模型跟 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中應用程式開發所使用的模型非常類似。  
  
 如果正確建置，<xref:System.Windows.Controls.UserControl> 就可以運用豐富內容、樣式和觸發程序的優點。  然而，如果控制項繼承自 <xref:System.Windows.Controls.UserControl>，則使用您的控制項的人將無法使用 <xref:System.Windows.DataTemplate> 或 <xref:System.Windows.Controls.ControlTemplate> 來自訂其外觀。  所以就有必要衍生自 <xref:System.Windows.Controls.Control> 類別或其中一個衍生類別 \(<xref:System.Windows.Controls.UserControl> 以外的\)，來建立可以支援樣板的自訂控制項。  
  
#### 從 UserControl 衍生的好處  
 如果適用下列所有條件的話，請考慮衍生自 <xref:System.Windows.Controls.UserControl>：  
  
-   您想要以類似建置應用程式的方式來建置控制項。  
  
-   您的控制項只包含現有的元件。  
  
-   您不需要支援複雜的自訂作業。  
  
### 衍生自 Control  
 大部分現有的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項是使用衍生自 <xref:System.Windows.Controls.Control> 類別的模型。  在建立繼承自 <xref:System.Windows.Controls.Control> 類別的控制項時，您要藉由使用樣板定義其外觀。  這樣做您便可以將作業邏輯與視覺化表示分開處理。  另一種確保 UI 和邏輯會分開處理的方式是，使用命令和繫結而不是事件，並且盡量避免參考 <xref:System.Windows.Controls.ControlTemplate> 中的項目。如果能夠將 UI 和邏輯適當分開處理，則控制項的使用者只要重新定義控制項的 <xref:System.Windows.Controls.ControlTemplate>，就能自訂控制項的外觀。雖然建置自訂的 <xref:System.Windows.Controls.Control> 不像建置 <xref:System.Windows.Controls.UserControl> 那樣簡單，但自訂的 <xref:System.Windows.Controls.Control> 可以提供最大的彈性。  
  
#### 從 Control 衍生的好處  
 如果適用下列任一條件的話，請考慮衍生自 <xref:System.Windows.Controls.Control>，而不要使用 <xref:System.Windows.Controls.UserControl> 類別：  
  
-   您想要透過 <xref:System.Windows.Controls.ControlTemplate> 自訂控制項的外觀。  
  
-   您想要控制項支援不同的主題。  
  
### 衍生自 FrameworkElement  
 衍生自 <xref:System.Windows.Controls.UserControl> 或 <xref:System.Windows.Controls.Control> 的控制項都需要撰寫現有的項目。  對於許多案例而言，這是可接受的方案，因為繼承自 <xref:System.Windows.FrameworkElement> 的任何物件都可以位於 <xref:System.Windows.Controls.ControlTemplate> 中。  然而，有時候控制項外觀需要的不僅止於簡單項目複合的功能。  在這些情況下，就適合使用 <xref:System.Windows.FrameworkElement> 做為元件的基礎。  
  
 建置以 <xref:System.Windows.FrameworkElement> 為基礎的元件有兩種標準方法：直接轉譯和自訂項目組合。  直接轉譯是覆寫<xref:System.Windows.FrameworkElement> 的 <xref:System.Windows.UIElement.OnRender%2A> 方法，並提供明確定義元件視覺效果的 <xref:System.Windows.Media.DrawingContext> 作業。  這是 <xref:System.Windows.Controls.Image> 和 <xref:System.Windows.Controls.Border> 所使用的方法。  自訂項目複合則是使用型別 <xref:System.Windows.Media.Visual> 的物件，撰寫元件的外觀。  如需範例，請參閱 [使用 DrawingVisual 物件](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)。  <xref:System.Windows.Controls.Primitives.Track> 是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中控制項使用自訂項目複合的範例。  您也可以在同一個控制項中混合直接轉譯和自訂項目複合。  
  
#### 從 FrameworkElement 衍生的好處  
 如果適用下列任一條件的話，請考慮衍生自 <xref:System.Windows.FrameworkElement>：  
  
-   您想要準確控制控制項的外觀，而這超出了簡單項目複合所能提供的控制。  
  
-   您想要藉由定義自己的轉譯邏輯，以定義控制項的外觀。  
  
-   您想要以全新方式撰寫現有的項目，而這超出 <xref:System.Windows.Controls.UserControl> 和 <xref:System.Windows.Controls.Control> 能力所及。  
  
<a name="control_authoring_basics"></a>   
## 控制項撰寫基本概念  
 如稍早所討論，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 其中一個最強大的功能，在於除了設定控制項的基本屬性之外，尚有能力變更其外觀和行為，並且不需要建立自訂控制項。樣式、資料繫結和觸發程序功能是藉由 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 事件系統而達成的。下列各節說明您應該遵循的一些做法，而不論您是使用哪種模型來建立自訂控制項，讓自訂控制項的使用者在使用這些功能，就如同在使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 隨附的控制項一樣。  
  
### 使用相依性屬性  
 當屬性是相依性屬性時，有可能會進行下列作業：  
  
-   設定樣式中的屬性。  
  
-   繫結屬性至資料來源。  
  
-   使用動態資源做為屬性值。  
  
-   將屬性顯示為動畫。  
  
 如果希望控制項屬性可以支援這些任一功能，就應該將控制項實作為相依性屬性。  下列範例會藉由執行下列動作，定義名為 `Value` 的相依性屬性：  
  
-   將名為 `ValueProperty` 的 <xref:System.Windows.DependencyProperty> 識別項定義為 `public` `static` `readonly` 欄位。  
  
-   藉由呼叫 <xref:System.Windows.DependencyProperty.Register%2A?displayProperty=fullName> 向屬性系統註冊屬性名稱，以指定下列項目：  
  
    -   屬性的名稱。  
  
    -   屬性的型別。  
  
    -   擁有屬性的型別。  
  
    -   屬性的中繼資料。  中繼資料包含屬性的預設值 <xref:System.Windows.CoerceValueCallback> 和 <xref:System.Windows.PropertyChangedCallback>。  
  
-   藉由實作屬性的 `get` 和 `set` 存取子，定義名為 `Value` 的 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 包裝函式屬性，這個名稱與註冊相依性屬性所使用的名稱相同。  請注意，`get` 與 `set` 存取子只能夠分別呼叫 <xref:System.Windows.DependencyObject.GetValue%2A> 以及 <xref:System.Windows.DependencyObject.SetValue%2A>。  建議您，相依性屬性的存取子不要包含其他的邏輯，因為用戶端和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可以略過存取子並直接呼叫 <xref:System.Windows.DependencyObject.GetValue%2A> 和 <xref:System.Windows.DependencyObject.SetValue%2A>。  例如，在屬性繫結到資料來源時，就不會呼叫屬性的 `set` 存取子。  取代將其他邏輯加入到 get 和 set 存取子的方式，是使用 <xref:System.Windows.ValidateValueCallback>、<xref:System.Windows.CoerceValueCallback> 和 <xref:System.Windows.PropertyChangedCallback> 委派在變更時回應或檢查值。  如需這些回呼的詳細資訊，請參閱[相依性屬性回呼和驗證](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)。  
  
-   針對名為 `CoerceValue` 的 <xref:System.Windows.CoerceValueCallback> 定義方法。  `CoerceValue` 可以確保 `Value` 大於或等於 `MinValue`，並小於或等於 `MaxValue`。  
  
-   針對名為 `OnValueChanged` 的 <xref:System.Windows.PropertyChangedCallback> 定義方法。  `OnValueChanged` 會建立 <xref:System.Windows.RoutedPropertyChangedEventArgs%601> 物件並準備引發 `ValueChanged` 路由事件。  下一節中將討論路由事件。  
  
 [!code-csharp[UserControlNumericUpDown#DependencyProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#dependencyproperty)]
 [!code-vb[UserControlNumericUpDown#DependencyProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#dependencyproperty)]  
  
 如需詳細資訊，請參閱[自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)。  
  
### 使用路由事件  
 就如同[相依性屬性](GTMT)會使用其他功能擴充 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 屬性的概念，[路由事件](GTMT)也同樣擴充了標準 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 事件的概念。  建立新的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項時，最好也能將事件實作為路由事件，因為路由事件支援下列行為：  
  
-   事件可以對多個控制項的父項目進行處理。  如果事件是反昇 \(Bubbling\) 事件，項目樹狀結構中的單一父項目可以訂閱事件。  然後應用程式作者可以使用一個處理常式回應多個控制項的事件。  例如，如果控制項是 <xref:System.Windows.Controls.ListBox> 中每個項目的一部分 \(因為包含在 <xref:System.Windows.DataTemplate> 中\)，應用程式開發人員就可以對 <xref:System.Windows.Controls.ListBox> 定義控制項事件的事件處理常式。  每當任一控制項上發生事件時，就會呼叫事件處理常式。  
  
-   路由事件可以在 <xref:System.Windows.EventSetter> 中使用，這樣可以讓應用程式開發人員指定樣式內的事件處理常式。  
  
-   路由事件可以在  <xref:System.Windows.EventTrigger> 中使用，這對於使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 顯示屬性的動畫非常有用。  如需詳細資訊，請參閱 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
 下列範例會藉由執行下列動作，定義路由事件：  
  
-   將名為 `ValueChangedEvent` 的 <xref:System.Windows.RoutedEvent> 識別項定義為 `public` `static` `readonly` 欄位。  
  
-   藉由呼叫 <xref:System.Windows.EventManager.RegisterRoutedEvent%2A?displayProperty=fullName> 方法，註冊路由事件。  範例會在呼叫 <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> 時指定下列資訊：  
  
    -   事件名稱是 `ValueChanged`。  
  
    -   路由策略是 <xref:System.Windows.RoutingStrategy>，這代表會先呼叫來源 \(引發事件的物件\) 上的事件處理常式，然後再接續呼叫來源父項目上的事件處理常式，從最接近的父項目上的事件處理常式開始。  
  
    -   事件處理常式的型別是 <xref:System.Windows.RoutedPropertyChangedEventHandler%601>，並以 <xref:System.Decimal> 型別建構。  
  
    -   事件的擁有者型別是 `NumericUpDown`。  
  
-   宣告名為 `ValueChanged` 的公用事件，並包含事件存取子宣告。  範例會在 `add` 存取子宣告中呼叫 <xref:System.Windows.UIElement.AddHandler%2A>，並在 `remove` 存取子宣告中呼叫 <xref:System.Windows.UIElement.RemoveHandler%2A>，以使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 事件服務。  
  
-   建立名為 `OnValueChanged` 的受保護虛擬方法，該方法會引發 `ValueChanged` 事件。  
  
 [!code-csharp[UserControlNumericUpDown#RoutedEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#routedevent)]
 [!code-vb[UserControlNumericUpDown#RoutedEvent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#routedevent)]  
  
 如需詳細資訊，請參閱[路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)和 [建立自訂路由事件](../../../../docs/framework/wpf/advanced/how-to-create-a-custom-routed-event.md)。  
  
### 使用繫結  
 若要降低控制項 UI 和邏輯間的耦合，請考慮使用資料繫結。  這在藉由使用 <xref:System.Windows.Controls.ControlTemplate> 定義控制項外觀時特別重要。  在您使用資料繫結時，也許可以排除從程式碼參考特定部分之 UI 的需要。  最好能避免參考 <xref:System.Windows.Controls.ControlTemplate> 中的項目，因為當程式碼參考 <xref:System.Windows.Controls.ControlTemplate> 中的項目，而 <xref:System.Windows.Controls.ControlTemplate> 變更時，被參考的項目就必須包含在新的 <xref:System.Windows.Controls.ControlTemplate> 中。  
  
 下列範例會更新 `NumericUpDown` 控制項的 <xref:System.Windows.Controls.TextBlock>，在程式碼中為其指派名稱並依據名稱參考文字方塊。  
  
 [!code-xml[UserControlNumericUpDownSimple#UIRefMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml#uirefmarkup)]  
  
 [!code-csharp[UserControlNumericUpDownSimple#UIRefCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml.cs#uirefcode)]
 [!code-vb[UserControlNumericUpDownSimple#UIRefCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDownSimple/VisualBasic/NumericUpDown.xaml.vb#uirefcode)]  
  
 下列範例使用繫結達成相同目的。  
  
 [!code-xml[UserControlNumericUpDown#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml#binding)]  
  
 如需資料繫結的詳細資訊，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
### 設計工具的設計  
 若要獲得 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] 中的自訂 WPF 控制項支援 \(例如使用 \[屬性\] 視窗編輯屬性\)，請遵循這些方針。  如需開發 [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]的詳細資訊，請參閱 [WPF Designer](http://msdn.microsoft.com/zh-tw/c6c65214-8411-4e16-b254-163ed4099c26)。  
  
#### 相依性屬性  
 請務必依照稍早「使用相依性屬性」中的討論來實作 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] `get` 和 `set` 存取子。 設計工具可以使用包裝函式來偵測相依性屬性的存在，但就跟 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和控制項用戶端一樣，設計工具在取得和設定屬性時不一定要呼叫存取子。  
  
#### 附加屬性  
 請使用下列方針，實作自訂控制項上的附加屬性：  
  
-   將 `public` `static` `readonly` <xref:System.Windows.DependencyProperty> 設為格式 *PropertyName*`Property`，這是使用 <xref:System.Windows.DependencyProperty.RegisterAttached%2A> 方法建立的。  傳遞至 <xref:System.Windows.DependencyProperty.RegisterAttached%2A> 的屬性名稱必須與 *PropertyName* 相符。  
  
-   實作一組 `public` `static` CLR 方法，分別名為 `Set`*PropertyName* 和 `Get`*PropertyName*。  這兩個方法都應接受衍生自 <xref:System.Windows.DependencyProperty> 的類別做為第一個引數。  `Set`*PropertyName* 方法也接受其型別與屬性之已註冊資料型別相符的引數。  `Get`*PropertyName* 方法應傳回相同型別的值。  如果遺漏 `Set`*PropertyName* 方法，屬性就會標示為唯讀。  
  
-   `Set` *PropertyName* 和 `Get`*PropertyName* 必須分別直接路由至目標相依性物件上的 <xref:System.Windows.DependencyObject.GetValue%2A> 和 <xref:System.Windows.DependencyObject.SetValue%2A> 方法。  藉由呼叫方法包裝函式，或直接呼叫目標相依性物件，設計工具可以存取附加屬性。  
  
 如需附加屬性的詳細資訊，請參閱[附加屬性概觀](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)。  
  
### 定義和使用共用資源  
 您可以將控制項加入到與應用程式相同的組件，或者將控制項封裝在不同的組件中，以用於多個應用程式。  在大多數情況下，不論使用的方法為何，本主題所討論的資訊都適用。  不過，有一項差異值得注意。  當您將控制項放入與應用程式相同的組件中時，可以任意將全域資源加入到 App.xaml 檔案。  但只包含控制項的組件沒有與其相關聯的 <xref:System.Windows.Application> 物件，因此不會有 App.xaml 檔案。  
  
 當應用程式尋找資源時，會以下列順序在三個層級中尋找：  
  
1.  項目層級。  
  
     系統會從參考資源的項目開始，然後搜尋邏輯父項目的資源，以此類推，直到達到根項目為止。  
  
2.  應用程式層級。  
  
     由 <xref:System.Windows.Application> 物件定義的資源。  
  
3.  佈景主題層級。  
  
     佈景主題層級字典會儲存在名為 Themes 的子資料夾。  Themes 資料夾中的檔案會與佈景主題對應。  例如，您可能有 Aero.NormalColor.xaml、Luna.NormalColor.xaml、Royale.NormalColor.xaml 等。  您也可以有名為 generic.xaml 的檔案。  當系統在佈景主題層級尋找資源時，會先在佈景主題特定檔案中尋找資源，再到 generic.xaml 中尋找資源。  
  
 當您的控制項位於與應用程式不同的組件中時，必須將全域資源置於項目層級或佈景主題層級。  這兩種方法各有其優點。  
  
#### 在項目層級定義資源  
 您可以在項目層級定義共用資源，方式是建立自訂資源字典，然後將它與控制項的資源字典合併。  當您使用這個方法時，可以隨意命名資源檔，而且資源檔可以與控制項位於相同的資料夾中。  項目層級的資源也可以使用簡單的字串做為索引鍵。  下列範例會建立名為 Dictionary1.xaml 的 <xref:System.Windows.Media.LinearGradientBrush> 資源檔。  
  
 [!code-xml[SharedResources#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/Dictionary1.xaml#1)]  
  
 定義字典之後，您需要將它與控制項的資源字典合併。  您可以使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 或程式碼完成這項動作。  
  
 下列範例會使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 合併資源字典。  
  
 [!code-xml[SharedResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml#2)]  
  
 這種方法的缺點是每次參考 <xref:System.Windows.ResourceDictionary> 物件時，就會建立它。  例如，如果您的程式庫中有 10 個自訂控制項，然後使用 XAML 合併每個控制項的共用資源字典，就會建立 10 個相同的 <xref:System.Windows.ResourceDictionary> 物件。  要避免這樣的問題，可以建立靜態類別，讓它在程式碼中合併資源，再傳回產生的 <xref:System.Windows.ResourceDictionary>。  
  
 下列範例會建立傳回共用 <xref:System.Windows.ResourceDictionary> 的類別。  
  
 [!code-csharp[SharedResources#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/SharedDictionaryManager.cs#3)]  
  
 下列範例會在呼叫 `InitilizeComponent` 之前，在自訂控制項的建構函式中將共用資源與該控制項的資源合併。  由於 `SharedDictionaryManager.SharedDictionary` 是靜態屬性，因此 <xref:System.Windows.ResourceDictionary> 只會建立一次。  由於資源字典是在呼叫 `InitializeComponent` 之前合併，因此控制項可在其 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案中使用資源。  
  
 [!code-csharp[SharedResources#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml.cs#4)]  
  
#### 在佈景主題層級定義資源  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可讓您為不同的 Windows 佈景主題建立資源。  身為控制項作者，您可以為特定佈景主題定義資源，以根據使用的佈景主題變更控制項的外觀。  例如，<xref:System.Windows.Controls.Button> 在 Windows 傳統配色佈景主題 \(Windows 2000 的預設佈景主題\) 中的外觀，就與 Windows Luna 佈景主題 \(Windows XP 的預設佈景主題\) 中的 <xref:System.Windows.Controls.Button> 不同，因為 <xref:System.Windows.Controls.Button> 針對每個佈景主題會使用不同的 <xref:System.Windows.Controls.ControlTemplate>。  
  
 某個佈景主題專屬的資源會存放在有特定檔名的資源字典中。  這些檔案必須位於名為 `Themes` 的資料夾中，這是包含控制項之資料夾的子資料夾。  下表列出資源字典檔以及與每個檔案相關聯的佈景主題：  
  
|資源字典檔名稱|Windows 佈景主題|  
|-------------|------------------|  
|`Classic.xaml`|Windows XP 上的傳統 Windows 9x\/2000 外觀|  
|`Luna.NormalColor.xaml`|Windows XP 上的預設藍色佈景主題|  
|`Luna.Homestead.xaml`|Windows XP 上的橄欖色佈景主題|  
|`Luna.Metallic.xaml`|Windows XP 上的銀色佈景主題|  
|`Royale.NormalColor.xaml`|Windows XP Media Center Edition 上的預設佈景主題|  
|`Aero.NormalColor.xaml`|Windows Vista 上的預設佈景主題|  
  
 您不需要為每個佈景主題定義資源。  如果未定義特定佈景主題的資源，則控制項會在 `Classic.xaml` 中檢查資源。  如果在對應於目前佈景主題的檔案中或在 `Classic.xaml` 中都未定義資源，控制項會使用名為 `generic.xaml` 的資源字典檔中的泛用資源。  `generic.xaml` 檔案位於與佈景主題特有資源字典檔相同的資料夾中。  雖然 `generic.xaml` 並未對應到特定 Windows 佈景主題，但它仍是佈景主題層級字典。  
  
 [具有與佈景主題和 UI 自動化支援的 NumericUpDown 自訂控制項範例](http://go.microsoft.com/fwlink/?LinkID=160025) \(英文\) 包含 `NumericUpDown` 控制項的兩個資源字典：一個在 generic.xaml 中，另一個在 Luna.NormalColor.xaml 中。  您可以執行應用程式，然後在 Windows XP 的銀色佈景主題和其他佈景主題之間切換，看看兩個控制項樣板之間的差異   \(如果您執行 Windows Vista，可以將 Luna.NormalColor.xaml 重新命名為 Aero.NormalColor.xaml，然後在兩個佈景主題之間切換，例如 Windows 傳統配色和 Windows Vista 的預設佈景主題\)。  
  
 當您將 <xref:System.Windows.Controls.ControlTemplate> 放入任何佈景主題特定資源字典檔，就必須為控制項建立靜態建構函式，然後在 <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> 上呼叫 <xref:System.Windows.DependencyProperty.OverrideMetadata%28System.Type%2CSystem.Windows.PropertyMetadata%29> 方法，如下列範例所示。  
  
 [!code-csharp[CustomControlNumericUpDownOneProject#StaticConstructor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/CSharp/NumericUpDown.cs#staticconstructor)]
 [!code-vb[CustomControlNumericUpDownOneProject#StaticConstructor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/visualbasic/numericupdown.vb#staticconstructor)]  
  
##### 定義和參考佈景主題資源的索引鍵  
 當您在項目層級定義資源時，可以指派字串做為它的索引鍵，然後透過字串存取資源。  當您在佈景主題層級定義資源時，則必須使用 <xref:System.Windows.ComponentResourceKey> 做為索引鍵。  下列範例會在 generic.xaml 中定義資源。  
  
  
  
 下列範例會藉由指定 <xref:System.Windows.ComponentResourceKey> 做為索引鍵來參考資源。  
  
  
  
##### 指定佈景主題資源的位置  
 若要尋找控制項的資源，裝載的應用程式必須知道組件是否包含控制項特定的資源。  為達此目的，您可以將 <xref:System.Windows.ThemeInfoAttribute> 加入到包含控制項的組件。  <xref:System.Windows.ThemeInfoAttribute> 有 <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> 屬性 \(指定泛用資源的位置\) 和 <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> 屬性 \(指定佈景主題特定資源的位置\)。  
  
 下列範例將 <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> 和 <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> 屬性設定為 <xref:System.Windows.ResourceDictionaryLocation>，指定泛用和佈景主題特定資源與控制項位於相同的組件中。  
  
 [!code-csharp[CustomControlNumericUpDown#ThemesSection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/Properties/AssemblyInfo.cs#themessection)]
 [!code-vb[CustomControlNumericUpDown#ThemesSection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/my project/assemblyinfo.vb#themessection)]  
  
## 請參閱  
 [WPF Designer](http://msdn.microsoft.com/zh-tw/c6c65214-8411-4e16-b254-163ed4099c26)   
 [WPF 中的 Pack URI](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)   
 [控制項自訂](../../../../docs/framework/wpf/controls/control-customization.md)