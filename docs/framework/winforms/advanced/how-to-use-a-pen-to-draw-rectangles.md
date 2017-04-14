---
title: "如何：使用畫筆繪製矩形 | Microsoft Docs"
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
  - "畫筆, 繪製矩形"
  - "矩形, 繪製"
ms.assetid: 54a7fa14-3ad8-4d64-b424-2a12005b250c
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：使用畫筆繪製矩形
若要繪製矩形，您需要 <xref:System.Drawing.Graphics> 物件和 <xref:System.Drawing.Pen> 物件。  <xref:System.Drawing.Graphics> 物件提供 <xref:System.Drawing.Graphics.DrawRectangle%2A> 方法，而 <xref:System.Drawing.Pen> 物件則是儲存線條的特性，例如色彩和寬度。  
  
## 範例  
 下列範例會繪製左上角位於 \(10, 10\) 的矩形。  矩形的寬度為 100 且高度為 50。  傳遞至 <xref:System.Drawing.Pen.%23ctor%2A> 建構函式的第二個引數表示畫筆寬度為 5 像素。  
  
 繪製矩形時，會將畫筆置於矩形界限的中央。  由於畫筆寬度為 5，因此繪製矩形四邊的寬度為 5 個像素，其中 1 個像素用來繪製界限，2 個像素繪製在內側，還有 2 個像素繪製在外側。  如需畫筆對齊的詳細資訊，請參閱 [如何：設定畫筆寬度和對齊](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md)。  
  
 下圖顯示的是產生的矩形。  虛線顯示的是當畫筆寬度為 1 個像素時所繪製的矩形。  矩形左上角的放大檢視顯示黑色粗線是置於虛線的中央。  
  
 ![畫筆](../../../../docs/framework/winforms/advanced/media/pens1.png "pens1")  
  
 [!code-csharp[System.Drawing.UsingAPen#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingAPen#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#21)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e`\(即 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數\)。  
  
## 請參閱  
 [使用畫筆繪製線條和形狀](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)