---
title: 如何：轉譯影像色彩
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], changing colors
- images [Windows Forms], changing colors
- image colors [Windows Forms]
ms.assetid: 2106fb9a-4d60-4dcf-9220-9f189a6c4d19
ms.openlocfilehash: 48f506f76ff6e9ca648822d073b6f6a852b9ca8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522532"
---
# <a name="how-to-translate-image-colors"></a>如何：轉譯影像色彩
翻譯將值加入至一個以上的四個色彩元件。 下表中，可以代表轉譯的色彩矩陣項目。  
  
|要轉換的元素|矩陣項目|  
|--------------------------------|------------------|  
|紅色|[4][0]|  
|綠色|[4][1]|  
|藍色|[4][2]|  
|Alpha|[4][3]|  
  
## <a name="example"></a>範例  
 下列範例會建構<xref:System.Drawing.Image>ColorBars.bmp 檔案中的物件。 然後程式碼會加入 0.75 到映像中的每個像素的紅色元件。 在原始圖像是繪製轉換後的映像的旁邊。  
  
 下圖顯示在右側的原始左側映像，而且已轉換的映像。  
  
 ![轉譯色彩](../../../../docs/framework/winforms/advanced/media/colortrans2.png "colortrans2")  
  
 下表列出四個橫條的色彩向量之前和之後的紅色的翻譯。 請注意，因為色彩元件的最大值為 1，第二個資料列中的紅色元件不會變更。 （同樣地，色彩元件的最小值為 0）。  
  
|原始|轉譯|  
|--------------|----------------|  
|黑色 （0，0，0，1）|(0.75, 0, 0, 1)|  
|紅色 （1，0，0，1）|(1, 0, 0, 1)|  
|綠色 （0、 1、 0，1）|(0.75, 1, 0, 1)|  
|藍色 （0，0，1，1）|(0.75, 0, 1, 1)|  
  
 [!code-csharp[System.Drawing.RecoloringImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.RecoloringImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例設計用於搭配 Windows Form，且其需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。 取代`ColorBars.bmp`映像檔案名稱與您系統為有效的路徑。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [Windows Forms 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [為影像重新著色](../../../../docs/framework/winforms/advanced/recoloring-images.md)
