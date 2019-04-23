---
title: RadioButton 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], RadioButton
- RadioButton [WPF], styles and templates
- ControlTemplate [WPF], RadioButton
- states [WPF], RadioButton
- templates [WPF], RadioButton
- parts [WPF], RadioButton
ms.assetid: 9acf93f7-dd2f-4010-8ce0-1edd81c52ae2
ms.openlocfilehash: f11a8338c96d14c3c518713865061e4095ff23b1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078716"
---
# <a name="radiobutton-styles-and-templates"></a><span data-ttu-id="bbf03-102">RadioButton 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="bbf03-102">RadioButton Styles and Templates</span></span>
<span data-ttu-id="bbf03-103">本主題描述的樣式和範本<xref:System.Windows.Controls.RadioButton>控制項。</span><span class="sxs-lookup"><span data-stu-id="bbf03-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.RadioButton> control.</span></span> <span data-ttu-id="bbf03-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>，讓控制項的獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="bbf03-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="bbf03-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="bbf03-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="radiobutton-parts"></a><span data-ttu-id="bbf03-106">RadioButton 組件</span><span class="sxs-lookup"><span data-stu-id="bbf03-106">RadioButton Parts</span></span>  
 <span data-ttu-id="bbf03-107"><xref:System.Windows.Controls.RadioButton>控制項沒有任何具名組件。</span><span class="sxs-lookup"><span data-stu-id="bbf03-107">The <xref:System.Windows.Controls.RadioButton> control does not have any named parts.</span></span>  
  
## <a name="radiobutton-states"></a><span data-ttu-id="bbf03-108">選項按鈕狀態</span><span class="sxs-lookup"><span data-stu-id="bbf03-108">RadioButton States</span></span>  
 <span data-ttu-id="bbf03-109">下表列出的視覺狀態<xref:System.Windows.Controls.RadioButton>控制項。</span><span class="sxs-lookup"><span data-stu-id="bbf03-109">The following table lists the visual states for the <xref:System.Windows.Controls.RadioButton> control.</span></span>  
  
|<span data-ttu-id="bbf03-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="bbf03-110">VisualState Name</span></span>|<span data-ttu-id="bbf03-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="bbf03-111">VisualStateGroup Name</span></span>|<span data-ttu-id="bbf03-112">描述</span><span class="sxs-lookup"><span data-stu-id="bbf03-112">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="bbf03-113">一般</span><span class="sxs-lookup"><span data-stu-id="bbf03-113">Normal</span></span>|<span data-ttu-id="bbf03-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="bbf03-114">CommonStates</span></span>|<span data-ttu-id="bbf03-115">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="bbf03-115">The default state.</span></span>|  
|<span data-ttu-id="bbf03-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="bbf03-116">MouseOver</span></span>|<span data-ttu-id="bbf03-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="bbf03-117">CommonStates</span></span>|<span data-ttu-id="bbf03-118">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="bbf03-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="bbf03-119">按下</span><span class="sxs-lookup"><span data-stu-id="bbf03-119">Pressed</span></span>|<span data-ttu-id="bbf03-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="bbf03-120">CommonStates</span></span>|<span data-ttu-id="bbf03-121">已按下控制項。</span><span class="sxs-lookup"><span data-stu-id="bbf03-121">The control is pressed.</span></span>|  
|<span data-ttu-id="bbf03-122">已停用</span><span class="sxs-lookup"><span data-stu-id="bbf03-122">Disabled</span></span>|<span data-ttu-id="bbf03-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="bbf03-123">CommonStates</span></span>|<span data-ttu-id="bbf03-124">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="bbf03-124">The control is disabled.</span></span>|  
|<span data-ttu-id="bbf03-125">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="bbf03-125">Focused</span></span>|<span data-ttu-id="bbf03-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="bbf03-126">FocusStates</span></span>|<span data-ttu-id="bbf03-127">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="bbf03-127">The control has focus.</span></span>|  
|<span data-ttu-id="bbf03-128">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="bbf03-128">Unfocused</span></span>|<span data-ttu-id="bbf03-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="bbf03-129">FocusStates</span></span>|<span data-ttu-id="bbf03-130">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="bbf03-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="bbf03-131">已核取</span><span class="sxs-lookup"><span data-stu-id="bbf03-131">Checked</span></span>|<span data-ttu-id="bbf03-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="bbf03-132">CheckStates</span></span>|<span data-ttu-id="bbf03-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 為 `true`。</span><span class="sxs-lookup"><span data-stu-id="bbf03-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|  
|<span data-ttu-id="bbf03-134">未選取</span><span class="sxs-lookup"><span data-stu-id="bbf03-134">Unchecked</span></span>|<span data-ttu-id="bbf03-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="bbf03-135">CheckStates</span></span>|<span data-ttu-id="bbf03-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 為 `false`。</span><span class="sxs-lookup"><span data-stu-id="bbf03-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|  
|<span data-ttu-id="bbf03-137">不定</span><span class="sxs-lookup"><span data-stu-id="bbf03-137">Indeterminate</span></span>|<span data-ttu-id="bbf03-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="bbf03-138">CheckStates</span></span>|<span data-ttu-id="bbf03-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> 已`true`，並<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>是`null`。</span><span class="sxs-lookup"><span data-stu-id="bbf03-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|  
|<span data-ttu-id="bbf03-140">驗證</span><span class="sxs-lookup"><span data-stu-id="bbf03-140">Valid</span></span>|<span data-ttu-id="bbf03-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="bbf03-141">ValidationStates</span></span>|<span data-ttu-id="bbf03-142">控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。</span><span class="sxs-lookup"><span data-stu-id="bbf03-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="bbf03-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="bbf03-143">InvalidFocused</span></span>|<span data-ttu-id="bbf03-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="bbf03-144">ValidationStates</span></span>|<span data-ttu-id="bbf03-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。</span><span class="sxs-lookup"><span data-stu-id="bbf03-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="bbf03-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="bbf03-146">InvalidUnfocused</span></span>|<span data-ttu-id="bbf03-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="bbf03-147">ValidationStates</span></span>|<span data-ttu-id="bbf03-148"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="bbf03-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="radiobutton-controltemplate-example"></a><span data-ttu-id="bbf03-149">RadioButton ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="bbf03-149">RadioButton ControlTemplate Example</span></span>  
 <span data-ttu-id="bbf03-150">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.RadioButton>控制項。</span><span class="sxs-lookup"><span data-stu-id="bbf03-150">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.RadioButton> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#RadioButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/radiobutton.xaml#radiobutton)]  
  
 <span data-ttu-id="bbf03-151">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="bbf03-151">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="bbf03-152">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="bbf03-152">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbf03-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbf03-153">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="bbf03-154">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="bbf03-154">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="bbf03-155">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="bbf03-155">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="bbf03-156">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="bbf03-156">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="bbf03-157">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="bbf03-157">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
