---
title: "限制 GDI+ 中的繪圖介面 | Microsoft Docs"
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
  - "裁剪, 使用 GDI+"
  - "GDI+, 裁剪"
  - "GDI+, 限制繪圖介面"
ms.assetid: 8b5f71d9-d2f0-4540-9c41-740f90fd4c26
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 限制 GDI+ 中的繪圖介面
裁剪是指限制對特定矩形或區域進行繪製。  下圖將顯示 "Hello" 字串被裁剪為心形的區域。  
  
 ![受限制的繪圖介面](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art30.png "AboutGdip02\_Art30")  
  
## 使用區域的裁剪  
 區域可從路徑建立，而路徑中可包含字串的字型外框，因此您可以使用外框文字來進行裁剪。  下圖將顯示裁減為文字字串內景的一組同心橢圓形。  
  
 ![受限制的繪圖介面](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art31.png "AboutGdip02\_Art31")  
  
 若要使用裁剪來進行繪製，請建立 <xref:System.Drawing.Graphics> 物件、設定其 <xref:System.Drawing.Graphics.Clip%2A> 屬性，然後呼叫相同 <xref:System.Drawing.Graphics> 物件的繪製方法：  
  
 [!code-csharp[LinesCurvesAndShapes#91](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#91)]
 [!code-vb[LinesCurvesAndShapes#91](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#91)]  
  
## 請參閱  
 <xref:System.Drawing.Graphics?displayProperty=fullName>   
 <xref:System.Drawing.Region?displayProperty=fullName>   
 [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [使用區域](../../../../docs/framework/winforms/advanced/using-regions.md)