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
ms.openlocfilehash: c7a14034d665c124d01e8a4b43c5d42968241925
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283652"
---
# <a name="tooltip-styles-and-templates"></a><span data-ttu-id="e491d-102">ToolTip 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="e491d-102">ToolTip Styles and Templates</span></span>
<span data-ttu-id="e491d-103">本主題描述 <xref:System.Windows.Controls.ToolTip> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="e491d-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolTip> control.</span></span> <span data-ttu-id="e491d-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="e491d-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="e491d-105">如需詳細資訊，請參閱[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。</span><span class="sxs-lookup"><span data-stu-id="e491d-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="tooltip-parts"></a><span data-ttu-id="e491d-106">工具提示元件</span><span class="sxs-lookup"><span data-stu-id="e491d-106">ToolTip Parts</span></span>  
 <span data-ttu-id="e491d-107"><xref:System.Windows.Controls.ToolTip> 控制項沒有任何已命名的元件。</span><span class="sxs-lookup"><span data-stu-id="e491d-107">The <xref:System.Windows.Controls.ToolTip> control does not have any named parts.</span></span>  
  
## <a name="tooltip-states"></a><span data-ttu-id="e491d-108">工具提示狀態</span><span class="sxs-lookup"><span data-stu-id="e491d-108">ToolTip States</span></span>  
 <span data-ttu-id="e491d-109">下表列出 <xref:System.Windows.Controls.ToolTip> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="e491d-109">The following table lists the visual states for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
|<span data-ttu-id="e491d-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="e491d-110">VisualState Name</span></span>|<span data-ttu-id="e491d-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="e491d-111">VisualStateGroup Name</span></span>|<span data-ttu-id="e491d-112">描述</span><span class="sxs-lookup"><span data-stu-id="e491d-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="e491d-113">Closed</span><span class="sxs-lookup"><span data-stu-id="e491d-113">Closed</span></span>|<span data-ttu-id="e491d-114">OpenStates</span><span class="sxs-lookup"><span data-stu-id="e491d-114">OpenStates</span></span>|<span data-ttu-id="e491d-115">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="e491d-115">The default state.</span></span>|  
|<span data-ttu-id="e491d-116">開啟</span><span class="sxs-lookup"><span data-stu-id="e491d-116">Open</span></span>|<span data-ttu-id="e491d-117">OpenStates</span><span class="sxs-lookup"><span data-stu-id="e491d-117">OpenStates</span></span>|<span data-ttu-id="e491d-118"><xref:System.Windows.Controls.ToolTip> 是可見的。</span><span class="sxs-lookup"><span data-stu-id="e491d-118">The <xref:System.Windows.Controls.ToolTip> is visible.</span></span>|  
|<span data-ttu-id="e491d-119">驗證</span><span class="sxs-lookup"><span data-stu-id="e491d-119">Valid</span></span>|<span data-ttu-id="e491d-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e491d-120">ValidationStates</span></span>|<span data-ttu-id="e491d-121">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="e491d-121">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="e491d-122">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="e491d-122">InvalidFocused</span></span>|<span data-ttu-id="e491d-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e491d-123">ValidationStates</span></span>|<span data-ttu-id="e491d-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="e491d-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="e491d-125">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="e491d-125">InvalidUnfocused</span></span>|<span data-ttu-id="e491d-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e491d-126">ValidationStates</span></span>|<span data-ttu-id="e491d-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="e491d-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tooltip-controltemplate-example"></a><span data-ttu-id="e491d-128">工具提示 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="e491d-128">ToolTip ControlTemplate Example</span></span>  
 <span data-ttu-id="e491d-129">下列範例顯示如何定義 <xref:System.Windows.Controls.ToolTip> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="e491d-129">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tooltip.xaml#tooltip)]  
  
 <span data-ttu-id="e491d-130">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="e491d-130">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="e491d-131">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="e491d-131">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e491d-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="e491d-132">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="e491d-133">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="e491d-133">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="e491d-134">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="e491d-134">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="e491d-135">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="e491d-135">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="e491d-136">建立控制項的範本</span><span class="sxs-lookup"><span data-stu-id="e491d-136">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
