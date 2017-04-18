---
title: "如何：在 Windows Form 上繪製直排文字 | Microsoft Docs"
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
  - "StringFormat.FormatFlags"
  - "Graphics.DrawString"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "字串 [Windows Form], 描繪垂直的"
  - "文字 [Windows Form], 繪製"
  - "文字 [Windows Form], 描繪垂直的"
  - "文字 [Windows Form], 垂直文字"
ms.assetid: 717a6131-00f6-4373-b574-9894e8317799
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：在 Windows Form 上繪製直排文字
下列程式碼範例會示範如何使用 <xref:System.Drawing.Graphics> 的 <xref:System.Drawing.Graphics.DrawString%2A> 方法，在表單上繪製直排文字。  
  
## 範例  
 [!code-cpp[System.Drawing.ConceptualHowTos#8](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#8)]
 [!code-csharp[System.Drawing.ConceptualHowTos#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#8)]
 [!code-vb[System.Drawing.ConceptualHowTos#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#8)]  
  
## 編譯程式碼  
 您不能在 <xref:System.Windows.Forms.Form.Load> 事件處理常式中呼叫這個方法。  如果表單被重新調整或被另一表單遮住，將不會重新繪製表單的內容。  若要自動重新繪製內容，您應覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法。  
  
## 穩固程式設計  
 下列情形可能會造成例外狀況 \(Exception\)：  
  
-   未安裝 Arial 字型  
  
## 請參閱  
 <xref:System.Drawing.Graphics.DrawString%2A>   
 <xref:System.Drawing.StringFormat.FormatFlags%2A>   
 <xref:System.Drawing.StringFormatFlags>   
 <xref:System.Windows.Forms.Control.OnPaint%2A>   
 [圖形程式設計入門](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)   
 [使用字型和文字](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)