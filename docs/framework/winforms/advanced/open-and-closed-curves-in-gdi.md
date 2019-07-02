---
title: GDI+ 中的開放型和封閉型曲線
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- curves [Windows Forms], filling
- GDI+, curves
- curves [Windows Forms], drawing
- curves
ms.assetid: 08d2cc9a-dc9d-4eed-bcbb-2c8e2ca5d3ae
ms.openlocfilehash: 06afdc4549f7c3c9b0636e5c7052dcca87a153f1
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505447"
---
# <a name="open-and-closed-curves-in-gdi"></a>GDI+ 中的開放型和封閉型曲線
下圖顯示兩個曲線： 開啟和其中一個已關閉。  
  
 ![開啟 & 封閉型曲線](./media/aboutgdip02-art24.gif "Aboutgdip02_art24")  
  
## <a name="managed-interface-for-curves"></a>曲線的 managed 的介面  
 封閉型曲線有內部，因此可以填滿筆刷。 <xref:System.Drawing.Graphics> GDI + 中的類別提供下列方法，以便填滿封閉的形狀和曲線： <xref:System.Drawing.Graphics.FillRectangle%2A>， <xref:System.Drawing.Graphics.FillEllipse%2A>， <xref:System.Drawing.Graphics.FillPie%2A>， <xref:System.Drawing.Graphics.FillPolygon%2A>， <xref:System.Drawing.Graphics.FillClosedCurve%2A>， <xref:System.Drawing.Graphics.FillPath%2A>，以及<xref:System.Drawing.Graphics.FillRegion%2A>。 每當您呼叫其中一個方法，您必須傳遞其中一個特定的筆刷類型 (<xref:System.Drawing.SolidBrush>， <xref:System.Drawing.Drawing2D.HatchBrush>， <xref:System.Drawing.TextureBrush>， <xref:System.Drawing.Drawing2D.LinearGradientBrush>，或<xref:System.Drawing.Drawing2D.PathGradientBrush>) 做為引數。  
  
 <xref:System.Drawing.Graphics.FillPie%2A>方法是附隨於<xref:System.Drawing.Graphics.DrawArc%2A>方法。 就如同<xref:System.Drawing.Graphics.DrawArc%2A>方法會繪製外框的橢圓形，部分<xref:System.Drawing.Graphics.FillPie%2A>方法會填滿橢圓形內部的一部分。 下列範例會繪製弧形，並填滿橢圓形內部的相對應的部分：  
  
 [!code-csharp[LinesCurvesAndShapes#21](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#21)]
 [!code-vb[LinesCurvesAndShapes#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#21)]  
  
 下圖顯示弧線和填滿的圓形。  
  
 ![開啟 & 封閉型曲線](./media/aboutgdip02-art25.gif "Aboutgdip02_art25")  
  
 <xref:System.Drawing.Graphics.FillClosedCurve%2A>方法是附隨於<xref:System.Drawing.Graphics.DrawClosedCurve%2A>方法。 這兩種方法會藉由連接的起始點的結束點，自動關閉曲線。 下列範例會繪製曲線通過 （0，0），（60，20），以及 （40、 50）。 然後曲線會自動關閉連接 （40、 50） 開始的點 （0，0），並使用純色填滿內部。  
  
 [!code-csharp[LinesCurvesAndShapes#22](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#22)]
 [!code-vb[LinesCurvesAndShapes#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#22)]  
  
 <xref:System.Drawing.Graphics.FillPath%2A>方法會填滿之路徑的個別部分的內部互相。 如果一段路徑不會形成封閉的曲線或圖形，<xref:System.Drawing.Graphics.FillPath%2A>方法會自動關閉該路徑的部分填滿它之前。 下列範例會繪製，並填滿弧線、 基線曲線、 字串和圓形圖組成的路徑：  
  
 [!code-csharp[LinesCurvesAndShapes#23](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#23)]
 [!code-vb[LinesCurvesAndShapes#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#23)]  
  
 下圖顯示包含或不含純色填滿的路徑。 請注意，在字串中的文字是所述，但未填入，藉由<xref:System.Drawing.Graphics.DrawPath%2A>方法。 它是<xref:System.Drawing.Graphics.FillPath%2A>繪製字串中字元的內部互相的方法。  
  
 ![路徑中的字串](./media/aboutgdip02-art26.gif "Aboutgdip02_art26")  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Point?displayProperty=nameWithType>
- [線條、曲線和形狀](lines-curves-and-shapes.md)
- [如何：建立繪圖的圖形物件](how-to-create-graphics-objects-for-drawing.md)
- [建構和繪製路徑](constructing-and-drawing-paths.md)
