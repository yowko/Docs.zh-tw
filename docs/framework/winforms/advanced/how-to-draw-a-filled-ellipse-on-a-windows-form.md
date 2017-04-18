---
title: "如何：在 Windows Form 上繪製實心橢圓形 | Microsoft Docs"
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
  - "Graphics.FillEllipse"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "圓形, 繪製"
  - "圓形"
  - "繪製, 橢圓形"
  - "橢圓形, 繪製"
  - "表單, 繪製橢圓形"
  - "圖案, 繪製"
ms.assetid: 781db806-950d-4c5b-b022-493f7fd0c4a8
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：在 Windows Form 上繪製實心橢圓形
這個範例會在表單上繪製實心橢圓形。  
  
## 範例  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## 編譯程式碼  
 您不能在 <xref:System.Windows.Forms.Form.Load> 事件處理常式中呼叫這個方法。  如果表單被重新調整或被另一表單遮住，將不會重新繪製表單的內容。  若要自動重新繪製內容，您應覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法。  
  
## 穩固程式設計  
 對任何消耗系統資源的物件 \(例如 <xref:System.Drawing.Brush> 和 <xref:System.Drawing.Graphics> 物件\)，您應一律呼叫 <xref:System.IDisposable.Dispose%2A>。  
  
## 請參閱  
 [Windows Form 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [圖形程式設計入門](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)   
 [Alpha 混色線條和填色](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)   
 [使用筆刷填滿形狀](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)