---
title: 在 WPF - .NET 桌面建立樣本
description: 瞭解如何在 Windows 演示文稿基礎和 .NET Core 中創建和引用控制項樣本。
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
# <a name="create-a-template-for-a-control"></a><span data-ttu-id="9e90a-103">為控制項建立樣本</span><span class="sxs-lookup"><span data-stu-id="9e90a-103">Create a template for a control</span></span>

<span data-ttu-id="9e90a-104">使用 Windows 簡報簡報 (WPF),您可以使用自己的可重用範本自訂現有控制項的可視結構和行為。</span><span class="sxs-lookup"><span data-stu-id="9e90a-104">With Windows Presentation Foundation (WPF), you can customize an existing control's visual structure and behavior with your own reusable template.</span></span> <span data-ttu-id="9e90a-105">範本可以全域應用於應用程式、視窗和頁面,也可以直接應用於控件。</span><span class="sxs-lookup"><span data-stu-id="9e90a-105">Templates can be applied globally to your application, windows and pages, or directly to controls.</span></span> <span data-ttu-id="9e90a-106">通過為現有控制項創建新範本,可以涵蓋大多數需要您創建新控制項的方案。</span><span class="sxs-lookup"><span data-stu-id="9e90a-106">Most scenarios that require you to create a new control can be covered by instead creating a new template for an existing control.</span></span>

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

<span data-ttu-id="9e90a-107">在本文中,您將探討<xref:System.Windows.Controls.ControlTemplate><xref:System.Windows.Controls.Button>為控制項創建新控制項。</span><span class="sxs-lookup"><span data-stu-id="9e90a-107">In this article, you'll explore creating a new <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>

## <a name="when-to-create-a-controltemplate"></a><span data-ttu-id="9e90a-108">何時建立控制項樣本</span><span class="sxs-lookup"><span data-stu-id="9e90a-108">When to create a ControlTemplate</span></span>

<span data-ttu-id="9e90a-109">控制項具有許多屬性,例如<xref:System.Windows.Controls.Border.Background%2A>與<xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Controls.Control.FontFamily%2A> 。</span><span class="sxs-lookup"><span data-stu-id="9e90a-109">Controls have many properties, such as <xref:System.Windows.Controls.Border.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, and <xref:System.Windows.Controls.Control.FontFamily%2A>.</span></span> <span data-ttu-id="9e90a-110">這些屬性控制控制件外觀的不同方面,但通過設置這些屬性可以進行的更改是有限的。</span><span class="sxs-lookup"><span data-stu-id="9e90a-110">These properties control different aspects of the control's appearance, but the changes that you can make by setting these properties are limited.</span></span> <span data-ttu-id="9e90a-111">例如,可以將<xref:System.Windows.Controls.Control.Foreground%2A>屬性設置為藍色,<xref:System.Windows.Controls.Control.FontStyle%2A>將 屬性設置為斜<xref:System.Windows.Controls.CheckBox>體。</span><span class="sxs-lookup"><span data-stu-id="9e90a-111">For example, you can set the <xref:System.Windows.Controls.Control.Foreground%2A> property to blue and <xref:System.Windows.Controls.Control.FontStyle%2A> to italic on a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="9e90a-112">如果要自訂控制件的外觀,超出控制項上其他屬性設定可以執行的內容,請建立一個<xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="9e90a-112">When you want to customize the control's appearance beyond what setting the other properties on the control can do, you create a <xref:System.Windows.Controls.ControlTemplate>.</span></span>

<span data-ttu-id="9e90a-113">在大多數用戶介面中,按鈕具有相同的常規外觀:帶有某些文本的矩形。</span><span class="sxs-lookup"><span data-stu-id="9e90a-113">In most user interfaces, a button has the same general appearance: a rectangle with some text.</span></span> <span data-ttu-id="9e90a-114">如果要創建圓角按鈕,可以創建從按鈕繼承的新控制項或重新創建按鈕的功能。</span><span class="sxs-lookup"><span data-stu-id="9e90a-114">If you wanted to create a rounded button, you could create a new control that inherits from the button or recreates the functionality of the button.</span></span> <span data-ttu-id="9e90a-115">此外,新的使用者控制項將提供圓形視覺物件。</span><span class="sxs-lookup"><span data-stu-id="9e90a-115">In addition, the new user control would provide the circular visual.</span></span>

