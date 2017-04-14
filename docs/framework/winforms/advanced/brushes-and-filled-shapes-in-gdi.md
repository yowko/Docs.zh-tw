---
title: "GDI+ 中的筆刷和填滿的形狀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "筆刷, GDI+"
  - "筆刷, 漸層"
  - "填滿的圖案, GDI+"
  - "GDI+, 筆刷"
  - "GDI+, 填滿的圖案"
  - "漸層筆刷"
  - "圖案, GDI+"
ms.assetid: e863e2a7-0294-4130-99b6-f1ea3201e7cd
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# GDI+ 中的筆刷和填滿的形狀
矩形或橢圓形之類的封閉型形狀是由外框和內景所組成。  外框是以畫筆繪製，而內景則是以筆刷填滿。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供了幾個筆刷類別，用來填滿封閉形狀的內景：<xref:System.Drawing.SolidBrush>、<xref:System.Drawing.Drawing2D.HatchBrush>、<xref:System.Drawing.TextureBrush>、<xref:System.Drawing.Drawing2D.LinearGradientBrush> 和 <xref:System.Drawing.Drawing2D.PathGradientBrush>。  這些類別全部都繼承自 <xref:System.Drawing.Brush> 類別。  下圖將顯示由實心筆刷 \(Solid Brush\) 填滿的矩形，以及由規劃筆刷填滿的橢圓形。  
  
 ![填滿的圖案](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art17.png "Aboutgdip02\_art17")  
  
## 實心筆刷  
 若要填滿封閉形狀，您需要 <xref:System.Drawing.Graphics> 類別執行個體和 <xref:System.Drawing.Brush>。  <xref:System.Drawing.Graphics> 類別執行個體提供方法，例如 <xref:System.Drawing.Graphics.FillRectangle%2A> 和 <xref:System.Drawing.Graphics.FillEllipse%2A>，而 <xref:System.Drawing.Brush> 則是儲存填入的屬性，例如色彩和圖樣。  <xref:System.Drawing.Brush> 會當成其中一個引數傳遞給填色方法 \(Fill Method\)。  下列程式碼範例會示範如何使用實心紅色填滿橢圓形。  
  
 [!code-csharp[LinesCurvesAndShapes#121](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
>  上述範例中所使用的筆刷是屬於 <xref:System.Drawing.SolidBrush> 型別，其繼承自 <xref:System.Drawing.Brush>。  
  
## 規劃筆刷  
 當您使用規劃筆刷填滿某個形狀時，您可以指定前景色彩、背景色彩和規劃的樣式。  前景色彩即為規劃的色彩。  
  
 [!code-csharp[LinesCurvesAndShapes#122](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供超過 50 種規劃樣式；下圖中所顯示的三種樣式為 <xref:System.Drawing.Drawing2D.HatchStyle>、<xref:System.Drawing.Drawing2D.HatchStyle> 和 <xref:System.Drawing.Drawing2D.HatchStyle>。  
  
 ![填滿的圖案](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art18.png "Aboutgdip02\_art18")  
  
## 紋理筆刷  
 如果您使用紋理筆刷，您可以使用儲存在點陣圖中的圖樣來填滿形狀。  例如，假設下列圖片儲存在名為 `MyTexture.bmp` 的磁片檔案中。  
  
 ![填滿的圖案](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art19.png "Aboutgdip02\_Art19")  
  
 下列程式碼範例會示範如何重複儲存在 `MyTexture.bmp` 的圖片來填滿橢圓形。  
  
 [!code-csharp[LinesCurvesAndShapes#123](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 下圖顯示的是已填滿的橢圓形。  
  
 ![填滿的圖案](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art20.png "AboutGdip02\_Art20")  
  
## 漸層筆刷  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供兩種漸層筆刷：直線和路徑。  您可以使用直線漸層路徑，當您以水平、垂直或對角方式在形狀上方移動時，將漸層變化的色彩填入形狀中。  下列程式碼範例會示範如何使用水平漸層筆刷，當您從橢圓形的左緣移動到右緣時，將由藍漸層為綠的色彩填入橢圓形。  
  
 [!code-csharp[LinesCurvesAndShapes#124](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 下圖顯示的是已填滿的橢圓形。  
  
 ![填滿的圖案](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art21.png "AboutGdip02\_Art21")  
  
 您可以設定使用路徑漸層筆刷，當您從形狀中心移到邊緣時變更形狀的色彩。  
  
 ![填滿的圖案](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art22.png "AboutGdip02\_Art22")  
  
 路徑漸層筆刷非常具有彈性。  下圖中用來填滿三角形的漸層筆刷會從中心點，由紅色逐漸在垂直中心處變成三種不同的色彩。  
  
 ![填滿的圖案](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art23.png "AboutGdip02\_Art23")  
  
## 請參閱  
 <xref:System.Drawing.SolidBrush?displayProperty=fullName>   
 <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=fullName>   
 <xref:System.Drawing.TextureBrush?displayProperty=fullName>   
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=fullName>   
 [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [如何：在 Windows Form 上繪製實心矩形](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-rectangle-on-a-windows-form.md)   
 [如何：在 Windows Form 上繪製實心橢圓形](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-ellipse-on-a-windows-form.md)