---
title: "控制項撰寫概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], authoring overview
- authoring overview for controls [WPF]
ms.assetid: 3d864748-cff0-4e63-9b23-d8e5a635b28f
caps.latest.revision: "32"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8a3722fc9cb5b4e992ddf695696fa1eb40c6ad4e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="control-authoring-overview"></a>控制項撰寫概觀
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 控制項模型由於具有擴充性，因此大幅減少了建立新控制項的需求。 不過，在某些情況下，您可能還是需要建立自訂控制項。 本主題將討論可讓您建立自訂控制項的需求降到最低的一些功能，以及 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的不同控制項撰寫模型。 本主題也將示範如何建立新的控制項。  
  
 
  
<a name="when_to_write_a_new_control"></a>   
## <a name="alternatives-to-writing-a-new-control"></a>撰寫新控制項的替代方案  
 在過去，若要從現有控制項自訂控制項，只能變更控制項的標準屬性，例如背景色彩、框線寬度和字型大小。 除了這些預先定義的參數外，若還想擴充控制項的外觀或行為，就需要建立新的控制項，建立的方式通常是繼承現有控制項並覆寫負責繪製控制項。  雖然您現在還是可以使用前述方式，但 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可以讓您藉由使用其豐富的內容模型、樣式、範本和觸發程序來自訂現有的控制項。 下列清單提供的範例說明如何在不建立新控制項的情況下，使用這些功能來建立自訂且一致的控制項。  
  
-   **豐富內容。** 許多標準的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項都支援豐富內容。 例如，內容屬性的<xref:System.Windows.Controls.Button>的型別<xref:System.Object>，所以理論上可以顯示任何項目<xref:System.Windows.Controls.Button>。  若要顯示的影像和文字的按鈕，您可以新增映像和<xref:System.Windows.Controls.TextBlock>至<xref:System.Windows.Controls.StackPanel>並指派<xref:System.Windows.Controls.StackPanel>至<xref:System.Windows.Controls.ContentControl.Content%2A>屬性。 因為控制項可以顯示 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 視覺化項目和任意資料，就比較不需要建立新控制項或修改現有控制項來支援複雜的視覺效果。 如需有關內容模型的<xref:System.Windows.Controls.Button>和其他內容模型中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，請參閱[WPF 內容模型](../../../../docs/framework/wpf/controls/wpf-content-model.md)。  
  
-   **樣式。** A<xref:System.Windows.Style>是代表控制項的屬性值的集合。 藉由使用樣式，您可以針對所要的控制項外觀和行為，建立可重複使用的表示方式，而不需要撰寫新的控制項。 例如，假設您想要所有您<xref:System.Windows.Controls.TextBlock>控制項有 14 個字型大小的紅色，新細明體字型。 您可以建立樣式作為資源，並對應地設定適當的屬性。 然後每隔<xref:System.Windows.Controls.TextBlock>加入您的應用程式將會具有相同的外觀。  
  
-   **資料範本。** A<xref:System.Windows.DataTemplate>可讓您自訂資料在控制項上的顯示方式。 例如，<xref:System.Windows.DataTemplate>可用來指定如何將資料顯示在<xref:System.Windows.Controls.ListBox>。  如需此作業的範例，請參閱[資料範本化概觀](../../../../docs/framework/wpf/data/data-templating-overview.md)。  除了自訂的資料、 外觀<xref:System.Windows.DataTemplate>可以包含 UI 項目，可自訂的 Ui 中讓您很大的彈性。  例如，藉由使用<xref:System.Windows.DataTemplate>，您可以建立<xref:System.Windows.Controls.ComboBox>中的每個項目包含核取方塊。  
  