<span data-ttu-id="9e90a-116">通過自定義現有控制項的可視佈局,可以避免創建新控制項。</span><span class="sxs-lookup"><span data-stu-id="9e90a-116">You can avoid creating new controls by customizing the visual layout of an existing control.</span></span> <span data-ttu-id="9e90a-117">使用圓角按鈕,建立<xref:System.Windows.Controls.ControlTemplate>具有所需視覺佈局的 。</span><span class="sxs-lookup"><span data-stu-id="9e90a-117">With a rounded button, you create a <xref:System.Windows.Controls.ControlTemplate> with the desired visual layout.</span></span>

<span data-ttu-id="9e90a-118">另一方面,如果需要具有新功能、不同屬性和新設置的控制項,則可以創建新<xref:System.Windows.Controls.UserControl>的 。</span><span class="sxs-lookup"><span data-stu-id="9e90a-118">On the other hand, if you need a control with new functionality, different properties, and new settings, you would create a new <xref:System.Windows.Controls.UserControl>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9e90a-119">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="9e90a-119">Prerequisites</span></span>

<span data-ttu-id="9e90a-120">建立新的 WPF 應用程式,並在*MainWindow.xaml(* 或您選擇的其他視窗)中設定**\<視窗>** 元素上的以下屬性:</span><span class="sxs-lookup"><span data-stu-id="9e90a-120">Create a new WPF application and in *MainWindow.xaml* (or another window of your choice) set the following properties on the **\<Window>** element:</span></span>

|     |     |
| --- | --- |
| **[!OP.NO-LOC(Title)]**         | `Template Intro Sample` |
| **[!OP.NO-LOC(SizeToContent)]** | `WidthAndHeight` |
| **[!OP.NO-LOC(MinWidth)]**      | `250` |

<span data-ttu-id="9e90a-121">將**\<視窗>** 元素的內容設定為以下 XAML:</span><span class="sxs-lookup"><span data-stu-id="9e90a-121">Set the content of the **\<Window>** element to the following XAML:</span></span>

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

<span data-ttu-id="9e90a-122">最後 *,MainWindow.xaml*檔案應類似於以下內容:</span><span class="sxs-lookup"><span data-stu-id="9e90a-122">In the end, the *MainWindow.xaml* file should look similar to the following:</span></span>

