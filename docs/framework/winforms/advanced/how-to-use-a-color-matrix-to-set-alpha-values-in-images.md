---
title: "如何：使用色彩矩陣設定影像中的 Alpha 值 | Microsoft Docs"
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
  - "點陣圖 [Windows Form], 使用色彩矩陣以達到半透明效果"
  - "影像 [Windows Form], 使用色彩矩陣以達到半透明效果"
  - "矩陣, Alpha 值"
  - "透明, 色彩矩陣"
ms.assetid: a27121e6-f7e9-4c09-84e2-f05aa9d2a1bb
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：使用色彩矩陣設定影像中的 Alpha 值
<xref:System.Drawing.Bitmap> 類別 \(繼承自 <xref:System.Drawing.Image> 類別\) 和 <xref:System.Drawing.Imaging.ImageAttributes> 類別提供取得和設定像素值的功能。  您可以使用 <xref:System.Drawing.Imaging.ImageAttributes> 類別來修改整個影像的 Alpha 值，或者呼叫 <xref:System.Drawing.Bitmap> 類別的 <xref:System.Drawing.Bitmap.SetPixel%2A> 方法來修改個別的像素值。  
  
## 範例  
 <xref:System.Drawing.Imaging.ImageAttributes> 類別具有許多屬性，可在呈現影像時用來修改影像。  在下列範例中，使用 <xref:System.Drawing.Imaging.ImageAttributes> 物件將所有 Alpha 值設定為原值的 80%。  做法是初始化色彩矩陣，然後將矩陣中的 Alpha 縮放值設定為 0.8。  然後將色彩矩陣的位址傳遞至 <xref:System.Drawing.Imaging.ImageAttributes> 物件的 <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> 方法，並將 <xref:System.Drawing.Imaging.ImageAttributes> 物件傳遞至 <xref:System.Drawing.Graphics> 物件的 <xref:System.Drawing.Graphics.DrawString%2A> 方法。  
  
 在呈現時，會將點陣圖中的 Alpha 值轉換為原值的 80%。  結果便會將影像與背景混合。  如下圖所示，點陣圖影像看起來為透明的，您可以透過影像看見實心黑線。  
  
 ![使用矩陣進行透明混色](../../../../docs/framework/winforms/advanced/media/image2.png "image2")  
  
 當影像出現在背景的白色部分上方時，影像已與白色混合。  而穿過黑色線條的影像部分則會與黑色混合。  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e` \(即 <xref:System.Windows.Forms.PaintEventHandler> 的參數\)。  
  
## 請參閱  
 [Windows Form 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [Alpha 混色線條和填色](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)