---
title: Expander 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], Expander
- ControlTemplate [WPF], Expander
- templates [WPF], Expander
- Expander [WPF], styles and templates
- states [WPF], Expander
- parts [WPF], Expander
ms.assetid: da2e5a1c-5230-4c21-98a5-59c7895facd7
ms.openlocfilehash: 26989474f264161be12bcc14fed614fdc7f775b6
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460337"
---
# <a name="expander-styles-and-templates"></a><span data-ttu-id="ad274-102">Expander 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="ad274-102">Expander Styles and Templates</span></span>
<span data-ttu-id="ad274-103">本主題描述 <xref:System.Windows.Controls.Expander> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="ad274-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Expander> control.</span></span> <span data-ttu-id="ad274-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="ad274-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="ad274-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="ad274-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="expander-parts"></a><span data-ttu-id="ad274-106">展開器元件</span><span class="sxs-lookup"><span data-stu-id="ad274-106">Expander Parts</span></span>  
 <span data-ttu-id="ad274-107"><xref:System.Windows.Controls.Expander> 控制項沒有任何已命名的元件。</span><span class="sxs-lookup"><span data-stu-id="ad274-107">The <xref:System.Windows.Controls.Expander> control does not have any named parts.</span></span>  
  
## <a name="expander-states"></a><span data-ttu-id="ad274-108">展開器狀態</span><span class="sxs-lookup"><span data-stu-id="ad274-108">Expander States</span></span>  
 <span data-ttu-id="ad274-109">下表列出 <xref:System.Windows.Controls.Expander> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="ad274-109">The following table lists the visual states for the <xref:System.Windows.Controls.Expander> control.</span></span>  
  
|<span data-ttu-id="ad274-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="ad274-110">VisualState Name</span></span>|<span data-ttu-id="ad274-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="ad274-111">VisualStateGroup Name</span></span>|<span data-ttu-id="ad274-112">描述</span><span class="sxs-lookup"><span data-stu-id="ad274-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ad274-113">一般</span><span class="sxs-lookup"><span data-stu-id="ad274-113">Normal</span></span>|<span data-ttu-id="ad274-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ad274-114">CommonStates</span></span>|<span data-ttu-id="ad274-115">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="ad274-115">The default state.</span></span>|  
|<span data-ttu-id="ad274-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="ad274-116">MouseOver</span></span>|<span data-ttu-id="ad274-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ad274-117">CommonStates</span></span>|<span data-ttu-id="ad274-118">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="ad274-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="ad274-119">Disabled</span><span class="sxs-lookup"><span data-stu-id="ad274-119">Disabled</span></span>|<span data-ttu-id="ad274-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ad274-120">CommonStates</span></span>|<span data-ttu-id="ad274-121">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="ad274-121">The control is disabled.</span></span>|  
|<span data-ttu-id="ad274-122">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="ad274-122">Focused</span></span>|<span data-ttu-id="ad274-123">FocusStates</span><span class="sxs-lookup"><span data-stu-id="ad274-123">FocusStates</span></span>|<span data-ttu-id="ad274-124">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="ad274-124">The control has focus.</span></span>|  
|<span data-ttu-id="ad274-125">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="ad274-125">Unfocused</span></span>|<span data-ttu-id="ad274-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="ad274-126">FocusStates</span></span>|<span data-ttu-id="ad274-127">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="ad274-127">The control does not have focus.</span></span>|  
|<span data-ttu-id="ad274-128">展開</span><span class="sxs-lookup"><span data-stu-id="ad274-128">Expanded</span></span>|<span data-ttu-id="ad274-129">ExpansionStates</span><span class="sxs-lookup"><span data-stu-id="ad274-129">ExpansionStates</span></span>|<span data-ttu-id="ad274-130">控制項已展開。</span><span class="sxs-lookup"><span data-stu-id="ad274-130">The control is expanded.</span></span>|  
|<span data-ttu-id="ad274-131">Collapsed</span><span class="sxs-lookup"><span data-stu-id="ad274-131">Collapsed</span></span>|<span data-ttu-id="ad274-132">ExpansionStates</span><span class="sxs-lookup"><span data-stu-id="ad274-132">ExpansionStates</span></span>|<span data-ttu-id="ad274-133">控制項不會展開。</span><span class="sxs-lookup"><span data-stu-id="ad274-133">The control is not expanded.</span></span>|  
|<span data-ttu-id="ad274-134">ExpandDown</span><span class="sxs-lookup"><span data-stu-id="ad274-134">ExpandDown</span></span>|<span data-ttu-id="ad274-135">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="ad274-135">ExpandDirectionStates</span></span>|<span data-ttu-id="ad274-136">控制項會向下展開。</span><span class="sxs-lookup"><span data-stu-id="ad274-136">The control expands down.</span></span>|  
|<span data-ttu-id="ad274-137">ExpandUp</span><span class="sxs-lookup"><span data-stu-id="ad274-137">ExpandUp</span></span>|<span data-ttu-id="ad274-138">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="ad274-138">ExpandDirectionStates</span></span>|<span data-ttu-id="ad274-139">控制項會展開。</span><span class="sxs-lookup"><span data-stu-id="ad274-139">The control expands up.</span></span>|  
|<span data-ttu-id="ad274-140">ExpandLeft</span><span class="sxs-lookup"><span data-stu-id="ad274-140">ExpandLeft</span></span>|<span data-ttu-id="ad274-141">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="ad274-141">ExpandDirectionStates</span></span>|<span data-ttu-id="ad274-142">控制項會向左展開。</span><span class="sxs-lookup"><span data-stu-id="ad274-142">The control expands left.</span></span>|  
|<span data-ttu-id="ad274-143">ExpandRight</span><span class="sxs-lookup"><span data-stu-id="ad274-143">ExpandRight</span></span>|<span data-ttu-id="ad274-144">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="ad274-144">ExpandDirectionStates</span></span>|<span data-ttu-id="ad274-145">控制項會向右展開。</span><span class="sxs-lookup"><span data-stu-id="ad274-145">The control expands right.</span></span>|  
|<span data-ttu-id="ad274-146">驗證</span><span class="sxs-lookup"><span data-stu-id="ad274-146">Valid</span></span>|<span data-ttu-id="ad274-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ad274-147">ValidationStates</span></span>|<span data-ttu-id="ad274-148">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="ad274-148">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="ad274-149">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="ad274-149">InvalidFocused</span></span>|<span data-ttu-id="ad274-150">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ad274-150">ValidationStates</span></span>|<span data-ttu-id="ad274-151"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="ad274-151">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="ad274-152">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="ad274-152">InvalidUnfocused</span></span>|<span data-ttu-id="ad274-153">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ad274-153">ValidationStates</span></span>|<span data-ttu-id="ad274-154"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="ad274-154">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="expander-controltemplate-example"></a><span data-ttu-id="ad274-155">展開器 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="ad274-155">Expander ControlTemplate Example</span></span>  
 <span data-ttu-id="ad274-156">下列範例顯示如何定義 <xref:System.Windows.Controls.Expander> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="ad274-156">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Expander> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Expander](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/expander.xaml#expander)]  
  
 <span data-ttu-id="ad274-157">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="ad274-157">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="ad274-158">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="ad274-158">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad274-159">請參閱</span><span class="sxs-lookup"><span data-stu-id="ad274-159">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="ad274-160">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="ad274-160">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="ad274-161">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="ad274-161">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="ad274-162">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="ad274-162">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="ad274-163">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="ad274-163">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
