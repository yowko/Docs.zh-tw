---
title: "如何：將現有點陣圖描繪至螢幕 | Microsoft Docs"
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
  - "點陣圖 [Windows Form], 在 Windows Form 中顯示"
  - "點陣圖 [Windows Form], 在 Windows Form 應用程式中載入"
  - "影像 [Windows Form], 在 Windows Form 上顯示"
ms.assetid: 5bc558d7-b326-4050-a834-b8600da0de95
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：將現有點陣圖描繪至螢幕
您可以在螢幕上輕鬆繪製現有影像。  首先，您需使用帶有檔案名稱 <xref:System.Drawing.Bitmap.%23ctor%28System.String%29> 的點陣圖建構函式來建立 <xref:System.Drawing.Bitmap> 物件。  這個建構函式可以接受數種不同檔案格式的影像，包括 BMP、GIF、JPEG、PNG 及 TIFF。  在您建立 <xref:System.Drawing.Bitmap> 物件後，將 <xref:System.Drawing.Bitmap> 物件傳遞至 <xref:System.Drawing.Graphics> 物件的 <xref:System.Drawing.Graphics.DrawImage%2A> 方法。  
  
## 範例  
 下列範例會從 JPEG 檔案建立 <xref:System.Drawing.Bitmap> 物件，然後繪製左上角位於 \(60, 10\) 的點陣圖。  
  
 下圖顯示的是在指定位置繪製的點陣圖。  
  
 ![影像位置](../../../../docs/framework/winforms/advanced/media/csimageposition1.png "csimageposition1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#21)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e` \(即 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數\)。  
  
## 請參閱  
 [Windows Form 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [使用影像、點陣圖、圖示和中繼檔](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)