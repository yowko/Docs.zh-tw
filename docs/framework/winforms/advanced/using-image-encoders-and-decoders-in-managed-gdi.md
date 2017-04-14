---
title: "使用 Managed GDI+ 中的影像編碼器和解碼器 | Microsoft Docs"
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
  - "影像解碼器, 使用"
  - "影像轉碼器, 使用"
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 使用 Managed GDI+ 中的影像編碼器和解碼器
<xref:System.Drawing> 命名空間提供 <xref:System.Drawing.Image> 和 <xref:System.Drawing.Bitmap> 類別，以供儲存與操作影像。  您可以藉由使用 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 中的影像編碼器，將影像從記憶體寫入磁碟。您也可以藉由使用 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 中的影像解碼器，將影像從磁碟載入記憶體。  編碼器會將 <xref:System.Drawing.Image> 或 <xref:System.Drawing.Bitmap> 物件中的資料，轉譯成指定的磁碟檔案格式。  解碼器則會將磁碟檔案中的資料轉譯為 <xref:System.Drawing.Image> 和 <xref:System.Drawing.Bitmap> 物件所需的格式。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 內建的編碼器與解碼器支援下列檔案類型：  
  
-   BMP  
  
-   GIF  
  
-   JPEG  
  
-   PNG  
  
-   TIFF  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 也有能夠支援下列檔案類型的內建解碼器：  
  
-   WMF  
  
-   EMF  
  
-   圖示  
  
 下列主題說明編碼器與解碼器的細節：  
  
## 在本節中  
 [如何：列出已安裝的編碼器](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 描述如何列出電腦中可用的編碼器。  
  
 [如何：列出已安裝的解碼器](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 描述如何列出電腦中可用的解碼器。  
  
 [如何：判斷編碼器所支援的參數](../../../../docs/framework/winforms/advanced/how-to-determine-the-parameters-supported-by-an-encoder.md)  
 描述如何列出編碼器支援的 <xref:System.Drawing.Imaging.EncoderParameters>。  
  
 [如何：將 BMP 影像轉換為 PNG 影像](../../../../docs/framework/winforms/advanced/how-to-convert-a-bmp-image-to-a-png-image.md)  
 描述如何以不同的影像格式儲存影像。  
  
 [如何：設定 JPEG 壓縮層級](../../../../docs/framework/winforms/advanced/how-to-set-jpeg-compression-level.md)  
 描述如何變更影像的品質等級。  
  
## 參考  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## 相關章節  
 [關於 GDI\+ Managed 程式碼](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
  
 [影像、點陣圖和中繼檔](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)