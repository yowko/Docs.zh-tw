---
title: "ListView 樣式和範本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], ListView
- states [WPF], ListView
- ControlTemplate [WPF], ListView
- styles [WPF], ListView
- ListView [WPF], styles and templates
- templates [WPF], ListView
ms.assetid: d2387356-2171-4785-822a-7247e024b4ee
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ccd597aa6d517bb3a7dda347c26c0eaf731a278f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="listview-styles-and-templates"></a><span data-ttu-id="0e162-102">ListView 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="0e162-102">ListView Styles and Templates</span></span>
<span data-ttu-id="0e162-103">本主題描述樣式和範本<xref:System.Windows.Controls.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="0e162-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="0e162-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="0e162-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="0e162-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="0e162-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="listview-parts"></a><span data-ttu-id="0e162-106">ListView 組件</span><span class="sxs-lookup"><span data-stu-id="0e162-106">ListView Parts</span></span>  
 <span data-ttu-id="0e162-107"><xref:System.Windows.Controls.ListView>控制項沒有任何已命名的組件。</span><span class="sxs-lookup"><span data-stu-id="0e162-107">The <xref:System.Windows.Controls.ListView> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="0e162-108">當您建立<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.ListView>，可能會包含您的範本<xref:System.Windows.Controls.ItemsPresenter>內<xref:System.Windows.Controls.ScrollViewer>。</span><span class="sxs-lookup"><span data-stu-id="0e162-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ListView>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="0e162-109">(<xref:System.Windows.Controls.ItemsPresenter>會顯示每個項目<xref:System.Windows.Controls.ListView>;<xref:System.Windows.Controls.ScrollViewer>可捲動控制項內)。</span><span class="sxs-lookup"><span data-stu-id="0e162-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ListView>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="0e162-110">如果<xref:System.Windows.Controls.ItemsPresenter>不是直接子系<xref:System.Windows.Controls.ScrollViewer>，您必須提供<xref:System.Windows.Controls.ItemsPresenter>名稱`ItemsPresenter`。</span><span class="sxs-lookup"><span data-stu-id="0e162-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="listview-states"></a><span data-ttu-id="0e162-111">ListView 狀態</span><span class="sxs-lookup"><span data-stu-id="0e162-111">ListView States</span></span>  
 <span data-ttu-id="0e162-112">下表列出的視覺狀態<xref:System.Windows.Controls.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="0e162-112">The following table lists the visual states for the <xref:System.Windows.Controls.ListView> control.</span></span>  
  
|<span data-ttu-id="0e162-113">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="0e162-113">VisualState Name</span></span>|<span data-ttu-id="0e162-114">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="0e162-114">VisualStateGroup Name</span></span>|<span data-ttu-id="0e162-115">描述</span><span class="sxs-lookup"><span data-stu-id="0e162-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="0e162-116">驗證</span><span class="sxs-lookup"><span data-stu-id="0e162-116">Valid</span></span>|<span data-ttu-id="0e162-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0e162-117">ValidationStates</span></span>|<span data-ttu-id="0e162-118">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="0e162-118">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="0e162-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="0e162-119">InvalidFocused</span></span>|<span data-ttu-id="0e162-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0e162-120">ValidationStates</span></span>|<span data-ttu-id="0e162-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="0e162-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="0e162-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="0e162-122">InvalidUnfocused</span></span>|<span data-ttu-id="0e162-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0e162-123">ValidationStates</span></span>|<span data-ttu-id="0e162-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="0e162-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="listviewitem-parts"></a><span data-ttu-id="0e162-125">ListViewItem 組件</span><span class="sxs-lookup"><span data-stu-id="0e162-125">ListViewItem Parts</span></span>  
 <span data-ttu-id="0e162-126"><xref:System.Windows.Controls.ListViewItem>控制項沒有任何已命名的組件。</span><span class="sxs-lookup"><span data-stu-id="0e162-126">The <xref:System.Windows.Controls.ListViewItem> control does not have any named parts.</span></span>  
  
## <a name="listviewitem-states"></a><span data-ttu-id="0e162-127">ListViewItem 狀態</span><span class="sxs-lookup"><span data-stu-id="0e162-127">ListViewItem States</span></span>  
 <span data-ttu-id="0e162-128">下表列出的狀態<xref:System.Windows.Controls.ListViewItem>控制項。</span><span class="sxs-lookup"><span data-stu-id="0e162-128">The following table lists the states for the <xref:System.Windows.Controls.ListViewItem> control.</span></span>  
  
