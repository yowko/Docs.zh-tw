---
title: "如何：繪製外框形狀 | Microsoft Docs"
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
  - "Graphics.DrawEllipse"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "圓形"
  - "圓形, 繪製"
  - "圓形"
  - "繪製, 圓形"
  - "繪製, 圖案"
  - "橢圓形, 繪製"
  - "表單, 描繪圓形"
  - "外框圖案, 繪製"
  - "外框圖案, 範例"
  - "圖案, 繪製"
ms.assetid: f4f9214c-607e-407d-8cdd-6549f0278451
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：繪製外框形狀
這個範例會在表單上繪製橢圓形外框和矩形外框。  
  
## 範例  
 [!code-cpp[System.Drawing.ConceptualHowTos#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#6)]
 [!code-csharp[System.Drawing.ConceptualHowTos#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#6)]
 [!code-vb[System.Drawing.ConceptualHowTos#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#6)]  
  
## 編譯程式碼  
 您不能在 <xref:System.Windows.Forms.Form.Load> 事件處理常式中呼叫這個方法。  如果表單被重新調整或被另一表單遮住，將不會重新繪製表單的內容。  若要自動重新繪製內容，您應覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法。  
  
## 穩固程式設計  
 對任何消耗系統資源的物件 \(例如 <xref:System.Drawing.Pen> 和 <xref:System.Drawing.Graphics> 物件\)，您應一律呼叫 <xref:System.IDisposable.Dispose%2A>。  
  
## 請參閱  
 <xref:System.Drawing.Graphics.DrawEllipse%2A>   
 <xref:System.Windows.Forms.Control.OnPaint%2A>   
 <xref:System.Drawing.Graphics.DrawRectangle%2A>   
 [圖形程式設計入門](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)   
 [使用畫筆繪製線條和形狀](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)   
 [Windows Form 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)