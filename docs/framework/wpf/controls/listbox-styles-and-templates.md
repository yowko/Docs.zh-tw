---
title: "ListBox 樣式和範本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], ListBox
- templates [WPF], ListBox
- states [WPF], ListBox
- ControlTemplate [WPF], ListBox
- parts [WPF], ListBox
- ListBox [WPF], styles and templates
ms.assetid: fc5764cb-c27b-495b-88d4-d969a8213ccb
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: edf8c50424a9694c4e00f5bf319d3122999bda85
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="listbox-styles-and-templates"></a><span data-ttu-id="ed022-102">ListBox 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="ed022-102">ListBox Styles and Templates</span></span>
<span data-ttu-id="ed022-103">本主題描述樣式和範本<xref:System.Windows.Controls.ListBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="ed022-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="ed022-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="ed022-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="ed022-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="ed022-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="listbox-parts"></a><span data-ttu-id="ed022-106">ListBox 組件</span><span class="sxs-lookup"><span data-stu-id="ed022-106">ListBox Parts</span></span>  
 <span data-ttu-id="ed022-107"><xref:System.Windows.Controls.ListBox>控制項沒有任何已命名的組件。</span><span class="sxs-lookup"><span data-stu-id="ed022-107">The <xref:System.Windows.Controls.ListBox> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="ed022-108">當您建立<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.ListBox>，可能會包含您的範本<xref:System.Windows.Controls.ItemsPresenter>內<xref:System.Windows.Controls.ScrollViewer>。</span><span class="sxs-lookup"><span data-stu-id="ed022-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ListBox>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="ed022-109">(<xref:System.Windows.Controls.ItemsPresenter>會顯示每個項目<xref:System.Windows.Controls.ListBox>;<xref:System.Windows.Controls.ScrollViewer>可捲動控制項內)。</span><span class="sxs-lookup"><span data-stu-id="ed022-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ListBox>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="ed022-110">如果<xref:System.Windows.Controls.ItemsPresenter>不是直接子系<xref:System.Windows.Controls.ScrollViewer>，您必須提供<xref:System.Windows.Controls.ItemsPresenter>名稱`ItemsPresenter`。</span><span class="sxs-lookup"><span data-stu-id="ed022-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="listbox-states"></a><span data-ttu-id="ed022-111">ListBox 狀態</span><span class="sxs-lookup"><span data-stu-id="ed022-111">ListBox States</span></span>  
 <span data-ttu-id="ed022-112">下表列出的視覺狀態<xref:System.Windows.Controls.ListBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="ed022-112">The following table lists the visual states for the <xref:System.Windows.Controls.ListBox> control.</span></span>  
  
|<span data-ttu-id="ed022-113">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="ed022-113">VisualState Name</span></span>|<span data-ttu-id="ed022-114">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="ed022-114">VisualStateGroup Name</span></span>|<span data-ttu-id="ed022-115">描述</span><span class="sxs-lookup"><span data-stu-id="ed022-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ed022-116">驗證</span><span class="sxs-lookup"><span data-stu-id="ed022-116">Valid</span></span>|<span data-ttu-id="ed022-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ed022-117">ValidationStates</span></span>|<span data-ttu-id="ed022-118">控制項有效。</span><span class="sxs-lookup"><span data-stu-id="ed022-118">The control is valid.</span></span>|  
|<span data-ttu-id="ed022-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="ed022-119">InvalidFocused</span></span>|<span data-ttu-id="ed022-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ed022-120">ValidationStates</span></span>|<span data-ttu-id="ed022-121">控制項無效且已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="ed022-121">The control is not valid and has focus.</span></span>|  
|<span data-ttu-id="ed022-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="ed022-122">InvalidUnfocused</span></span>|<span data-ttu-id="ed022-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ed022-123">ValidationStates</span></span>|<span data-ttu-id="ed022-124">控制項無效且未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="ed022-124">The control is not valid and does not have focus.</span></span>|  
  
## <a name="listboxitem-parts"></a><span data-ttu-id="ed022-125">ListBoxItem 組件</span><span class="sxs-lookup"><span data-stu-id="ed022-125">ListBoxItem Parts</span></span>  
 <span data-ttu-id="ed022-126"><xref:System.Windows.Controls.ListBoxItem>控制項沒有任何已命名的組件。</span><span class="sxs-lookup"><span data-stu-id="ed022-126">The <xref:System.Windows.Controls.ListBoxItem> control does not have any named parts.</span></span>  
  
## <a name="listboxitem-states"></a><span data-ttu-id="ed022-127">ListBoxItem 狀態</span><span class="sxs-lookup"><span data-stu-id="ed022-127">ListBoxItem States</span></span>  
 <span data-ttu-id="ed022-128">下表列出的視覺狀態<xref:System.Windows.Controls.ListBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="ed022-128">The following table lists the visual states for the <xref:System.Windows.Controls.ListBox> control.</span></span>  
  
