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
ms.openlocfilehash: 89b781d3e5b88a66598a301a1d08cf7dfedd57a5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962904"
---
# <a name="transforms-overview"></a>轉換概觀
本主題描述如何使用 2d <xref:System.Windows.Media.Transform>類別來旋轉、縮放、移動 (轉譯) 和扭曲<xref:System.Windows.FrameworkElement>物件。  

<a name="whatIsATransformSection"></a>   
## <a name="what-is-a-transform"></a>什麼是轉換？  
 <xref:System.Windows.Media.Transform>定義如何對應或轉換, 從一個座標空間指向另一個座標空間。 這個對應是由轉換<xref:System.Windows.Media.Matrix>所描述, 這是三個數據列的集合, 其中包含三個數據行的<xref:System.Double>值。  
  
> [!NOTE]
> Windows Presentation Foundation (WPF) 使用資料列主要的矩陣。 向量會以資料列向量表示，而非資料行向量。  
  
 下表顯示 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 矩陣的結構。  
  
### <a name="a-2-d-transformation-matrix"></a>2D 轉換矩陣  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> 預設值：1.0|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> 預設值：0.0|0.0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> 預設值：0.0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> 預設值：1.0|0.0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> 預設值：0.0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> 預設值：0.0|1.0|  
  
 透過操作矩陣值，您可以旋轉、縮放、扭曲及移動 (平移) 物件。 例如, 如果您將第三個數據列 ( <xref:System.Windows.Media.Matrix.OffsetX%2A>值) 的第一個資料行中的值變更為 100, 就可以使用它來沿著 X 軸移動物件100單位。 如果您將第二個資料列的第二個資料行中的值變更為 3，則您可以使用它將物件伸展至其目前高度的三倍。 如果您同時變更這兩個值，您可以將物件沿著 x 軸移動 100 單位並將其高度伸展為 3 倍。 因為 Windows Presentation Foundation (WPF) 只支援仿射轉換, 所以右欄中的值一律為 0, 0, 1。  
  
 雖然 Windows Presentation Foundation (WPF) 可讓您直接操控矩陣值, 但它也提供<xref:System.Windows.Media.Transform>數個類別, 可讓您轉換物件, 而不需要知道基礎矩陣結構的設定方式。 例如, <xref:System.Windows.Media.ScaleTransform>類別可讓您透過設定其<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>和<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>屬性來調整物件, 而不是操作轉換矩陣。 同樣地, <xref:System.Windows.Media.RotateTransform>類別也可讓您藉由只設定其<xref:System.Windows.Media.RotateTransform.Angle%2A>屬性來旋轉物件。  
  
<a name="transformClassesSection"></a>   
## <a name="transform-classes"></a>轉換類別  
 Windows Presentation Foundation (WPF) 為一般轉換作業提供下列<xref:System.Windows.Media.Transform>二維類別:  
  
|類別|說明|範例|圖例|  
|-----------|-----------------|-------------|------------------|  
|<xref:System.Windows.Media.RotateTransform>|依據指定<xref:System.Windows.Media.RotateTransform.Angle%2A>的旋轉元素。|[旋轉物件](how-to-rotate-an-object.md)|![旋轉圖例](./media/graphicsmm-thumbnails-rotate.png "graphicsmm_thumbnails_rotate")|  
|<xref:System.Windows.Media.ScaleTransform>|根據指定<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>的和<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>數量來縮放元素。|[縮放元素](how-to-scale-an-element.md)|![縮放圖例](./media/graphicsmm-thumbnails-scale.png "graphicsmm_thumbnails_scale")|  
|<xref:System.Windows.Media.SkewTransform>|根據指定<xref:System.Windows.Media.SkewTransform.AngleX%2A>的和<xref:System.Windows.Media.SkewTransform.AngleY%2A>數量來扭曲元素。|[扭曲元素](how-to-skew-an-element.md)|![扭曲圖例](./media/graphicsmm-thumbnails-skew.png "graphicsmm_thumbnails_skew")|  
|<xref:System.Windows.Media.TranslateTransform>|依據指定<xref:System.Windows.Media.TranslateTransform.X%2A>的和<xref:System.Windows.Media.TranslateTransform.Y%2A>數量移動 (轉譯) 元素。|[平移元素](how-to-translate-an-element.md)|![平移圖例](./media/graphicsmm-thumbnails-translate.png "graphicsmm_thumbnails_translate")|  
  
 若要建立更複雜的轉換, Windows Presentation Foundation (WPF) 提供下列兩個類別:  
  
