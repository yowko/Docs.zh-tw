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
ms.openlocfilehash: be267e832180b49686079f426dfa5c30ffdd81b0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518059"
---
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a>如何：使用縮圖調整畫布大小
此範例示範如何使用<xref:System.Windows.Controls.Primitives.Thumb>控制項調整大小<xref:System.Windows.Controls.Canvas>控制項。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Controls.Primitives.Thumb>控制項提供拖放功能，可用來移動或調整控制項大小藉由監視<xref:System.Windows.Controls.Primitives.Thumb.DragStarted>，<xref:System.Windows.Controls.Primitives.Thumb.DragDelta>並<xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>事件<xref:System.Windows.Controls.Primitives.Thumb>。  
  
 使用者開始拖曳作業上暫停滑鼠指標時，請按下滑鼠左的按鈕<xref:System.Windows.Controls.Primitives.Thumb>控制項。 只要滑鼠左的按鈕已按下，將會繼續拖曳作業。 拖曳作業期間，<xref:System.Windows.Controls.Primitives.Thumb.DragDelta>可以出現一次以上。 每次它發生時，<xref:System.Windows.Controls.Primitives.DragDeltaEventArgs>類別提供的滑鼠位置中的變更對應的位置變更。 當使用者放開滑鼠左的按鈕時，已完成拖曳作業。 在拖曳作業只會提供新的座標。它不會不會自動重新定位<xref:System.Windows.Controls.Primitives.Thumb>。  
  
 下列範例所示<xref:System.Windows.Controls.Primitives.Thumb>控制項的子項目<xref:System.Windows.Controls.Canvas>控制項。 事件處理常式，如其<xref:System.Windows.Controls.Primitives.Thumb.DragDelta>事件會提供邏輯來移動<xref:System.Windows.Controls.Primitives.Thumb>並調整大小<xref:System.Windows.Controls.Canvas>。 事件處理常式<xref:System.Windows.Controls.Primitives.Thumb.DragStarted>並<xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>事件變更的色彩<xref:System.Windows.Controls.Primitives.Thumb>在拖曳作業期間。 下列範例會定義<xref:System.Windows.Controls.Primitives.Thumb>。  
  
 [!code-xaml[Thumb#thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 下列範例所示<xref:System.Windows.Controls.Primitives.Thumb.DragDelta>，它會將事件處理常式<xref:System.Windows.Controls.Primitives.Thumb>並調整大小<xref:System.Windows.Controls.Canvas>以回應滑鼠移動。  
  
 [!code-csharp[Thumb#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 下列範例所示<xref:System.Windows.Controls.Primitives.Thumb.DragStarted>事件處理常式。  
  
 [!code-csharp[Thumb#DragStartedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 下列範例所示<xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>事件處理常式。  
  
 [!code-csharp[Thumb#DragCompletedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 如需完整的範例，請參閱[捲動方塊拖放功能範例](https://go.microsoft.com/fwlink/?LinkID=160042)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.Primitives.Thumb>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
