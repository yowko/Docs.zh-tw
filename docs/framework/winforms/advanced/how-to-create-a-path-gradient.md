---
title: HOW TO：建立路徑漸層
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- path gradients [Windows Forms], creating
- gradients [Windows Forms], creating path
- graphics paths [Windows Forms], creating gradient
ms.assetid: 1948e834-e104-481c-b71d-d8aa9e4d106e
ms.openlocfilehash: 31a8c68f382f81da2acac363bba6c8822e535770
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186091"
---
# <a name="how-to-create-a-path-gradient"></a>HOW TO：建立路徑漸層
<xref:System.Drawing.Drawing2D.PathGradientBrush>類別可讓您自訂您逐漸變更色彩填滿圖形的方式。 例如，您可以指定路徑的中心的一種色彩和路徑的界限的另一種色彩。 您也可以指定不同的色彩，每個界限的數個點的路徑。  
  
> [!NOTE]
>  在  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，路徑是一系列的線條和曲線維護<xref:System.Drawing.Drawing2D.GraphicsPath>物件。 如需詳細資訊[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]路徑，請參閱[GDI + 中的圖形路徑](graphics-paths-in-gdi.md)並[Constructing 和繪製路徑](constructing-and-drawing-paths.md)。  
  
### <a name="to-fill-an-ellipse-with-a-path-gradient"></a>若要使用的路徑漸層填滿橢圓形  
  
