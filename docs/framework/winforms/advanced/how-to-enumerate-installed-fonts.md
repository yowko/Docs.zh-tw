---
title: "如何：列舉已安裝的字型 | Microsoft Docs"
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
  - "範例 [Windows Form], 字型"
  - "字型, 列舉安裝的"
ms.assetid: 26d74ef5-0f39-4eeb-8d20-00e66e014abe
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：列舉已安裝的字型
<xref:System.Drawing.Text.InstalledFontCollection> 類別繼承自 <xref:System.Drawing.Text.FontCollection> 抽象基底類別。  您可以使用 <xref:System.Drawing.Text.InstalledFontCollection> 物件來列舉安裝在電腦上的字型。  <xref:System.Drawing.Text.InstalledFontCollection> 物件的 <xref:System.Drawing.Text.FontCollection.Families%2A> 屬性是 <xref:System.Drawing.FontFamily> 物件的陣列。  
  
## 範例  
 下列範例會列出安裝在電腦上的所有字型家族名稱清單。  程式碼將會擷取 <xref:System.Drawing.Text.FontCollection.Families%2A> 屬性所傳回的陣列中的每個 <xref:System.Drawing.FontFamily> 物件的 <xref:System.Drawing.FontFamily.Name%2A> 屬性。  由於家族名稱是擷取而來的，因此可將它們串連起來形成以逗號分隔的清單。  接著 <xref:System.Drawing.Graphics> 類別的 <xref:System.Drawing.Graphics.DrawString%2A> 方法會在矩形中繪製以逗號分隔的清單。  
  
 如果執行上述程式碼，它的輸出將會類似於下圖中所顯示的內容。  
  
 ![已安裝字型](../../../../docs/framework/winforms/advanced/media/csfontstext6.png "csfontstext6")  
  
 [!code-csharp[System.Drawing.FontsAndText#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.FontsAndText#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#11)]  
  
## 編譯程式碼  
 前述範例是專為與 Windows Form 搭配使用而設計的，而且它需要有 <xref:System.Windows.Forms.PaintEventArgs> `e` \(這是 <xref:System.Windows.Forms.PaintEventHandler> 的參數\)。  此外，您應該匯入 <xref:System.Drawing.Text> 命名空間。  
  
## 請參閱  
 [使用字型和文字](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)