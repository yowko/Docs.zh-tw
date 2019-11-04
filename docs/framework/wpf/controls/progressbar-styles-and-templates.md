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
ms.openlocfilehash: 3a1bea39ba9b6d2cff9937a3fee1d1de41daf16b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459879"
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="cf591-102">ProgressBar 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="cf591-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="cf591-103">本主題描述 <xref:System.Windows.Controls.ProgressBar> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="cf591-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="cf591-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="cf591-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="cf591-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="cf591-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="cf591-106">ProgressBar 元件</span><span class="sxs-lookup"><span data-stu-id="cf591-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="cf591-107">下表列出 <xref:System.Windows.Controls.ProgressBar> 控制項的已命名元件。</span><span class="sxs-lookup"><span data-stu-id="cf591-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="cf591-108">組件</span><span class="sxs-lookup"><span data-stu-id="cf591-108">Part</span></span>|<span data-ttu-id="cf591-109">輸入</span><span class="sxs-lookup"><span data-stu-id="cf591-109">Type</span></span>|<span data-ttu-id="cf591-110">描述</span><span class="sxs-lookup"><span data-stu-id="cf591-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="cf591-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="cf591-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="cf591-112">表示進度的物件。</span><span class="sxs-lookup"><span data-stu-id="cf591-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="cf591-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="cf591-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="cf591-114">定義進度指標路徑的物件。</span><span class="sxs-lookup"><span data-stu-id="cf591-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="cf591-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="cf591-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="cf591-116">Embellishes 進度列的物件。</span><span class="sxs-lookup"><span data-stu-id="cf591-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="cf591-117">ProgressBar 狀態</span><span class="sxs-lookup"><span data-stu-id="cf591-117">ProgressBar States</span></span>  
 <span data-ttu-id="cf591-118">下表列出 <xref:System.Windows.Controls.ProgressBar> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="cf591-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="cf591-119">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="cf591-119">VisualState Name</span></span>|<span data-ttu-id="cf591-120">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="cf591-120">VisualStateGroup Name</span></span>|<span data-ttu-id="cf591-121">描述</span><span class="sxs-lookup"><span data-stu-id="cf591-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="cf591-122">確定</span><span class="sxs-lookup"><span data-stu-id="cf591-122">Determinate</span></span>|<span data-ttu-id="cf591-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="cf591-123">CommonStates</span></span>|<span data-ttu-id="cf591-124"><xref:System.Windows.Controls.ProgressBar> 會根據 <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> 屬性來報告進度。</span><span class="sxs-lookup"><span data-stu-id="cf591-124"><xref:System.Windows.Controls.ProgressBar> reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="cf591-125">處於</span><span class="sxs-lookup"><span data-stu-id="cf591-125">Indeterminate</span></span>|<span data-ttu-id="cf591-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="cf591-126">CommonStates</span></span>|<span data-ttu-id="cf591-127"><xref:System.Windows.Controls.ProgressBar> 會以重複模式來報告一般進度。</span><span class="sxs-lookup"><span data-stu-id="cf591-127"><xref:System.Windows.Controls.ProgressBar> reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="cf591-128">驗證</span><span class="sxs-lookup"><span data-stu-id="cf591-128">Valid</span></span>|<span data-ttu-id="cf591-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="cf591-129">ValidationStates</span></span>|<span data-ttu-id="cf591-130">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="cf591-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="cf591-131">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="cf591-131">InvalidFocused</span></span>|<span data-ttu-id="cf591-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="cf591-132">ValidationStates</span></span>|<span data-ttu-id="cf591-133"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="cf591-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="cf591-134">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="cf591-134">InvalidUnfocused</span></span>|<span data-ttu-id="cf591-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="cf591-135">ValidationStates</span></span>|<span data-ttu-id="cf591-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="cf591-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="cf591-137">ProgressBar ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="cf591-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="cf591-138">下列範例顯示如何定義 <xref:System.Windows.Controls.ProgressBar> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="cf591-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="cf591-139">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="cf591-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="cf591-140">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="cf591-140">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf591-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="cf591-141">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="cf591-142">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="cf591-142">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="cf591-143">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="cf591-143">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="cf591-144">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="cf591-144">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="cf591-145">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="cf591-145">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
