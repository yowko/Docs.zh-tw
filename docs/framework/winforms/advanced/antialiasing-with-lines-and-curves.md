---
title: 線條和曲線的反鋸齒功能
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- antialiasing
- antialiasing [Windows Forms], smoothing modes
- GDI+, antialiasing
ms.assetid: 810da1a4-c136-4abf-88df-68e49efdd8d4
ms.openlocfilehash: cbc9033f18f1ab255862c8f8e2891aa9b68cf8d6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61961072"
---
# <a name="antialiasing-with-lines-and-curves"></a>線條和曲線的反鋸齒功能
當您使用[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]繪製一條線，您提供的起點和結束點的行，但您沒有提供任何資訊的個別像素，該行。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 若要判斷哪一個像素為單位將會開啟到特定顯示裝置上顯示線條的顯示驅動程式軟體一起運作。  
  
## <a name="aliasing"></a>別名  
 請考慮直接紅線從點 （4，2） 進入點 （16，10）。 假設座標系統的原點位於左上角和測量單位為像素。 也假設，x 軸指向右側，而 y 軸往下。 下圖顯示彩色背景上繪製的紅線放大的的檢視。  
  
 ![行，不使用反鋸齒](./media/aboutgdip02-art33.gif "AboutGdip02_Art33")  
  
 紅色的像素，用來轉譯線條是不透明的。 行中有任何半透明的像素為單位。 這種類型的一行轉譯所產生的線條有不規則的外觀和該行看起來有點像階梯。 這項技術會代表某一行的階梯稱為別名;階梯是在假設線的別名。  
  
## <a name="antialiasing"></a>消除鋸齒功能  
 繪製線條的更複雜的技術牽涉到使用不透明的像素為單位以及部分透明像素為單位。 像素為單位設定為純紅色或紅色和背景色彩的混合體，以根據接近行。 這種類型的轉譯稱為反鋸齒功能，而導致人們的眼睛視為較平滑的列。 下圖顯示如何將特定的像素為單位混合與背景以產生反鋸齒線條。  
  
 ![消除鋸齒線條](./media/aboutgdip02-art34.gif "AboutGdip02_Art34")  
  
 消除鋸齒功能，也稱為 平滑處理，也可以套用至曲線。 下圖顯示平滑的橢圓形的放大的檢視。  
  
 ![消除鋸齒曲線](./media/aboutgdip02-art35.gif "AboutGdip02_Art35")  
  
 下圖顯示相同的橢圓形的實際大小，一次沒有反鋸齒功能，另一次使用反鋸齒功能。  
  
 ![反鋸齒功能範例](./media/aboutgdip02-art36.gif "AboutGdip02_Art36")  
  
 若要繪製的直線和曲線，使用反鋸齒功能，建立的執行個體<xref:System.Drawing.Graphics>類別，並設定其<xref:System.Drawing.Graphics.SmoothingMode%2A>屬性設<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>或<xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>。 然後呼叫其中一個繪圖的方法相同<xref:System.Drawing.Graphics>類別。  
  
 [!code-csharp[LinesCurvesAndShapes#81](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#81)]
 [!code-vb[LinesCurvesAndShapes#81](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#81)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Drawing2D.SmoothingMode?displayProperty=nameWithType>
- [線條、曲線和形狀](lines-curves-and-shapes.md)
- [如何：使用文字反鋸齒功能](how-to-use-antialiasing-with-text.md)
