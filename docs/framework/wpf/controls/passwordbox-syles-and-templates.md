---
title: PasswordBox 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], PasswordBox
- templates [WPF], PasswordBox
- ControlTemplate [WPF], PasswordBox
- states [WPF], PasswordBox
- PasswordBox [WPF], styles and templates
- parts [WPF], PasswordBox
ms.assetid: deb52107-959f-4a60-b303-d21a0a933060
ms.openlocfilehash: 464e2ff88b6e311470f6afe107d770922d9a395d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689230"
---
# <a name="passwordbox-syles-and-templates"></a><span data-ttu-id="070be-102">PasswordBox 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="070be-102">PasswordBox Syles and Templates</span></span>
<span data-ttu-id="070be-103">本主題描述的樣式和範本<xref:System.Windows.Controls.PasswordBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="070be-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.PasswordBox> control.</span></span> <span data-ttu-id="070be-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>，讓控制項的獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="070be-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="070be-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="070be-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="passwordbox-parts"></a><span data-ttu-id="070be-106">PasswordBox 組件</span><span class="sxs-lookup"><span data-stu-id="070be-106">PasswordBox Parts</span></span>  
 <span data-ttu-id="070be-107">下表列出的具名組件<xref:System.Windows.Controls.PasswordBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="070be-107">The following table lists the named parts for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
|<span data-ttu-id="070be-108">組件</span><span class="sxs-lookup"><span data-stu-id="070be-108">Part</span></span>|<span data-ttu-id="070be-109">類型</span><span class="sxs-lookup"><span data-stu-id="070be-109">Type</span></span>|<span data-ttu-id="070be-110">描述</span><span class="sxs-lookup"><span data-stu-id="070be-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="070be-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="070be-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="070be-112">可包含的視覺元素<xref:System.Windows.FrameworkElement>。</span><span class="sxs-lookup"><span data-stu-id="070be-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="070be-113">文字<xref:System.Windows.Controls.PasswordBox>會顯示此項目中。</span><span class="sxs-lookup"><span data-stu-id="070be-113">The text of the <xref:System.Windows.Controls.PasswordBox> is displayed in this element.</span></span>|  
  
## <a name="passwordbox-states"></a><span data-ttu-id="070be-114">PasswordBox 狀態</span><span class="sxs-lookup"><span data-stu-id="070be-114">PasswordBox States</span></span>  
 <span data-ttu-id="070be-115">下表列出的視覺狀態<xref:System.Windows.Controls.PasswordBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="070be-115">The following table lists the visual states for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
|<span data-ttu-id="070be-116">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="070be-116">VisualState Name</span></span>|<span data-ttu-id="070be-117">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="070be-117">VisualStateGroup Name</span></span>|<span data-ttu-id="070be-118">描述</span><span class="sxs-lookup"><span data-stu-id="070be-118">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="070be-119">一般</span><span class="sxs-lookup"><span data-stu-id="070be-119">Normal</span></span>|<span data-ttu-id="070be-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="070be-120">CommonStates</span></span>|<span data-ttu-id="070be-121">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="070be-121">The default state.</span></span>|  
|<span data-ttu-id="070be-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="070be-122">MouseOver</span></span>|<span data-ttu-id="070be-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="070be-123">CommonStates</span></span>|<span data-ttu-id="070be-124">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="070be-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="070be-125">已停用</span><span class="sxs-lookup"><span data-stu-id="070be-125">Disabled</span></span>|<span data-ttu-id="070be-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="070be-126">CommonStates</span></span>|<span data-ttu-id="070be-127">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="070be-127">The control is disabled.</span></span>|  
|<span data-ttu-id="070be-128">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="070be-128">Focused</span></span>|<span data-ttu-id="070be-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="070be-129">FocusStates</span></span>|<span data-ttu-id="070be-130">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="070be-130">The control has focus.</span></span>|  
|<span data-ttu-id="070be-131">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="070be-131">Unfocused</span></span>|<span data-ttu-id="070be-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="070be-132">FocusStates</span></span>|<span data-ttu-id="070be-133">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="070be-133">The control does not have focus.</span></span>|  
|<span data-ttu-id="070be-134">驗證</span><span class="sxs-lookup"><span data-stu-id="070be-134">Valid</span></span>|<span data-ttu-id="070be-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="070be-135">ValidationStates</span></span>|<span data-ttu-id="070be-136">控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。</span><span class="sxs-lookup"><span data-stu-id="070be-136">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="070be-137">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="070be-137">InvalidFocused</span></span>|<span data-ttu-id="070be-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="070be-138">ValidationStates</span></span>|<span data-ttu-id="070be-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。</span><span class="sxs-lookup"><span data-stu-id="070be-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="070be-140">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="070be-140">InvalidUnfocused</span></span>|<span data-ttu-id="070be-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="070be-141">ValidationStates</span></span>|<span data-ttu-id="070be-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="070be-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="passwordbox-controltemplate-example"></a><span data-ttu-id="070be-143">PasswordBox ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="070be-143">PasswordBox ControlTemplate Example</span></span>  
 <span data-ttu-id="070be-144">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.PasswordBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="070be-144">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#PasswordBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]  
  
 <span data-ttu-id="070be-145">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="070be-145">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="070be-146">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="070be-146">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="070be-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="070be-147">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="070be-148">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="070be-148">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [<span data-ttu-id="070be-149">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="070be-149">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)
- [<span data-ttu-id="070be-150">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="070be-150">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="070be-151">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="070be-151">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
