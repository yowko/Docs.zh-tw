---
title: Menu 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], Menu
- ControlTemplate [WPF], Menu
- Menu [WPF], styles and templates
- states [WPF], Menu
- templates [WPF], Menu
- parts [WPF], Menu
ms.assetid: b89da183-9b87-42c6-ac53-731a42c7b09e
ms.openlocfilehash: 6818be4ac92dbdd7de0c6c6fa65109e21eadc2f5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094199"
---
# <a name="menu-styles-and-templates"></a><span data-ttu-id="12dc4-102">Menu 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="12dc4-102">Menu Styles and Templates</span></span>
<span data-ttu-id="12dc4-103">本主題描述的樣式和範本<xref:System.Windows.Controls.Menu>控制項。</span><span class="sxs-lookup"><span data-stu-id="12dc4-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Menu> control.</span></span> <span data-ttu-id="12dc4-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>，讓控制項的獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="12dc4-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="12dc4-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="12dc4-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="menu-parts"></a><span data-ttu-id="12dc4-106">功能表組件</span><span class="sxs-lookup"><span data-stu-id="12dc4-106">Menu Parts</span></span>  
 <span data-ttu-id="12dc4-107"><xref:System.Windows.Controls.Menu>控制項沒有任何具名組件。</span><span class="sxs-lookup"><span data-stu-id="12dc4-107">The <xref:System.Windows.Controls.Menu> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="12dc4-108">當您建立<xref:System.Windows.Controls.ControlTemplate>for <xref:System.Windows.Controls.Menu>，您的範本可能會包含<xref:System.Windows.Controls.ItemsPresenter>內<xref:System.Windows.Controls.ScrollViewer>。</span><span class="sxs-lookup"><span data-stu-id="12dc4-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.Menu>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="12dc4-109">(<xref:System.Windows.Controls.ItemsPresenter>會顯示在每個項目<xref:System.Windows.Controls.Menu>;<xref:System.Windows.Controls.ScrollViewer>可在控制項內捲動)。</span><span class="sxs-lookup"><span data-stu-id="12dc4-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.Menu>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="12dc4-110">如果<xref:System.Windows.Controls.ItemsPresenter>不是直接子系<xref:System.Windows.Controls.ScrollViewer>，您必須給予<xref:System.Windows.Controls.ItemsPresenter>名稱， `ItemsPresenter`。</span><span class="sxs-lookup"><span data-stu-id="12dc4-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="menu-states"></a><span data-ttu-id="12dc4-111">功能表狀態</span><span class="sxs-lookup"><span data-stu-id="12dc4-111">Menu States</span></span>  
 <span data-ttu-id="12dc4-112">下表列出的視覺狀態<xref:System.Windows.Controls.Menu>控制項。</span><span class="sxs-lookup"><span data-stu-id="12dc4-112">The following table lists the visual states for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
|<span data-ttu-id="12dc4-113">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="12dc4-113">VisualState Name</span></span>|<span data-ttu-id="12dc4-114">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="12dc4-114">VisualStateGroup Name</span></span>|<span data-ttu-id="12dc4-115">描述</span><span class="sxs-lookup"><span data-stu-id="12dc4-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="12dc4-116">驗證</span><span class="sxs-lookup"><span data-stu-id="12dc4-116">Valid</span></span>|<span data-ttu-id="12dc4-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="12dc4-117">ValidationStates</span></span>|<span data-ttu-id="12dc4-118">控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。</span><span class="sxs-lookup"><span data-stu-id="12dc4-118">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="12dc4-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="12dc4-119">InvalidFocused</span></span>|<span data-ttu-id="12dc4-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="12dc4-120">ValidationStates</span></span>|<span data-ttu-id="12dc4-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。</span><span class="sxs-lookup"><span data-stu-id="12dc4-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="12dc4-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="12dc4-122">InvalidUnfocused</span></span>|<span data-ttu-id="12dc4-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="12dc4-123">ValidationStates</span></span>|<span data-ttu-id="12dc4-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="12dc4-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="menuitem-parts"></a><span data-ttu-id="12dc4-125">MenuItem 的組件</span><span class="sxs-lookup"><span data-stu-id="12dc4-125">MenuItem Parts</span></span>  
 <span data-ttu-id="12dc4-126">下表列出的具名組件<xref:System.Windows.Controls.Menu>控制項。</span><span class="sxs-lookup"><span data-stu-id="12dc4-126">The following table lists the named parts for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
