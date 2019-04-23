---
title: Button 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Button
- parts [WPF], Button
- styles [WPF], Button
- Button [WPF], styles and templates
- templates [WPF], Button
- ControlTemplate [WPF], Button
ms.assetid: e223c759-f8c4-4717-acfb-b1e40bdf5f3b
ms.openlocfilehash: ec64c7c2051b12cba01135054a90e54864b7386a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116333"
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="7f795-102">Button 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="7f795-102">Button Styles and Templates</span></span>
<span data-ttu-id="7f795-103">本主題描述的樣式和範本<xref:System.Windows.Controls.Button>控制項。</span><span class="sxs-lookup"><span data-stu-id="7f795-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="7f795-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>，讓控制項的獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="7f795-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="7f795-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="7f795-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="7f795-106">按鈕組件</span><span class="sxs-lookup"><span data-stu-id="7f795-106">Button Parts</span></span>  
 <span data-ttu-id="7f795-107"><xref:System.Windows.Controls.Button>控制項沒有任何具名組件。</span><span class="sxs-lookup"><span data-stu-id="7f795-107">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="7f795-108">按鈕狀態</span><span class="sxs-lookup"><span data-stu-id="7f795-108">Button States</span></span>  
 <span data-ttu-id="7f795-109">下表列出的視覺狀態<xref:System.Windows.Controls.Button>控制項。</span><span class="sxs-lookup"><span data-stu-id="7f795-109">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="7f795-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="7f795-110">VisualState Name</span></span>|<span data-ttu-id="7f795-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="7f795-111">VisualStateGroup Name</span></span>|<span data-ttu-id="7f795-112">描述</span><span class="sxs-lookup"><span data-stu-id="7f795-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="7f795-113">一般</span><span class="sxs-lookup"><span data-stu-id="7f795-113">Normal</span></span>|<span data-ttu-id="7f795-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7f795-114">CommonStates</span></span>|<span data-ttu-id="7f795-115">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="7f795-115">The default state.</span></span>|  
|<span data-ttu-id="7f795-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="7f795-116">MouseOver</span></span>|<span data-ttu-id="7f795-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7f795-117">CommonStates</span></span>|<span data-ttu-id="7f795-118">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="7f795-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="7f795-119">按下</span><span class="sxs-lookup"><span data-stu-id="7f795-119">Pressed</span></span>|<span data-ttu-id="7f795-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7f795-120">CommonStates</span></span>|<span data-ttu-id="7f795-121">已按下控制項。</span><span class="sxs-lookup"><span data-stu-id="7f795-121">The control is pressed.</span></span>|  
|<span data-ttu-id="7f795-122">已停用</span><span class="sxs-lookup"><span data-stu-id="7f795-122">Disabled</span></span>|<span data-ttu-id="7f795-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7f795-123">CommonStates</span></span>|<span data-ttu-id="7f795-124">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="7f795-124">The control is disabled.</span></span>|  
|<span data-ttu-id="7f795-125">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="7f795-125">Focused</span></span>|<span data-ttu-id="7f795-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="7f795-126">FocusStates</span></span>|<span data-ttu-id="7f795-127">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="7f795-127">The control has focus.</span></span>|  
|<span data-ttu-id="7f795-128">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="7f795-128">Unfocused</span></span>|<span data-ttu-id="7f795-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="7f795-129">FocusStates</span></span>|<span data-ttu-id="7f795-130">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="7f795-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="7f795-131">驗證</span><span class="sxs-lookup"><span data-stu-id="7f795-131">Valid</span></span>|<span data-ttu-id="7f795-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7f795-132">ValidationStates</span></span>|<span data-ttu-id="7f795-133">控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。</span><span class="sxs-lookup"><span data-stu-id="7f795-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="7f795-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="7f795-134">InvalidFocused</span></span>|<span data-ttu-id="7f795-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7f795-135">ValidationStates</span></span>|<span data-ttu-id="7f795-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`和控制項有焦點。</span><span class="sxs-lookup"><span data-stu-id="7f795-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="7f795-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="7f795-137">InvalidUnfocused</span></span>|<span data-ttu-id="7f795-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7f795-138">ValidationStates</span></span>|<span data-ttu-id="7f795-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`和控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="7f795-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="7f795-140">按鈕 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="7f795-140">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="7f795-141">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.Button>控制項。</span><span class="sxs-lookup"><span data-stu-id="7f795-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="7f795-142">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="7f795-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="7f795-143">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="7f795-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f795-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f795-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="7f795-145">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="7f795-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="7f795-146">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="7f795-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="7f795-147">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="7f795-147">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="7f795-148">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="7f795-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
