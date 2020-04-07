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
ms.openlocfilehash: e055dcbd557f9b90eb2fe99ad15a05b6f229fd28
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805918"
---
# <a name="togglebutton-styles-and-templates"></a><span data-ttu-id="e6147-102">ToggleButton 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="e6147-102">ToggleButton Styles and Templates</span></span>

<span data-ttu-id="e6147-103">本主題介紹控件的<xref:System.Windows.Controls.Primitives.ToggleButton>樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="e6147-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span> <span data-ttu-id="e6147-104">您可以修改預設值<xref:System.Windows.Controls.ControlTemplate>,為控制項提供唯一的外觀。</span><span class="sxs-lookup"><span data-stu-id="e6147-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="e6147-105">有關詳細資訊,請參閱為[控制項建立樣本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。</span><span class="sxs-lookup"><span data-stu-id="e6147-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>

## <a name="togglebutton-parts"></a><span data-ttu-id="e6147-106">切換按鈕零件</span><span class="sxs-lookup"><span data-stu-id="e6147-106">ToggleButton Parts</span></span>

<span data-ttu-id="e6147-107">該<xref:System.Windows.Controls.Primitives.ToggleButton>控件沒有任何命名部件。</span><span class="sxs-lookup"><span data-stu-id="e6147-107">The <xref:System.Windows.Controls.Primitives.ToggleButton> control does not have any named parts.</span></span>

## <a name="togglebutton-states"></a><span data-ttu-id="e6147-108">切換按鈕狀態</span><span class="sxs-lookup"><span data-stu-id="e6147-108">ToggleButton States</span></span>

<span data-ttu-id="e6147-109">下表列出了控件的<xref:System.Windows.Controls.Primitives.ToggleButton>可視狀態。</span><span class="sxs-lookup"><span data-stu-id="e6147-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

|<span data-ttu-id="e6147-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="e6147-110">VisualState Name</span></span>|<span data-ttu-id="e6147-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="e6147-111">VisualStateGroup Name</span></span>|<span data-ttu-id="e6147-112">描述</span><span class="sxs-lookup"><span data-stu-id="e6147-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="e6147-113">正常</span><span class="sxs-lookup"><span data-stu-id="e6147-113">Normal</span></span>|<span data-ttu-id="e6147-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e6147-114">CommonStates</span></span>|<span data-ttu-id="e6147-115">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="e6147-115">The default state.</span></span>|
|<span data-ttu-id="e6147-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="e6147-116">MouseOver</span></span>|<span data-ttu-id="e6147-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e6147-117">CommonStates</span></span>|<span data-ttu-id="e6147-118">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="e6147-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="e6147-119">按下</span><span class="sxs-lookup"><span data-stu-id="e6147-119">Pressed</span></span>|<span data-ttu-id="e6147-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e6147-120">CommonStates</span></span>|<span data-ttu-id="e6147-121">已按下控制項。</span><span class="sxs-lookup"><span data-stu-id="e6147-121">The control is pressed.</span></span>|
|<span data-ttu-id="e6147-122">已停用</span><span class="sxs-lookup"><span data-stu-id="e6147-122">Disabled</span></span>|<span data-ttu-id="e6147-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e6147-123">CommonStates</span></span>|<span data-ttu-id="e6147-124">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="e6147-124">The control is disabled.</span></span>|
|<span data-ttu-id="e6147-125">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="e6147-125">Focused</span></span>|<span data-ttu-id="e6147-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="e6147-126">FocusStates</span></span>|<span data-ttu-id="e6147-127">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="e6147-127">The control has focus.</span></span>|
|<span data-ttu-id="e6147-128">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="e6147-128">Unfocused</span></span>|<span data-ttu-id="e6147-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="e6147-129">FocusStates</span></span>|<span data-ttu-id="e6147-130">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="e6147-130">The control does not have focus.</span></span>|
|<span data-ttu-id="e6147-131">已檢查</span><span class="sxs-lookup"><span data-stu-id="e6147-131">Checked</span></span>|<span data-ttu-id="e6147-132">檢查狀態</span><span class="sxs-lookup"><span data-stu-id="e6147-132">CheckStates</span></span>|<span data-ttu-id="e6147-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 為 `true`。</span><span class="sxs-lookup"><span data-stu-id="e6147-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|
|<span data-ttu-id="e6147-134">未核取</span><span class="sxs-lookup"><span data-stu-id="e6147-134">Unchecked</span></span>|<span data-ttu-id="e6147-135">檢查狀態</span><span class="sxs-lookup"><span data-stu-id="e6147-135">CheckStates</span></span>|<span data-ttu-id="e6147-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 為 `false`。</span><span class="sxs-lookup"><span data-stu-id="e6147-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|
|<span data-ttu-id="e6147-137">定</span><span class="sxs-lookup"><span data-stu-id="e6147-137">Indeterminate</span></span>|<span data-ttu-id="e6147-138">檢查狀態</span><span class="sxs-lookup"><span data-stu-id="e6147-138">CheckStates</span></span>|<span data-ttu-id="e6147-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> 為 `true`，而 <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 為 `null`。</span><span class="sxs-lookup"><span data-stu-id="e6147-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|
|<span data-ttu-id="e6147-140">有效</span><span class="sxs-lookup"><span data-stu-id="e6147-140">Valid</span></span>|<span data-ttu-id="e6147-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e6147-141">ValidationStates</span></span>|<span data-ttu-id="e6147-142">控制項使用<xref:System.Windows.Controls.Validation>類別<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>, 附加`false`屬性為 。</span><span class="sxs-lookup"><span data-stu-id="e6147-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="e6147-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="e6147-143">InvalidFocused</span></span>|<span data-ttu-id="e6147-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e6147-144">ValidationStates</span></span>|<span data-ttu-id="e6147-145">附加<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>屬性`true`是 ,控件具有焦點。</span><span class="sxs-lookup"><span data-stu-id="e6147-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|
|<span data-ttu-id="e6147-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="e6147-146">InvalidUnfocused</span></span>|<span data-ttu-id="e6147-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e6147-147">ValidationStates</span></span>|<span data-ttu-id="e6147-148">附加<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>屬性`true`為 ,控件沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="e6147-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|

> [!NOTE]
> <span data-ttu-id="e6147-149">如果控件範本中不存在不確定的可視狀態,則"未選中的可視狀態"將用作預設可視狀態。</span><span class="sxs-lookup"><span data-stu-id="e6147-149">If the Indeterminate visual state does not exist in your control template, then the Unchecked visual state will be used as default visual state.</span></span>

## <a name="togglebutton-controltemplate-example"></a><span data-ttu-id="e6147-150">切換按鈕控制樣本範例</span><span class="sxs-lookup"><span data-stu-id="e6147-150">ToggleButton ControlTemplate Example</span></span>

<span data-ttu-id="e6147-151">下面的範例展示如何為<xref:System.Windows.Controls.ControlTemplate><xref:System.Windows.Controls.Primitives.ToggleButton>控制項定義 。</span><span class="sxs-lookup"><span data-stu-id="e6147-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

[!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]

<span data-ttu-id="e6147-152">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="e6147-152">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="e6147-153">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="e6147-153">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="e6147-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6147-154">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="e6147-155">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="e6147-155">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="e6147-156">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="e6147-156">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="e6147-157">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="e6147-157">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="e6147-158">為控制項建立樣本</span><span class="sxs-lookup"><span data-stu-id="e6147-158">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
