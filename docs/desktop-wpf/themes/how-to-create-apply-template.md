---
title: 在 WPF 中建立範本-.NET Desktop
description: 瞭解如何在 Windows Presentation Foundation 和 .NET Core 中建立和參考控制項範本。
author: thraka
ms.author: adegeo
ms.date: 11/15/2019
no-loc:
- <Window>
- <ControlTemplate>
- <Ellipse>
- <ContentPresenter>
- <Trigger>
- <Setter>
- <PropertyTrigger>
- <Grid>
- <VisualStateManager.VisualStateGroups>
- <VisualStateGroup>
- <VisualState>
- <Storyboard>
- SizeToContent
- MinWidth
- TargetType
- Title
helpviewer_keywords:
- control contract [WPF]
- controls [WPF], visual structure changes
- ControlTemplate [WPF], customizing for existing controls
- skinning controls [WPF]
- controls [WPF], appearance specified by state
- templates [WPF], custom for existing controls
ms.openlocfilehash: c901864d387b8de976bbfa9a9b3c14a7d5a0b4d8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "82071245"
---
# <a name="create-a-template-for-a-control"></a><span data-ttu-id="0beae-103">建立控制項的範本</span><span class="sxs-lookup"><span data-stu-id="0beae-103">Create a template for a control</span></span>

<span data-ttu-id="0beae-104">使用 Windows Presentation Foundation （WPF），您可以使用自己可重複使用的範本，自訂現有控制項的視覺結構和行為。</span><span class="sxs-lookup"><span data-stu-id="0beae-104">With Windows Presentation Foundation (WPF), you can customize an existing control's visual structure and behavior with your own reusable template.</span></span> <span data-ttu-id="0beae-105">範本可全域套用至您的應用程式、視窗和頁面，或直接套用到控制項。</span><span class="sxs-lookup"><span data-stu-id="0beae-105">Templates can be applied globally to your application, windows and pages, or directly to controls.</span></span> <span data-ttu-id="0beae-106">大部分需要您建立新控制項的案例，可以改為涵蓋現有控制項的新範本。</span><span class="sxs-lookup"><span data-stu-id="0beae-106">Most scenarios that require you to create a new control can be covered by instead creating a new template for an existing control.</span></span>

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

<span data-ttu-id="0beae-107">在本文中，您將探索如何建立<xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button>控制項的新。</span><span class="sxs-lookup"><span data-stu-id="0beae-107">In this article, you'll explore creating a new <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>

## <a name="when-to-create-a-controltemplate"></a><span data-ttu-id="0beae-108">建立 ControlTemplate 的時機</span><span class="sxs-lookup"><span data-stu-id="0beae-108">When to create a ControlTemplate</span></span>

<span data-ttu-id="0beae-109">控制項有許多屬性，例如<xref:System.Windows.Controls.Border.Background%2A>、 <xref:System.Windows.Controls.Control.Foreground%2A>和。 <xref:System.Windows.Controls.Control.FontFamily%2A></span><span class="sxs-lookup"><span data-stu-id="0beae-109">Controls have many properties, such as <xref:System.Windows.Controls.Border.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, and <xref:System.Windows.Controls.Control.FontFamily%2A>.</span></span> <span data-ttu-id="0beae-110">這些屬性會控制控制面板的不同層面，但是您可以藉由設定這些屬性所做的變更會受到限制。</span><span class="sxs-lookup"><span data-stu-id="0beae-110">These properties control different aspects of the control's appearance, but the changes that you can make by setting these properties are limited.</span></span> <span data-ttu-id="0beae-111">例如，您可以將<xref:System.Windows.Controls.Control.Foreground%2A>屬性設定為藍色，並<xref:System.Windows.Controls.Control.FontStyle%2A>將設為斜體<xref:System.Windows.Controls.CheckBox>。</span><span class="sxs-lookup"><span data-stu-id="0beae-111">For example, you can set the <xref:System.Windows.Controls.Control.Foreground%2A> property to blue and <xref:System.Windows.Controls.Control.FontStyle%2A> to italic on a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="0beae-112">當您想要自訂控制項的外觀，而不是控制項的其他屬性設定時，您會建立<xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="0beae-112">When you want to customize the control's appearance beyond what setting the other properties on the control can do, you create a <xref:System.Windows.Controls.ControlTemplate>.</span></span>

