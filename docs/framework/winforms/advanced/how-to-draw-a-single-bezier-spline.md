---
title: "如何： 繪製單一 B &#233; zier 曲線"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines [Windows Forms], drawing
- drawing [Windows Forms], Bezier splines
ms.assetid: f4f3fe30-f0a6-4743-ac91-11310cebea9f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0ebdba9e01824cc764a6ab759da049add180ba83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-single-b233zier-spline"></a>如何： 繪製單一 B &#233; zier 曲線
貝茲曲線由四個點所定義： 一個起始點，兩個控制點和端點。  
  
## <a name="example"></a>範例  
 下列範例會繪製具有 （10，100） 的起點和終點 （200，100） 的貝茲曲線。 控制項點為 （100，10） 和 150 （150）。  
  
 下圖顯示產生的貝茲曲線，以及其起點、 控點和端點。 下圖也會顯示曲線的凸殼，也就是所連接的四個點之直線的多邊形。  
  
 ![貝茲曲線](../../../../docs/framework/winforms/advanced/media/bezierspline1.png "BezierSpline1")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Drawing.Graphics.DrawBezier%2A>  
 [GDI+ 中的貝茲曲線](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 [操作說明：繪製一連串的貝茲曲線](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)
