---
title: "如何：在 Windows Form 上繪製實心矩形 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Graphics.FillRectangle"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "繪製矩形"
  - "繪製, 矩形"
  - "矩形, 繪製"
ms.assetid: d656a93c-987d-4809-aafd-493fe17450f0
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：在 Windows Form 上繪製實心矩形
這個範例會在表單上繪製實心矩形。  
  
## 範例  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## 編譯程式碼  
 您不能在 <xref:System.Windows.Forms.Form.Load> 事件處理常式中呼叫這個方法。  如果表單被重新調整或被另一表單遮住，將不會重新繪製表單的內容。  若要自動重新繪製內容，您應覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法。  
  
## 穩固程式設計  
 對任何消耗系統資源的物件 \(例如 <xref:System.Drawing.Brush> 和 <xref:System.Drawing.Graphics> 物件\)，您應一律呼叫 <xref:System.IDisposable.Dispose%2A>。  
  
## 請參閱  
 <xref:System.Drawing.Graphics.FillRectangle%2A>   
 <xref:System.Windows.Forms.Control.OnPaint%2A>   
 [圖形程式設計入門](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)   
 [Windows Form 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [使用畫筆繪製線條和形狀](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)   
 [GDI\+ 中的筆刷和填滿的形狀](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)