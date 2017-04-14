---
title: "如何：建立路徑漸層 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "漸層, 建立路徑"
  - "圖形路徑, 建立漸層"
  - "路徑漸層, 建立"
ms.assetid: 1948e834-e104-481c-b71d-d8aa9e4d106e
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 如何：建立路徑漸層
<xref:System.Drawing.Drawing2D.PathGradientBrush> 類別可讓您自訂使用漸層色彩填滿形狀的方式。  例如，您可以為路徑的中央指定一種色彩，為路徑的界限指定另外一種色彩。  也可以在路徑的界限上每幾個點就指定不同的色彩。  
  
> [!NOTE]
>  在 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 中，路徑是由 <xref:System.Drawing.Drawing2D.GraphicsPath> 物件維護的線條和曲線序列。  如需 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 路徑的詳細資訊，請參閱[GDI\+ 中的圖形路徑](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md)和[建構和繪製路徑](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)。  
  
### 若要使用路徑漸層填滿橢圓形  
  
-   下列範例會使用路徑漸層筆刷來填滿橢圓形。  中心色彩設定為藍色，界限色彩設定為青色。  下圖顯示的是已填滿的橢圓形。  
  
     ![漸層路徑](../../../../docs/framework/winforms/advanced/media/pathgradient1.png "pathgradient1")  
  
     根據預設，路徑漸層筆刷不會延伸到路徑界限之外。  如果您使用路徑漸層筆刷來填入延伸到路徑界限外的圖形，路徑外的螢幕區域將不會被填入。  
  
     下列圖例顯示將下列程式碼中的 <xref:System.Drawing.Graphics.FillEllipse%2A> 呼叫變更為 `e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)` 時所產生的影響。  
  
     ![漸層路徑](../../../../docs/framework/winforms/advanced/media/pathgradient2.png "pathgradient2")  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     上述程式碼範例是專為與 Windows Form 搭配使用而設計的，而且需要 <xref:System.Windows.Forms.PaintEventArgs> \(即 <xref:System.Windows.Forms.PaintEventHandler> 的參數\)。  
  
### 若要指定界限上的點  
  
-   下列範例會從星形路徑建構出路徑漸層筆刷。  程式碼會設定 <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A> 屬性，這個屬性會將星形中心點的色彩設定為紅色。  然後程式碼會在 `points` 陣列中，於個別點上設定 <xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A> 屬性以指定不同的色彩 \(儲存在 `colors` 陣列中\)。  程式碼中的最後一個陳述式會使用路徑漸層筆刷來填滿星形路徑。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
-   下列範例將繪製路徑漸層，但程式碼中沒有 <xref:System.Drawing.Drawing2D.GraphicsPath> 物件。  範例中特定的 <xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A> 建構函式會接收點陣列，但是不需要 <xref:System.Drawing.Drawing2D.GraphicsPath> 物件。  此外，請注意 <xref:System.Drawing.Drawing2D.PathGradientBrush> 是用來填滿矩形，而非路徑。  矩形比用來定義筆刷的封閉路徑大，因此有部分矩形不會用筆刷來繪製。  下圖顯示的是矩形 \(虛線\) 和使用路徑漸層筆刷繪製的矩形部分。  
  
     ![漸層](../../../../docs/framework/winforms/advanced/media/gradient4.png "gradient4")  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### 若要自訂路徑漸層  
  
-   自訂路徑漸層筆刷的其中一個方式是設定它的 <xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A> 屬性。  焦點比例 \(Focus Scale\) 會指定位於主要路徑內的內部路徑。  這個內部路徑全部都會顯示為中心色彩，而不只是中心點。  
  
     下列範例會根據橢圓形路徑來建立路徑漸層筆刷。  程式碼會將界限色彩設定為藍色，將中心色彩設定為青色，然後使用路徑漸層筆刷來填滿橢圓形路徑。  
  
     接下來，程式碼會設定路徑漸層筆刷的焦點比例。  x 焦點比例會設定為 0.3，y 焦點比例設定為 0.8。  程式碼會呼叫 <xref:System.Drawing.Graphics> 物件的 <xref:System.Drawing.Graphics.TranslateTransform%2A> 方法，使後續的 <xref:System.Drawing.Graphics.FillPath%2A> 呼叫會填滿位於第一個橢圓形右邊的橢圓形。  
  
     若要查看焦點比例的效果，假設有一個小的橢圓形與主要橢圓形共用同一個中心。  小的 \(內部\) 橢圓形是以水平縮放因數 0.3 和垂直縮放因數 0.8 縮放主要橢圓形 \(從中心\)。  當您從外部橢圓形的界限移動到內部橢圓形的界限時，色彩會從藍色逐漸變成青色。  當您從內部橢圓形的界限移動到共用中心時，色彩會保持為青色。  
  
     下圖顯示下列程式碼的輸出。  左邊的橢圓形只有中心點是青色。  右邊的橢圓形則是在內部路徑中全部是青色。  
  
 ![漸層](../../../../docs/framework/winforms/advanced/media/focusscales1nogamma.png "focusscales1NoGamma")  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### 若要使用插補來自訂  
  
-   自訂路徑漸層筆刷的另一個方式是指定內插色彩陣列和內插位置陣列。  
  
     下列範例會根據三角形來建立路徑漸層筆刷。  程式碼會設定路徑漸層筆刷的 <xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A> 屬性，以指定插補色彩陣列 \(深綠色, 青色, 藍色\) 和插補位置陣列 \(0, 0.25, 1\)。  當您從三角形的界限移動到中心點時，色彩會從深綠色逐漸變成青色，然後再從青色變成藍色。  從深綠色變成青色是發生在深綠色到藍色之間的 25% 位置。  
  
     下圖顯示的是使用自訂路徑漸層筆刷填滿的三角形。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### 若要設定中心點  
  
-   依照預設，路徑漸層筆刷的中心點位於用來建構筆刷的路徑中心點。  藉由設定 <xref:System.Drawing.Drawing2D.PathGradientBrush> 類別的 <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> 屬性，變更中心點的位置。  
  
     下列範例會根據橢圓形來建立路徑漸層筆刷。  橢圓形的中心位於 \(70, 35\)，但是路徑漸層筆刷的中心點卻設定為 \(120, 40\)。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     下圖顯示的是填滿的橢圓形和路徑漸層筆刷的中心點。  
  
     ![漸層路徑](../../../../docs/framework/winforms/advanced/media/pathgradient5.png "pathgradient5")  
  
-   您可以將路徑漸層筆刷的中心點設定為用來建構筆刷的路徑之外的位置。  下列範例可取代上述程式碼中用來設定 <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> 屬性的呼叫。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     下圖顯示的是包含這項變更的輸出。  
  
     ![漸層路徑](../../../../docs/framework/winforms/advanced/media/pathgradient6.png "pathgradient6")  
  
     在上圖中，橢圓形最右邊的點不是純藍色 \(但是非常接近\)。  漸層中色彩的位置和 \(145, 35\) 這點的填色一樣，色彩為純藍色 \(0, 0, 255\)。  但是，因為路徑漸層筆刷只會繪製路徑的內部，因此填色絕不會到達 \(145, 35\)。  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它們需要 <xref:System.Windows.Forms.PaintEventArgs> `e` \(即 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數\)。  
  
## 請參閱  
 [使用漸層筆刷填滿形狀](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)