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
ms.openlocfilehash: fa192e20ea84e96c9f85ff84e16c63b7f56c8a98
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283544"
---
# <a name="contextmenu-styles-and-templates"></a><span data-ttu-id="188e5-102">ContextMenu 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="188e5-102">ContextMenu Styles and Templates</span></span>
<span data-ttu-id="188e5-103">本主題描述 <xref:System.Windows.Controls.ContextMenu> 控制項的樣式和範本。</span><span class="sxs-lookup"><span data-stu-id="188e5-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ContextMenu> control.</span></span> <span data-ttu-id="188e5-104">您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。</span><span class="sxs-lookup"><span data-stu-id="188e5-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="188e5-105">如需詳細資訊，請參閱[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。</span><span class="sxs-lookup"><span data-stu-id="188e5-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="contextmenu-parts"></a><span data-ttu-id="188e5-106">CoNtextMenu 元件</span><span class="sxs-lookup"><span data-stu-id="188e5-106">ContextMenu Parts</span></span>  
 <span data-ttu-id="188e5-107"><xref:System.Windows.Controls.ContextMenu> 控制項沒有任何已命名的元件。</span><span class="sxs-lookup"><span data-stu-id="188e5-107">The <xref:System.Windows.Controls.ContextMenu> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="188e5-108">當您建立 <xref:System.Windows.Controls.ContextMenu>的 <xref:System.Windows.Controls.ControlTemplate> 時，您的範本可能會在 <xref:System.Windows.Controls.ScrollViewer>中包含 <xref:System.Windows.Controls.ItemsPresenter>。</span><span class="sxs-lookup"><span data-stu-id="188e5-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ContextMenu>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="188e5-109">（<xref:System.Windows.Controls.ItemsPresenter> 會顯示 <xref:System.Windows.Controls.ContextMenu>中的每個專案，<xref:System.Windows.Controls.ScrollViewer> 可在控制項內進行滾動）。</span><span class="sxs-lookup"><span data-stu-id="188e5-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ContextMenu>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="188e5-110">如果 <xref:System.Windows.Controls.ItemsPresenter> 不是 <xref:System.Windows.Controls.ScrollViewer>的直接子系，您必須為 <xref:System.Windows.Controls.ItemsPresenter> 指定名稱，`ItemsPresenter`。</span><span class="sxs-lookup"><span data-stu-id="188e5-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="contextmenu-states"></a><span data-ttu-id="188e5-111">CoNtextMenu 狀態</span><span class="sxs-lookup"><span data-stu-id="188e5-111">ContextMenu States</span></span>  
 <span data-ttu-id="188e5-112">下表列出 <xref:System.Windows.Controls.ContextMenu> 控制項的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="188e5-112">The following table lists the visual states for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
|<span data-ttu-id="188e5-113">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="188e5-113">VisualState Name</span></span>|<span data-ttu-id="188e5-114">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="188e5-114">VisualStateGroup Name</span></span>|<span data-ttu-id="188e5-115">描述</span><span class="sxs-lookup"><span data-stu-id="188e5-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="188e5-116">驗證</span><span class="sxs-lookup"><span data-stu-id="188e5-116">Valid</span></span>|<span data-ttu-id="188e5-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="188e5-117">ValidationStates</span></span>|<span data-ttu-id="188e5-118">控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。</span><span class="sxs-lookup"><span data-stu-id="188e5-118">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="188e5-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="188e5-119">InvalidFocused</span></span>|<span data-ttu-id="188e5-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="188e5-120">ValidationStates</span></span>|<span data-ttu-id="188e5-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。</span><span class="sxs-lookup"><span data-stu-id="188e5-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="188e5-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="188e5-122">InvalidUnfocused</span></span>|<span data-ttu-id="188e5-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="188e5-123">ValidationStates</span></span>|<span data-ttu-id="188e5-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="188e5-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="contextmenu-controltemplate-example"></a><span data-ttu-id="188e5-125">CoNtextMenu ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="188e5-125">ContextMenu ControlTemplate Example</span></span>  
 <span data-ttu-id="188e5-126">下列範例顯示如何定義 <xref:System.Windows.Controls.ContextMenu> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="188e5-126">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#contextmenu)]  
  
 <span data-ttu-id="188e5-127"><xref:System.Windows.Controls.ControlTemplate> 使用下列資源。</span><span class="sxs-lookup"><span data-stu-id="188e5-127">The <xref:System.Windows.Controls.ControlTemplate> uses the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="188e5-128">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。</span><span class="sxs-lookup"><span data-stu-id="188e5-128">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="188e5-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="188e5-129">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="188e5-130">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="188e5-130">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="188e5-131">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="188e5-131">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="188e5-132">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="188e5-132">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="188e5-133">建立控制項的範本</span><span class="sxs-lookup"><span data-stu-id="188e5-133">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
