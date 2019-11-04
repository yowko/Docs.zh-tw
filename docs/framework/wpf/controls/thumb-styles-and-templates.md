---
title: Thumb 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Thumb
- styles [WPF], Thumb
- templates [WPF], Thumb
- Thumb [WPF], styles and templates
- ControlTemplate [WPF], Thumb
- parts [WPF], Thumb
ms.assetid: 86a49235-62d9-414e-923e-53126e3f930a
ms.openlocfilehash: c2114a02016db96d898a394b6892b6d3042d81ff
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458232"
---
# <a name="thumb-styles-and-templates"></a><span data-ttu-id="90e73-102">Thumb 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="90e73-102">Thumb Styles and Templates</span></span>

<span data-ttu-id="90e73-103">本主題描述 <xref:System.Windows.Controls.Primitives.Thumb> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="90e73-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="90e73-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="90e73-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="90e73-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="90e73-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>

## <a name="thumb-parts"></a><span data-ttu-id="90e73-106">Thumb 部分</span><span class="sxs-lookup"><span data-stu-id="90e73-106">Thumb Parts</span></span>

<span data-ttu-id="90e73-107"><xref:System.Windows.Controls.Primitives.Thumb> 控制項沒有任何已命名的元件。</span><span class="sxs-lookup"><span data-stu-id="90e73-107">The <xref:System.Windows.Controls.Primitives.Thumb> control does not have any named parts.</span></span>

## <a name="thumb-states"></a><span data-ttu-id="90e73-108">Thumb 狀態</span><span class="sxs-lookup"><span data-stu-id="90e73-108">Thumb States</span></span>

<span data-ttu-id="90e73-109">下表列出 <xref:System.Windows.Controls.Primitives.Thumb> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="90e73-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>

|<span data-ttu-id="90e73-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="90e73-110">VisualState Name</span></span>|<span data-ttu-id="90e73-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="90e73-111">VisualStateGroup Name</span></span>|<span data-ttu-id="90e73-112">描述</span><span class="sxs-lookup"><span data-stu-id="90e73-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="90e73-113">一般</span><span class="sxs-lookup"><span data-stu-id="90e73-113">Normal</span></span>|<span data-ttu-id="90e73-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="90e73-114">CommonStates</span></span>|<span data-ttu-id="90e73-115">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="90e73-115">The default state.</span></span>|
|<span data-ttu-id="90e73-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="90e73-116">MouseOver</span></span>|<span data-ttu-id="90e73-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="90e73-117">CommonStates</span></span>|<span data-ttu-id="90e73-118">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="90e73-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="90e73-119">按下</span><span class="sxs-lookup"><span data-stu-id="90e73-119">Pressed</span></span>|<span data-ttu-id="90e73-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="90e73-120">CommonStates</span></span>|<span data-ttu-id="90e73-121">已按下控制項。</span><span class="sxs-lookup"><span data-stu-id="90e73-121">The control is pressed.</span></span>|
|<span data-ttu-id="90e73-122">Disabled</span><span class="sxs-lookup"><span data-stu-id="90e73-122">Disabled</span></span>|<span data-ttu-id="90e73-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="90e73-123">CommonStates</span></span>|<span data-ttu-id="90e73-124">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="90e73-124">The control is disabled.</span></span>|
|<span data-ttu-id="90e73-125">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="90e73-125">Focused</span></span>|<span data-ttu-id="90e73-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="90e73-126">FocusStates</span></span>|<span data-ttu-id="90e73-127">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="90e73-127">The control has focus.</span></span>|
|<span data-ttu-id="90e73-128">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="90e73-128">Unfocused</span></span>|<span data-ttu-id="90e73-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="90e73-129">FocusStates</span></span>|<span data-ttu-id="90e73-130">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="90e73-130">The control does not have focus.</span></span>|
|<span data-ttu-id="90e73-131">驗證</span><span class="sxs-lookup"><span data-stu-id="90e73-131">Valid</span></span>|<span data-ttu-id="90e73-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="90e73-132">ValidationStates</span></span>|<span data-ttu-id="90e73-133">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="90e73-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="90e73-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="90e73-134">InvalidFocused</span></span>|<span data-ttu-id="90e73-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="90e73-135">ValidationStates</span></span>|<span data-ttu-id="90e73-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="90e73-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="90e73-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="90e73-137">InvalidUnfocused</span></span>|<span data-ttu-id="90e73-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="90e73-138">ValidationStates</span></span>|<span data-ttu-id="90e73-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="90e73-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="thumb-controltemplate-example"></a><span data-ttu-id="90e73-140">Thumb ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="90e73-140">Thumb ControlTemplate Example</span></span>

<span data-ttu-id="90e73-141">下列範例顯示如何定義 <xref:System.Windows.Controls.Primitives.Thumb> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="90e73-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>

[!code-xaml[ControlTemplateExamples#Thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]

<span data-ttu-id="90e73-142">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="90e73-142">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="90e73-143">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="90e73-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="90e73-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="90e73-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="90e73-145">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="90e73-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="90e73-146">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="90e73-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="90e73-147">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="90e73-147">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="90e73-148">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="90e73-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
