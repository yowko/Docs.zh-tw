---
title: StatusBar 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], StatusBar
- styles [WPF], StatusBar
- templates [WPF], StatusBar
- states [WPF], StatusBar
- parts [WPF], StatusBar
- StatusBar [WPF], styles and templates
ms.assetid: 9f5e1c25-81eb-4756-a0ac-d9e1fbe33ee2
ms.openlocfilehash: ee3bd060268d5ab6f713a74f871d7de0dd77782b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660459"
---
# <a name="statusbar-styles-and-templates"></a><span data-ttu-id="3c94d-102">StatusBar 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="3c94d-102">StatusBar Styles and Templates</span></span>
<span data-ttu-id="3c94d-103">本主題描述的樣式和範本<xref:System.Windows.Controls.Primitives.StatusBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="3c94d-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span> <span data-ttu-id="3c94d-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>，讓控制項的獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="3c94d-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="3c94d-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="3c94d-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="statusbar-parts"></a><span data-ttu-id="3c94d-106">StatusBar 組件</span><span class="sxs-lookup"><span data-stu-id="3c94d-106">StatusBar Parts</span></span>  
 <span data-ttu-id="3c94d-107"><xref:System.Windows.Controls.Primitives.StatusBar>控制項沒有任何具名組件。</span><span class="sxs-lookup"><span data-stu-id="3c94d-107">The <xref:System.Windows.Controls.Primitives.StatusBar> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="3c94d-108">StatusBar 狀態</span><span class="sxs-lookup"><span data-stu-id="3c94d-108">StatusBar States</span></span>  
 <span data-ttu-id="3c94d-109">下表列出的視覺狀態<xref:System.Windows.Controls.Primitives.StatusBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="3c94d-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
|<span data-ttu-id="3c94d-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="3c94d-110">VisualState Name</span></span>|<span data-ttu-id="3c94d-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="3c94d-111">VisualStateGroup Name</span></span>|<span data-ttu-id="3c94d-112">描述</span><span class="sxs-lookup"><span data-stu-id="3c94d-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="3c94d-113">驗證</span><span class="sxs-lookup"><span data-stu-id="3c94d-113">Valid</span></span>|<span data-ttu-id="3c94d-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3c94d-114">ValidationStates</span></span>|<span data-ttu-id="3c94d-115">控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。</span><span class="sxs-lookup"><span data-stu-id="3c94d-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="3c94d-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="3c94d-116">InvalidFocused</span></span>|<span data-ttu-id="3c94d-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3c94d-117">ValidationStates</span></span>|<span data-ttu-id="3c94d-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。</span><span class="sxs-lookup"><span data-stu-id="3c94d-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="3c94d-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="3c94d-119">InvalidUnfocused</span></span>|<span data-ttu-id="3c94d-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3c94d-120">ValidationStates</span></span>|<span data-ttu-id="3c94d-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="3c94d-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbaritem-parts"></a><span data-ttu-id="3c94d-122">StatusBarItem 組件</span><span class="sxs-lookup"><span data-stu-id="3c94d-122">StatusBarItem Parts</span></span>  
 <span data-ttu-id="3c94d-123"><xref:System.Windows.Controls.Primitives.StatusBarItem>控制項沒有任何具名組件。</span><span class="sxs-lookup"><span data-stu-id="3c94d-123">The <xref:System.Windows.Controls.Primitives.StatusBarItem> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="3c94d-124">StatusBar 狀態</span><span class="sxs-lookup"><span data-stu-id="3c94d-124">StatusBar States</span></span>  
 <span data-ttu-id="3c94d-125">下表列出的視覺狀態<xref:System.Windows.Controls.Primitives.StatusBarItem>控制項。</span><span class="sxs-lookup"><span data-stu-id="3c94d-125">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBarItem> control.</span></span>  
  
|<span data-ttu-id="3c94d-126">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="3c94d-126">VisualState Name</span></span>|<span data-ttu-id="3c94d-127">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="3c94d-127">VisualStateGroup Name</span></span>|<span data-ttu-id="3c94d-128">描述</span><span class="sxs-lookup"><span data-stu-id="3c94d-128">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="3c94d-129">驗證</span><span class="sxs-lookup"><span data-stu-id="3c94d-129">Valid</span></span>|<span data-ttu-id="3c94d-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3c94d-130">ValidationStates</span></span>|<span data-ttu-id="3c94d-131">控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。</span><span class="sxs-lookup"><span data-stu-id="3c94d-131">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="3c94d-132">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="3c94d-132">InvalidFocused</span></span>|<span data-ttu-id="3c94d-133">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3c94d-133">ValidationStates</span></span>|<span data-ttu-id="3c94d-134"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。</span><span class="sxs-lookup"><span data-stu-id="3c94d-134">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="3c94d-135">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="3c94d-135">InvalidUnfocused</span></span>|<span data-ttu-id="3c94d-136">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3c94d-136">ValidationStates</span></span>|<span data-ttu-id="3c94d-137"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="3c94d-137">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbar-controltemplate-example"></a><span data-ttu-id="3c94d-138">StatusBar ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="3c94d-138">StatusBar ControlTemplate Example</span></span>  
 <span data-ttu-id="3c94d-139">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.Primitives.StatusBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="3c94d-139">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#StatusBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/statusbar.xaml#statusbar)]  
  
 <span data-ttu-id="3c94d-140"><xref:System.Windows.Controls.ControlTemplate>會使用一個或多個下列資源。</span><span class="sxs-lookup"><span data-stu-id="3c94d-140">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="3c94d-141">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="3c94d-141">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c94d-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c94d-142">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="3c94d-143">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="3c94d-143">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [<span data-ttu-id="3c94d-144">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="3c94d-144">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)
- [<span data-ttu-id="3c94d-145">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="3c94d-145">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="3c94d-146">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="3c94d-146">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
