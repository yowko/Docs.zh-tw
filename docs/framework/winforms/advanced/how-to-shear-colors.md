---
title: HOW TO：分歧色彩
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
ms.openlocfilehash: bb5f9043ea5bdd25e984d73d3640c80f599714e6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826388"
---
# <a name="how-to-shear-colors"></a>HOW TO：分歧色彩
切變增加，或另一個色彩元件等比例的量減少色彩元件。 例如，請考慮其中紅色元件會增加一倍的藍色元件值的轉換。 在這類轉換 （0.7，0.5，1），就會變成 （0.2，0.5，1） 的色彩。 新的紅色元件是 0.2 版 + (1/2)(1) = 0.7。  
  
## <a name="example"></a>範例  
 下列範例會建構<xref:System.Drawing.Image>ColorBars4.bmp 檔案中的物件。 然後程式碼會套用至映像中的每個像素上的一段所述的切變轉換。  
  
 下圖顯示原始的映像，在左邊和分歧的映像，在右側： 
  
 ![使用彩色的等量分散-並存說明原始映像和分歧的映像的兩個正方形。](./media/how-to-shear-colors/original-image-sheared-image.png)  
  
 下表列出四個橫條的色彩向量之前, 和之後切變的轉換。  
  
|原始|修剪|  
|--------------|-------------|  
|(0, 0, 1, 1)|(0.5, 0, 1, 1)|  
|(0.5, 1, 0.5, 1)|(0.75, 1, 0.5, 1)|  
|(1, 1, 0, 1)|(1, 1, 0, 1)|  
|(0.4, 0.4, 0.4, 1)|(0.6, 0.4, 0.4, 1)|  
  
 [!code-csharp[System.Drawing.Misc3#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。 取代`ColorBars.bmp`映像名稱和您系統上有效的路徑。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Windows Forms 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)
- [為影像重新著色](recoloring-images.md)
