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
ms.openlocfilehash: b194b22c04ac586cbb10a021bac422bbb92a28f0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356204"
---
# <a name="checkbox-styles-and-templates"></a><span data-ttu-id="8e49a-102">CheckBox 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="8e49a-102">CheckBox Styles and Templates</span></span>
<span data-ttu-id="8e49a-103">本主題描述的樣式和範本<xref:System.Windows.Controls.CheckBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="8e49a-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.CheckBox> control.</span></span> <span data-ttu-id="8e49a-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>，讓控制項的獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="8e49a-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="8e49a-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="8e49a-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="checkbox-parts"></a><span data-ttu-id="8e49a-106">核取方塊部分</span><span class="sxs-lookup"><span data-stu-id="8e49a-106">CheckBox Parts</span></span>  
 <span data-ttu-id="8e49a-107"><xref:System.Windows.Controls.CheckBox>控制項沒有任何具名組件。</span><span class="sxs-lookup"><span data-stu-id="8e49a-107">The <xref:System.Windows.Controls.CheckBox> control does not have any named parts.</span></span>  
  
## <a name="checkbox-states"></a><span data-ttu-id="8e49a-108">核取方塊狀態</span><span class="sxs-lookup"><span data-stu-id="8e49a-108">CheckBox States</span></span>  
 <span data-ttu-id="8e49a-109">下表列出的視覺狀態<xref:System.Windows.Controls.CheckBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="8e49a-109">The following table lists the visual states for the <xref:System.Windows.Controls.CheckBox> control.</span></span>  
  
|<span data-ttu-id="8e49a-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="8e49a-110">VisualState Name</span></span>|<span data-ttu-id="8e49a-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="8e49a-111">VisualStateGroup Name</span></span>|<span data-ttu-id="8e49a-112">描述</span><span class="sxs-lookup"><span data-stu-id="8e49a-112">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="8e49a-113">一般</span><span class="sxs-lookup"><span data-stu-id="8e49a-113">Normal</span></span>|<span data-ttu-id="8e49a-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="8e49a-114">CommonStates</span></span>|<span data-ttu-id="8e49a-115">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="8e49a-115">The default state.</span></span>|  
|<span data-ttu-id="8e49a-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="8e49a-116">MouseOver</span></span>|<span data-ttu-id="8e49a-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="8e49a-117">CommonStates</span></span>|<span data-ttu-id="8e49a-118">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="8e49a-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="8e49a-119">按下</span><span class="sxs-lookup"><span data-stu-id="8e49a-119">Pressed</span></span>|<span data-ttu-id="8e49a-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="8e49a-120">CommonStates</span></span>|<span data-ttu-id="8e49a-121">已按下控制項。</span><span class="sxs-lookup"><span data-stu-id="8e49a-121">The control is pressed.</span></span>|  
|<span data-ttu-id="8e49a-122">已停用</span><span class="sxs-lookup"><span data-stu-id="8e49a-122">Disabled</span></span>|<span data-ttu-id="8e49a-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="8e49a-123">CommonStates</span></span>|<span data-ttu-id="8e49a-124">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="8e49a-124">The control is disabled.</span></span>|  
|<span data-ttu-id="8e49a-125">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="8e49a-125">Focused</span></span>|<span data-ttu-id="8e49a-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="8e49a-126">FocusStates</span></span>|<span data-ttu-id="8e49a-127">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="8e49a-127">The control has focus.</span></span>|  
|<span data-ttu-id="8e49a-128">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="8e49a-128">Unfocused</span></span>|<span data-ttu-id="8e49a-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="8e49a-129">FocusStates</span></span>|<span data-ttu-id="8e49a-130">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="8e49a-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="8e49a-131">已核取</span><span class="sxs-lookup"><span data-stu-id="8e49a-131">Checked</span></span>|<span data-ttu-id="8e49a-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="8e49a-132">CheckStates</span></span>|<span data-ttu-id="8e49a-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 為 `true`。</span><span class="sxs-lookup"><span data-stu-id="8e49a-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|  
|<span data-ttu-id="8e49a-134">未選取</span><span class="sxs-lookup"><span data-stu-id="8e49a-134">Unchecked</span></span>|<span data-ttu-id="8e49a-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="8e49a-135">CheckStates</span></span>|<span data-ttu-id="8e49a-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 為 `false`。</span><span class="sxs-lookup"><span data-stu-id="8e49a-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|  
|<span data-ttu-id="8e49a-137">不定</span><span class="sxs-lookup"><span data-stu-id="8e49a-137">Indeterminate</span></span>|<span data-ttu-id="8e49a-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="8e49a-138">CheckStates</span></span>|<span data-ttu-id="8e49a-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> 已`true`，並<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>是`null`。</span><span class="sxs-lookup"><span data-stu-id="8e49a-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|  
|<span data-ttu-id="8e49a-140">驗證</span><span class="sxs-lookup"><span data-stu-id="8e49a-140">Valid</span></span>|<span data-ttu-id="8e49a-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8e49a-141">ValidationStates</span></span>|<span data-ttu-id="8e49a-142">控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。</span><span class="sxs-lookup"><span data-stu-id="8e49a-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="8e49a-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="8e49a-143">InvalidUnfocused</span></span>|<span data-ttu-id="8e49a-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8e49a-144">ValidationStates</span></span>|<span data-ttu-id="8e49a-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。</span><span class="sxs-lookup"><span data-stu-id="8e49a-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="8e49a-146">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="8e49a-146">InvalidFocused</span></span>|<span data-ttu-id="8e49a-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8e49a-147">ValidationStates</span></span>|<span data-ttu-id="8e49a-148"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="8e49a-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="checkbox-controltemplate-example"></a><span data-ttu-id="8e49a-149">核取方塊 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="8e49a-149">CheckBox ControlTemplate Example</span></span>  
 <span data-ttu-id="8e49a-150">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.CheckBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="8e49a-150">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.CheckBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#CheckBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/checkbox.xaml#checkbox)]  
  
 <span data-ttu-id="8e49a-151">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="8e49a-151">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="8e49a-152">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="8e49a-152">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e49a-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e49a-153">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="8e49a-154">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="8e49a-154">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="8e49a-155">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="8e49a-155">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="8e49a-156">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="8e49a-156">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="8e49a-157">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="8e49a-157">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
