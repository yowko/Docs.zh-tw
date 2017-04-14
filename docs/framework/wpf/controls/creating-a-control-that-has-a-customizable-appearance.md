---
title: "建立外觀可自訂的控制項 | Microsoft Docs"
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
  - "控制項 [WPF], 自訂"
  - "控制項 [WPF], 定義視覺結構和行為"
  - "ControlTemplate [WPF], 自訂外觀"
  - "自訂外觀 [WPF], ControlTemplate"
  - "管理控制項狀態 [WPF], VisualStateManager"
  - "VisualStateManager [WPF], 最佳作法"
  - "VisualStateManager [WPF], 管理控制項的狀態"
ms.assetid: 9e356d3d-a3d0-4b01-a25f-2d43e4d53fe5
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 建立外觀可自訂的控制項
<a name="introduction"></a> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 能夠讓您建立外觀可加以自訂的控制項。  例如，您可以透過建立新的 <xref:System.Windows.Controls.ControlTemplate> 來變更 <xref:System.Windows.Controls.CheckBox> 的外觀，功能遠比設定屬性來得強大。  下圖顯示使用預設 <xref:System.Windows.Controls.ControlTemplate> 的 <xref:System.Windows.Controls.CheckBox>，以及使用自訂 <xref:System.Windows.Controls.ControlTemplate> 的 <xref:System.Windows.Controls.CheckBox>。  
  
 ![具有預設控制項範本的核取方塊。](../../../../docs/framework/wpf/controls/media/ndp-checkboxdefault.png "NDP\_CheckBoxDefault")  
使用預設控制項樣板的 CheckBox  
  
 ![具有自訂控制項範本的核取方塊。](../../../../docs/framework/wpf/controls/media/ndp-checkboxcustom.png "NDP\_CheckBoxCustom")  
使用自訂控制項樣板的 CheckBox  
  
 如果在建立控制項時遵循組件和狀態模型，您的控制項外觀將可以自訂。  Microsoft Expression Blend 這類設計工具支援組件和狀態模型，所以當您遵循此模型時，將可在這些類型的應用程式中自訂控制項。  本主題討論組件和狀態模型，以及如何在建立您自己的控制項時遵循模型。  本主題使用自訂控制項範例 `NumericUpDown` 說明本模型的原理。  `NumericUpDown` 控制項會顯示一個數值，使用者可以藉由按一下控制項的按鈕而增加或減少其值。  下圖顯示本主題中所討論的 `NumericUpDown` 控制項。  
  
 ![NumericUpDown 自訂控制項。](../../../../docs/framework/wpf/controls/media/ndp-numericupdown.png "NDP\_NumericUPDown")  
自訂的 NumericUpDown 控制項  
  
 此主題包括下列章節：  
  
