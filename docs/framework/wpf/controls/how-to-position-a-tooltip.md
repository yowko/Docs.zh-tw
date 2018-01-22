---
title: "如何：置放工具提示"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], positioning
- positioning ToolTip controls [WPF]
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc81fa247f21448a4ccbd62baccb72c0ec14bb31
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-position-a-tooltip"></a><span data-ttu-id="8d8cb-102">如何：置放工具提示</span><span class="sxs-lookup"><span data-stu-id="8d8cb-102">How to: Position a ToolTip</span></span>
<span data-ttu-id="8d8cb-103">這個範例示範如何在螢幕上指定工具提示的位置。</span><span class="sxs-lookup"><span data-stu-id="8d8cb-103">This example shows how to specify the position of a tooltip on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d8cb-104">範例</span><span class="sxs-lookup"><span data-stu-id="8d8cb-104">Example</span></span>  
 <span data-ttu-id="8d8cb-105">您可以使用放置在工具提示的五個屬性定義中的一組<xref:System.Windows.Controls.ToolTip>和<xref:System.Windows.Controls.ToolTipService>類別。</span><span class="sxs-lookup"><span data-stu-id="8d8cb-105">You can position a tooltip by using a set of five properties that are defined in both the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> classes.</span></span> <span data-ttu-id="8d8cb-106">下表顯示這兩個集合的五個屬性，並提供根據類別參考文件的連結。</span><span class="sxs-lookup"><span data-stu-id="8d8cb-106">The following table shows these two sets of five properties and provides links to their reference documentation according to class.</span></span>  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a><span data-ttu-id="8d8cb-107">對應的工具提示屬性，根據類別</span><span class="sxs-lookup"><span data-stu-id="8d8cb-107">Corresponding tooltip properties according to class</span></span>  
  
|<span data-ttu-id="8d8cb-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType>類別屬性</span><span class="sxs-lookup"><span data-stu-id="8d8cb-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> class properties</span></span>|<span data-ttu-id="8d8cb-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType>類別屬性</span><span class="sxs-lookup"><span data-stu-id="8d8cb-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> class properties</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="8d8cb-110">如果您定義工具提示的內容使用<xref:System.Windows.Controls.ToolTip>物件，您可以使用其中一個類別的屬性; 不過，<xref:System.Windows.Controls.ToolTipService>屬性的優先順序。</span><span class="sxs-lookup"><span data-stu-id="8d8cb-110">If you define the contents of a tooltip by using a <xref:System.Windows.Controls.ToolTip> object, you can use the properties of either class; however, the <xref:System.Windows.Controls.ToolTipService> properties take precedence.</span></span> <span data-ttu-id="8d8cb-111">使用<xref:System.Windows.Controls.ToolTipService>內容為未定義的工具提示<xref:System.Windows.Controls.ToolTip>物件。</span><span class="sxs-lookup"><span data-stu-id="8d8cb-111">Use the <xref:System.Windows.Controls.ToolTipService> properties for tooltips that are not defined as <xref:System.Windows.Controls.ToolTip> objects.</span></span>  
  
 <span data-ttu-id="8d8cb-112">下圖顯示如何使用放置在工具提示的這些屬性。</span><span class="sxs-lookup"><span data-stu-id="8d8cb-112">The following illustrations show how to position a tooltip by using these properties.</span></span> <span data-ttu-id="8d8cb-113">雖然、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]這些圖中的範例示範如何設定所定義的屬性<xref:System.Windows.Controls.ToolTip>類別的對應屬性<xref:System.Windows.Controls.ToolTipService>類別遵循相同的配置規則。</span><span class="sxs-lookup"><span data-stu-id="8d8cb-113">Although, the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples in these illustrations show how to set the properties that are defined by the <xref:System.Windows.Controls.ToolTip> class, the corresponding properties of the <xref:System.Windows.Controls.ToolTipService> class follow the same layout rules.</span></span> <span data-ttu-id="8d8cb-114">如需可能的值為位置屬性的詳細資訊，請參閱[快顯視窗放置行為](../../../../docs/framework/wpf/controls/popup-placement-behavior.md)。</span><span class="sxs-lookup"><span data-stu-id="8d8cb-114">For more information about the possible values for the Placement property, see [Popup Placement Behavior](../../../../docs/framework/wpf/controls/popup-placement-behavior.md).</span></span>  
  
 <span data-ttu-id="8d8cb-115">![ToolTip 位置](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")</span><span class="sxs-lookup"><span data-stu-id="8d8cb-115">![ToolTip placement](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")</span></span>  
<span data-ttu-id="8d8cb-116">ToolTip 位置使用放置屬性</span><span class="sxs-lookup"><span data-stu-id="8d8cb-116">ToolTip placement by using the Placement property</span></span>  
  
 <span data-ttu-id="8d8cb-117">![使用定位矩形放置 ToolTip](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")</span><span class="sxs-lookup"><span data-stu-id="8d8cb-117">![Placing a ToolTip by using a placement rectangle](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")</span></span>  
<span data-ttu-id="8d8cb-118">ToolTip 位置使用 Placement 與 PlacementRectangle 屬性</span><span class="sxs-lookup"><span data-stu-id="8d8cb-118">ToolTip placement by using the Placement and PlacementRectangle properties</span></span>  
  
 <span data-ttu-id="8d8cb-119">![ToolTip 位置圖表](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")</span><span class="sxs-lookup"><span data-stu-id="8d8cb-119">![ToolTip placement diagram](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")</span></span>  
<span data-ttu-id="8d8cb-120">ToolTip 位置使用的位置、 PlacementRectangle 和位移屬性</span><span class="sxs-lookup"><span data-stu-id="8d8cb-120">ToolTip placement by using the Placement, PlacementRectangle, and Offset properties</span></span>  
  
 <span data-ttu-id="8d8cb-121">下列範例示範如何使用<xref:System.Windows.Controls.ToolTip>屬性，以指定的內容會以工具提示的位置<xref:System.Windows.Controls.ToolTip>物件。</span><span class="sxs-lookup"><span data-stu-id="8d8cb-121">The following example shows how to use the <xref:System.Windows.Controls.ToolTip> properties to specify the position of a tooltip whose content is a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 <span data-ttu-id="8d8cb-122">下列範例示範如何使用<xref:System.Windows.Controls.ToolTipService>屬性，以指定其內容不是為工具提示的位置<xref:System.Windows.Controls.ToolTip>物件。</span><span class="sxs-lookup"><span data-stu-id="8d8cb-122">The following example shows how to use the <xref:System.Windows.Controls.ToolTipService> properties to specify the position of a tooltip whose content is not a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a><span data-ttu-id="8d8cb-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="8d8cb-123">See Also</span></span>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [<span data-ttu-id="8d8cb-124">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="8d8cb-124">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)  
 [<span data-ttu-id="8d8cb-125">工具提示概觀</span><span class="sxs-lookup"><span data-stu-id="8d8cb-125">ToolTip Overview</span></span>](../../../../docs/framework/wpf/controls/tooltip-overview.md)  
 [<span data-ttu-id="8d8cb-126">使用 ContextMenuService 和 ToolTipService</span><span class="sxs-lookup"><span data-stu-id="8d8cb-126">Use the ContextMenuService and ToolTipService</span></span>](http://msdn.microsoft.com/library/809b0e9c-d612-4cda-b8af-1a698c68f4d1)
