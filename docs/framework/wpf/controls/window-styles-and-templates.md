---
title: Window 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], Window
- templates [WPF], Window
- styles [WPF], Window
- ControlTemplate [WPF], Window
- Window [WPF], styles and templates
- states [WPF], Window
ms.assetid: 2dfdf025-347b-4342-bf28-95206c273f35
ms.openlocfilehash: 01233c5d0179e1a6f9bed651cd1f18058bfac168
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283605"
---
# <a name="window-styles-and-templates"></a><span data-ttu-id="56fc6-102">Window 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="56fc6-102">Window Styles and Templates</span></span>
<span data-ttu-id="56fc6-103">本主題描述 <xref:System.Windows.Window> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="56fc6-103">This topic describes the styles and templates for the <xref:System.Windows.Window> control.</span></span> <span data-ttu-id="56fc6-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="56fc6-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="56fc6-105">如需詳細資訊，請參閱[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。</span><span class="sxs-lookup"><span data-stu-id="56fc6-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="window-parts"></a><span data-ttu-id="56fc6-106">視窗元件</span><span class="sxs-lookup"><span data-stu-id="56fc6-106">Window Parts</span></span>  
 <span data-ttu-id="56fc6-107"><xref:System.Windows.Window> 控制項沒有任何已命名的元件。</span><span class="sxs-lookup"><span data-stu-id="56fc6-107">The <xref:System.Windows.Window> control does not have any named parts.</span></span>  
  
## <a name="window-states"></a><span data-ttu-id="56fc6-108">視窗狀態</span><span class="sxs-lookup"><span data-stu-id="56fc6-108">Window States</span></span>  
 <span data-ttu-id="56fc6-109">下表列出 <xref:System.Windows.Window> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="56fc6-109">The following table lists the visual states for the <xref:System.Windows.Window> control.</span></span>  
  
|<span data-ttu-id="56fc6-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="56fc6-110">VisualState Name</span></span>|<span data-ttu-id="56fc6-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="56fc6-111">VisualStateGroup Name</span></span>|<span data-ttu-id="56fc6-112">描述</span><span class="sxs-lookup"><span data-stu-id="56fc6-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="56fc6-113">驗證</span><span class="sxs-lookup"><span data-stu-id="56fc6-113">Valid</span></span>|<span data-ttu-id="56fc6-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="56fc6-114">ValidationStates</span></span>|<span data-ttu-id="56fc6-115">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="56fc6-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="56fc6-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="56fc6-116">InvalidFocused</span></span>|<span data-ttu-id="56fc6-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="56fc6-117">ValidationStates</span></span>|<span data-ttu-id="56fc6-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="56fc6-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="56fc6-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="56fc6-119">InvalidUnfocused</span></span>|<span data-ttu-id="56fc6-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="56fc6-120">ValidationStates</span></span>|<span data-ttu-id="56fc6-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="56fc6-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="window-controltemplate-example"></a><span data-ttu-id="56fc6-122">視窗 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="56fc6-122">Window ControlTemplate Example</span></span>  
 <span data-ttu-id="56fc6-123">下列範例顯示如何定義 <xref:System.Windows.Window> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="56fc6-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Window> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/window.xaml#window)]  
  
 <span data-ttu-id="56fc6-124"><xref:System.Windows.Controls.ControlTemplate> 會使用下列一或多個資源。</span><span class="sxs-lookup"><span data-stu-id="56fc6-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="56fc6-125">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="56fc6-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56fc6-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="56fc6-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="56fc6-127">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="56fc6-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="56fc6-128">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="56fc6-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="56fc6-129">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="56fc6-129">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="56fc6-130">建立控制項的範本</span><span class="sxs-lookup"><span data-stu-id="56fc6-130">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
