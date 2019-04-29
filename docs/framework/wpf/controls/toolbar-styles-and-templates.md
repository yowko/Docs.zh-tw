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
ms.openlocfilehash: 1cbb8d54a544b70b4a484c06c6bb2e9ca25029da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790737"
---
# <a name="toolbar-styles-and-templates"></a><span data-ttu-id="319ff-102">ToolBar 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="319ff-102">ToolBar Styles and Templates</span></span>
<span data-ttu-id="319ff-103">本主題描述的樣式和範本<xref:System.Windows.Controls.ToolBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="319ff-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolBar> control.</span></span> <span data-ttu-id="319ff-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>，讓控制項的獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="319ff-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="319ff-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="319ff-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="toolbar-parts"></a><span data-ttu-id="319ff-106">工具列組件</span><span class="sxs-lookup"><span data-stu-id="319ff-106">ToolBar Parts</span></span>  
 <span data-ttu-id="319ff-107">下表列出的具名組件<xref:System.Windows.Controls.ToolBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="319ff-107">The following table lists the named parts for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="319ff-108">組件</span><span class="sxs-lookup"><span data-stu-id="319ff-108">Part</span></span>|<span data-ttu-id="319ff-109">類型</span><span class="sxs-lookup"><span data-stu-id="319ff-109">Type</span></span>|<span data-ttu-id="319ff-110">描述</span><span class="sxs-lookup"><span data-stu-id="319ff-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="319ff-111">PART_ToolBarPanel</span><span class="sxs-lookup"><span data-stu-id="319ff-111">PART_ToolBarPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarPanel>|<span data-ttu-id="319ff-112">物件，包含的控制項上<xref:System.Windows.Controls.ToolBar>。</span><span class="sxs-lookup"><span data-stu-id="319ff-112">The object that contains the controls on the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
|<span data-ttu-id="319ff-113">PART_ToolBarOverflowPanel</span><span class="sxs-lookup"><span data-stu-id="319ff-113">PART_ToolBarOverflowPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|<span data-ttu-id="319ff-114">物件，包含溢位區域中的控制項<xref:System.Windows.Controls.ToolBar>。</span><span class="sxs-lookup"><span data-stu-id="319ff-114">The object that contains the controls that are in the overflow area of the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
  
 <span data-ttu-id="319ff-115">當您建立<xref:System.Windows.Controls.ControlTemplate>for <xref:System.Windows.Controls.ToolBar>，您的範本可能會包含<xref:System.Windows.Controls.ItemsPresenter>內<xref:System.Windows.Controls.ScrollViewer>。</span><span class="sxs-lookup"><span data-stu-id="319ff-115">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ToolBar>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="319ff-116">(<xref:System.Windows.Controls.ItemsPresenter>會顯示在每個項目<xref:System.Windows.Controls.ToolBar>;<xref:System.Windows.Controls.ScrollViewer>可在控制項內捲動)。</span><span class="sxs-lookup"><span data-stu-id="319ff-116">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ToolBar>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="319ff-117">如果<xref:System.Windows.Controls.ItemsPresenter>不是直接子系<xref:System.Windows.Controls.ScrollViewer>，您必須給予<xref:System.Windows.Controls.ItemsPresenter>名稱， `ItemsPresenter`。</span><span class="sxs-lookup"><span data-stu-id="319ff-117">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="toolbar-states"></a><span data-ttu-id="319ff-118">工具列狀態</span><span class="sxs-lookup"><span data-stu-id="319ff-118">ToolBar States</span></span>  
 <span data-ttu-id="319ff-119">下表列出的視覺狀態<xref:System.Windows.Controls.ToolBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="319ff-119">The following table lists the visual states for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="319ff-120">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="319ff-120">VisualState Name</span></span>|<span data-ttu-id="319ff-121">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="319ff-121">VisualStateGroup Name</span></span>|<span data-ttu-id="319ff-122">描述</span><span class="sxs-lookup"><span data-stu-id="319ff-122">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="319ff-123">驗證</span><span class="sxs-lookup"><span data-stu-id="319ff-123">Valid</span></span>|<span data-ttu-id="319ff-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="319ff-124">ValidationStates</span></span>|<span data-ttu-id="319ff-125">控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。</span><span class="sxs-lookup"><span data-stu-id="319ff-125">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="319ff-126">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="319ff-126">InvalidFocused</span></span>|<span data-ttu-id="319ff-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="319ff-127">ValidationStates</span></span>|<span data-ttu-id="319ff-128"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。</span><span class="sxs-lookup"><span data-stu-id="319ff-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="319ff-129">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="319ff-129">InvalidUnfocused</span></span>|<span data-ttu-id="319ff-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="319ff-130">ValidationStates</span></span>|<span data-ttu-id="319ff-131"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="319ff-131">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="toolbar-controltemplate-example"></a><span data-ttu-id="319ff-132">工具列 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="319ff-132">ToolBar ControlTemplate Example</span></span>  
 <span data-ttu-id="319ff-133">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.ToolBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="319ff-133">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/toolbar.xaml#toolbar)]  
  
 <span data-ttu-id="319ff-134">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="319ff-134">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="319ff-135">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="319ff-135">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="319ff-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="319ff-136">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="319ff-137">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="319ff-137">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="319ff-138">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="319ff-138">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="319ff-139">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="319ff-139">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="319ff-140">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="319ff-140">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
