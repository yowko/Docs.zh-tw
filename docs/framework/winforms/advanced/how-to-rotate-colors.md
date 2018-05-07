---
title: 如何：旋轉色彩
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], rotating
- examples [Windows Forms], rotating colors
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
ms.openlocfilehash: 258ef9cd5eb8d569b2982614e3087df730a18c57
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-rotate-colors"></a>如何：旋轉色彩
中度空間旋轉很難視覺化。 我們可以讓您更輕鬆地視覺化起來保留固定的色彩元件之一。 假設同意將固定為 1 的 alpha 元件 （完全不透明）。 然後我們可以將三維色彩空間視覺化具有紅色、 綠色和藍色軸下, 圖所示。  
  
 ![重新著色，以便](../../../../docs/framework/winforms/advanced/media/recoloring03.gif "recoloring03")  
  
 色彩可以視為 3d 空間中的點。 例如，空間中的點 （1，0，0） 表示的色彩為紅色，而空間中的點 （0，1，0） 代表綠色。  
  
 下圖顯示旋轉色彩 （1，0，0） 的意義紅色、 綠色分別平面中 60 度角。 以平行的紅色、 綠色分別平面的平面旋轉可以視為藍色軸旋轉。  
  
 ![重新著色，以便](../../../../docs/framework/winforms/advanced/media/recoloring04.gif "recoloring04")  
  
 下圖顯示如何初始化色彩矩陣執行有關的三個座標的軸 （紅色、 綠色、 藍色） 的旋轉。  
  
 ![重新著色，以便](../../../../docs/framework/winforms/advanced/media/recoloring05.gif "recoloring05")  
  
## <a name="example"></a>範例  
 下列範例會為所有的一種色彩 （1、 0、 0.6） 與藍色軸的 60 度旋轉套用的映像。 旋轉的角度是紅色、 綠色分別平面平行平面中清理掉。  
  
 下圖顯示原始的映像，在左邊和右邊的旋轉色彩的映像。  
  
 ![旋轉色彩](../../../../docs/framework/winforms/advanced/media/colortrans5.png "colortrans5")  
  
 下圖顯示色彩旋轉，執行下列程式碼中的視覺效果。  
  
 ![重新著色，以便](../../../../docs/framework/winforms/advanced/media/recoloring06.gif "recoloring06")  
  
 [!code-csharp[System.Drawing.RotateColors#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例設計用於搭配 Windows Form，且其需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。 取代`RotationInput.bmp`映像檔案名稱與您系統上有效的路徑。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [Windows Forms 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [為影像重新著色](../../../../docs/framework/winforms/advanced/recoloring-images.md)
