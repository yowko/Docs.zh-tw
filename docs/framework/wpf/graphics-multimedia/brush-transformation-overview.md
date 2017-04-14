---
title: "筆刷轉換概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "筆刷, 轉換屬性"
  - "屬性, 轉換"
  - "轉換筆刷屬性"
ms.assetid: 8b9bfc09-12fd-4cd5-b445-99949f27bc39
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 筆刷轉換概觀
Brush 類別提供兩種轉換屬性：<xref:System.Windows.Media.Brush.Transform%2A> 和 <xref:System.Windows.Media.Brush.RelativeTransform%2A>。  這些屬性可讓您旋轉、縮放、扭曲和轉譯筆刷的內容。  本主題描述這兩個屬性的差異，並提供它們使用方式的範例。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="prerequisites"></a>   
## 必要條件  
 若要了解本主題，則應該先了解所轉換的筆刷功能。  如果是 <xref:System.Windows.Media.LinearGradientBrush> 和 <xref:System.Windows.Media.RadialGradientBrush>，請參閱[使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)。  如果是 <xref:System.Windows.Media.ImageBrush>、<xref:System.Windows.Media.DrawingBrush> 或 <xref:System.Windows.Media.VisualBrush>，請參閱[使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)。  您也應該熟悉[轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)中所述的 2D 轉換。  
  
<a name="transformversusrelativetransform"></a>   
## Transform 與 RelativeTransform 屬性的差異  
 當您將轉換套用至筆刷的 <xref:System.Windows.Media.Brush.Transform%2A> 屬性時，如果想要轉換所繪製中心的筆刷內容，則需要知道所繪製區域的大小。  假設所繪製區域的寬度為 200 個[與裝置無關的像素](GTMT)，而高度為 150。  如果使用 <xref:System.Windows.Media.RotateTransform> 在筆刷的中心將筆刷輸出旋轉 45 度，則會看到 <xref:System.Windows.Media.RotateTransform> 的 <xref:System.Windows.Media.RotateTransform.CenterX%2A> 為 100，而 <xref:System.Windows.Media.RotateTransform.CenterY%2A> 為 75。  
  
 當您將轉換套用至筆刷的 <xref:System.Windows.Media.Brush.RelativeTransform%2A> 屬性時，在筆刷輸出對應至所繪製區域之前，該轉換會先套用至筆刷。  下列清單說明筆刷內容的處理和轉換順序。  
  
1.  處理筆刷內容。  如果是 <xref:System.Windows.Media.GradientBrush>，這表示判斷漸層區域。  如果是 <xref:System.Windows.Media.TileBrush>，則 <xref:System.Windows.Media.TileBrush.Viewbox%2A> 會對應至 <xref:System.Windows.Media.TileBrush.Viewport%2A>。  這會變成筆刷的輸出。  
  
2.  將筆刷輸出投影至 1 x 1 的轉換矩形。  
  
3.  套用筆刷的 <xref:System.Windows.Media.Brush.RelativeTransform%2A> \(如果有的話\)。  
  
4.  將轉換的輸出投影至要繪製的區域。  
  
