---
title: 如何：建立路徑漸層
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- path gradients [Windows Forms], creating
- gradients [Windows Forms], creating path
- graphics paths [Windows Forms], creating gradient
ms.assetid: 1948e834-e104-481c-b71d-d8aa9e4d106e
ms.openlocfilehash: cf4dc558c008fb8adfc327a6a894a428e985df03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182638"
---
# <a name="how-to-create-a-path-gradient"></a>如何：建立路徑漸層
該<xref:System.Drawing.Drawing2D.PathGradientBrush>類允許您自訂使用逐漸更改的顏色填充形狀的方式。 例如，可以為路徑的中心指定一種顏色，為路徑的邊界指定另一種顏色。 您還可以為路徑邊界上的多個點指定單獨的顏色。  
  
> [!NOTE]
> 在 GDI+中，路徑是由<xref:System.Drawing.Drawing2D.GraphicsPath>物件維護的線和曲線序列。 有關 GDI+ 路徑的詳細資訊，請參閱[GDI+ 中的圖形路徑](graphics-paths-in-gdi.md)以及[構造和繪圖路徑](constructing-and-drawing-paths.md)。  

本文中的示例是從控制項<xref:System.Windows.Forms.Control.Paint>的事件處理常式調用的方法。  

### <a name="to-fill-an-ellipse-with-a-path-gradient"></a>用路徑漸變填充橢圓  
  
