---
title: 如何：使用縮圖調整畫布大小
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resizing Canvas control [WPF]
- controls [WPF], Thumb
- controls [WPF], Canvas
- Thumb control [WPF]
- Canvas control [WPF]
ms.assetid: 7dc9f435-726c-4d4d-be41-eb24cfe17bef
ms.openlocfilehash: 84f5ac2b53124b7f4d7c15741e94b40e7ee81526
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124295"
---
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a><span data-ttu-id="f6e71-102">如何：使用縮圖調整畫布大小</span><span class="sxs-lookup"><span data-stu-id="f6e71-102">How to: Resize a Canvas by Using a Thumb</span></span>
<span data-ttu-id="f6e71-103">這個範例示範如何使用 <xref:System.Windows.Controls.Primitives.Thumb> 控制項來調整 <xref:System.Windows.Controls.Canvas> 控制項的大小。</span><span class="sxs-lookup"><span data-stu-id="f6e71-103">This example shows how to use a <xref:System.Windows.Controls.Primitives.Thumb> control to resize a <xref:System.Windows.Controls.Canvas> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6e71-104">範例</span><span class="sxs-lookup"><span data-stu-id="f6e71-104">Example</span></span>  
 <span data-ttu-id="f6e71-105"><xref:System.Windows.Controls.Primitives.Thumb> 控制項提供的拖曳功能，可以用來透過監視 <xref:System.Windows.Controls.Primitives.Thumb>的 <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>、<xref:System.Windows.Controls.Primitives.Thumb.DragDelta> 和 <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> 事件來移動控制項或調整其大小。</span><span class="sxs-lookup"><span data-stu-id="f6e71-105">The <xref:System.Windows.Controls.Primitives.Thumb> control provides drag functionality that can be used to move or resize controls by monitoring the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> and <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> events of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 <span data-ttu-id="f6e71-106">當滑鼠指標停留在 <xref:System.Windows.Controls.Primitives.Thumb> 控制項上時，使用者可以按下滑鼠左鍵，開始拖曳作業。</span><span class="sxs-lookup"><span data-stu-id="f6e71-106">The user begins a drag operation by pressing the left mouse button when the mouse pointer is paused on the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="f6e71-107">只要滑鼠左鍵保持按下，拖曳作業就會繼續。</span><span class="sxs-lookup"><span data-stu-id="f6e71-107">The drag operation continues as long as the left mouse button remains pressed.</span></span> <span data-ttu-id="f6e71-108">在拖曳作業期間，<xref:System.Windows.Controls.Primitives.Thumb.DragDelta> 可能會發生一次以上。</span><span class="sxs-lookup"><span data-stu-id="f6e71-108">During the drag operation, the <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> can occur more than once.</span></span> <span data-ttu-id="f6e71-109">每次發生這種情況時，<xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> 類別都會提供相對於滑鼠位置變更的位置變更。</span><span class="sxs-lookup"><span data-stu-id="f6e71-109">Each time it occurs, the <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> class provides the change in position that corresponds to the change in mouse position.</span></span> <span data-ttu-id="f6e71-110">當使用者放開滑鼠左鍵時，拖曳作業就會完成。</span><span class="sxs-lookup"><span data-stu-id="f6e71-110">When the user releases the left mouse button, the drag operation is finished.</span></span> <span data-ttu-id="f6e71-111">拖曳作業只會提供新的座標。它不會自動重新置放 <xref:System.Windows.Controls.Primitives.Thumb>。</span><span class="sxs-lookup"><span data-stu-id="f6e71-111">The drag operation only provides new coordinates; it does not automatically reposition the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 <span data-ttu-id="f6e71-112">下列範例顯示 <xref:System.Windows.Controls.Primitives.Thumb> 控制項，這是 <xref:System.Windows.Controls.Canvas> 控制項的子項目。</span><span class="sxs-lookup"><span data-stu-id="f6e71-112">The following example shows a <xref:System.Windows.Controls.Primitives.Thumb> control that is the child element of a <xref:System.Windows.Controls.Canvas> control.</span></span> <span data-ttu-id="f6e71-113">其 <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> 事件的事件處理常式會提供移動 <xref:System.Windows.Controls.Primitives.Thumb> 和調整 <xref:System.Windows.Controls.Canvas>大小的邏輯。</span><span class="sxs-lookup"><span data-stu-id="f6e71-113">The event handler for its <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> event provides the logic to move the <xref:System.Windows.Controls.Primitives.Thumb> and resize the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="f6e71-114"><xref:System.Windows.Controls.Primitives.Thumb.DragStarted> 和 <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> 事件的事件處理常式會在拖曳作業期間變更 <xref:System.Windows.Controls.Primitives.Thumb> 的色彩。</span><span class="sxs-lookup"><span data-stu-id="f6e71-114">The event handlers for the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> and <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> event change the color of the <xref:System.Windows.Controls.Primitives.Thumb> during a drag operation.</span></span> <span data-ttu-id="f6e71-115">下列範例會定義 <xref:System.Windows.Controls.Primitives.Thumb>。</span><span class="sxs-lookup"><span data-stu-id="f6e71-115">The following example defines the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 [!code-xaml[Thumb#thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 <span data-ttu-id="f6e71-116">下列範例會顯示移動 <xref:System.Windows.Controls.Primitives.Thumb> 的 <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> 事件處理常式，並調整 <xref:System.Windows.Controls.Canvas> 以回應滑鼠移動。</span><span class="sxs-lookup"><span data-stu-id="f6e71-116">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> event handler that moves the <xref:System.Windows.Controls.Primitives.Thumb> and resizes the <xref:System.Windows.Controls.Canvas> in response to a mouse movement.</span></span>  
  
 [!code-csharp[Thumb#2](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 <span data-ttu-id="f6e71-117">下列範例會顯示 <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="f6e71-117">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> event handler.</span></span>  
  
 [!code-csharp[Thumb#DragStartedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 <span data-ttu-id="f6e71-118">下列範例會顯示 <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="f6e71-118">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> event handler.</span></span>  
  
 [!code-csharp[Thumb#DragCompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 <span data-ttu-id="f6e71-119">如需完整範例，請參閱[捲動方塊功能範例](https://github.com/Microsoft/WPF-Samples/tree/master/Drag%20and%20Drop/DragDropThumbOps)。</span><span class="sxs-lookup"><span data-stu-id="f6e71-119">For the complete sample, see [Thumb Drag Functionality Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Drag%20and%20Drop/DragDropThumbOps).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6e71-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6e71-120">See also</span></span>

- <xref:System.Windows.Controls.Primitives.Thumb>
- <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>
- <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>
- <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
