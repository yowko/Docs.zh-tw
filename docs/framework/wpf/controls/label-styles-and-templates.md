---
title: Label 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], Label
- parts [WPF], Label
- ControlTemplate [WPF], Label
- styles [WPF], Label
- Label [WPF], styles and templates
- states [WPF], Label
ms.assetid: c1d5359a-8e4a-4925-ab3e-e92bf6694859
ms.openlocfilehash: c3bf4dc629bbb3e4ea21862c6893b001749f4649
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459397"
---
# <a name="label-styles-and-templates"></a><span data-ttu-id="f35d9-102">Label 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="f35d9-102">Label Styles and Templates</span></span>
<span data-ttu-id="f35d9-103">本主題描述 <xref:System.Windows.Controls.Label> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="f35d9-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Label> control.</span></span> <span data-ttu-id="f35d9-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="f35d9-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="f35d9-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="f35d9-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="label-parts"></a><span data-ttu-id="f35d9-106">標籤元件</span><span class="sxs-lookup"><span data-stu-id="f35d9-106">Label Parts</span></span>  
 <span data-ttu-id="f35d9-107"><xref:System.Windows.Controls.Label> 控制項沒有任何已命名的元件。</span><span class="sxs-lookup"><span data-stu-id="f35d9-107">The <xref:System.Windows.Controls.Label> control does not have any named parts.</span></span>  
  
## <a name="label-states"></a><span data-ttu-id="f35d9-108">標籤狀態</span><span class="sxs-lookup"><span data-stu-id="f35d9-108">Label States</span></span>  
 <span data-ttu-id="f35d9-109">下表列出 <xref:System.Windows.Controls.Label> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="f35d9-109">The following table lists the visual states for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
|<span data-ttu-id="f35d9-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="f35d9-110">VisualState Name</span></span>|<span data-ttu-id="f35d9-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="f35d9-111">VisualStateGroup Name</span></span>|<span data-ttu-id="f35d9-112">描述</span><span class="sxs-lookup"><span data-stu-id="f35d9-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f35d9-113">驗證</span><span class="sxs-lookup"><span data-stu-id="f35d9-113">Valid</span></span>|<span data-ttu-id="f35d9-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f35d9-114">ValidationStates</span></span>|<span data-ttu-id="f35d9-115">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="f35d9-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="f35d9-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="f35d9-116">InvalidFocused</span></span>|<span data-ttu-id="f35d9-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f35d9-117">ValidationStates</span></span>|<span data-ttu-id="f35d9-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="f35d9-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="f35d9-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="f35d9-119">InvalidUnfocused</span></span>|<span data-ttu-id="f35d9-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f35d9-120">ValidationStates</span></span>|<span data-ttu-id="f35d9-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="f35d9-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="label-controltemplate-example"></a><span data-ttu-id="f35d9-122">標籤 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="f35d9-122">Label ControlTemplate Example</span></span>  
 <span data-ttu-id="f35d9-123">下列範例顯示如何定義 <xref:System.Windows.Controls.Label> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="f35d9-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Label](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/label.xaml#label)]  
  
 <span data-ttu-id="f35d9-124"><xref:System.Windows.Controls.ControlTemplate> 會使用下列一或多個資源。</span><span class="sxs-lookup"><span data-stu-id="f35d9-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="f35d9-125">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="f35d9-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f35d9-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="f35d9-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="f35d9-127">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="f35d9-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="f35d9-128">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="f35d9-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="f35d9-129">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="f35d9-129">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="f35d9-130">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="f35d9-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
