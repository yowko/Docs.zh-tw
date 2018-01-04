---
title: "ToggleButton 樣式和範本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], ToggleButton
- ToggleButton [WPF], styles and templates
- ControlTemplate [WPF], ToggleButton
- styles [WPF], ToggleButton
- templates [WPF], ToggleButton
- parts [WPF], ToggleButton
ms.assetid: 54f23f30-4bcb-4f09-8ce4-376a13a255a1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5c143717b691e79771fbaa55724d9d9748259e3f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="togglebutton-syles-and-templates"></a><span data-ttu-id="35244-102">ToggleButton 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="35244-102">ToggleButton Syles and Templates</span></span>
<span data-ttu-id="35244-103">本主題描述樣式和範本<xref:System.Windows.Controls.Primitives.ToggleButton>控制項。</span><span class="sxs-lookup"><span data-stu-id="35244-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span> <span data-ttu-id="35244-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="35244-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="35244-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="35244-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="togglebutton-parts"></a><span data-ttu-id="35244-106">ToggleButton 組件</span><span class="sxs-lookup"><span data-stu-id="35244-106">ToggleButton Parts</span></span>  
 <span data-ttu-id="35244-107"><xref:System.Windows.Controls.Primitives.ToggleButton>控制項沒有任何已命名的組件。</span><span class="sxs-lookup"><span data-stu-id="35244-107">The <xref:System.Windows.Controls.Primitives.ToggleButton> control does not have any named parts.</span></span>  
  
## <a name="togglebutton-states"></a><span data-ttu-id="35244-108">切換狀態</span><span class="sxs-lookup"><span data-stu-id="35244-108">ToggleButton States</span></span>  
 <span data-ttu-id="35244-109">下表列出的視覺狀態<xref:System.Windows.Controls.Primitives.ToggleButton>控制項。</span><span class="sxs-lookup"><span data-stu-id="35244-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>  
  
|<span data-ttu-id="35244-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="35244-110">VisualState Name</span></span>|<span data-ttu-id="35244-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="35244-111">VisualStateGroup Name</span></span>|<span data-ttu-id="35244-112">描述</span><span class="sxs-lookup"><span data-stu-id="35244-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="35244-113">一般</span><span class="sxs-lookup"><span data-stu-id="35244-113">Normal</span></span>|<span data-ttu-id="35244-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="35244-114">CommonStates</span></span>|<span data-ttu-id="35244-115">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="35244-115">The default state.</span></span>|  
|<span data-ttu-id="35244-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="35244-116">MouseOver</span></span>|<span data-ttu-id="35244-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="35244-117">CommonStates</span></span>|<span data-ttu-id="35244-118">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="35244-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="35244-119">按下</span><span class="sxs-lookup"><span data-stu-id="35244-119">Pressed</span></span>|<span data-ttu-id="35244-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="35244-120">CommonStates</span></span>|<span data-ttu-id="35244-121">已按下控制項。</span><span class="sxs-lookup"><span data-stu-id="35244-121">The control is pressed.</span></span>|  
|<span data-ttu-id="35244-122">已停用</span><span class="sxs-lookup"><span data-stu-id="35244-122">Disabled</span></span>|<span data-ttu-id="35244-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="35244-123">CommonStates</span></span>|<span data-ttu-id="35244-124">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="35244-124">The control is disabled.</span></span>|  
|<span data-ttu-id="35244-125">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="35244-125">Focused</span></span>|<span data-ttu-id="35244-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="35244-126">FocusStates</span></span>|<span data-ttu-id="35244-127">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="35244-127">The control has focus.</span></span>|  
|<span data-ttu-id="35244-128">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="35244-128">Unfocused</span></span>|<span data-ttu-id="35244-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="35244-129">FocusStates</span></span>|<span data-ttu-id="35244-130">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="35244-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="35244-131">已核取</span><span class="sxs-lookup"><span data-stu-id="35244-131">Checked</span></span>|<span data-ttu-id="35244-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="35244-132">CheckStates</span></span>|<span data-ttu-id="35244-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 為 `true`。</span><span class="sxs-lookup"><span data-stu-id="35244-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|  
|<span data-ttu-id="35244-134">若未選取</span><span class="sxs-lookup"><span data-stu-id="35244-134">Unchecked</span></span>|<span data-ttu-id="35244-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="35244-135">CheckStates</span></span>|<span data-ttu-id="35244-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 為 `false`。</span><span class="sxs-lookup"><span data-stu-id="35244-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|  
|<span data-ttu-id="35244-137">不定</span><span class="sxs-lookup"><span data-stu-id="35244-137">Indeterminate</span></span>|<span data-ttu-id="35244-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="35244-138">CheckStates</span></span>|<span data-ttu-id="35244-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A>是`true`，和<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>是`null`。</span><span class="sxs-lookup"><span data-stu-id="35244-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|  
|<span data-ttu-id="35244-140">驗證</span><span class="sxs-lookup"><span data-stu-id="35244-140">Valid</span></span>|<span data-ttu-id="35244-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="35244-141">ValidationStates</span></span>|<span data-ttu-id="35244-142">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="35244-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="35244-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="35244-143">InvalidFocused</span></span>|<span data-ttu-id="35244-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="35244-144">ValidationStates</span></span>|<span data-ttu-id="35244-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="35244-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="35244-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="35244-146">InvalidUnfocused</span></span>|<span data-ttu-id="35244-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="35244-147">ValidationStates</span></span>|<span data-ttu-id="35244-148"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="35244-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="35244-149">如果不確定的視覺狀態不存在於控制項範本，然後取消核取的視覺狀態會用作預設視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="35244-149">If the Indeterminate visual state does not exist in your control template, then the Unchecked visual state will be used as default visual state.</span></span>  
  
## <a name="togglebutton-controltemplate-example"></a><span data-ttu-id="35244-150">ToggleButton ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="35244-150">ToggleButton ControlTemplate Example</span></span>  
 <span data-ttu-id="35244-151">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.Primitives.ToggleButton>控制項。</span><span class="sxs-lookup"><span data-stu-id="35244-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToggleButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]  
  
 <span data-ttu-id="35244-152">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="35244-152">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="35244-153">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041)。</span><span class="sxs-lookup"><span data-stu-id="35244-153">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35244-154">請參閱</span><span class="sxs-lookup"><span data-stu-id="35244-154">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="35244-155">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="35244-155">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="35244-156">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="35244-156">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="35244-157">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="35244-157">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="35244-158">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="35244-158">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
