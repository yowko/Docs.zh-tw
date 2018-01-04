---
title: "StatusBar 樣式和範本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], StatusBar
- styles [WPF], StatusBar
- templates [WPF], StatusBar
- states [WPF], StatusBar
- parts [WPF], StatusBar
- StatusBar [WPF], styles and templates
ms.assetid: 9f5e1c25-81eb-4756-a0ac-d9e1fbe33ee2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 370f8f9bc61ffbdd3b98743d11f61613803e6d98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="statusbar-styles-and-templates"></a><span data-ttu-id="870d8-102">StatusBar 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="870d8-102">StatusBar Styles and Templates</span></span>
<span data-ttu-id="870d8-103">本主題描述樣式和範本<xref:System.Windows.Controls.Primitives.StatusBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="870d8-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span> <span data-ttu-id="870d8-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="870d8-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="870d8-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="870d8-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="statusbar-parts"></a><span data-ttu-id="870d8-106">StatusBar 組件</span><span class="sxs-lookup"><span data-stu-id="870d8-106">StatusBar Parts</span></span>  
 <span data-ttu-id="870d8-107"><xref:System.Windows.Controls.Primitives.StatusBar>控制項沒有任何已命名的組件。</span><span class="sxs-lookup"><span data-stu-id="870d8-107">The <xref:System.Windows.Controls.Primitives.StatusBar> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="870d8-108">StatusBar 狀態</span><span class="sxs-lookup"><span data-stu-id="870d8-108">StatusBar States</span></span>  
 <span data-ttu-id="870d8-109">下表列出的視覺狀態<xref:System.Windows.Controls.Primitives.StatusBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="870d8-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
|<span data-ttu-id="870d8-110">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="870d8-110">VisualState Name</span></span>|<span data-ttu-id="870d8-111">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="870d8-111">VisualStateGroup Name</span></span>|<span data-ttu-id="870d8-112">描述</span><span class="sxs-lookup"><span data-stu-id="870d8-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="870d8-113">驗證</span><span class="sxs-lookup"><span data-stu-id="870d8-113">Valid</span></span>|<span data-ttu-id="870d8-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="870d8-114">ValidationStates</span></span>|<span data-ttu-id="870d8-115">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="870d8-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="870d8-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="870d8-116">InvalidFocused</span></span>|<span data-ttu-id="870d8-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="870d8-117">ValidationStates</span></span>|<span data-ttu-id="870d8-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="870d8-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="870d8-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="870d8-119">InvalidUnfocused</span></span>|<span data-ttu-id="870d8-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="870d8-120">ValidationStates</span></span>|<span data-ttu-id="870d8-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="870d8-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbaritem-parts"></a><span data-ttu-id="870d8-122">StatusBarItem 組件</span><span class="sxs-lookup"><span data-stu-id="870d8-122">StatusBarItem Parts</span></span>  
 <span data-ttu-id="870d8-123"><xref:System.Windows.Controls.Primitives.StatusBarItem>控制項沒有任何已命名的組件。</span><span class="sxs-lookup"><span data-stu-id="870d8-123">The <xref:System.Windows.Controls.Primitives.StatusBarItem> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="870d8-124">StatusBar 狀態</span><span class="sxs-lookup"><span data-stu-id="870d8-124">StatusBar States</span></span>  
 <span data-ttu-id="870d8-125">下表列出的視覺狀態<xref:System.Windows.Controls.Primitives.StatusBarItem>控制項。</span><span class="sxs-lookup"><span data-stu-id="870d8-125">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBarItem> control.</span></span>  
  
|<span data-ttu-id="870d8-126">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="870d8-126">VisualState Name</span></span>|<span data-ttu-id="870d8-127">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="870d8-127">VisualStateGroup Name</span></span>|<span data-ttu-id="870d8-128">描述</span><span class="sxs-lookup"><span data-stu-id="870d8-128">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="870d8-129">驗證</span><span class="sxs-lookup"><span data-stu-id="870d8-129">Valid</span></span>|<span data-ttu-id="870d8-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="870d8-130">ValidationStates</span></span>|<span data-ttu-id="870d8-131">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="870d8-131">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="870d8-132">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="870d8-132">InvalidFocused</span></span>|<span data-ttu-id="870d8-133">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="870d8-133">ValidationStates</span></span>|<span data-ttu-id="870d8-134"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="870d8-134">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="870d8-135">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="870d8-135">InvalidUnfocused</span></span>|<span data-ttu-id="870d8-136">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="870d8-136">ValidationStates</span></span>|<span data-ttu-id="870d8-137"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="870d8-137">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbar-controltemplate-example"></a><span data-ttu-id="870d8-138">StatusBar ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="870d8-138">StatusBar ControlTemplate Example</span></span>  
 <span data-ttu-id="870d8-139">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.Primitives.StatusBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="870d8-139">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#StatusBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/statusbar.xaml#statusbar)]  
  
 <span data-ttu-id="870d8-140"><xref:System.Windows.Controls.ControlTemplate>會使用一個或多個下列資源。</span><span class="sxs-lookup"><span data-stu-id="870d8-140">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="870d8-141">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041)。</span><span class="sxs-lookup"><span data-stu-id="870d8-141">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="870d8-142">請參閱</span><span class="sxs-lookup"><span data-stu-id="870d8-142">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="870d8-143">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="870d8-143">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="870d8-144">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="870d8-144">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="870d8-145">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="870d8-145">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="870d8-146">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="870d8-146">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
