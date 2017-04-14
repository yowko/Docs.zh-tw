---
title: "如何：使用複合模式控制 Alpha 混色 | Microsoft Docs"
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
  - "Alpha 混色, 複合"
  - "色彩, 混色"
  - "色彩, 控制透明度"
ms.assetid: f331df2d-b395-4b0a-95be-24fec8c9bbb5
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：使用複合模式控制 Alpha 混色
有時候，您可能會想要建立具有下列特性的螢幕外點陣圖：  
  
-   色彩中的 Alpha 值小於 255。  
  
-   建立點陣圖時不要使色彩彼此產生 Alpha 混色。  
  
-   顯示完成的點陣圖時，點陣圖中的色彩已與顯示裝置上的背景色彩產生 Alpha 混色。  
  
 若要建立此類點陣圖，請先建構空白的 <xref:System.Drawing.Bitmap> 物件，然後再根據該點陣圖建構 <xref:System.Drawing.Graphics> 物件。  請將 <xref:System.Drawing.Graphics> 物件的複合模式設定為 <xref:System.Drawing.Drawing2D.CompositingMode?displayProperty=fullName>。  
  
## 範例  
 下列範例根據 <xref:System.Drawing.Bitmap> 物件來建立 <xref:System.Drawing.Graphics> 物件。  程式碼使用 <xref:System.Drawing.Graphics> 物件和兩個半透明筆刷 \(Alpha \= 160\) 在點陣圖上進行塗繪。  程式碼會使用半透明的筆刷來填滿紅色橢圓形和綠色橢圓形。  綠色橢圓形與紅色橢圓形重疊，但是因為 <xref:System.Drawing.Graphics> 物件的複合模式已設定為 <xref:System.Drawing.Drawing2D.CompositingMode>，因此綠色和紅色不會混合。  
  
 程式碼會在螢幕上繪製兩次點陣圖：一次是在白色背景上，一次是在多種色彩的背景上。  屬於這兩個橢圓形一部分的點陣圖中的像素具有 Alpha 元素值 160，因此橢圓形會與螢幕上的背景色彩混合。  
  
 下圖顯示的是程式碼範例的輸出。  請注意，橢圓形會與背景混合，但是不會彼此混合。  
  
 ![原始檔複製](../../../../docs/framework/winforms/advanced/media/sourcecopy.png "sourcecopy")  
  
 程式碼範例中包含此陳述式：  
  
 [!code-csharp[System.Drawing.AlphaBlending#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.AlphaBlending#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#41)]  
  
 如果想要將橢圓形彼此混合，同時也要與背景混合，請將上述陳述式變更如下：  
  
 [!code-csharp[System.Drawing.AlphaBlending#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.AlphaBlending#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#42)]  
  
 下圖顯示的是修改程式碼後的輸出。  
  
 ![原始檔停留](../../../../docs/framework/winforms/advanced/media/sourceover.png "sourceover")  
  
 [!code-csharp[System.Drawing.AlphaBlending#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#43)]
 [!code-vb[System.Drawing.AlphaBlending#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#43)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e` \(即 <xref:System.Windows.Forms.PaintEventHandler> 的參數\)。  
  
## 請參閱  
 <xref:System.Drawing.Color.FromArgb%2A>   
 [Alpha 混色線條和填色](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)