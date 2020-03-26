---
title: 轉換概觀
ms.date: 03/30/2017
helpviewer_keywords:
- transformations [WPF], about transformations
- classes [WPF], 2D transform
- transform classes [WPF], 2D
- 2D transform classes
- FrameworkElement objects [WPF], rotating
- FrameworkElement objects [WPF], skewing
- FrameworkElement objects [WPF], translating
- Transforms [WPF], about Transforms
- FrameworkElement objects [WPF], scaling
ms.assetid: 8f153d5e-ed61-4aa5-a7cd-286f0c427a13
ms.openlocfilehash: c5f29404a301eb023ff24b2890531dede6440ec4
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111955"
---
# <a name="transforms-overview"></a>轉換概觀
本主題介紹如何使用 2D<xref:System.Windows.Media.Transform>類旋轉、縮放、移動（平移）和傾斜<xref:System.Windows.FrameworkElement>物件。  

<a name="whatIsATransformSection"></a>
## <a name="what-is-a-transform"></a>什麼是轉換？  
 定義<xref:System.Windows.Media.Transform>如何映射或轉換從一個座標空間到另一個座標空間的點。 此映射由轉換描述，該<xref:System.Windows.Media.Matrix>轉換是包含三列值的<xref:System.Double>三行的集合。  
  
> [!NOTE]
> Windows 演示基礎 （WPF） 使用行主矩陣。 向量會以資料列向量表示，而非資料行向量。  
  
 下表顯示 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 矩陣的結構。  
  
### <a name="a-2d-transformation-matrix"></a>二維變換矩陣  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> 預設：1.0|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> 預設：0.0|0.0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> 預設：0.0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> 預設：1.0|0.0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> 預設：0.0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> 預設：0.0|1.0|  
  
 透過操作矩陣值，您可以旋轉、縮放、扭曲及移動 (平移) 物件。 例如，如果將第三行（<xref:System.Windows.Media.Matrix.OffsetX%2A>值）第一列中的值更改為 100，則可以使用該值沿 X 軸移動物件 100 個單位。 如果您將第二個資料列的第二個資料行中的值變更為 3，則您可以使用它將物件伸展至其目前高度的三倍。 如果您同時變更這兩個值，您可以將物件沿著 x 軸移動 100 單位並將其高度伸展為 3 倍。 由於 Windows 演示文稿基礎 （WPF） 僅支援仿外轉換，因此右列中的值始終為 0、0、1。  
  
 儘管 Windows 演示文稿基礎 （WPF） 使您能夠直接操作矩陣值，但它也提供了<xref:System.Windows.Media.Transform>多個類，使您能夠轉換物件而無需知道基礎矩陣結構的配置方式。 例如，<xref:System.Windows.Media.ScaleTransform>類使您能夠通過設置物件<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>和<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>屬性來縮放物件，而不是操作轉換矩陣。 同樣，<xref:System.Windows.Media.RotateTransform>類使您能夠通過設置物件的屬性來旋轉物件<xref:System.Windows.Media.RotateTransform.Angle%2A>。  
  
<a name="transformClassesSection"></a>
## <a name="transform-classes"></a>轉換類別  
 Windows 演示基礎 （WPF） 為常見<xref:System.Windows.Media.Transform>轉換操作提供以下 2D 類：  
  
|類別|描述|範例|圖例|  
|-----------|-----------------|-------------|------------------|  
|<xref:System.Windows.Media.RotateTransform>|按指定的<xref:System.Windows.Media.RotateTransform.Angle%2A>旋轉元素。|[旋轉物件](how-to-rotate-an-object.md)|![旋轉圖例](./media/graphicsmm-thumbnails-rotate.png "graphicsmm_thumbnails_rotate")|  
|<xref:System.Windows.Media.ScaleTransform>|按指定<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>和<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>數量縮放元素。|[縮放元素](how-to-scale-an-element.md)|![縮放圖例](./media/graphicsmm-thumbnails-scale.png "graphicsmm_thumbnails_scale")|  
|<xref:System.Windows.Media.SkewTransform>|按指定<xref:System.Windows.Media.SkewTransform.AngleX%2A>和<xref:System.Windows.Media.SkewTransform.AngleY%2A>數量傾斜元素。|[扭曲元素](how-to-skew-an-element.md)|![傾斜圖例](./media/graphicsmm-thumbnails-skew.png "graphicsmm_thumbnails_skew")|  
|<xref:System.Windows.Media.TranslateTransform>|按指定<xref:System.Windows.Media.TranslateTransform.X%2A>和<xref:System.Windows.Media.TranslateTransform.Y%2A>數量移動（翻譯）元素。|[平移元素](how-to-translate-an-element.md)|![轉譯圖例](./media/graphicsmm-thumbnails-translate.png "graphicsmm_thumbnails_translate")|  
  
 對於創建更複雜的轉換，Windows 演示文稿基礎 （WPF） 提供以下兩個類：  
  
