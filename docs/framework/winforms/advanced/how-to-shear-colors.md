---
title: "如何：切變色彩 | Microsoft Docs"
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
  - "色彩, 切變"
  - "色彩, 具有色彩矩陣的轉換"
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：切變色彩
切變會將色彩元素增加或減少另一個色彩元素一定比例的量。  例如，將紅色元素增加藍色元素值的一半就屬於這類轉換。  在這類轉換中，色彩 \(0.2, 0.5, 1\) 會變成色彩 \(0.7, 0.5, 1\)。  新的紅色元素為 0.2 \+ \(1\/2\)\(1\) \= 0.7。  
  
## 範例  
 下列範例會從 ColorBars4.bmp 檔案建構 <xref:System.Drawing.Image> 物件。  然後程式碼會將上一段中所描述的切變轉換套用於影像中的每一個像素。  
  
 下圖左邊顯示的是原始的影像，右邊顯示的是切變的影像。  
  
 ![分歧色彩](../../../../docs/framework/winforms/advanced/media/colortrans6.png "colortrans6")  
  
 下表會列出切變轉換前後四列的色彩向量。  
  
|原始|切變後|  
|--------|---------|  
|\(0, 0, 1, 1\)|\(0.5, 0, 1, 1\)|  
|\(0.5, 1, 0.5, 1\)|\(0.75, 1, 0.5, 1\)|  
|\(1, 1, 0, 1\)|\(1, 1, 0, 1\)|  
|\(0.4, 0.4, 0.4, 1\)|\(0.6, 0.4, 0.4, 1\)|  
  
 [!code-csharp[System.Drawing.Misc3#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e`\(即 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數\)。  請以系統中有效的影像名稱和路徑來取代 `ColorBars.bmp`。  
  
## 請參閱  
 <xref:System.Drawing.Imaging.ColorMatrix>   
 <xref:System.Drawing.Imaging.ImageAttributes>   
 [Windows Form 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [將影像重新著色](../../../../docs/framework/winforms/advanced/recoloring-images.md)