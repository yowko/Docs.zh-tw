---
title: 如何：繪製基本曲線
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cardinal splines [Windows Forms], drawing
- drawing [Windows Forms], cardinal splines
- graphics [Windows Forms], cardinal splines
ms.assetid: a4a41e80-4461-4b47-b6bd-2c5e68881994
ms.openlocfilehash: 3ad06eb28e1d8e6b5d5f4a77e545f174d8a68d9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-cardinal-splines"></a>如何：繪製基本曲線
基本曲線是曲線順利通過指定的點集合。 若要繪製基本曲線，建立<xref:System.Drawing.Graphics>物件，並傳遞至點陣列位址<xref:System.Drawing.Graphics.DrawCurve%2A>方法。  
  
### <a name="drawing-a-bell-shaped-cardinal-spline"></a>繪製鐘型曲線  
  
-   下列範例會繪製鐘型曲線通過五個指定點。 下圖顯示曲線和五個點。  
  
     ![基本曲線](../../../../docs/framework/winforms/advanced/media/cardinalspline1.png "CardinalSpline1")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#21)]  
  
### <a name="drawing-a-closed-cardinal-spline"></a>繪製封閉的基線曲線  
  
-   使用<xref:System.Drawing.Graphics.DrawClosedCurve%2A>方法<xref:System.Drawing.Graphics>繪製封閉的基線曲線的類別。 封閉的基線曲線的曲線會持續進行陣列中的最後一個點，並連接陣列中的第一個點。 下列範例會繪製封閉的基線曲線通過六個指定的點。 下圖顯示六個點以及曲線已關閉。  
  
 ![基本曲線](../../../../docs/framework/winforms/advanced/media/cardinalspline1a.png "CardinalSpline1A")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#22)]  
  
### <a name="changing-the-bend-of-a-cardinal-spline"></a>變更的彎曲的基本曲線  
  
-   變更的方式所傳遞的張力引數的彎曲的基線曲線<xref:System.Drawing.Graphics.DrawCurve%2A>方法。 下列範例會繪製通過相同的一組點的三個基本曲線。 下圖顯示三個曲線與其張力值。 請注意張力為 0 時，點會連接的直線。  
  
 ![基本曲線](../../../../docs/framework/winforms/advanced/media/cardinalspline2.png "CardinalSpline2")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#23)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 前面的範例專為搭配 Windows Form 使用，而且會要求<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。  
  
## <a name="see-also"></a>另請參閱  
 [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [建構和繪製曲線](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
