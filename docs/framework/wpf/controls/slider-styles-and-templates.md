---
title: Slider 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], Slider
- states [WPF], Slider
- Slider [WPF], styles and templates
- styles [WPF], Slider
- templates [WPF], Slider
- ControlTemplate [WPF], Slider
ms.assetid: d89aa97b-075a-4752-9c41-9679df65c491
ms.openlocfilehash: 334cb4a44788980262110eadac3305283bb61a92
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458399"
---
# <a name="slider-styles-and-templates"></a><span data-ttu-id="fd565-102">Slider 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="fd565-102">Slider Styles and Templates</span></span>
<span data-ttu-id="fd565-103">本主題描述 <xref:System.Windows.Controls.Slider> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="fd565-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Slider> control.</span></span> <span data-ttu-id="fd565-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="fd565-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="fd565-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="fd565-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="slider-parts"></a><span data-ttu-id="fd565-106">滑杆元件</span><span class="sxs-lookup"><span data-stu-id="fd565-106">Slider Parts</span></span>  
 <span data-ttu-id="fd565-107">下表列出 <xref:System.Windows.Controls.Slider> 控制項的已命名元件。</span><span class="sxs-lookup"><span data-stu-id="fd565-107">The following table lists the named parts for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="fd565-108">組件</span><span class="sxs-lookup"><span data-stu-id="fd565-108">Part</span></span>|<span data-ttu-id="fd565-109">輸入</span><span class="sxs-lookup"><span data-stu-id="fd565-109">Type</span></span>|<span data-ttu-id="fd565-110">描述</span><span class="sxs-lookup"><span data-stu-id="fd565-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="fd565-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="fd565-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="fd565-112">元素的容器，表示 <xref:System.Windows.Controls.Slider>的位置。</span><span class="sxs-lookup"><span data-stu-id="fd565-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Slider>.</span></span>|  
|<span data-ttu-id="fd565-113">PART_SelectionRange</span><span class="sxs-lookup"><span data-stu-id="fd565-113">PART_SelectionRange</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="fd565-114">沿著 <xref:System.Windows.Controls.Slider>顯示選取範圍的元素。</span><span class="sxs-lookup"><span data-stu-id="fd565-114">The element that displays a selection range along the <xref:System.Windows.Controls.Slider>.</span></span>  <span data-ttu-id="fd565-115">只有在 `true`<xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> 屬性時，才會顯示選取範圍。</span><span class="sxs-lookup"><span data-stu-id="fd565-115">The selection range is visible only if the <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> property is `true`.</span></span>|  
  
## <a name="slider-states"></a><span data-ttu-id="fd565-116">滑杆狀態</span><span class="sxs-lookup"><span data-stu-id="fd565-116">Slider States</span></span>  
 <span data-ttu-id="fd565-117">下表列出 <xref:System.Windows.Controls.Slider> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="fd565-117">The following table lists the visual states for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="fd565-118">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="fd565-118">VisualState Name</span></span>|<span data-ttu-id="fd565-119">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="fd565-119">VisualStateGroup Name</span></span>|<span data-ttu-id="fd565-120">描述</span><span class="sxs-lookup"><span data-stu-id="fd565-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="fd565-121">一般</span><span class="sxs-lookup"><span data-stu-id="fd565-121">Normal</span></span>|<span data-ttu-id="fd565-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="fd565-122">CommonStates</span></span>|<span data-ttu-id="fd565-123">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="fd565-123">The default state.</span></span>|  
|<span data-ttu-id="fd565-124">MouseOver</span><span class="sxs-lookup"><span data-stu-id="fd565-124">MouseOver</span></span>|<span data-ttu-id="fd565-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="fd565-125">CommonStates</span></span>|<span data-ttu-id="fd565-126">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="fd565-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="fd565-127">Disabled</span><span class="sxs-lookup"><span data-stu-id="fd565-127">Disabled</span></span>|<span data-ttu-id="fd565-128">CommonStates</span><span class="sxs-lookup"><span data-stu-id="fd565-128">CommonStates</span></span>|<span data-ttu-id="fd565-129">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="fd565-129">The control is disabled.</span></span>|  
|<span data-ttu-id="fd565-130">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="fd565-130">Focused</span></span>|<span data-ttu-id="fd565-131">FocusStates</span><span class="sxs-lookup"><span data-stu-id="fd565-131">FocusStates</span></span>|<span data-ttu-id="fd565-132">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="fd565-132">The control has focus.</span></span>|  
|<span data-ttu-id="fd565-133">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="fd565-133">Unfocused</span></span>|<span data-ttu-id="fd565-134">FocusStates</span><span class="sxs-lookup"><span data-stu-id="fd565-134">FocusStates</span></span>|<span data-ttu-id="fd565-135">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="fd565-135">The control does not have focus.</span></span>|  
|<span data-ttu-id="fd565-136">驗證</span><span class="sxs-lookup"><span data-stu-id="fd565-136">Valid</span></span>|<span data-ttu-id="fd565-137">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fd565-137">ValidationStates</span></span>|<span data-ttu-id="fd565-138">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="fd565-138">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="fd565-139">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="fd565-139">InvalidFocused</span></span>|<span data-ttu-id="fd565-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fd565-140">ValidationStates</span></span>|<span data-ttu-id="fd565-141"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="fd565-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="fd565-142">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="fd565-142">InvalidUnfocused</span></span>|<span data-ttu-id="fd565-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fd565-143">ValidationStates</span></span>|<span data-ttu-id="fd565-144"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="fd565-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="slider-controltemplate-example"></a><span data-ttu-id="fd565-145">滑杆 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="fd565-145">Slider ControlTemplate Example</span></span>  
 <span data-ttu-id="fd565-146">下列範例顯示如何定義 <xref:System.Windows.Controls.Slider> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="fd565-146">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Slider](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#slider)]  
  
 <span data-ttu-id="fd565-147">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="fd565-147">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="fd565-148">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="fd565-148">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd565-149">請參閱</span><span class="sxs-lookup"><span data-stu-id="fd565-149">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="fd565-150">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="fd565-150">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="fd565-151">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="fd565-151">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="fd565-152">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="fd565-152">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="fd565-153">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="fd565-153">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
