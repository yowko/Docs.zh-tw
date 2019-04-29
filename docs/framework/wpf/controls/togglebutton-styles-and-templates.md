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
ms.openlocfilehash: 46fd7d07c3904ee752ae3f467f65af4b0c031c84
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790750"
---
# <a name="togglebutton-styles-and-templates"></a><span data-ttu-id="c4a22-102">ToggleButton 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="c4a22-102">ToggleButton Styles and Templates</span></span>

<span data-ttu-id="c4a22-103">本主題描述的樣式和範本<xref:System.Windows.Controls.Primitives.ToggleButton>控制項。</span><span class="sxs-lookup"><span data-stu-id="c4a22-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span> <span data-ttu-id="c4a22-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>，讓控制項的獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="c4a22-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="c4a22-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="c4a22-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>

## <a name="togglebutton-parts"></a><span data-ttu-id="c4a22-106">ToggleButton 組件</span><span class="sxs-lookup"><span data-stu-id="c4a22-106">ToggleButton Parts</span></span>

<span data-ttu-id="c4a22-107"><xref:System.Windows.Controls.Primitives.ToggleButton>控制項沒有任何具名組件。</span><span class="sxs-lookup"><span data-stu-id="c4a22-107">The <xref:System.Windows.Controls.Primitives.ToggleButton> control does not have any named parts.</span></span>

## <a name="togglebutton-states"></a><span data-ttu-id="c4a22-108">ToggleButton 狀態</span><span class="sxs-lookup"><span data-stu-id="c4a22-108">ToggleButton States</span></span>

<span data-ttu-id="c4a22-109">下表列出的視覺狀態<xref:System.Windows.Controls.Primitives.ToggleButton>控制項。</span><span class="sxs-lookup"><span data-stu-id="c4a22-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

|<span data-ttu-id="c4a22-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="c4a22-110">VisualState Name</span></span>|<span data-ttu-id="c4a22-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="c4a22-111">VisualStateGroup Name</span></span>|<span data-ttu-id="c4a22-112">描述</span><span class="sxs-lookup"><span data-stu-id="c4a22-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="c4a22-113">一般</span><span class="sxs-lookup"><span data-stu-id="c4a22-113">Normal</span></span>|<span data-ttu-id="c4a22-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c4a22-114">CommonStates</span></span>|<span data-ttu-id="c4a22-115">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="c4a22-115">The default state.</span></span>|
|<span data-ttu-id="c4a22-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="c4a22-116">MouseOver</span></span>|<span data-ttu-id="c4a22-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c4a22-117">CommonStates</span></span>|<span data-ttu-id="c4a22-118">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="c4a22-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="c4a22-119">按下</span><span class="sxs-lookup"><span data-stu-id="c4a22-119">Pressed</span></span>|<span data-ttu-id="c4a22-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c4a22-120">CommonStates</span></span>|<span data-ttu-id="c4a22-121">已按下控制項。</span><span class="sxs-lookup"><span data-stu-id="c4a22-121">The control is pressed.</span></span>|
|<span data-ttu-id="c4a22-122">已停用</span><span class="sxs-lookup"><span data-stu-id="c4a22-122">Disabled</span></span>|<span data-ttu-id="c4a22-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c4a22-123">CommonStates</span></span>|<span data-ttu-id="c4a22-124">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="c4a22-124">The control is disabled.</span></span>|
|<span data-ttu-id="c4a22-125">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="c4a22-125">Focused</span></span>|<span data-ttu-id="c4a22-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="c4a22-126">FocusStates</span></span>|<span data-ttu-id="c4a22-127">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="c4a22-127">The control has focus.</span></span>|
|<span data-ttu-id="c4a22-128">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="c4a22-128">Unfocused</span></span>|<span data-ttu-id="c4a22-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="c4a22-129">FocusStates</span></span>|<span data-ttu-id="c4a22-130">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="c4a22-130">The control does not have focus.</span></span>|
|<span data-ttu-id="c4a22-131">已核取</span><span class="sxs-lookup"><span data-stu-id="c4a22-131">Checked</span></span>|<span data-ttu-id="c4a22-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="c4a22-132">CheckStates</span></span>|<span data-ttu-id="c4a22-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 為 `true`。</span><span class="sxs-lookup"><span data-stu-id="c4a22-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|
|<span data-ttu-id="c4a22-134">未選取</span><span class="sxs-lookup"><span data-stu-id="c4a22-134">Unchecked</span></span>|<span data-ttu-id="c4a22-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="c4a22-135">CheckStates</span></span>|<span data-ttu-id="c4a22-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 為 `false`。</span><span class="sxs-lookup"><span data-stu-id="c4a22-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|
|<span data-ttu-id="c4a22-137">不定</span><span class="sxs-lookup"><span data-stu-id="c4a22-137">Indeterminate</span></span>|<span data-ttu-id="c4a22-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="c4a22-138">CheckStates</span></span>|<span data-ttu-id="c4a22-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> 已`true`，並<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>是`null`。</span><span class="sxs-lookup"><span data-stu-id="c4a22-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|
|<span data-ttu-id="c4a22-140">驗證</span><span class="sxs-lookup"><span data-stu-id="c4a22-140">Valid</span></span>|<span data-ttu-id="c4a22-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c4a22-141">ValidationStates</span></span>|<span data-ttu-id="c4a22-142">控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。</span><span class="sxs-lookup"><span data-stu-id="c4a22-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="c4a22-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="c4a22-143">InvalidFocused</span></span>|<span data-ttu-id="c4a22-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c4a22-144">ValidationStates</span></span>|<span data-ttu-id="c4a22-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。</span><span class="sxs-lookup"><span data-stu-id="c4a22-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="c4a22-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="c4a22-146">InvalidUnfocused</span></span>|<span data-ttu-id="c4a22-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c4a22-147">ValidationStates</span></span>|<span data-ttu-id="c4a22-148"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="c4a22-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

> [!NOTE]
> <span data-ttu-id="c4a22-149">不定的視覺狀態不存在於您的控制項範本中，如果未選取的視覺狀態將會用為預設的可見狀態。</span><span class="sxs-lookup"><span data-stu-id="c4a22-149">If the Indeterminate visual state does not exist in your control template, then the Unchecked visual state will be used as default visual state.</span></span>

## <a name="togglebutton-controltemplate-example"></a><span data-ttu-id="c4a22-150">ToggleButton ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="c4a22-150">ToggleButton ControlTemplate Example</span></span>

<span data-ttu-id="c4a22-151">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.Primitives.ToggleButton>控制項。</span><span class="sxs-lookup"><span data-stu-id="c4a22-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

[!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]

<span data-ttu-id="c4a22-152">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="c4a22-152">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="c4a22-153">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="c4a22-153">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="c4a22-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4a22-154">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="c4a22-155">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="c4a22-155">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="c4a22-156">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="c4a22-156">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="c4a22-157">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="c4a22-157">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="c4a22-158">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="c4a22-158">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
