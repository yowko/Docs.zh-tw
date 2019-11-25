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
ms.openlocfilehash: 843c9003edbe94115719a63a968eda3833515a85
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283378"
---
# <a name="statusbar-styles-and-templates"></a><span data-ttu-id="1c930-102">StatusBar 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="1c930-102">StatusBar Styles and Templates</span></span>
<span data-ttu-id="1c930-103">本主題描述 <xref:System.Windows.Controls.Primitives.StatusBar> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="1c930-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span> <span data-ttu-id="1c930-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="1c930-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="1c930-105">如需詳細資訊，請參閱[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。</span><span class="sxs-lookup"><span data-stu-id="1c930-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="statusbar-parts"></a><span data-ttu-id="1c930-106">狀態列部分</span><span class="sxs-lookup"><span data-stu-id="1c930-106">StatusBar Parts</span></span>  
 <span data-ttu-id="1c930-107"><xref:System.Windows.Controls.Primitives.StatusBar> 控制項沒有任何已命名的元件。</span><span class="sxs-lookup"><span data-stu-id="1c930-107">The <xref:System.Windows.Controls.Primitives.StatusBar> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="1c930-108">狀態列狀態</span><span class="sxs-lookup"><span data-stu-id="1c930-108">StatusBar States</span></span>  
 <span data-ttu-id="1c930-109">下表列出 <xref:System.Windows.Controls.Primitives.StatusBar> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="1c930-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
|<span data-ttu-id="1c930-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="1c930-110">VisualState Name</span></span>|<span data-ttu-id="1c930-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="1c930-111">VisualStateGroup Name</span></span>|<span data-ttu-id="1c930-112">描述</span><span class="sxs-lookup"><span data-stu-id="1c930-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="1c930-113">驗證</span><span class="sxs-lookup"><span data-stu-id="1c930-113">Valid</span></span>|<span data-ttu-id="1c930-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1c930-114">ValidationStates</span></span>|<span data-ttu-id="1c930-115">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="1c930-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="1c930-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="1c930-116">InvalidFocused</span></span>|<span data-ttu-id="1c930-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1c930-117">ValidationStates</span></span>|<span data-ttu-id="1c930-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="1c930-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="1c930-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="1c930-119">InvalidUnfocused</span></span>|<span data-ttu-id="1c930-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1c930-120">ValidationStates</span></span>|<span data-ttu-id="1c930-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="1c930-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbaritem-parts"></a><span data-ttu-id="1c930-122">StatusBarItem 元件</span><span class="sxs-lookup"><span data-stu-id="1c930-122">StatusBarItem Parts</span></span>  
 <span data-ttu-id="1c930-123"><xref:System.Windows.Controls.Primitives.StatusBarItem> 控制項沒有任何已命名的元件。</span><span class="sxs-lookup"><span data-stu-id="1c930-123">The <xref:System.Windows.Controls.Primitives.StatusBarItem> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="1c930-124">狀態列狀態</span><span class="sxs-lookup"><span data-stu-id="1c930-124">StatusBar States</span></span>  
 <span data-ttu-id="1c930-125">下表列出 <xref:System.Windows.Controls.Primitives.StatusBarItem> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="1c930-125">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBarItem> control.</span></span>  
  
|<span data-ttu-id="1c930-126">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="1c930-126">VisualState Name</span></span>|<span data-ttu-id="1c930-127">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="1c930-127">VisualStateGroup Name</span></span>|<span data-ttu-id="1c930-128">描述</span><span class="sxs-lookup"><span data-stu-id="1c930-128">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="1c930-129">驗證</span><span class="sxs-lookup"><span data-stu-id="1c930-129">Valid</span></span>|<span data-ttu-id="1c930-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1c930-130">ValidationStates</span></span>|<span data-ttu-id="1c930-131">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="1c930-131">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="1c930-132">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="1c930-132">InvalidFocused</span></span>|<span data-ttu-id="1c930-133">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1c930-133">ValidationStates</span></span>|<span data-ttu-id="1c930-134"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="1c930-134">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="1c930-135">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="1c930-135">InvalidUnfocused</span></span>|<span data-ttu-id="1c930-136">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1c930-136">ValidationStates</span></span>|<span data-ttu-id="1c930-137"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="1c930-137">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbar-controltemplate-example"></a><span data-ttu-id="1c930-138">狀態列 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="1c930-138">StatusBar ControlTemplate Example</span></span>  
 <span data-ttu-id="1c930-139">下列範例顯示如何定義 <xref:System.Windows.Controls.Primitives.StatusBar> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="1c930-139">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#StatusBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/statusbar.xaml#statusbar)]  
  
 <span data-ttu-id="1c930-140"><xref:System.Windows.Controls.ControlTemplate> 會使用下列一或多個資源。</span><span class="sxs-lookup"><span data-stu-id="1c930-140">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="1c930-141">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="1c930-141">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c930-142">請參閱</span><span class="sxs-lookup"><span data-stu-id="1c930-142">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="1c930-143">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="1c930-143">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="1c930-144">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="1c930-144">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="1c930-145">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="1c930-145">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="1c930-146">建立控制項的範本</span><span class="sxs-lookup"><span data-stu-id="1c930-146">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
