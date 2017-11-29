---
title: "Slider 樣式和範本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], Slider
- states [WPF], Slider
- Slider [WPF], styles and templates
- styles [WPF], Slider
- templates [WPF], Slider
- ControlTemplate [WPF], Slider
ms.assetid: d89aa97b-075a-4752-9c41-9679df65c491
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9dfa340cf42e5e7ed105bf14eb0f7a24ea85a1b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="slider-styles-and-templates"></a><span data-ttu-id="1dd14-102">Slider 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="1dd14-102">Slider Styles and Templates</span></span>
<span data-ttu-id="1dd14-103">本主題描述樣式和範本<xref:System.Windows.Controls.Slider>控制項。</span><span class="sxs-lookup"><span data-stu-id="1dd14-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Slider> control.</span></span> <span data-ttu-id="1dd14-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="1dd14-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="1dd14-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="1dd14-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="slider-parts"></a><span data-ttu-id="1dd14-106">滑桿組件</span><span class="sxs-lookup"><span data-stu-id="1dd14-106">Slider Parts</span></span>  
 <span data-ttu-id="1dd14-107">下表列出的具名組件<xref:System.Windows.Controls.Slider>控制項。</span><span class="sxs-lookup"><span data-stu-id="1dd14-107">The following table lists the named parts for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="1dd14-108">組件</span><span class="sxs-lookup"><span data-stu-id="1dd14-108">Part</span></span>|<span data-ttu-id="1dd14-109">類型</span><span class="sxs-lookup"><span data-stu-id="1dd14-109">Type</span></span>|<span data-ttu-id="1dd14-110">說明</span><span class="sxs-lookup"><span data-stu-id="1dd14-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="1dd14-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="1dd14-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="1dd14-112">此元素會指出的位置的容器<xref:System.Windows.Controls.Slider>。</span><span class="sxs-lookup"><span data-stu-id="1dd14-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Slider>.</span></span>|  
|<span data-ttu-id="1dd14-113">PART_SelectionRange</span><span class="sxs-lookup"><span data-stu-id="1dd14-113">PART_SelectionRange</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="1dd14-114">顯示的選取範圍的項目<xref:System.Windows.Controls.Slider>。</span><span class="sxs-lookup"><span data-stu-id="1dd14-114">The element that displays a selection range along the <xref:System.Windows.Controls.Slider>.</span></span>  <span data-ttu-id="1dd14-115">選取範圍會顯示只有當<xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A>屬性是`true`。</span><span class="sxs-lookup"><span data-stu-id="1dd14-115">The selection range is visible only if the <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> property is `true`.</span></span>|  
  
## <a name="slider-states"></a><span data-ttu-id="1dd14-116">滑桿狀態</span><span class="sxs-lookup"><span data-stu-id="1dd14-116">Slider States</span></span>  
 <span data-ttu-id="1dd14-117">下表列出的視覺狀態<xref:System.Windows.Controls.Slider>控制項。</span><span class="sxs-lookup"><span data-stu-id="1dd14-117">The following table lists the visual states for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="1dd14-118">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="1dd14-118">VisualState Name</span></span>|<span data-ttu-id="1dd14-119">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="1dd14-119">VisualStateGroup Name</span></span>|<span data-ttu-id="1dd14-120">描述</span><span class="sxs-lookup"><span data-stu-id="1dd14-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="1dd14-121">一般</span><span class="sxs-lookup"><span data-stu-id="1dd14-121">Normal</span></span>|<span data-ttu-id="1dd14-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="1dd14-122">CommonStates</span></span>|<span data-ttu-id="1dd14-123">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="1dd14-123">The default state.</span></span>|  
|<span data-ttu-id="1dd14-124">MouseOver</span><span class="sxs-lookup"><span data-stu-id="1dd14-124">MouseOver</span></span>|<span data-ttu-id="1dd14-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="1dd14-125">CommonStates</span></span>|<span data-ttu-id="1dd14-126">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="1dd14-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="1dd14-127">已停用</span><span class="sxs-lookup"><span data-stu-id="1dd14-127">Disabled</span></span>|<span data-ttu-id="1dd14-128">CommonStates</span><span class="sxs-lookup"><span data-stu-id="1dd14-128">CommonStates</span></span>|<span data-ttu-id="1dd14-129">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="1dd14-129">The control is disabled.</span></span>|  
|<span data-ttu-id="1dd14-130">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="1dd14-130">Focused</span></span>|<span data-ttu-id="1dd14-131">FocusStates</span><span class="sxs-lookup"><span data-stu-id="1dd14-131">FocusStates</span></span>|<span data-ttu-id="1dd14-132">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="1dd14-132">The control has focus.</span></span>|  
|<span data-ttu-id="1dd14-133">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="1dd14-133">Unfocused</span></span>|<span data-ttu-id="1dd14-134">FocusStates</span><span class="sxs-lookup"><span data-stu-id="1dd14-134">FocusStates</span></span>|<span data-ttu-id="1dd14-135">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="1dd14-135">The control does not have focus.</span></span>|  
|<span data-ttu-id="1dd14-136">驗證</span><span class="sxs-lookup"><span data-stu-id="1dd14-136">Valid</span></span>|<span data-ttu-id="1dd14-137">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1dd14-137">ValidationStates</span></span>|<span data-ttu-id="1dd14-138">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="1dd14-138">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="1dd14-139">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="1dd14-139">InvalidFocused</span></span>|<span data-ttu-id="1dd14-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1dd14-140">ValidationStates</span></span>|<span data-ttu-id="1dd14-141"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="1dd14-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="1dd14-142">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="1dd14-142">InvalidUnfocused</span></span>|<span data-ttu-id="1dd14-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1dd14-143">ValidationStates</span></span>|<span data-ttu-id="1dd14-144"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="1dd14-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="slider-controltemplate-example"></a><span data-ttu-id="1dd14-145">滑桿 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="1dd14-145">Slider ControlTemplate Example</span></span>  
 <span data-ttu-id="1dd14-146">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.Slider>控制項。</span><span class="sxs-lookup"><span data-stu-id="1dd14-146">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Slider](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#slider)]  
  
 <span data-ttu-id="1dd14-147">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="1dd14-147">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="1dd14-148">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041)。</span><span class="sxs-lookup"><span data-stu-id="1dd14-148">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd14-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1dd14-149">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="1dd14-150">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="1dd14-150">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="1dd14-151">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="1dd14-151">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="1dd14-152">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="1dd14-152">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="1dd14-153">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="1dd14-153">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
