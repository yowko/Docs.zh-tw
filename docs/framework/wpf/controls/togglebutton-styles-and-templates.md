---
title: ToggleButton 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], ToggleButton
- ToggleButton [WPF], styles and templates
- ControlTemplate [WPF], ToggleButton
- styles [WPF], ToggleButton
- templates [WPF], ToggleButton
- parts [WPF], ToggleButton
ms.assetid: 54f23f30-4bcb-4f09-8ce4-376a13a255a1
ms.openlocfilehash: a4c449a561017659db7f54fd3cdb8964742650de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283667"
---
# <a name="togglebutton-styles-and-templates"></a><span data-ttu-id="69b05-102">ToggleButton 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="69b05-102">ToggleButton Styles and Templates</span></span>

<span data-ttu-id="69b05-103">本主題描述 <xref:System.Windows.Controls.Primitives.ToggleButton> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="69b05-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span> <span data-ttu-id="69b05-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="69b05-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="69b05-105">如需詳細資訊，請參閱[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。</span><span class="sxs-lookup"><span data-stu-id="69b05-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>

## <a name="togglebutton-parts"></a><span data-ttu-id="69b05-106">切換按鈕部分</span><span class="sxs-lookup"><span data-stu-id="69b05-106">ToggleButton Parts</span></span>

<span data-ttu-id="69b05-107"><xref:System.Windows.Controls.Primitives.ToggleButton> 控制項沒有任何已命名的元件。</span><span class="sxs-lookup"><span data-stu-id="69b05-107">The <xref:System.Windows.Controls.Primitives.ToggleButton> control does not have any named parts.</span></span>

## <a name="togglebutton-states"></a><span data-ttu-id="69b05-108">切換按鈕狀態</span><span class="sxs-lookup"><span data-stu-id="69b05-108">ToggleButton States</span></span>

<span data-ttu-id="69b05-109">下表列出 <xref:System.Windows.Controls.Primitives.ToggleButton> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="69b05-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

|<span data-ttu-id="69b05-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="69b05-110">VisualState Name</span></span>|<span data-ttu-id="69b05-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="69b05-111">VisualStateGroup Name</span></span>|<span data-ttu-id="69b05-112">描述</span><span class="sxs-lookup"><span data-stu-id="69b05-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="69b05-113">一般</span><span class="sxs-lookup"><span data-stu-id="69b05-113">Normal</span></span>|<span data-ttu-id="69b05-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="69b05-114">CommonStates</span></span>|<span data-ttu-id="69b05-115">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="69b05-115">The default state.</span></span>|
|<span data-ttu-id="69b05-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="69b05-116">MouseOver</span></span>|<span data-ttu-id="69b05-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="69b05-117">CommonStates</span></span>|<span data-ttu-id="69b05-118">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="69b05-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="69b05-119">按下</span><span class="sxs-lookup"><span data-stu-id="69b05-119">Pressed</span></span>|<span data-ttu-id="69b05-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="69b05-120">CommonStates</span></span>|<span data-ttu-id="69b05-121">已按下控制項。</span><span class="sxs-lookup"><span data-stu-id="69b05-121">The control is pressed.</span></span>|
|<span data-ttu-id="69b05-122">已停用</span><span class="sxs-lookup"><span data-stu-id="69b05-122">Disabled</span></span>|<span data-ttu-id="69b05-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="69b05-123">CommonStates</span></span>|<span data-ttu-id="69b05-124">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="69b05-124">The control is disabled.</span></span>|
|<span data-ttu-id="69b05-125">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="69b05-125">Focused</span></span>|<span data-ttu-id="69b05-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="69b05-126">FocusStates</span></span>|<span data-ttu-id="69b05-127">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="69b05-127">The control has focus.</span></span>|
|<span data-ttu-id="69b05-128">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="69b05-128">Unfocused</span></span>|<span data-ttu-id="69b05-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="69b05-129">FocusStates</span></span>|<span data-ttu-id="69b05-130">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="69b05-130">The control does not have focus.</span></span>|
|<span data-ttu-id="69b05-131">已核取</span><span class="sxs-lookup"><span data-stu-id="69b05-131">Checked</span></span>|<span data-ttu-id="69b05-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="69b05-132">CheckStates</span></span>|<span data-ttu-id="69b05-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 為 `true`。</span><span class="sxs-lookup"><span data-stu-id="69b05-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|
|<span data-ttu-id="69b05-134">選定</span><span class="sxs-lookup"><span data-stu-id="69b05-134">Unchecked</span></span>|<span data-ttu-id="69b05-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="69b05-135">CheckStates</span></span>|<span data-ttu-id="69b05-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 為 `false`。</span><span class="sxs-lookup"><span data-stu-id="69b05-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|
|<span data-ttu-id="69b05-137">處於</span><span class="sxs-lookup"><span data-stu-id="69b05-137">Indeterminate</span></span>|<span data-ttu-id="69b05-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="69b05-138">CheckStates</span></span>|<span data-ttu-id="69b05-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> 為 `true`，<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> `null`。</span><span class="sxs-lookup"><span data-stu-id="69b05-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|
|<span data-ttu-id="69b05-140">有效</span><span class="sxs-lookup"><span data-stu-id="69b05-140">Valid</span></span>|<span data-ttu-id="69b05-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="69b05-141">ValidationStates</span></span>|<span data-ttu-id="69b05-142">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="69b05-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="69b05-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="69b05-143">InvalidFocused</span></span>|<span data-ttu-id="69b05-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="69b05-144">ValidationStates</span></span>|<span data-ttu-id="69b05-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="69b05-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="69b05-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="69b05-146">InvalidUnfocused</span></span>|<span data-ttu-id="69b05-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="69b05-147">ValidationStates</span></span>|<span data-ttu-id="69b05-148"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="69b05-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

> [!NOTE]
> <span data-ttu-id="69b05-149">如果您的控制項範本中沒有未定的視覺狀態，則會使用未核取的視覺狀態做為預設的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="69b05-149">If the Indeterminate visual state does not exist in your control template, then the Unchecked visual state will be used as default visual state.</span></span>

## <a name="togglebutton-controltemplate-example"></a><span data-ttu-id="69b05-150">切換按鈕 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="69b05-150">ToggleButton ControlTemplate Example</span></span>

<span data-ttu-id="69b05-151">下列範例顯示如何定義 <xref:System.Windows.Controls.Primitives.ToggleButton> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="69b05-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

[!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]

<span data-ttu-id="69b05-152">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="69b05-152">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="69b05-153">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="69b05-153">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="69b05-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69b05-154">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="69b05-155">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="69b05-155">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="69b05-156">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="69b05-156">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="69b05-157">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="69b05-157">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="69b05-158">建立控制項的範本</span><span class="sxs-lookup"><span data-stu-id="69b05-158">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
