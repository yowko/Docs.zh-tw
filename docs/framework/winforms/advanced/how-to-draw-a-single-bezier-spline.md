---
title: HOW TO：繪製單一 B&#233;zier 曲線
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines [Windows Forms], drawing
- drawing [Windows Forms], Bezier splines
ms.assetid: f4f3fe30-f0a6-4743-ac91-11310cebea9f
ms.openlocfilehash: ebb53e7df979a553ed4a44deba34345c9ecac772
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004223"
---
# <a name="how-to-draw-a-single-b233zier-spline"></a>HOW TO：繪製單一 B&#233;zier 曲線
四個點所定義的貝茲曲線︰ 起點、 兩個控制點和結束點。  
  
## <a name="example"></a>範例  
 下列範例會繪製貝茲曲線，（10，100） 的起始點與結束點 （200，100）。 兩個控制點位於 （100，10） 和 150 （150）。  
  
 下圖顯示產生的貝茲曲線，加上其起始點，控點和結束點。 此圖也會顯示曲線的凸殼，也就是依據連接四個點的直線，線條與多邊形。  
  
 ![貝茲曲線的圖例。](./media/how-to-draw-a-single-bezier-spline/bezier-spline-illustration.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Graphics.DrawBezier%2A>
- [GDI+ 中的貝茲曲線](bezier-splines-in-gdi.md)
- [如何：繪製一連串的貝茲曲線](how-to-draw-a-sequence-of-bezier-splines.md)
