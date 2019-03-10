---
title: 使用全局轉換
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], world transformation
- world transformation [Windows Forms], examples
ms.assetid: 1e717711-1361-448e-aa49-0f3ec43110c9
ms.openlocfilehash: cc6bcca42e84580199f75c64087af6d98f476d4b
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715694"
---
# <a name="using-the-world-transformation"></a>使用全局轉換
全局轉換是屬性<xref:System.Drawing.Graphics>類別。 指定全局轉換的數字會儲存在<xref:System.Drawing.Drawing2D.Matrix>物件，代表 3 × 3 的矩陣。 <xref:System.Drawing.Drawing2D.Matrix>和<xref:System.Drawing.Graphics>類別有幾種方式來設定數字的自然變換矩陣中。  
  
## <a name="different-types-of-transformations"></a>不同類型的轉換  
 在下列範例中，程式碼，先建立 50 x 50 矩形，並放在原點 （0，0）。 原點是在用戶端區域的左上角。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.MiscLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#11)]  
  
 下列程式碼適用於展開矩形在 x 方向的 1.75，在 y 方向的 0.5 倍壓縮矩形的縮放轉換：  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.MiscLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#12)]  
  
 結果是在 x 方向較長且少於 y 方向的原始矩形。  
  
 若要旋轉而不是縮放矩形，請使用下列程式碼：  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.MiscLegacyTopics#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#13)]  
  
 若要翻譯的矩形，請使用下列程式碼：  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.MiscLegacyTopics#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Drawing.Drawing2D.Matrix>
- [座標系統和轉換](coordinate-systems-and-transformations.md)
- [使用 Managed GDI+ 中的轉換](using-transformations-in-managed-gdi.md)
