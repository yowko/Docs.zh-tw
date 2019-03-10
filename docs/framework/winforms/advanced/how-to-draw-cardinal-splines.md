---
title: HOW TO：繪製基本曲線
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cardinal splines [Windows Forms], drawing
- drawing [Windows Forms], cardinal splines
- graphics [Windows Forms], cardinal splines
ms.assetid: a4a41e80-4461-4b47-b6bd-2c5e68881994
ms.openlocfilehash: 687143273a07acba4b4d60acb1be25eee165b91d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710481"
---
# <a name="how-to-draw-cardinal-splines"></a>HOW TO：繪製基本曲線
基本曲線是一條曲線順利通過一組指定的點。 若要繪製基本曲線，建立<xref:System.Drawing.Graphics>物件，並指向陣列的位址傳遞<xref:System.Drawing.Graphics.DrawCurve%2A>方法。  
  
### <a name="drawing-a-bell-shaped-cardinal-spline"></a>繪製基本鐘型曲線  
  
-   下列範例會繪製的鐘型基線曲線通過五個指定的點。 下圖顯示曲線和五個點。  
  
     ![基本曲線](./media/cardinalspline1.png "CardinalSpline1")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#21)]  
  
### <a name="drawing-a-closed-cardinal-spline"></a>繪製封閉的基線曲線  
  
-   使用<xref:System.Drawing.Graphics.DrawClosedCurve%2A>方法的<xref:System.Drawing.Graphics>類別用來繪製封閉的基線曲線。 在封閉的基線曲線曲線會繼續進行到陣列中的最後一個點，並在陣列中的第一個點會連線。 下列範例會繪製封閉的基線曲線通過六個指定的點。 下圖是封閉的曲線，以及六個點。  
  
 ![基本曲線](./media/cardinalspline1a.png "CardinalSpline1A")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#22)]  
  
### <a name="changing-the-bend-of-a-cardinal-spline"></a>變更的彎曲的基線曲線  
  
-   變更的方式傳遞的張力引數的彎曲的基本曲線<xref:System.Drawing.Graphics.DrawCurve%2A>方法。 下列範例會繪製通過相同的一組點的三個基本曲線。 下圖顯示三個曲線，以及其張力值。 請注意，張力為 0 時，點是以直線來連接。  
  
 ![基本曲線](./media/cardinalspline2.png "CardinalSpline2")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#23)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例專為搭配 Windows Form 使用，而且它們需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。  
  
## <a name="see-also"></a>另請參閱
- [線條、曲線和形狀](lines-curves-and-shapes.md)
- [建構和繪製曲線](constructing-and-drawing-curves.md)
