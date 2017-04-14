---
title: "如何：建立垂直文字 | Microsoft Docs"
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
  - "字串 [Windows Form], 描繪垂直的"
  - "文字 [Windows Form], 描繪垂直的"
  - "垂直文字, 繪製"
  - "Windows Form, 繪製垂直文字"
ms.assetid: 50c69046-4188-47d9-b949-cc2610ffd337
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：建立垂直文字
您可以使用 <xref:System.Drawing.StringFormat> 物件指定以垂直而非水平方式繪製文字。  
  
## 範例  
 下列範例會將 <xref:System.Drawing.StringFormatFlags> 值指派給 <xref:System.Drawing.StringFormat> 物件的 <xref:System.Drawing.StringFormat.FormatFlags%2A> 屬性。  這個 <xref:System.Drawing.StringFormat> 物件會傳遞給 <xref:System.Drawing.Graphics> 類別的 <xref:System.Drawing.Graphics.DrawString%2A> 方法。  <xref:System.Drawing.StringFormatFlags> 值是 <xref:System.Drawing.StringFormatFlags> 列舉型別的成員。  
  
 下圖顯示的是垂直文字。  
  
 ![字型文字](../../../../docs/framework/winforms/advanced/media/csfontstext5.png "csfontstext5")  
  
 [!code-csharp[System.Drawing.FontsAndText#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## 編譯程式碼  
  
-   上述範例是專為與 Windows Form 搭配使用而設計的，而且需要 <xref:System.Windows.Forms.PaintEventArgs> `e`  \(即 <xref:System.Windows.Forms.PaintEventHandler> 的參數\)。  
  
## 請參閱  
 [如何：使用 GDI 繪製文字](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)