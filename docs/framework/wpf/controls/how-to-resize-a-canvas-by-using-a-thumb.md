---
title: HOW TO：使用指標調整畫布大小
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
ms.openlocfilehash: 14942157429b029147d47e2f88428c56e66523d1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146350"
---
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a><span data-ttu-id="1e32a-102">HOW TO：使用指標調整畫布大小</span><span class="sxs-lookup"><span data-stu-id="1e32a-102">How to: Resize a Canvas by Using a Thumb</span></span>
<span data-ttu-id="1e32a-103">此範例示範如何使用<xref:System.Windows.Controls.Primitives.Thumb>控制項調整大小<xref:System.Windows.Controls.Canvas>控制項。</span><span class="sxs-lookup"><span data-stu-id="1e32a-103">This example shows how to use a <xref:System.Windows.Controls.Primitives.Thumb> control to resize a <xref:System.Windows.Controls.Canvas> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e32a-104">範例</span><span class="sxs-lookup"><span data-stu-id="1e32a-104">Example</span></span>  
 <span data-ttu-id="1e32a-105"><xref:System.Windows.Controls.Primitives.Thumb>控制項提供拖放功能，可用來移動或調整控制項大小藉由監視<xref:System.Windows.Controls.Primitives.Thumb.DragStarted>，<xref:System.Windows.Controls.Primitives.Thumb.DragDelta>並<xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>事件<xref:System.Windows.Controls.Primitives.Thumb>。</span><span class="sxs-lookup"><span data-stu-id="1e32a-105">The <xref:System.Windows.Controls.Primitives.Thumb> control provides drag functionality that can be used to move or resize controls by monitoring the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> and <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> events of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 <span data-ttu-id="1e32a-106">使用者開始拖曳作業上暫停滑鼠指標時，請按下滑鼠左的按鈕<xref:System.Windows.Controls.Primitives.Thumb>控制項。</span><span class="sxs-lookup"><span data-stu-id="1e32a-106">The user begins a drag operation by pressing the left mouse button when the mouse pointer is paused on the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="1e32a-107">只要滑鼠左的按鈕已按下，將會繼續拖曳作業。</span><span class="sxs-lookup"><span data-stu-id="1e32a-107">The drag operation continues as long as the left mouse button remains pressed.</span></span> <span data-ttu-id="1e32a-108">拖曳作業期間，<xref:System.Windows.Controls.Primitives.Thumb.DragDelta>可以出現一次以上。</span><span class="sxs-lookup"><span data-stu-id="1e32a-108">During the drag operation, the <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> can occur more than once.</span></span> <span data-ttu-id="1e32a-109">每次它發生時，<xref:System.Windows.Controls.Primitives.DragDeltaEventArgs>類別提供的滑鼠位置中的變更對應的位置變更。</span><span class="sxs-lookup"><span data-stu-id="1e32a-109">Each time it occurs, the <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> class provides the change in position that corresponds to the change in mouse position.</span></span> <span data-ttu-id="1e32a-110">當使用者放開滑鼠左的按鈕時，已完成拖曳作業。</span><span class="sxs-lookup"><span data-stu-id="1e32a-110">When the user releases the left mouse button, the drag operation is finished.</span></span> <span data-ttu-id="1e32a-111">在拖曳作業只會提供新的座標。它不會不會自動重新定位<xref:System.Windows.Controls.Primitives.Thumb>。</span><span class="sxs-lookup"><span data-stu-id="1e32a-111">The drag operation only provides new coordinates; it does not automatically reposition the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 <span data-ttu-id="1e32a-112">下列範例所示<xref:System.Windows.Controls.Primitives.Thumb>控制項的子項目<xref:System.Windows.Controls.Canvas>控制項。</span><span class="sxs-lookup"><span data-stu-id="1e32a-112">The following example shows a <xref:System.Windows.Controls.Primitives.Thumb> control that is the child element of a <xref:System.Windows.Controls.Canvas> control.</span></span> <span data-ttu-id="1e32a-113">事件處理常式，如其<xref:System.Windows.Controls.Primitives.Thumb.DragDelta>事件會提供邏輯來移動<xref:System.Windows.Controls.Primitives.Thumb>並調整大小<xref:System.Windows.Controls.Canvas>。</span><span class="sxs-lookup"><span data-stu-id="1e32a-113">The event handler for its <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> event provides the logic to move the <xref:System.Windows.Controls.Primitives.Thumb> and resize the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="1e32a-114">事件處理常式<xref:System.Windows.Controls.Primitives.Thumb.DragStarted>並<xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>事件變更的色彩<xref:System.Windows.Controls.Primitives.Thumb>在拖曳作業期間。</span><span class="sxs-lookup"><span data-stu-id="1e32a-114">The event handlers for the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> and <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> event change the color of the <xref:System.Windows.Controls.Primitives.Thumb> during a drag operation.</span></span> <span data-ttu-id="1e32a-115">下列範例會定義<xref:System.Windows.Controls.Primitives.Thumb>。</span><span class="sxs-lookup"><span data-stu-id="1e32a-115">The following example defines the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 [!code-xaml[Thumb#thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 <span data-ttu-id="1e32a-116">下列範例所示<xref:System.Windows.Controls.Primitives.Thumb.DragDelta>，它會將事件處理常式<xref:System.Windows.Controls.Primitives.Thumb>並調整大小<xref:System.Windows.Controls.Canvas>以回應滑鼠移動。</span><span class="sxs-lookup"><span data-stu-id="1e32a-116">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> event handler that moves the <xref:System.Windows.Controls.Primitives.Thumb> and resizes the <xref:System.Windows.Controls.Canvas> in response to a mouse movement.</span></span>  
  
 [!code-csharp[Thumb#2](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 <span data-ttu-id="1e32a-117">下列範例所示<xref:System.Windows.Controls.Primitives.Thumb.DragStarted>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1e32a-117">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> event handler.</span></span>  
  
 [!code-csharp[Thumb#DragStartedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 <span data-ttu-id="1e32a-118">下列範例所示<xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1e32a-118">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> event handler.</span></span>  
  
 [!code-csharp[Thumb#DragCompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 <span data-ttu-id="1e32a-119">如需完整的範例，請參閱[捲動方塊拖放功能範例](https://go.microsoft.com/fwlink/?LinkID=160042)。</span><span class="sxs-lookup"><span data-stu-id="1e32a-119">For the complete sample, see [Thumb Drag Functionality Sample](https://go.microsoft.com/fwlink/?LinkID=160042).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e32a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e32a-120">See also</span></span>

- <xref:System.Windows.Controls.Primitives.Thumb>
- <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>
- <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>
- <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
