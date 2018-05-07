---
title: 如何： 繪製 B 順序&#233;zier 曲線
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- splines [Windows Forms], drawing Bezier
- Bezier splines [Windows Forms], drawing sequence of
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
ms.openlocfilehash: 8439e08109630b9a59c8e0359aa4d18e5241412c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a>如何： 繪製 B 順序&#233;zier 曲線
您可以使用<xref:System.Drawing.Graphics.DrawBeziers%2A>方法<xref:System.Drawing.Graphics>類別繪製一系列連接的貝茲曲線。  
  
## <a name="example"></a>範例  
 下列範例會繪製包含兩個連接的貝茲曲線的曲線。 第一個貝茲曲線的結束點是第二個貝茲曲線開始點。  
  
 下圖顯示連接的曲線，和七個點。  
  
 ![貝茲曲線](../../../../docs/framework/winforms/advanced/media/bezierspline2.png "BezierSpline2")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。  
  
## <a name="see-also"></a>另請參閱  
 [Windows Forms 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [GDI+ 中的貝茲曲線](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 [建構和繪製曲線](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
