---
title: "Thumb 樣式和範本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], Thumb
- styles [WPF], Thumb
- templates [WPF], Thumb
- Thumb [WPF], styles and templates
- ControlTemplate [WPF], Thumb
- parts [WPF], Thumb
ms.assetid: 86a49235-62d9-414e-923e-53126e3f930a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 780ddc07c79aab111c17f9e7e551cfde85c68f3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="thumb-syles-and-templates"></a><span data-ttu-id="fb0d2-102">Thumb 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="fb0d2-102">Thumb Syles and Templates</span></span>
<span data-ttu-id="fb0d2-103">本主題描述樣式和範本<xref:System.Windows.Controls.Primitives.Thumb>控制項。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="fb0d2-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="fb0d2-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="thumb-parts"></a><span data-ttu-id="fb0d2-106">捲動方塊組件</span><span class="sxs-lookup"><span data-stu-id="fb0d2-106">Thumb Parts</span></span>  
 <span data-ttu-id="fb0d2-107"><xref:System.Windows.Controls.Primitives.Thumb>控制項沒有任何已命名的組件。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-107">The <xref:System.Windows.Controls.Primitives.Thumb> control does not have any named parts.</span></span>  
  
## <a name="thumb-states"></a><span data-ttu-id="fb0d2-108">捲動方塊的狀態</span><span class="sxs-lookup"><span data-stu-id="fb0d2-108">Thumb States</span></span>  
 <span data-ttu-id="fb0d2-109">下表列出的視覺狀態<xref:System.Windows.Controls.Primitives.Thumb>控制項。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
|<span data-ttu-id="fb0d2-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="fb0d2-110">VisualState Name</span></span>|<span data-ttu-id="fb0d2-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="fb0d2-111">VisualStateGroup Name</span></span>|<span data-ttu-id="fb0d2-112">描述</span><span class="sxs-lookup"><span data-stu-id="fb0d2-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="fb0d2-113">一般</span><span class="sxs-lookup"><span data-stu-id="fb0d2-113">Normal</span></span>|<span data-ttu-id="fb0d2-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="fb0d2-114">CommonStates</span></span>|<span data-ttu-id="fb0d2-115">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-115">The default state.</span></span>|  
|<span data-ttu-id="fb0d2-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="fb0d2-116">MouseOver</span></span>|<span data-ttu-id="fb0d2-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="fb0d2-117">CommonStates</span></span>|<span data-ttu-id="fb0d2-118">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="fb0d2-119">按下</span><span class="sxs-lookup"><span data-stu-id="fb0d2-119">Pressed</span></span>|<span data-ttu-id="fb0d2-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="fb0d2-120">CommonStates</span></span>|<span data-ttu-id="fb0d2-121">已按下控制項。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-121">The control is pressed.</span></span>|  
|<span data-ttu-id="fb0d2-122">已停用</span><span class="sxs-lookup"><span data-stu-id="fb0d2-122">Disabled</span></span>|<span data-ttu-id="fb0d2-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="fb0d2-123">CommonStates</span></span>|<span data-ttu-id="fb0d2-124">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-124">The control is disabled.</span></span>|  
|<span data-ttu-id="fb0d2-125">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="fb0d2-125">Focused</span></span>|<span data-ttu-id="fb0d2-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="fb0d2-126">FocusStates</span></span>|<span data-ttu-id="fb0d2-127">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-127">The control has focus.</span></span>|  
|<span data-ttu-id="fb0d2-128">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="fb0d2-128">Unfocused</span></span>|<span data-ttu-id="fb0d2-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="fb0d2-129">FocusStates</span></span>|<span data-ttu-id="fb0d2-130">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="fb0d2-131">驗證</span><span class="sxs-lookup"><span data-stu-id="fb0d2-131">Valid</span></span>|<span data-ttu-id="fb0d2-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fb0d2-132">ValidationStates</span></span>|<span data-ttu-id="fb0d2-133">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="fb0d2-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="fb0d2-134">InvalidFocused</span></span>|<span data-ttu-id="fb0d2-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fb0d2-135">ValidationStates</span></span>|<span data-ttu-id="fb0d2-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="fb0d2-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="fb0d2-137">InvalidUnfocused</span></span>|<span data-ttu-id="fb0d2-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="fb0d2-138">ValidationStates</span></span>|<span data-ttu-id="fb0d2-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="thumb-controltemplate-example"></a><span data-ttu-id="fb0d2-140">捲動方塊 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="fb0d2-140">Thumb ControlTemplate Example</span></span>  
 <span data-ttu-id="fb0d2-141">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.Primitives.Thumb>控制項。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]  
  
 <span data-ttu-id="fb0d2-142">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="fb0d2-143">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041)。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-143">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb0d2-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="fb0d2-144">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="fb0d2-145">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="fb0d2-145">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="fb0d2-146">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="fb0d2-146">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="fb0d2-147">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="fb0d2-147">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="fb0d2-148">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="fb0d2-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
