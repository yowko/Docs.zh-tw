---
title: "Frame 樣式和範本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], Frame
- templates [WPF], Frame
- ControlTemplate [WPF], Frame
- Frame [WPF], styles and templates
- states [WPF], Frame
- styles [WPF], Frame
ms.assetid: a01c32e2-c951-46a0-a82f-2614ca241f0b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 603c4f766b836c7a301cc151112457ddb0972d10
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="frame-styles-and-templates"></a><span data-ttu-id="6e1a1-102">Frame 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="6e1a1-102">Frame Styles and Templates</span></span>
<span data-ttu-id="6e1a1-103">本主題描述樣式和範本<xref:System.Windows.Controls.Frame>控制項。</span><span class="sxs-lookup"><span data-stu-id="6e1a1-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Frame> control.</span></span> <span data-ttu-id="6e1a1-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="6e1a1-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="6e1a1-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="6e1a1-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="frame-parts"></a><span data-ttu-id="6e1a1-106">框架組件</span><span class="sxs-lookup"><span data-stu-id="6e1a1-106">Frame Parts</span></span>  
 <span data-ttu-id="6e1a1-107">下表列出的具名組件<xref:System.Windows.Controls.Frame>控制項。</span><span class="sxs-lookup"><span data-stu-id="6e1a1-107">The following table lists the named parts for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="6e1a1-108">組件</span><span class="sxs-lookup"><span data-stu-id="6e1a1-108">Part</span></span>|<span data-ttu-id="6e1a1-109">類型</span><span class="sxs-lookup"><span data-stu-id="6e1a1-109">Type</span></span>|<span data-ttu-id="6e1a1-110">說明</span><span class="sxs-lookup"><span data-stu-id="6e1a1-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6e1a1-111">PART_FrameCP</span><span class="sxs-lookup"><span data-stu-id="6e1a1-111">PART_FrameCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="6e1a1-112">內容區域中。</span><span class="sxs-lookup"><span data-stu-id="6e1a1-112">The content area.</span></span>|  
  
## <a name="frame-states"></a><span data-ttu-id="6e1a1-113">畫面格的狀態</span><span class="sxs-lookup"><span data-stu-id="6e1a1-113">Frame States</span></span>  
 <span data-ttu-id="6e1a1-114">下表列出的視覺狀態<xref:System.Windows.Controls.Frame>控制項。</span><span class="sxs-lookup"><span data-stu-id="6e1a1-114">The following table lists the visual states for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="6e1a1-115">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="6e1a1-115">VisualState Name</span></span>|<span data-ttu-id="6e1a1-116">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="6e1a1-116">VisualStateGroup Name</span></span>|<span data-ttu-id="6e1a1-117">描述</span><span class="sxs-lookup"><span data-stu-id="6e1a1-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6e1a1-118">驗證</span><span class="sxs-lookup"><span data-stu-id="6e1a1-118">Valid</span></span>|<span data-ttu-id="6e1a1-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6e1a1-119">ValidationStates</span></span>|<span data-ttu-id="6e1a1-120">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="6e1a1-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="6e1a1-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="6e1a1-121">InvalidFocused</span></span>|<span data-ttu-id="6e1a1-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6e1a1-122">ValidationStates</span></span>|<span data-ttu-id="6e1a1-123"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="6e1a1-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="6e1a1-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="6e1a1-124">InvalidUnfocused</span></span>|<span data-ttu-id="6e1a1-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6e1a1-125">ValidationStates</span></span>|<span data-ttu-id="6e1a1-126"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="6e1a1-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="frame-controltemplate-example"></a><span data-ttu-id="6e1a1-127">框架 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="6e1a1-127">Frame ControlTemplate Example</span></span>  
 <span data-ttu-id="6e1a1-128">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.Frame>控制項。</span><span class="sxs-lookup"><span data-stu-id="6e1a1-128">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Frame](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/frame.xaml#frame)]  
  
 <span data-ttu-id="6e1a1-129">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="6e1a1-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="6e1a1-130">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041)。</span><span class="sxs-lookup"><span data-stu-id="6e1a1-130">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e1a1-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e1a1-131">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="6e1a1-132">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="6e1a1-132">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="6e1a1-133">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="6e1a1-133">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="6e1a1-134">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="6e1a1-134">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="6e1a1-135">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="6e1a1-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
