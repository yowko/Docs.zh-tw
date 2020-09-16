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
# <a name="styles-and-templates-in-wpf"></a><span data-ttu-id="eb3f3-104">WPF 中的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="eb3f3-104">Styles and templates in WPF</span></span>

<span data-ttu-id="eb3f3-105">Windows Presentation Foundation (WPF) 樣式設定和範本化參考一組功能，可讓開發人員和設計人員針對其產品建立視覺效果吸引人的效果和一致的外觀。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-105">Windows Presentation Foundation (WPF) styling and templating refer to a suite of features that let developers and designers create visually compelling effects and a consistent appearance for their product.</span></span> <span data-ttu-id="eb3f3-106">自訂應用程式的外觀時，您需要強大的樣式設定和範本化模型，讓您在應用程式內和應用程式之間進行維護和共用外觀。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-106">When customizing the appearance of an app, you want a strong styling and templating model that enables maintenance and sharing of appearance within and among apps.</span></span> <span data-ttu-id="eb3f3-107">WPF 會提供該模型。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-107">WPF provides that model.</span></span>

<span data-ttu-id="eb3f3-108">WPF 樣式模型的另一項功能，就是展示和邏輯的分隔。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-108">Another feature of the WPF styling model is the separation of presentation and logic.</span></span> <span data-ttu-id="eb3f3-109">在開發人員使用 c # 或 Visual Basic 處理常式設計邏輯的同時，設計工具可以使用 XAML 來處理應用程式的外觀。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-109">Designers can work on the appearance of an app by using only XAML at the same time that developers work on the programming logic by using C# or Visual Basic.</span></span>

<span data-ttu-id="eb3f3-110">本總覽著重于應用程式的樣式設定和範本化層面，並不會討論任何資料系結概念。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-110">This overview focuses on the styling and templating aspects of the app and doesn't discuss any data-binding concepts.</span></span> <span data-ttu-id="eb3f3-111">如需有關資料繫結的資訊，請參閱[資料繫結概觀](../data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-111">For information about data binding, see [Data Binding Overview](../data/data-binding-overview.md).</span></span>

<span data-ttu-id="eb3f3-112">請務必瞭解資源，這些資源可讓您重複使用樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-112">It's important to understand resources, which are what enable styles and templates to be reused.</span></span> <span data-ttu-id="eb3f3-113">如需有關資源的詳細資訊，請參閱 [XAML 資源](xaml-resources-define.md)。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-113">For more information about resources, see [XAML Resources](xaml-resources-define.md).</span></span>

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sample"></a><span data-ttu-id="eb3f3-114">範例</span><span class="sxs-lookup"><span data-stu-id="eb3f3-114">Sample</span></span>

<span data-ttu-id="eb3f3-115">本總覽中提供的範例程式碼是以 [簡單的相片流覽應用程式](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) 為基礎，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-115">The sample code provided in this overview is based on a [simple photo browsing application](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) shown in the following illustration.</span></span>

<span data-ttu-id="eb3f3-116">![已設定樣式的 ListView](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")</span><span class="sxs-lookup"><span data-stu-id="eb3f3-116">![Styled ListView](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")</span></span>

<span data-ttu-id="eb3f3-117">這個簡單的相片範例使用樣式設定和範本化，來創造引人注目的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-117">This simple photo sample uses styling and templating to create a visually compelling user experience.</span></span> <span data-ttu-id="eb3f3-118">此範例有兩個 <xref:System.Windows.Controls.TextBlock> 元素，以及一個系結 <xref:System.Windows.Controls.ListBox> 至影像清單的控制項。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-118">The sample has two <xref:System.Windows.Controls.TextBlock> elements and a <xref:System.Windows.Controls.ListBox> control that is bound to a list of images.</span></span>

