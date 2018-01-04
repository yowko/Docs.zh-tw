---
title: "透過建立 ControlTemplate 自訂現有控制項的外觀"
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
- control contract [WPF]
- controls [WPF], visual structure changes
- ControlTemplate [WPF], customizing for existing controls
- skinning controls [WPF]
- controls [WPF], appearance specified by state
- templates [WPF], custom for existing controls
ms.assetid: 678dd116-43a2-4b8c-82b5-6b826f126e31
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0019b739c794cbffa62b49749371c2a19f752267
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-the-appearance-of-an-existing-control-by-creating-a-controltemplate"></a>透過建立 ControlTemplate 自訂現有控制項的外觀
<a name="introduction"></a>A<xref:System.Windows.Controls.ControlTemplate>指定的視覺化結構和控制項的視覺行為。 您可以自訂控制項的外觀，提供新的 it <xref:System.Windows.Controls.ControlTemplate>。 當您建立<xref:System.Windows.Controls.ControlTemplate>，您不需要變更它的功能取代現有的控制項的外觀。 例如，您可以讓按鈕在您的應用程式而不是預設的方形，round，但仍會引發按鈕<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。  
  
 本主題說明不同的部分<xref:System.Windows.Controls.ControlTemplate>，示範如何建立簡單<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.Button>，並說明如何了解控制項的控制項合約，可讓您可以自訂其外觀。 因為您建立<xref:System.Windows.Controls.ControlTemplate>中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您可以變更控制項的外觀，而不需要撰寫任何程式碼。 您也可以使用設計工具 (例如 Microsoft Expression Blend) 來建立自訂控制項樣板。 本主題說明中的範例[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，自訂的外觀<xref:System.Windows.Controls.Button>，並列出完整的範例，本主題的結尾。 如需有關使用 Expression Blend 的詳細資訊，請參閱[設定支援範本之控制項的樣式](http://go.microsoft.com/fwlink/?LinkId=161153)。  
  
 下列圖例顯示<xref:System.Windows.Controls.Button>使用<xref:System.Windows.Controls.ControlTemplate>本主題中所建立。  
  
 ![具有自訂控制項範本的按鈕。] (../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP_ButtonNormal")  
使用自訂控制項範本的按鈕  
  
 ![具有紅色框線的按鈕。] (../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
使用自訂控制項範本且滑鼠指標移至其上方的按鈕  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 本主題假設您了解如何建立和使用控制項與樣式，如[控制項](../../../../docs/framework/wpf/controls/index.md)所述。 本主題所討論的概念適用於項目繼承自<xref:System.Windows.Controls.Control>類別，除了<xref:System.Windows.Controls.UserControl>。 您不能套用<xref:System.Windows.Controls.ControlTemplate>至<xref:System.Windows.Controls.UserControl>。  
  
<a name="when_you_should_create_a_controltemplate"></a>   
## <a name="when-you-should-create-a-controltemplate"></a>建立 ControlTemplate 的適當時機  
 控制項具有許多屬性，例如<xref:System.Windows.Controls.Border.Background%2A>， <xref:System.Windows.Controls.Control.Foreground%2A>，和<xref:System.Windows.Controls.Control.FontFamily%2A>，您可以設定為指定的控制項的外觀，不同層面，但您可以藉由設定這些屬性進行的變更會受到限制。 例如，您可以設定<xref:System.Windows.Controls.Control.Foreground%2A>為藍色的屬性和<xref:System.Windows.Controls.Control.FontStyle%2A>上為斜體<xref:System.Windows.Controls.CheckBox>。  
  
 無法建立新<xref:System.Windows.Controls.ControlTemplate>所有控制項中的控制項，每個[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-應用程式會具有相同的一般外觀，這會限制建立應用程式使用自訂的外觀及操作的能力。 根據預設，每個<xref:System.Windows.Controls.CheckBox>具有類似特性。 比方說，內容<xref:System.Windows.Controls.CheckBox>永遠是右邊的 選取指標，並核取記號，一律會用來指出<xref:System.Windows.Controls.CheckBox>已選取。  
  
 您建立<xref:System.Windows.Controls.ControlTemplate>當您想要自訂控制項的外觀，超過在控制項上哪些設定其他屬性將會執行。 在範例中的<xref:System.Windows.Controls.CheckBox>，假設您想要選擇指示器上方 核取方塊內容，而且您想以指出 X<xref:System.Windows.Controls.CheckBox>已選取。 您指定這些變更的<xref:System.Windows.Controls.ControlTemplate>的<xref:System.Windows.Controls.CheckBox>。  
  
 下圖顯示<xref:System.Windows.Controls.CheckBox>，會使用預設<xref:System.Windows.Controls.ControlTemplate>。  
  
 ![核取方塊具有預設控制項範本。] (../../../../docs/framework/wpf/controls/media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
使用預設控制項範本的 CheckBox  
  
 下圖顯示<xref:System.Windows.Controls.CheckBox>使用自訂<xref:System.Windows.Controls.ControlTemplate>放置內容<xref:System.Windows.Controls.CheckBox>上方選取指標，並顯示 X 時<xref:System.Windows.Controls.CheckBox>已選取。  
  
 ![核取方塊具有自訂控制項範本。] (../../../../docs/framework/wpf/controls/media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
使用自訂控制項範本的 CheckBox  
  
 <xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.CheckBox>在這個範例是相當複雜，因此本主題會使用建立的簡單範例<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.Button>。  
  
<a name="changing_the_visual_structure_of_a_control"></a>   
## <a name="changing-the-visual-structure-of-a-control"></a>變更控制項的視覺結構  
 在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，控制項通常是複合<xref:System.Windows.FrameworkElement>物件。 當您建立<xref:System.Windows.Controls.ControlTemplate>，您將合併<xref:System.Windows.FrameworkElement>物件來建立單一的控制項。 A<xref:System.Windows.Controls.ControlTemplate>只能有一個<xref:System.Windows.FrameworkElement>為根元素。 根項目通常會包含其他<xref:System.Windows.FrameworkElement>物件。 這些物件的組合會構成控制項的視覺結構。  
  
 下列範例會建立自訂<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.Button>。 <xref:System.Windows.Controls.ControlTemplate>建立的視覺化結構<xref:System.Windows.Controls.Button>。 此範例並不會變更您將滑鼠指標移至按鈕上或按一下按鈕時的按鈕外觀。 變更按鈕處於不同狀態時的外觀將在本主題稍後討論。  
  
 在此範例中，視覺結構是由下列部分所組成：  
  
-   A<xref:System.Windows.Controls.Border>名為`RootElement`做為範本的根<xref:System.Windows.FrameworkElement>。  
  
-   A<xref:System.Windows.Controls.Grid>也就是子系`RootElement`。  
  
-   A<xref:System.Windows.Controls.ContentPresenter>顯示按鈕的內容。 <xref:System.Windows.Controls.ContentPresenter>可讓任何要顯示的物件類型。  
  
 [!code-xaml[VSMButtonTemplate#BasicTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]  
  
### <a name="preserving-the-functionality-of-a-controls-properties-by-using-templatebinding"></a>使用 TemplateBinding 來保留控制項屬性的功能  
 當您建立新<xref:System.Windows.Controls.ControlTemplate>，您仍可能會想要使用的公用屬性，來變更控制項的外觀。 [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)標記延伸的項目中的屬性繫結<xref:System.Windows.Controls.ControlTemplate>由控制項所定義的公用屬性。 當您使用 [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) 時，會讓控制項上的屬性能夠作為範本的參數。 也就是說，已設定控制項上的屬性時，該值會傳遞給具有 [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) 的元素。  
  
 下列範例會重複使用先前範例的一部分[TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)繫結中的項目屬性的標記延伸<xref:System.Windows.Controls.ControlTemplate>按鈕所定義的公用屬性。  
  
 [!code-xaml[VSMButtonTemplate#TemplateBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]  
  
 在此範例中，<xref:System.Windows.Controls.Grid>具有其<xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType>屬性範本繫結至<xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>。 因為<xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType>是範本繫結，您可以建立多個使用相同的按鈕<xref:System.Windows.Controls.ControlTemplate>並設定<xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>每個按鈕上的不同值。 如果<xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>已不是範本的內容繫結中項目的<xref:System.Windows.Controls.ControlTemplate>，設定<xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>按鈕的上會有任何影響按鈕的外觀。  
  
 請注意，兩個屬性的名稱不一定要相同。 在上述範例中，<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType>屬性<xref:System.Windows.Controls.Button>範本繫結至<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>屬性<xref:System.Windows.Controls.ContentPresenter>。 這可讓您以水平方式置放按鈕的內容。 <xref:System.Windows.Controls.ContentPresenter>沒有屬性，名為`HorizontalContentAlignment`，但<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType>可以繫結至<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>。 當您的範本繫結某個屬性時，請確定目標與來源屬性是相同類型。  
  
 <xref:System.Windows.Controls.Control>類別會定義必須由造成影響在控制項上的，當這些設定控制項範本的數個屬性。 如何<xref:System.Windows.Controls.ControlTemplate>屬性取決於屬性的使用。 <xref:System.Windows.Controls.ControlTemplate>必須使用下列方式之一的屬性：  
  
-   中的項目<xref:System.Windows.Controls.ControlTemplate>範本繫結到屬性。  
  
-   中的項目<xref:System.Windows.Controls.ControlTemplate>從父系繼承屬性<xref:System.Windows.FrameworkElement>。  
  
 下表列出繼承的控制項的視覺屬性<xref:System.Windows.Controls.Control>類別。 它同時也指出控制項的預設控制項範本是否使用繼承的屬性值，或是否必須以範本方式繫結。  
  
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
  
 資料表會列出只能繼承自的視覺屬性<xref:System.Windows.Controls.Control>類別。 除了資料表中所列的屬性，控制項可能也會繼承<xref:System.Windows.FrameworkElement.DataContext%2A>， <xref:System.Windows.FrameworkElement.Language%2A>，和<xref:System.Windows.Controls.TextBlock.TextDecorations%2A>從父架構項目屬性。  
  
 此外，如果<xref:System.Windows.Controls.ContentPresenter>處於<xref:System.Windows.Controls.ControlTemplate>的<xref:System.Windows.Controls.ContentControl>、<xref:System.Windows.Controls.ContentPresenter>會自動繫結至<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>和<xref:System.Windows.Controls.ContentControl.Content%2A>屬性。 同樣地，<xref:System.Windows.Controls.ItemsPresenter>位於<xref:System.Windows.Controls.ControlTemplate>的<xref:System.Windows.Controls.ItemsControl>會自動繫結至<xref:System.Windows.Controls.ItemsControl.Items%2A>和<xref:System.Windows.Controls.ItemsPresenter>屬性。  
  
 下列範例會建立使用的兩個按鈕<xref:System.Windows.Controls.ControlTemplate>上述範例中所定義。 範例會設定<xref:System.Windows.Controls.Control.Background%2A>， <xref:System.Windows.Controls.Control.Foreground%2A>，和<xref:System.Windows.Controls.Control.FontSize%2A>每個按鈕上的屬性。 設定<xref:System.Windows.Controls.Control.Background%2A>屬性沒有作用，因為它是繫結中的範本<xref:System.Windows.Controls.ControlTemplate>。 即使<xref:System.Windows.Controls.Control.Foreground%2A>和<xref:System.Windows.Controls.Control.FontSize%2A>屬性不是範本繫結，設定沒有作用，因為會繼承其值。  
  
 [!code-xaml[VSMButtonTemplate#ButtonDeclaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]  
  
 上述範例會產生類似下圖的輸出。  
  
 ![兩個按鈕，一個為藍色，一個為紫色。] (../../../../docs/framework/wpf/controls/media/ndp-buttontwo.png "NDP_ButtonTwo")  
兩個具有不同背景色彩的按鈕  
  
<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>   
## <a name="changing-the-appearance-of-a-control-depending-on-its-state"></a>依控制項的狀態變更其外觀  
 具有預設外觀的按鈕與上述範例中按鈕之間的差異在於，預設按鈕在處於不同狀態時會稍微變更。 例如，預設按鈕會在使用者按下按鈕時，或當滑鼠指標移至按鈕上時，變更外觀。 雖然<xref:System.Windows.Controls.ControlTemplate>不會變更功能的控制項，它並變更控制項的視覺行為。 視覺行為會描述控制項處於特定狀態時的外觀。 若要了解控制項的功能與視覺行為之間有何差異，請思考一下按鈕範例。 按鈕的功能，就會引發<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件時按一下它時，但是按鈕的視覺化行為是指向或按下時變更其外觀。  
  
 您使用<xref:System.Windows.VisualState>物件處於特定狀態時，指定控制項的外觀。 A<xref:System.Windows.VisualState>包含<xref:System.Windows.Media.Animation.Storyboard>變更中之項目的外觀<xref:System.Windows.Controls.ControlTemplate>。 您不必撰寫任何程式碼將會發生因為控制項的邏輯會將狀態變更使用此值設<xref:System.Windows.VisualStateManager>。 當控制項進入所指定的狀態<xref:System.Windows.VisualState.Name%2A?displayProperty=nameWithType>屬性，<xref:System.Windows.Media.Animation.Storyboard>開始。 當控制項結束狀態，<xref:System.Windows.Media.Animation.Storyboard>停止。  
  
 下列範例所示<xref:System.Windows.VisualState>變更的外觀<xref:System.Windows.Controls.Button>當滑鼠指標位於它。 <xref:System.Windows.Media.Animation.Storyboard>變更按鈕的框線色彩的色彩`BorderBrush`。 如果您參考<xref:System.Windows.Controls.ControlTemplate>範例在開始本主題時，您可以回想，`BorderBrush`名稱<xref:System.Windows.Media.SolidColorBrush>，指派給<xref:System.Windows.Controls.Border.Background%2A>的<xref:System.Windows.Controls.Border>。  
  
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
  
 <xref:System.Windows.Controls.Button>定義兩個狀態群組：`CommonStates`群組包含`Normal`， `MouseOver`， `Pressed`，和`Disabled`狀態。 `FocusStates` 群組則包含 `Focused` 和 `Unfocused` 狀態。 相同狀態群組中的狀態彼此互斥。 控制項就每一群組而言一律僅限處於一種狀態。 例如，<xref:System.Windows.Controls.Button>可以有焦點，滑鼠指標不是透過它，因此，即使<xref:System.Windows.Controls.Button>中`Focused`狀態可以是`MouseOver`， `Pressed`，或`Normal`狀態。  
  
 您將加入<xref:System.Windows.VisualState>物件加入至<xref:System.Windows.VisualStateGroup>物件。 您將加入<xref:System.Windows.VisualStateGroup>物件加入至<xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType>附加屬性。 下列範例會定義<xref:System.Windows.VisualState>物件`Normal`， `MouseOver`，和`Pressed`狀態，全部都在`CommonStates`群組。 <xref:System.Windows.VisualState.Name%2A>每個<xref:System.Windows.VisualState>符合上表中的名稱。 為了簡化範例，已省略 `Disabled` 狀態及`FocusStates` 群組中的狀態，但在本主題結尾的完整範例中已將它們都包含在內。  
  
> [!NOTE]
>  請務必設定<xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType>附加屬性的根<xref:System.Windows.FrameworkElement>的<xref:System.Windows.Controls.ControlTemplate>。  
  
 [!code-xaml[VSMButtonTemplate#VisualStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualstates)]  
  
 上述範例會產生類似下列圖例的輸出。  
  
 ![具有自訂控制項範本的按鈕。] (../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP_ButtonNormal")  
使用處於正常狀態之自訂控制項範本的按鈕  
  
 ![具有紅色框線的按鈕。] (../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
使用處於滑鼠移至上方狀態之自訂控制項範本的按鈕  
  
 ![框線呈現為透明的已按下按鈕。] (../../../../docs/framework/wpf/controls/media/ndp-buttonpressed.png "NDP_ButtonPressed")  
使用處於已按下狀態之自訂控制項範本的按鈕  
  
 若要尋找 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 隨附之控制項的視覺狀態，請參閱[控制項的樣式和範本](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)。  
  
<a name="specifying_the_behavior_of_a_control_when_it_transitions_between_states"></a>   
## <a name="specifying-the-behavior-of-a-control-when-it-transitions-between-states"></a>指定控制項在狀態之間轉換時的行為  
 在上述範例中，在使用者按一下按鈕時，按鈕的外觀也會變更，但除非按下按鈕整整一秒，否則使用者並不會看到效果。 動畫預設要一秒鐘的時間才會產生。 使用者會按一下，然後放開更少的時間，因為視覺化回應不是有效，如果您離開<xref:System.Windows.Controls.ControlTemplate>處於預設狀態。  
  
 您可以指定發生順暢地加入轉換從某個狀態到另一個控制項的動畫所花的時間量<xref:System.Windows.VisualTransition>物件加入至<xref:System.Windows.Controls.ControlTemplate>。 當您建立<xref:System.Windows.VisualTransition>，您可以指定一或多個項目：  
  
-   狀態之間進行轉換所需的時間。  
  
-   在轉換時發生的其他控制項外觀變更。  
  
-   哪些狀態<xref:System.Windows.VisualTransition>套用至。  
  
### <a name="specifying-the-duration-of-a-transition"></a>指定轉換的持續時間  
 您可以指定多久轉換會藉由設定<xref:System.Windows.VisualTransition.GeneratedDuration%2A>屬性。 上述範例有<xref:System.Windows.VisualState>指定按鈕的框線變成透明，按下按鈕時，但動畫所花太長的時間會很明顯，如果按鈕快速並放開按鍵時。 您可以使用<xref:System.Windows.VisualTransition>至指定的時間進行控制轉換為已按下狀態。 下列範例會指定控制項需要 1/100 秒的時間來進入已按下狀態。  
  
 [!code-xaml[VSMButtonTemplate#PressedTransition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]  
  
### <a name="specifying-changes-to-the-controls-appearance-during-a-transition"></a>指定轉換時對控制項外觀造成的變更  
 <xref:System.Windows.VisualTransition>包含<xref:System.Windows.Media.Animation.Storyboard>開始時控制項不同狀態之間轉換。 例如，您可以指定在控制項從 `MouseOver` 狀態轉換到 `Normal` 狀態時產生動畫。 下列範例會建立<xref:System.Windows.VisualTransition>，指定當使用者將滑鼠指標離開 按鈕，按鈕的框線變更藍色，黃色，然後黑色 1.5 秒中。  
  
 [!code-xaml[VSMButtonTemplate#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]  
  
### <a name="specifying-when-a-visualtransition-is-applied"></a>指定套用 VisualTransition 的時機  
 A<xref:System.Windows.VisualTransition>可以限制套用至特定狀態，或它可以套用任何時候控制項之間的轉換狀態。 在上述範例中，<xref:System.Windows.VisualTransition>時控制項將會從套用`MouseOver`狀態`Normal`狀態; 在此範例之前，<xref:System.Windows.VisualTransition>當控制項進入套用`Pressed`狀態。 您可以限制何時<xref:System.Windows.VisualTransition>藉由設定套用<xref:System.Windows.VisualTransition.To%2A>和<xref:System.Windows.VisualTransition.From%2A>屬性。 下表說明限制的層級 (依最嚴格到最不嚴格的順序排列)。  
  
|限制的類型|來源的值|目標的值|  
|-------------------------|-------------------|-----------------|  
|從指定的狀態到另一個指定的狀態|名稱<xref:System.Windows.VisualState>|名稱<xref:System.Windows.VisualState>|  
|從任何狀態到指定的狀態|未設定|名稱<xref:System.Windows.VisualState>|  
|從指定的狀態到任何狀態|名稱<xref:System.Windows.VisualState>|未設定|  
|從任何狀態到任何其他狀態|未設定|未設定|  
  
 您可以有多個<xref:System.Windows.VisualTransition>中的物件<xref:System.Windows.VisualStateGroup>，參考相同的狀態，但它們將會使用上表所指定的順序。 在下列範例中，有兩個<xref:System.Windows.VisualTransition>物件。 控制當轉換從`Pressed`狀態`MouseOver`狀態， <xref:System.Windows.VisualTransition> ，同時具有<xref:System.Windows.VisualTransition.From%2A>和<xref:System.Windows.VisualTransition.To%2A>集使用。 當控制項從不是 `Pressed` 的狀態轉換到 `MouseOver` 狀態時，則會使用另一個狀態。  
  
 [!code-xaml[VSMButtonTemplate#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]  
  
 <xref:System.Windows.VisualStateGroup>具有<xref:System.Windows.VisualStateGroup.Transitions%2A>屬性，其中包含<xref:System.Windows.VisualTransition>物件套用到<xref:System.Windows.VisualState>中的物件<xref:System.Windows.VisualStateGroup>。 做為<xref:System.Windows.Controls.ControlTemplate>作者，您可以包含任何自由<xref:System.Windows.VisualTransition>想。 不過，如果<xref:System.Windows.VisualTransition.To%2A>和<xref:System.Windows.VisualTransition.From%2A>屬性會設為不是處於的狀態名稱<xref:System.Windows.VisualStateGroup>、<xref:System.Windows.VisualTransition>會被忽略。  
  
 下列範例所示<xref:System.Windows.VisualStateGroup>如`CommonStates`。 此範例會定義<xref:System.Windows.VisualTransition>的每個按鈕的下列轉換。  
  
-   轉換到 `Pressed` 狀態。  
  
-   轉換到 `MouseOver` 狀態。  
  
-   從 `Pressed` 狀態轉換到 `MouseOver` 狀態。  
  
-   從 `MouseOver` 狀態轉換到 `Normal` 狀態。  
  
 [!code-xaml[VSMButtonTemplate#VisualTransitions](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]  
  
<a name="customizing_other_controls_by_understanding_the_control_contract"></a>   
## <a name="customizing-other-controls-by-understanding-the-control-contract"></a>透過了解控制項合約來自訂其他控制項  
 使用的控制項<xref:System.Windows.Controls.ControlTemplate>來指定其視覺化結構 (利用<xref:System.Windows.FrameworkElement>物件) 和視覺化行為 (使用<xref:System.Windows.VisualState>物件) 使用組件的控制項模式。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 4 隨附的許多控制項都使用此模型。 組件，<xref:System.Windows.Controls.ControlTemplate>作者需要注意的透過控制項合約溝通。 在您了解控制項合約的組件之後，即可自訂任何使用組件控制項模型之控制項的外觀。  
  
 控制項合約有三個元素：  
  
-   控制項邏輯所使用的視覺元素。  
  
-   控制項的狀態及每個狀態所屬的群組。  
  
-   在視覺上影響控制項的公用屬性。  
  
### <a name="visual-elements-in-the-control-contract"></a>控制項合約中的視覺元素  
 控制項的邏輯互動有時<xref:System.Windows.FrameworkElement>位於<xref:System.Windows.Controls.ControlTemplate>。 例如，控制項可能會處理它其中一個元素的事件。 當控制項預期應找到特定<xref:System.Windows.FrameworkElement>中<xref:System.Windows.Controls.ControlTemplate>，它必須傳達的資訊給<xref:System.Windows.Controls.ControlTemplate>作者。 此控制項會使用<xref:System.Windows.TemplatePartAttribute>來傳遞的類型預期的項目和項目的名稱應該是什麼。 <xref:System.Windows.Controls.Button>沒有<xref:System.Windows.FrameworkElement>在其控制項合約，而其他控制項，例如組件<xref:System.Windows.Controls.ComboBox>，執行。  
  
 下列範例所示<xref:System.Windows.TemplatePartAttribute>指定的物件<xref:System.Windows.Controls.ComboBox>類別。 邏輯<xref:System.Windows.Controls.ComboBox>預期應找到<xref:System.Windows.Controls.TextBox>名為`PART_EditableTextBox`和<xref:System.Windows.Controls.Primitives.Popup>名為`PART_Popup`中其<xref:System.Windows.Controls.ControlTemplate>。  
  
 [!code-csharp[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]  
  
 下列範例示範簡化<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.ComboBox>包含所指定的項目<xref:System.Windows.TemplatePartAttribute>物件<xref:System.Windows.Controls.ComboBox>類別。  
  
 [!code-xaml[VSMButtonTemplate#ComboBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]  
  
### <a name="states-in-the-control-contract"></a>控制項合約中的狀態  
 控制項的狀態也是控制項合約的一部分。 建立的範例<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.Button>示範如何指定的外觀<xref:System.Windows.Controls.Button>根據其狀態。 您建立<xref:System.Windows.VisualState>每個指定的狀態，並讓所有<xref:System.Windows.VisualState>物件共用<xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A>中<xref:System.Windows.VisualStateGroup>中所述，[取決於其狀態控制項的外觀會變更](#changing_the_appearance_of_a_control_depending_on_its_state)稍早在此主題。 協力廠商控制項應該使用指定的狀態<xref:System.Windows.TemplateVisualStateAttribute>，可讓設計工具，例如 Expression Blend 時，若要公開控制項的狀態，供撰寫控制項範本。  
  
 若要尋找 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 隨附之控制項的控制項合約，請參閱[控制項的樣式和範本](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)。  
  
### <a name="properties-in-the-control-contract"></a>控制項合約中的屬性  
 在視覺上影響控制項的公用屬性也包含在控制項合約中。 您可以設定這些屬性，以變更控制項的外觀，而不需要建立新<xref:System.Windows.Controls.ControlTemplate>。 您也可以使用[TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)繫結中的項目屬性的標記延伸<xref:System.Windows.Controls.ControlTemplate>所定義的公用屬性<xref:System.Windows.Controls.Button>。  
  
 下列範例示範按鈕的控制項合約。  
  
 [!code-csharp[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]  
  
 建立時<xref:System.Windows.Controls.ControlTemplate>，通常是最容易開頭的現有<xref:System.Windows.Controls.ControlTemplate>並對它進行變更。 您可以執行下列動作，以變更現有<xref:System.Windows.Controls.ControlTemplate>:  
  
-   使用設計工具 (例如 Expression Blend)，這會提供可用來建立控制項範本的圖形化使用者介面。 如需詳細資訊，請參閱[設定支援範本之控制項的樣式](http://go.microsoft.com/fwlink/?LinkId=161153)。  
  
-   取得預設<xref:System.Windows.Controls.ControlTemplate>並進行編輯。 若要尋找 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 隨附的預設控制項範本，請參閱[預設 WPF 佈景主題](http://go.microsoft.com/fwlink/?LinkID=158252)。  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>完整範例  
 下列範例顯示完整<xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ControlTemplate> ，本主題中討論。  
  
 [!code-xaml[VSMButtonTemplate#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]  
  
## <a name="see-also"></a>請參閱  
 [樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)
