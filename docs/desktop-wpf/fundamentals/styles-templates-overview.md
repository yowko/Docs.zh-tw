---
title: 樣式及範本
description: 深入瞭解 .NET Core Windows Presentation Foundation (WPF) 的 XAML 資源。 瞭解與樣式和主題相關的 XAML 資源類型。
author: adegeo
ms.author: adegeo
ms.date: 09/09/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: 61cddfeb0d881ad2f2006db50ebb33f6a0c870ba
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90535432"
---
# <a name="styles-and-templates-in-wpf"></a>WPF 中的樣式和範本

Windows Presentation Foundation (WPF) 樣式設定和範本化參考一組功能，可讓開發人員和設計人員針對其產品建立視覺效果吸引人的效果和一致的外觀。 自訂應用程式的外觀時，您需要強大的樣式設定和範本化模型，讓您在應用程式內和應用程式之間進行維護和共用外觀。 WPF 會提供該模型。

WPF 樣式模型的另一項功能，就是展示和邏輯的分隔。 在開發人員使用 c # 或 Visual Basic 處理常式設計邏輯的同時，設計工具可以使用 XAML 來處理應用程式的外觀。

本總覽著重于應用程式的樣式設定和範本化層面，並不會討論任何資料系結概念。 如需有關資料繫結的資訊，請參閱[資料繫結概觀](../data/data-binding-overview.md)。

請務必瞭解資源，這些資源可讓您重複使用樣式和範本。 如需有關資源的詳細資訊，請參閱 [XAML 資源](xaml-resources-define.md)。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sample"></a>範例

本總覽中提供的範例程式碼是以 [簡單的相片流覽應用程式](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) 為基礎，如下圖所示。

