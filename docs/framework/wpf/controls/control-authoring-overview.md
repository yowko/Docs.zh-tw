---
title: 控制項撰寫概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], authoring overview
- authoring overview for controls [WPF]
ms.assetid: 3d864748-cff0-4e63-9b23-d8e5a635b28f
ms.openlocfilehash: 2326520039085beb5f5294e23db67b67f9d7d7da
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243267"
---
# <a name="control-authoring-overview"></a>控制項創作概述

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 控制項模型由於具有擴充性，因此大幅減少了建立新控制項的需求。 不過，在某些情況下，您可能還是需要建立自訂控制項。 本主題將討論可讓您建立自訂控制項的需求降到最低的一些功能，以及 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的不同控制項撰寫模型。 本主題也將示範如何建立新的控制項。

<a name="when_to_write_a_new_control"></a>

## <a name="alternatives-to-writing-a-new-control"></a>撰寫新控制項的替代方案

在過去，若要從現有控制項自訂控制項，只能變更控制項的標準屬性，例如背景色彩、框線寬度和字型大小。 除了這些預先定義的參數外，若還想擴充控制項的外觀或行為，就需要建立新的控制項，建立的方式通常是繼承現有控制項並覆寫負責繪製控制項。  雖然您現在還是可以使用前述方式，但 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可以讓您藉由使用其豐富的內容模型、樣式、範本和觸發程序來自訂現有的控制項。 下列清單提供的範例說明如何在不建立新控制項的情況下，使用這些功能來建立自訂且一致的控制項。

- **豐富內容。** 許多標準的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項都支援豐富內容。 例如,內容<xref:System.Windows.Controls.Button>屬性的<xref:System.Object>類型 為 ,因此理論上任何內容<xref:System.Windows.Controls.Button>都可以顯示在上。  要有一個按鈕顯示圖像和文本,可以將圖像和<xref:System.Windows.Controls.TextBlock>添加到<xref:System.Windows.Controls.StackPanel>,<xref:System.Windows.Controls.StackPanel>並將分配給<xref:System.Windows.Controls.ContentControl.Content%2A>屬性。 因為控制項可以顯示 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 視覺化項目和任意資料，就比較不需要建立新控制項或修改現有控制項來支援複雜的視覺效果。 有關<xref:System.Windows.Controls.Button>中 的內容模型和其他內容模型的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]詳細資訊 ,請參閱[WPF 內容模型](wpf-content-model.md)。

- **風格。** A<xref:System.Windows.Style>是表示控制件屬性的值的集合。 藉由使用樣式，您可以針對所要的控制項外觀和行為，建立可重複使用的表示方式，而不需要撰寫新的控制項。 例如,假設您希望所有<xref:System.Windows.Controls.TextBlock>控制項具有字體大小為 14 的紅色 Arial 字型。 您可以建立樣式作為資源，並對應地設定適當的屬性。 然後,<xref:System.Windows.Controls.TextBlock>添加到應用程式的每個外觀都將具有相同的外觀。

- **數據範本。** A<xref:System.Windows.DataTemplate>使您能夠自定義數據在控制項上的顯示方式。 例如,可用於<xref:System.Windows.DataTemplate>指定數據在中的<xref:System.Windows.Controls.ListBox>顯示方式。  如需此作業的範例，請參閱[資料範本化概觀](../data/data-templating-overview.md)。  除了自定義數據的外觀外,a<xref:System.Windows.DataTemplate>還可以包含 UI 元素,這為您提供了自定義 UI 的很大靈活性。  例如,通過使用<xref:System.Windows.DataTemplate>, 可以創建<xref:System.Windows.Controls.ComboBox>一個,其中每個專案都包含一個複選框。

