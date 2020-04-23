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
# <a name="styles-and-templates-in-wpf"></a><span data-ttu-id="b07ce-104">WPF 中的樣式和樣本</span><span class="sxs-lookup"><span data-stu-id="b07ce-104">Styles and templates in WPF</span></span>

<span data-ttu-id="b07ce-105">Windows 示範基礎 (WPF) 樣式和範本化是指一組功能,這些功能使開發人員和設計人員能夠為其產品創建視覺上引人注目的效果和一致的外觀。</span><span class="sxs-lookup"><span data-stu-id="b07ce-105">Windows Presentation Foundation (WPF) styling and templating refer to a suite of features that let developers and designers create visually compelling effects and a consistent appearance for their product.</span></span> <span data-ttu-id="b07ce-106">自定義應用的外觀時,您需要一個強大的樣式和範本模型,以便維護和共用應用內部和應用程式之間的外觀。</span><span class="sxs-lookup"><span data-stu-id="b07ce-106">When customizing the appearance of an app, you want a strong styling and templating model that enables maintenance and sharing of appearance within and among apps.</span></span> <span data-ttu-id="b07ce-107">WPF 提供該模型。</span><span class="sxs-lookup"><span data-stu-id="b07ce-107">WPF provides that model.</span></span>

<span data-ttu-id="b07ce-108">WPF 樣式模型的另一個功能是表示和邏輯的分離。</span><span class="sxs-lookup"><span data-stu-id="b07ce-108">Another feature of the WPF styling model is the separation of presentation and logic.</span></span> <span data-ttu-id="b07ce-109">設計人員可以同時使用 XAML 處理應用的外觀,而開發人員則使用 C# 或 Visual Basic 處理程式設計邏輯。</span><span class="sxs-lookup"><span data-stu-id="b07ce-109">Designers can work on the appearance of an app by using only XAML at the same time that developers work on the programming logic by using C# or Visual Basic.</span></span>

<span data-ttu-id="b07ce-110">此概述側重於應用程式的樣式和範本化方面,不討論任何數據綁定概念。</span><span class="sxs-lookup"><span data-stu-id="b07ce-110">This overview focuses on the styling and templating aspects of the app and doesn't discuss any data-binding concepts.</span></span> <span data-ttu-id="b07ce-111">如需有關資料繫結的資訊，請參閱[資料繫結概觀](../data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b07ce-111">For information about data binding, see [Data Binding Overview](../data/data-binding-overview.md).</span></span>

<span data-ttu-id="b07ce-112">瞭解資源非常重要,這些資源使樣式和範本能夠重複使用。</span><span class="sxs-lookup"><span data-stu-id="b07ce-112">It's important to understand resources, which are what enable styles and templates to be reused.</span></span> <span data-ttu-id="b07ce-113">如需有關資源的詳細資訊，請參閱 [XAML 資源](xaml-resources-define.md)。</span><span class="sxs-lookup"><span data-stu-id="b07ce-113">For more information about resources, see [XAML Resources](xaml-resources-define.md).</span></span>

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sample"></a><span data-ttu-id="b07ce-114">範例</span><span class="sxs-lookup"><span data-stu-id="b07ce-114">Sample</span></span>

