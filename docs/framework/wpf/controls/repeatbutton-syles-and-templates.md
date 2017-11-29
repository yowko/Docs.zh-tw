---
title: "RepeatButton 樣式和範本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RepeatButton [WPF], styles and templates
- styles [WPF], RepeatButton
- templates [WPF], RepeatButton
- parts [WPF], RepeatButton
- ControlTemplate [WPF], RepeatButton
- states [WPF], RepeatButton
ms.assetid: fd340743-f44f-4990-9077-085301469670
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4895757e909d5e15fd6540b19e1eeec414e1f4e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="repeatbutton-syles-and-templates"></a><span data-ttu-id="4b1c7-102">RepeatButton 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="4b1c7-102">RepeatButton Syles and Templates</span></span>
<span data-ttu-id="4b1c7-103">本主題描述樣式和範本<xref:System.Windows.Controls.Primitives.RepeatButton>控制項。</span><span class="sxs-lookup"><span data-stu-id="4b1c7-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span> <span data-ttu-id="4b1c7-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="4b1c7-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="4b1c7-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="4b1c7-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="repeatbutton-parts"></a><span data-ttu-id="4b1c7-106">RepeatButton 組件</span><span class="sxs-lookup"><span data-stu-id="4b1c7-106">RepeatButton Parts</span></span>  
 <span data-ttu-id="4b1c7-107"><xref:System.Windows.Controls.Primitives.RepeatButton>控制項沒有任何已命名的組件。</span><span class="sxs-lookup"><span data-stu-id="4b1c7-107">The <xref:System.Windows.Controls.Primitives.RepeatButton> control does not have any named parts.</span></span>  
  
## <a name="repeatbutton-states"></a><span data-ttu-id="4b1c7-108">RepeatButton 狀態</span><span class="sxs-lookup"><span data-stu-id="4b1c7-108">RepeatButton States</span></span>  
 <span data-ttu-id="4b1c7-109">下表列出的視覺狀態<xref:System.Windows.Controls.Primitives.RepeatButton>控制項。</span><span class="sxs-lookup"><span data-stu-id="4b1c7-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span>  
  
|<span data-ttu-id="4b1c7-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="4b1c7-110">VisualState Name</span></span>|<span data-ttu-id="4b1c7-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="4b1c7-111">VisualStateGroup Name</span></span>|<span data-ttu-id="4b1c7-112">描述</span><span class="sxs-lookup"><span data-stu-id="4b1c7-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="4b1c7-113">一般</span><span class="sxs-lookup"><span data-stu-id="4b1c7-113">Normal</span></span>|<span data-ttu-id="4b1c7-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="4b1c7-114">CommonStates</span></span>|<span data-ttu-id="4b1c7-115">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="4b1c7-115">The default state.</span></span>|  
|<span data-ttu-id="4b1c7-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="4b1c7-116">MouseOver</span></span>|<span data-ttu-id="4b1c7-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="4b1c7-117">CommonStates</span></span>|<span data-ttu-id="4b1c7-118">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="4b1c7-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="4b1c7-119">按下</span><span class="sxs-lookup"><span data-stu-id="4b1c7-119">Pressed</span></span>|<span data-ttu-id="4b1c7-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="4b1c7-120">CommonStates</span></span>|<span data-ttu-id="4b1c7-121">已按下控制項。</span><span class="sxs-lookup"><span data-stu-id="4b1c7-121">The control is pressed.</span></span>|  
|<span data-ttu-id="4b1c7-122">已停用</span><span class="sxs-lookup"><span data-stu-id="4b1c7-122">Disabled</span></span>|<span data-ttu-id="4b1c7-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="4b1c7-123">CommonStates</span></span>|<span data-ttu-id="4b1c7-124">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="4b1c7-124">The control is disabled.</span></span>|  
|<span data-ttu-id="4b1c7-125">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="4b1c7-125">Focused</span></span>|<span data-ttu-id="4b1c7-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="4b1c7-126">FocusStates</span></span>|<span data-ttu-id="4b1c7-127">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="4b1c7-127">The control has focus.</span></span>|  
|<span data-ttu-id="4b1c7-128">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="4b1c7-128">Unfocused</span></span>|<span data-ttu-id="4b1c7-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="4b1c7-129">FocusStates</span></span>|<span data-ttu-id="4b1c7-130">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="4b1c7-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="4b1c7-131">驗證</span><span class="sxs-lookup"><span data-stu-id="4b1c7-131">Valid</span></span>|<span data-ttu-id="4b1c7-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="4b1c7-132">ValidationStates</span></span>|<span data-ttu-id="4b1c7-133">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="4b1c7-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="4b1c7-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="4b1c7-134">InvalidFocused</span></span>|<span data-ttu-id="4b1c7-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="4b1c7-135">ValidationStates</span></span>|<span data-ttu-id="4b1c7-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="4b1c7-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="4b1c7-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="4b1c7-137">InvalidUnfocused</span></span>|<span data-ttu-id="4b1c7-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="4b1c7-138">ValidationStates</span></span>|<span data-ttu-id="4b1c7-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="4b1c7-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="repeatbutton-controltemplate-example"></a><span data-ttu-id="4b1c7-140">RepeatButton ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="4b1c7-140">RepeatButton ControlTemplate Example</span></span>  
 <span data-ttu-id="4b1c7-141">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.Primitives.RepeatButton>控制項。</span><span class="sxs-lookup"><span data-stu-id="4b1c7-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#RepeatButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#repeatbutton)]  
  
 <span data-ttu-id="4b1c7-142">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="4b1c7-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="4b1c7-143">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041)。</span><span class="sxs-lookup"><span data-stu-id="4b1c7-143">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b1c7-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b1c7-144">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="4b1c7-145">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="4b1c7-145">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="4b1c7-146">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="4b1c7-146">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="4b1c7-147">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="4b1c7-147">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="4b1c7-148">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="4b1c7-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
