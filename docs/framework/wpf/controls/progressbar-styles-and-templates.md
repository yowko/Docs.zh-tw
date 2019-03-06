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
ms.openlocfilehash: 7041a5497355a806894b0a0e0363fffde134aadb
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377246"
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="4eab2-102">ProgressBar 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="4eab2-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="4eab2-103">本主題描述的樣式和範本<xref:System.Windows.Controls.ProgressBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="4eab2-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="4eab2-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>，讓控制項的獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="4eab2-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="4eab2-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="4eab2-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="4eab2-106">ProgressBar 組件</span><span class="sxs-lookup"><span data-stu-id="4eab2-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="4eab2-107">下表列出的具名組件<xref:System.Windows.Controls.ProgressBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="4eab2-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="4eab2-108">組件</span><span class="sxs-lookup"><span data-stu-id="4eab2-108">Part</span></span>|<span data-ttu-id="4eab2-109">類型</span><span class="sxs-lookup"><span data-stu-id="4eab2-109">Type</span></span>|<span data-ttu-id="4eab2-110">描述</span><span class="sxs-lookup"><span data-stu-id="4eab2-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="4eab2-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="4eab2-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="4eab2-112">物件，表示進度。</span><span class="sxs-lookup"><span data-stu-id="4eab2-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="4eab2-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="4eab2-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="4eab2-114">定義進度列指示器的路徑的物件。</span><span class="sxs-lookup"><span data-stu-id="4eab2-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="4eab2-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="4eab2-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="4eab2-116">物件，embellishes 進度列。</span><span class="sxs-lookup"><span data-stu-id="4eab2-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="4eab2-117">進度列狀態</span><span class="sxs-lookup"><span data-stu-id="4eab2-117">ProgressBar States</span></span>  
 <span data-ttu-id="4eab2-118">下表列出的視覺狀態<xref:System.Windows.Controls.ProgressBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="4eab2-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="4eab2-119">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="4eab2-119">VisualState Name</span></span>|<span data-ttu-id="4eab2-120">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="4eab2-120">VisualStateGroup Name</span></span>|<span data-ttu-id="4eab2-121">描述</span><span class="sxs-lookup"><span data-stu-id="4eab2-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="4eab2-122">確定</span><span class="sxs-lookup"><span data-stu-id="4eab2-122">Determinate</span></span>|<span data-ttu-id="4eab2-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="4eab2-123">CommonStates</span></span>|<span data-ttu-id="4eab2-124"><xref:System.Windows.Controls.ProgressBar> 報告進度根據<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="4eab2-124"><xref:System.Windows.Controls.ProgressBar> reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="4eab2-125">不定</span><span class="sxs-lookup"><span data-stu-id="4eab2-125">Indeterminate</span></span>|<span data-ttu-id="4eab2-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="4eab2-126">CommonStates</span></span>|<span data-ttu-id="4eab2-127"><xref:System.Windows.Controls.ProgressBar> 報告的重複模式的泛型進度。</span><span class="sxs-lookup"><span data-stu-id="4eab2-127"><xref:System.Windows.Controls.ProgressBar> reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="4eab2-128">驗證</span><span class="sxs-lookup"><span data-stu-id="4eab2-128">Valid</span></span>|<span data-ttu-id="4eab2-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="4eab2-129">ValidationStates</span></span>|<span data-ttu-id="4eab2-130">控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。</span><span class="sxs-lookup"><span data-stu-id="4eab2-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="4eab2-131">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="4eab2-131">InvalidFocused</span></span>|<span data-ttu-id="4eab2-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="4eab2-132">ValidationStates</span></span>|<span data-ttu-id="4eab2-133"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。</span><span class="sxs-lookup"><span data-stu-id="4eab2-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="4eab2-134">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="4eab2-134">InvalidUnfocused</span></span>|<span data-ttu-id="4eab2-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="4eab2-135">ValidationStates</span></span>|<span data-ttu-id="4eab2-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="4eab2-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="4eab2-137">ProgressBar 的 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="4eab2-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="4eab2-138">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.ProgressBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="4eab2-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="4eab2-139">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="4eab2-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="4eab2-140">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="4eab2-140">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eab2-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4eab2-141">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="4eab2-142">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="4eab2-142">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="4eab2-143">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="4eab2-143">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="4eab2-144">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="4eab2-144">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="4eab2-145">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="4eab2-145">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
