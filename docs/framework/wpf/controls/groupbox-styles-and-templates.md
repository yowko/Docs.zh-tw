---
title: GroupBox 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], GroupBox
- parts [WPF], GroupBox
- GroupBox [WPF], styles and templates
- states [WPF], GroupBox
- styles [WPF], GroupBox
- templates [WPF], GroupBox
ms.assetid: 33df7037-0a1b-476f-b9d0-41566a777699
ms.openlocfilehash: 474cda0abc6a18c015836c749c78f4d33aa5abd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187483"
---
# <a name="groupbox-styles-and-templates"></a><span data-ttu-id="2f783-102">GroupBox 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="2f783-102">GroupBox Styles and Templates</span></span>
<a name="introduction"></a><span data-ttu-id="2f783-103">本主題介紹控制項的<xref:System.Windows.Controls.GroupBox>樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="2f783-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.GroupBox> control.</span></span> <span data-ttu-id="2f783-104">您可以修改預設值<xref:System.Windows.Controls.ControlTemplate>，為控制項提供唯一的外觀。</span><span class="sxs-lookup"><span data-stu-id="2f783-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="2f783-105">有關詳細資訊，請參閱為[控制項創建範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。</span><span class="sxs-lookup"><span data-stu-id="2f783-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
<a name="groupbox_parts"></a>
## <a name="groupbox-parts"></a><span data-ttu-id="2f783-106">組盒零件</span><span class="sxs-lookup"><span data-stu-id="2f783-106">GroupBox Parts</span></span>  
 <span data-ttu-id="2f783-107">該<xref:System.Windows.Controls.GroupBox>控制項沒有任何命名部件。</span><span class="sxs-lookup"><span data-stu-id="2f783-107">The <xref:System.Windows.Controls.GroupBox> control does not have any named parts.</span></span>  
  
<a name="groupbox_states"></a>
## <a name="groupbox-states"></a><span data-ttu-id="2f783-108">組盒狀態</span><span class="sxs-lookup"><span data-stu-id="2f783-108">GroupBox States</span></span>  
 <span data-ttu-id="2f783-109">下表列出了控制項的<xref:System.Windows.Controls.GroupBox>可視狀態。</span><span class="sxs-lookup"><span data-stu-id="2f783-109">The following table lists the visual states for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
|<span data-ttu-id="2f783-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="2f783-110">VisualState Name</span></span>|<span data-ttu-id="2f783-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="2f783-111">VisualStateGroup Name</span></span>|<span data-ttu-id="2f783-112">描述</span><span class="sxs-lookup"><span data-stu-id="2f783-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="2f783-113">有效</span><span class="sxs-lookup"><span data-stu-id="2f783-113">Valid</span></span>|<span data-ttu-id="2f783-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2f783-114">ValidationStates</span></span>|<span data-ttu-id="2f783-115">控制項使用 類<xref:System.Windows.Controls.Validation>，<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性為`false`。</span><span class="sxs-lookup"><span data-stu-id="2f783-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="2f783-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="2f783-116">InvalidFocused</span></span>|<span data-ttu-id="2f783-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2f783-117">ValidationStates</span></span>|<span data-ttu-id="2f783-118">附加<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>屬性具有`true`控制項具有焦點。</span><span class="sxs-lookup"><span data-stu-id="2f783-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="2f783-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="2f783-119">InvalidUnfocused</span></span>|<span data-ttu-id="2f783-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2f783-120">ValidationStates</span></span>|<span data-ttu-id="2f783-121">附加<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>屬性是`true`具有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="2f783-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
<a name="groupbox_controltemplate_example"></a>
## <a name="groupbox-controltemplate-example"></a><span data-ttu-id="2f783-122">組盒控制範本示例</span><span class="sxs-lookup"><span data-stu-id="2f783-122">GroupBox ControlTemplate Example</span></span>  
 <span data-ttu-id="2f783-123">下面的示例演示如何為<xref:System.Windows.Controls.ControlTemplate><xref:System.Windows.Controls.GroupBox>控制項定義 。</span><span class="sxs-lookup"><span data-stu-id="2f783-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 <span data-ttu-id="2f783-124">使用<xref:System.Windows.Controls.ControlTemplate>以下一個或多個資源。</span><span class="sxs-lookup"><span data-stu-id="2f783-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="2f783-125">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="2f783-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f783-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f783-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="2f783-127">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="2f783-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="2f783-128">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="2f783-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="2f783-129">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="2f783-129">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="2f783-130">為控制項創建範本</span><span class="sxs-lookup"><span data-stu-id="2f783-130">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
