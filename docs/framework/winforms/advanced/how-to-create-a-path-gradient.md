---
title: 作法：建立路徑漸層
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- path gradients [Windows Forms], creating
- gradients [Windows Forms], creating path
- graphics paths [Windows Forms], creating gradient
ms.assetid: 1948e834-e104-481c-b71d-d8aa9e4d106e
ms.openlocfilehash: 8399a56fca87704e10456a4cf8109d7c80d4db45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964408"
---
# <a name="how-to-create-a-path-gradient"></a>作法：建立路徑漸層
<xref:System.Drawing.Drawing2D.PathGradientBrush>類別可讓您自訂以逐漸變更色彩填滿圖形的方式。 例如, 您可以為路徑的中心指定一個色彩, 並為路徑的界限指定另一個色彩。 您也可以針對路徑界限中的每個點指定不同的色彩。  
  
> [!NOTE]
> 在 gdi + 中, 路徑是一系列由<xref:System.Drawing.Drawing2D.GraphicsPath>物件維護的線條和曲線。 如需 GDI + 路徑的詳細資訊, 請參閱[GDI + 中的圖形路徑](graphics-paths-in-gdi.md)和[構造和繪製路徑](constructing-and-drawing-paths.md)。  

本文中的範例是從控制項的<xref:System.Windows.Forms.Control.Paint>事件處理常式呼叫的方法。  

### <a name="to-fill-an-ellipse-with-a-path-gradient"></a>若要以路徑漸層填滿橢圓形  
  
