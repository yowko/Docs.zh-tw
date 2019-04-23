---
title: 使用轉換調整色彩
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], for scaling colors
- colors [Windows Forms], scaling
ms.assetid: df23c887-7fd6-4b15-ad94-e30b5bd4b849
ms.openlocfilehash: 9c8f2392137d04f56096120cec64b60c42c47419
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107976"
---
# <a name="using-transformations-to-scale-colors"></a>使用轉換調整色彩
一或多個所提供的數字的四個色彩元件，將乘上縮放轉換。 下表提供代表調整色彩矩陣項目。  
  
|若要調整的元件|矩陣項目|  
|----------------------------|------------------|  
|紅色|[0][0]|  
|綠色|[1][1]|  
|藍色|[2][2]|  
|Alpha|[3][3]|  
  
## <a name="scaling-one-color"></a>調整的一種色彩  
 下列範例會建構<xref:System.Drawing.Image>ColorBars2.bmp 檔案中的物件。 然後程式碼會調整每個像素的藍色元件映像中的 2 倍。 原始的映像與已轉換的映像一起繪製。  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 下圖顯示在右側的原始的映像，在左邊和縮放的影像：  
  
 ![如果螢幕擷取畫面會比較原始和調整色彩。](./media/using-transformations-to-scale-colors/four-bar-scale-one-color.png)  
  
 下表列出四個橫條的色彩向量之前, 和之後的藍色的縮放比例。 請注意，在第四個彩色橫條的藍色元件發生從 0.8 0.6。 這是因為[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]會保留結果的小數部分。 例如，(2)(0.8) version=1.6 應用程式，而 1.6 的小數部分是 0.6。 保留小數部分，可確保結果一定是在間隔 [0，1]。  
  
|原始|調整|  
|--------------|------------|  
|(0.4, 0.4, 0.4, 1)|(0.4, 0.4, 0.8, 1)|  
|(0.4, 0.2, 0.2, 1)|(0.4, 0.2, 0.4, 1)|  
|(0.2, 0.4, 0.2, 1)|(0.2, 0.4, 0.4, 1)|  
|(0.4, 0.4, 0.8, 1)|(0.4, 0.4, 0.6, 1)|  
  
## <a name="scaling-multiple-colors"></a>多個色彩調整  
 下列範例會建構<xref:System.Drawing.Image>ColorBars2.bmp 檔案中的物件。 然後程式碼會調整映像中每個像素的紅色、 綠色和藍色元件。 紅色元件相應減少百分之 25 的綠色元件相應減少 35%，藍色元件相應減少 50%。  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 下圖顯示在右側的原始的映像，在左邊和縮放的影像：  
  
 ![如果螢幕擷取畫面會比較原始和調整色彩。](./media/using-transformations-to-scale-colors/four-bar-scale-multiple-colors.png)  
  
 下表列出四個橫條的色彩向量之前, 和之後紅色、 綠色和藍色的調整。  
  
|原始|調整|  
|--------------|------------|  
|(0.6, 0.6, 0.6, 1)|(0.45, 0.39, 0.3, 1)|  
|(0, 1, 1, 1)|(0, 0.65, 0.5, 1)|  
|(1, 1, 0, 1)|(0.75, 0.65, 0, 1)|  
|(1, 0, 1, 1)|(0.75, 0, 0.5, 1)|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Windows Forms 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)
- [為影像重新著色](recoloring-images.md)
