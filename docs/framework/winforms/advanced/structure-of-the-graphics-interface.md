---
title: "圖形介面的結構 | Microsoft Docs"
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
  - "GDI+, 使用 Managed 介面"
  - "圖形, 類別結構"
ms.assetid: 010a1e46-656b-40a1-8d5d-87aa05ee1243
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 圖形介面的結構
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 的 Managed 類別介面約有 60 個類別、50 個列舉型別 \(Enumeration\) 和 8 個結構。  <xref:System.Drawing.Graphics> 類別是 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 功能的核心，它是實際繪製線條、曲線、圖形、影像和文字的類別。  
  
## 重要類別  
 許多類別都可與 <xref:System.Drawing.Graphics> 類別搭配使用。  例如，<xref:System.Drawing.Graphics.DrawLine%2A> 方法接收 <xref:System.Drawing.Pen> 物件，此物件會保留繪製的線條屬性 \(色彩、寬度、虛線樣式等等\)。  <xref:System.Drawing.Graphics.FillRectangle%2A> 方法可接收 <xref:System.Drawing.Drawing2D.LinearGradientBrush> 物件的指標，這個物件若與 <xref:System.Drawing.Graphics> 物件搭配使用，便可使用漸層色彩來填滿矩形。  <xref:System.Drawing.Font> 和 <xref:System.Drawing.StringFormat> 物件則會影響 <xref:System.Drawing.Graphics> 物件繪製文字的方式。  <xref:System.Drawing.Drawing2D.Matrix> 物件可儲存和管理 <xref:System.Drawing.Graphics> 物件的全局轉換，後者是用來旋轉影像、調整影像的比例和翻轉影像。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 在組織圖形資料方面提供了數種架構 \(例如 <xref:System.Drawing.Rectangle>、<xref:System.Drawing.Point> 和 <xref:System.Drawing.Size>\)。  同時還有一些類別主要做為結構化資料型別。  例如，<xref:System.Drawing.Imaging.BitmapData> 類別是 <xref:System.Drawing.Bitmap> 類別的 Helper，而 <xref:System.Drawing.Drawing2D.PathData> 類別則是 <xref:System.Drawing.Drawing2D.GraphicsPath> 類別的 Helper。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 定義了數種列舉型別，這些列舉型別是相關常數的集合。  例如，<xref:System.Drawing.Drawing2D.LineJoin> 列舉型別包含 <xref:System.Drawing.Drawing2D.LineJoin>、<xref:System.Drawing.Drawing2D.LineJoin> 和 <xref:System.Drawing.Drawing2D.LineJoin> 項目，這些項目可指定用來聯結 \(Join\) 兩條線的樣式。  
  
## 請參閱  
 [圖形概觀](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)   
 [關於 GDI\+ Managed 程式碼](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)   
 [使用 Managed 圖形類別](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)