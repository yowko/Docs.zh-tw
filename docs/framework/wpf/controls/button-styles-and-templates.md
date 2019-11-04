---
title: Button 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Button
- parts [WPF], Button
- styles [WPF], Button
- Button [WPF], styles and templates
- templates [WPF], Button
- ControlTemplate [WPF], Button
ms.assetid: e223c759-f8c4-4717-acfb-b1e40bdf5f3b
ms.openlocfilehash: 64764d43191d30c191c5d6519982b16cfc86d26e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460950"
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="0f9e5-102">Button 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="0f9e5-102">Button Styles and Templates</span></span>
<span data-ttu-id="0f9e5-103">本主題描述 <xref:System.Windows.Controls.Button> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="0f9e5-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="0f9e5-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="0f9e5-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="0f9e5-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="0f9e5-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="0f9e5-106">按鈕部分</span><span class="sxs-lookup"><span data-stu-id="0f9e5-106">Button Parts</span></span>  
 <span data-ttu-id="0f9e5-107"><xref:System.Windows.Controls.Button> 控制項沒有任何已命名的元件。</span><span class="sxs-lookup"><span data-stu-id="0f9e5-107">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="0f9e5-108">按鈕狀態</span><span class="sxs-lookup"><span data-stu-id="0f9e5-108">Button States</span></span>  
 <span data-ttu-id="0f9e5-109">下表列出 <xref:System.Windows.Controls.Button> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="0f9e5-109">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="0f9e5-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="0f9e5-110">VisualState Name</span></span>|<span data-ttu-id="0f9e5-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="0f9e5-111">VisualStateGroup Name</span></span>|<span data-ttu-id="0f9e5-112">描述</span><span class="sxs-lookup"><span data-stu-id="0f9e5-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="0f9e5-113">一般</span><span class="sxs-lookup"><span data-stu-id="0f9e5-113">Normal</span></span>|<span data-ttu-id="0f9e5-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="0f9e5-114">CommonStates</span></span>|<span data-ttu-id="0f9e5-115">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="0f9e5-115">The default state.</span></span>|  
|<span data-ttu-id="0f9e5-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="0f9e5-116">MouseOver</span></span>|<span data-ttu-id="0f9e5-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="0f9e5-117">CommonStates</span></span>|<span data-ttu-id="0f9e5-118">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="0f9e5-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="0f9e5-119">按下</span><span class="sxs-lookup"><span data-stu-id="0f9e5-119">Pressed</span></span>|<span data-ttu-id="0f9e5-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="0f9e5-120">CommonStates</span></span>|<span data-ttu-id="0f9e5-121">已按下控制項。</span><span class="sxs-lookup"><span data-stu-id="0f9e5-121">The control is pressed.</span></span>|  
|<span data-ttu-id="0f9e5-122">Disabled</span><span class="sxs-lookup"><span data-stu-id="0f9e5-122">Disabled</span></span>|<span data-ttu-id="0f9e5-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="0f9e5-123">CommonStates</span></span>|<span data-ttu-id="0f9e5-124">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="0f9e5-124">The control is disabled.</span></span>|  
|<span data-ttu-id="0f9e5-125">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="0f9e5-125">Focused</span></span>|<span data-ttu-id="0f9e5-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="0f9e5-126">FocusStates</span></span>|<span data-ttu-id="0f9e5-127">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="0f9e5-127">The control has focus.</span></span>|  
|<span data-ttu-id="0f9e5-128">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="0f9e5-128">Unfocused</span></span>|<span data-ttu-id="0f9e5-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="0f9e5-129">FocusStates</span></span>|<span data-ttu-id="0f9e5-130">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="0f9e5-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="0f9e5-131">驗證</span><span class="sxs-lookup"><span data-stu-id="0f9e5-131">Valid</span></span>|<span data-ttu-id="0f9e5-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0f9e5-132">ValidationStates</span></span>|<span data-ttu-id="0f9e5-133">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="0f9e5-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="0f9e5-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="0f9e5-134">InvalidFocused</span></span>|<span data-ttu-id="0f9e5-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0f9e5-135">ValidationStates</span></span>|<span data-ttu-id="0f9e5-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性 `true`，且控制項具有焦點。</span><span class="sxs-lookup"><span data-stu-id="0f9e5-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="0f9e5-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="0f9e5-137">InvalidUnfocused</span></span>|<span data-ttu-id="0f9e5-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0f9e5-138">ValidationStates</span></span>|<span data-ttu-id="0f9e5-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性 `true`，而且控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="0f9e5-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="0f9e5-140">按鈕 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="0f9e5-140">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="0f9e5-141">下列範例顯示如何定義 <xref:System.Windows.Controls.Button> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="0f9e5-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="0f9e5-142">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="0f9e5-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="0f9e5-143">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="0f9e5-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f9e5-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="0f9e5-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="0f9e5-145">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="0f9e5-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="0f9e5-146">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="0f9e5-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="0f9e5-147">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="0f9e5-147">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="0f9e5-148">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="0f9e5-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
