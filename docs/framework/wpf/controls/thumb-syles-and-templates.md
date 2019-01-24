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
ms.openlocfilehash: e987932e00be09fdf5ac34bb2bfb24a890368a15
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596380"
---
# <a name="thumb-syles-and-templates"></a><span data-ttu-id="7a1a6-102">Thumb 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="7a1a6-102">Thumb Syles and Templates</span></span>
<span data-ttu-id="7a1a6-103">本主題描述的樣式和範本<xref:System.Windows.Controls.Primitives.Thumb>控制項。</span><span class="sxs-lookup"><span data-stu-id="7a1a6-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="7a1a6-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>，讓控制項的獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="7a1a6-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="7a1a6-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="7a1a6-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="thumb-parts"></a><span data-ttu-id="7a1a6-106">捲動方塊的組件</span><span class="sxs-lookup"><span data-stu-id="7a1a6-106">Thumb Parts</span></span>  
 <span data-ttu-id="7a1a6-107"><xref:System.Windows.Controls.Primitives.Thumb>控制項沒有任何具名組件。</span><span class="sxs-lookup"><span data-stu-id="7a1a6-107">The <xref:System.Windows.Controls.Primitives.Thumb> control does not have any named parts.</span></span>  
  
## <a name="thumb-states"></a><span data-ttu-id="7a1a6-108">捲動方塊的狀態</span><span class="sxs-lookup"><span data-stu-id="7a1a6-108">Thumb States</span></span>  
 <span data-ttu-id="7a1a6-109">下表列出的視覺狀態<xref:System.Windows.Controls.Primitives.Thumb>控制項。</span><span class="sxs-lookup"><span data-stu-id="7a1a6-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
|<span data-ttu-id="7a1a6-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="7a1a6-110">VisualState Name</span></span>|<span data-ttu-id="7a1a6-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="7a1a6-111">VisualStateGroup Name</span></span>|<span data-ttu-id="7a1a6-112">描述</span><span class="sxs-lookup"><span data-stu-id="7a1a6-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="7a1a6-113">一般</span><span class="sxs-lookup"><span data-stu-id="7a1a6-113">Normal</span></span>|<span data-ttu-id="7a1a6-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7a1a6-114">CommonStates</span></span>|<span data-ttu-id="7a1a6-115">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="7a1a6-115">The default state.</span></span>|  
|<span data-ttu-id="7a1a6-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="7a1a6-116">MouseOver</span></span>|<span data-ttu-id="7a1a6-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7a1a6-117">CommonStates</span></span>|<span data-ttu-id="7a1a6-118">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="7a1a6-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="7a1a6-119">按下</span><span class="sxs-lookup"><span data-stu-id="7a1a6-119">Pressed</span></span>|<span data-ttu-id="7a1a6-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7a1a6-120">CommonStates</span></span>|<span data-ttu-id="7a1a6-121">已按下控制項。</span><span class="sxs-lookup"><span data-stu-id="7a1a6-121">The control is pressed.</span></span>|  
|<span data-ttu-id="7a1a6-122">已停用</span><span class="sxs-lookup"><span data-stu-id="7a1a6-122">Disabled</span></span>|<span data-ttu-id="7a1a6-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7a1a6-123">CommonStates</span></span>|<span data-ttu-id="7a1a6-124">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="7a1a6-124">The control is disabled.</span></span>|  
|<span data-ttu-id="7a1a6-125">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="7a1a6-125">Focused</span></span>|<span data-ttu-id="7a1a6-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="7a1a6-126">FocusStates</span></span>|<span data-ttu-id="7a1a6-127">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="7a1a6-127">The control has focus.</span></span>|  
|<span data-ttu-id="7a1a6-128">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="7a1a6-128">Unfocused</span></span>|<span data-ttu-id="7a1a6-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="7a1a6-129">FocusStates</span></span>|<span data-ttu-id="7a1a6-130">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="7a1a6-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="7a1a6-131">驗證</span><span class="sxs-lookup"><span data-stu-id="7a1a6-131">Valid</span></span>|<span data-ttu-id="7a1a6-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7a1a6-132">ValidationStates</span></span>|<span data-ttu-id="7a1a6-133">控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。</span><span class="sxs-lookup"><span data-stu-id="7a1a6-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="7a1a6-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="7a1a6-134">InvalidFocused</span></span>|<span data-ttu-id="7a1a6-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7a1a6-135">ValidationStates</span></span>|<span data-ttu-id="7a1a6-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。</span><span class="sxs-lookup"><span data-stu-id="7a1a6-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="7a1a6-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="7a1a6-137">InvalidUnfocused</span></span>|<span data-ttu-id="7a1a6-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7a1a6-138">ValidationStates</span></span>|<span data-ttu-id="7a1a6-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="7a1a6-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="thumb-controltemplate-example"></a><span data-ttu-id="7a1a6-140">Thumb ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="7a1a6-140">Thumb ControlTemplate Example</span></span>  
 <span data-ttu-id="7a1a6-141">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.Primitives.Thumb>控制項。</span><span class="sxs-lookup"><span data-stu-id="7a1a6-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]  
  
 <span data-ttu-id="7a1a6-142">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="7a1a6-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="7a1a6-143">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="7a1a6-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a1a6-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a1a6-144">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="7a1a6-145">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="7a1a6-145">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [<span data-ttu-id="7a1a6-146">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="7a1a6-146">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)
- [<span data-ttu-id="7a1a6-147">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="7a1a6-147">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="7a1a6-148">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="7a1a6-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
