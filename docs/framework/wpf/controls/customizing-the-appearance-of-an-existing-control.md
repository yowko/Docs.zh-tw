---
title: "透過建立 ControlTemplate 自訂現有控制項的外觀 | Microsoft Docs"
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
  - "控制項合約 [WPF]"
  - "控制項 [WPF], 狀態所指定的外觀"
  - "控制項 [WPF], 視覺結構變更"
  - "ControlTemplate [WPF], 現有控制項的自訂"
  - "面板設定控制項 [WPF]"
  - "範本 [WPF], 現有控制項的自訂"
ms.assetid: 678dd116-43a2-4b8c-82b5-6b826f126e31
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 透過建立 ControlTemplate 自訂現有控制項的外觀
<a name="introduction"></a> <xref:System.Windows.Controls.ControlTemplate> 會指定控制項的視覺化結構和視覺化行為。  您可以為控制項提供新的 <xref:System.Windows.Controls.ControlTemplate> 來自訂它的外觀。  當您建立 <xref:System.Windows.Controls.ControlTemplate> 時，會取代現有控制項的外觀，而不會變更它的功能。  例如，您可以讓應用程式中的按鈕變成圓形，而不是使用預設的方形，但是此按鈕仍然會引發 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件。  
  
 本主題說明 <xref:System.Windows.Controls.ControlTemplate> 的各個部分、示範如何為 <xref:System.Windows.Controls.Button> 建立簡單的 <xref:System.Windows.Controls.ControlTemplate>，並說明如何了解控制項的控制項合約，好讓您可以自訂其外觀。  因為您會在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中建立 <xref:System.Windows.Controls.ControlTemplate>，所以您可以變更控制項的外觀，而不需撰寫任何程式碼。  您也可以使用設計工具，例如 Microsoft Expression Blend，若要建立自訂控制項樣板。  本主題將說明 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中自訂 <xref:System.Windows.Controls.Button> 外觀的範例，並且於本主題結尾列出完整的範例。  如需使用 Expression Blend 的詳細資訊，請參閱[設定支援範本之控制項的樣式](http://go.microsoft.com/fwlink/?LinkId=161153)。  
  
 下圖顯示的 <xref:System.Windows.Controls.Button> 會使用本主題中建立的 <xref:System.Windows.Controls.ControlTemplate>。  
  
 ![具有自訂控制項範本的按鈕。](../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP\_ButtonNormal")  
使用自訂控制項樣板的按鈕  
  
 ![具有紅色外框的按鈕。](../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP\_ButtonMouseOver")  
使用自訂控制項樣板且上方有滑鼠指標的按鈕  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="prerequisites"></a>   
## 必要條件  
 本主題假設您已經了解如何建立及使用控制項和樣式，如[控制項](../../../../docs/framework/wpf/controls/index.md)中所討論。  本主題所討論的概念適用於繼承自 <xref:System.Windows.Controls.Control> 類別的項目，但是 <xref:System.Windows.Controls.UserControl> 除外。  您無法將 <xref:System.Windows.Controls.ControlTemplate> 套用至 <xref:System.Windows.Controls.UserControl>。  
  
<a name="when_you_should_create_a_controltemplate"></a>   
## 您應該建立 ControlTemplate 的時機  
 控制項有許多屬性，例如 <xref:System.Windows.Controls.Border.Background%2A>、<xref:System.Windows.Controls.Control.Foreground%2A> 和 <xref:System.Windows.Controls.Control.FontFamily%2A>，您可以設定這些屬性來指定控制項外觀的不同層面，但是能夠藉由設定這些屬性進行的變更會受到限制。  例如，您可以在 <xref:System.Windows.Controls.CheckBox> 上將 <xref:System.Windows.Controls.Control.Foreground%2A> 屬性設定為藍色，並將 <xref:System.Windows.Controls.Control.FontStyle%2A> 設定為斜體。  
  
 如果無法為控制項建立新的 <xref:System.Windows.Controls.ControlTemplate>，每一個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式中的所有控制項都會有相同的一般外觀，這樣會限制建立擁有自訂外觀及操作方式之應用程式的能力。  根據預設，每一個 <xref:System.Windows.Controls.CheckBox> 都有類似的特性。  例如，<xref:System.Windows.Controls.CheckBox> 的內容一定會在選取指示器的右邊，而且一定會使用核取記號來表示已選取 <xref:System.Windows.Controls.CheckBox>。  
  
 當您想在控制項上設定其他屬性所產生的作用之外自訂控制項的外觀時，會建立 <xref:System.Windows.Controls.ControlTemplate>。  在 <xref:System.Windows.Controls.CheckBox> 的範例中，假設您希望核取方塊的內容位於選取指示器的上方，而且希望 X 表示已選取 <xref:System.Windows.Controls.CheckBox>。  您可以在 <xref:System.Windows.Controls.CheckBox> 的 <xref:System.Windows.Controls.ControlTemplate> 中指定這些變更。  
  
 下圖顯示使用預設 <xref:System.Windows.Controls.ControlTemplate> 的 <xref:System.Windows.Controls.CheckBox>。  
  
 ![具有預設控制項範本的核取方塊。](../../../../docs/framework/wpf/controls/media/ndp-checkboxdefault.png "NDP\_CheckBoxDefault")  
使用預設控制項樣板的 CheckBox  
  
 下圖顯示的 <xref:System.Windows.Controls.CheckBox> 會使用自訂的 <xref:System.Windows.Controls.ControlTemplate> 將 <xref:System.Windows.Controls.CheckBox> 的內容放在選取指示器上方，並且在已選取 <xref:System.Windows.Controls.CheckBox> 時顯示 X。  
  
 ![具有自訂控制項範本的核取方塊。](../../../../docs/framework/wpf/controls/media/ndp-checkboxcustom.png "NDP\_CheckBoxCustom")  
使用自訂控制項樣板的 CheckBox  
  
 此範例中 <xref:System.Windows.Controls.CheckBox> 的 <xref:System.Windows.Controls.ControlTemplate> 相對而言比較複雜，因此本主題會使用較簡單的範例為 <xref:System.Windows.Controls.Button> 建立 <xref:System.Windows.Controls.ControlTemplate>。  
  
<a name="changing_the_visual_structure_of_a_control"></a>   
## 變更控制項的視覺化結構  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，控制項通常是複合 <xref:System.Windows.FrameworkElement> 物件。  當您建立 <xref:System.Windows.Controls.ControlTemplate> 時，會結合 <xref:System.Windows.FrameworkElement> 物件來建置單一控制項。  <xref:System.Windows.Controls.ControlTemplate> 必須只能有一個 <xref:System.Windows.FrameworkElement> 做為其根項目。  此根項目通常包含其他 <xref:System.Windows.FrameworkElement> 物件。  物件的組合會組成控制項的視覺化結構。  
  
 下列範例會針對 <xref:System.Windows.Controls.Button> 建立自訂的 <xref:System.Windows.Controls.ControlTemplate>。  <xref:System.Windows.Controls.ControlTemplate> 會建立 <xref:System.Windows.Controls.Button> 的視覺化結構。  這個範例並不會在您將滑鼠指標移到按鈕上方或按一下按鈕時，改變按鈕的外觀。  本主題稍後將會討論如何在不同的狀態下變更按鈕的外觀。  
  
 在此範例中，視覺化結構包含以下各部分：  
  
-   名為 `RootElement` 的 <xref:System.Windows.Controls.Border>，可當做樣板的根 <xref:System.Windows.FrameworkElement>。  
  
-   <xref:System.Windows.Controls.Grid>，它是 `RootElement` 的子系。  
  
-   顯示按鈕內容的 <xref:System.Windows.Controls.ContentPresenter>。  <xref:System.Windows.Controls.ContentPresenter> 可讓任何類型的物件顯示。  
  
 [!code-xml[VSMButtonTemplate#BasicTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]  
  
### 使用 TemplateBinding 保留控制項屬性的功能  
 當您建立新的 <xref:System.Windows.Controls.ControlTemplate> 時，可能仍然會想要使用公用屬性變更控制項的外觀。  [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) 標記延伸會將 <xref:System.Windows.Controls.ControlTemplate> 中項目的屬性繫結到控制項所定義的公用屬性。  當您使用 [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) 時，可將控制項上的屬性當做樣板參數使用。  也就是說，設定控制項上的某個屬性時，會將值傳遞至具有 [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) 的項目上。  
  
 下列範例會重複上面範例中使用 [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) 標記延伸的部分，將 <xref:System.Windows.Controls.ControlTemplate> 中項目的屬性繫結到按鈕所定義的公用屬性。  
  
 [!code-xml[VSMButtonTemplate#TemplateBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]  
  
 在此範例中，<xref:System.Windows.Controls.Grid> 的 <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=fullName> 屬性樣板會繫結至 <xref:System.Windows.Controls.Control.Background%2A?displayProperty=fullName>。  因為 <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=fullName> 會繫結樣板，所以您可以建立多個使用相同 <xref:System.Windows.Controls.ControlTemplate> 的按鈕，並在每一個按鈕上將 <xref:System.Windows.Controls.Control.Background%2A?displayProperty=fullName> 設定為不同的值。  如果 <xref:System.Windows.Controls.Control.Background%2A?displayProperty=fullName> 的樣板未繫結至 <xref:System.Windows.Controls.ControlTemplate> 中項目的屬性，則設定按鈕的 <xref:System.Windows.Controls.Control.Background%2A?displayProperty=fullName> 對於按鈕的外觀不會有任何影響。  
  
 請注意，這兩個屬性的名稱不必相同。  在上面的範例中，<xref:System.Windows.Controls.Button> 的 <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=fullName> 屬性樣板繫結至 <xref:System.Windows.Controls.ContentPresenter> 的 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=fullName> 屬性。  這樣可讓按鈕的內容水平定位。  <xref:System.Windows.Controls.ContentPresenter> 沒有名為 `HorizontalContentAlignment` 的屬性，但是 <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=fullName> 可以繫結至 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=fullName>。  當您將樣板繫結至屬性時，務必確定目標和來源屬性的型別相同。  
  
 <xref:System.Windows.Controls.Control> 類別定義了數個控制項樣板必須使用的屬性，設定這些屬性時，會對控制項產生影響。  <xref:System.Windows.Controls.ControlTemplate> 使用此屬性的方式取決於屬性。  <xref:System.Windows.Controls.ControlTemplate> 必須以下列其中一種方式使用此屬性：  
  
-   <xref:System.Windows.Controls.ControlTemplate> 樣板中的項目繫結至此屬性。  
  
-   <xref:System.Windows.Controls.ControlTemplate> 中的項目從父 <xref:System.Windows.FrameworkElement> 繼承此屬性。  
  
 下表列出控制項繼承自 <xref:System.Windows.Controls.Control> 類別的視覺化屬性。  同時也會指出控制項的預設控制項樣板會使用繼承的屬性值，還是必須繫結樣板。  
  
|屬性|使用方法|  
|--------|----------|  
|<xref:System.Windows.Controls.Control.Background%2A>|樣板繫結|  
|<xref:System.Windows.Controls.Control.BorderThickness%2A>|樣板繫結|  
|<xref:System.Windows.Controls.Control.BorderBrush%2A>|樣板繫結|  
|<xref:System.Windows.Controls.Control.FontFamily%2A>|屬性繼承或樣板繫結|  
|<xref:System.Windows.Controls.Control.FontSize%2A>|屬性繼承或樣板繫結|  
|<xref:System.Windows.Controls.Control.FontStretch%2A>|屬性繼承或樣板繫結|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|屬性繼承或樣板繫結|  
|<xref:System.Windows.Controls.Control.Foreground%2A>|屬性繼承或樣板繫結|  
|<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>|樣板繫結|  
|<xref:System.Windows.Controls.Control.Padding%2A>|樣板繫結|  
|<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>|樣板繫結|  
  
 此表中只列出繼承自 <xref:System.Windows.Controls.Control> 類別的視覺化屬性。  除了上表中列出的屬性之外，控制項也可以從父代架構項目繼承 <xref:System.Windows.FrameworkElement.DataContext%2A>、<xref:System.Windows.FrameworkElement.Language%2A> 和 <xref:System.Windows.Controls.TextBlock.TextDecorations%2A> 屬性。  
  
 此外，如果 <xref:System.Windows.Controls.ContentPresenter> 位於 <xref:System.Windows.Controls.ContentControl> 的 <xref:System.Windows.Controls.ControlTemplate> 中，<xref:System.Windows.Controls.ContentPresenter> 將會自動繫結至 <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> 和 <xref:System.Windows.Controls.ContentControl.Content%2A> 屬性。  同樣地，位於 <xref:System.Windows.Controls.ItemsControl> 之 <xref:System.Windows.Controls.ControlTemplate> 內的 <xref:System.Windows.Controls.ItemsPresenter> 將會自動繫結至 <xref:System.Windows.Controls.ItemsControl.Items%2A> 和 <xref:System.Windows.Controls.ItemsPresenter> 屬性。  
  
 下列範例會建立兩個按鈕，這兩個按鈕會使用前一個範例中所定義的 <xref:System.Windows.Controls.ControlTemplate>。  此範例會在每一個按鈕上設定 <xref:System.Windows.Controls.Control.Background%2A>、<xref:System.Windows.Controls.Control.Foreground%2A> 和 <xref:System.Windows.Controls.Control.FontSize%2A> 屬性。  設定 <xref:System.Windows.Controls.Control.Background%2A> 屬性會有效果，因為它在 <xref:System.Windows.Controls.ControlTemplate> 中會繫結樣板。  即使 <xref:System.Windows.Controls.Control.Foreground%2A> 和 <xref:System.Windows.Controls.Control.FontSize%2A> 屬性未繫結樣板，設定這些屬性還是有效果，因為它們的值是繼承而來的。  
  
 [!code-xml[VSMButtonTemplate#ButtonDeclaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]  
  
 上面的範例產生的輸出與下圖相似。  
  
 ![兩個按鈕，一個為藍色，一個為紫色。](../../../../docs/framework/wpf/controls/media/ndp-buttontwo.png "NDP\_ButtonTwo")  
兩個具有不同背景色彩的按鈕  
  
<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>   
## 根據控制項的狀態變更其外觀  
 採用預設外觀的按鈕與上述範例中的按鈕之間的差異在於，預設按鈕處於不同狀態時會有細微的變化。  例如，按下預設按鈕或是滑鼠指標移到按鈕上方時，按鈕的外觀會改變。  雖然 <xref:System.Windows.Controls.ControlTemplate> 不會變更控制項的功能，但是卻會變更控制項的視覺化行為。  視覺化行為描述控制項處於特定狀態時的外觀。  若要了解控制項的功能與視覺化行為之間的差異，請考慮此按鈕範例。  此按鈕的功能是在按一下時引發 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件，但是此按鈕的視覺化行為則是在指向或按下按鈕時改變其外觀。  
  
 您可以使用 <xref:System.Windows.VisualState> 物件指定控制項處於特定狀態時的外觀。  <xref:System.Windows.VisualState> 包含 <xref:System.Windows.Media.Animation.Storyboard>，它會變更 <xref:System.Windows.Controls.ControlTemplate> 中項目的外觀。  您不必撰寫任何程式碼，也能讓這個情況發生，因為控制項的邏輯會使用 <xref:System.Windows.VisualStateManager> 來變更狀態。  控制項進入 <xref:System.Windows.VisualState.Name%2A?displayProperty=fullName> 屬性所指定的狀態時，<xref:System.Windows.Media.Animation.Storyboard> 就會開始。  當控制項離開該狀態時，<xref:System.Windows.Media.Animation.Storyboard> 就會停止。  
  
 下列範例顯示 <xref:System.Windows.VisualState> 會在滑鼠指標位於 <xref:System.Windows.Controls.Button> 的上方時變更其外觀。  <xref:System.Windows.Media.Animation.Storyboard> 會藉由變更 `BorderBrush` 的色彩來變更按鈕的框線色彩。  如果您參考本主題開頭的 <xref:System.Windows.Controls.ControlTemplate> 範例，就會想起 `BorderBrush` 是指派給 <xref:System.Windows.Controls.Border> 之 <xref:System.Windows.Controls.Border.Background%2A> 的 <xref:System.Windows.Media.SolidColorBrush> 名稱。  
  
 [!code-xml[VSMButtonTemplate#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#4)]  
  
 此控制項負責定義屬於其控制項合約一部分的狀態，本主題稍後的[了解控制項合約來自訂其他控制項](#customizing_other_controls_by_understanding_the_control_contract)中將對此提供詳細討論。  下表列出為 <xref:System.Windows.Controls.Button> 指定的狀態。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|--------------------|-------------------------|--------|  
|Normal|CommonStates|預設狀態。|  
|MouseOver|CommonStates|滑鼠指標位於控制項上方。|  
|Pressed|CommonStates|已按下控制項。|  
|Disabled|CommonStates|控制項已停用。|  
|Focused|FocusStates|控制項擁有焦點。|  
|Unfocused|FocusStates|控制項沒有焦點。|  
  
 <xref:System.Windows.Controls.Button> 定義了兩個狀態群組：`CommonStates` 群組包含 `Normal`、`MouseOver`、`Pressed` 和 `Disabled` 狀態。  `FocusStates` 群組則包含 `Focused` 和 `Unfocused` 狀態。  相同狀態群組內的狀態會互斥 \(Mutually Exclusive\)。  此控制項在一個群組中會固定處於一種狀態。  例如，即使滑鼠指標不在 <xref:System.Windows.Controls.Button> 上方，它也可以有焦點，所以處於 `Focused` 狀態下的 <xref:System.Windows.Controls.Button> 可以處於 `MouseOver`、`Pressed` 或 `Normal` 狀態。  
  
 您會將 <xref:System.Windows.VisualState> 物件加入至 <xref:System.Windows.VisualStateGroup> 物件。  再將 <xref:System.Windows.VisualStateGroup> 物件加入至 <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=fullName> 附加屬性。  下列範例會針對 `Normal`、`MouseOver` 和 `Pressed` 狀態定義 <xref:System.Windows.VisualState> 物件，這些狀態都在 `CommonStates` 群組中。  每一個 <xref:System.Windows.VisualState> 的 <xref:System.Windows.VisualState.Name%2A> 都會符合上表中的名稱。  `Disabled` 狀態及 `FocusStates` 群組中的狀態則會省略，以便維持範例精簡，但是這些狀態都會包含在本主題最後的完整範例中。  
  
> [!NOTE]
>  請務必在 <xref:System.Windows.Controls.ControlTemplate> 的根 <xref:System.Windows.FrameworkElement> 上設定 <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=fullName> 附加屬性。  
  
 [!code-xml[VSMButtonTemplate#VisualStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualstates)]  
  
 上面的範例產生的輸出與下圖相似。  
  
 ![具有自訂控制項範本的按鈕。](../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP\_ButtonNormal")  
使用自訂控制項樣板的正常狀態按鈕  
  
 ![具有紅色外框的按鈕。](../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP\_ButtonMouseOver")  
使用自訂控制項樣板且處於滑鼠位於上方狀態的按鈕  
  
 ![已按下按鈕的框線呈現為透明。](../../../../docs/framework/wpf/controls/media/ndp-buttonpressed.png "NDP\_ButtonPressed")  
使用自訂控制項樣板的按下狀態按鈕  
  
 若要尋找 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 所附控制項的可見狀態，請參閱[控制項的樣式和範本](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)。  
  
<a name="specifying_the_behavior_of_a_control_when_it_transitions_between_states"></a>   
## 指定控制項在不同狀態之間轉換時的行為  
 在上面的範例中，按鈕的外觀也會在使用者按一下按鈕時改變，但是除非按住按鈕長達一秒，否則使用者不會看見這個效果。  根據預設，動畫發生的時間需要一秒鐘。  因為使用者可能在更短的時間內按下及放開按鈕，所以如果您將 <xref:System.Windows.Controls.ControlTemplate> 保持在預設狀態，視覺化回應將不會有效果。  
  
 您可以透過將 <xref:System.Windows.VisualTransition> 物件加入至 <xref:System.Windows.Controls.ControlTemplate> 的方式指定動畫發生所需的時間，以便讓控制項順利地從某個狀態轉換到另一個狀態。  當您建立 <xref:System.Windows.VisualTransition> 時，會指定下列其中的一或多項：  
  
-   發生狀態轉換所需的時間。  
  
-   轉換時，控制項外觀所發生的其他變更。  
  
-   套用 <xref:System.Windows.VisualTransition> 的狀態。  
  
### 指定轉換的持續期間  
 您可以設定 <xref:System.Windows.VisualTransition.GeneratedDuration%2A> 屬性來指定轉換所需的時間。  上面範例中的 <xref:System.Windows.VisualState> 會指定當按下按鈕時，按鈕的框線會變成透明，但是在快速按下及放開按鈕時，會因為動畫需要更多時間才能呈現，而看不到其效果。  您可以使用 <xref:System.Windows.VisualTransition> 來指定控制項轉換至按下狀態所需的時間。  下列範例指定控制項需要花百分之一秒的時間進入按下狀態。  
  
 [!code-xml[VSMButtonTemplate#PressedTransition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]  
  
### 指定控制項外觀在轉換期間的變更  
 <xref:System.Windows.VisualTransition> 包含控制項在不同狀態之間轉換時開始的 <xref:System.Windows.Media.Animation.Storyboard>。  例如，您可以指定當控制項從 `MouseOver` 狀態轉換至 `Normal` 狀態時發生某個動畫。  下列範例會建立 <xref:System.Windows.VisualTransition>，用來指定使用者從按鈕移開滑鼠指標時，按鈕的框線在 1.5 秒內會變為藍色，接著是黃色，然後是黑色。  
  
 [!code-xml[VSMButtonTemplate#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]  
  
### 指定套用 VisualTransition 的時機  
 <xref:System.Windows.VisualTransition> 可以限制為只套用到某些狀態，或者可以在控制項於兩個狀態之間轉換的任何時間套用。  在前一個範例中，當控制項從 `MouseOver` 狀態進入 `Normal` 狀態時會套用 <xref:System.Windows.VisualTransition>；而在更早的範例中，當控制項進入 `Pressed` 狀態時會套用 <xref:System.Windows.VisualTransition>。  您可以設定 <xref:System.Windows.VisualTransition.To%2A> 和 <xref:System.Windows.VisualTransition.From%2A> 屬性，藉此限制套用 <xref:System.Windows.VisualTransition> 的時機。  下表說明最嚴格到最不嚴格的限制層級。  
  
|限制類型|來源值|結果值|  
|----------|---------|---------|  
|從指定的狀態到另一個指定的狀態|<xref:System.Windows.VisualState> 的名稱|<xref:System.Windows.VisualState> 的名稱|  
|從任一狀態到指定的狀態|未設定|<xref:System.Windows.VisualState> 的名稱|  
|從指定的狀態到任一狀態|<xref:System.Windows.VisualState> 的名稱|未設定|  
|從任一狀態到任一其他狀態|未設定|未設定|  
  
 在參考相同狀態的 <xref:System.Windows.VisualStateGroup> 中，可以有多個 <xref:System.Windows.VisualTransition> 物件，但是這些物件會按照上表指定的順序使用。  下列範例中有兩個 <xref:System.Windows.VisualTransition> 物件。  控制項由 `Pressed` 狀態轉換到 `MouseOver` 狀態時，會使用同時設定 <xref:System.Windows.VisualTransition.From%2A> 和 <xref:System.Windows.VisualTransition.To%2A> 的 <xref:System.Windows.VisualTransition>。  當控制項從不是 `Pressed` 的狀態轉換為 `MouseOver` 狀態時，會使用其他狀態。  
  
 [!code-xml[VSMButtonTemplate#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]  
  
 <xref:System.Windows.VisualStateGroup> 具有 <xref:System.Windows.VisualStateGroup.Transitions%2A> 屬性，此屬性包含了套用到 <xref:System.Windows.VisualStateGroup> 內之 <xref:System.Windows.VisualState> 物件的 <xref:System.Windows.VisualTransition> 物件。  您身為 <xref:System.Windows.Controls.ControlTemplate> 作者，可以隨意包含您想要的任何 <xref:System.Windows.VisualTransition>。  但是，如果 <xref:System.Windows.VisualTransition.To%2A> 和 <xref:System.Windows.VisualTransition.From%2A> 屬性設定為不在 <xref:System.Windows.VisualStateGroup> 內的狀態名稱，則會忽略 <xref:System.Windows.VisualTransition>。  
  
 下列範例會針對 `CommonStates` 顯示 <xref:System.Windows.VisualStateGroup>。  此範例會針對下列每一個按鈕的轉換定義 <xref:System.Windows.VisualTransition>。  
  
-   轉換為 `Pressed` 狀態。  
  
-   轉換為 `MouseOver` 狀態。  
  
-   從 `Pressed` 狀態到 `MouseOver` 狀態。  
  
-   從 `MouseOver` 狀態到 `Normal` 狀態。  
  
 [!code-xml[VSMButtonTemplate#VisualTransitions](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]  
  
<a name="customizing_other_controls_by_understanding_the_control_contract"></a>   
## 了解控制項合約來自訂其他控制項  
 使用 <xref:System.Windows.Controls.ControlTemplate> 來指定視覺化結構 \(利用 <xref:System.Windows.FrameworkElement> 物件\) 和視覺化行為 \(利用 <xref:System.Windows.VisualState> 物件\) 的控制項會使用組件控制項模型。  隨附於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 4 的許多控制項都是使用此模型。  <xref:System.Windows.Controls.ControlTemplate> 作者需要了解的組件會透過控制項合約來溝通。  當您了解控制項合約的組件時，就可以自訂任何使用組件控制項模型的控制項外觀。  
  
 控制項合約有三個項目：  
  
-   控制項邏輯使用的視覺化項目。  
  
-   控制項的狀態，以及每一種狀態所屬的群組。  
  
-   影響控制項視覺外觀的公用屬性。  
  
### 控制項合約中的視覺項目  
 有時控制項的邏輯會與 <xref:System.Windows.Controls.ControlTemplate> 中的 <xref:System.Windows.FrameworkElement> 互動。  例如，控制項可能會處理它的其中一個項目的事件。  當控制項預定尋找 <xref:System.Windows.Controls.ControlTemplate> 內的特定 <xref:System.Windows.FrameworkElement> 時，它必須將該資訊傳達給 <xref:System.Windows.Controls.ControlTemplate> 作者。  控制項會使用 <xref:System.Windows.TemplatePartAttribute> 來傳達所預期的項目類型以及項目應有的名稱。  <xref:System.Windows.Controls.Button> 在它的控制項合約內並沒有 <xref:System.Windows.FrameworkElement> 組件，但是其他控制項 \(如 <xref:System.Windows.Controls.ComboBox>\) 則有。  
  
 下列範例會顯示 <xref:System.Windows.Controls.ComboBox> 類別上所指定的 <xref:System.Windows.TemplatePartAttribute> 物件。  <xref:System.Windows.Controls.ComboBox> 的邏輯預定在其 <xref:System.Windows.Controls.ControlTemplate> 中尋找名為 `PART_EditableTextBox` 的 <xref:System.Windows.Controls.TextBox> 以及名為 `PART_Popup` 的 <xref:System.Windows.Controls.Primitives.Popup>。  
  
 [!code-csharp[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]  
  
 下列範例顯示 <xref:System.Windows.Controls.ComboBox> 的簡化 <xref:System.Windows.Controls.ControlTemplate>，其中包含 <xref:System.Windows.TemplatePartAttribute> 物件在 <xref:System.Windows.Controls.ComboBox> 類別上指定的項目。  
  
 [!code-xml[VSMButtonTemplate#ComboBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]  
  
### 控制項合約中的狀態  
 控制項的狀態也屬於控制項合約的一部分。  為 <xref:System.Windows.Controls.Button> 建立 <xref:System.Windows.Controls.ControlTemplate> 的範例會顯示如何指定依據狀態指定 <xref:System.Windows.Controls.Button> 的外觀。  您會針對每一種指定的狀態建立 <xref:System.Windows.VisualState>，並且將共用 <xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A> 的所有 <xref:System.Windows.VisualState> 物件放入 <xref:System.Windows.VisualStateGroup>，如同本主題稍早的[根據控制項的狀態變更其外觀](#changing_the_appearance_of_a_control_depending_on_its_state)中所述。  協力廠商控制項應該藉由指定狀態<xref:System.Windows.TemplateVisualStateAttribute>，可讓設計工具，例如 Expression Blend，若要公開 \(expose\) 為撰寫控制項樣板的控制項的狀態。  
  
 若要尋找 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 所附控制項的控制項合約，請參閱[控制項的樣式和範本](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)。  
  
### 控制項合約中的屬性  
 在視覺上影響此控制項的公用屬性也會包含在控制項合約內。  您可以設定這些屬性來變更控制項的外觀，而不用建立新的 <xref:System.Windows.Controls.ControlTemplate>。  您也可以使用 [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) 標記延伸，將 <xref:System.Windows.Controls.ControlTemplate> 中項目的屬性繫結到 <xref:System.Windows.Controls.Button> 所定義的公用屬性。  
  
 下列範例顯示按鈕的控制項合約。  
  
 [!code-csharp[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]  
  
 當建立 <xref:System.Windows.Controls.ControlTemplate> 時，通常最簡單的方法是從現有的 <xref:System.Windows.Controls.ControlTemplate> 開始，並對它進行變更。  您可以執行下列其中一個動作來變更現有的 <xref:System.Windows.Controls.ControlTemplate>：  
  
-   使用設計工具 \(如 Expression Blend\)，這項工具提供了圖形使用者介面來建立控制項樣板。  如需詳細資訊，請參閱[為支援樣板的控制項設定樣式](http://go.microsoft.com/fwlink/?LinkId=161153) \(英文\)。  
  
-   取得預設的 <xref:System.Windows.Controls.ControlTemplate> 並加以編輯。  若要尋找 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 隨附的預設控制項範本，請參閱[預設 WPF 主題](http://go.microsoft.com/fwlink/?LinkID=158252) \(英文\)。  
  
<a name="complete_example"></a>   
## 完整範例  
 下列範例顯示本主題中所討論的完整 <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ControlTemplate>。  
  
 [!code-xml[VSMButtonTemplate#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]  
  
## 請參閱  
 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)