<span data-ttu-id="0beae-113">在大部分的使用者介面中，按鈕具有相同的一般外觀：具有一些文字的矩形。</span><span class="sxs-lookup"><span data-stu-id="0beae-113">In most user interfaces, a button has the same general appearance: a rectangle with some text.</span></span> <span data-ttu-id="0beae-114">如果您想要建立圓角按鈕，可以建立一個繼承自按鈕的新控制項，或重建按鈕的功能。</span><span class="sxs-lookup"><span data-stu-id="0beae-114">If you wanted to create a rounded button, you could create a new control that inherits from the button or recreates the functionality of the button.</span></span> <span data-ttu-id="0beae-115">此外，新的使用者控制項也會提供圓形視覺效果。</span><span class="sxs-lookup"><span data-stu-id="0beae-115">In addition, the new user control would provide the circular visual.</span></span>

<span data-ttu-id="0beae-116">您可以藉由自訂現有控制項的視覺化版面配置，來避免建立新的控制項。</span><span class="sxs-lookup"><span data-stu-id="0beae-116">You can avoid creating new controls by customizing the visual layout of an existing control.</span></span> <span data-ttu-id="0beae-117">使用圓角按鈕，您可以<xref:System.Windows.Controls.ControlTemplate>使用所需的視覺效果版面配置來建立。</span><span class="sxs-lookup"><span data-stu-id="0beae-117">With a rounded button, you create a <xref:System.Windows.Controls.ControlTemplate> with the desired visual layout.</span></span>

<span data-ttu-id="0beae-118">另一方面，如果您需要具有新功能、不同屬性和新設定的控制項，則會建立新<xref:System.Windows.Controls.UserControl>的。</span><span class="sxs-lookup"><span data-stu-id="0beae-118">On the other hand, if you need a control with new functionality, different properties, and new settings, you would create a new <xref:System.Windows.Controls.UserControl>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0beae-119">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="0beae-119">Prerequisites</span></span>

<span data-ttu-id="0beae-120">建立新的 WPF 應用程式，並在*mainwindow.xaml*中（或您選擇的另一個視窗），在\*\* \<視窗>\*\* 專案上設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="0beae-120">Create a new WPF application and in *MainWindow.xaml* (or another window of your choice) set the following properties on the **\<Window>** element:</span></span>

|     |     |
| --- | --- |
| **[!OP.NO-LOC(Title)]**         | `Template Intro Sample` |
| **[!OP.NO-LOC(SizeToContent)]** | `WidthAndHeight` |
| **[!OP.NO-LOC(MinWidth)]**      | `250` |

<span data-ttu-id="0beae-121">將\*\* \<Window>\*\* 元素的內容設定為下列 XAML：</span><span class="sxs-lookup"><span data-stu-id="0beae-121">Set the content of the **\<Window>** element to the following XAML:</span></span>

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

<span data-ttu-id="0beae-122">最後， *mainwindow.xaml*應該看起來像下面這樣：</span><span class="sxs-lookup"><span data-stu-id="0beae-122">In the end, the *MainWindow.xaml* file should look similar to the following:</span></span>