- **控件範本。** 中的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]許多控制項<xref:System.Windows.Controls.ControlTemplate>使用 定義控制項的結構和外觀,這將控制元件的外觀與控制項的功能分開。 您可以通過重新定義控制件的外觀來大幅更改<xref:System.Windows.Controls.ControlTemplate>其 外觀。  例如，假設您希望控制項看起來像號誌燈。 這個控制項具有簡單的使用者介面和功能。  控制項是三個圓圈，每次只會亮其中一個。 經過一些思考後,您可能會意識到<xref:System.Windows.Controls.RadioButton>, 提供一次只選擇一個功能的功能,<xref:System.Windows.Controls.RadioButton>但 默認的外觀看起來與紅綠燈上的燈光一樣。  由於<xref:System.Windows.Controls.RadioButton>使用控制項樣本定義其外觀,因此很容易重新定義<xref:System.Windows.Controls.ControlTemplate>,以適應控制項的要求,並使用單選按鈕來使工作點亮。

  > [!NOTE]
  > 儘管<xref:System.Windows.Controls.RadioButton>可以<xref:System.Windows.DataTemplate>使用<xref:System.Windows.DataTemplate>a 是不夠的此範例中。  定義<xref:System.Windows.DataTemplate>控件內容的外觀。 在的情況下<xref:System.Windows.Controls.RadioButton>,內容是圓右側顯示的任何內容,指示是否選擇了<xref:System.Windows.Controls.RadioButton>。  在號誌燈的範例中，選項按鈕只需要是可以發亮的圓圈。 由於停止燈的外觀要求與 的預設外觀非常<xref:System.Windows.Controls.RadioButton>不同 ,因此有必要重新<xref:System.Windows.Controls.ControlTemplate>定義 。  通常,用於<xref:System.Windows.DataTemplate>定義控制件的內容(或資料),並且<xref:System.Windows.Controls.ControlTemplate>用於定義控制項的結構。

- **觸發器。** 允許您<xref:System.Windows.Trigger>動態更改控制件的外觀和行為,而無需創建新控制項。 例如,假設您應用程式中有多個<xref:System.Windows.Controls.ListBox>控制項,並希望每個<xref:System.Windows.Controls.ListBox>控制項中的項在選擇時為粗體和紅色。 您的第一本能可能是建立一個類別,該類別繼承<xref:System.Windows.Controls.ListBox>並重<xref:System.Windows.Controls.Primitives.Selector.OnSelectionChanged%2A>寫 方法以更改所選項的外觀,但更好的方法是將觸發器添加到更改所選項外觀的<xref:System.Windows.Controls.ListBoxItem>樣式 。 觸發程序可讓您變更屬性值，或是依據屬性值採取動作。 使您能夠<xref:System.Windows.EventTrigger>在發生事件時執行操作。

如需樣式、範本和觸發程序的詳細資訊，請參閱[設定樣式和範本](styling-and-templating.md)。

一般而言，若您的控制項可以對應到現有控制項的功能，但您希望控制項看起來不太一樣，則應該先考慮是否能使用本節中所討論的任何方法來變更現有控制項的外觀。

<a name="models_for_control_authoring"></a>

## <a name="models-for-control-authoring"></a>控制項撰寫模型

豐富的內容模型、樣式、範本和觸發程序，可以讓您將建立新控制項的需求降到最低。 然而，若有必要建立新的控制項，最好能先了解 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的不同控制項撰寫模型。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供三種建立控制項的常用模型，每種模型都提供不同的功能集和不同程度的彈性。 三個模型的基礎類是<xref:System.Windows.Controls.UserControl>,<xref:System.Windows.Controls.Control><xref:System.Windows.FrameworkElement>和 。

### <a name="deriving-from-usercontrol"></a>衍生自 UserControl

