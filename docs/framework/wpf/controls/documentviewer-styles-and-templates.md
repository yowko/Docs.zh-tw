---
title: DocumentViewer 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], DocumentViewer
- DocumentViewer [WPF], styles and templates
- states [WPF], DocumentViewer
- ControlTemplate [WPF], DocumentViewer
- parts [WPF], DocumentViewer
- styles [WPF], DocumentViewer
ms.assetid: 6bd4ff8f-ea6a-4084-ac58-e7a67446ce1c
ms.openlocfilehash: ac1dc4f74a8e8f3ad2e84c6d50239ec827306c28
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283523"
---
# <a name="documentviewer-styles-and-templates"></a><span data-ttu-id="61de5-102">DocumentViewer 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="61de5-102">DocumentViewer Styles and Templates</span></span>
<span data-ttu-id="61de5-103">本主題描述 <xref:System.Windows.Controls.DocumentViewer> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="61de5-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span> <span data-ttu-id="61de5-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="61de5-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="61de5-105">如需詳細資訊，請參閱[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。</span><span class="sxs-lookup"><span data-stu-id="61de5-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="documentviewer-parts"></a><span data-ttu-id="61de5-106">DocumentViewer 元件</span><span class="sxs-lookup"><span data-stu-id="61de5-106">DocumentViewer Parts</span></span>  
 <span data-ttu-id="61de5-107">下表列出 <xref:System.Windows.Controls.DocumentViewer> 控制項的已命名元件。</span><span class="sxs-lookup"><span data-stu-id="61de5-107">The following table lists the named parts for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="61de5-108">組件</span><span class="sxs-lookup"><span data-stu-id="61de5-108">Part</span></span>|<span data-ttu-id="61de5-109">輸入</span><span class="sxs-lookup"><span data-stu-id="61de5-109">Type</span></span>|<span data-ttu-id="61de5-110">描述</span><span class="sxs-lookup"><span data-stu-id="61de5-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="61de5-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="61de5-111">PART_ContentHost</span></span>|<xref:System.Windows.Controls.ScrollViewer>|<span data-ttu-id="61de5-112">內容和捲動區域。</span><span class="sxs-lookup"><span data-stu-id="61de5-112">The content and scrolling area.</span></span>|  
|<span data-ttu-id="61de5-113">PART_FindToolBarHost</span><span class="sxs-lookup"><span data-stu-id="61de5-113">PART_FindToolBarHost</span></span>|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="61de5-114">[搜尋] 方塊（依預設位於底部）。</span><span class="sxs-lookup"><span data-stu-id="61de5-114">The search box, at the bottom by default.</span></span>|  
  
## <a name="documentviewer-states"></a><span data-ttu-id="61de5-115">DocumentViewer 狀態</span><span class="sxs-lookup"><span data-stu-id="61de5-115">DocumentViewer States</span></span>  
 <span data-ttu-id="61de5-116">下表列出 <xref:System.Windows.Controls.DocumentViewer> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="61de5-116">The following table lists the visual states for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="61de5-117">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="61de5-117">VisualState Name</span></span>|<span data-ttu-id="61de5-118">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="61de5-118">VisualStateGroup Name</span></span>|<span data-ttu-id="61de5-119">描述</span><span class="sxs-lookup"><span data-stu-id="61de5-119">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="61de5-120">驗證</span><span class="sxs-lookup"><span data-stu-id="61de5-120">Valid</span></span>|<span data-ttu-id="61de5-121">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="61de5-121">ValidationStates</span></span>|<span data-ttu-id="61de5-122">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="61de5-122">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="61de5-123">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="61de5-123">InvalidFocused</span></span>|<span data-ttu-id="61de5-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="61de5-124">ValidationStates</span></span>|<span data-ttu-id="61de5-125"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="61de5-125">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="61de5-126">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="61de5-126">InvalidUnfocused</span></span>|<span data-ttu-id="61de5-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="61de5-127">ValidationStates</span></span>|<span data-ttu-id="61de5-128"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="61de5-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="documentviewer-controltemplate-example"></a><span data-ttu-id="61de5-129">DocumentViewer ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="61de5-129">DocumentViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="61de5-130">下列範例顯示如何定義 <xref:System.Windows.Controls.DocumentViewer> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="61de5-130">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#DocumentViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/documentviewer.xaml#documentviewer)]  
  
 <span data-ttu-id="61de5-131">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="61de5-131">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="61de5-132">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="61de5-132">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61de5-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="61de5-133">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="61de5-134">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="61de5-134">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="61de5-135">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="61de5-135">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="61de5-136">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="61de5-136">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="61de5-137">建立控制項的範本</span><span class="sxs-lookup"><span data-stu-id="61de5-137">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
