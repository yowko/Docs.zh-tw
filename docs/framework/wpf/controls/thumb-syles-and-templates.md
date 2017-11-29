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
ms.openlocfilehash: 7d9f0b8559497939737b97568a679953d392d5be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="thumb-syles-and-templates"></a><span data-ttu-id="c7d19-102">Thumb 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="c7d19-102">Thumb Syles and Templates</span></span>
<span data-ttu-id="c7d19-103">本主題描述樣式和範本<xref:System.Windows.Controls.Primitives.Thumb>控制項。</span><span class="sxs-lookup"><span data-stu-id="c7d19-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="c7d19-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="c7d19-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="c7d19-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="c7d19-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="thumb-parts"></a><span data-ttu-id="c7d19-106">捲動方塊組件</span><span class="sxs-lookup"><span data-stu-id="c7d19-106">Thumb Parts</span></span>  
 <span data-ttu-id="c7d19-107"><xref:System.Windows.Controls.Primitives.Thumb>控制項沒有任何已命名的組件。</span><span class="sxs-lookup"><span data-stu-id="c7d19-107">The <xref:System.Windows.Controls.Primitives.Thumb> control does not have any named parts.</span></span>  
  
## <a name="thumb-states"></a><span data-ttu-id="c7d19-108">捲動方塊的狀態</span><span class="sxs-lookup"><span data-stu-id="c7d19-108">Thumb States</span></span>  
 <span data-ttu-id="c7d19-109">下表列出的視覺狀態<xref:System.Windows.Controls.Primitives.Thumb>控制項。</span><span class="sxs-lookup"><span data-stu-id="c7d19-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
|<span data-ttu-id="c7d19-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="c7d19-110">VisualState Name</span></span>|<span data-ttu-id="c7d19-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="c7d19-111">VisualStateGroup Name</span></span>|<span data-ttu-id="c7d19-112">描述</span><span class="sxs-lookup"><span data-stu-id="c7d19-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="c7d19-113">一般</span><span class="sxs-lookup"><span data-stu-id="c7d19-113">Normal</span></span>|<span data-ttu-id="c7d19-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c7d19-114">CommonStates</span></span>|<span data-ttu-id="c7d19-115">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="c7d19-115">The default state.</span></span>|  
|<span data-ttu-id="c7d19-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="c7d19-116">MouseOver</span></span>|<span data-ttu-id="c7d19-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c7d19-117">CommonStates</span></span>|<span data-ttu-id="c7d19-118">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="c7d19-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="c7d19-119">按下</span><span class="sxs-lookup"><span data-stu-id="c7d19-119">Pressed</span></span>|<span data-ttu-id="c7d19-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c7d19-120">CommonStates</span></span>|<span data-ttu-id="c7d19-121">已按下控制項。</span><span class="sxs-lookup"><span data-stu-id="c7d19-121">The control is pressed.</span></span>|  
|<span data-ttu-id="c7d19-122">已停用</span><span class="sxs-lookup"><span data-stu-id="c7d19-122">Disabled</span></span>|<span data-ttu-id="c7d19-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c7d19-123">CommonStates</span></span>|<span data-ttu-id="c7d19-124">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="c7d19-124">The control is disabled.</span></span>|  
|<span data-ttu-id="c7d19-125">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="c7d19-125">Focused</span></span>|<span data-ttu-id="c7d19-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="c7d19-126">FocusStates</span></span>|<span data-ttu-id="c7d19-127">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="c7d19-127">The control has focus.</span></span>|  
|<span data-ttu-id="c7d19-128">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="c7d19-128">Unfocused</span></span>|<span data-ttu-id="c7d19-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="c7d19-129">FocusStates</span></span>|<span data-ttu-id="c7d19-130">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="c7d19-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="c7d19-131">驗證</span><span class="sxs-lookup"><span data-stu-id="c7d19-131">Valid</span></span>|<span data-ttu-id="c7d19-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c7d19-132">ValidationStates</span></span>|<span data-ttu-id="c7d19-133">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="c7d19-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="c7d19-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="c7d19-134">InvalidFocused</span></span>|<span data-ttu-id="c7d19-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c7d19-135">ValidationStates</span></span>|<span data-ttu-id="c7d19-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="c7d19-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="c7d19-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="c7d19-137">InvalidUnfocused</span></span>|<span data-ttu-id="c7d19-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c7d19-138">ValidationStates</span></span>|<span data-ttu-id="c7d19-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="c7d19-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="thumb-controltemplate-example"></a><span data-ttu-id="c7d19-140">捲動方塊 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="c7d19-140">Thumb ControlTemplate Example</span></span>  
 <span data-ttu-id="c7d19-141">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.Primitives.Thumb>控制項。</span><span class="sxs-lookup"><span data-stu-id="c7d19-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]  
  
 <span data-ttu-id="c7d19-142">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="c7d19-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="c7d19-143">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041)。</span><span class="sxs-lookup"><span data-stu-id="c7d19-143">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7d19-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7d19-144">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="c7d19-145">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="c7d19-145">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="c7d19-146">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="c7d19-146">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="c7d19-147">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="c7d19-147">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="c7d19-148">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="c7d19-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
