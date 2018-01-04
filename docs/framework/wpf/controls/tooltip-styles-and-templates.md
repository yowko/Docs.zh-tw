---
title: "ToolTip 樣式和範本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], ToolTip
- styles [WPF], ToolTip
- states [WPF], ToolTip
- ToolTip [WPF], styles and templates
- ControlTemplate [WPF], ToolTip
- templates [WPF], ToolTip
ms.assetid: 405fe385-4de9-49ee-a448-d8f4d1f740dd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4e39372083ede5649addee4b493f2425116ec2aa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="tooltip-styles-and-templates"></a><span data-ttu-id="b1ad0-102">ToolTip 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="b1ad0-102">ToolTip Styles and Templates</span></span>
<span data-ttu-id="b1ad0-103">本主題描述樣式和範本<xref:System.Windows.Controls.ToolTip>控制項。</span><span class="sxs-lookup"><span data-stu-id="b1ad0-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolTip> control.</span></span> <span data-ttu-id="b1ad0-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="b1ad0-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="b1ad0-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="b1ad0-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="tooltip-parts"></a><span data-ttu-id="b1ad0-106">工具提示的組件</span><span class="sxs-lookup"><span data-stu-id="b1ad0-106">ToolTip Parts</span></span>  
 <span data-ttu-id="b1ad0-107"><xref:System.Windows.Controls.ToolTip>控制項沒有任何已命名的組件。</span><span class="sxs-lookup"><span data-stu-id="b1ad0-107">The <xref:System.Windows.Controls.ToolTip> control does not have any named parts.</span></span>  
  
## <a name="tooltip-states"></a><span data-ttu-id="b1ad0-108">工具提示狀態</span><span class="sxs-lookup"><span data-stu-id="b1ad0-108">ToolTip States</span></span>  
 <span data-ttu-id="b1ad0-109">下表列出的視覺狀態<xref:System.Windows.Controls.ToolTip>控制項。</span><span class="sxs-lookup"><span data-stu-id="b1ad0-109">The following table lists the visual states for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
|<span data-ttu-id="b1ad0-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="b1ad0-110">VisualState Name</span></span>|<span data-ttu-id="b1ad0-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="b1ad0-111">VisualStateGroup Name</span></span>|<span data-ttu-id="b1ad0-112">描述</span><span class="sxs-lookup"><span data-stu-id="b1ad0-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="b1ad0-113">Closed</span><span class="sxs-lookup"><span data-stu-id="b1ad0-113">Closed</span></span>|<span data-ttu-id="b1ad0-114">OpenStates</span><span class="sxs-lookup"><span data-stu-id="b1ad0-114">OpenStates</span></span>|<span data-ttu-id="b1ad0-115">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="b1ad0-115">The default state.</span></span>|  
|<span data-ttu-id="b1ad0-116">開啟</span><span class="sxs-lookup"><span data-stu-id="b1ad0-116">Open</span></span>|<span data-ttu-id="b1ad0-117">OpenStates</span><span class="sxs-lookup"><span data-stu-id="b1ad0-117">OpenStates</span></span>|<span data-ttu-id="b1ad0-118"><xref:System.Windows.Controls.ToolTip>為可見。</span><span class="sxs-lookup"><span data-stu-id="b1ad0-118">The <xref:System.Windows.Controls.ToolTip> is visible.</span></span>|  
|<span data-ttu-id="b1ad0-119">驗證</span><span class="sxs-lookup"><span data-stu-id="b1ad0-119">Valid</span></span>|<span data-ttu-id="b1ad0-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b1ad0-120">ValidationStates</span></span>|<span data-ttu-id="b1ad0-121">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="b1ad0-121">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="b1ad0-122">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="b1ad0-122">InvalidFocused</span></span>|<span data-ttu-id="b1ad0-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b1ad0-123">ValidationStates</span></span>|<span data-ttu-id="b1ad0-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="b1ad0-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="b1ad0-125">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="b1ad0-125">InvalidUnfocused</span></span>|<span data-ttu-id="b1ad0-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b1ad0-126">ValidationStates</span></span>|<span data-ttu-id="b1ad0-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="b1ad0-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tooltip-controltemplate-example"></a><span data-ttu-id="b1ad0-128">工具提示 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="b1ad0-128">ToolTip ControlTemplate Example</span></span>  
 <span data-ttu-id="b1ad0-129">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.ToolTip>控制項。</span><span class="sxs-lookup"><span data-stu-id="b1ad0-129">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tooltip.xaml#tooltip)]  
  
 <span data-ttu-id="b1ad0-130">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="b1ad0-130">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="b1ad0-131">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041)。</span><span class="sxs-lookup"><span data-stu-id="b1ad0-131">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1ad0-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="b1ad0-132">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="b1ad0-133">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="b1ad0-133">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="b1ad0-134">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="b1ad0-134">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="b1ad0-135">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="b1ad0-135">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="b1ad0-136">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="b1ad0-136">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
