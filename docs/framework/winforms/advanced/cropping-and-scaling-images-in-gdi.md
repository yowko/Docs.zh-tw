---
title: "在 GDI+ 中裁剪和縮放影像 | Microsoft Docs"
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
  - "壓縮資料, 影像"
  - "GDI+, 裁剪影像"
  - "GDI+, 將影像縮放比例"
  - "影像 [Windows Form], 壓縮"
  - "影像 [Windows Form], 裁剪"
  - "影像 [Windows Form], 擴充"
  - "影像 [Windows Form], 縮放比例"
  - "矩形, 目的"
  - "矩形, 來源"
ms.assetid: ad5daf26-005f-45bc-a2af-e0e97777a21a
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 在 GDI+ 中裁剪和縮放影像
您可以使用 <xref:System.Drawing.Graphics> 類別的 <xref:System.Drawing.Graphics.DrawImage%2A> 方法來繪製並定位向量影像和點陣影像。  <xref:System.Drawing.Graphics.DrawImage%2A> 是一個多載方法，因此可使用許多種方法提供引數給它。  
  
## DrawImage 變異  
 <xref:System.Drawing.Graphics.DrawImage%2A> 方法的其中一個變異可接收 <xref:System.Drawing.Bitmap> 和 <xref:System.Drawing.Rectangle>。  矩形可指定繪製作業的目的地；也就是說，它可以指定繪製影像的位置。  如果目的矩形的大小和原始影像大小並不相同，該影像將縮放至適合目的矩形的大小。  下列程式碼範例會示範如何繪製三次相同的影像：一次不使用縮放、一次使用放大，還有一次使用縮小：  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 下圖將顯示這三個圖片。  
  
 ![縮放](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.png "AboutGdip03\_Art06")  
  
 有些 <xref:System.Drawing.Graphics.DrawImage%2A> 方法的變異具有來源矩形參數和目的矩形參數。  來源矩形參數指定要繪製的原始影像區域。  目的矩形指定用來繪製該影像區域的位置。  如果目的矩形大小和來源矩形大小並不相同，圖片將縮放至適合目的矩形的大小。  
  
 下列程式碼範例示範如何從 Runner.jpg 檔案建構 <xref:System.Drawing.Bitmap>。  整個影像從 \(0, 0\) 開始繪製，且不進行縮放。  接著影像中的一小部分會繪製兩次：一次使用縮小，另一次使用放大。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 下列圖示將顯示未縮放的影像，以及經過縮小和放大的影像部分。  
  
 ![裁剪和縮放](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.png "AboutGdip03\_Art07")  
  
## 請參閱  
 [影像、點陣圖和中繼檔](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [使用影像、點陣圖、圖示和中繼檔](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)