---
title: "Alpha 混色線條和填色 | Microsoft Docs"
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
  - "Alpha 混色"
  - "Alpha 混色, 與填入一起使用"
  - "Alpha 混色, 與線條一起使用"
  - "範例 [Windows Form], Alpha 混色"
  - "填入, Alpha 混色"
  - "線條, 加入透明度"
  - "線條, Alpha 混色"
  - "圖案, 加入透明度"
ms.assetid: 5440f48c-3ac9-44c3-b170-c1c110bdbab8
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Alpha 混色線條和填色
在 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 中，色彩是 32 位元值，各以 8 個位元來表示 Alpha、紅色、綠色和藍色。  Alpha 值表示色彩的透明度，也就是色彩與背景色彩混合的程度。  Alpha 值的範圍從 0 到 255，0 表示完全透明的色彩，255 則表示完全不透明的色彩。  
  
 Alpha 混色是依照像素混合來源色彩和背景色彩資料。  指定來源色彩中的每一個元素 \(紅色、綠色、藍色\) 都會根據下列公式與背景色彩中的對應元素混合：  
  
 displayColor \= sourceColor × alpha \/ 255 \+ backgroundColor × \(255 – alpha\) \/ 255  
  
 例如，假設來源色彩的紅色元素為 150，背景色彩的紅色元素為 100。  如果 Alpha 值為 200，則產生色彩的紅色元素計算方式如下：  
  
 150 × 200 \/ 255 \+ 100 × \(255 – 200\) \/ 255 \= 139  
  
## 在本節中  
 [如何：繪製不透明和半透明線條](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)  
 示範如何繪製 Alpha 混色線條。  
  
 [如何：使用不透明和半透明筆刷繪製](../../../../docs/framework/winforms/advanced/how-to-draw-with-opaque-and-semitransparent-brushes.md)  
 解說如何以筆刷繪製 Alpha 混色。  
  
 [如何：使用複合模式控制 Alpha 混色](../../../../docs/framework/winforms/advanced/how-to-use-compositing-mode-to-control-alpha-blending.md)  
 說明如何使用 <xref:System.Drawing.Drawing2D.CompositingMode> 以控制 Alpha 混色。  
  
 [如何：使用色彩矩陣設定影像中的 Alpha 值](../../../../docs/framework/winforms/advanced/how-to-use-a-color-matrix-to-set-alpha-values-in-images.md)  
 解說如何使用 <xref:System.Drawing.Imaging.ColorMatrix> 物件以控制 Alpha 混色。