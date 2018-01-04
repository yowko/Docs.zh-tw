---
title: "在 GDI+ 中裁剪和縮放影像"
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0bbe7ac4b8c541ea76392f94f538e41816cf5c3f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cropping-and-scaling-images-in-gdi"></a>在 GDI+ 中裁剪和縮放影像
您可以使用<xref:System.Drawing.Graphics.DrawImage%2A>方法<xref:System.Drawing.Graphics>繪製及定位向量影像和點陣影像的類別。 <xref:System.Drawing.Graphics.DrawImage%2A>是多載的方法，因此沒有提供引數的數種方式。  
  
## <a name="drawimage-variations"></a>DrawImage 變化  
 其中一個變化<xref:System.Drawing.Graphics.DrawImage%2A>方法會接收<xref:System.Drawing.Bitmap>和<xref:System.Drawing.Rectangle>。 矩形指定的目的地繪圖作業。也就是說，它會指定要在其中繪製影像的矩形。 如果目的矩形的大小不同於原始的映像的大小，以符合目的地矩形縮放影像。 下列程式碼範例示範如何繪製相同的映像三次： 一次沒有縮放、 另一次使用的擴充和另一次使用的壓縮：  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 下圖顯示三個圖片。  
  
 ![調整](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.gif "AboutGdip03_Art06")  
  
 一些變化<xref:System.Drawing.Graphics.DrawImage%2A>方法有來源矩形參數，以及目的地矩形參數。 來源矩形參數會指定要繪製之原始影像的一部分。 目的矩形指定要在其中繪製影像的該部分。 如果目的矩形的大小不同於來源矩形的大小，圖片會調整為適合滿目的矩形。  
  
 下列程式碼範例示範如何建構<xref:System.Drawing.Bitmap>Runner.jpg 檔案中。 在沒有縮放繪製整個影像 （0，0）。 然後一小部分的影像繪製兩次： 一次使用壓縮，另一次使用放大。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 下圖顯示未縮放的影像，以及壓縮和展開的影像部分。  
  
 ![裁剪和縮放](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.gif "AboutGdip03_Art07")  
  
## <a name="see-also"></a>請參閱  
 [影像、點陣圖和中繼檔](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [使用影像、點陣圖、圖示和中繼檔](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
