---
title: PasswordBox 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], PasswordBox
- templates [WPF], PasswordBox
- ControlTemplate [WPF], PasswordBox
- states [WPF], PasswordBox
- PasswordBox [WPF], styles and templates
- parts [WPF], PasswordBox
ms.assetid: deb52107-959f-4a60-b303-d21a0a933060
ms.openlocfilehash: 227ccbda8d570868258508935a5d95f0f40663ab
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458834"
---
# <a name="passwordbox-styles-and-templates"></a><span data-ttu-id="f3bfe-102">PasswordBox 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="f3bfe-102">PasswordBox Styles and Templates</span></span>

<span data-ttu-id="f3bfe-103">本主題描述 <xref:System.Windows.Controls.PasswordBox> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.PasswordBox> control.</span></span> <span data-ttu-id="f3bfe-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="f3bfe-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>

## <a name="passwordbox-parts"></a><span data-ttu-id="f3bfe-106">PasswordBox 元件</span><span class="sxs-lookup"><span data-stu-id="f3bfe-106">PasswordBox Parts</span></span>

<span data-ttu-id="f3bfe-107">下表列出 <xref:System.Windows.Controls.PasswordBox> 控制項的已命名元件。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-107">The following table lists the named parts for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

|<span data-ttu-id="f3bfe-108">組件</span><span class="sxs-lookup"><span data-stu-id="f3bfe-108">Part</span></span>|<span data-ttu-id="f3bfe-109">輸入</span><span class="sxs-lookup"><span data-stu-id="f3bfe-109">Type</span></span>|<span data-ttu-id="f3bfe-110">描述</span><span class="sxs-lookup"><span data-stu-id="f3bfe-110">Description</span></span>|
|-|-|-|
|<span data-ttu-id="f3bfe-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="f3bfe-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="f3bfe-112">可以包含 <xref:System.Windows.FrameworkElement>的視覺元素。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="f3bfe-113"><xref:System.Windows.Controls.PasswordBox> 的文字會顯示在此元素中。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-113">The text of the <xref:System.Windows.Controls.PasswordBox> is displayed in this element.</span></span>|

## <a name="passwordbox-states"></a><span data-ttu-id="f3bfe-114">PasswordBox 狀態</span><span class="sxs-lookup"><span data-stu-id="f3bfe-114">PasswordBox States</span></span>

<span data-ttu-id="f3bfe-115">下表列出 <xref:System.Windows.Controls.PasswordBox> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-115">The following table lists the visual states for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

|<span data-ttu-id="f3bfe-116">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="f3bfe-116">VisualState Name</span></span>|<span data-ttu-id="f3bfe-117">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="f3bfe-117">VisualStateGroup Name</span></span>|<span data-ttu-id="f3bfe-118">描述</span><span class="sxs-lookup"><span data-stu-id="f3bfe-118">Description</span></span>|
|-|-|-|
|<span data-ttu-id="f3bfe-119">一般</span><span class="sxs-lookup"><span data-stu-id="f3bfe-119">Normal</span></span>|<span data-ttu-id="f3bfe-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f3bfe-120">CommonStates</span></span>|<span data-ttu-id="f3bfe-121">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-121">The default state.</span></span>|
|<span data-ttu-id="f3bfe-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="f3bfe-122">MouseOver</span></span>|<span data-ttu-id="f3bfe-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f3bfe-123">CommonStates</span></span>|<span data-ttu-id="f3bfe-124">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-124">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="f3bfe-125">Disabled</span><span class="sxs-lookup"><span data-stu-id="f3bfe-125">Disabled</span></span>|<span data-ttu-id="f3bfe-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f3bfe-126">CommonStates</span></span>|<span data-ttu-id="f3bfe-127">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-127">The control is disabled.</span></span>|
|<span data-ttu-id="f3bfe-128">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="f3bfe-128">Focused</span></span>|<span data-ttu-id="f3bfe-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="f3bfe-129">FocusStates</span></span>|<span data-ttu-id="f3bfe-130">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-130">The control has focus.</span></span>|
|<span data-ttu-id="f3bfe-131">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="f3bfe-131">Unfocused</span></span>|<span data-ttu-id="f3bfe-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="f3bfe-132">FocusStates</span></span>|<span data-ttu-id="f3bfe-133">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-133">The control does not have focus.</span></span>|
|<span data-ttu-id="f3bfe-134">驗證</span><span class="sxs-lookup"><span data-stu-id="f3bfe-134">Valid</span></span>|<span data-ttu-id="f3bfe-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f3bfe-135">ValidationStates</span></span>|<span data-ttu-id="f3bfe-136">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-136">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="f3bfe-137">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="f3bfe-137">InvalidFocused</span></span>|<span data-ttu-id="f3bfe-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f3bfe-138">ValidationStates</span></span>|<span data-ttu-id="f3bfe-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="f3bfe-140">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="f3bfe-140">InvalidUnfocused</span></span>|<span data-ttu-id="f3bfe-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f3bfe-141">ValidationStates</span></span>|<span data-ttu-id="f3bfe-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="passwordbox-controltemplate-example"></a><span data-ttu-id="f3bfe-143">PasswordBox ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="f3bfe-143">PasswordBox ControlTemplate Example</span></span>

<span data-ttu-id="f3bfe-144">下列範例顯示如何定義 <xref:System.Windows.Controls.PasswordBox> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-144">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

[!code-xaml[ControlTemplateExamples#PasswordBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]

<span data-ttu-id="f3bfe-145">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-145">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="f3bfe-146">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-146">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="f3bfe-147">請參閱</span><span class="sxs-lookup"><span data-stu-id="f3bfe-147">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="f3bfe-148">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="f3bfe-148">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="f3bfe-149">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="f3bfe-149">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="f3bfe-150">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="f3bfe-150">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="f3bfe-151">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="f3bfe-151">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
