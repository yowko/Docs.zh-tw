---
title: "如何：在 Windows Form 上繪製文字 | Microsoft Docs"
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
  - "表單, 繪製文字"
  - "文字, 繪製"
ms.assetid: 5d2447a9-21a1-4adc-b954-5516f2bb9b2c
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：在 Windows Form 上繪製文字
下列程式碼範例示範如何使用 <xref:System.Drawing.Graphics> 的 <xref:System.Drawing.Graphics.DrawString%2A> 方法，在表單上繪製文字。  此外，您也可以使用 <xref:System.Windows.Forms.TextRenderer> 在表單上繪製文字。  如需詳細資訊，請參閱 [如何：使用 GDI 繪製文字](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)。  
  
## 範例  
 [!code-cpp[System.Drawing.ConceptualHowTos#7](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#7)]
 [!code-csharp[System.Drawing.ConceptualHowTos#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#7)]
 [!code-vb[System.Drawing.ConceptualHowTos#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#7)]  
  
## 編譯程式碼  
 您不能在 <xref:System.Windows.Forms.Form.Load> 事件處理常式中呼叫 <xref:System.Drawing.Graphics.DrawString%2A> 方法。  如果表單被重新調整或被另一表單遮住，將不會重新繪製表單的內容。  若要自動重新繪製內容，您應覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法。  
  
## 穩固程式設計  
 下列情形可能會造成例外狀況 \(Exception\)：  
  
-   未安裝 Arial 字型  
  
## 請參閱  
 <xref:System.Drawing.Graphics.DrawString%2A>   
 <xref:System.Windows.Forms.TextRenderer.DrawText%2A>   
 <xref:System.Drawing.StringFormat.FormatFlags%2A>   
 <xref:System.Drawing.StringFormatFlags>   
 <xref:System.Windows.Forms.TextFormatFlags>   
 <xref:System.Windows.Forms.Control.OnPaint%2A>   
 [圖形程式設計入門](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)   
 [如何：使用 GDI 繪製文字](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)