|類別|描述|範例|  
|-----------|-----------------|-------------|  
|<xref:System.Windows.Media.TransformGroup>|將多個<xref:System.Windows.Media.TransformGroup>物件分組為單個<xref:System.Windows.Media.Transform>物件，然後可以應用於轉換屬性。|[將多個轉換套用至物件](how-to-apply-multiple-transforms-to-an-object.md)|  
|<xref:System.Windows.Media.MatrixTransform>|創建其他<xref:System.Windows.Media.Transform>類未提供的自訂轉換。 使用 時<xref:System.Windows.Media.MatrixTransform>，將直接操作矩陣。|[使用 MatrixTransform 建立自訂轉換](how-to-use-a-matrixtransform-to-create-custom-transforms.md)|  
  
 Windows 演示基礎 （WPF） 還提供 3D 轉換。 如需詳細資訊，請參閱 <xref:System.Windows.Media.Media3D.Transform3D> 類別。  
  
<a name="transformationproperties"></a>
## <a name="common-transformation-properties"></a>常見轉換屬性  
 轉換物件的一種方法是聲明適當的<xref:System.Windows.Media.Transform>類型並將其應用於物件的轉換屬性。 不同類型的物件擁有不同類型的轉換屬性。 下表列出了幾種常用的 Windows 演示文稿基礎 （WPF） 類型及其轉換屬性。  
  
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
 當您轉換物件時，您不只是轉換物件，也同時轉換該物件所在的座標空間。 根據預設，轉換會以目標物件之座標系統的原點為中心：(0,0)。 唯一的例外<xref:System.Windows.Media.TranslateTransform>是;<xref:System.Windows.Media.TranslateTransform> a 沒有要設置的中心屬性，因為轉換效果是相同的，無論它居中。  
  
 下面的示例使用<xref:System.Windows.Media.RotateTransform>將<xref:System.Windows.Shapes.Rectangle>元素（一種類型為<xref:System.Windows.FrameworkElement>的 ）在其預設中心 （0， 0） 上旋轉 45 度。 下圖顯示旋轉的效果。  
  
 ![以 &#40;0,0&#41; 為中心旋轉 45 度的 FrameworkElement](./media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm_FE_rotated_about_upperleft_corner")  
以點 (0,0) 為中心旋轉 45 度的矩形元素  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 根據預設，元素會以其左上角 (0, 0) 為中心旋轉。 <xref:System.Windows.Media.ScaleTransform> <xref:System.Windows.Media.SkewTransform>和<xref:System.Windows.Media.RotateTransform>類提供 CenterX 和 CenterY 屬性，使您能夠指定應用轉換的點。  
  
 下一個示例還使用<xref:System.Windows.Media.RotateTransform>將<xref:System.Windows.Shapes.Rectangle>元素旋轉 45 度;如果將 元素旋轉 45 度。但是，這一次<xref:System.Windows.Media.RotateTransform.CenterX%2A><xref:System.Windows.Media.RotateTransform.CenterY%2A>的 和 屬性被<xref:System.Windows.Media.RotateTransform>設置，以便 具有一個中心 （25， 25）。 下圖顯示旋轉的效果。  
  
 ![以 &#40;25, 25&#41; 為中心旋轉 45 度的幾何](./media/graphicsmm-fe-rotated-about-center.png "graphicsmm_FE_rotated_about_center")  
以點 (25, 25) 為中心旋轉 45 度的矩形元素  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>
## <a name="transforming-a-frameworkelement"></a>轉換 FrameworkElement  
 要將轉換應用於 ，<xref:System.Windows.FrameworkElement>創建<xref:System.Windows.Media.Transform>並將其應用於<xref:System.Windows.FrameworkElement>類提供的兩個屬性之一：  
  
- <xref:System.Windows.FrameworkElement.LayoutTransform%2A>• 在佈局通過之前應用的轉換。 套用轉換之後，版面配置系統會處理已轉換的元素大小和位置。  
  
- <xref:System.Windows.UIElement.RenderTransform%2A>• 修改元素外觀但在佈局傳遞完成後應用的轉換。 通過使用 屬性<xref:System.Windows.UIElement.RenderTransform%2A>而不是 屬性，<xref:System.Windows.FrameworkElement.LayoutTransform%2A>可以獲得性能優勢。  
  
 您應該使用哪個屬性？ 由於它提供的性能優勢，因此盡可能使用 該<xref:System.Windows.UIElement.RenderTransform%2A>屬性，尤其是在使用動畫<xref:System.Windows.Media.Transform>物件時。 縮放、<xref:System.Windows.FrameworkElement.LayoutTransform%2A>旋轉或傾斜時使用 該屬性，您需要元素的父級以調整到元素的轉換大小。 請注意，當物件與<xref:System.Windows.FrameworkElement.LayoutTransform%2A>屬性一起使用時，<xref:System.Windows.Media.TranslateTransform>物件似乎對元素沒有影響。 這是因為版面配置系統會在其處理期間將已平移元素移回到其原始位置。  
  
 如需有關 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中版面配置的詳細資訊，請參閱[版面配置](../advanced/layout.md)概觀。  
  
<a name="exampleRotateAnElement45degSection"></a>
## <a name="example-rotate-a-frameworkelement-45-degrees"></a>範例︰將 FrameworkElement 旋轉 45 度  
 下面的示例使用<xref:System.Windows.Media.RotateTransform>沿時針旋轉按鈕 45 度。 該按鈕包含在具有兩個<xref:System.Windows.Controls.StackPanel>其他按鈕的 中。  
  
 預設情況下，a<xref:System.Windows.Media.RotateTransform>圍繞點旋轉 （0， 0）。 因為範例沒有指定中心值，所以按鈕會以點 (0, 0) (也就是左上角) 為中心旋轉。 <xref:System.Windows.Media.RotateTransform>應用於 屬性<xref:System.Windows.UIElement.RenderTransform%2A>。 下圖顯示轉換的結果。  
  
 ![使用 RenderTransform 進行轉換的按鈕](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
以左上角為中心順時針旋轉 45 度  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 下一個示例還使用<xref:System.Windows.Media.RotateTransform>順時針旋轉按鈕 45 度，但它也將按鈕<xref:System.Windows.UIElement.RenderTransformOrigin%2A>的將設置為 （0.5， 0.5）。 <xref:System.Windows.UIElement.RenderTransformOrigin%2A>屬性的值與按鈕的大小相關。 因此，旋轉會套用到按鈕的中心，而非其左上角。 下圖顯示轉換的結果。  
  
 ![以其中心轉換的按鈕](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
圍繞中心順時針旋轉 45 度  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 下面的示例使用 屬性<xref:System.Windows.FrameworkElement.LayoutTransform%2A>而不是 屬性<xref:System.Windows.UIElement.RenderTransform%2A>來旋轉按鈕。  這會使轉換影響按鈕的版面配置，這會觸發版面配置系統的完整作業。 因此，按鈕會旋轉並重新調整位置，因為它的大小已變更。 下圖顯示轉換的結果。  
  
 ![使用 LayoutTransform 進行轉換的按鈕](./media/graphicsmm-layouttransform.png "graphicsmm_LayoutTransform")  
用來旋轉按鈕的 LayoutTransform  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample3](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>
## <a name="animating-transformations"></a>以動畫顯示轉換  
 因為它們從<xref:System.Windows.Media.Animation.Animatable>類繼承，<xref:System.Windows.Media.Transform>因此類可以進行動畫處理。 要為<xref:System.Windows.Media.Transform>動畫，請將相容類型的動畫應用於要設置動畫的屬性。  
  
 下面的<xref:System.Windows.Media.Animation.Storyboard>示例使用 和 a，<xref:System.Windows.Media.Animation.DoubleAnimation><xref:System.Windows.Media.RotateTransform><xref:System.Windows.Controls.Button>在按一下時進行旋轉。  
  
 [!code-xaml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 有關完整示例，請參閱[2D 變換示例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)。 如需動畫的詳細資訊，請參閱[動畫概觀](animation-overview.md)。  
  
<a name="freezable_features"></a>
## <a name="freezable-features"></a>Freezable 功能  
 <xref:System.Windows.Freezable>由於該<xref:System.Windows.Media.Transform>類從類繼承，因此提供了幾個特殊功能：<xref:System.Windows.Media.Transform>物件可以聲明為[資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)，在多個物件之間共用，使唯讀以提高性能，克隆，使執行緒安全。 有關<xref:System.Windows.Freezable>物件提供的不同要素的詳細資訊，請參閱[可凍結物件概述](../advanced/freezable-objects-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Matrix>
- [如何使用主題](transformations-how-to-topics.md)
- [2D 變換示例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)