|類別|描述|範例|  
|-----------|-----------------|-------------|  
|<xref:System.Windows.Media.TransformGroup>|將多<xref:System.Windows.Media.TransformGroup>個物件組成單一<xref:System.Windows.Media.Transform> , 讓您可以套用至轉換屬性。|[將多個轉換套用至物件](how-to-apply-multiple-transforms-to-an-object.md)|  
|<xref:System.Windows.Media.MatrixTransform>|建立其他<xref:System.Windows.Media.Transform>類別未提供的自訂轉換。 當您使用<xref:System.Windows.Media.MatrixTransform>時, 您會直接操控矩陣。|[使用 MatrixTransform 建立自訂轉換](how-to-use-a-matrixtransform-to-create-custom-transforms.md)|  
  
 Windows Presentation Foundation (WPF) 也提供3D 轉換。 如需詳細資訊，請參閱 <xref:System.Windows.Media.Media3D.Transform3D> 類別。  
  
<a name="transformationproperties"></a>   
## <a name="common-transformation-properties"></a>常見轉換屬性  
 轉換物件的其中一種方式是宣告適當<xref:System.Windows.Media.Transform>的類型, 並將其套用至物件的轉換屬性。 不同類型的物件擁有不同類型的轉換屬性。 下表列出數個常用的 Windows Presentation Foundation (WPF) 類型及其轉換屬性。  
  
|類型|轉換屬性|  
|----------|-------------------------------|  
|<xref:System.Windows.Media.Brush>|<xref:System.Windows.Media.Brush.Transform%2A>、 <xref:System.Windows.Media.Brush.RelativeTransform%2A>|  
|<xref:System.Windows.Media.ContainerVisual>|<xref:System.Windows.Media.ContainerVisual.Transform%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|  
|<xref:System.Windows.FrameworkElement>|<xref:System.Windows.UIElement.RenderTransform%2A>、 <xref:System.Windows.FrameworkElement.LayoutTransform%2A>|  
|<xref:System.Windows.Media.Geometry>|<xref:System.Windows.Media.Geometry.Transform%2A>|  
|<xref:System.Windows.Media.TextEffect>|<xref:System.Windows.Media.TextEffect.Transform%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.RenderTransform%2A>|  
  
