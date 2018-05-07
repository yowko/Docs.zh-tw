---
title: 如何：使用色彩重新對應表
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- color tables [Windows Forms], remapping colors with
- custom colors [Windows Forms], creating with color remap table
- color remap tables [Windows Forms], using
ms.assetid: 977df1ce-8665-42d4-9fb1-ef7f0ff63419
ms.openlocfilehash: ba763cc7960e71c6fc705d40eefdbde163d06181
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-color-remap-table"></a>如何：使用色彩重新對應表
重新對應是轉換的色彩，色彩重新對應表根據映像中的程序。 色彩重新對應表是陣列<xref:System.Drawing.Imaging.ColorMap>物件。 每個<xref:System.Drawing.Imaging.ColorMap>陣列中的物件具有<xref:System.Drawing.Imaging.ColorMap.OldColor%2A>屬性和<xref:System.Drawing.Imaging.ColorMap.NewColor%2A>屬性。  
  
 當[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]繪製影像，影像的每個像素會與舊的色彩的陣列。 如果像素的色彩符合舊的色彩，其色彩會變更為對應的新色彩。 僅針對轉譯來變更色彩，影像本身的色彩值 (儲存在<xref:System.Drawing.Image>或<xref:System.Drawing.Bitmap>物件) 不會變更。  
  
 若要繪製重新對應的影像，初始化陣列<xref:System.Drawing.Imaging.ColorMap>物件。 傳遞至該陣列<xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A>方法<xref:System.Drawing.Imaging.ImageAttributes>物件，並將傳遞<xref:System.Drawing.Imaging.ImageAttributes>物件<xref:System.Drawing.Graphics.DrawImage%2A>方法<xref:System.Drawing.Graphics>物件。  
  
## <a name="example"></a>範例  
 下列範例會建立<xref:System.Drawing.Image>RemapInput.bmp 檔案中的物件。 程式碼會建立包含單一色彩重新對應表<xref:System.Drawing.Imaging.ColorMap>物件。 <xref:System.Drawing.Imaging.ColorMap.OldColor%2A>屬性`ColorRemap`物件為紅色，而<xref:System.Drawing.Imaging.ColorMap.NewColor%2A>屬性是藍色。 影像是不含重新對應的繪製一次，另一次重新對應。 重新對應的程序變更為藍色所有紅色的像素。  
  
 下圖顯示在右側的原始左側的映像和重新對應的影像。  
  
 ![色彩重新對應](../../../../docs/framework/winforms/advanced/media/colortrans7.png "colortrans7")  
  
 [!code-csharp[System.Drawing.RecoloringImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.RecoloringImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例設計用於搭配 Windows Form，且其需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。  
  
## <a name="see-also"></a>另請參閱  
 [為影像重新著色](../../../../docs/framework/winforms/advanced/recoloring-images.md)  
 [影像、點陣圖和中繼檔](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
