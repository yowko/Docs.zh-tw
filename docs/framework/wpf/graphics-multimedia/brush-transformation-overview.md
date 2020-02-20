---
title: 筆刷轉換概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], transformation properties
- properties [WPF], transformation
- transformation properties of brushes [WPF]
ms.assetid: 8b9bfc09-12fd-4cd5-b445-99949f27bc39
ms.openlocfilehash: 1d3a56014e0975f3616b7f90021b4290ced5daab
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453126"
---
# <a name="brush-transformation-overview"></a>筆刷轉換概觀
筆刷類別提供兩個轉換屬性： <xref:System.Windows.Media.Brush.Transform%2A> 和 <xref:System.Windows.Media.Brush.RelativeTransform%2A>。 上述屬性可讓您旋轉、縮放、扭曲及平移筆刷的內容。 本主題說明這兩種屬性之間的差異並提供使用方式範例。  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Prerequisites  
 若要了解本主題，您應該了解您要轉換的筆刷功能。 如 <xref:System.Windows.Media.LinearGradientBrush> 和 <xref:System.Windows.Media.RadialGradientBrush>，請參閱[使用純色和漸層繪製的色彩總覽](painting-with-solid-colors-and-gradients-overview.md)。 如 <xref:System.Windows.Media.ImageBrush>、<xref:System.Windows.Media.DrawingBrush>或 <xref:System.Windows.Media.VisualBrush>，請參閱[使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)。 您也應該熟悉[轉換概觀](transforms-overview.md)中所述的 2D 轉換。  
  
<a name="transformversusrelativetransform"></a>   
## <a name="differences-between-the-transform-and-relativetransform-properties"></a>Transform 和 RelativeTransform 屬性之間的差異  
 當您將轉換套用至筆刷的 <xref:System.Windows.Media.Brush.Transform%2A> 屬性時，如果您想要轉換其中心的筆刷內容，則需要知道繪製區域的大小。 假設繪製的區域寬度為 200 裝置獨立像素且高度為 150。  如果您使用 <xref:System.Windows.Media.RotateTransform> 旋轉筆刷在其中心的輸出45度，則會提供 <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform.CenterX%2A> 100 和75的 <xref:System.Windows.Media.RotateTransform.CenterY%2A>。  
  
 當您將轉換套用至筆刷的 <xref:System.Windows.Media.Brush.RelativeTransform%2A> 屬性時，會先將該轉換套用至筆刷，然後才會將其輸出對應到繪製的區域。 下列清單說明筆刷內容的處理和轉換順序。  
  
1. 處理筆刷的內容。 就 <xref:System.Windows.Media.GradientBrush>而言，這表示決定漸層區域。 若為 <xref:System.Windows.Media.TileBrush>，<xref:System.Windows.Media.TileBrush.Viewbox%2A> 會對應至 <xref:System.Windows.Media.TileBrush.Viewport%2A>。 這會成為筆刷的輸出。  
  
2. 將筆刷的輸出投影至 1 x 1 轉換矩形。  
  
3. 套用筆刷的 <xref:System.Windows.Media.Brush.RelativeTransform%2A>（如果有的話）。  
  
4. 將轉換後的輸出投影至要繪製的區域。  
  
