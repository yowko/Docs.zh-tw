---
title: TextBox 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TextBox
- parts [WPF], TextBox
- states [WPF], TextBox
- styles [WPF], TextBox
- templates [WPF], TextBox
- TextBox [WPF], styles and templates
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
ms.openlocfilehash: 41e390c261836909240cc146a48729d48c4a410e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283692"
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="5754c-102">TextBox 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="5754c-102">TextBox Styles and Templates</span></span>
<span data-ttu-id="5754c-103">本主題描述 <xref:System.Windows.Controls.TextBox> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="5754c-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="5754c-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="5754c-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="5754c-105">如需詳細資訊，請參閱[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。</span><span class="sxs-lookup"><span data-stu-id="5754c-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="5754c-106">TextBox 元件</span><span class="sxs-lookup"><span data-stu-id="5754c-106">TextBox Parts</span></span>  
 <span data-ttu-id="5754c-107">下表列出 <xref:System.Windows.Controls.TextBox> 控制項的已命名元件。</span><span class="sxs-lookup"><span data-stu-id="5754c-107">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="5754c-108">組件</span><span class="sxs-lookup"><span data-stu-id="5754c-108">Part</span></span>|<span data-ttu-id="5754c-109">輸入</span><span class="sxs-lookup"><span data-stu-id="5754c-109">Type</span></span>|<span data-ttu-id="5754c-110">描述</span><span class="sxs-lookup"><span data-stu-id="5754c-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="5754c-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="5754c-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="5754c-112">可以包含 <xref:System.Windows.FrameworkElement>的視覺元素。</span><span class="sxs-lookup"><span data-stu-id="5754c-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="5754c-113"><xref:System.Windows.Controls.TextBox> 的文字會顯示在此元素中。</span><span class="sxs-lookup"><span data-stu-id="5754c-113">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="5754c-114">文字方塊狀態</span><span class="sxs-lookup"><span data-stu-id="5754c-114">TextBox States</span></span>  
 <span data-ttu-id="5754c-115">下表列出 <xref:System.Windows.Controls.TextBox> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="5754c-115">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="5754c-116">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="5754c-116">VisualState Name</span></span>|<span data-ttu-id="5754c-117">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="5754c-117">VisualStateGroup Name</span></span>|<span data-ttu-id="5754c-118">描述</span><span class="sxs-lookup"><span data-stu-id="5754c-118">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="5754c-119">一般</span><span class="sxs-lookup"><span data-stu-id="5754c-119">Normal</span></span>|<span data-ttu-id="5754c-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="5754c-120">CommonStates</span></span>|<span data-ttu-id="5754c-121">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="5754c-121">The default state.</span></span>|  
|<span data-ttu-id="5754c-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="5754c-122">MouseOver</span></span>|<span data-ttu-id="5754c-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="5754c-123">CommonStates</span></span>|<span data-ttu-id="5754c-124">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="5754c-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="5754c-125">已停用</span><span class="sxs-lookup"><span data-stu-id="5754c-125">Disabled</span></span>|<span data-ttu-id="5754c-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="5754c-126">CommonStates</span></span>|<span data-ttu-id="5754c-127">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="5754c-127">The control is disabled.</span></span>|  
|<span data-ttu-id="5754c-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="5754c-128">ReadOnly</span></span>|<span data-ttu-id="5754c-129">CommonStates</span><span class="sxs-lookup"><span data-stu-id="5754c-129">CommonStates</span></span>|<span data-ttu-id="5754c-130">使用者無法變更 <xref:System.Windows.Controls.TextBox>中的文字。</span><span class="sxs-lookup"><span data-stu-id="5754c-130">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="5754c-131">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="5754c-131">Focused</span></span>|<span data-ttu-id="5754c-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="5754c-132">FocusStates</span></span>|<span data-ttu-id="5754c-133">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="5754c-133">The control has focus.</span></span>|  
|<span data-ttu-id="5754c-134">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="5754c-134">Unfocused</span></span>|<span data-ttu-id="5754c-135">FocusStates</span><span class="sxs-lookup"><span data-stu-id="5754c-135">FocusStates</span></span>|<span data-ttu-id="5754c-136">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="5754c-136">The control does not have focus.</span></span>|  
|<span data-ttu-id="5754c-137">驗證</span><span class="sxs-lookup"><span data-stu-id="5754c-137">Valid</span></span>|<span data-ttu-id="5754c-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5754c-138">ValidationStates</span></span>|<span data-ttu-id="5754c-139">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="5754c-139">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="5754c-140">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="5754c-140">InvalidFocused</span></span>|<span data-ttu-id="5754c-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5754c-141">ValidationStates</span></span>|<span data-ttu-id="5754c-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="5754c-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="5754c-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="5754c-143">InvalidUnfocused</span></span>|<span data-ttu-id="5754c-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5754c-144">ValidationStates</span></span>|<span data-ttu-id="5754c-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="5754c-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="5754c-146">TextBox ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="5754c-146">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="5754c-147">下列範例顯示如何定義 <xref:System.Windows.Controls.TextBox> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="5754c-147">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="5754c-148">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="5754c-148">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="5754c-149">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="5754c-149">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5754c-150">請參閱</span><span class="sxs-lookup"><span data-stu-id="5754c-150">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="5754c-151">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="5754c-151">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="5754c-152">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="5754c-152">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="5754c-153">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="5754c-153">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="5754c-154">建立控制項的範本</span><span class="sxs-lookup"><span data-stu-id="5754c-154">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
