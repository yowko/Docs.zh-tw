---
title: "如何：取得字型度量資訊 | Microsoft Docs"
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
  - "字型度量資訊, 取得"
  - "字型, 取得度量資訊"
ms.assetid: ff7c0616-67f7-4fa2-84ee-b8d642f2b09b
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：取得字型度量資訊
<xref:System.Drawing.FontFamily> 類別提供下列方法，用來擷取特定家族\/樣式組合的各種度量資訊 \(Metric\)：  
  
-   <xref:System.Drawing.FontFamily.GetEmHeight%2A> \(FontStyle\)  
  
-   <xref:System.Drawing.FontFamily.GetCellAscent%2A> \(FontStyle\)  
  
-   <xref:System.Drawing.FontFamily.GetCellDescent%2A> \(FontStyle\)  
  
-   <xref:System.Drawing.FontFamily.GetLineSpacing%2A> \(FontStyle\)  
  
 這些方法傳回來的數字是以字型設計單位為其單位，因此與特定 <xref:System.Drawing.Font> 物件的大小和單位無關。  
  
 下圖顯示的是不同的矩陣。  
  
 ![字型文字](../../../../docs/framework/winforms/advanced/media/fontstext7a.png "fontstext7A")  
  
## 範例  
 下列範例會顯示 Arial 字型家族標準樣式的矩陣。  程式碼也會建立大小為 16 個像素的 <xref:System.Drawing.Font> 物件 \(根據 Arial 家族\)，並顯示該特定 <xref:System.Drawing.Font> 物件的度量資訊 \(以像素為單位\)。  
  
 下圖顯示的是範例程式碼的輸出。  
  
 ![字型文字](../../../../docs/framework/winforms/advanced/media/csfontstext8.png "csFontsText8")  
  
 請注意上圖中輸出的最前面兩行。  <xref:System.Drawing.Font> 物件會傳回 16 個像素的大小，而 <xref:System.Drawing.FontFamily> 物件則是傳回 2,048 em 高度。  這兩個數字 \(16 和 2,048\) 是在字型設計單位和 <xref:System.Drawing.Font> 物件單位 \(在這個範例中為像素\) 之間轉換的關鍵。  
  
 例如，您可以依照下列方式，將上升部分從設計單位轉換為像素：  
  
 ![字型文字](../../../../docs/framework/winforms/advanced/media/fontstext9.png "FontsText9")  
  
 下列程式碼藉由設定 <xref:System.Drawing.PointF> 物件的 <xref:System.Drawing.PointF.Y%2A> 資料成員，來垂直放置文字。  每一個新文字行的 Y 座標都會增加 `font.Height`。  <xref:System.Drawing.Font> 物件的 <xref:System.Drawing.Font.Height%2A> 屬性會傳回該特定 <xref:System.Drawing.Font> 物件的行距 \(以像素為單位\)。  在這個範例中，<xref:System.Drawing.Font.Height%2A> 傳回的數字是 19。  請注意，這個數字與轉換行距度量資訊為像素時所取得的數字 \(四捨五入為整數\) 相同。  
  
 請注意，em 高度 \(也稱為大小或 em 大小\) 不是上升部分和下降部分的總和。  上升部分和下降部分的總和稱為儲存格高度。  儲存格高度減去內部前置字元就等於 em 高度。  儲存格高度加上外部前置字元等於行距。  
  
 [!code-csharp[System.Drawing.FontsAndText#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.FontsAndText#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#71)]  
  
## 編譯程式碼  
 前述範例是專為與 Windows Form 搭配使用而設計的，而且它需要有 <xref:System.Windows.Forms.PaintEventArgs> `e` \(這是 <xref:System.Windows.Forms.PaintEventHandler> 的參數\)。  
  
## 請參閱  
 [Windows Form 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [使用字型和文字](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)