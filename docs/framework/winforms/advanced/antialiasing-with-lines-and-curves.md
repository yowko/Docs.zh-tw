---
title: "線條和曲線的反鋸齒功能 | Microsoft Docs"
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
  - "消除鋸齒"
  - "消除鋸齒, 平滑模式"
  - "GDI+, 消除鋸齒"
ms.assetid: 810da1a4-c136-4abf-88df-68e49efdd8d4
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 線條和曲線的反鋸齒功能
使用 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 繪製線條時，您必須提供線條的起始點和結束點，但不必提供該線條的個別像素相關資訊。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 與顯示驅動程式軟體搭配以決定必須開啟哪些像素，才可以在特定顯示裝置上顯示該線條。  
  
## 鋸齒  
 舉這條從點 \(4, 2\) 到點 \(16, 10\) 的直色紅線做為範例說明。  假設座標系統的原點在左上角，而度量單位為像素。  同時我們也假設 X 軸指向右方，而 Y 軸則向下延伸。  下圖將顯示在多重色彩背景上繪製的紅色線條的放大檢視畫面。  
  
 ![線條，無反鋸齒](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art33.png "AboutGdip02\_Art33")  
  
 用來呈現線條的紅色像素是不透明的。  這條直線的像素全部都是不透明的。  此類線條繪製方式所產生的線條會出現不規則 \(Jagged\) 外觀，看起來有點像階梯。  這種將線條繪製成階梯狀的技術稱為鋸齒 \(Aliasing\)；這種階梯為理論線條的鋸齒。  
  
## 反鋸齒  
 另一種更為複雜的繪製線條技術是同時使用透明的像素和不透明的像素。  像素將設為純紅色或紅色與背景色彩的混色，但是這需要視像素與線條接近的程度。  此類繪製方式稱為反鋸齒 \(Antialiasing\)，並可產生肉眼便可察覺、更為平滑的線條。  下圖將顯示某些像素將與背景混色以產生反鋸齒線條。  
  
 ![對線條進行反鋸齒處理](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art34.png "AboutGdip02\_Art34")  
  
 反鋸齒 \(亦稱為平滑化\) 也可套用至曲線。  下圖將顯示平滑橢圓形的放大檢視畫面。  
  
 ![對曲線進行反鋸齒處理](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art35.png "AboutGdip02\_Art35")  
  
 下圖將顯示同一個橢圓形的實際大小，一個未使用反鋸齒功能，另一個則使用反鋸齒功能。  
  
 ![反鋸齒功能範例](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art36.gif "AboutGdip02\_Art36")  
  
 若要繪製使用反鋸齒功能的線條和曲線，請建立 <xref:System.Drawing.Graphics> 類別執行個體，並將其 <xref:System.Drawing.Graphics.SmoothingMode%2A> 屬性設定為 <xref:System.Drawing.Drawing2D.SmoothingMode> 或 <xref:System.Drawing.Drawing2D.SmoothingMode>。  然後，呼叫相同 <xref:System.Drawing.Graphics> 類別的其中一個繪圖方法。  
  
 [!code-csharp[LinesCurvesAndShapes#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#81)]
 [!code-vb[LinesCurvesAndShapes#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#81)]  
  
## 請參閱  
 <xref:System.Drawing.Drawing2D.SmoothingMode?displayProperty=fullName>   
 [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [如何：使用文字反鋸齒功能](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)