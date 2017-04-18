---
title: "如何：建構字型系列和字型 | Microsoft Docs"
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
  - "字型系列, 建構"
  - "字型, 建構"
ms.assetid: d3a4a223-9492-4b54-9afd-db1c31c3cefd
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：建構字型系列和字型
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 會將字樣相同但樣式不同的字型組成字型家族。  例如，Arial 字型家族包含下列字型：  
  
-   Arial Regular  
  
-   Arial Bold  
  
-   Arial Italic  
  
-   Arial Bold Italic  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 使用四種樣式來組成家族：標準、粗體、斜體和粗斜體。  像 *narrow* 和 *rounded* 這些形容詞不被視為是樣式，而是視為家族名稱的一部分。  例如，Arial Narrow 便是具有下列成員的字型家族：  
  
-   Arial Narrow Regular  
  
-   Arial Narrow Bold  
  
-   Arial Narrow Italic  
  
-   Arial Narrow Bold Italic  
  
 在使用 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 繪製文字之前，需要先建構 <xref:System.Drawing.FontFamily> 物件和 <xref:System.Drawing.Font> 物件。  <xref:System.Drawing.FontFamily> 物件會指定字樣 \(例如 Arial\)，而 <xref:System.Drawing.Font> 物件則會指定大小、樣式和單位。  
  
## 範例  
 下列範例將會建構標準樣式、大小為 16 個像素的 Arial 字型。  在下列程式碼中，傳遞至 <xref:System.Drawing.Font.%23ctor%2A> 建構函式的第一個引數是 <xref:System.Drawing.FontFamily> 物件。  第二個引數會以第四個引數所識別的單位指定字型的大小，  第三個引數會識別樣式。  
  
 <xref:System.Drawing.GraphicsUnit> 是 <xref:System.Drawing.GraphicsUnit> 列舉型別的成員，而 <xref:System.Drawing.FontStyle> 是 <xref:System.Drawing.FontStyle> 列舉型別的成員。  
  
 [!code-csharp[System.Drawing.FontsAndText#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.FontsAndText#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#61)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e` \(即 <xref:System.Windows.Forms.PaintEventHandler> 的參數\)。  
  
## 請參閱  
 [使用字型和文字](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)   
 [Windows Form 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)