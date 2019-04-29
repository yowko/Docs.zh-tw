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
ms.openlocfilehash: 24def466509c12eb69307de139e83dd5a1ed5ce4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790672"
---
# <a name="tooltip-styles-and-templates"></a><span data-ttu-id="079fc-102">ToolTip 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="079fc-102">ToolTip Styles and Templates</span></span>
<span data-ttu-id="079fc-103">本主題描述的樣式和範本<xref:System.Windows.Controls.ToolTip>控制項。</span><span class="sxs-lookup"><span data-stu-id="079fc-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolTip> control.</span></span> <span data-ttu-id="079fc-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>，讓控制項的獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="079fc-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="079fc-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="079fc-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="tooltip-parts"></a><span data-ttu-id="079fc-106">工具提示部分</span><span class="sxs-lookup"><span data-stu-id="079fc-106">ToolTip Parts</span></span>  
 <span data-ttu-id="079fc-107"><xref:System.Windows.Controls.ToolTip>控制項沒有任何具名組件。</span><span class="sxs-lookup"><span data-stu-id="079fc-107">The <xref:System.Windows.Controls.ToolTip> control does not have any named parts.</span></span>  
  
## <a name="tooltip-states"></a><span data-ttu-id="079fc-108">工具提示的狀態</span><span class="sxs-lookup"><span data-stu-id="079fc-108">ToolTip States</span></span>  
 <span data-ttu-id="079fc-109">下表列出的視覺狀態<xref:System.Windows.Controls.ToolTip>控制項。</span><span class="sxs-lookup"><span data-stu-id="079fc-109">The following table lists the visual states for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
|<span data-ttu-id="079fc-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="079fc-110">VisualState Name</span></span>|<span data-ttu-id="079fc-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="079fc-111">VisualStateGroup Name</span></span>|<span data-ttu-id="079fc-112">描述</span><span class="sxs-lookup"><span data-stu-id="079fc-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="079fc-113">Closed</span><span class="sxs-lookup"><span data-stu-id="079fc-113">Closed</span></span>|<span data-ttu-id="079fc-114">OpenStates</span><span class="sxs-lookup"><span data-stu-id="079fc-114">OpenStates</span></span>|<span data-ttu-id="079fc-115">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="079fc-115">The default state.</span></span>|  
|<span data-ttu-id="079fc-116">開啟</span><span class="sxs-lookup"><span data-stu-id="079fc-116">Open</span></span>|<span data-ttu-id="079fc-117">OpenStates</span><span class="sxs-lookup"><span data-stu-id="079fc-117">OpenStates</span></span>|<span data-ttu-id="079fc-118"><xref:System.Windows.Controls.ToolTip>為可見。</span><span class="sxs-lookup"><span data-stu-id="079fc-118">The <xref:System.Windows.Controls.ToolTip> is visible.</span></span>|  
|<span data-ttu-id="079fc-119">驗證</span><span class="sxs-lookup"><span data-stu-id="079fc-119">Valid</span></span>|<span data-ttu-id="079fc-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="079fc-120">ValidationStates</span></span>|<span data-ttu-id="079fc-121">控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。</span><span class="sxs-lookup"><span data-stu-id="079fc-121">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="079fc-122">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="079fc-122">InvalidFocused</span></span>|<span data-ttu-id="079fc-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="079fc-123">ValidationStates</span></span>|<span data-ttu-id="079fc-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。</span><span class="sxs-lookup"><span data-stu-id="079fc-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="079fc-125">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="079fc-125">InvalidUnfocused</span></span>|<span data-ttu-id="079fc-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="079fc-126">ValidationStates</span></span>|<span data-ttu-id="079fc-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="079fc-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tooltip-controltemplate-example"></a><span data-ttu-id="079fc-128">工具提示 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="079fc-128">ToolTip ControlTemplate Example</span></span>  
 <span data-ttu-id="079fc-129">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.ToolTip>控制項。</span><span class="sxs-lookup"><span data-stu-id="079fc-129">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tooltip.xaml#tooltip)]  
  
 <span data-ttu-id="079fc-130">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="079fc-130">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="079fc-131">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="079fc-131">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="079fc-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="079fc-132">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="079fc-133">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="079fc-133">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="079fc-134">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="079fc-134">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="079fc-135">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="079fc-135">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="079fc-136">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="079fc-136">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
