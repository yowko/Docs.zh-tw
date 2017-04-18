---
title: "在 GDI+ 中繪製、定位和複製影像 | Microsoft Docs"
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
  - "繪製, 影像"
  - "繪製, 光柵影像"
  - "GDI+, 複製影像"
  - "GDI+, 描繪影像"
  - "GDI+, 定位影像"
  - "影像 [Windows Form], 複製"
  - "影像 [Windows Form], 繪製"
  - "影像 [Windows Form], 位置"
  - "光柵影像"
ms.assetid: 09f0c07a-19c0-43b4-90a2-862a10545ce8
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 在 GDI+ 中繪製、定位和複製影像
您可以使用 <xref:System.Drawing.Bitmap> 類別來載入和顯示點陣影像，也可以使用 <xref:System.Drawing.Imaging.Metafile> 類別來載入和顯示向量影像。  <xref:System.Drawing.Bitmap> 和 <xref:System.Drawing.Imaging.Metafile> 類別都繼承自 <xref:System.Drawing.Image> 類別。  若要顯示向量影像，您需要 <xref:System.Drawing.Graphics> 類別執行個體和 <xref:System.Drawing.Imaging.Metafile>。  若要顯示點陣影像，您需要 <xref:System.Drawing.Graphics> 類別執行個體和 <xref:System.Drawing.Bitmap>。  <xref:System.Drawing.Graphics> 類別執行個體提供 <xref:System.Drawing.Graphics.DrawImage%2A> 方法來接收 <xref:System.Drawing.Imaging.Metafile> 或 <xref:System.Drawing.Bitmap> 做為引數。  
  
## 檔案類型和複製  
 下列程式碼範例會示範如何從 Climber.jpg 檔案建立 <xref:System.Drawing.Bitmap> 並顯示此點陣圖。  影像左上角的目的點 \(10, 10\) 是由第二個和第三個參數指定。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#11)]  
  
 下圖顯示該影像。  
  
 ![影像範例](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art04.png "AboutGdip03\_Art04")  
  
 您可以使用下列各種圖形檔案格式來建構 <xref:System.Drawing.Bitmap> 物件：BMP、GIF、JPEG、EXIF、PNG、TIFF 和 ICON。  
  
 下列程式碼範例會示範如何從各種檔案類型建立 <xref:System.Drawing.Bitmap> 物件，並顯示該點陣圖。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#12)]  
  
 <xref:System.Drawing.Bitmap> 類別提供 <xref:System.Drawing.Bitmap.Clone%2A> 方法，可用來製作現有 <xref:System.Drawing.Bitmap> 物件的複本。  <xref:System.Drawing.Bitmap.Clone%2A> 方法具有來源矩形參數，可指定您要複製的原始點陣圖區域。  下列程式碼範例會示範如何藉由複製現有 <xref:System.Drawing.Bitmap> 上半部來建立 <xref:System.Drawing.Bitmap>。  然後同時繪製這兩個影像。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#13)]  
  
 下圖將顯示這兩個影像。  
  
 ![裁剪](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art05.png "AboutGdip03\_Art05")  
  
## 請參閱  
 [影像、點陣圖和中繼檔](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [如何：建立繪製的圖形物件](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)   
 [使用影像、點陣圖、圖示和中繼檔](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)