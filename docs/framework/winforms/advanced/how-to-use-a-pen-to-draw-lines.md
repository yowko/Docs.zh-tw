---
title: "如何：使用畫筆繪製線條 | Microsoft Docs"
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
  - "線條, 繪製"
  - "畫筆, 繪製線條"
ms.assetid: 0828c331-a438-4bdd-a4d6-3ef1e59e8795
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：使用畫筆繪製線條
若要繪製線條，您需要 <xref:System.Drawing.Graphics> 物件和 <xref:System.Drawing.Pen> 物件。  <xref:System.Drawing.Graphics> 物件提供 <xref:System.Drawing.Graphics.DrawLine%2A> 方法，而 <xref:System.Drawing.Pen> 物件則是儲存線條的特性，例如色彩和寬度。  
  
## 範例  
 下列範例會從 \(20, 10\) 到 \(300, 100\) 繪製線條。  第一個陳述式使用 <xref:System.Drawing.Pen.%23ctor%2A> 類別建構函式建立黑色畫筆。  傳遞至 <xref:System.Drawing.Pen.%23ctor%2A> 建構函式的其中一個引數是使用 <xref:System.Drawing.Color.FromArgb%2A> 方法建立的 <xref:System.Drawing.Color> 物件。  用來建立 <xref:System.Drawing.Color> 物件 \(255, 0, 0, 0\) 的值會對應至色彩的  Alpha、紅色、綠色和藍色元素。  這些值會定義不透明的黑色畫筆。  
  
 [!code-csharp[System.Drawing.UsingAPen#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e`\(即 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數\)。  
  
## 請參閱  
 <xref:System.Drawing.Pen>   
 [使用畫筆繪製線條和形狀](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)   
 [GDI\+ 中的畫筆、線條和矩形](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)