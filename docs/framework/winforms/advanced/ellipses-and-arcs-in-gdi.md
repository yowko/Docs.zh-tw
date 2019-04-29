---
title: GDI+ 中的橢圓形和弧形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- arcs
- GDI+, arcs
- drawing [Windows Forms], ellipses
- GDI+, ellipses
- ellipses
- drawing [Windows Forms], arcs
ms.assetid: 34f35133-a835-4ca4-81f6-0dfedee8b683
ms.openlocfilehash: 8bbc2eda6450128eac55576259880e83f07099ab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756634"
---
# <a name="ellipses-and-arcs-in-gdi"></a>GDI+ 中的橢圓形和弧形
您可以輕鬆地繪製橢圓形和弧形使用<xref:System.Drawing.Graphics.DrawEllipse%2A>並<xref:System.Drawing.Graphics.DrawArc%2A>方法<xref:System.Drawing.Graphics>類別。  
  
## <a name="drawing-an-ellipse"></a>繪製橢圓形  
 若要繪製橢圓形，您需要<xref:System.Drawing.Graphics>物件和<xref:System.Drawing.Pen>物件。 <xref:System.Drawing.Graphics>物件會提供<xref:System.Drawing.Graphics.DrawEllipse%2A>方法，而<xref:System.Drawing.Pen>物件會儲存屬性，例如寬度和色彩，用來呈現橢圓形的行。 <xref:System.Drawing.Pen>物件會傳遞做為其中一個引數<xref:System.Drawing.Graphics.DrawEllipse%2A>方法。 其餘的引數傳遞至<xref:System.Drawing.Graphics.DrawEllipse%2A>方法指定的橢圓形的週框矩形。 下圖顯示以及其周框的橢圓形。  
  
 ![橢圓形和弧形](./media/aboutgdip02-art05.gif "Aboutgdip02_art05")  
  
 下列範例會繪製橢圓形;週框矩形的寬度為 80，40，高度和的左上角 （100，50）：  
  
 [!code-csharp[LinesCurvesAndShapes#51](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#51)]
 [!code-vb[LinesCurvesAndShapes#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#51)]  
  
 <xref:System.Drawing.Graphics.DrawEllipse%2A> 一個多載方法的<xref:System.Drawing.Graphics>類別中，因此有幾種方式，您可以提供引數。 例如，您可以建構<xref:System.Drawing.Rectangle>，並傳遞<xref:System.Drawing.Rectangle>到<xref:System.Drawing.Graphics.DrawEllipse%2A>做為引數的方法：  
  
 [!code-csharp[LinesCurvesAndShapes#52](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#52)]
 [!code-vb[LinesCurvesAndShapes#52](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#52)]  
  
## <a name="drawing-an-arc"></a>繪製弧形  
 弧形是橢圓形的一部分。 若要繪製弧形，請呼叫<xref:System.Drawing.Graphics.DrawArc%2A>方法的<xref:System.Drawing.Graphics>類別。 參數<xref:System.Drawing.Graphics.DrawArc%2A>方法會做為參數的相同<xref:System.Drawing.Graphics.DrawEllipse%2A>方法，不同之處在於<xref:System.Drawing.Graphics.DrawArc%2A>需要開始角度和掃掠角度。 下列範例會繪製具有 30 度的開始角度和掃掠角度為 180 度弧線：  
  
 [!code-csharp[LinesCurvesAndShapes#53](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#53)]
 [!code-vb[LinesCurvesAndShapes#53](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#53)]  
  
 下圖顯示弧線、 橢圓形和週框矩形。  
  
 ![橢圓形和弧形](./media/aboutgdip02-art06.gif "Aboutgdip02_art06")  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [線條、曲線和形狀](lines-curves-and-shapes.md)
- [如何：建立繪圖的圖形物件](how-to-create-graphics-objects-for-drawing.md)
- [如何：建立畫筆](how-to-create-a-pen.md)
- [如何：繪製外框的形狀](how-to-draw-an-outlined-shape.md)
