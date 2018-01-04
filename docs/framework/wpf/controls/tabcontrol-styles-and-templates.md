---
title: "TabControl 樣式和範本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], TabControl
- TabControl [WPF], styles and templates [WPF]
- parts [WPF], TabControl
- styles [WPF], TabControl
- states [WPF], TabControl
- templates [WPF], TabControl
ms.assetid: f6b19a30-f10e-4fa1-96ce-f17a54092ab6
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 22d1e4dbd8e7a3ca6ec9f0c91e5e59be2f683455
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="tabcontrol-styles-and-templates"></a><span data-ttu-id="c7f1f-102">TabControl 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="c7f1f-102">TabControl Styles and Templates</span></span>
<span data-ttu-id="c7f1f-103">本主題描述樣式和範本<xref:System.Windows.Controls.TabControl>控制項。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.TabControl> control.</span></span> <span data-ttu-id="c7f1f-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="c7f1f-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="tabcontrol-parts"></a><span data-ttu-id="c7f1f-106">TabControl 組件</span><span class="sxs-lookup"><span data-stu-id="c7f1f-106">TabControl Parts</span></span>  
 <span data-ttu-id="c7f1f-107">下表列出的具名組件<xref:System.Windows.Controls.TabControl>控制項。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-107">The following table lists the named parts for the <xref:System.Windows.Controls.TabControl> control.</span></span>  
  
|<span data-ttu-id="c7f1f-108">組件</span><span class="sxs-lookup"><span data-stu-id="c7f1f-108">Part</span></span>|<span data-ttu-id="c7f1f-109">類型</span><span class="sxs-lookup"><span data-stu-id="c7f1f-109">Type</span></span>|<span data-ttu-id="c7f1f-110">描述</span><span class="sxs-lookup"><span data-stu-id="c7f1f-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="c7f1f-111">PART_SelectedContentHost</span><span class="sxs-lookup"><span data-stu-id="c7f1f-111">PART_SelectedContentHost</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="c7f1f-112">顯示目前選取的內容物件<xref:System.Windows.Controls.TabItem>。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-112">The object that shows the content of the currently selected <xref:System.Windows.Controls.TabItem>.</span></span>|  
  
 <span data-ttu-id="c7f1f-113">當您建立<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.TabControl>，可能會包含您的範本<xref:System.Windows.Controls.ItemsPresenter>內<xref:System.Windows.Controls.ScrollViewer>。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-113">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.TabControl>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="c7f1f-114">(<xref:System.Windows.Controls.ItemsPresenter>會顯示每個項目<xref:System.Windows.Controls.TabControl>;<xref:System.Windows.Controls.ScrollViewer>可捲動控制項內)。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-114">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.TabControl>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="c7f1f-115">如果<xref:System.Windows.Controls.ItemsPresenter>不是直接子系<xref:System.Windows.Controls.ScrollViewer>，您必須提供<xref:System.Windows.Controls.ItemsPresenter>名稱`ItemsPresenter`。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-115">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="tabcontrol-states"></a><span data-ttu-id="c7f1f-116">TabControl 狀態</span><span class="sxs-lookup"><span data-stu-id="c7f1f-116">TabControl States</span></span>  
 <span data-ttu-id="c7f1f-117">下表列出的視覺狀態<xref:System.Windows.Controls.TabControl>控制項。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-117">The following table lists the visual states for the <xref:System.Windows.Controls.TabControl> control.</span></span>  
  
|<span data-ttu-id="c7f1f-118">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="c7f1f-118">VisualState Name</span></span>|<span data-ttu-id="c7f1f-119">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="c7f1f-119">VisualStateGroup Name</span></span>|<span data-ttu-id="c7f1f-120">描述</span><span class="sxs-lookup"><span data-stu-id="c7f1f-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="c7f1f-121">一般</span><span class="sxs-lookup"><span data-stu-id="c7f1f-121">Normal</span></span>|<span data-ttu-id="c7f1f-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c7f1f-122">CommonStates</span></span>|<span data-ttu-id="c7f1f-123">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-123">The default state.</span></span>|  
|<span data-ttu-id="c7f1f-124">已停用</span><span class="sxs-lookup"><span data-stu-id="c7f1f-124">Disabled</span></span>|<span data-ttu-id="c7f1f-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c7f1f-125">CommonStates</span></span>|<span data-ttu-id="c7f1f-126">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-126">The control is disabled.</span></span>|  
|<span data-ttu-id="c7f1f-127">驗證</span><span class="sxs-lookup"><span data-stu-id="c7f1f-127">Valid</span></span>|<span data-ttu-id="c7f1f-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c7f1f-128">ValidationStates</span></span>|<span data-ttu-id="c7f1f-129">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="c7f1f-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="c7f1f-130">InvalidFocused</span></span>|<span data-ttu-id="c7f1f-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c7f1f-131">ValidationStates</span></span>|<span data-ttu-id="c7f1f-132"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="c7f1f-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="c7f1f-133">InvalidUnfocused</span></span>|<span data-ttu-id="c7f1f-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c7f1f-134">ValidationStates</span></span>|<span data-ttu-id="c7f1f-135"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tabitem-parts"></a><span data-ttu-id="c7f1f-136">TabItem 組件</span><span class="sxs-lookup"><span data-stu-id="c7f1f-136">TabItem Parts</span></span>  
 <span data-ttu-id="c7f1f-137"><xref:System.Windows.Controls.TabItem>控制項沒有任何已命名的組件。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-137">The <xref:System.Windows.Controls.TabItem> control does not have any named parts.</span></span>  
  