- 下面的示例使用路徑漸層筆刷填充橢圓。 中心顏色設置為藍色，邊界顏色設置為水色。 下圖顯示了填充的橢圓。  
  
     ![漸變路徑填充橢圓。](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse.png)  
  
     預設情況下，路徑漸層筆刷不會擴展到路徑的邊界之外。 如果使用路徑漸層筆刷填充超出路徑邊界的圖形，則不會填充路徑外部的螢幕區域。  
  
     下圖顯示了如果將以下代碼中的<xref:System.Drawing.Graphics.FillEllipse%2A?displayProperty=nameWithType>調用更改為`e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`：  
  
     ![漸變路徑超出路徑的邊界。](./media/how-to-create-a-path-gradient/gradient-path-extended-beyond-boundary.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     前面的代碼示例設計用於 Windows 表單，它要求<xref:System.Windows.Forms.PaintEventArgs>e，這是 的<xref:System.Windows.Forms.PaintEventHandler>參數。  
  
### <a name="to-specify-points-on-the-boundary"></a>指定邊界上的點  
  
- 下面的示例從星形路徑構造路徑漸層筆刷。 代碼設置屬性<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A>，該屬性將星形的質心處的顏色設置為紅色。 然後，代碼設置屬性<xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A>以在`points`陣列中的單個點指定各種顏色`colors`（存儲在陣列中）。 最後的代碼語句使用路徑漸層筆刷填充星形路徑。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
- 下面的示例繪製一個路徑漸變，沒有<xref:System.Drawing.Drawing2D.GraphicsPath>代碼中的物件。 示例中的特定<xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A>建構函式接收點陣列，但不需要<xref:System.Drawing.Drawing2D.GraphicsPath>物件。 此外，請注意，<xref:System.Drawing.Drawing2D.PathGradientBrush>用於填充矩形，而不是路徑。 矩形大於用於定義畫筆的封閉路徑，因此某些矩形不是由畫筆繪製的。 下圖顯示了矩形（虛線）和由路徑漸層筆刷繪製的矩形部分：
  
     ![由路徑漸層筆刷繪製的漸變部分。](./media/how-to-create-a-path-gradient/gradient-painted-path-gradient-brush.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### <a name="to-customize-a-path-gradient"></a>自訂路徑漸變  
  
- 自訂路徑漸層筆刷的一種方法是設置其<xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A>屬性。 焦點比例指定位於主路徑內的內路徑。 中心顏色顯示在該內部路徑的任何地方，而不僅僅是中心點。  
  
     下面的示例基於橢圓路徑創建路徑漸層筆刷。 代碼將邊界顏色設置為藍色，將中心顏色設置為水族，然後使用路徑漸層筆刷填充橢圓路徑。  
  
     接下來，代碼設置路徑漸層筆刷的焦點比例。 x 焦點比例設置為 0.3，y 焦點比例設置為 0.8。 代碼調用<xref:System.Drawing.Graphics.TranslateTransform%2A><xref:System.Drawing.Graphics>物件的方法，以便後續調用以<xref:System.Drawing.Graphics.FillPath%2A>填充位於第一個橢圓右側的橢圓。  
  
     要查看焦點縮放的效果，想像一個與主橢圓共用中心的小橢圓。 小橢圓是水準縮放（大約其中心）的主橢圓，由 0.3 倍和垂直 0.8 倍數垂直縮放。 當您從外部橢圓的邊界移動到內部橢圓的邊界時，顏色會逐漸從藍色變為淺綠色。 當您從內部橢圓的邊界移動到共用中心時，顏色將保持淺色。  
  
     下圖顯示下列程式碼的輸出。 左側的橢圓僅在中心點處是水族。 右邊的橢圓在內路內隨處可見。  
  
 ![焦點尺度的漸變效果](./media/how-to-create-a-path-gradient/focus-scales-aqua-inner-outer-ellipse.png)  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### <a name="to-customize-with-interpolation"></a>使用插值進行自訂  
  
- 自訂路徑漸層筆刷的另一種方法是指定插值顏色陣列和插值位置陣列。  
  
     下面的示例基於三角形創建路徑漸層筆刷。 代碼設置路徑漸變<xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A>畫筆的屬性以指定插值顏色陣列（深綠色、水彩、藍色）和插值位置陣列（0、0.25、1）。 當您從三角形的邊界移動到中心點時，顏色逐漸從深綠色變為淺綠色，然後從淺綠色變為藍色。 從深綠色到淺綠色的變化發生在從深綠色到藍色25%的距離。  
  
     下圖顯示了使用自訂路徑漸層筆刷填充的三角形。  
  
     ![用自訂路徑漸層筆刷填充的三角形。](./media/how-to-create-a-path-gradient/gradient-brush-filled-triangle.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### <a name="to-set-the-center-point"></a>設置中心點  
  
- 預設情況下，路徑漸層筆刷的中心點位於用於構造畫筆的路徑的質心。 您可以通過設置<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A><xref:System.Drawing.Drawing2D.PathGradientBrush>類的屬性來更改中心點的位置。  
  
     下面的示例基於橢圓創建路徑漸層筆刷。 橢圓的中心位於 （70， 35），但路徑漸層筆刷的中心點設置為 （120， 40）。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     下圖顯示了填充橢圓和路徑漸層筆刷的中心點：  
  
     ![具有填充橢圓和中心點的漸變路徑。](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse-center-point.png)  
  
- 您可以將路徑漸層筆刷的中心點設置為用於構造畫筆的路徑外部的位置。 下面的示例替換調用以在前面的代碼中設置<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A>屬性。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     下圖顯示了此更改的輸出：  
  
     ![路徑外部中心點的漸變路徑。](./media/how-to-create-a-path-gradient/gradient-path-center-point-outside.png)  
  
     在前面的圖中，橢圓最右邊的點不是純藍色（儘管它們非常接近）。 漸變中的顏色定位如下填充到達該點 （145， 35），其中顏色為純藍色 （0，0，255）。 但填充永遠不會達到 （145， 35），因為路徑漸層筆刷只在其路徑內繪製。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 前面的示例設計用於 Windows 表單，它們需要<xref:System.Windows.Forms.PaintEventArgs>`e`，這是事件處理常式的<xref:System.Windows.Forms.Control.Paint>參數。  
  
## <a name="see-also"></a>另請參閱

- [使用漸層筆刷填滿形狀](using-a-gradient-brush-to-fill-shapes.md)
