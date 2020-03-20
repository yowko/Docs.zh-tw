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
ms.openlocfilehash: 460ebb37ee62691a1e282f756840121fd378ebd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182469"
---
# <a name="using-nested-graphics-containers"></a>使用巢狀圖形容器
GDI+ 提供了可用於臨時替換或增強<xref:System.Drawing.Graphics>物件中部分狀態的容器。 通過調用<xref:System.Drawing.Graphics.BeginContainer%2A><xref:System.Drawing.Graphics>物件的方法創建容器。 您可以重複調用<xref:System.Drawing.Graphics.BeginContainer%2A>以形成嵌套容器。 到 的每個<xref:System.Drawing.Graphics.BeginContainer%2A>調用都必須與 調用<xref:System.Drawing.Graphics.EndContainer%2A>配對。  
  
## <a name="transformations-in-nested-containers"></a>嵌套容器中的轉換  
 下面的示例在該<xref:System.Drawing.Graphics><xref:System.Drawing.Graphics>物件中創建一個物件和一個容器。 <xref:System.Drawing.Graphics>物體的世界變換是 x 方向的平移 100 個單位，y 方向為 80 個單位。 容器的世界變換是30度的旋轉。 代碼發出調用`DrawRectangle(pen, -60, -30, 120, 60)`兩次。 第<xref:System.Drawing.Graphics.DrawRectangle%2A>一個調用是在容器內;也就是說，調用位於 調用<xref:System.Drawing.Graphics.BeginContainer%2A>和<xref:System.Drawing.Graphics.EndContainer%2A>之間的調用中。 的第二個調用<xref:System.Drawing.Graphics.DrawRectangle%2A>是在調用<xref:System.Drawing.Graphics.EndContainer%2A>之後。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#61)]  
  
 在前面的代碼中，從容器內部繪製的矩形首先由容器的世界變換（旋轉）轉換，然後由<xref:System.Drawing.Graphics>物件的世界變換（轉換）轉換。 僅由<xref:System.Drawing.Graphics>物件的世界變換（轉換）從容器外部繪製的矩形進行轉換。 下圖顯示了兩個矩形：
  
 ![顯示嵌套容器的插圖。](./media/using-nested-graphics-containers/nested-containers-illustration.png)  
  
## <a name="clipping-in-nested-containers"></a>在嵌套容器中剪切  
 下面的示例演示嵌套容器如何處理裁剪區域。 該代碼在該<xref:System.Drawing.Graphics><xref:System.Drawing.Graphics>物件中創建一個物件和一個容器。 <xref:System.Drawing.Graphics>物件的裁剪區域是一個矩形，容器的裁剪區域是一個橢圓。 代碼對<xref:System.Drawing.Graphics.DrawLine%2A>該方法進行兩次調用。 向的第一個<xref:System.Drawing.Graphics.DrawLine%2A>調用在容器內，第二個調用<xref:System.Drawing.Graphics.DrawLine%2A>在容器外部（在調用 之後）。 <xref:System.Drawing.Graphics.EndContainer%2A> 第一行由兩個裁剪區域的交點剪切。 第二行僅由<xref:System.Drawing.Graphics>物件的矩形裁剪區域進行剪切。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#62)]
 [!code-vb[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#62)]  
  
 下圖顯示了兩條剪貼線：
  
 ![顯示帶有剪切線的嵌套容器的插圖。](./media/using-nested-graphics-containers/nested-container-clipped-lines.png)  
  
 如前兩個示例所示，轉換和裁剪區域在嵌套容器中是累積的。 如果設置容器和<xref:System.Drawing.Graphics>物件的世界變換，則兩個轉換將應用於從容器內部提取的專案。 將首先應用容器的變換，然後應用<xref:System.Drawing.Graphics>物件的變換。 如果設置容器和<xref:System.Drawing.Graphics>物件的裁剪區域，則從容器內部繪製的專案將由兩個裁剪區域的交點剪切。  
  
## <a name="quality-settings-in-nested-containers"></a>嵌套容器中的品質設置  
 嵌套容器中<xref:System.Drawing.Graphics.SmoothingMode%2A>的品質<xref:System.Drawing.Graphics.TextRenderingHint%2A>設置 （、等） 不是累積的;相反，容器的品質設置會暫時替換<xref:System.Drawing.Graphics>物件的品質設置。 創建新容器時，該容器的品質設置將設置為預設值。 例如，假設您有一個<xref:System.Drawing.Graphics>具有平滑模式的物件。 <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> 創建容器時，容器內的平滑模式是預設平滑模式。 您可以自由設置容器的平滑模式，並且從容器內部繪製的任何專案都將根據您設置的模式繪製。 調用後繪製的專案<xref:System.Drawing.Graphics.EndContainer%2A>將根據調用<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias><xref:System.Drawing.Graphics.BeginContainer%2A>之前就位的平滑模式 （） 繪製。  
  
## <a name="several-layers-of-nested-containers"></a>嵌套容器的幾個層  
 您不限於物件中的一個<xref:System.Drawing.Graphics>容器。 您可以創建一系列容器，每個容器都嵌套在前面，並且可以指定每個嵌套容器的世界轉換、裁剪區域和品質設置。 如果從最內層容器內調用繪圖方法，則轉換將按順序應用，從最內層容器開始，到最外層容器結束。 從最內側容器內繪製的專案將由所有裁剪區域的交集剪切。  
  
 下面的示例創建一個<xref:System.Drawing.Graphics>物件，並將其文本呈現提示設置到<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>。 代碼創建兩個容器，一個嵌套在另一個容器中。 外部容器的文本呈現提示設置為<xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>，內部容器的文本呈現提示設置為<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>。 代碼繪製三個字串：一個來自內部容器，一個來自外部容器，一個來自<xref:System.Drawing.Graphics>物件本身。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#63)]
 [!code-vb[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#63)]  
  
 下圖顯示了三個字串。 從內部容器和物件繪製的<xref:System.Drawing.Graphics>字串通過抗鋸齒平滑。 從外部容器繪製的字串不會通過反鋸齒平滑，<xref:System.Drawing.Graphics.TextRenderingHint%2A>因為屬性設置為<xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>。  
  
 ![顯示從嵌套容器中提取的字串的插圖。](./media/using-nested-graphics-containers/nested-containers-three-strings.png)  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Graphics>
- [管理圖形物件的狀態](managing-the-state-of-a-graphics-object.md)
