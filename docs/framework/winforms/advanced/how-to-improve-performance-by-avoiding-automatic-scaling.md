---
title: "如何：避免自動縮放以提高效能 | Microsoft Docs"
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
  - "自動縮放比例"
  - "影像 [Windows Form], 改善效能"
  - "影像 [Windows Form], 在沒有自動縮放比例下使用"
  - "效能, 改善影像"
ms.assetid: 5fe2c95d-8653-4d55-bf0d-e5afa28f223b
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：避免自動縮放以提高效能
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 可在您繪製影像時自動地縮放，這個動作會降低電腦效能。  此外，您可以將目的端矩形的維度傳遞至 <xref:System.Drawing.Graphics.DrawImage%2A> 方法以控制影像的縮放。  
  
 下列 <xref:System.Drawing.Graphics.DrawImage%2A> 方法呼叫會指定左上角位於 \(50, 30\)，但是不會指定目的端矩形：  
  
 [!code-csharp[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#31)]  
  
 雖然就所需的引數個數而言，這是 <xref:System.Drawing.Graphics.DrawImage%2A> 方法最簡單的版本，但是不一定最有效。  如果用於 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 的解析度 \(通常是 96 DPI\) 與儲存於 <xref:System.Drawing.Image> 物件的解析度不同，則 <xref:System.Drawing.Graphics.DrawImage%2A> 方法會縮放影像。  例如，假設 <xref:System.Drawing.Image> 物件的寬度為 216 像素，並且儲存的水平解析度值為 72 DPI。  因為 216 除以 72 等於 3，所以 <xref:System.Drawing.Graphics.DrawImage%2A> 會縮放影像，將影像寬度調整為 3 英吋，解析度為 96 DPI。  也就是說，<xref:System.Drawing.Graphics.DrawImage%2A> 所顯示的影像寬度為 96x3 \= 288 像素。  
  
 即使您的螢幕解析度不是 96 DPI，[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 可能還是會將螢幕解析度當做是 96 DPI 來縮放影像。  那是因為 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> 物件與裝置內容有關，並且在 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 查詢裝置內容以取得螢幕解析度時，不論實際螢幕解析度為何，結果通常是 96。  您可以在 <xref:System.Drawing.Graphics.DrawImage%2A> 方法中指定目的端矩形以避免自動縮放。  
  
## 範例  
 下列範例會繪製兩次相同的影像。  第一種情況不指定目的端矩形的寬度和高度，而是自動縮放影像。  第二種情況會將目的端矩形的寬度和高度 \(以像素為單位\) 指定成與原始影像的寬度和高度相同。  下圖顯示的是呈現兩次的影像。  
  
 ![調整的紋理](../../../../docs/framework/winforms/advanced/media/csscaledtexture1.png "csscaledtexture1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#32)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e` \(即 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數\)。  以系統中有效的影像名稱及路徑取代 Texture.jpg。  
  
## 請參閱  
 [影像、點陣圖和中繼檔](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [使用影像、點陣圖、圖示和中繼檔](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)