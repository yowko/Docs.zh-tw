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
ms.openlocfilehash: 0b55d2000b8a70bc42373cb976a84ff54ebc4245
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169568"
---
# <a name="brush-transformation-overview"></a>筆刷轉換概觀
Brush 類別提供兩個轉換屬性：<xref:System.Windows.Media.Brush.Transform%2A>和<xref:System.Windows.Media.Brush.RelativeTransform%2A>。 上述屬性可讓您旋轉、縮放、扭曲及平移筆刷的內容。 本主題說明這兩種屬性之間的差異並提供使用方式範例。  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 若要了解本主題，您應該了解您要轉換的筆刷功能。 針對<xref:System.Windows.Media.LinearGradientBrush>並<xref:System.Windows.Media.RadialGradientBrush>，請參閱[使用純色和漸層概觀繪製](painting-with-solid-colors-and-gradients-overview.md)。 針對<xref:System.Windows.Media.ImageBrush>， <xref:System.Windows.Media.DrawingBrush>，或<xref:System.Windows.Media.VisualBrush>，請參閱[使用影像、 繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)。 您也應該熟悉[轉換概觀](transforms-overview.md)中所述的 2D 轉換。  
  
<a name="transformversusrelativetransform"></a>   
## <a name="differences-between-the-transform-and-relativetransform-properties"></a>Transform 和 RelativeTransform 屬性之間的差異  
 當您將轉換套用至筆刷的<xref:System.Windows.Media.Brush.Transform%2A>屬性，您必須知道繪製區域的大小，如果您想要轉換的筆刷內容，繞著中心。 假設繪製的區域寬度為 200 裝置獨立像素且高度為 150。  如果您使用<xref:System.Windows.Media.RotateTransform>旋轉筆刷的輸出其中心點的 45 度，並會提供<xref:System.Windows.Media.RotateTransform><xref:System.Windows.Media.RotateTransform.CenterX%2A>為 100 和<xref:System.Windows.Media.RotateTransform.CenterY%2A>的 75。  
  
 當您將轉換套用至筆刷的<xref:System.Windows.Media.Brush.RelativeTransform%2A>屬性，其輸出會對應到繪製區域之前，該轉換會套用到筆刷。 下列清單說明筆刷內容的處理和轉換順序。  
  
1.  處理筆刷的內容。 針對<xref:System.Windows.Media.GradientBrush>，這表示決定漸層停駐區域。 針對<xref:System.Windows.Media.TileBrush>，則<xref:System.Windows.Media.TileBrush.Viewbox%2A>對應至<xref:System.Windows.Media.TileBrush.Viewport%2A>。 這會成為筆刷的輸出。  
  
2.  將筆刷的輸出投影至 1 x 1 轉換矩形。  
  
3.  套用筆刷的<xref:System.Windows.Media.Brush.RelativeTransform%2A>，如果有的話。  
  
4.  將轉換後的輸出投影至要繪製的區域。  
  
