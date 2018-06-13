---
title: 如何：縮放期間使用插補法模式控制影像品質
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interpolation mode [Windows Forms], controlling image quality
- images [Windows Forms], scaling
- images [Windows Forms], controlling quality
ms.assetid: fde9bccf-8aa5-4b0d-ba4b-788740627b02
ms.openlocfilehash: 72a9cb3a19f0d449dcb376a65f1734b79ed61ab9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522355"
---
# <a name="how-to-use-interpolation-mode-to-control-image-quality-during-scaling"></a>如何：縮放期間使用插補法模式控制影像品質
插補模式<xref:System.Drawing.Graphics>物件會影響方式[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]標尺 （兩端之間自動縮放和壓縮） 映像。 <xref:System.Drawing.Drawing2D.InterpolationMode>列舉會定義數個插補模式，其中有些下列清單所示：  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bicubic>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>  
  
 若要縮放影像，原始的映像中的每個像素必須對應到較大的映像中的像素為單位的群組。 若要壓縮影像，原始的映像中的像素為單位的群組必須對應到較小的映像中的單一像素為單位。 執行這些對應的演算法的效能決定縮放的影像品質。 產生高品質縮放的影像的演算法通常需要更多的處理時間。 在上述清單中，<xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>是最低品質模式和<xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>是最高品質的模式。  
  
 若要設定的插補模式，將指定的成員<xref:System.Drawing.Drawing2D.InterpolationMode>列舉<xref:System.Drawing.Graphics.InterpolationMode%2A>屬性<xref:System.Drawing.Graphics>物件。  
  
## <a name="example"></a>範例  
 下列範例會繪製影像，並再壓縮影像的三種不同的插補模式。  
  
 下圖顯示原始的映像和三個較小的影像。  
  
 ![具有各種插補設定的影像](../../../../docs/framework/winforms/advanced/media/csgrapes1.png "csgrapes1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#81)]
 [!code-vb[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#81)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。  
  
## <a name="see-also"></a>另請參閱  
 [影像、點陣圖和中繼檔](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [使用影像、點陣圖、圖示和中繼檔](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
