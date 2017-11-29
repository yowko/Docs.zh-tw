---
title: "Expander 樣式和範本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], Expander
- ControlTemplate [WPF], Expander
- templates [WPF], Expander
- Expander [WPF], styles and templates
- states [WPF], Expander
- parts [WPF], Expander
ms.assetid: da2e5a1c-5230-4c21-98a5-59c7895facd7
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 04225458e9889c511b7aaa359239512e316cbb26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="expander-styles-and-templates"></a><span data-ttu-id="1fe2f-102">Expander 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="1fe2f-102">Expander Styles and Templates</span></span>
<span data-ttu-id="1fe2f-103">本主題描述樣式和範本<xref:System.Windows.Controls.Expander>控制項。</span><span class="sxs-lookup"><span data-stu-id="1fe2f-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Expander> control.</span></span> <span data-ttu-id="1fe2f-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="1fe2f-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="1fe2f-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="1fe2f-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="expander-parts"></a><span data-ttu-id="1fe2f-106">Expander 組件</span><span class="sxs-lookup"><span data-stu-id="1fe2f-106">Expander Parts</span></span>  
 <span data-ttu-id="1fe2f-107"><xref:System.Windows.Controls.Expander>控制項沒有任何已命名的組件。</span><span class="sxs-lookup"><span data-stu-id="1fe2f-107">The <xref:System.Windows.Controls.Expander> control does not have any named parts.</span></span>  
  
## <a name="expander-states"></a><span data-ttu-id="1fe2f-108">展開器狀態</span><span class="sxs-lookup"><span data-stu-id="1fe2f-108">Expander States</span></span>  
 <span data-ttu-id="1fe2f-109">下表列出的視覺狀態<xref:System.Windows.Controls.Expander>控制項。</span><span class="sxs-lookup"><span data-stu-id="1fe2f-109">The following table lists the visual states for the <xref:System.Windows.Controls.Expander> control.</span></span>  
  
