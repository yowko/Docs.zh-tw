---
title: "TextBox 樣式和範本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], TextBox
- parts [WPF], TextBox
- states [WPF], TextBox
- styles [WPF], TextBox
- templates [WPF], TextBox
- TextBox [WPF], styles and templates
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7f5cfd1c0715c7f9610f85201cd40a3973a2be64
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="cd692-102">TextBox 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="cd692-102">TextBox Styles and Templates</span></span>
<span data-ttu-id="cd692-103">本主題描述樣式和範本<xref:System.Windows.Controls.TextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="cd692-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="cd692-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="cd692-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="cd692-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="cd692-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="cd692-106">文字方塊中的組件</span><span class="sxs-lookup"><span data-stu-id="cd692-106">TextBox Parts</span></span>  
 <span data-ttu-id="cd692-107">下表列出的具名組件<xref:System.Windows.Controls.TextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="cd692-107">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="cd692-108">組件</span><span class="sxs-lookup"><span data-stu-id="cd692-108">Part</span></span>|<span data-ttu-id="cd692-109">類型</span><span class="sxs-lookup"><span data-stu-id="cd692-109">Type</span></span>|<span data-ttu-id="cd692-110">說明</span><span class="sxs-lookup"><span data-stu-id="cd692-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="cd692-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="cd692-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="cd692-112">可以包含視覺項目<xref:System.Windows.FrameworkElement>。</span><span class="sxs-lookup"><span data-stu-id="cd692-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="cd692-113">文字<xref:System.Windows.Controls.TextBox>會顯示在這個項目。</span><span class="sxs-lookup"><span data-stu-id="cd692-113">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="cd692-114">文字方塊中的狀態</span><span class="sxs-lookup"><span data-stu-id="cd692-114">TextBox States</span></span>  
 <span data-ttu-id="cd692-115">下表列出的視覺狀態<xref:System.Windows.Controls.TextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="cd692-115">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="cd692-116">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="cd692-116">VisualState Name</span></span>|<span data-ttu-id="cd692-117">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="cd692-117">VisualStateGroup Name</span></span>|<span data-ttu-id="cd692-118">描述</span><span class="sxs-lookup"><span data-stu-id="cd692-118">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="cd692-119">一般</span><span class="sxs-lookup"><span data-stu-id="cd692-119">Normal</span></span>|<span data-ttu-id="cd692-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="cd692-120">CommonStates</span></span>|<span data-ttu-id="cd692-121">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="cd692-121">The default state.</span></span>|  
|<span data-ttu-id="cd692-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="cd692-122">MouseOver</span></span>|<span data-ttu-id="cd692-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="cd692-123">CommonStates</span></span>|<span data-ttu-id="cd692-124">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="cd692-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="cd692-125">已停用</span><span class="sxs-lookup"><span data-stu-id="cd692-125">Disabled</span></span>|<span data-ttu-id="cd692-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="cd692-126">CommonStates</span></span>|<span data-ttu-id="cd692-127">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="cd692-127">The control is disabled.</span></span>|  
|<span data-ttu-id="cd692-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="cd692-128">ReadOnly</span></span>|<span data-ttu-id="cd692-129">CommonStates</span><span class="sxs-lookup"><span data-stu-id="cd692-129">CommonStates</span></span>|<span data-ttu-id="cd692-130">使用者無法變更中的文字<xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="cd692-130">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="cd692-131">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="cd692-131">Focused</span></span>|<span data-ttu-id="cd692-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="cd692-132">FocusStates</span></span>|<span data-ttu-id="cd692-133">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="cd692-133">The control has focus.</span></span>|  
|<span data-ttu-id="cd692-134">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="cd692-134">Unfocused</span></span>|<span data-ttu-id="cd692-135">FocusStates</span><span class="sxs-lookup"><span data-stu-id="cd692-135">FocusStates</span></span>|<span data-ttu-id="cd692-136">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="cd692-136">The control does not have focus.</span></span>|  
|<span data-ttu-id="cd692-137">驗證</span><span class="sxs-lookup"><span data-stu-id="cd692-137">Valid</span></span>|<span data-ttu-id="cd692-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="cd692-138">ValidationStates</span></span>|<span data-ttu-id="cd692-139">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="cd692-139">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="cd692-140">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="cd692-140">InvalidFocused</span></span>|<span data-ttu-id="cd692-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="cd692-141">ValidationStates</span></span>|<span data-ttu-id="cd692-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="cd692-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="cd692-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="cd692-143">InvalidUnfocused</span></span>|<span data-ttu-id="cd692-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="cd692-144">ValidationStates</span></span>|<span data-ttu-id="cd692-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="cd692-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="cd692-146">文字方塊 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="cd692-146">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="cd692-147">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.TextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="cd692-147">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="cd692-148">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="cd692-148">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="cd692-149">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041)。</span><span class="sxs-lookup"><span data-stu-id="cd692-149">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd692-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd692-150">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="cd692-151">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="cd692-151">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="cd692-152">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="cd692-152">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="cd692-153">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="cd692-153">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="cd692-154">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="cd692-154">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
