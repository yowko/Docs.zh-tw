---
title: B&#233;zier GDI + 中的曲線
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines
- splines [Windows Forms], Bezier
- GDI+, Bezier splines
ms.assetid: 5774ce1e-87d4-4bc7-88c4-4862052781b8
ms.openlocfilehash: ff4e9eb18610b70c88e057d3d44020321bbb9f4f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107324"
---
# <a name="b233zier-splines-in-gdi"></a>B&#233;zier GDI + 中的曲線
貝茲曲線是由四個點指定曲線： 兩個結束點 （p1 和 p2） 和兩個控制點 （c1 和 c2）。 曲線開始 p1 和 p2 當做結尾。 曲線的控制點，透過未通過，但控制點作用類似磁鐵，曲線納入特定指示和影響曲線的彎曲的方式。 下圖顯示加上其端點和控制點貝茲曲線。  
  
 ![貝茲曲線](./media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")  
  
 曲線開始 p1，並會朝控制點 c1 移動。 P1 曲線的切線是從 p1 到 c1 繪製的線條。 端點 p2 的切線是取自 c2 為 p2 的線條。  
  
## <a name="drawing-bzier-splines"></a>繪製貝茲曲線  
 若要繪製貝茲曲線，您需要的執行個體<xref:System.Drawing.Graphics>類別和<xref:System.Drawing.Pen>。 執行個體<xref:System.Drawing.Graphics>類別會提供<xref:System.Drawing.Graphics.DrawBezier%2A>方法，而<xref:System.Drawing.Pen>儲存屬性，例如寬度和色彩，用來呈現曲線的行。 <xref:System.Drawing.Pen>做為其中一個引數會傳遞<xref:System.Drawing.Graphics.DrawBezier%2A>方法。 其餘的引數傳遞至<xref:System.Drawing.Graphics.DrawBezier%2A>方法還有端點的控點。 下列範例會繪製貝茲曲線的起始點 （0，0），控制點 （40，20） 和 （80，150） 和結束點 （100，10）：  
  
 [!code-csharp[LinesCurvesAndShapes#71](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#71)]
 [!code-vb[LinesCurvesAndShapes#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#71)]  
  
 下圖顯示曲線的控制點，，兩正切函數的行。  
  
 ![貝茲曲線](./media/aboutgdip02-art12.gif "Aboutgdip02_art12")  
  
 匹貝茲最初所開發的貝茲曲線在汽車的產業中設計的。 而因為證明為十分有用，許多電腦輔助設計的類型也用來定義字型的外框。 貝茲曲線，可能會產生各種不同的圖形，其中會顯示在下圖中。  
  
 ![Paths](./media/aboutgdip02-art13.gif "Aboutgdip02_art13")  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [線條、曲線和形狀](lines-curves-and-shapes.md)
- [建構和繪製曲線](constructing-and-drawing-curves.md)
- [如何：建立繪圖的圖形物件](how-to-create-graphics-objects-for-drawing.md)
- [如何：建立畫筆](how-to-create-a-pen.md)
