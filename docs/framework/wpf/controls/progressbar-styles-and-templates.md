---
title: ProgressBar 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ProgressBar
- ProgressBar [WPF], styles and templates
- styles [WPF], ProgressBar
- ControlTemplate [WPF], ProgressBar
- templates [WPF], ProgressBar
- states [WPF], ProgressBar
ms.assetid: 935aa600-16e6-4947-a905-37a189a583dd
ms.openlocfilehash: 89aea3e80fe17ece8a17f62f62290d34ddd55c60
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
ms.locfileid: "34456919"
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="d913b-102">ProgressBar 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="d913b-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="d913b-103">本主題描述樣式和範本<xref:System.Windows.Controls.ProgressBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="d913b-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="d913b-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="d913b-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="d913b-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="d913b-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="d913b-106">ProgressBar 組件</span><span class="sxs-lookup"><span data-stu-id="d913b-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="d913b-107">下表列出的具名組件<xref:System.Windows.Controls.ProgressBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="d913b-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="d913b-108">組件</span><span class="sxs-lookup"><span data-stu-id="d913b-108">Part</span></span>|<span data-ttu-id="d913b-109">類型</span><span class="sxs-lookup"><span data-stu-id="d913b-109">Type</span></span>|<span data-ttu-id="d913b-110">描述</span><span class="sxs-lookup"><span data-stu-id="d913b-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d913b-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="d913b-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="d913b-112">物件，表示進度。</span><span class="sxs-lookup"><span data-stu-id="d913b-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="d913b-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="d913b-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="d913b-114">定義進度列指示器的路徑物件。</span><span class="sxs-lookup"><span data-stu-id="d913b-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="d913b-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="d913b-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="d913b-116">物件，embellishes 進度列。</span><span class="sxs-lookup"><span data-stu-id="d913b-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="d913b-117">進度列狀態</span><span class="sxs-lookup"><span data-stu-id="d913b-117">ProgressBar States</span></span>  
 <span data-ttu-id="d913b-118">下表列出的視覺狀態<xref:System.Windows.Controls.ProgressBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="d913b-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="d913b-119">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="d913b-119">VisualState Name</span></span>|<span data-ttu-id="d913b-120">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="d913b-120">VisualStateGroup Name</span></span>|<span data-ttu-id="d913b-121">描述</span><span class="sxs-lookup"><span data-stu-id="d913b-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="d913b-122">確定</span><span class="sxs-lookup"><span data-stu-id="d913b-122">Determinate</span></span>|<span data-ttu-id="d913b-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d913b-123">CommonStates</span></span>|<span data-ttu-id="d913b-124"><xref:System.Windows.Controls.ProgressBar> 報告進度根據<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="d913b-124"><xref:System.Windows.Controls.ProgressBar> reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="d913b-125">不定</span><span class="sxs-lookup"><span data-stu-id="d913b-125">Indeterminate</span></span>|<span data-ttu-id="d913b-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d913b-126">CommonStates</span></span>|<span data-ttu-id="d913b-127"><xref:System.Windows.Controls.ProgressBar> 報告泛型的進度，以重複模式。</span><span class="sxs-lookup"><span data-stu-id="d913b-127"><xref:System.Windows.Controls.ProgressBar> reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="d913b-128">驗證</span><span class="sxs-lookup"><span data-stu-id="d913b-128">Valid</span></span>|<span data-ttu-id="d913b-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d913b-129">ValidationStates</span></span>|<span data-ttu-id="d913b-130">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="d913b-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d913b-131">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d913b-131">InvalidFocused</span></span>|<span data-ttu-id="d913b-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d913b-132">ValidationStates</span></span>|<span data-ttu-id="d913b-133"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="d913b-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d913b-134">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d913b-134">InvalidUnfocused</span></span>|<span data-ttu-id="d913b-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d913b-135">ValidationStates</span></span>|<span data-ttu-id="d913b-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="d913b-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="d913b-137">ProgressBar ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="d913b-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="d913b-138">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.ProgressBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="d913b-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="d913b-139">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="d913b-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="d913b-140">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="d913b-140">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d913b-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d913b-141">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="d913b-142">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="d913b-142">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="d913b-143">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="d913b-143">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="d913b-144">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="d913b-144">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="d913b-145">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="d913b-145">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
