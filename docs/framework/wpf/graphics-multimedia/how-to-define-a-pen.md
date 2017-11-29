---
title: "操作說明：定義畫筆"
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
- pens [WPF], defining
- creating [WPF], pens
ms.assetid: 7a4f2900-cdf9-49de-84e0-ba5d0ded4d33
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c173b895f67164152d5930efc6a385bc480aaa81
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-define-a-pen"></a>操作說明：定義畫筆
這個範例示範如何使用<xref:System.Windows.Media.Pen>概述圖形。 若要建立簡單<xref:System.Windows.Media.Pen>，您只需要指定其<xref:System.Windows.Media.Pen.Thickness%2A>和<xref:System.Windows.Media.Pen.Brush%2A>。 您可以藉由指定建立更複雜的畫筆<xref:System.Windows.Media.Pen.DashStyle%2A>， <xref:System.Windows.Media.Pen.DashCap%2A>， <xref:System.Windows.Media.Pen.LineJoin%2A>， <xref:System.Windows.Media.Pen.StartLineCap%2A>，和<xref:System.Windows.Media.Pen.EndLineCap%2A>。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.Pen>概述所定義的圖形<xref:System.Windows.Media.GeometryDrawing>。  
  
 [!code-csharp[PenExamples_snip#PenExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PenExamples_snip/CSharp/PenExample.cs#penexamplewholepage)]
 [!code-vb[PenExamples_snip#PenExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PenExamples_snip/VisualBasic/PenExample.vb#penexamplewholepage)]  
  
 ![由 Pen 所描繪的外框會產生](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple-pen.jpg "graphicsmm_simple_pen")  
GeometryDrawing
