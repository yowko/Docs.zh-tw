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
ms.openlocfilehash: e5befffc86f26176da4accfc01239a08d4978713
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283769"
---
# <a name="groupbox-styles-and-templates"></a><span data-ttu-id="37fbf-102">GroupBox 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="37fbf-102">GroupBox Styles and Templates</span></span>
<a name="introduction"></a><span data-ttu-id="37fbf-103">本主題描述 <xref:System.Windows.Controls.GroupBox> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="37fbf-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.GroupBox> control.</span></span> <span data-ttu-id="37fbf-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="37fbf-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="37fbf-105">如需詳細資訊，請參閱[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。</span><span class="sxs-lookup"><span data-stu-id="37fbf-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
<a name="groupbox_parts"></a>   
## <a name="groupbox-parts"></a><span data-ttu-id="37fbf-106">群組方塊元件</span><span class="sxs-lookup"><span data-stu-id="37fbf-106">GroupBox Parts</span></span>  
 <span data-ttu-id="37fbf-107"><xref:System.Windows.Controls.GroupBox> 控制項沒有任何已命名的元件。</span><span class="sxs-lookup"><span data-stu-id="37fbf-107">The <xref:System.Windows.Controls.GroupBox> control does not have any named parts.</span></span>  
  
<a name="groupbox_states"></a>   
## <a name="groupbox-states"></a><span data-ttu-id="37fbf-108">群組方塊狀態</span><span class="sxs-lookup"><span data-stu-id="37fbf-108">GroupBox States</span></span>  
 <span data-ttu-id="37fbf-109">下表列出 <xref:System.Windows.Controls.GroupBox> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="37fbf-109">The following table lists the visual states for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
|<span data-ttu-id="37fbf-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="37fbf-110">VisualState Name</span></span>|<span data-ttu-id="37fbf-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="37fbf-111">VisualStateGroup Name</span></span>|<span data-ttu-id="37fbf-112">描述</span><span class="sxs-lookup"><span data-stu-id="37fbf-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="37fbf-113">驗證</span><span class="sxs-lookup"><span data-stu-id="37fbf-113">Valid</span></span>|<span data-ttu-id="37fbf-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="37fbf-114">ValidationStates</span></span>|<span data-ttu-id="37fbf-115">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="37fbf-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="37fbf-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="37fbf-116">InvalidFocused</span></span>|<span data-ttu-id="37fbf-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="37fbf-117">ValidationStates</span></span>|<span data-ttu-id="37fbf-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="37fbf-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="37fbf-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="37fbf-119">InvalidUnfocused</span></span>|<span data-ttu-id="37fbf-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="37fbf-120">ValidationStates</span></span>|<span data-ttu-id="37fbf-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="37fbf-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
<a name="groupbox_controltemplate_example"></a>   
## <a name="groupbox-controltemplate-example"></a><span data-ttu-id="37fbf-122">分組 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="37fbf-122">GroupBox ControlTemplate Example</span></span>  
 <span data-ttu-id="37fbf-123">下列範例顯示如何定義 <xref:System.Windows.Controls.GroupBox> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="37fbf-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 <span data-ttu-id="37fbf-124"><xref:System.Windows.Controls.ControlTemplate> 會使用下列一或多個資源。</span><span class="sxs-lookup"><span data-stu-id="37fbf-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="37fbf-125">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="37fbf-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37fbf-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="37fbf-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="37fbf-127">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="37fbf-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="37fbf-128">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="37fbf-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="37fbf-129">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="37fbf-129">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="37fbf-130">建立控制項的範本</span><span class="sxs-lookup"><span data-stu-id="37fbf-130">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
