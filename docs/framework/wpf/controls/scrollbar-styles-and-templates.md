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
ms.openlocfilehash: 7093a78555aefd73f9bb05c0a7b5fab6b66176fc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283406"
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="253d4-102">ScrollBar 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="253d4-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="253d4-103">本主題描述 <xref:System.Windows.Controls.Primitives.ScrollBar> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="253d4-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="253d4-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="253d4-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="253d4-105">如需詳細資訊，請參閱[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。</span><span class="sxs-lookup"><span data-stu-id="253d4-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="253d4-106">捲軸部分</span><span class="sxs-lookup"><span data-stu-id="253d4-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="253d4-107">下表列出 <xref:System.Windows.Controls.Primitives.ScrollBar> 控制項的已命名元件。</span><span class="sxs-lookup"><span data-stu-id="253d4-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="253d4-108">組件</span><span class="sxs-lookup"><span data-stu-id="253d4-108">Part</span></span>|<span data-ttu-id="253d4-109">輸入</span><span class="sxs-lookup"><span data-stu-id="253d4-109">Type</span></span>|<span data-ttu-id="253d4-110">描述</span><span class="sxs-lookup"><span data-stu-id="253d4-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="253d4-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="253d4-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="253d4-112">元素的容器，表示 <xref:System.Windows.Controls.Primitives.ScrollBar>的位置。</span><span class="sxs-lookup"><span data-stu-id="253d4-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="253d4-113">捲軸狀態</span><span class="sxs-lookup"><span data-stu-id="253d4-113">ScrollBar States</span></span>  
 <span data-ttu-id="253d4-114">下表列出 <xref:System.Windows.Controls.Primitives.ScrollBar> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="253d4-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="253d4-115">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="253d4-115">VisualState Name</span></span>|<span data-ttu-id="253d4-116">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="253d4-116">VisualStateGroup Name</span></span>|<span data-ttu-id="253d4-117">描述</span><span class="sxs-lookup"><span data-stu-id="253d4-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="253d4-118">一般</span><span class="sxs-lookup"><span data-stu-id="253d4-118">Normal</span></span>|<span data-ttu-id="253d4-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="253d4-119">CommonStates</span></span>|<span data-ttu-id="253d4-120">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="253d4-120">The default state.</span></span>|  
|<span data-ttu-id="253d4-121">MouseOver</span><span class="sxs-lookup"><span data-stu-id="253d4-121">MouseOver</span></span>|<span data-ttu-id="253d4-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="253d4-122">CommonStates</span></span>|<span data-ttu-id="253d4-123">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="253d4-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="253d4-124">已停用</span><span class="sxs-lookup"><span data-stu-id="253d4-124">Disabled</span></span>|<span data-ttu-id="253d4-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="253d4-125">CommonStates</span></span>|<span data-ttu-id="253d4-126">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="253d4-126">The control is disabled.</span></span>|  
|<span data-ttu-id="253d4-127">驗證</span><span class="sxs-lookup"><span data-stu-id="253d4-127">Valid</span></span>|<span data-ttu-id="253d4-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="253d4-128">ValidationStates</span></span>|<span data-ttu-id="253d4-129">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="253d4-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="253d4-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="253d4-130">InvalidFocused</span></span>|<span data-ttu-id="253d4-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="253d4-131">ValidationStates</span></span>|<span data-ttu-id="253d4-132"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性 `true`，且控制項具有焦點。</span><span class="sxs-lookup"><span data-stu-id="253d4-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="253d4-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="253d4-133">InvalidUnfocused</span></span>|<span data-ttu-id="253d4-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="253d4-134">ValidationStates</span></span>|<span data-ttu-id="253d4-135"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性 `true`，而且控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="253d4-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="253d4-136">捲軸 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="253d4-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="253d4-137">下列範例顯示如何定義 <xref:System.Windows.Controls.Primitives.ScrollBar> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="253d4-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="253d4-138">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="253d4-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="253d4-139">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="253d4-139">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="253d4-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="253d4-140">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="253d4-141">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="253d4-141">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="253d4-142">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="253d4-142">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="253d4-143">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="253d4-143">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="253d4-144">建立控制項的範本</span><span class="sxs-lookup"><span data-stu-id="253d4-144">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
