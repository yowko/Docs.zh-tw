---
title: "GDI+ 中的開放型和封閉型曲線"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- curves [Windows Forms], filling
- GDI+, curves
- curves [Windows Forms], drawing
- curves
ms.assetid: 08d2cc9a-dc9d-4eed-bcbb-2c8e2ca5d3ae
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cde1aae6196ef8b773b8c072a42c700924f9c8cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="open-and-closed-curves-in-gdi"></a>GDI+ 中的開放型和封閉型曲線
下圖顯示兩個曲線： 開啟單一，另一個已關閉。  
  
 ![開放型 & 封閉型曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art24.gif "Aboutgdip02_art24")  
  
## <a name="managed-interface-for-curves"></a>曲線的 managed 的介面  
 封閉型曲線有內部，因此可以填滿的筆刷。 <xref:System.Drawing.Graphics>類別[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]提供下列方法，以便填滿封閉的圖形和曲線： <xref:System.Drawing.Graphics.FillRectangle%2A>， <xref:System.Drawing.Graphics.FillEllipse%2A>， <xref:System.Drawing.Graphics.FillPie%2A>， <xref:System.Drawing.Graphics.FillPolygon%2A>， <xref:System.Drawing.Graphics.FillClosedCurve%2A>， <xref:System.Drawing.Graphics.FillPath%2A>，和<xref:System.Drawing.Graphics.FillRegion%2A>。 每當您呼叫其中一種方法時，您必須傳遞其中一個特定的筆刷類型 (<xref:System.Drawing.SolidBrush>， <xref:System.Drawing.Drawing2D.HatchBrush>， <xref:System.Drawing.TextureBrush>， <xref:System.Drawing.Drawing2D.LinearGradientBrush>，或<xref:System.Drawing.Drawing2D.PathGradientBrush>) 做為引數。  
  
 <xref:System.Drawing.Graphics.FillPie%2A>方法是<xref:System.Drawing.Graphics.DrawArc%2A>方法。 就像<xref:System.Drawing.Graphics.DrawArc%2A>方法繪製外框的橢圓形的一部分<xref:System.Drawing.Graphics.FillPie%2A>方法填入一部分的橢圓形內部。 下列範例會繪製弧形，並填滿橢圓形內部的對應部分：  
  
 [!code-csharp[LinesCurvesAndShapes#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#21)]
 [!code-vb[LinesCurvesAndShapes#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#21)]  
  
 下圖顯示弧形和填滿的圓形。  
  
 ![開放型 & 封閉型曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art25.gif "Aboutgdip02_art25")  
  
 <xref:System.Drawing.Graphics.FillClosedCurve%2A>方法是<xref:System.Drawing.Graphics.DrawClosedCurve%2A>方法。 這兩種方法會藉由連接的起始點的結束點，自動關閉曲線。 下列範例會繪製曲線，通過 （0，0），（60，20） 和 （40、 50）。 曲線後，自動關閉連接 （40、 50） 的起始點 （0，0），並利用純色填滿內部。  
  
 [!code-csharp[LinesCurvesAndShapes#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#22)]
 [!code-vb[LinesCurvesAndShapes#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#22)]  
  
 <xref:System.Drawing.Graphics.FillPath%2A>方法填滿內部的路徑的個別項目。 如果路徑的一不會形成封閉的曲線或圖形，<xref:System.Drawing.Graphics.FillPath%2A>方法填滿它之前會自動關閉該片段的路徑。 下列範例會繪製，並填滿弧線、 曲線、 字串和圓形圖所組成的路徑：  
  
 [!code-csharp[LinesCurvesAndShapes#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#23)]
 [!code-vb[LinesCurvesAndShapes#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#23)]  
  
 下圖顯示逾時或無純色填滿的路徑。 請注意，在字串中的文字是所述，但不是填滿，由<xref:System.Drawing.Graphics.DrawPath%2A>方法。 它是<xref:System.Drawing.Graphics.FillPath%2A>繪製內部的字串中字元的方法。  
  
 ![字串之路徑中的](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art26.gif "Aboutgdip02_art26")  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 <xref:System.Drawing.Point?displayProperty=nameWithType>  
 [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [操作說明：建立繪圖的圖形物件](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [建構和繪製路徑](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
