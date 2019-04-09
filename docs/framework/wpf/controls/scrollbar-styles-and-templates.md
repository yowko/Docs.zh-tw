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
ms.openlocfilehash: 22b2206067302f621a94a1e9abca1607792b3393
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144504"
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="9bf60-102">ScrollBar 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="9bf60-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="9bf60-103">本主題描述的樣式和範本<xref:System.Windows.Controls.Primitives.ScrollBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="9bf60-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="9bf60-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>，讓控制項的獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="9bf60-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="9bf60-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="9bf60-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="9bf60-106">捲軸的組件</span><span class="sxs-lookup"><span data-stu-id="9bf60-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="9bf60-107">下表列出的具名組件<xref:System.Windows.Controls.Primitives.ScrollBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="9bf60-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="9bf60-108">組件</span><span class="sxs-lookup"><span data-stu-id="9bf60-108">Part</span></span>|<span data-ttu-id="9bf60-109">類型</span><span class="sxs-lookup"><span data-stu-id="9bf60-109">Type</span></span>|<span data-ttu-id="9bf60-110">描述</span><span class="sxs-lookup"><span data-stu-id="9bf60-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="9bf60-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="9bf60-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="9bf60-112">指出的位置之項目的容器<xref:System.Windows.Controls.Primitives.ScrollBar>。</span><span class="sxs-lookup"><span data-stu-id="9bf60-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="9bf60-113">捲軸狀態</span><span class="sxs-lookup"><span data-stu-id="9bf60-113">ScrollBar States</span></span>  
 <span data-ttu-id="9bf60-114">下表列出的視覺狀態<xref:System.Windows.Controls.Primitives.ScrollBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="9bf60-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="9bf60-115">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="9bf60-115">VisualState Name</span></span>|<span data-ttu-id="9bf60-116">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="9bf60-116">VisualStateGroup Name</span></span>|<span data-ttu-id="9bf60-117">描述</span><span class="sxs-lookup"><span data-stu-id="9bf60-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="9bf60-118">一般</span><span class="sxs-lookup"><span data-stu-id="9bf60-118">Normal</span></span>|<span data-ttu-id="9bf60-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="9bf60-119">CommonStates</span></span>|<span data-ttu-id="9bf60-120">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="9bf60-120">The default state.</span></span>|  
|<span data-ttu-id="9bf60-121">MouseOver</span><span class="sxs-lookup"><span data-stu-id="9bf60-121">MouseOver</span></span>|<span data-ttu-id="9bf60-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="9bf60-122">CommonStates</span></span>|<span data-ttu-id="9bf60-123">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="9bf60-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="9bf60-124">已停用</span><span class="sxs-lookup"><span data-stu-id="9bf60-124">Disabled</span></span>|<span data-ttu-id="9bf60-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="9bf60-125">CommonStates</span></span>|<span data-ttu-id="9bf60-126">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="9bf60-126">The control is disabled.</span></span>|  
|<span data-ttu-id="9bf60-127">驗證</span><span class="sxs-lookup"><span data-stu-id="9bf60-127">Valid</span></span>|<span data-ttu-id="9bf60-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9bf60-128">ValidationStates</span></span>|<span data-ttu-id="9bf60-129">控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。</span><span class="sxs-lookup"><span data-stu-id="9bf60-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="9bf60-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="9bf60-130">InvalidFocused</span></span>|<span data-ttu-id="9bf60-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9bf60-131">ValidationStates</span></span>|<span data-ttu-id="9bf60-132"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。</span><span class="sxs-lookup"><span data-stu-id="9bf60-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="9bf60-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="9bf60-133">InvalidUnfocused</span></span>|<span data-ttu-id="9bf60-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9bf60-134">ValidationStates</span></span>|<span data-ttu-id="9bf60-135"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="9bf60-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="9bf60-136">ScrollBar 的 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="9bf60-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="9bf60-137">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.Primitives.ScrollBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="9bf60-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="9bf60-138">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="9bf60-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="9bf60-139">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="9bf60-139">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bf60-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bf60-140">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="9bf60-141">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="9bf60-141">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="9bf60-142">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="9bf60-142">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="9bf60-143">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="9bf60-143">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="9bf60-144">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="9bf60-144">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
