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
ms.openlocfilehash: 979ed7292a0f6582753305d1a7704c48aa751003
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460216"
---
# <a name="menu-styles-and-templates"></a><span data-ttu-id="67a8e-102">Menu 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="67a8e-102">Menu Styles and Templates</span></span>
<span data-ttu-id="67a8e-103">本主題描述 <xref:System.Windows.Controls.Menu> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="67a8e-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Menu> control.</span></span> <span data-ttu-id="67a8e-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="67a8e-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="67a8e-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="67a8e-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="menu-parts"></a><span data-ttu-id="67a8e-106">功能表元件</span><span class="sxs-lookup"><span data-stu-id="67a8e-106">Menu Parts</span></span>  
 <span data-ttu-id="67a8e-107"><xref:System.Windows.Controls.Menu> 控制項沒有任何已命名的元件。</span><span class="sxs-lookup"><span data-stu-id="67a8e-107">The <xref:System.Windows.Controls.Menu> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="67a8e-108">當您建立 <xref:System.Windows.Controls.Menu>的 <xref:System.Windows.Controls.ControlTemplate> 時，您的範本可能會在 <xref:System.Windows.Controls.ScrollViewer>中包含 <xref:System.Windows.Controls.ItemsPresenter>。</span><span class="sxs-lookup"><span data-stu-id="67a8e-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.Menu>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="67a8e-109">（<xref:System.Windows.Controls.ItemsPresenter> 會顯示 <xref:System.Windows.Controls.Menu>中的每個專案，<xref:System.Windows.Controls.ScrollViewer> 可在控制項內進行滾動）。</span><span class="sxs-lookup"><span data-stu-id="67a8e-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.Menu>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="67a8e-110">如果 <xref:System.Windows.Controls.ItemsPresenter> 不是 <xref:System.Windows.Controls.ScrollViewer>的直接子系，您必須為 <xref:System.Windows.Controls.ItemsPresenter> 指定名稱，`ItemsPresenter`。</span><span class="sxs-lookup"><span data-stu-id="67a8e-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="menu-states"></a><span data-ttu-id="67a8e-111">功能表狀態</span><span class="sxs-lookup"><span data-stu-id="67a8e-111">Menu States</span></span>  
 <span data-ttu-id="67a8e-112">下表列出 <xref:System.Windows.Controls.Menu> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="67a8e-112">The following table lists the visual states for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
|<span data-ttu-id="67a8e-113">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="67a8e-113">VisualState Name</span></span>|<span data-ttu-id="67a8e-114">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="67a8e-114">VisualStateGroup Name</span></span>|<span data-ttu-id="67a8e-115">描述</span><span class="sxs-lookup"><span data-stu-id="67a8e-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="67a8e-116">驗證</span><span class="sxs-lookup"><span data-stu-id="67a8e-116">Valid</span></span>|<span data-ttu-id="67a8e-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="67a8e-117">ValidationStates</span></span>|<span data-ttu-id="67a8e-118">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="67a8e-118">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="67a8e-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="67a8e-119">InvalidFocused</span></span>|<span data-ttu-id="67a8e-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="67a8e-120">ValidationStates</span></span>|<span data-ttu-id="67a8e-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="67a8e-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="67a8e-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="67a8e-122">InvalidUnfocused</span></span>|<span data-ttu-id="67a8e-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="67a8e-123">ValidationStates</span></span>|<span data-ttu-id="67a8e-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="67a8e-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="menuitem-parts"></a><span data-ttu-id="67a8e-125">MenuItem 部分</span><span class="sxs-lookup"><span data-stu-id="67a8e-125">MenuItem Parts</span></span>  
 <span data-ttu-id="67a8e-126">下表列出 <xref:System.Windows.Controls.Menu> 控制項的已命名元件。</span><span class="sxs-lookup"><span data-stu-id="67a8e-126">The following table lists the named parts for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
