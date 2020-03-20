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
ms.openlocfilehash: deac1be2fd19703055b76af8173111b4453f0d6b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186520"
---
# <a name="brush-transformation-overview"></a>筆刷轉換概觀
Brush 類提供兩個轉換屬性<xref:System.Windows.Media.Brush.Transform%2A>：<xref:System.Windows.Media.Brush.RelativeTransform%2A>和 。 上述屬性可讓您旋轉、縮放、扭曲及平移筆刷的內容。 本主題說明這兩種屬性之間的差異並提供使用方式範例。  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>必要條件  
 若要了解本主題，您應該了解您要轉換的筆刷功能。 對於<xref:System.Windows.Media.LinearGradientBrush><xref:System.Windows.Media.RadialGradientBrush>和 ，請參閱[具有純色和漸變的繪畫概述](painting-with-solid-colors-and-gradients-overview.md)。 對於<xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.DrawingBrush>、或<xref:System.Windows.Media.VisualBrush>，請參閱[使用圖像、繪圖和視覺物件進行繪畫](painting-with-images-drawings-and-visuals.md)。 您也應該熟悉[轉換概觀](transforms-overview.md)中所述的 2D 轉換。  
  
<a name="transformversusrelativetransform"></a>
## <a name="differences-between-the-transform-and-relativetransform-properties"></a>Transform 和 RelativeTransform 屬性之間的差異  
 將畫筆<xref:System.Windows.Media.Brush.Transform%2A>的屬性應用於畫筆屬性時，如果要變換畫筆中心上的畫筆內容，則需要知道繪製區域的大小。 假設繪製的區域寬度為 200 裝置獨立像素且高度為 150。  如果使用 的<xref:System.Windows.Media.RotateTransform>將畫筆的輸出圍繞其中心旋轉 45 度，則給出<xref:System.Windows.Media.RotateTransform>100<xref:System.Windows.Media.RotateTransform.CenterX%2A>和 75<xref:System.Windows.Media.RotateTransform.CenterY%2A>的 a。  
  
 將轉換應用於畫筆的屬性<xref:System.Windows.Media.Brush.RelativeTransform%2A>時，該轉換將應用於畫筆，然後再將其輸出映射到繪製區域。 下列清單說明筆刷內容的處理和轉換順序。  
  
1. 處理筆刷的內容。 對於<xref:System.Windows.Media.GradientBrush>，這意味著確定漸變區域。 對於<xref:System.Windows.Media.TileBrush>，<xref:System.Windows.Media.TileBrush.Viewbox%2A>映射到 。 <xref:System.Windows.Media.TileBrush.Viewport%2A> 這會成為筆刷的輸出。  
  
2. 將筆刷的輸出投影至 1 x 1 轉換矩形。  
  
3. 如果畫筆有<xref:System.Windows.Media.Brush.RelativeTransform%2A>，則應用畫筆的 。。"  
  
4. 將轉換後的輸出投影至要繪製的區域。  
  
