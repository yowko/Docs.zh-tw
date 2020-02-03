---
title: TrackBar 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- TrackBar
helpviewer_keywords:
- sliders [Windows Forms], about sliders
- TrackBar control [Windows Forms], about TrackBar control
- slider controls [Windows Forms], about slider controls
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
ms.openlocfilehash: 6901405100df4633c84850757f55b756bc9a0199
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741463"
---
# <a name="trackbar-control-overview-windows-forms"></a><span data-ttu-id="67625-102">TrackBar 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="67625-102">TrackBar Control Overview (Windows Forms)</span></span>
<span data-ttu-id="67625-103">Windows Forms <xref:System.Windows.Forms.TrackBar> 控制項（有時也稱為「滑杆」控制項）是用來流覽大量資訊，或用來以視覺方式調整數值設定。</span><span class="sxs-lookup"><span data-stu-id="67625-103">The Windows Forms <xref:System.Windows.Forms.TrackBar> control (also sometimes called a "slider" control) is used for navigating through a large amount of information or for visually adjusting a numeric setting.</span></span> <span data-ttu-id="67625-104"><xref:System.Windows.Forms.TrackBar> 控制項有兩個部分： thumb （也稱為滑杆）和刻度標記。</span><span class="sxs-lookup"><span data-stu-id="67625-104">The <xref:System.Windows.Forms.TrackBar> control has two parts: the thumb, also known as a slider, and the tick marks.</span></span> <span data-ttu-id="67625-105">捲動方塊是可以調整的部分。</span><span class="sxs-lookup"><span data-stu-id="67625-105">The thumb is the part that can be adjusted.</span></span> <span data-ttu-id="67625-106">其位置會對應至 <xref:System.Windows.Forms.TrackBar.Value%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="67625-106">Its position corresponds to the <xref:System.Windows.Forms.TrackBar.Value%2A> property.</span></span> <span data-ttu-id="67625-107">刻度是以固定間隔分隔的視覺指示器。</span><span class="sxs-lookup"><span data-stu-id="67625-107">The tick marks are visual indicators that are spaced at regular intervals.</span></span> <span data-ttu-id="67625-108">並排會以您指定的增量移動，而且可以水準或垂直對齊。</span><span class="sxs-lookup"><span data-stu-id="67625-108">The trackbar moves in increments that you specify and can be aligned horizontally or vertically.</span></span> <span data-ttu-id="67625-109">例如，您可以使用追蹤列來控制系統的游標閃爍頻率或滑鼠速度。</span><span class="sxs-lookup"><span data-stu-id="67625-109">For example, you might use the track bar to control the cursor blink rate or mouse speed for a system.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="67625-110">索引鍵內容</span><span class="sxs-lookup"><span data-stu-id="67625-110">Key Properties</span></span>  
 <span data-ttu-id="67625-111"><xref:System.Windows.Forms.TrackBar> 控制項的索引鍵屬性是 <xref:System.Windows.Forms.TrackBar.Value%2A>、<xref:System.Windows.Forms.TrackBar.TickFrequency%2A>、<xref:System.Windows.Forms.TrackBar.Minimum%2A>和 <xref:System.Windows.Forms.TrackBar.Maximum%2A>。</span><span class="sxs-lookup"><span data-stu-id="67625-111">The key properties of the <xref:System.Windows.Forms.TrackBar> control are <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A>, and <xref:System.Windows.Forms.TrackBar.Maximum%2A>.</span></span> <span data-ttu-id="67625-112"><xref:System.Windows.Forms.TrackBar.TickFrequency%2A> 是刻度的間距。</span><span class="sxs-lookup"><span data-stu-id="67625-112"><xref:System.Windows.Forms.TrackBar.TickFrequency%2A> is the spacing of the ticks.</span></span> <span data-ttu-id="67625-113"><xref:System.Windows.Forms.TrackBar.Minimum%2A> 和 <xref:System.Windows.Forms.TrackBar.Maximum%2A> 是可在追蹤列上表示的最小和最大值。</span><span class="sxs-lookup"><span data-stu-id="67625-113"><xref:System.Windows.Forms.TrackBar.Minimum%2A> and <xref:System.Windows.Forms.TrackBar.Maximum%2A> are the smallest and largest values that can be represented on the track bar.</span></span>  
  
 <span data-ttu-id="67625-114">另外還有兩個重要的屬性 <xref:System.Windows.Forms.TrackBar.SmallChange%2A> 和 <xref:System.Windows.Forms.TrackBar.LargeChange%2A>。</span><span class="sxs-lookup"><span data-stu-id="67625-114">Two other important properties are <xref:System.Windows.Forms.TrackBar.SmallChange%2A> and <xref:System.Windows.Forms.TrackBar.LargeChange%2A>.</span></span> <span data-ttu-id="67625-115"><xref:System.Windows.Forms.TrackBar.SmallChange%2A> 屬性的值是捲動方塊的位置數目，以回應按下向左鍵或向右鍵。</span><span class="sxs-lookup"><span data-stu-id="67625-115">The value of the <xref:System.Windows.Forms.TrackBar.SmallChange%2A> property is the number of positions the thumb moves in response to having the LEFT or RIGHT ARROW key pressed.</span></span> <span data-ttu-id="67625-116">[<xref:System.Windows.Forms.TrackBar.LargeChange%2A>] 屬性的值是捲動方塊的位置數，以回應按下 PAGE UP 或 PAGE DOWN 鍵，或在捲軸兩側的追蹤列上按一下滑鼠右鍵。</span><span class="sxs-lookup"><span data-stu-id="67625-116">The value of the <xref:System.Windows.Forms.TrackBar.LargeChange%2A> property is the number of positions the thumb moves in response to having the PAGE UP or PAGE DOWN key pressed, or in response to mouse clicks on the track bar on either side of the thumb.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67625-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67625-117">See also</span></span>

- <xref:System.Windows.Forms.TrackBar>
- [<span data-ttu-id="67625-118">TrackBar 控制項</span><span class="sxs-lookup"><span data-stu-id="67625-118">TrackBar Control</span></span>](trackbar-control-windows-forms.md)
