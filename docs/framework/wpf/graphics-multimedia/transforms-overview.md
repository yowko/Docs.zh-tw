---
title: 轉換概觀
ms.date: 03/30/2017
helpviewer_keywords:
- transformations [WPF], about transformations
- classes [WPF], 2-D transform
- transform classes [WPF], 2-D
- 2-D transform classes
- FrameworkElement objects [WPF], rotating
- FrameworkElement objects [WPF], skewing
- FrameworkElement objects [WPF], translating
- Transforms [WPF], about Transforms
- FrameworkElement objects [WPF], scaling
ms.assetid: 8f153d5e-ed61-4aa5-a7cd-286f0c427a13
ms.openlocfilehash: 84d52da4eb51256f9de898f4553136deb2d9ab0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="transforms-overview"></a>轉換概觀
本主題描述如何使用[!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)]<xref:System.Windows.Media.Transform>旋轉、 縮放、 移動類別 （轉換） 和傾斜<xref:System.Windows.FrameworkElement>物件。  
  
  
<a name="whatIsATransformSection"></a>   
## <a name="what-is-a-transform"></a>什麼是轉換？  
 A<xref:System.Windows.Media.Transform>定義如何對應，或轉換，指向另一個座標空間從一個座標空間。 此對應所轉換描述<xref:System.Windows.Media.Matrix>，這是三個資料列集合的三個資料行具有<xref:System.Double>值。  
  
> [!NOTE]
>  Windows Presentation Foundation (WPF) 使用資料列為主矩陣。 向量會以資料列向量表示，而非資料行向量。  
  
 下表顯示 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 矩陣的結構。  
  
### <a name="a-2-d-transformation-matrix"></a>2D 轉換矩陣  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> 預設：1.0|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> 預設：0.0|0.0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> 預設：0.0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> 預設：1.0|0.0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> 預設：0.0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> 預設：0.0|1.0|  
  
 透過操作矩陣值，您可以旋轉、縮放、扭曲及移動 (平移) 物件。 例如，如果您變更了第三個資料列的第一個資料行中的值 (<xref:System.Windows.Media.Matrix.OffsetX%2A>值) 為 100，您可以使用它移動物件 100 單位沿著 x 軸。 如果您將第二個資料列的第二個資料行中的值變更為 3，則您可以使用它將物件伸展至其目前高度的三倍。 如果您同時變更這兩個值，您可以將物件沿著 x 軸移動 100 單位並將其高度伸展為 3 倍。 因為 Windows Presentation Foundation (WPF) 只支援仿射轉換，右邊的資料行中的值總是 0，0、 1。  
  
 雖然 Windows Presentation Foundation (WPF) 可讓您直接操作矩陣值，它也提供數個<xref:System.Windows.Media.Transform>類別，可讓您不需要知道基礎矩陣結構的設定方式轉換物件。 例如，<xref:System.Windows.Media.ScaleTransform>類別可讓您藉由設定縮放物件及其<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>和<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>屬性，而不是管理的轉換矩陣。 同樣地，<xref:System.Windows.Media.RotateTransform>類別可讓您旋轉物件直接設定其<xref:System.Windows.Media.RotateTransform.Angle%2A>屬性。  
  
<a name="transformClassesSection"></a>   
## <a name="transform-classes"></a>轉換類別  
 Windows Presentation Foundation (WPF) 提供了下列[!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)]<xref:System.Windows.Media.Transform>一般轉換作業的類別：  
  
|類別|描述|範例|圖例|  
|-----------|-----------------|-------------|------------------|  
|<xref:System.Windows.Media.RotateTransform>|項目以指定方向旋轉<xref:System.Windows.Media.RotateTransform.Angle%2A>。|[旋轉物件](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object.md)|![旋轉圖例](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-rotate.png "graphicsmm_thumbnails_rotate")|  
|<xref:System.Windows.Media.ScaleTransform>|調整項目指定<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>和<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>金額。|[縮放元素](../../../../docs/framework/wpf/graphics-multimedia/how-to-scale-an-element.md)|![縮放圖例](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-scale.png "graphicsmm_thumbnails_scale")|  
|<xref:System.Windows.Media.SkewTransform>|扭曲項目指定<xref:System.Windows.Media.SkewTransform.AngleX%2A>和<xref:System.Windows.Media.SkewTransform.AngleY%2A>金額。|[扭曲元素](../../../../docs/framework/wpf/graphics-multimedia/how-to-skew-an-element.md)|![扭曲圖例](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-skew.png "graphicsmm_thumbnails_skew")|  
|<xref:System.Windows.Media.TranslateTransform>|移動 （轉譯） 所指定的項目<xref:System.Windows.Media.TranslateTransform.X%2A>和<xref:System.Windows.Media.TranslateTransform.Y%2A>金額。|[平移元素](../../../../docs/framework/wpf/graphics-multimedia/how-to-translate-an-element.md)|![平移圖例](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-translate.png "graphicsmm_thumbnails_translate")|  
  
 要建立更複雜的轉換，Windows Presentation Foundation (WPF) 提供下列兩個類別：  
  
