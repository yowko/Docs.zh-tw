---
title: 在 WPF 中建立範本-.NET Desktop
description: 瞭解如何在 Windows Presentation Foundation 和 .NET Core 中建立和參考控制項範本。
author: adegeo
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
ms.openlocfilehash: c372659676b450cde789c96e45c7ec5de2aea194
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325729"
---
# <a name="create-a-template-for-a-control"></a><span data-ttu-id="66224-103">建立控制項的範本</span><span class="sxs-lookup"><span data-stu-id="66224-103">Create a template for a control</span></span>

<span data-ttu-id="66224-104">使用 Windows Presentation Foundation （WPF），您可以使用自己可重複使用的範本，自訂現有控制項的視覺結構和行為。</span><span class="sxs-lookup"><span data-stu-id="66224-104">With Windows Presentation Foundation (WPF), you can customize an existing control's visual structure and behavior with your own reusable template.</span></span> <span data-ttu-id="66224-105">範本可全域套用至您的應用程式、視窗和頁面，或直接套用到控制項。</span><span class="sxs-lookup"><span data-stu-id="66224-105">Templates can be applied globally to your application, windows and pages, or directly to controls.</span></span> <span data-ttu-id="66224-106">大部分需要您建立新控制項的案例，可以改為涵蓋現有控制項的新範本。</span><span class="sxs-lookup"><span data-stu-id="66224-106">Most scenarios that require you to create a new control can be covered by instead creating a new template for an existing control.</span></span>

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

<span data-ttu-id="66224-107">在本文中，您將探索如何建立 <xref:System.Windows.Controls.ControlTemplate> 控制項的新 <xref:System.Windows.Controls.Button> 。</span><span class="sxs-lookup"><span data-stu-id="66224-107">In this article, you'll explore creating a new <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>

## <a name="when-to-create-a-controltemplate"></a><span data-ttu-id="66224-108">建立 ControlTemplate 的時機</span><span class="sxs-lookup"><span data-stu-id="66224-108">When to create a ControlTemplate</span></span>

<span data-ttu-id="66224-109">控制項有許多屬性，例如 <xref:System.Windows.Controls.Border.Background%2A> 、 <xref:System.Windows.Controls.Control.Foreground%2A> 和 <xref:System.Windows.Controls.Control.FontFamily%2A> 。</span><span class="sxs-lookup"><span data-stu-id="66224-109">Controls have many properties, such as <xref:System.Windows.Controls.Border.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, and <xref:System.Windows.Controls.Control.FontFamily%2A>.</span></span> <span data-ttu-id="66224-110">這些屬性會控制控制面板的不同層面，但是您可以藉由設定這些屬性所做的變更會受到限制。</span><span class="sxs-lookup"><span data-stu-id="66224-110">These properties control different aspects of the control's appearance, but the changes that you can make by setting these properties are limited.</span></span> <span data-ttu-id="66224-111">例如，您可以將屬性設定 <xref:System.Windows.Controls.Control.Foreground%2A> 為藍色，並將設 <xref:System.Windows.Controls.Control.FontStyle%2A> 為斜體 <xref:System.Windows.Controls.CheckBox> 。</span><span class="sxs-lookup"><span data-stu-id="66224-111">For example, you can set the <xref:System.Windows.Controls.Control.Foreground%2A> property to blue and <xref:System.Windows.Controls.Control.FontStyle%2A> to italic on a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="66224-112">當您想要自訂控制項的外觀，而不是控制項的其他屬性設定時，您會建立 <xref:System.Windows.Controls.ControlTemplate> 。</span><span class="sxs-lookup"><span data-stu-id="66224-112">When you want to customize the control's appearance beyond what setting the other properties on the control can do, you create a <xref:System.Windows.Controls.ControlTemplate>.</span></span>

<span data-ttu-id="66224-113">在大部分的使用者介面中，按鈕具有相同的一般外觀：具有一些文字的矩形。</span><span class="sxs-lookup"><span data-stu-id="66224-113">In most user interfaces, a button has the same general appearance: a rectangle with some text.</span></span> <span data-ttu-id="66224-114">如果您想要建立圓角按鈕，可以建立一個繼承自按鈕的新控制項，或重建按鈕的功能。</span><span class="sxs-lookup"><span data-stu-id="66224-114">If you wanted to create a rounded button, you could create a new control that inherits from the button or recreates the functionality of the button.</span></span> <span data-ttu-id="66224-115">此外，新的使用者控制項也會提供圓形視覺效果。</span><span class="sxs-lookup"><span data-stu-id="66224-115">In addition, the new user control would provide the circular visual.</span></span>

