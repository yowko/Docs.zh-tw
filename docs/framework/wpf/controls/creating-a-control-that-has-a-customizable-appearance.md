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
ms.openlocfilehash: d9cf092cf47d4fb70b15033d039777d3279b633a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283565"
---
# <a name="creating-a-control-that-has-a-customizable-appearance"></a>建立外觀可自訂的控制項

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 讓您能夠建立可自訂外觀的控制項。 例如，您可以藉由建立新的 <xref:System.Windows.Controls.ControlTemplate>，將 <xref:System.Windows.Controls.CheckBox> 的外觀變更為超過設定屬性的用途。 下圖顯示使用預設 <xref:System.Windows.Controls.ControlTemplate> 的 <xref:System.Windows.Controls.CheckBox>，以及使用自訂 <xref:System.Windows.Controls.ControlTemplate>的 <xref:System.Windows.Controls.CheckBox>。

![搭配預設控制項範本的核取方塊。](./media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")
使用預設控制項範本的 CheckBox

![搭配自訂控制項範本的核取方塊。](./media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")
使用自訂控制項範本的 CheckBox

如果您在建立控制項時遵循 [元件與狀態] 模型，控制項的外觀將可自訂。 設計工具（例如 Blend for Visual Studio）支援 [元件] 和 [狀態] 模型，因此當您遵循此模型時，您的控制項就可以在這些類型的應用程式中自訂。  本主題討論「元件和狀態」模型，以及當您建立自己的控制項時要如何追蹤。 本主題使用自訂控制項的範例 `NumericUpDown`，來說明此模型的原理。  [`NumericUpDown`] 控制項會顯示數值，使用者可以按一下控制項的按鈕來增加或減少此值。  下圖顯示本主題中討論的 `NumericUpDown` 控制項。

![NumericUpDown 自訂控制項。](./media/ndp-numericupdown.png "NDP_NumericUPDown")
自訂 NumericUpDown 控制項

本主題包含下列各節：

- [先決條件](#prerequisites)

- [元件和狀態模型](#parts_and_states_model)

- [在 ControlTemplate 中定義控制項的視覺化結構和視覺行為](#defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate)

- [在程式碼中使用部分 ControlTemplate](#using_parts_of_the_controltemplate_in_code)

- [提供控制項合約](#providing_the_control_contract)

- [完整範例](#complete_example)

<a name="prerequisites"></a>

## <a name="prerequisites"></a>先決條件

本主題假設您知道如何為現有的控制項建立新的 <xref:System.Windows.Controls.ControlTemplate>、熟悉控制項合約上的元素為何，以及瞭解[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)中所討論的概念。

> [!NOTE]
> 若要建立可自訂其外觀的控制項，您必須建立繼承自 <xref:System.Windows.Controls.Control> 類別的控制項，或是 <xref:System.Windows.Controls.UserControl>以外的其中一個子類別。  繼承自 <xref:System.Windows.Controls.UserControl> 的控制項是可以快速建立的控制項，但不會使用 <xref:System.Windows.Controls.ControlTemplate>，而且您無法自訂其外觀。

<a name="parts_and_states_model"></a>

## <a name="parts-and-states-model"></a>元件和狀態模型

[元件和狀態] 模型會指定如何定義控制項的視覺化結構和視覺行為。 若要遵循元件和狀態模型，您應該執行下列動作：

- 在控制項的 <xref:System.Windows.Controls.ControlTemplate> 中，定義視覺效果結構和視覺效果的行為。

- 當控制項的邏輯與控制項範本的部分互動時，請遵循特定的最佳做法。

- 提供控制合約，以指定應包含在 <xref:System.Windows.Controls.ControlTemplate>中的內容。

當您在控制項的 <xref:System.Windows.Controls.ControlTemplate> 中定義視覺化結構和視覺效果時，應用程式作者可以藉由建立新的 <xref:System.Windows.Controls.ControlTemplate> 而不是撰寫程式碼，來變更控制項的視覺化結構和視覺化行為。   您必須提供控制合約，告訴應用程式作者應該在 <xref:System.Windows.Controls.ControlTemplate>中定義 <xref:System.Windows.FrameworkElement> 物件和狀態。 當您與 <xref:System.Windows.Controls.ControlTemplate> 中的元件互動時，您應該遵循一些最佳作法，讓您的控制項能夠適當地處理不完整的 <xref:System.Windows.Controls.ControlTemplate>。  如果您遵循這三項原則，應用程式作者就能夠為您的控制項建立 <xref:System.Windows.Controls.ControlTemplate>，就像是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]隨附的控制項一樣容易。  下一節將詳細說明每個建議。

<a name="defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate"></a>

## <a name="defining-the-visual-structure-and-visual-behavior-of-a-control-in-a-controltemplate"></a>在 ControlTemplate 中定義控制項的視覺化結構和視覺行為

當您使用「元件和狀態」模型來建立自訂控制項時，您可以在其 <xref:System.Windows.Controls.ControlTemplate> 而不是在其邏輯中，定義控制項的視覺化結構和視覺效果行為。  控制項的視覺化結構是組成控制項的 <xref:System.Windows.FrameworkElement> 物件的複合。  視覺行為是控制項處於特定狀態時的顯示方式。   如需建立 <xref:System.Windows.Controls.ControlTemplate> 的詳細資訊，以指定控制項的視覺化結構和視覺行為，請參閱[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。

在 `NumericUpDown` 控制項的範例中，視覺化結構包含兩個 <xref:System.Windows.Controls.Primitives.RepeatButton> 控制項和一個 <xref:System.Windows.Controls.TextBlock>。  如果您在 `NumericUpDown` 控制項的程式碼中加入這些控制項--在其函式中（例如），則這些控制項的位置會是改變。  您不需要在其程式碼中定義控制項的視覺化結構和視覺行為，而是在 <xref:System.Windows.Controls.ControlTemplate>中定義它。  然後，應用程式開發人員自訂按鈕和 <xref:System.Windows.Controls.TextBlock> 的位置，並指定 `Value` 為負數時所發生的行為，因為可以取代 <xref:System.Windows.Controls.ControlTemplate>。

下列範例顯示 `NumericUpDown` 控制項的視覺化結構，其中包括增加 `Value`的 <xref:System.Windows.Controls.Primitives.RepeatButton>、要降低 `Value`的 <xref:System.Windows.Controls.Primitives.RepeatButton>，以及顯示 <xref:System.Windows.Controls.TextBlock> 的 `Value`。

[!code-xaml[VSMCustomControl#VisualStructure](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#visualstructure)]

`NumericUpDown` 控制項的視覺行為是，如果值為負數，則其值為紅色字型。  如果您在 `Value` 為負數時，在程式碼中變更 <xref:System.Windows.Controls.TextBlock> 的 <xref:System.Windows.Controls.TextBlock.Foreground%2A>，則 `NumericUpDown` 一律會顯示紅色的負數值。 您可以藉由將 <xref:System.Windows.VisualState> 物件加入至 <xref:System.Windows.Controls.ControlTemplate>，在 <xref:System.Windows.Controls.ControlTemplate> 中指定控制項的視覺行為。  下列範例顯示 `Positive` 和 `Negative` 狀態的 <xref:System.Windows.VisualState> 物件。  `Positive` 和 `Negative` 互斥（控制項一律為兩者的其中一個），因此範例會將 <xref:System.Windows.VisualState> 物件放入單一 <xref:System.Windows.VisualStateGroup>中。  當控制項進入 `Negative` 狀態時，<xref:System.Windows.Controls.TextBlock> 的 <xref:System.Windows.Controls.TextBlock.Foreground%2A> 會變成紅色。  當控制項處於 `Positive` 狀態時，<xref:System.Windows.Controls.TextBlock.Foreground%2A> 會回到其原始值。  [建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)中會進一步討論在 <xref:System.Windows.Controls.ControlTemplate> 中定義 <xref:System.Windows.VisualState> 物件。

> [!NOTE]
> 請務必在 <xref:System.Windows.Controls.ControlTemplate>的根 <xref:System.Windows.FrameworkElement> 上設定 <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> 附加屬性。

[!code-xaml[VSMCustomControl#ValueStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]

<a name="using_parts_of_the_controltemplate_in_code"></a>

## <a name="using-parts-of-the-controltemplate-in-code"></a>在程式碼中使用部分 ControlTemplate

<xref:System.Windows.Controls.ControlTemplate> 作者可能會省略 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.VisualState> 物件（特意或錯誤），但您的控制項邏輯可能需要這些元件才能正常運作。 [元件和狀態] 模型會指定您的控制項應可復原遺失 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.VisualState> 物件的 <xref:System.Windows.Controls.ControlTemplate>。  如果 <xref:System.Windows.Controls.ControlTemplate>中遺漏 <xref:System.Windows.FrameworkElement>、<xref:System.Windows.VisualState>或 <xref:System.Windows.VisualStateGroup>，則您的控制項不應該擲回例外狀況或報告錯誤。 本節說明與 <xref:System.Windows.FrameworkElement> 物件互動和管理狀態的建議做法。

### <a name="anticipate-missing-frameworkelement-objects"></a>預期遺漏 FrameworkElement 物件

當您在 <xref:System.Windows.Controls.ControlTemplate>中定義 <xref:System.Windows.FrameworkElement> 物件時，控制項的邏輯可能需要與其中一部分互動。  例如，`NumericUpDown` 控制項會訂閱按鈕的 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件來增加或減少 `Value`，並將 <xref:System.Windows.Controls.TextBlock> 的 <xref:System.Windows.Controls.TextBlock.Text%2A> 屬性設定為 [`Value`]。 如果自訂 <xref:System.Windows.Controls.ControlTemplate> 省略 <xref:System.Windows.Controls.TextBlock> 或按鈕，控制項就會失去其部分功能，但您應該確定控制項不會造成錯誤。 例如，如果 <xref:System.Windows.Controls.ControlTemplate> 不包含要變更 `Value`的按鈕，`NumericUpDown` 會失去該功能，但使用 <xref:System.Windows.Controls.ControlTemplate> 的應用程式將會繼續執行。

下列做法可確保您的控制項適當地回應遺失的 <xref:System.Windows.FrameworkElement> 物件：

1. 設定您需要在程式碼中參考之每個 <xref:System.Windows.FrameworkElement> 的 `x:Name` 屬性。

2. 針對您需要互動的每個 <xref:System.Windows.FrameworkElement> 定義私用屬性。

3. 訂閱及取消訂閱您的控制項在 <xref:System.Windows.FrameworkElement> 屬性的 set 存取子中處理的任何事件。

4. 在 <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> 方法中，設定您在步驟2中定義的 <xref:System.Windows.FrameworkElement> 屬性。 這是 <xref:System.Windows.Controls.ControlTemplate> 中的 <xref:System.Windows.FrameworkElement> 可供控制項使用的最早版本。 使用 <xref:System.Windows.FrameworkElement> 的 `x:Name` 從 <xref:System.Windows.Controls.ControlTemplate>取得。

5. 在存取其成員之前，請先確認 <xref:System.Windows.FrameworkElement> 不 `null`。  如果 `null`，請勿報告錯誤。

下列範例會根據上述清單中的建議，顯示 `NumericUpDown` 控制項與 <xref:System.Windows.FrameworkElement> 物件的互動方式。

在定義 <xref:System.Windows.Controls.ControlTemplate>中 `NumericUpDown` 控制項之視覺結構的範例中，增加 `Value` 的 <xref:System.Windows.Controls.Primitives.RepeatButton> 會將其 `x:Name` 屬性設定為 `UpButton`。  下列範例會宣告名為 `UpButtonElement` 的屬性，其代表在 <xref:System.Windows.Controls.ControlTemplate>中宣告的 <xref:System.Windows.Controls.Primitives.RepeatButton>。 如果未 `null``UpDownElement`，則 `set` 存取子會先取消訂閱按鈕的 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件，然後設定屬性，然後訂閱 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件。 此外，也會針對其他 <xref:System.Windows.Controls.Primitives.RepeatButton>（稱為 `DownButtonElement`）定義屬性，但此處並未顯示。

[!code-csharp[VSMCustomControl#UpButtonProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#upbuttonproperty)]
[!code-vb[VSMCustomControl#UpButtonProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#upbuttonproperty)]

下列範例顯示 `NumericUpDown` 控制項的 <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>。  這個範例會使用 <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> 方法，從 <xref:System.Windows.Controls.ControlTemplate>取得 <xref:System.Windows.FrameworkElement> 物件。  請注意，此範例會保護 <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> 尋找具有指定名稱的 <xref:System.Windows.FrameworkElement> 不是預期類型的情況。 最好的做法是忽略具有指定之 `x:Name` 但類型錯誤的元素。

[!code-csharp[VSMCustomControl#ApplyTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
[!code-vb[VSMCustomControl#ApplyTemplate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]

藉由遵循先前範例中所示的作法，您可以確保在 <xref:System.Windows.Controls.ControlTemplate> 遺漏 <xref:System.Windows.FrameworkElement>時，您的控制項仍會繼續執行。

### <a name="use-the-visualstatemanager-to-manage-states"></a>使用 VisualStateManager 來管理狀態

<xref:System.Windows.VisualStateManager> 會持續追蹤控制項的狀態，並執行在狀態之間轉換所需的邏輯。 當您將 <xref:System.Windows.VisualState> 物件加入至 <xref:System.Windows.Controls.ControlTemplate>時，您會將其加入至 <xref:System.Windows.VisualStateGroup>，並將 <xref:System.Windows.VisualStateGroup> 加入至 <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> 附加屬性，讓 <xref:System.Windows.VisualStateManager> 可以存取它們。

下列範例會重複先前的範例，顯示對應至控制項之 `Positive` 和 `Negative` 狀態的 <xref:System.Windows.VisualState> 物件。 `Negative`<xref:System.Windows.VisualState> 中的 <xref:System.Windows.Media.Animation.Storyboard> 會將 <xref:System.Windows.Controls.TextBlock> 的 <xref:System.Windows.Controls.TextBlock.Foreground%2A> 轉換成紅色。   當 `NumericUpDown` 控制項處於 [`Negative`] 狀態時，`Negative` 狀態中的分鏡腳本就會開始。  然後當控制項回到 `Positive` 狀態時，`Negative` 狀態中的 <xref:System.Windows.Media.Animation.Storyboard> 就會停止。  `Positive`<xref:System.Windows.VisualState> 不需要包含 <xref:System.Windows.Media.Animation.Storyboard>，因為當 `Negative` 的 <xref:System.Windows.Media.Animation.Storyboard> 停止時，<xref:System.Windows.Controls.TextBlock.Foreground%2A> 會回到其原始色彩。

[!code-xaml[VSMCustomControl#ValueStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]

請注意，<xref:System.Windows.Controls.TextBlock> 提供名稱，但 <xref:System.Windows.Controls.TextBlock> 不在 `NumericUpDown` 的控制合約中，因為控制項的邏輯永遠不會參考 <xref:System.Windows.Controls.TextBlock>。  <xref:System.Windows.Controls.ControlTemplate> 所參考的元素具有名稱，但不需要是控制項合約的一部分，因為控制項的新 <xref:System.Windows.Controls.ControlTemplate> 可能不需要參考該專案。  例如，針對 `NumericUpDown` 建立新 <xref:System.Windows.Controls.ControlTemplate> 的人，可能會藉由變更 <xref:System.Windows.Controls.Control.Foreground%2A>來決定不表示 `Value` 為負數。  在這種情況下，程式碼和 <xref:System.Windows.Controls.ControlTemplate> 都不會依名稱參考 <xref:System.Windows.Controls.TextBlock>。

控制項的邏輯會負責變更控制項的狀態。 下列範例顯示當 `Value` 為0或更大時，`NumericUpDown` 控制項會呼叫 <xref:System.Windows.VisualStateManager.GoToState%2A> 方法來進入 `Positive` 狀態，而當 `Negative` 小於0時，則為 `Value` 狀態。

[!code-csharp[VSMCustomControl#ValueStateChange](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#valuestatechange)]
[!code-vb[VSMCustomControl#ValueStateChange](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#valuestatechange)]

<xref:System.Windows.VisualStateManager.GoToState%2A> 方法會執行必要的邏輯，以適當地啟動和停止分鏡腳本。 當控制項呼叫 <xref:System.Windows.VisualStateManager.GoToState%2A> 以變更其狀態時，<xref:System.Windows.VisualStateManager> 會執行下列動作：

- 如果控制項要有 <xref:System.Windows.Media.Animation.Storyboard>的 <xref:System.Windows.VisualState>，腳本就會開始。 然後，如果控制項的 <xref:System.Windows.VisualState> 具有 <xref:System.Windows.Media.Animation.Storyboard>，則腳本會結束。

- 如果控制項已在指定的狀態中，<xref:System.Windows.VisualStateManager.GoToState%2A> 不會採取任何動作，且會傳回 `true`。

- 如果指定的狀態不存在於 `control`的 <xref:System.Windows.Controls.ControlTemplate> 中，<xref:System.Windows.VisualStateManager.GoToState%2A> 不會採取任何動作，而會傳回 `false`。

#### <a name="best-practices-for-working-with-the-visualstatemanager"></a>使用 VisualStateManager 的最佳做法

建議您執行下列動作，以維護控制項的狀態：

- 使用屬性來追蹤其狀態。

- 建立可在狀態之間轉換的 helper 方法。

`NumericUpDown` 控制項會使用其 `Value` 屬性來追蹤它是否處於 `Positive` 或 `Negative` 狀態。  `NumericUpDown` 控制項也會定義 `Focused` 和 `UnFocused` 狀態，以追蹤 <xref:System.Windows.UIElement.IsFocused%2A> 屬性。 如果您使用的狀態並未自然對應至控制項的屬性，您可以定義私用屬性來追蹤狀態。

更新所有狀態的單一方法會將呼叫集中在 <xref:System.Windows.VisualStateManager>，並讓您的程式碼可管理。 下列範例顯示 `NumericUpDown` 控制項的 helper 方法，`UpdateStates`。 當 `Value` 大於或等於0時，<xref:System.Windows.Controls.Control> 會處於 `Positive` 狀態。  當 `Value` 小於0時，控制項就會處於 `Negative` 狀態。  當 `true`<xref:System.Windows.UIElement.IsFocused%2A> 時，控制項會處於 `Focused` 狀態;否則，它會處於 `Unfocused` 狀態。  無論狀態變更為何，控制項都可以在需要變更其狀態時呼叫 `UpdateStates`。

[!code-csharp[VSMCustomControl#UpdateStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#updatestates)]
[!code-vb[VSMCustomControl#UpdateStates](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#updatestates)]

如果您在控制項已處於該狀態時，將狀態名稱傳遞給 <xref:System.Windows.VisualStateManager.GoToState%2A>，<xref:System.Windows.VisualStateManager.GoToState%2A> 不會執行任何動作，因此您不需要檢查控制項的目前狀態。  例如，如果 `Value` 從一個負數變更為另一個負數，則 `Negative` 狀態的分鏡腳本不會中斷，使用者也不會在控制項中看到變更。

當您呼叫 <xref:System.Windows.VisualStateManager.GoToState%2A>時，<xref:System.Windows.VisualStateManager> 會使用 <xref:System.Windows.VisualStateGroup> 物件來決定要結束的狀態。 控制項在其 <xref:System.Windows.Controls.ControlTemplate> 中定義的每個 <xref:System.Windows.VisualStateGroup> 一定會處於一種狀態，而且只有在從相同 <xref:System.Windows.VisualStateGroup>進入另一個狀態時，才會離開狀態。 例如，`NumericUpDown` 控制項的 <xref:System.Windows.Controls.ControlTemplate> 會定義一個 <xref:System.Windows.VisualState> 中的 `Positive` 和 `Negative`<xref:System.Windows.VisualStateGroup> 物件，以及另一個 `Focused` 中的 `Unfocused`和 <xref:System.Windows.VisualState> 物件。 （當控制項從 `Positive` 狀態變成 `Negative` 狀態時，您可以查看本主題的[完整範例](#complete_example)一節中所定義的 `Focused` 和 `Unfocused`<xref:System.Windows.VisualState>，反之亦然，控制項會保持在 `Focused` 或 `Unfocused` 狀態。

有三個典型的位置，控制項的狀態可能會變更：

- 當 <xref:System.Windows.Controls.ControlTemplate> 套用至 <xref:System.Windows.Controls.Control>時。

- 當屬性變更時。

- 發生事件時。

下列範例示範如何在這些情況下更新 `NumericUpDown` 控制項的狀態。

您應該在 <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> 方法中更新控制項的狀態，如此一來，當套用 <xref:System.Windows.Controls.ControlTemplate> 時，控制項就會顯示為正確的狀態。 下列範例會呼叫 <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> 中的 `UpdateStates`，以確保控制項處於適當的狀態。  例如，假設您建立一個 `NumericUpDown` 控制項，然後將其 <xref:System.Windows.Controls.Control.Foreground%2A> 設定為綠色，並 `Value` 為-5。  如果您未在 <xref:System.Windows.Controls.ControlTemplate> 套用至 `NumericUpDown` 控制項時呼叫 `UpdateStates`，則控制項不會處於 `Negative` 狀態，而值會是綠色而不是紅色。  您必須呼叫 `UpdateStates`，讓控制項處於 `Negative` 狀態。

[!code-csharp[VSMCustomControl#ApplyTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
[!code-vb[VSMCustomControl#ApplyTemplate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]

當屬性變更時，您通常需要更新控制項的狀態。 下列範例顯示整個 `ValueChangedCallback` 方法。 因為 `Value` 變更時，會呼叫 `ValueChangedCallback`，所以方法會呼叫 `UpdateStates`，以防 `Value` 從正數變更為負數，反之亦然。 當 `Value` 變更但仍為正面或負面時，可以接受呼叫 `UpdateStates`，因為在這種情況下，控制項將不會變更狀態。

[!code-csharp[VSMCustomControl#EntireValueChangedCallback](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#entirevaluechangedcallback)]
[!code-vb[VSMCustomControl#EntireValueChangedCallback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#entirevaluechangedcallback)]

當發生事件時，您可能也需要更新狀態。 下列範例顯示 `NumericUpDown` 會呼叫 <xref:System.Windows.Controls.Control> 上的 `UpdateStates` 來處理 <xref:System.Windows.UIElement.GotFocus> 事件。

[!code-csharp[VSMCustomControl#OnGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#ongotfocus)]
[!code-vb[VSMCustomControl#OnGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#ongotfocus)]

<xref:System.Windows.VisualStateManager> 可協助您管理控制項的狀態。 藉由使用 <xref:System.Windows.VisualStateManager>，您可以確保您的控制項在狀態之間進行正確轉換。  如果您遵循本節所述的建議來使用 <xref:System.Windows.VisualStateManager>，您的控制項程式碼仍可讀取及維護。

<a name="providing_the_control_contract"></a>

## <a name="providing-the-control-contract"></a>提供控制項合約

您會提供控制項合約，讓 <xref:System.Windows.Controls.ControlTemplate> 的作者知道要將哪個內容放在範本中。 控制項合約有三個元素：

- 控制項邏輯所使用的視覺元素。

- 控制項的狀態及每個狀態所屬的群組。

- 在視覺上影響控制項的公用屬性。

建立新 <xref:System.Windows.Controls.ControlTemplate> 的人必須知道控制項的邏輯所使用的 <xref:System.Windows.FrameworkElement> 物件、每個物件的類型，以及其名稱為何。 <xref:System.Windows.Controls.ControlTemplate> 的作者也必須知道控制項可以放入的每個可能狀態的名稱，以及狀態所在的 <xref:System.Windows.VisualStateGroup>。

回到 `NumericUpDown` 範例，控制項預期 <xref:System.Windows.Controls.ControlTemplate> 具有下列 <xref:System.Windows.FrameworkElement> 物件：

- 稱為 `UpButton`的 <xref:System.Windows.Controls.Primitives.RepeatButton>。

- 稱為 `DownButton.` 的 <xref:System.Windows.Controls.Primitives.RepeatButton>

 控制項可以處於下列狀態：

- 在 `ValueStates`<xref:System.Windows.VisualStateGroup>

  - `Positive`

  - `Negative`

- 在 `FocusStates`<xref:System.Windows.VisualStateGroup>

  - `Focused`

  - `Unfocused`

若要指定控制項預期的 <xref:System.Windows.FrameworkElement> 物件，您可以使用 <xref:System.Windows.TemplatePartAttribute>，它會指定預期元素的名稱和類型。  若要指定控制項的可能狀態，請使用 <xref:System.Windows.TemplateVisualStateAttribute>，這會指定狀態名稱及其所屬 <xref:System.Windows.VisualStateGroup>。  將 <xref:System.Windows.TemplatePartAttribute> 和 <xref:System.Windows.TemplateVisualStateAttribute> 放在控制項的類別定義上。

任何會影響控制面板的公用屬性也是控制合約的一部分。

下列範例會指定 `NumericUpDown` 控制項的 <xref:System.Windows.FrameworkElement> 物件和狀態。

[!code-csharp[VSMCustomControl#ControlContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controlcontract)]
[!code-vb[VSMCustomControl#ControlContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controlcontract)]

<a name="complete_example"></a>

## <a name="complete-example"></a>完整範例

下列範例是 `NumericUpDown` 控制項的整個 <xref:System.Windows.Controls.ControlTemplate>。

[!code-xaml[VSMCustomControl#NUDTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/themes/generic.xaml#nudtemplate)]

下列範例顯示 `NumericUpDown`的邏輯。

[!code-csharp[VSMCustomControl#ControlLogic](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controllogic)]
[!code-vb[VSMCustomControl#ControlLogic](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controllogic)]

## <a name="see-also"></a>請參閱

- [建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)
- [控制項自訂](control-customization.md)
