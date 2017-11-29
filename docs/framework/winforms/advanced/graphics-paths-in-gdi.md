---
title: "GDI+ 中的圖形路徑"
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
- graphics [Windows Forms], paths
- GDI+, drawing paths
- paths [Windows Forms], drawing
- drawing [Windows Forms], paths
ms.assetid: a5500dec-666c-41fd-9da3-2169dd89c5eb
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e027228ea1cc047f213c28ac3a4984c2f0227c5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="graphics-paths-in-gdi"></a>GDI+ 中的圖形路徑
路徑格式結合線條、 矩形和簡單的曲線。 回想一下[向量圖形概觀](../../../../docs/framework/winforms/advanced/vector-graphics-overview.md)下列的基本建置組塊經證實繪製圖片時最有用：  
  
-   線條  
  
-   矩形  
  
-   省略符號  
  
-   弧線  
  
-   多邊形  
  
-   基本曲線  
  
-   貝茲曲線  
  
 在 GDI + 中，<xref:System.Drawing.Drawing2D.GraphicsPath>物件可讓您收集成一個單位的一系列的建置組塊。 然後可以呼叫以繪製整個序列線條、 矩形、 多邊形和曲線的<xref:System.Drawing.Graphics.DrawPath%2A>方法<xref:System.Drawing.Graphics>類別。 下圖顯示一條線、 弧線、 貝茲曲線和基本曲線相結合所產生的路徑。  
  
 ![路徑](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art14.gif "Aboutgdip02_art14")  
  
## <a name="using-a-path"></a>使用路徑  
 <xref:System.Drawing.Drawing2D.GraphicsPath>類別會提供下列方法來建立一連串的項目要繪製： <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>， <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>， <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>， <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>， <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>， <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> （適用於曲線），和<xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>。 每一種方法多載。也就是說，每個方法都支援數個不同的參數清單。 例如，一個變化<xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>方法收到四個整數，與另一種變形<xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>方法會接收兩個<xref:System.Drawing.Point>物件。  
  
 加入路徑中的線條、 矩形和貝茲曲線的方法有複數附屬方法，將數個項目加入至單一呼叫中的路徑： <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>， <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>，和<xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>。 此外，<xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>和<xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>方法有附屬方法<xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A>和<xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>，一個封閉的曲線或圓形圖加入路徑。  
  
 若要繪製的路徑，您需要<xref:System.Drawing.Graphics>物件<xref:System.Drawing.Pen>物件，和<xref:System.Drawing.Drawing2D.GraphicsPath>物件。 <xref:System.Drawing.Graphics>物件提供<xref:System.Drawing.Graphics.DrawPath%2A>方法，而<xref:System.Drawing.Pen>物件會儲存屬性，例如 寬度 和 用來呈現路徑線條色彩。 <xref:System.Drawing.Drawing2D.GraphicsPath>物件儲存的直線和曲線的路徑順序。 <xref:System.Drawing.Pen>物件和<xref:System.Drawing.Drawing2D.GraphicsPath>物件會傳遞做為引數<xref:System.Drawing.Graphics.DrawPath%2A>方法。 下列範例會繪製一條線、 橢圓形及貝茲曲線組成的路徑：  
  
 [!code-csharp[LinesCurvesAndShapes#101](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#101)]
 [!code-vb[LinesCurvesAndShapes#101](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#101)]  
  
 下圖顯示的路徑。  
  
 ![路徑](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art15.gif "Aboutgdip02_art15")  
  
 除了新增至路徑的線條、 矩形和曲線，您可以新增至路徑的路徑。 這可讓您結合以形成大型、 複雜的路徑的現有路徑。  
  
 [!code-csharp[LinesCurvesAndShapes#102](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#102)]
 [!code-vb[LinesCurvesAndShapes#102](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#102)]  
  
 有兩個您可以將路徑加入其他項目： 字串和派形。 圓形圖是橢圓形的一部分內部。 下列範例會建立從弧線、 曲線、 字串和圓形圖路徑：  
  
 [!code-csharp[LinesCurvesAndShapes#103](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#103)]
 [!code-vb[LinesCurvesAndShapes#103](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#103)]  
  
 下圖顯示的路徑。 請注意，路徑可能沒有連接。弧線、 曲線、 字串和圓形圖會分隔。  
  
 ![路徑](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art16.gif "Aboutgdip02_Art16")  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 <xref:System.Drawing.Point?displayProperty=nameWithType>  
 [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [操作說明：建立繪圖的圖形物件](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [建構和繪製路徑](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
