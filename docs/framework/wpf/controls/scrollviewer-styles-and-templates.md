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
ms.openlocfilehash: 70a2002ab114f2bbd6a4e550ae9006e214ee27a5
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458426"
---
# <a name="scrollviewer-styles-and-templates"></a><span data-ttu-id="e741a-102">ScrollViewer 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="e741a-102">ScrollViewer Styles and Templates</span></span>
<span data-ttu-id="e741a-103">本主題描述 <xref:System.Windows.Controls.ScrollViewer> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="e741a-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span> <span data-ttu-id="e741a-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="e741a-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="e741a-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="e741a-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollviewer-parts"></a><span data-ttu-id="e741a-106">ScrollViewer 元件</span><span class="sxs-lookup"><span data-stu-id="e741a-106">ScrollViewer Parts</span></span>  
 <span data-ttu-id="e741a-107">下表列出 <xref:System.Windows.Controls.ScrollViewer> 控制項的已命名元件。</span><span class="sxs-lookup"><span data-stu-id="e741a-107">The following table lists the named parts for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="e741a-108">組件</span><span class="sxs-lookup"><span data-stu-id="e741a-108">Part</span></span>|<span data-ttu-id="e741a-109">輸入</span><span class="sxs-lookup"><span data-stu-id="e741a-109">Type</span></span>|<span data-ttu-id="e741a-110">描述</span><span class="sxs-lookup"><span data-stu-id="e741a-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="e741a-111">PART_ScrollContentPresenter</span><span class="sxs-lookup"><span data-stu-id="e741a-111">PART_ScrollContentPresenter</span></span>|<xref:System.Windows.Controls.ScrollContentPresenter>|<span data-ttu-id="e741a-112"><xref:System.Windows.Controls.ScrollViewer>中內容的預留位置。</span><span class="sxs-lookup"><span data-stu-id="e741a-112">The placeholder for content in the <xref:System.Windows.Controls.ScrollViewer>.</span></span>|  
|<span data-ttu-id="e741a-113">PART_HorizontalScrollBar</span><span class="sxs-lookup"><span data-stu-id="e741a-113">PART_HorizontalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="e741a-114">用來水準滾動內容的 <xref:System.Windows.Controls.Primitives.ScrollBar>。</span><span class="sxs-lookup"><span data-stu-id="e741a-114">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content horizontally.</span></span>|  
|<span data-ttu-id="e741a-115">PART_VerticalScrollBar</span><span class="sxs-lookup"><span data-stu-id="e741a-115">PART_VerticalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="e741a-116">用來垂直捲動內容的 <xref:System.Windows.Controls.Primitives.ScrollBar>。</span><span class="sxs-lookup"><span data-stu-id="e741a-116">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content vertically.</span></span>|  
  
## <a name="scrollviewer-states"></a><span data-ttu-id="e741a-117">ScrollViewer 狀態</span><span class="sxs-lookup"><span data-stu-id="e741a-117">ScrollViewer States</span></span>  
 <span data-ttu-id="e741a-118">下表列出 <xref:System.Windows.Controls.ScrollViewer> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="e741a-118">The following table lists the visual states for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="e741a-119">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="e741a-119">VisualState Name</span></span>|<span data-ttu-id="e741a-120">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="e741a-120">VisualStateGroup Name</span></span>|<span data-ttu-id="e741a-121">描述</span><span class="sxs-lookup"><span data-stu-id="e741a-121">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="e741a-122">驗證</span><span class="sxs-lookup"><span data-stu-id="e741a-122">Valid</span></span>|<span data-ttu-id="e741a-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e741a-123">ValidationStates</span></span>|<span data-ttu-id="e741a-124">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="e741a-124">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="e741a-125">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="e741a-125">InvalidFocused</span></span>|<span data-ttu-id="e741a-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e741a-126">ValidationStates</span></span>|<span data-ttu-id="e741a-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="e741a-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="e741a-128">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="e741a-128">InvalidUnfocused</span></span>|<span data-ttu-id="e741a-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e741a-129">ValidationStates</span></span>|<span data-ttu-id="e741a-130"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="e741a-130">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollviewer-controltemplate-example"></a><span data-ttu-id="e741a-131">ScrollViewer ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="e741a-131">ScrollViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="e741a-132">下列範例顯示如何定義 <xref:System.Windows.Controls.ScrollViewer> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="e741a-132">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollviewer.xaml#scrollviewer)]  
  
 <span data-ttu-id="e741a-133">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="e741a-133">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="e741a-134">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="e741a-134">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e741a-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="e741a-135">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="e741a-136">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="e741a-136">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="e741a-137">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="e741a-137">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="e741a-138">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="e741a-138">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="e741a-139">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="e741a-139">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