5.  套用筆刷的<xref:System.Windows.Media.Transform>，如果有的話。  
  
 因為<xref:System.Windows.Media.Brush.RelativeTransform%2A>套用時將筆刷的輸出會對應到 1x1 矩形，轉換中心點和位移的值似乎有相對關係。 比方說，如果您使用<xref:System.Windows.Media.RotateTransform>旋轉筆刷的輸出其中心點的 45 度，並會提供<xref:System.Windows.Media.RotateTransform><xref:System.Windows.Media.RotateTransform.CenterX%2A>為 0.5 和<xref:System.Windows.Media.RotateTransform.CenterY%2A>為 0.5。  
  
 下圖顯示具有已旋轉 45 度使用的數個筆刷的輸出<xref:System.Windows.Media.Brush.RelativeTransform%2A>和<xref:System.Windows.Media.Brush.Transform%2A>屬性。  
  
 ![RelativeTransform 和 Transform 屬性](./media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm_brushrelativetransform_transform_small")  
  
<a name="relativetransformandtilebrush"></a>   
## <a name="using-relativetransform-with-a-tilebrush"></a>搭配 TileBrush 使用 RelativeTransform  
 拼貼筆刷會比其他筆刷更為複雜，因為套用<xref:System.Windows.Media.Brush.RelativeTransform%2A>其中一個可能會產生非預期的結果。 例如，使用下列影像。  
  
 ![來源映像](./media/graphicsmm-reltransform-1-original-image.jpg "graphicsmm_reltransform_1_original_image")  
  
 下列範例會使用<xref:System.Windows.Media.ImageBrush>來繪製的矩形區域，以前面的影像。 它會套用<xref:System.Windows.Media.RotateTransform>要<xref:System.Windows.Media.ImageBrush>物件的<xref:System.Windows.Media.Brush.RelativeTransform%2A>屬性，並設定其<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性設<xref:System.Windows.Media.Stretch.UniformToFill>，自動縮放以完全填滿矩形時，它應該保留影像的外觀比例。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 這個範例會產生下列輸出：  
  
 ![轉換後的輸出](./media/graphicsmm-reltransform-6-output.png "graphicsmm_reltransform_6_output")  
  
 請注意，影像會扭曲，即使筆刷<xref:System.Windows.Media.TileBrush.Stretch%2A>已設為<xref:System.Windows.Media.Stretch.UniformToFill>。 這是因為套用相對轉換後的筆刷<xref:System.Windows.Media.TileBrush.Viewbox%2A>對應至其<xref:System.Windows.Media.TileBrush.Viewport%2A>。 下列清單描述程序的每個步驟︰  
  
1.  專案 筆刷的內容 (<xref:System.Windows.Media.TileBrush.Viewbox%2A>) 到其基底的並排顯示 (<xref:System.Windows.Media.TileBrush.Viewport%2A>) 使用筆刷的<xref:System.Windows.Media.TileBrush.Stretch%2A>設定。  
  
     ![自動縮放 Viewbox 以符合檢視區](./media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm_reltransform_2_viewbox_to_viewport")  
  
2.  將基底的並排顯示投影至 1 x 1 轉換矩形。  
  
     ![將檢視區對應至轉換矩形](./media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm_reltransform_3_output_to_transform")  
  
3.  套用<xref:System.Windows.Media.RotateTransform>。  
  
     ![套用相對轉換](./media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm_reltransform_4_transform_rotate")  
  
4.  將轉換後基底的並排顯示投影至要繪製的區域。  
  
     ![將轉換後的筆刷投影至輸出區域](./media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm_reltransform_5_transform_to_output")  
  
<a name="rotateexample"></a>   
## <a name="example-rotate-an-imagebrush-45-degrees"></a>範例：旋轉 ImageBrush 45 度  
 下列範例會套用<xref:System.Windows.Media.RotateTransform>要<xref:System.Windows.Media.Brush.RelativeTransform%2A>屬性<xref:System.Windows.Media.ImageBrush>。 <xref:System.Windows.Media.RotateTransform>物件的<xref:System.Windows.Media.RotateTransform.CenterX%2A>和<xref:System.Windows.Media.RotateTransform.CenterY%2A>屬性都設為 0.5，相對座標內容中心點。 如此一來，會以筆刷內容的中心為中心點旋轉。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 下一個範例也適用於<xref:System.Windows.Media.RotateTransform>要<xref:System.Windows.Media.ImageBrush>，但會使用<xref:System.Windows.Media.Brush.Transform%2A>屬性而非<xref:System.Windows.Media.Brush.RelativeTransform%2A>屬性。 若要旋轉筆刷的中心，<xref:System.Windows.Media.RotateTransform>物件的<xref:System.Windows.Media.RotateTransform.CenterX%2A>和<xref:System.Windows.Media.RotateTransform.CenterY%2A>必須設為絕對座標。 因為使用筆刷繪製的矩形為 175 x 90 像素，所以其中心點為 (87.5, 45)。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 下圖顯示沒有轉換，將轉換套用至筆刷<xref:System.Windows.Media.Brush.RelativeTransform%2A>屬性，以及將轉換套用至<xref:System.Windows.Media.Brush.Transform%2A>屬性。  
  
 ![筆刷的 RelativeTransform 和 Transform 設定](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
 這個範例是某完整範例的一部分。 如需完整的範例，請參閱 [Brush 範例](https://go.microsoft.com/fwlink/?LinkID=159973)。 如需筆刷的詳細資訊，請參閱 [WPF 筆刷概觀](wpf-brushes-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Brush.Transform%2A>
- <xref:System.Windows.Media.Brush.RelativeTransform%2A>
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Brush>
- [使用純色和漸層繪製的概觀](painting-with-solid-colors-and-gradients-overview.md)
- [使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)
- [轉換概觀](transforms-overview.md)
