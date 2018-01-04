---
title: "如何：使用縮圖調整畫布大小"
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
- resizing Canvas control [WPF]
- controls [WPF], Thumb
- controls [WPF], Canvas
- Thumb control [WPF]
- Canvas control [WPF]
ms.assetid: 7dc9f435-726c-4d4d-be41-eb24cfe17bef
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c73509d58112e47f707e82243005bfdf9edca151
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a>如何：使用縮圖調整畫布大小
這個範例示範如何使用<xref:System.Windows.Controls.Primitives.Thumb>控制項調整大小<xref:System.Windows.Controls.Canvas>控制項。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Controls.Primitives.Thumb>控制項提供可用來移動或調整控制項大小所監視的拖曳功能<xref:System.Windows.Controls.Primitives.Thumb.DragStarted>，<xref:System.Windows.Controls.Primitives.Thumb.DragDelta>和<xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>事件<xref:System.Windows.Controls.Primitives.Thumb>。  
  
 使用者開始拖曳作業時滑鼠指標暫停在按下滑鼠左的按鈕<xref:System.Windows.Controls.Primitives.Thumb>控制項。 只要滑鼠左鍵按下的按鍵，則會繼續拖曳作業。 拖曳作業期間，<xref:System.Windows.Controls.Primitives.Thumb.DragDelta>可以出現一次以上。 每次它發生時，<xref:System.Windows.Controls.Primitives.DragDeltaEventArgs>類別提供滑鼠位置中的變更對應的位置中的變更。 當使用者放開滑鼠左的按鈕時，已完成拖曳作業。 在拖曳作業只會提供新的座標。它不會不會自動重新定位<xref:System.Windows.Controls.Primitives.Thumb>。  
  
 下列範例所示<xref:System.Windows.Controls.Primitives.Thumb>控制項的子元素<xref:System.Windows.Controls.Canvas>控制項。 此事件處理常式，如其<xref:System.Windows.Controls.Primitives.Thumb.DragDelta>事件提供邏輯以移動<xref:System.Windows.Controls.Primitives.Thumb>和調整大小<xref:System.Windows.Controls.Canvas>。 事件處理常式<xref:System.Windows.Controls.Primitives.Thumb.DragStarted>和<xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>事件變更的色彩<xref:System.Windows.Controls.Primitives.Thumb>拖曳作業期間。 下列範例會定義<xref:System.Windows.Controls.Primitives.Thumb>。  
  
 [!code-xaml[Thumb#thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 下列範例所示<xref:System.Windows.Controls.Primitives.Thumb.DragDelta>移動的事件處理常式<xref:System.Windows.Controls.Primitives.Thumb>並調整大小<xref:System.Windows.Controls.Canvas>回應滑鼠移動。  
  
 [!code-csharp[Thumb#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 下列範例所示<xref:System.Windows.Controls.Primitives.Thumb.DragStarted>事件處理常式。  
  
 [!code-csharp[Thumb#DragStartedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 下列範例所示<xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>事件處理常式。  
  
 [!code-csharp[Thumb#DragCompletedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 如需完整範例，請參閱[捲動方塊的拖曳功能範例](http://go.microsoft.com/fwlink/?LinkID=160042)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Controls.Primitives.Thumb>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
