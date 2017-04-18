---
title: "如何：使用文字反鋸齒功能 | Microsoft Docs"
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
  - "消除鋸齒, 與文字一起使用"
  - "字串 [Windows Form], 在描繪時消除鋸齒"
  - "字串 [Windows Form], 平滑描繪"
  - "文字 [Windows Form], 消除鋸齒"
  - "文字 [Windows Form], 平滑"
ms.assetid: 48fc34f3-f236-4b01-a0cb-f0752e6d22ae
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：使用文字反鋸齒功能
*反鋸齒*是指讓繪圖和文字的鋸齒邊緣變得平滑，以改善其外觀或可讀性。  藉由使用 Managed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 類別，您可以呈現高品質的反鋸齒文字，也可以呈現較低品質的文字。  一般而言，較高品質的呈現比較低品質的呈現需要較長的處理時間。  若要設定文字品質等級，請將 <xref:System.Drawing.Graphics> 的 <xref:System.Drawing.Graphics.TextRenderingHint%2A> 屬性設為 <xref:System.Drawing.Text.TextRenderingHint> 列舉型別的其中一個元素。  
  
## 範例  
 下列程式碼範例會使用兩種不同的品質設定來繪製文字。  
  
 下圖顯示的是範例程式碼的輸出。  
  
 ![字型文字](../../../../docs/framework/winforms/advanced/media/fontstext10.png "FontsText10")  
  
 [!code-csharp[System.Drawing.FontsAndText#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
  
## 編譯程式碼  
 上述程式碼範例是專為與 Windows Form 搭配使用而設計的，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e` \(即 <xref:System.Windows.Forms.PaintEventHandler> 的參數\)。  
  
## 請參閱  
 [使用字型和文字](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)