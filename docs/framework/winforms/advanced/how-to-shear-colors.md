---
title: 如何：切變色彩
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
ms.openlocfilehash: 825e5a90ebb0d9df3b894ce7bd353e917b676939
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142390"
---
# <a name="how-to-shear-colors"></a>如何：切變色彩
剪切會增加或減少顏色分量，以與另一種顏色分量成正比。 例如，考慮紅色分量增加藍色分量值一半的轉換。 在這樣的轉換下，顏色（0.2，0.5，1）將成為（0.7，0.5，1）。 新的紅色分量為 0.2 = （1/2）（1） = 0.7。  
  
## <a name="example"></a>範例  
 下面的示例從檔 ColorBars4.bmp 構造物件<xref:System.Drawing.Image>。 然後，代碼將前一段中描述的剪切變換應用於圖像中的每個圖元。  
  
 下圖顯示了左側的原始圖像和右側的謝線圖像：
  
 ![兩個正方形，帶彩色條紋並排顯示原始圖像和謝線圖像。](./media/how-to-shear-colors/original-image-sheared-image.png)  
  
 下表列出了剪切變換前後四個條形的顏色向量。  
  
|原始|剪切|  
|--------------|-------------|  
|(0, 0, 1, 1)|(0.5, 0, 1, 1)|  
|(0.5, 1, 0.5, 1)|(0.75, 1, 0.5, 1)|  
|(1, 1, 0, 1)|(1, 1, 0, 1)|  
|(0.4, 0.4, 0.4, 1)|(0.6, 0.4, 0.4, 1)|  
  
 [!code-csharp[System.Drawing.Misc3#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 前面的示例設計用於 Windows 表單，它需要<xref:System.Windows.Forms.PaintEventArgs>`e`，這是事件處理常式的<xref:System.Windows.Forms.Control.Paint>參數。 替換為`ColorBars.bmp`系統上有效的圖像名稱和路徑。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Windows Form 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)
- [將影像重新著色](recoloring-images.md)