|<span data-ttu-id="ed022-129">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="ed022-129">VisualState Name</span></span>|<span data-ttu-id="ed022-130">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="ed022-130">VisualStateGroup Name</span></span>|<span data-ttu-id="ed022-131">描述</span><span class="sxs-lookup"><span data-stu-id="ed022-131">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ed022-132">一般</span><span class="sxs-lookup"><span data-stu-id="ed022-132">Normal</span></span>|<span data-ttu-id="ed022-133">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ed022-133">CommonStates</span></span>|<span data-ttu-id="ed022-134">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="ed022-134">The default state.</span></span>|  
|<span data-ttu-id="ed022-135">MouseOver</span><span class="sxs-lookup"><span data-stu-id="ed022-135">MouseOver</span></span>|<span data-ttu-id="ed022-136">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ed022-136">CommonStates</span></span>|<span data-ttu-id="ed022-137">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="ed022-137">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="ed022-138">已停用</span><span class="sxs-lookup"><span data-stu-id="ed022-138">Disabled</span></span>|<span data-ttu-id="ed022-139">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ed022-139">CommonStates</span></span>|<span data-ttu-id="ed022-140">項目已停用。</span><span class="sxs-lookup"><span data-stu-id="ed022-140">The item is disabled.</span></span>|  
|<span data-ttu-id="ed022-141">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="ed022-141">Focused</span></span>|<span data-ttu-id="ed022-142">FocusStates</span><span class="sxs-lookup"><span data-stu-id="ed022-142">FocusStates</span></span>|<span data-ttu-id="ed022-143">項目已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="ed022-143">The item has focus.</span></span>|  
|<span data-ttu-id="ed022-144">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="ed022-144">Unfocused</span></span>|<span data-ttu-id="ed022-145">FocusStates</span><span class="sxs-lookup"><span data-stu-id="ed022-145">FocusStates</span></span>|<span data-ttu-id="ed022-146">項目未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="ed022-146">The item does not have focus.</span></span>|  
|<span data-ttu-id="ed022-147">未選取</span><span class="sxs-lookup"><span data-stu-id="ed022-147">Unselected</span></span>|<span data-ttu-id="ed022-148">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="ed022-148">SelectionStates</span></span>|<span data-ttu-id="ed022-149">項目未獲選取。</span><span class="sxs-lookup"><span data-stu-id="ed022-149">The item is not selected.</span></span>|  
|<span data-ttu-id="ed022-150">已選取</span><span class="sxs-lookup"><span data-stu-id="ed022-150">Selected</span></span>|<span data-ttu-id="ed022-151">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="ed022-151">SelectionStates</span></span>|<span data-ttu-id="ed022-152">項目目前已獲選取。</span><span class="sxs-lookup"><span data-stu-id="ed022-152">The item is currentlyplate selected.</span></span>|  
|<span data-ttu-id="ed022-153">SelectedUnfocused</span><span class="sxs-lookup"><span data-stu-id="ed022-153">SelectedUnfocused</span></span>|<span data-ttu-id="ed022-154">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="ed022-154">SelectionStates</span></span>|<span data-ttu-id="ed022-155">項目已獲選取，但未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="ed022-155">The item is selected, but does not have focus.</span></span>|  
|<span data-ttu-id="ed022-156">驗證</span><span class="sxs-lookup"><span data-stu-id="ed022-156">Valid</span></span>|<span data-ttu-id="ed022-157">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ed022-157">ValidationStates</span></span>|<span data-ttu-id="ed022-158">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="ed022-158">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="ed022-159">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="ed022-159">InvalidFocused</span></span>|<span data-ttu-id="ed022-160">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ed022-160">ValidationStates</span></span>|<span data-ttu-id="ed022-161"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="ed022-161">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="ed022-162">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="ed022-162">InvalidUnfocused</span></span>|<span data-ttu-id="ed022-163">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ed022-163">ValidationStates</span></span>|<span data-ttu-id="ed022-164"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="ed022-164">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="listbox-controltemplate-example"></a><span data-ttu-id="ed022-165">ListBox ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="ed022-165">ListBox ControlTemplate Example</span></span>  
 <span data-ttu-id="ed022-166">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.ListBox>和<xref:System.Windows.Controls.ListBoxItem>控制項。</span><span class="sxs-lookup"><span data-stu-id="ed022-166">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ListBox> and <xref:System.Windows.Controls.ListBoxItem> controls.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ListBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listbox.xaml#listbox)]  
  
 <span data-ttu-id="ed022-167">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="ed022-167">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="ed022-168">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041)。</span><span class="sxs-lookup"><span data-stu-id="ed022-168">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed022-169">請參閱</span><span class="sxs-lookup"><span data-stu-id="ed022-169">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="ed022-170">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="ed022-170">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="ed022-171">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="ed022-171">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="ed022-172">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="ed022-172">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="ed022-173">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="ed022-173">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
