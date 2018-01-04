---
title: "TrackBar 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: TrackBar
helpviewer_keywords:
- sliders [Windows Forms], about sliders
- TrackBar control [Windows Forms], about TrackBar control
- slider controls [Windows Forms], about slider controls
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e62fc49a8a08c79138df080246b99b6fe891162e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="trackbar-control-overview-windows-forms"></a><span data-ttu-id="98efa-102">TrackBar 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="98efa-102">TrackBar Control Overview (Windows Forms)</span></span>
<span data-ttu-id="98efa-103">Windows Form<xref:System.Windows.Forms.TrackBar>控制項 （有時也稱為 「 滑桿 」 控制項） 用來瀏覽大量的資訊或以視覺方式調整數字設定。</span><span class="sxs-lookup"><span data-stu-id="98efa-103">The Windows Forms <xref:System.Windows.Forms.TrackBar> control (also sometimes called a "slider" control) is used for navigating through a large amount of information or for visually adjusting a numeric setting.</span></span> <span data-ttu-id="98efa-104"><xref:System.Windows.Forms.TrackBar>控制項有兩個部分： 也稱為滑桿，與刻度標記縮圖。</span><span class="sxs-lookup"><span data-stu-id="98efa-104">The <xref:System.Windows.Forms.TrackBar> control has two parts: the thumb, also known as a slider, and the tick marks.</span></span> <span data-ttu-id="98efa-105">基本原則是可調整的部分。</span><span class="sxs-lookup"><span data-stu-id="98efa-105">The thumb is the part that can be adjusted.</span></span> <span data-ttu-id="98efa-106">它的位置對應至<xref:System.Windows.Forms.TrackBar.Value%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="98efa-106">Its position corresponds to the <xref:System.Windows.Forms.TrackBar.Value%2A> property.</span></span> <span data-ttu-id="98efa-107">刻度是定期為間距的視覺指標。</span><span class="sxs-lookup"><span data-stu-id="98efa-107">The tick marks are visual indicators that are spaced at regular intervals.</span></span> <span data-ttu-id="98efa-108">Trackbar 移動您指定和可以對齊水平或垂直增量。</span><span class="sxs-lookup"><span data-stu-id="98efa-108">The trackbar moves in increments that you specify and can be aligned horizontally or vertically.</span></span> <span data-ttu-id="98efa-109">例如，您可能會使用追蹤列來控制系統游標閃爍頻率或滑鼠速度。</span><span class="sxs-lookup"><span data-stu-id="98efa-109">For example, you might use the track bar to control the cursor blink rate or mouse speed for a system.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="98efa-110">索引鍵內容</span><span class="sxs-lookup"><span data-stu-id="98efa-110">Key Properties</span></span>  
 <span data-ttu-id="98efa-111">索引鍵屬性<xref:System.Windows.Forms.TrackBar>控制是<xref:System.Windows.Forms.TrackBar.Value%2A>， <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>， <xref:System.Windows.Forms.TrackBar.Minimum%2A>，和<xref:System.Windows.Forms.TrackBar.Maximum%2A>。</span><span class="sxs-lookup"><span data-stu-id="98efa-111">The key properties of the <xref:System.Windows.Forms.TrackBar> control are <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A>, and <xref:System.Windows.Forms.TrackBar.Maximum%2A>.</span></span> <span data-ttu-id="98efa-112"><xref:System.Windows.Forms.TrackBar.TickFrequency%2A>是刻度的間距。</span><span class="sxs-lookup"><span data-stu-id="98efa-112"><xref:System.Windows.Forms.TrackBar.TickFrequency%2A> is the spacing of the ticks.</span></span> <span data-ttu-id="98efa-113"><xref:System.Windows.Forms.TrackBar.Minimum%2A>和<xref:System.Windows.Forms.TrackBar.Maximum%2A>是可以在追蹤列表示的最小和最大值。</span><span class="sxs-lookup"><span data-stu-id="98efa-113"><xref:System.Windows.Forms.TrackBar.Minimum%2A> and <xref:System.Windows.Forms.TrackBar.Maximum%2A> are the smallest and largest values that can be represented on the track bar.</span></span>  
  
 <span data-ttu-id="98efa-114">其他兩個重要的屬性是<xref:System.Windows.Forms.TrackBar.SmallChange%2A>和<xref:System.Windows.Forms.TrackBar.LargeChange%2A>。</span><span class="sxs-lookup"><span data-stu-id="98efa-114">Two other important properties are <xref:System.Windows.Forms.TrackBar.SmallChange%2A> and <xref:System.Windows.Forms.TrackBar.LargeChange%2A>.</span></span> <span data-ttu-id="98efa-115">值<xref:System.Windows.Forms.TrackBar.SmallChange%2A>屬性是回應需要按下的左或向右箭號鍵移動捲動方塊的位置數目。</span><span class="sxs-lookup"><span data-stu-id="98efa-115">The value of the <xref:System.Windows.Forms.TrackBar.SmallChange%2A> property is the number of positions the thumb moves in response to having the LEFT or RIGHT ARROW key pressed.</span></span> <span data-ttu-id="98efa-116">值<xref:System.Windows.Forms.TrackBar.LargeChange%2A>屬性是捲動方塊回應具有 PAGE UP 或 PAGE DOWN 按鍵，移動或以回應滑鼠按一下捲動方塊的任一端追蹤列上的位置數目。</span><span class="sxs-lookup"><span data-stu-id="98efa-116">The value of the <xref:System.Windows.Forms.TrackBar.LargeChange%2A> property is the number of positions the thumb moves in response to having the PAGE UP or PAGE DOWN key pressed, or in response to mouse clicks on the track bar on either side of the thumb.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98efa-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="98efa-117">See Also</span></span>  
 <xref:System.Windows.Forms.TrackBar>  
 [<span data-ttu-id="98efa-118">TrackBar 控制項</span><span class="sxs-lookup"><span data-stu-id="98efa-118">TrackBar Control</span></span>](../../../../docs/framework/winforms/controls/trackbar-control-windows-forms.md)
