---
title: Frame 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], Frame
- templates [WPF], Frame
- ControlTemplate [WPF], Frame
- Frame [WPF], styles and templates
- states [WPF], Frame
- styles [WPF], Frame
ms.assetid: a01c32e2-c951-46a0-a82f-2614ca241f0b
ms.openlocfilehash: 89f4fc21637d20ca226507463093bc6bae2241fc
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460318"
---
# <a name="frame-styles-and-templates"></a><span data-ttu-id="3f7c6-102">Frame 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="3f7c6-102">Frame Styles and Templates</span></span>
<span data-ttu-id="3f7c6-103">本主題描述 <xref:System.Windows.Controls.Frame> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="3f7c6-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Frame> control.</span></span> <span data-ttu-id="3f7c6-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="3f7c6-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="3f7c6-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="3f7c6-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="frame-parts"></a><span data-ttu-id="3f7c6-106">框架元件</span><span class="sxs-lookup"><span data-stu-id="3f7c6-106">Frame Parts</span></span>  
 <span data-ttu-id="3f7c6-107">下表列出 <xref:System.Windows.Controls.Frame> 控制項的已命名元件。</span><span class="sxs-lookup"><span data-stu-id="3f7c6-107">The following table lists the named parts for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="3f7c6-108">組件</span><span class="sxs-lookup"><span data-stu-id="3f7c6-108">Part</span></span>|<span data-ttu-id="3f7c6-109">輸入</span><span class="sxs-lookup"><span data-stu-id="3f7c6-109">Type</span></span>|<span data-ttu-id="3f7c6-110">描述</span><span class="sxs-lookup"><span data-stu-id="3f7c6-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="3f7c6-111">PART_FrameCP</span><span class="sxs-lookup"><span data-stu-id="3f7c6-111">PART_FrameCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="3f7c6-112">內容區域。</span><span class="sxs-lookup"><span data-stu-id="3f7c6-112">The content area.</span></span>|  
  
## <a name="frame-states"></a><span data-ttu-id="3f7c6-113">畫面格狀態</span><span class="sxs-lookup"><span data-stu-id="3f7c6-113">Frame States</span></span>  
 <span data-ttu-id="3f7c6-114">下表列出 <xref:System.Windows.Controls.Frame> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="3f7c6-114">The following table lists the visual states for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="3f7c6-115">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="3f7c6-115">VisualState Name</span></span>|<span data-ttu-id="3f7c6-116">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="3f7c6-116">VisualStateGroup Name</span></span>|<span data-ttu-id="3f7c6-117">描述</span><span class="sxs-lookup"><span data-stu-id="3f7c6-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="3f7c6-118">驗證</span><span class="sxs-lookup"><span data-stu-id="3f7c6-118">Valid</span></span>|<span data-ttu-id="3f7c6-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3f7c6-119">ValidationStates</span></span>|<span data-ttu-id="3f7c6-120">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="3f7c6-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="3f7c6-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="3f7c6-121">InvalidFocused</span></span>|<span data-ttu-id="3f7c6-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3f7c6-122">ValidationStates</span></span>|<span data-ttu-id="3f7c6-123"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="3f7c6-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="3f7c6-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="3f7c6-124">InvalidUnfocused</span></span>|<span data-ttu-id="3f7c6-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3f7c6-125">ValidationStates</span></span>|<span data-ttu-id="3f7c6-126"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="3f7c6-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="frame-controltemplate-example"></a><span data-ttu-id="3f7c6-127">框架 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="3f7c6-127">Frame ControlTemplate Example</span></span>  
 <span data-ttu-id="3f7c6-128">下列範例顯示如何定義 <xref:System.Windows.Controls.Frame> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="3f7c6-128">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Frame](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/frame.xaml#frame)]  
  
 <span data-ttu-id="3f7c6-129">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="3f7c6-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="3f7c6-130">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="3f7c6-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f7c6-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="3f7c6-131">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="3f7c6-132">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="3f7c6-132">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="3f7c6-133">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="3f7c6-133">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="3f7c6-134">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="3f7c6-134">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="3f7c6-135">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="3f7c6-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
