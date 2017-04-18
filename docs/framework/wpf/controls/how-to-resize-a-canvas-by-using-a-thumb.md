---
title: "如何：使用縮圖調整畫布大小 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Canvas 控制項"
  - "控制項, Canvas"
  - "控制項, Thumb"
  - "調整 Canvas 控制項大小"
  - "Thumb 控制項"
ms.assetid: 7dc9f435-726c-4d4d-be41-eb24cfe17bef
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：使用縮圖調整畫布大小
本範例說明如何使用 <xref:System.Windows.Controls.Primitives.Thumb> 控制項調整 <xref:System.Windows.Controls.Canvas> 控制項的大小。  
  
## 範例  
 <xref:System.Windows.Controls.Primitives.Thumb> 控制項提供拖曳功能，可藉由監視 <xref:System.Windows.Controls.Primitives.Thumb> 的 <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>、<xref:System.Windows.Controls.Primitives.Thumb.DragDelta> 和 <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> 事件，用來移動或調整控制項的大小。  
  
 使用者會在滑鼠指標暫停在 <xref:System.Windows.Controls.Primitives.Thumb> 控制項上時按滑鼠左鍵，開始拖曳作業。  拖曳作業會持續到使用者放開滑鼠左鍵為止。  在拖曳作業期間，<xref:System.Windows.Controls.Primitives.Thumb.DragDelta> 可能會發生一次以上。  每次發生時，<xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> 類別會提供對應於滑鼠位置變更的位置變更。  當使用這放開滑鼠左鍵時，拖曳作業便完成。  拖曳作業只提供新座標，並不會自動調整 <xref:System.Windows.Controls.Primitives.Thumb> 的位置。  
  
 下列範例會顯示 <xref:System.Windows.Controls.Primitives.Thumb> 控制項，這是 <xref:System.Windows.Controls.Canvas> 控制項的子項目。  其 <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> 事件的事件處理常式會提供移動 <xref:System.Windows.Controls.Primitives.Thumb> 和調整 <xref:System.Windows.Controls.Canvas> 大小的邏輯。  <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> 和 <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> 事件的事件處理常式則會在拖曳作業期間變更 <xref:System.Windows.Controls.Primitives.Thumb> 的色彩。  下列範例會定義 <xref:System.Windows.Controls.Primitives.Thumb>。  
  
 [!code-xml[Thumb#thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 下列範例會示範 <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> 事件處理常式如何回應滑鼠移動，移動 <xref:System.Windows.Controls.Primitives.Thumb> 並調整 <xref:System.Windows.Controls.Canvas> 的大小。  
  
 [!code-csharp[Thumb#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 下列範例顯示 <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> 事件處理常式。  
  
 [!code-csharp[Thumb#DragStartedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 下列範例顯示 <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> 事件處理常式。  
  
 [!code-csharp[Thumb#DragCompletedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 如需完整範例，請參閱[縮圖拖曳功能範例](http://go.microsoft.com/fwlink/?LinkID=160042) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Controls.Primitives.Thumb>   
 <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>   
 <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>   
 <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>