## <a name="tabitem-states"></a><span data-ttu-id="c7f1f-138">TabItem 狀態</span><span class="sxs-lookup"><span data-stu-id="c7f1f-138">TabItem States</span></span>  
 <span data-ttu-id="c7f1f-139">下表列出的視覺狀態<xref:System.Windows.Controls.TabItem>控制項。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-139">The following table lists the visual states for the <xref:System.Windows.Controls.TabItem> control.</span></span>  
  
|<span data-ttu-id="c7f1f-140">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="c7f1f-140">VisualState Name</span></span>|<span data-ttu-id="c7f1f-141">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="c7f1f-141">VisualStateGroup Name</span></span>|<span data-ttu-id="c7f1f-142">描述</span><span class="sxs-lookup"><span data-stu-id="c7f1f-142">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="c7f1f-143">一般</span><span class="sxs-lookup"><span data-stu-id="c7f1f-143">Normal</span></span>|<span data-ttu-id="c7f1f-144">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c7f1f-144">CommonStates</span></span>|<span data-ttu-id="c7f1f-145">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-145">The default state.</span></span>|  
|<span data-ttu-id="c7f1f-146">MouseOver</span><span class="sxs-lookup"><span data-stu-id="c7f1f-146">MouseOver</span></span>|<span data-ttu-id="c7f1f-147">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c7f1f-147">CommonStates</span></span>|<span data-ttu-id="c7f1f-148">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-148">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="c7f1f-149">已停用</span><span class="sxs-lookup"><span data-stu-id="c7f1f-149">Disabled</span></span>|<span data-ttu-id="c7f1f-150">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c7f1f-150">CommonStates</span></span>|<span data-ttu-id="c7f1f-151">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-151">The control is disabled.</span></span>|  
|<span data-ttu-id="c7f1f-152">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="c7f1f-152">Focused</span></span>|<span data-ttu-id="c7f1f-153">FocusStates</span><span class="sxs-lookup"><span data-stu-id="c7f1f-153">FocusStates</span></span>|<span data-ttu-id="c7f1f-154">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-154">The control has focus.</span></span>|  
|<span data-ttu-id="c7f1f-155">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="c7f1f-155">Unfocused</span></span>|<span data-ttu-id="c7f1f-156">FocusStates</span><span class="sxs-lookup"><span data-stu-id="c7f1f-156">FocusStates</span></span>|<span data-ttu-id="c7f1f-157">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-157">The control does not have focus.</span></span>|  
|<span data-ttu-id="c7f1f-158">已選取</span><span class="sxs-lookup"><span data-stu-id="c7f1f-158">Selected</span></span>|<span data-ttu-id="c7f1f-159">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="c7f1f-159">SelectionStates</span></span>|<span data-ttu-id="c7f1f-160">選取控制項。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-160">The control is selected.</span></span>|  
|<span data-ttu-id="c7f1f-161">未選取</span><span class="sxs-lookup"><span data-stu-id="c7f1f-161">Unselected</span></span>|<span data-ttu-id="c7f1f-162">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="c7f1f-162">SelectionStates</span></span>|<span data-ttu-id="c7f1f-163">未選取控制項。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-163">The control is not selected.</span></span>|  
|<span data-ttu-id="c7f1f-164">驗證</span><span class="sxs-lookup"><span data-stu-id="c7f1f-164">Valid</span></span>|<span data-ttu-id="c7f1f-165">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c7f1f-165">ValidationStates</span></span>|<span data-ttu-id="c7f1f-166">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-166">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="c7f1f-167">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="c7f1f-167">InvalidFocused</span></span>|<span data-ttu-id="c7f1f-168">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c7f1f-168">ValidationStates</span></span>|<span data-ttu-id="c7f1f-169"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-169">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="c7f1f-170">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="c7f1f-170">InvalidUnfocused</span></span>|<span data-ttu-id="c7f1f-171">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c7f1f-171">ValidationStates</span></span>|<span data-ttu-id="c7f1f-172"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-172">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tabcontrol-controltemplate-example"></a><span data-ttu-id="c7f1f-173">TabControl ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="c7f1f-173">TabControl ControlTemplate Example</span></span>  
 <span data-ttu-id="c7f1f-174">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.TabControl>和<xref:System.Windows.Controls.TabItem>控制項。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-174">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TabControl> and <xref:System.Windows.Controls.TabItem> controls.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TabControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tabcontrol.xaml#tabcontrol)]  
  
 <span data-ttu-id="c7f1f-175">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-175">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="c7f1f-176">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041)。</span><span class="sxs-lookup"><span data-stu-id="c7f1f-176">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7f1f-177">請參閱</span><span class="sxs-lookup"><span data-stu-id="c7f1f-177">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="c7f1f-178">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="c7f1f-178">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="c7f1f-179">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="c7f1f-179">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="c7f1f-180">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="c7f1f-180">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="c7f1f-181">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="c7f1f-181">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
