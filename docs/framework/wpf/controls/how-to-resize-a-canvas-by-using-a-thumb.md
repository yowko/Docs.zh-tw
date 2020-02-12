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
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a>如何：使用縮圖調整畫布大小
這個範例示範如何使用 <xref:System.Windows.Controls.Primitives.Thumb> 控制項來調整 <xref:System.Windows.Controls.Canvas> 控制項的大小。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Controls.Primitives.Thumb> 控制項提供的拖曳功能，可以用來透過監視 <xref:System.Windows.Controls.Primitives.Thumb>的 <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>、<xref:System.Windows.Controls.Primitives.Thumb.DragDelta> 和 <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> 事件來移動控制項或調整其大小。  
  
 當滑鼠指標停留在 <xref:System.Windows.Controls.Primitives.Thumb> 控制項上時，使用者可以按下滑鼠左鍵，開始拖曳作業。 只要滑鼠左鍵保持按下，拖曳作業就會繼續。 在拖曳作業期間，<xref:System.Windows.Controls.Primitives.Thumb.DragDelta> 可能會發生一次以上。 每次發生這種情況時，<xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> 類別都會提供相對於滑鼠位置變更的位置變更。 當使用者放開滑鼠左鍵時，拖曳作業就會完成。 拖曳作業只會提供新的座標。它不會自動重新置放 <xref:System.Windows.Controls.Primitives.Thumb>。  
  
 下列範例顯示 <xref:System.Windows.Controls.Primitives.Thumb> 控制項，這是 <xref:System.Windows.Controls.Canvas> 控制項的子項目。 其 <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> 事件的事件處理常式會提供移動 <xref:System.Windows.Controls.Primitives.Thumb> 和調整 <xref:System.Windows.Controls.Canvas>大小的邏輯。 <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> 和 <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> 事件的事件處理常式會在拖曳作業期間變更 <xref:System.Windows.Controls.Primitives.Thumb> 的色彩。 下列範例會定義 <xref:System.Windows.Controls.Primitives.Thumb>。  
  
 [!code-xaml[Thumb#thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 下列範例會顯示移動 <xref:System.Windows.Controls.Primitives.Thumb> 的 <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> 事件處理常式，並調整 <xref:System.Windows.Controls.Canvas> 以回應滑鼠移動。  
  
 [!code-csharp[Thumb#2](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 下列範例會顯示 <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> 事件處理常式。  
  
 [!code-csharp[Thumb#DragStartedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 下列範例會顯示 <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> 事件處理常式。  
  
 [!code-csharp[Thumb#DragCompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 如需完整範例，請參閱[捲動方塊功能範例](https://github.com/Microsoft/WPF-Samples/tree/master/Drag%20and%20Drop/DragDropThumbOps)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.Primitives.Thumb>
- <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>
- <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>
- <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