-   下列範例會填滿橢圓形使用路徑漸層筆刷。 之中心色彩設定為藍色，邊界色彩設定為青色。 下圖顯示實心的橢圓形。  
  
     ![漸層停駐的路徑會填滿橢圓形。](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse.png)  
  
     根據預設，路徑漸層筆刷不會延伸超出路徑的界限。 如果您使用路徑漸層筆刷填滿圖形超出路徑的界限時，在路徑外螢幕區域不會被填入。  
  
     下圖顯示如果您變更，會發生什麼事<xref:System.Drawing.Graphics.FillEllipse%2A>在下列程式碼中呼叫`e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`:  
  
     ![擴充到界限路徑的漸層停駐的路徑。](./media/how-to-create-a-path-gradient/gradient-path-extended-beyond-boundary.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     上述程式碼範例專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs>e，也就是參數的<xref:System.Windows.Forms.PaintEventHandler>。  
  
### <a name="to-specify-points-on-the-boundary"></a>若要指定點的界限  
  
-   下列範例會建構路徑漸層筆刷從星形的路徑。 程式碼集<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A>屬性，設定在為紅色星號的距心的色彩。 然後程式碼集<xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A>屬性來指定各種色彩 (儲存在`colors`陣列) 在個別的點`points`陣列。 最後的程式碼陳述式會填滿星形路徑與路徑漸層筆刷。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
-   下列範例會繪製路徑漸層，而不需要<xref:System.Drawing.Drawing2D.GraphicsPath>程式碼中的物件。 特定<xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A>建構函式，在範例中會收到一個點的陣列，但不需要<xref:System.Drawing.Drawing2D.GraphicsPath>物件。 另請注意，<xref:System.Drawing.Drawing2D.PathGradientBrush>用來填滿矩形，而不是路徑。 矩形大於封閉的路徑，用來定義筆刷，因此部分矩形將不會繪製筆刷。 下圖顯示矩形 （虛線） 和路徑的漸層筆刷繪製之矩形的部分： 
  
     ![路徑漸層筆刷繪製漸層的部分。](./media/how-to-create-a-path-gradient/gradient-painted-path-gradient-brush.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### <a name="to-customize-a-path-gradient"></a>若要自訂路徑漸層  
  
-   自訂路徑漸層筆刷的一種方法是設定其<xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A>屬性。 焦點標尺指定內部路徑位於內的主要路徑。 內部路徑中，而不是只在 center 點時，會到處都顯示在中心色彩。  
  
     下列範例會建立路徑的漸層筆刷，根據橢圓形的路徑。 程式碼界限色彩設定為藍色，中心色彩設定為青色、，然後再使用路徑漸層筆刷填滿橢圓形的路徑。  
  
     接下來，程式碼會設定路徑漸層筆刷的焦點比例。 X 焦點小數位數設定為 0.3，而 y 焦點比例設為 0.8。 程式碼會呼叫<xref:System.Drawing.Graphics.TranslateTransform%2A>方法<xref:System.Drawing.Graphics>物件，讓後續呼叫<xref:System.Drawing.Graphics.FillPath%2A>會填滿橢圓形位在右邊的第一個橢圓形。  
  
     若要查看焦點標尺的效果，想像一下與主要的橢圓形共用其中心點小橢圓形。 小 （內部） 的橢圓形是主要的省略符號 （繞著中心中） 水平調整，以 0.3 的因數和垂直 0.8 倍。 當您移動從外部的橢圓形的界限內部的橢圓形的界限時，色彩會逐漸從藍色為青色。 當您從內部的橢圓形的界限移到共用的中心，色彩會保持為青色。  
  
     下圖顯示下列程式碼的輸出。 在左側的省略符號是 aqua 只在 center 點。 在右邊的省略符號是 aqua everywhere 內的內部路徑。  
  
 ![漸層效果的焦點標尺](./media/how-to-create-a-path-gradient/focus-scales-aqua-inner-outer-ellipse.png)  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### <a name="to-customize-with-interpolation"></a>若要自訂內插補點  
  
-   若要自訂路徑漸層筆刷的另一種方式是指定插補色彩的陣列和陣列的內插補點位置。  
  
     下列範例會建立路徑漸層筆刷的三角形為基礎。 程式碼集<xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A>路徑漸層筆刷指定深綠色、 青色 （藍） 的插補色彩的陣列和陣列的內插補點位置 （0，0.25，1） 的屬性。 當您移動三角形的界限從中心點時，色彩會逐漸從深綠色為青綠色，然後從青色藍色。 深綠色 aqua 的變更會在 25%的深綠色和藍色之間的距離。  
  
     下圖顯示填入 自訂路徑漸層筆刷的三角形。  
  
     ![自訂路徑漸層筆刷填滿的三角形。](./media/how-to-create-a-path-gradient/gradient-brush-filled-triangle.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### <a name="to-set-the-center-point"></a>若要設定的中心點  
  
-   根據預設，路徑漸層筆刷的中心點位於用來建構筆刷的路徑的距心。 您可以藉由設定變更的中心點的位置<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A>屬性<xref:System.Drawing.Drawing2D.PathGradientBrush>類別。  
  
     下列範例會建立路徑的漸層筆刷，根據一個橢圓形。 橢圓形的中心是 70 (35），但會設定路徑漸層筆刷的中心點為 （120，40）。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     下圖顯示實心的橢圓形和路徑的漸層筆刷的中心點：  
  
     ![漸層填滿橢圓形和中心點的路徑。](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse-center-point.png)  
  
-   您可以設定路徑漸層筆刷的中心點，用來建構筆刷在路徑外的位置。 下列範例會將呼叫以設定<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A>前面的程式碼的屬性。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     下圖顯示這項變更的輸出：  
  
     ![漸層停駐在路徑外的中心點的路徑。](./media/how-to-create-a-path-gradient/gradient-path-center-point-outside.png)  
  
     在上圖中，最右邊的省略符號的點不是單純的藍色 （不過非常接近）。 在漸層色彩位於如同填滿達到 （145，35） 點，色彩會是純藍色 （0，0，255）。 但永遠不會達到填滿 （145，35） 因為路徑漸層筆刷繪製只在其路徑。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例專為搭配 Windows Form 使用，而且它們需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。  
  
## <a name="see-also"></a>另請參閱

- [使用漸層筆刷填滿形狀](using-a-gradient-brush-to-fill-shapes.md)
