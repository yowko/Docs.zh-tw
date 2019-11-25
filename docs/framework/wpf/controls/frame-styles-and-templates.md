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
ms.openlocfilehash: de853198c97c99319bea4a816c9a6eca5dc5d917
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283737"
---
# <a name="frame-styles-and-templates"></a><span data-ttu-id="3fa9f-102">Frame 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="3fa9f-102">Frame Styles and Templates</span></span>
<span data-ttu-id="3fa9f-103">本主題描述 <xref:System.Windows.Controls.Frame> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="3fa9f-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Frame> control.</span></span> <span data-ttu-id="3fa9f-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="3fa9f-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="3fa9f-105">如需詳細資訊，請參閱[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。</span><span class="sxs-lookup"><span data-stu-id="3fa9f-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="frame-parts"></a><span data-ttu-id="3fa9f-106">框架元件</span><span class="sxs-lookup"><span data-stu-id="3fa9f-106">Frame Parts</span></span>  
 <span data-ttu-id="3fa9f-107">下表列出 <xref:System.Windows.Controls.Frame> 控制項的已命名元件。</span><span class="sxs-lookup"><span data-stu-id="3fa9f-107">The following table lists the named parts for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="3fa9f-108">組件</span><span class="sxs-lookup"><span data-stu-id="3fa9f-108">Part</span></span>|<span data-ttu-id="3fa9f-109">輸入</span><span class="sxs-lookup"><span data-stu-id="3fa9f-109">Type</span></span>|<span data-ttu-id="3fa9f-110">描述</span><span class="sxs-lookup"><span data-stu-id="3fa9f-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="3fa9f-111">PART_FrameCP</span><span class="sxs-lookup"><span data-stu-id="3fa9f-111">PART_FrameCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="3fa9f-112">內容區域。</span><span class="sxs-lookup"><span data-stu-id="3fa9f-112">The content area.</span></span>|  
  
## <a name="frame-states"></a><span data-ttu-id="3fa9f-113">畫面格狀態</span><span class="sxs-lookup"><span data-stu-id="3fa9f-113">Frame States</span></span>  
 <span data-ttu-id="3fa9f-114">下表列出 <xref:System.Windows.Controls.Frame> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="3fa9f-114">The following table lists the visual states for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="3fa9f-115">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="3fa9f-115">VisualState Name</span></span>|<span data-ttu-id="3fa9f-116">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="3fa9f-116">VisualStateGroup Name</span></span>|<span data-ttu-id="3fa9f-117">描述</span><span class="sxs-lookup"><span data-stu-id="3fa9f-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="3fa9f-118">驗證</span><span class="sxs-lookup"><span data-stu-id="3fa9f-118">Valid</span></span>|<span data-ttu-id="3fa9f-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3fa9f-119">ValidationStates</span></span>|<span data-ttu-id="3fa9f-120">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="3fa9f-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="3fa9f-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="3fa9f-121">InvalidFocused</span></span>|<span data-ttu-id="3fa9f-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3fa9f-122">ValidationStates</span></span>|<span data-ttu-id="3fa9f-123"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="3fa9f-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="3fa9f-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="3fa9f-124">InvalidUnfocused</span></span>|<span data-ttu-id="3fa9f-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3fa9f-125">ValidationStates</span></span>|<span data-ttu-id="3fa9f-126"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="3fa9f-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="frame-controltemplate-example"></a><span data-ttu-id="3fa9f-127">框架 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="3fa9f-127">Frame ControlTemplate Example</span></span>  
 <span data-ttu-id="3fa9f-128">下列範例顯示如何定義 <xref:System.Windows.Controls.Frame> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="3fa9f-128">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Frame](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/frame.xaml#frame)]  
  
 <span data-ttu-id="3fa9f-129">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="3fa9f-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="3fa9f-130">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="3fa9f-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fa9f-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="3fa9f-131">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="3fa9f-132">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="3fa9f-132">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="3fa9f-133">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="3fa9f-133">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="3fa9f-134">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="3fa9f-134">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="3fa9f-135">建立控制項的範本</span><span class="sxs-lookup"><span data-stu-id="3fa9f-135">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
