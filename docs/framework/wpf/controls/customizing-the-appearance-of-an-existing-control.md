---
title: 透過建立 ControlTemplate 自訂現有控制項的外觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control contract [WPF]
- controls [WPF], visual structure changes
- ControlTemplate [WPF], customizing for existing controls
- skinning controls [WPF]
- controls [WPF], appearance specified by state
- templates [WPF], custom for existing controls
ms.assetid: 678dd116-43a2-4b8c-82b5-6b826f126e31
ms.openlocfilehash: f8802ae00de2bdb87e4e47fb82f6ebdf2108e2a9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547289"
---
# <a name="customizing-the-appearance-of-an-existing-control-by-creating-a-controltemplate"></a>透過建立 ControlTemplate 自訂現有控制項的外觀
<a name="introduction"></a> A<xref:System.Windows.Controls.ControlTemplate>指定的視覺結構和控制項的視覺行為。 您可以藉由提供新自訂控制項的外觀<xref:System.Windows.Controls.ControlTemplate>。 當您建立<xref:System.Windows.Controls.ControlTemplate>，您會取代現有控制項的外觀，而不變更其功能。 例如，您可以讓按鈕在您的應用程式而不是預設的方形，round，但仍會引發按鈕<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。  
  
 本主題說明的各個部分<xref:System.Windows.Controls.ControlTemplate>，示範如何建立簡單<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.Button>，並說明如何了解控制項合約的控制項，讓您可以自訂其外觀。 因為您會建立<xref:System.Windows.Controls.ControlTemplate>在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您可以變更控制項的外觀，而不需要撰寫任何程式碼。 您也可以使用設計工具 (例如 Microsoft Expression Blend) 來建立自訂控制項樣板。 本主題說明中的範例[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]來自訂外觀<xref:System.Windows.Controls.Button>，並列出完整的範例，在本主題結尾處。 如需有關使用 Expression Blend 的詳細資訊，請參閱[設定支援範本之控制項的樣式](https://go.microsoft.com/fwlink/?LinkId=161153)。  
  
 下列圖例顯示<xref:System.Windows.Controls.Button>使用<xref:System.Windows.Controls.ControlTemplate>本主題中所建立。  
  
 ![具有自訂控制項範本的按鈕。](../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP_ButtonNormal")  
使用自訂控制項範本的按鈕  
  
 ![具有紅色外框的按鈕。](../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
使用自訂控制項範本且滑鼠指標移至其上方的按鈕  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 本主題假設您了解如何建立和使用控制項與樣式，如[控制項](../../../../docs/framework/wpf/controls/index.md)所述。 本主題中討論的概念適用於項目繼承自<xref:System.Windows.Controls.Control>類別，除了<xref:System.Windows.Controls.UserControl>。 您不能套用<xref:System.Windows.Controls.ControlTemplate>至<xref:System.Windows.Controls.UserControl>。  
  
<a name="when_you_should_create_a_controltemplate"></a>   
## <a name="when-you-should-create-a-controltemplate"></a>建立 ControlTemplate 的適當時機  
 控制項有許多屬性，例如<xref:System.Windows.Controls.Border.Background%2A>， <xref:System.Windows.Controls.Control.Foreground%2A>，和<xref:System.Windows.Controls.Control.FontFamily%2A>，您可以設定為指定的控制項的外觀不同層面，但您可以藉由設定這些屬性進行的變更是有限。 例如，您可以設定<xref:System.Windows.Controls.Control.Foreground%2A>藍色的屬性和<xref:System.Windows.Controls.Control.FontStyle%2A>上為斜體<xref:System.Windows.Controls.CheckBox>。  
  
 無需在建立新<xref:System.Windows.Controls.ControlTemplate>控制項，所有控制項中每個[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-架構的應用程式會有相同的一般外觀，這會限制能夠建立應用程式使用自訂的外觀與風格。 根據預設，每個<xref:System.Windows.Controls.CheckBox>具有類似的特性。 比方說的內容<xref:System.Windows.Controls.CheckBox>總是右邊的選取範圍指標中，並核取記號一律用來指出<xref:System.Windows.Controls.CheckBox>已選取。  
  
 您建立<xref:System.Windows.Controls.ControlTemplate>當您想要自訂控制項的外觀就在控制項上設定其他屬性。 在範例中的<xref:System.Windows.Controls.CheckBox>假設您想要在選取範圍指標上方的核取方塊的內容，您想要以 X 指出，<xref:System.Windows.Controls.CheckBox>已選取。 指定在這些變更<xref:System.Windows.Controls.ControlTemplate>的<xref:System.Windows.Controls.CheckBox>。  
  
 如下圖所示<xref:System.Windows.Controls.CheckBox>使用預設<xref:System.Windows.Controls.ControlTemplate>。  
  
 ![核取方塊具有預設控制項範本。](../../../../docs/framework/wpf/controls/media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
使用預設控制項範本的 CheckBox  
  
 如下圖所示<xref:System.Windows.Controls.CheckBox>使用自訂<xref:System.Windows.Controls.ControlTemplate>的內容放<xref:System.Windows.Controls.CheckBox>上方顯示 X 與選取範圍指標時<xref:System.Windows.Controls.CheckBox>已選取。  
  
 ![核取方塊具有自訂控制項範本。](../../../../docs/framework/wpf/controls/media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
使用自訂控制項範本的 CheckBox  
  
 <xref:System.Windows.Controls.ControlTemplate> For<xref:System.Windows.Controls.CheckBox>在此範例中是相當複雜，因此本主題會使用建立的簡單範例<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.Button>。  
  
<a name="changing_the_visual_structure_of_a_control"></a>   
## <a name="changing-the-visual-structure-of-a-control"></a>變更控制項的視覺結構  
 在  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，控制項通常是複合<xref:System.Windows.FrameworkElement>物件。 當您建立<xref:System.Windows.Controls.ControlTemplate>，您將結合<xref:System.Windows.FrameworkElement>物件來建置單一的控制項。 A<xref:System.Windows.Controls.ControlTemplate>只能有一個<xref:System.Windows.FrameworkElement>作為其根項目。 根元素通常會包含其他<xref:System.Windows.FrameworkElement>物件。 這些物件的組合會構成控制項的視覺結構。  
  
 下列範例會建立自訂<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.Button>。 <xref:System.Windows.Controls.ControlTemplate>建立的視覺結構<xref:System.Windows.Controls.Button>。 此範例並不會變更您將滑鼠指標移至按鈕上或按一下按鈕時的按鈕外觀。 變更按鈕處於不同狀態時的外觀將在本主題稍後討論。  
  
 在此範例中，視覺結構是由下列部分所組成：  
  
-   A<xref:System.Windows.Controls.Border>名為`RootElement`做為範本的根<xref:System.Windows.FrameworkElement>。  
  
-   A<xref:System.Windows.Controls.Grid>也就是子系`RootElement`。  
  
-   A<xref:System.Windows.Controls.ContentPresenter>顯示按鈕的內容。 <xref:System.Windows.Controls.ContentPresenter>可讓任何類型的物件可顯示。  
  
 [!code-xaml[VSMButtonTemplate#BasicTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]  
  
### <a name="preserving-the-functionality-of-a-controls-properties-by-using-templatebinding"></a>使用 TemplateBinding 來保留控制項屬性的功能  
 當您建立新<xref:System.Windows.Controls.ControlTemplate>，您仍可能會想要使用的公用屬性來變更控制項的外觀。 [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)標記延伸模組會將繫結項目中的屬性<xref:System.Windows.Controls.ControlTemplate>至控制項所定義的公用屬性。 當您使用 [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) 時，會讓控制項上的屬性能夠作為範本的參數。 也就是說，已設定控制項上的屬性時，該值會傳遞給具有 [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) 的元素。  
  
 下列範例會重複使用上述範例的一部分[TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)屬性中的項目繫結標記延伸<xref:System.Windows.Controls.ControlTemplate>按鈕所定義的公用屬性。  
  
 [!code-xaml[VSMButtonTemplate#TemplateBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]  
  
 在此範例中，<xref:System.Windows.Controls.Grid>有其<xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType>屬性範本繫結至<xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>。 因為<xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType>是範本方式繫結，您可以建立使用相同的多個按鈕<xref:System.Windows.Controls.ControlTemplate>並設定<xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>每個按鈕上的不同值。 如果<xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>已不是範本繫結至屬性中的項目<xref:System.Windows.Controls.ControlTemplate>，將<xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>的按鈕會有任何影響按鈕的外觀。  
  
 請注意，兩個屬性的名稱不一定要相同。 在上述範例中，<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType>的屬性<xref:System.Windows.Controls.Button>範本繫結至<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>屬性<xref:System.Windows.Controls.ContentPresenter>。 這可讓您以水平方式置放按鈕的內容。 <xref:System.Windows.Controls.ContentPresenter> 沒有名為的屬性`HorizontalContentAlignment`，但<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType>可以繫結至<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>。 當您的範本繫結某個屬性時，請確定目標與來源屬性是相同類型。  
  
 <xref:System.Windows.Controls.Control>類別會定義數個屬性，必須使用控制項範本，來設定時，有在控制項上的效果。 如何<xref:System.Windows.Controls.ControlTemplate>屬性取決於屬性的使用。 <xref:System.Windows.Controls.ControlTemplate>必須使用其中一種以下列方式的屬性：  
  
-   中的項目<xref:System.Windows.Controls.ControlTemplate>範本繫結至屬性。  
  
-   中的項目<xref:System.Windows.Controls.ControlTemplate>繼承自父代的屬性<xref:System.Windows.FrameworkElement>。  
  
 下表列出由從控制項繼承的視覺屬性<xref:System.Windows.Controls.Control>類別。 它同時也指出控制項的預設控制項範本是否使用繼承的屬性值，或是否必須以範本方式繫結。  
  
|屬性|使用方式|  
|--------------|------------------|  
|<xref:System.Windows.Controls.Control.Background%2A>|範本繫結|  
|<xref:System.Windows.Controls.Control.BorderThickness%2A>|範本繫結|  
|<xref:System.Windows.Controls.Control.BorderBrush%2A>|範本繫結|  
|<xref:System.Windows.Controls.Control.FontFamily%2A>|屬性繼承或範本繫結|  
|<xref:System.Windows.Controls.Control.FontSize%2A>|屬性繼承或範本繫結|  
|<xref:System.Windows.Controls.Control.FontStretch%2A>|屬性繼承或範本繫結|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|屬性繼承或範本繫結|  
|<xref:System.Windows.Controls.Control.Foreground%2A>|屬性繼承或範本繫結|  
|<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>|範本繫結|  
|<xref:System.Windows.Controls.Control.Padding%2A>|範本繫結|  
|<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>|範本繫結|  
  
 資料表只會列出 visual 屬性繼承自<xref:System.Windows.Controls.Control>類別。 除了資料表中所列的屬性，控制項可能也會繼承<xref:System.Windows.FrameworkElement.DataContext%2A>， <xref:System.Windows.FrameworkElement.Language%2A>，和<xref:System.Windows.Controls.TextBlock.TextDecorations%2A>從父架構元素的屬性。  
  
 此外，如果<xref:System.Windows.Controls.ContentPresenter>處於<xref:System.Windows.Controls.ControlTemplate>的<xref:System.Windows.Controls.ContentControl>，則<xref:System.Windows.Controls.ContentPresenter>會自動繫結至<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>和<xref:System.Windows.Controls.ContentControl.Content%2A>屬性。 同樣地，<xref:System.Windows.Controls.ItemsPresenter>位於<xref:System.Windows.Controls.ControlTemplate>的<xref:System.Windows.Controls.ItemsControl>會自動繫結至<xref:System.Windows.Controls.ItemsControl.Items%2A>和<xref:System.Windows.Controls.ItemsPresenter>屬性。  
  
 下列範例會建立使用的兩個按鈕<xref:System.Windows.Controls.ControlTemplate>上述範例中所定義。 範例會設定<xref:System.Windows.Controls.Control.Background%2A>， <xref:System.Windows.Controls.Control.Foreground%2A>，和<xref:System.Windows.Controls.Control.FontSize%2A>每個按鈕上的屬性。 設定<xref:System.Windows.Controls.Control.Background%2A>屬性沒有作用，因為它是繫結中的範本<xref:System.Windows.Controls.ControlTemplate>。 即使<xref:System.Windows.Controls.Control.Foreground%2A>和<xref:System.Windows.Controls.Control.FontSize%2A>屬性不是範本方式繫結，將其設定沒有作用，因為會繼承其值。  
  
 [!code-xaml[VSMButtonTemplate#ButtonDeclaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]  
  
 上述範例會產生類似下圖的輸出。  
  
 ![兩個按鈕，一個為藍色，一個為紫色。](../../../../docs/framework/wpf/controls/media/ndp-buttontwo.png "NDP_ButtonTwo")  
兩個具有不同背景色彩的按鈕  
  
<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>   
## <a name="changing-the-appearance-of-a-control-depending-on-its-state"></a>依控制項的狀態變更其外觀  
 具有預設外觀的按鈕與上述範例中按鈕之間的差異在於，預設按鈕在處於不同狀態時會稍微變更。 例如，預設按鈕會在使用者按下按鈕時，或當滑鼠指標移至按鈕上時，變更外觀。 雖然<xref:System.Windows.Controls.ControlTemplate>不會變更功能的控制項，但是會變更控制項的視覺行為。 視覺行為會描述控制項處於特定狀態時的外觀。 若要了解控制項的功能與視覺行為之間有何差異，請思考一下按鈕範例。 按鈕的功能是以引發<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件時按下它時，但按鈕的視覺行為是指向或按下時，變更其外觀。  
  
 您使用<xref:System.Windows.VisualState>物件處於特定狀態時，指定控制項的外觀。 A<xref:System.Windows.VisualState>包含<xref:System.Windows.Media.Animation.Storyboard>變更其外觀的項目在<xref:System.Windows.Controls.ControlTemplate>。 您不必撰寫任何程式碼，因為控制項的邏輯會將狀態變更所使用<xref:System.Windows.VisualStateManager>。 當控制項進入所指定的狀態<xref:System.Windows.VisualState.Name%2A?displayProperty=nameWithType>屬性，<xref:System.Windows.Media.Animation.Storyboard>開始。 當控制項結束狀態，<xref:System.Windows.Media.Animation.Storyboard>停止。  
  
 下列範例所示<xref:System.Windows.VisualState>變更其外觀的<xref:System.Windows.Controls.Button>當滑鼠指標位在它。 <xref:System.Windows.Media.Animation.Storyboard>變更按鈕的框線色彩的色彩變更`BorderBrush`。 如果您參考<xref:System.Windows.Controls.ControlTemplate>範例位於本主題開頭，您將會想起`BorderBrush`名稱<xref:System.Windows.Media.SolidColorBrush>指派給<xref:System.Windows.Controls.Border.Background%2A>的<xref:System.Windows.Controls.Border>。  
  
 [!code-xaml[VSMButtonTemplate#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#4)]  
  
 控制項需負責在定義其控制項合約時一併定義狀態，本主題稍後的[透過了解控制項合約來自訂其他控制項](#customizing_other_controls_by_understanding_the_control_contract)中會詳細討論。 下表列出針對所指定的狀態<xref:System.Windows.Controls.Button>。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|----------------------|---------------------------|-----------------|  
|一般|CommonStates|預設狀態。|  
|MouseOver|CommonStates|滑鼠指標移到控制項上。|  
|按下|CommonStates|已按下控制項。|  
|已停用|CommonStates|已停用控制項。|  
|已取得焦點|FocusStates|控制項已取得焦點。|  
|未取得焦點|FocusStates|控制項未取得焦點。|  
  
 <xref:System.Windows.Controls.Button>定義兩個狀態群組：`CommonStates`群組包含`Normal`， `MouseOver`， `Pressed`，和`Disabled`狀態。 `FocusStates` 群組則包含 `Focused` 和 `Unfocused` 狀態。 相同狀態群組中的狀態彼此互斥。 控制項就每一群組而言一律僅限處於一種狀態。 例如，<xref:System.Windows.Controls.Button>能夠擁有焦點，滑鼠指標不是，因此，即使<xref:System.Windows.Controls.Button>中`Focused`狀態可以是`MouseOver`， `Pressed`，或`Normal`狀態。  
  
 您將新增<xref:System.Windows.VisualState>物件至<xref:System.Windows.VisualStateGroup>物件。 您將新增<xref:System.Windows.VisualStateGroup>物件至<xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType>附加屬性。 下列範例會定義<xref:System.Windows.VisualState>的物件`Normal`， `MouseOver`，以及`Pressed`狀態，全部都在`CommonStates`群組。 <xref:System.Windows.VisualState.Name%2A>每個<xref:System.Windows.VisualState>符合上表中的名稱。 為了簡化範例，已省略 `Disabled` 狀態及`FocusStates` 群組中的狀態，但在本主題結尾的完整範例中已將它們都包含在內。  
  
> [!NOTE]
>  請務必設定<xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType>附加屬性上的根<xref:System.Windows.FrameworkElement>的<xref:System.Windows.Controls.ControlTemplate>。  
  
 [!code-xaml[VSMButtonTemplate#VisualStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualstates)]  
  
 上述範例會產生類似下列圖例的輸出。  
  
 ![具有自訂控制項範本的按鈕。](../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP_ButtonNormal")  
使用處於正常狀態之自訂控制項範本的按鈕  
  
 ![具有紅色外框的按鈕。](../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
使用處於滑鼠移至上方狀態之自訂控制項範本的按鈕  
  
 ![上框線呈現透明的已按下按鈕。](../../../../docs/framework/wpf/controls/media/ndp-buttonpressed.png "NDP_ButtonPressed")  
使用處於已按下狀態之自訂控制項範本的按鈕  
  
 若要尋找 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 隨附之控制項的視覺狀態，請參閱[控制項的樣式和範本](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)。  
  
<a name="specifying_the_behavior_of_a_control_when_it_transitions_between_states"></a>   
## <a name="specifying-the-behavior-of-a-control-when-it-transitions-between-states"></a>指定控制項在狀態之間轉換時的行為  
 在上述範例中，在使用者按一下按鈕時，按鈕的外觀也會變更，但除非按下按鈕整整一秒，否則使用者並不會看到效果。 動畫預設要一秒鐘的時間才會產生。 因為使用者可能按一下又放開按鈕，在更短時間內，視覺回饋將不會有效，如果您離開<xref:System.Windows.Controls.ControlTemplate>處於預設狀態。  
  
 您可以指定發生順暢轉換從某個狀態到另一個控制項，加上動畫所花費的時間量<xref:System.Windows.VisualTransition>物件至<xref:System.Windows.Controls.ControlTemplate>。 當您建立<xref:System.Windows.VisualTransition>，您指定一或多個項目：  
  
-   狀態之間進行轉換所需的時間。  
  
-   在轉換時發生的其他控制項外觀變更。  
  
-   何種狀態<xref:System.Windows.VisualTransition>套用至。  
  
### <a name="specifying-the-duration-of-a-transition"></a>指定轉換的持續時間  
 您可以指定多久轉換會藉由設定<xref:System.Windows.VisualTransition.GeneratedDuration%2A>屬性。 上述範例具有<xref:System.Windows.VisualState>指定按鈕的框線變成透明的按下按鈕時，但動畫耗費太多時間會很明顯的如果快速地按下並釋放按鍵時。 您可以使用<xref:System.Windows.VisualTransition>至指定的時間花費控制項轉換為已按下的狀態。 下列範例會指定控制項需要 1/100 秒的時間來進入已按下狀態。  
  
 [!code-xaml[VSMButtonTemplate#PressedTransition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]  
  
### <a name="specifying-changes-to-the-controls-appearance-during-a-transition"></a>指定轉換時對控制項外觀造成的變更  
 <xref:System.Windows.VisualTransition>包含<xref:System.Windows.Media.Animation.Storyboard>開始時的控制項狀態之間轉換。 例如，您可以指定在控制項從 `MouseOver` 狀態轉換到 `Normal` 狀態時產生動畫。 下列範例會建立<xref:System.Windows.VisualTransition>，指定當使用者移動滑鼠指標離開 按鈕，按鈕的框線變更藍色、 再變成黃色，然後為黑色在 1.5 秒內。  
  
 [!code-xaml[VSMButtonTemplate#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]  
  
### <a name="specifying-when-a-visualtransition-is-applied"></a>指定套用 VisualTransition 的時機  
 A<xref:System.Windows.VisualTransition>可以限制套用至特定狀態，或它可以套用任何時候控制項之間的轉換狀態。 在上述範例中，<xref:System.Windows.VisualTransition>控制項將會從時，會套用`MouseOver`狀態`Normal`狀態; 在該範例之前，<xref:System.Windows.VisualTransition>時，才在控制項進入套用`Pressed`狀態。 您可以限制何時<xref:System.Windows.VisualTransition>藉由設定會套用<xref:System.Windows.VisualTransition.To%2A>和<xref:System.Windows.VisualTransition.From%2A>屬性。 下表說明限制的層級 (依最嚴格到最不嚴格的順序排列)。  
  
|限制的類型|來源的值|目標的值|  
|-------------------------|-------------------|-----------------|  
|從指定的狀態到另一個指定的狀態|名稱 <xref:System.Windows.VisualState>|名稱 <xref:System.Windows.VisualState>|  
|從任何狀態到指定的狀態|未設定|名稱 <xref:System.Windows.VisualState>|  
|從指定的狀態到任何狀態|名稱 <xref:System.Windows.VisualState>|未設定|  
|從任何狀態到任何其他狀態|未設定|未設定|  
  
 您可以有多個<xref:System.Windows.VisualTransition>中的物件<xref:System.Windows.VisualStateGroup>，參考相同的狀態，但它們將使用上表指定的順序。 在下列範例中，有兩個<xref:System.Windows.VisualTransition>物件。 當控制項從不`Pressed`狀態`MouseOver`狀態<xref:System.Windows.VisualTransition>，同時具有<xref:System.Windows.VisualTransition.From%2A>和<xref:System.Windows.VisualTransition.To%2A>集使用。 當控制項從不是 `Pressed` 的狀態轉換到 `MouseOver` 狀態時，則會使用另一個狀態。  
  
 [!code-xaml[VSMButtonTemplate#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]  
  
 <xref:System.Windows.VisualStateGroup>已經<xref:System.Windows.VisualStateGroup.Transitions%2A>屬性，其中包含<xref:System.Windows.VisualTransition>套用至物件<xref:System.Windows.VisualState>中的物件<xref:System.Windows.VisualStateGroup>。 作為<xref:System.Windows.Controls.ControlTemplate>作者，您可以自由地包含任何<xref:System.Windows.VisualTransition>想。 不過，如果<xref:System.Windows.VisualTransition.To%2A>並<xref:System.Windows.VisualTransition.From%2A>屬性會設為不是處於的狀態名稱<xref:System.Windows.VisualStateGroup>，則<xref:System.Windows.VisualTransition>會被忽略。  
  
 下列範例所示<xref:System.Windows.VisualStateGroup>針對`CommonStates`。 此範例會定義<xref:System.Windows.VisualTransition>針對每個按鈕的下列轉換。  
  
-   轉換到 `Pressed` 狀態。  
  
-   轉換到 `MouseOver` 狀態。  
  
-   從 `Pressed` 狀態轉換到 `MouseOver` 狀態。  
  
-   從 `MouseOver` 狀態轉換到 `Normal` 狀態。  
  
 [!code-xaml[VSMButtonTemplate#VisualTransitions](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]  
  
<a name="customizing_other_controls_by_understanding_the_control_contract"></a>   
## <a name="customizing-other-controls-by-understanding-the-control-contract"></a>透過了解控制項合約來自訂其他控制項  
 使用的控制項<xref:System.Windows.Controls.ControlTemplate>來指定其視覺結構 (利用<xref:System.Windows.FrameworkElement>物件) 與視覺行為 (藉由使用<xref:System.Windows.VisualState>物件) 會使用組件控制項模型。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 4 隨附的許多控制項都使用此模型。 組件，<xref:System.Windows.Controls.ControlTemplate>作者需要注意的透過控制項合約來溝通。 在您了解控制項合約的組件之後，即可自訂任何使用組件控制項模型之控制項的外觀。  
  
 控制項合約有三個元素：  
  
-   控制項邏輯所使用的視覺元素。  
  
-   控制項的狀態及每個狀態所屬的群組。  
  
-   在視覺上影響控制項的公用屬性。  
  
### <a name="visual-elements-in-the-control-contract"></a>控制項合約中的視覺元素  
 有時，控制項的邏輯互動<xref:System.Windows.FrameworkElement>位於<xref:System.Windows.Controls.ControlTemplate>。 例如，控制項可能會處理它其中一個元素的事件。 當控制項預期要尋找特定<xref:System.Windows.FrameworkElement>中<xref:System.Windows.Controls.ControlTemplate>，它必須該資訊傳達給<xref:System.Windows.Controls.ControlTemplate>作者。 控制項使用<xref:System.Windows.TemplatePartAttribute>來傳達所預期的項目和項目的名稱應該是類型。 <xref:System.Windows.Controls.Button>沒有<xref:System.Windows.FrameworkElement>中控制項合約，但其他控制項，例如組件<xref:System.Windows.Controls.ComboBox>，執行。  
  
 下列範例所示<xref:System.Windows.TemplatePartAttribute>物件上指定<xref:System.Windows.Controls.ComboBox>類別。 邏輯<xref:System.Windows.Controls.ComboBox>預期會找到<xref:System.Windows.Controls.TextBox>名為`PART_EditableTextBox`並<xref:System.Windows.Controls.Primitives.Popup>名為`PART_Popup`在其<xref:System.Windows.Controls.ControlTemplate>。  
  
 [!code-csharp[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]  
  
 下列範例示範簡化<xref:System.Windows.Controls.ControlTemplate>for<xref:System.Windows.Controls.ComboBox>包含所指定的項目<xref:System.Windows.TemplatePartAttribute>物件上<xref:System.Windows.Controls.ComboBox>類別。  
  
 [!code-xaml[VSMButtonTemplate#ComboBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]  
  
### <a name="states-in-the-control-contract"></a>控制項合約中的狀態  
 控制項的狀態也是控制項合約的一部分。 建立的範例<xref:System.Windows.Controls.ControlTemplate>for<xref:System.Windows.Controls.Button>示範如何指定的外觀<xref:System.Windows.Controls.Button>根據其狀態。 您建立<xref:System.Windows.VisualState>每個指定的狀態，並讓所有<xref:System.Windows.VisualState>物件共用<xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A>中<xref:System.Windows.VisualStateGroup>所述，在[變更外觀的控制項根據其狀態](#changing_the_appearance_of_a_control_depending_on_its_state)稍早在此主題。 協力廠商控制項應該使用指定的狀態<xref:System.Windows.TemplateVisualStateAttribute>，這可讓設計工具，例如 Expression Blend，來公開控制項的狀態以供撰寫控制項範本。  
  
 若要尋找 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 隨附之控制項的控制項合約，請參閱[控制項的樣式和範本](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)。  
  
### <a name="properties-in-the-control-contract"></a>控制項合約中的屬性  
 在視覺上影響控制項的公用屬性也包含在控制項合約中。 您可以設定這些屬性來變更控制項的外觀，而不需要建立新<xref:System.Windows.Controls.ControlTemplate>。 您也可以使用[TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)屬性中的項目繫結標記延伸<xref:System.Windows.Controls.ControlTemplate>所定義的公用屬性<xref:System.Windows.Controls.Button>。  
  
 下列範例示範按鈕的控制項合約。  
  
 [!code-csharp[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]  
  
 建立時<xref:System.Windows.Controls.ControlTemplate>，通常是最簡單的方式開始與現有<xref:System.Windows.Controls.ControlTemplate>並對它進行變更。 您可以執行下列動作，以變更現有的其中一項<xref:System.Windows.Controls.ControlTemplate>:  
  
-   使用設計工具 (例如 Expression Blend)，這會提供可用來建立控制項範本的圖形化使用者介面。 如需詳細資訊，請參閱[設定支援範本之控制項的樣式](https://go.microsoft.com/fwlink/?LinkId=161153)。  
  
-   取得預設<xref:System.Windows.Controls.ControlTemplate>並加以編輯。 若要尋找 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 隨附的預設控制項範本，請參閱[預設 WPF 佈景主題](https://go.microsoft.com/fwlink/?LinkID=158252)。  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>完整範例  
 下列範例示範完整<xref:System.Windows.Controls.Button><xref:System.Windows.Controls.ControlTemplate>本主題中所討論。  
  
 [!code-xaml[VSMButtonTemplate#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]  
  
## <a name="see-also"></a>另請參閱
- [樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)
