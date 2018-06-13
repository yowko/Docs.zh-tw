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
ms.openlocfilehash: b18aa6798c2d7c66eaca6cb98b55e9050868f258
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457836"
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="3fa3e-102">TextBox 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="3fa3e-102">TextBox Styles and Templates</span></span>
<span data-ttu-id="3fa3e-103">本主題描述樣式和範本<xref:System.Windows.Controls.TextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="3fa3e-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="3fa3e-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="3fa3e-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="3fa3e-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="3fa3e-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="3fa3e-106">文字方塊中的組件</span><span class="sxs-lookup"><span data-stu-id="3fa3e-106">TextBox Parts</span></span>  
 <span data-ttu-id="3fa3e-107">下表列出的具名組件<xref:System.Windows.Controls.TextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="3fa3e-107">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="3fa3e-108">組件</span><span class="sxs-lookup"><span data-stu-id="3fa3e-108">Part</span></span>|<span data-ttu-id="3fa3e-109">類型</span><span class="sxs-lookup"><span data-stu-id="3fa3e-109">Type</span></span>|<span data-ttu-id="3fa3e-110">描述</span><span class="sxs-lookup"><span data-stu-id="3fa3e-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="3fa3e-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="3fa3e-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="3fa3e-112">可以包含視覺項目<xref:System.Windows.FrameworkElement>。</span><span class="sxs-lookup"><span data-stu-id="3fa3e-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="3fa3e-113">文字<xref:System.Windows.Controls.TextBox>會顯示在這個項目。</span><span class="sxs-lookup"><span data-stu-id="3fa3e-113">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="3fa3e-114">文字方塊中的狀態</span><span class="sxs-lookup"><span data-stu-id="3fa3e-114">TextBox States</span></span>  
 <span data-ttu-id="3fa3e-115">下表列出的視覺狀態<xref:System.Windows.Controls.TextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="3fa3e-115">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="3fa3e-116">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="3fa3e-116">VisualState Name</span></span>|<span data-ttu-id="3fa3e-117">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="3fa3e-117">VisualStateGroup Name</span></span>|<span data-ttu-id="3fa3e-118">描述</span><span class="sxs-lookup"><span data-stu-id="3fa3e-118">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="3fa3e-119">一般</span><span class="sxs-lookup"><span data-stu-id="3fa3e-119">Normal</span></span>|<span data-ttu-id="3fa3e-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="3fa3e-120">CommonStates</span></span>|<span data-ttu-id="3fa3e-121">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="3fa3e-121">The default state.</span></span>|  
|<span data-ttu-id="3fa3e-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="3fa3e-122">MouseOver</span></span>|<span data-ttu-id="3fa3e-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="3fa3e-123">CommonStates</span></span>|<span data-ttu-id="3fa3e-124">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="3fa3e-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="3fa3e-125">已停用</span><span class="sxs-lookup"><span data-stu-id="3fa3e-125">Disabled</span></span>|<span data-ttu-id="3fa3e-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="3fa3e-126">CommonStates</span></span>|<span data-ttu-id="3fa3e-127">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="3fa3e-127">The control is disabled.</span></span>|  
|<span data-ttu-id="3fa3e-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="3fa3e-128">ReadOnly</span></span>|<span data-ttu-id="3fa3e-129">CommonStates</span><span class="sxs-lookup"><span data-stu-id="3fa3e-129">CommonStates</span></span>|<span data-ttu-id="3fa3e-130">使用者無法變更中的文字<xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="3fa3e-130">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="3fa3e-131">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="3fa3e-131">Focused</span></span>|<span data-ttu-id="3fa3e-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="3fa3e-132">FocusStates</span></span>|<span data-ttu-id="3fa3e-133">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="3fa3e-133">The control has focus.</span></span>|  
|<span data-ttu-id="3fa3e-134">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="3fa3e-134">Unfocused</span></span>|<span data-ttu-id="3fa3e-135">FocusStates</span><span class="sxs-lookup"><span data-stu-id="3fa3e-135">FocusStates</span></span>|<span data-ttu-id="3fa3e-136">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="3fa3e-136">The control does not have focus.</span></span>|  
|<span data-ttu-id="3fa3e-137">驗證</span><span class="sxs-lookup"><span data-stu-id="3fa3e-137">Valid</span></span>|<span data-ttu-id="3fa3e-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3fa3e-138">ValidationStates</span></span>|<span data-ttu-id="3fa3e-139">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="3fa3e-139">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="3fa3e-140">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="3fa3e-140">InvalidFocused</span></span>|<span data-ttu-id="3fa3e-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3fa3e-141">ValidationStates</span></span>|<span data-ttu-id="3fa3e-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="3fa3e-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="3fa3e-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="3fa3e-143">InvalidUnfocused</span></span>|<span data-ttu-id="3fa3e-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3fa3e-144">ValidationStates</span></span>|<span data-ttu-id="3fa3e-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="3fa3e-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="3fa3e-146">文字方塊 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="3fa3e-146">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="3fa3e-147">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.TextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="3fa3e-147">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="3fa3e-148">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="3fa3e-148">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="3fa3e-149">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="3fa3e-149">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fa3e-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fa3e-150">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="3fa3e-151">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="3fa3e-151">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="3fa3e-152">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="3fa3e-152">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="3fa3e-153">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="3fa3e-153">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="3fa3e-154">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="3fa3e-154">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