|<span data-ttu-id="12dc4-127">組件</span><span class="sxs-lookup"><span data-stu-id="12dc4-127">Part</span></span>|<span data-ttu-id="12dc4-128">類型</span><span class="sxs-lookup"><span data-stu-id="12dc4-128">Type</span></span>|<span data-ttu-id="12dc4-129">描述</span><span class="sxs-lookup"><span data-stu-id="12dc4-129">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="12dc4-130">PART_Popup</span><span class="sxs-lookup"><span data-stu-id="12dc4-130">PART_Popup</span></span>|<xref:System.Windows.Controls.Primitives.Popup>|<span data-ttu-id="12dc4-131">子功能表區域。</span><span class="sxs-lookup"><span data-stu-id="12dc4-131">The area for the submenu.</span></span>|  
  
 <span data-ttu-id="12dc4-132">當您建立<xref:System.Windows.Controls.ControlTemplate>for <xref:System.Windows.Controls.MenuItem>，您的範本可能會包含<xref:System.Windows.Controls.ItemsPresenter>內<xref:System.Windows.Controls.ScrollViewer>。</span><span class="sxs-lookup"><span data-stu-id="12dc4-132">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.MenuItem>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="12dc4-133">(<xref:System.Windows.Controls.ItemsPresenter>會顯示在每個項目<xref:System.Windows.Controls.MenuItem>;<xref:System.Windows.Controls.ScrollViewer>可在控制項內捲動)。</span><span class="sxs-lookup"><span data-stu-id="12dc4-133">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.MenuItem>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="12dc4-134">如果<xref:System.Windows.Controls.ItemsPresenter>不是直接子系<xref:System.Windows.Controls.ScrollViewer>，您必須給予<xref:System.Windows.Controls.ItemsPresenter>名稱， `ItemsPresenter`。</span><span class="sxs-lookup"><span data-stu-id="12dc4-134">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="menuitem-states"></a><span data-ttu-id="12dc4-135">功能表項目狀態</span><span class="sxs-lookup"><span data-stu-id="12dc4-135">MenuItem States</span></span>  
 <span data-ttu-id="12dc4-136">下表列出的視覺狀態<xref:System.Windows.Controls.MenuItem>控制項。</span><span class="sxs-lookup"><span data-stu-id="12dc4-136">The following table lists the visual states for the <xref:System.Windows.Controls.MenuItem> control.</span></span>  
  
|<span data-ttu-id="12dc4-137">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="12dc4-137">VisualState Name</span></span>|<span data-ttu-id="12dc4-138">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="12dc4-138">VisualStateGroup Name</span></span>|<span data-ttu-id="12dc4-139">描述</span><span class="sxs-lookup"><span data-stu-id="12dc4-139">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="12dc4-140">驗證</span><span class="sxs-lookup"><span data-stu-id="12dc4-140">Valid</span></span>|<span data-ttu-id="12dc4-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="12dc4-141">ValidationStates</span></span>|<span data-ttu-id="12dc4-142">控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。</span><span class="sxs-lookup"><span data-stu-id="12dc4-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="12dc4-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="12dc4-143">InvalidFocused</span></span>|<span data-ttu-id="12dc4-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="12dc4-144">ValidationStates</span></span>|<span data-ttu-id="12dc4-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。</span><span class="sxs-lookup"><span data-stu-id="12dc4-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="12dc4-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="12dc4-146">InvalidUnfocused</span></span>|<span data-ttu-id="12dc4-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="12dc4-147">ValidationStates</span></span>|<span data-ttu-id="12dc4-148"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="12dc4-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="menu-and-menuitem-controltemplate-example"></a><span data-ttu-id="12dc4-149">功能表和功能表項目 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="12dc4-149">Menu and MenuItem ControlTemplate Example</span></span>  
 <span data-ttu-id="12dc4-150">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.Menu>控制項。</span><span class="sxs-lookup"><span data-stu-id="12dc4-150">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Menu](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menu)]  
  
 <span data-ttu-id="12dc4-151">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.MenuItem>控制項。</span><span class="sxs-lookup"><span data-stu-id="12dc4-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.MenuItem> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#MenuItem](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuitem)]  
  
 <span data-ttu-id="12dc4-152">下列範例會定義`MenuScrollViewer`，上述範例中所用。</span><span class="sxs-lookup"><span data-stu-id="12dc4-152">The following example defines the `MenuScrollViewer`, which is used in the previous example.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#MenuScrollViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuscrollviewer)]  
  
 <span data-ttu-id="12dc4-153"><xref:System.Windows.Controls.ControlTemplate>範例會使用一或多個下列的資源。</span><span class="sxs-lookup"><span data-stu-id="12dc4-153">The <xref:System.Windows.Controls.ControlTemplate> examples use one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="12dc4-154">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="12dc4-154">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12dc4-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12dc4-155">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="12dc4-156">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="12dc4-156">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="12dc4-157">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="12dc4-157">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="12dc4-158">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="12dc4-158">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="12dc4-159">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="12dc4-159">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
