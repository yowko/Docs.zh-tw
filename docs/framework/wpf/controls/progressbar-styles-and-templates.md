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
ms.openlocfilehash: 6551701e86dd6abcd42f143f146c7bdadfeabbcf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283445"
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="83a2c-102">ProgressBar 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="83a2c-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="83a2c-103">本主題描述 <xref:System.Windows.Controls.ProgressBar> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="83a2c-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="83a2c-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="83a2c-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="83a2c-105">如需詳細資訊，請參閱[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。</span><span class="sxs-lookup"><span data-stu-id="83a2c-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="83a2c-106">ProgressBar 元件</span><span class="sxs-lookup"><span data-stu-id="83a2c-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="83a2c-107">下表列出 <xref:System.Windows.Controls.ProgressBar> 控制項的已命名元件。</span><span class="sxs-lookup"><span data-stu-id="83a2c-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="83a2c-108">組件</span><span class="sxs-lookup"><span data-stu-id="83a2c-108">Part</span></span>|<span data-ttu-id="83a2c-109">輸入</span><span class="sxs-lookup"><span data-stu-id="83a2c-109">Type</span></span>|<span data-ttu-id="83a2c-110">描述</span><span class="sxs-lookup"><span data-stu-id="83a2c-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="83a2c-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="83a2c-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="83a2c-112">表示進度的物件。</span><span class="sxs-lookup"><span data-stu-id="83a2c-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="83a2c-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="83a2c-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="83a2c-114">定義進度指標路徑的物件。</span><span class="sxs-lookup"><span data-stu-id="83a2c-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="83a2c-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="83a2c-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="83a2c-116">Embellishes 進度列的物件。</span><span class="sxs-lookup"><span data-stu-id="83a2c-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="83a2c-117">ProgressBar 狀態</span><span class="sxs-lookup"><span data-stu-id="83a2c-117">ProgressBar States</span></span>  
 <span data-ttu-id="83a2c-118">下表列出 <xref:System.Windows.Controls.ProgressBar> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="83a2c-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="83a2c-119">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="83a2c-119">VisualState Name</span></span>|<span data-ttu-id="83a2c-120">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="83a2c-120">VisualStateGroup Name</span></span>|<span data-ttu-id="83a2c-121">描述</span><span class="sxs-lookup"><span data-stu-id="83a2c-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="83a2c-122">確定</span><span class="sxs-lookup"><span data-stu-id="83a2c-122">Determinate</span></span>|<span data-ttu-id="83a2c-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="83a2c-123">CommonStates</span></span>|<span data-ttu-id="83a2c-124"><xref:System.Windows.Controls.ProgressBar> 會根據 <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> 屬性來報告進度。</span><span class="sxs-lookup"><span data-stu-id="83a2c-124"><xref:System.Windows.Controls.ProgressBar> reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="83a2c-125">處於</span><span class="sxs-lookup"><span data-stu-id="83a2c-125">Indeterminate</span></span>|<span data-ttu-id="83a2c-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="83a2c-126">CommonStates</span></span>|<span data-ttu-id="83a2c-127"><xref:System.Windows.Controls.ProgressBar> 會以重複模式來報告一般進度。</span><span class="sxs-lookup"><span data-stu-id="83a2c-127"><xref:System.Windows.Controls.ProgressBar> reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="83a2c-128">驗證</span><span class="sxs-lookup"><span data-stu-id="83a2c-128">Valid</span></span>|<span data-ttu-id="83a2c-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="83a2c-129">ValidationStates</span></span>|<span data-ttu-id="83a2c-130">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="83a2c-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="83a2c-131">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="83a2c-131">InvalidFocused</span></span>|<span data-ttu-id="83a2c-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="83a2c-132">ValidationStates</span></span>|<span data-ttu-id="83a2c-133"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="83a2c-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="83a2c-134">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="83a2c-134">InvalidUnfocused</span></span>|<span data-ttu-id="83a2c-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="83a2c-135">ValidationStates</span></span>|<span data-ttu-id="83a2c-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="83a2c-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="83a2c-137">ProgressBar ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="83a2c-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="83a2c-138">下列範例顯示如何定義 <xref:System.Windows.Controls.ProgressBar> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="83a2c-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="83a2c-139">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="83a2c-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="83a2c-140">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="83a2c-140">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83a2c-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="83a2c-141">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="83a2c-142">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="83a2c-142">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="83a2c-143">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="83a2c-143">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="83a2c-144">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="83a2c-144">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="83a2c-145">建立控制項的範本</span><span class="sxs-lookup"><span data-stu-id="83a2c-145">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
