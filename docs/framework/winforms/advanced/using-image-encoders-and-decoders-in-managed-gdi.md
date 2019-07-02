---
title: 使用 Managed GDI+ 中的影像編碼器和解碼器
ms.date: 03/30/2017
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
ms.openlocfilehash: 8cd66f3ce3da462867da9e23c38b3f6d877c058c
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505085"
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a>使用 Managed GDI+ 中的影像編碼器和解碼器
<xref:System.Drawing>命名空間提供<xref:System.Drawing.Image>和<xref:System.Drawing.Bitmap>來儲存及操作影像的類別。 藉由使用 GDI + 中的影像編碼器，您可以將映像從記憶體寫入磁碟。 藉由使用 GDI + 中的影像解碼器，您可以從磁碟載入映像載入記憶體。 編碼器會將轉譯中的資料<xref:System.Drawing.Image>或<xref:System.Drawing.Bitmap>到指定的磁碟檔案格式的物件。 解碼器會轉譯檔案中的資料磁碟所需的格式來<xref:System.Drawing.Image>和<xref:System.Drawing.Bitmap>物件。  
  
 GDI + 具有內建的編碼器和解碼器，支援下列檔案類型：  
  
- BMP  
  
- GIF  
  
- JPEG  
  
- PNG  
  
- TIFF  
  
 GDI + 還有內建解碼器，支援下列檔案類型：  
  
- WMF  
  
- EMF  
  
- 圖示  
  
 下列主題將討論編碼器與解碼器的更多詳細資料：  
  
## <a name="in-this-section"></a>本節內容  
 [如何：列出已安裝的編碼器](how-to-list-installed-encoders.md)  
 描述如何列出電腦上可用的編碼器。  
  
 [如何：列出已安裝的解碼器](how-to-list-installed-decoders.md)  
 描述如何列出電腦上可用解碼器。  
  
 [如何：判斷編碼器所支援的參數](how-to-determine-the-parameters-supported-by-an-encoder.md)  
 描述如何列出<xref:System.Drawing.Imaging.EncoderParameters>編碼器所支援。  
  
 [如何：將 BMP 影像轉換為 PNG 影像](how-to-convert-a-bmp-image-to-a-png-image.md)  
 描述如何將影像儲存在不同的影像格式。  
  
 [如何：設定 JPEG 壓縮層級](how-to-set-jpeg-compression-level.md)  
 描述如何變更影像的品質等級。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a>相關章節  
 [關於 GDI+ Managed 程式碼](about-gdi-managed-code.md)  
  
 [影像、點陣圖和中繼檔](images-bitmaps-and-metafiles.md)
