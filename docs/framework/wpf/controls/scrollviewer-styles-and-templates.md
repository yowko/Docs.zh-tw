---
title: ScrollViewer 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ScrollViewer
- states [WPF], ScrollViewer
- styles [WPF], ScrollViewer
- templates [WPF], ScrollViewer
- ControlTemplate [WPF], ScrollViewer
- ScrollViewer [WPF], styles and templates
ms.assetid: dffdd822-ae69-4946-abaf-710860cd65b2
ms.openlocfilehash: b54dcacf55a750d7c1253db20147d18de47d027e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283400"
---
# <a name="scrollviewer-styles-and-templates"></a><span data-ttu-id="771a9-102">ScrollViewer 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="771a9-102">ScrollViewer Styles and Templates</span></span>
<span data-ttu-id="771a9-103">本主題描述 <xref:System.Windows.Controls.ScrollViewer> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="771a9-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span> <span data-ttu-id="771a9-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="771a9-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="771a9-105">如需詳細資訊，請參閱[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。</span><span class="sxs-lookup"><span data-stu-id="771a9-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="scrollviewer-parts"></a><span data-ttu-id="771a9-106">ScrollViewer 元件</span><span class="sxs-lookup"><span data-stu-id="771a9-106">ScrollViewer Parts</span></span>  
 <span data-ttu-id="771a9-107">下表列出 <xref:System.Windows.Controls.ScrollViewer> 控制項的已命名元件。</span><span class="sxs-lookup"><span data-stu-id="771a9-107">The following table lists the named parts for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="771a9-108">組件</span><span class="sxs-lookup"><span data-stu-id="771a9-108">Part</span></span>|<span data-ttu-id="771a9-109">輸入</span><span class="sxs-lookup"><span data-stu-id="771a9-109">Type</span></span>|<span data-ttu-id="771a9-110">描述</span><span class="sxs-lookup"><span data-stu-id="771a9-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="771a9-111">PART_ScrollContentPresenter</span><span class="sxs-lookup"><span data-stu-id="771a9-111">PART_ScrollContentPresenter</span></span>|<xref:System.Windows.Controls.ScrollContentPresenter>|<span data-ttu-id="771a9-112"><xref:System.Windows.Controls.ScrollViewer>中內容的預留位置。</span><span class="sxs-lookup"><span data-stu-id="771a9-112">The placeholder for content in the <xref:System.Windows.Controls.ScrollViewer>.</span></span>|  
|<span data-ttu-id="771a9-113">PART_HorizontalScrollBar</span><span class="sxs-lookup"><span data-stu-id="771a9-113">PART_HorizontalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="771a9-114">用來水準滾動內容的 <xref:System.Windows.Controls.Primitives.ScrollBar>。</span><span class="sxs-lookup"><span data-stu-id="771a9-114">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content horizontally.</span></span>|  
|<span data-ttu-id="771a9-115">PART_VerticalScrollBar</span><span class="sxs-lookup"><span data-stu-id="771a9-115">PART_VerticalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="771a9-116">用來垂直捲動內容的 <xref:System.Windows.Controls.Primitives.ScrollBar>。</span><span class="sxs-lookup"><span data-stu-id="771a9-116">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content vertically.</span></span>|  
  
## <a name="scrollviewer-states"></a><span data-ttu-id="771a9-117">ScrollViewer 狀態</span><span class="sxs-lookup"><span data-stu-id="771a9-117">ScrollViewer States</span></span>  
 <span data-ttu-id="771a9-118">下表列出 <xref:System.Windows.Controls.ScrollViewer> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="771a9-118">The following table lists the visual states for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="771a9-119">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="771a9-119">VisualState Name</span></span>|<span data-ttu-id="771a9-120">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="771a9-120">VisualStateGroup Name</span></span>|<span data-ttu-id="771a9-121">描述</span><span class="sxs-lookup"><span data-stu-id="771a9-121">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="771a9-122">驗證</span><span class="sxs-lookup"><span data-stu-id="771a9-122">Valid</span></span>|<span data-ttu-id="771a9-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="771a9-123">ValidationStates</span></span>|<span data-ttu-id="771a9-124">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="771a9-124">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="771a9-125">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="771a9-125">InvalidFocused</span></span>|<span data-ttu-id="771a9-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="771a9-126">ValidationStates</span></span>|<span data-ttu-id="771a9-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="771a9-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="771a9-128">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="771a9-128">InvalidUnfocused</span></span>|<span data-ttu-id="771a9-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="771a9-129">ValidationStates</span></span>|<span data-ttu-id="771a9-130"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="771a9-130">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollviewer-controltemplate-example"></a><span data-ttu-id="771a9-131">ScrollViewer ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="771a9-131">ScrollViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="771a9-132">下列範例顯示如何定義 <xref:System.Windows.Controls.ScrollViewer> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="771a9-132">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollviewer.xaml#scrollviewer)]  
  
 <span data-ttu-id="771a9-133">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="771a9-133">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="771a9-134">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="771a9-134">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="771a9-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="771a9-135">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="771a9-136">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="771a9-136">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="771a9-137">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="771a9-137">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="771a9-138">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="771a9-138">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="771a9-139">建立控制項的範本</span><span class="sxs-lookup"><span data-stu-id="771a9-139">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
