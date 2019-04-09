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
ms.openlocfilehash: c5f805c251d3f6b256035e568798cd6d252ea9a4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115436"
---
# <a name="expander-styles-and-templates"></a><span data-ttu-id="d1b36-102">Expander 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="d1b36-102">Expander Styles and Templates</span></span>
<span data-ttu-id="d1b36-103">本主題描述的樣式和範本<xref:System.Windows.Controls.Expander>控制項。</span><span class="sxs-lookup"><span data-stu-id="d1b36-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Expander> control.</span></span> <span data-ttu-id="d1b36-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>，讓控制項的獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="d1b36-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="d1b36-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="d1b36-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="expander-parts"></a><span data-ttu-id="d1b36-106">展開器組件</span><span class="sxs-lookup"><span data-stu-id="d1b36-106">Expander Parts</span></span>  
 <span data-ttu-id="d1b36-107"><xref:System.Windows.Controls.Expander>控制項沒有任何具名組件。</span><span class="sxs-lookup"><span data-stu-id="d1b36-107">The <xref:System.Windows.Controls.Expander> control does not have any named parts.</span></span>  
  
## <a name="expander-states"></a><span data-ttu-id="d1b36-108">展開器狀態</span><span class="sxs-lookup"><span data-stu-id="d1b36-108">Expander States</span></span>  
 <span data-ttu-id="d1b36-109">下表列出的視覺狀態<xref:System.Windows.Controls.Expander>控制項。</span><span class="sxs-lookup"><span data-stu-id="d1b36-109">The following table lists the visual states for the <xref:System.Windows.Controls.Expander> control.</span></span>  
  
