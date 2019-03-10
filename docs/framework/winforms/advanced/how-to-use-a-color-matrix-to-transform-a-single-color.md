---
title: HOW TO：使用色彩矩陣轉換單一色彩
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image colors [Windows Forms], transforming
- color matrices [Windows Forms], using
ms.assetid: 44df4556-a433-49c0-ac0f-9a12063a5860
ms.openlocfilehash: f19039c69f27f78e838ea1a891690451af3f0cdc
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705593"
---
# <a name="how-to-use-a-color-matrix-to-transform-a-single-color"></a>HOW TO：使用色彩矩陣轉換單一色彩
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供<xref:System.Drawing.Image>和<xref:System.Drawing.Bitmap>來儲存及操作影像的類別。 <xref:System.Drawing.Image> 和<xref:System.Drawing.Bitmap>物件會儲存每個像素的色彩為 32 位元數字：8 位元用於紅色、 綠色、 藍色和 alpha 的每個。 每四個元件是從 0 到 255，0 代表不含濃度，表示完整濃度 255 的數字。 Alpha 元件指定色彩的透明度：0 是完全透明的而且完全不透明 255。  
  
 色彩向量是表單 （紅色、 綠色、 藍色、 alpha） 的 4-tuple。 例如，色彩向量 （0，255，0，255） 表示不透明的色彩，含紅色或藍色，但有綠色的濃度。  
  
 表示色彩的另一個慣例會將數字 1 用於完整濃度。 使用這個慣例，會由向量 （0、 1、 0、 1） 表示前面段落中所述的色彩。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 會使用 1 慣例成完整濃度，當它執行色彩轉換。  
  
 您可以套用色彩向量線性轉換 （旋轉、 縮放和 like） 乘以 4 × 4 矩陣色彩向量。 不過，您無法使用 4 × 4 矩陣，以執行翻譯 （非線性）。 如果您將虛擬的第五個座標 （例如，數字 1） 加入每一個色彩向量時，您可以使用 5 × 5 矩陣来套用的線性轉換和轉譯的任意組合。 轉換，其中包含後面接著翻譯的線性轉換稱為仿射轉換。  
  
 例如，假設您想要開始色彩 （0.2，0.0、 0.4，1.0），並套用下列轉換：  
  
1.  雙重紅色元件  
  
2.  加上紅色、 綠色和藍色元件 0.2  
  
 下列矩陣乘法會依列出的順序執行成對的轉換。  
  
 ![重新著色](./media/recoloring01.gif "recoloring01")  
  
 色彩矩陣的項目編製索引 （以零為起始） 的資料列，然後資料行。 比方說，第五個資料列和第三個資料行的矩陣 M 中的項目被以 M [4] [2]。  
  
 5 × 5 身分識別矩陣 （下圖所示） 具有對角線上的 1 和 0 的其他位置。 如果您將色彩向量乘以身分識別矩陣時，就不會變更色彩的向量。 便利的方式來形成 「 色彩 」 轉換的矩陣是以身分識別矩陣開始進行小幅變更會產生所需的轉換。  
  
 ![重新著色](./media/recoloring02.gif "recoloring02")  
  
 矩陣和轉換的詳細討論，請參閱[座標系統和轉換](coordinate-systems-and-transformations.md)。  
  
## <a name="example"></a>範例  
 下列範例會為所有的一種色彩 （0.2，0.0、 0.4，1.0） 與先前段落中所述的轉換套用的映像。  
  
 下圖顯示原始的映像，在左邊和轉換後的映像，在右邊。  
  
 ![色彩](./media/colortrans1.png "colortrans1")  
  
 下列範例中的程式碼會使用下列步驟執行的重新著色：  
  
1.  初始化<xref:System.Drawing.Imaging.ColorMatrix>物件。  
  
2.  建立<xref:System.Drawing.Imaging.ImageAttributes>物件，並傳遞<xref:System.Drawing.Imaging.ColorMatrix>物件<xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A>方法<xref:System.Drawing.Imaging.ImageAttributes>物件。  
  
3.  傳遞<xref:System.Drawing.Imaging.ImageAttributes>物件至<xref:System.Drawing.Graphics.DrawImage%2A>方法<xref:System.Drawing.Graphics>物件。  
  
 [!code-csharp[System.Drawing.RecoloringImages#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.RecoloringImages#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。  
  
## <a name="see-also"></a>另請參閱
- [為影像重新著色](recoloring-images.md)
- [座標系統和轉換](coordinate-systems-and-transformations.md)
