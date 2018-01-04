---
title: "ScrollViewer 樣式和範本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], ScrollViewer
- states [WPF], ScrollViewer
- styles [WPF], ScrollViewer
- templates [WPF], ScrollViewer
- ControlTemplate [WPF], ScrollViewer
- ScrollViewer [WPF], styles and templates
ms.assetid: dffdd822-ae69-4946-abaf-710860cd65b2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 74f8a693a143e1c6788dd79a1c1bbd1954f8cfd0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="scrollviewer-styles-and-templates"></a><span data-ttu-id="01895-102">ScrollViewer 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="01895-102">ScrollViewer Styles and Templates</span></span>
<span data-ttu-id="01895-103">本主題描述樣式和範本<xref:System.Windows.Controls.ScrollViewer>控制項。</span><span class="sxs-lookup"><span data-stu-id="01895-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span> <span data-ttu-id="01895-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="01895-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="01895-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="01895-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollviewer-parts"></a><span data-ttu-id="01895-106">ScrollViewer 組件</span><span class="sxs-lookup"><span data-stu-id="01895-106">ScrollViewer Parts</span></span>  
 <span data-ttu-id="01895-107">下表列出的具名組件<xref:System.Windows.Controls.ScrollViewer>控制項。</span><span class="sxs-lookup"><span data-stu-id="01895-107">The following table lists the named parts for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="01895-108">組件</span><span class="sxs-lookup"><span data-stu-id="01895-108">Part</span></span>|<span data-ttu-id="01895-109">類型</span><span class="sxs-lookup"><span data-stu-id="01895-109">Type</span></span>|<span data-ttu-id="01895-110">描述</span><span class="sxs-lookup"><span data-stu-id="01895-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="01895-111">PART_ScrollContentPresenter</span><span class="sxs-lookup"><span data-stu-id="01895-111">PART_ScrollContentPresenter</span></span>|<xref:System.Windows.Controls.ScrollContentPresenter>|<span data-ttu-id="01895-112">在內容預留位置<xref:System.Windows.Controls.ScrollViewer>。</span><span class="sxs-lookup"><span data-stu-id="01895-112">The placeholder for content in the <xref:System.Windows.Controls.ScrollViewer>.</span></span>|  
|<span data-ttu-id="01895-113">PART_HorizontalScrollBar</span><span class="sxs-lookup"><span data-stu-id="01895-113">PART_HorizontalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="01895-114"><xref:System.Windows.Controls.Primitives.ScrollBar>用來水平捲動內容。</span><span class="sxs-lookup"><span data-stu-id="01895-114">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content horizontally.</span></span>|  
|<span data-ttu-id="01895-115">PART_VerticalScrollBar</span><span class="sxs-lookup"><span data-stu-id="01895-115">PART_VerticalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="01895-116"><xref:System.Windows.Controls.Primitives.ScrollBar>用於垂直捲動內容。</span><span class="sxs-lookup"><span data-stu-id="01895-116">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content vertically.</span></span>|  
  
## <a name="scrollviewer-states"></a><span data-ttu-id="01895-117">ScrollViewer 狀態</span><span class="sxs-lookup"><span data-stu-id="01895-117">ScrollViewer States</span></span>  
 <span data-ttu-id="01895-118">下表列出的視覺狀態<xref:System.Windows.Controls.ScrollViewer>控制項。</span><span class="sxs-lookup"><span data-stu-id="01895-118">The following table lists the visual states for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="01895-119">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="01895-119">VisualState Name</span></span>|<span data-ttu-id="01895-120">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="01895-120">VisualStateGroup Name</span></span>|<span data-ttu-id="01895-121">描述</span><span class="sxs-lookup"><span data-stu-id="01895-121">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="01895-122">驗證</span><span class="sxs-lookup"><span data-stu-id="01895-122">Valid</span></span>|<span data-ttu-id="01895-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="01895-123">ValidationStates</span></span>|<span data-ttu-id="01895-124">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="01895-124">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="01895-125">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="01895-125">InvalidFocused</span></span>|<span data-ttu-id="01895-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="01895-126">ValidationStates</span></span>|<span data-ttu-id="01895-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="01895-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="01895-128">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="01895-128">InvalidUnfocused</span></span>|<span data-ttu-id="01895-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="01895-129">ValidationStates</span></span>|<span data-ttu-id="01895-130"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="01895-130">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollviewer-controltemplate-example"></a><span data-ttu-id="01895-131">ScrollViewer ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="01895-131">ScrollViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="01895-132">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.ScrollViewer>控制項。</span><span class="sxs-lookup"><span data-stu-id="01895-132">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollviewer.xaml#scrollviewer)]  
  
 <span data-ttu-id="01895-133">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="01895-133">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="01895-134">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041)。</span><span class="sxs-lookup"><span data-stu-id="01895-134">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01895-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="01895-135">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="01895-136">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="01895-136">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="01895-137">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="01895-137">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="01895-138">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="01895-138">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="01895-139">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="01895-139">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
