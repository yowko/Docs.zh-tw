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
ms.openlocfilehash: 2e247ec2bcd57c2fb2f5c32f61d38a2e7a267ff1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517569"
---
# <a name="b233zier-splines-in-gdi"></a>B&#233;zier GDI + 中的曲線
貝茲曲線是四個點所指定的曲線： 兩個結束點 （p1 和 p2） 和兩個控制點 （c1 和 c2）。 曲線開始 p1 和 p2 當做結尾。 曲線不會通過的控點，但控點做為磁鐵曲線納入特定指示和影響曲線彎曲的方式。 下圖顯示其端點和控制點貝茲曲線。  
  
 ![貝茲曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")  
  
 曲線開始 p1 和控制點 c1 移。 P1 曲線的切線是 c1 從 p1 繪製的線條。 端點 p2 的切線是取自 c2 為 p2 的線條。  
  
## <a name="drawing-bzier-splines"></a>繪製貝茲曲線  
 若要繪製的貝茲曲線，您需要的執行個體<xref:System.Drawing.Graphics>類別和<xref:System.Drawing.Pen>。 執行個體<xref:System.Drawing.Graphics>類別提供<xref:System.Drawing.Graphics.DrawBezier%2A>方法，而<xref:System.Drawing.Pen>儲存屬性，例如 寬度 和 用來呈現曲線的線條色彩。 <xref:System.Drawing.Pen>做為其中一個引數會傳遞<xref:System.Drawing.Graphics.DrawBezier%2A>方法。 其餘的引數傳遞至<xref:System.Drawing.Graphics.DrawBezier%2A>方法進行的端點和控點。 下列範例會繪製貝茲曲線，以起始點 （0，0），控制點 （40，20） 和 （80，150） 和結束點 （100，10）：  
  
 [!code-csharp[LinesCurvesAndShapes#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#71)]
 [!code-vb[LinesCurvesAndShapes#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#71)]  
  
 下圖顯示曲線、 控制點和兩個正切函數的行。  
  
 ![貝茲曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art12.gif "Aboutgdip02_art12")  
  
 貝茲曲線原本由所開發的匹貝茲汽車產業中的設計。 它們多種類型的電腦輔助設計會很有用，因為證明，也可用來定義字型的外框。 貝茲曲線，可能會產生各種圖形，其中一些會在下圖顯示。  
  
 ![路徑](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art13.gif "Aboutgdip02_art13")  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [建構和繪製曲線](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)  
 [操作說明：建立繪圖的圖形物件](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [操作說明：建立畫筆](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)
