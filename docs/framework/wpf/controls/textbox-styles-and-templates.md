---
title: TextBox 樣式和範本
description: 瞭解 Windows Presentation Foundation TextBox 控制項的樣式和範本。 修改 ControlTemplate，讓控制項具有獨特的外觀。
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TextBox
- parts [WPF], TextBox
- states [WPF], TextBox
- styles [WPF], TextBox
- templates [WPF], TextBox
- TextBox [WPF], styles and templates
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
ms.openlocfilehash: 0e15fd40f5590ee46da49cc6c0d5fb30e051f7e4
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164730"
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="659c9-104">TextBox 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="659c9-104">TextBox Styles and Templates</span></span>
<span data-ttu-id="659c9-105">本主題描述控制項的樣式和範本 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="659c9-105">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="659c9-106">您可以修改預設值 <xref:System.Windows.Controls.ControlTemplate> ，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="659c9-106">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="659c9-107">如需詳細資訊，請參閱[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。</span><span class="sxs-lookup"><span data-stu-id="659c9-107">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="659c9-108">TextBox 元件</span><span class="sxs-lookup"><span data-stu-id="659c9-108">TextBox Parts</span></span>  
 <span data-ttu-id="659c9-109">下表列出控制項的已命名元件 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="659c9-109">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="659c9-110">部分</span><span class="sxs-lookup"><span data-stu-id="659c9-110">Part</span></span>|<span data-ttu-id="659c9-111">類型</span><span class="sxs-lookup"><span data-stu-id="659c9-111">Type</span></span>|<span data-ttu-id="659c9-112">描述</span><span class="sxs-lookup"><span data-stu-id="659c9-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="659c9-113">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="659c9-113">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="659c9-114">可以包含的視覺元素 <xref:System.Windows.FrameworkElement> 。</span><span class="sxs-lookup"><span data-stu-id="659c9-114">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="659c9-115">的文字 <xref:System.Windows.Controls.TextBox> 會顯示在此元素中。</span><span class="sxs-lookup"><span data-stu-id="659c9-115">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="659c9-116">文字方塊狀態</span><span class="sxs-lookup"><span data-stu-id="659c9-116">TextBox States</span></span>  
 <span data-ttu-id="659c9-117">下表列出控制項的視覺狀態 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="659c9-117">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="659c9-118">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="659c9-118">VisualState Name</span></span>|<span data-ttu-id="659c9-119">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="659c9-119">VisualStateGroup Name</span></span>|<span data-ttu-id="659c9-120">描述</span><span class="sxs-lookup"><span data-stu-id="659c9-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="659c9-121">正常</span><span class="sxs-lookup"><span data-stu-id="659c9-121">Normal</span></span>|<span data-ttu-id="659c9-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="659c9-122">CommonStates</span></span>|<span data-ttu-id="659c9-123">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="659c9-123">The default state.</span></span>|  
|<span data-ttu-id="659c9-124">MouseOver</span><span class="sxs-lookup"><span data-stu-id="659c9-124">MouseOver</span></span>|<span data-ttu-id="659c9-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="659c9-125">CommonStates</span></span>|<span data-ttu-id="659c9-126">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="659c9-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="659c9-127">已停用</span><span class="sxs-lookup"><span data-stu-id="659c9-127">Disabled</span></span>|<span data-ttu-id="659c9-128">CommonStates</span><span class="sxs-lookup"><span data-stu-id="659c9-128">CommonStates</span></span>|<span data-ttu-id="659c9-129">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="659c9-129">The control is disabled.</span></span>|  
|<span data-ttu-id="659c9-130">唯讀</span><span class="sxs-lookup"><span data-stu-id="659c9-130">ReadOnly</span></span>|<span data-ttu-id="659c9-131">CommonStates</span><span class="sxs-lookup"><span data-stu-id="659c9-131">CommonStates</span></span>|<span data-ttu-id="659c9-132">使用者無法變更中的文字 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="659c9-132">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="659c9-133">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="659c9-133">Focused</span></span>|<span data-ttu-id="659c9-134">FocusStates</span><span class="sxs-lookup"><span data-stu-id="659c9-134">FocusStates</span></span>|<span data-ttu-id="659c9-135">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="659c9-135">The control has focus.</span></span>|  
|<span data-ttu-id="659c9-136">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="659c9-136">Unfocused</span></span>|<span data-ttu-id="659c9-137">FocusStates</span><span class="sxs-lookup"><span data-stu-id="659c9-137">FocusStates</span></span>|<span data-ttu-id="659c9-138">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="659c9-138">The control does not have focus.</span></span>|  
|<span data-ttu-id="659c9-139">有效</span><span class="sxs-lookup"><span data-stu-id="659c9-139">Valid</span></span>|<span data-ttu-id="659c9-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="659c9-140">ValidationStates</span></span>|<span data-ttu-id="659c9-141">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `false` 。</span><span class="sxs-lookup"><span data-stu-id="659c9-141">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="659c9-142">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="659c9-142">InvalidFocused</span></span>|<span data-ttu-id="659c9-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="659c9-143">ValidationStates</span></span>|<span data-ttu-id="659c9-144"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性的 `true` 焦點是控制項。</span><span class="sxs-lookup"><span data-stu-id="659c9-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="659c9-145">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="659c9-145">InvalidUnfocused</span></span>|<span data-ttu-id="659c9-146">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="659c9-146">ValidationStates</span></span>|<span data-ttu-id="659c9-147"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="659c9-147">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="659c9-148">TextBox ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="659c9-148">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="659c9-149">下列範例顯示如何定義 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.TextBox> 控制項的。</span><span class="sxs-lookup"><span data-stu-id="659c9-149">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="659c9-150">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="659c9-150">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="659c9-151">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="659c9-151">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="659c9-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="659c9-152">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="659c9-153">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="659c9-153">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="659c9-154">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="659c9-154">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="659c9-155">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="659c9-155">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="659c9-156">建立控制項的範本</span><span class="sxs-lookup"><span data-stu-id="659c9-156">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