<span data-ttu-id="eb3f3-119">如需完整範例，請參閱[樣式設定和範本化範例簡介 (英文)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-119">For the complete sample, see [Introduction to Styling and Templating Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="styles"></a><span data-ttu-id="eb3f3-120">樣式</span><span class="sxs-lookup"><span data-stu-id="eb3f3-120">Styles</span></span>

<span data-ttu-id="eb3f3-121">您可以將 <xref:System.Windows.Style> 視為將一組屬性值套用至多個元素的方便方式。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-121">You can think of a <xref:System.Windows.Style> as a convenient way to apply a set of property values to multiple elements.</span></span> <span data-ttu-id="eb3f3-122">您可以在任何衍生自或的專案上使用樣式， <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> 例如 <xref:System.Windows.Window> 或 <xref:System.Windows.Controls.Button> 。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-122">You can use a style on any element that derives from <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement> such as a <xref:System.Windows.Window> or a <xref:System.Windows.Controls.Button>.</span></span>

<span data-ttu-id="eb3f3-123">宣告樣式最常見的方式，就是在 XAML 檔案中的區段中的資源 `Resources` 。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-123">The most common way to declare a style is as a resource in the `Resources` section in a XAML file.</span></span> <span data-ttu-id="eb3f3-124">由於樣式是資源，因此它們會遵守適用于所有資源的相同範圍規則。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-124">Because styles are resources, they obey the same scoping rules that apply to all resources.</span></span> <span data-ttu-id="eb3f3-125">單純地說，您宣告的樣式會影響可以套用樣式的位置。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-125">Put simply, where you declare a style affects where the style can be applied.</span></span> <span data-ttu-id="eb3f3-126">例如，如果您在應用程式定義 XAML 檔案的根項目中宣告樣式，則可以在應用程式中的任何位置使用該樣式。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-126">For example, if you declare the style in the root element of your app definition XAML file, the style can be used anywhere in your app.</span></span>

<span data-ttu-id="eb3f3-127">例如，下列 XAML 程式碼會宣告兩種樣式 `TextBlock` ：一個自動套用至所有 `TextBlock` 元素，另一個則必須明確參考。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-127">For example, the following XAML code declares two styles for a `TextBlock`, one automatically applied to all `TextBlock` elements, and another that must be explicitly referenced.</span></span>

[!code-xaml[SnippetDefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

<span data-ttu-id="eb3f3-128">以下是使用上述宣告的樣式範例。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-128">Here is an example of the styles declared above being used.</span></span>

[!code-xaml[SnippetTextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

![樣式的 textblock](./media/styles-and-templates-overview/stylingintro-textblocks.png)

<span data-ttu-id="eb3f3-130">如需詳細資訊，請參閱 [建立控制項的樣式](styles-templates-create-apply-style.md)。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-130">For more information, see [Create a style for a control](styles-templates-create-apply-style.md).</span></span>

## <a name="controltemplates"></a><span data-ttu-id="eb3f3-131">ControlTemplates</span><span class="sxs-lookup"><span data-stu-id="eb3f3-131">ControlTemplates</span></span>

<span data-ttu-id="eb3f3-132">在 WPF 中， <xref:System.Windows.Controls.ControlTemplate> 控制項的會定義控制項的外觀。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-132">In WPF, the <xref:System.Windows.Controls.ControlTemplate> of a control defines the appearance of the control.</span></span> <span data-ttu-id="eb3f3-133">您可以藉由定義新的控制項 <xref:System.Windows.Controls.ControlTemplate> 並將其指派給控制項，來變更控制項的結構和外觀。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-133">You can change the structure and appearance of a control by defining a new <xref:System.Windows.Controls.ControlTemplate> and assigning it to a control.</span></span> <span data-ttu-id="eb3f3-134">在許多情況下，範本提供您足夠的彈性，因此您不必撰寫自己的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-134">In many cases, templates give you enough flexibility so that you do not have to write your own custom controls.</span></span>

<span data-ttu-id="eb3f3-135">每個控制項都有指派給 Control 的預設範本 [。 template](xref:System.Windows.Controls.Control.Template) 屬性。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-135">Each control has a default template assigned to the [Control.Template](xref:System.Windows.Controls.Control.Template) property.</span></span> <span data-ttu-id="eb3f3-136">此範本會將控制項的視覺呈現與控制項的功能連接在一起。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-136">The template connects the visual presentation of the control with the control's capabilities.</span></span> <span data-ttu-id="eb3f3-137">由於您是在 XAML 中定義範本，因此您可以變更控制項的外觀，而不需要撰寫任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-137">Because you define a template in XAML, you can change the control's appearance without writing any code.</span></span> <span data-ttu-id="eb3f3-138">每個範本都是針對特定的控制項（例如）所設計 <xref:System.Windows.Controls.Button> 。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-138">Each template is designed for a specific control, such as a <xref:System.Windows.Controls.Button>.</span></span>

<span data-ttu-id="eb3f3-139">您通常會在 XAML 檔案的區段上將範本宣告為資源 `Resources` 。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-139">Commonly you declare a template as a resource on the `Resources` section of a XAML file.</span></span> <span data-ttu-id="eb3f3-140">如同所有資源，適用範圍規則。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-140">As with all resources, scoping rules apply.</span></span>

<span data-ttu-id="eb3f3-141">控制項範本與樣式有許多相關。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-141">Control templates are a lot more involved than a style.</span></span> <span data-ttu-id="eb3f3-142">這是因為控制項範本會重寫整個控制項的視覺外觀，而樣式只會將屬性變更套用至現有的控制項。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-142">This is because the control template rewrites the visual appearance of the entire control, while a style simply applies property changes to the existing control.</span></span> <span data-ttu-id="eb3f3-143">不過，由於控制項的範本是藉由設定 [ [範本](xref:System.Windows.Controls.Control.Template) ] 屬性來套用，因此您可以使用樣式來定義或設定範本。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-143">However, since the template of a control is applied by setting the [Control.Template](xref:System.Windows.Controls.Control.Template) property, you can use a style to define or set a template.</span></span>

<span data-ttu-id="eb3f3-144">設計工具通常可讓您建立現有範本的複本並加以修改。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-144">Designers generally allow you to create a copy of an existing template and modify it.</span></span> <span data-ttu-id="eb3f3-145">例如，在 Visual Studio WPF 設計工具中，選取 `CheckBox` 控制項，然後以滑鼠右鍵按一下並選取 [**編輯範本**  >  **建立複本**]。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-145">For example, in the Visual Studio WPF designer, select a `CheckBox` control, and then right-click and select **Edit template** > **Create a copy**.</span></span> <span data-ttu-id="eb3f3-146">此命令會產生 *可定義範本的樣式*。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-146">This command generates a *style that defines a template*.</span></span>

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

<span data-ttu-id="eb3f3-147">編輯範本的複本是瞭解範本運作方式的絕佳方式。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-147">Editing a copy of a template is a great way to learn how templates work.</span></span> <span data-ttu-id="eb3f3-148">除了建立新的空白範本，您還可以更輕鬆地編輯複本並變更視覺效果簡報的一些層面。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-148">Instead of creating a new blank template, it's easier to edit a copy and change a few aspects of the visual presentation.</span></span>

<span data-ttu-id="eb3f3-149">如需範例，請參閱 [建立控制項的範本](../themes/how-to-create-apply-template.md)。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-149">For an example, see [Create a template for a control](../themes/how-to-create-apply-template.md).</span></span>

### <a name="templatebinding"></a><span data-ttu-id="eb3f3-150">TemplateBinding</span><span class="sxs-lookup"><span data-stu-id="eb3f3-150">TemplateBinding</span></span>

<span data-ttu-id="eb3f3-151">您可能已經注意到，在上一節中定義的範本資源使用 [TemplateBinding 標記延伸](/dotnet/desktop/wpf/advanced/templatebinding-markup-extension)。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-151">You may have noticed that the template resource defined in the previous section uses the [TemplateBinding Markup Extension](/dotnet/desktop/wpf/advanced/templatebinding-markup-extension).</span></span> <span data-ttu-id="eb3f3-152">`TemplateBinding`是範本案例的優化形式的系結，類似于使用所建立的系結 `{Binding RelativeSource={RelativeSource TemplatedParent}}` 。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-152">A `TemplateBinding` is an optimized form of a binding for template scenarios, analogous to a binding constructed with `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="eb3f3-153">`TemplateBinding` 適用于將範本的元件系結至控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-153">`TemplateBinding` is useful for binding parts of the template to properties of the control.</span></span> <span data-ttu-id="eb3f3-154">例如，每個控制項都有一個 <xref:System.Windows.Controls.Control.BorderThickness> 屬性。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-154">For example, each control has a <xref:System.Windows.Controls.Control.BorderThickness> property.</span></span> <span data-ttu-id="eb3f3-155">使用 `TemplateBinding` 來管理範本中的哪個元素會受到此控制項設定的影響。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-155">Use a `TemplateBinding` to manage which element in the template is affected by this control setting.</span></span>

### <a name="contentcontrol-and-itemscontrol"></a><span data-ttu-id="eb3f3-156">ContentControl 和 ItemsControl</span><span class="sxs-lookup"><span data-stu-id="eb3f3-156">ContentControl and ItemsControl</span></span>

<span data-ttu-id="eb3f3-157">如果 <xref:System.Windows.Controls.ContentPresenter> 在的中宣告，則會自動系結 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.ContentControl> <xref:System.Windows.Controls.ContentPresenter> 至 <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> 和 <xref:System.Windows.Controls.ContentControl.Content%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-157">If a <xref:System.Windows.Controls.ContentPresenter> is declared in the <xref:System.Windows.Controls.ControlTemplate> of a <xref:System.Windows.Controls.ContentControl>, the <xref:System.Windows.Controls.ContentPresenter> will automatically bind to the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> and <xref:System.Windows.Controls.ContentControl.Content%2A> properties.</span></span> <span data-ttu-id="eb3f3-158">同樣地， <xref:System.Windows.Controls.ItemsPresenter> 在中的會 <xref:System.Windows.Controls.ControlTemplate> 自動系結 <xref:System.Windows.Controls.ItemsControl> 至 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 和 <xref:System.Windows.Controls.ItemsControl.Items%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-158">Likewise, an <xref:System.Windows.Controls.ItemsPresenter> that is in the <xref:System.Windows.Controls.ControlTemplate> of an <xref:System.Windows.Controls.ItemsControl> will automatically bind to the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> and <xref:System.Windows.Controls.ItemsControl.Items%2A> properties.</span></span>

## <a name="datatemplates"></a><span data-ttu-id="eb3f3-159">DataTemplates</span><span class="sxs-lookup"><span data-stu-id="eb3f3-159">DataTemplates</span></span>

<span data-ttu-id="eb3f3-160">在此範例應用程式中，有一個系結 <xref:System.Windows.Controls.ListBox> 至相片清單的控制項。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-160">In this sample app, there is a <xref:System.Windows.Controls.ListBox> control that is bound to a list of photos.</span></span>

[!code-xaml[ListBox](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window3.xaml#SnippetListBox)]

<span data-ttu-id="eb3f3-161">這 <xref:System.Windows.Controls.ListBox> 目前看起來如下所示。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-161">This <xref:System.Windows.Controls.ListBox> currently looks like the following.</span></span>

<span data-ttu-id="eb3f3-162">![套用範本之前的 ListBox](./media/styles-and-templates-overview/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")</span><span class="sxs-lookup"><span data-stu-id="eb3f3-162">![ListBox before applying template](./media/styles-and-templates-overview/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")</span></span>

<span data-ttu-id="eb3f3-163">大多數控制項都有某個型別的內容，而該內容通常來自您要繫結的資料。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-163">Most controls have some type of content, and that content often comes from data that you are binding to.</span></span> <span data-ttu-id="eb3f3-164">在此範例中，該資料是相片清單。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-164">In this sample, the data is the list of photos.</span></span> <span data-ttu-id="eb3f3-165">在 WPF 中，您可以使用 <xref:System.Windows.DataTemplate> 來定義資料的視覺標記法。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-165">In WPF, you use a <xref:System.Windows.DataTemplate> to define the visual representation of data.</span></span> <span data-ttu-id="eb3f3-166">基本上，您放入的內容會 <xref:System.Windows.DataTemplate> 決定資料在轉譯應用程式中的樣子。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-166">Basically, what you put into a <xref:System.Windows.DataTemplate> determines what the data looks like in the rendered app.</span></span>

<span data-ttu-id="eb3f3-167">在我們的範例應用程式中，每個自訂 `Photo` 物件都有一個 `Source` 字串類型的屬性，可指定映射的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-167">In our sample app, each custom `Photo` object has a `Source` property of type string that specifies the file path of the image.</span></span> <span data-ttu-id="eb3f3-168">目前，相片物件是顯示成檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-168">Currently, the photo objects appear as file paths.</span></span>

[!code-csharp[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Photo.cs#PhotoClass)]
[!code-vb[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/Photo.vb#PhotoClass)]

<span data-ttu-id="eb3f3-169">若要讓相片以影像形式出現，您可以建立 <xref:System.Windows.DataTemplate> 做為資源。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-169">For the photos to appear as images, you create a <xref:System.Windows.DataTemplate> as a resource.</span></span>

[!code-xaml[DataTemplate](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window4.xaml#SnippetDataTemplate)]

<span data-ttu-id="eb3f3-170">請注意， <xref:System.Windows.DataTemplate.DataType%2A> 屬性與的屬性類似 <xref:System.Windows.Style.TargetType%2A> <xref:System.Windows.Style> 。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-170">Notice that the <xref:System.Windows.DataTemplate.DataType%2A> property is similar to the <xref:System.Windows.Style.TargetType%2A> property of the <xref:System.Windows.Style>.</span></span> <span data-ttu-id="eb3f3-171">如果您 <xref:System.Windows.DataTemplate> 是在 resources 區段中，當您將 <xref:System.Windows.DataTemplate.DataType%2A> 屬性指定為型別並省略時 `x:Key` ， <xref:System.Windows.DataTemplate> 會在該型別出現時套用。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-171">If your <xref:System.Windows.DataTemplate> is in the resources section, when you specify the <xref:System.Windows.DataTemplate.DataType%2A> property to a type and omit an `x:Key`, the <xref:System.Windows.DataTemplate> is applied whenever that type appears.</span></span> <span data-ttu-id="eb3f3-172">您一律可以使用指派給的選項， <xref:System.Windows.DataTemplate> `x:Key` 然後將它設定為 `StaticResource` 取得類型的屬性 <xref:System.Windows.DataTemplate> ，例如 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 屬性或 <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-172">You always have the option to assign the <xref:System.Windows.DataTemplate> with an `x:Key` and then set it as a `StaticResource` for properties that take <xref:System.Windows.DataTemplate> types, such as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> property or the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> property.</span></span>

<span data-ttu-id="eb3f3-173">基本上， <xref:System.Windows.DataTemplate> 上述範例中的會定義每次有物件時 `Photo` ，都應該在中顯示為 <xref:System.Windows.Controls.Image> <xref:System.Windows.Controls.Border> 。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-173">Essentially, the <xref:System.Windows.DataTemplate> in the above example defines that whenever there is a `Photo` object, it should appear as an <xref:System.Windows.Controls.Image> within a <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="eb3f3-174">如此一來 <xref:System.Windows.DataTemplate> ，我們的應用程式現在看起來會像這樣。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-174">With this <xref:System.Windows.DataTemplate>, our app now looks like this.</span></span>

<span data-ttu-id="eb3f3-175">![圖片影像](./media/styles-and-templates-overview/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")</span><span class="sxs-lookup"><span data-stu-id="eb3f3-175">![Photo image](./media/styles-and-templates-overview/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")</span></span>

<span data-ttu-id="eb3f3-176">資料範本化模型還提供其他功能。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-176">The data templating model provides other features.</span></span> <span data-ttu-id="eb3f3-177">例如，如果您要顯示的集合資料包含使用 <xref:System.Windows.Controls.HeaderedItemsControl> 類型（例如或）的其他集合 <xref:System.Windows.Controls.Menu> ，則 <xref:System.Windows.Controls.TreeView> 會有 <xref:System.Windows.HierarchicalDataTemplate> 。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-177">For example, if you are displaying collection data that contains other collections using a <xref:System.Windows.Controls.HeaderedItemsControl> type such as a <xref:System.Windows.Controls.Menu> or a <xref:System.Windows.Controls.TreeView>, there is the <xref:System.Windows.HierarchicalDataTemplate>.</span></span> <span data-ttu-id="eb3f3-178">另一個資料範本化功能是 <xref:System.Windows.Controls.DataTemplateSelector> ，可讓您 <xref:System.Windows.DataTemplate> 根據自訂邏輯選擇要使用的。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-178">Another data templating feature is the <xref:System.Windows.Controls.DataTemplateSelector>, which allows you to choose a <xref:System.Windows.DataTemplate> to use based on custom logic.</span></span> <span data-ttu-id="eb3f3-179">如需詳細資訊，請參閱[資料範本化概觀](/dotnet/desktop/wpf/data/data-templating-overview)，其中提供不同資料範本化功能的更深入探討。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-179">For more information, see [Data Templating Overview](/dotnet/desktop/wpf/data/data-templating-overview), which provides a more in-depth discussion of the different data templating features.</span></span>

## <a name="triggers"></a><span data-ttu-id="eb3f3-180">觸發程序</span><span class="sxs-lookup"><span data-stu-id="eb3f3-180">Triggers</span></span>

<span data-ttu-id="eb3f3-181">觸發程序會在屬性值發生變更或在某個事件被引發時，設定屬性或啟動動作 (例如動畫)。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-181">A trigger sets properties or starts actions, such as an animation, when a property value changes or when an event is raised.</span></span> <span data-ttu-id="eb3f3-182"><xref:System.Windows.Style>、 <xref:System.Windows.Controls.ControlTemplate> 和都 <xref:System.Windows.DataTemplate> 具有 `Triggers` 可包含一組觸發程式的屬性。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-182"><xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, and <xref:System.Windows.DataTemplate> all have a `Triggers` property that can contain a set of triggers.</span></span> <span data-ttu-id="eb3f3-183">有數種類型的觸發程式。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-183">There are several types of triggers.</span></span>

### <a name="propertytriggers"></a><span data-ttu-id="eb3f3-184">PropertyTriggers</span><span class="sxs-lookup"><span data-stu-id="eb3f3-184">PropertyTriggers</span></span>

<span data-ttu-id="eb3f3-185"><xref:System.Windows.Trigger>，會根據屬性的值來設定屬性值或啟動動作，稱為屬性觸發程式。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-185">A <xref:System.Windows.Trigger> that sets property values or starts actions based on the value of a property is called a property trigger.</span></span>

<span data-ttu-id="eb3f3-186">若要示範如何使用屬性觸發程式，您可以讓每個 <xref:System.Windows.Controls.ListBoxItem> 部分透明，除非已選取它。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-186">To demonstrate how to use property triggers, you can make each <xref:System.Windows.Controls.ListBoxItem> partially transparent unless it is selected.</span></span> <span data-ttu-id="eb3f3-187">下列樣式會將的 <xref:System.Windows.UIElement.Opacity%2A> 值設定 <xref:System.Windows.Controls.ListBoxItem> 為 `0.5` 。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-187">The following style sets the <xref:System.Windows.UIElement.Opacity%2A> value of a <xref:System.Windows.Controls.ListBoxItem> to `0.5`.</span></span> <span data-ttu-id="eb3f3-188">但是，當 <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> 屬性是時， `true` <xref:System.Windows.UIElement.Opacity%2A> 會設定為 `1.0` 。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-188">When the <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> property is `true`, however, the <xref:System.Windows.UIElement.Opacity%2A> is set to `1.0`.</span></span>

[!code-xaml[PropertyTrigger](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window5.xaml#SnippetPropertyTrigger)]

<span data-ttu-id="eb3f3-189">這個範例會使用 <xref:System.Windows.Trigger> 來設定屬性值，但請注意，此 <xref:System.Windows.Trigger> 類別也有 <xref:System.Windows.TriggerBase.EnterActions%2A> 和 <xref:System.Windows.TriggerBase.ExitActions%2A> 屬性可讓觸發程式執行動作。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-189">This example uses a <xref:System.Windows.Trigger> to set a property value, but note that the <xref:System.Windows.Trigger> class also has the <xref:System.Windows.TriggerBase.EnterActions%2A> and <xref:System.Windows.TriggerBase.ExitActions%2A> properties that enable a trigger to perform actions.</span></span>

<span data-ttu-id="eb3f3-190">請注意，的 <xref:System.Windows.FrameworkElement.MaxHeight%2A> 屬性 <xref:System.Windows.Controls.ListBoxItem> 會設定為 `75` 。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-190">Notice that the <xref:System.Windows.FrameworkElement.MaxHeight%2A> property of the <xref:System.Windows.Controls.ListBoxItem> is set to `75`.</span></span> <span data-ttu-id="eb3f3-191">在下圖中，第三個專案是選取的專案。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-191">In the following illustration, the third item is the selected item.</span></span>

<span data-ttu-id="eb3f3-192">![已設定樣式的 ListView](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")</span><span class="sxs-lookup"><span data-stu-id="eb3f3-192">![Styled ListView](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")</span></span>

### <a name="eventtriggers-and-storyboards"></a><span data-ttu-id="eb3f3-193">EventTrigger 和分鏡腳本</span><span class="sxs-lookup"><span data-stu-id="eb3f3-193">EventTriggers and Storyboards</span></span>

<span data-ttu-id="eb3f3-194">另一種類型的觸發程式是 <xref:System.Windows.EventTrigger> ，它會根據事件的發生次數來啟動一組動作。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-194">Another type of trigger is the <xref:System.Windows.EventTrigger>, which starts a set of actions based on the occurrence of an event.</span></span> <span data-ttu-id="eb3f3-195">例如，下列 <xref:System.Windows.EventTrigger> 物件指定當滑鼠指標進入時，屬性會在 <xref:System.Windows.Controls.ListBoxItem> <xref:System.Windows.FrameworkElement.MaxHeight%2A> `90` `0.2` 第二個句點的動畫上繪製成值。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-195">For example, the following <xref:System.Windows.EventTrigger> objects specify that when the mouse pointer enters the <xref:System.Windows.Controls.ListBoxItem>, the <xref:System.Windows.FrameworkElement.MaxHeight%2A> property animates to a value of `90` over a `0.2` second period.</span></span> <span data-ttu-id="eb3f3-196">當滑鼠指標從項目移開時，該屬性會在 `1` 秒的期間內恢復成原始值。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-196">When the mouse moves away from the item, the property returns to the original value over a period of `1` second.</span></span> <span data-ttu-id="eb3f3-197">請注意，不需要指定 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 動畫的值 <xref:System.Windows.ContentElement.MouseLeave> 。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-197">Note how it is not necessary to specify a <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> value for the <xref:System.Windows.ContentElement.MouseLeave> animation.</span></span> <span data-ttu-id="eb3f3-198">這是因為動畫能夠記錄原始值。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-198">This is because the animation is able to keep track of the original value.</span></span>

[!code-xaml[StyleEventTriggers](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window6.xaml#SnippetStyleEventTriggers)]

<span data-ttu-id="eb3f3-199">如需詳細資訊，請參閱分鏡腳本 [總覽](/dotnet/desktop/wpf/graphics-multimedia/storyboards-overview)。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-199">For more information, see the [Storyboards overview](/dotnet/desktop/wpf/graphics-multimedia/storyboards-overview).</span></span>

<span data-ttu-id="eb3f3-200">在下圖中，滑鼠指向第三個專案。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-200">In the following illustration, the mouse is pointing to the third item.</span></span>

<span data-ttu-id="eb3f3-201">![樣式範例螢幕擷取畫面](./media/styles-and-templates-overview/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span><span class="sxs-lookup"><span data-stu-id="eb3f3-201">![Styling sample screenshot](./media/styles-and-templates-overview/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span></span>

### <a name="multitriggers-datatriggers-and-multidatatriggers"></a><span data-ttu-id="eb3f3-202">MultiTrigger、DataTrigger 及 MultiDataTrigger</span><span class="sxs-lookup"><span data-stu-id="eb3f3-202">MultiTriggers, DataTriggers, and MultiDataTriggers</span></span>

<span data-ttu-id="eb3f3-203">除了 <xref:System.Windows.Trigger> 和 <xref:System.Windows.EventTrigger> 之外，還有其他類型的觸發程式。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-203">In addition to <xref:System.Windows.Trigger> and <xref:System.Windows.EventTrigger>, there are other types of triggers.</span></span> <span data-ttu-id="eb3f3-204"><xref:System.Windows.MultiTrigger> 可讓您根據多個條件來設定屬性值。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-204"><xref:System.Windows.MultiTrigger> allows you to set property values based on multiple conditions.</span></span> <span data-ttu-id="eb3f3-205"><xref:System.Windows.DataTrigger> <xref:System.Windows.MultiDataTrigger> 當條件的屬性是資料系結時，您可以使用和。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-205">You use <xref:System.Windows.DataTrigger> and <xref:System.Windows.MultiDataTrigger> when the property of your condition is data-bound.</span></span>

## <a name="visual-states"></a><span data-ttu-id="eb3f3-206">視覺狀態</span><span class="sxs-lookup"><span data-stu-id="eb3f3-206">Visual States</span></span>

<span data-ttu-id="eb3f3-207">控制項一律處於特定 **狀態**。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-207">Controls are always in a specific **state**.</span></span> <span data-ttu-id="eb3f3-208">例如，當滑鼠移到控制項的介面上方時，控制項就會被視為處於的一般狀態 `MouseOver` 。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-208">For example, when the mouse moves over the surface of a control, the control is considered to be in a common state of `MouseOver`.</span></span> <span data-ttu-id="eb3f3-209">沒有特定狀態的控制項會被視為處於一般 `Normal` 狀態。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-209">A control without a specific state is considered to be in the common `Normal` state.</span></span> <span data-ttu-id="eb3f3-210">狀態分成群組，而先前提及的狀態是狀態群組的一部分 `CommonStates` 。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-210">States are broken into groups, and the previously mentioned states are part of the state group `CommonStates`.</span></span> <span data-ttu-id="eb3f3-211">大部分的控制項都有兩個狀態群組： `CommonStates` 和 `FocusStates` 。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-211">Most controls have two state groups: `CommonStates` and `FocusStates`.</span></span> <span data-ttu-id="eb3f3-212">針對套用至控制項的每個狀態群組，控制項一律會處於每個群組的其中一個狀態，例如 `CommonStates.MouseOver` 和 `FocusStates.Unfocused` 。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-212">Of each state group applied to a control, a control is always in one state of each group, such as `CommonStates.MouseOver` and `FocusStates.Unfocused`.</span></span> <span data-ttu-id="eb3f3-213">不過，控制項不能在相同群組中的兩個不同狀態，例如 `CommonStates.Normal` 和 `CommonStates.Disabled` 。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-213">However, a control can't be in two different states within the same group, such as `CommonStates.Normal` and `CommonStates.Disabled`.</span></span> <span data-ttu-id="eb3f3-214">以下是大部分控制項辨識和使用的狀態表格。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-214">Here is a table of states most controls recognize and use.</span></span>

| <span data-ttu-id="eb3f3-215">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="eb3f3-215">VisualState Name</span></span> | <span data-ttu-id="eb3f3-216">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="eb3f3-216">VisualStateGroup Name</span></span> | <span data-ttu-id="eb3f3-217">描述</span><span class="sxs-lookup"><span data-stu-id="eb3f3-217">Description</span></span> |
| ---------------- | --------------------- | ----------- |
| <span data-ttu-id="eb3f3-218">正常</span><span class="sxs-lookup"><span data-stu-id="eb3f3-218">Normal</span></span>           | <span data-ttu-id="eb3f3-219">CommonStates</span><span class="sxs-lookup"><span data-stu-id="eb3f3-219">CommonStates</span></span>          | <span data-ttu-id="eb3f3-220">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-220">The default state.</span></span> |
| <span data-ttu-id="eb3f3-221">MouseOver</span><span class="sxs-lookup"><span data-stu-id="eb3f3-221">MouseOver</span></span>        | <span data-ttu-id="eb3f3-222">CommonStates</span><span class="sxs-lookup"><span data-stu-id="eb3f3-222">CommonStates</span></span>          | <span data-ttu-id="eb3f3-223">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-223">The mouse pointer is positioned over the control.</span></span> |
| <span data-ttu-id="eb3f3-224">按下</span><span class="sxs-lookup"><span data-stu-id="eb3f3-224">Pressed</span></span>          | <span data-ttu-id="eb3f3-225">CommonStates</span><span class="sxs-lookup"><span data-stu-id="eb3f3-225">CommonStates</span></span>          | <span data-ttu-id="eb3f3-226">已按下控制項。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-226">The control is pressed.</span></span> |
| <span data-ttu-id="eb3f3-227">已停用</span><span class="sxs-lookup"><span data-stu-id="eb3f3-227">Disabled</span></span>         | <span data-ttu-id="eb3f3-228">CommonStates</span><span class="sxs-lookup"><span data-stu-id="eb3f3-228">CommonStates</span></span>          | <span data-ttu-id="eb3f3-229">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-229">The control is disabled.</span></span> |
| <span data-ttu-id="eb3f3-230">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="eb3f3-230">Focused</span></span>          | <span data-ttu-id="eb3f3-231">FocusStates</span><span class="sxs-lookup"><span data-stu-id="eb3f3-231">FocusStates</span></span>           | <span data-ttu-id="eb3f3-232">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-232">The control has focus.</span></span> |
| <span data-ttu-id="eb3f3-233">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="eb3f3-233">Unfocused</span></span>        | <span data-ttu-id="eb3f3-234">FocusStates</span><span class="sxs-lookup"><span data-stu-id="eb3f3-234">FocusStates</span></span>           | <span data-ttu-id="eb3f3-235">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-235">The control does not have focus.</span></span> |

<span data-ttu-id="eb3f3-236">藉由在 <xref:System.Windows.VisualStateManager?displayProperty=fullName> 控制項範本的根項目上定義，您就可以在控制項進入特定狀態時觸發動畫。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-236">By defining a <xref:System.Windows.VisualStateManager?displayProperty=fullName> on the root element of a control template, you can trigger animations when a control enters a specific state.</span></span> <span data-ttu-id="eb3f3-237">會宣告要 `VisualStateManager` <xref:System.Windows.VisualStateGroup> 監看的和的組合 <xref:System.Windows.VisualState> 。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-237">The `VisualStateManager` declares which combinations of <xref:System.Windows.VisualStateGroup> and <xref:System.Windows.VisualState> to watch.</span></span> <span data-ttu-id="eb3f3-238">當控制項進入監看的狀態時，就會啟動所定義的動畫 `VisaulStateManager` 。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-238">When the control enters a watched state, the animation defined by the `VisaulStateManager` is started.</span></span>

<span data-ttu-id="eb3f3-239">例如，下列 XAML 程式碼會監看 `CommonStates.MouseOver` 狀態，以建立名為之元素填滿色彩的動畫 `backgroundElement` 。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-239">For example, the following XAML code watches the `CommonStates.MouseOver` state to animate the fill color of the element named `backgroundElement`.</span></span> <span data-ttu-id="eb3f3-240">當控制項返回 `CommonStates.Normal` 狀態時，會還原名為的專案之填滿色彩 `backgroundElement` 。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-240">When the control returns to the `CommonStates.Normal` state, the fill color of the element named `backgroundElement` is restored.</span></span>

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

<span data-ttu-id="eb3f3-241">如需分鏡腳本的詳細資訊，請參閱分鏡腳本 [總覽](/dotnet/desktop/wpf/graphics-multimedia/storyboards-overview)。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-241">For more information about storyboards, see [Storyboards Overview](/dotnet/desktop/wpf/graphics-multimedia/storyboards-overview).</span></span>

## <a name="shared-resources-and-themes"></a><span data-ttu-id="eb3f3-242">共用的資源和主題</span><span class="sxs-lookup"><span data-stu-id="eb3f3-242">Shared resources and themes</span></span>

<span data-ttu-id="eb3f3-243">一般的 WPF 應用程式可能會有多個在應用程式中套用的 UI 資源。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-243">A typical WPF app might have multiple UI resources that are applied throughout the app.</span></span> <span data-ttu-id="eb3f3-244">這組資源統稱可視為應用程式的主題。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-244">Collectively, this set of resources can be considered the theme for the app.</span></span> <span data-ttu-id="eb3f3-245">WPF 支援使用封裝為類別的資源字典，將 UI 資源封裝成主題 <xref:System.Windows.ResourceDictionary> 。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-245">WPF provides support for packaging UI resources as a theme by using a resource dictionary that is encapsulated as the <xref:System.Windows.ResourceDictionary> class.</span></span>

<span data-ttu-id="eb3f3-246">WPF 主題的定義方式是使用 WPF 為了自訂任何專案的視覺效果所公開的樣式設定和範本化機制。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-246">WPF themes are defined by using the styling and templating mechanism that WPF exposes for customizing the visuals of any element.</span></span>

<span data-ttu-id="eb3f3-247">WPF 主題資源會儲存在內嵌的資源字典中。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-247">WPF theme resources are stored in embedded resource dictionaries.</span></span> <span data-ttu-id="eb3f3-248">這些資源字典必須內嵌在已簽署的組件內，並且可內嵌在與程式碼本身相同的組件中，也可內嵌在並存的組件中。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-248">These resource dictionaries must be embedded within a signed assembly, and can either be embedded in the same assembly as the code itself or in a side-by-side assembly.</span></span> <span data-ttu-id="eb3f3-249">針對 PresentationFramework.dll，包含 WPF 控制項的元件，主題資源是在一系列並存元件中。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-249">For PresentationFramework.dll, the assembly that contains WPF controls, theme resources are in a series of side-by-side assemblies.</span></span>

<span data-ttu-id="eb3f3-250">當搜尋元素的樣式時，佈景主題會成為最後一個要查看的地方。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-250">The theme becomes the last place to look when searching for the style of an element.</span></span> <span data-ttu-id="eb3f3-251">搜尋通常會先向上找出搜尋適當資源的專案樹狀結構，然後查看應用程式資源集合，最後再查詢系統。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-251">Typically, the search will begin by walking up the element tree searching for an appropriate resource, then look in the app resource collection and finally query the system.</span></span> <span data-ttu-id="eb3f3-252">這可讓應用程式開發人員有機會在到達主題之前，先重新定義樹狀結構或應用層級上任何物件的樣式。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-252">This gives app developers a chance to redefine the style for any object at the tree or app level before reaching the theme.</span></span>

<span data-ttu-id="eb3f3-253">您可以將資源字典定義為個別檔案，讓您可以跨多個應用程式重複使用主題。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-253">You can define resource dictionaries as individual files that enable you to reuse a theme across multiple apps.</span></span> <span data-ttu-id="eb3f3-254">您也可以透過定義多個資源字典來提供類型相同但值不同的資源，以建立可切換的佈景主題。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-254">You can also create swappable themes by defining multiple resource dictionaries that provide the same types of resources but with different values.</span></span> <span data-ttu-id="eb3f3-255">在應用層級重新定義這些樣式或其他資源，是將應用程式用於外觀的建議方式。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-255">Redefining these styles or other resources at the app level is the recommended approach for skinning an app.</span></span>

<span data-ttu-id="eb3f3-256">若要在應用程式之間共用一組資源，包括樣式和範本，您可以建立 XAML 檔案並定義 <xref:System.Windows.ResourceDictionary> 包含檔案參考的 `shared.xaml` 。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-256">To share a set of resources, including styles and templates, across apps, you can create a XAML file and define a <xref:System.Windows.ResourceDictionary> that includes reference to a `shared.xaml` file.</span></span>

```xaml
<ResourceDictionary.MergedDictionaries>
  <ResourceDictionary Source="Shared.xaml" />
</ResourceDictionary.MergedDictionaries>
```

<span data-ttu-id="eb3f3-257">它是的共用 `shared.xaml` ，它本身會定義 <xref:System.Windows.ResourceDictionary> 包含一組樣式和筆刷資源的，讓應用程式中的控制項能夠有一致的外觀。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-257">It is the sharing of `shared.xaml`, which itself defines a <xref:System.Windows.ResourceDictionary> that contains a set of style and brush resources, that enables the controls in an app to have a consistent look.</span></span>

<span data-ttu-id="eb3f3-258">如需詳細資訊，請參閱 [合併的資源字典](/dotnet/desktop/wpf/advanced/merged-resource-dictionaries)。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-258">For more information, see [Merged resource dictionaries](/dotnet/desktop/wpf/advanced/merged-resource-dictionaries).</span></span>

<span data-ttu-id="eb3f3-259">如果您要建立自訂控制項的主題，請參閱[控制項撰寫總覽](/dotnet/desktop/wpf/controls/control-authoring-overview#defining-resources-at-the-theme-level)的**主題層級的定義資源**一節。</span><span class="sxs-lookup"><span data-stu-id="eb3f3-259">If you are creating a theme for your custom control, see the **Defining resources at the theme level** section of the [Control authoring overview](/dotnet/desktop/wpf/controls/control-authoring-overview#defining-resources-at-the-theme-level).</span></span>

## <a name="see-also"></a><span data-ttu-id="eb3f3-260">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb3f3-260">See also</span></span>

- [<span data-ttu-id="eb3f3-261">WPF 中的 Pack URI</span><span class="sxs-lookup"><span data-stu-id="eb3f3-261">Pack URIs in WPF</span></span>](/dotnet/desktop/wpf/app-development/pack-uris-in-wpf)
- [<span data-ttu-id="eb3f3-262">作法：尋找 ControlTemplate 產生的元素</span><span class="sxs-lookup"><span data-stu-id="eb3f3-262">How to: Find ControlTemplate-Generated Elements</span></span>](/dotnet/desktop/wpf/controls/how-to-find-controltemplate-generated-elements)
- [<span data-ttu-id="eb3f3-263">尋找 DataTemplate 產生的元素</span><span class="sxs-lookup"><span data-stu-id="eb3f3-263">Find DataTemplate-Generated Elements</span></span>](/dotnet/desktop/wpf/data/how-to-find-datatemplate-generated-elements)
