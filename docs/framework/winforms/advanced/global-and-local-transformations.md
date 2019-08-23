---
title: 全域和區域轉換
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- matrices [Windows Forms], using transformations
- transformations [Windows Forms], global
- transformations [Windows Forms], local
ms.assetid: b601d66d-d572-4f11-9d2e-92f0dc8893f3
ms.openlocfilehash: f62efb31e95b0797272997fadbc28459579a0de0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955194"
---
# <a name="global-and-local-transformations"></a>全域和區域轉換
全域轉換是一種轉換, 適用于指定<xref:System.Drawing.Graphics>物件所繪製的每個專案。 相反地, 「局部轉換」是一種轉換, 適用于要繪製的特定專案。  
  
## <a name="global-transformations"></a>全域轉換  
 若要建立全域轉換, 請先<xref:System.Drawing.Graphics>建立物件, 然後再操控<xref:System.Drawing.Graphics.Transform%2A>其屬性。 <xref:System.Drawing.Graphics.Transform%2A> 屬性<xref:System.Drawing.Drawing2D.Matrix>是物件, 因此可以保留任何一系列的仿射轉換。 儲存在<xref:System.Drawing.Graphics.Transform%2A>屬性中的轉換稱為「世界轉換」。 <xref:System.Drawing.Graphics.RotateTransform%2A> <xref:System.Drawing.Graphics.MultiplyTransform%2A> <xref:System.Drawing.Graphics.TranslateTransform%2A> <xref:System.Drawing.Graphics.ScaleTransform%2A>類別提供數種方法來建立複合世界轉換:、、和。 <xref:System.Drawing.Graphics> 下列範例會繪製一個橢圓形兩次: 一次是在建立世界轉換之後, 一次在之後。 轉換會先依 y 方向調整為0.5 因數, 然後在 x 方向轉譯50單位, 然後旋轉30度。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.CoordinateSystems#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#21)]  
  
 下圖顯示轉換所涉及的矩陣。  
  
 ![Transformations](./media/aboutgdip05-art14.gif "AboutGdip05_art14")  
  
> [!NOTE]
> 在上述範例中, 橢圓形會繞過座標系統的原點, 位於工作區的左上角。 這會產生不同的結果, 而不是旋轉其本身中心的橢圓形。  
  
## <a name="local-transformations"></a>本機轉換  
 本機轉換會套用至要繪製的特定專案。 例如, <xref:System.Drawing.Drawing2D.GraphicsPath>物件<xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A>的方法可讓您轉換該路徑的資料點。 下列範例會繪製沒有轉換的矩形, 以及具有旋轉轉換的路徑。 (假設沒有任何世界轉換)。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.CoordinateSystems#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#22)]  
  
 您可以結合「世界」轉換與「本機」轉換來達到各種不同的結果。 例如, 您可以使用「世界」轉換來修改座標系統, 並使用「區域」轉換來旋轉和縮放在新座標系統上繪製的物件。  
  
 假設您想要一個座標系統, 其原點為200圖元, 從工作區的左邊緣到工作區的頂端150圖元。 此外, 假設您希望測量單位是圖元, 而 X 軸指向右側, 而 y 軸指向上方。 預設座標系統會將 y 軸指向下方, 因此您需要跨水準軸執行反映。 下圖顯示這類反映的矩陣。  
  
 ![Transformations](./media/aboutgdip05-art15.gif "AboutGdip05_art15")  
  
 接下來, 假設您需要向右和150個單位執行轉譯200單位。  
  
 下列範例會藉由設定<xref:System.Drawing.Graphics>物件的世界轉換, 建立剛才描述的座標系統。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.CoordinateSystems#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#23)]  
  
 下列程式碼 (放在上述範例的結尾) 會建立一個路徑, 其中包含一個矩形, 其左下角位於新座標系統的原點。 矩形會填入一次, 但不含本機轉換, 一次是使用本機轉換。 「局部」轉換是由一因數2的水準調整組成, 後面接著30度的旋轉。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#24](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#24)]
 [!code-vb[System.Drawing.CoordinateSystems#24](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#24)]  
  
 下圖顯示新的座標系統和兩個矩形。  
  
 ![Transformations](./media/aboutgdip05-art16.gif "AboutGdip05_art16")  
  
## <a name="see-also"></a>另請參閱

- [座標系統和轉換](coordinate-systems-and-transformations.md)
- [使用 Managed GDI+ 中的轉換](using-transformations-in-managed-gdi.md)
