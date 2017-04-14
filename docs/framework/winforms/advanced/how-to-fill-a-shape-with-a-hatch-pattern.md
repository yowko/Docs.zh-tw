---
title: "如何：以規劃圖樣填滿形狀 | Microsoft Docs"
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
  - "筆刷, 使用規劃筆刷"
  - "模式, 加入到圖案"
  - "圖案, 以圖樣填滿"
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：以規劃圖樣填滿形狀
規劃圖樣是由兩個色彩組成：一個是背景的色彩，另一個是在背景上形成圖樣的線條色彩。  若要使用規劃圖樣填滿封閉形狀，請使用 <xref:System.Drawing.Drawing2D.HatchBrush> 物件。  下列範例將說明如何使用規劃圖樣填滿橢圓形：  
  
## 範例  
 <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> 建構函式有三個引數：規劃樣式、規劃線條的色彩和背景色彩。  規劃樣式引數可以是 <xref:System.Drawing.Drawing2D.HatchStyle> 列舉型別中的任何值。  <xref:System.Drawing.Drawing2D.HatchStyle> 列舉型別中的元素超過五十個，下列清單顯示了其中幾個元素：  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle>  
  
 下圖顯示的是已填滿的橢圓形。  
  
 ![規劃圖樣](../../../../docs/framework/winforms/advanced/media/hatch1.png "hatch1")  
  
 [!code-csharp[System.Drawing.UsingABrush#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e`\(即 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數\)。  
  
## 請參閱  
 [使用筆刷填滿形狀](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)