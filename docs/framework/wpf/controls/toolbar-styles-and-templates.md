---
title: "ToolBar 樣式和範本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], ToolBar
- styles [WPF], ToolBar
- ControlTemplate [WPF], ToolBar
- parts [WPF], ToolBar
- ToolBar [WPF], styles and templates
- templates [WPF], ToolBar
ms.assetid: bd875f46-4690-46f5-81e0-f11a9822484f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d56858f3785a4d4d49a0781fbf4c19397a3bb375
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="toolbar-styles-and-templates"></a><span data-ttu-id="e6437-102">ToolBar 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="e6437-102">ToolBar Styles and Templates</span></span>
<span data-ttu-id="e6437-103">本主題描述樣式和範本<xref:System.Windows.Controls.ToolBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="e6437-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolBar> control.</span></span> <span data-ttu-id="e6437-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="e6437-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="e6437-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="e6437-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="toolbar-parts"></a><span data-ttu-id="e6437-106">工具列組件</span><span class="sxs-lookup"><span data-stu-id="e6437-106">ToolBar Parts</span></span>  
 <span data-ttu-id="e6437-107">下表列出的具名組件<xref:System.Windows.Controls.ToolBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="e6437-107">The following table lists the named parts for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="e6437-108">組件</span><span class="sxs-lookup"><span data-stu-id="e6437-108">Part</span></span>|<span data-ttu-id="e6437-109">類型</span><span class="sxs-lookup"><span data-stu-id="e6437-109">Type</span></span>|<span data-ttu-id="e6437-110">描述</span><span class="sxs-lookup"><span data-stu-id="e6437-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="e6437-111">PART_ToolBarPanel</span><span class="sxs-lookup"><span data-stu-id="e6437-111">PART_ToolBarPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarPanel>|<span data-ttu-id="e6437-112">物件上包含之控制項<xref:System.Windows.Controls.ToolBar>。</span><span class="sxs-lookup"><span data-stu-id="e6437-112">The object that contains the controls on the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
|<span data-ttu-id="e6437-113">PART_ToolBarOverflowPanel</span><span class="sxs-lookup"><span data-stu-id="e6437-113">PART_ToolBarOverflowPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|<span data-ttu-id="e6437-114">物件，其中包含的溢位區域中的控制項<xref:System.Windows.Controls.ToolBar>。</span><span class="sxs-lookup"><span data-stu-id="e6437-114">The object that contains the controls that are in the overflow area of the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
  
 <span data-ttu-id="e6437-115">當您建立<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.ToolBar>，可能會包含您的範本<xref:System.Windows.Controls.ItemsPresenter>內<xref:System.Windows.Controls.ScrollViewer>。</span><span class="sxs-lookup"><span data-stu-id="e6437-115">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ToolBar>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="e6437-116">(<xref:System.Windows.Controls.ItemsPresenter>會顯示每個項目<xref:System.Windows.Controls.ToolBar>;<xref:System.Windows.Controls.ScrollViewer>可捲動控制項內)。</span><span class="sxs-lookup"><span data-stu-id="e6437-116">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ToolBar>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="e6437-117">如果<xref:System.Windows.Controls.ItemsPresenter>不是直接子系<xref:System.Windows.Controls.ScrollViewer>，您必須提供<xref:System.Windows.Controls.ItemsPresenter>名稱`ItemsPresenter`。</span><span class="sxs-lookup"><span data-stu-id="e6437-117">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="toolbar-states"></a><span data-ttu-id="e6437-118">工具列狀態</span><span class="sxs-lookup"><span data-stu-id="e6437-118">ToolBar States</span></span>  
 <span data-ttu-id="e6437-119">下表列出的視覺狀態<xref:System.Windows.Controls.ToolBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="e6437-119">The following table lists the visual states for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="e6437-120">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="e6437-120">VisualState Name</span></span>|<span data-ttu-id="e6437-121">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="e6437-121">VisualStateGroup Name</span></span>|<span data-ttu-id="e6437-122">描述</span><span class="sxs-lookup"><span data-stu-id="e6437-122">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="e6437-123">驗證</span><span class="sxs-lookup"><span data-stu-id="e6437-123">Valid</span></span>|<span data-ttu-id="e6437-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e6437-124">ValidationStates</span></span>|<span data-ttu-id="e6437-125">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="e6437-125">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="e6437-126">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="e6437-126">InvalidFocused</span></span>|<span data-ttu-id="e6437-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e6437-127">ValidationStates</span></span>|<span data-ttu-id="e6437-128"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="e6437-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="e6437-129">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="e6437-129">InvalidUnfocused</span></span>|<span data-ttu-id="e6437-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e6437-130">ValidationStates</span></span>|<span data-ttu-id="e6437-131"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="e6437-131">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="toolbar-controltemplate-example"></a><span data-ttu-id="e6437-132">工具列 ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="e6437-132">ToolBar ControlTemplate Example</span></span>  
 <span data-ttu-id="e6437-133">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.ToolBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="e6437-133">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/toolbar.xaml#toolbar)]  
  
 <span data-ttu-id="e6437-134">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="e6437-134">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="e6437-135">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041)。</span><span class="sxs-lookup"><span data-stu-id="e6437-135">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6437-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="e6437-136">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="e6437-137">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="e6437-137">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="e6437-138">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="e6437-138">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="e6437-139">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="e6437-139">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="e6437-140">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="e6437-140">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
