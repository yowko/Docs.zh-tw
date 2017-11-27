---
title: "如何：建立路徑漸層"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- path gradients [Windows Forms], creating
- gradients [Windows Forms], creating path
- graphics paths [Windows Forms], creating gradient
ms.assetid: 1948e834-e104-481c-b71d-d8aa9e4d106e
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6222b22ea0bb38ea95304d43a6dab0deee0d2d05
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-a-path-gradient"></a>如何：建立路徑漸層
<xref:System.Drawing.Drawing2D.PathGradientBrush>類別可讓您自訂您漸層色彩填滿圖形的方式。 比方說，您可以指定一個色彩為路徑的中央和路徑的界限的另一種色彩。 您也可以指定不同的色彩，每個界限的幾個點的路徑。  
  
> [!NOTE]
>  在[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，路徑是一串的直線和曲線所維護<xref:System.Drawing.Drawing2D.GraphicsPath>物件。 如需有關[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]路徑，請參閱[GDI + 中的圖形路徑](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md)和[Constructing 和繪製路徑](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)。  
  
### <a name="to-fill-an-ellipse-with-a-path-gradient"></a>若要使用的路徑漸層填滿橢圓形  
  
-   下列範例會填滿橢圓形路徑漸層筆刷。 中心色彩設定為藍色並界限色彩設定為青色。 下圖顯示實心的橢圓形。  
  
     ![漸層路徑](../../../../docs/framework/winforms/advanced/media/pathgradient1.png "pathgradient1")  
  
     根據預設，路徑漸層筆刷不會延伸超出路徑的界限。 如果您使用路徑漸層筆刷填滿超出路徑的邊界的圖形，在路徑外螢幕區域不會被填入。  
  
     下圖顯示如果您變更，會發生什麼事<xref:System.Drawing.Graphics.FillEllipse%2A>在下列程式碼中呼叫`e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`。  
  
     ![漸層路徑](../../../../docs/framework/winforms/advanced/media/pathgradient2.png "pathgradient2")  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     上述程式碼範例設計用於搭配 Windows Form，且其需要<xref:System.Windows.Forms.PaintEventArgs>e 是參數的<xref:System.Windows.Forms.PaintEventHandler>。  
  
### <a name="to-specify-points-on-the-boundary"></a>若要指定點的界限  
  
-   下列範例會建構路徑漸層筆刷從星形的路徑。 程式碼集<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A>屬性，設定在為紅色星號的距心的色彩。 然後程式碼集<xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A>屬性來指定不同的色彩 (儲存在`colors`陣列) 中的個別點`points`陣列。 最後的程式碼陳述式會填滿星形路徑與路徑漸層筆刷。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
-   下列範例會繪製路徑漸層，而不<xref:System.Drawing.Drawing2D.GraphicsPath>程式碼中的物件。 特定<xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A>接收的點陣列建構函式在範例中，但不需要<xref:System.Drawing.Drawing2D.GraphicsPath>物件。 另請注意，<xref:System.Drawing.Drawing2D.PathGradientBrush>用來填滿的矩形，不是路徑。 矩形會大於已關閉用來定義筆刷，因此部分矩形將不會繪製筆刷的路徑。 下圖顯示的矩形 （虛線） 和部分路徑漸層筆刷繪製的矩形。  
  
     ![漸層停駐](../../../../docs/framework/winforms/advanced/media/gradient4.png "gradient4")  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### <a name="to-customize-a-path-gradient"></a>若要自訂路徑漸層  
  
-   若要自訂路徑漸層筆刷的一種方式為設定其<xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A>屬性。 焦點比例指定主要路徑內的內部路徑。 中心色彩全部都會顯示內部路徑，而不是只在中心點。  
  
     下列範例會建立路徑漸層筆刷根據橢圓形的路徑。 程式碼界限色彩設定為藍色，中心色彩設定為青色，，然後再使用路徑漸層筆刷填滿橢圓形的路徑。  
  
     接下來，此程式碼會設定路徑的漸層筆刷的焦點比例。 X 焦點小數位數設定為 0.3，和 y 焦點小數位數設定為 0.8。 程式碼會呼叫<xref:System.Drawing.Graphics.TranslateTransform%2A>方法<xref:System.Drawing.Graphics>物件以便後續呼叫<xref:System.Drawing.Graphics.FillPath%2A>會填滿橢圓形位於右邊的第一個橢圓形。  
  
     若要查看焦點比例的效果，假設共用同一個中心與主要橢圓形的小型橢圓形。 小 （內部） 橢圓形是主要的省略符號 （關於其中心） 水平調整，因數為 0.3 平和垂直方式，因數為 0.8。 當您移動從外部橢圓形的邊界內部的橢圓形的邊界時，色彩逐漸從變成藍色青色。 當您從內部橢圓形的邊界移到共用的中心，色彩會保持為青色。  
  
     下圖顯示下列程式碼的輸出。 在左側橢圓形是青色的中心點。 在右邊的省略符號是青色 everywhere 內的內部路徑。  
  
 ![漸層停駐](../../../../docs/framework/winforms/advanced/media/focusscales1nogamma.png "focusscales1NoGamma")  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### <a name="to-customize-with-interpolation"></a>若要自訂使用插補  
  
-   若要自訂路徑漸層筆刷的另一種方式是指定插補色彩的陣列和陣列的插補的位置。  
  
     下列範例會建立路徑漸層筆刷根據三角形。 程式碼集<xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A>路徑漸層筆刷深綠色、 青色 （藍） 的插補色彩的陣列和陣列的插補位置 （0，0.25，1） 指定的屬性。 當您移動的三角形界限從中心點，色彩會逐漸從深綠色青色，然後從青色為藍色。 深綠色青色的變更會發生在 25%的距離為藍色深綠色。  
  
     下圖顯示自訂路徑漸層筆刷填滿的三角形。  
  
     ![漸層路徑](../../../../docs/framework/winforms/advanced/media/pathgradient4.png "pathgradient4")  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### <a name="to-set-the-center-point"></a>若要設定的中心點  
  
-   根據預設，路徑漸層筆刷的中心點位於用來建構筆刷的路徑的距心。 您可以藉由設定變更的中心點的位置<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A>屬性<xref:System.Drawing.Drawing2D.PathGradientBrush>類別。  
  
     下列範例會建立路徑漸層筆刷根據橢圓形。 橢圓形的中心位於 70 (35），但路徑漸層筆刷的中心點設定為 120 (40）。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     下圖顯示實心的橢圓形和路徑的漸層筆刷的中心點。  
  
     ![漸層路徑](../../../../docs/framework/winforms/advanced/media/pathgradient5.png "pathgradient5")  
  
-   您可以設定用來建構筆刷的路徑以外的位置路徑的漸層筆刷的中心點。 下列範例會取代設定的呼叫<xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A>上述程式碼中的屬性。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     下圖顯示這項變更的輸出。  
  
     ![漸層路徑](../../../../docs/framework/winforms/advanced/media/pathgradient6.png "pathgradient6")  
  
     在上圖中，最右邊的省略符號的點不是純藍色 （雖然它們是非常接近）。 中所使用漸層的色彩都位於如同填滿到達其中色彩會 （0，0，255） 的純藍色點 （145，35）。 但永遠不會到達填滿 （145，35） 因為路徑的漸層筆刷繪製只在其路徑。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 前面的範例專為搭配 Windows Form 使用，而且會要求<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。  
  
## <a name="see-also"></a>另請參閱  
 [使用漸層筆刷填滿形狀](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)
