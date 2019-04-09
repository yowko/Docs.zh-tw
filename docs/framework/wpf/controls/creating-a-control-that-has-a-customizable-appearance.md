---
title: 建立外觀可自訂的控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], customizing
- VisualStateManager [WPF], managing the state of a control
- ControlTemplate [WPF], customizing appearance
- controls [WPF], defining the visual structure and behavior of
- customizing appearance [WPF], ControlTemplate
- managing control states [WPF], VisualStateManager
- VisualStateManager [WPF], best practice
ms.assetid: 9e356d3d-a3d0-4b01-a25f-2d43e4d53fe5
ms.openlocfilehash: 17b6fd604b5eca54d6323701dafdd38f9f6e7328
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131012"
---
# <a name="creating-a-control-that-has-a-customizable-appearance"></a>建立外觀可自訂的控制項
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 可讓您能夠建立可自訂其外觀的控制項。 例如，您可以變更的外觀<xref:System.Windows.Controls.CheckBox>超出設定為何屬性會藉由建立新的執行<xref:System.Windows.Controls.ControlTemplate>。 如下圖所示<xref:System.Windows.Controls.CheckBox>所使用的預設值<xref:System.Windows.Controls.ControlTemplate>並<xref:System.Windows.Controls.CheckBox>，使用自訂<xref:System.Windows.Controls.ControlTemplate>。  
  
 ![核取方塊具有預設控制項範本。](./media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
使用預設控制項範本的 CheckBox  
  
 ![核取方塊具有自訂控制項範本。](./media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
使用自訂控制項範本的 CheckBox  
  
 如果您建立的控制項，您可以遵循的組件與狀態的模型，則會自訂控制項的外觀。 例如 Microsoft Expression Blend 設計工具支援組件與狀態模型，因此您的控制項時遵循此模型是可自訂這些類型的應用程式中。  本主題討論的組件與狀態的模型，以及如何建立您自己的控制項時，請遵循它。 本主題使用的自訂控制項，範例`NumericUpDown`，以說明此模型的原理。  `NumericUpDown`控制項會顯示數值，此使用者可以增加或減少上控制項的按鈕即可。  下圖顯示`NumericUpDown`本主題所述的控制項。  
  
 ![NumericUpDown 自訂控制項。](./media/ndp-numericupdown.png "NDP_NumericUPDown")  
自訂的 NumericUpDown 控制項  
  
 此主題包括下列章節：  
  
-   [必要條件](#prerequisites)  
  
-   [組件以及狀態模型](#parts_and_states_model)  
  
-   [在 ControlTemplate 中定義的視覺結構和控制項的視覺化行為](#defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate)  
  
-   [使用組件的程式碼中的 ControlTemplate](#using_parts_of_the_controltemplate_in_code)  
  
-   [提供控制項合約](#providing_the_control_contract)  
  
-   [完整範例](#complete_example)  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 本主題假設您知道如何建立新<xref:System.Windows.Controls.ControlTemplate>為現有的控制項，熟悉控制項合約上的項目是什麼，並了解中所討論的概念[自訂現有控制項的外觀建立 ControlTemplate](customizing-the-appearance-of-an-existing-control.md)。  
  
> [!NOTE]
>  若要建立可以自訂其外觀的控制項，您必須建立繼承自控制項<xref:System.Windows.Controls.Control>類別或其中一個子類別以外<xref:System.Windows.Controls.UserControl>。  控制項是繼承自<xref:System.Windows.Controls.UserControl>是一個控制項，您可以快速建立，但它不會使用<xref:System.Windows.Controls.ControlTemplate>而且您無法自訂其外觀。  
  
<a name="parts_and_states_model"></a>   
## <a name="parts-and-states-model"></a>組件以及狀態模型  
 組件與狀態的模型會指定如何定義視覺結構和控制項的視覺行為。 若要遵循的組件與狀態的模型，您應該執行下列作業：  
  
-   定義視覺結構和視覺化行為<xref:System.Windows.Controls.ControlTemplate>的控制項。  
  
-   當控制項的邏輯進行互動的控制項範本的組件時，請遵循某些最佳作法。  
  
-   提供指定應該包含在控制項合約<xref:System.Windows.Controls.ControlTemplate>。  
  
 當您定義視覺結構和視覺化行為<xref:System.Windows.Controls.ControlTemplate>控制項的應用程式作者可以變更的視覺結構和控制項的視覺化行為來建立新<xref:System.Windows.Controls.ControlTemplate>而不需要撰寫程式碼。   您必須提供控制項合約，告訴應用程式作者這<xref:System.Windows.FrameworkElement>中，則應該定義物件和狀態<xref:System.Windows.Controls.ControlTemplate>。 當您互動中的組件時，您應該遵循一些最佳作法<xref:System.Windows.Controls.ControlTemplate>，讓您的控制項適當地處理不完整<xref:System.Windows.Controls.ControlTemplate>。  如果您遵循下列三項原則，應用程式作者將能夠建立<xref:System.Windows.Controls.ControlTemplate>控制項只是因為它們可能輕易地可以控制項，隨附[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。  下節說明每個詳細建議。  
  
<a name="defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate"></a>   
## <a name="defining-the-visual-structure-and-visual-behavior-of-a-control-in-a-controltemplate"></a>在 ControlTemplate 中定義的視覺結構和控制項的視覺化行為  
 您可以使用組件與狀態的模型，以建立您的自訂控制項，當您定義控制項的視覺結構和視覺化的行為，在其<xref:System.Windows.Controls.ControlTemplate>而不是在其邏輯中。  控制項的視覺結構是個複合<xref:System.Windows.FrameworkElement>組成控制項的物件。  視覺行為是處於特定狀態時，會出現在控制項的方式。   如需有關建立<xref:System.Windows.Controls.ControlTemplate>，指定的視覺結構和控制項的視覺化行為，請參閱 <<c2> [ 透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。  
  
 在範例中的`NumericUpDown`控制項的視覺化結構包含兩個<xref:System.Windows.Controls.Primitives.RepeatButton>控制項和<xref:System.Windows.Controls.TextBlock>。  如果您的程式碼中加入這些控制項`NumericUpDown`控制-在其建構函式，例如這些控制項的位置就不可改變。  而不是在其程式碼中定義控制項的視覺結構和視覺化行為，您應該定義在<xref:System.Windows.Controls.ControlTemplate>。  然後應用程式開發人員自訂按鈕的位置及<xref:System.Windows.Controls.TextBlock>並指定哪些行為發生時`Value`是負數因為<xref:System.Windows.Controls.ControlTemplate>可以取代。  
  
 下列範例顯示的視覺結構`NumericUpDown`控制項，其中包含<xref:System.Windows.Controls.Primitives.RepeatButton>增加`Value`，則<xref:System.Windows.Controls.Primitives.RepeatButton>減少`Value`，和<xref:System.Windows.Controls.TextBlock>顯示`Value`。  
  
 [!code-xaml[VSMCustomControl#VisualStructure](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#visualstructure)]  
  
 視覺行為`NumericUpDown`控制項是如果它是負數，則值為紅色字型。  如果您變更<xref:System.Windows.Controls.TextBlock.Foreground%2A>的<xref:System.Windows.Controls.TextBlock>程式碼中的時機`Value`是負數，`NumericUpDown`一律會顯示為紅色的負值。 您指定之控制項的視覺行為<xref:System.Windows.Controls.ControlTemplate>加上<xref:System.Windows.VisualState>物件到<xref:System.Windows.Controls.ControlTemplate>。  下列範例所示<xref:System.Windows.VisualState>的物件`Positive`和`Negative`狀態。  `Positive` 並`Negative`是互斥 （控制項永遠是在兩個的其中一個），因此此範例會將放<xref:System.Windows.VisualState>成單一物件<xref:System.Windows.VisualStateGroup>。  當控制項進入`Negative`狀態，<xref:System.Windows.Controls.TextBlock.Foreground%2A>的<xref:System.Windows.Controls.TextBlock>會變成紅色。  當控制項處於`Positive`狀態，<xref:System.Windows.Controls.TextBlock.Foreground%2A>回到其原始值。  定義<xref:System.Windows.VisualState>中的物件<xref:System.Windows.Controls.ControlTemplate>中進一步討論[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。  
  
> [!NOTE]
>  請務必設定<xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType>附加屬性上的根<xref:System.Windows.FrameworkElement>的<xref:System.Windows.Controls.ControlTemplate>。  
  
 [!code-xaml[VSMCustomControl#ValueStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
<a name="using_parts_of_the_controltemplate_in_code"></a>   
## <a name="using-parts-of-the-controltemplate-in-code"></a>使用組件的程式碼中的 ControlTemplate  
 A<xref:System.Windows.Controls.ControlTemplate>作者可能會省略<xref:System.Windows.FrameworkElement>或<xref:System.Windows.VisualState>物件，故意或不小心，但控制項的邏輯可能會需要這些組件，才能正確運作。 組件與狀態模型可讓您指定應回復到您的控制項<xref:System.Windows.Controls.ControlTemplate>缺少<xref:System.Windows.FrameworkElement>或<xref:System.Windows.VisualState>物件。  您的控制項不應該擲回的例外狀況或報告錯誤如果<xref:System.Windows.FrameworkElement>， <xref:System.Windows.VisualState>，或<xref:System.Windows.VisualStateGroup>缺少<xref:System.Windows.Controls.ControlTemplate>。 本章節描述與互動的建議的作法<xref:System.Windows.FrameworkElement>物件，並管理狀態。  
  
### <a name="anticipate-missing-frameworkelement-objects"></a>預期遺漏的 FrameworkElement 物件  
 當您定義<xref:System.Windows.FrameworkElement>中的物件<xref:System.Windows.Controls.ControlTemplate>，控制項的邏輯可能需要其中一些互動。  比方說，`NumericUpDown`控制訂閱 buttons<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件，以增加或減少`Value`，並設定<xref:System.Windows.Controls.TextBlock.Text%2A>屬性<xref:System.Windows.Controls.TextBlock>至`Value`。 如果自訂<xref:System.Windows.Controls.ControlTemplate>省略<xref:System.Windows.Controls.TextBlock>或按鈕時，它是可接受的控制項失去其中一些功能，但您應該先確認您的控制項不會造成錯誤。 比方說，如果<xref:System.Windows.Controls.ControlTemplate>不包含按鈕，即可變更`Value`，則`NumericUpDown`失去該功能，但使用的應用程式<xref:System.Windows.Controls.ControlTemplate>仍會繼續執行。  
  
 下列作法可確保您的控制項適當地回應遺漏<xref:System.Windows.FrameworkElement>物件：  
  
1.  設定`x:Name`針對每個屬性<xref:System.Windows.FrameworkElement>，您需要在程式碼中參考。  
  
2.  針對每一個定義私用屬性<xref:System.Windows.FrameworkElement>，您需要進行互動。  
  
3.  訂閱及取消訂閱從您的控制項處理中的任何事件<xref:System.Windows.FrameworkElement>屬性的 set 存取子。  
  
4.  設定<xref:System.Windows.FrameworkElement>中所定義的屬性中的步驟 2<xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>方法。 這是最早的<xref:System.Windows.FrameworkElement>在<xref:System.Windows.Controls.ControlTemplate>是控制項可用。 使用`x:Name`的<xref:System.Windows.FrameworkElement>若要取得從<xref:System.Windows.Controls.ControlTemplate>。  
  
5.  請確認<xref:System.Windows.FrameworkElement>不是`null`之前存取它的成員。  如果是`null`，不會回報錯誤。  
  
 下列範例會顯示如何`NumericUpDown`與控制項互動<xref:System.Windows.FrameworkElement>符合前述清單中建議的物件。  
  
 在範例中定義的視覺結構`NumericUpDown`在中控制可<xref:System.Windows.Controls.ControlTemplate>，則<xref:System.Windows.Controls.Primitives.RepeatButton>，增加`Value`具有其`x:Name`屬性設為`UpButton`。  下列範例宣告名為的屬性`UpButtonElement`，表示<xref:System.Windows.Controls.Primitives.RepeatButton>中宣告<xref:System.Windows.Controls.ControlTemplate>。 `set`存取子先取消訂閱至按鈕的<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件如果`UpDownElement`不是`null`，然後它會設定屬性，並接著訂閱<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。 另外還有一個屬性定義，但不是會顯示在這裡，為其他<xref:System.Windows.Controls.Primitives.RepeatButton>，稱為`DownButtonElement`。  
  
 [!code-csharp[VSMCustomControl#UpButtonProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#upbuttonproperty)]
 [!code-vb[VSMCustomControl#UpButtonProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#upbuttonproperty)]  
  
 下列範例所示<xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>針對`NumericUpDown`控制項。  此範例會使用<xref:System.Windows.FrameworkElement.GetTemplateChild%2A>方法來取得<xref:System.Windows.FrameworkElement>物件從<xref:System.Windows.Controls.ControlTemplate>。  請注意，此範例可防範情況<xref:System.Windows.FrameworkElement.GetTemplateChild%2A>尋找<xref:System.Windows.FrameworkElement>具有指定名稱不是預期的類型。 它也是最佳做法是略過具有指定的項目`x:Name`但屬於錯誤類型。  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 依照先前範例所示的作法，確定您的控制項，將會繼續執行時<xref:System.Windows.Controls.ControlTemplate>遺漏<xref:System.Windows.FrameworkElement>。  
  
### <a name="use-the-visualstatemanager-to-manage-states"></a>使用 VisualStateManager 管理狀態  
 <xref:System.Windows.VisualStateManager>會追蹤控制項的狀態以及執行狀態之間轉換所需的邏輯。 當您將加入<xref:System.Windows.VisualState>物件至<xref:System.Windows.Controls.ControlTemplate>，將它們加入<xref:System.Windows.VisualStateGroup>並新增<xref:System.Windows.VisualStateGroup>來<xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType>附加屬性，讓<xref:System.Windows.VisualStateManager>可存取它們。  
  
 下列範例會重複上一個範例會顯示<xref:System.Windows.VisualState>對應至物件`Positive`和`Negative`控制項狀態。 <xref:System.Windows.Media.Animation.Storyboard>中`Negative`<xref:System.Windows.VisualState>會變成<xref:System.Windows.Controls.TextBlock.Foreground%2A>的<xref:System.Windows.Controls.TextBlock>紅色。   當`NumericUpDown`控制項處於`Negative`狀態時，在分鏡腳本`Negative`狀態開始。  然後<xref:System.Windows.Media.Animation.Storyboard>中`Negative`時，控制權會傳回狀態就會停止`Positive`狀態。  `Positive`<xref:System.Windows.VisualState>不需要包含<xref:System.Windows.Media.Animation.Storyboard>因為時<xref:System.Windows.Media.Animation.Storyboard>如`Negative`停止，<xref:System.Windows.Controls.TextBlock.Foreground%2A>回到其原始的色彩。  
  
 [!code-xaml[VSMCustomControl#ValueStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
 請注意，<xref:System.Windows.Controls.TextBlock>有一個名稱，但<xref:System.Windows.Controls.TextBlock>的控制項合約中不是`NumericUpDown`因為控制項的邏輯會永遠不會參考<xref:System.Windows.Controls.TextBlock>。  中所參考的項目<xref:System.Windows.Controls.ControlTemplate>有名稱，但不是需要是控制項合約的一部分，因為新<xref:System.Windows.Controls.ControlTemplate>的控制項可能不需要參考該項目。  比方說，建立新的人<xref:System.Windows.Controls.ControlTemplate>for`NumericUpDown`可能會決定不表示`Value`變更為負數<xref:System.Windows.Controls.Control.Foreground%2A>。  在此情況下，都不的程式碼也<xref:System.Windows.Controls.ControlTemplate>參考<xref:System.Windows.Controls.TextBlock>依名稱。  
  
 控制項的邏輯會負責變更控制項的狀態。 下列範例顯示`NumericUpDown`控制呼叫<xref:System.Windows.VisualStateManager.GoToState%2A>方法來進入`Positive`狀態時`Value`0 或更大，而`Negative`時`Value`小於 0。  
  
 [!code-csharp[VSMCustomControl#ValueStateChange](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#valuestatechange)]
 [!code-vb[VSMCustomControl#ValueStateChange](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#valuestatechange)]  
  
 <xref:System.Windows.VisualStateManager.GoToState%2A>方法會執行所需的啟動和停止將分鏡腳本的適當的邏輯。 當控制項便會呼叫<xref:System.Windows.VisualStateManager.GoToState%2A>若要變更其狀態，<xref:System.Windows.VisualStateManager>會進行下列作業：  
  
-   如果<xref:System.Windows.VisualState>控制項要具有<xref:System.Windows.Media.Animation.Storyboard>，分鏡腳本開始。 然後，如果<xref:System.Windows.VisualState>控制項來自具有<xref:System.Windows.Media.Animation.Storyboard>，分鏡腳本結束。  
  
-   如果控制項已在指定時，狀態<xref:System.Windows.VisualStateManager.GoToState%2A>會採取任何動作，並傳回`true`。  
  
-   如果指定的狀態不存在於<xref:System.Windows.Controls.ControlTemplate>的`control`，<xref:System.Windows.VisualStateManager.GoToState%2A>會採取任何動作，並傳回`false`。  
  
#### <a name="best-practices-for-working-with-the-visualstatemanager"></a>使用 VisualStateManager 的最佳作法  
 我們建議您下列工作來維護您的控制項狀態：  
  
-   您可以使用屬性來追蹤其狀態。  
  
-   建立狀態之間轉換的 helper 方法。  
  
 `NumericUpDown`控制項會使用其`Value`屬性來追蹤是否處於`Positive`或`Negative`狀態。  `NumericUpDown`控制項也會定義`Focused`並`UnFocused`所述，哪一個資料軌<xref:System.Windows.UIElement.IsFocused%2A>屬性。 如果您使用不會自然對應至的控制項屬性的狀態，您可以定義追蹤狀態的私用屬性。  
  
 更新所有狀態的單一方法可以集中呼叫<xref:System.Windows.VisualStateManager>並保持可管理您的程式碼。 下列範例所示`NumericUpDown`控制項的協助程式方法， `UpdateStates`。 當`Value`大於或等於 0，<xref:System.Windows.Controls.Control>處於`Positive`狀態。  當`Value`是小於 0，控制項是在`Negative`狀態。  當<xref:System.Windows.UIElement.IsFocused%2A>是`true`，在控制項處於`Focused`狀態; 否則它是在`Unfocused`狀態。  控制項可以呼叫`UpdateStates`每當需要變更其狀態，無論何種狀態變更。  
  
 [!code-csharp[VSMCustomControl#UpdateStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#updatestates)]
 [!code-vb[VSMCustomControl#UpdateStates](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#updatestates)]  
  
 如果您傳遞的狀態名稱<xref:System.Windows.VisualStateManager.GoToState%2A>控制項已處於該狀態中，當<xref:System.Windows.VisualStateManager.GoToState%2A>不執行任何動作，因此您不需要檢查控制項的目前狀態。  例如，如果`Value`從一個負的數字變更為另一個負數數字，分鏡腳本`Negative`狀態不會中斷與使用者看不到控制項中的變更。  
  
 <xref:System.Windows.VisualStateManager>會使用<xref:System.Windows.VisualStateGroup>物件來判斷的狀態下，當您呼叫結束<xref:System.Windows.VisualStateManager.GoToState%2A>。 此控制項一律會在每個狀態<xref:System.Windows.VisualStateGroup>定義於其<xref:System.Windows.Controls.ControlTemplate>後進入另一個狀態從相同，只保留狀態<xref:System.Windows.VisualStateGroup>。 比方說，<xref:System.Windows.Controls.ControlTemplate>的`NumericUpDown`控制項會定義`Positive`並`Negative`<xref:System.Windows.VisualState>中其中一個物件<xref:System.Windows.VisualStateGroup>而`Focused`和`Unfocused`<xref:System.Windows.VisualState>中另一個物件。 (您所見`Focused`並`Unfocused`<xref:System.Windows.VisualState>中定義[完整範例](#complete_example)時的控制項將會從本主題中的區段`Positive`狀態`Negative`狀態，或反之亦然，控制會保留在請`Focused`或`Unfocused`狀態。  
  
 有三個典型的地方，其中可能會變更控制項的狀態：  
  
-   當<xref:System.Windows.Controls.ControlTemplate>套用至<xref:System.Windows.Controls.Control>。  
  
-   當屬性變更時。  
  
-   在事件發生時。  
  
 下列範例將示範如何更新的狀態`NumericUpDown`在這些情況下的控制項。  
  
 您應該更新之控制項的狀態<xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>方法，使控制項出現在正確的狀態時<xref:System.Windows.Controls.ControlTemplate>套用。 下列範例會呼叫`UpdateStates`在<xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>以確保控制項處於適當狀態。  例如，假設您建立`NumericUpDown`控制項，並將其<xref:System.Windows.Controls.Control.Foreground%2A>綠色和`Value`以-5。  如果您不能呼叫`UpdateStates`時<xref:System.Windows.Controls.ControlTemplate>套用至`NumericUpDown`控制項，控制項不在`Negative`狀態，而且值是綠色，而不是紅色。  您必須呼叫`UpdateStates`若要將控制項放在`Negative`狀態。  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 您通常需要更新的控制項屬性變更時的狀態。 下列範例顯示整個`ValueChangedCallback`方法。 因為`ValueChangedCallback`時，會呼叫`Value`有所變更，方法會呼叫`UpdateStates`萬一`Value`變更從正為負數，反之亦然。 它會呼叫可接受`UpdateStates`當`Value`變更，但會保持正數或負數，因為在此情況下，控制項不會變更狀態。  
  
 [!code-csharp[VSMCustomControl#EntireValueChangedCallback](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#entirevaluechangedcallback)]
 [!code-vb[VSMCustomControl#EntireValueChangedCallback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#entirevaluechangedcallback)]  
  
 此外，您可能也需要在事件發生時，更新狀態。 下列範例顯示`NumericUpDown`呼叫`UpdateStates`上<xref:System.Windows.Controls.Control>處理<xref:System.Windows.UIElement.GotFocus>事件。  
  
 [!code-csharp[VSMCustomControl#OnGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#ongotfocus)]
 [!code-vb[VSMCustomControl#OnGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#ongotfocus)]  
  
 <xref:System.Windows.VisualStateManager>可協助您管理您的控制項狀態。 使用<xref:System.Windows.VisualStateManager>，確定您的控制項正確狀態之間轉換。  如果您遵循使用這一節所述的建議<xref:System.Windows.VisualStateManager>，控制項的程式碼仍可讀取且可維護。  
  
<a name="providing_the_control_contract"></a>   
## <a name="providing-the-control-contract"></a>提供控制項合約  
 提供控制項合約，讓<xref:System.Windows.Controls.ControlTemplate>作者會知道要放在範本中的項目。 控制項合約有三個元素：  
  
-   控制項邏輯所使用的視覺元素。  
  
-   控制項的狀態及每個狀態所屬的群組。  
  
-   在視覺上影響控制項的公用屬性。  
  
 建立新的某人<xref:System.Windows.Controls.ControlTemplate>必須知道<xref:System.Windows.FrameworkElement>控制項的邏輯會使用的物件，每個物件類型，以及它的名稱。 A<xref:System.Windows.Controls.ControlTemplate>作者也必須知道的控制項可以在中，每個可能狀態，以及哪些名稱<xref:System.Windows.VisualStateGroup>處於的狀態。  
  
 返回`NumericUpDown`範例中，控制項預期<xref:System.Windows.Controls.ControlTemplate>具有下列<xref:System.Windows.FrameworkElement>物件：  
  
-   A<xref:System.Windows.Controls.Primitives.RepeatButton>稱為`UpButton`。  
  
-   A<xref:System.Windows.Controls.Primitives.RepeatButton>呼叫 `DownButton.`  
  
 控制項可以處於下列狀態：  
  
-   在 `ValueStates`<xref:System.Windows.VisualStateGroup>  
  
    -   `Positive`  
  
    -   `Negative`  
  
-   在 `FocusStates`<xref:System.Windows.VisualStateGroup>  
  
    -   `Focused`  
  
    -   `Unfocused`  
  
 若要指定的項目<xref:System.Windows.FrameworkElement>物件的控制項預期，您使用<xref:System.Windows.TemplatePartAttribute>，以指定的名稱和預期的項目型別。  若要指定控制項的可能狀態，您使用<xref:System.Windows.TemplateVisualStateAttribute>，以指定的狀態名稱，以及其<xref:System.Windows.VisualStateGroup>它屬於。  放<xref:System.Windows.TemplatePartAttribute>和<xref:System.Windows.TemplateVisualStateAttribute>控制項的類別定義。  
  
 任何會影響您外觀的公用屬性也是控制項的控制項合約的一部分。  
  
 下列範例會指定<xref:System.Windows.FrameworkElement>物件和狀態`NumericUpDown`控制項。  
  
 [!code-csharp[VSMCustomControl#ControlContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controlcontract)]
 [!code-vb[VSMCustomControl#ControlContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controlcontract)]  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>完整範例  
 下列範例會將整個<xref:System.Windows.Controls.ControlTemplate>針對`NumericUpDown`控制項。  
  
 [!code-xaml[VSMCustomControl#NUDTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/themes/generic.xaml#nudtemplate)]  
  
 下列範例顯示的邏輯`NumericUpDown`。  
  
 [!code-csharp[VSMCustomControl#ControlLogic](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controllogic)]
 [!code-vb[VSMCustomControl#ControlLogic](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controllogic)]  
  
## <a name="see-also"></a>另請參閱

- [透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)
- [控制項自訂](control-customization.md)