- 下列範例會以路徑漸層筆刷填滿橢圓形。 中間色彩設定為藍色, 且邊界色彩設定為淺綠色。 下圖顯示已填滿的橢圓形。  
  
     ![漸層路徑會填滿橢圓形。](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse.png)  
  
     根據預設, 路徑漸層筆刷不會延伸至路徑的界限之外。 如果您使用路徑漸層筆刷來填滿超出路徑界限的圖形, 則不會填滿路徑外的螢幕區域。  
  
     下圖顯示當您將下列程式碼中<xref:System.Drawing.Graphics.FillEllipse%2A?displayProperty=nameWithType>的呼叫變更為`e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`時, 會發生什麼情況:  
  
     ![漸層路徑延伸超出路徑界限。](./media/how-to-create-a-path-gradient/gradient-path-extended-beyond-boundary.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     上述程式碼範例的設計目的是要與 Windows Forms 搭配使用, 而且<xref:System.Windows.Forms.PaintEventArgs>它需要 e, 這是的<xref:System.Windows.Forms.PaintEventHandler>參數。  
  
### <a name="to-specify-points-on-the-boundary"></a>若要指定界限上的點  
  
- 下列範例會從星形形路徑中, 建立路徑漸層筆刷。 程式碼會設定<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A>屬性, 將星號的距心色彩設定為紅色。 然後, 程式碼會<xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A>設定屬性, 以指定`points`陣列中個別點`colors`的各種色彩 (儲存在陣列中)。 最後的程式碼語句會以路徑漸層筆刷填滿星形形路徑。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
- 下列範例會在程式碼中繪製路徑<xref:System.Drawing.Drawing2D.GraphicsPath>漸層, 而不使用物件。 範例中<xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A>的特定函數會接收點陣列, 但不<xref:System.Drawing.Drawing2D.GraphicsPath>需要物件。 另請注意<xref:System.Drawing.Drawing2D.PathGradientBrush> , 是用來填滿矩形, 而不是路徑。 矩形大於用來定義筆刷的封閉路徑, 因此筆刷不會繪製某些矩形。 下圖顯示以路徑漸層筆刷繪製的矩形 (虛線) 和矩形部分: 
  
     ![由路徑漸層筆刷繪製的漸層部分。](./media/how-to-create-a-path-gradient/gradient-painted-path-gradient-brush.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### <a name="to-customize-a-path-gradient"></a>自訂路徑漸層  
  
- 自訂路徑漸層筆刷的其中一個方法是<xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A>設定其屬性。 焦點縮放會指定位於主要路徑內部的內部路徑。 中央色彩會顯示在內部路徑的任何位置, 而不是僅在中心點。  
  
     下列範例會建立以橢圓形路徑為基礎的路徑漸層筆刷。 程式碼會將邊界色彩設定為藍色, 並將中間色彩設定為淺綠色, 然後使用路徑漸層筆刷來填滿橢圓形路徑。  
  
     接下來, 程式碼會設定路徑漸層筆刷的焦點縮放。 X 焦點尺規設定為 0.3, 而 y 焦點尺規設定為0.8。 程式碼會呼叫<xref:System.Drawing.Graphics.TranslateTransform%2A> <xref:System.Drawing.Graphics>物件的方法, 讓後續的呼叫填滿位於第一個橢圓形右邊的橢圓形。<xref:System.Drawing.Graphics.FillPath%2A>  
  
     若要查看焦點刻度的效果, 請想像一個小橢圓形, 其中心與主要橢圓形共用。 小型 (內部) 橢圓形是以0.3 和垂直因數 (0.8) 水準縮放的主要橢圓形 (大約是其中心)。 當您從外部橢圓形的界限移至內部橢圓形的界限時, 色彩會從藍色逐漸變更為淺綠色。 當您從內部橢圓形的界限移到共用中心時, 色彩會保持為淺綠色。  
  
     下圖顯示下列程式碼的輸出。 左邊的橢圓形只有在中心點才是淺綠色。 右邊的橢圓形在內部路徑內部的任何位置都是綠色。  
  
 ![焦點縮放的漸層效果](./media/how-to-create-a-path-gradient/focus-scales-aqua-inner-outer-ellipse.png)  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### <a name="to-customize-with-interpolation"></a>使用插補自訂  
  
- 自訂路徑漸層筆刷的另一種方式, 是指定插補色彩的陣列和插補位置的陣列。  
  
     下列範例會根據三角形建立路徑漸層筆刷。 程式碼會設定<xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A>路徑漸層筆刷的屬性, 以指定插補色彩的陣列 (深綠色、綠色、藍色) 和插補位置的陣列 (0、0.25、1)。 當您從三角形的邊界移至中心點時, 色彩會從深綠色逐漸變更為淺青, 然後從青色變成藍色。 從深綠色到青色的變更會以 25% 的距離, 從深綠色到藍色。  
  
     下圖顯示填滿自訂路徑漸層筆刷的三角形。  
  
     ![填滿自訂路徑漸層筆刷的三角形。](./media/how-to-create-a-path-gradient/gradient-brush-filled-triangle.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### <a name="to-set-the-center-point"></a>若要設定中心點  
  
- 根據預設, 路徑漸層筆刷的中心點會位於用來建立筆刷之路徑的距心。 您可以藉由設定<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> <xref:System.Drawing.Drawing2D.PathGradientBrush>類別的屬性, 來變更中心點的位置。  
  
     下列範例會根據橢圓形建立路徑漸層筆刷。 橢圓形的中心位於 (70, 35), 但路徑漸層筆刷的中心點設定為 (120, 40)。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     下圖顯示已填滿的橢圓形和路徑漸層筆刷的中心點:  
  
     ![具有實心橢圓形和中心點的漸層路徑。](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse-center-point.png)  
  
- 您可以將路徑漸層筆刷的中心點設定為用來建立筆刷之路徑以外的位置。 下列範例會取代呼叫來設定上述程式<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A>代碼中的屬性。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     下圖顯示此變更的輸出:  
  
     ![中間點位於路徑外的漸層路徑。](./media/how-to-create-a-path-gradient/gradient-path-center-point-outside.png)  
  
     在上圖中, 橢圓形最右邊的點不是純藍色 (雖然非常接近)。 漸層中的色彩會位於填滿的點 (145, 35), 其中的色彩會是純藍色 (0, 0, 255)。 但填滿永遠不會到達 (145, 35), 因為路徑漸層筆刷只會在其路徑內繪製。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 先前的範例是針對與 Windows Forms 搭配使用所設計, 而且<xref:System.Windows.Forms.PaintEventArgs>它們需要`e`, 這<xref:System.Windows.Forms.Control.Paint>是事件處理常式的參數。  
  
## <a name="see-also"></a>另請參閱

- [使用漸層筆刷填滿形狀](using-a-gradient-brush-to-fill-shapes.md)
