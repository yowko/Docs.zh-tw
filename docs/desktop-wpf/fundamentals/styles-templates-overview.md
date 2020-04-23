---
title: 樣式及範本
description: 瞭解 .NET Core 的 Windows 演示基礎 (WPF) 中的 XAML 資源。 瞭解與樣式和主題相關的 XAML 資源類型。
author: thraka
ms.author: adegeo
ms.date: 09/09/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: f845e739ec3cae502d1e4fd6631f987c5364a42e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071882"
---
# <a name="styles-and-templates-in-wpf"></a>WPF 中的樣式和樣本

Windows 示範基礎 (WPF) 樣式和範本化是指一組功能,這些功能使開發人員和設計人員能夠為其產品創建視覺上引人注目的效果和一致的外觀。 自定義應用的外觀時,您需要一個強大的樣式和範本模型,以便維護和共用應用內部和應用程式之間的外觀。 WPF 提供該模型。

WPF 樣式模型的另一個功能是表示和邏輯的分離。 設計人員可以同時使用 XAML 處理應用的外觀,而開發人員則使用 C# 或 Visual Basic 處理程式設計邏輯。

此概述側重於應用程式的樣式和範本化方面,不討論任何數據綁定概念。 如需有關資料繫結的資訊，請參閱[資料繫結概觀](../data/data-binding-overview.md)。

瞭解資源非常重要,這些資源使樣式和範本能夠重複使用。 如需有關資源的詳細資訊，請參閱 [XAML 資源](xaml-resources-define.md)。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sample"></a>範例

