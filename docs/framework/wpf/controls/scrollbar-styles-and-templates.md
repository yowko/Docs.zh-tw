---
title: "ScrollBar 樣式和範本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], ScrollBar
- ControlTemplate [WPF], ScrollBar
- states [WPF], ScrollBar
- ScrollBar [WPF], styles and templates
- templates [WPF], ScrollBar
- parts [WPF], ScrollBar
ms.assetid: 066ea45a-e27d-43b0-adfe-cce6934c22f5
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 14b40a458b271a4f8b88c167367771235f25c7a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="0bbb9-102">ScrollBar 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="0bbb9-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="0bbb9-103">本主題描述樣式和範本<xref:System.Windows.Controls.Primitives.ScrollBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="0bbb9-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="0bbb9-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="0bbb9-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="0bbb9-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="0bbb9-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="0bbb9-106">捲軸的組件</span><span class="sxs-lookup"><span data-stu-id="0bbb9-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="0bbb9-107">下表列出的具名組件<xref:System.Windows.Controls.Primitives.ScrollBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="0bbb9-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="0bbb9-108">組件</span><span class="sxs-lookup"><span data-stu-id="0bbb9-108">Part</span></span>|<span data-ttu-id="0bbb9-109">類型</span><span class="sxs-lookup"><span data-stu-id="0bbb9-109">Type</span></span>|<span data-ttu-id="0bbb9-110">描述</span><span class="sxs-lookup"><span data-stu-id="0bbb9-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="0bbb9-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="0bbb9-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="0bbb9-112">此元素會指出的位置的容器<xref:System.Windows.Controls.Primitives.ScrollBar>。</span><span class="sxs-lookup"><span data-stu-id="0bbb9-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="0bbb9-113">捲軸狀態</span><span class="sxs-lookup"><span data-stu-id="0bbb9-113">ScrollBar States</span></span>  
 <span data-ttu-id="0bbb9-114">下表列出的視覺狀態<xref:System.Windows.Controls.Primitives.ScrollBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="0bbb9-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="0bbb9-115">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="0bbb9-115">VisualState Name</span></span>|<span data-ttu-id="0bbb9-116">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="0bbb9-116">VisualStateGroup Name</span></span>|<span data-ttu-id="0bbb9-117">描述</span><span class="sxs-lookup"><span data-stu-id="0bbb9-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="0bbb9-118">一般</span><span class="sxs-lookup"><span data-stu-id="0bbb9-118">Normal</span></span>|<span data-ttu-id="0bbb9-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="0bbb9-119">CommonStates</span></span>|<span data-ttu-id="0bbb9-120">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="0bbb9-120">The default state.</span></span>|  
|<span data-ttu-id="0bbb9-121">MouseOver</span><span class="sxs-lookup"><span data-stu-id="0bbb9-121">MouseOver</span></span>|<span data-ttu-id="0bbb9-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="0bbb9-122">CommonStates</span></span>|<span data-ttu-id="0bbb9-123">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="0bbb9-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="0bbb9-124">已停用</span><span class="sxs-lookup"><span data-stu-id="0bbb9-124">Disabled</span></span>|<span data-ttu-id="0bbb9-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="0bbb9-125">CommonStates</span></span>|<span data-ttu-id="0bbb9-126">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="0bbb9-126">The control is disabled.</span></span>|  
|<span data-ttu-id="0bbb9-127">驗證</span><span class="sxs-lookup"><span data-stu-id="0bbb9-127">Valid</span></span>|<span data-ttu-id="0bbb9-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0bbb9-128">ValidationStates</span></span>|<span data-ttu-id="0bbb9-129">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="0bbb9-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="0bbb9-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="0bbb9-130">InvalidFocused</span></span>|<span data-ttu-id="0bbb9-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0bbb9-131">ValidationStates</span></span>|<span data-ttu-id="0bbb9-132"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="0bbb9-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="0bbb9-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="0bbb9-133">InvalidUnfocused</span></span>|<span data-ttu-id="0bbb9-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0bbb9-134">ValidationStates</span></span>|<span data-ttu-id="0bbb9-135"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="0bbb9-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="0bbb9-136">捲軸 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="0bbb9-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="0bbb9-137">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.Primitives.ScrollBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="0bbb9-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="0bbb9-138">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="0bbb9-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="0bbb9-139">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041)。</span><span class="sxs-lookup"><span data-stu-id="0bbb9-139">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bbb9-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="0bbb9-140">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="0bbb9-141">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="0bbb9-141">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="0bbb9-142">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="0bbb9-142">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="0bbb9-143">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="0bbb9-143">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="0bbb9-144">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="0bbb9-144">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
