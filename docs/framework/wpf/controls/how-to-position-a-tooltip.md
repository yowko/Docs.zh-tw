---
title: 如何：置放工具提示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], positioning
- positioning ToolTip controls [WPF]
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
ms.openlocfilehash: 0f52703e4fe127daa40f220280f084b2026580cc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186943"
---
# <a name="how-to-position-a-tooltip"></a><span data-ttu-id="e3940-102">如何：置放工具提示</span><span class="sxs-lookup"><span data-stu-id="e3940-102">How to: Position a ToolTip</span></span>
<span data-ttu-id="e3940-103">此示例演示如何在螢幕上指定工具提示的位置。</span><span class="sxs-lookup"><span data-stu-id="e3940-103">This example shows how to specify the position of a tooltip on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3940-104">範例</span><span class="sxs-lookup"><span data-stu-id="e3940-104">Example</span></span>  
 <span data-ttu-id="e3940-105">可以使用 在 和<xref:System.Windows.Controls.ToolTip><xref:System.Windows.Controls.ToolTipService>類 中定義的一組五個屬性來定位工具提示。</span><span class="sxs-lookup"><span data-stu-id="e3940-105">You can position a tooltip by using a set of five properties that are defined in both the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> classes.</span></span> <span data-ttu-id="e3940-106">下表顯示了這兩組五個屬性，並根據類提供指向其參考文檔的連結。</span><span class="sxs-lookup"><span data-stu-id="e3940-106">The following table shows these two sets of five properties and provides links to their reference documentation according to class.</span></span>  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a><span data-ttu-id="e3940-107">根據類對應的工具提示屬性</span><span class="sxs-lookup"><span data-stu-id="e3940-107">Corresponding tooltip properties according to class</span></span>  
  
|<span data-ttu-id="e3940-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType>類屬性</span><span class="sxs-lookup"><span data-stu-id="e3940-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> class properties</span></span>|<span data-ttu-id="e3940-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType>類屬性</span><span class="sxs-lookup"><span data-stu-id="e3940-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> class properties</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="e3940-110">如果使用物件定義工具提示的內容，則可以使用任一類的屬性<xref:System.Windows.Controls.ToolTip>;如果使用物件定義工具提示的內容，則可以使用任一類的屬性。但是，<xref:System.Windows.Controls.ToolTipService>屬性優先。</span><span class="sxs-lookup"><span data-stu-id="e3940-110">If you define the contents of a tooltip by using a <xref:System.Windows.Controls.ToolTip> object, you can use the properties of either class; however, the <xref:System.Windows.Controls.ToolTipService> properties take precedence.</span></span> <span data-ttu-id="e3940-111">對未<xref:System.Windows.Controls.ToolTipService>定義為<xref:System.Windows.Controls.ToolTip>物件的工具提示使用屬性。</span><span class="sxs-lookup"><span data-stu-id="e3940-111">Use the <xref:System.Windows.Controls.ToolTipService> properties for tooltips that are not defined as <xref:System.Windows.Controls.ToolTip> objects.</span></span>  
  
 <span data-ttu-id="e3940-112">下圖顯示了如何使用這些屬性定位工具提示。</span><span class="sxs-lookup"><span data-stu-id="e3940-112">The following illustrations show how to position a tooltip by using these properties.</span></span> <span data-ttu-id="e3940-113">儘管這些插圖[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中的示例演示如何設置由<xref:System.Windows.Controls.ToolTip>類定義的屬性，但類的<xref:System.Windows.Controls.ToolTipService>相應屬性遵循相同的佈局規則。</span><span class="sxs-lookup"><span data-stu-id="e3940-113">Although, the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples in these illustrations show how to set the properties that are defined by the <xref:System.Windows.Controls.ToolTip> class, the corresponding properties of the <xref:System.Windows.Controls.ToolTipService> class follow the same layout rules.</span></span> <span data-ttu-id="e3940-114">有關放置屬性的可能值的詳細資訊，請參閱[彈出放置行為](popup-placement-behavior.md)。</span><span class="sxs-lookup"><span data-stu-id="e3940-114">For more information about the possible values for the Placement property, see [Popup Placement Behavior](popup-placement-behavior.md).</span></span>  

 <span data-ttu-id="e3940-115">下圖顯示了使用"放置"屬性的工具提示放置：</span><span class="sxs-lookup"><span data-stu-id="e3940-115">The following image shows tooltip placement by using the Placement property:</span></span>  
  
 ![使用放置屬性顯示工具提示放置的圖表。](./media/how-to-position-a-tooltip/tooltip-placement-property.png)

 <span data-ttu-id="e3940-117">下圖使用"放置"和"放置矩形"屬性顯示工具提示放置：</span><span class="sxs-lookup"><span data-stu-id="e3940-117">The following image shows tooltip placement by using the Placement and PlacementRectangle properties:</span></span>

 ![使用放置矩形屬性顯示工具提示放置位置的圖表。](./media/how-to-position-a-tooltip/tooltip-placement-rectangle-property.png)  

 <span data-ttu-id="e3940-119">下圖使用"放置"、放置矩形和偏移屬性顯示工具提示放置：</span><span class="sxs-lookup"><span data-stu-id="e3940-119">The following image shows tooltip placement by using the Placement, PlacementRectangle, and Offset properties:</span></span>
  
 ![使用"偏移"屬性顯示工具提示放置位置的圖表。](./media/how-to-position-a-tooltip/tooltip-placement-offset-property.png)

 <span data-ttu-id="e3940-121">下面的示例演示如何使用<xref:System.Windows.Controls.ToolTip>屬性來指定其內容為<xref:System.Windows.Controls.ToolTip>物件的工具提示的位置。</span><span class="sxs-lookup"><span data-stu-id="e3940-121">The following example shows how to use the <xref:System.Windows.Controls.ToolTip> properties to specify the position of a tooltip whose content is a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 <span data-ttu-id="e3940-122">下面的示例演示如何使用<xref:System.Windows.Controls.ToolTipService>屬性來指定其內容不是<xref:System.Windows.Controls.ToolTip>物件的工具提示的位置。</span><span class="sxs-lookup"><span data-stu-id="e3940-122">The following example shows how to use the <xref:System.Windows.Controls.ToolTipService> properties to specify the position of a tooltip whose content is not a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a><span data-ttu-id="e3940-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3940-123">See also</span></span>

- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [<span data-ttu-id="e3940-124">如何使用主題</span><span class="sxs-lookup"><span data-stu-id="e3940-124">How-to Topics</span></span>](tooltip-how-to-topics.md)
- [<span data-ttu-id="e3940-125">工具提示概觀</span><span class="sxs-lookup"><span data-stu-id="e3940-125">ToolTip Overview</span></span>](tooltip-overview.md)
