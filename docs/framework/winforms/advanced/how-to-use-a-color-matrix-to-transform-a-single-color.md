---
title: 如何：使用色彩矩陣轉換單一色彩
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image colors [Windows Forms], transforming
- color matrices [Windows Forms], using
ms.assetid: 44df4556-a433-49c0-ac0f-9a12063a5860
ms.openlocfilehash: 741259fcf853c82dfd13b43edc92e50d8767887b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-color-matrix-to-transform-a-single-color"></a>如何：使用色彩矩陣轉換單一色彩
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供<xref:System.Drawing.Image>和<xref:System.Drawing.Bitmap>類別來儲存和管理影像。 <xref:System.Drawing.Image> 和<xref:System.Drawing.Bitmap>物件會儲存每個像素色彩的 32 位元數字： 8 位元每個紅色、 綠色、 藍色及 alpha。 四個元件的每一個都是從 0 到 255，0 代表不含濃度，代表完整的濃度 255 的數字。 Alpha 元件指定色彩的透明度： 0 是完全透明，而 255 是完全不透明。  
  
 色彩向量是紅色、 綠色、 藍色 （alpha） 格式的 4 tuple。 例如，色彩向量 （0，255，0，255） 代表不透明的色彩，含紅色或藍色，但有綠色的濃度。  
  
 表示色彩的另一個慣例是使用數字 1 的完整的濃度。 使用這個慣例，在上一段所述的色彩則表示向量 （0、 1、 0，1）。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 當它執行色彩轉換會使用 1 的慣例為完整的濃度。  
  
 您可以套用到色彩向量的線性轉換 （旋轉、 調整及 like） 乘以 4 × 4 矩陣的色彩向量。 不過，您無法使用 4 × 4 矩陣，來執行 （「 非線性的 」） 的翻譯。 如果您將空的第五個座標 （例如，數字 1） 加入每一個色彩向量，您可以使用 5 × 5 矩陣來套用線性轉換和翻譯的任意組合。 包含後面接著翻譯線性轉換稱為仿射轉換。  
  
 例如，假設您想要使用的色彩 （0.2、 0.0、 0.4、 1.0） 啟動，並套用下列轉換：  
  
1.  Double 紅色的元件  
  
2.  0.2 加入紅色、 綠色和藍色元件  
  
 下列的矩陣乘法會列出的順序執行成對的轉換。  
  
 ![重新著色，以便](../../../../docs/framework/winforms/advanced/media/recoloring01.gif "recoloring01")  
  
 色彩矩陣的項目會依照資料列和資料行索引 （以零為起始）。 例如，由 M [4] [2] 表示第五個資料列和第三個資料行的矩陣 M 中的項目。  
  
 5 × 5 身分識別矩陣 （如圖所示） 具有對角線上的 1 和 0 其他位置。 如果您將色彩向量乘以矩陣時，就不會變更色彩向量。 便利的方式，以形成色彩轉換的矩陣是單位矩陣以開頭，並且進行小幅變更產生所需的轉換。  
  
 ![重新著色，以便](../../../../docs/framework/winforms/advanced/media/recoloring02.gif "recoloring02")  
  
 矩陣和轉換的更詳細討論，請參閱[座標系統和轉換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)。  
  
## <a name="example"></a>範例  
 下列範例會為所有的一種色彩 （0.2、 0.0、 0.4、 1.0） 與前面段落中所述的轉換套用的映像。  
  
 下圖顯示在右側的原始左側映像，而且已轉換的映像。  
  
 ![色彩](../../../../docs/framework/winforms/advanced/media/colortrans1.png "colortrans1")  
  
 下列範例中的程式碼會使用下列步驟執行重新著色，以便：  
  
1.  初始化<xref:System.Drawing.Imaging.ColorMatrix>物件。  
  
2.  建立<xref:System.Drawing.Imaging.ImageAttributes>物件，並傳遞<xref:System.Drawing.Imaging.ColorMatrix>物件<xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A>方法<xref:System.Drawing.Imaging.ImageAttributes>物件。  
  
3.  傳遞<xref:System.Drawing.Imaging.ImageAttributes>物件<xref:System.Drawing.Graphics.DrawImage%2A>方法<xref:System.Drawing.Graphics>物件。  
  
 [!code-csharp[System.Drawing.RecoloringImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.RecoloringImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。  
  
## <a name="see-also"></a>另請參閱  
 [為影像重新著色](../../../../docs/framework/winforms/advanced/recoloring-images.md)  
 [座標系統和轉換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)
