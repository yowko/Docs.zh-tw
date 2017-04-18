---
title: "如何：定義畫筆 | Microsoft Docs"
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
  - "建立, 畫筆"
  - "畫筆, 定義"
ms.assetid: 7a4f2900-cdf9-49de-84e0-ba5d0ded4d33
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 2
---
# 如何：定義畫筆
本範例示範如何使用 <xref:System.Windows.Media.Pen> 來繪製圖案的外框。  若要建立簡單的 <xref:System.Windows.Media.Pen>，您只需要指定其 <xref:System.Windows.Media.Pen.Thickness%2A> 和 <xref:System.Windows.Media.Pen.Brush%2A>。  您可以透過指定 <xref:System.Windows.Media.Pen.DashStyle%2A>、<xref:System.Windows.Media.Pen.DashCap%2A>、<xref:System.Windows.Media.Pen.LineJoin%2A>、<xref:System.Windows.Media.Pen.StartLineCap%2A> 和 <xref:System.Windows.Media.Pen.EndLineCap%2A>，建立較複雜的畫筆。  
  
## 範例  
 下列範例使用 <xref:System.Windows.Media.Pen>，為 <xref:System.Windows.Media.GeometryDrawing> 定義的圖案繪製外框。  
  
 [!code-csharp[PenExamples_snip#PenExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PenExamples_snip/CSharp/PenExample.cs#penexamplewholepage)]
 [!code-vb[PenExamples_snip#PenExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PenExamples_snip/VisualBasic/PenExample.vb#penexamplewholepage)]  
  
 ![由 Pen 所描繪的外框](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple-pen.png "graphicsmm\_simple\_pen")  
GeometryDrawing