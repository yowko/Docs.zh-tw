---
title: "PasswordBox 樣式和範本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], PasswordBox
- templates [WPF], PasswordBox
- ControlTemplate [WPF], PasswordBox
- states [WPF], PasswordBox
- PasswordBox [WPF], styles and templates
- parts [WPF], PasswordBox
ms.assetid: deb52107-959f-4a60-b303-d21a0a933060
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 17a9292ef6aeba157780be5ec87d67725eb833a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="passwordbox-syles-and-templates"></a><span data-ttu-id="1f1e4-102">PasswordBox 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="1f1e4-102">PasswordBox Syles and Templates</span></span>
<span data-ttu-id="1f1e4-103">本主題描述樣式和範本<xref:System.Windows.Controls.PasswordBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="1f1e4-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.PasswordBox> control.</span></span> <span data-ttu-id="1f1e4-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="1f1e4-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="1f1e4-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="1f1e4-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="passwordbox-parts"></a><span data-ttu-id="1f1e4-106">PasswordBox 組件</span><span class="sxs-lookup"><span data-stu-id="1f1e4-106">PasswordBox Parts</span></span>  
 <span data-ttu-id="1f1e4-107">下表列出的具名組件<xref:System.Windows.Controls.PasswordBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="1f1e4-107">The following table lists the named parts for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
|<span data-ttu-id="1f1e4-108">組件</span><span class="sxs-lookup"><span data-stu-id="1f1e4-108">Part</span></span>|<span data-ttu-id="1f1e4-109">類型</span><span class="sxs-lookup"><span data-stu-id="1f1e4-109">Type</span></span>|<span data-ttu-id="1f1e4-110">說明</span><span class="sxs-lookup"><span data-stu-id="1f1e4-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="1f1e4-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="1f1e4-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="1f1e4-112">可以包含視覺項目<xref:System.Windows.FrameworkElement>。</span><span class="sxs-lookup"><span data-stu-id="1f1e4-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="1f1e4-113">文字<xref:System.Windows.Controls.PasswordBox>會顯示在這個項目。</span><span class="sxs-lookup"><span data-stu-id="1f1e4-113">The text of the <xref:System.Windows.Controls.PasswordBox> is displayed in this element.</span></span>|  
  
## <a name="passwordbox-states"></a><span data-ttu-id="1f1e4-114">PasswordBox 狀態</span><span class="sxs-lookup"><span data-stu-id="1f1e4-114">PasswordBox States</span></span>  
 <span data-ttu-id="1f1e4-115">下表列出的視覺狀態<xref:System.Windows.Controls.PasswordBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="1f1e4-115">The following table lists the visual states for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
|<span data-ttu-id="1f1e4-116">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="1f1e4-116">VisualState Name</span></span>|<span data-ttu-id="1f1e4-117">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="1f1e4-117">VisualStateGroup Name</span></span>|<span data-ttu-id="1f1e4-118">描述</span><span class="sxs-lookup"><span data-stu-id="1f1e4-118">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="1f1e4-119">一般</span><span class="sxs-lookup"><span data-stu-id="1f1e4-119">Normal</span></span>|<span data-ttu-id="1f1e4-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="1f1e4-120">CommonStates</span></span>|<span data-ttu-id="1f1e4-121">預設狀態。</span><span class="sxs-lookup"><span data-stu-id="1f1e4-121">The default state.</span></span>|  
|<span data-ttu-id="1f1e4-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="1f1e4-122">MouseOver</span></span>|<span data-ttu-id="1f1e4-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="1f1e4-123">CommonStates</span></span>|<span data-ttu-id="1f1e4-124">滑鼠指標移到控制項上。</span><span class="sxs-lookup"><span data-stu-id="1f1e4-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="1f1e4-125">已停用</span><span class="sxs-lookup"><span data-stu-id="1f1e4-125">Disabled</span></span>|<span data-ttu-id="1f1e4-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="1f1e4-126">CommonStates</span></span>|<span data-ttu-id="1f1e4-127">已停用控制項。</span><span class="sxs-lookup"><span data-stu-id="1f1e4-127">The control is disabled.</span></span>|  
|<span data-ttu-id="1f1e4-128">已取得焦點</span><span class="sxs-lookup"><span data-stu-id="1f1e4-128">Focused</span></span>|<span data-ttu-id="1f1e4-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="1f1e4-129">FocusStates</span></span>|<span data-ttu-id="1f1e4-130">控制項已取得焦點。</span><span class="sxs-lookup"><span data-stu-id="1f1e4-130">The control has focus.</span></span>|  
|<span data-ttu-id="1f1e4-131">未取得焦點</span><span class="sxs-lookup"><span data-stu-id="1f1e4-131">Unfocused</span></span>|<span data-ttu-id="1f1e4-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="1f1e4-132">FocusStates</span></span>|<span data-ttu-id="1f1e4-133">控制項未取得焦點。</span><span class="sxs-lookup"><span data-stu-id="1f1e4-133">The control does not have focus.</span></span>|  
|<span data-ttu-id="1f1e4-134">驗證</span><span class="sxs-lookup"><span data-stu-id="1f1e4-134">Valid</span></span>|<span data-ttu-id="1f1e4-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1f1e4-135">ValidationStates</span></span>|<span data-ttu-id="1f1e4-136">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="1f1e4-136">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="1f1e4-137">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="1f1e4-137">InvalidFocused</span></span>|<span data-ttu-id="1f1e4-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1f1e4-138">ValidationStates</span></span>|<span data-ttu-id="1f1e4-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="1f1e4-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="1f1e4-140">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="1f1e4-140">InvalidUnfocused</span></span>|<span data-ttu-id="1f1e4-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1f1e4-141">ValidationStates</span></span>|<span data-ttu-id="1f1e4-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="1f1e4-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="passwordbox-controltemplate-example"></a><span data-ttu-id="1f1e4-143">PasswordBox ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="1f1e4-143">PasswordBox ControlTemplate Example</span></span>  
 <span data-ttu-id="1f1e4-144">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.PasswordBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="1f1e4-144">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#PasswordBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]  
  
 <span data-ttu-id="1f1e4-145">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="1f1e4-145">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="1f1e4-146">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041)。</span><span class="sxs-lookup"><span data-stu-id="1f1e4-146">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f1e4-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f1e4-147">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="1f1e4-148">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="1f1e4-148">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="1f1e4-149">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="1f1e4-149">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="1f1e4-150">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="1f1e4-150">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="1f1e4-151">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="1f1e4-151">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
