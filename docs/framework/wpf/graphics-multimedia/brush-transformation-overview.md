---
title: "筆刷轉換概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], transformation properties
- properties [WPF], transformation
- transformation properties of brushes [WPF]
ms.assetid: 8b9bfc09-12fd-4cd5-b445-99949f27bc39
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b57c5ee36c9ed9c89fc8ca1bfb7ea265c2460c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="brush-transformation-overview"></a>筆刷轉換概觀
這個筆刷類別會提供兩個轉換屬性：<xref:System.Windows.Media.Brush.Transform%2A>和<xref:System.Windows.Media.Brush.RelativeTransform%2A>。 上述屬性可讓您旋轉、縮放、扭曲及平移筆刷的內容。 本主題說明這兩種屬性之間的差異並提供使用方式範例。  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 若要了解本主題，您應該了解您要轉換的筆刷功能。 如<xref:System.Windows.Media.LinearGradientBrush>和<xref:System.Windows.Media.RadialGradientBrush>，請參閱[使用單色和漸層概觀繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)。 如<xref:System.Windows.Media.ImageBrush>， <xref:System.Windows.Media.DrawingBrush>，或<xref:System.Windows.Media.VisualBrush>，請參閱[使用映像、 繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)。 您也應該熟悉[轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)中所述的 2D 轉換。  
  
<a name="transformversusrelativetransform"></a>   
## <a name="differences-between-the-transform-and-relativetransform-properties"></a>Transform 和 RelativeTransform 屬性之間的差異  
 當您將轉換套用至筆刷的<xref:System.Windows.Media.Brush.Transform%2A>屬性，您需要知道繪製區域的大小，如果您想要對其中心筆刷內容轉換。 假設繪製的區域寬度為 200 裝置獨立像素且高度為 150。  如果您使用<xref:System.Windows.Media.RotateTransform>輸出其中心點的 45 度旋轉筆刷、 可能賦予<xref:System.Windows.Media.RotateTransform><xref:System.Windows.Media.RotateTransform.CenterX%2A>為 100 和<xref:System.Windows.Media.RotateTransform.CenterY%2A>的 75。  
  
 當您將轉換套用至筆刷的<xref:System.Windows.Media.Brush.RelativeTransform%2A>屬性，該轉換套用到筆刷之前它的輸出會對應至繪製區域。 下列清單說明筆刷內容的處理和轉換順序。  
  
1.  處理筆刷的內容。 如<xref:System.Windows.Media.GradientBrush>，這表示決定漸層停駐區域。 如<xref:System.Windows.Media.TileBrush>、<xref:System.Windows.Media.TileBrush.Viewbox%2A>對應至<xref:System.Windows.Media.TileBrush.Viewport%2A>。 這會成為筆刷的輸出。  
  
2.  將筆刷的輸出投影至 1 x 1 轉換矩形。  
  
3.  套用的筆刷<xref:System.Windows.Media.Brush.RelativeTransform%2A>，如果有的話。  
  
4.  將轉換後的輸出投影至要繪製的區域。  
  