<span data-ttu-id="66224-116">您可以藉由自訂現有控制項的視覺化版面配置，來避免建立新的控制項。</span><span class="sxs-lookup"><span data-stu-id="66224-116">You can avoid creating new controls by customizing the visual layout of an existing control.</span></span> <span data-ttu-id="66224-117">使用圓角按鈕，您可以 <xref:System.Windows.Controls.ControlTemplate> 使用所需的視覺效果版面配置來建立。</span><span class="sxs-lookup"><span data-stu-id="66224-117">With a rounded button, you create a <xref:System.Windows.Controls.ControlTemplate> with the desired visual layout.</span></span>

<span data-ttu-id="66224-118">另一方面，如果您需要具有新功能、不同屬性和新設定的控制項，則會建立新的 <xref:System.Windows.Controls.UserControl> 。</span><span class="sxs-lookup"><span data-stu-id="66224-118">On the other hand, if you need a control with new functionality, different properties, and new settings, you would create a new <xref:System.Windows.Controls.UserControl>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="66224-119">先決條件</span><span class="sxs-lookup"><span data-stu-id="66224-119">Prerequisites</span></span>

<span data-ttu-id="66224-120">建立新的 WPF 應用程式，並在*mainwindow.xaml* （或您選擇的另一個視窗）中，設定元素的下列屬性 **\<Window>** ：</span><span class="sxs-lookup"><span data-stu-id="66224-120">Create a new WPF application and in *MainWindow.xaml* (or another window of your choice) set the following properties on the **\<Window>** element:</span></span>

|     |     |
| --- | --- |
| **Title**         | `Template Intro Sample` |
| **SizeToContent** | `WidthAndHeight` |
| **MinWidth**      | `250` |

<span data-ttu-id="66224-121">將元素的內容設定 **\<Window>** 為下列 XAML：</span><span class="sxs-lookup"><span data-stu-id="66224-121">Set the content of the **\<Window>** element to the following XAML:</span></span>

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

<span data-ttu-id="66224-122">最後， *mainwindow.xaml*應該看起來像下面這樣：</span><span class="sxs-lookup"><span data-stu-id="66224-122">In the end, the *MainWindow.xaml* file should look similar to the following:</span></span>