|類別|描述|範例|  
|-----------|-----------------|-------------|  
|<xref:System.Windows.Media.TransformGroup>|群組多個<xref:System.Windows.Media.TransformGroup>物件到單一<xref:System.Windows.Media.Transform>您可以再套用轉換屬性。|[將多個轉換套用至物件](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-multiple-transforms-to-an-object.md)|  
|<xref:System.Windows.Media.MatrixTransform>|建立自訂的轉換不提供其他<xref:System.Windows.Media.Transform>類別。 當您使用<xref:System.Windows.Media.MatrixTransform>，直接操作矩陣。|[使用 MatrixTransform 建立自訂轉換](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-matrixtransform-to-create-custom-transforms.md)|  
  
 Windows Presentation Foundation (WPF) 也會提供[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]轉換。 如需詳細資訊，請參閱 <xref:System.Windows.Media.Media3D.Transform3D> 類別。  
  
<a name="transformationproperties"></a>   
## <a name="common-transformation-properties"></a>常見轉換屬性  
 轉換物件的其中一種方式是宣告適當<xref:System.Windows.Media.Transform>輸入，並將它套用至轉換物件的屬性。 不同類型的物件擁有不同類型的轉換屬性。 下表列出的是數個常用的 Windows Presentation Foundation (WPF) 型別及其轉換屬性。  
  
|類型|轉換屬性|  
|----------|-------------------------------|  
|<xref:System.Windows.Media.Brush>|<xref:System.Windows.Media.Brush.Transform%2A>, <xref:System.Windows.Media.Brush.RelativeTransform%2A>|  
|<xref:System.Windows.Media.ContainerVisual>|<xref:System.Windows.Media.ContainerVisual.Transform%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|  
|<xref:System.Windows.FrameworkElement>|<xref:System.Windows.UIElement.RenderTransform%2A>, <xref:System.Windows.FrameworkElement.LayoutTransform%2A>|  
|<xref:System.Windows.Media.Geometry>|<xref:System.Windows.Media.Geometry.Transform%2A>|  
|<xref:System.Windows.Media.TextEffect>|<xref:System.Windows.Media.TextEffect.Transform%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.RenderTransform%2A>|  
  