|<span data-ttu-id="1fe2f-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="1fe2f-110">VisualState Name</span></span>|<span data-ttu-id="1fe2f-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="1fe2f-111">VisualStateGroup Name</span></span>|<span data-ttu-id="1fe2f-112">描述</span><span class="sxs-lookup"><span data-stu-id="1fe2f-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="1fe2f-113">一般</span><span class="sxs-lookup"><span data-stu-id="1fe2f-113">Normal</span></span>|<span data-ttu-id="1fe2f-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="1fe2f-114">CommonStates</span></span>|<span data-ttu-id="1fe2f-115">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="1fe2f-115">The default state.</span></span>|  
|<span data-ttu-id="1fe2f-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="1fe2f-116">MouseOver</span></span>|<span data-ttu-id="1fe2f-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="1fe2f-117">CommonStates</span></span>|<span data-ttu-id="1fe2f-118">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="1fe2f-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="1fe2f-119">已停用</span><span class="sxs-lookup"><span data-stu-id="1fe2f-119">Disabled</span></span>|<span data-ttu-id="1fe2f-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="1fe2f-120">CommonStates</span></span>|<span data-ttu-id="1fe2f-121">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="1fe2f-121">The control is disabled.</span></span>|  
|<span data-ttu-id="1fe2f-122">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="1fe2f-122">Focused</span></span>|<span data-ttu-id="1fe2f-123">FocusStates</span><span class="sxs-lookup"><span data-stu-id="1fe2f-123">FocusStates</span></span>|<span data-ttu-id="1fe2f-124">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="1fe2f-124">The control has focus.</span></span>|  
|<span data-ttu-id="1fe2f-125">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="1fe2f-125">Unfocused</span></span>|<span data-ttu-id="1fe2f-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="1fe2f-126">FocusStates</span></span>|<span data-ttu-id="1fe2f-127">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="1fe2f-127">The control does not have focus.</span></span>|  
|<span data-ttu-id="1fe2f-128">展開的</span><span class="sxs-lookup"><span data-stu-id="1fe2f-128">Expanded</span></span>|<span data-ttu-id="1fe2f-129">ExpansionStates</span><span class="sxs-lookup"><span data-stu-id="1fe2f-129">ExpansionStates</span></span>|<span data-ttu-id="1fe2f-130">展開此控制項。</span><span class="sxs-lookup"><span data-stu-id="1fe2f-130">The control is expanded.</span></span>|  
|<span data-ttu-id="1fe2f-131">Collapsed</span><span class="sxs-lookup"><span data-stu-id="1fe2f-131">Collapsed</span></span>|<span data-ttu-id="1fe2f-132">ExpansionStates</span><span class="sxs-lookup"><span data-stu-id="1fe2f-132">ExpansionStates</span></span>|<span data-ttu-id="1fe2f-133">不展開的控制項。</span><span class="sxs-lookup"><span data-stu-id="1fe2f-133">The control is not expanded.</span></span>|  
|<span data-ttu-id="1fe2f-134">ExpandDown</span><span class="sxs-lookup"><span data-stu-id="1fe2f-134">ExpandDown</span></span>|<span data-ttu-id="1fe2f-135">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="1fe2f-135">ExpandDirectionStates</span></span>|<span data-ttu-id="1fe2f-136">控制項以向下擴展。</span><span class="sxs-lookup"><span data-stu-id="1fe2f-136">The control expands down.</span></span>|  
|<span data-ttu-id="1fe2f-137">ExpandUp</span><span class="sxs-lookup"><span data-stu-id="1fe2f-137">ExpandUp</span></span>|<span data-ttu-id="1fe2f-138">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="1fe2f-138">ExpandDirectionStates</span></span>|<span data-ttu-id="1fe2f-139">控制項將向上擴充。</span><span class="sxs-lookup"><span data-stu-id="1fe2f-139">The control expands up.</span></span>|  
|<span data-ttu-id="1fe2f-140">ExpandLeft</span><span class="sxs-lookup"><span data-stu-id="1fe2f-140">ExpandLeft</span></span>|<span data-ttu-id="1fe2f-141">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="1fe2f-141">ExpandDirectionStates</span></span>|<span data-ttu-id="1fe2f-142">控制項會向左展開。</span><span class="sxs-lookup"><span data-stu-id="1fe2f-142">The control expands left.</span></span>|  
|<span data-ttu-id="1fe2f-143">ExpandRight</span><span class="sxs-lookup"><span data-stu-id="1fe2f-143">ExpandRight</span></span>|<span data-ttu-id="1fe2f-144">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="1fe2f-144">ExpandDirectionStates</span></span>|<span data-ttu-id="1fe2f-145">向右展開控制項。</span><span class="sxs-lookup"><span data-stu-id="1fe2f-145">The control expands right.</span></span>|  
|<span data-ttu-id="1fe2f-146">驗證</span><span class="sxs-lookup"><span data-stu-id="1fe2f-146">Valid</span></span>|<span data-ttu-id="1fe2f-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1fe2f-147">ValidationStates</span></span>|<span data-ttu-id="1fe2f-148">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="1fe2f-148">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="1fe2f-149">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="1fe2f-149">InvalidFocused</span></span>|<span data-ttu-id="1fe2f-150">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1fe2f-150">ValidationStates</span></span>|<span data-ttu-id="1fe2f-151"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="1fe2f-151">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="1fe2f-152">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="1fe2f-152">InvalidUnfocused</span></span>|<span data-ttu-id="1fe2f-153">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1fe2f-153">ValidationStates</span></span>|<span data-ttu-id="1fe2f-154"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="1fe2f-154">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="expander-controltemplate-example"></a><span data-ttu-id="1fe2f-155">Expander ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="1fe2f-155">Expander ControlTemplate Example</span></span>  
 <span data-ttu-id="1fe2f-156">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.Expander>控制項。</span><span class="sxs-lookup"><span data-stu-id="1fe2f-156">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Expander> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Expander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/expander.xaml#expander)]  
  
 <span data-ttu-id="1fe2f-157">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="1fe2f-157">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="1fe2f-158">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041)。</span><span class="sxs-lookup"><span data-stu-id="1fe2f-158">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fe2f-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1fe2f-159">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="1fe2f-160">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="1fe2f-160">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="1fe2f-161">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="1fe2f-161">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="1fe2f-162">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="1fe2f-162">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="1fe2f-163">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="1fe2f-163">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
