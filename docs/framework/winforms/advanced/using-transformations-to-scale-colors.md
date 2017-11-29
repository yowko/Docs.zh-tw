---
title: "使用轉換調整色彩"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], for scaling colors
- colors [Windows Forms], scaling
ms.assetid: df23c887-7fd6-4b15-ad94-e30b5bd4b849
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a4584b74cd7a394f7dd04d0cfba150b907ca7c82
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="using-transformations-to-scale-colors"></a>使用轉換調整色彩
一或多個四個色彩元件的數字會乘以縮放轉換。 下表提供代表調整色彩矩陣項目。  
  
|要調整大小的元件|矩陣項目|  
|----------------------------|------------------|  
|紅色|[0][0]|  
|綠色|[1][1]|  
|藍色|[2][2]|  
|Alpha|[3][3]|  
  
## <a name="scaling-one-color"></a>調整一種色彩  
 下列範例會建構<xref:System.Drawing.Image>ColorBars2.bmp 檔案中的物件。 然後程式碼可調整每個像素的藍色元件映像中的 2 倍。 在原始圖像是繪製轉換後的映像的旁邊。  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 下圖顯示在右側的原始左側的映像和縮放的影像。  
  
 ![調整色彩](../../../../docs/framework/winforms/advanced/media/colortrans3.png "colortrans3")  
  
 下表列出四個橫條的色彩向量之前和之後藍色的縮放比例。 請注意，在第四個彩色橫條的藍色元件發生從 0.8 0.6。 這是因為[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]保留結果的小數部分。 例如，(2)(0.8) = 1.6，和 1.6 的小數部分是 0.6。 保留僅小數部分，可確保結果一律會在間隔 [0，1]。  
  
|原始|縮放|  
|--------------|------------|  
|(0.4, 0.4, 0.4, 1)|(0.4, 0.4, 0.8, 1)|  
|(0.4, 0.2, 0.2, 1)|(0.4, 0.2, 0.4, 1)|  
|(0.2, 0.4, 0.2, 1)|(0.2, 0.4, 0.4, 1)|  
|(0.4, 0.4, 0.8, 1)|(0.4, 0.4, 0.6, 1)|  
  
## <a name="scaling-multiple-colors"></a>多個色彩調整  
 下列範例會建構<xref:System.Drawing.Image>ColorBars2.bmp 檔案中的物件。 然後程式碼會縮放映像中的每個像素的紅色、 綠色和藍色元件。 紅色元件會縮小 25%、 綠色元件會縮小 35%和藍色元件會縮小 50%。  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 下圖顯示在右側的原始左側的映像和縮放的影像。  
  
 ![調整色彩](../../../../docs/framework/winforms/advanced/media/colortrans4.png "colortrans4")  
  
 下表列出四個橫條的色彩向量之前和之後紅色、 綠色和藍色的調整。  
  
|原始|縮放|  
|--------------|------------|  
|(0.6, 0.6, 0.6, 1)|(0.45, 0.39, 0.3, 1)|  
|(0, 1, 1, 1)|(0, 0.65, 0.5, 1)|  
|(1, 1, 0, 1)|(0.75, 0.65, 0, 1)|  
|(1, 0, 1, 1)|(0.75, 0, 0.5, 1)|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [Windows Forms 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [為影像重新著色](../../../../docs/framework/winforms/advanced/recoloring-images.md)
