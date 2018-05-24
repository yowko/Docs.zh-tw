---
title: ContextMenu 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], ContextMenu
- parts [WPF], ContextMenu
- ContextMenu [WPF], styles and templates
- styles [WPF], ContextMenu
- ControlTemplate [WPF], ContextMenu
- states [WPF], ContextMenu
ms.assetid: 342d1f17-c406-4f94-8f55-867c5f3ea511
ms.openlocfilehash: 671fb0a4f178c9e16149f6d47945670ea0e64d48
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
---
# <a name="contextmenu-styles-and-templates"></a><span data-ttu-id="91f41-102">ContextMenu 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="91f41-102">ContextMenu Styles and Templates</span></span>
<span data-ttu-id="91f41-103">本主題描述樣式和範本<xref:System.Windows.Controls.ContextMenu>控制項。</span><span class="sxs-lookup"><span data-stu-id="91f41-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ContextMenu> control.</span></span> <span data-ttu-id="91f41-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="91f41-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="91f41-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="91f41-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="contextmenu-parts"></a><span data-ttu-id="91f41-106">ContextMenu 組件</span><span class="sxs-lookup"><span data-stu-id="91f41-106">ContextMenu Parts</span></span>  
 <span data-ttu-id="91f41-107"><xref:System.Windows.Controls.ContextMenu>控制項沒有任何已命名的組件。</span><span class="sxs-lookup"><span data-stu-id="91f41-107">The <xref:System.Windows.Controls.ContextMenu> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="91f41-108">當您建立<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.ContextMenu>，可能會包含您的範本<xref:System.Windows.Controls.ItemsPresenter>內<xref:System.Windows.Controls.ScrollViewer>。</span><span class="sxs-lookup"><span data-stu-id="91f41-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ContextMenu>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="91f41-109">(<xref:System.Windows.Controls.ItemsPresenter>會顯示每個項目<xref:System.Windows.Controls.ContextMenu>;<xref:System.Windows.Controls.ScrollViewer>可捲動控制項內)。</span><span class="sxs-lookup"><span data-stu-id="91f41-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ContextMenu>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="91f41-110">如果<xref:System.Windows.Controls.ItemsPresenter>不是直接子系<xref:System.Windows.Controls.ScrollViewer>，您必須提供<xref:System.Windows.Controls.ItemsPresenter>名稱`ItemsPresenter`。</span><span class="sxs-lookup"><span data-stu-id="91f41-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="contextmenu-states"></a><span data-ttu-id="91f41-111">ContextMenu 狀態</span><span class="sxs-lookup"><span data-stu-id="91f41-111">ContextMenu States</span></span>  
 <span data-ttu-id="91f41-112">下表列出的視覺狀態<xref:System.Windows.Controls.ContextMenu>控制項。</span><span class="sxs-lookup"><span data-stu-id="91f41-112">The following table lists the visual states for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
|<span data-ttu-id="91f41-113">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="91f41-113">VisualState Name</span></span>|<span data-ttu-id="91f41-114">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="91f41-114">VisualStateGroup Name</span></span>|<span data-ttu-id="91f41-115">描述</span><span class="sxs-lookup"><span data-stu-id="91f41-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="91f41-116">驗證</span><span class="sxs-lookup"><span data-stu-id="91f41-116">Valid</span></span>|<span data-ttu-id="91f41-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="91f41-117">ValidationStates</span></span>|<span data-ttu-id="91f41-118">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="91f41-118">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="91f41-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="91f41-119">InvalidFocused</span></span>|<span data-ttu-id="91f41-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="91f41-120">ValidationStates</span></span>|<span data-ttu-id="91f41-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="91f41-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="91f41-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="91f41-122">InvalidUnfocused</span></span>|<span data-ttu-id="91f41-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="91f41-123">ValidationStates</span></span>|<span data-ttu-id="91f41-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="91f41-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="contextmenu-controltemplate-example"></a><span data-ttu-id="91f41-125">ContextMenu ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="91f41-125">ContextMenu ControlTemplate Example</span></span>  
 <span data-ttu-id="91f41-126">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.ContextMenu>控制項。</span><span class="sxs-lookup"><span data-stu-id="91f41-126">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ContextMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#contextmenu)]  
  
 <span data-ttu-id="91f41-127"><xref:System.Windows.Controls.ControlTemplate>使用下列資源。</span><span class="sxs-lookup"><span data-stu-id="91f41-127">The <xref:System.Windows.Controls.ControlTemplate> uses the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="91f41-128">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="91f41-128">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91f41-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91f41-129">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="91f41-130">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="91f41-130">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="91f41-131">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="91f41-131">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="91f41-132">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="91f41-132">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="91f41-133">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="91f41-133">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
