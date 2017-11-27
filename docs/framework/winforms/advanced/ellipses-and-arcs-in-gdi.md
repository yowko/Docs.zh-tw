---
title: "GDI+ 中的橢圓形和弧形"
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
- arcs
- GDI+, arcs
- drawing [Windows Forms], ellipses
- GDI+, ellipses
- ellipses
- drawing [Windows Forms], arcs
ms.assetid: 34f35133-a835-4ca4-81f6-0dfedee8b683
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ebeae1d076a0ebcf36d52dee1af0c0ad5f04fdf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ellipses-and-arcs-in-gdi"></a>GDI+ 中的橢圓形和弧形
您可以輕鬆地繪製橢圓形和弧形使用<xref:System.Drawing.Graphics.DrawEllipse%2A>和<xref:System.Drawing.Graphics.DrawArc%2A>方法<xref:System.Drawing.Graphics>類別。  
  
## <a name="drawing-an-ellipse"></a>繪製橢圓形  
 若要繪製橢圓形，您需要<xref:System.Drawing.Graphics>物件和<xref:System.Drawing.Pen>物件。 <xref:System.Drawing.Graphics>物件提供<xref:System.Drawing.Graphics.DrawEllipse%2A>方法，而<xref:System.Drawing.Pen>物件會儲存屬性，例如寬度和色彩，用來呈現橢圓形的行。 <xref:System.Drawing.Pen>物件會傳遞做為其中一個引數<xref:System.Drawing.Graphics.DrawEllipse%2A>方法。 其餘的引數傳遞至<xref:System.Drawing.Graphics.DrawEllipse%2A>方法指定的橢圓形之周框。 下圖顯示以及其周框的橢圓形。  
  
 ![橢圓形和弧形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art05.gif "Aboutgdip02_art05")  
  
 下列範例會繪製橢圓形。周框的寬度為 80，為 40，高度和的左上角 （100，50）：  
  
 [!code-csharp[LinesCurvesAndShapes#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#51)]
 [!code-vb[LinesCurvesAndShapes#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#51)]  
  
 <xref:System.Drawing.Graphics.DrawEllipse%2A>是一種多載的方法<xref:System.Drawing.Graphics>類別中，因此您可以提供引數的數種方式。 例如，您可以建構<xref:System.Drawing.Rectangle>並傳遞<xref:System.Drawing.Rectangle>至<xref:System.Drawing.Graphics.DrawEllipse%2A>做為引數的方法：  
  
 [!code-csharp[LinesCurvesAndShapes#52](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#52)]
 [!code-vb[LinesCurvesAndShapes#52](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#52)]  
  
## <a name="drawing-an-arc"></a>繪製弧形，  
 弧線是橢圓形的一部分。 若要繪製弧形，呼叫<xref:System.Drawing.Graphics.DrawArc%2A>方法<xref:System.Drawing.Graphics>類別。 參數的<xref:System.Drawing.Graphics.DrawArc%2A>方法和步驟完全相同的參數<xref:System.Drawing.Graphics.DrawEllipse%2A>方法，不同處在於<xref:System.Drawing.Graphics.DrawArc%2A>需要開始角度和掃掠角度。 下列範例會繪製弧形，30 度開始角度與掃掠角度為 180 度：  
  
 [!code-csharp[LinesCurvesAndShapes#53](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#53)]
 [!code-vb[LinesCurvesAndShapes#53](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#53)]  
  
 下圖顯示弧線、 橢圓形和週框矩形。  
  
 ![橢圓形和弧形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art06.gif "Aboutgdip02_art06")  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [操作說明：建立繪圖的圖形物件](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [操作說明：建立畫筆](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)  
 [操作說明：繪製外框形狀](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)
