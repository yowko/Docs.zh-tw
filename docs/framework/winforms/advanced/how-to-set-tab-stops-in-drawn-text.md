---
title: "如何：在已繪製的文字中設定定位停駐點 | Microsoft Docs"
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
  - "索引標籤, 描繪的文字"
  - "文字, 以包含定位停駐點的方式描繪"
ms.assetid: 64878f98-39ba-4303-b63f-0859ab682eeb
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：在已繪製的文字中設定定位停駐點
您可以經由呼叫 <xref:System.Drawing.StringFormat> 物件的 <xref:System.Drawing.StringFormat.SetTabStops%2A> 方法，然後將該 <xref:System.Drawing.StringFormat> 物件傳遞至 <xref:System.Drawing.Graphics> 類別的 <xref:System.Drawing.Graphics.DrawString%2A> 方法，以設定文字的定位停駐點。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer?displayProperty=fullName> 不支援將定位停駐點加入至繪製的文字，但您可以使用 <xref:System.Windows.Forms.TextFormatFlags?displayProperty=fullName> 旗標擴充現有的定位停駐點。  
  
## 範例  
 下列範例會在 150、250 和 350 設定定位停駐點。  然後程式碼會顯示名稱和考試成績的索引標籤式清單。  
  
 下圖顯示的是索引標籤式文字。  
  
 ![字型文字](../../../../docs/framework/winforms/advanced/media/fontstext4.png "fontstext4")  
  
 下列程式碼會將兩個引數傳遞至 <xref:System.Drawing.StringFormat.SetTabStops%2A> 方法。  第二個引數是包含定位點位移 \(Offset\) 的陣列。  傳遞至 <xref:System.Drawing.StringFormat.SetTabStops%2A> 第一個引數是 0，表示陣列中的第一個位移是從週框左邊緣的位置 0 開始測量。  
  
 [!code-csharp[System.Drawing.FontsAndText#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## 編譯程式碼  
  
-   前述範例是專為與 Windows Form 搭配使用而設計的，而且它需要有 <xref:System.Windows.Forms.PaintEventArgs> `e` \(這是 <xref:System.Windows.Forms.PaintEventHandler> 的參數\)。  
  
## 請參閱  
 [使用字型和文字](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)   
 [如何：使用 GDI 繪製文字](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)