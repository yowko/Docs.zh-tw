---
title: "在 GDI+ 中繪製、定位和複製影像"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- raster images [Windows Forms]
- images [Windows Forms], positioning
- drawing [Windows Forms], images
- drawing [Windows Forms], raster images
- images [Windows Forms], cloning
- images [Windows Forms], drawing
- GDI+, drawing images
- GDI+, cloning images
- GDI+, positioning images
ms.assetid: 09f0c07a-19c0-43b4-90a2-862a10545ce8
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a3ba716a36280d2ac08dae907abbdbe05e563dfc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="drawing-positioning-and-cloning-images-in-gdi"></a>在 GDI+ 中繪製、定位和複製影像
您可以使用<xref:System.Drawing.Bitmap>類別來載入及顯示點陣影像，而且您可以使用<xref:System.Drawing.Imaging.Metafile>類別來載入及顯示向量影像。 <xref:System.Drawing.Bitmap>和<xref:System.Drawing.Imaging.Metafile>類別繼承自<xref:System.Drawing.Image>類別。 若要顯示的向量映像，您需要的執行個體<xref:System.Drawing.Graphics>類別和<xref:System.Drawing.Imaging.Metafile>。 若要顯示點陣影像，您需要的執行個體<xref:System.Drawing.Graphics>類別和<xref:System.Drawing.Bitmap>。 執行個體<xref:System.Drawing.Graphics>類別提供<xref:System.Drawing.Graphics.DrawImage%2A>方法，這個方法會接收<xref:System.Drawing.Imaging.Metafile>或<xref:System.Drawing.Bitmap>做為引數。  
  
## <a name="file-types-and-cloning"></a>檔案類型和複製  
 下列程式碼範例示範如何建構<xref:System.Drawing.Bitmap>Climber.jpg 檔案中，並顯示點陣圖。 影像的左上角的目的地點 （10，10），第二個和第三個參數中指定。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#11)]  
  
 下圖顯示映像。  
  
 ![影像範例](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art04.gif "AboutGdip03_Art04")  
  
 您可以建構<xref:System.Drawing.Bitmap>從各種不同的圖形物件檔案格式： BMP、 GIF、 JPEG、 EXIF、 PNG、 TIFF 和圖示。  
  
 下列程式碼範例示範如何建構<xref:System.Drawing.Bitmap>物件從不同的檔案類型，則會顯示點陣圖。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#12)]  
  
 <xref:System.Drawing.Bitmap>類別提供<xref:System.Drawing.Bitmap.Clone%2A>方法可讓您製作現有<xref:System.Drawing.Bitmap>。 <xref:System.Drawing.Bitmap.Clone%2A>方法擁有的來源矩形參數可讓您指定的一部分，您要複製的原始點陣圖。 下列程式碼範例示範如何建立<xref:System.Drawing.Bitmap>藉由複製現有的上半部<xref:System.Drawing.Bitmap>。 然後會繪製這兩個映像。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#13)]  
  
 下圖顯示兩個映像。  
  
 ![裁剪](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art05.gif "AboutGdip03_Art05")  
  
## <a name="see-also"></a>另請參閱  
 [影像、點陣圖和中繼檔](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [操作說明：建立繪圖的圖形物件](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [使用影像、點陣圖、圖示和中繼檔](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
