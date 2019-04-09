---
title: 在 GDI+ 中繪製、定位和複製影像
ms.date: 03/30/2017
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
ms.openlocfilehash: b5f98e7bdef9ff8ed0a4cd0e040cb92a31f30503
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188444"
---
# <a name="drawing-positioning-and-cloning-images-in-gdi"></a>在 GDI+ 中繪製、定位和複製影像
您可以使用<xref:System.Drawing.Bitmap>類別來載入和顯示點陣影像，以及您可以使用<xref:System.Drawing.Imaging.Metafile>類別來載入和顯示向量影像。 <xref:System.Drawing.Bitmap>並<xref:System.Drawing.Imaging.Metafile>類別繼承自<xref:System.Drawing.Image>類別。 若要顯示的向量映像，您需要的執行個體<xref:System.Drawing.Graphics>類別和<xref:System.Drawing.Imaging.Metafile>。 若要顯示點陣影像，您需要的執行個體<xref:System.Drawing.Graphics>類別和<xref:System.Drawing.Bitmap>。 執行個體<xref:System.Drawing.Graphics>類別會提供<xref:System.Drawing.Graphics.DrawImage%2A>方法，它會接收<xref:System.Drawing.Imaging.Metafile>或<xref:System.Drawing.Bitmap>做為引數。  
  
## <a name="file-types-and-cloning"></a>檔案類型，以及複製  
 下列程式碼範例示範如何建構<xref:System.Drawing.Bitmap>從 Climber.jpg 檔案，並顯示點陣圖。 映像，左上角的目的點 （10，10），第二個和第三個參數中指定。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#11)]  
  
 下圖顯示的影像。  
  
 ![影像範例](./media/aboutgdip03-art04.gif "AboutGdip03_Art04")  
  
 您可以建構<xref:System.Drawing.Bitmap>各式各樣的圖形物件檔案格式：BMP、 GIF、 JPEG、 EXIF、 PNG、 TIFF 和圖示。  
  
 下列程式碼範例示範如何建構<xref:System.Drawing.Bitmap>各種檔案類型的物件，並顯示點陣圖。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#12)]  
  
 <xref:System.Drawing.Bitmap>類別會提供<xref:System.Drawing.Bitmap.Clone%2A>方法，可用來建立一份現有<xref:System.Drawing.Bitmap>。 <xref:System.Drawing.Bitmap.Clone%2A>方法具有可用來指定您想要複製的原始點陣圖一部分的來源矩形參數。 下列程式碼範例示範如何建立<xref:System.Drawing.Bitmap>藉由複製現有的上半部<xref:System.Drawing.Bitmap>。 然後會繪製這兩個映像。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#13)]  
  
 下圖顯示兩個映像。  
  
 ![Cropping](./media/aboutgdip03-art05.gif "AboutGdip03_Art05")  
  
## <a name="see-also"></a>另請參閱

- [影像、點陣圖和中繼檔](images-bitmaps-and-metafiles.md)
- [HOW TO：建立繪製的圖形物件](how-to-create-graphics-objects-for-drawing.md)
- [使用影像、點陣圖、圖示和中繼檔](working-with-images-bitmaps-icons-and-metafiles.md)