5.  套用的筆刷<xref:System.Windows.Media.Transform>，如果有的話。  
  
 因為<xref:System.Windows.Media.Brush.RelativeTransform%2A>筆刷的輸出會對應至 1x1 矩形，轉換中心點和位移的值似乎是相對時套用。 例如，如果您使用<xref:System.Windows.Media.RotateTransform>輸出其中心點的 45 度旋轉筆刷、 可能賦予<xref:System.Windows.Media.RotateTransform><xref:System.Windows.Media.RotateTransform.CenterX%2A>為 0.5 和<xref:System.Windows.Media.RotateTransform.CenterY%2A>為 0.5。  
  
 下圖顯示的已旋轉 45 度使用的數個筆刷輸出<xref:System.Windows.Media.Brush.RelativeTransform%2A>和<xref:System.Windows.Media.Brush.Transform%2A>屬性。  
  
 ![RelativeTransform 和 Transform 屬性](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm_brushrelativetransform_transform_small")  
  
<a name="relativetransformandtilebrush"></a>   
## <a name="using-relativetransform-with-a-tilebrush"></a>搭配 TileBrush 使用 RelativeTransform  
 拼貼筆刷會比其他筆刷更為複雜，因為套用<xref:System.Windows.Media.Brush.RelativeTransform%2A>其中一個可能會產生非預期的結果。 例如，使用下列影像。  
  
 ![來源映像](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-1-original-image.jpg "graphicsmm_reltransform_1_original_image")  
  
 下列範例會使用<xref:System.Windows.Media.ImageBrush>來繪製的上述影像的矩形區域。 它會套用<xref:System.Windows.Media.RotateTransform>至<xref:System.Windows.Media.ImageBrush>物件的<xref:System.Windows.Media.Brush.RelativeTransform%2A>屬性，並設定其<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性<xref:System.Windows.Media.Stretch.UniformToFill>，完全填滿的矩形拉長時，它應該保留影像的外觀比例。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 這個範例會產生下列輸出：  
  
 ![轉換後的輸出](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-6-output.png "graphicsmm_reltransform_6_output")  
  
 請注意，影像會扭曲，即使筆刷的<xref:System.Windows.Media.TileBrush.Stretch%2A>設<xref:System.Windows.Media.Stretch.UniformToFill>。 這是因為套用相對轉換後的筆刷<xref:System.Windows.Media.TileBrush.Viewbox%2A>對應到其<xref:System.Windows.Media.TileBrush.Viewport%2A>。 下列清單描述程序的每個步驟︰  
  
1.  專案 筆刷的內容 (<xref:System.Windows.Media.TileBrush.Viewbox%2A>) 到其基底的並排顯示 (<xref:System.Windows.Media.TileBrush.Viewport%2A>) 使用筆刷的<xref:System.Windows.Media.TileBrush.Stretch%2A>設定。  
  
     ![自動縮放 Viewbox 以符合檢視區](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm_reltransform_2_viewbox_to_viewport")  
  
2.  將基底的並排顯示投影至 1 x 1 轉換矩形。  
  
     ![將檢視區對應至轉換矩形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm_reltransform_3_output_to_transform")  
  
3.  套用<xref:System.Windows.Media.RotateTransform>。  
  
     ![套用相對轉換](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm_reltransform_4_transform_rotate")  
  
4.  將轉換後基底的並排顯示投影至要繪製的區域。  
  
     ![將轉換後的筆刷投影至輸出區域](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm_reltransform_5_transform_to_output")  
  
<a name="rotateexample"></a>   
## <a name="example-rotate-an-imagebrush-45-degrees"></a>範例︰ 旋轉 ImageBrush 45 度  
 下列範例會套用<xref:System.Windows.Media.RotateTransform>至<xref:System.Windows.Media.Brush.RelativeTransform%2A>屬性<xref:System.Windows.Media.ImageBrush>。 <xref:System.Windows.Media.RotateTransform>物件的<xref:System.Windows.Media.RotateTransform.CenterX%2A>和<xref:System.Windows.Media.RotateTransform.CenterY%2A>屬性都設定為 0.5，相對座標的內容的中心點。 如此一來，會以筆刷內容的中心為中心點旋轉。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 下一個範例也適用於<xref:System.Windows.Media.RotateTransform>至<xref:System.Windows.Media.ImageBrush>，但是會使用<xref:System.Windows.Media.Brush.Transform%2A>屬性而非<xref:System.Windows.Media.Brush.RelativeTransform%2A>屬性。 若要旋轉的中心，筆刷<xref:System.Windows.Media.RotateTransform>物件的<xref:System.Windows.Media.RotateTransform.CenterX%2A>和<xref:System.Windows.Media.RotateTransform.CenterY%2A>必須設為絕對座標。 因為使用筆刷繪製的矩形為 175 x 90 像素，所以其中心點為 (87.5, 45)。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 下圖顯示的筆刷的轉換，轉換套用至沒有<xref:System.Windows.Media.Brush.RelativeTransform%2A>屬性，與套用至轉換<xref:System.Windows.Media.Brush.Transform%2A>屬性。  
  
 ![筆刷的 RelativeTransform 和 Transform 設定](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
 這個範例是某完整範例的一部分。 如需完整的範例，請參閱 [Brush 範例](http://go.microsoft.com/fwlink/?LinkID=159973)。 如需筆刷的詳細資訊，請參閱 [WPF 筆刷概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.Brush.Transform%2A>  
 <xref:System.Windows.Media.Brush.RelativeTransform%2A>  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.Brush>  
 [使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
