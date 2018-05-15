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
ms.openlocfilehash: ca7033f3a9f2d8a46c9a19c0b1e4e441efb39c7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="checkbox-styles-and-templates"></a><span data-ttu-id="ffb5b-102">CheckBox 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="ffb5b-102">CheckBox Styles and Templates</span></span>
<span data-ttu-id="ffb5b-103">本主題描述樣式和範本<xref:System.Windows.Controls.CheckBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.CheckBox> control.</span></span> <span data-ttu-id="ffb5b-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="ffb5b-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="checkbox-parts"></a><span data-ttu-id="ffb5b-106">核取方塊組件</span><span class="sxs-lookup"><span data-stu-id="ffb5b-106">CheckBox Parts</span></span>  
 <span data-ttu-id="ffb5b-107"><xref:System.Windows.Controls.CheckBox>控制項沒有任何已命名的組件。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-107">The <xref:System.Windows.Controls.CheckBox> control does not have any named parts.</span></span>  
  
## <a name="checkbox-states"></a><span data-ttu-id="ffb5b-108">核取方塊狀態</span><span class="sxs-lookup"><span data-stu-id="ffb5b-108">CheckBox States</span></span>  
 <span data-ttu-id="ffb5b-109">下表列出的視覺狀態<xref:System.Windows.Controls.CheckBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-109">The following table lists the visual states for the <xref:System.Windows.Controls.CheckBox> control.</span></span>  
  
|<span data-ttu-id="ffb5b-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="ffb5b-110">VisualState Name</span></span>|<span data-ttu-id="ffb5b-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="ffb5b-111">VisualStateGroup Name</span></span>|<span data-ttu-id="ffb5b-112">描述</span><span class="sxs-lookup"><span data-stu-id="ffb5b-112">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="ffb5b-113">一般</span><span class="sxs-lookup"><span data-stu-id="ffb5b-113">Normal</span></span>|<span data-ttu-id="ffb5b-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ffb5b-114">CommonStates</span></span>|<span data-ttu-id="ffb5b-115">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-115">The default state.</span></span>|  
|<span data-ttu-id="ffb5b-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="ffb5b-116">MouseOver</span></span>|<span data-ttu-id="ffb5b-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ffb5b-117">CommonStates</span></span>|<span data-ttu-id="ffb5b-118">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="ffb5b-119">按下</span><span class="sxs-lookup"><span data-stu-id="ffb5b-119">Pressed</span></span>|<span data-ttu-id="ffb5b-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ffb5b-120">CommonStates</span></span>|<span data-ttu-id="ffb5b-121">已按下控制項。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-121">The control is pressed.</span></span>|  
|<span data-ttu-id="ffb5b-122">已停用</span><span class="sxs-lookup"><span data-stu-id="ffb5b-122">Disabled</span></span>|<span data-ttu-id="ffb5b-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ffb5b-123">CommonStates</span></span>|<span data-ttu-id="ffb5b-124">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-124">The control is disabled.</span></span>|  
|<span data-ttu-id="ffb5b-125">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="ffb5b-125">Focused</span></span>|<span data-ttu-id="ffb5b-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="ffb5b-126">FocusStates</span></span>|<span data-ttu-id="ffb5b-127">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-127">The control has focus.</span></span>|  
|<span data-ttu-id="ffb5b-128">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="ffb5b-128">Unfocused</span></span>|<span data-ttu-id="ffb5b-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="ffb5b-129">FocusStates</span></span>|<span data-ttu-id="ffb5b-130">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="ffb5b-131">已核取</span><span class="sxs-lookup"><span data-stu-id="ffb5b-131">Checked</span></span>|<span data-ttu-id="ffb5b-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="ffb5b-132">CheckStates</span></span>|<span data-ttu-id="ffb5b-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 為 `true`。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|  
|<span data-ttu-id="ffb5b-134">若未選取</span><span class="sxs-lookup"><span data-stu-id="ffb5b-134">Unchecked</span></span>|<span data-ttu-id="ffb5b-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="ffb5b-135">CheckStates</span></span>|<span data-ttu-id="ffb5b-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 為 `false`。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|  
|<span data-ttu-id="ffb5b-137">不定</span><span class="sxs-lookup"><span data-stu-id="ffb5b-137">Indeterminate</span></span>|<span data-ttu-id="ffb5b-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="ffb5b-138">CheckStates</span></span>|<span data-ttu-id="ffb5b-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> 是`true`，和<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>是`null`。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|  
|<span data-ttu-id="ffb5b-140">驗證</span><span class="sxs-lookup"><span data-stu-id="ffb5b-140">Valid</span></span>|<span data-ttu-id="ffb5b-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ffb5b-141">ValidationStates</span></span>|<span data-ttu-id="ffb5b-142">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="ffb5b-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="ffb5b-143">InvalidUnfocused</span></span>|<span data-ttu-id="ffb5b-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ffb5b-144">ValidationStates</span></span>|<span data-ttu-id="ffb5b-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="ffb5b-146">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="ffb5b-146">InvalidFocused</span></span>|<span data-ttu-id="ffb5b-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ffb5b-147">ValidationStates</span></span>|<span data-ttu-id="ffb5b-148"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="checkbox-controltemplate-example"></a><span data-ttu-id="ffb5b-149">核取方塊 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="ffb5b-149">CheckBox ControlTemplate Example</span></span>  
 <span data-ttu-id="ffb5b-150">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.CheckBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-150">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.CheckBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#CheckBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/checkbox.xaml#checkbox)]  
  
 <span data-ttu-id="ffb5b-151">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-151">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="ffb5b-152">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041)。</span><span class="sxs-lookup"><span data-stu-id="ffb5b-152">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffb5b-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffb5b-153">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="ffb5b-154">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="ffb5b-154">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="ffb5b-155">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="ffb5b-155">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="ffb5b-156">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="ffb5b-156">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="ffb5b-157">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="ffb5b-157">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
