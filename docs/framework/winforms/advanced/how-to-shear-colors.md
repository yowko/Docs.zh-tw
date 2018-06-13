---
title: 如何：切變色彩
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
ms.openlocfilehash: 204f15ce44d5ad688be0ea9ac0fa4a90781b25dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522443"
---
# <a name="how-to-shear-colors"></a>如何：切變色彩
切變增加，或另一個色彩元件等比例的量減少色彩元件。 例如，請考慮的轉換一半的值的藍色元件其中增加的紅色元件。 在這類轉換 （0.7，0.5，1），就會變成 （0.2，0.5，1） 的色彩。 新的紅色元件為 0.2 + (1/2)(1) = 0.7。  
  
## <a name="example"></a>範例  
 下列範例會建構<xref:System.Drawing.Image>ColorBars4.bmp 檔案中的物件。 程式碼會接著套用切變映像中的每個像素在上一段所述的轉換。  
  
 下圖顯示在右側的原始左側的映像和分歧映像。  
  
 ![分歧色彩](../../../../docs/framework/winforms/advanced/media/colortrans6.png "colortrans6")  
  
 下表列出四個橫條的色彩向量切變轉換之前和之後。  
  
|原始|修剪|  
|--------------|-------------|  
|(0, 0, 1, 1)|(0.5, 0, 1, 1)|  
|(0.5, 1, 0.5, 1)|(0.75, 1, 0.5, 1)|  
|(1, 1, 0, 1)|(1, 1, 0, 1)|  
|(0.4, 0.4, 0.4, 1)|(0.6, 0.4, 0.4, 1)|  
  
 [!code-csharp[System.Drawing.Misc3#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例設計用於搭配 Windows Form，且其需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。 取代`ColorBars.bmp`映像名稱與您系統上有效的路徑。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [Windows Forms 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [為影像重新著色](../../../../docs/framework/winforms/advanced/recoloring-images.md)
