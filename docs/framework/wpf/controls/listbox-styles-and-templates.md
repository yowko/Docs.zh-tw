---
title: ListBox 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], ListBox
- templates [WPF], ListBox
- states [WPF], ListBox
- ControlTemplate [WPF], ListBox
- parts [WPF], ListBox
- ListBox [WPF], styles and templates
ms.assetid: fc5764cb-c27b-495b-88d4-d969a8213ccb
ms.openlocfilehash: 441db59a6d04787985245db057074798bed6b3e8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157049"
---
# <a name="listbox-styles-and-templates"></a><span data-ttu-id="b143c-102">ListBox 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="b143c-102">ListBox Styles and Templates</span></span>
<span data-ttu-id="b143c-103">本主題描述的樣式和範本<xref:System.Windows.Controls.ListBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="b143c-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="b143c-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>，讓控制項的獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="b143c-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="b143c-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="b143c-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="listbox-parts"></a><span data-ttu-id="b143c-106">ListBox 組件</span><span class="sxs-lookup"><span data-stu-id="b143c-106">ListBox Parts</span></span>  
 <span data-ttu-id="b143c-107"><xref:System.Windows.Controls.ListBox>控制項沒有任何具名組件。</span><span class="sxs-lookup"><span data-stu-id="b143c-107">The <xref:System.Windows.Controls.ListBox> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="b143c-108">當您建立<xref:System.Windows.Controls.ControlTemplate>for <xref:System.Windows.Controls.ListBox>，您的範本可能會包含<xref:System.Windows.Controls.ItemsPresenter>內<xref:System.Windows.Controls.ScrollViewer>。</span><span class="sxs-lookup"><span data-stu-id="b143c-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ListBox>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="b143c-109">(<xref:System.Windows.Controls.ItemsPresenter>會顯示在每個項目<xref:System.Windows.Controls.ListBox>;<xref:System.Windows.Controls.ScrollViewer>可在控制項內捲動)。</span><span class="sxs-lookup"><span data-stu-id="b143c-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ListBox>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="b143c-110">如果<xref:System.Windows.Controls.ItemsPresenter>不是直接子系<xref:System.Windows.Controls.ScrollViewer>，您必須給予<xref:System.Windows.Controls.ItemsPresenter>名稱， `ItemsPresenter`。</span><span class="sxs-lookup"><span data-stu-id="b143c-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="listbox-states"></a><span data-ttu-id="b143c-111">ListBox 狀態</span><span class="sxs-lookup"><span data-stu-id="b143c-111">ListBox States</span></span>  
 <span data-ttu-id="b143c-112">下表列出的視覺狀態<xref:System.Windows.Controls.ListBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="b143c-112">The following table lists the visual states for the <xref:System.Windows.Controls.ListBox> control.</span></span>  
  
|<span data-ttu-id="b143c-113">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="b143c-113">VisualState Name</span></span>|<span data-ttu-id="b143c-114">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="b143c-114">VisualStateGroup Name</span></span>|<span data-ttu-id="b143c-115">描述</span><span class="sxs-lookup"><span data-stu-id="b143c-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="b143c-116">驗證</span><span class="sxs-lookup"><span data-stu-id="b143c-116">Valid</span></span>|<span data-ttu-id="b143c-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b143c-117">ValidationStates</span></span>|<span data-ttu-id="b143c-118">控制項有效。</span><span class="sxs-lookup"><span data-stu-id="b143c-118">The control is valid.</span></span>|  
|<span data-ttu-id="b143c-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="b143c-119">InvalidFocused</span></span>|<span data-ttu-id="b143c-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b143c-120">ValidationStates</span></span>|<span data-ttu-id="b143c-121">控制項無效且已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="b143c-121">The control is not valid and has focus.</span></span>|  
|<span data-ttu-id="b143c-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="b143c-122">InvalidUnfocused</span></span>|<span data-ttu-id="b143c-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b143c-123">ValidationStates</span></span>|<span data-ttu-id="b143c-124">控制項無效且未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="b143c-124">The control is not valid and does not have focus.</span></span>|  
  
## <a name="listboxitem-parts"></a><span data-ttu-id="b143c-125">ListBoxItem 組件</span><span class="sxs-lookup"><span data-stu-id="b143c-125">ListBoxItem Parts</span></span>  
 <span data-ttu-id="b143c-126"><xref:System.Windows.Controls.ListBoxItem>控制項沒有任何具名組件。</span><span class="sxs-lookup"><span data-stu-id="b143c-126">The <xref:System.Windows.Controls.ListBoxItem> control does not have any named parts.</span></span>  
  
## <a name="listboxitem-states"></a><span data-ttu-id="b143c-127">ListBoxItem 狀態</span><span class="sxs-lookup"><span data-stu-id="b143c-127">ListBoxItem States</span></span>  
 <span data-ttu-id="b143c-128">下表列出的視覺狀態<xref:System.Windows.Controls.ListBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="b143c-128">The following table lists the visual states for the <xref:System.Windows.Controls.ListBox> control.</span></span>  
  
