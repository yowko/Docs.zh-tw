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
ms.openlocfilehash: a5a8201f0adb44347bdd42081e0263176d179321
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="global-and-local-transformations"></a>全域和區域轉換
全域轉換為轉換套用至所繪製的每個項目的指定<xref:System.Drawing.Graphics>物件。 相反地，區域轉換為套用至要繪製的特定項目的轉換。  
  
## <a name="global-transformations"></a>全域轉換  
 若要建立全域的轉換，建構<xref:System.Drawing.Graphics>物件，然後再操作其<xref:System.Drawing.Graphics.Transform%2A>屬性。 <xref:System.Drawing.Graphics.Transform%2A>屬性是<xref:System.Drawing.Drawing2D.Matrix>物件，因此它能容納仿射轉換的任何序列。 轉換儲存在<xref:System.Drawing.Graphics.Transform%2A>呼叫全局轉換的屬性。 <xref:System.Drawing.Graphics>類別提供數種方法建立複合的自然變換： <xref:System.Drawing.Graphics.MultiplyTransform%2A>， <xref:System.Drawing.Graphics.RotateTransform%2A>， <xref:System.Drawing.Graphics.ScaleTransform%2A>，和<xref:System.Drawing.Graphics.TranslateTransform%2A>。 下列範例會繪製橢圓形兩次： 一次之前建立的自然變換和之後的一次。 轉換會先根據 0.5 y 方向的因數來縮放則轉換 x 方向的 50 個單位，並再旋轉 30 度。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#21)]  
  
 下圖顯示參與轉換矩陣。  
  
 ![轉換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art14.gif "AboutGdip05_art14")  
  
> [!NOTE]
>  在上述範例中，會在用戶端區域的左上角座標系統的原點旋轉橢圓形。 這會產生不同的結果旋轉中心橢圓形。  
  
## <a name="local-transformations"></a>區域轉換  
 局部的轉換套用至要繪製的特定項目。 例如，<xref:System.Drawing.Drawing2D.GraphicsPath>物件具有<xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A>方法，可讓您轉換該路徑的資料點。 下列範例會繪製任何轉換的矩形和旋轉轉換的路徑。 （假設是沒有全局轉換）。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#22)]  
  
 您可以結合自然變換和區域轉換來達成各種不同的結果。 例如，您可以使用全局轉換修訂座標系統，並使用本機的轉換，旋轉和縮放繪製在新的座標系統上的物件。  
  
 假設您想從工作區左邊緣與其來源 200 像素和 150 個像素，從用戶端區域的頂端座標系統。 此外，假設您想要的度量單位為像素 x 軸指向右側和 y 軸向上。 預設座標系統有 y 軸指向下方，因此您需要執行反映在水平軸。 下圖顯示此類反射的矩陣。  
  
 ![轉換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art15.gif "AboutGdip05_art15")  
  
 接下來，假設您要執行轉譯 200 的單位，向右和向下的 150 單位。  
  
 下列範例會建立剛剛所述設定的自然變換的座標系統<xref:System.Drawing.Graphics>物件。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#23)]  
  
 下列程式碼 （放在前述範例中的結尾） 會建立單一的新的座標系統的原始位置左下角矩形組成的路徑。 矩形填滿一次使用任何本機的轉換，另一次使用區域轉換。 「 本機 」 轉換包含水平延展，後面接著 30 度旋轉的 2 倍。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#24)]
 [!code-vb[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#24)]  
  
 下圖顯示新的座標系統和兩個矩形。  
  
 ![轉換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art16.gif "AboutGdip05_art16")  
  
## <a name="see-also"></a>另請參閱  
 [座標系統和轉換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [使用 Managed GDI+ 中的轉換](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