-   **控制項範本。** 中的許多控制項[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用<xref:System.Windows.Controls.ControlTemplate>來定義控制項的結構及外觀，控制項的外觀，藉以區別控制項的功能。 您可以重新定義，以大幅變更控制項的外觀及其<xref:System.Windows.Controls.ControlTemplate>。  例如，假設您希望控制項看起來像號誌燈。 這個控制項具有簡單的使用者介面和功能。  控制項是三個圓圈，每次只會亮其中一個。 後一些反映中，您可能會注意<xref:System.Windows.Controls.RadioButton>提供的功能只能有一個選取的時間，但預設外觀的<xref:System.Windows.Controls.RadioButton>看起來不像是燈號誌燈。  因為<xref:System.Windows.Controls.RadioButton>使用控制項範本定義其外觀時，很容易就能重新定義<xref:System.Windows.Controls.ControlTemplate>符合需求的控制項，並使用選項按鈕，讓您燈。  
  
    > [!NOTE]
    >  雖然<xref:System.Windows.Controls.RadioButton>可以使用<xref:System.Windows.DataTemplate>、<xref:System.Windows.DataTemplate>不足無法在此範例中。  <xref:System.Windows.DataTemplate>定義控制項的內容的外觀。 如果是<xref:System.Windows.Controls.RadioButton>，內容是任何出現在右邊的圓形，表示是否<xref:System.Windows.Controls.RadioButton>已選取。  在號誌燈的範例中，選項按鈕只需要是可以發亮的圓圈。 因為燈的外觀需求讓不同的預設外觀<xref:System.Windows.Controls.RadioButton>，就必須重新定義<xref:System.Windows.Controls.ControlTemplate>。  一般情況下<xref:System.Windows.DataTemplate>用來定義的內容 （或資料） 的控制項，以及<xref:System.Windows.Controls.ControlTemplate>用於定義控制項結構的方式。  
  
-   **觸發程序。** A<xref:System.Windows.Trigger>可讓您以動態方式變更的外觀和行為的控制項，而不建立新的控制項。 例如，假設您有多個<xref:System.Windows.Controls.ListBox>應用程式中的控制項和想要在每個項目<xref:System.Windows.Controls.ListBox>是粗體的紅色，選取此選項。 建立繼承自的類別可能就是您第一種天性<xref:System.Windows.Controls.ListBox>並覆寫<xref:System.Windows.Controls.Primitives.Selector.OnSelectionChanged%2A>方法，以變更選取的項目，但更好的方法的外觀是將觸發程序加入至樣式<xref:System.Windows.Controls.ListBoxItem>變更的外觀選取的項目。 觸發程序可讓您變更屬性值，或是依據屬性值採取動作。 <xref:System.Windows.EventTrigger>可讓您在事件發生時採取的動作。  
  
 如需樣式、範本和觸發程序的詳細資訊，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。  
  
 一般而言，若您的控制項可以對應到現有控制項的功能，但您希望控制項看起來不太一樣，則應該先考慮是否能使用本節中所討論的任何方法來變更現有控制項的外觀。  
  
<a name="models_for_control_authoring"></a>   
## <a name="models-for-control-authoring"></a>控制項撰寫模型  
 豐富的內容模型、樣式、範本和觸發程序，可以讓您將建立新控制項的需求降到最低。 然而，若有必要建立新的控制項，最好能先了解 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的不同控制項撰寫模型。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供三種建立控制項的常用模型，每種模型都提供不同的功能集和不同程度的彈性。 三個模型的基底類別<xref:System.Windows.Controls.UserControl>， <xref:System.Windows.Controls.Control>，和<xref:System.Windows.FrameworkElement>。  
  
### <a name="deriving-from-usercontrol"></a>衍生自 UserControl  
 最簡單的方式建立的控制項[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]是衍生自<xref:System.Windows.Controls.UserControl>。 當您建立控制項的繼承自<xref:System.Windows.Controls.UserControl>，新增至現有的元件<xref:System.Windows.Controls.UserControl>並參考中的事件處理常式命名元件， [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。 接著，您可以在程式碼中參考該具名項目，並定義事件處理常式。 這個開發模型與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中應用程式開發所使用的模型非常類似。  
  
 如果正確，建置<xref:System.Windows.Controls.UserControl>可以利用豐富內容、 樣式和觸發程序的優點。 不過，如果您的控制項是繼承自<xref:System.Windows.Controls.UserControl>，使用您的控制項人不能使用<xref:System.Windows.DataTemplate>或<xref:System.Windows.Controls.ControlTemplate>以自訂其外觀。  必須衍生自<xref:System.Windows.Controls.Control>類別或其衍生類別的其中一個 (以外<xref:System.Windows.Controls.UserControl>) 來建立自訂控制項，以支援範本。  
  
#### <a name="benefits-of-deriving-from-usercontrol"></a>從 UserControl 衍生的優點  
 請考慮衍生自<xref:System.Windows.Controls.UserControl>如果下列所有動作套用：  
  
-   您想要以類似建置應用程式的方式來建置控制項。  
  
-   您的控制項只包含現有的元件。  
  
-   您不需要支援複雜的自訂作業。  
  
### <a name="deriving-from-control"></a>衍生自 Control  
 衍生自<xref:System.Windows.Controls.Control>類別是使用大部分現有的模型[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項。 當您建立的控制項，繼承自<xref:System.Windows.Controls.Control>類別，您定義它的外觀使用範本。 這樣做您便可以將作業邏輯與視覺表示方式分開處理。 您也可以確保使用命令和繫結，而不是事件，並避免參考的項目中的 UI 和邏輯分離<xref:System.Windows.Controls.ControlTemplate>盡可能。  如果正確解除解合 UI 和使用控制項的邏輯，控制項的使用者可以重新定義控制項的<xref:System.Windows.Controls.ControlTemplate>以自訂其外觀。 雖然建置自訂<xref:System.Windows.Controls.Control>不只要建置<xref:System.Windows.Controls.UserControl>，自訂<xref:System.Windows.Controls.Control>提供最大的彈性。  
  
#### <a name="benefits-of-deriving-from-control"></a>從 Control 衍生的優點  
 請考慮衍生自<xref:System.Windows.Controls.Control>而不是使用<xref:System.Windows.Controls.UserControl>類別若有任何則適用下列步驟：  
  
-   您想要透過可自訂控制項的外觀<xref:System.Windows.Controls.ControlTemplate>。  
  
-   您想要控制項支援不同的佈景主題。  
  
### <a name="deriving-from-frameworkelement"></a>衍生自 FrameworkElement  
 衍生自的<xref:System.Windows.Controls.UserControl>或<xref:System.Windows.Controls.Control>依賴撰寫現有項目。 對於許多案例中，這是可以接受的解決方案，因為任何物件繼承自<xref:System.Windows.FrameworkElement>可以位於<xref:System.Windows.Controls.ControlTemplate>。 然而，有時候控制項外觀需要的不僅止於簡單項目組合的功能。 針對這些案例，以元件為基礎<xref:System.Windows.FrameworkElement>是適當的選擇。  
  
 有兩種標準方法，用於建置<xref:System.Windows.FrameworkElement>-基礎元件： 直接轉譯和自訂項目組合。 直接轉譯牽涉到覆寫<xref:System.Windows.UIElement.OnRender%2A>方法<xref:System.Windows.FrameworkElement>並提供<xref:System.Windows.Media.DrawingContext>明確定義元件的視覺效果的作業。 這是所使用的方法<xref:System.Windows.Controls.Image>和<xref:System.Windows.Controls.Border>。 自訂項目組合牽涉到使用型別的物件<xref:System.Windows.Media.Visual>來撰寫您的元件的外觀。 如需範例，請參閱[使用 DrawingVisual 物件](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)。 <xref:System.Windows.Controls.Primitives.Track>是中的控制項範例[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用自訂項目組合。 您也可以在同一個控制項中混合使用直接轉譯和自訂項目組合。  
  
#### <a name="benefits-of-deriving-from-frameworkelement"></a>從 FrameworkElement 衍生的優點  
 請考慮衍生自<xref:System.Windows.FrameworkElement>如果有則適用下列步驟：  
  
-   您想要精確控制控制項的外觀，而這超出了簡單項目組合所能提供的控制。  
  
-   您想要藉由定義自己的轉譯邏輯，來定義控制項的外觀。  
  
-   您想要撰寫 novel 超越什麼是可行的方式中的現有項目<xref:System.Windows.Controls.UserControl>和<xref:System.Windows.Controls.Control>。  
  
<a name="control_authoring_basics"></a>   
## <a name="control-authoring-basics"></a>控制項撰寫基本概念  
 如稍早所討論，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 其中一個最強大的功能，在於除了設定控制項的基本屬性之外，尚有能力變更其外觀和行為，並且不需要建立自訂控制項。 樣式、資料繫結和觸發程序功能是透過 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 事件系統來達成的。 下列各節說明您應該遵循的一些做法，而不論您是使用哪種模型來建立自訂控制項，讓自訂控制項的使用者能夠使用這些功能，就如同使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 隨附的控制項一樣。  
  
### <a name="use-dependency-properties"></a>使用相依性屬性  
 當屬性是相依性屬性時，有可能會進行下列作業：  
  
-   設定樣式中的屬性。  
  
-   將屬性繫結至資料來源。  
  
-   使用動態資源作為屬性值。  
  
-   顯示屬性的動畫。  
  
 若希望控制項屬性可以支援這些任一功能，就應該將控制項實作為相依性屬性。 下列範例會藉由執行下列動作，定義名為 `Value` 的相依性屬性：  
  
-   定義<xref:System.Windows.DependencyProperty>名為識別項`ValueProperty`為`public` `static` `readonly`欄位。  
  
-   向屬性系統中的屬性名稱，藉由呼叫<xref:System.Windows.DependencyProperty.Register%2A?displayProperty=nameWithType>，以指定下列項目：  
  
    -   屬性的名稱。  
  
    -   屬性的類型。  
  
    -   擁有屬性的類型。  
  
    -   屬性的中繼資料。 中繼資料包含屬性的預設值，<xref:System.Windows.CoerceValueCallback>和<xref:System.Windows.PropertyChangedCallback>。  
  
-   藉由實作屬性的 `get` 和 `set` 存取子，定義名為 `Value` 的 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 包裝函式屬性，這個名稱與註冊相依性屬性所使用的名稱相同。 請注意，`get`和`set`存取子時，只能呼叫<xref:System.Windows.DependencyObject.GetValue%2A>和<xref:System.Windows.DependencyObject.SetValue%2A>分別。 建議的相依性屬性的存取子不會包含額外的邏輯因為用戶端和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]可以略過的存取子，以及呼叫<xref:System.Windows.DependencyObject.GetValue%2A>和<xref:System.Windows.DependencyObject.SetValue%2A>直接。 例如，在屬性繫結到資料來源時，就不會呼叫屬性的 `set` 存取子。  而不是其他邏輯新增至 get 和 set 存取子，請使用<xref:System.Windows.ValidateValueCallback>， <xref:System.Windows.CoerceValueCallback>，和<xref:System.Windows.PropertyChangedCallback>回應或當監視變更，請檢查值的委派。  如需這些回呼的詳細資訊，請參閱[相依性屬性回呼和驗證](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)。  
  
-   定義方法<xref:System.Windows.CoerceValueCallback>名為`CoerceValue`。 `CoerceValue` 可以確保 `Value` 大於或等於 `MinValue`，且小於或等於 `MaxValue`。  
  
-   定義方法<xref:System.Windows.PropertyChangedCallback>具名`OnValueChanged`。 `OnValueChanged`建立<xref:System.Windows.RoutedPropertyChangedEventArgs%601>物件，並準備以引發`ValueChanged`路由的事件。 下一節中將討論路由事件。  
  
 [!code-csharp[UserControlNumericUpDown#DependencyProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#dependencyproperty)]
 [!code-vb[UserControlNumericUpDown#DependencyProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#dependencyproperty)]  
  
 如需詳細資訊，請參閱[自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)。  
  
### <a name="use-routed-events"></a>使用路由事件  
 就如同相依性屬性會使用其他功能擴充 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 屬性的概念，路由事件也同樣擴充了標準 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 事件的概念。 建立新的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項時，最好也能將事件實作為路由事件，因為路由事件支援下列行為：  
  
-   事件可以對多個控制項的父項進行處理。 若事件是反昇事件，項目樹狀結構中的單一父項可以訂閱事件。 然後應用程式作者可以使用一個處理常式，以回應多個控制項的事件。 例如，如果您的控制項是中的每個項目的一部分<xref:System.Windows.Controls.ListBox>(因為它包含在<xref:System.Windows.DataTemplate>)，應用程式開發人員可以定義您的控制項事件的事件處理常式上<xref:System.Windows.Controls.ListBox>。 每當任一控制項上發生事件時，就會呼叫事件處理常式。  
  
-   路由的事件可用於<xref:System.Windows.EventSetter>，可讓應用程式開發人員指定於樣式中的事件處理常式。  
  
-   路由的事件可用於<xref:System.Windows.EventTrigger>，這是用於建立屬性動畫使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 如需詳細資訊，請參閱 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
 下列範例會藉由執行下列動作，定義路由事件：  
  
-   定義<xref:System.Windows.RoutedEvent>名為識別項`ValueChangedEvent`為`public` `static` `readonly`欄位。  
  
-   藉由呼叫註冊路由的事件<xref:System.Windows.EventManager.RegisterRoutedEvent%2A?displayProperty=nameWithType>方法。 此範例會呼叫時，指定下列資訊<xref:System.Windows.EventManager.RegisterRoutedEvent%2A>:  
  
    -   事件名稱是 `ValueChanged`。  
  
    -   路由策略是<xref:System.Windows.RoutingStrategy.Bubble>，這表示來源 （引發事件的物件） 上的事件處理常式會呼叫第一次，然後將來源的父項目上的事件處理常式呼叫連續，從上最接近的事件處理常式父項目。  
  
    -   此事件處理常式的類型是<xref:System.Windows.RoutedPropertyChangedEventHandler%601>、 建構與<xref:System.Decimal>型別。  
  
    -   事件的擁有者類型是 `NumericUpDown`。  
  
-   宣告名為 `ValueChanged` 的公用事件，並包含事件存取子宣告。 範例會呼叫<xref:System.Windows.UIElement.AddHandler%2A>中`add`存取子宣告和<xref:System.Windows.UIElement.RemoveHandler%2A>中`remove`使用存取子宣告[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]事件服務。  
  
-   建立名為 `OnValueChanged` 的受保護虛擬方法，該方法會引發 `ValueChanged` 事件。  
  
 [!code-csharp[UserControlNumericUpDown#RoutedEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#routedevent)]
 [!code-vb[UserControlNumericUpDown#RoutedEvent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#routedevent)]  
  
 如需詳細資訊，請參閱[路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)和[建立自訂路由事件](../../../../docs/framework/wpf/advanced/how-to-create-a-custom-routed-event.md)。  
  
### <a name="use-binding"></a>使用繫結  
 若要降低控制項 UI 和邏輯間的耦合，請考慮使用資料繫結。 這是非常重要，如果您使用定義控制項的外觀<xref:System.Windows.Controls.ControlTemplate>。 在您使用資料繫結時，也許可以排除從程式碼參考特定部分之 UI 的需要。 最好避免參考中的項目<xref:System.Windows.Controls.ControlTemplate>因為當程式碼參考中的項目<xref:System.Windows.Controls.ControlTemplate>和<xref:System.Windows.Controls.ControlTemplate>變更時，參考的項目必須包含在新<xref:System.Windows.Controls.ControlTemplate>。  
  
 下列範例會更新<xref:System.Windows.Controls.TextBlock>的`NumericUpDown`控制項，指派名稱給它，並在程式碼中依名稱參考的文字方塊。  
  
 [!code-xaml[UserControlNumericUpDownSimple#UIRefMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml#uirefmarkup)]  
  
 [!code-csharp[UserControlNumericUpDownSimple#UIRefCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml.cs#uirefcode)]
 [!code-vb[UserControlNumericUpDownSimple#UIRefCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDownSimple/VisualBasic/NumericUpDown.xaml.vb#uirefcode)]  
  
 下列範例使用繫結達成相同目的。  
  
 [!code-xaml[UserControlNumericUpDown#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml#binding)]  
  
 如需資料繫結的詳細資訊，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
### <a name="design-for-designers"></a>設計工具的設計  
 若要獲得 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] 中的自訂 WPF 控制項支援 (例如使用 [屬性] 視窗編輯屬性)，請遵循這些方針。  如需開發 [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] 設計工具的詳細資訊，請參閱 [WPF 設計工具](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)。  
  
#### <a name="dependency-properties"></a>相依性屬性  
 請務必依照稍早「使用相依性屬性」中的討論來實作 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] `get` 和 `set` 存取子。 設計工具可以使用包裝函式來偵測相依性屬性的存在，但就跟 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和控制項用戶端一樣，設計工具在取得或設定屬性時不一定要呼叫存取子。  
  
#### <a name="attached-properties"></a>附加屬性  
 請使用下列方針，實作自訂控制項上的附加屬性：  
  
-   具有`public` `static` `readonly` <xref:System.Windows.DependencyProperty>表單的*PropertyName* `Property` ，建立使用<xref:System.Windows.DependencyProperty.RegisterAttached%2A>方法。 傳遞至屬性名稱<xref:System.Windows.DependencyProperty.RegisterAttached%2A>必須符合*PropertyName*。  
  
-   實作一組 `public` `static` CLR 方法，分別名為 `Set`<屬性名稱> 和 `Get`<屬性名稱>。 這兩種方法應該接受衍生自類別<xref:System.Windows.DependencyProperty>做為其第一個引數。 `Set`*PropertyName* 方法也接受其型別與屬性之已註冊資料型別相符的引數。 <屬性名稱>`Get` 方法應傳回相同類型的值。 若遺漏 <屬性名稱>`Set` 方法，屬性就會標示為唯讀。  
  
-   `Set`*PropertyName*和`Get` *PropertyName*必須直接路由傳送<xref:System.Windows.DependencyObject.GetValue%2A>和<xref:System.Windows.DependencyObject.SetValue%2A>分別方法上的目標相依性物件。 藉由呼叫方法包裝函式，或直接呼叫目標相依性物件，設計工具可以存取附加屬性。  
  
 如需附加屬性的詳細資訊，請參閱[附加屬性概觀](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)。  
  
### <a name="define-and-use-shared-resources"></a>定義和使用共用資源  
 您可以將控制項納入與應用程式相同的組件，或者將控制項封裝在不同的組件中，以用於多個應用程式。 在大多數情況下，不論使用的方法為何，本主題所討論的資訊都適用。  不過，有一項差異值得注意。  當您將控制項放入與應用程式相同的組件中時，可以任意將全域資源新增至 App.xaml 檔案。 但包含只有控制項的組件沒有<xref:System.Windows.Application>物件與其相關聯，因此 App.xaml 檔案就無法使用。  
  
 當應用程式尋找資源時，會以下列順序在三個層級中尋找：  
  
1.  項目層級。  
  
     系統會從參考資源的項目開始，然後搜尋邏輯父項的資源，以此類推，直到達到根項目為止。  
  
2.  應用程式層級。  
  
     定義之資源<xref:System.Windows.Application>物件。  
  
3.  佈景主題層級。  
  
     佈景主題層級字典會儲存在名為 Themes 的子資料夾。  Themes 資料夾中的檔案會與佈景主題對應。  例如，您可能有 Aero.NormalColor.xaml、Luna.NormalColor.xaml、Royale.NormalColor.xaml 等等。  您也可以有名為 generic.xaml 的檔案。  當系統在佈景主題層級尋找資源時，會先在佈景主題特定檔案中尋找資源，再到 generic.xaml 中尋找資源。  
  
 當您的控制項位於與應用程式不同的組件中時，必須將全域資源置於項目層級或佈景主題層級。 這兩種方法各有其優點。  
  
#### <a name="defining-resources-at-the-element-level"></a>在項目層級定義資源  
 您可以在項目層級定義共用資源，方式是建立自訂資源字典，然後將它與控制項的資源字典合併。  當您使用這個方法時，可以隨意命名資源檔，而且資源檔可以與控制項位於相同的資料夾中。 項目層級的資源也可以使用簡單的字串作為索引鍵。 下列範例會建立<xref:System.Windows.Media.LinearGradientBrush>名為 Dictionary1.xaml 資源檔。  
  
 [!code-xaml[SharedResources#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/Dictionary1.xaml#1)]  
  
 定義字典之後，您需要將它與控制項的資源字典合併。  您可以使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 或程式碼完成這項動作。  
  
 下列範例會使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 合併資源字典。  
  
 [!code-xaml[SharedResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml#2)]  
  
 這個方法的缺點在於<xref:System.Windows.ResourceDictionary>參考它的每次建立物件。  例如，如果您有 10 個自訂控制項程式庫中，使用 XAML 來合併每個控制項的共用的資源字典時，您建立 10 個相同<xref:System.Windows.ResourceDictionary>物件。  您可以避免這個狀況建立靜態類別，會合併在程式碼中的資源，並傳回產生<xref:System.Windows.ResourceDictionary>。  
  
 下列範例會建立一個類別，會傳回共用<xref:System.Windows.ResourceDictionary>。  
  
 [!code-csharp[SharedResources#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/SharedDictionaryManager.cs#3)]  
  
 下列範例會在呼叫 `InitializeComponent` 之前，在自訂控制項的建構函式中將共用資源與該控制項的資源合併。  因為`SharedDictionaryManager.SharedDictionary`是靜態屬性，<xref:System.Windows.ResourceDictionary>建立一次。 由於資源字典是在呼叫 `InitializeComponent` 之前合併，因此控制項可在其 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案中使用資源。  
  
 [!code-csharp[SharedResources#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml.cs#4)]  
  
#### <a name="defining-resources-at-the-theme-level"></a>在佈景主題層級定義資源  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可讓您為不同的 Windows 佈景主題建立資源。  身為控制項作者，您可以為特定佈景主題定義資源，以根據使用的佈景主題變更控制項的外觀。 例如的外觀<xref:System.Windows.Controls.Button>在傳統 Windows 佈景主題 （Windows 2000 的預設佈景主題） 不同於<xref:System.Windows.Controls.Button>Windows Luna 佈景主題 （Windows XP 的預設佈景主題） 因為<xref:System.Windows.Controls.Button>使用不同<xref:System.Windows.Controls.ControlTemplate>每個佈景主題。  
  
 某個佈景主題專屬的資源會存放在具有特定檔名的資源字典中。 這些檔案必須位於名為 `Themes` 的資料夾中，這是包含控制項之資料夾的子資料夾。 下表列出資源字典檔以及與每個檔案相關聯的佈景主題：  
  
|資源字典檔名稱|Windows 佈景主題|  
|-----------------------------------|-------------------|  
|`Classic.xaml`|Windows XP 上的傳統 Windows 9x/2000 外觀|  
|`Luna.NormalColor.xaml`|Windows XP 上的預設藍色佈景主題|  
|`Luna.Homestead.xaml`|Windows XP 上的橄欖色佈景主題|  
|`Luna.Metallic.xaml`|Windows XP 上的銀色佈景主題|  
|`Royale.NormalColor.xaml`|Windows XP Media Center Edition 上的預設佈景主題|  
|`Aero.NormalColor.xaml`|Windows Vista 上的預設佈景主題|  
  
 您不需要為每個佈景主題定義資源。 若未定義特定佈景主題的資源，則控制項會在 `Classic.xaml` 中檢查資源。 若在對應於目前佈景主題的檔案中或在 `Classic.xaml` 中都未定義資源，控制項會使用名為 `generic.xaml` 的資源字典檔中的一般資源。  `generic.xaml` 檔案位於與佈景主題特有資源字典檔相同的資料夾中。 雖然 `generic.xaml` 並未對應到特定 Windows 佈景主題，但它仍是佈景主題層級字典。  
  
 [具有與佈景主題和 UI 自動化支援的 NumericUpDown 自訂控制項範例](http://go.microsoft.com/fwlink/?LinkID=160025)包含 `NumericUpDown` 控制項的兩個資源字典：一個在 generic.xaml 中，另一個在 Luna.NormalColor.xaml 中。  您可以執行應用程式，然後在 Windows XP 的銀色佈景主題和其他佈景主題之間切換，查看兩個控制項範本之間的差異。 (若您執行 Windows Vista，則可以將 Luna.NormalColor.xaml 重新命名為 Aero.NormalColor.xaml，然後在兩個佈景主題之間切換，例如 Windows 傳統配色和 Windows Vista 的預設佈景主題。)  
  
 當您將<xref:System.Windows.Controls.ControlTemplate>在任何主題特定資源字典檔，您必須建立您的控制項和呼叫靜態建構函式<xref:System.Windows.DependencyProperty.OverrideMetadata%28System.Type%2CSystem.Windows.PropertyMetadata%29>方法<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>，如下列範例所示。  
  
 [!code-csharp[CustomControlNumericUpDownOneProject#StaticConstructor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/CSharp/NumericUpDown.cs#staticconstructor)]
 [!code-vb[CustomControlNumericUpDownOneProject#StaticConstructor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/visualbasic/numericupdown.vb#staticconstructor)]  
  
##### <a name="defining-and-referencing-keys-for-theme-resources"></a>定義和參考佈景主題資源的索引鍵  
 當您在項目層級定義資源時，可以指派字串作為它的索引鍵，然後透過字串存取資源。 當您定義的資源時的佈景主題的層級時，您必須使用<xref:System.Windows.ComponentResourceKey>做為索引鍵。  下列範例會在 generic.xaml 中定義資源。  
  
 [!code-xaml[ThemeResourcesControlLibrary#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/Themes/generic.xaml#5)]  
  
 下列範例會參考資源，藉由指定<xref:System.Windows.ComponentResourceKey>做為索引鍵。  
  
 [!code-xaml[ThemeResourcesControlLibrary#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/NumericUpDown.xaml#6)]  
  
##### <a name="specifying-the-location-of-theme-resources"></a>指定佈景主題資源的位置  
 若要尋找控制項的資源，裝載的應用程式必須知道組件是否包含控制項特定的資源。 您可以藉由新增完成，<xref:System.Windows.ThemeInfoAttribute>包含控制項之組件。 <xref:System.Windows.ThemeInfoAttribute>具有<xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A>屬性，指定的一般資源的位置和<xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A>屬性，指定佈景主題特定資源的位置。  
  
 下列範例會設定<xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A>和<xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A>屬性<xref:System.Windows.ResourceDictionaryLocation.SourceAssembly>，指定的泛型和佈景主題特定資源位於相同的組件控制項。  
  
 [!code-csharp[CustomControlNumericUpDown#ThemesSection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/Properties/AssemblyInfo.cs#themessection)]
 [!code-vb[CustomControlNumericUpDown#ThemesSection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/my project/assemblyinfo.vb#themessection)]  
  
## <a name="see-also"></a>另請參閱  
 [WPF 設計工具](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [WPF 中的 Pack URI](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [控制項自訂](../../../../docs/framework/wpf/controls/control-customization.md)