<a name="transformcenter"></a>   
## <a name="transformations-and-coordinate-systems"></a>轉換和座標系統  
 當您轉換物件時，您不只是轉換物件，也同時轉換該物件所在的座標空間。 根據預設, 轉換會以目標物件座標系統的原點為中心:(0, 0)。 唯一的例外狀況<xref:System.Windows.Media.TranslateTransform>是<xref:System.Windows.Media.TranslateTransform> , 沒有要設定的中間屬性, 因為不論其置中位置為何, 轉譯效果都相同。  
  
 下列範例會使用<xref:System.Windows.Media.RotateTransform>來<xref:System.Windows.Shapes.Rectangle>旋轉<xref:System.Windows.FrameworkElement>元素 (其預設中心的類型, 45 度), (0, 0)。 下圖顯示旋轉的效果。  
  
 ![FrameworkElement 旋轉45度約&#40;0, 0&#41; ](./media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm_FE_rotated_about_upperleft_corner")  
以點 (0,0) 為中心旋轉 45 度的矩形元素  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 根據預設，元素會以其左上角 (0, 0) 為中心旋轉。 <xref:System.Windows.Media.RotateTransform>、和類別<xref:System.Windows.Media.SkewTransform>提供 system.windows.media.rotatetransform.centerx 和 CenterY 屬性, 可讓您指定套用轉換的時間點。 <xref:System.Windows.Media.ScaleTransform>  
  
 下一個範例也會使用<xref:System.Windows.Media.RotateTransform>將<xref:System.Windows.Shapes.Rectangle>元素旋轉45度, <xref:System.Windows.Media.RotateTransform.CenterX%2A>不過, 這次會設定和<xref:System.Windows.Media.RotateTransform.CenterY%2A>屬性, 使<xref:System.Windows.Media.RotateTransform>的中心為 (25, 25)。 下圖顯示旋轉的效果。  
  
 ![旋轉45度約&#40;25, 25&#41;的幾何](./media/graphicsmm-fe-rotated-about-center.png "graphicsmm_FE_rotated_about_center")  
以點 (25, 25) 為中心旋轉 45 度的矩形元素  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>   
## <a name="transforming-a-frameworkelement"></a>轉換 FrameworkElement  
 若要將轉換套用<xref:System.Windows.FrameworkElement>至, 請<xref:System.Windows.Media.Transform>建立, 並將它套用至<xref:System.Windows.FrameworkElement>類別提供的兩個屬性其中之一:  
  
- <xref:System.Windows.FrameworkElement.LayoutTransform%2A>–在版面配置傳遞之前套用的轉換。 套用轉換之後，版面配置系統會處理已轉換的元素大小和位置。  
  
- <xref:System.Windows.UIElement.RenderTransform%2A>–修改元素外觀的轉換, 但在版面配置傳遞完成後才會套用。 藉由使用<xref:System.Windows.UIElement.RenderTransform%2A>屬性, 而不<xref:System.Windows.FrameworkElement.LayoutTransform%2A>是屬性, 您可以獲得效能優勢。  
  
 您應該使用哪個屬性？ 基於它所提供的效能優勢, 請盡可能使用<xref:System.Windows.UIElement.RenderTransform%2A>屬性, 特別是當您使用動畫<xref:System.Windows.Media.Transform>物件時。 縮放、旋轉或扭曲時, 請使用屬性,而您需要元素的父系,以調整為專案的已轉換大小。<xref:System.Windows.FrameworkElement.LayoutTransform%2A> 請注意, 當與<xref:System.Windows.FrameworkElement.LayoutTransform%2A>屬性搭配使用時, <xref:System.Windows.Media.TranslateTransform>物件似乎不會影響元素。 這是因為版面配置系統會在其處理期間將已平移元素移回到其原始位置。  
  
 如需有關 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中版面配置的詳細資訊，請參閱[版面配置](../advanced/layout.md)概觀。  
  
<a name="exampleRotateAnElement45degSection"></a>   
## <a name="example-rotate-a-frameworkelement-45-degrees"></a>範例：旋轉 FrameworkElement 45 度  
 下列範例會使用<xref:System.Windows.Media.RotateTransform>來以45度順時針旋轉按鈕。 按鈕包含在有兩個<xref:System.Windows.Controls.StackPanel>其他按鈕的中。  
  
 根據預設, <xref:System.Windows.Media.RotateTransform>會將點 (0, 0) 旋轉。 因為範例沒有指定中心值，所以按鈕會以點 (0, 0) (也就是左上角) 為中心旋轉。 <xref:System.Windows.Media.RotateTransform>會套用<xref:System.Windows.UIElement.RenderTransform%2A>至屬性。 下圖顯示轉換的結果。  
  
 ![使用 RenderTransform 轉換的按鈕](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
以左上角為中心順時針旋轉 45 度  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 下一個範例也會使用<xref:System.Windows.Media.RotateTransform>來順時針旋轉按鈕45度, 但它也會<xref:System.Windows.UIElement.RenderTransformOrigin%2A>將按鈕的設定為 (0.5, 0.5)。 <xref:System.Windows.UIElement.RenderTransformOrigin%2A>屬性的值是相對於按鈕的大小。 因此，旋轉會套用到按鈕的中心，而非其左上角。 下圖顯示轉換的結果。  
  
 已![轉換其中心的按鈕](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
圍繞中心順時針旋轉 45 度  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 下列範例會使用<xref:System.Windows.FrameworkElement.LayoutTransform%2A>屬性, 而不是<xref:System.Windows.UIElement.RenderTransform%2A>屬性來旋轉按鈕。  這會使轉換影響按鈕的版面配置，這會觸發版面配置系統的完整作業。 因此，按鈕會旋轉並重新調整位置，因為它的大小已變更。 下圖顯示轉換的結果。  
  
 ![使用 LayoutTransform 轉換的按鈕](./media/graphicsmm-layouttransform.png "graphicsmm_LayoutTransform")  
用來旋轉按鈕的 LayoutTransform  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample3](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>   
## <a name="animating-transformations"></a>建立轉換的動畫  
 因為它們繼承自<xref:System.Windows.Media.Animation.Animatable>類別, 所以可以製作動畫的<xref:System.Windows.Media.Transform>類別。 若要建立<xref:System.Windows.Media.Transform>動畫, 請將相容類型的動畫套用至您想要建立動畫的屬性。  
  
 <xref:System.Windows.Media.Animation.Storyboard>下列範例會使用<xref:System.Windows.Media.Animation.DoubleAnimation>和<xref:System.Windows.Media.RotateTransform>搭配來進行按一下時的<xref:System.Windows.Controls.Button>微調。  
  
 [!code-xaml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 如需完整範例，請參閱 [2D 轉換範例](https://go.microsoft.com/fwlink/?LinkID=158252)。 如需動畫的詳細資訊，請參閱[動畫概觀](animation-overview.md)。  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Freezable 功能  
 因為它繼承<xref:System.Windows.Freezable>自類別<xref:System.Windows.Media.Transform> , 所以類別提供數個特殊功能: <xref:System.Windows.Media.Transform>物件可以宣告為[資源](../advanced/xaml-resources.md), 在多個物件之間共用, 使其成為唯讀以改善效能、複製和設為安全線程。 如需<xref:System.Windows.Freezable>物件所提供之不同功能的詳細資訊, 請參閱可[凍結物件的總覽](../advanced/freezable-objects-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Matrix>
- [HOW-TO 主題](transformations-how-to-topics.md)
- [2D 轉換範例](https://go.microsoft.com/fwlink/?LinkID=158252)
