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
ms.openlocfilehash: f30a0abb3e4252737e513b531b8d5f49a0d47f0b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458440"
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="b5c1e-102">ScrollBar 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="b5c1e-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="b5c1e-103">本主題描述 <xref:System.Windows.Controls.Primitives.ScrollBar> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="b5c1e-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="b5c1e-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="b5c1e-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="b5c1e-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="b5c1e-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="b5c1e-106">捲軸部分</span><span class="sxs-lookup"><span data-stu-id="b5c1e-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="b5c1e-107">下表列出 <xref:System.Windows.Controls.Primitives.ScrollBar> 控制項的已命名元件。</span><span class="sxs-lookup"><span data-stu-id="b5c1e-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="b5c1e-108">組件</span><span class="sxs-lookup"><span data-stu-id="b5c1e-108">Part</span></span>|<span data-ttu-id="b5c1e-109">輸入</span><span class="sxs-lookup"><span data-stu-id="b5c1e-109">Type</span></span>|<span data-ttu-id="b5c1e-110">描述</span><span class="sxs-lookup"><span data-stu-id="b5c1e-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="b5c1e-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="b5c1e-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="b5c1e-112">元素的容器，表示 <xref:System.Windows.Controls.Primitives.ScrollBar>的位置。</span><span class="sxs-lookup"><span data-stu-id="b5c1e-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="b5c1e-113">捲軸狀態</span><span class="sxs-lookup"><span data-stu-id="b5c1e-113">ScrollBar States</span></span>  
 <span data-ttu-id="b5c1e-114">下表列出 <xref:System.Windows.Controls.Primitives.ScrollBar> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="b5c1e-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="b5c1e-115">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="b5c1e-115">VisualState Name</span></span>|<span data-ttu-id="b5c1e-116">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="b5c1e-116">VisualStateGroup Name</span></span>|<span data-ttu-id="b5c1e-117">描述</span><span class="sxs-lookup"><span data-stu-id="b5c1e-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="b5c1e-118">一般</span><span class="sxs-lookup"><span data-stu-id="b5c1e-118">Normal</span></span>|<span data-ttu-id="b5c1e-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="b5c1e-119">CommonStates</span></span>|<span data-ttu-id="b5c1e-120">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="b5c1e-120">The default state.</span></span>|  
|<span data-ttu-id="b5c1e-121">MouseOver</span><span class="sxs-lookup"><span data-stu-id="b5c1e-121">MouseOver</span></span>|<span data-ttu-id="b5c1e-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="b5c1e-122">CommonStates</span></span>|<span data-ttu-id="b5c1e-123">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="b5c1e-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="b5c1e-124">Disabled</span><span class="sxs-lookup"><span data-stu-id="b5c1e-124">Disabled</span></span>|<span data-ttu-id="b5c1e-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="b5c1e-125">CommonStates</span></span>|<span data-ttu-id="b5c1e-126">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="b5c1e-126">The control is disabled.</span></span>|  
|<span data-ttu-id="b5c1e-127">驗證</span><span class="sxs-lookup"><span data-stu-id="b5c1e-127">Valid</span></span>|<span data-ttu-id="b5c1e-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b5c1e-128">ValidationStates</span></span>|<span data-ttu-id="b5c1e-129">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="b5c1e-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="b5c1e-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="b5c1e-130">InvalidFocused</span></span>|<span data-ttu-id="b5c1e-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b5c1e-131">ValidationStates</span></span>|<span data-ttu-id="b5c1e-132"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性 `true`，且控制項具有焦點。</span><span class="sxs-lookup"><span data-stu-id="b5c1e-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="b5c1e-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="b5c1e-133">InvalidUnfocused</span></span>|<span data-ttu-id="b5c1e-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b5c1e-134">ValidationStates</span></span>|<span data-ttu-id="b5c1e-135"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性 `true`，而且控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="b5c1e-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="b5c1e-136">捲軸 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="b5c1e-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="b5c1e-137">下列範例顯示如何定義 <xref:System.Windows.Controls.Primitives.ScrollBar> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="b5c1e-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="b5c1e-138">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="b5c1e-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="b5c1e-139">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="b5c1e-139">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5c1e-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="b5c1e-140">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="b5c1e-141">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="b5c1e-141">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="b5c1e-142">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="b5c1e-142">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="b5c1e-143">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="b5c1e-143">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="b5c1e-144">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="b5c1e-144">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