-   [必要條件](#prerequisites)  
  
-   [組件和狀態模型](#parts_and_states_model)  
  
-   [在 ControlTemplate 中定義控制項的視覺化結構和視覺化行為](#defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate)  
  
-   [在程式碼中使用 ControlTemplate 的組件](#using_parts_of_the_controltemplate_in_code)  
  
-   [提供控制項合約](#providing_the_control_contract)  
  
-   [完整範例](#complete_example)  
  
<a name="prerequisites"></a>   
## 必要條件  
 本主題假設您已知道如何為現有控制項建立新的 <xref:System.Windows.Controls.ControlTemplate>、熟悉控制項合約上的項目，並了解[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)中所討論的概念。  
  
> [!NOTE]
>  若要建立外觀可自訂的控制項，您建立的控制項必須繼承自 <xref:System.Windows.Controls.Control> 類別或 <xref:System.Windows.Controls.UserControl> 以外的其中一個子類別。  繼承自 <xref:System.Windows.Controls.UserControl> 的控制項是可以快速建立的控制項，但是它不使用 <xref:System.Windows.Controls.ControlTemplate>，所以您無法自訂其外觀。  
  
<a name="parts_and_states_model"></a>   
## 組件和狀態模型  
 組件和狀態模型指定如何定義控制項的視覺化結構和視覺化行為。  若要遵循組件和狀態模型，您應該執行下列作業：  
  
-   在控制項的 <xref:System.Windows.Controls.ControlTemplate> 中定義視覺化結構和視覺化行為。  
  
-   當控制項邏輯與控制項範本的組件互動時，遵循特定的最佳做法。  
  
-   提供控制項合約，指定 <xref:System.Windows.Controls.ControlTemplate> 中應包括哪些項目。  
  
 在控制項的 <xref:System.Windows.Controls.ControlTemplate> 中定義視覺化結構和視覺化行為之後，應用程式作者即可藉由建立新的 <xref:System.Windows.Controls.ControlTemplate> 變更控制項的視覺化結構和視覺化行為，而不需要撰寫程式碼。  您必須提供控制項合約，用以告知應用程式作者應在 <xref:System.Windows.Controls.ControlTemplate> 中定義哪些 <xref:System.Windows.FrameworkElement> 物件和狀態。  與 <xref:System.Windows.Controls.ControlTemplate> 中的組件互動時應遵循某些最佳做法，您的控制項才能正確處理不完整的 <xref:System.Windows.Controls.ControlTemplate>。  如果您遵循上述三個原則，應用程式作者便能夠為您的控制項建立 <xref:System.Windows.Controls.ControlTemplate>，過程就如同為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 隨附的控制項建立控制項範本一樣簡單。  下一節將詳細說明每項建議。  
  
<a name="defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate"></a>   
## 在 ControlTemplate 中定義控制項的視覺化結構和視覺化行為  
 使用組件和狀態模型建立您自訂的控制項時，請在控制項的 <xref:System.Windows.Controls.ControlTemplate> 中定義其視覺化結構和視覺化行為，而不要在其邏輯中定義。  控制項的視覺化結構是組成控制項之 <xref:System.Windows.FrameworkElement> 物件的複合。  視覺化行為則是控制項處於特定狀態時的顯示方式。  如需建立 <xref:System.Windows.Controls.ControlTemplate> 以指定控制項之視覺化結構和視覺化行為的詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。  
  
 在 `NumericUpDown` 控制項的範例中，視覺化結構包括兩個 <xref:System.Windows.Controls.Primitives.RepeatButton> 控制項和一個 <xref:System.Windows.Controls.TextBlock>。  如果您將這些控制項加入 `NumericUpDown` 控制項的程式碼中 \(例如加入其建構函式中\)，則控制項的位置將無法改變。  因此，請不要在控制項的程式碼中定義控制項的視覺化結構和視覺化行為，而是在 <xref:System.Windows.Controls.ControlTemplate> 中定義。  接著應用程式開發人員就能自訂按鈕位置和 <xref:System.Windows.Controls.TextBlock>，並指定當 `Value` 為負時應發生的行為，因為 <xref:System.Windows.Controls.ControlTemplate> 是可以取代的。  
  
 下列範例顯示 `NumericUpDown` 控制項的視覺化結構，其中包括一個增加 `Value` 的 <xref:System.Windows.Controls.Primitives.RepeatButton>、一個減少 `Value` 的 <xref:System.Windows.Controls.Primitives.RepeatButton>，以及一個用來顯示 `Value` 的 <xref:System.Windows.Controls.TextBlock>。  
  
 [!code-xml[VSMCustomControl#VisualStructure](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#visualstructure)]  
  
 `NumericUpDown` 控制項有一項視覺化行為是，當值為負時，以紅色字型顯示該值。  如果您在 `Value` 為負時變更程式碼中 <xref:System.Windows.Controls.TextBlock> 的 <xref:System.Windows.Controls.TextBlock.Foreground%2A>，則 `NumericUpDown` 會永遠顯示紅色的負值。  您可以在 <xref:System.Windows.Controls.ControlTemplate> 中加入 <xref:System.Windows.VisualState> 物件，藉此在 <xref:System.Windows.Controls.ControlTemplate> 中指定控制項的視覺化行為。  下列範例顯示 `Positive` 和 `Negative` 狀態的 <xref:System.Windows.VisualState> 物件。  `Positive` 和 `Negative` 彼此互斥 \(表示控制項必定處於這兩種狀態其中一種\)，所以範例會將 <xref:System.Windows.VisualState> 物件置於單一 <xref:System.Windows.VisualStateGroup> 中。  當控制項進入 `Negative` 狀態時，<xref:System.Windows.Controls.TextBlock> 的 <xref:System.Windows.Controls.TextBlock.Foreground%2A> 就會變成紅色。  當控制項處於 `Positive` 狀態時，<xref:System.Windows.Controls.TextBlock.Foreground%2A> 又會恢復其原始值。  [透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)中會進一步討論在 <xref:System.Windows.Controls.ControlTemplate> 中定義 <xref:System.Windows.VisualState> 物件。  
  
> [!NOTE]
>  請務必在 <xref:System.Windows.Controls.ControlTemplate> 的根 <xref:System.Windows.FrameworkElement> 上設定 <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=fullName> 附加屬性。  
  
 [!code-xml[VSMCustomControl#ValueStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
<a name="using_parts_of_the_controltemplate_in_code"></a>   
## 在程式碼中使用 ControlTemplate 的組件  
 <xref:System.Windows.Controls.ControlTemplate> 作者可能會故意或不小心省略了 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.VisualState> 物件，但控制項邏輯可能需要這些組件才能正常運作。  組件和狀態模型可指定控制項應該對遺失 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.VisualState> 物件的 <xref:System.Windows.Controls.ControlTemplate> 保持彈性，  也就是說，當 <xref:System.Windows.Controls.ControlTemplate> 中遺失 <xref:System.Windows.FrameworkElement>、<xref:System.Windows.VisualState> 或 <xref:System.Windows.VisualStateGroup> 時，控制項不應擲回例外狀況或報告錯誤。  本節說明與 <xref:System.Windows.FrameworkElement> 物件互動以及管理狀態的建議做法。  
  
### 預測遺失的 FrameworkElement 物件  
 在 <xref:System.Windows.Controls.ControlTemplate> 中定義 <xref:System.Windows.FrameworkElement> 物件時，控制項邏輯可能需要與其中某些物件互動。  例如，`NumericUpDown` 控制項訂閱按鈕的 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件以便增加或減少 `Value`，並將 <xref:System.Windows.Controls.TextBlock> 的 <xref:System.Windows.Controls.TextBlock.Text%2A> 屬性設為 `Value`。  如果自訂的 <xref:System.Windows.Controls.ControlTemplate> 省略 <xref:System.Windows.Controls.TextBlock> 或按鈕，控制項會損失部分功能但仍可接受，不過您應該要確定控制項不會因此造成錯誤。  例如，如果 <xref:System.Windows.Controls.ControlTemplate> 不含可變更 `Value` 的按鈕，則 `NumericUpDown` 會失去功能，但使用此 <xref:System.Windows.Controls.ControlTemplate> 的應用程式仍可繼續執行。  
  
 下列做法可確保您的控制項正確回應遺失的 <xref:System.Windows.FrameworkElement> 物件：  
  
1.  為程式碼中需要參考的每個 <xref:System.Windows.FrameworkElement> 設定 `x:Name` 屬性 \(Attribute\)。  
  
2.  為需要進行互動的每個 <xref:System.Windows.FrameworkElement> 定義私用屬性 \(Property\)。  
  
3.  在 <xref:System.Windows.FrameworkElement> 屬性 \(Property\) 的 set 存取子中訂閱控制項要處理的事件，再取消訂閱。  
  
4.  在 <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> 方法中設定您在步驟 2 中定義的 <xref:System.Windows.FrameworkElement> 屬性 \(Property\)。  這是控制項最早能接觸到 <xref:System.Windows.Controls.ControlTemplate> 中 <xref:System.Windows.FrameworkElement> 的地方。  使用 <xref:System.Windows.FrameworkElement> 的 `x:Name`，從 <xref:System.Windows.Controls.ControlTemplate> 取得此值。  
  
5.  在存取 <xref:System.Windows.FrameworkElement> 的成員之前，先檢查其是否為 `null`。  如果為 `null`，不會報告錯誤。  
  
 下列範例顯示 `NumericUpDown` 控制項如何以符合上列建議的方式，來與 <xref:System.Windows.FrameworkElement> 物件互動。  
  
 在 <xref:System.Windows.Controls.ControlTemplate> 中定義 `NumericUpDown` 控制項之視覺化結構的範例中，<xref:System.Windows.Controls.Primitives.RepeatButton> \(用於增加 `Value`\) 的 `x:Name` 屬性 \(Attribute\) 設為 `UpButton`。  下列範例宣告一個名為 `UpButtonElement` 的屬性 \(Property\)，代表在 <xref:System.Windows.Controls.ControlTemplate> 中宣告的 <xref:System.Windows.Controls.Primitives.RepeatButton>。  如果 `UpDownElement` 不是 `null`，則 `set` 存取子會先取消訂閱按鈕的 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件、接著設定屬性，然後再訂閱 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件。  另外也會為另一個 <xref:System.Windows.Controls.Primitives.RepeatButton> 定義一個名為 `DownButtonElement` 的屬性，但不會在此處顯示。  
  
 [!code-csharp[VSMCustomControl#UpButtonProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#upbuttonproperty)]
 [!code-vb[VSMCustomControl#UpButtonProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#upbuttonproperty)]  
  
 下列範例顯示 `NumericUpDown` 控制項的 <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>。  此範例使用 <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> 方法取得 <xref:System.Windows.Controls.ControlTemplate> 中的 <xref:System.Windows.FrameworkElement> 物件。  請注意，此範例會預防 <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> 找到具有指定名稱之 <xref:System.Windows.FrameworkElement> 但型別不正確的情節。  這也是忽略具有指定之 `x:Name` 但型別錯誤之項目的最佳做法。  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 遵循以上範例中所顯示的做法，即可確保當 <xref:System.Windows.Controls.ControlTemplate> 遺失 <xref:System.Windows.FrameworkElement> 時，您的控制項仍可繼續執行。  
  
### 使用 VisualStateManager 管理狀態  
 <xref:System.Windows.VisualStateManager> 會記錄控制項的狀態，並執行在狀態間轉換時所需的邏輯。  將 <xref:System.Windows.VisualState> 物件加入至 <xref:System.Windows.Controls.ControlTemplate> 時，應將這些物件加入至 <xref:System.Windows.VisualStateGroup>，然後將 <xref:System.Windows.VisualStateGroup> 加入 <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=fullName> 附加屬性，如此 <xref:System.Windows.VisualStateManager> 就能存取這些物件。  
  
 下列範例會重複之前的範例，根據控制項的 `Positive` 和 `Negative` 狀態顯示 <xref:System.Windows.VisualState> 物件。  `Negative` <xref:System.Windows.VisualState> 中的 <xref:System.Windows.Media.Animation.Storyboard> 會將 <xref:System.Windows.Controls.TextBlock> 的 <xref:System.Windows.Controls.TextBlock.Foreground%2A> 轉為紅色。  當 `NumericUpDown` 控制項位於 `Negative` 狀態時，`Negative` 狀態中的 Storyboard 便會啟動。  而當控制項回復 `Positive` 狀態時，`Negative` 狀態中的 <xref:System.Windows.Media.Animation.Storyboard> 就會停止。  `Positive` <xref:System.Windows.VisualState> 不需要包含 <xref:System.Windows.Media.Animation.Storyboard>，因為當 `Negative` 的 <xref:System.Windows.Media.Animation.Storyboard> 停止時，<xref:System.Windows.Controls.TextBlock.Foreground%2A> 就會恢復其原始顏色。  
  
 [!code-xml[VSMCustomControl#ValueStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
 請注意，<xref:System.Windows.Controls.TextBlock> 會加以命名，但是 <xref:System.Windows.Controls.TextBlock> 不在 `NumericUpDown` 的控制項合約中，因為控制項的邏輯絕不會參考 <xref:System.Windows.Controls.TextBlock>。  雖然 <xref:System.Windows.Controls.ControlTemplate> 中參考的項目都有名稱，但是不一定要是控制項合約的一部分，因為控制項的新 <xref:System.Windows.Controls.ControlTemplate> 可能不需要參考該項目。  例如，為 `NumericUpDown` 建立新 <xref:System.Windows.Controls.ControlTemplate> 的人可能決定不藉由變更 <xref:System.Windows.Controls.Control.Foreground%2A> 的方式指出 `Value` 是負的。  在這種情況下，程式碼和 <xref:System.Windows.Controls.ControlTemplate> 都不會透過名稱參考 <xref:System.Windows.Controls.TextBlock>。  
  
 控制項邏輯負責變更控制項的狀態。  下列範例顯示當 `Value` 大於或等於 0 時，`NumericUpDown` 控制項會呼叫 <xref:System.Windows.VisualStateManager.GoToState%2A> 方法進入 `Positive` 狀態，而當 `Value` 小於 0 時則進入 `Negative` 狀態。  
  
 [!code-csharp[VSMCustomControl#ValueStateChange](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#valuestatechange)]
 [!code-vb[VSMCustomControl#ValueStateChange](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#valuestatechange)]  
  
 <xref:System.Windows.VisualStateManager.GoToState%2A> 方法會執行正確啟動和停止 Storyboard 所需的邏輯。  當控制項呼叫 <xref:System.Windows.VisualStateManager.GoToState%2A> 變更其狀態時，<xref:System.Windows.VisualStateManager> 會進行下列作業：  
  
-   如果控制項將進入的 <xref:System.Windows.VisualState> 具有 <xref:System.Windows.Media.Animation.Storyboard>，Storyboard 就會啟動。  接著，如果控制項將離開的 <xref:System.Windows.VisualState> 具有 <xref:System.Windows.Media.Animation.Storyboard>，Storyboard 就會停止。  
  
-   如果控制項已經處於指定的狀態中，<xref:System.Windows.VisualStateManager.GoToState%2A> 不會採取任何動作，並且會傳回 `true`。  
  
-   如果指定的狀態不存在於 `control` 的 <xref:System.Windows.Controls.ControlTemplate> 中，則 <xref:System.Windows.VisualStateManager.GoToState%2A> 不會採取任何動作，並且會傳回 `false`。  
  
#### 使用 VisualStateManager 的最佳做法  
 建議您執行下列作業來維持控制項的狀態：  
  
-   使用屬性追蹤其狀態。  
  
-   建立 Helper 方法以在狀態之間轉換。  
  
 `NumericUpDown` 控制項會使用 `Value` 屬性來追蹤它是處於 `Positive` 或 `Negative` 狀態。  `NumericUpDown` 控制項還會定義 `Focused` 和 `UnFocused` 狀態，用來追蹤 <xref:System.Windows.UIElement.IsFocused%2A> 屬性。  如果您使用的狀態並未自然回應控制項的屬性，可以定義私用屬性來追蹤狀態。  
  
 更新所有狀態的單一方法會集中呼叫 <xref:System.Windows.VisualStateManager>，並且讓您的程式碼維持在可管理的範圍內。  下列範例顯示 `NumericUpDown` 控制項的 Helper 方法 `UpdateStates`。  當 `Value` 大於或等於 0 時，<xref:System.Windows.Controls.Control> 處於 `Positive` 狀態。  當 `Value` 小於 0 時，控制項處於 `Negative` 狀態。  當 <xref:System.Windows.UIElement.IsFocused%2A> 為 `true` 時，控制項會處於 `Focused` 狀態；否則為 `Unfocused` 狀態。  控制項可以在需要變更狀態時呼叫 `UpdateStates`，無論狀態變更為何。  
  
 [!code-csharp[VSMCustomControl#UpdateStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#updatestates)]
 [!code-vb[VSMCustomControl#UpdateStates](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#updatestates)]  
  
 如果您傳遞給 <xref:System.Windows.VisualStateManager.GoToState%2A> 的狀態名稱為控制項所處的狀態，則 <xref:System.Windows.VisualStateManager.GoToState%2A> 不會執行任何動作，所以您不需要檢查控制項的目前狀態。  例如，如果 `Value` 從一個負數變更為另一個負數，則 `Negative` 狀態的 Storyboard 不會中斷，使用者也不會看到控制項出現任何變更。  
  
 當您呼叫 <xref:System.Windows.VisualStateManager.GoToState%2A> 時，<xref:System.Windows.VisualStateManager> 會使用 <xref:System.Windows.VisualStateGroup> 物件判斷要離開哪個狀態。  控制項在每一個於 <xref:System.Windows.Controls.ControlTemplate> 定義的 <xref:System.Windows.VisualStateGroup> 中都會處於某一種狀態，而只有在同一 <xref:System.Windows.VisualStateGroup> 中進入另一種狀態時，才會離開該狀態。  例如，`NumericUpDown` 控制項的 <xref:System.Windows.Controls.ControlTemplate> 在某個 <xref:System.Windows.VisualStateGroup> 中定義了 `Positive` 和 `Negative` <xref:System.Windows.VisualState> 物件，並在另一個群組中定義了 `Focused` 和 `Unfocused` <xref:System.Windows.VisualState> 物件。  您可以在本主題中看見[完整範例](#complete_example)一節中定義的 `Focused` 和 `Unfocused` <xref:System.Windows.VisualState>。當控制項從 `Positive` 狀態進入 `Negative` 狀態 \(或反向變更\) 時，控制項會保持為 `Focused` 或 `Unfocused` 狀態。  
  
 控制項狀態可能發生變更的典型位置有以下三個：  
  
-   當 <xref:System.Windows.Controls.ControlTemplate> 套用至 <xref:System.Windows.Controls.Control> 時。  
  
-   當屬性變更時。  
  
-   當事件發生時。  
  
 下列範例示範更新上述情形中的 `NumericUpDown` 控制項狀態。  
  
 您應該在 <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> 方法中更新控制項狀態，如此當套用 <xref:System.Windows.Controls.ControlTemplate> 時控制項才會出現在正確狀態中。  下列範例會在 <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> 中呼叫 `UpdateStates`，以確保控制項處於正確狀態。  例如，假設您建立了 `NumericUpDown` 控制項，然後將它的 <xref:System.Windows.Controls.Control.Foreground%2A> 設為綠色以及 `Value` 設為 \-5。  如果您在 <xref:System.Windows.Controls.ControlTemplate> 套用至 `NumericUpDown` 控制項時未呼叫 `UpdateStates`，則控制項不會處於 `Negative` 狀態，而且值將是綠色，不是紅色。  您必須呼叫 `UpdateStates` 以將控制項放到 `Negative` 狀態。  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 當屬性變更時，您經常需要更新控制項狀態。  下列範例顯示完整的 `ValueChangedCallback` 方法。  由於 `ValueChangedCallback` 是在 `Value` 變更時呼叫，因此方法會在 `Value` 從正值變為負值 \(或相反\) 時呼叫 `UpdateStates`。  當 `Value` 有所變更但仍維持正值或負值時，仍然可以呼叫 `UpdateStates`，因為在這種情況下控制項並不會變更狀態。  
  
 [!code-csharp[VSMCustomControl#EntireValueChangedCallback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#entirevaluechangedcallback)]
 [!code-vb[VSMCustomControl#EntireValueChangedCallback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#entirevaluechangedcallback)]  
  
 發生事件時，您可能也需要更新狀態。  下列範例顯示 `NumericUpDown` 在 <xref:System.Windows.Controls.Control> 上呼叫 `UpdateStates`，以處理 <xref:System.Windows.UIElement.GotFocus> 事件。  
  
 [!code-csharp[VSMCustomControl#OnGotFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#ongotfocus)]
 [!code-vb[VSMCustomControl#OnGotFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#ongotfocus)]  
  
 <xref:System.Windows.VisualStateManager> 可協助您管理控制項狀態。  藉由使用 <xref:System.Windows.VisualStateManager>，可以確保控制項正確轉換其狀態。  如果您在使用 <xref:System.Windows.VisualStateManager> 時遵循本節所述建議，您的控制項程式碼將可維持可讀性並且易於維護。  
  
<a name="providing_the_control_contract"></a>   
## 提供控制項合約  
 您可以提供控制項合約，這樣可讓 <xref:System.Windows.Controls.ControlTemplate> 作者了解範本中包括哪些項目。  控制項合約有三個項目：  
  
-   控制項邏輯使用的視覺化項目。  
  
-   控制項的狀態，以及每一種狀態所屬的群組。  
  
-   影響控制項視覺外觀的公用屬性。  
  
 建立新的 <xref:System.Windows.Controls.ControlTemplate> 時，需要知道控制項邏輯使用哪些 <xref:System.Windows.FrameworkElement> 物件、每個物件的所屬型別，以及其名稱為何。  <xref:System.Windows.Controls.ControlTemplate> 作者也需要知道控制項會進入的每個可能狀態之名稱，以及狀態屬於哪個 <xref:System.Windows.VisualStateGroup>。  
  
 回到 `NumericUpDown` 範例，控制項預期 <xref:System.Windows.Controls.ControlTemplate> 擁有下列 <xref:System.Windows.FrameworkElement> 物件：  
  
-   名為 `UpButton` 的 <xref:System.Windows.Controls.Primitives.RepeatButton>。  
  
-   名為 `DownButton.` 的 <xref:System.Windows.Controls.Primitives.RepeatButton>。  
  
 控制項可以處於下列狀態：  
  
-   屬於 `ValueStates` <xref:System.Windows.VisualStateGroup>  
  
    -   `Positive`  
  
    -   `Negative`  
  
-   屬於 `FocusStates` <xref:System.Windows.VisualStateGroup>  
  
    -   `Focused`  
  
    -   `Unfocused`  
  
 若要指定控制項應預期哪些 <xref:System.Windows.FrameworkElement> 物件，請使用 <xref:System.Windows.TemplatePartAttribute> 指定預期項目的名稱和型別。  若要指定控制項的可能狀態，請使用 <xref:System.Windows.TemplateVisualStateAttribute> 指定狀態的名稱以及狀態所屬的 <xref:System.Windows.VisualStateGroup>。  將 <xref:System.Windows.TemplatePartAttribute> 和 <xref:System.Windows.TemplateVisualStateAttribute> 放入控制項的類別定義。  
  
 任何會影響控制項外觀的公用屬性，也都是控制項合約的一部分。  
  
 下列範例指定 `NumericUpDown` 控制項的 <xref:System.Windows.FrameworkElement> 物件和狀態。  
  
 [!code-csharp[VSMCustomControl#ControlContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controlcontract)]
 [!code-vb[VSMCustomControl#ControlContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controlcontract)]  
  
<a name="complete_example"></a>   
## 完整範例  
 下列範例是 `NumericUpDown` 控制項的完整 <xref:System.Windows.Controls.ControlTemplate>。  
  
 [!code-xml[VSMCustomControl#NUDTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/themes/generic.xaml#nudtemplate)]  
  
 下列範例顯示 `NumericUpDown` 的邏輯。  
  
 [!code-csharp[VSMCustomControl#ControlLogic](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controllogic)]
 [!code-vb[VSMCustomControl#ControlLogic](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controllogic)]  
  
## 請參閱  
 [透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)   
 [控制項自訂](../../../../docs/framework/wpf/controls/control-customization.md)