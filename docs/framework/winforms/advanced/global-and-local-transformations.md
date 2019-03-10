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
ms.openlocfilehash: 07ef61e3a41448f051fb9b7da2cfd91d7cbf26b5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711846"
---
# <a name="global-and-local-transformations"></a>全域和區域轉換
「 全域 」 轉換這種轉換會套用至由繪製每個項目指定<xref:System.Drawing.Graphics>物件。 相較之下，「 本機 」 轉換是套用至特定的項目要繪製的轉換。  
  
## <a name="global-transformations"></a>全域的轉換  
 若要建立全域的轉換，建構<xref:System.Drawing.Graphics>物件，然後再操作其<xref:System.Drawing.Graphics.Transform%2A>屬性。 <xref:System.Drawing.Graphics.Transform%2A>屬性是<xref:System.Drawing.Drawing2D.Matrix>物件，因此它可以保留任何順序的仿射轉換。 轉換儲存在<xref:System.Drawing.Graphics.Transform%2A>屬性稱為全局轉換。 <xref:System.Drawing.Graphics>類別提供多種方法來建立複合的全局轉換： <xref:System.Drawing.Graphics.MultiplyTransform%2A>， <xref:System.Drawing.Graphics.RotateTransform%2A>， <xref:System.Drawing.Graphics.ScaleTransform%2A>，和<xref:System.Drawing.Graphics.TranslateTransform%2A>。 下列範例會繪製一個橢圓形兩次： 一次之前建立的自然變換和之後的一次。 轉換第一次調整 y 方向的 0.5 倍然後平移 x 方向的 50 個單位，並再旋轉 30 度。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.CoordinateSystems#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#21)]  
  
 下圖顯示參與轉換矩陣。  
  
 ![Transformations](./media/aboutgdip05-art14.gif "AboutGdip05_art14")  
  
> [!NOTE]
>  在上述範例中，省略符號會旋轉的座標系統中，工作區的左上角原點。 這會產生旋轉橢圓形繞著自己中心不同的結果。  
  
## <a name="local-transformations"></a>區域轉換  
 局部的轉換套用至特定的項目要繪製。 例如，<xref:System.Drawing.Drawing2D.GraphicsPath>物件具有<xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A>方法，可讓您將資料點，該路徑的轉換。 下列範例會繪製任何轉換的矩形和旋轉轉換的路徑。 （假設沒有任何全局轉換）。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.CoordinateSystems#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#22)]  
  
 您可以結合自然變換和區域轉換來達成各種不同的結果。 例如，您可以使用全局轉換到修改座標系統，並使用本機的轉換，旋轉和縮放新的座標系統上所繪製的物件。  
  
 假設您想要具有其原始 200 像素為單位從工作區左邊緣和工作區頂端的 150 個像素座標系統。 此外，假設您想要的像素，與 x 軸指向右側和 y 軸向上的測量單位。 預設座標系統中將有 y 軸指向下方，因此您必須執行反映在水平軸。 下圖顯示此類反射的矩陣。  
  
 ![Transformations](./media/aboutgdip05-art15.gif "AboutGdip05_art15")  
  
 接下來，假設您要執行轉譯的 200 個單位向右和向下的 150 單位。  
  
 下列範例會建立所設定的自然變換剛描述的座標系統<xref:System.Drawing.Graphics>物件。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.CoordinateSystems#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#23)]  
  
 下列程式碼 （放在前述範例中的結尾） 會建立單一的新的座標系統的原始位置左下方角矩形組成的路徑。 矩形填滿一次搭配任何本機的轉換與一次本機的轉換。 「 本機 」 轉換包含水平調整，後面接著 30 度旋轉的 2 倍。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#24](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#24)]
 [!code-vb[System.Drawing.CoordinateSystems#24](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#24)]  
  
 下圖顯示新的座標系統和兩個矩形。  
  
 ![Transformations](./media/aboutgdip05-art16.gif "AboutGdip05_art16")  
  
## <a name="see-also"></a>另請參閱
- [座標系統和轉換](coordinate-systems-and-transformations.md)
- [使用 Managed GDI+ 中的轉換](using-transformations-in-managed-gdi.md)
