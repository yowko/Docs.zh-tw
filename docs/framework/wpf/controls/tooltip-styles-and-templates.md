---
title: ToolTip 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ToolTip
- styles [WPF], ToolTip
- states [WPF], ToolTip
- ToolTip [WPF], styles and templates
- ControlTemplate [WPF], ToolTip
- templates [WPF], ToolTip
ms.assetid: 405fe385-4de9-49ee-a448-d8f4d1f740dd
ms.openlocfilehash: 53b21f610ba957370fac70b79e6a827d624b6473
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457290"
---
# <a name="tooltip-styles-and-templates"></a><span data-ttu-id="f87e1-102">ToolTip 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="f87e1-102">ToolTip Styles and Templates</span></span>
<span data-ttu-id="f87e1-103">本主題描述樣式和範本<xref:System.Windows.Controls.ToolTip>控制項。</span><span class="sxs-lookup"><span data-stu-id="f87e1-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolTip> control.</span></span> <span data-ttu-id="f87e1-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="f87e1-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="f87e1-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="f87e1-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="tooltip-parts"></a><span data-ttu-id="f87e1-106">工具提示的組件</span><span class="sxs-lookup"><span data-stu-id="f87e1-106">ToolTip Parts</span></span>  
 <span data-ttu-id="f87e1-107"><xref:System.Windows.Controls.ToolTip>控制項沒有任何已命名的組件。</span><span class="sxs-lookup"><span data-stu-id="f87e1-107">The <xref:System.Windows.Controls.ToolTip> control does not have any named parts.</span></span>  
  
## <a name="tooltip-states"></a><span data-ttu-id="f87e1-108">工具提示狀態</span><span class="sxs-lookup"><span data-stu-id="f87e1-108">ToolTip States</span></span>  
 <span data-ttu-id="f87e1-109">下表列出的視覺狀態<xref:System.Windows.Controls.ToolTip>控制項。</span><span class="sxs-lookup"><span data-stu-id="f87e1-109">The following table lists the visual states for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
|<span data-ttu-id="f87e1-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="f87e1-110">VisualState Name</span></span>|<span data-ttu-id="f87e1-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="f87e1-111">VisualStateGroup Name</span></span>|<span data-ttu-id="f87e1-112">描述</span><span class="sxs-lookup"><span data-stu-id="f87e1-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f87e1-113">Closed</span><span class="sxs-lookup"><span data-stu-id="f87e1-113">Closed</span></span>|<span data-ttu-id="f87e1-114">OpenStates</span><span class="sxs-lookup"><span data-stu-id="f87e1-114">OpenStates</span></span>|<span data-ttu-id="f87e1-115">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="f87e1-115">The default state.</span></span>|  
|<span data-ttu-id="f87e1-116">開啟</span><span class="sxs-lookup"><span data-stu-id="f87e1-116">Open</span></span>|<span data-ttu-id="f87e1-117">OpenStates</span><span class="sxs-lookup"><span data-stu-id="f87e1-117">OpenStates</span></span>|<span data-ttu-id="f87e1-118"><xref:System.Windows.Controls.ToolTip>為可見。</span><span class="sxs-lookup"><span data-stu-id="f87e1-118">The <xref:System.Windows.Controls.ToolTip> is visible.</span></span>|  
|<span data-ttu-id="f87e1-119">驗證</span><span class="sxs-lookup"><span data-stu-id="f87e1-119">Valid</span></span>|<span data-ttu-id="f87e1-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f87e1-120">ValidationStates</span></span>|<span data-ttu-id="f87e1-121">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="f87e1-121">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="f87e1-122">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="f87e1-122">InvalidFocused</span></span>|<span data-ttu-id="f87e1-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f87e1-123">ValidationStates</span></span>|<span data-ttu-id="f87e1-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="f87e1-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="f87e1-125">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="f87e1-125">InvalidUnfocused</span></span>|<span data-ttu-id="f87e1-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f87e1-126">ValidationStates</span></span>|<span data-ttu-id="f87e1-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="f87e1-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tooltip-controltemplate-example"></a><span data-ttu-id="f87e1-128">工具提示 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="f87e1-128">ToolTip ControlTemplate Example</span></span>  
 <span data-ttu-id="f87e1-129">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.ToolTip>控制項。</span><span class="sxs-lookup"><span data-stu-id="f87e1-129">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tooltip.xaml#tooltip)]  
  
 <span data-ttu-id="f87e1-130">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="f87e1-130">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="f87e1-131">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="f87e1-131">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f87e1-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f87e1-132">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="f87e1-133">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="f87e1-133">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="f87e1-134">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="f87e1-134">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="f87e1-135">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="f87e1-135">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="f87e1-136">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="f87e1-136">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
