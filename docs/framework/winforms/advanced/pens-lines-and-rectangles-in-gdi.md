---
title: GDI+ 中的畫筆、線條和矩形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines
- GDI+, lines
- drawing [Windows Forms], rectangles
- rectangles
- drawing [Windows Forms], lines
- GDI+, pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- GDI+, rectangles
- examples [Windows Forms], GDI+
- lines [Windows Forms], dashed
ms.assetid: 30b25aae-e3eb-4479-bdb8-187cf651fc84
ms.openlocfilehash: 84752773c0b56d9684dc31620d463d4ddccf9dad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078222"
---
# <a name="pens-lines-and-rectangles-in-gdi"></a>GDI+ 中的畫筆、線條和矩形
若要使用繪製線條[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]您需要建立<xref:System.Drawing.Graphics>物件和<xref:System.Drawing.Pen>物件。 <xref:System.Drawing.Graphics>物件提供的方法，實際進行繪製，而<xref:System.Drawing.Pen>物件會儲存屬性，例如線條色彩、 寬度和樣式。  
  
## <a name="drawing-a-line"></a>繪製一條線  
 若要繪製一條線，請呼叫<xref:System.Drawing.Graphics.DrawLine%2A>方法的<xref:System.Drawing.Graphics>物件。 <xref:System.Drawing.Pen>物件會傳遞做為其中一個引數<xref:System.Drawing.Graphics.DrawLine%2A>方法。 下列範例會繪製一條線從點 （4，2） 到點 （12，6）：  
  
 [!code-csharp[LinesCurvesAndShapes#41](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#41)]
 [!code-vb[LinesCurvesAndShapes#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#41)]  
  
 <xref:System.Drawing.Graphics.DrawLine%2A> 一個多載方法的<xref:System.Drawing.Graphics>類別中，因此有幾種方式，您可以提供引數。 例如，您可以建構兩個<xref:System.Drawing.Point>物件並傳遞<xref:System.Drawing.Point>物件做為引數<xref:System.Drawing.Graphics.DrawLine%2A>方法：  
  
 [!code-csharp[LinesCurvesAndShapes#42](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#42)]
 [!code-vb[LinesCurvesAndShapes#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#42)]  
  
## <a name="constructing-a-pen"></a>建構的畫筆  
 您可以指定特定屬性，當您建構<xref:System.Drawing.Pen>物件。 例如，一個`Pen`建構函式可讓您指定的色彩和寬度。 下列範例會繪製藍線的寬度為 2 從 （0，0） 到 （60，30）：  
  
 [!code-csharp[LinesCurvesAndShapes#43](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#43)]
 [!code-vb[LinesCurvesAndShapes#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#43)]  
  
## <a name="dashed-lines-and-line-caps"></a>虛線和線條端點  
 <xref:System.Drawing.Pen>物件也會公開屬性，例如<xref:System.Drawing.Pen.DashStyle%2A>，可用來指定線條的功能。 下列範例會繪製一條虛線從 （100，50） 到 300 (80）：  
  
 [!code-csharp[LinesCurvesAndShapes#44](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#44)]
 [!code-vb[LinesCurvesAndShapes#44](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#44)]  
  
 您可以使用的屬性<xref:System.Drawing.Pen>設定列的許多其他屬性的物件。 <xref:System.Drawing.Pen.StartCap%2A>和<xref:System.Drawing.Pen.EndCap%2A>屬性指定線結束部分的外觀，端點可以是一般、 正方形、 圓角、 三角，或自訂的圖形。 <xref:System.Drawing.Pen.LineJoin%2A>屬性可讓您指定連接的直線是斜接 （加入具有銳利的角）、 斜、 捨入，或裁剪。 下圖顯示具有各種不同的端點和聯結樣式的行。  
  
 ![Lines](./media/aboutgdip02-art04.gif "Aboutgdip02_art04")  
  
## <a name="drawing-a-rectangle"></a>繪製矩形  
 繪製矩形[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]類似於繪製線條。 若要繪製矩形，您需要<xref:System.Drawing.Graphics>物件和<xref:System.Drawing.Pen>物件。 <xref:System.Drawing.Graphics>物件會提供<xref:System.Drawing.Graphics.DrawRectangle%2A>方法，而<xref:System.Drawing.Pen>物件會儲存屬性，例如線條寬度和色彩。 <xref:System.Drawing.Pen>物件會傳遞做為其中一個引數<xref:System.Drawing.Graphics.DrawRectangle%2A>方法。 下列範例會繪製在其左上角的矩形 （100，50），寬度為 80，以及高度為 40:  
  
 [!code-csharp[LinesCurvesAndShapes#45](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#45)]
 [!code-vb[LinesCurvesAndShapes#45](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#45)]  
  
 <xref:System.Drawing.Graphics.DrawRectangle%2A> 一個多載方法的<xref:System.Drawing.Graphics>類別中，因此有幾種方式，您可以提供引數。 例如，您可以建構<xref:System.Drawing.Rectangle>物件，並傳遞<xref:System.Drawing.Rectangle>物件到<xref:System.Drawing.Graphics.DrawRectangle%2A>做為引數的方法：  
  
 [!code-csharp[LinesCurvesAndShapes#46](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#46)]
 [!code-vb[LinesCurvesAndShapes#46](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#46)]  
  
 A<xref:System.Drawing.Rectangle>物件具有方法和屬性來操作和收集矩形的相關資訊。 例如，<xref:System.Drawing.Rectangle.Inflate%2A>和<xref:System.Drawing.Rectangle.Offset%2A>方法變更的大小和位置的矩形。 <xref:System.Drawing.Rectangle.IntersectsWith%2A>方法會告訴您該矩形是否與另一個指定的矩形，而<xref:System.Drawing.Rectangle.Contains%2A>方法會告訴您指定的點是否在矩形內部。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Rectangle?displayProperty=nameWithType>
- [HOW TO：建立畫筆](how-to-create-a-pen.md)
- [HOW TO：在 Windows Form 上繪製線條](how-to-draw-a-line-on-a-windows-form.md)
- [HOW TO：繪製外框形狀](how-to-draw-an-outlined-shape.md)
