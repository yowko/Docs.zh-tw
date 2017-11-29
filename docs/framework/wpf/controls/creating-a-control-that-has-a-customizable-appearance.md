---
title: "建立外觀可自訂的控制項"
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
- controls [WPF], customizing
- VisualStateManager [WPF], managing the state of a control
- ControlTemplate [WPF], customizing appearance
- controls [WPF], defining the visual structure and behavior of
- customizing appearance [WPF], ControlTemplate
- managing control states [WPF], VisualStateManager
- VisualStateManager [WPF], best practice
ms.assetid: 9e356d3d-a3d0-4b01-a25f-2d43e4d53fe5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4e76e1d814df5946d0e0f946cbc8d55507a07c96
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="creating-a-control-that-has-a-customizable-appearance"></a>建立外觀可自訂的控制項
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]可讓您建立控制項，您可以自訂其外觀。 例如，您可以變更的外觀<xref:System.Windows.Controls.CheckBox>超出什麼設定屬性會藉由建立新的執行<xref:System.Windows.Controls.ControlTemplate>。 下圖顯示<xref:System.Windows.Controls.CheckBox>，會使用預設<xref:System.Windows.Controls.ControlTemplate>和<xref:System.Windows.Controls.CheckBox>使用自訂<xref:System.Windows.Controls.ControlTemplate>。  
  
 ![核取方塊具有預設控制項範本。] (../../../../docs/framework/wpf/controls/media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
使用預設控制項範本的 CheckBox  
  
 ![核取方塊具有自訂控制項範本。] (../../../../docs/framework/wpf/controls/media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
使用自訂控制項範本的 CheckBox  
  
 如果您建立的控制項，您可以遵循的組件和狀態的模型，將可以自訂控制項的外觀。 設計工具，例如 Microsoft Expression Blend 支援的組件和狀態模型，讓控制項時，請依照此模型是可自訂這些類型的應用程式中。  本主題討論的組件和狀態的模型，以及如何建立您自己的控制項時遵循。 本主題使用的自訂控制項，範例`NumericUpDown`，以說明這個模型的原理。  `NumericUpDown`控制項會顯示數值，此使用者可以增加或減少上控制項的按鈕即可。  下圖顯示`NumericUpDown`本主題所討論的控制項。  
  
 ![NumericUpDown 自訂控制項。] (../../../../docs/framework/wpf/controls/media/ndp-numericupdown.png "NDP_NumericUPDown")  
自訂數值上下按鈕控制項  
  
 此主題包括下列章節：  
  
-   [必要條件](#prerequisites)  
  
-   [組件和狀態模型](#parts_and_states_model)  
  
-   [ControlTemplate 中定義視覺化結構和控制項的視覺行為](#defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate)  
  
-   [使用程式碼中 ControlTemplate 的組件](#using_parts_of_the_controltemplate_in_code)  
  
-   [提供控制項合約](#providing_the_control_contract)  
  
-   [完整範例](#complete_example)  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 本主題假設您知道如何建立新<xref:System.Windows.Controls.ControlTemplate>為現有的控制項，熟悉控制項合約上的項目是什麼，並了解討論的概念[自訂的現有控制項的外觀建立 ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。  
  
> [!NOTE]
>  若要建立的控制項可以具有自訂其外觀，您必須建立繼承自控制項<xref:System.Windows.Controls.Control>類別或其中一個子類別以外<xref:System.Windows.Controls.UserControl>。  控制項是繼承自<xref:System.Windows.Controls.UserControl>是控制項，您可以快速建立，但不會使用<xref:System.Windows.Controls.ControlTemplate>，您無法自訂其外觀。  
  
<a name="parts_and_states_model"></a>   
## <a name="parts-and-states-model"></a>組件和狀態模型  
 組件和狀態模型指定如何定義視覺化結構和控制項的視覺行為。 若要遵循的組件和狀態的模型，您應該執行下列作業：  
  
-   定義視覺結構和視覺化中的行為<xref:System.Windows.Controls.ControlTemplate>的控制項。  
  
-   當控制項的邏輯互動控制項範本的組件時，請遵循某些最佳作法。  
  
-   提供控制項來指定應該包含在合約<xref:System.Windows.Controls.ControlTemplate>。  
  
 當您定義的視覺化結構和視覺化中的行為<xref:System.Windows.Controls.ControlTemplate>控制項的應用程式作者可以變更視覺化結構和視覺化您的控制項的行為來建立新<xref:System.Windows.Controls.ControlTemplate>而不是撰寫程式碼。   您必須提供會告訴應用程式控制項合約位作者的<xref:System.Windows.FrameworkElement>應該中定義物件和狀態<xref:System.Windows.Controls.ControlTemplate>。 當您互動中的組件時，您應該遵循的一些最佳做法<xref:System.Windows.Controls.ControlTemplate>，讓控制項適當地處理不完整<xref:System.Windows.Controls.ControlTemplate>。  如果您遵循這些三個原則時，應用程式作者將能夠建立<xref:System.Windows.Controls.ControlTemplate>控制項只是您會看到輕鬆可以控制項，隨附於[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。  下節說明每個詳細建議。  
  
<a name="defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate"></a>   
## <a name="defining-the-visual-structure-and-visual-behavior-of-a-control-in-a-controltemplate"></a>ControlTemplate 中定義視覺化結構和控制項的視覺行為  
 當您使用的組件和狀態的模型建立您的自訂控制項時，您會定義控制項的視覺化結構和視覺化中的行為及其<xref:System.Windows.Controls.ControlTemplate>而不是在其邏輯中。  控制項的視覺化結構是複合的<xref:System.Windows.FrameworkElement>組成控制項的物件。  視覺化行為是處於特定狀態時，會出現在控制項的方式。   如需有關建立<xref:System.Windows.Controls.ControlTemplate>，指定視覺化結構和視覺控制項的行為，請參閱[自訂現有控制項的外觀，藉由建立 ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。  
  
 在範例中的`NumericUpDown`控制項的視覺化結構包含兩個<xref:System.Windows.Controls.Primitives.RepeatButton>控制項和<xref:System.Windows.Controls.TextBlock>。  如果您的程式碼中將這些控制項`NumericUpDown`控制--在其建構函式，例如這些控制項的位置會是不變。  而不是程式碼中定義控制項的視覺化結構和視覺化行為，您應該定義在<xref:System.Windows.Controls.ControlTemplate>。  然後應用程式開發人員若要自訂按鈕的位置和<xref:System.Windows.Controls.TextBlock>並指定哪些行為發生時`Value`為負數因為<xref:System.Windows.Controls.ControlTemplate>可以取代。  
  
 下列範例示範的視覺化結構`NumericUpDown`控制項，其包含<xref:System.Windows.Controls.Primitives.RepeatButton>增加`Value`、<xref:System.Windows.Controls.Primitives.RepeatButton>減少`Value`，和<xref:System.Windows.Controls.TextBlock>顯示`Value`。  
  
 [!code-xaml[VSMCustomControl#VisualStructure](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#visualstructure)]  
  
 視覺化行為`NumericUpDown`控制項是負數時，值是紅色字型。  如果您變更<xref:System.Windows.Controls.TextBlock.Foreground%2A>的<xref:System.Windows.Controls.TextBlock>在程式碼時`Value`是負數，`NumericUpDown`永遠會顯示為紅色的負值。 指定控制項的視覺行為<xref:System.Windows.Controls.ControlTemplate>加<xref:System.Windows.VisualState>物件加入至<xref:System.Windows.Controls.ControlTemplate>。  下列範例所示<xref:System.Windows.VisualState>物件`Positive`和`Negative`狀態。  `Positive`和`Negative`是互為獨佔模式 （控制項永遠是在兩個的其中一個），因此範例將<xref:System.Windows.VisualState>物件到單一<xref:System.Windows.VisualStateGroup>。  當控制項進入`Negative`狀態，<xref:System.Windows.Controls.TextBlock.Foreground%2A>的<xref:System.Windows.Controls.TextBlock>會變成紅色。  當控制項處於`Positive`狀態，<xref:System.Windows.Controls.TextBlock.Foreground%2A>回到其原始值。  定義<xref:System.Windows.VisualState>中的物件<xref:System.Windows.Controls.ControlTemplate>中進一步討論[自訂現有控制項的外觀，藉由建立 ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。  
  
> [!NOTE]
>  請務必設定<xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType>附加屬性的根<xref:System.Windows.FrameworkElement>的<xref:System.Windows.Controls.ControlTemplate>。  
  
 [!code-xaml[VSMCustomControl#ValueStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
<a name="using_parts_of_the_controltemplate_in_code"></a>   
## <a name="using-parts-of-the-controltemplate-in-code"></a>使用程式碼中 ControlTemplate 的組件  
 A<xref:System.Windows.Controls.ControlTemplate>作者可能會省略<xref:System.Windows.FrameworkElement>或<xref:System.Windows.VisualState>物件，故意或不小心，但控制項的邏輯可能會需要這些組件正常運作。 組件和狀態模型可讓您指定控制項是否應回復到<xref:System.Windows.Controls.ControlTemplate>遺失<xref:System.Windows.FrameworkElement>或<xref:System.Windows.VisualState>物件。  您的控制項不應該擲回例外狀況或報表錯誤如果<xref:System.Windows.FrameworkElement>， <xref:System.Windows.VisualState>，或<xref:System.Windows.VisualStateGroup>遺漏<xref:System.Windows.Controls.ControlTemplate>。 本章節描述與互動的建議的作法<xref:System.Windows.FrameworkElement>物件和管理狀態。  
  
### <a name="anticipate-missing-frameworkelement-objects"></a>預期會發生遺漏的 FrameworkElement 物件  
 當您定義<xref:System.Windows.FrameworkElement>中的物件<xref:System.Windows.Controls.ControlTemplate>，可能需要其中部分互動的控制項的邏輯。  比方說，`NumericUpDown`按鈕的控制項訂閱<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件，以增加或減少`Value`並設定<xref:System.Windows.Controls.TextBlock.Text%2A>屬性<xref:System.Windows.Controls.TextBlock>至`Value`。 如果自訂<xref:System.Windows.Controls.ControlTemplate>省略<xref:System.Windows.Controls.TextBlock>或按鈕時，是可接受的控制項失去的某些功能，但您應該確定您的控制項不會造成錯誤。 例如，如果<xref:System.Windows.Controls.ControlTemplate>不包含按鈕來變更`Value`、`NumericUpDown`失去該功能，但使用的應用程式<xref:System.Windows.Controls.ControlTemplate>仍會繼續執行。  
  
 下列做法可確保您的控制項適當地回應缺少<xref:System.Windows.FrameworkElement>物件：  
  
1.  設定`x:Name`每個屬性<xref:System.Windows.FrameworkElement>，您需要在程式碼中參考。  
  
2.  針對每一個定義私用屬性<xref:System.Windows.FrameworkElement>，您需要進行互動。  
  
3.  訂閱及取消訂閱任何事件，以處理您的控制項<xref:System.Windows.FrameworkElement>屬性的 set 存取子。  
  
4.  設定<xref:System.Windows.FrameworkElement>中所定義的屬性中的步驟 2<xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>方法。 這是最早的<xref:System.Windows.FrameworkElement>中<xref:System.Windows.Controls.ControlTemplate>是控制項可用。 使用`x:Name`的<xref:System.Windows.FrameworkElement>取得從<xref:System.Windows.Controls.ControlTemplate>。  
  
5.  請檢查<xref:System.Windows.FrameworkElement>不`null`之前存取它的成員。  如果是`null`，不會回報錯誤。  
  
 下列範例會顯示如何`NumericUpDown`與控制項互動<xref:System.Windows.FrameworkElement>符合前述清單中建議的物件。  
  
 在範例中定義的視覺化結構`NumericUpDown`控制<xref:System.Windows.Controls.ControlTemplate>、<xref:System.Windows.Controls.Primitives.RepeatButton>增加`Value`具有其`x:Name`屬性設為`UpButton`。  下列範例會宣告稱為屬性`UpButtonElement`表示<xref:System.Windows.Controls.Primitives.RepeatButton>中宣告<xref:System.Windows.Controls.ControlTemplate>。 `set`存取子先取消訂閱的按鈕<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件如果`UpDownElement`不`null`，然後設定屬性，然後其訂閱<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。 另外還有屬性定義，但不是會顯示在這裡，其他<xref:System.Windows.Controls.Primitives.RepeatButton>，稱為`DownButtonElement`。  
  
 [!code-csharp[VSMCustomControl#UpButtonProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#upbuttonproperty)]
 [!code-vb[VSMCustomControl#UpButtonProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#upbuttonproperty)]  
  
 下列範例所示<xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>如`NumericUpDown`控制項。  此範例會使用<xref:System.Windows.FrameworkElement.GetTemplateChild%2A>方法來取得<xref:System.Windows.FrameworkElement>物件從<xref:System.Windows.Controls.ControlTemplate>。  請注意，此範例防範狀況下<xref:System.Windows.FrameworkElement.GetTemplateChild%2A>尋找<xref:System.Windows.FrameworkElement>具有指定名稱不是預期的類型。 也是最佳做法是略過具有指定的項目`x:Name`但屬於錯誤的類型。  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 遵循先前的範例所示的作法，確定您的控制項，將會繼續執行時<xref:System.Windows.Controls.ControlTemplate>遺漏<xref:System.Windows.FrameworkElement>。  
  
### <a name="use-the-visualstatemanager-to-manage-states"></a>使用 VisualStateManager 管理狀態  
 <xref:System.Windows.VisualStateManager>會追蹤的控制項狀態，並執行狀態之間轉換所需的邏輯。 當您將加入<xref:System.Windows.VisualState>物件加入至<xref:System.Windows.Controls.ControlTemplate>，將它們加入<xref:System.Windows.VisualStateGroup>並加入<xref:System.Windows.VisualStateGroup>至<xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType>附加屬性，讓<xref:System.Windows.VisualStateManager>已存取它們。  
  
 下列範例會重複上一個範例會顯示<xref:System.Windows.VisualState>物件對應於`Positive`和`Negative`控制項的狀態。 <xref:System.Windows.Media.Animation.Storyboard>中`Negative`<xref:System.Windows.VisualState>開啟<xref:System.Windows.Controls.TextBlock.Foreground%2A>的<xref:System.Windows.Controls.TextBlock>紅色。   當`NumericUpDown`控制項處於`Negative`狀態時，在分鏡腳本`Negative`狀態開始。  然後在<xref:System.Windows.Media.Animation.Storyboard>中`Negative`時控制權會傳回狀態就會停止`Positive`狀態。  `Positive` <xref:System.Windows.VisualState>不需要包含<xref:System.Windows.Media.Animation.Storyboard>因為時<xref:System.Windows.Media.Animation.Storyboard>如`Negative`停止，<xref:System.Windows.Controls.TextBlock.Foreground%2A>回到其原始的色彩。  
  
 [!code-xaml[VSMCustomControl#ValueStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
 請注意，<xref:System.Windows.Controls.TextBlock>提供的名稱，但<xref:System.Windows.Controls.TextBlock>控制項合約中不是`NumericUpDown`因為永遠不會參考控制項的邏輯<xref:System.Windows.Controls.TextBlock>。  中所參考的項目<xref:System.Windows.Controls.ControlTemplate>有名稱，但不是需要是控制合約的一部分，因為新<xref:System.Windows.Controls.ControlTemplate>的控制項可能不需要參照該元素。  例如，建立新的人<xref:System.Windows.Controls.ControlTemplate>如`NumericUpDown`可能決定不表示`Value`藉由變更為負數<xref:System.Windows.Controls.Control.Foreground%2A>。  在此情況下，都沒有程式碼和<xref:System.Windows.Controls.ControlTemplate>參考<xref:System.Windows.Controls.TextBlock>依名稱。  
  
 控制項的邏輯會負責變更控制項的狀態。 下列範例會顯示`NumericUpDown`控制呼叫<xref:System.Windows.VisualStateManager.GoToState%2A>方法進入`Positive`狀態`Value`0 或更大，而`Negative`狀態`Value`小於 0。  
  
 [!code-csharp[VSMCustomControl#ValueStateChange](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#valuestatechange)]
 [!code-vb[VSMCustomControl#ValueStateChange](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#valuestatechange)]  
  
 <xref:System.Windows.VisualStateManager.GoToState%2A>方法會執行所需的啟動和停止將分鏡腳本適當的邏輯。 控制當呼叫<xref:System.Windows.VisualStateManager.GoToState%2A>若要變更其狀態，<xref:System.Windows.VisualStateManager>會進行下列作業：  
  
-   如果<xref:System.Windows.VisualState>控制項移至具有<xref:System.Windows.Media.Animation.Storyboard>，分鏡腳本開始。 如果<xref:System.Windows.VisualState>控制項來自具有<xref:System.Windows.Media.Animation.Storyboard>，分鏡腳本結束。  
  
-   如果控制項已指定，則處於<xref:System.Windows.VisualStateManager.GoToState%2A>會採取任何動作，並傳回`true`。  
  
-   如果指定的狀態不存在於<xref:System.Windows.Controls.ControlTemplate>的`control`，<xref:System.Windows.VisualStateManager.GoToState%2A>會採取任何動作，並傳回`false`。  
  
#### <a name="best-practices-for-working-with-the-visualstatemanager"></a>使用 VisualStateManager 的最佳作法  
 我們建議您下列工作來維護控制項的狀態：  
  
-   您可以使用屬性來追蹤其狀態。  
  
-   建立狀態之間轉換的 helper 方法。  
  
 `NumericUpDown`控制會使用其`Value`內容來追蹤其是否處於`Positive`或`Negative`狀態。  `NumericUpDown`控制項也會定義`Focused`和`UnFocused`所述，曲目<xref:System.Windows.UIElement.IsFocused%2A>屬性。 如果您使用不會自然對應到控制項屬性的狀態，您可以定義追蹤狀態的私用屬性。  
  
 更新所有狀態的單一方法，集中管理呼叫<xref:System.Windows.VisualStateManager>並讓您的程式碼保持易於管理。 下列範例所示`NumericUpDown`控制項的協助程式方法， `UpdateStates`。 當`Value`大於或等於 0，<xref:System.Windows.Controls.Control>處於`Positive`狀態。  當`Value`為小於 0 的控制項是在`Negative`狀態。  當<xref:System.Windows.UIElement.IsFocused%2A>是`true`，控制項處於`Focused`狀態; 否則它處於`Unfocused`狀態。  控制項可以呼叫`UpdateStates`每當程式需要變更其狀態，無論何種狀態會變更。  
  
 [!code-csharp[VSMCustomControl#UpdateStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#updatestates)]
 [!code-vb[VSMCustomControl#UpdateStates](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#updatestates)]  
  
 如果您要傳入的狀態名稱<xref:System.Windows.VisualStateManager.GoToState%2A>控制項已經處於該狀態中，當<xref:System.Windows.VisualStateManager.GoToState%2A>不做任何動作，因此您不需要檢查控制項的目前狀態。  例如，如果`Value`從一個負的數字變更為另一個負數值，如分鏡腳本`Negative`狀態不會中斷與使用者看不到控制項中的變更。  
  
 <xref:System.Windows.VisualStateManager>使用<xref:System.Windows.VisualStateGroup>物件來判斷的狀態下，當您呼叫結束<xref:System.Windows.VisualStateManager.GoToState%2A>。 控制項永遠是一種狀態<xref:System.Windows.VisualStateGroup>，它定義於其<xref:System.Windows.Controls.ControlTemplate>後會進入另一個狀態從相同，只保留狀態<xref:System.Windows.VisualStateGroup>。 例如，<xref:System.Windows.Controls.ControlTemplate>的`NumericUpDown`控制定義`Positive`和`Negative`<xref:System.Windows.VisualState>中其中一個物件<xref:System.Windows.VisualStateGroup>和`Focused`和`Unfocused`<xref:System.Windows.VisualState>中另一個物件。 (您可以看到`Focused`和`Unfocused`<xref:System.Windows.VisualState>中定義[完整的範例](#complete_example)當控制項進入從本主題中的區段`Positive`狀態`Negative`狀態，或反之亦然，控制項仍會停留在`Focused`或`Unfocused`狀態。  
  
 有三種典型的位置，可能會變更控制項的狀態：  
  
-   當<xref:System.Windows.Controls.ControlTemplate>套用至<xref:System.Windows.Controls.Control>。  
  
-   當屬性變更時。  
  
-   事件發生時。  
  
 下列範例將示範更新的狀態`NumericUpDown`在這些情況下的控制項。  
  
 您應該更新控制項的狀態<xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>方法，讓控制項出現在正確的狀態何時<xref:System.Windows.Controls.ControlTemplate>套用。 下列範例會呼叫`UpdateStates`中<xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>確保控制項處於適當狀態。  例如，假設您建立`NumericUpDown`控制，並將其<xref:System.Windows.Controls.Control.Foreground%2A>綠色和`Value`於-5。  如果您不會呼叫`UpdateStates`時<xref:System.Windows.Controls.ControlTemplate>套用至`NumericUpDown`控制項，控制項不是在`Negative`狀態和值為綠色，而不是紅色。  您必須呼叫`UpdateStates`將控制項放`Negative`狀態。  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 您通常需要更新控制項屬性變更時的狀態。 下列範例示範整個`ValueChangedCallback`方法。 因為`ValueChangedCallback`時，會呼叫`Value`變更時，這個方法會呼叫`UpdateStates`以防`Value`變更正為負數，反之亦然。 是可接受呼叫`UpdateStates`時`Value`改變，但是會保持正數或負數，因為在此情況下，此控制項不會變更狀態。  
  
 [!code-csharp[VSMCustomControl#EntireValueChangedCallback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#entirevaluechangedcallback)]
 [!code-vb[VSMCustomControl#EntireValueChangedCallback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#entirevaluechangedcallback)]  
  
 此外，您可能也需要更新事件發生時的狀態。 下列範例會顯示`NumericUpDown`呼叫`UpdateStates`上<xref:System.Windows.Controls.Control>處理<xref:System.Windows.UIElement.GotFocus>事件。  
  
 [!code-csharp[VSMCustomControl#OnGotFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#ongotfocus)]
 [!code-vb[VSMCustomControl#OnGotFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#ongotfocus)]  
  
 <xref:System.Windows.VisualStateManager>可協助您管理您的控制項狀態。 使用<xref:System.Windows.VisualStateManager>，確定您的控制項正確不同狀態之間轉換。  如果您遵循建議使用這一節所述<xref:System.Windows.VisualStateManager>，控制項的程式碼仍可讀取與維護。  
  
<a name="providing_the_control_contract"></a>   
## <a name="providing-the-control-contract"></a>提供控制項合約  
 提供控制項合約以便<xref:System.Windows.Controls.ControlTemplate>作者會知道要將範本中的項目。 控制項合約有三個元素：  
  
-   控制項邏輯所使用的視覺元素。  
  
-   控制項的狀態及每個狀態所屬的群組。  
  
-   在視覺上影響控制項的公用屬性。  
  
 建立新的其他人<xref:System.Windows.Controls.ControlTemplate>需要知道<xref:System.Windows.FrameworkElement>控制項的邏輯會使用的物件，每個物件類型，以及它的名稱。 A<xref:System.Windows.Controls.ControlTemplate>作者也必須知道的控制項可以在中，每個可能狀態，而且其名稱<xref:System.Windows.VisualStateGroup>處於。  
  
 返回`NumericUpDown`範例中，控制項必須要有<xref:System.Windows.Controls.ControlTemplate>已經下列<xref:System.Windows.FrameworkElement>物件：  
  
-   A<xref:System.Windows.Controls.Primitives.RepeatButton>呼叫`UpButton`。  
  
-   A<xref:System.Windows.Controls.Primitives.RepeatButton>呼叫`DownButton.`  
  
 控制項可以處於下列狀態：  
  
-   在`ValueStates`<xref:System.Windows.VisualStateGroup>  
  
    -   `Positive`  
  
    -   `Negative`  
  
-   在`FocusStates`<xref:System.Windows.VisualStateGroup>  
  
    -   `Focused`  
  
    -   `Unfocused`  
  
 若要指定的項目<xref:System.Windows.FrameworkElement>物件控制項必須要有，則使用<xref:System.Windows.TemplatePartAttribute>，以指定的名稱和預期的項目型別。  若要指定控制項的可能狀態，您使用<xref:System.Windows.TemplateVisualStateAttribute>，以指定的狀態名稱和其<xref:System.Windows.VisualStateGroup>它屬於。  Put<xref:System.Windows.TemplatePartAttribute>和<xref:System.Windows.TemplateVisualStateAttribute>類別定義上的控制項。  
  
 任何會影響您的控制項的外觀的公用屬性也會控制合約的一部分。  
  
 下列範例會指定<xref:System.Windows.FrameworkElement>物件和狀態`NumericUpDown`控制項。  
  
 [!code-csharp[VSMCustomControl#ControlContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controlcontract)]
 [!code-vb[VSMCustomControl#ControlContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controlcontract)]  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>完整範例  
 下列範例會將整個<xref:System.Windows.Controls.ControlTemplate>如`NumericUpDown`控制項。  
  
 [!code-xaml[VSMCustomControl#NUDTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/themes/generic.xaml#nudtemplate)]  
  
 下列範例顯示的邏輯`NumericUpDown`。  
  
 [!code-csharp[VSMCustomControl#ControlLogic](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controllogic)]
 [!code-vb[VSMCustomControl#ControlLogic](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controllogic)]  
  
## <a name="see-also"></a>另請參閱  
 [透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)  
 [控制項自訂](../../../../docs/framework/wpf/controls/control-customization.md)
