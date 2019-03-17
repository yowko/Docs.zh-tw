---
title: 使用巢狀圖形容器
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], nested containers
- graphics [Windows Forms], clipping
- graphics [Windows Forms], transformations in nested objects
ms.assetid: a0d9f178-43a4-4323-bb5a-d3e3f77ae6c1
ms.openlocfilehash: a66edd0297b723b81c31675c9b0e6b6def9ed10a
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125859"
---
# <a name="using-nested-graphics-containers"></a>使用巢狀圖形容器
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供容器，您可以使用暫時取代或擴充中狀態的一部分<xref:System.Drawing.Graphics>物件。 您可以建立一個容器藉由呼叫<xref:System.Drawing.Graphics.BeginContainer%2A>方法的<xref:System.Drawing.Graphics>物件。 您可以呼叫<xref:System.Drawing.Graphics.BeginContainer%2A>重複，以形成巢狀的容器。 每次呼叫<xref:System.Drawing.Graphics.BeginContainer%2A>必須藉由呼叫配對<xref:System.Drawing.Graphics.EndContainer%2A>。  
  
## <a name="transformations-in-nested-containers"></a>巢狀容器中的轉換  
 下列範例會建立<xref:System.Drawing.Graphics>物件和容器，以在其中<xref:System.Drawing.Graphics>物件。 自然變換<xref:System.Drawing.Graphics>物件是在 x 方向轉譯 100 單位和 80 的單位，在 y 方向。 容器的自然變換是 30 度的旋轉。 程式碼進行呼叫`DrawRectangle(pen, -60, -30, 120, 60)`兩次。 第一次呼叫<xref:System.Drawing.Graphics.DrawRectangle%2A>內的容器，亦即，呼叫是對呼叫之間<xref:System.Drawing.Graphics.BeginContainer%2A>和<xref:System.Drawing.Graphics.EndContainer%2A>。 第二次呼叫<xref:System.Drawing.Graphics.DrawRectangle%2A>之後呼叫<xref:System.Drawing.Graphics.EndContainer%2A>。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#61)]  
  
 在上述程式碼中，從在容器內繪製的矩形轉換第一次以全局轉換 （輪替） 的容器，再以的自然變換<xref:System.Drawing.Graphics>物件 （轉譯）。 從容器外繪製的矩形只轉換的自然變換<xref:System.Drawing.Graphics>物件 （轉譯）。 下圖顯示兩個矩形： 
  
 ![顯示巢狀的容器的圖例。](./media/using-nested-graphics-containers/nested-containers-illustration.png)  
  
## <a name="clipping-in-nested-containers"></a>巢狀容器中的裁剪功能  
 下列範例示範如何巢狀的容器處理裁剪區域。 程式碼會建立<xref:System.Drawing.Graphics>物件和容器，以在其中<xref:System.Drawing.Graphics>物件。 裁剪區域<xref:System.Drawing.Graphics>物件是矩形，容器的裁剪區域是一個橢圓形。 程式碼會建立兩個呼叫<xref:System.Drawing.Graphics.DrawLine%2A>方法。 第一次呼叫<xref:System.Drawing.Graphics.DrawLine%2A>內的第二個呼叫與容器<xref:System.Drawing.Graphics.DrawLine%2A>超出容器 (在呼叫之後<xref:System.Drawing.Graphics.EndContainer%2A>)。 第一行是由兩個裁剪區域的交集裁剪。 第二行只會裁剪矩形的裁剪區域<xref:System.Drawing.Graphics>物件。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#62)]
 [!code-vb[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#62)]  
  
 下圖顯示兩個裁剪的線條：
  
 ![顯示圖例，裁剪的線條的巢狀的容器。](./media/using-nested-graphics-containers/nested-container-clipped-lines.png)  
  
 如上述兩個範例所示，將會累積在巢狀容器轉換和裁剪區域。 如果您設定容器的全局轉換和<xref:System.Drawing.Graphics>物件，這兩種轉換會套用至從繪製在容器內的項目。 容器的轉換會套用第一個和轉換<xref:System.Drawing.Graphics>物件將會套用第二個。 如果您設定容器的裁剪區域和<xref:System.Drawing.Graphics>物件，在兩個裁剪區域的交集會裁剪取自容器內的項目。  
  
## <a name="quality-settings-in-nested-containers"></a>巢狀容器中的品質設定  
 品質設定 (<xref:System.Drawing.Graphics.SmoothingMode%2A>， <xref:System.Drawing.Graphics.TextRenderingHint%2A>，等等) 中巢狀的容器不是累計的; 相反地，容器的品質設定暫時取代的品質設定<xref:System.Drawing.Graphics>物件。 當您建立新的容器時，該容器的品質設定會設為預設值。 例如，假設您有<xref:System.Drawing.Graphics>平滑模式物件<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>。 當您建立容器時，容器內的平滑化模式會是預設的平滑處理模式。 您可以自由地設定平滑模式的容器，並根據您設定的模式來繪製從繪製在容器內的任何項目。 繪製呼叫之後的項目<xref:System.Drawing.Graphics.EndContainer%2A>會繪製根據平滑模式 (<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>)，已備妥再呼叫<xref:System.Drawing.Graphics.BeginContainer%2A>。  
  
## <a name="several-layers-of-nested-containers"></a>數個層級的巢狀容器  
 您不一定要在一個容器<xref:System.Drawing.Graphics>物件。 您可以建立一連串的容器，每個巢狀方式置於先前所述，，您可以指定全局轉換、 裁剪區域和每一個這些巢狀容器的品質設定。 如果您呼叫繪製方法從最內層的容器時，轉換會套用順序，從最內層的容器開始和結尾最外層的容器中。 所有的裁剪區域的交集會裁剪取自最內層的容器項目。  
  
 下列範例會建立<xref:System.Drawing.Graphics>物件，並設定其文字轉譯提示<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>。 程式碼會建立兩個容器，巢狀於另一個。 外部容器的文字呈現提示設定為<xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>，而內部容器的文字呈現提示設定為<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>。 程式碼繪製三個字串： 從內部的容器，從外部的容器，其中一個，另一個從<xref:System.Drawing.Graphics>物件本身。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#63)]
 [!code-vb[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#63)]  
  
 下圖顯示三個字串。 繪製從內部的容器，以及從字串<xref:System.Drawing.Graphics>物件會由反鋸齒功能經過平滑處理。 因為取自外部容器的字串不藉由消除鋸齒平滑<xref:System.Drawing.Graphics.TextRenderingHint%2A>屬性設定為<xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>。  
  
 ![顯示圖例，取自巢狀容器的字串。](./media/using-nested-graphics-containers/nested-containers-three-strings.png)  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Drawing.Graphics>
- [管理圖形物件的狀態](managing-the-state-of-a-graphics-object.md)
