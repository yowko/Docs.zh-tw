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
ms.openlocfilehash: 4e91a640b36e4793567c9e728fd71ec8ce596743
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158414"
---
# <a name="documentviewer-styles-and-templates"></a><span data-ttu-id="ce9b2-102">DocumentViewer 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="ce9b2-102">DocumentViewer Styles and Templates</span></span>
<span data-ttu-id="ce9b2-103">本主題描述的樣式和範本<xref:System.Windows.Controls.DocumentViewer>控制項。</span><span class="sxs-lookup"><span data-stu-id="ce9b2-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span> <span data-ttu-id="ce9b2-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>，讓控制項的獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="ce9b2-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="ce9b2-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="ce9b2-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="documentviewer-parts"></a><span data-ttu-id="ce9b2-106">DocumentViewer 組件</span><span class="sxs-lookup"><span data-stu-id="ce9b2-106">DocumentViewer Parts</span></span>  
 <span data-ttu-id="ce9b2-107">下表列出的具名組件<xref:System.Windows.Controls.DocumentViewer>控制項。</span><span class="sxs-lookup"><span data-stu-id="ce9b2-107">The following table lists the named parts for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="ce9b2-108">組件</span><span class="sxs-lookup"><span data-stu-id="ce9b2-108">Part</span></span>|<span data-ttu-id="ce9b2-109">類型</span><span class="sxs-lookup"><span data-stu-id="ce9b2-109">Type</span></span>|<span data-ttu-id="ce9b2-110">描述</span><span class="sxs-lookup"><span data-stu-id="ce9b2-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ce9b2-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="ce9b2-111">PART_ContentHost</span></span>|<xref:System.Windows.Controls.ScrollViewer>|<span data-ttu-id="ce9b2-112">內容和捲動區域。</span><span class="sxs-lookup"><span data-stu-id="ce9b2-112">The content and scrolling area.</span></span>|  
|<span data-ttu-id="ce9b2-113">PART_FindToolBarHost</span><span class="sxs-lookup"><span data-stu-id="ce9b2-113">PART_FindToolBarHost</span></span>|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="ce9b2-114">搜尋方塊中，依預設底部。</span><span class="sxs-lookup"><span data-stu-id="ce9b2-114">The search box, at the bottom by default.</span></span>|  
  
## <a name="documentviewer-states"></a><span data-ttu-id="ce9b2-115">DocumentViewer 狀態</span><span class="sxs-lookup"><span data-stu-id="ce9b2-115">DocumentViewer States</span></span>  
 <span data-ttu-id="ce9b2-116">下表列出的視覺狀態<xref:System.Windows.Controls.DocumentViewer>控制項。</span><span class="sxs-lookup"><span data-stu-id="ce9b2-116">The following table lists the visual states for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="ce9b2-117">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="ce9b2-117">VisualState Name</span></span>|<span data-ttu-id="ce9b2-118">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="ce9b2-118">VisualStateGroup Name</span></span>|<span data-ttu-id="ce9b2-119">描述</span><span class="sxs-lookup"><span data-stu-id="ce9b2-119">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ce9b2-120">驗證</span><span class="sxs-lookup"><span data-stu-id="ce9b2-120">Valid</span></span>|<span data-ttu-id="ce9b2-121">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ce9b2-121">ValidationStates</span></span>|<span data-ttu-id="ce9b2-122">控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。</span><span class="sxs-lookup"><span data-stu-id="ce9b2-122">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="ce9b2-123">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="ce9b2-123">InvalidFocused</span></span>|<span data-ttu-id="ce9b2-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ce9b2-124">ValidationStates</span></span>|<span data-ttu-id="ce9b2-125"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。</span><span class="sxs-lookup"><span data-stu-id="ce9b2-125">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="ce9b2-126">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="ce9b2-126">InvalidUnfocused</span></span>|<span data-ttu-id="ce9b2-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ce9b2-127">ValidationStates</span></span>|<span data-ttu-id="ce9b2-128"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="ce9b2-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="documentviewer-controltemplate-example"></a><span data-ttu-id="ce9b2-129">DocumentViewer ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="ce9b2-129">DocumentViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="ce9b2-130">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.DocumentViewer>控制項。</span><span class="sxs-lookup"><span data-stu-id="ce9b2-130">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#DocumentViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/documentviewer.xaml#documentviewer)]  
  
 <span data-ttu-id="ce9b2-131">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="ce9b2-131">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="ce9b2-132">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="ce9b2-132">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce9b2-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce9b2-133">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="ce9b2-134">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="ce9b2-134">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="ce9b2-135">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="ce9b2-135">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="ce9b2-136">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="ce9b2-136">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="ce9b2-137">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="ce9b2-137">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