[!code-xaml[InitialWhole](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#InitialWhole)]

<span data-ttu-id="0beae-123">如果您執行應用程式，它看起來會像下面這樣：</span><span class="sxs-lookup"><span data-stu-id="0beae-123">If you run the application, it looks like the following:</span></span>

![具有兩個 .unstyled-list 按鈕的 WPF 視窗](media/create-apply-template/unstyled-button.png)

## <a name="create-a-controltemplate"></a><span data-ttu-id="0beae-125">建立 ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="0beae-125">Create a ControlTemplate</span></span>

<span data-ttu-id="0beae-126">宣告的最常見方式<xref:System.Windows.Controls.ControlTemplate>就是 XAML 檔案中`Resources`區段的資源。</span><span class="sxs-lookup"><span data-stu-id="0beae-126">The most common way to declare a <xref:System.Windows.Controls.ControlTemplate> is as a resource in the `Resources` section in a XAML file.</span></span> <span data-ttu-id="0beae-127">因為範本是資源，所以它們會遵守適用于所有資源的相同範圍規則。</span><span class="sxs-lookup"><span data-stu-id="0beae-127">Because templates are resources, they obey the same scoping rules that apply to all resources.</span></span> <span data-ttu-id="0beae-128">簡單地說，您可以在其中宣告範本會影響可套用範本的位置。</span><span class="sxs-lookup"><span data-stu-id="0beae-128">Put simply, where you declare a template affects where the template can be applied.</span></span> <span data-ttu-id="0beae-129">例如，如果您在應用程式定義 XAML 檔案的根項目中宣告範本，則範本可以在應用程式的任何位置使用。</span><span class="sxs-lookup"><span data-stu-id="0beae-129">For example, if you declare the template in the root element of your application definition XAML file, the template can be used anywhere in your application.</span></span> <span data-ttu-id="0beae-130">如果您在視窗中定義範本，則只有該視窗中的控制項可以使用此範本。</span><span class="sxs-lookup"><span data-stu-id="0beae-130">If you define the template in a window, only the controls in that window can use the template.</span></span>

<span data-ttu-id="0beae-131">若要開始，請將`Window.Resources`元素新增至您的*mainwindow.xaml*檔案：</span><span class="sxs-lookup"><span data-stu-id="0beae-131">To start with, add a `Window.Resources` element to your *MainWindow.xaml* file:</span></span>

[!code-xaml[WindowResStart](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window2.xaml#WindowResStart)]

<span data-ttu-id="0beae-132">使用設定下列屬性來建立新\*\* \<的 ControlTemplate>\*\* ：</span><span class="sxs-lookup"><span data-stu-id="0beae-132">Create a new **\<ControlTemplate>** with the following properties set:</span></span>

|     |     |
| --- | --- |
| <span data-ttu-id="0beae-133">**x:Key**</span><span class="sxs-lookup"><span data-stu-id="0beae-133">**x:Key**</span></span>         | `roundbutton` |
| **TargetType**    | `Button` |

<span data-ttu-id="0beae-134">這個控制項範本很簡單：</span><span class="sxs-lookup"><span data-stu-id="0beae-134">This control template will be simple:</span></span>

- <span data-ttu-id="0beae-135">控制項的根項目，a<xref:System.Windows.Controls.Grid></span><span class="sxs-lookup"><span data-stu-id="0beae-135">a root element for the control, a <xref:System.Windows.Controls.Grid></span></span>
- <span data-ttu-id="0beae-136"><xref:System.Windows.Shapes.Ellipse> ，用來繪製按鈕的圓角外觀</span><span class="sxs-lookup"><span data-stu-id="0beae-136">an <xref:System.Windows.Shapes.Ellipse> to draw the rounded appearance of the button</span></span>
- <span data-ttu-id="0beae-137">， <xref:System.Windows.Controls.ContentPresenter>用來顯示使用者指定的按鈕內容</span><span class="sxs-lookup"><span data-stu-id="0beae-137">a <xref:System.Windows.Controls.ContentPresenter> to display the user-specified button content</span></span>

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#ControlTemplate)]

### <a name="templatebinding"></a><span data-ttu-id="0beae-138">TemplateBinding</span><span class="sxs-lookup"><span data-stu-id="0beae-138">TemplateBinding</span></span>

<span data-ttu-id="0beae-139">當您建立新<xref:System.Windows.Controls.ControlTemplate>的時，您仍可能想要使用公用屬性來變更控制項的外觀。</span><span class="sxs-lookup"><span data-stu-id="0beae-139">When you create a new <xref:System.Windows.Controls.ControlTemplate>, you still might want to use the public properties to change the control's appearance.</span></span> <span data-ttu-id="0beae-140">[TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md)標記延伸會將位於的<xref:System.Windows.Controls.ControlTemplate>專案屬性系結至控制項所定義的公用屬性。</span><span class="sxs-lookup"><span data-stu-id="0beae-140">The [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) markup extension binds a property of an element that is in the <xref:System.Windows.Controls.ControlTemplate> to a public property that is defined by the control.</span></span> <span data-ttu-id="0beae-141">當您使用[TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md)時，您會啟用控制項的屬性，作為範本的參數。</span><span class="sxs-lookup"><span data-stu-id="0beae-141">When you use a [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md), you enable properties on the control to act as parameters to the template.</span></span> <span data-ttu-id="0beae-142">也就是說，已設定控制項上的屬性時，該值會傳遞給具有 [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) 的元素。</span><span class="sxs-lookup"><span data-stu-id="0beae-142">That is, when a property on a control is set, that value is passed on to the element that has the [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) on it.</span></span>

### <a name="ellipse"></a><span data-ttu-id="0beae-143">橢圓形</span><span class="sxs-lookup"><span data-stu-id="0beae-143">Ellipse</span></span>

<span data-ttu-id="0beae-144">請注意， **:::no-loc text="Fill":::** **:::no-loc text="Stroke":::** \*\* \<橢圓形>\*\* 元素的和屬性會系結至控制項的<xref:System.Windows.Controls.Control.Foreground>和<xref:System.Windows.Controls.Control.Background>屬性。</span><span class="sxs-lookup"><span data-stu-id="0beae-144">Notice that the **:::no-loc text="Fill":::** and **:::no-loc text="Stroke":::** properties of the **\<Ellipse>** element are bound to the control's <xref:System.Windows.Controls.Control.Foreground> and <xref:System.Windows.Controls.Control.Background> properties.</span></span>

### <a name="contentpresenter"></a><span data-ttu-id="0beae-145">ContentPresenter</span><span class="sxs-lookup"><span data-stu-id="0beae-145">ContentPresenter</span></span>

<span data-ttu-id="0beae-146">ContentPresenter>元素也會加入至範本。 [ \< ](xref:System.Windows.Controls.ContentPresenter)</span><span class="sxs-lookup"><span data-stu-id="0beae-146">A [\<ContentPresenter>](xref:System.Windows.Controls.ContentPresenter) element is also added to the template.</span></span> <span data-ttu-id="0beae-147">由於此範本是針對按鈕而設計的，因此請考慮按鈕會繼承自<xref:System.Windows.Controls.ContentControl>。</span><span class="sxs-lookup"><span data-stu-id="0beae-147">Because this template is designed for a button, take into consideration that the button inherits from <xref:System.Windows.Controls.ContentControl>.</span></span> <span data-ttu-id="0beae-148">按鈕會顯示元素的內容。</span><span class="sxs-lookup"><span data-stu-id="0beae-148">The button presents the content of the element.</span></span> <span data-ttu-id="0beae-149">您可以在按鈕內設定任何專案，例如純文字或甚至另一個控制項。</span><span class="sxs-lookup"><span data-stu-id="0beae-149">You can set anything inside of the button, such as plain text or even another control.</span></span> <span data-ttu-id="0beae-150">下列這兩個都是有效的按鈕：</span><span class="sxs-lookup"><span data-stu-id="0beae-150">Both of the following are valid buttons:</span></span>

```xaml
<Button>My Text</Button>

<!-- and -->

<Button>
    <CheckBox>Checkbox in a button</CheckBox>
</Button>
```

<span data-ttu-id="0beae-151">在上述兩個範例中，文字和核取方塊都會設定為 [ [Content](xref:System.Windows.Controls.ContentControl.Content) ] 屬性。</span><span class="sxs-lookup"><span data-stu-id="0beae-151">In both of the previous examples, the text and the checkbox are set as the [Button.Content](xref:System.Windows.Controls.ContentControl.Content) property.</span></span> <span data-ttu-id="0beae-152">無論內容設定為何，都可以透過\*\* \<ContentPresenter>\*\* 來呈現，這就是範本的用途。</span><span class="sxs-lookup"><span data-stu-id="0beae-152">Whatever is set as the content can be presented through a **\<ContentPresenter>**, which is what the template does.</span></span>

<span data-ttu-id="0beae-153"><xref:System.Windows.Controls.ControlTemplate>如果套用至<xref:System.Windows.Controls.ContentControl>型別（例如`Button`）， <xref:System.Windows.Controls.ContentPresenter>則會在專案樹狀結構中搜尋。</span><span class="sxs-lookup"><span data-stu-id="0beae-153">If the <xref:System.Windows.Controls.ControlTemplate> is applied to a <xref:System.Windows.Controls.ContentControl> type, such as a `Button`, a <xref:System.Windows.Controls.ContentPresenter> is searched for in the element tree.</span></span> <span data-ttu-id="0beae-154">`ContentPresenter`如果找到，此範本會自動將控制項的<xref:System.Windows.Controls.ContentControl.Content>屬性系結至`ContentPresenter`。</span><span class="sxs-lookup"><span data-stu-id="0beae-154">If the `ContentPresenter` is found, the template automatically binds the control's <xref:System.Windows.Controls.ContentControl.Content> property to the `ContentPresenter`.</span></span>

## <a name="use-the-template"></a><span data-ttu-id="0beae-155">使用範本</span><span class="sxs-lookup"><span data-stu-id="0beae-155">Use the template</span></span>

<span data-ttu-id="0beae-156">尋找在本文開頭所宣告的按鈕。</span><span class="sxs-lookup"><span data-stu-id="0beae-156">Find the buttons that were declared at the start of this article.</span></span>

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

<span data-ttu-id="0beae-157">將第二個按鈕<xref:System.Windows.Controls.Control.Template>的屬性設定`roundbutton`為資源：</span><span class="sxs-lookup"><span data-stu-id="0beae-157">Set the second button's <xref:System.Windows.Controls.Control.Template> property to the `roundbutton` resource:</span></span>

[!code-xaml[StyledButton](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButton)]

<span data-ttu-id="0beae-158">如果您執行專案並查看結果，您會看到按鈕具有圓角背景。</span><span class="sxs-lookup"><span data-stu-id="0beae-158">If you run the project and look at the result, you'll see that the button has a rounded background.</span></span>

![具有一個樣板橢圓形按鈕的 WPF 視窗](media/create-apply-template/styled-button.png)

<span data-ttu-id="0beae-160">您可能已經注意到按鈕不是圓形，而是扭曲。</span><span class="sxs-lookup"><span data-stu-id="0beae-160">You may have noticed that the button isn't a circle but is skewed.</span></span> <span data-ttu-id="0beae-161">由於\*\* \<橢圓形>\*\* 元素的運作方式，它一律會展開以填滿可用的空間。</span><span class="sxs-lookup"><span data-stu-id="0beae-161">Because of the way the **\<Ellipse>** element works, it always expands to fill the available space.</span></span> <span data-ttu-id="0beae-162">將按鈕的**:::no-loc text="width":::** 和**:::no-loc text="height":::** 屬性變更為相同的值，使圓形成為一致：</span><span class="sxs-lookup"><span data-stu-id="0beae-162">Make the circle uniform by changing the button's  **:::no-loc text="width":::** and **:::no-loc text="height":::** properties to the same value:</span></span>

[!code-xaml[StyledButtonSize](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButtonSize)]

![具有一個範本迴圈按鈕的 WPF 視窗](media/create-apply-template/styled-uniform-button.png)

## <a name="add-a-trigger"></a><span data-ttu-id="0beae-164">新增觸發程式</span><span class="sxs-lookup"><span data-stu-id="0beae-164">Add a Trigger</span></span>

<span data-ttu-id="0beae-165">雖然套用範本的按鈕看起來不同，但其行為與任何其他按鈕相同。</span><span class="sxs-lookup"><span data-stu-id="0beae-165">Even though a button with a template applied looks different, it behaves the same as any other button.</span></span> <span data-ttu-id="0beae-166">如果您按下按鈕，就<xref:System.Windows.Controls.Primitives.ButtonBase.Click>會引發事件。</span><span class="sxs-lookup"><span data-stu-id="0beae-166">If you press the button, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event fires.</span></span> <span data-ttu-id="0beae-167">不過，您可能已經注意到，當您將滑鼠移至按鈕上方時，按鈕的視覺效果不會變更。</span><span class="sxs-lookup"><span data-stu-id="0beae-167">However, you may have noticed that when you move your mouse over the button, the button's visuals don't change.</span></span> <span data-ttu-id="0beae-168">這些視覺效果的互動都是由範本定義。</span><span class="sxs-lookup"><span data-stu-id="0beae-168">These visual interactions are all defined by the template.</span></span>

<span data-ttu-id="0beae-169">透過 WPF 提供的動態事件和屬性系統，您可以監看特定屬性的值，然後在適當時重新建立範本的樣式。</span><span class="sxs-lookup"><span data-stu-id="0beae-169">With the dynamic event and property systems that WPF provides, you can watch a specific property for a value and then restyle the template when appropriate.</span></span> <span data-ttu-id="0beae-170">在此範例中，您會看到按鈕的<xref:System.Windows.UIElement.IsMouseOver>屬性。</span><span class="sxs-lookup"><span data-stu-id="0beae-170">In this example, you'll watch the button's <xref:System.Windows.UIElement.IsMouseOver> property.</span></span> <span data-ttu-id="0beae-171">當滑鼠停留在控制項上時，使用新的色彩將\*\* \<橢圓形>\*\* 樣式。</span><span class="sxs-lookup"><span data-stu-id="0beae-171">When the mouse is over the control, style the **\<Ellipse>** with a new color.</span></span> <span data-ttu-id="0beae-172">這種類型的觸發程式稱為*PropertyTrigger*。</span><span class="sxs-lookup"><span data-stu-id="0beae-172">This type of trigger is known as a *PropertyTrigger*.</span></span>

<span data-ttu-id="0beae-173">若要這樣做，您必須將名稱新增至您可以參考的\*\* \<省略號>\*\* 。</span><span class="sxs-lookup"><span data-stu-id="0beae-173">For this to work, you'll need to add a name to the **\<Ellipse>** that you can reference.</span></span> <span data-ttu-id="0beae-174">為它命名為**backgroundElement**。</span><span class="sxs-lookup"><span data-stu-id="0beae-174">Give it the name of **backgroundElement**.</span></span>

[!code-xaml[EllipseName](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml#EllipseName)]

<span data-ttu-id="0beae-175">接下來，將新<xref:System.Windows.Trigger>的新增至[ControlTemplate](xref:System.Windows.Controls.ControlTemplate.Triggers)集合。</span><span class="sxs-lookup"><span data-stu-id="0beae-175">Next, add a new <xref:System.Windows.Trigger> to the [ControlTemplate.Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) collection.</span></span> <span data-ttu-id="0beae-176">觸發程式將會監`IsMouseOver`看此值`true`的事件。</span><span class="sxs-lookup"><span data-stu-id="0beae-176">The trigger will watch the `IsMouseOver` event for the value `true`.</span></span>

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml?name=ControlTemplate&highlight=6-10)]

<span data-ttu-id="0beae-177">接下來，將\*\* \<Setter>\*\* 新增至\*\* \<觸發程式>\*\* ，將\*\* \<橢圓形>\*\* 的**Fill**屬性變更為新的色彩。</span><span class="sxs-lookup"><span data-stu-id="0beae-177">Next, add a **\<Setter>** to the **\<Trigger>** that changes the **Fill** property of the **\<Ellipse>** to a new color.</span></span>

[!code-xaml[MouseOver](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#MouseOver)]

<span data-ttu-id="0beae-178">執行專案。</span><span class="sxs-lookup"><span data-stu-id="0beae-178">Run the project.</span></span> <span data-ttu-id="0beae-179">請注意，當您將滑鼠指標移至按鈕上方時， \*\* \<橢圓形\*\*的色彩>變更。</span><span class="sxs-lookup"><span data-stu-id="0beae-179">Notice that when you move the mouse over the button, the color of the **\<Ellipse>** changes.</span></span>

![滑鼠移至 WPF 按鈕以變更填滿色彩](media/create-apply-template/mouse-move-over-button.gif)

## <a name="use-a-visualstate"></a><span data-ttu-id="0beae-181">使用 VisualState</span><span class="sxs-lookup"><span data-stu-id="0beae-181">Use a VisualState</span></span>

<span data-ttu-id="0beae-182">視覺狀態是由控制項所定義和觸發。</span><span class="sxs-lookup"><span data-stu-id="0beae-182">Visual states are defined and triggered by a control.</span></span> <span data-ttu-id="0beae-183">例如，當滑鼠移到控制項上方時，就會觸發`CommonStates.MouseOver`狀態。</span><span class="sxs-lookup"><span data-stu-id="0beae-183">For example, when the mouse is moved on top of the control, the `CommonStates.MouseOver` state is triggered.</span></span> <span data-ttu-id="0beae-184">您可以根據控制項的目前狀態來建立屬性變更的動畫。</span><span class="sxs-lookup"><span data-stu-id="0beae-184">You can animate property changes based on the current state of the control.</span></span> <span data-ttu-id="0beae-185">在上一節中， \*\* \<PropertyTrigger>\*\* 是用來在`IsMouseOver`屬性為時，將按鈕`AliceBlue`的前景變更為`true`。</span><span class="sxs-lookup"><span data-stu-id="0beae-185">In the previous section, a **\<PropertyTrigger>** was used to change the foreground of the button to `AliceBlue` when the `IsMouseOver` property was `true`.</span></span> <span data-ttu-id="0beae-186">而是建立視覺狀態，以動畫顯示此色彩的變更，並提供順暢的轉換。</span><span class="sxs-lookup"><span data-stu-id="0beae-186">Instead, create a visual state that animates the change of this color, providing a smooth transition.</span></span> <span data-ttu-id="0beae-187">如需*VisualStates*的詳細資訊，請參閱[WPF 中的樣式和範本](../fundamentals/styles-templates-overview.md#visual-states)。</span><span class="sxs-lookup"><span data-stu-id="0beae-187">For more information about *VisualStates*, see [Styles and templates in WPF](../fundamentals/styles-templates-overview.md#visual-states).</span></span>

<span data-ttu-id="0beae-188">若要將\*\* \<PropertyTrigger>\*\* 轉換成動畫視覺狀態，請先從您的範本中移除\*\* \<ControlTemplate 元素>\*\* 專案。</span><span class="sxs-lookup"><span data-stu-id="0beae-188">To convert the **\<PropertyTrigger>** to an animated visual state, First, remove the **\<ControlTemplate.Triggers>** element from your template.</span></span>

[!code-xaml[CleanTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#CleanTemplate)]

<span data-ttu-id="0beae-189">接下來，在控制項範本的\*\* \<>根方格**中，加入** \<system.windows.visualstatemanager.visualstategroups>\*\* 元素，以及的\*\* \<VisualStateGroup>。\*\* `CommonStates`</span><span class="sxs-lookup"><span data-stu-id="0beae-189">Next, in the **\<Grid>** root of the control template, add the **\<VisualStateManager.VisualStateGroups>** element with a **\<VisualStateGroup>** for `CommonStates`.</span></span> <span data-ttu-id="0beae-190">定義兩個狀態`Normal` ： `MouseOver`和。</span><span class="sxs-lookup"><span data-stu-id="0beae-190">Define two states, `Normal` and `MouseOver`.</span></span>

[!code-xaml[VisualState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#VisualState)]

<span data-ttu-id="0beae-191">當觸發該狀態時，會套用\*\* \<VisualState>\*\* 中所定義的任何動畫。</span><span class="sxs-lookup"><span data-stu-id="0beae-191">Any animations defined in a **\<VisualState>** are applied when that state is triggered.</span></span> <span data-ttu-id="0beae-192">建立每個狀態的動畫。</span><span class="sxs-lookup"><span data-stu-id="0beae-192">Create animations for each state.</span></span> <span data-ttu-id="0beae-193">動畫會放在分\*\* \<\*\* 鏡腳本>元素的內部。</span><span class="sxs-lookup"><span data-stu-id="0beae-193">Animations are put inside of a **\<Storyboard>** element.</span></span> <span data-ttu-id="0beae-194">如需有關分鏡腳本的詳細資訊，請參閱分鏡腳本[總覽](../../framework/wpf/graphics-multimedia/storyboards-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="0beae-194">For more information about storyboards, see [Storyboards Overview](../../framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span>

- <span data-ttu-id="0beae-195">正常</span><span class="sxs-lookup"><span data-stu-id="0beae-195">Normal</span></span>

  <span data-ttu-id="0beae-196">此狀態會將橢圓形填滿動畫，並將其還原`Background`為控制項的色彩。</span><span class="sxs-lookup"><span data-stu-id="0beae-196">This state animates the ellipse fill, restoring it to the control's `Background` color.</span></span>

  [!code-xaml[NormalState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#NormalState)]

- <span data-ttu-id="0beae-197">MouseOver</span><span class="sxs-lookup"><span data-stu-id="0beae-197">MouseOver</span></span>

  <span data-ttu-id="0beae-198">此狀態會以動畫`Background`將橢圓形色彩繪製到新`Yellow`的色彩：。</span><span class="sxs-lookup"><span data-stu-id="0beae-198">This state animates the ellipse `Background` color to a new color: `Yellow`.</span></span>

  [!code-xaml[MouseOverState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#MouseOverState)]

<span data-ttu-id="0beae-199">ControlTemplate>現在看起來應該如下所示。 \*\* \< \*\*</span><span class="sxs-lookup"><span data-stu-id="0beae-199">The **\<ControlTemplate>** should now look like the following.</span></span>

[!code-xaml[FinalTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window7.xaml#FinalTemplate)]

<span data-ttu-id="0beae-200">執行專案。</span><span class="sxs-lookup"><span data-stu-id="0beae-200">Run the project.</span></span> <span data-ttu-id="0beae-201">請注意，當您將滑鼠游標移至按鈕上方時， \*\* \<橢圓形>\*\* 的色彩會以動畫呈現。</span><span class="sxs-lookup"><span data-stu-id="0beae-201">Notice that when you move the mouse over the button, the color of the **\<Ellipse>** animates.</span></span>

![滑鼠移至 WPF 按鈕以變更填滿色彩](media/create-apply-template/mouse-move-over-button-visualstate.gif)

## <a name="next-steps"></a><span data-ttu-id="0beae-203">後續步驟</span><span class="sxs-lookup"><span data-stu-id="0beae-203">Next steps</span></span>

- [<span data-ttu-id="0beae-204">在 WPF 中建立控制項的樣式</span><span class="sxs-lookup"><span data-stu-id="0beae-204">Create a style for a control in WPF</span></span>](../fundamentals/styles-templates-create-apply-style.md)
- [<span data-ttu-id="0beae-205">WPF 中的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="0beae-205">Styles and templates in WPF</span></span>](../fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="0beae-206">XAML 資源的總覽</span><span class="sxs-lookup"><span data-stu-id="0beae-206">Overview of XAML Resources</span></span>](../fundamentals/xaml-resources-define.md)
