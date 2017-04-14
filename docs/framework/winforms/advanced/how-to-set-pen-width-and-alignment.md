---
title: "如何：設定畫筆寬度和對齊 | Microsoft Docs"
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
  - "畫筆, 設定對齊方式"
  - "畫筆, 設定寬度"
ms.assetid: a202af36-4d31-4401-a126-b232f51db581
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：設定畫筆寬度和對齊
建立 <xref:System.Drawing.Pen> 時，您可以提供畫筆寬度，做為建構函式的其中一個引數。  您也可以使用 <xref:System.Drawing.Pen> 類別的 <xref:System.Drawing.Pen.Width%2A> 屬性來變更畫筆寬度。  
  
 理論線條的寬度為 0。  當您繪製寬度為 1 個像素的線條時，像素會對齊理論線條的中央。  如果繪製的線條寬度超過 1 個像素，像素會對齊理論上線條的中央，或顯示在理論上線條的其中一側。  您可以設定 <xref:System.Drawing.Pen> 的畫筆對齊屬性，以決定該畫筆所繪製的像素相對於理論線條的位置。  
  
 下列程式碼範例中所出現的 <xref:System.Drawing.Drawing2D.PenAlignment> 值、<xref:System.Drawing.Drawing2D.PenAlignment> 值和 <xref:System.Drawing.Drawing2D.PenAlignment> 值是 <xref:System.Drawing.Drawing2D.PenAlignment> 列舉型別的成員。  
  
 下列程式碼範例繪製兩次線條：一次是使用寬度為 1 的黑色畫筆，另一次是使用寬度為 10 的綠色畫筆。  
  
### 若要改變畫筆的寬度  
  
-   請將 <xref:System.Drawing.Pen.Alignment%2A> 屬性值設定為 <xref:System.Drawing.Drawing2D.PenAlignment> \(預設值\)，以指定綠色畫筆繪製的像素對齊理論線條的中央。  下圖顯示的是產生的線條。  
  
     ![畫筆](../../../../docs/framework/winforms/advanced/media/pens1a.png "pens1A")  
  
     下列程式碼範例繪製兩次矩形：一次是使用寬度為 1 的黑色畫筆，另一次是使用寬度為 10 的綠色畫筆。  
  
     [!code-csharp[System.Drawing.UsingAPen#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#41)]
     [!code-vb[System.Drawing.UsingAPen#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#41)]  
  
### 若要變更畫筆對齊  
  
-   請將 <xref:System.Drawing.Pen.Alignment%2A> 屬性值設定為 <xref:System.Drawing.Drawing2D.PenAlignment>，以指定綠色畫筆繪製的像素對齊矩形界限的中央。  
  
     下圖顯示的是產生的矩形。  
  
     ![畫筆](../../../../docs/framework/winforms/advanced/media/pens2.png "pens2")  
  
     [!code-csharp[System.Drawing.UsingAPen#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#42)]
     [!code-vb[System.Drawing.UsingAPen#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#42)]  
  
### 若要建立內凹畫筆  
  
-   依照下列方式修改上述程式碼範例中的第三個陳述式，便可變更綠色畫筆的對齊方式：  
  
     [!code-csharp[System.Drawing.UsingAPen#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#43)]
     [!code-vb[System.Drawing.UsingAPen#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#43)]  
  
     現在，寬的綠色線條中的像素會顯示在矩形的內部，如下圖所示。  
  
     ![畫筆](../../../../docs/framework/winforms/advanced/media/pens3.png "pens3")  
  
## 請參閱  
 [使用畫筆繪製線條和形狀](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)   
 [Windows Form 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)