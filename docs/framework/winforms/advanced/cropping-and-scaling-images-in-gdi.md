---
title: 在 GDI+ 中裁剪和縮放影像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, scaling images
- GDI+, cropping images
- images [Windows Forms], cropping
- compressing data [Windows Forms], images
- images [Windows Forms], expansion
- images [Windows Forms], scaling
- rectangles [Windows Forms], source
- rectangles [Windows Forms], destination
- images [Windows Forms], compression
ms.assetid: ad5daf26-005f-45bc-a2af-e0e97777a21a
ms.openlocfilehash: 311673c30283cdf3e0206d143daab8c01adc2bce
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718788"
---
# <a name="cropping-and-scaling-images-in-gdi"></a>在 GDI+ 中裁剪和縮放影像
您可以使用<xref:System.Drawing.Graphics.DrawImage%2A>方法的<xref:System.Drawing.Graphics>類別，以繪製和向量映像和點陣影像的位置。 <xref:System.Drawing.Graphics.DrawImage%2A> 是多載的方法，因此沒有提供引數的數種方式。  
  
## <a name="drawimage-variations"></a>DrawImage 變化  
 其中一個變化<xref:System.Drawing.Graphics.DrawImage%2A>方法會接收<xref:System.Drawing.Bitmap>和<xref:System.Drawing.Rectangle>。 矩形指定的目的地，繪製作業;也就是說，它會指定在其中繪製影像的矩形。 如果目的地矩形的大小不同於原始的映像的大小，影像會縮放以符合目的地矩形。 下列程式碼範例示範如何繪製相同的映像三次： 一次，且不進行縮放，另一次展開時，使用，另一次壓縮：  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 下圖顯示三個的圖片。  
  
 ![Scaling](./media/aboutgdip03-art06.gif "AboutGdip03_Art06")  
  
 一些變化<xref:System.Drawing.Graphics.DrawImage%2A>方法有來源矩形的參數，以及目的地矩形的參數。 來源矩形參數會指定要繪製之原始影像的部分。 目的矩形會指定要在其中繪製影像的該部分的矩形。 如果目的地矩形的大小是不同於來源矩形的大小，圖片會調整為適合滿目的矩形。  
  
 下列程式碼範例示範如何建構<xref:System.Drawing.Bitmap>Runner.jpg 檔案中。 在沒有縮放繪製整個影像 （0，0）。 然後映像的一小部分繪製兩次： 一次使用壓縮，另一次使用擴充功能。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 下圖顯示未縮放的影像，並壓縮和展開的影像部分。  
  
 ![裁剪和縮放](./media/aboutgdip03-art07.gif "AboutGdip03_Art07")  
  
## <a name="see-also"></a>另請參閱
- [影像、點陣圖和中繼檔](images-bitmaps-and-metafiles.md)
- [使用影像、點陣圖、圖示和中繼檔](working-with-images-bitmaps-icons-and-metafiles.md)