<a name="transformcenter"></a>   
## <a name="transformations-and-coordinate-systems"></a>轉換和座標系統  
 當您轉換物件時，您不只是轉換物件，也同時轉換該物件所在的座標空間。 根據預設，轉換會以目標物件之座標系統的原點為中心：(0,0)。 唯一的例外是<xref:System.Windows.Media.TranslateTransform>;<xref:System.Windows.Media.TranslateTransform>沒有設定，因為轉譯效果是，它會置中相同的中心屬性。  
  
 下列範例會使用<xref:System.Windows.Media.RotateTransform>旋轉<xref:System.Windows.Shapes.Rectangle>元素中，一種<xref:System.Windows.FrameworkElement>，旋轉 45 度預設中心，（0，0）。 下圖顯示旋轉的效果。  
  
 ![旋轉 45 度的 FrameworkElement &#40;0，0&#41;](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm_FE_rotated_about_upperleft_corner")  
以點 (0,0) 為中心旋轉 45 度的矩形元素  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 根據預設，元素會以其左上角 (0, 0) 為中心旋轉。 <xref:System.Windows.Media.RotateTransform>， <xref:System.Windows.Media.ScaleTransform>，和<xref:System.Windows.Media.SkewTransform>類別提供 CenterX 和 CenterY 屬性，可讓您指定套用轉換的點。  
  
 下一個範例也會使用<xref:System.Windows.Media.RotateTransform>旋轉<xref:System.Windows.Shapes.Rectangle>旋轉 45 度; 的項目不過，這次<xref:System.Windows.Media.RotateTransform.CenterX%2A>和<xref:System.Windows.Media.RotateTransform.CenterY%2A>屬性會設定讓<xref:System.Windows.Media.RotateTransform>具有的中心 （25，25）。 下圖顯示旋轉的效果。  
  
 ![關於旋轉 45 度的幾何&#40;25，25&#41;](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-fe-rotated-about-center.png "graphicsmm_FE_rotated_about_center")  
以點 (25, 25) 為中心旋轉 45 度的矩形元素  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>   
## <a name="transforming-a-frameworkelement"></a>轉換 FrameworkElement  
 若要套用的轉換， <xref:System.Windows.FrameworkElement>，建立<xref:System.Windows.Media.Transform>並將它套用到兩個屬性的其中一個，<xref:System.Windows.FrameworkElement>類別提供：  
  
-   <xref:System.Windows.FrameworkElement.LayoutTransform%2A> – 套用之前在配置階段轉換。 套用轉換之後，版面配置系統會處理已轉換的元素大小和位置。  
  
-   <xref:System.Windows.UIElement.RenderTransform%2A> – 修改項目的外觀，但是配置傳遞之後，會套用的轉換已完成。 使用<xref:System.Windows.UIElement.RenderTransform%2A>屬性而非<xref:System.Windows.FrameworkElement.LayoutTransform%2A>屬性，您可以取得效能優勢。  
  
 您應該使用哪個屬性？ 因為它會提供效能優勢，使用<xref:System.Windows.UIElement.RenderTransform%2A>屬性只要可能，特別是當您使用動畫顯示<xref:System.Windows.Media.Transform>物件。 使用<xref:System.Windows.FrameworkElement.LayoutTransform%2A>縮放、 旋轉，或扭曲時的屬性，且需要項目的父項目的轉換後的大小調整。 請注意，搭配使用時<xref:System.Windows.FrameworkElement.LayoutTransform%2A>屬性，<xref:System.Windows.Media.TranslateTransform>物件會出現在項目上沒有作用。 這是因為版面配置系統會在其處理期間將已平移元素移回到其原始位置。  
  
 如需有關 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中版面配置的詳細資訊，請參閱[版面配置](../../../../docs/framework/wpf/advanced/layout.md)概觀。  
  
<a name="exampleRotateAnElement45degSection"></a>   
## <a name="example-rotate-a-frameworkelement-45-degrees"></a>範例︰將 FrameworkElement 旋轉 45 度  
 下列範例會使用<xref:System.Windows.Media.RotateTransform>順時針方向按鈕旋轉 45 度。 中包含按鈕<xref:System.Windows.Controls.StackPanel>，有兩個其他按鈕。  
  
 根據預設，<xref:System.Windows.Media.RotateTransform>旋轉的點 （0，0）。 因為範例沒有指定中心值，所以按鈕會以點 (0, 0) (也就是左上角) 為中心旋轉。 <xref:System.Windows.Media.RotateTransform>套用至<xref:System.Windows.UIElement.RenderTransform%2A>屬性。 下圖顯示轉換的結果。  
  
 ![使用 rendertransform 經過轉換的按鈕](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
以左上角為中心順時針旋轉 45 度  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 下一個範例也會使用<xref:System.Windows.Media.RotateTransform>旋轉 45 度順時鐘方向的按鈕，但它也設定<xref:System.Windows.UIElement.RenderTransformOrigin%2A>按鈕的 （0.5，0.5）。 值<xref:System.Windows.UIElement.RenderTransformOrigin%2A>屬性是相對於按鈕的大小。 因此，旋轉會套用到按鈕的中心，而非其左上角。 下圖顯示轉換的結果。  
  
 ![對其中心轉換的按鈕](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
圍繞中心順時針旋轉 45 度  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 下列範例會使用<xref:System.Windows.FrameworkElement.LayoutTransform%2A>屬性而非<xref:System.Windows.UIElement.RenderTransform%2A>旋轉按鈕的屬性。  這會使轉換影響按鈕的版面配置，這會觸發版面配置系統的完整作業。 因此，按鈕會旋轉並重新調整位置，因為它的大小已變更。 下圖顯示轉換的結果。  
  
 ![使用 layouttransform 經過轉換的按鈕](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-layouttransform.png "graphicsmm_LayoutTransform")  
用來旋轉按鈕的 LayoutTransform  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>   
## <a name="animating-transformations"></a>建立轉換的動畫  
 因為它們是繼承自<xref:System.Windows.Media.Animation.Animatable>類別<xref:System.Windows.Media.Transform>類別可以動畫顯示。 若要建立動畫<xref:System.Windows.Media.Transform>，套用至您想要製作動畫的屬性的動畫相容的型別。  
  
 下列範例會使用<xref:System.Windows.Media.Animation.Storyboard>和<xref:System.Windows.Media.Animation.DoubleAnimation>與<xref:System.Windows.Media.RotateTransform>進行<xref:System.Windows.Controls.Button>微調在按一下時其位置。  
  
 [!code-xaml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 如需完整範例，請參閱 [2D 轉換範例](http://go.microsoft.com/fwlink/?LinkID=158252)。 如需動畫的詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Freezable 功能  
 因為它繼承自<xref:System.Windows.Freezable>類別<xref:System.Windows.Media.Transform>類別提供數個特殊功能：<xref:System.Windows.Media.Transform>物件可以宣告為[資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)、 變成唯讀，以改善的多個物件之間共用效能考量，複製，而且進行安全執行緒。 如需有關各項功能所提供的<xref:System.Windows.Freezable>物件，請參閱[Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.Matrix>  
 [HOW-TO 主題](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [2D 轉換範例](http://go.microsoft.com/fwlink/?LinkID=158252)
