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
ms.openlocfilehash: 9c6a8ad0a954d244fb693e25965ab52dda114068
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459844"
---
# <a name="repeatbutton-styles-and-templates"></a><span data-ttu-id="3a0c7-102">RepeatButton 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="3a0c7-102">RepeatButton Styles and Templates</span></span>

<span data-ttu-id="3a0c7-103">本主題描述 <xref:System.Windows.Controls.Primitives.RepeatButton> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="3a0c7-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span> <span data-ttu-id="3a0c7-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="3a0c7-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="3a0c7-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="3a0c7-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>

## <a name="repeatbutton-parts"></a><span data-ttu-id="3a0c7-106">RepeatButton 元件</span><span class="sxs-lookup"><span data-stu-id="3a0c7-106">RepeatButton Parts</span></span>

<span data-ttu-id="3a0c7-107"><xref:System.Windows.Controls.Primitives.RepeatButton> 控制項沒有任何已命名的元件。</span><span class="sxs-lookup"><span data-stu-id="3a0c7-107">The <xref:System.Windows.Controls.Primitives.RepeatButton> control does not have any named parts.</span></span>

## <a name="repeatbutton-states"></a><span data-ttu-id="3a0c7-108">RepeatButton 狀態</span><span class="sxs-lookup"><span data-stu-id="3a0c7-108">RepeatButton States</span></span>

<span data-ttu-id="3a0c7-109">下表列出 <xref:System.Windows.Controls.Primitives.RepeatButton> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="3a0c7-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span>

|<span data-ttu-id="3a0c7-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="3a0c7-110">VisualState Name</span></span>|<span data-ttu-id="3a0c7-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="3a0c7-111">VisualStateGroup Name</span></span>|<span data-ttu-id="3a0c7-112">描述</span><span class="sxs-lookup"><span data-stu-id="3a0c7-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="3a0c7-113">一般</span><span class="sxs-lookup"><span data-stu-id="3a0c7-113">Normal</span></span>|<span data-ttu-id="3a0c7-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="3a0c7-114">CommonStates</span></span>|<span data-ttu-id="3a0c7-115">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="3a0c7-115">The default state.</span></span>|
|<span data-ttu-id="3a0c7-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="3a0c7-116">MouseOver</span></span>|<span data-ttu-id="3a0c7-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="3a0c7-117">CommonStates</span></span>|<span data-ttu-id="3a0c7-118">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="3a0c7-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="3a0c7-119">按下</span><span class="sxs-lookup"><span data-stu-id="3a0c7-119">Pressed</span></span>|<span data-ttu-id="3a0c7-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="3a0c7-120">CommonStates</span></span>|<span data-ttu-id="3a0c7-121">已按下控制項。</span><span class="sxs-lookup"><span data-stu-id="3a0c7-121">The control is pressed.</span></span>|
|<span data-ttu-id="3a0c7-122">Disabled</span><span class="sxs-lookup"><span data-stu-id="3a0c7-122">Disabled</span></span>|<span data-ttu-id="3a0c7-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="3a0c7-123">CommonStates</span></span>|<span data-ttu-id="3a0c7-124">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="3a0c7-124">The control is disabled.</span></span>|
|<span data-ttu-id="3a0c7-125">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="3a0c7-125">Focused</span></span>|<span data-ttu-id="3a0c7-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="3a0c7-126">FocusStates</span></span>|<span data-ttu-id="3a0c7-127">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="3a0c7-127">The control has focus.</span></span>|
|<span data-ttu-id="3a0c7-128">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="3a0c7-128">Unfocused</span></span>|<span data-ttu-id="3a0c7-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="3a0c7-129">FocusStates</span></span>|<span data-ttu-id="3a0c7-130">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="3a0c7-130">The control does not have focus.</span></span>|
|<span data-ttu-id="3a0c7-131">驗證</span><span class="sxs-lookup"><span data-stu-id="3a0c7-131">Valid</span></span>|<span data-ttu-id="3a0c7-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3a0c7-132">ValidationStates</span></span>|<span data-ttu-id="3a0c7-133">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="3a0c7-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="3a0c7-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="3a0c7-134">InvalidFocused</span></span>|<span data-ttu-id="3a0c7-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3a0c7-135">ValidationStates</span></span>|<span data-ttu-id="3a0c7-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="3a0c7-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="3a0c7-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="3a0c7-137">InvalidUnfocused</span></span>|<span data-ttu-id="3a0c7-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3a0c7-138">ValidationStates</span></span>|<span data-ttu-id="3a0c7-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="3a0c7-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="repeatbutton-controltemplate-example"></a><span data-ttu-id="3a0c7-140">RepeatButton ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="3a0c7-140">RepeatButton ControlTemplate Example</span></span>

<span data-ttu-id="3a0c7-141">下列範例顯示如何定義 <xref:System.Windows.Controls.Primitives.RepeatButton> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="3a0c7-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span>

[!code-xaml[ControlTemplateExamples#RepeatButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#repeatbutton)]

<span data-ttu-id="3a0c7-142">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="3a0c7-142">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="3a0c7-143">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="3a0c7-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="3a0c7-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="3a0c7-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="3a0c7-145">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="3a0c7-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="3a0c7-146">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="3a0c7-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="3a0c7-147">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="3a0c7-147">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="3a0c7-148">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="3a0c7-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