<span data-ttu-id="b07ce-115">這個概述中提供的範例碼以下圖的[簡單照片瀏覽應用程式](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="b07ce-115">The sample code provided in this overview is based on a [simple photo browsing application](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) shown in the following illustration.</span></span>

<span data-ttu-id="b07ce-116">![已設定樣式的 ListView](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")</span><span class="sxs-lookup"><span data-stu-id="b07ce-116">![Styled ListView](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")</span></span>

<span data-ttu-id="b07ce-117">這個簡單的相片範例使用樣式設定和範本化，來創造引人注目的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="b07ce-117">This simple photo sample uses styling and templating to create a visually compelling user experience.</span></span> <span data-ttu-id="b07ce-118">該範例具有兩<xref:System.Windows.Controls.TextBlock>個元素和<xref:System.Windows.Controls.ListBox>一個綁定到圖像清單的控制項。</span><span class="sxs-lookup"><span data-stu-id="b07ce-118">The sample has two <xref:System.Windows.Controls.TextBlock> elements and a <xref:System.Windows.Controls.ListBox> control that is bound to a list of images.</span></span>

<span data-ttu-id="b07ce-119">如需完整範例，請參閱[樣式設定和範本化範例簡介 (英文)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="b07ce-119">For the complete sample, see [Introduction to Styling and Templating Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="styles"></a><span data-ttu-id="b07ce-120">樣式</span><span class="sxs-lookup"><span data-stu-id="b07ce-120">Styles</span></span>

<span data-ttu-id="b07ce-121">可以將<xref:System.Windows.Style>a 視為將一組屬性值應用於多個元素的便捷方法。</span><span class="sxs-lookup"><span data-stu-id="b07ce-121">You can think of a <xref:System.Windows.Style> as a convenient way to apply a set of property values to multiple elements.</span></span> <span data-ttu-id="b07ce-122"><xref:System.Windows.FrameworkElement>可以在派生自<xref:System.Windows.FrameworkContentElement>或<xref:System.Windows.Window>或 或的任何元素上使用<xref:System.Windows.Controls.Button>樣式。</span><span class="sxs-lookup"><span data-stu-id="b07ce-122">You can use a style on any element that derives from <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement> such as a <xref:System.Windows.Window> or a <xref:System.Windows.Controls.Button>.</span></span>

<span data-ttu-id="b07ce-123">聲明樣式的最常見方法是作為 XAML`Resources`檔中 部分中的資源。</span><span class="sxs-lookup"><span data-stu-id="b07ce-123">The most common way to declare a style is as a resource in the `Resources` section in a XAML file.</span></span> <span data-ttu-id="b07ce-124">因為樣式是資源,因此它們遵循適用於所有資源的相同範圍規則。</span><span class="sxs-lookup"><span data-stu-id="b07ce-124">Because styles are resources, they obey the same scoping rules that apply to all resources.</span></span> <span data-ttu-id="b07ce-125">簡單地說,聲明樣式會影響樣式的應用位置。</span><span class="sxs-lookup"><span data-stu-id="b07ce-125">Put simply, where you declare a style affects where the style can be applied.</span></span> <span data-ttu-id="b07ce-126">例如,如果在應用定義 XAML 檔的根元素中聲明樣式,則可以在應用中的任意位置使用該樣式。</span><span class="sxs-lookup"><span data-stu-id="b07ce-126">For example, if you declare the style in the root element of your app definition XAML file, the style can be used anywhere in your app.</span></span>

<span data-ttu-id="b07ce-127">例如,以下 XAML 代碼聲明的兩個`TextBlock`樣式`TextBlock`為 a , 一個自動應用於所有元素, 另一個必須顯式引用。</span><span class="sxs-lookup"><span data-stu-id="b07ce-127">For example, the following XAML code declares two styles for a `TextBlock`, one automatically applied to all `TextBlock` elements, and another that must be explicitly referenced.</span></span>

[!code-xaml[SnippetDefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

<span data-ttu-id="b07ce-128">下面是上面聲明使用的樣式的示例。</span><span class="sxs-lookup"><span data-stu-id="b07ce-128">Here is an example of the styles declared above being used.</span></span>

[!code-xaml[SnippetTextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

![樣式化文字塊](./media/styles-and-templates-overview/stylingintro-textblocks.png)

<span data-ttu-id="b07ce-130">有關詳細資訊,請參閱為[控制項建立樣式](styles-templates-create-apply-style.md)。</span><span class="sxs-lookup"><span data-stu-id="b07ce-130">For more information, see [Create a style for a control](styles-templates-create-apply-style.md).</span></span>

## <a name="controltemplates"></a><span data-ttu-id="b07ce-131">ControlTemplates</span><span class="sxs-lookup"><span data-stu-id="b07ce-131">ControlTemplates</span></span>

<span data-ttu-id="b07ce-132">在 WPF<xref:System.Windows.Controls.ControlTemplate>中,控制件的定義控制件的外觀。</span><span class="sxs-lookup"><span data-stu-id="b07ce-132">In WPF, the <xref:System.Windows.Controls.ControlTemplate> of a control defines the appearance of the control.</span></span> <span data-ttu-id="b07ce-133">您可以通過定義<xref:System.Windows.Controls.ControlTemplate>新 控制件並將其分配給控制項來更改控制項的結構和外觀。</span><span class="sxs-lookup"><span data-stu-id="b07ce-133">You can change the structure and appearance of a control by defining a new <xref:System.Windows.Controls.ControlTemplate> and assigning it to a control.</span></span> <span data-ttu-id="b07ce-134">在許多情況下,範本為您提供足夠的靈活性,因此您不必編寫自己的自定義控制項。</span><span class="sxs-lookup"><span data-stu-id="b07ce-134">In many cases, templates give you enough flexibility so that you do not have to write your own custom controls.</span></span>

<span data-ttu-id="b07ce-135">每個控制項都有一個預設樣本分配給[控制項.Template](xref:System.Windows.Controls.Control.Template)屬性。</span><span class="sxs-lookup"><span data-stu-id="b07ce-135">Each control has a default template assigned to the [Control.Template](xref:System.Windows.Controls.Control.Template) property.</span></span> <span data-ttu-id="b07ce-136">該範本將控制件的可視化表示與控制項的功能連接起來。</span><span class="sxs-lookup"><span data-stu-id="b07ce-136">The template connects the visual presentation of the control with the control's capabilities.</span></span> <span data-ttu-id="b07ce-137">由於在 XAML 中定義範本,因此無需編寫任何代碼即可更改控制項的外觀。</span><span class="sxs-lookup"><span data-stu-id="b07ce-137">Because you define a template in XAML, you can change the control's appearance without writing any code.</span></span> <span data-ttu-id="b07ce-138">每個樣本都專為特定控制項而設計,<xref:System.Windows.Controls.Button>例如 。</span><span class="sxs-lookup"><span data-stu-id="b07ce-138">Each template is designed for a specific control, such as a <xref:System.Windows.Controls.Button>.</span></span>

<span data-ttu-id="b07ce-139">通常,在 XAML`Resources`檔部分將範本聲明為資源。</span><span class="sxs-lookup"><span data-stu-id="b07ce-139">Commonly you declare a template as a resource on the `Resources` section of a XAML file.</span></span> <span data-ttu-id="b07ce-140">與所有資源一樣,範圍規則適用。</span><span class="sxs-lookup"><span data-stu-id="b07ce-140">As with all resources, scoping rules apply.</span></span>

<span data-ttu-id="b07ce-141">控件範本比樣式涉及更多。</span><span class="sxs-lookup"><span data-stu-id="b07ce-141">Control templates are a lot more involved than a style.</span></span> <span data-ttu-id="b07ce-142">這是因為控制項樣本重寫整個控制項的可視外觀,而樣式只是將屬性更改應用於現有控制項。</span><span class="sxs-lookup"><span data-stu-id="b07ce-142">This is because the control template rewrites the visual appearance of the entire control, while a style simply applies property changes to the existing control.</span></span> <span data-ttu-id="b07ce-143">但是,由於控件的範本是通過設置[Control.template](xref:System.Windows.Controls.Control.Template)屬性應用的,因此可以使用樣式來定義或設置範本。</span><span class="sxs-lookup"><span data-stu-id="b07ce-143">However, since the template of a control is applied by setting the [Control.Template](xref:System.Windows.Controls.Control.Template) property, you can use a style to define or set a template.</span></span>

<span data-ttu-id="b07ce-144">設計器通常允許您創建現有範本的副本並對其進行修改。</span><span class="sxs-lookup"><span data-stu-id="b07ce-144">Designers generally allow you to create a copy of an existing template and modify it.</span></span> <span data-ttu-id="b07ce-145">例如,在可視化工作室 WPF 設計器`CheckBox`中, 選擇控制項,然後右鍵單擊並選擇 **「編輯範本** > **創建副本**」。</span><span class="sxs-lookup"><span data-stu-id="b07ce-145">For example, in the Visual Studio WPF designer, select a `CheckBox` control, and then right-click and select **Edit template** > **Create a copy**.</span></span> <span data-ttu-id="b07ce-146">這個指令產生*定義樣本的樣式*。</span><span class="sxs-lookup"><span data-stu-id="b07ce-146">This command generates a *style that defines a template*.</span></span>

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

<span data-ttu-id="b07ce-147">編輯範本複本是瞭解範本工作方式的好方法。</span><span class="sxs-lookup"><span data-stu-id="b07ce-147">Editing a copy of a template is a great way to learn how templates work.</span></span> <span data-ttu-id="b07ce-148">編輯副本並更改可視化演示文稿的幾個方面,而不是創建新的空白範本。</span><span class="sxs-lookup"><span data-stu-id="b07ce-148">Instead of creating a new blank template, it's easier to edit a copy and change a few aspects of the visual presentation.</span></span>

<span data-ttu-id="b07ce-149">例如,請參閱為[控制項建立樣本](../themes/how-to-create-apply-template.md)。</span><span class="sxs-lookup"><span data-stu-id="b07ce-149">For an example, see [Create a template for a control](../themes/how-to-create-apply-template.md).</span></span>

### <a name="templatebinding"></a><span data-ttu-id="b07ce-150">TemplateBinding</span><span class="sxs-lookup"><span data-stu-id="b07ce-150">TemplateBinding</span></span>

<span data-ttu-id="b07ce-151">您可能已經注意到上一個中定義的樣本資源使用[樣本的結合的標記延伸](../../framework/wpf/advanced/templatebinding-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="b07ce-151">You may have noticed that the template resource defined in the previous section uses the [TemplateBinding Markup Extension](../../framework/wpf/advanced/templatebinding-markup-extension.md).</span></span> <span data-ttu-id="b07ce-152">A`TemplateBinding`是範本方案綁定的優化形式,類似於使用 建`{Binding RelativeSource={RelativeSource TemplatedParent}}`構的綁定。</span><span class="sxs-lookup"><span data-stu-id="b07ce-152">A `TemplateBinding` is an optimized form of a binding for template scenarios, analogous to a binding constructed with `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="b07ce-153">`TemplateBinding`可用於將範本的某些部分綁定到控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="b07ce-153">`TemplateBinding` is useful for binding parts of the template to properties of the control.</span></span> <span data-ttu-id="b07ce-154">例如,每個控件都有一個<xref:System.Windows.Controls.Control.BorderThickness>屬性。</span><span class="sxs-lookup"><span data-stu-id="b07ce-154">For example, each control has a <xref:System.Windows.Controls.Control.BorderThickness> property.</span></span> <span data-ttu-id="b07ce-155">使用`TemplateBinding`管理範本中的哪個元素受此控制項設置的影響。</span><span class="sxs-lookup"><span data-stu-id="b07ce-155">Use a `TemplateBinding` to manage which element in the template is affected by this control setting.</span></span>

### <a name="contentcontrol-and-itemscontrol"></a><span data-ttu-id="b07ce-156">內容控制和專案控制</span><span class="sxs-lookup"><span data-stu-id="b07ce-156">ContentControl and ItemsControl</span></span>

<span data-ttu-id="b07ce-157"><xref:System.Windows.Controls.ContentPresenter>如果在<xref:System.Windows.Controls.ControlTemplate>中聲明的<xref:System.Windows.Controls.ContentControl><xref:System.Windows.Controls.ContentPresenter><xref:System.Windows.Controls.ContentControl.ContentTemplate%2A><xref:System.Windows.Controls.ContentControl.Content%2A>。</span><span class="sxs-lookup"><span data-stu-id="b07ce-157">If a <xref:System.Windows.Controls.ContentPresenter> is declared in the <xref:System.Windows.Controls.ControlTemplate> of a <xref:System.Windows.Controls.ContentControl>, the <xref:System.Windows.Controls.ContentPresenter> will automatically bind to the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> and <xref:System.Windows.Controls.ContentControl.Content%2A> properties.</span></span> <span data-ttu-id="b07ce-158">同樣,<xref:System.Windows.Controls.ItemsPresenter><xref:System.Windows.Controls.ControlTemplate>中<xref:System.Windows.Controls.ItemsControl>的 的 a<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A><xref:System.Windows.Controls.ItemsControl.Items%2A>將自動綁定到和 屬性。</span><span class="sxs-lookup"><span data-stu-id="b07ce-158">Likewise, an <xref:System.Windows.Controls.ItemsPresenter> that is in the <xref:System.Windows.Controls.ControlTemplate> of an <xref:System.Windows.Controls.ItemsControl> will automatically bind to the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> and <xref:System.Windows.Controls.ItemsControl.Items%2A> properties.</span></span>

## <a name="datatemplates"></a><span data-ttu-id="b07ce-159">資料範本</span><span class="sxs-lookup"><span data-stu-id="b07ce-159">DataTemplates</span></span>

<span data-ttu-id="b07ce-160">在此範例應用中,有一個<xref:System.Windows.Controls.ListBox>控制項綁定到照片清單。</span><span class="sxs-lookup"><span data-stu-id="b07ce-160">In this sample app, there is a <xref:System.Windows.Controls.ListBox> control that is bound to a list of photos.</span></span>

[!code-xaml[ListBox](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window3.xaml#SnippetListBox)]

<span data-ttu-id="b07ce-161">目前<xref:System.Windows.Controls.ListBox>如下所示。</span><span class="sxs-lookup"><span data-stu-id="b07ce-161">This <xref:System.Windows.Controls.ListBox> currently looks like the following.</span></span>

<span data-ttu-id="b07ce-162">![套用範本之前的 ListBox](./media/styles-and-templates-overview/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")</span><span class="sxs-lookup"><span data-stu-id="b07ce-162">![ListBox before applying template](./media/styles-and-templates-overview/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")</span></span>

<span data-ttu-id="b07ce-163">大多數控制項都有某個型別的內容，而該內容通常來自您要繫結的資料。</span><span class="sxs-lookup"><span data-stu-id="b07ce-163">Most controls have some type of content, and that content often comes from data that you are binding to.</span></span> <span data-ttu-id="b07ce-164">在此範例中，該資料是相片清單。</span><span class="sxs-lookup"><span data-stu-id="b07ce-164">In this sample, the data is the list of photos.</span></span> <span data-ttu-id="b07ce-165">在 WPF<xref:System.Windows.DataTemplate>中, 使用 定義數據的可視表示形式。</span><span class="sxs-lookup"><span data-stu-id="b07ce-165">In WPF, you use a <xref:System.Windows.DataTemplate> to define the visual representation of data.</span></span> <span data-ttu-id="b07ce-166">基本上,您放入的<xref:System.Windows.DataTemplate>,決定了數據在呈現應用中的外觀。</span><span class="sxs-lookup"><span data-stu-id="b07ce-166">Basically, what you put into a <xref:System.Windows.DataTemplate> determines what the data looks like in the rendered app.</span></span>

<span data-ttu-id="b07ce-167">在我們的範例應用中,每個自定義`Photo`物件都有一`Source`個類型字串的屬性,用於指定圖像的檔路徑。</span><span class="sxs-lookup"><span data-stu-id="b07ce-167">In our sample app, each custom `Photo` object has a `Source` property of type string that specifies the file path of the image.</span></span> <span data-ttu-id="b07ce-168">目前，相片物件是顯示成檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="b07ce-168">Currently, the photo objects appear as file paths.</span></span>

[!code-csharp[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Photo.cs#PhotoClass)]
[!code-vb[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/Photo.vb#PhotoClass)]

<span data-ttu-id="b07ce-169">要將照片顯示為圖像,請創建一<xref:System.Windows.DataTemplate>個資源。</span><span class="sxs-lookup"><span data-stu-id="b07ce-169">For the photos to appear as images, you create a <xref:System.Windows.DataTemplate> as a resource.</span></span>

[!code-xaml[DataTemplate](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window4.xaml#SnippetDataTemplate)]

<span data-ttu-id="b07ce-170">請注意,<xref:System.Windows.DataTemplate.DataType%2A>該屬性<xref:System.Windows.Style.TargetType%2A>與的<xref:System.Windows.Style>屬性 類似。</span><span class="sxs-lookup"><span data-stu-id="b07ce-170">Notice that the <xref:System.Windows.DataTemplate.DataType%2A> property is similar to the <xref:System.Windows.Style.TargetType%2A> property of the <xref:System.Windows.Style>.</span></span> <span data-ttu-id="b07ce-171">如果 位於資源部分中,則當您<xref:System.Windows.DataTemplate.DataType%2A>將 屬性指定為類型並省`x:Key`略 時 ,每當出現該類型時,<xref:System.Windows.DataTemplate><xref:System.Windows.DataTemplate>都會應用 。</span><span class="sxs-lookup"><span data-stu-id="b07ce-171">If your <xref:System.Windows.DataTemplate> is in the resources section, when you specify the <xref:System.Windows.DataTemplate.DataType%2A> property to a type and omit an `x:Key`, the <xref:System.Windows.DataTemplate> is applied whenever that type appears.</span></span> <span data-ttu-id="b07ce-172">您始終可以選擇使用分配,<xref:System.Windows.DataTemplate>`x:Key``StaticResource`然後將其設定為用於<xref:System.Windows.DataTemplate>採用類型的屬性,<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>如屬性<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>或 屬性。</span><span class="sxs-lookup"><span data-stu-id="b07ce-172">You always have the option to assign the <xref:System.Windows.DataTemplate> with an `x:Key` and then set it as a `StaticResource` for properties that take <xref:System.Windows.DataTemplate> types, such as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> property or the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> property.</span></span>

<span data-ttu-id="b07ce-173">從本質上講,<xref:System.Windows.DataTemplate>上述示例中的定義是,每當有物件`Photo`時,它應顯示為 中的<xref:System.Windows.Controls.Image><xref:System.Windows.Controls.Border>a。</span><span class="sxs-lookup"><span data-stu-id="b07ce-173">Essentially, the <xref:System.Windows.DataTemplate> in the above example defines that whenever there is a `Photo` object, it should appear as an <xref:System.Windows.Controls.Image> within a <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="b07ce-174">有了這個<xref:System.Windows.DataTemplate>,我們的應用程式現在看起來像這樣。</span><span class="sxs-lookup"><span data-stu-id="b07ce-174">With this <xref:System.Windows.DataTemplate>, our app now looks like this.</span></span>

<span data-ttu-id="b07ce-175">![圖片影像](./media/styles-and-templates-overview/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")</span><span class="sxs-lookup"><span data-stu-id="b07ce-175">![Photo image](./media/styles-and-templates-overview/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")</span></span>

<span data-ttu-id="b07ce-176">資料範本化模型還提供其他功能。</span><span class="sxs-lookup"><span data-stu-id="b07ce-176">The data templating model provides other features.</span></span> <span data-ttu-id="b07ce-177">例如,<xref:System.Windows.Controls.HeaderedItemsControl>如果顯示的集合資料包含使用類型(如<xref:System.Windows.Controls.Menu>或 )<xref:System.Windows.Controls.TreeView>的其他集合<xref:System.Windows.HierarchicalDataTemplate>,則存在 。</span><span class="sxs-lookup"><span data-stu-id="b07ce-177">For example, if you are displaying collection data that contains other collections using a <xref:System.Windows.Controls.HeaderedItemsControl> type such as a <xref:System.Windows.Controls.Menu> or a <xref:System.Windows.Controls.TreeView>, there is the <xref:System.Windows.HierarchicalDataTemplate>.</span></span> <span data-ttu-id="b07ce-178">另一個資料樣本化功能是<xref:System.Windows.Controls.DataTemplateSelector>,它允許您根據自訂邏輯<xref:System.Windows.DataTemplate>選擇 要使用的 。</span><span class="sxs-lookup"><span data-stu-id="b07ce-178">Another data templating feature is the <xref:System.Windows.Controls.DataTemplateSelector>, which allows you to choose a <xref:System.Windows.DataTemplate> to use based on custom logic.</span></span> <span data-ttu-id="b07ce-179">如需詳細資訊，請參閱[資料範本化概觀](../../framework/wpf/data/data-templating-overview.md)，其中提供不同資料範本化功能的更深入探討。</span><span class="sxs-lookup"><span data-stu-id="b07ce-179">For more information, see [Data Templating Overview](../../framework/wpf/data/data-templating-overview.md), which provides a more in-depth discussion of the different data templating features.</span></span>

## <a name="triggers"></a><span data-ttu-id="b07ce-180">觸發程序</span><span class="sxs-lookup"><span data-stu-id="b07ce-180">Triggers</span></span>

<span data-ttu-id="b07ce-181">觸發程序會在屬性值發生變更或在某個事件被引發時，設定屬性或啟動動作 (例如動畫)。</span><span class="sxs-lookup"><span data-stu-id="b07ce-181">A trigger sets properties or starts actions, such as an animation, when a property value changes or when an event is raised.</span></span> <span data-ttu-id="b07ce-182"><xref:System.Windows.Style><xref:System.Windows.Controls.ControlTemplate>,並且<xref:System.Windows.DataTemplate>所有`Triggers`屬性都可以包含一組觸發器。</span><span class="sxs-lookup"><span data-stu-id="b07ce-182"><xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, and <xref:System.Windows.DataTemplate> all have a `Triggers` property that can contain a set of triggers.</span></span> <span data-ttu-id="b07ce-183">有幾種類型的觸發器。</span><span class="sxs-lookup"><span data-stu-id="b07ce-183">There are several types of triggers.</span></span>

### <a name="propertytriggers"></a><span data-ttu-id="b07ce-184">屬性觸發器</span><span class="sxs-lookup"><span data-stu-id="b07ce-184">PropertyTriggers</span></span>

<span data-ttu-id="b07ce-185">設置<xref:System.Windows.Trigger>屬性值或基於屬性值啟動操作的 A 稱為屬性觸發器。</span><span class="sxs-lookup"><span data-stu-id="b07ce-185">A <xref:System.Windows.Trigger> that sets property values or starts actions based on the value of a property is called a property trigger.</span></span>

<span data-ttu-id="b07ce-186">要演示如何使用屬性觸發器,可以使每個<xref:System.Windows.Controls.ListBoxItem>觸發器部分透明,除非已選擇。</span><span class="sxs-lookup"><span data-stu-id="b07ce-186">To demonstrate how to use property triggers, you can make each <xref:System.Windows.Controls.ListBoxItem> partially transparent unless it is selected.</span></span> <span data-ttu-id="b07ce-187">以下樣式設置<xref:System.Windows.UIElement.Opacity%2A><xref:System.Windows.Controls.ListBoxItem>`0.5`到的值。</span><span class="sxs-lookup"><span data-stu-id="b07ce-187">The following style sets the <xref:System.Windows.UIElement.Opacity%2A> value of a <xref:System.Windows.Controls.ListBoxItem> to `0.5`.</span></span> <span data-ttu-id="b07ce-188">但是,<xref:System.Windows.Controls.ListBoxItem.IsSelected%2A>`true`當 屬性<xref:System.Windows.UIElement.Opacity%2A>為`1.0`時 ,設定為 。</span><span class="sxs-lookup"><span data-stu-id="b07ce-188">When the <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> property is `true`, however, the <xref:System.Windows.UIElement.Opacity%2A> is set to `1.0`.</span></span>

[!code-xaml[PropertyTrigger](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window5.xaml#SnippetPropertyTrigger)]

<span data-ttu-id="b07ce-189">此範例使用<xref:System.Windows.Trigger>設定 屬性值,但請<xref:System.Windows.Trigger>注意, 類別還具有使觸發<xref:System.Windows.TriggerBase.EnterActions%2A>器<xref:System.Windows.TriggerBase.ExitActions%2A>執行操作 的和 屬性。</span><span class="sxs-lookup"><span data-stu-id="b07ce-189">This example uses a <xref:System.Windows.Trigger> to set a property value, but note that the <xref:System.Windows.Trigger> class also has the <xref:System.Windows.TriggerBase.EnterActions%2A> and <xref:System.Windows.TriggerBase.ExitActions%2A> properties that enable a trigger to perform actions.</span></span>

<span data-ttu-id="b07ce-190">請注意,<xref:System.Windows.FrameworkElement.MaxHeight%2A>屬性<xref:System.Windows.Controls.ListBoxItem>設定為`75`。</span><span class="sxs-lookup"><span data-stu-id="b07ce-190">Notice that the <xref:System.Windows.FrameworkElement.MaxHeight%2A> property of the <xref:System.Windows.Controls.ListBoxItem> is set to `75`.</span></span> <span data-ttu-id="b07ce-191">在下圖中,第三個專案是所選項。</span><span class="sxs-lookup"><span data-stu-id="b07ce-191">In the following illustration, the third item is the selected item.</span></span>

<span data-ttu-id="b07ce-192">![已設定樣式的 ListView](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")</span><span class="sxs-lookup"><span data-stu-id="b07ce-192">![Styled ListView](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")</span></span>

### <a name="eventtriggers-and-storyboards"></a><span data-ttu-id="b07ce-193">EventTrigger 和分鏡腳本</span><span class="sxs-lookup"><span data-stu-id="b07ce-193">EventTriggers and Storyboards</span></span>

<span data-ttu-id="b07ce-194">另一種類型的觸發器是<xref:System.Windows.EventTrigger>,它根據事件的發生啟動一組操作。</span><span class="sxs-lookup"><span data-stu-id="b07ce-194">Another type of trigger is the <xref:System.Windows.EventTrigger>, which starts a set of actions based on the occurrence of an event.</span></span> <span data-ttu-id="b07ce-195">例如,以下<xref:System.Windows.EventTrigger>物件指定當滑鼠指標進入<xref:System.Windows.Controls.ListBoxItem>時<xref:System.Windows.FrameworkElement.MaxHeight%2A>, 屬性將動畫化`90``0.2`為超過 第二個週期的值。</span><span class="sxs-lookup"><span data-stu-id="b07ce-195">For example, the following <xref:System.Windows.EventTrigger> objects specify that when the mouse pointer enters the <xref:System.Windows.Controls.ListBoxItem>, the <xref:System.Windows.FrameworkElement.MaxHeight%2A> property animates to a value of `90` over a `0.2` second period.</span></span> <span data-ttu-id="b07ce-196">當滑鼠指標從項目移開時，該屬性會在 `1` 秒的期間內恢復成原始值。</span><span class="sxs-lookup"><span data-stu-id="b07ce-196">When the mouse moves away from the item, the property returns to the original value over a period of `1` second.</span></span> <span data-ttu-id="b07ce-197">請注意,如何不必為<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A><xref:System.Windows.ContentElement.MouseLeave>動畫指定值。</span><span class="sxs-lookup"><span data-stu-id="b07ce-197">Note how it is not necessary to specify a <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> value for the <xref:System.Windows.ContentElement.MouseLeave> animation.</span></span> <span data-ttu-id="b07ce-198">這是因為動畫能夠記錄原始值。</span><span class="sxs-lookup"><span data-stu-id="b07ce-198">This is because the animation is able to keep track of the original value.</span></span>

[!code-xaml[StyleEventTriggers](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window6.xaml#SnippetStyleEventTriggers)]

<span data-ttu-id="b07ce-199">有關詳細資訊,請參閱[情節提要概述](../../framework/wpf/graphics-multimedia/storyboards-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b07ce-199">For more information, see the [Storyboards overview](../../framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span>

<span data-ttu-id="b07ce-200">在下圖中,滑鼠指向第三個專案。</span><span class="sxs-lookup"><span data-stu-id="b07ce-200">In the following illustration, the mouse is pointing to the third item.</span></span>

<span data-ttu-id="b07ce-201">![樣式範例螢幕擷取](./media/styles-and-templates-overview/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span><span class="sxs-lookup"><span data-stu-id="b07ce-201">![Styling sample screenshot](./media/styles-and-templates-overview/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span></span>

### <a name="multitriggers-datatriggers-and-multidatatriggers"></a><span data-ttu-id="b07ce-202">MultiTrigger、DataTrigger 及 MultiDataTrigger</span><span class="sxs-lookup"><span data-stu-id="b07ce-202">MultiTriggers, DataTriggers, and MultiDataTriggers</span></span>

<span data-ttu-id="b07ce-203">除了<xref:System.Windows.Trigger>和<xref:System.Windows.EventTrigger>之外,還有其他類型的觸發器。</span><span class="sxs-lookup"><span data-stu-id="b07ce-203">In addition to <xref:System.Windows.Trigger> and <xref:System.Windows.EventTrigger>, there are other types of triggers.</span></span> <span data-ttu-id="b07ce-204"><xref:System.Windows.MultiTrigger>允許您根據多個條件設置屬性值。</span><span class="sxs-lookup"><span data-stu-id="b07ce-204"><xref:System.Windows.MultiTrigger> allows you to set property values based on multiple conditions.</span></span> <span data-ttu-id="b07ce-205">使用<xref:System.Windows.DataTrigger>條件的屬性<xref:System.Windows.MultiDataTrigger>為數據綁定時使用。</span><span class="sxs-lookup"><span data-stu-id="b07ce-205">You use <xref:System.Windows.DataTrigger> and <xref:System.Windows.MultiDataTrigger> when the property of your condition is data-bound.</span></span>

## <a name="visual-states"></a><span data-ttu-id="b07ce-206">視覺狀態</span><span class="sxs-lookup"><span data-stu-id="b07ce-206">Visual States</span></span>

<span data-ttu-id="b07ce-207">控制項始終處於特定**狀態**。</span><span class="sxs-lookup"><span data-stu-id="b07ce-207">Controls are always in a specific **state**.</span></span> <span data-ttu-id="b07ce-208">例如,當滑鼠在控制項的表面上移動時,控制項被視為的通用`MouseOver`狀態 。</span><span class="sxs-lookup"><span data-stu-id="b07ce-208">For example, when the mouse moves over the surface of a control, the control is considered to be in a common state of `MouseOver`.</span></span> <span data-ttu-id="b07ce-209">沒有特定狀態的控件被視為處於公共`Normal`狀態。</span><span class="sxs-lookup"><span data-stu-id="b07ce-209">A control without a specific state is considered to be in the common `Normal` state.</span></span> <span data-ttu-id="b07ce-210">州被分為組,前面提到的州是州組的`CommonStates`一部分。</span><span class="sxs-lookup"><span data-stu-id="b07ce-210">States are broken into groups, and the previously mentioned states are part of the state group `CommonStates`.</span></span> <span data-ttu-id="b07ce-211">大多數控制項有兩個狀態群組`CommonStates``FocusStates`: 與 。</span><span class="sxs-lookup"><span data-stu-id="b07ce-211">Most controls have two state groups: `CommonStates` and `FocusStates`.</span></span> <span data-ttu-id="b07ce-212">套用於控制項的每個狀態群組中,控制項始終處於每個群組的一個狀態,`CommonStates.MouseOver`如`FocusStates.Unfocused`與 。</span><span class="sxs-lookup"><span data-stu-id="b07ce-212">Of each state group applied to a control, a control is always in one state of each group, such as `CommonStates.MouseOver` and `FocusStates.Unfocused`.</span></span> <span data-ttu-id="b07ce-213">但是,控制項不能處於同一組中的兩個不同的狀態,例如`CommonStates.Normal`和`CommonStates.Disabled`。</span><span class="sxs-lookup"><span data-stu-id="b07ce-213">However, a control can't be in two different states within the same group, such as `CommonStates.Normal` and `CommonStates.Disabled`.</span></span> <span data-ttu-id="b07ce-214">下面是大多數控件識別和使用狀態的表。</span><span class="sxs-lookup"><span data-stu-id="b07ce-214">Here is a table of states most controls recognize and use.</span></span>

| <span data-ttu-id="b07ce-215">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="b07ce-215">VisualState Name</span></span> | <span data-ttu-id="b07ce-216">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="b07ce-216">VisualStateGroup Name</span></span> | <span data-ttu-id="b07ce-217">描述</span><span class="sxs-lookup"><span data-stu-id="b07ce-217">Description</span></span> |
| ---------------- | --------------------- | ----------- |
| <span data-ttu-id="b07ce-218">正常</span><span class="sxs-lookup"><span data-stu-id="b07ce-218">Normal</span></span>           | <span data-ttu-id="b07ce-219">CommonStates</span><span class="sxs-lookup"><span data-stu-id="b07ce-219">CommonStates</span></span>          | <span data-ttu-id="b07ce-220">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="b07ce-220">The default state.</span></span> |
| <span data-ttu-id="b07ce-221">MouseOver</span><span class="sxs-lookup"><span data-stu-id="b07ce-221">MouseOver</span></span>        | <span data-ttu-id="b07ce-222">CommonStates</span><span class="sxs-lookup"><span data-stu-id="b07ce-222">CommonStates</span></span>          | <span data-ttu-id="b07ce-223">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="b07ce-223">The mouse pointer is positioned over the control.</span></span> |
| <span data-ttu-id="b07ce-224">按下</span><span class="sxs-lookup"><span data-stu-id="b07ce-224">Pressed</span></span>          | <span data-ttu-id="b07ce-225">CommonStates</span><span class="sxs-lookup"><span data-stu-id="b07ce-225">CommonStates</span></span>          | <span data-ttu-id="b07ce-226">已按下控制項。</span><span class="sxs-lookup"><span data-stu-id="b07ce-226">The control is pressed.</span></span> |
| <span data-ttu-id="b07ce-227">已停用</span><span class="sxs-lookup"><span data-stu-id="b07ce-227">Disabled</span></span>         | <span data-ttu-id="b07ce-228">CommonStates</span><span class="sxs-lookup"><span data-stu-id="b07ce-228">CommonStates</span></span>          | <span data-ttu-id="b07ce-229">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="b07ce-229">The control is disabled.</span></span> |
| <span data-ttu-id="b07ce-230">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="b07ce-230">Focused</span></span>          | <span data-ttu-id="b07ce-231">FocusStates</span><span class="sxs-lookup"><span data-stu-id="b07ce-231">FocusStates</span></span>           | <span data-ttu-id="b07ce-232">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="b07ce-232">The control has focus.</span></span> |
| <span data-ttu-id="b07ce-233">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="b07ce-233">Unfocused</span></span>        | <span data-ttu-id="b07ce-234">FocusStates</span><span class="sxs-lookup"><span data-stu-id="b07ce-234">FocusStates</span></span>           | <span data-ttu-id="b07ce-235">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="b07ce-235">The control does not have focus.</span></span> |

<span data-ttu-id="b07ce-236">透過控制項樣本<xref:System.Windows.VisualStateManager?displayProperty=fullName>的根元素上定義, 可以在控制項進入特定狀態時觸發動畫。</span><span class="sxs-lookup"><span data-stu-id="b07ce-236">By defining a <xref:System.Windows.VisualStateManager?displayProperty=fullName> on the root element of a control template, you can trigger animations when a control enters a specific state.</span></span> <span data-ttu-id="b07ce-237">聲明`VisualStateManager`<xref:System.Windows.VisualStateGroup><xref:System.Windows.VisualState>和 要觀察的哪些組合。</span><span class="sxs-lookup"><span data-stu-id="b07ce-237">The `VisualStateManager` declares which combinations of <xref:System.Windows.VisualStateGroup> and <xref:System.Windows.VisualState> to watch.</span></span> <span data-ttu-id="b07ce-238">當控制項進入監視狀態時,`VisaulStateManager`將啟動 由定義的動畫。</span><span class="sxs-lookup"><span data-stu-id="b07ce-238">When the control enters a watched state, the animation defined by the `VisaulStateManager` is started.</span></span>

<span data-ttu-id="b07ce-239">例如,以下 XAML`CommonStates.MouseOver`代碼監視 狀態,為`backgroundElement`名為的元素的填充顏色設置動畫。</span><span class="sxs-lookup"><span data-stu-id="b07ce-239">For example, the following XAML code watches the `CommonStates.MouseOver` state to animate the fill color of the element named `backgroundElement`.</span></span> <span data-ttu-id="b07ce-240">當控件返回到狀態`CommonStates.Normal`時,將還原`backgroundElement`命名 元素的填充顏色。</span><span class="sxs-lookup"><span data-stu-id="b07ce-240">When the control returns to the `CommonStates.Normal` state, the fill color of the element named `backgroundElement` is restored.</span></span>

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

<span data-ttu-id="b07ce-241">有關情節提要的詳細資訊,請參閱[情節提要概述](../../framework/wpf/graphics-multimedia/storyboards-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b07ce-241">For more information about storyboards, see [Storyboards Overview](../../framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span>

## <a name="shared-resources-and-themes"></a><span data-ttu-id="b07ce-242">分享資源及主題</span><span class="sxs-lookup"><span data-stu-id="b07ce-242">Shared resources and themes</span></span>

<span data-ttu-id="b07ce-243">典型的 WPF 應用可能具有多個在整個應用中應用的 UI 資源。</span><span class="sxs-lookup"><span data-stu-id="b07ce-243">A typical WPF app might have multiple UI resources that are applied throughout the app.</span></span> <span data-ttu-id="b07ce-244">總之,這組資源可以被視為應用的主題。</span><span class="sxs-lookup"><span data-stu-id="b07ce-244">Collectively, this set of resources can be considered the theme for the app.</span></span> <span data-ttu-id="b07ce-245">WPF 透過使用封裝<xref:System.Windows.ResourceDictionary>為類的資源字典,支援將UI資源打包為主題。</span><span class="sxs-lookup"><span data-stu-id="b07ce-245">WPF provides support for packaging UI resources as a theme by using a resource dictionary that is encapsulated as the <xref:System.Windows.ResourceDictionary> class.</span></span>

<span data-ttu-id="b07ce-246">WPF 主題通過使用 WPF 公開的樣式和範本機制來自定義任何元素的可視化物件來定義。</span><span class="sxs-lookup"><span data-stu-id="b07ce-246">WPF themes are defined by using the styling and templating mechanism that WPF exposes for customizing the visuals of any element.</span></span>

<span data-ttu-id="b07ce-247">WPF 主題資源存儲在嵌入式資源字典中。</span><span class="sxs-lookup"><span data-stu-id="b07ce-247">WPF theme resources are stored in embedded resource dictionaries.</span></span> <span data-ttu-id="b07ce-248">這些資源字典必須內嵌在已簽署的組件內，並且可內嵌在與程式碼本身相同的組件中，也可內嵌在並存的組件中。</span><span class="sxs-lookup"><span data-stu-id="b07ce-248">These resource dictionaries must be embedded within a signed assembly, and can either be embedded in the same assembly as the code itself or in a side-by-side assembly.</span></span> <span data-ttu-id="b07ce-249">對於包含 WPF 控件的程式集,主題資源位於一系列並行程式集中。</span><span class="sxs-lookup"><span data-stu-id="b07ce-249">For PresentationFramework.dll, the assembly that contains WPF controls, theme resources are in a series of side-by-side assemblies.</span></span>

<span data-ttu-id="b07ce-250">當搜尋元素的樣式時，佈景主題會成為最後一個要查看的地方。</span><span class="sxs-lookup"><span data-stu-id="b07ce-250">The theme becomes the last place to look when searching for the style of an element.</span></span> <span data-ttu-id="b07ce-251">通常,搜索將首先遍走元素樹以搜索適當的資源,然後查看應用資源集合,最後查詢系統。</span><span class="sxs-lookup"><span data-stu-id="b07ce-251">Typically, the search will begin by walking up the element tree searching for an appropriate resource, then look in the app resource collection and finally query the system.</span></span> <span data-ttu-id="b07ce-252">這使應用開發人員有機會在到達主題之前重新定義樹或應用級別上任何對象的樣式。</span><span class="sxs-lookup"><span data-stu-id="b07ce-252">This gives app developers a chance to redefine the style for any object at the tree or app level before reaching the theme.</span></span>

<span data-ttu-id="b07ce-253">您可以將資源字典定義為單個檔,以便跨多個應用重用主題。</span><span class="sxs-lookup"><span data-stu-id="b07ce-253">You can define resource dictionaries as individual files that enable you to reuse a theme across multiple apps.</span></span> <span data-ttu-id="b07ce-254">您也可以透過定義多個資源字典來提供類型相同但值不同的資源，以建立可切換的佈景主題。</span><span class="sxs-lookup"><span data-stu-id="b07ce-254">You can also create swappable themes by defining multiple resource dictionaries that provide the same types of resources but with different values.</span></span> <span data-ttu-id="b07ce-255">在應用級別重新定義這些樣式或其他資源是蒙皮應用的建議方法。</span><span class="sxs-lookup"><span data-stu-id="b07ce-255">Redefining these styles or other resources at the app level is the recommended approach for skinning an app.</span></span>

<span data-ttu-id="b07ce-256">要跨應用共享一組資源(包括樣式和範本),可以創建 XAML 檔並定義<xref:System.Windows.ResourceDictionary>`shared.xaml`包含對 檔的引用。</span><span class="sxs-lookup"><span data-stu-id="b07ce-256">To share a set of resources, including styles and templates, across apps, you can create a XAML file and define a <xref:System.Windows.ResourceDictionary> that includes reference to a `shared.xaml` file.</span></span>

```xaml
<ResourceDictionary.MergedDictionaries>
  <ResourceDictionary Source="Shared.xaml" />
</ResourceDictionary.MergedDictionaries>
```

<span data-ttu-id="b07ce-257">它是的`shared.xaml`共用,它本身定義了<xref:System.Windows.ResourceDictionary>包含一組樣式和畫筆資源的 ,使應用中的控制項具有一致的外觀。</span><span class="sxs-lookup"><span data-stu-id="b07ce-257">It is the sharing of `shared.xaml`, which itself defines a <xref:System.Windows.ResourceDictionary> that contains a set of style and brush resources, that enables the controls in an app to have a consistent look.</span></span>

<span data-ttu-id="b07ce-258">有關詳細資訊,請參閱[合併的資源字典](../../framework/wpf/advanced/merged-resource-dictionaries.md)。</span><span class="sxs-lookup"><span data-stu-id="b07ce-258">For more information, see [Merged resource dictionaries](../../framework/wpf/advanced/merged-resource-dictionaries.md).</span></span>

<span data-ttu-id="b07ce-259">如果要為自定義控制項建立主題,請參閱[控制件創作概述](../../framework/wpf/controls/control-authoring-overview.md#defining-resources-at-the-theme-level)**的主題級別部分的"定義資源**"。</span><span class="sxs-lookup"><span data-stu-id="b07ce-259">If you are creating a theme for your custom control, see the **Defining resources at the theme level** section of the [Control authoring overview](../../framework/wpf/controls/control-authoring-overview.md#defining-resources-at-the-theme-level).</span></span>

## <a name="see-also"></a><span data-ttu-id="b07ce-260">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b07ce-260">See also</span></span>

- [<span data-ttu-id="b07ce-261">WPF 中的 Pack URI</span><span class="sxs-lookup"><span data-stu-id="b07ce-261">Pack URIs in WPF</span></span>](../../framework/wpf/app-development/pack-uris-in-wpf.md)
- [<span data-ttu-id="b07ce-262">操作說明：尋找 ControlTemplate 產生的元素</span><span class="sxs-lookup"><span data-stu-id="b07ce-262">How to: Find ControlTemplate-Generated Elements</span></span>](../../framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)
- [<span data-ttu-id="b07ce-263">尋找資料樣本產生的元素</span><span class="sxs-lookup"><span data-stu-id="b07ce-263">Find DataTemplate-Generated Elements</span></span>](../../framework/wpf/data/how-to-find-datatemplate-generated-elements.md)
