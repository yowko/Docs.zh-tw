---
title: "如何：建立和使用 Canvas | Microsoft Docs"
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
  - "Canvas 控制項, 建立"
  - "Canvas 控制項, 使用"
  - "控制項, Canvas"
ms.assetid: 420b9487-9a15-477c-9489-a22a4dec7779
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：建立和使用 Canvas
本範例示範如何建立和使用 <xref:System.Windows.Controls.Canvas> 的執行個體。  
  
## 範例  
 下列範例使用 <xref:System.Windows.Controls.Canvas> 的 <xref:System.Windows.Controls.Canvas.SetTop%2A> 和 <xref:System.Windows.Controls.Canvas.SetLeft%2A> 方法，明確放置兩個 <xref:System.Windows.Controls.TextBlock> 項目。  此範例也會將 `LightSteelBlue` 的 <xref:System.Windows.Controls.Control.Background%2A> 色彩指派給 <xref:System.Windows.Controls.Canvas>。  
  
> [!NOTE]
>  當您使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 放置 <xref:System.Windows.Controls.TextBlock> 項目時，請使用 <xref:System.Windows.Controls.Canvas.Top%2A> 和 <xref:System.Windows.Controls.Canvas.Left%2A> 屬性。  
  
 [!code-csharp[CanvasCode#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasCode/CSharp/Canvas_Code.cs#1)]
 [!code-vb[CanvasCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasCode/VisualBasic/canvas_vb.vb#1)]  
  
## 請參閱  
 <xref:System.Windows.Controls.Canvas>   
 <xref:System.Windows.Controls.TextBlock>   
 <xref:System.Windows.Controls.Canvas.SetTop%2A>   
 <xref:System.Windows.Controls.Canvas.SetLeft%2A>   
 <xref:System.Windows.Controls.Canvas.Top%2A>   
 <xref:System.Windows.Controls.Canvas.Left%2A>   
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/controls/canvas-how-to-topics.md)