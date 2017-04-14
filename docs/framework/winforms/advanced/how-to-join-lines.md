---
title: "如何：聯結線條 | Microsoft Docs"
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
  - "斜面框線聯結樣式"
  - "繪製, 連接線"
  - "圖形, 連接線"
  - "GraphicsPath 物件"
  - "線聯結"
  - "線條, 聯結"
  - "斜接線條聯結樣式"
  - "Pen 類別"
  - "圓角線條聯結樣式"
ms.assetid: 9fc480c2-3c75-4fd1-8ab5-296a99e820e2
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：聯結線條
線條聯結是指兩端相連或重疊的兩條線所形成的共同區域。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供三種線條聯結樣式：斜接、斜切和圓角。  線條聯結樣式是 <xref:System.Drawing.Pen> 類別的屬性。  當您指定 <xref:System.Drawing.Pen> 物件的線條聯結樣式時，會將該聯結樣式套用至使用該畫筆繪製的任何 <xref:System.Drawing.Drawing2D.GraphicsPath> 物件中的所有連接線。  
  
 下圖顯示的是斜切線聯結範例結果。  
  
 ![畫筆](../../../../docs/framework/winforms/advanced/media/pens5.png "pens5")  
  
## 範例  
 您可以使用 <xref:System.Drawing.Pen> 類別的 <xref:System.Drawing.Pen.LineJoin%2A> 屬性來指定線條聯結樣式。  下列範例示範水平線和垂直線之間的斜切線聯結。  在下列程式碼中，指派給 <xref:System.Drawing.Pen.LineJoin%2A> 屬性的值 <xref:System.Drawing.Drawing2D.LineJoin> 是 <xref:System.Drawing.Drawing2D.LineJoin> 列舉型別的成員。  <xref:System.Drawing.Drawing2D.LineJoin> 列舉型別的其他成員為 <xref:System.Drawing.Drawing2D.LineJoin> 和 <xref:System.Drawing.Drawing2D.LineJoin>。  
  
 [!code-csharp[System.Drawing.UsingAPen#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingAPen#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#31)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e` \(即 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數\)。  
  
## 請參閱  
 [使用畫筆繪製線條和形狀](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)