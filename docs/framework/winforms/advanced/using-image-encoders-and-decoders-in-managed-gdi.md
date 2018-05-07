---
title: 使用 Managed GDI+ 中的影像編碼器和解碼器
ms.date: 03/30/2017
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
ms.openlocfilehash: b2e51587209cb4df41ea1fd18ce5c2088ee07a2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a>使用 Managed GDI+ 中的影像編碼器和解碼器
<xref:System.Drawing>命名空間提供<xref:System.Drawing.Image>和<xref:System.Drawing.Bitmap>類別來儲存和管理影像。 使用中的影像編碼器[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，您可以從記憶體寫入映像至磁碟。 使用中的影像解碼器[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，您可以將記憶體從磁碟載入影像。 編碼器將在資料轉譯<xref:System.Drawing.Image>或<xref:System.Drawing.Bitmap>到指定的磁碟檔案格式的物件。 解碼器會將轉譯檔案中的資料磁碟所需的格式來<xref:System.Drawing.Image>和<xref:System.Drawing.Bitmap>物件。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 具有內建編碼器和解碼器支援下列檔案類型：  
  
-   BMP  
  
-   GIF  
  
-   JPEG  
  
-   PNG  
  
-   TIFF  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 也有支援下列檔案類型的內建解碼器：  
  
-   WMF  
  
-   EMF  
  
-   圖示  
  
 下列主題將討論編碼器與解碼器的更多詳細資料：  
  
## <a name="in-this-section"></a>本節內容  
 [操作說明：列出已安裝的編碼器](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 描述如何列出電腦上可用的編碼器。  
  
 [操作說明：列出已安裝的解碼器](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 描述如何列出電腦上可用的解碼器。  
  
 [操作說明：判斷編碼器所支援的參數](../../../../docs/framework/winforms/advanced/how-to-determine-the-parameters-supported-by-an-encoder.md)  
 描述如何列出<xref:System.Drawing.Imaging.EncoderParameters>編碼器所支援。  
  
 [操作說明：將 BMP 影像轉換為 PNG 影像](../../../../docs/framework/winforms/advanced/how-to-convert-a-bmp-image-to-a-png-image.md)  
 描述如何將影像儲存為不同的影像格式。  
  
 [操作說明：設定 JPEG 壓縮層級](../../../../docs/framework/winforms/advanced/how-to-set-jpeg-compression-level.md)  
 描述如何變更影像的品質等級。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a>相關章節  
 [關於 GDI+ Managed 程式碼](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
  
 [影像、點陣圖和中繼檔](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
