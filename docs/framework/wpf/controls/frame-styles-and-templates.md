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
ms.openlocfilehash: 0d6860af587da89094663779c894689e8a911af8
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357387"
---
# <a name="frame-styles-and-templates"></a><span data-ttu-id="5146c-102">Frame 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="5146c-102">Frame Styles and Templates</span></span>
<span data-ttu-id="5146c-103">本主題描述的樣式和範本<xref:System.Windows.Controls.Frame>控制項。</span><span class="sxs-lookup"><span data-stu-id="5146c-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Frame> control.</span></span> <span data-ttu-id="5146c-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>，讓控制項的獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="5146c-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="5146c-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="5146c-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="frame-parts"></a><span data-ttu-id="5146c-106">框架組件</span><span class="sxs-lookup"><span data-stu-id="5146c-106">Frame Parts</span></span>  
 <span data-ttu-id="5146c-107">下表列出的具名組件<xref:System.Windows.Controls.Frame>控制項。</span><span class="sxs-lookup"><span data-stu-id="5146c-107">The following table lists the named parts for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="5146c-108">組件</span><span class="sxs-lookup"><span data-stu-id="5146c-108">Part</span></span>|<span data-ttu-id="5146c-109">類型</span><span class="sxs-lookup"><span data-stu-id="5146c-109">Type</span></span>|<span data-ttu-id="5146c-110">描述</span><span class="sxs-lookup"><span data-stu-id="5146c-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="5146c-111">PART_FrameCP</span><span class="sxs-lookup"><span data-stu-id="5146c-111">PART_FrameCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="5146c-112">內容區域中。</span><span class="sxs-lookup"><span data-stu-id="5146c-112">The content area.</span></span>|  
  
## <a name="frame-states"></a><span data-ttu-id="5146c-113">框架狀態</span><span class="sxs-lookup"><span data-stu-id="5146c-113">Frame States</span></span>  
 <span data-ttu-id="5146c-114">下表列出的視覺狀態<xref:System.Windows.Controls.Frame>控制項。</span><span class="sxs-lookup"><span data-stu-id="5146c-114">The following table lists the visual states for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="5146c-115">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="5146c-115">VisualState Name</span></span>|<span data-ttu-id="5146c-116">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="5146c-116">VisualStateGroup Name</span></span>|<span data-ttu-id="5146c-117">描述</span><span class="sxs-lookup"><span data-stu-id="5146c-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="5146c-118">驗證</span><span class="sxs-lookup"><span data-stu-id="5146c-118">Valid</span></span>|<span data-ttu-id="5146c-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5146c-119">ValidationStates</span></span>|<span data-ttu-id="5146c-120">控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。</span><span class="sxs-lookup"><span data-stu-id="5146c-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="5146c-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="5146c-121">InvalidFocused</span></span>|<span data-ttu-id="5146c-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5146c-122">ValidationStates</span></span>|<span data-ttu-id="5146c-123"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。</span><span class="sxs-lookup"><span data-stu-id="5146c-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="5146c-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="5146c-124">InvalidUnfocused</span></span>|<span data-ttu-id="5146c-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5146c-125">ValidationStates</span></span>|<span data-ttu-id="5146c-126"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="5146c-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="frame-controltemplate-example"></a><span data-ttu-id="5146c-127">框架 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="5146c-127">Frame ControlTemplate Example</span></span>  
 <span data-ttu-id="5146c-128">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.Frame>控制項。</span><span class="sxs-lookup"><span data-stu-id="5146c-128">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Frame](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/frame.xaml#frame)]  
  
 <span data-ttu-id="5146c-129">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="5146c-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="5146c-130">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="5146c-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5146c-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5146c-131">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="5146c-132">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="5146c-132">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="5146c-133">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="5146c-133">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="5146c-134">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="5146c-134">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="5146c-135">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="5146c-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