5. 如果畫筆有<xref:System.Windows.Media.Transform>，則應用畫筆的 。。"  
  
 由於<xref:System.Windows.Media.Brush.RelativeTransform%2A>在畫筆的輸出映射到 1 x 1 矩形時應用，因此變換中心和偏移值看起來是相對的。 例如，如果使用<xref:System.Windows.Media.RotateTransform>將畫筆的輸出圍繞其中心旋轉 45 度，則給出<xref:System.Windows.Media.RotateTransform>0.5 和<xref:System.Windows.Media.RotateTransform.CenterX%2A>0.5<xref:System.Windows.Media.RotateTransform.CenterY%2A>的 a。  
  
 下圖顯示了使用<xref:System.Windows.Media.Brush.RelativeTransform%2A>和<xref:System.Windows.Media.Brush.Transform%2A>屬性旋轉 45 度的多個畫筆的輸出。  
  
 ![RelativeTransform 和 Transform 屬性](./media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm_brushrelativetransform_transform_small")  
  
<a name="relativetransformandtilebrush"></a>
## <a name="using-relativetransform-with-a-tilebrush"></a>搭配 TileBrush 使用 RelativeTransform  
 由於磁貼畫筆比其他畫筆複雜，因此對畫筆應用<xref:System.Windows.Media.Brush.RelativeTransform%2A>可能會產生意外的結果。 例如，使用下列影像。  
  
 ![影像來源](./media/graphicsmm-reltransform-1-original-image.jpg "graphicsmm_reltransform_1_original_image")  
  
 下面的示例使用 使用<xref:System.Windows.Media.ImageBrush>前面的圖像繪製矩形區域。 <xref:System.Windows.Media.RotateTransform>它應用於<xref:System.Windows.Media.ImageBrush>物件的<xref:System.Windows.Media.Brush.RelativeTransform%2A>屬性，並將其<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性設置到<xref:System.Windows.Media.Stretch.UniformToFill>，當圖像拉伸以完全填充矩形時，該屬性應保留圖像的縱橫比。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 這個範例會產生下列輸出：  
  
 ![轉換後的輸出](./media/graphicsmm-reltransform-6-output.png "graphicsmm_reltransform_6_output")  
  
 請注意，即使畫筆<xref:System.Windows.Media.TileBrush.Stretch%2A>設置為<xref:System.Windows.Media.Stretch.UniformToFill>，圖像也會失真。 這是因為在畫筆<xref:System.Windows.Media.TileBrush.Viewbox%2A>映射到其<xref:System.Windows.Media.TileBrush.Viewport%2A>後應用相對轉換。 下列清單描述程序的每個步驟︰  
  
1. 使用畫筆的<xref:System.Windows.Media.TileBrush.Viewbox%2A><xref:System.Windows.Media.TileBrush.Stretch%2A>設置將畫筆的內容 （ ） 投影到<xref:System.Windows.Media.TileBrush.Viewport%2A>其基礎磁貼上。  
  
     ![自動縮放 Viewbox 以符合檢視區](./media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm_reltransform_2_viewbox_to_viewport")  
  
2. 將基底的並排顯示投影至 1 x 1 轉換矩形。  
  
     ![將檢視區對應至轉換矩形](./media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm_reltransform_3_output_to_transform")  
  
3. 應用<xref:System.Windows.Media.RotateTransform>。  
  
     ![套用相對轉換](./media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm_reltransform_4_transform_rotate")  
  
4. 將轉換後基底的並排顯示投影至要繪製的區域。  
  
     ![將轉換後的筆刷投影至輸出區域](./media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm_reltransform_5_transform_to_output")  
  
<a name="rotateexample"></a>
## <a name="example-rotate-an-imagebrush-45-degrees"></a>範例︰ 旋轉 ImageBrush 45 度  
 下面的示例<xref:System.Windows.Media.RotateTransform>將 應用於 的屬性<xref:System.Windows.Media.Brush.RelativeTransform%2A><xref:System.Windows.Media.ImageBrush>。 物件<xref:System.Windows.Media.RotateTransform><xref:System.Windows.Media.RotateTransform.CenterX%2A>和<xref:System.Windows.Media.RotateTransform.CenterY%2A>屬性都設置為 0.5，即內容中心點的相對座標。 如此一來，會以筆刷內容的中心為中心點旋轉。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 下一<xref:System.Windows.Media.RotateTransform>個示例也適用于 ，<xref:System.Windows.Media.ImageBrush>但使用 屬性<xref:System.Windows.Media.Brush.Transform%2A>而不是 屬性。 <xref:System.Windows.Media.Brush.RelativeTransform%2A> 要圍繞其中心旋轉畫筆，<xref:System.Windows.Media.RotateTransform>必須將物件的<xref:System.Windows.Media.RotateTransform.CenterX%2A>和<xref:System.Windows.Media.RotateTransform.CenterY%2A>旋轉設置為絕對座標。 因為使用筆刷繪製的矩形為 175 x 90 像素，所以其中心點為 (87.5, 45)。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 下圖顯示了沒有轉換的畫筆，該畫筆將轉換應用於<xref:System.Windows.Media.Brush.RelativeTransform%2A>屬性，並將轉換應用於<xref:System.Windows.Media.Brush.Transform%2A>該屬性。  
  
 ![筆刷的 RelativeTransform 和 Transform 設定](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
 這個範例是某完整範例的一部分。 有關完整示例，請參閱[畫筆示例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)。 如需筆刷的詳細資訊，請參閱 [WPF 筆刷概觀](wpf-brushes-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Brush.Transform%2A>
- <xref:System.Windows.Media.Brush.RelativeTransform%2A>
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Brush>
- [使用純色和漸層繪製的概觀](painting-with-solid-colors-and-gradients-overview.md)
- [使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)
- [轉換概觀](transforms-overview.md)