[!code-xaml[InitialWhole](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#InitialWhole)]

<span data-ttu-id="9e90a-123">如果運行該應用程式,它如下所示:</span><span class="sxs-lookup"><span data-stu-id="9e90a-123">If you run the application, it looks like the following:</span></span>

![帶兩個未樣式按鈕的 WPF 視窗](media/create-apply-template/unstyled-button.png)

## <a name="create-a-controltemplate"></a><span data-ttu-id="9e90a-125">建立 ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="9e90a-125">Create a ControlTemplate</span></span>

<span data-ttu-id="9e90a-126">聲明<xref:System.Windows.Controls.ControlTemplate>的最常見方法是作為 XAML`Resources`檔中 的節中的資源。</span><span class="sxs-lookup"><span data-stu-id="9e90a-126">The most common way to declare a <xref:System.Windows.Controls.ControlTemplate> is as a resource in the `Resources` section in a XAML file.</span></span> <span data-ttu-id="9e90a-127">由於範本是資源,因此它們遵循適用於所有資源的相同範圍規則。</span><span class="sxs-lookup"><span data-stu-id="9e90a-127">Because templates are resources, they obey the same scoping rules that apply to all resources.</span></span> <span data-ttu-id="9e90a-128">簡單地說,聲明範本的位置會影響範本的應用位置。</span><span class="sxs-lookup"><span data-stu-id="9e90a-128">Put simply, where you declare a template affects where the template can be applied.</span></span> <span data-ttu-id="9e90a-129">例如,如果在應用程式定義 XAML 檔的根元素中聲明範本,則可以在應用程式中的任何位置使用該範本。</span><span class="sxs-lookup"><span data-stu-id="9e90a-129">For example, if you declare the template in the root element of your application definition XAML file, the template can be used anywhere in your application.</span></span> <span data-ttu-id="9e90a-130">如果在視窗中定義範本,則只有該視窗中的控制項可以使用該範本。</span><span class="sxs-lookup"><span data-stu-id="9e90a-130">If you define the template in a window, only the controls in that window can use the template.</span></span>

<span data-ttu-id="9e90a-131">首先,向`Window.Resources`*MainWindow.xaml*檔案加入元素:</span><span class="sxs-lookup"><span data-stu-id="9e90a-131">To start with, add a `Window.Resources` element to your *MainWindow.xaml* file:</span></span>

[!code-xaml[WindowResStart](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window2.xaml#WindowResStart)]

<span data-ttu-id="9e90a-132">使用以下屬性集建立新**\<的 ControlTemplate>:**</span><span class="sxs-lookup"><span data-stu-id="9e90a-132">Create a new **\<ControlTemplate>** with the following properties set:</span></span>

|     |     |
| --- | --- |
| <span data-ttu-id="9e90a-133">**x:Key**</span><span class="sxs-lookup"><span data-stu-id="9e90a-133">**x:Key**</span></span>         | `roundbutton` |
| **TargetType**    | `Button` |

<span data-ttu-id="9e90a-134">此控制項樣本非常簡單:</span><span class="sxs-lookup"><span data-stu-id="9e90a-134">This control template will be simple:</span></span>

- <span data-ttu-id="9e90a-135">控件的根元素,<xref:System.Windows.Controls.Grid></span><span class="sxs-lookup"><span data-stu-id="9e90a-135">a root element for the control, a <xref:System.Windows.Controls.Grid></span></span>
- <span data-ttu-id="9e90a-136">繪製<xref:System.Windows.Shapes.Ellipse>按鍵的圓舍入外觀</span><span class="sxs-lookup"><span data-stu-id="9e90a-136">an <xref:System.Windows.Shapes.Ellipse> to draw the rounded appearance of the button</span></span>
- <span data-ttu-id="9e90a-137">a<xref:System.Windows.Controls.ContentPresenter>以顯示使用者指定的按鈕內容</span><span class="sxs-lookup"><span data-stu-id="9e90a-137">a <xref:System.Windows.Controls.ContentPresenter> to display the user-specified button content</span></span>

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#ControlTemplate)]

### <a name="templatebinding"></a><span data-ttu-id="9e90a-138">TemplateBinding</span><span class="sxs-lookup"><span data-stu-id="9e90a-138">TemplateBinding</span></span>

<span data-ttu-id="9e90a-139">創建新<xref:System.Windows.Controls.ControlTemplate>時 ,仍可能仍要使用公共屬性來更改控制件的外觀。</span><span class="sxs-lookup"><span data-stu-id="9e90a-139">When you create a new <xref:System.Windows.Controls.ControlTemplate>, you still might want to use the public properties to change the control's appearance.</span></span> <span data-ttu-id="9e90a-140">[樣本繫結](../../framework/wpf/advanced/templatebinding-markup-extension.md)標記延伸將 元素的屬性綁定<xref:System.Windows.Controls.ControlTemplate>到由控制項定義的公共屬性。</span><span class="sxs-lookup"><span data-stu-id="9e90a-140">The [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) markup extension binds a property of an element that is in the <xref:System.Windows.Controls.ControlTemplate> to a public property that is defined by the control.</span></span> <span data-ttu-id="9e90a-141">使用[範本繫結](../../framework/wpf/advanced/templatebinding-markup-extension.md)項時,將啟用控制件上的屬性作為範本的參數。</span><span class="sxs-lookup"><span data-stu-id="9e90a-141">When you use a [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md), you enable properties on the control to act as parameters to the template.</span></span> <span data-ttu-id="9e90a-142">也就是說，已設定控制項上的屬性時，該值會傳遞給具有 [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) 的元素。</span><span class="sxs-lookup"><span data-stu-id="9e90a-142">That is, when a property on a control is set, that value is passed on to the element that has the [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) on it.</span></span>

### <a name="ellipse"></a><span data-ttu-id="9e90a-143">橢圓形</span><span class="sxs-lookup"><span data-stu-id="9e90a-143">Ellipse</span></span>

<span data-ttu-id="9e90a-144">**:::no-loc text="Fill":::** 請注意**:::no-loc text="Stroke":::**<xref:System.Windows.Controls.Control.Foreground>,**\<橢圓>** 元素的 和 屬性綁<xref:System.Windows.Controls.Control.Background>定到控制項和 屬性。</span><span class="sxs-lookup"><span data-stu-id="9e90a-144">Notice that the **:::no-loc text="Fill":::** and **:::no-loc text="Stroke":::** properties of the **\<Ellipse>** element are bound to the control's <xref:System.Windows.Controls.Control.Foreground> and <xref:System.Windows.Controls.Control.Background> properties.</span></span>

### <a name="contentpresenter"></a><span data-ttu-id="9e90a-145">ContentPresenter</span><span class="sxs-lookup"><span data-stu-id="9e90a-145">ContentPresenter</span></span>

<span data-ttu-id="9e90a-146">內容演示者>元素也會添加到範本中。 [ \< ](xref:System.Windows.Controls.ContentPresenter)</span><span class="sxs-lookup"><span data-stu-id="9e90a-146">A [\<ContentPresenter>](xref:System.Windows.Controls.ContentPresenter) element is also added to the template.</span></span> <span data-ttu-id="9e90a-147">由於此範本是為按鈕設計的,因此,考慮到該按鈕從<xref:System.Windows.Controls.ContentControl>繼承。</span><span class="sxs-lookup"><span data-stu-id="9e90a-147">Because this template is designed for a button, take into consideration that the button inherits from <xref:System.Windows.Controls.ContentControl>.</span></span> <span data-ttu-id="9e90a-148">該按鈕顯示元素的內容。</span><span class="sxs-lookup"><span data-stu-id="9e90a-148">The button presents the content of the element.</span></span> <span data-ttu-id="9e90a-149">您可以在按鈕內設置任何內容,例如純文本或其他控件。</span><span class="sxs-lookup"><span data-stu-id="9e90a-149">You can set anything inside of the button, such as plain text or even another control.</span></span> <span data-ttu-id="9e90a-150">以下兩個按鈕均為有效按鈕:</span><span class="sxs-lookup"><span data-stu-id="9e90a-150">Both of the following are valid buttons:</span></span>

```xaml
<Button>My Text</Button>

<!-- and -->

<Button>
    <CheckBox>Checkbox in a button</CheckBox>
</Button>
```

<span data-ttu-id="9e90a-151">在前面的兩個範例中,文本和複選框都設置為[Button.Content](xref:System.Windows.Controls.ContentControl.Content)屬性。</span><span class="sxs-lookup"><span data-stu-id="9e90a-151">In both of the previous examples, the text and the checkbox are set as the [Button.Content](xref:System.Windows.Controls.ContentControl.Content) property.</span></span> <span data-ttu-id="9e90a-152">任何設置為內容的內容都可以通過**\<ContentPresenter>**(即範本)顯示,這是範本的作用。</span><span class="sxs-lookup"><span data-stu-id="9e90a-152">Whatever is set as the content can be presented through a **\<ContentPresenter>**, which is what the template does.</span></span>

<span data-ttu-id="9e90a-153">如果 套<xref:System.Windows.Controls.ContentControl>用型態`Button`(如元素樹中搜尋<xref:System.Windows.Controls.ContentPresenter><xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="9e90a-153">If the <xref:System.Windows.Controls.ControlTemplate> is applied to a <xref:System.Windows.Controls.ContentControl> type, such as a `Button`, a <xref:System.Windows.Controls.ContentPresenter> is searched for in the element tree.</span></span> <span data-ttu-id="9e90a-154">找不到`ContentPresenter`,樣本會自動將控制的屬性 的<xref:System.Windows.Controls.ContentControl.Content>屬性 。 `ContentPresenter`</span><span class="sxs-lookup"><span data-stu-id="9e90a-154">If the `ContentPresenter` is found, the template automatically binds the control's <xref:System.Windows.Controls.ContentControl.Content> property to the `ContentPresenter`.</span></span>

## <a name="use-the-template"></a><span data-ttu-id="9e90a-155">使用範本</span><span class="sxs-lookup"><span data-stu-id="9e90a-155">Use the template</span></span>

<span data-ttu-id="9e90a-156">查找本文開頭聲明的按鈕。</span><span class="sxs-lookup"><span data-stu-id="9e90a-156">Find the buttons that were declared at the start of this article.</span></span>

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

<span data-ttu-id="9e90a-157">將第二個按鈕的屬性<xref:System.Windows.Controls.Control.Template>設定`roundbutton`為 資源:</span><span class="sxs-lookup"><span data-stu-id="9e90a-157">Set the second button's <xref:System.Windows.Controls.Control.Template> property to the `roundbutton` resource:</span></span>

[!code-xaml[StyledButton](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButton)]

<span data-ttu-id="9e90a-158">如果執行項目並查看結果,您將看到該按鈕具有圓潤的背景。</span><span class="sxs-lookup"><span data-stu-id="9e90a-158">If you run the project and look at the result, you'll see that the button has a rounded background.</span></span>

![帶一個樣本橢圓形按鈕的 WPF 視窗](media/create-apply-template/styled-button.png)

<span data-ttu-id="9e90a-160">您可能已經注意到該按鈕不是圓,而是偏斜的。</span><span class="sxs-lookup"><span data-stu-id="9e90a-160">You may have noticed that the button isn't a circle but is skewed.</span></span> <span data-ttu-id="9e90a-161">由於**\<橢圓>** 元素的工作方式,它總是展開以填充可用空間。</span><span class="sxs-lookup"><span data-stu-id="9e90a-161">Because of the way the **\<Ellipse>** element works, it always expands to fill the available space.</span></span> <span data-ttu-id="9e90a-162">透過按鈕**:::no-loc text="width":::** 與屬性**:::no-loc text="height":::** 變更為相同的值,使圓均勻:</span><span class="sxs-lookup"><span data-stu-id="9e90a-162">Make the circle uniform by changing the button's  **:::no-loc text="width":::** and **:::no-loc text="height":::** properties to the same value:</span></span>

[!code-xaml[StyledButtonSize](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButtonSize)]

![以樣本圓形按鈕的 WPF 視窗](media/create-apply-template/styled-uniform-button.png)

## <a name="add-a-trigger"></a><span data-ttu-id="9e90a-164">新增觸發器</span><span class="sxs-lookup"><span data-stu-id="9e90a-164">Add a Trigger</span></span>

<span data-ttu-id="9e90a-165">即使應用了範本的按鈕看起來不同,它的外觀與任何其他按鈕相同。</span><span class="sxs-lookup"><span data-stu-id="9e90a-165">Even though a button with a template applied looks different, it behaves the same as any other button.</span></span> <span data-ttu-id="9e90a-166">如果按下該按鈕,事件將<xref:System.Windows.Controls.Primitives.ButtonBase.Click>觸發。</span><span class="sxs-lookup"><span data-stu-id="9e90a-166">If you press the button, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event fires.</span></span> <span data-ttu-id="9e90a-167">但是,您可能已經注意到,當您將滑鼠移到按鈕上時,按鈕的視覺效果不會更改。</span><span class="sxs-lookup"><span data-stu-id="9e90a-167">However, you may have noticed that when you move your mouse over the button, the button's visuals don't change.</span></span> <span data-ttu-id="9e90a-168">這些可視化交互都由範本定義。</span><span class="sxs-lookup"><span data-stu-id="9e90a-168">These visual interactions are all defined by the template.</span></span>

<span data-ttu-id="9e90a-169">使用 WPF 提供的動態事件和屬性系統,可以監視值的特定屬性,然後在適當的時候重新設置範本的樣式。</span><span class="sxs-lookup"><span data-stu-id="9e90a-169">With the dynamic event and property systems that WPF provides, you can watch a specific property for a value and then restyle the template when appropriate.</span></span> <span data-ttu-id="9e90a-170">這個選項, 您會觀看按鈕的屬性<xref:System.Windows.UIElement.IsMouseOver>。</span><span class="sxs-lookup"><span data-stu-id="9e90a-170">In this example, you'll watch the button's <xref:System.Windows.UIElement.IsMouseOver> property.</span></span> <span data-ttu-id="9e90a-171">當滑鼠位於控件上時,使用新顏色對**\<橢圓>** 進行樣式設置。</span><span class="sxs-lookup"><span data-stu-id="9e90a-171">When the mouse is over the control, style the **\<Ellipse>** with a new color.</span></span> <span data-ttu-id="9e90a-172">這種類型的觸發器稱為*屬性觸發器*。</span><span class="sxs-lookup"><span data-stu-id="9e90a-172">This type of trigger is known as a *PropertyTrigger*.</span></span>

<span data-ttu-id="9e90a-173">為此,您需要向**\<橢圓>** 添加一個名稱,以便參考。</span><span class="sxs-lookup"><span data-stu-id="9e90a-173">For this to work, you'll need to add a name to the **\<Ellipse>** that you can reference.</span></span> <span data-ttu-id="9e90a-174">給它的背景**元素**的名稱。</span><span class="sxs-lookup"><span data-stu-id="9e90a-174">Give it the name of **backgroundElement**.</span></span>

[!code-xaml[EllipseName](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml#EllipseName)]

<span data-ttu-id="9e90a-175">接下來,<xref:System.Windows.Trigger>向[控件範本.Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers)集合添加新。</span><span class="sxs-lookup"><span data-stu-id="9e90a-175">Next, add a new <xref:System.Windows.Trigger> to the [ControlTemplate.Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) collection.</span></span> <span data-ttu-id="9e90a-176">觸發器將監視值`IsMouseOver``true`的事件。</span><span class="sxs-lookup"><span data-stu-id="9e90a-176">The trigger will watch the `IsMouseOver` event for the value `true`.</span></span>

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml?name=ControlTemplate&highlight=6-10)]

<span data-ttu-id="9e90a-177">接下來,將**\<setter>** 添加到**\<將\*\*\*\*\<橢圓>** 的**填充**屬性更改為新顏色的觸發器>。</span><span class="sxs-lookup"><span data-stu-id="9e90a-177">Next, add a **\<Setter>** to the **\<Trigger>** that changes the **Fill** property of the **\<Ellipse>** to a new color.</span></span>

[!code-xaml[MouseOver](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#MouseOver)]

<span data-ttu-id="9e90a-178">執行專案。</span><span class="sxs-lookup"><span data-stu-id="9e90a-178">Run the project.</span></span> <span data-ttu-id="9e90a-179">請注意,當您將滑鼠移到按鈕上時,**\<橢圓的顏色>** 更改。</span><span class="sxs-lookup"><span data-stu-id="9e90a-179">Notice that when you move the mouse over the button, the color of the **\<Ellipse>** changes.</span></span>

![滑鼠在 WPF 按鍵上移動以改變填充顏色](media/create-apply-template/mouse-move-over-button.gif)

## <a name="use-a-visualstate"></a><span data-ttu-id="9e90a-181">使用視覺狀態</span><span class="sxs-lookup"><span data-stu-id="9e90a-181">Use a VisualState</span></span>

<span data-ttu-id="9e90a-182">可視狀態由控件定義和觸發。</span><span class="sxs-lookup"><span data-stu-id="9e90a-182">Visual states are defined and triggered by a control.</span></span> <span data-ttu-id="9e90a-183">例如,當滑鼠移動到控制項的頂部時,`CommonStates.MouseOver`將觸發狀態。</span><span class="sxs-lookup"><span data-stu-id="9e90a-183">For example, when the mouse is moved on top of the control, the `CommonStates.MouseOver` state is triggered.</span></span> <span data-ttu-id="9e90a-184">您可以根據控制項的當前狀態為屬性更改設定動畫。</span><span class="sxs-lookup"><span data-stu-id="9e90a-184">You can animate property changes based on the current state of the control.</span></span> <span data-ttu-id="9e90a-185">在`AliceBlue``IsMouseOver``true`上**一\<節中,屬性觸發器>** 用於將按鈕的前景更改為 屬性為 時。</span><span class="sxs-lookup"><span data-stu-id="9e90a-185">In the previous section, a **\<PropertyTrigger>** was used to change the foreground of the button to `AliceBlue` when the `IsMouseOver` property was `true`.</span></span> <span data-ttu-id="9e90a-186">相反,創建一個可視狀態,為更改此顏色設置動畫,從而提供平滑過渡。</span><span class="sxs-lookup"><span data-stu-id="9e90a-186">Instead, create a visual state that animates the change of this color, providing a smooth transition.</span></span> <span data-ttu-id="9e90a-187">有關 Visual*狀態*的詳細資訊,請參閱[WPF 中的樣式和樣本](../fundamentals/styles-templates-overview.md#visual-states)。</span><span class="sxs-lookup"><span data-stu-id="9e90a-187">For more information about *VisualStates*, see [Styles and templates in WPF](../fundamentals/styles-templates-overview.md#visual-states).</span></span>

<span data-ttu-id="9e90a-188">要將**\<屬性觸發>** 轉換為動畫視覺狀態,首先,請從範本中刪除**\<ControlTemplate.Trigger>** 元素。</span><span class="sxs-lookup"><span data-stu-id="9e90a-188">To convert the **\<PropertyTrigger>** to an animated visual state, First, remove the **\<ControlTemplate.Triggers>** element from your template.</span></span>

[!code-xaml[CleanTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#CleanTemplate)]

<span data-ttu-id="9e90a-189">接下來,在**\<控件範本的網格>** 根中,添加**\<VisualStateManager.VisualStateGroup>** 元素,該元素具有**\<VisualStateGroup** `CommonStates`>。</span><span class="sxs-lookup"><span data-stu-id="9e90a-189">Next, in the **\<Grid>** root of the control template, add the **\<VisualStateManager.VisualStateGroups>** element with a **\<VisualStateGroup>** for `CommonStates`.</span></span> <span data-ttu-id="9e90a-190">定義兩種狀態`Normal`,`MouseOver`與 。</span><span class="sxs-lookup"><span data-stu-id="9e90a-190">Define two states, `Normal` and `MouseOver`.</span></span>

[!code-xaml[VisualState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#VisualState)]

<span data-ttu-id="9e90a-191">觸發**\<該**狀態時,將應用 VisualState>中定义的任何动画。</span><span class="sxs-lookup"><span data-stu-id="9e90a-191">Any animations defined in a **\<VisualState>** are applied when that state is triggered.</span></span> <span data-ttu-id="9e90a-192">為每個狀態創建動畫。</span><span class="sxs-lookup"><span data-stu-id="9e90a-192">Create animations for each state.</span></span> <span data-ttu-id="9e90a-193">動畫放在**\<情節提要>** 元素的內。</span><span class="sxs-lookup"><span data-stu-id="9e90a-193">Animations are put inside of a **\<Storyboard>** element.</span></span> <span data-ttu-id="9e90a-194">有關情節提要的詳細資訊,請參閱[情節提要概述](../../framework/wpf/graphics-multimedia/storyboards-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9e90a-194">For more information about storyboards, see [Storyboards Overview](../../framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span>

- <span data-ttu-id="9e90a-195">正常</span><span class="sxs-lookup"><span data-stu-id="9e90a-195">Normal</span></span>

  <span data-ttu-id="9e90a-196">此狀態為橢圓填充設置動畫,將其還原到控制項`Background`的顏色。</span><span class="sxs-lookup"><span data-stu-id="9e90a-196">This state animates the ellipse fill, restoring it to the control's `Background` color.</span></span>

  [!code-xaml[NormalState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#NormalState)]

- <span data-ttu-id="9e90a-197">MouseOver</span><span class="sxs-lookup"><span data-stu-id="9e90a-197">MouseOver</span></span>

  <span data-ttu-id="9e90a-198">此狀態將橢圓`Background`顏色動畫為新顏色`Yellow`: 。</span><span class="sxs-lookup"><span data-stu-id="9e90a-198">This state animates the ellipse `Background` color to a new color: `Yellow`.</span></span>

  [!code-xaml[MouseOverState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#MouseOverState)]

<span data-ttu-id="9e90a-199">控件範本>現在應如下所示。 \*\* \< \*\*</span><span class="sxs-lookup"><span data-stu-id="9e90a-199">The **\<ControlTemplate>** should now look like the following.</span></span>

[!code-xaml[FinalTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window7.xaml#FinalTemplate)]

<span data-ttu-id="9e90a-200">執行專案。</span><span class="sxs-lookup"><span data-stu-id="9e90a-200">Run the project.</span></span> <span data-ttu-id="9e90a-201">請注意,當您將滑鼠移到按鈕上時,**\<橢圓的顏色>** 動畫。</span><span class="sxs-lookup"><span data-stu-id="9e90a-201">Notice that when you move the mouse over the button, the color of the **\<Ellipse>** animates.</span></span>

![滑鼠在 WPF 按鍵上移動以改變填充顏色](media/create-apply-template/mouse-move-over-button-visualstate.gif)

## <a name="next-steps"></a><span data-ttu-id="9e90a-203">後續步驟</span><span class="sxs-lookup"><span data-stu-id="9e90a-203">Next steps</span></span>

- [<span data-ttu-id="9e90a-204">為 WPF 中的控制項建立樣式</span><span class="sxs-lookup"><span data-stu-id="9e90a-204">Create a style for a control in WPF</span></span>](../fundamentals/styles-templates-create-apply-style.md)
- [<span data-ttu-id="9e90a-205">WPF 中的樣式和樣本</span><span class="sxs-lookup"><span data-stu-id="9e90a-205">Styles and templates in WPF</span></span>](../fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="9e90a-206">XAML 資源概述</span><span class="sxs-lookup"><span data-stu-id="9e90a-206">Overview of XAML Resources</span></span>](../fundamentals/xaml-resources-define.md)
