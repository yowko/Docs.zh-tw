---
title: ToolBar 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], ToolBar
- styles [WPF], ToolBar
- ControlTemplate [WPF], ToolBar
- parts [WPF], ToolBar
- ToolBar [WPF], styles and templates
- templates [WPF], ToolBar
ms.assetid: bd875f46-4690-46f5-81e0-f11a9822484f
ms.openlocfilehash: a984311234386cb205d5db35f18a743ca535ff05
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283661"
---
# <a name="toolbar-styles-and-templates"></a><span data-ttu-id="43b63-102">ToolBar 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="43b63-102">ToolBar Styles and Templates</span></span>
<span data-ttu-id="43b63-103">本主題描述 <xref:System.Windows.Controls.ToolBar> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="43b63-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolBar> control.</span></span> <span data-ttu-id="43b63-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="43b63-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="43b63-105">如需詳細資訊，請參閱[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。</span><span class="sxs-lookup"><span data-stu-id="43b63-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="toolbar-parts"></a><span data-ttu-id="43b63-106">工具列元件</span><span class="sxs-lookup"><span data-stu-id="43b63-106">ToolBar Parts</span></span>  
 <span data-ttu-id="43b63-107">下表列出 <xref:System.Windows.Controls.ToolBar> 控制項的已命名元件。</span><span class="sxs-lookup"><span data-stu-id="43b63-107">The following table lists the named parts for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="43b63-108">組件</span><span class="sxs-lookup"><span data-stu-id="43b63-108">Part</span></span>|<span data-ttu-id="43b63-109">輸入</span><span class="sxs-lookup"><span data-stu-id="43b63-109">Type</span></span>|<span data-ttu-id="43b63-110">描述</span><span class="sxs-lookup"><span data-stu-id="43b63-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="43b63-111">PART_ToolBarPanel</span><span class="sxs-lookup"><span data-stu-id="43b63-111">PART_ToolBarPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarPanel>|<span data-ttu-id="43b63-112">包含 <xref:System.Windows.Controls.ToolBar>上之控制項的物件。</span><span class="sxs-lookup"><span data-stu-id="43b63-112">The object that contains the controls on the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
|<span data-ttu-id="43b63-113">PART_ToolBarOverflowPanel</span><span class="sxs-lookup"><span data-stu-id="43b63-113">PART_ToolBarOverflowPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|<span data-ttu-id="43b63-114">物件，包含 <xref:System.Windows.Controls.ToolBar>之溢位區域中的控制項。</span><span class="sxs-lookup"><span data-stu-id="43b63-114">The object that contains the controls that are in the overflow area of the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
  
 <span data-ttu-id="43b63-115">當您建立 <xref:System.Windows.Controls.ToolBar>的 <xref:System.Windows.Controls.ControlTemplate> 時，您的範本可能會在 <xref:System.Windows.Controls.ScrollViewer>中包含 <xref:System.Windows.Controls.ItemsPresenter>。</span><span class="sxs-lookup"><span data-stu-id="43b63-115">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ToolBar>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="43b63-116">（<xref:System.Windows.Controls.ItemsPresenter> 會顯示 <xref:System.Windows.Controls.ToolBar>中的每個專案，<xref:System.Windows.Controls.ScrollViewer> 可在控制項內進行滾動）。</span><span class="sxs-lookup"><span data-stu-id="43b63-116">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ToolBar>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="43b63-117">如果 <xref:System.Windows.Controls.ItemsPresenter> 不是 <xref:System.Windows.Controls.ScrollViewer>的直接子系，您必須為 <xref:System.Windows.Controls.ItemsPresenter> 指定名稱，`ItemsPresenter`。</span><span class="sxs-lookup"><span data-stu-id="43b63-117">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="toolbar-states"></a><span data-ttu-id="43b63-118">工具列狀態</span><span class="sxs-lookup"><span data-stu-id="43b63-118">ToolBar States</span></span>  
 <span data-ttu-id="43b63-119">下表列出 <xref:System.Windows.Controls.ToolBar> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="43b63-119">The following table lists the visual states for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="43b63-120">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="43b63-120">VisualState Name</span></span>|<span data-ttu-id="43b63-121">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="43b63-121">VisualStateGroup Name</span></span>|<span data-ttu-id="43b63-122">描述</span><span class="sxs-lookup"><span data-stu-id="43b63-122">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="43b63-123">驗證</span><span class="sxs-lookup"><span data-stu-id="43b63-123">Valid</span></span>|<span data-ttu-id="43b63-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="43b63-124">ValidationStates</span></span>|<span data-ttu-id="43b63-125">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="43b63-125">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="43b63-126">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="43b63-126">InvalidFocused</span></span>|<span data-ttu-id="43b63-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="43b63-127">ValidationStates</span></span>|<span data-ttu-id="43b63-128"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="43b63-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="43b63-129">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="43b63-129">InvalidUnfocused</span></span>|<span data-ttu-id="43b63-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="43b63-130">ValidationStates</span></span>|<span data-ttu-id="43b63-131"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="43b63-131">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="toolbar-controltemplate-example"></a><span data-ttu-id="43b63-132">工具列 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="43b63-132">ToolBar ControlTemplate Example</span></span>  
 <span data-ttu-id="43b63-133">下列範例顯示如何定義 <xref:System.Windows.Controls.ToolBar> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="43b63-133">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/toolbar.xaml#toolbar)]  
  
 <span data-ttu-id="43b63-134">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="43b63-134">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="43b63-135">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="43b63-135">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43b63-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="43b63-136">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="43b63-137">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="43b63-137">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="43b63-138">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="43b63-138">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="43b63-139">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="43b63-139">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="43b63-140">建立控制項的範本</span><span class="sxs-lookup"><span data-stu-id="43b63-140">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
