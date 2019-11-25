---
title: RepeatButton 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatButton [WPF], styles and templates
- styles [WPF], RepeatButton
- templates [WPF], RepeatButton
- parts [WPF], RepeatButton
- ControlTemplate [WPF], RepeatButton
- states [WPF], RepeatButton
ms.assetid: fd340743-f44f-4990-9077-085301469670
ms.openlocfilehash: 8585e98536fd908daa11f21da395cab44924d612
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283419"
---
# <a name="repeatbutton-styles-and-templates"></a><span data-ttu-id="fbf21-102">RepeatButton 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="fbf21-102">RepeatButton Styles and Templates</span></span>

<span data-ttu-id="fbf21-103">本主題描述 <xref:System.Windows.Controls.Primitives.RepeatButton> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="fbf21-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span> <span data-ttu-id="fbf21-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="fbf21-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="fbf21-105">如需詳細資訊，請參閱[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。</span><span class="sxs-lookup"><span data-stu-id="fbf21-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>

## <a name="repeatbutton-parts"></a><span data-ttu-id="fbf21-106">RepeatButton 元件</span><span class="sxs-lookup"><span data-stu-id="fbf21-106">RepeatButton Parts</span></span>

<span data-ttu-id="fbf21-107"><xref:System.Windows.Controls.Primitives.RepeatButton> 控制項沒有任何已命名的元件。</span><span class="sxs-lookup"><span data-stu-id="fbf21-107">The <xref:System.Windows.Controls.Primitives.RepeatButton> control does not have any named parts.</span></span>

## <a name="repeatbutton-states"></a><span data-ttu-id="fbf21-108">RepeatButton 狀態</span><span class="sxs-lookup"><span data-stu-id="fbf21-108">RepeatButton States</span></span>

<span data-ttu-id="fbf21-109">下表列出 <xref:System.Windows.Controls.Primitives.RepeatButton> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="fbf21-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span>

|<span data-ttu-id="fbf21-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="fbf21-110">VisualState Name</span></span>|<span data-ttu-id="fbf21-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="fbf21-111">VisualStateGroup Name</span></span>|<span data-ttu-id="fbf21-112">描述</span><span class="sxs-lookup"><span data-stu-id="fbf21-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="fbf21-113">一般</span><span class="sxs-lookup"><span data-stu-id="fbf21-113">Normal</span></span>|<span data-ttu-id="fbf21-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="fbf21-114">CommonStates</span></span>|<span data-ttu-id="fbf21-115">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="fbf21-115">The default state.</span></span>|
|<span data-ttu-id="fbf21-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="fbf21-116">MouseOver</span></span>|<span data-ttu-id="fbf21-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="fbf21-117">CommonStates</span></span>|<span data-ttu-id="fbf21-118">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="fbf21-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="fbf21-119">按下</span><span class="sxs-lookup"><span data-stu-id="fbf21-119">Pressed</span></span>|<span data-ttu-id="fbf21-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="fbf21-120">CommonStates</span></span>|<span data-ttu-id="fbf21-121">已按下控制項。</span><span class="sxs-lookup"><span data-stu-id="fbf21-121">The control is pressed.</span></span>|
|<span data-ttu-id="fbf21-122">已停用</span><span class="sxs-lookup"><span data-stu-id="fbf21-122">Disabled</span></span>|<span data-ttu-id="fbf21-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="fbf21-123">CommonStates</span></span>|<span data-ttu-id="fbf21-124">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="fbf21-124">The control is disabled.</span></span>|
|<span data-ttu-id="fbf21-125">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="fbf21-125">Focused</span></span>|<span data-ttu-id="fbf21-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="fbf21-126">FocusStates</span></span>|<span data-ttu-id="fbf21-127">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="fbf21-127">The control has focus.</span></span>|
|<span data-ttu-id="fbf21-128">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="fbf21-128">Unfocused</span></span>|<span data-ttu-id="fbf21-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="fbf21-129">FocusStates</span></span>|<span data-ttu-id="fbf21-130">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="fbf21-130">The control does not have focus.</span></span>|
|<span data-ttu-id="fbf21-131">驗證</span><span class="sxs-lookup"><span data-stu-id="fbf21-131">Valid</span></span>|<span data-ttu-id="fbf21-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fbf21-132">ValidationStates</span></span>|<span data-ttu-id="fbf21-133">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="fbf21-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="fbf21-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="fbf21-134">InvalidFocused</span></span>|<span data-ttu-id="fbf21-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fbf21-135">ValidationStates</span></span>|<span data-ttu-id="fbf21-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="fbf21-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="fbf21-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="fbf21-137">InvalidUnfocused</span></span>|<span data-ttu-id="fbf21-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fbf21-138">ValidationStates</span></span>|<span data-ttu-id="fbf21-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="fbf21-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="repeatbutton-controltemplate-example"></a><span data-ttu-id="fbf21-140">RepeatButton ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="fbf21-140">RepeatButton ControlTemplate Example</span></span>

<span data-ttu-id="fbf21-141">下列範例顯示如何定義 <xref:System.Windows.Controls.Primitives.RepeatButton> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="fbf21-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span>

[!code-xaml[ControlTemplateExamples#RepeatButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#repeatbutton)]

<span data-ttu-id="fbf21-142">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="fbf21-142">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="fbf21-143">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="fbf21-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="fbf21-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="fbf21-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="fbf21-145">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="fbf21-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="fbf21-146">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="fbf21-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="fbf21-147">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="fbf21-147">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="fbf21-148">建立控制項的範本</span><span class="sxs-lookup"><span data-stu-id="fbf21-148">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