這個概述中提供的範例碼以下圖的[簡單照片瀏覽應用程式](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。

![已設定樣式的 ListView](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

這個簡單的相片範例使用樣式設定和範本化，來創造引人注目的使用者體驗。 該範例具有兩<xref:System.Windows.Controls.TextBlock>個元素和<xref:System.Windows.Controls.ListBox>一個綁定到圖像清單的控制項。

如需完整範例，請參閱[樣式設定和範本化範例簡介 (英文)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。

## <a name="styles"></a>樣式

可以將<xref:System.Windows.Style>a 視為將一組屬性值應用於多個元素的便捷方法。 <xref:System.Windows.FrameworkElement>可以在派生自<xref:System.Windows.FrameworkContentElement>或<xref:System.Windows.Window>或 或的任何元素上使用<xref:System.Windows.Controls.Button>樣式。

聲明樣式的最常見方法是作為 XAML`Resources`檔中 部分中的資源。 因為樣式是資源,因此它們遵循適用於所有資源的相同範圍規則。 簡單地說,聲明樣式會影響樣式的應用位置。 例如,如果在應用定義 XAML 檔的根元素中聲明樣式,則可以在應用中的任意位置使用該樣式。

例如,以下 XAML 代碼聲明的兩個`TextBlock`樣式`TextBlock`為 a , 一個自動應用於所有元素, 另一個必須顯式引用。

[!code-xaml[SnippetDefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

下面是上面聲明使用的樣式的示例。

[!code-xaml[SnippetTextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

![樣式化文字塊](./media/styles-and-templates-overview/stylingintro-textblocks.png)

有關詳細資訊,請參閱為[控制項建立樣式](styles-templates-create-apply-style.md)。

## <a name="controltemplates"></a>ControlTemplates

在 WPF<xref:System.Windows.Controls.ControlTemplate>中,控制件的定義控制件的外觀。 您可以通過定義<xref:System.Windows.Controls.ControlTemplate>新 控制件並將其分配給控制項來更改控制項的結構和外觀。 在許多情況下,範本為您提供足夠的靈活性,因此您不必編寫自己的自定義控制項。

每個控制項都有一個預設樣本分配給[控制項.Template](xref:System.Windows.Controls.Control.Template)屬性。 該範本將控制件的可視化表示與控制項的功能連接起來。 由於在 XAML 中定義範本,因此無需編寫任何代碼即可更改控制項的外觀。 每個樣本都專為特定控制項而設計,<xref:System.Windows.Controls.Button>例如 。

通常,在 XAML`Resources`檔部分將範本聲明為資源。 與所有資源一樣,範圍規則適用。

控件範本比樣式涉及更多。 這是因為控制項樣本重寫整個控制項的可視外觀,而樣式只是將屬性更改應用於現有控制項。 但是,由於控件的範本是通過設置[Control.template](xref:System.Windows.Controls.Control.Template)屬性應用的,因此可以使用樣式來定義或設置範本。

設計器通常允許您創建現有範本的副本並對其進行修改。 例如,在可視化工作室 WPF 設計器`CheckBox`中, 選擇控制項,然後右鍵單擊並選擇 **「編輯範本** > **創建副本**」。 這個指令產生*定義樣本的樣式*。

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

編輯範本複本是瞭解範本工作方式的好方法。 編輯副本並更改可視化演示文稿的幾個方面,而不是創建新的空白範本。

例如,請參閱為[控制項建立樣本](../themes/how-to-create-apply-template.md)。

### <a name="templatebinding"></a>TemplateBinding

您可能已經注意到上一個中定義的樣本資源使用[樣本的結合的標記延伸](../../framework/wpf/advanced/templatebinding-markup-extension.md)。 A`TemplateBinding`是範本方案綁定的優化形式,類似於使用 建`{Binding RelativeSource={RelativeSource TemplatedParent}}`構的綁定。 `TemplateBinding`可用於將範本的某些部分綁定到控制項的屬性。 例如,每個控件都有一個<xref:System.Windows.Controls.Control.BorderThickness>屬性。 使用`TemplateBinding`管理範本中的哪個元素受此控制項設置的影響。

### <a name="contentcontrol-and-itemscontrol"></a>內容控制和專案控制

<xref:System.Windows.Controls.ContentPresenter>如果在<xref:System.Windows.Controls.ControlTemplate>中聲明的<xref:System.Windows.Controls.ContentControl><xref:System.Windows.Controls.ContentPresenter><xref:System.Windows.Controls.ContentControl.ContentTemplate%2A><xref:System.Windows.Controls.ContentControl.Content%2A>。 同樣,<xref:System.Windows.Controls.ItemsPresenter><xref:System.Windows.Controls.ControlTemplate>中<xref:System.Windows.Controls.ItemsControl>的 的 a<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A><xref:System.Windows.Controls.ItemsControl.Items%2A>將自動綁定到和 屬性。

## <a name="datatemplates"></a>資料範本

在此範例應用中,有一個<xref:System.Windows.Controls.ListBox>控制項綁定到照片清單。

[!code-xaml[ListBox](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window3.xaml#SnippetListBox)]

目前<xref:System.Windows.Controls.ListBox>如下所示。

![套用範本之前的 ListBox](./media/styles-and-templates-overview/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")

大多數控制項都有某個型別的內容，而該內容通常來自您要繫結的資料。 在此範例中，該資料是相片清單。 在 WPF<xref:System.Windows.DataTemplate>中, 使用 定義數據的可視表示形式。 基本上,您放入的<xref:System.Windows.DataTemplate>,決定了數據在呈現應用中的外觀。

在我們的範例應用中,每個自定義`Photo`物件都有一`Source`個類型字串的屬性,用於指定圖像的檔路徑。 目前，相片物件是顯示成檔案路徑。

[!code-csharp[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Photo.cs#PhotoClass)]
[!code-vb[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/Photo.vb#PhotoClass)]

要將照片顯示為圖像,請創建一<xref:System.Windows.DataTemplate>個資源。

[!code-xaml[DataTemplate](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window4.xaml#SnippetDataTemplate)]

請注意,<xref:System.Windows.DataTemplate.DataType%2A>該屬性<xref:System.Windows.Style.TargetType%2A>與的<xref:System.Windows.Style>屬性 類似。 如果 位於資源部分中,則當您<xref:System.Windows.DataTemplate.DataType%2A>將 屬性指定為類型並省`x:Key`略 時 ,每當出現該類型時,<xref:System.Windows.DataTemplate><xref:System.Windows.DataTemplate>都會應用 。 您始終可以選擇使用分配,<xref:System.Windows.DataTemplate>`x:Key``StaticResource`然後將其設定為用於<xref:System.Windows.DataTemplate>採用類型的屬性,<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>如屬性<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>或 屬性。

從本質上講,<xref:System.Windows.DataTemplate>上述示例中的定義是,每當有物件`Photo`時,它應顯示為 中的<xref:System.Windows.Controls.Image><xref:System.Windows.Controls.Border>a。 有了這個<xref:System.Windows.DataTemplate>,我們的應用程式現在看起來像這樣。

![圖片影像](./media/styles-and-templates-overview/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")

資料範本化模型還提供其他功能。 例如,<xref:System.Windows.Controls.HeaderedItemsControl>如果顯示的集合資料包含使用類型(如<xref:System.Windows.Controls.Menu>或 )<xref:System.Windows.Controls.TreeView>的其他集合<xref:System.Windows.HierarchicalDataTemplate>,則存在 。 另一個資料樣本化功能是<xref:System.Windows.Controls.DataTemplateSelector>,它允許您根據自訂邏輯<xref:System.Windows.DataTemplate>選擇 要使用的 。 如需詳細資訊，請參閱[資料範本化概觀](../../framework/wpf/data/data-templating-overview.md)，其中提供不同資料範本化功能的更深入探討。

## <a name="triggers"></a>觸發程序

觸發程序會在屬性值發生變更或在某個事件被引發時，設定屬性或啟動動作 (例如動畫)。 <xref:System.Windows.Style><xref:System.Windows.Controls.ControlTemplate>,並且<xref:System.Windows.DataTemplate>所有`Triggers`屬性都可以包含一組觸發器。 有幾種類型的觸發器。

### <a name="propertytriggers"></a>屬性觸發器

設置<xref:System.Windows.Trigger>屬性值或基於屬性值啟動操作的 A 稱為屬性觸發器。

要演示如何使用屬性觸發器,可以使每個<xref:System.Windows.Controls.ListBoxItem>觸發器部分透明,除非已選擇。 以下樣式設置<xref:System.Windows.UIElement.Opacity%2A><xref:System.Windows.Controls.ListBoxItem>`0.5`到的值。 但是,<xref:System.Windows.Controls.ListBoxItem.IsSelected%2A>`true`當 屬性<xref:System.Windows.UIElement.Opacity%2A>為`1.0`時 ,設定為 。

[!code-xaml[PropertyTrigger](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window5.xaml#SnippetPropertyTrigger)]

此範例使用<xref:System.Windows.Trigger>設定 屬性值,但請<xref:System.Windows.Trigger>注意, 類別還具有使觸發<xref:System.Windows.TriggerBase.EnterActions%2A>器<xref:System.Windows.TriggerBase.ExitActions%2A>執行操作 的和 屬性。

請注意,<xref:System.Windows.FrameworkElement.MaxHeight%2A>屬性<xref:System.Windows.Controls.ListBoxItem>設定為`75`。 在下圖中,第三個專案是所選項。

![已設定樣式的 ListView](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

### <a name="eventtriggers-and-storyboards"></a>EventTrigger 和分鏡腳本

另一種類型的觸發器是<xref:System.Windows.EventTrigger>,它根據事件的發生啟動一組操作。 例如,以下<xref:System.Windows.EventTrigger>物件指定當滑鼠指標進入<xref:System.Windows.Controls.ListBoxItem>時<xref:System.Windows.FrameworkElement.MaxHeight%2A>, 屬性將動畫化`90``0.2`為超過 第二個週期的值。 當滑鼠指標從項目移開時，該屬性會在 `1` 秒的期間內恢復成原始值。 請注意,如何不必為<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A><xref:System.Windows.ContentElement.MouseLeave>動畫指定值。 這是因為動畫能夠記錄原始值。

[!code-xaml[StyleEventTriggers](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window6.xaml#SnippetStyleEventTriggers)]

有關詳細資訊,請參閱[情節提要概述](../../framework/wpf/graphics-multimedia/storyboards-overview.md)。

在下圖中,滑鼠指向第三個專案。

![樣式範例螢幕擷取](./media/styles-and-templates-overview/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>MultiTrigger、DataTrigger 及 MultiDataTrigger

除了<xref:System.Windows.Trigger>和<xref:System.Windows.EventTrigger>之外,還有其他類型的觸發器。 <xref:System.Windows.MultiTrigger>允許您根據多個條件設置屬性值。 使用<xref:System.Windows.DataTrigger>條件的屬性<xref:System.Windows.MultiDataTrigger>為數據綁定時使用。

## <a name="visual-states"></a>視覺狀態

控制項始終處於特定**狀態**。 例如,當滑鼠在控制項的表面上移動時,控制項被視為的通用`MouseOver`狀態 。 沒有特定狀態的控件被視為處於公共`Normal`狀態。 州被分為組,前面提到的州是州組的`CommonStates`一部分。 大多數控制項有兩個狀態群組`CommonStates``FocusStates`: 與 。 套用於控制項的每個狀態群組中,控制項始終處於每個群組的一個狀態,`CommonStates.MouseOver`如`FocusStates.Unfocused`與 。 但是,控制項不能處於同一組中的兩個不同的狀態,例如`CommonStates.Normal`和`CommonStates.Disabled`。 下面是大多數控件識別和使用狀態的表。

| VisualState 名稱 | VisualStateGroup 名稱 | 描述 |
| ---------------- | --------------------- | ----------- |
| 正常           | CommonStates          | 預設狀態。 |
| MouseOver        | CommonStates          | 滑鼠指標移到控制項上。 |
| 按下          | CommonStates          | 已按下控制項。 |
| 已停用         | CommonStates          | 已停用控制項。 |
| 已取得焦點          | FocusStates           | 控制項已取得焦點。 |
| 未取得焦點        | FocusStates           | 控制項未取得焦點。 |

透過控制項樣本<xref:System.Windows.VisualStateManager?displayProperty=fullName>的根元素上定義, 可以在控制項進入特定狀態時觸發動畫。 聲明`VisualStateManager`<xref:System.Windows.VisualStateGroup><xref:System.Windows.VisualState>和 要觀察的哪些組合。 當控制項進入監視狀態時,`VisaulStateManager`將啟動 由定義的動畫。

例如,以下 XAML`CommonStates.MouseOver`代碼監視 狀態,為`backgroundElement`名為的元素的填充顏色設置動畫。 當控件返回到狀態`CommonStates.Normal`時,將還原`backgroundElement`命名 元素的填充顏色。

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

有關情節提要的詳細資訊,請參閱[情節提要概述](../../framework/wpf/graphics-multimedia/storyboards-overview.md)。

## <a name="shared-resources-and-themes"></a>分享資源及主題

典型的 WPF 應用可能具有多個在整個應用中應用的 UI 資源。 總之,這組資源可以被視為應用的主題。 WPF 透過使用封裝<xref:System.Windows.ResourceDictionary>為類的資源字典,支援將UI資源打包為主題。

WPF 主題通過使用 WPF 公開的樣式和範本機制來自定義任何元素的可視化物件來定義。

WPF 主題資源存儲在嵌入式資源字典中。 這些資源字典必須內嵌在已簽署的組件內，並且可內嵌在與程式碼本身相同的組件中，也可內嵌在並存的組件中。 對於包含 WPF 控件的程式集,主題資源位於一系列並行程式集中。

當搜尋元素的樣式時，佈景主題會成為最後一個要查看的地方。 通常,搜索將首先遍走元素樹以搜索適當的資源,然後查看應用資源集合,最後查詢系統。 這使應用開發人員有機會在到達主題之前重新定義樹或應用級別上任何對象的樣式。

您可以將資源字典定義為單個檔,以便跨多個應用重用主題。 您也可以透過定義多個資源字典來提供類型相同但值不同的資源，以建立可切換的佈景主題。 在應用級別重新定義這些樣式或其他資源是蒙皮應用的建議方法。

要跨應用共享一組資源(包括樣式和範本),可以創建 XAML 檔並定義<xref:System.Windows.ResourceDictionary>`shared.xaml`包含對 檔的引用。

```xaml
<ResourceDictionary.MergedDictionaries>
  <ResourceDictionary Source="Shared.xaml" />
</ResourceDictionary.MergedDictionaries>
```

它是的`shared.xaml`共用,它本身定義了<xref:System.Windows.ResourceDictionary>包含一組樣式和畫筆資源的 ,使應用中的控制項具有一致的外觀。

有關詳細資訊,請參閱[合併的資源字典](../../framework/wpf/advanced/merged-resource-dictionaries.md)。

如果要為自定義控制項建立主題,請參閱[控制件創作概述](../../framework/wpf/controls/control-authoring-overview.md#defining-resources-at-the-theme-level)**的主題級別部分的"定義資源**"。

## <a name="see-also"></a>另請參閱

- [WPF 中的 Pack URI](../../framework/wpf/app-development/pack-uris-in-wpf.md)
- [操作說明：尋找 ControlTemplate 產生的元素](../../framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)
- [尋找資料樣本產生的元素](../../framework/wpf/data/how-to-find-datatemplate-generated-elements.md)