|<span data-ttu-id="b143c-129">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="b143c-129">VisualState Name</span></span>|<span data-ttu-id="b143c-130">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="b143c-130">VisualStateGroup Name</span></span>|<span data-ttu-id="b143c-131">描述</span><span class="sxs-lookup"><span data-stu-id="b143c-131">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="b143c-132">一般</span><span class="sxs-lookup"><span data-stu-id="b143c-132">Normal</span></span>|<span data-ttu-id="b143c-133">CommonStates</span><span class="sxs-lookup"><span data-stu-id="b143c-133">CommonStates</span></span>|<span data-ttu-id="b143c-134">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="b143c-134">The default state.</span></span>|  
|<span data-ttu-id="b143c-135">MouseOver</span><span class="sxs-lookup"><span data-stu-id="b143c-135">MouseOver</span></span>|<span data-ttu-id="b143c-136">CommonStates</span><span class="sxs-lookup"><span data-stu-id="b143c-136">CommonStates</span></span>|<span data-ttu-id="b143c-137">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="b143c-137">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="b143c-138">已停用</span><span class="sxs-lookup"><span data-stu-id="b143c-138">Disabled</span></span>|<span data-ttu-id="b143c-139">CommonStates</span><span class="sxs-lookup"><span data-stu-id="b143c-139">CommonStates</span></span>|<span data-ttu-id="b143c-140">項目已停用。</span><span class="sxs-lookup"><span data-stu-id="b143c-140">The item is disabled.</span></span>|  
|<span data-ttu-id="b143c-141">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="b143c-141">Focused</span></span>|<span data-ttu-id="b143c-142">FocusStates</span><span class="sxs-lookup"><span data-stu-id="b143c-142">FocusStates</span></span>|<span data-ttu-id="b143c-143">項目已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="b143c-143">The item has focus.</span></span>|  
|<span data-ttu-id="b143c-144">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="b143c-144">Unfocused</span></span>|<span data-ttu-id="b143c-145">FocusStates</span><span class="sxs-lookup"><span data-stu-id="b143c-145">FocusStates</span></span>|<span data-ttu-id="b143c-146">項目未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="b143c-146">The item does not have focus.</span></span>|  
|<span data-ttu-id="b143c-147">未選取</span><span class="sxs-lookup"><span data-stu-id="b143c-147">Unselected</span></span>|<span data-ttu-id="b143c-148">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="b143c-148">SelectionStates</span></span>|<span data-ttu-id="b143c-149">項目未獲選取。</span><span class="sxs-lookup"><span data-stu-id="b143c-149">The item is not selected.</span></span>|  
|<span data-ttu-id="b143c-150">已選取</span><span class="sxs-lookup"><span data-stu-id="b143c-150">Selected</span></span>|<span data-ttu-id="b143c-151">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="b143c-151">SelectionStates</span></span>|<span data-ttu-id="b143c-152">項目目前已獲選取。</span><span class="sxs-lookup"><span data-stu-id="b143c-152">The item is currentlyplate selected.</span></span>|  
|<span data-ttu-id="b143c-153">SelectedUnfocused</span><span class="sxs-lookup"><span data-stu-id="b143c-153">SelectedUnfocused</span></span>|<span data-ttu-id="b143c-154">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="b143c-154">SelectionStates</span></span>|<span data-ttu-id="b143c-155">項目已獲選取，但未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="b143c-155">The item is selected, but does not have focus.</span></span>|  
|<span data-ttu-id="b143c-156">驗證</span><span class="sxs-lookup"><span data-stu-id="b143c-156">Valid</span></span>|<span data-ttu-id="b143c-157">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b143c-157">ValidationStates</span></span>|<span data-ttu-id="b143c-158">控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。</span><span class="sxs-lookup"><span data-stu-id="b143c-158">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="b143c-159">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="b143c-159">InvalidFocused</span></span>|<span data-ttu-id="b143c-160">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b143c-160">ValidationStates</span></span>|<span data-ttu-id="b143c-161"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。</span><span class="sxs-lookup"><span data-stu-id="b143c-161">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="b143c-162">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="b143c-162">InvalidUnfocused</span></span>|<span data-ttu-id="b143c-163">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b143c-163">ValidationStates</span></span>|<span data-ttu-id="b143c-164"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="b143c-164">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="listbox-controltemplate-example"></a><span data-ttu-id="b143c-165">ListBox ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="b143c-165">ListBox ControlTemplate Example</span></span>  
 <span data-ttu-id="b143c-166">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>for<xref:System.Windows.Controls.ListBox>和<xref:System.Windows.Controls.ListBoxItem>控制項。</span><span class="sxs-lookup"><span data-stu-id="b143c-166">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ListBox> and <xref:System.Windows.Controls.ListBoxItem> controls.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ListBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listbox.xaml#listbox)]  
  
 <span data-ttu-id="b143c-167">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="b143c-167">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="b143c-168">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="b143c-168">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b143c-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b143c-169">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="b143c-170">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="b143c-170">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="b143c-171">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="b143c-171">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="b143c-172">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="b143c-172">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="b143c-173">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="b143c-173">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
