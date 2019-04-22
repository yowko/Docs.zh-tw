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
ms.openlocfilehash: 9c0edfd7ab4772eb9a1f5ecdd3db611fa36bf8d3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59226829"
---
# <a name="scrollviewer-styles-and-templates"></a><span data-ttu-id="7cef5-102">ScrollViewer 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="7cef5-102">ScrollViewer Styles and Templates</span></span>
<span data-ttu-id="7cef5-103">本主題描述的樣式和範本<xref:System.Windows.Controls.ScrollViewer>控制項。</span><span class="sxs-lookup"><span data-stu-id="7cef5-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span> <span data-ttu-id="7cef5-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>，讓控制項的獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="7cef5-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="7cef5-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="7cef5-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollviewer-parts"></a><span data-ttu-id="7cef5-106">ScrollViewer 組件</span><span class="sxs-lookup"><span data-stu-id="7cef5-106">ScrollViewer Parts</span></span>  
 <span data-ttu-id="7cef5-107">下表列出的具名組件<xref:System.Windows.Controls.ScrollViewer>控制項。</span><span class="sxs-lookup"><span data-stu-id="7cef5-107">The following table lists the named parts for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="7cef5-108">組件</span><span class="sxs-lookup"><span data-stu-id="7cef5-108">Part</span></span>|<span data-ttu-id="7cef5-109">類型</span><span class="sxs-lookup"><span data-stu-id="7cef5-109">Type</span></span>|<span data-ttu-id="7cef5-110">描述</span><span class="sxs-lookup"><span data-stu-id="7cef5-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="7cef5-111">PART_ScrollContentPresenter</span><span class="sxs-lookup"><span data-stu-id="7cef5-111">PART_ScrollContentPresenter</span></span>|<xref:System.Windows.Controls.ScrollContentPresenter>|<span data-ttu-id="7cef5-112">內容中的預留位置<xref:System.Windows.Controls.ScrollViewer>。</span><span class="sxs-lookup"><span data-stu-id="7cef5-112">The placeholder for content in the <xref:System.Windows.Controls.ScrollViewer>.</span></span>|  
|<span data-ttu-id="7cef5-113">PART_HorizontalScrollBar</span><span class="sxs-lookup"><span data-stu-id="7cef5-113">PART_HorizontalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="7cef5-114"><xref:System.Windows.Controls.Primitives.ScrollBar>用來水平捲動內容。</span><span class="sxs-lookup"><span data-stu-id="7cef5-114">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content horizontally.</span></span>|  
|<span data-ttu-id="7cef5-115">PART_VerticalScrollBar</span><span class="sxs-lookup"><span data-stu-id="7cef5-115">PART_VerticalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="7cef5-116"><xref:System.Windows.Controls.Primitives.ScrollBar>使用垂直捲動內容。</span><span class="sxs-lookup"><span data-stu-id="7cef5-116">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content vertically.</span></span>|  
  
## <a name="scrollviewer-states"></a><span data-ttu-id="7cef5-117">ScrollViewer 狀態</span><span class="sxs-lookup"><span data-stu-id="7cef5-117">ScrollViewer States</span></span>  
 <span data-ttu-id="7cef5-118">下表列出的視覺狀態<xref:System.Windows.Controls.ScrollViewer>控制項。</span><span class="sxs-lookup"><span data-stu-id="7cef5-118">The following table lists the visual states for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="7cef5-119">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="7cef5-119">VisualState Name</span></span>|<span data-ttu-id="7cef5-120">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="7cef5-120">VisualStateGroup Name</span></span>|<span data-ttu-id="7cef5-121">描述</span><span class="sxs-lookup"><span data-stu-id="7cef5-121">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="7cef5-122">驗證</span><span class="sxs-lookup"><span data-stu-id="7cef5-122">Valid</span></span>|<span data-ttu-id="7cef5-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7cef5-123">ValidationStates</span></span>|<span data-ttu-id="7cef5-124">控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。</span><span class="sxs-lookup"><span data-stu-id="7cef5-124">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="7cef5-125">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="7cef5-125">InvalidFocused</span></span>|<span data-ttu-id="7cef5-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7cef5-126">ValidationStates</span></span>|<span data-ttu-id="7cef5-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。</span><span class="sxs-lookup"><span data-stu-id="7cef5-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="7cef5-128">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="7cef5-128">InvalidUnfocused</span></span>|<span data-ttu-id="7cef5-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7cef5-129">ValidationStates</span></span>|<span data-ttu-id="7cef5-130"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="7cef5-130">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollviewer-controltemplate-example"></a><span data-ttu-id="7cef5-131">ScrollViewer ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="7cef5-131">ScrollViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="7cef5-132">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.ScrollViewer>控制項。</span><span class="sxs-lookup"><span data-stu-id="7cef5-132">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollviewer.xaml#scrollviewer)]  
  
 <span data-ttu-id="7cef5-133">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="7cef5-133">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="7cef5-134">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="7cef5-134">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cef5-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7cef5-135">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="7cef5-136">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="7cef5-136">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="7cef5-137">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="7cef5-137">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="7cef5-138">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="7cef5-138">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="7cef5-139">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="7cef5-139">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