|<span data-ttu-id="0e162-129">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="0e162-129">VisualState Name</span></span>|<span data-ttu-id="0e162-130">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="0e162-130">VisualStateGroup Name</span></span>|<span data-ttu-id="0e162-131">描述</span><span class="sxs-lookup"><span data-stu-id="0e162-131">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="0e162-132">一般</span><span class="sxs-lookup"><span data-stu-id="0e162-132">Normal</span></span>|<span data-ttu-id="0e162-133">CommonStates</span><span class="sxs-lookup"><span data-stu-id="0e162-133">CommonStates</span></span>|<span data-ttu-id="0e162-134">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="0e162-134">The default state.</span></span>|  
|<span data-ttu-id="0e162-135">已停用</span><span class="sxs-lookup"><span data-stu-id="0e162-135">Disabled</span></span>|<span data-ttu-id="0e162-136">CommonStates</span><span class="sxs-lookup"><span data-stu-id="0e162-136">CommonStates</span></span>|<span data-ttu-id="0e162-137">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="0e162-137">The control is disabled.</span></span>|  
|<span data-ttu-id="0e162-138">MouseOver</span><span class="sxs-lookup"><span data-stu-id="0e162-138">MouseOver</span></span>|<span data-ttu-id="0e162-139">CommonStates</span><span class="sxs-lookup"><span data-stu-id="0e162-139">CommonStates</span></span>|<span data-ttu-id="0e162-140">滑鼠指標位於<xref:System.Windows.Controls.ComboBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="0e162-140">The mouse pointer is over the <xref:System.Windows.Controls.ComboBox> control.</span></span>|  
|<span data-ttu-id="0e162-141">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="0e162-141">Focused</span></span>|<span data-ttu-id="0e162-142">FocusStates</span><span class="sxs-lookup"><span data-stu-id="0e162-142">FocusStates</span></span>|<span data-ttu-id="0e162-143">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="0e162-143">The control has focus.</span></span>|  
|<span data-ttu-id="0e162-144">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="0e162-144">Unfocused</span></span>|<span data-ttu-id="0e162-145">FocusStates</span><span class="sxs-lookup"><span data-stu-id="0e162-145">FocusStates</span></span>|<span data-ttu-id="0e162-146">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="0e162-146">The control does not have focus.</span></span>|  
|<span data-ttu-id="0e162-147">已選取</span><span class="sxs-lookup"><span data-stu-id="0e162-147">Selected</span></span>|<span data-ttu-id="0e162-148">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="0e162-148">SelectionStates</span></span>|<span data-ttu-id="0e162-149">目前選取項目。</span><span class="sxs-lookup"><span data-stu-id="0e162-149">The item is currently selected.</span></span>|  
|<span data-ttu-id="0e162-150">未選取</span><span class="sxs-lookup"><span data-stu-id="0e162-150">Unselected</span></span>|<span data-ttu-id="0e162-151">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="0e162-151">SelectionStates</span></span>|<span data-ttu-id="0e162-152">項目未獲選取。</span><span class="sxs-lookup"><span data-stu-id="0e162-152">The item is not selected.</span></span>|  
|<span data-ttu-id="0e162-153">SelectedUnfocused</span><span class="sxs-lookup"><span data-stu-id="0e162-153">SelectedUnfocused</span></span>|<span data-ttu-id="0e162-154">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="0e162-154">SelectionStates</span></span>|<span data-ttu-id="0e162-155">項目已獲選取，但未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="0e162-155">The item is selected, but does not have focus.</span></span>|  
|<span data-ttu-id="0e162-156">驗證</span><span class="sxs-lookup"><span data-stu-id="0e162-156">Valid</span></span>|<span data-ttu-id="0e162-157">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0e162-157">ValidationStates</span></span>|<span data-ttu-id="0e162-158">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="0e162-158">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="0e162-159">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="0e162-159">InvalidFocused</span></span>|<span data-ttu-id="0e162-160">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0e162-160">ValidationStates</span></span>|<span data-ttu-id="0e162-161"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="0e162-161">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="0e162-162">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="0e162-162">InvalidUnfocused</span></span>|<span data-ttu-id="0e162-163">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0e162-163">ValidationStates</span></span>|<span data-ttu-id="0e162-164"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="0e162-164">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="listview-controltemplate-examples"></a><span data-ttu-id="0e162-165">ListView ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="0e162-165">ListView ControlTemplate Examples</span></span>  
 <span data-ttu-id="0e162-166">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.ListView>控制項和其相關聯的類型。</span><span class="sxs-lookup"><span data-stu-id="0e162-166">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ListView> control and its associated types.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ListView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listview.xaml#listview)]  
  
 <span data-ttu-id="0e162-167"><xref:System.Windows.Controls.ControlTemplate>範例會使用一或多個下列資源。</span><span class="sxs-lookup"><span data-stu-id="0e162-167">The <xref:System.Windows.Controls.ControlTemplate> examples use one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="0e162-168">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041)。</span><span class="sxs-lookup"><span data-stu-id="0e162-168">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e162-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e162-169">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="0e162-170">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="0e162-170">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="0e162-171">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="0e162-171">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="0e162-172">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="0e162-172">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="0e162-173">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="0e162-173">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