|<span data-ttu-id="d1b36-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="d1b36-110">VisualState Name</span></span>|<span data-ttu-id="d1b36-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="d1b36-111">VisualStateGroup Name</span></span>|<span data-ttu-id="d1b36-112">描述</span><span class="sxs-lookup"><span data-stu-id="d1b36-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d1b36-113">一般</span><span class="sxs-lookup"><span data-stu-id="d1b36-113">Normal</span></span>|<span data-ttu-id="d1b36-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d1b36-114">CommonStates</span></span>|<span data-ttu-id="d1b36-115">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="d1b36-115">The default state.</span></span>|  
|<span data-ttu-id="d1b36-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="d1b36-116">MouseOver</span></span>|<span data-ttu-id="d1b36-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d1b36-117">CommonStates</span></span>|<span data-ttu-id="d1b36-118">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="d1b36-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="d1b36-119">已停用</span><span class="sxs-lookup"><span data-stu-id="d1b36-119">Disabled</span></span>|<span data-ttu-id="d1b36-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d1b36-120">CommonStates</span></span>|<span data-ttu-id="d1b36-121">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="d1b36-121">The control is disabled.</span></span>|  
|<span data-ttu-id="d1b36-122">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="d1b36-122">Focused</span></span>|<span data-ttu-id="d1b36-123">FocusStates</span><span class="sxs-lookup"><span data-stu-id="d1b36-123">FocusStates</span></span>|<span data-ttu-id="d1b36-124">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="d1b36-124">The control has focus.</span></span>|  
|<span data-ttu-id="d1b36-125">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="d1b36-125">Unfocused</span></span>|<span data-ttu-id="d1b36-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="d1b36-126">FocusStates</span></span>|<span data-ttu-id="d1b36-127">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="d1b36-127">The control does not have focus.</span></span>|  
|<span data-ttu-id="d1b36-128">展開</span><span class="sxs-lookup"><span data-stu-id="d1b36-128">Expanded</span></span>|<span data-ttu-id="d1b36-129">ExpansionStates</span><span class="sxs-lookup"><span data-stu-id="d1b36-129">ExpansionStates</span></span>|<span data-ttu-id="d1b36-130">展開此控制項。</span><span class="sxs-lookup"><span data-stu-id="d1b36-130">The control is expanded.</span></span>|  
|<span data-ttu-id="d1b36-131">Collapsed</span><span class="sxs-lookup"><span data-stu-id="d1b36-131">Collapsed</span></span>|<span data-ttu-id="d1b36-132">ExpansionStates</span><span class="sxs-lookup"><span data-stu-id="d1b36-132">ExpansionStates</span></span>|<span data-ttu-id="d1b36-133">無法展開此控制項。</span><span class="sxs-lookup"><span data-stu-id="d1b36-133">The control is not expanded.</span></span>|  
|<span data-ttu-id="d1b36-134">ExpandDown</span><span class="sxs-lookup"><span data-stu-id="d1b36-134">ExpandDown</span></span>|<span data-ttu-id="d1b36-135">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="d1b36-135">ExpandDirectionStates</span></span>|<span data-ttu-id="d1b36-136">控制會向下展開。</span><span class="sxs-lookup"><span data-stu-id="d1b36-136">The control expands down.</span></span>|  
|<span data-ttu-id="d1b36-137">ExpandUp</span><span class="sxs-lookup"><span data-stu-id="d1b36-137">ExpandUp</span></span>|<span data-ttu-id="d1b36-138">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="d1b36-138">ExpandDirectionStates</span></span>|<span data-ttu-id="d1b36-139">控制項將向上擴充。</span><span class="sxs-lookup"><span data-stu-id="d1b36-139">The control expands up.</span></span>|  
|<span data-ttu-id="d1b36-140">ExpandLeft</span><span class="sxs-lookup"><span data-stu-id="d1b36-140">ExpandLeft</span></span>|<span data-ttu-id="d1b36-141">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="d1b36-141">ExpandDirectionStates</span></span>|<span data-ttu-id="d1b36-142">控制項會向左展開。</span><span class="sxs-lookup"><span data-stu-id="d1b36-142">The control expands left.</span></span>|  
|<span data-ttu-id="d1b36-143">ExpandRight</span><span class="sxs-lookup"><span data-stu-id="d1b36-143">ExpandRight</span></span>|<span data-ttu-id="d1b36-144">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="d1b36-144">ExpandDirectionStates</span></span>|<span data-ttu-id="d1b36-145">控制項會向右展開。</span><span class="sxs-lookup"><span data-stu-id="d1b36-145">The control expands right.</span></span>|  
|<span data-ttu-id="d1b36-146">驗證</span><span class="sxs-lookup"><span data-stu-id="d1b36-146">Valid</span></span>|<span data-ttu-id="d1b36-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d1b36-147">ValidationStates</span></span>|<span data-ttu-id="d1b36-148">控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。</span><span class="sxs-lookup"><span data-stu-id="d1b36-148">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d1b36-149">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d1b36-149">InvalidFocused</span></span>|<span data-ttu-id="d1b36-150">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d1b36-150">ValidationStates</span></span>|<span data-ttu-id="d1b36-151"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。</span><span class="sxs-lookup"><span data-stu-id="d1b36-151">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d1b36-152">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d1b36-152">InvalidUnfocused</span></span>|<span data-ttu-id="d1b36-153">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d1b36-153">ValidationStates</span></span>|<span data-ttu-id="d1b36-154"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="d1b36-154">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="expander-controltemplate-example"></a><span data-ttu-id="d1b36-155">Expander ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="d1b36-155">Expander ControlTemplate Example</span></span>  
 <span data-ttu-id="d1b36-156">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.Expander>控制項。</span><span class="sxs-lookup"><span data-stu-id="d1b36-156">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Expander> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Expander](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/expander.xaml#expander)]  
  
 <span data-ttu-id="d1b36-157">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="d1b36-157">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="d1b36-158">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="d1b36-158">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1b36-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1b36-159">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="d1b36-160">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="d1b36-160">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="d1b36-161">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="d1b36-161">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="d1b36-162">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="d1b36-162">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="d1b36-163">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="d1b36-163">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
