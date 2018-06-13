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
ms.openlocfilehash: 9d2f5e4d886d8fc46ecb14dd4f1bda67debdae97
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457640"
---
# <a name="label-styles-and-templates"></a><span data-ttu-id="7479f-102">Label 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="7479f-102">Label Styles and Templates</span></span>
<span data-ttu-id="7479f-103">本主題描述樣式和範本<xref:System.Windows.Controls.Label>控制項。</span><span class="sxs-lookup"><span data-stu-id="7479f-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Label> control.</span></span> <span data-ttu-id="7479f-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="7479f-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="7479f-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="7479f-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="label-parts"></a><span data-ttu-id="7479f-106">標籤部分</span><span class="sxs-lookup"><span data-stu-id="7479f-106">Label Parts</span></span>  
 <span data-ttu-id="7479f-107"><xref:System.Windows.Controls.Label>控制項沒有任何已命名的組件。</span><span class="sxs-lookup"><span data-stu-id="7479f-107">The <xref:System.Windows.Controls.Label> control does not have any named parts.</span></span>  
  
## <a name="label-states"></a><span data-ttu-id="7479f-108">標籤狀態</span><span class="sxs-lookup"><span data-stu-id="7479f-108">Label States</span></span>  
 <span data-ttu-id="7479f-109">下表列出的視覺狀態<xref:System.Windows.Controls.Label>控制項。</span><span class="sxs-lookup"><span data-stu-id="7479f-109">The following table lists the visual states for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
|<span data-ttu-id="7479f-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="7479f-110">VisualState Name</span></span>|<span data-ttu-id="7479f-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="7479f-111">VisualStateGroup Name</span></span>|<span data-ttu-id="7479f-112">描述</span><span class="sxs-lookup"><span data-stu-id="7479f-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="7479f-113">驗證</span><span class="sxs-lookup"><span data-stu-id="7479f-113">Valid</span></span>|<span data-ttu-id="7479f-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7479f-114">ValidationStates</span></span>|<span data-ttu-id="7479f-115">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="7479f-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="7479f-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="7479f-116">InvalidFocused</span></span>|<span data-ttu-id="7479f-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7479f-117">ValidationStates</span></span>|<span data-ttu-id="7479f-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="7479f-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="7479f-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="7479f-119">InvalidUnfocused</span></span>|<span data-ttu-id="7479f-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7479f-120">ValidationStates</span></span>|<span data-ttu-id="7479f-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="7479f-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="label-controltemplate-example"></a><span data-ttu-id="7479f-122">標籤 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="7479f-122">Label ControlTemplate Example</span></span>  
 <span data-ttu-id="7479f-123">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.Label>控制項。</span><span class="sxs-lookup"><span data-stu-id="7479f-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Label](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/label.xaml#label)]  
  
 <span data-ttu-id="7479f-124"><xref:System.Windows.Controls.ControlTemplate>會使用一個或多個下列資源。</span><span class="sxs-lookup"><span data-stu-id="7479f-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="7479f-125">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="7479f-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7479f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7479f-126">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="7479f-127">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="7479f-127">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="7479f-128">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="7479f-128">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="7479f-129">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="7479f-129">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="7479f-130">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="7479f-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
