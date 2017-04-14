---
title: "GDI+ 中的多邊形 | Microsoft Docs"
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
  - "繪製, 多邊形"
  - "GDI+, 多邊形"
  - "多邊形"
ms.assetid: a72213d2-d69a-4c2b-a75c-be7b20390c13
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# GDI+ 中的多邊形
多邊形是指具有三個或三個以上直邊的封閉型形狀。  例如，三角形便是一個具有三個直邊的多邊形，矩形是具有四個邊的多邊形，五角形是具有五個邊的多邊形。  下圖將顯示數個多邊形。  
  
 ![多邊形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art07.png "Aboutgdip02\_art07")  
  
## 繪製多邊形  
 若要繪製多邊形，您需要 <xref:System.Drawing.Graphics> 物件、<xref:System.Drawing.Pen> 物件和 <xref:System.Drawing.Point> 物件陣列 \(或 <xref:System.Drawing.PointF> 物件陣列\)。  <xref:System.Drawing.Graphics> 物件提供 <xref:System.Drawing.Graphics.DrawPolygon%2A> 方法。  <xref:System.Drawing.Pen> 物件儲存產生多邊形的線條屬性，例如寬度和色彩，而 <xref:System.Drawing.Point> 物件陣列則是儲存直線所連接的各點。  <xref:System.Drawing.Pen> 物件和 <xref:System.Drawing.Point> 物件陣列會當成引數傳遞至 <xref:System.Drawing.Graphics.DrawPolygon%2A> 方法。  下列範例即繪製三邊的多邊形。  請注意， `myPointArray` 中只有三個點：\(0, 0\)、\(50, 30\) 和 \(30, 60\)。  <xref:System.Drawing.Graphics.DrawPolygon%2A> 方法會繪製一條線從 \(30, 60\) 返回至起始點 \(0, 0\)，藉此自動封閉多邊形。  
  
 [!code-csharp[LinesCurvesAndShapes#111](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#111)]
 [!code-vb[LinesCurvesAndShapes#111](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#111)]  
  
 下圖顯示該多邊形。  
  
 ![多邊形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art08.png "Aboutgdip02\_art08")  
  
## 請參閱  
 <xref:System.Drawing.Graphics?displayProperty=fullName>   
 <xref:System.Drawing.Pen?displayProperty=fullName>   
 [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [如何：建立畫筆](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)