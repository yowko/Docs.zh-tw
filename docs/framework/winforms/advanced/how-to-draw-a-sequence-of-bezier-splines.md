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
ms.openlocfilehash: 2b74b03137d5a450fb1e436a514877d1a17229ad
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654246"
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a>HOW TO：繪製順序的 B&#233;zier 曲線
您可以使用<xref:System.Drawing.Graphics.DrawBeziers%2A>方法的<xref:System.Drawing.Graphics>類別用來繪製一系列連接的貝茲曲線。  
  
## <a name="example"></a>範例  
 下列範例會繪製曲線，其中包含的兩個連接的貝茲曲線。 第一個貝茲曲線的結束點是第二個貝茲曲線的起始點。  
  
 下圖顯示連接的曲線，以及在七個點：  
  
 ![圖形： 顯示連接的曲線，以及七個點。](./media/how-to-draw-a-sequence-of-bezier-splines/bezier-spline-seven-points.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。  
  
## <a name="see-also"></a>另請參閱
- [Windows Forms 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)
- [GDI+ 中的貝茲曲線](bezier-splines-in-gdi.md)
- [建構和繪製曲線](constructing-and-drawing-curves.md)
