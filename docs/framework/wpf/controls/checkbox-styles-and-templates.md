---
title: CheckBox 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], CheckBox
- templates [WPF], CheckBox
- parts [WPF], CheckBox
- ControlTemplate [WPF], CheckBox
- CheckBox [WPF], styles and templates
- styles [WPF], CheckBox
ms.assetid: bfdaec96-d101-4d3d-864d-c27e6b621d03
ms.openlocfilehash: b9eee48c01f53e12bbe4a72f84c20eab68d5de23
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283809"
---
# <a name="checkbox-styles-and-templates"></a><span data-ttu-id="bbd68-102">CheckBox 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="bbd68-102">CheckBox Styles and Templates</span></span>
<span data-ttu-id="bbd68-103">本主題描述 <xref:System.Windows.Controls.CheckBox> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="bbd68-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.CheckBox> control.</span></span> <span data-ttu-id="bbd68-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="bbd68-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="bbd68-105">如需詳細資訊，請參閱[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。</span><span class="sxs-lookup"><span data-stu-id="bbd68-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="checkbox-parts"></a><span data-ttu-id="bbd68-106">核取方塊元件</span><span class="sxs-lookup"><span data-stu-id="bbd68-106">CheckBox Parts</span></span>  
 <span data-ttu-id="bbd68-107"><xref:System.Windows.Controls.CheckBox> 控制項沒有任何已命名的元件。</span><span class="sxs-lookup"><span data-stu-id="bbd68-107">The <xref:System.Windows.Controls.CheckBox> control does not have any named parts.</span></span>  
  
## <a name="checkbox-states"></a><span data-ttu-id="bbd68-108">核取方塊狀態</span><span class="sxs-lookup"><span data-stu-id="bbd68-108">CheckBox States</span></span>  
 <span data-ttu-id="bbd68-109">下表列出 <xref:System.Windows.Controls.CheckBox> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="bbd68-109">The following table lists the visual states for the <xref:System.Windows.Controls.CheckBox> control.</span></span>  
  
|<span data-ttu-id="bbd68-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="bbd68-110">VisualState Name</span></span>|<span data-ttu-id="bbd68-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="bbd68-111">VisualStateGroup Name</span></span>|<span data-ttu-id="bbd68-112">描述</span><span class="sxs-lookup"><span data-stu-id="bbd68-112">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="bbd68-113">一般</span><span class="sxs-lookup"><span data-stu-id="bbd68-113">Normal</span></span>|<span data-ttu-id="bbd68-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="bbd68-114">CommonStates</span></span>|<span data-ttu-id="bbd68-115">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="bbd68-115">The default state.</span></span>|  
|<span data-ttu-id="bbd68-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="bbd68-116">MouseOver</span></span>|<span data-ttu-id="bbd68-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="bbd68-117">CommonStates</span></span>|<span data-ttu-id="bbd68-118">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="bbd68-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="bbd68-119">按下</span><span class="sxs-lookup"><span data-stu-id="bbd68-119">Pressed</span></span>|<span data-ttu-id="bbd68-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="bbd68-120">CommonStates</span></span>|<span data-ttu-id="bbd68-121">已按下控制項。</span><span class="sxs-lookup"><span data-stu-id="bbd68-121">The control is pressed.</span></span>|  
|<span data-ttu-id="bbd68-122">已停用</span><span class="sxs-lookup"><span data-stu-id="bbd68-122">Disabled</span></span>|<span data-ttu-id="bbd68-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="bbd68-123">CommonStates</span></span>|<span data-ttu-id="bbd68-124">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="bbd68-124">The control is disabled.</span></span>|  
|<span data-ttu-id="bbd68-125">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="bbd68-125">Focused</span></span>|<span data-ttu-id="bbd68-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="bbd68-126">FocusStates</span></span>|<span data-ttu-id="bbd68-127">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="bbd68-127">The control has focus.</span></span>|  
|<span data-ttu-id="bbd68-128">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="bbd68-128">Unfocused</span></span>|<span data-ttu-id="bbd68-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="bbd68-129">FocusStates</span></span>|<span data-ttu-id="bbd68-130">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="bbd68-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="bbd68-131">已核取</span><span class="sxs-lookup"><span data-stu-id="bbd68-131">Checked</span></span>|<span data-ttu-id="bbd68-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="bbd68-132">CheckStates</span></span>|<span data-ttu-id="bbd68-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 為 `true`。</span><span class="sxs-lookup"><span data-stu-id="bbd68-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|  
|<span data-ttu-id="bbd68-134">選定</span><span class="sxs-lookup"><span data-stu-id="bbd68-134">Unchecked</span></span>|<span data-ttu-id="bbd68-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="bbd68-135">CheckStates</span></span>|<span data-ttu-id="bbd68-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 為 `false`。</span><span class="sxs-lookup"><span data-stu-id="bbd68-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|  
|<span data-ttu-id="bbd68-137">處於</span><span class="sxs-lookup"><span data-stu-id="bbd68-137">Indeterminate</span></span>|<span data-ttu-id="bbd68-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="bbd68-138">CheckStates</span></span>|<span data-ttu-id="bbd68-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> 為 `true`，<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> `null`。</span><span class="sxs-lookup"><span data-stu-id="bbd68-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|  
|<span data-ttu-id="bbd68-140">驗證</span><span class="sxs-lookup"><span data-stu-id="bbd68-140">Valid</span></span>|<span data-ttu-id="bbd68-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="bbd68-141">ValidationStates</span></span>|<span data-ttu-id="bbd68-142">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="bbd68-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="bbd68-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="bbd68-143">InvalidUnfocused</span></span>|<span data-ttu-id="bbd68-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="bbd68-144">ValidationStates</span></span>|<span data-ttu-id="bbd68-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="bbd68-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="bbd68-146">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="bbd68-146">InvalidFocused</span></span>|<span data-ttu-id="bbd68-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="bbd68-147">ValidationStates</span></span>|<span data-ttu-id="bbd68-148"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="bbd68-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="checkbox-controltemplate-example"></a><span data-ttu-id="bbd68-149">CheckBox ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="bbd68-149">CheckBox ControlTemplate Example</span></span>  
 <span data-ttu-id="bbd68-150">下列範例顯示如何定義 <xref:System.Windows.Controls.CheckBox> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="bbd68-150">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.CheckBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#CheckBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/checkbox.xaml#checkbox)]  
  
 <span data-ttu-id="bbd68-151">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="bbd68-151">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="bbd68-152">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="bbd68-152">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbd68-153">請參閱</span><span class="sxs-lookup"><span data-stu-id="bbd68-153">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="bbd68-154">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="bbd68-154">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="bbd68-155">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="bbd68-155">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="bbd68-156">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="bbd68-156">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="bbd68-157">建立控制項的範本</span><span class="sxs-lookup"><span data-stu-id="bbd68-157">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
