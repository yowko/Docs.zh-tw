---
title: "向量圖形概觀 | Microsoft Docs"
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
  - "座標系統"
  - "圖形, 向量圖形"
  - "內含到內含端點"
ms.assetid: 0195df81-66be-452d-bb53-5a582ebfdc09
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 向量圖形概觀
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 在座標系統上繪製線條、矩形和其他形狀。  您可以選擇各種座標系統，但預設的座標系統具有原點，位置在指向右方的 X 軸和指向下方的 Y 軸的左上角處。  預設座標的度量單位為像素。  
  
## GDI\+ 建置區塊  
 ![向量圖形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art01.png "AboutGdip02\_Art01")  
  
 電腦監視器在名為圖片元素或像素的點矩形陣列 \(Rectangular Array\) 上建立自己的顯示。  每個監視器在螢幕上出現的像素數目會有所不同，通常使用者可設定個別監視器上出現的像素數目。  
  
 ![向量圖形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art02.png "AboutGdip02\_Art02")  
  
 當您使用 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 來繪製線條、矩形或曲線時，必須提供要繪製項目的某些重要資訊。  例如，您可以提供兩個點來指定線條範圍，也可以提供點、高度和寬度來指定矩形範圍。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 是與顯示驅動程式軟體搭配使用，來決定必須開啟哪些像素才可顯示該線條、矩形或曲線。  下圖將說明為顯示從點 \(4, 2\) 到點 \(12, 8\) 的線條所啟用的像素。  
  
 ![向量圖形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art03.png "AboutGdip02\_Art03")  
  
 時間將會證明某些基本的建置組塊最適合用來建立 2\-D 圖片。  下列清單即說明這些 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 支援的建置區塊：  
  
-   程式行  
  
-   矩形  
  
-   橢圓形  
  
-   弧形  
  
-   多邊形  
  
-   基本曲線  
  
-   貝茲曲線  
  
## 使用圖形物件的繪圖方法  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 中的 <xref:System.Drawing.Graphics> 類別提供下列方法來繪製上述清單中的項目：<xref:System.Drawing.Graphics.DrawLine%2A>、<xref:System.Drawing.Graphics.DrawRectangle%2A>、<xref:System.Drawing.Graphics.DrawEllipse%2A>、<xref:System.Drawing.Graphics.DrawPolygon%2A>、<xref:System.Drawing.Graphics.DrawArc%2A>、<xref:System.Drawing.Graphics.DrawCurve%2A> \(用於基本曲線\) 和 <xref:System.Drawing.Graphics.DrawBezier%2A>。  這些方法都為多載；也就是說，所有方法都支援數個不同的參數清單。  例如，<xref:System.Drawing.Graphics.DrawLine%2A> 方法的其中一個變異可接收一個 <xref:System.Drawing.Pen> 物件和四個整數，而 <xref:System.Drawing.Graphics.DrawLine%2A> 方法的另一個變異則可接收一個 <xref:System.Drawing.Pen> 物件和兩個 <xref:System.Drawing.Point> 物件。  
  
 繪製線條、矩形和貝茲曲線的方法包含許多可在單一呼叫中繪製數個項目的搭配方法：<xref:System.Drawing.Graphics.DrawLines%2A>、<xref:System.Drawing.Graphics.DrawRectangles%2A> 和 <xref:System.Drawing.Graphics.DrawBeziers%2A>。  此外，<xref:System.Drawing.Graphics.DrawCurve%2A> 方法有一個搭配方法：<xref:System.Drawing.Graphics.DrawClosedCurve%2A>，它可將曲線的結束點連接到起始點以封閉曲線。  
  
 <xref:System.Drawing.Graphics> 類別的所有繪圖方法都可與 <xref:System.Drawing.Pen> 物件搭配使用。  若要繪製任何項目，至少必須建立兩個物件：<xref:System.Drawing.Graphics> 物件和 <xref:System.Drawing.Pen> 物件。  <xref:System.Drawing.Pen> 物件會儲存屬性，例如要繪製項目的線條寬度和色彩。  <xref:System.Drawing.Pen> 物件會當成其中一個引數傳遞給繪圖方法。  例如，<xref:System.Drawing.Graphics.DrawLine%2A> 方法的其中一個變異可接收一個 <xref:System.Drawing.Pen> 物件和四個整數，如下例所示，它將繪製寬度為 100、高度為 50 以及左上角為 \(20, 10\) 的矩形：  
  
 [!code-csharp[LinesCurvesAndShapes#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#11)]
 [!code-vb[LinesCurvesAndShapes#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#11)]  
  
## 請參閱  
 <xref:System.Drawing.Graphics?displayProperty=fullName>   
 <xref:System.Drawing.Pen?displayProperty=fullName>   
 [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [如何：建立繪製的圖形物件](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)