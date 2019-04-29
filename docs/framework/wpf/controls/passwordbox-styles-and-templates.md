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
ms.openlocfilehash: 7783330dd56ec5b2759e783a6935761eb3587978
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770639"
---
# <a name="passwordbox-styles-and-templates"></a><span data-ttu-id="8144b-102">PasswordBox 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="8144b-102">PasswordBox Styles and Templates</span></span>

<span data-ttu-id="8144b-103">本主題描述的樣式和範本<xref:System.Windows.Controls.PasswordBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="8144b-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.PasswordBox> control.</span></span> <span data-ttu-id="8144b-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>，讓控制項的獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="8144b-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="8144b-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="8144b-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>

## <a name="passwordbox-parts"></a><span data-ttu-id="8144b-106">PasswordBox 組件</span><span class="sxs-lookup"><span data-stu-id="8144b-106">PasswordBox Parts</span></span>

<span data-ttu-id="8144b-107">下表列出的具名組件<xref:System.Windows.Controls.PasswordBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="8144b-107">The following table lists the named parts for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

|<span data-ttu-id="8144b-108">組件</span><span class="sxs-lookup"><span data-stu-id="8144b-108">Part</span></span>|<span data-ttu-id="8144b-109">類型</span><span class="sxs-lookup"><span data-stu-id="8144b-109">Type</span></span>|<span data-ttu-id="8144b-110">描述</span><span class="sxs-lookup"><span data-stu-id="8144b-110">Description</span></span>|
|-|-|-|
|<span data-ttu-id="8144b-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="8144b-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="8144b-112">可包含的視覺元素<xref:System.Windows.FrameworkElement>。</span><span class="sxs-lookup"><span data-stu-id="8144b-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="8144b-113">文字<xref:System.Windows.Controls.PasswordBox>會顯示此項目中。</span><span class="sxs-lookup"><span data-stu-id="8144b-113">The text of the <xref:System.Windows.Controls.PasswordBox> is displayed in this element.</span></span>|

## <a name="passwordbox-states"></a><span data-ttu-id="8144b-114">PasswordBox 狀態</span><span class="sxs-lookup"><span data-stu-id="8144b-114">PasswordBox States</span></span>

<span data-ttu-id="8144b-115">下表列出的視覺狀態<xref:System.Windows.Controls.PasswordBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="8144b-115">The following table lists the visual states for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

|<span data-ttu-id="8144b-116">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="8144b-116">VisualState Name</span></span>|<span data-ttu-id="8144b-117">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="8144b-117">VisualStateGroup Name</span></span>|<span data-ttu-id="8144b-118">描述</span><span class="sxs-lookup"><span data-stu-id="8144b-118">Description</span></span>|
|-|-|-|
|<span data-ttu-id="8144b-119">一般</span><span class="sxs-lookup"><span data-stu-id="8144b-119">Normal</span></span>|<span data-ttu-id="8144b-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="8144b-120">CommonStates</span></span>|<span data-ttu-id="8144b-121">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="8144b-121">The default state.</span></span>|
|<span data-ttu-id="8144b-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="8144b-122">MouseOver</span></span>|<span data-ttu-id="8144b-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="8144b-123">CommonStates</span></span>|<span data-ttu-id="8144b-124">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="8144b-124">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="8144b-125">已停用</span><span class="sxs-lookup"><span data-stu-id="8144b-125">Disabled</span></span>|<span data-ttu-id="8144b-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="8144b-126">CommonStates</span></span>|<span data-ttu-id="8144b-127">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="8144b-127">The control is disabled.</span></span>|
|<span data-ttu-id="8144b-128">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="8144b-128">Focused</span></span>|<span data-ttu-id="8144b-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="8144b-129">FocusStates</span></span>|<span data-ttu-id="8144b-130">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="8144b-130">The control has focus.</span></span>|
|<span data-ttu-id="8144b-131">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="8144b-131">Unfocused</span></span>|<span data-ttu-id="8144b-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="8144b-132">FocusStates</span></span>|<span data-ttu-id="8144b-133">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="8144b-133">The control does not have focus.</span></span>|
|<span data-ttu-id="8144b-134">驗證</span><span class="sxs-lookup"><span data-stu-id="8144b-134">Valid</span></span>|<span data-ttu-id="8144b-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8144b-135">ValidationStates</span></span>|<span data-ttu-id="8144b-136">控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。</span><span class="sxs-lookup"><span data-stu-id="8144b-136">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="8144b-137">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="8144b-137">InvalidFocused</span></span>|<span data-ttu-id="8144b-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8144b-138">ValidationStates</span></span>|<span data-ttu-id="8144b-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。</span><span class="sxs-lookup"><span data-stu-id="8144b-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="8144b-140">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="8144b-140">InvalidUnfocused</span></span>|<span data-ttu-id="8144b-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8144b-141">ValidationStates</span></span>|<span data-ttu-id="8144b-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="8144b-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="passwordbox-controltemplate-example"></a><span data-ttu-id="8144b-143">PasswordBox ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="8144b-143">PasswordBox ControlTemplate Example</span></span>

<span data-ttu-id="8144b-144">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.PasswordBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="8144b-144">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

[!code-xaml[ControlTemplateExamples#PasswordBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]

<span data-ttu-id="8144b-145">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="8144b-145">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="8144b-146">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="8144b-146">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="8144b-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8144b-147">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="8144b-148">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="8144b-148">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="8144b-149">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="8144b-149">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="8144b-150">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="8144b-150">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="8144b-151">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="8144b-151">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
