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
ms.openlocfilehash: 4ba90182468466773644c7375059f0cc01675b33
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283469"
---
# <a name="passwordbox-styles-and-templates"></a><span data-ttu-id="e8594-102">PasswordBox 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="e8594-102">PasswordBox Styles and Templates</span></span>

<span data-ttu-id="e8594-103">本主題描述 <xref:System.Windows.Controls.PasswordBox> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="e8594-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.PasswordBox> control.</span></span> <span data-ttu-id="e8594-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="e8594-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="e8594-105">如需詳細資訊，請參閱[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。</span><span class="sxs-lookup"><span data-stu-id="e8594-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>

## <a name="passwordbox-parts"></a><span data-ttu-id="e8594-106">PasswordBox 元件</span><span class="sxs-lookup"><span data-stu-id="e8594-106">PasswordBox Parts</span></span>

<span data-ttu-id="e8594-107">下表列出 <xref:System.Windows.Controls.PasswordBox> 控制項的已命名元件。</span><span class="sxs-lookup"><span data-stu-id="e8594-107">The following table lists the named parts for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

|<span data-ttu-id="e8594-108">組件</span><span class="sxs-lookup"><span data-stu-id="e8594-108">Part</span></span>|<span data-ttu-id="e8594-109">輸入</span><span class="sxs-lookup"><span data-stu-id="e8594-109">Type</span></span>|<span data-ttu-id="e8594-110">描述</span><span class="sxs-lookup"><span data-stu-id="e8594-110">Description</span></span>|
|-|-|-|
|<span data-ttu-id="e8594-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="e8594-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="e8594-112">可以包含 <xref:System.Windows.FrameworkElement>的視覺元素。</span><span class="sxs-lookup"><span data-stu-id="e8594-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="e8594-113"><xref:System.Windows.Controls.PasswordBox> 的文字會顯示在此元素中。</span><span class="sxs-lookup"><span data-stu-id="e8594-113">The text of the <xref:System.Windows.Controls.PasswordBox> is displayed in this element.</span></span>|

## <a name="passwordbox-states"></a><span data-ttu-id="e8594-114">PasswordBox 狀態</span><span class="sxs-lookup"><span data-stu-id="e8594-114">PasswordBox States</span></span>

<span data-ttu-id="e8594-115">下表列出 <xref:System.Windows.Controls.PasswordBox> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="e8594-115">The following table lists the visual states for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

|<span data-ttu-id="e8594-116">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="e8594-116">VisualState Name</span></span>|<span data-ttu-id="e8594-117">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="e8594-117">VisualStateGroup Name</span></span>|<span data-ttu-id="e8594-118">描述</span><span class="sxs-lookup"><span data-stu-id="e8594-118">Description</span></span>|
|-|-|-|
|<span data-ttu-id="e8594-119">一般</span><span class="sxs-lookup"><span data-stu-id="e8594-119">Normal</span></span>|<span data-ttu-id="e8594-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e8594-120">CommonStates</span></span>|<span data-ttu-id="e8594-121">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="e8594-121">The default state.</span></span>|
|<span data-ttu-id="e8594-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="e8594-122">MouseOver</span></span>|<span data-ttu-id="e8594-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e8594-123">CommonStates</span></span>|<span data-ttu-id="e8594-124">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="e8594-124">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="e8594-125">已停用</span><span class="sxs-lookup"><span data-stu-id="e8594-125">Disabled</span></span>|<span data-ttu-id="e8594-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e8594-126">CommonStates</span></span>|<span data-ttu-id="e8594-127">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="e8594-127">The control is disabled.</span></span>|
|<span data-ttu-id="e8594-128">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="e8594-128">Focused</span></span>|<span data-ttu-id="e8594-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="e8594-129">FocusStates</span></span>|<span data-ttu-id="e8594-130">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="e8594-130">The control has focus.</span></span>|
|<span data-ttu-id="e8594-131">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="e8594-131">Unfocused</span></span>|<span data-ttu-id="e8594-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="e8594-132">FocusStates</span></span>|<span data-ttu-id="e8594-133">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="e8594-133">The control does not have focus.</span></span>|
|<span data-ttu-id="e8594-134">驗證</span><span class="sxs-lookup"><span data-stu-id="e8594-134">Valid</span></span>|<span data-ttu-id="e8594-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e8594-135">ValidationStates</span></span>|<span data-ttu-id="e8594-136">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="e8594-136">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="e8594-137">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="e8594-137">InvalidFocused</span></span>|<span data-ttu-id="e8594-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e8594-138">ValidationStates</span></span>|<span data-ttu-id="e8594-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="e8594-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="e8594-140">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="e8594-140">InvalidUnfocused</span></span>|<span data-ttu-id="e8594-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e8594-141">ValidationStates</span></span>|<span data-ttu-id="e8594-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="e8594-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="passwordbox-controltemplate-example"></a><span data-ttu-id="e8594-143">PasswordBox ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="e8594-143">PasswordBox ControlTemplate Example</span></span>

<span data-ttu-id="e8594-144">下列範例顯示如何定義 <xref:System.Windows.Controls.PasswordBox> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="e8594-144">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

[!code-xaml[ControlTemplateExamples#PasswordBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]

<span data-ttu-id="e8594-145">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="e8594-145">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="e8594-146">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="e8594-146">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="e8594-147">請參閱</span><span class="sxs-lookup"><span data-stu-id="e8594-147">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="e8594-148">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="e8594-148">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="e8594-149">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="e8594-149">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="e8594-150">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="e8594-150">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="e8594-151">建立控制項的範本</span><span class="sxs-lookup"><span data-stu-id="e8594-151">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