![已設定樣式的 ListView](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

這個簡單的相片範例使用樣式設定和範本化，來創造引人注目的使用者體驗。 此範例有兩個 <xref:System.Windows.Controls.TextBlock> 元素，以及一個系結 <xref:System.Windows.Controls.ListBox> 至影像清單的控制項。

如需完整範例，請參閱[樣式設定和範本化範例簡介 (英文)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。

## <a name="styles"></a>樣式

您可以將 <xref:System.Windows.Style> 視為將一組屬性值套用至多個元素的方便方式。 您可以在任何衍生自或的專案上使用樣式， <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> 例如 <xref:System.Windows.Window> 或 <xref:System.Windows.Controls.Button> 。

宣告樣式最常見的方式，就是在 XAML 檔案中的區段中的資源 `Resources` 。 由於樣式是資源，因此它們會遵守適用于所有資源的相同範圍規則。 單純地說，您宣告的樣式會影響可以套用樣式的位置。 例如，如果您在應用程式定義 XAML 檔案的根項目中宣告樣式，則可以在應用程式中的任何位置使用該樣式。

例如，下列 XAML 程式碼會宣告兩種樣式 `TextBlock` ：一個自動套用至所有 `TextBlock` 元素，另一個則必須明確參考。

[!code-xaml[SnippetDefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

以下是使用上述宣告的樣式範例。

[!code-xaml[SnippetTextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

![樣式的 textblock](./media/styles-and-templates-overview/stylingintro-textblocks.png)

如需詳細資訊，請參閱 [建立控制項的樣式](styles-templates-create-apply-style.md)。

## <a name="controltemplates"></a>ControlTemplates

在 WPF 中， <xref:System.Windows.Controls.ControlTemplate> 控制項的會定義控制項的外觀。 您可以藉由定義新的控制項 <xref:System.Windows.Controls.ControlTemplate> 並將其指派給控制項，來變更控制項的結構和外觀。 在許多情況下，範本提供您足夠的彈性，因此您不必撰寫自己的自訂控制項。

每個控制項都有指派給 Control 的預設範本 [。 template](xref:System.Windows.Controls.Control.Template) 屬性。 此範本會將控制項的視覺呈現與控制項的功能連接在一起。 由於您是在 XAML 中定義範本，因此您可以變更控制項的外觀，而不需要撰寫任何程式碼。 每個範本都是針對特定的控制項（例如）所設計 <xref:System.Windows.Controls.Button> 。

您通常會在 XAML 檔案的區段上將範本宣告為資源 `Resources` 。 如同所有資源，適用範圍規則。

控制項範本與樣式有許多相關。 這是因為控制項範本會重寫整個控制項的視覺外觀，而樣式只會將屬性變更套用至現有的控制項。 不過，由於控制項的範本是藉由設定 [ [範本](xref:System.Windows.Controls.Control.Template) ] 屬性來套用，因此您可以使用樣式來定義或設定範本。

設計工具通常可讓您建立現有範本的複本並加以修改。 例如，在 Visual Studio WPF 設計工具中，選取 `CheckBox` 控制項，然後以滑鼠右鍵按一下並選取 [**編輯範本**  >  **建立複本**]。 此命令會產生 *可定義範本的樣式*。

```xaml
<Style x:Key="CheckBoxStyle1" TargetType="{x:Type CheckBox}">
    <Setter Property="FocusVisualStyle" Value="{StaticResource FocusVisual1}"/>
    <Setter Property="Background" Value="{StaticResource OptionMark.Static.Background1}"/>
    <Setter Property="BorderBrush" Value="{StaticResource OptionMark.Static.Border1}"/>
    <Setter Property="Foreground" Value="{DynamicResource {x:Static SystemColors.ControlTextBrushKey}}"/>
    <Setter Property="BorderThickness" Value="1"/>
    <Setter Property="Template">
        <Setter.Value>
            <ControlTemplate TargetType="{x:Type CheckBox}">
                <Grid x:Name="templateRoot" Background="Transparent" SnapsToDevicePixels="True">
                    <Grid.ColumnDefinitions>
                        <ColumnDefinition Width="Auto"/>
                        <ColumnDefinition Width="*"/>
                    </Grid.ColumnDefinitions>
                    <Border x:Name="checkBoxBorder" Background="{TemplateBinding Background}" BorderThickness="{TemplateBinding BorderThickness}" BorderBrush="{TemplateBinding BorderBrush}" HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="1" VerticalAlignment="{TemplateBinding VerticalContentAlignment}">
                        <Grid x:Name="markGrid">
                            <Path x:Name="optionMark" Data="F1 M 9.97498,1.22334L 4.6983,9.09834L 4.52164,9.09834L 0,5.19331L 1.27664,3.52165L 4.255,6.08833L 8.33331,1.52588e-005L 9.97498,1.22334 Z " Fill="{StaticResource OptionMark.Static.Glyph1}" Margin="1" Opacity="0" Stretch="None"/>
                            <Rectangle x:Name="indeterminateMark" Fill="{StaticResource OptionMark.Static.Glyph1}" Margin="2" Opacity="0"/>
                        </Grid>
                    </Border>
                    <ContentPresenter x:Name="contentPresenter" Grid.Column="1" Focusable="False" HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="{TemplateBinding Padding}" RecognizesAccessKey="True" SnapsToDevicePixels="{TemplateBinding SnapsToDevicePixels}" VerticalAlignment="{TemplateBinding VerticalContentAlignment}"/>
                </Grid>
                <ControlTemplate.Triggers>
                    <Trigger Property="HasContent" Value="true">
                        <Setter Property="FocusVisualStyle" Value="{StaticResource OptionMarkFocusVisual1}"/>
                        <Setter Property="Padding" Value="4,-1,0,0"/>

... content removed to save space ...
```

編輯範本的複本是瞭解範本運作方式的絕佳方式。 除了建立新的空白範本，您還可以更輕鬆地編輯複本並變更視覺效果簡報的一些層面。

如需範例，請參閱 [建立控制項的範本](../themes/how-to-create-apply-template.md)。

### <a name="templatebinding"></a>TemplateBinding

您可能已經注意到，在上一節中定義的範本資源使用 [TemplateBinding 標記延伸](/dotnet/desktop/wpf/advanced/templatebinding-markup-extension)。 `TemplateBinding`是範本案例的優化形式的系結，類似于使用所建立的系結 `{Binding RelativeSource={RelativeSource TemplatedParent}}` 。 `TemplateBinding` 適用于將範本的元件系結至控制項的屬性。 例如，每個控制項都有一個 <xref:System.Windows.Controls.Control.BorderThickness> 屬性。 使用 `TemplateBinding` 來管理範本中的哪個元素會受到此控制項設定的影響。

### <a name="contentcontrol-and-itemscontrol"></a>ContentControl 和 ItemsControl

如果 <xref:System.Windows.Controls.ContentPresenter> 在的中宣告，則會自動系結 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.ContentControl> <xref:System.Windows.Controls.ContentPresenter> 至 <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> 和 <xref:System.Windows.Controls.ContentControl.Content%2A> 屬性。 同樣地， <xref:System.Windows.Controls.ItemsPresenter> 在中的會 <xref:System.Windows.Controls.ControlTemplate> 自動系結 <xref:System.Windows.Controls.ItemsControl> 至 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 和 <xref:System.Windows.Controls.ItemsControl.Items%2A> 屬性。

## <a name="datatemplates"></a>DataTemplates

在此範例應用程式中，有一個系結 <xref:System.Windows.Controls.ListBox> 至相片清單的控制項。

[!code-xaml[ListBox](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window3.xaml#SnippetListBox)]

這 <xref:System.Windows.Controls.ListBox> 目前看起來如下所示。

![套用範本之前的 ListBox](./media/styles-and-templates-overview/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")

大多數控制項都有某個型別的內容，而該內容通常來自您要繫結的資料。 在此範例中，該資料是相片清單。 在 WPF 中，您可以使用 <xref:System.Windows.DataTemplate> 來定義資料的視覺標記法。 基本上，您放入的內容會 <xref:System.Windows.DataTemplate> 決定資料在轉譯應用程式中的樣子。

在我們的範例應用程式中，每個自訂 `Photo` 物件都有一個 `Source` 字串類型的屬性，可指定映射的檔案路徑。 目前，相片物件是顯示成檔案路徑。

[!code-csharp[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Photo.cs#PhotoClass)]
[!code-vb[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/Photo.vb#PhotoClass)]

若要讓相片以影像形式出現，您可以建立 <xref:System.Windows.DataTemplate> 做為資源。

[!code-xaml[DataTemplate](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window4.xaml#SnippetDataTemplate)]

請注意， <xref:System.Windows.DataTemplate.DataType%2A> 屬性與的屬性類似 <xref:System.Windows.Style.TargetType%2A> <xref:System.Windows.Style> 。 如果您 <xref:System.Windows.DataTemplate> 是在 resources 區段中，當您將 <xref:System.Windows.DataTemplate.DataType%2A> 屬性指定為型別並省略時 `x:Key` ， <xref:System.Windows.DataTemplate> 會在該型別出現時套用。 您一律可以使用指派給的選項， <xref:System.Windows.DataTemplate> `x:Key` 然後將它設定為 `StaticResource` 取得類型的屬性 <xref:System.Windows.DataTemplate> ，例如 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 屬性或 <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> 屬性。

基本上， <xref:System.Windows.DataTemplate> 上述範例中的會定義每次有物件時 `Photo` ，都應該在中顯示為 <xref:System.Windows.Controls.Image> <xref:System.Windows.Controls.Border> 。 如此一來 <xref:System.Windows.DataTemplate> ，我們的應用程式現在看起來會像這樣。

![圖片影像](./media/styles-and-templates-overview/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")

資料範本化模型還提供其他功能。 例如，如果您要顯示的集合資料包含使用 <xref:System.Windows.Controls.HeaderedItemsControl> 類型（例如或）的其他集合 <xref:System.Windows.Controls.Menu> ，則 <xref:System.Windows.Controls.TreeView> 會有 <xref:System.Windows.HierarchicalDataTemplate> 。 另一個資料範本化功能是 <xref:System.Windows.Controls.DataTemplateSelector> ，可讓您 <xref:System.Windows.DataTemplate> 根據自訂邏輯選擇要使用的。 如需詳細資訊，請參閱[資料範本化概觀](/dotnet/desktop/wpf/data/data-templating-overview)，其中提供不同資料範本化功能的更深入探討。

## <a name="triggers"></a>觸發程序

觸發程序會在屬性值發生變更或在某個事件被引發時，設定屬性或啟動動作 (例如動畫)。 <xref:System.Windows.Style>、 <xref:System.Windows.Controls.ControlTemplate> 和都 <xref:System.Windows.DataTemplate> 具有 `Triggers` 可包含一組觸發程式的屬性。 有數種類型的觸發程式。

### <a name="propertytriggers"></a>PropertyTriggers

<xref:System.Windows.Trigger>，會根據屬性的值來設定屬性值或啟動動作，稱為屬性觸發程式。

若要示範如何使用屬性觸發程式，您可以讓每個 <xref:System.Windows.Controls.ListBoxItem> 部分透明，除非已選取它。 下列樣式會將的 <xref:System.Windows.UIElement.Opacity%2A> 值設定 <xref:System.Windows.Controls.ListBoxItem> 為 `0.5` 。 但是，當 <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> 屬性是時， `true` <xref:System.Windows.UIElement.Opacity%2A> 會設定為 `1.0` 。

[!code-xaml[PropertyTrigger](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window5.xaml#SnippetPropertyTrigger)]

這個範例會使用 <xref:System.Windows.Trigger> 來設定屬性值，但請注意，此 <xref:System.Windows.Trigger> 類別也有 <xref:System.Windows.TriggerBase.EnterActions%2A> 和 <xref:System.Windows.TriggerBase.ExitActions%2A> 屬性可讓觸發程式執行動作。

請注意，的 <xref:System.Windows.FrameworkElement.MaxHeight%2A> 屬性 <xref:System.Windows.Controls.ListBoxItem> 會設定為 `75` 。 在下圖中，第三個專案是選取的專案。

![已設定樣式的 ListView](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

### <a name="eventtriggers-and-storyboards"></a>EventTrigger 和分鏡腳本

另一種類型的觸發程式是 <xref:System.Windows.EventTrigger> ，它會根據事件的發生次數來啟動一組動作。 例如，下列 <xref:System.Windows.EventTrigger> 物件指定當滑鼠指標進入時，屬性會在 <xref:System.Windows.Controls.ListBoxItem> <xref:System.Windows.FrameworkElement.MaxHeight%2A> `90` `0.2` 第二個句點的動畫上繪製成值。 當滑鼠指標從項目移開時，該屬性會在 `1` 秒的期間內恢復成原始值。 請注意，不需要指定 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 動畫的值 <xref:System.Windows.ContentElement.MouseLeave> 。 這是因為動畫能夠記錄原始值。

[!code-xaml[StyleEventTriggers](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window6.xaml#SnippetStyleEventTriggers)]

如需詳細資訊，請參閱分鏡腳本 [總覽](/dotnet/desktop/wpf/graphics-multimedia/storyboards-overview)。

在下圖中，滑鼠指向第三個專案。

![樣式範例螢幕擷取畫面](./media/styles-and-templates-overview/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>MultiTrigger、DataTrigger 及 MultiDataTrigger

除了 <xref:System.Windows.Trigger> 和 <xref:System.Windows.EventTrigger> 之外，還有其他類型的觸發程式。 <xref:System.Windows.MultiTrigger> 可讓您根據多個條件來設定屬性值。 <xref:System.Windows.DataTrigger> <xref:System.Windows.MultiDataTrigger> 當條件的屬性是資料系結時，您可以使用和。

## <a name="visual-states"></a>視覺狀態

控制項一律處於特定 **狀態**。 例如，當滑鼠移到控制項的介面上方時，控制項就會被視為處於的一般狀態 `MouseOver` 。 沒有特定狀態的控制項會被視為處於一般 `Normal` 狀態。 狀態分成群組，而先前提及的狀態是狀態群組的一部分 `CommonStates` 。 大部分的控制項都有兩個狀態群組： `CommonStates` 和 `FocusStates` 。 針對套用至控制項的每個狀態群組，控制項一律會處於每個群組的其中一個狀態，例如 `CommonStates.MouseOver` 和 `FocusStates.Unfocused` 。 不過，控制項不能在相同群組中的兩個不同狀態，例如 `CommonStates.Normal` 和 `CommonStates.Disabled` 。 以下是大部分控制項辨識和使用的狀態表格。

| VisualState 名稱 | VisualStateGroup 名稱 | 描述 |
| ---------------- | --------------------- | ----------- |
| 正常           | CommonStates          | 預設狀態。 |
| MouseOver        | CommonStates          | 滑鼠指標移到控制項上。 |
| 按下          | CommonStates          | 已按下控制項。 |
| 已停用         | CommonStates          | 已停用控制項。 |
| 已取得焦點          | FocusStates           | 控制項已取得焦點。 |
| 未取得焦點        | FocusStates           | 控制項未取得焦點。 |

藉由在 <xref:System.Windows.VisualStateManager?displayProperty=fullName> 控制項範本的根項目上定義，您就可以在控制項進入特定狀態時觸發動畫。 會宣告要 `VisualStateManager` <xref:System.Windows.VisualStateGroup> 監看的和的組合 <xref:System.Windows.VisualState> 。 當控制項進入監看的狀態時，就會啟動所定義的動畫 `VisaulStateManager` 。

例如，下列 XAML 程式碼會監看 `CommonStates.MouseOver` 狀態，以建立名為之元素填滿色彩的動畫 `backgroundElement` 。 當控制項返回 `CommonStates.Normal` 狀態時，會還原名為的專案之填滿色彩 `backgroundElement` 。

```xaml
<ControlTemplate x:Key="roundbutton" TargetType="Button">
    <Grid>
        <VisualStateManager.VisualStateGroups>
            <VisualStateGroup Name="CommonStates">
                <VisualState Name="Normal">
                    <ColorAnimation Storyboard.TargetName="backgroundElement"
                                    Storyboard.TargetProperty="(Shape.Fill).(SolidColorBrush.Color)"
                                    To="{TemplateBinding Background}"
                                    Duration="0:0:0.3"/>
                </VisualState>
                <VisualState Name="MouseOver">
                    <ColorAnimation Storyboard.TargetName="backgroundElement"
                                    Storyboard.TargetProperty="(Shape.Fill).(SolidColorBrush.Color)"
                                    To="Yellow"
                                    Duration="0:0:0.3"/>
                </VisualState>
            </VisualStateGroup>
        </VisualStateManager.VisualStateGroups>

        ...
```

如需分鏡腳本的詳細資訊，請參閱分鏡腳本 [總覽](/dotnet/desktop/wpf/graphics-multimedia/storyboards-overview)。

## <a name="shared-resources-and-themes"></a>共用的資源和主題

一般的 WPF 應用程式可能會有多個在應用程式中套用的 UI 資源。 這組資源統稱可視為應用程式的主題。 WPF 支援使用封裝為類別的資源字典，將 UI 資源封裝成主題 <xref:System.Windows.ResourceDictionary> 。

WPF 主題的定義方式是使用 WPF 為了自訂任何專案的視覺效果所公開的樣式設定和範本化機制。

WPF 主題資源會儲存在內嵌的資源字典中。 這些資源字典必須內嵌在已簽署的組件內，並且可內嵌在與程式碼本身相同的組件中，也可內嵌在並存的組件中。 針對 PresentationFramework.dll，包含 WPF 控制項的元件，主題資源是在一系列並存元件中。

當搜尋元素的樣式時，佈景主題會成為最後一個要查看的地方。 搜尋通常會先向上找出搜尋適當資源的專案樹狀結構，然後查看應用程式資源集合，最後再查詢系統。 這可讓應用程式開發人員有機會在到達主題之前，先重新定義樹狀結構或應用層級上任何物件的樣式。

您可以將資源字典定義為個別檔案，讓您可以跨多個應用程式重複使用主題。 您也可以透過定義多個資源字典來提供類型相同但值不同的資源，以建立可切換的佈景主題。 在應用層級重新定義這些樣式或其他資源，是將應用程式用於外觀的建議方式。

若要在應用程式之間共用一組資源，包括樣式和範本，您可以建立 XAML 檔案並定義 <xref:System.Windows.ResourceDictionary> 包含檔案參考的 `shared.xaml` 。

```xaml
<ResourceDictionary.MergedDictionaries>
  <ResourceDictionary Source="Shared.xaml" />
</ResourceDictionary.MergedDictionaries>
```

它是的共用 `shared.xaml` ，它本身會定義 <xref:System.Windows.ResourceDictionary> 包含一組樣式和筆刷資源的，讓應用程式中的控制項能夠有一致的外觀。

如需詳細資訊，請參閱 [合併的資源字典](/dotnet/desktop/wpf/advanced/merged-resource-dictionaries)。

如果您要建立自訂控制項的主題，請參閱[控制項撰寫總覽](/dotnet/desktop/wpf/controls/control-authoring-overview#defining-resources-at-the-theme-level)的**主題層級的定義資源**一節。

## <a name="see-also"></a>另請參閱

- [WPF 中的 Pack URI](/dotnet/desktop/wpf/app-development/pack-uris-in-wpf)
- [作法：尋找 ControlTemplate 產生的元素](/dotnet/desktop/wpf/controls/how-to-find-controltemplate-generated-elements)
- [尋找 DataTemplate 產生的元素](/dotnet/desktop/wpf/data/how-to-find-datatemplate-generated-elements)
