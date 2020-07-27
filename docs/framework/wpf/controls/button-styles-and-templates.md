---
title: Button 樣式和範本
description: 瞭解 Windows Presentation Foundation Button 控制項的樣式和範本。 修改 ControlTemplate，讓控制項具有獨特的外觀。
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Button
- parts [WPF], Button
- styles [WPF], Button
- Button [WPF], styles and templates
- templates [WPF], Button
- ControlTemplate [WPF], Button
ms.assetid: e223c759-f8c4-4717-acfb-b1e40bdf5f3b
ms.openlocfilehash: 11509adeef397f26eb040e6e98d0edb333b2515f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166266"
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="7cdbf-104">Button 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="7cdbf-104">Button Styles and Templates</span></span>
<span data-ttu-id="7cdbf-105">本主題描述控制項的樣式和範本 <xref:System.Windows.Controls.Button> 。</span><span class="sxs-lookup"><span data-stu-id="7cdbf-105">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="7cdbf-106">您可以修改預設值 <xref:System.Windows.Controls.ControlTemplate> ，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="7cdbf-106">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="7cdbf-107">如需詳細資訊，請參閱[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。</span><span class="sxs-lookup"><span data-stu-id="7cdbf-107">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="7cdbf-108">按鈕部分</span><span class="sxs-lookup"><span data-stu-id="7cdbf-108">Button Parts</span></span>  
 <span data-ttu-id="7cdbf-109"><xref:System.Windows.Controls.Button>控制項沒有任何已命名的元件。</span><span class="sxs-lookup"><span data-stu-id="7cdbf-109">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="7cdbf-110">按鈕狀態</span><span class="sxs-lookup"><span data-stu-id="7cdbf-110">Button States</span></span>  
 <span data-ttu-id="7cdbf-111">下表列出控制項的視覺狀態 <xref:System.Windows.Controls.Button> 。</span><span class="sxs-lookup"><span data-stu-id="7cdbf-111">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="7cdbf-112">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="7cdbf-112">VisualState Name</span></span>|<span data-ttu-id="7cdbf-113">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="7cdbf-113">VisualStateGroup Name</span></span>|<span data-ttu-id="7cdbf-114">描述</span><span class="sxs-lookup"><span data-stu-id="7cdbf-114">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="7cdbf-115">正常</span><span class="sxs-lookup"><span data-stu-id="7cdbf-115">Normal</span></span>|<span data-ttu-id="7cdbf-116">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7cdbf-116">CommonStates</span></span>|<span data-ttu-id="7cdbf-117">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="7cdbf-117">The default state.</span></span>|  
|<span data-ttu-id="7cdbf-118">MouseOver</span><span class="sxs-lookup"><span data-stu-id="7cdbf-118">MouseOver</span></span>|<span data-ttu-id="7cdbf-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7cdbf-119">CommonStates</span></span>|<span data-ttu-id="7cdbf-120">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="7cdbf-120">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="7cdbf-121">按下</span><span class="sxs-lookup"><span data-stu-id="7cdbf-121">Pressed</span></span>|<span data-ttu-id="7cdbf-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7cdbf-122">CommonStates</span></span>|<span data-ttu-id="7cdbf-123">已按下控制項。</span><span class="sxs-lookup"><span data-stu-id="7cdbf-123">The control is pressed.</span></span>|  
|<span data-ttu-id="7cdbf-124">已停用</span><span class="sxs-lookup"><span data-stu-id="7cdbf-124">Disabled</span></span>|<span data-ttu-id="7cdbf-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7cdbf-125">CommonStates</span></span>|<span data-ttu-id="7cdbf-126">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="7cdbf-126">The control is disabled.</span></span>|  
|<span data-ttu-id="7cdbf-127">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="7cdbf-127">Focused</span></span>|<span data-ttu-id="7cdbf-128">FocusStates</span><span class="sxs-lookup"><span data-stu-id="7cdbf-128">FocusStates</span></span>|<span data-ttu-id="7cdbf-129">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="7cdbf-129">The control has focus.</span></span>|  
|<span data-ttu-id="7cdbf-130">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="7cdbf-130">Unfocused</span></span>|<span data-ttu-id="7cdbf-131">FocusStates</span><span class="sxs-lookup"><span data-stu-id="7cdbf-131">FocusStates</span></span>|<span data-ttu-id="7cdbf-132">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="7cdbf-132">The control does not have focus.</span></span>|  
|<span data-ttu-id="7cdbf-133">有效</span><span class="sxs-lookup"><span data-stu-id="7cdbf-133">Valid</span></span>|<span data-ttu-id="7cdbf-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7cdbf-134">ValidationStates</span></span>|<span data-ttu-id="7cdbf-135">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `false` 。</span><span class="sxs-lookup"><span data-stu-id="7cdbf-135">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="7cdbf-136">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="7cdbf-136">InvalidFocused</span></span>|<span data-ttu-id="7cdbf-137">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7cdbf-137">ValidationStates</span></span>|<span data-ttu-id="7cdbf-138"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性為 `true` ，且控制項具有焦點。</span><span class="sxs-lookup"><span data-stu-id="7cdbf-138">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="7cdbf-139">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="7cdbf-139">InvalidUnfocused</span></span>|<span data-ttu-id="7cdbf-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7cdbf-140">ValidationStates</span></span>|<span data-ttu-id="7cdbf-141"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性為 `true` ，且控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="7cdbf-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="7cdbf-142">按鈕 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="7cdbf-142">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="7cdbf-143">下列範例顯示如何定義 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button> 控制項的。</span><span class="sxs-lookup"><span data-stu-id="7cdbf-143">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="7cdbf-144">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="7cdbf-144">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="7cdbf-145">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="7cdbf-145">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cdbf-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7cdbf-146">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="7cdbf-147">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="7cdbf-147">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="7cdbf-148">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="7cdbf-148">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="7cdbf-149">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="7cdbf-149">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="7cdbf-150">建立控制項的範本</span><span class="sxs-lookup"><span data-stu-id="7cdbf-150">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
