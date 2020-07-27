---
title: Menu 樣式和範本
description: 瞭解功能表控制項 Windows Presentation Foundation 的樣式和範本。 修改 ControlTemplate，讓控制項具有獨特的外觀。
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], Menu
- ControlTemplate [WPF], Menu
- Menu [WPF], styles and templates
- states [WPF], Menu
- templates [WPF], Menu
- parts [WPF], Menu
ms.assetid: b89da183-9b87-42c6-ac53-731a42c7b09e
ms.openlocfilehash: 5187e4a479609686e39e043808931141ca52078c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164549"
---
# <a name="menu-styles-and-templates"></a><span data-ttu-id="6ad62-104">Menu 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="6ad62-104">Menu Styles and Templates</span></span>
<span data-ttu-id="6ad62-105">本主題描述控制項的樣式和範本 <xref:System.Windows.Controls.Menu> 。</span><span class="sxs-lookup"><span data-stu-id="6ad62-105">This topic describes the styles and templates for the <xref:System.Windows.Controls.Menu> control.</span></span> <span data-ttu-id="6ad62-106">您可以修改預設值 <xref:System.Windows.Controls.ControlTemplate> ，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="6ad62-106">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="6ad62-107">如需詳細資訊，請參閱[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。</span><span class="sxs-lookup"><span data-stu-id="6ad62-107">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="menu-parts"></a><span data-ttu-id="6ad62-108">功能表元件</span><span class="sxs-lookup"><span data-stu-id="6ad62-108">Menu Parts</span></span>  
 <span data-ttu-id="6ad62-109"><xref:System.Windows.Controls.Menu>控制項沒有任何已命名的元件。</span><span class="sxs-lookup"><span data-stu-id="6ad62-109">The <xref:System.Windows.Controls.Menu> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="6ad62-110">當您建立的時 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Menu> ，您的範本可能會 <xref:System.Windows.Controls.ItemsPresenter> 在中包含 <xref:System.Windows.Controls.ScrollViewer> 。</span><span class="sxs-lookup"><span data-stu-id="6ad62-110">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.Menu>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="6ad62-111">（會 <xref:System.Windows.Controls.ItemsPresenter> 顯示中的每個專案 <xref:System.Windows.Controls.Menu> ; 會 <xref:System.Windows.Controls.ScrollViewer> 啟用控制項內的滾動功能）。</span><span class="sxs-lookup"><span data-stu-id="6ad62-111">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.Menu>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="6ad62-112">如果不 <xref:System.Windows.Controls.ItemsPresenter> 是的直接子系 <xref:System.Windows.Controls.ScrollViewer> ，您就必須指定 <xref:System.Windows.Controls.ItemsPresenter> 名稱 `ItemsPresenter` 。</span><span class="sxs-lookup"><span data-stu-id="6ad62-112">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="menu-states"></a><span data-ttu-id="6ad62-113">功能表狀態</span><span class="sxs-lookup"><span data-stu-id="6ad62-113">Menu States</span></span>  
 <span data-ttu-id="6ad62-114">下表列出控制項的視覺狀態 <xref:System.Windows.Controls.Menu> 。</span><span class="sxs-lookup"><span data-stu-id="6ad62-114">The following table lists the visual states for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
|<span data-ttu-id="6ad62-115">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="6ad62-115">VisualState Name</span></span>|<span data-ttu-id="6ad62-116">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="6ad62-116">VisualStateGroup Name</span></span>|<span data-ttu-id="6ad62-117">描述</span><span class="sxs-lookup"><span data-stu-id="6ad62-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6ad62-118">有效</span><span class="sxs-lookup"><span data-stu-id="6ad62-118">Valid</span></span>|<span data-ttu-id="6ad62-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6ad62-119">ValidationStates</span></span>|<span data-ttu-id="6ad62-120">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `false` 。</span><span class="sxs-lookup"><span data-stu-id="6ad62-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="6ad62-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="6ad62-121">InvalidFocused</span></span>|<span data-ttu-id="6ad62-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6ad62-122">ValidationStates</span></span>|<span data-ttu-id="6ad62-123"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性的 `true` 焦點是控制項。</span><span class="sxs-lookup"><span data-stu-id="6ad62-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="6ad62-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="6ad62-124">InvalidUnfocused</span></span>|<span data-ttu-id="6ad62-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6ad62-125">ValidationStates</span></span>|<span data-ttu-id="6ad62-126"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="6ad62-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="menuitem-parts"></a><span data-ttu-id="6ad62-127">MenuItem 部分</span><span class="sxs-lookup"><span data-stu-id="6ad62-127">MenuItem Parts</span></span>  
 <span data-ttu-id="6ad62-128">下表列出控制項的已命名元件 <xref:System.Windows.Controls.Menu> 。</span><span class="sxs-lookup"><span data-stu-id="6ad62-128">The following table lists the named parts for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
|<span data-ttu-id="6ad62-129">部分</span><span class="sxs-lookup"><span data-stu-id="6ad62-129">Part</span></span>|<span data-ttu-id="6ad62-130">類型</span><span class="sxs-lookup"><span data-stu-id="6ad62-130">Type</span></span>|<span data-ttu-id="6ad62-131">描述</span><span class="sxs-lookup"><span data-stu-id="6ad62-131">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6ad62-132">PART_Popup</span><span class="sxs-lookup"><span data-stu-id="6ad62-132">PART_Popup</span></span>|<xref:System.Windows.Controls.Primitives.Popup>|<span data-ttu-id="6ad62-133">子功能表的區域。</span><span class="sxs-lookup"><span data-stu-id="6ad62-133">The area for the submenu.</span></span>|  
  
 <span data-ttu-id="6ad62-134">當您建立的時 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.MenuItem> ，您的範本可能會 <xref:System.Windows.Controls.ItemsPresenter> 在中包含 <xref:System.Windows.Controls.ScrollViewer> 。</span><span class="sxs-lookup"><span data-stu-id="6ad62-134">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.MenuItem>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="6ad62-135">（會 <xref:System.Windows.Controls.ItemsPresenter> 顯示中的每個專案 <xref:System.Windows.Controls.MenuItem> ; 會 <xref:System.Windows.Controls.ScrollViewer> 啟用控制項內的滾動功能）。</span><span class="sxs-lookup"><span data-stu-id="6ad62-135">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.MenuItem>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="6ad62-136">如果不 <xref:System.Windows.Controls.ItemsPresenter> 是的直接子系 <xref:System.Windows.Controls.ScrollViewer> ，您就必須指定 <xref:System.Windows.Controls.ItemsPresenter> 名稱 `ItemsPresenter` 。</span><span class="sxs-lookup"><span data-stu-id="6ad62-136">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="menuitem-states"></a><span data-ttu-id="6ad62-137">MenuItem 狀態</span><span class="sxs-lookup"><span data-stu-id="6ad62-137">MenuItem States</span></span>  
 <span data-ttu-id="6ad62-138">下表列出控制項的視覺狀態 <xref:System.Windows.Controls.MenuItem> 。</span><span class="sxs-lookup"><span data-stu-id="6ad62-138">The following table lists the visual states for the <xref:System.Windows.Controls.MenuItem> control.</span></span>  
  
|<span data-ttu-id="6ad62-139">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="6ad62-139">VisualState Name</span></span>|<span data-ttu-id="6ad62-140">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="6ad62-140">VisualStateGroup Name</span></span>|<span data-ttu-id="6ad62-141">描述</span><span class="sxs-lookup"><span data-stu-id="6ad62-141">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6ad62-142">有效</span><span class="sxs-lookup"><span data-stu-id="6ad62-142">Valid</span></span>|<span data-ttu-id="6ad62-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6ad62-143">ValidationStates</span></span>|<span data-ttu-id="6ad62-144">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `false` 。</span><span class="sxs-lookup"><span data-stu-id="6ad62-144">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="6ad62-145">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="6ad62-145">InvalidFocused</span></span>|<span data-ttu-id="6ad62-146">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6ad62-146">ValidationStates</span></span>|<span data-ttu-id="6ad62-147"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性的 `true` 焦點是控制項。</span><span class="sxs-lookup"><span data-stu-id="6ad62-147">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="6ad62-148">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="6ad62-148">InvalidUnfocused</span></span>|<span data-ttu-id="6ad62-149">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6ad62-149">ValidationStates</span></span>|<span data-ttu-id="6ad62-150"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="6ad62-150">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="menu-and-menuitem-controltemplate-example"></a><span data-ttu-id="6ad62-151">功能表和 MenuItem ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="6ad62-151">Menu and MenuItem ControlTemplate Example</span></span>  
 <span data-ttu-id="6ad62-152">下列範例顯示如何定義 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Menu> 控制項的。</span><span class="sxs-lookup"><span data-stu-id="6ad62-152">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Menu](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menu)]  
  
 <span data-ttu-id="6ad62-153">下列範例顯示如何定義 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.MenuItem> 控制項的。</span><span class="sxs-lookup"><span data-stu-id="6ad62-153">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.MenuItem> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#MenuItem](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuitem)]  
  
 <span data-ttu-id="6ad62-154">下列範例 `MenuScrollViewer` 會定義上一個範例中所使用的。</span><span class="sxs-lookup"><span data-stu-id="6ad62-154">The following example defines the `MenuScrollViewer`, which is used in the previous example.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#MenuScrollViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuscrollviewer)]  
  
 <span data-ttu-id="6ad62-155">這些 <xref:System.Windows.Controls.ControlTemplate> 範例會使用下列一或多個資源。</span><span class="sxs-lookup"><span data-stu-id="6ad62-155">The <xref:System.Windows.Controls.ControlTemplate> examples use one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="6ad62-156">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="6ad62-156">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ad62-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ad62-157">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="6ad62-158">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="6ad62-158">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="6ad62-159">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="6ad62-159">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="6ad62-160">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="6ad62-160">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="6ad62-161">建立控制項的範本</span><span class="sxs-lookup"><span data-stu-id="6ad62-161">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
