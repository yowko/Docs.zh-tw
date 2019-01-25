---
title: GDI+ 中的圖形路徑
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], paths
- GDI+, drawing paths
- paths [Windows Forms], drawing
- drawing [Windows Forms], paths
ms.assetid: a5500dec-666c-41fd-9da3-2169dd89c5eb
ms.openlocfilehash: 55cd3284f331e9793a0bb73f26ed16bbd99fa116
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685642"
---
# <a name="graphics-paths-in-gdi"></a>GDI+ 中的圖形路徑
路徑被形成藉由結合線條、 矩形和簡單的曲線。 回想一下[向量圖形概觀](../../../../docs/framework/winforms/advanced/vector-graphics-overview.md)是最適合繪製圖片證明了下列的基本建置組塊：  
  
-   線條  
  
-   矩形  
  
-   省略符號  
  
-   Arcs  
  
-   多邊形  
  
-   基線曲線  
  
-   貝茲曲線  
  
 在 GDI + 中，<xref:System.Drawing.Drawing2D.GraphicsPath>物件可讓您收集成一個單位的一連串的這些建置組塊。 然後可以有一個呼叫繪製一連串完整的線條、 矩形、 多邊形和曲線<xref:System.Drawing.Graphics.DrawPath%2A>方法的<xref:System.Drawing.Graphics>類別。 下圖顯示一條線，弧形、 貝茲曲線的基線曲線相結合所產生的路徑。  
  
 ![Path](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art14.gif "Aboutgdip02_art14")  
  
## <a name="using-a-path"></a>使用路徑  
 <xref:System.Drawing.Drawing2D.GraphicsPath>類別提供下列方法來建立一連串要繪製的項目： <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>， <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>， <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>， <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>， <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>， <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> （適用於基本曲線），和<xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>。 每一種方法多載;也就是說，每一種方法支援數個不同的參數清單。 比方說，一個變化<xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>方法會收到四個整數，與另一個變化<xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>方法會接收兩個<xref:System.Drawing.Point>物件。  
  
 加入路徑的線條、 矩形和貝茲曲線的方法有數個項目新增至單一呼叫中的路徑的複數隨附方法： <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>， <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>，和<xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>。 此外，<xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>並<xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>方法有隨附方法<xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A>和<xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>，將關閉的曲線或圓形圖新增至路徑。  
  
 若要繪製的路徑，您需要<xref:System.Drawing.Graphics>物件，<xref:System.Drawing.Pen>物件，和<xref:System.Drawing.Drawing2D.GraphicsPath>物件。 <xref:System.Drawing.Graphics>物件會提供<xref:System.Drawing.Graphics.DrawPath%2A>方法，而<xref:System.Drawing.Pen>物件會儲存屬性，例如 寬度 和 用來呈現的路徑線條的色彩。 <xref:System.Drawing.Drawing2D.GraphicsPath>物件會儲存一連串的直線和曲線路徑所組成。 <xref:System.Drawing.Pen>物件和<xref:System.Drawing.Drawing2D.GraphicsPath>物件會當做參數傳遞給<xref:System.Drawing.Graphics.DrawPath%2A>方法。 下列範例會繪製包含線條、 橢圓形和貝茲曲線的路徑：  
  
 [!code-csharp[LinesCurvesAndShapes#101](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#101)]
 [!code-vb[LinesCurvesAndShapes#101](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#101)]  
  
 下圖顯示的路徑。  
  
 ![Path](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art15.gif "Aboutgdip02_art15")  
  
 除了新增至路徑的線條、 矩形和曲線，您可以新增至路徑的路徑。 這可讓您結合現有的路徑，以形成大型且複雜的路徑。  
  
 [!code-csharp[LinesCurvesAndShapes#102](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#102)]
 [!code-vb[LinesCurvesAndShapes#102](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#102)]  
  
 您可以將它新增至路徑的其他兩個項目： 字串和派形。 圓形圖會是橢圓形的一部分內部。 下列範例會建立從弧線、 的基本曲線、 字串和圓形路徑：  
  
 [!code-csharp[LinesCurvesAndShapes#103](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#103)]
 [!code-vb[LinesCurvesAndShapes#103](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#103)]  
  
 下圖顯示的路徑。 請注意，路徑可能沒有連線;弧線、 基線曲線、 字串和圓形圖會分隔。  
  
 ![Paths](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art16.gif "Aboutgdip02_Art16")  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- <xref:System.Drawing.Point?displayProperty=nameWithType>
- [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)
- [如何：建立繪圖的圖形物件](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)
- [建構和繪製路徑](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