建立控制項[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的最簡單方法是派生自<xref:System.Windows.Controls.UserControl>。 生成從<xref:System.Windows.Controls.UserControl>繼承的控制項時,將現有元件添加到中<xref:System.Windows.Controls.UserControl>的命名元件和引用事件處理程式。 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 接著，您可以在程式碼中參考該具名項目，並定義事件處理常式。 這個開發模型與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中應用程式開發所使用的模型非常類似。

如果構建正確,則<xref:System.Windows.Controls.UserControl>可以利用豐富的內容、樣式和觸發器的優勢。 但是,如果控件繼承自<xref:System.Windows.Controls.UserControl>,則使用控件的使用者將無法<xref:System.Windows.DataTemplate>使用<xref:System.Windows.Controls.ControlTemplate>或自定義其外觀。  必須從<xref:System.Windows.Controls.Control>類或其派生類之一(<xref:System.Windows.Controls.UserControl>除 )派生才能創建支援範本的自定義控制項。

#### <a name="benefits-of-deriving-from-usercontrol"></a>從 UserControl 衍生的優點

請考慮派生,<xref:System.Windows.Controls.UserControl>如果以下所有都適用:

- 您想要以類似建置應用程式的方式來建置控制項。

- 您的控制項只包含現有的元件。

- 您不需要支援複雜的自訂作業。

### <a name="deriving-from-control"></a>衍生自 Control

從類<xref:System.Windows.Controls.Control>派生是大多數[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]現有控件使用的模型。 創建從<xref:System.Windows.Controls.Control>類繼承的控制項時,可以使用範本定義其外觀。 這樣做您便可以將作業邏輯與視覺表示方式分開處理。 還可以通過使用命令和綁定而不是事件來確保 UI 和邏輯的分離,並盡可能<xref:System.Windows.Controls.ControlTemplate>避免引用中的元素。  如果控件的 UI 和邏輯已正確分離,則控制項的使用者可以重新定義控制<xref:System.Windows.Controls.ControlTemplate>項的,以自訂其外觀。 儘管構建自定義<xref:System.Windows.Controls.Control>不像構建<xref:System.Windows.Controls.UserControl>一 樣簡單,<xref:System.Windows.Controls.Control>但自定義 提供了最大的靈活性。

#### <a name="benefits-of-deriving-from-control"></a>從 Control 衍生的優點

請考慮派生,<xref:System.Windows.Controls.Control>而不是使用類別<xref:System.Windows.Controls.UserControl>, 如果以下任一適用:

- 您希望控件的外觀可以通過<xref:System.Windows.Controls.ControlTemplate>進行 自定義。

- 您想要控制項支援不同的佈景主題。

### <a name="deriving-from-frameworkelement"></a>衍生自 FrameworkElement

派生或<xref:System.Windows.Controls.UserControl><xref:System.Windows.Controls.Control>依賴於組合現有元素的控制項。 對於許多方案,這是一個可接受的解決方案,因為從<xref:System.Windows.FrameworkElement>繼承的任何物件都可以位於 中<xref:System.Windows.Controls.ControlTemplate>。 然而，有時候控制項外觀需要的不僅止於簡單項目組合的功能。 對於這些方案,基於<xref:System.Windows.FrameworkElement>元件是正確的選擇。

基於構建<xref:System.Windows.FrameworkElement>的元件有兩種標準方法:直接呈現和自定義元素組合。 直接呈現涉及重寫<xref:System.Windows.UIElement.OnRender%2A>和<xref:System.Windows.FrameworkElement>提供<xref:System.Windows.Media.DrawingContext>顯式定義元件視覺物件的操作。 這是<xref:System.Windows.Controls.Image>和<xref:System.Windows.Controls.Border>使用的方法。 自定義元素組合涉及使用類型<xref:System.Windows.Media.Visual>物件來組合元件的外觀。 如需範例，請參閱[使用 DrawingVisual 物件](../graphics-multimedia/using-drawingvisual-objects.md)。 <xref:System.Windows.Controls.Primitives.Track>是 中使用自定義元素組合[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的控制項的範例。 您也可以在同一個控制項中混合使用直接轉譯和自訂項目組合。

#### <a name="benefits-of-deriving-from-frameworkelement"></a>從 FrameworkElement 衍生的優點

請考慮派生,<xref:System.Windows.FrameworkElement>如果以下任何一項適用:

- 您想要精確控制控制項的外觀，而這超出了簡單項目組合所能提供的控制。

- 您想要藉由定義自己的轉譯邏輯，來定義控制項的外觀。

- 您希望以新穎的方式撰寫現有元素,超越和<xref:System.Windows.Controls.UserControl><xref:System.Windows.Controls.Control>。

<a name="control_authoring_basics"></a>

## <a name="control-authoring-basics"></a>控制項撰寫基本概念

如稍早所討論，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 其中一個最強大的功能，在於除了設定控制項的基本屬性之外，尚有能力變更其外觀和行為，並且不需要建立自訂控制項。 樣式、資料繫結和觸發程序功能是透過 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 事件系統來達成的。 下列各節說明您應該遵循的一些做法，而不論您是使用哪種模型來建立自訂控制項，讓自訂控制項的使用者能夠使用這些功能，就如同使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 隨附的控制項一樣。

### <a name="use-dependency-properties"></a>使用相依性屬性

當屬性是相依性屬性時，有可能會進行下列作業：

- 設定樣式中的屬性。

- 將屬性繫結至資料來源。

- 使用動態資源作為屬性值。

- 顯示屬性的動畫。

若希望控制項屬性可以支援這些任一功能，就應該將控制項實作為相依性屬性。 下列範例會藉由執行下列動作，定義名為 `Value` 的相依性屬性：

- 定義<xref:System.Windows.DependencyProperty>`ValueProperty`為欄位的`public``static``readonly`識別碼。

- 以呼叫<xref:System.Windows.DependencyProperty.Register%2A?displayProperty=nameWithType>向屬性系統註冊屬性名稱,以指定以下內容:

  - 屬性的名稱。

  - 屬性的類型。

  - 擁有屬性的類型。

  - 屬性的中繼資料。 中繼資料包含屬性的預設值<xref:System.Windows.CoerceValueCallback>a<xref:System.Windows.PropertyChangedCallback>與 。

- 定義名為的`Value`CLR 包裝器屬性,該屬性與用於註冊依賴項屬性的名稱相同,通過`get`實現`set`屬性和訪問器。 請注意,`get``set`與存取器僅分別<xref:System.Windows.DependencyObject.GetValue%2A><xref:System.Windows.DependencyObject.SetValue%2A>呼叫 。 建議依賴項屬性的訪問器不包含其他邏輯,因為客戶端[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]可以繞過訪問器<xref:System.Windows.DependencyObject.GetValue%2A><xref:System.Windows.DependencyObject.SetValue%2A>並直接呼叫。 例如，在屬性繫結到資料來源時，就不會呼叫屬性的 `set` 存取子。  與其向 get 和設置訪問器添加其他邏輯,<xref:System.Windows.ValidateValueCallback>請<xref:System.Windows.CoerceValueCallback><xref:System.Windows.PropertyChangedCallback>使用 和委託在值更改時回應或檢查該值。  如需這些回呼的詳細資訊，請參閱[相依性屬性回呼和驗證](../advanced/dependency-property-callbacks-and-validation.md)。

- 定義命名<xref:System.Windows.CoerceValueCallback>`CoerceValue`的方法。 `CoerceValue` 可以確保 `Value` 大於或等於 `MinValue`，且小於或等於 `MaxValue`。

- 定義名為`OnValueChanged`的方法<xref:System.Windows.PropertyChangedCallback>。 `OnValueChanged`創建一<xref:System.Windows.RoutedPropertyChangedEventArgs%601>個對象並準備`ValueChanged`引發路由事件。 下一節中將討論路由事件。

[!code-csharp[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#dependencyproperty)]
[!code-vb[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#dependencyproperty)]

如需詳細資訊，請參閱[自訂相依性屬性](../advanced/custom-dependency-properties.md)。

### <a name="use-routed-events"></a>使用路由事件

正如依賴項屬性擴展了具有附加功能的 CLR 屬性的概念一樣,路由事件擴展了標準 CLR 事件的概念。 建立新的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項時，最好也能將事件實作為路由事件，因為路由事件支援下列行為：

- 事件可以對多個控制項的父項進行處理。 若事件是反昇事件，項目樹狀結構中的單一父項可以訂閱事件。 然後應用程式作者可以使用一個處理常式，以回應多個控制項的事件。 例如,如果控件是<xref:System.Windows.Controls.ListBox>中 每個項的一部分(因為它<xref:System.Windows.DataTemplate>包含在中),則應用程式開發人員可以在上為控制項的事件定義事件處理<xref:System.Windows.Controls.ListBox>程式。 每當任一控制項上發生事件時，就會呼叫事件處理常式。

- 路由事件可以在 中使用<xref:System.Windows.EventSetter>, 這使應用程式開發人員能夠在樣式中指定事件的處理程式。

- 路由事件可用於 中<xref:System.Windows.EventTrigger>, 這可[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]用於使用 對屬性進行動畫處理。 有關詳細資訊,請參閱[動畫概述](../graphics-multimedia/animation-overview.md)。

下列範例會藉由執行下列動作，定義路由事件：

- 定義<xref:System.Windows.RoutedEvent>`ValueChangedEvent`為欄位的`public``static``readonly`識別碼。

- 通過調用<xref:System.Windows.EventManager.RegisterRoutedEvent%2A?displayProperty=nameWithType>方法註冊路由事件。 這個範例指定呼叫 時的以下<xref:System.Windows.EventManager.RegisterRoutedEvent%2A>資訊 :

  - 事件名稱是 `ValueChanged`。

  - 路由策略為<xref:System.Windows.RoutingStrategy.Bubble>,這意味著首先調用源上的事件處理程式(引發事件的物件),然後連續調用源父元素上的事件處理程式,從最近父元素上的事件處理程式開始。

  - 事件處理程式的類型是<xref:System.Windows.RoutedPropertyChangedEventHandler%601>,<xref:System.Decimal>用 類型建構。

  - 事件的擁有者類型是 `NumericUpDown`。

- 宣告名為 `ValueChanged` 的公用事件，並包含事件存取子宣告。 訪問器聲明<xref:System.Windows.UIElement.AddHandler%2A>`add`<xref:System.Windows.UIElement.RemoveHandler%2A>`remove`和訪問器聲明中的範例呼叫[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用事件服務。

- 建立名為 `OnValueChanged` 的受保護虛擬方法，該方法會引發 `ValueChanged` 事件。

[!code-csharp[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#routedevent)]
[!code-vb[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#routedevent)]

如需詳細資訊，請參閱[路由事件概觀](../advanced/routed-events-overview.md)和[建立自訂路由事件](../advanced/how-to-create-a-custom-routed-event.md)。

### <a name="use-binding"></a>使用繫結

若要降低控制項 UI 和邏輯間的耦合，請考慮使用資料繫結。 如果使用 定義控制項外觀,則這一點尤其重要<xref:System.Windows.Controls.ControlTemplate>。 在您使用資料繫結時，也許可以排除從程式碼參考特定部分之 UI 的需要。 最好避免引用<xref:System.Windows.Controls.ControlTemplate>中的元素,因為當代碼引用<xref:System.Windows.Controls.ControlTemplate>中的<xref:System.Windows.Controls.ControlTemplate>元素並 更改時,引用的元素需要<xref:System.Windows.Controls.ControlTemplate>包含在新的 中。

下面的範例更新<xref:System.Windows.Controls.TextBlock>控制項`NumericUpDown`, 為其分配名稱,並在代碼中按名稱引用文本框。

[!code-xaml[UserControlNumericUpDownSimple#UIRefMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml#uirefmarkup)]

[!code-csharp[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml.cs#uirefcode)]
[!code-vb[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDownSimple/VisualBasic/NumericUpDown.xaml.vb#uirefcode)]

下列範例使用繫結達成相同目的。

[!code-xaml[UserControlNumericUpDown#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml#binding)]

如需資料繫結的詳細資訊，請參閱[資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)。

### <a name="design-for-designers"></a>設計工具的設計

要在 Visual Studio 的 WPF 設計器中接收對自訂 WPF 控件的支援(例如,使用"屬性"視窗進行屬性編輯),請遵循以下準則。  有關為 WPF 設計器進行開發的詳細資訊,請參閱[可視化工作室中的 XAML 設計](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)。

#### <a name="dependency-properties"></a>相依性屬性

請務必實現`get`CLR`set`和 訪問器,如前面所述,在"使用依賴項屬性"。 設計工具可以使用包裝函式來偵測相依性屬性的存在，但就跟 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和控制項用戶端一樣，設計工具在取得或設定屬性時不一定要呼叫存取子。

#### <a name="attached-properties"></a>附加屬性

請使用下列方針，實作自訂控制項上的附加屬性：

- `readonly`<xref:System.Windows.DependencyProperty.RegisterAttached%2A>`static`具有使用方法創建的表單屬性名稱。 `public` <xref:System.Windows.DependencyProperty> * * `Property` 傳遞給的屬性名稱<xref:System.Windows.DependencyProperty.RegisterAttached%2A>必須與*屬性名稱符合*。

- 實作一組 `public` `static` CLR 方法，分別名為 `Set`<屬性名稱>** 和 `Get`<屬性名稱>**。 這兩種方法都應接受派生為<xref:System.Windows.DependencyProperty>第一個參數的類。 `Set`*PropertyName* 方法也接受其型別與屬性之已註冊資料型別相符的引數。 <屬性名稱>`Get`** 方法應傳回相同類型的值。 若遺漏 <屬性名稱>`Set`** 方法，屬性就會標示為唯讀。

- `Set`*屬性名稱*`Get`和*屬性名稱*必須分別直接<xref:System.Windows.DependencyObject.GetValue%2A><xref:System.Windows.DependencyObject.SetValue%2A>路由到 目標依賴項物件和上的方法。 藉由呼叫方法包裝函式，或直接呼叫目標相依性物件，設計工具可以存取附加屬性。

如需附加屬性的詳細資訊，請參閱[附加屬性概觀](../advanced/attached-properties-overview.md)。

### <a name="define-and-use-shared-resources"></a>定義和使用共用資源

您可以將控制項納入與應用程式相同的組件，或者將控制項封裝在不同的組件中，以用於多個應用程式。 在大多數情況下，不論使用的方法為何，本主題所討論的資訊都適用。  不過，有一項差異值得注意。  當您將控制項放入與應用程式相同的組件中時，可以任意將全域資源新增至 App.xaml 檔案。 但是,僅包含控制項的程式集沒有與其關聯的<xref:System.Windows.Application>物件,因此 App.xaml 檔不可用。

當應用程式尋找資源時，會以下列順序在三個層級中尋找：

1. 項目層級。

   系統會從參考資源的項目開始，然後搜尋邏輯父項的資源，以此類推，直到達到根項目為止。

2. 應用程式層級。

   由<xref:System.Windows.Application>物件定義的資源。

3. 佈景主題層級。

   佈景主題層級字典會儲存在名為 Themes 的子資料夾。  Themes 資料夾中的檔案會與佈景主題對應。  例如，您可能有 Aero.NormalColor.xaml、Luna.NormalColor.xaml、Royale.NormalColor.xaml 等等。  您也可以有名為 generic.xaml 的檔案。  當系統在佈景主題層級尋找資源時，會先在佈景主題特定檔案中尋找資源，再到 generic.xaml 中尋找資源。

當您的控制項位於與應用程式不同的組件中時，必須將全域資源置於項目層級或佈景主題層級。 這兩種方法各有其優點。

#### <a name="defining-resources-at-the-element-level"></a>在項目層級定義資源

您可以通過創建自定義資源字典並將其與控制項的資源字典合併,在元素級別定義共享資源。  當您使用這個方法時，可以隨意命名資源檔，而且資源檔可以與控制項位於相同的資料夾中。 項目層級的資源也可以使用簡單的字串作為索引鍵。 下面的範例建立名為<xref:System.Windows.Media.LinearGradientBrush>字典1.xaml的資源檔。

[!code-xaml[SharedResources#1](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/Dictionary1.xaml#1)]

定義字典之後，您需要將它與控制項的資源字典合併。  您可以使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 或程式碼完成這項動作。

下列範例會使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 合併資源字典。

[!code-xaml[SharedResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml#2)]

此方法的缺點是每次引用物件時都會<xref:System.Windows.ResourceDictionary>創建物件。  例如,如果庫中有 10 個自定義控制項,並且使用 XAML 合併每個控制件的共享資源字典,則<xref:System.Windows.ResourceDictionary>創建 10 個相同的物件。  可以通過創建一個靜態類來合併代碼中的資源並返回生成<xref:System.Windows.ResourceDictionary>的 ,來避免這種情況。

下面的範例創建一個返回共用<xref:System.Windows.ResourceDictionary>的類。

[!code-csharp[SharedResources#3](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/SharedDictionaryManager.cs#3)]

下列範例會在呼叫 `InitializeComponent` 之前，在自訂控制項的建構函式中將共用資源與該控制項的資源合併。  由於`SharedDictionaryManager.SharedDictionary`是靜態屬性,<xref:System.Windows.ResourceDictionary>因此僅建立一次 。 由於資源字典是在呼叫 `InitializeComponent` 之前合併，因此控制項可在其 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案中使用資源。

[!code-csharp[SharedResources#4](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml.cs#4)]

#### <a name="defining-resources-at-the-theme-level"></a>在佈景主題層級定義資源

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可讓您為不同的 Windows 佈景主題建立資源。  身為控制項作者，您可以為特定佈景主題定義資源，以根據使用的佈景主題變更控制項的外觀。 例如,Windows<xref:System.Windows.Controls.Button>經典主題(Windows 2000 的預設主題)的<xref:System.Windows.Controls.Button>外觀不同於 Windows Luna 主題(Windows<xref:System.Windows.Controls.Button>XP 的預設<xref:System.Windows.Controls.ControlTemplate>主題),因為 每個主題使用不同的 主題。

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

包含主題和 UI 自動化支援的[C#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp)或[視覺化基本](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic)數位 UpDown`NumericUpDown`自訂控制件包含 兩個用於該控制項的資源字典:一個在泛型.xaml 中,另一個位於 Luna.NormalColor.xaml 中。

將<xref:System.Windows.Controls.ControlTemplate>放入 任何特定於主題的資源字典檔中時,必須為控制項創建靜態構造函數,<xref:System.Windows.DependencyProperty.OverrideMetadata%28System.Type%2CSystem.Windows.PropertyMetadata%29><xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>並在上調用方法,如以下範例所示。

[!code-csharp[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/CSharp/NumericUpDown.cs#staticconstructor)]
[!code-vb[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/visualbasic/numericupdown.vb#staticconstructor)]

##### <a name="defining-and-referencing-keys-for-theme-resources"></a>定義和參考佈景主題資源的索引鍵

當您在項目層級定義資源時，可以指派字串作為它的索引鍵，然後透過字串存取資源。 在主題級別定義資源時,必須使用<xref:System.Windows.ComponentResourceKey>作為 鍵。  下列範例會在 generic.xaml 中定義資源。

[!code-xaml[ThemeResourcesControlLibrary#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/Themes/generic.xaml#5)]

下面的示例通過指定<xref:System.Windows.ComponentResourceKey>為鍵來引用資源。

[!code-xaml[ThemeResourcesControlLibrary#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/NumericUpDown.xaml#6)]

##### <a name="specifying-the-location-of-theme-resources"></a>指定佈景主題資源的位置

若要尋找控制項的資源，裝載的應用程式必須知道組件是否包含控制項特定的資源。 可以通過將<xref:System.Windows.ThemeInfoAttribute>添加到 包含控制項的程式集來實現此目的。 具有<xref:System.Windows.ThemeInfoAttribute>指定通用<xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A>資源位置的屬性,以及指定特定於主題的資源的位置<xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A>的屬性。

下面的範例將<xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A><xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A>和<xref:System.Windows.ResourceDictionaryLocation.SourceAssembly>屬性設置 到 ,以指定泛型和主題特定的資源與控制項位於同一程式集中。

[!code-csharp[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/Properties/AssemblyInfo.cs#themessection)]
[!code-vb[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/my project/assemblyinfo.vb#themessection)]

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中設計 XAML](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [WPF 中的 Pack URI](../app-development/pack-uris-in-wpf.md)
- [控制項自訂](control-customization.md)
