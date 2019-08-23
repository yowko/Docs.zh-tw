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
ms.openlocfilehash: 63a0b724b71c4a4901c2dedcf502045a75ec405c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933723"
---
# <a name="customizing-the-appearance-of-an-existing-control-by-creating-a-controltemplate"></a>透過建立 ControlTemplate 自訂現有控制項的外觀
<a name="introduction"></a>會<xref:System.Windows.Controls.ControlTemplate>指定控制項的視覺化結構和視覺行為。 您可以藉由提供新<xref:System.Windows.Controls.ControlTemplate>的來自訂控制項的外觀。 當您建立<xref:System.Windows.Controls.ControlTemplate>時, 您可以取代現有控制項的外觀, 而不需要變更其功能。 例如, 您可以將應用程式中的按鈕改成四捨五入, 而不是預設的方形圖形, 但是按鈕仍然會<xref:System.Windows.Controls.Primitives.ButtonBase.Click>引發事件。  
  
 本主題說明的各個部分<xref:System.Windows.Controls.ControlTemplate>, 示範如何建立的簡單<xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button>, 並說明如何瞭解控制項的控制項合約, 讓您可以自訂其外觀。 因為您<xref:System.Windows.Controls.ControlTemplate>在中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]建立, 所以可以變更控制項的外觀, 而不需要撰寫任何程式碼。 您也可以使用設計工具 (例如 Microsoft Expression Blend) 來建立自訂控制項樣板。 本主題顯示中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]的範例, 可自訂的外觀<xref:System.Windows.Controls.Button> , 並列出主題結尾的完整範例。 如需有關使用 Expression Blend 的詳細資訊，請參閱[設定支援範本之控制項的樣式](https://go.microsoft.com/fwlink/?LinkId=161153)。  
  
 下圖顯示<xref:System.Windows.Controls.Button>使用本主題中所<xref:System.Windows.Controls.ControlTemplate>建立之的。  
  
 ![具有自訂控制項範本的按鈕。](./media/ndp-buttonnormal.png "NDP_ButtonNormal")  
使用自訂控制項範本的按鈕  
  
 ![具有紅色框線的按鈕。](./media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
使用自訂控制項範本且滑鼠指標移至其上方的按鈕  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 本主題假設您了解如何建立和使用控制項與樣式，如[控制項](index.md)所述。 本主題所討論的概念適用于繼承自<xref:System.Windows.Controls.Control>類別的元素, 但除外。 <xref:System.Windows.Controls.UserControl> 您無法將<xref:System.Windows.Controls.ControlTemplate>套用<xref:System.Windows.Controls.UserControl>至。  
  
<a name="when_you_should_create_a_controltemplate"></a>   
## <a name="when-you-should-create-a-controltemplate"></a>建立 ControlTemplate 的適當時機  
 控制項有許多屬性 (例如<xref:System.Windows.Controls.Border.Background%2A>、 <xref:System.Windows.Controls.Control.Foreground%2A>和<xref:System.Windows.Controls.Control.FontFamily%2A>), 您可以設定來指定控制面板的不同層面, 但是您可以藉由設定這些屬性所做的變更會受到限制。 例如, 您可以將<xref:System.Windows.Controls.Control.Foreground%2A>屬性設定為藍色, 並<xref:System.Windows.Controls.Control.FontStyle%2A>將設為斜體。 <xref:System.Windows.Controls.CheckBox>  
  
 如果沒有建立新<xref:System.Windows.Controls.ControlTemplate>的 for 控制項, 則每個[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式中的所有控制項都有相同的一般外觀, 這會限制以自訂外觀和風格建立應用程式的能力。 根據預設, 每<xref:System.Windows.Controls.CheckBox>個都有類似的特性。 例如, 的內容<xref:System.Windows.Controls.CheckBox>一律會在選取範圍指標的右邊, 而核取記號一律用來表示<xref:System.Windows.Controls.CheckBox>已選取。  
  
 <xref:System.Windows.Controls.ControlTemplate>當您想要自訂控制項的外觀, 而不是控制項的其他屬性設定時, 您會建立。 在的範例<xref:System.Windows.Controls.CheckBox>中, 假設您希望核取方塊的內容位於選取範圍指標上方, 而且您想要 X 表示<xref:System.Windows.Controls.CheckBox>已選取。 您可以在的中<xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.CheckBox>指定這些變更。  
  
 下圖顯示<xref:System.Windows.Controls.CheckBox>使用預設值<xref:System.Windows.Controls.ControlTemplate>的。  
  
 ![具有預設控制項範本的核取方塊。](./media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
使用預設控制項範本的 CheckBox  
  
 下圖顯示<xref:System.Windows.Controls.CheckBox>的會使用自訂<xref:System.Windows.Controls.ControlTemplate>將的內容<xref:System.Windows.Controls.CheckBox>放在<xref:System.Windows.Controls.CheckBox>選取指標上方, 並在選取時顯示 X。  
  
 ![包含自訂控制項範本的核取方塊。](./media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
使用自訂控制項範本的 CheckBox  
  
 這個範例<xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button>中的是相當複雜的, 因此本主題會使用為建立的較簡單範例。 <xref:System.Windows.Controls.CheckBox> <xref:System.Windows.Controls.ControlTemplate>  
  
<a name="changing_the_visual_structure_of_a_control"></a>   
## <a name="changing-the-visual-structure-of-a-control"></a>變更控制項的視覺結構  
 在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中, 控制項通常是複合<xref:System.Windows.FrameworkElement>物件。 當您建立<xref:System.Windows.Controls.ControlTemplate>時, 會結合<xref:System.Windows.FrameworkElement>物件來建立單一控制項。 必須只有一個<xref:System.Windows.FrameworkElement>做為其根項目。 <xref:System.Windows.Controls.ControlTemplate> 根項目通常包含其他<xref:System.Windows.FrameworkElement>物件。 這些物件的組合會構成控制項的視覺結構。  
  
 下列範例會建立的自<xref:System.Windows.Controls.ControlTemplate>定義<xref:System.Windows.Controls.Button>。 會建立的視覺化結構<xref:System.Windows.Controls.Button>。 <xref:System.Windows.Controls.ControlTemplate> 此範例並不會變更您將滑鼠指標移至按鈕上或按一下按鈕時的按鈕外觀。 變更按鈕處於不同狀態時的外觀將在本主題稍後討論。  
  
 在此範例中，視覺結構是由下列部分所組成：  
  
- 名為的, 作為範本的根<xref:System.Windows.FrameworkElement>。 <xref:System.Windows.Controls.Border> `RootElement`  
  
- , 其為的`RootElement`子系。 <xref:System.Windows.Controls.Grid>  
  
- <xref:System.Windows.Controls.ContentPresenter> , 會顯示按鈕的內容。 <xref:System.Windows.Controls.ContentPresenter>可顯示任何類型的物件。  
  
 [!code-xaml[VSMButtonTemplate#BasicTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]  
  
### <a name="preserving-the-functionality-of-a-controls-properties-by-using-templatebinding"></a>使用 TemplateBinding 來保留控制項屬性的功能  
 當您建立新<xref:System.Windows.Controls.ControlTemplate>的時, 您仍可能想要使用公用屬性來變更控制項的外觀。 [TemplateBinding](../advanced/templatebinding-markup-extension.md)標記延伸會將位於的<xref:System.Windows.Controls.ControlTemplate>專案屬性系結至控制項所定義的公用屬性。 當您使用 [TemplateBinding](../advanced/templatebinding-markup-extension.md) 時，會讓控制項上的屬性能夠作為範本的參數。 也就是說，已設定控制項上的屬性時，該值會傳遞給具有 [TemplateBinding](../advanced/templatebinding-markup-extension.md) 的元素。  
  
 下列範例會重複上述範例中使用[TemplateBinding](../advanced/templatebinding-markup-extension.md)標記延伸的部分, 以將中<xref:System.Windows.Controls.ControlTemplate>的專案屬性系結至按鈕所定義的公用屬性。  
  
 [!code-xaml[VSMButtonTemplate#TemplateBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]  
  
 在此範例中, <xref:System.Windows.Controls.Grid>的<xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType>屬性範本系結至<xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>。 因為<xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType>是範本系結, 所以您可以建立多個使用相同<xref:System.Windows.Controls.ControlTemplate>的按鈕, <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>並將設定為每個按鈕上的不同值。 如果<xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>不是系結至<xref:System.Windows.Controls.ControlTemplate>中專案之屬性的範本, 設定<xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>按鈕的就不會影響按鈕的外觀。  
  
 請注意，兩個屬性的名稱不一定要相同。 在上述<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType>範例中, 的屬性<xref:System.Windows.Controls.Button> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>是系結<xref:System.Windows.Controls.ContentPresenter>至之屬性的範本。 這可讓您以水平方式置放按鈕的內容。 <xref:System.Windows.Controls.ContentPresenter>沒有名為`HorizontalContentAlignment`的屬性, 但<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType>可以系結至<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>。 當您的範本繫結某個屬性時，請確定目標與來源屬性是相同類型。  
  
 <xref:System.Windows.Controls.Control>類別會定義數個屬性, 控制項範本必須使用這些屬性, 才能在設定時對控制項產生影響。 <xref:System.Windows.Controls.ControlTemplate>如何使用屬性取決於屬性。 <xref:System.Windows.Controls.ControlTemplate>必須以下列其中一種方式使用屬性:  
  
- <xref:System.Windows.Controls.ControlTemplate>範本中的元素會系結至屬性。  
  
- 中<xref:System.Windows.Controls.ControlTemplate>的元素會從父系<xref:System.Windows.FrameworkElement>繼承屬性。  
  
 下表列出控制項從<xref:System.Windows.Controls.Control>類別繼承而來的視覺屬性。 它同時也指出控制項的預設控制項範本是否使用繼承的屬性值，或是否必須以範本方式繫結。  
  
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
  
 資料表只會列出繼承自<xref:System.Windows.Controls.Control>類別的視覺屬性。 除了表格中列出的屬性之外, 控制項也可以從父 framework 元素<xref:System.Windows.FrameworkElement.DataContext%2A>繼承<xref:System.Windows.FrameworkElement.Language%2A>、和<xref:System.Windows.Controls.TextBlock.TextDecorations%2A>屬性。  
  
 <xref:System.Windows.Controls.ContentPresenter>此外, 如果位於<xref:System.Windows.Controls.ControlTemplate>的<xref:System.Windows.Controls.ContentControl> <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> , <xref:System.Windows.Controls.ContentPresenter>將會自動系結至和<xref:System.Windows.Controls.ContentControl.Content%2A>屬性。 同樣地, <xref:System.Windows.Controls.ItemsPresenter> <xref:System.Windows.Controls.ControlTemplate>在的<xref:System.Windows.Controls.ItemsControl>中, 會自動系結至<xref:System.Windows.Controls.ItemsControl.Items%2A>和<xref:System.Windows.Controls.ItemsPresenter>屬性。  
  
 下列範例會建立兩個按鈕, 使用<xref:System.Windows.Controls.ControlTemplate>上述範例中所定義的。 此範例會在<xref:System.Windows.Controls.Control.Background%2A>每<xref:System.Windows.Controls.Control.Foreground%2A>個按鈕<xref:System.Windows.Controls.Control.FontSize%2A>上設定、和屬性。 設定屬性有效果, 因為它是在中系結的<xref:System.Windows.Controls.ControlTemplate>範本。 <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Control.Foreground%2A>雖然和<xref:System.Windows.Controls.Control.FontSize%2A>屬性不是範本系結, 但設定它們會有效果, 因為它們的值會被繼承。  
  
 [!code-xaml[VSMButtonTemplate#ButtonDeclaration](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]  
  
 上述範例會產生類似下圖的輸出。  
  
 ![兩個按鈕: 一個藍色和一個紫色。](./media/ndp-buttontwo.png "NDP_ButtonTwo")  
兩個具有不同背景色彩的按鈕  
  
<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>   
## <a name="changing-the-appearance-of-a-control-depending-on-its-state"></a>依控制項的狀態變更其外觀  
 具有預設外觀的按鈕與上述範例中按鈕之間的差異在於，預設按鈕在處於不同狀態時會稍微變更。 例如，預設按鈕會在使用者按下按鈕時，或當滑鼠指標移至按鈕上時，變更外觀。 雖然不<xref:System.Windows.Controls.ControlTemplate>會變更控制項的功能, 但它確實會變更控制項的視覺行為。 視覺行為會描述控制項處於特定狀態時的外觀。 若要了解控制項的功能與視覺行為之間有何差異，請思考一下按鈕範例。 按鈕的功能是在按一下時引發<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件, 但按鈕的視覺效果行為是在指向或按下時變更其外觀。  
  
 當控制項<xref:System.Windows.VisualState>處於特定狀態時, 您可以使用物件來指定控制項的外觀。 包含, 它會變更中的<xref:System.Windows.Controls.ControlTemplate>元素外觀。 <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.VisualState> 您不需要撰寫任何程式碼來進行這項操作, 因為控制項的邏輯會藉由使用<xref:System.Windows.VisualStateManager>來變更狀態。 當控制項進入<xref:System.Windows.VisualState.Name%2A?displayProperty=nameWithType>屬性所指定的狀態時<xref:System.Windows.Media.Animation.Storyboard> , 就會開始。 當控制項離開狀態時, <xref:System.Windows.Media.Animation.Storyboard>就會停止。  
  
 下列範例會顯示<xref:System.Windows.VisualState> , <xref:System.Windows.Controls.Button>當滑鼠指標停留在其上方時, 會變更的外觀。 會藉由變更的色彩`BorderBrush`來變更按鈕的框線色彩。<xref:System.Windows.Media.Animation.Storyboard> 如果您<xref:System.Windows.Controls.ControlTemplate>參考本主題開頭的範例, 您會<xref:System.Windows.Media.SolidColorBrush> `BorderBrush`回想一下, 是指派給<xref:System.Windows.Controls.Border.Background%2A>之<xref:System.Windows.Controls.Border>的名稱。  
  
 [!code-xaml[VSMButtonTemplate#4](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#4)]  
  
 控制項需負責在定義其控制項合約時一併定義狀態，本主題稍後的[透過了解控制項合約來自訂其他控制項](#customizing_other_controls_by_understanding_the_control_contract)中會詳細討論。 下表列出針對<xref:System.Windows.Controls.Button>指定的狀態。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|----------------------|---------------------------|-----------------|  
|一般|CommonStates|預設狀態。|  
|MouseOver|CommonStates|滑鼠指標移到控制項上。|  
|按下|CommonStates|已按下控制項。|  
|已停用|CommonStates|已停用控制項。|  
|已取得焦點|FocusStates|控制項已取得焦點。|  
|未取得焦點|FocusStates|控制項未取得焦點。|  
  
 `Pressed` `Normal` `CommonStates` `MouseOver`會定義兩個狀態群組: 群組包含、、和`Disabled`狀態。 <xref:System.Windows.Controls.Button> `FocusStates` 群組則包含 `Focused` 和 `Unfocused` 狀態。 相同狀態群組中的狀態彼此互斥。 控制項就每一群組而言一律僅限處於一種狀態。 例如, <xref:System.Windows.Controls.Button>即使滑鼠指標不在其上, 也可以有焦點, 因此`Focused`狀態中的<xref:System.Windows.Controls.Button>可以是`MouseOver`、 `Pressed`或`Normal`狀態。  
  
 您要<xref:System.Windows.VisualState>將物件<xref:System.Windows.VisualStateGroup>新增至物件。 您可以<xref:System.Windows.VisualStateGroup>將物件加入<xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType>至附加屬性。 下列範例<xref:System.Windows.VisualState>會定義`Normal`、 `MouseOver`和`Pressed`狀態的物件, 這些都是在群組中。`CommonStates` <xref:System.Windows.VisualState.Name%2A> 各自<xref:System.Windows.VisualState>的會符合上表中的名稱。 為了簡化範例，已省略 `Disabled` 狀態及`FocusStates` 群組中的狀態，但在本主題結尾的完整範例中已將它們都包含在內。  
  
> [!NOTE]
> 請務必在的根目錄<xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> <xref:System.Windows.FrameworkElement> <xref:System.Windows.Controls.ControlTemplate>上設定附加屬性。  
  
 [!code-xaml[VSMButtonTemplate#VisualStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualstates)]  
  
 上述範例會產生類似下列圖例的輸出。  
  
 ![具有自訂控制項範本的按鈕。](./media/ndp-buttonnormal.png "NDP_ButtonNormal")  
使用處於正常狀態之自訂控制項範本的按鈕  
  
 ![具有紅色框線的按鈕。](./media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
使用處於滑鼠移至上方狀態之自訂控制項範本的按鈕  
  
 ![框線在按下的按鈕上是透明的。](./media/ndp-buttonpressed.png "NDP_ButtonPressed")  
使用處於已按下狀態之自訂控制項範本的按鈕  
  
 若要尋找 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 隨附之控制項的視覺狀態，請參閱[控制項的樣式和範本](control-styles-and-templates.md)。  
  
<a name="specifying_the_behavior_of_a_control_when_it_transitions_between_states"></a>   
## <a name="specifying-the-behavior-of-a-control-when-it-transitions-between-states"></a>指定控制項在狀態之間轉換時的行為  
 在上述範例中，在使用者按一下按鈕時，按鈕的外觀也會變更，但除非按下按鈕整整一秒，否則使用者並不會看到效果。 動畫預設要一秒鐘的時間才會產生。 由於使用者可能會在很短的時間內按一下並放開按鈕, 因此如果您讓<xref:System.Windows.Controls.ControlTemplate>處於預設狀態, 視覺效果的意見反應將無法生效。  
  
 您可以將物件加入<xref:System.Windows.VisualTransition> <xref:System.Windows.Controls.ControlTemplate>至, 以指定動畫發生的時間量, 以順利地將控制項從某個狀態轉換成另一個狀態。 當您建立<xref:System.Windows.VisualTransition>時, 您可以指定下列一或多個動作:  
  
- 狀態之間進行轉換所需的時間。  
  
- 在轉換時發生的其他控制項外觀變更。  
  
- 適用于的<xref:System.Windows.VisualTransition>狀態。  
  
### <a name="specifying-the-duration-of-a-transition"></a>指定轉換的持續時間  
 您可以藉由設定<xref:System.Windows.VisualTransition.GeneratedDuration%2A>屬性來指定轉換所需的時間長度。 先前的範例具有<xref:System.Windows.VisualState> , 其指定按鈕的框線會在按下按鈕時變成透明的, 但如果按鈕快速按下並放開, 動畫會花太長的時間才會明顯。 您可以使用<xref:System.Windows.VisualTransition>來指定控制項轉換為按下狀態所需的時間量。 下列範例會指定控制項需要 1/100 秒的時間來進入已按下狀態。  
  
 [!code-xaml[VSMButtonTemplate#PressedTransition](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]  
  
### <a name="specifying-changes-to-the-controls-appearance-during-a-transition"></a>指定轉換時對控制項外觀造成的變更  
 <xref:System.Windows.VisualTransition> 包含,它會在控制項在狀態<xref:System.Windows.Media.Animation.Storyboard>之間轉換時開始。 例如，您可以指定在控制項從 `MouseOver` 狀態轉換到 `Normal` 狀態時產生動畫。 下列範例<xref:System.Windows.VisualTransition>會建立, 指定當使用者將滑鼠指標移開按鈕時, 按鈕的框線會變更為藍色, 然後變成黃色, 而在1.5 秒中則為黑色。  
  
 [!code-xaml[VSMButtonTemplate#8](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]  
  
### <a name="specifying-when-a-visualtransition-is-applied"></a>指定套用 VisualTransition 的時機  
 <xref:System.Windows.VisualTransition>可以限制為只套用至特定狀態, 或可在控制項于狀態之間轉換時套用。 在上述範例中, 當<xref:System.Windows.VisualTransition>控制項`MouseOver`從狀態`Normal`變成狀態時, 會套用, 在這之前的範例中, <xref:System.Windows.VisualTransition>會在控制項進入`Pressed`狀態時套用。 藉由<xref:System.Windows.VisualTransition> <xref:System.Windows.VisualTransition.To%2A>設定和<xref:System.Windows.VisualTransition.From%2A>屬性, 您可以限制套用的時機。 下表說明限制的層級 (依最嚴格到最不嚴格的順序排列)。  
  
|限制的類型|來源的值|目標的值|  
|-------------------------|-------------------|-----------------|  
|從指定的狀態到另一個指定的狀態|的名稱<xref:System.Windows.VisualState>|的名稱<xref:System.Windows.VisualState>|  
|從任何狀態到指定的狀態|未設定|的名稱<xref:System.Windows.VisualState>|  
|從指定的狀態到任何狀態|的名稱<xref:System.Windows.VisualState>|未設定|  
|從任何狀態到任何其他狀態|未設定|未設定|  
  
 在中<xref:System.Windows.VisualTransition>,您可以有多個參考相同狀態的物件, 但它們將會依照上一個資料表指定的順序來使用。 <xref:System.Windows.VisualStateGroup> 在下列範例中, 有兩個<xref:System.Windows.VisualTransition>物件。 當控制項從`Pressed`狀態<xref:System.Windows.VisualTransition.To%2A>轉換`MouseOver`到狀態時, 會使用同時<xref:System.Windows.VisualTransition> <xref:System.Windows.VisualTransition.From%2A>具有和設定的。 當控制項從不是 `Pressed` 的狀態轉換到 `MouseOver` 狀態時，則會使用另一個狀態。  
  
 [!code-xaml[VSMButtonTemplate#7](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]  
  
 <xref:System.Windows.VisualTransition> <xref:System.Windows.VisualStateGroup> <xref:System.Windows.VisualState>具有屬性, 其中包含適用于中之物件的物件。 <xref:System.Windows.VisualStateGroup.Transitions%2A> <xref:System.Windows.VisualStateGroup> 身為<xref:System.Windows.Controls.ControlTemplate>作者, 您可以隨意包含任何<xref:System.Windows.VisualTransition>您想要的。 不過, 如果<xref:System.Windows.VisualTransition.To%2A>和<xref:System.Windows.VisualTransition.From%2A>屬性設定為<xref:System.Windows.VisualTransition>不在中<xref:System.Windows.VisualStateGroup>的狀態名稱, 則會忽略。  
  
 下列範例會顯示<xref:System.Windows.VisualStateGroup> `CommonStates`的。 此範例會<xref:System.Windows.VisualTransition>針對每個按鈕的下列轉換定義。  
  
- 轉換到 `Pressed` 狀態。  
  
- 轉換到 `MouseOver` 狀態。  
  
- 從 `Pressed` 狀態轉換到 `MouseOver` 狀態。  
  
- 從 `MouseOver` 狀態轉換到 `Normal` 狀態。  
  
 [!code-xaml[VSMButtonTemplate#VisualTransitions](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]  
  
<a name="customizing_other_controls_by_understanding_the_control_contract"></a>   
## <a name="customizing-other-controls-by-understanding-the-control-contract"></a>透過了解控制項合約來自訂其他控制項  
 使用<xref:System.Windows.Controls.ControlTemplate>來指定其視覺化結構 (藉由使用<xref:System.Windows.FrameworkElement>物件) 和視覺行為 (藉由使用<xref:System.Windows.VisualState>物件) 的控制項會使用元件控制項模型。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 4 隨附的許多控制項都使用此模型。 <xref:System.Windows.Controls.ControlTemplate>作者必須注意的部分會透過控制合約進行通訊。 在您了解控制項合約的組件之後，即可自訂任何使用組件控制項模型之控制項的外觀。  
  
 控制項合約有三個元素：  
  
- 控制項邏輯所使用的視覺元素。  
  
- 控制項的狀態及每個狀態所屬的群組。  
  
- 在視覺上影響控制項的公用屬性。  
  
### <a name="visual-elements-in-the-control-contract"></a>控制項合約中的視覺元素  
 有時候, 控制項的邏輯會與<xref:System.Windows.FrameworkElement>位於<xref:System.Windows.Controls.ControlTemplate>中的進行互動。 例如，控制項可能會處理它其中一個元素的事件。 當控制項預期<xref:System.Windows.FrameworkElement> <xref:System.Windows.Controls.ControlTemplate>在中找到特定的時, 必須將該資訊<xref:System.Windows.Controls.ControlTemplate>傳達給作者。 控制項會使用<xref:System.Windows.TemplatePartAttribute>來傳達預期的專案類型, 以及元素的名稱。 在<xref:System.Windows.Controls.Button>其控制項合約<xref:System.Windows.FrameworkElement>中沒有部分, 而其他<xref:System.Windows.Controls.ComboBox>控制項 (例如) 則會這麼做。  
  
 下列範例顯示<xref:System.Windows.TemplatePartAttribute>在<xref:System.Windows.Controls.ComboBox>類別上指定的物件。 的<xref:System.Windows.Controls.ComboBox>邏輯預期會在其`PART_Popup` `PART_EditableTextBox` <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.TextBox> 中尋找<xref:System.Windows.Controls.ControlTemplate>名為的和名為的。  
  
 [!code-csharp[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]  
  
 <xref:System.Windows.Controls.ControlTemplate>下列範例顯示的<xref:System.Windows.Controls.ComboBox>簡化, 其中包含<xref:System.Windows.Controls.ComboBox>類別上的<xref:System.Windows.TemplatePartAttribute>物件所指定的專案。  
  
 [!code-xaml[VSMButtonTemplate#ComboBoxTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]  
  
### <a name="states-in-the-control-contract"></a>控制項合約中的狀態  
 控制項的狀態也是控制項合約的一部分。 建立<xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button>的範例說明如何根據其狀態來指定的外觀。 <xref:System.Windows.Controls.Button> 您<xref:System.Windows.VisualState>會針對每個指定的狀態建立, <xref:System.Windows.VisualState>並將共用的<xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A>所有物件<xref:System.Windows.VisualStateGroup>放入中, 如根據本主題稍早的[狀態變更控制項的外觀](#changing_the_appearance_of_a_control_depending_on_its_state)中所述。 協力廠商控制項應該使用<xref:System.Windows.TemplateVisualStateAttribute>來指定狀態, 這可讓設計工具 (例如 Expression Blend) 公開控制項的撰寫控制項範本狀態。  
  
 若要尋找 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 隨附之控制項的控制項合約，請參閱[控制項的樣式和範本](control-styles-and-templates.md)。  
  
### <a name="properties-in-the-control-contract"></a>控制項合約中的屬性  
 在視覺上影響控制項的公用屬性也包含在控制項合約中。 您可以設定這些屬性來變更控制項的外觀, 而不需要建立新<xref:System.Windows.Controls.ControlTemplate>的。 您也可以使用[TemplateBinding](../advanced/templatebinding-markup-extension.md)標記延伸, 將中的<xref:System.Windows.Controls.ControlTemplate>專案屬性系結至所定義<xref:System.Windows.Controls.Button>的公用屬性。  
  
 下列範例示範按鈕的控制項合約。  
  
 [!code-csharp[VSMButtonTemplate#ButtonContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]  
  
 建立<xref:System.Windows.Controls.ControlTemplate>時, 通常會最簡單的方式是從現有<xref:System.Windows.Controls.ControlTemplate>的開始, 並對其進行變更。 您可以執行下列其中一項動作來變更現有<xref:System.Windows.Controls.ControlTemplate>的:  
  
- 使用設計工具 (例如 Expression Blend)，這會提供可用來建立控制項範本的圖形化使用者介面。 如需詳細資訊，請參閱[設定支援範本之控制項的樣式](https://go.microsoft.com/fwlink/?LinkId=161153)。  
  
- 取得預設值<xref:System.Windows.Controls.ControlTemplate>並加以編輯。 若要尋找 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 隨附的預設控制項範本，請參閱[預設 WPF 佈景主題](https://go.microsoft.com/fwlink/?LinkID=158252)。  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>完整範例  
 下列範例會顯示本主題<xref:System.Windows.Controls.Button>中討論的完整<xref:System.Windows.Controls.ControlTemplate> 。  
  
 [!code-xaml[VSMButtonTemplate#3](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]  
  
## <a name="see-also"></a>另請參閱

- [樣式設定和範本化](styling-and-templating.md)