[!code-xaml[InitialWhole](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#InitialWhole)]

<span data-ttu-id="66224-123">如果您執行應用程式，它看起來會像下面這樣：</span><span class="sxs-lookup"><span data-stu-id="66224-123">If you run the application, it looks like the following:</span></span>

![具有兩個 .unstyled-list 按鈕的 WPF 視窗](media/create-apply-template/unstyled-button.png)

## <a name="create-a-controltemplate"></a><span data-ttu-id="66224-125">建立 ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="66224-125">Create a ControlTemplate</span></span>

<span data-ttu-id="66224-126">宣告的最常見方式 <xref:System.Windows.Controls.ControlTemplate> 就是 XAML 檔案中區段的資源 `Resources` 。</span><span class="sxs-lookup"><span data-stu-id="66224-126">The most common way to declare a <xref:System.Windows.Controls.ControlTemplate> is as a resource in the `Resources` section in a XAML file.</span></span> <span data-ttu-id="66224-127">因為範本是資源，所以它們會遵守適用于所有資源的相同範圍規則。</span><span class="sxs-lookup"><span data-stu-id="66224-127">Because templates are resources, they obey the same scoping rules that apply to all resources.</span></span> <span data-ttu-id="66224-128">簡單地說，您可以在其中宣告範本會影響可套用範本的位置。</span><span class="sxs-lookup"><span data-stu-id="66224-128">Put simply, where you declare a template affects where the template can be applied.</span></span> <span data-ttu-id="66224-129">例如，如果您在應用程式定義 XAML 檔案的根項目中宣告範本，則範本可以在應用程式的任何位置使用。</span><span class="sxs-lookup"><span data-stu-id="66224-129">For example, if you declare the template in the root element of your application definition XAML file, the template can be used anywhere in your application.</span></span> <span data-ttu-id="66224-130">如果您在視窗中定義範本，則只有該視窗中的控制項可以使用此範本。</span><span class="sxs-lookup"><span data-stu-id="66224-130">If you define the template in a window, only the controls in that window can use the template.</span></span>

<span data-ttu-id="66224-131">若要開始，請將 `Window.Resources` 元素新增至您的*mainwindow.xaml*檔案：</span><span class="sxs-lookup"><span data-stu-id="66224-131">To start with, add a `Window.Resources` element to your *MainWindow.xaml* file:</span></span>

[!code-xaml[WindowResStart](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window2.xaml#WindowResStart)]

<span data-ttu-id="66224-132">建立 **\<ControlTemplate>** 具有下列屬性集的新：</span><span class="sxs-lookup"><span data-stu-id="66224-132">Create a new **\<ControlTemplate>** with the following properties set:</span></span>

|     |     |
| --- | --- |
| <span data-ttu-id="66224-133">**x:Key**</span><span class="sxs-lookup"><span data-stu-id="66224-133">**x:Key**</span></span>         | `roundbutton` |
| **TargetType**    | `Button` |

<span data-ttu-id="66224-134">這個控制項範本很簡單：</span><span class="sxs-lookup"><span data-stu-id="66224-134">This control template will be simple:</span></span>

- <span data-ttu-id="66224-135">控制項的根項目，a<xref:System.Windows.Controls.Grid></span><span class="sxs-lookup"><span data-stu-id="66224-135">a root element for the control, a <xref:System.Windows.Controls.Grid></span></span>
- <span data-ttu-id="66224-136"><xref:System.Windows.Shapes.Ellipse>，用來繪製按鈕的圓角外觀</span><span class="sxs-lookup"><span data-stu-id="66224-136">an <xref:System.Windows.Shapes.Ellipse> to draw the rounded appearance of the button</span></span>
- <span data-ttu-id="66224-137"><xref:System.Windows.Controls.ContentPresenter>，用來顯示使用者指定的按鈕內容</span><span class="sxs-lookup"><span data-stu-id="66224-137">a <xref:System.Windows.Controls.ContentPresenter> to display the user-specified button content</span></span>

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#ControlTemplate)]

### <a name="templatebinding"></a><span data-ttu-id="66224-138">TemplateBinding</span><span class="sxs-lookup"><span data-stu-id="66224-138">TemplateBinding</span></span>

<span data-ttu-id="66224-139">當您建立新的時 <xref:System.Windows.Controls.ControlTemplate> ，您仍可能想要使用公用屬性來變更控制項的外觀。</span><span class="sxs-lookup"><span data-stu-id="66224-139">When you create a new <xref:System.Windows.Controls.ControlTemplate>, you still might want to use the public properties to change the control's appearance.</span></span> <span data-ttu-id="66224-140">[TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md)標記延伸會將位於的專案屬性系結 <xref:System.Windows.Controls.ControlTemplate> 至控制項所定義的公用屬性。</span><span class="sxs-lookup"><span data-stu-id="66224-140">The [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) markup extension binds a property of an element that is in the <xref:System.Windows.Controls.ControlTemplate> to a public property that is defined by the control.</span></span> <span data-ttu-id="66224-141">當您使用[TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md)時，您會啟用控制項的屬性，作為範本的參數。</span><span class="sxs-lookup"><span data-stu-id="66224-141">When you use a [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md), you enable properties on the control to act as parameters to the template.</span></span> <span data-ttu-id="66224-142">也就是說，已設定控制項上的屬性時，該值會傳遞給具有 [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) 的元素。</span><span class="sxs-lookup"><span data-stu-id="66224-142">That is, when a property on a control is set, that value is passed on to the element that has the [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) on it.</span></span>

### <a name="ellipse"></a><span data-ttu-id="66224-143">橢圓形</span><span class="sxs-lookup"><span data-stu-id="66224-143">Ellipse</span></span>

<span data-ttu-id="66224-144">請注意， **:::no-loc text="Fill":::** 元素的和 **:::no-loc text="Stroke":::** 屬性會系結 **\<Ellipse>** 至控制項的 <xref:System.Windows.Controls.Control.Foreground> 和 <xref:System.Windows.Controls.Control.Background> 屬性。</span><span class="sxs-lookup"><span data-stu-id="66224-144">Notice that the **:::no-loc text="Fill":::** and **:::no-loc text="Stroke":::** properties of the **\<Ellipse>** element are bound to the control's <xref:System.Windows.Controls.Control.Foreground> and <xref:System.Windows.Controls.Control.Background> properties.</span></span>

### <a name="contentpresenter"></a><span data-ttu-id="66224-145">ContentPresenter</span><span class="sxs-lookup"><span data-stu-id="66224-145">ContentPresenter</span></span>

<span data-ttu-id="66224-146">[\<ContentPresenter>](xref:System.Windows.Controls.ContentPresenter)元素也會加入至範本。</span><span class="sxs-lookup"><span data-stu-id="66224-146">A [\<ContentPresenter>](xref:System.Windows.Controls.ContentPresenter) element is also added to the template.</span></span> <span data-ttu-id="66224-147">由於此範本是針對按鈕而設計的，因此請考慮按鈕會繼承自 <xref:System.Windows.Controls.ContentControl> 。</span><span class="sxs-lookup"><span data-stu-id="66224-147">Because this template is designed for a button, take into consideration that the button inherits from <xref:System.Windows.Controls.ContentControl>.</span></span> <span data-ttu-id="66224-148">按鈕會顯示元素的內容。</span><span class="sxs-lookup"><span data-stu-id="66224-148">The button presents the content of the element.</span></span> <span data-ttu-id="66224-149">您可以在按鈕內設定任何專案，例如純文字或甚至另一個控制項。</span><span class="sxs-lookup"><span data-stu-id="66224-149">You can set anything inside of the button, such as plain text or even another control.</span></span> <span data-ttu-id="66224-150">下列這兩個都是有效的按鈕：</span><span class="sxs-lookup"><span data-stu-id="66224-150">Both of the following are valid buttons:</span></span>

```xaml
<Button>My Text</Button>

<!-- and -->

<Button>
    <CheckBox>Checkbox in a button</CheckBox>
</Button>
```

<span data-ttu-id="66224-151">在上述兩個範例中，文字和核取方塊都會設定為 [ [Content](xref:System.Windows.Controls.ContentControl.Content) ] 屬性。</span><span class="sxs-lookup"><span data-stu-id="66224-151">In both of the previous examples, the text and the checkbox are set as the [Button.Content](xref:System.Windows.Controls.ContentControl.Content) property.</span></span> <span data-ttu-id="66224-152">無論內容設定為何，都可以透過來呈現 **\<ContentPresenter>** ，這就是範本的用途。</span><span class="sxs-lookup"><span data-stu-id="66224-152">Whatever is set as the content can be presented through a **\<ContentPresenter>**, which is what the template does.</span></span>

<span data-ttu-id="66224-153">如果套用 <xref:System.Windows.Controls.ControlTemplate> 至 <xref:System.Windows.Controls.ContentControl> 型別（例如 `Button` ）， <xref:System.Windows.Controls.ContentPresenter> 則會在專案樹狀結構中搜尋。</span><span class="sxs-lookup"><span data-stu-id="66224-153">If the <xref:System.Windows.Controls.ControlTemplate> is applied to a <xref:System.Windows.Controls.ContentControl> type, such as a `Button`, a <xref:System.Windows.Controls.ContentPresenter> is searched for in the element tree.</span></span> <span data-ttu-id="66224-154">如果 `ContentPresenter` 找到，此範本會自動將控制項的屬性系結 <xref:System.Windows.Controls.ContentControl.Content> 至 `ContentPresenter` 。</span><span class="sxs-lookup"><span data-stu-id="66224-154">If the `ContentPresenter` is found, the template automatically binds the control's <xref:System.Windows.Controls.ContentControl.Content> property to the `ContentPresenter`.</span></span>

## <a name="use-the-template"></a><span data-ttu-id="66224-155">使用範本</span><span class="sxs-lookup"><span data-stu-id="66224-155">Use the template</span></span>

<span data-ttu-id="66224-156">尋找在本文開頭所宣告的按鈕。</span><span class="sxs-lookup"><span data-stu-id="66224-156">Find the buttons that were declared at the start of this article.</span></span>

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

<span data-ttu-id="66224-157">將第二個按鈕的 <xref:System.Windows.Controls.Control.Template> 屬性設定為 `roundbutton` 資源：</span><span class="sxs-lookup"><span data-stu-id="66224-157">Set the second button's <xref:System.Windows.Controls.Control.Template> property to the `roundbutton` resource:</span></span>

[!code-xaml[StyledButton](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButton)]

<span data-ttu-id="66224-158">如果您執行專案並查看結果，您會看到按鈕具有圓角背景。</span><span class="sxs-lookup"><span data-stu-id="66224-158">If you run the project and look at the result, you'll see that the button has a rounded background.</span></span>

![具有一個樣板橢圓形按鈕的 WPF 視窗](media/create-apply-template/styled-button.png)

<span data-ttu-id="66224-160">您可能已經注意到按鈕不是圓形，而是扭曲。</span><span class="sxs-lookup"><span data-stu-id="66224-160">You may have noticed that the button isn't a circle but is skewed.</span></span> <span data-ttu-id="66224-161">由於元素的運作方式 **\<Ellipse>** ，它一律會展開以填滿可用的空間。</span><span class="sxs-lookup"><span data-stu-id="66224-161">Because of the way the **\<Ellipse>** element works, it always expands to fill the available space.</span></span> <span data-ttu-id="66224-162">將按鈕的 **:::no-loc text="width":::** 和 **:::no-loc text="height":::** 屬性變更為相同的值，使圓形成為一致：</span><span class="sxs-lookup"><span data-stu-id="66224-162">Make the circle uniform by changing the button's  **:::no-loc text="width":::** and **:::no-loc text="height":::** properties to the same value:</span></span>

[!code-xaml[StyledButtonSize](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButtonSize)]

![具有一個範本迴圈按鈕的 WPF 視窗](media/create-apply-template/styled-uniform-button.png)

## <a name="add-a-trigger"></a><span data-ttu-id="66224-164">新增觸發程式</span><span class="sxs-lookup"><span data-stu-id="66224-164">Add a Trigger</span></span>

<span data-ttu-id="66224-165">雖然套用範本的按鈕看起來不同，但其行為與任何其他按鈕相同。</span><span class="sxs-lookup"><span data-stu-id="66224-165">Even though a button with a template applied looks different, it behaves the same as any other button.</span></span> <span data-ttu-id="66224-166">如果您按下按鈕，就會 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 引發事件。</span><span class="sxs-lookup"><span data-stu-id="66224-166">If you press the button, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event fires.</span></span> <span data-ttu-id="66224-167">不過，您可能已經注意到，當您將滑鼠移至按鈕上方時，按鈕的視覺效果不會變更。</span><span class="sxs-lookup"><span data-stu-id="66224-167">However, you may have noticed that when you move your mouse over the button, the button's visuals don't change.</span></span> <span data-ttu-id="66224-168">這些視覺效果的互動都是由範本定義。</span><span class="sxs-lookup"><span data-stu-id="66224-168">These visual interactions are all defined by the template.</span></span>

<span data-ttu-id="66224-169">透過 WPF 提供的動態事件和屬性系統，您可以監看特定屬性的值，然後在適當時重新建立範本的樣式。</span><span class="sxs-lookup"><span data-stu-id="66224-169">With the dynamic event and property systems that WPF provides, you can watch a specific property for a value and then restyle the template when appropriate.</span></span> <span data-ttu-id="66224-170">在此範例中，您會看到按鈕的 <xref:System.Windows.UIElement.IsMouseOver> 屬性。</span><span class="sxs-lookup"><span data-stu-id="66224-170">In this example, you'll watch the button's <xref:System.Windows.UIElement.IsMouseOver> property.</span></span> <span data-ttu-id="66224-171">當滑鼠停留在控制項上時，使用新的色彩來建立樣式 **\<Ellipse>** 。</span><span class="sxs-lookup"><span data-stu-id="66224-171">When the mouse is over the control, style the **\<Ellipse>** with a new color.</span></span> <span data-ttu-id="66224-172">這種類型的觸發程式稱為*PropertyTrigger*。</span><span class="sxs-lookup"><span data-stu-id="66224-172">This type of trigger is known as a *PropertyTrigger*.</span></span>

<span data-ttu-id="66224-173">若要讓此作業正常執行，您必須將名稱新增至 **\<Ellipse>** 您可以參考的。</span><span class="sxs-lookup"><span data-stu-id="66224-173">For this to work, you'll need to add a name to the **\<Ellipse>** that you can reference.</span></span> <span data-ttu-id="66224-174">為它命名為**backgroundElement**。</span><span class="sxs-lookup"><span data-stu-id="66224-174">Give it the name of **backgroundElement**.</span></span>

[!code-xaml[EllipseName](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml#EllipseName)]

<span data-ttu-id="66224-175">接下來，將新的新增 <xref:System.Windows.Trigger> 至[ControlTemplate](xref:System.Windows.Controls.ControlTemplate.Triggers)集合。</span><span class="sxs-lookup"><span data-stu-id="66224-175">Next, add a new <xref:System.Windows.Trigger> to the [ControlTemplate.Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) collection.</span></span> <span data-ttu-id="66224-176">觸發程式將會監看此 `IsMouseOver` 值的事件 `true` 。</span><span class="sxs-lookup"><span data-stu-id="66224-176">The trigger will watch the `IsMouseOver` event for the value `true`.</span></span>

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml?name=ControlTemplate&highlight=6-10)]

<span data-ttu-id="66224-177">接下來，將新增 **\<Setter>** 至 **\<Trigger>** ，將的**Fill**屬性變更 **\<Ellipse>** 為新的色彩。</span><span class="sxs-lookup"><span data-stu-id="66224-177">Next, add a **\<Setter>** to the **\<Trigger>** that changes the **Fill** property of the **\<Ellipse>** to a new color.</span></span>

[!code-xaml[MouseOver](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#MouseOver)]

<span data-ttu-id="66224-178">執行專案。</span><span class="sxs-lookup"><span data-stu-id="66224-178">Run the project.</span></span> <span data-ttu-id="66224-179">請注意，當您將滑鼠游標移至按鈕上方時，會 **\<Ellipse>** 發生變更的色彩。</span><span class="sxs-lookup"><span data-stu-id="66224-179">Notice that when you move the mouse over the button, the color of the **\<Ellipse>** changes.</span></span>

![滑鼠移至 WPF 按鈕以變更填滿色彩](media/create-apply-template/mouse-move-over-button.gif)

## <a name="use-a-visualstate"></a><span data-ttu-id="66224-181">使用 VisualState</span><span class="sxs-lookup"><span data-stu-id="66224-181">Use a VisualState</span></span>

<span data-ttu-id="66224-182">視覺狀態是由控制項所定義和觸發。</span><span class="sxs-lookup"><span data-stu-id="66224-182">Visual states are defined and triggered by a control.</span></span> <span data-ttu-id="66224-183">例如，當滑鼠移到控制項上方時， `CommonStates.MouseOver` 就會觸發狀態。</span><span class="sxs-lookup"><span data-stu-id="66224-183">For example, when the mouse is moved on top of the control, the `CommonStates.MouseOver` state is triggered.</span></span> <span data-ttu-id="66224-184">您可以根據控制項的目前狀態來建立屬性變更的動畫。</span><span class="sxs-lookup"><span data-stu-id="66224-184">You can animate property changes based on the current state of the control.</span></span> <span data-ttu-id="66224-185">在上一節中， **\<PropertyTrigger>** 當屬性為時，用來將按鈕的前景變更為 `AliceBlue` `IsMouseOver` `true` 。</span><span class="sxs-lookup"><span data-stu-id="66224-185">In the previous section, a **\<PropertyTrigger>** was used to change the foreground of the button to `AliceBlue` when the `IsMouseOver` property was `true`.</span></span> <span data-ttu-id="66224-186">而是建立視覺狀態，以動畫顯示此色彩的變更，並提供順暢的轉換。</span><span class="sxs-lookup"><span data-stu-id="66224-186">Instead, create a visual state that animates the change of this color, providing a smooth transition.</span></span> <span data-ttu-id="66224-187">如需*VisualStates*的詳細資訊，請參閱[WPF 中的樣式和範本](../fundamentals/styles-templates-overview.md#visual-states)。</span><span class="sxs-lookup"><span data-stu-id="66224-187">For more information about *VisualStates*, see [Styles and templates in WPF](../fundamentals/styles-templates-overview.md#visual-states).</span></span>

<span data-ttu-id="66224-188">若要將轉換成 **\<PropertyTrigger>** 動畫視覺狀態，請先 **\<ControlTemplate.Triggers>** 從您的範本中移除元素。</span><span class="sxs-lookup"><span data-stu-id="66224-188">To convert the **\<PropertyTrigger>** to an animated visual state, First, remove the **\<ControlTemplate.Triggers>** element from your template.</span></span>

[!code-xaml[CleanTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#CleanTemplate)]

<span data-ttu-id="66224-189">接下來，在 **\<Grid>** 控制項範本的根目錄中，加入具有之的 **\<VisualStateManager.VisualStateGroups>** 元素 **\<VisualStateGroup>** `CommonStates` 。</span><span class="sxs-lookup"><span data-stu-id="66224-189">Next, in the **\<Grid>** root of the control template, add the **\<VisualStateManager.VisualStateGroups>** element with a **\<VisualStateGroup>** for `CommonStates`.</span></span> <span data-ttu-id="66224-190">定義兩個狀態： `Normal` 和 `MouseOver` 。</span><span class="sxs-lookup"><span data-stu-id="66224-190">Define two states, `Normal` and `MouseOver`.</span></span>

[!code-xaml[VisualState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#VisualState)]

<span data-ttu-id="66224-191">**\<VisualState>** 當觸發該狀態時，會套用在中定義的任何動畫。</span><span class="sxs-lookup"><span data-stu-id="66224-191">Any animations defined in a **\<VisualState>** are applied when that state is triggered.</span></span> <span data-ttu-id="66224-192">建立每個狀態的動畫。</span><span class="sxs-lookup"><span data-stu-id="66224-192">Create animations for each state.</span></span> <span data-ttu-id="66224-193">動畫會放在元素內 **\<Storyboard>** 。</span><span class="sxs-lookup"><span data-stu-id="66224-193">Animations are put inside of a **\<Storyboard>** element.</span></span> <span data-ttu-id="66224-194">如需有關分鏡腳本的詳細資訊，請參閱分鏡腳本[總覽](../../framework/wpf/graphics-multimedia/storyboards-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="66224-194">For more information about storyboards, see [Storyboards Overview](../../framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span>

- <span data-ttu-id="66224-195">正常</span><span class="sxs-lookup"><span data-stu-id="66224-195">Normal</span></span>

  <span data-ttu-id="66224-196">此狀態會將橢圓形填滿動畫，並將其還原為控制項的 `Background` 色彩。</span><span class="sxs-lookup"><span data-stu-id="66224-196">This state animates the ellipse fill, restoring it to the control's `Background` color.</span></span>

  [!code-xaml[NormalState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#NormalState)]

- <span data-ttu-id="66224-197">MouseOver</span><span class="sxs-lookup"><span data-stu-id="66224-197">MouseOver</span></span>

  <span data-ttu-id="66224-198">此狀態會以動畫將橢圓形 `Background` 色彩繪製到新的色彩： `Yellow` 。</span><span class="sxs-lookup"><span data-stu-id="66224-198">This state animates the ellipse `Background` color to a new color: `Yellow`.</span></span>

  [!code-xaml[MouseOverState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#MouseOverState)]

<span data-ttu-id="66224-199">**\<ControlTemplate>** 現在看起來應該如下所示。</span><span class="sxs-lookup"><span data-stu-id="66224-199">The **\<ControlTemplate>** should now look like the following.</span></span>

[!code-xaml[FinalTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window7.xaml#FinalTemplate)]

<span data-ttu-id="66224-200">執行專案。</span><span class="sxs-lookup"><span data-stu-id="66224-200">Run the project.</span></span> <span data-ttu-id="66224-201">請注意，當您將滑鼠游標移至按鈕上方時，會以動畫的色彩呈現 **\<Ellipse>** 。</span><span class="sxs-lookup"><span data-stu-id="66224-201">Notice that when you move the mouse over the button, the color of the **\<Ellipse>** animates.</span></span>

![滑鼠移至 WPF 按鈕以變更填滿色彩](media/create-apply-template/mouse-move-over-button-visualstate.gif)

## <a name="next-steps"></a><span data-ttu-id="66224-203">後續步驟</span><span class="sxs-lookup"><span data-stu-id="66224-203">Next steps</span></span>

- [<span data-ttu-id="66224-204">在 WPF 中建立控制項的樣式</span><span class="sxs-lookup"><span data-stu-id="66224-204">Create a style for a control in WPF</span></span>](../fundamentals/styles-templates-create-apply-style.md)
- [<span data-ttu-id="66224-205">WPF 中的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="66224-205">Styles and templates in WPF</span></span>](../fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="66224-206">XAML 資源的總覽</span><span class="sxs-lookup"><span data-stu-id="66224-206">Overview of XAML Resources</span></span>](../fundamentals/xaml-resources-define.md)
