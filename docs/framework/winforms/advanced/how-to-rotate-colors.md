---
title: 如何：旋轉色彩
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], rotating
- examples [Windows Forms], rotating colors
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
ms.openlocfilehash: 8d2717dd7b819e963126072279b361fda02188bc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111331"
---
# <a name="how-to-rotate-colors"></a>如何：旋轉色彩
四維色彩空間中的旋轉很難視覺化。 通過同意固定其中一種顏色元件，我們可以更輕鬆地視覺化旋轉。 假設我們同意將 Alpha 元件固定為 1（完全不透明）。 然後，我們可以用紅色、綠色和藍色軸視覺化三維色彩空間，如下圖所示。  
  
 ![顯示紅色、綠色和藍色軸旋轉的插圖。](./media/how-to-rotate-colors/rotation-red-green-blue-axes.gif)  
  
 顏色可以被視為 3D 空間中的點。 例如，空格中的點 （1， 0， 0） 表示紅色，空格中的點 （0， 1， 0） 表示綠色。  
  
 下圖顯示了在紅綠平面中通過 60 度角旋轉顏色 （1， 0， 0） 的含義。 與紅-綠平面平行的平面上的旋轉可視為藍色軸的旋轉。  
  
 ![顯示藍色軸旋轉的插圖。](./media/how-to-rotate-colors/rotation-about-blue-axis.gif)  
  
 下圖演示如何初始化顏色矩陣以對三個座標軸（紅色、綠色、藍色）執行每個座標軸的旋轉：  
  
 ![初始化顏色矩陣以執行大約三個軸的旋轉。](./media/how-to-rotate-colors/rotation-about-three-axes.gif)  
  
## <a name="example"></a>範例  
 下面的示例採用一個全部為一種顏色（1，0，0.6）的圖像，並應用 60 度旋轉藍色軸。 旋轉角度在與紅綠色平面平行的平面中掃出。  
  
 下圖顯示了左側的原始圖像和右側的顏色旋轉圖像：  
  
 ![顯示原始圖像和顏色旋轉圖像的插圖。](./media/how-to-rotate-colors/original-color-rotated-images.png)  
  
 下圖顯示了以下代碼中執行的顏色旋轉的視覺化效果：
  
 ![顯示顏色旋轉視覺化的插圖。](./media/how-to-rotate-colors/visualization-color-rotation.gif)  
  
 [!code-csharp[System.Drawing.RotateColors#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 前面的示例設計用於 Windows 表單，它需要<xref:System.Windows.Forms.PaintEventArgs>`e`，這是事件處理常式的<xref:System.Windows.Forms.Control.Paint>參數。 替換為`RotationInput.bmp`系統上有效的映射檔案名和路徑。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Windows Form 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)
- [將影像重新著色](recoloring-images.md)
