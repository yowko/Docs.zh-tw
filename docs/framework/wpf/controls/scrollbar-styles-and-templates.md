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
ms.openlocfilehash: 016556fb825ddf60af7dc572d6fda7323b9bb09d
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671975"
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="ced02-102">ScrollBar 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="ced02-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="ced02-103">本主題描述<xref:System.Windows.Controls.Primitives.ScrollBar>控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="ced02-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="ced02-104">您可以修改預設值<xref:System.Windows.Controls.ControlTemplate> , 為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="ced02-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="ced02-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="ced02-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="ced02-106">捲軸部分</span><span class="sxs-lookup"><span data-stu-id="ced02-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="ced02-107">下表列出<xref:System.Windows.Controls.Primitives.ScrollBar>控制項的已命名元件。</span><span class="sxs-lookup"><span data-stu-id="ced02-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="ced02-108">組件</span><span class="sxs-lookup"><span data-stu-id="ced02-108">Part</span></span>|<span data-ttu-id="ced02-109">類型</span><span class="sxs-lookup"><span data-stu-id="ced02-109">Type</span></span>|<span data-ttu-id="ced02-110">描述</span><span class="sxs-lookup"><span data-stu-id="ced02-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ced02-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="ced02-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="ced02-112">元素的容器, 這個專案表示的位置<xref:System.Windows.Controls.Primitives.ScrollBar>。</span><span class="sxs-lookup"><span data-stu-id="ced02-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="ced02-113">捲軸狀態</span><span class="sxs-lookup"><span data-stu-id="ced02-113">ScrollBar States</span></span>  
 <span data-ttu-id="ced02-114">下表列出<xref:System.Windows.Controls.Primitives.ScrollBar>控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="ced02-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="ced02-115">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="ced02-115">VisualState Name</span></span>|<span data-ttu-id="ced02-116">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="ced02-116">VisualStateGroup Name</span></span>|<span data-ttu-id="ced02-117">描述</span><span class="sxs-lookup"><span data-stu-id="ced02-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="ced02-118">一般</span><span class="sxs-lookup"><span data-stu-id="ced02-118">Normal</span></span>|<span data-ttu-id="ced02-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ced02-119">CommonStates</span></span>|<span data-ttu-id="ced02-120">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="ced02-120">The default state.</span></span>|  
|<span data-ttu-id="ced02-121">MouseOver</span><span class="sxs-lookup"><span data-stu-id="ced02-121">MouseOver</span></span>|<span data-ttu-id="ced02-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ced02-122">CommonStates</span></span>|<span data-ttu-id="ced02-123">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="ced02-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="ced02-124">已停用</span><span class="sxs-lookup"><span data-stu-id="ced02-124">Disabled</span></span>|<span data-ttu-id="ced02-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ced02-125">CommonStates</span></span>|<span data-ttu-id="ced02-126">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="ced02-126">The control is disabled.</span></span>|  
|<span data-ttu-id="ced02-127">驗證</span><span class="sxs-lookup"><span data-stu-id="ced02-127">Valid</span></span>|<span data-ttu-id="ced02-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ced02-128">ValidationStates</span></span>|<span data-ttu-id="ced02-129">控制項使用<xref:System.Windows.Controls.Validation>類別<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> , 而附加屬性是`false`。</span><span class="sxs-lookup"><span data-stu-id="ced02-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="ced02-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="ced02-130">InvalidFocused</span></span>|<span data-ttu-id="ced02-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ced02-131">ValidationStates</span></span>|<span data-ttu-id="ced02-132">附加屬性為`true` , 且控制項具有焦點。 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ced02-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="ced02-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="ced02-133">InvalidUnfocused</span></span>|<span data-ttu-id="ced02-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ced02-134">ValidationStates</span></span>|<span data-ttu-id="ced02-135">附加屬性為`true` , 且控制項沒有焦點。 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ced02-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="ced02-136">捲軸 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="ced02-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="ced02-137">下列範例顯示如何定義<xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Primitives.ScrollBar>控制項的。</span><span class="sxs-lookup"><span data-stu-id="ced02-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="ced02-138">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="ced02-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="ced02-139">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="ced02-139">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ced02-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ced02-140">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="ced02-141">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="ced02-141">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="ced02-142">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="ced02-142">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="ced02-143">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="ced02-143">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="ced02-144">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="ced02-144">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
