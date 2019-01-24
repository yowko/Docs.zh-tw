---
title: HOW TO：轉譯影像色彩
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], changing colors
- images [Windows Forms], changing colors
- image colors [Windows Forms]
ms.assetid: 2106fb9a-4d60-4dcf-9220-9f189a6c4d19
ms.openlocfilehash: 7a3ed1f3f6b3e89c8df160b7e753839e20acd877
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549755"
---
# <a name="how-to-translate-image-colors"></a>HOW TO：轉譯影像色彩
翻譯加入到一或多個四個色彩元件的值。 下表提供色彩矩陣項目表示的翻譯。  
  
|要轉換的元素|矩陣項目|  
|--------------------------------|------------------|  
|紅色|[4][0]|  
|綠色|[4][1]|  
|藍色|[4][2]|  
|Alpha|[4][3]|  
  
## <a name="example"></a>範例  
 下列範例會建構<xref:System.Drawing.Image>ColorBars.bmp 檔案中的物件。 然後程式碼會新增至映像中的每個像素的紅色元件 0.75。 原始的映像與已轉換的映像一起繪製。  
  
 下圖顯示原始的映像，在左邊和轉換後的映像，在右邊。  
  
 ![轉譯色彩](../../../../docs/framework/winforms/advanced/media/colortrans2.png "colortrans2")  
  
 下表列出四個橫條的色彩向量之前, 和之後的紅色的翻譯。 請注意，因為色彩元件的最大值為 1，第二個資料列中的紅色元件不會變更。 （同樣地，色彩元件的最小值是 0）。  
  
|原始|轉譯|  
|--------------|----------------|  
|黑色 （0，0，0，1）|(0.75, 0, 0, 1)|  
|紅色 （1，0，0，1）|(1, 0, 0, 1)|  
|綠色 （0、 1、 0、 1）|(0.75, 1, 0, 1)|  
|藍色 （0，0，1，1）|(0.75, 0, 1, 1)|  
  
 [!code-csharp[System.Drawing.RecoloringImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.RecoloringImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。 取代`ColorBars.bmp`映像檔案名稱與您系統為有效的路徑。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Windows Forms 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [為影像重新著色](../../../../docs/framework/winforms/advanced/recoloring-images.md)