|<span data-ttu-id="67a8e-127">組件</span><span class="sxs-lookup"><span data-stu-id="67a8e-127">Part</span></span>|<span data-ttu-id="67a8e-128">輸入</span><span class="sxs-lookup"><span data-stu-id="67a8e-128">Type</span></span>|<span data-ttu-id="67a8e-129">描述</span><span class="sxs-lookup"><span data-stu-id="67a8e-129">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="67a8e-130">PART_Popup</span><span class="sxs-lookup"><span data-stu-id="67a8e-130">PART_Popup</span></span>|<xref:System.Windows.Controls.Primitives.Popup>|<span data-ttu-id="67a8e-131">子功能表的區域。</span><span class="sxs-lookup"><span data-stu-id="67a8e-131">The area for the submenu.</span></span>|  
  
 <span data-ttu-id="67a8e-132">當您建立 <xref:System.Windows.Controls.MenuItem>的 <xref:System.Windows.Controls.ControlTemplate> 時，您的範本可能會在 <xref:System.Windows.Controls.ScrollViewer>中包含 <xref:System.Windows.Controls.ItemsPresenter>。</span><span class="sxs-lookup"><span data-stu-id="67a8e-132">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.MenuItem>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="67a8e-133">（<xref:System.Windows.Controls.ItemsPresenter> 會顯示 <xref:System.Windows.Controls.MenuItem>中的每個專案，<xref:System.Windows.Controls.ScrollViewer> 可在控制項內進行滾動）。</span><span class="sxs-lookup"><span data-stu-id="67a8e-133">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.MenuItem>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="67a8e-134">如果 <xref:System.Windows.Controls.ItemsPresenter> 不是 <xref:System.Windows.Controls.ScrollViewer>的直接子系，您必須為 <xref:System.Windows.Controls.ItemsPresenter> 指定名稱，`ItemsPresenter`。</span><span class="sxs-lookup"><span data-stu-id="67a8e-134">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="menuitem-states"></a><span data-ttu-id="67a8e-135">MenuItem 狀態</span><span class="sxs-lookup"><span data-stu-id="67a8e-135">MenuItem States</span></span>  
 <span data-ttu-id="67a8e-136">下表列出 <xref:System.Windows.Controls.MenuItem> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="67a8e-136">The following table lists the visual states for the <xref:System.Windows.Controls.MenuItem> control.</span></span>  
  
|<span data-ttu-id="67a8e-137">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="67a8e-137">VisualState Name</span></span>|<span data-ttu-id="67a8e-138">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="67a8e-138">VisualStateGroup Name</span></span>|<span data-ttu-id="67a8e-139">描述</span><span class="sxs-lookup"><span data-stu-id="67a8e-139">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="67a8e-140">驗證</span><span class="sxs-lookup"><span data-stu-id="67a8e-140">Valid</span></span>|<span data-ttu-id="67a8e-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="67a8e-141">ValidationStates</span></span>|<span data-ttu-id="67a8e-142">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="67a8e-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="67a8e-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="67a8e-143">InvalidFocused</span></span>|<span data-ttu-id="67a8e-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="67a8e-144">ValidationStates</span></span>|<span data-ttu-id="67a8e-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="67a8e-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="67a8e-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="67a8e-146">InvalidUnfocused</span></span>|<span data-ttu-id="67a8e-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="67a8e-147">ValidationStates</span></span>|<span data-ttu-id="67a8e-148"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="67a8e-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="menu-and-menuitem-controltemplate-example"></a><span data-ttu-id="67a8e-149">功能表和 MenuItem ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="67a8e-149">Menu and MenuItem ControlTemplate Example</span></span>  
 <span data-ttu-id="67a8e-150">下列範例顯示如何定義 <xref:System.Windows.Controls.Menu> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="67a8e-150">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Menu](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menu)]  
  
 <span data-ttu-id="67a8e-151">下列範例顯示如何定義 <xref:System.Windows.Controls.MenuItem> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="67a8e-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.MenuItem> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#MenuItem](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuitem)]  
  
 <span data-ttu-id="67a8e-152">下列範例會定義上一個範例中使用的 `MenuScrollViewer`。</span><span class="sxs-lookup"><span data-stu-id="67a8e-152">The following example defines the `MenuScrollViewer`, which is used in the previous example.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#MenuScrollViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuscrollviewer)]  
  
 <span data-ttu-id="67a8e-153"><xref:System.Windows.Controls.ControlTemplate> 範例會使用下列一或多個資源。</span><span class="sxs-lookup"><span data-stu-id="67a8e-153">The <xref:System.Windows.Controls.ControlTemplate> examples use one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="67a8e-154">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="67a8e-154">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67a8e-155">請參閱</span><span class="sxs-lookup"><span data-stu-id="67a8e-155">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="67a8e-156">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="67a8e-156">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="67a8e-157">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="67a8e-157">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="67a8e-158">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="67a8e-158">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="67a8e-159">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="67a8e-159">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