5. 套用筆刷的 <xref:System.Windows.Media.Transform>（如果有的話）。  
  
 由於 <xref:System.Windows.Media.Brush.RelativeTransform%2A> 會在筆刷的輸出對應至 1 x 1 的矩形時套用，因此，轉換置中和位移值會顯示為相對。 例如，如果您使用 <xref:System.Windows.Media.RotateTransform> 旋轉筆刷在其中心的輸出45度，則會提供 <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform.CenterX%2A> 0.5 和0.5 的 <xref:System.Windows.Media.RotateTransform.CenterY%2A>。  
  
 下圖顯示使用 <xref:System.Windows.Media.Brush.RelativeTransform%2A> 和 <xref:System.Windows.Media.Brush.Transform%2A> 屬性，以45度旋轉的數筆筆刷的輸出。  
  
 ![RelativeTransform 和轉換屬性](./media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm_brushrelativetransform_transform_small")  
  
<a name="relativetransformandtilebrush"></a>   
## <a name="using-relativetransform-with-a-tilebrush"></a>搭配 TileBrush 使用 RelativeTransform  
 因為磚筆刷比其他筆刷複雜，所以將 <xref:System.Windows.Media.Brush.RelativeTransform%2A> 套用至其中一個可能會產生非預期的結果。 例如，使用下列影像。  
  
 ![來源影像](./media/graphicsmm-reltransform-1-original-image.jpg "graphicsmm_reltransform_1_original_image")  
  
 下列範例會使用 <xref:System.Windows.Media.ImageBrush> 來繪製具有上一個影像的矩形區域。 它會將 <xref:System.Windows.Media.RotateTransform> 套用至 <xref:System.Windows.Media.ImageBrush> 物件的 <xref:System.Windows.Media.Brush.RelativeTransform%2A> 屬性，並將其 <xref:System.Windows.Media.TileBrush.Stretch%2A> 屬性設定為 [<xref:System.Windows.Media.Stretch.UniformToFill>]，這應該會在伸展以填滿矩形時，保留影像的外觀比例。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 這個範例會產生下列輸出：  
  
 ![轉換的輸出](./media/graphicsmm-reltransform-6-output.png "graphicsmm_reltransform_6_output")  
  
 請注意，即使筆刷的 <xref:System.Windows.Media.TileBrush.Stretch%2A> 設定為 <xref:System.Windows.Media.Stretch.UniformToFill>，影像還是會扭曲。 這是因為在筆刷的 <xref:System.Windows.Media.TileBrush.Viewbox%2A> 對應到其 <xref:System.Windows.Media.TileBrush.Viewport%2A>之後，會套用相對轉換。 下列清單描述程序的每個步驟︰  
  
1. 使用筆刷的 <xref:System.Windows.Media.TileBrush.Stretch%2A> 設定，將筆刷的內容（<xref:System.Windows.Media.TileBrush.Viewbox%2A>）投影到其基底磚（<xref:System.Windows.Media.TileBrush.Viewport%2A>）。  
  
     ![延展 Viewbox 以符合視口](./media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm_reltransform_2_viewbox_to_viewport")  
  
2. 將基底的並排顯示投影至 1 x 1 轉換矩形。  
  
     ![將視口對應至轉換矩形](./media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm_reltransform_3_output_to_transform")  
  
3. 套用 <xref:System.Windows.Media.RotateTransform>。  
  
     ![套用相對轉換](./media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm_reltransform_4_transform_rotate")  
  
4. 將轉換後基底的並排顯示投影至要繪製的區域。  
  
     ![將轉換後的筆刷投影至輸出區域](./media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm_reltransform_5_transform_to_output")  
  
<a name="rotateexample"></a>   
## <a name="example-rotate-an-imagebrush-45-degrees"></a>範例︰ 旋轉 ImageBrush 45 度  
 下列範例會將 <xref:System.Windows.Media.RotateTransform> 套用至 <xref:System.Windows.Media.ImageBrush>的 <xref:System.Windows.Media.Brush.RelativeTransform%2A> 屬性。 <xref:System.Windows.Media.RotateTransform> 物件的 <xref:System.Windows.Media.RotateTransform.CenterX%2A> 和 <xref:System.Windows.Media.RotateTransform.CenterY%2A> 屬性都設定為0.5，也就是內容中心點的相對座標。 如此一來，會以筆刷內容的中心為中心點旋轉。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 下一個範例也會將 <xref:System.Windows.Media.RotateTransform> 套用至 <xref:System.Windows.Media.ImageBrush>，但會使用 <xref:System.Windows.Media.Brush.Transform%2A> 屬性，而不是 <xref:System.Windows.Media.Brush.RelativeTransform%2A> 屬性。 若要旋轉筆刷的中心，<xref:System.Windows.Media.RotateTransform> 物件的 <xref:System.Windows.Media.RotateTransform.CenterX%2A> 和 <xref:System.Windows.Media.RotateTransform.CenterY%2A> 必須設定為 [絕對座標]。 因為使用筆刷繪製的矩形為 175 x 90 像素，所以其中心點為 (87.5, 45)。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 下圖顯示沒有轉換的筆刷、套用至 <xref:System.Windows.Media.Brush.RelativeTransform%2A> 屬性的轉換，以及套用至 <xref:System.Windows.Media.Brush.Transform%2A> 屬性的轉換。  
  
 ![筆刷 RelativeTransform 和轉換設定](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
 這個範例是某完整範例的一部分。 如需完整的範例，請參閱 [Brush 範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)。 如需筆刷的詳細資訊，請參閱 [WPF 筆刷概觀](wpf-brushes-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Brush.Transform%2A>
- <xref:System.Windows.Media.Brush.RelativeTransform%2A>
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Brush>
- [使用純色和漸層繪製的概觀](painting-with-solid-colors-and-gradients-overview.md)
- [使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)
- [轉換概觀](transforms-overview.md)
