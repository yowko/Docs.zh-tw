---
title: ScrollBar 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], ScrollBar
- ControlTemplate [WPF], ScrollBar
- states [WPF], ScrollBar
- ScrollBar [WPF], styles and templates
- templates [WPF], ScrollBar
- parts [WPF], ScrollBar
ms.assetid: 066ea45a-e27d-43b0-adfe-cce6934c22f5
ms.openlocfilehash: 926fc3373bb40eb12462dcead278d458cefad7cf
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="ddd42-102">ScrollBar 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="ddd42-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="ddd42-103">本主題描述樣式和範本<xref:System.Windows.Controls.Primitives.ScrollBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="ddd42-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="ddd42-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="ddd42-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="ddd42-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="ddd42-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="ddd42-106">捲軸的組件</span><span class="sxs-lookup"><span data-stu-id="ddd42-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="ddd42-107">下表列出的具名組件<xref:System.Windows.Controls.Primitives.ScrollBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="ddd42-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="ddd42-108">組件</span><span class="sxs-lookup"><span data-stu-id="ddd42-108">Part</span></span>|<span data-ttu-id="ddd42-109">類型</span><span class="sxs-lookup"><span data-stu-id="ddd42-109">Type</span></span>|<span data-ttu-id="ddd42-110">描述</span><span class="sxs-lookup"><span data-stu-id="ddd42-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ddd42-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="ddd42-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="ddd42-112">此元素會指出的位置的容器<xref:System.Windows.Controls.Primitives.ScrollBar>。</span><span class="sxs-lookup"><span data-stu-id="ddd42-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="ddd42-113">捲軸狀態</span><span class="sxs-lookup"><span data-stu-id="ddd42-113">ScrollBar States</span></span>  
 <span data-ttu-id="ddd42-114">下表列出的視覺狀態<xref:System.Windows.Controls.Primitives.ScrollBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="ddd42-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="ddd42-115">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="ddd42-115">VisualState Name</span></span>|<span data-ttu-id="ddd42-116">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="ddd42-116">VisualStateGroup Name</span></span>|<span data-ttu-id="ddd42-117">描述</span><span class="sxs-lookup"><span data-stu-id="ddd42-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="ddd42-118">一般</span><span class="sxs-lookup"><span data-stu-id="ddd42-118">Normal</span></span>|<span data-ttu-id="ddd42-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ddd42-119">CommonStates</span></span>|<span data-ttu-id="ddd42-120">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="ddd42-120">The default state.</span></span>|  
|<span data-ttu-id="ddd42-121">MouseOver</span><span class="sxs-lookup"><span data-stu-id="ddd42-121">MouseOver</span></span>|<span data-ttu-id="ddd42-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ddd42-122">CommonStates</span></span>|<span data-ttu-id="ddd42-123">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="ddd42-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="ddd42-124">已停用</span><span class="sxs-lookup"><span data-stu-id="ddd42-124">Disabled</span></span>|<span data-ttu-id="ddd42-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ddd42-125">CommonStates</span></span>|<span data-ttu-id="ddd42-126">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="ddd42-126">The control is disabled.</span></span>|  
|<span data-ttu-id="ddd42-127">驗證</span><span class="sxs-lookup"><span data-stu-id="ddd42-127">Valid</span></span>|<span data-ttu-id="ddd42-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ddd42-128">ValidationStates</span></span>|<span data-ttu-id="ddd42-129">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="ddd42-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="ddd42-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="ddd42-130">InvalidFocused</span></span>|<span data-ttu-id="ddd42-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ddd42-131">ValidationStates</span></span>|<span data-ttu-id="ddd42-132"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="ddd42-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="ddd42-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="ddd42-133">InvalidUnfocused</span></span>|<span data-ttu-id="ddd42-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ddd42-134">ValidationStates</span></span>|<span data-ttu-id="ddd42-135"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="ddd42-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="ddd42-136">捲軸 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="ddd42-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="ddd42-137">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.Primitives.ScrollBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="ddd42-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="ddd42-138">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="ddd42-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="ddd42-139">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="ddd42-139">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddd42-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ddd42-140">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="ddd42-141">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="ddd42-141">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="ddd42-142">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="ddd42-142">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="ddd42-143">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="ddd42-143">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="ddd42-144">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="ddd42-144">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
