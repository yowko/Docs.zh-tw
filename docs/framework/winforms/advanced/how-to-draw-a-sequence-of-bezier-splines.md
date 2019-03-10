---
title: HOW TO：繪製順序的 B&#233;zier 曲線
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- splines [Windows Forms], drawing Bezier
- Bezier splines [Windows Forms], drawing sequence of
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
ms.openlocfilehash: 1de2f44be189cb2ff874a748ae6093c945120178
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711784"
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a>HOW TO：繪製順序的 B&#233;zier 曲線
您可以使用<xref:System.Drawing.Graphics.DrawBeziers%2A>方法的<xref:System.Drawing.Graphics>類別用來繪製一系列連接的貝茲曲線。  
  
## <a name="example"></a>範例  
 下列範例會繪製曲線，其中包含的兩個連接的貝茲曲線。 第一個貝茲曲線的結束點是第二個貝茲曲線的起始點。  
  
 下圖顯示連接的曲線，以及在七個點。  
  
 ![Bezier Spline](./media/bezierspline2.png "BezierSpline2")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。  
  
## <a name="see-also"></a>另請參閱
- [Windows Forms 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)
- [GDI+ 中的貝茲曲線](bezier-splines-in-gdi.md)
- [建構和繪製曲線](constructing-and-drawing-curves.md)