5.  套用筆刷的 <xref:System.Windows.Media.Transform> \(如果有的話\)。  
  
 因為是在將筆刷輸出對應至 1 x 1 矩形時套用 <xref:System.Windows.Media.Brush.RelativeTransform%2A>，所以轉換中心和位移 \(Offset\) 值會是相對的。  例如，如果使用 <xref:System.Windows.Media.RotateTransform> 在筆刷的中心將筆刷輸出旋轉 45 度，則會看到 <xref:System.Windows.Media.RotateTransform> 的 <xref:System.Windows.Media.RotateTransform.CenterX%2A> 為 0.5，而 <xref:System.Windows.Media.RotateTransform.CenterY%2A> 為 0.5。  
  
 下圖顯示數個使用 <xref:System.Windows.Media.Brush.RelativeTransform%2A> 和 <xref:System.Windows.Media.Brush.Transform%2A> 屬性旋轉 45 度之筆刷的輸出。  
  
 ![RelativeTransform 和 Transform 屬性](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm\_brushrelativetransform\_transform\_small")  
  
<a name="relativetransformandtilebrush"></a>   
## 搭配使用 RelativeTransform 與 TileBrush  
 因為並排顯示筆刷比其他筆刷還要複雜，所以將 <xref:System.Windows.Media.Brush.RelativeTransform%2A> 套用至並排顯示筆刷可能會產生未預期的結果。  以下列影像為例。  
  
 ![影像來源](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-1-original-image.png "graphicsmm\_reltransform\_1\_original\_image")  
  
 下列範例使用 <xref:System.Windows.Media.ImageBrush> 來繪製內含先前影像的矩形區域。  它會將 <xref:System.Windows.Media.RotateTransform> 套用至 <xref:System.Windows.Media.ImageBrush> 物件的 <xref:System.Windows.Media.Brush.RelativeTransform%2A> 屬性，並將它的 <xref:System.Windows.Media.TileBrush.Stretch%2A> 屬性設定為 <xref:System.Windows.Media.Stretch>，而在將影像自動縮放為完全填滿矩形時，應該保留影像的外觀比例 \(Aspect Ratio\)。  
  
 [!code-xml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 這個範例會產生下列輸出：  
  
 ![轉換後的輸出](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-6-output.png "graphicsmm\_reltransform\_6\_output")  
  
 請注意，即使筆刷的 <xref:System.Windows.Media.TileBrush.Stretch%2A> 設定為 <xref:System.Windows.Media.Stretch>，影像還是會失真。  這是因為將筆刷的 <xref:System.Windows.Media.TileBrush.Viewbox%2A> 對應至它的 <xref:System.Windows.Media.TileBrush.Viewport%2A> 之後，會套用相對轉換。  下列清單說明程序的每個步驟：  
  
1.  使用筆刷的 <xref:System.Windows.Media.TileBrush.Stretch%2A> 設定，將筆刷內容 \(<xref:System.Windows.Media.TileBrush.Viewbox%2A>\) 投影至它的基底並排顯示 \(<xref:System.Windows.Media.TileBrush.Viewport%2A>\)。  
  
     ![自動縮放 Viewbox 以符合檢視區](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm\_reltransform\_2\_viewbox\_to\_viewport")  
  
2.  將基底並排顯示投影至 1 x 1 的轉換矩形。  
  
     ![將檢視區對應至轉換矩形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm\_reltransform\_3\_output\_to\_transform")  
  
3.  套用 <xref:System.Windows.Media.RotateTransform>。  
  
     ![套用相對轉換](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm\_reltransform\_4\_transform\_rotate")  
  
4.  將轉換的基底並排顯示投影至要繪製的區域。  
  
     ![將轉換後的筆刷投影至輸出區域](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm\_reltransform\_5\_transform\_to\_output")  
  
<a name="rotateexample"></a>   
## 範例：將 ImageBrush 旋轉 45 度  
 下列範例會將 <xref:System.Windows.Media.RotateTransform> 套用至 <xref:System.Windows.Media.ImageBrush> 的 <xref:System.Windows.Media.Brush.RelativeTransform%2A> 屬性。  <xref:System.Windows.Media.RotateTransform> 物件的 <xref:System.Windows.Media.RotateTransform.CenterX%2A> 和 <xref:System.Windows.Media.RotateTransform.CenterY%2A> 屬性都設定為 0.5，這是內容中心點的相對座標。  因此，筆刷的內容會以其中心進行旋轉。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 下一個範例也會將 <xref:System.Windows.Media.RotateTransform> 套用至 <xref:System.Windows.Media.ImageBrush>，但是使用 <xref:System.Windows.Media.Brush.Transform%2A> 屬性，而不是 <xref:System.Windows.Media.Brush.RelativeTransform%2A> 屬性。  若要以中心旋轉筆刷，則 <xref:System.Windows.Media.RotateTransform> 物件的 <xref:System.Windows.Media.RotateTransform.CenterX%2A> 和 <xref:System.Windows.Media.RotateTransform.CenterY%2A> 必須設定為絕對座標。  因為使用筆刷繪製的矩形是 175 x 90 個像素，所以它的中心點是 \(87.5, 45\)。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xml[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 下圖顯示不含轉換的筆刷、將轉換套用至 <xref:System.Windows.Media.Brush.RelativeTransform%2A> 屬性的筆刷，以及將轉換套用至 <xref:System.Windows.Media.Brush.Transform%2A> 屬性的筆刷。  
  
 ![筆刷的 RelativeTransform 和 Transform 設定](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk\_graphicsmm\_transformandrelativetransform")  
  
 這個範例是完整範例的一部分。  如需完整範例，請參閱[筆刷範例](http://go.microsoft.com/fwlink/?LinkID=159973) \(英文\)。  如需筆刷的詳細資訊，請參閱 [WPF 筆刷概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md)。  
  
## 請參閱  
 <xref:System.Windows.Media.Brush.Transform%2A>   
 <xref:System.Windows.Media.Brush.RelativeTransform%2A>   
 <xref:System.Windows.Media.Transform>   
 <xref:System.Windows.Media.Brush>   
 [使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)   
 [使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)   
 [轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)