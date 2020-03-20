---
title: 畫筆概述
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
ms.openlocfilehash: 7a9474b392052900952f5b677ad94b16025de8dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186569"
---
# <a name="wpf-brushes-overview"></a>WPF 筆刷概觀
螢幕上可見的一切可見，因為它是由畫筆繪製的。 例如，畫筆用於描述按鈕的背景、文本的前景和形狀的填充。 本主題介紹使用[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]畫筆繪畫的概念，並提供示例。 筆刷可讓您以任何項目 (從簡單的純色到複雜的圖樣和影像集) 繪製 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 物件。  
  
<a name="paintingwithbrush"></a>
## <a name="painting-with-a-brush"></a>用畫筆繪畫  
 具有<xref:System.Windows.Media.Brush>輸出的區域的"繪製"。 不同的筆刷有不同類型的輸出。 有些畫筆用純色繪製區域，其他畫筆使用漸變、圖案、圖像或繪圖繪製區域。 下圖顯示了每種不同<xref:System.Windows.Media.Brush>類型的示例。  
  
 ![筆刷類型](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")  
畫筆示例  
  
 大多數可視物件都允許您指定繪製它們的方式。 下表列出了可以使用 的<xref:System.Windows.Media.Brush>一些常見物件和屬性。  
  
|類別|筆刷屬性|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 以下各節介紹不同類型的<xref:System.Windows.Media.Brush>類型，並提供每種類型的示例。  
  
<a name="paintwithsolidcolorbrush"></a>
## <a name="paint-with-a-solid-color"></a>純色塗料  
 A<xref:System.Windows.Media.SolidColorBrush>用固體<xref:System.Windows.Media.Color>繪製區域。 指定<xref:System.Windows.Media.SolidColorBrush.Color%2A><xref:System.Windows.Media.SolidColorBrush>： 的方法有多種，例如，您可以指定其 Alpha、紅色、藍色和綠色通道或使用<xref:System.Windows.Media.Colors>類提供的預定義顏色之一。  
  
 下面的示例使用 來<xref:System.Windows.Media.SolidColorBrush>繪製 的<xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>。 下圖顯示了繪製的矩形。  
  
 ![使用 SolidColorBrush 繪製的矩形](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")  
使用單色筆刷繪製的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 有關該類的詳細資訊，<xref:System.Windows.Media.SolidColorBrush>請參閱[使用純色和漸變概述進行繪畫](painting-with-solid-colors-and-gradients-overview.md)。  
  
<a name="paintwithlineargradientbrush"></a>
## <a name="paint-with-a-linear-gradient"></a>使用線性漸層繪製  
 繪製<xref:System.Windows.Media.LinearGradientBrush>具有線性漸層的區域。 線性漸層會沿著一條線 (漸層軸) 混合兩個或更多色彩。 您可以使用<xref:System.Windows.Media.GradientStop>物件指定漸變中的顏色及其位置。  
  
 下面的示例使用 來<xref:System.Windows.Media.LinearGradientBrush>繪製 的<xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>。 下圖顯示了繪製的矩形。  
  
 ![使用 LinearGradientBrush 繪製的矩形](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")  
使用線性漸層畫筆繪製的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 有關該類的詳細資訊，<xref:System.Windows.Media.LinearGradientBrush>請參閱[使用純色和漸變概述進行繪畫](painting-with-solid-colors-and-gradients-overview.md)。  
  
<a name="paintwithradialgradientbrush"></a>
## <a name="paint-with-a-radial-gradient"></a>使用徑向漸變繪製  
 繪製<xref:System.Windows.Media.RadialGradientBrush>具有徑向漸變的區域。 徑向漸變在一個圓圈上混合兩種或多種顏色。 與類一<xref:System.Windows.Media.LinearGradientBrush>樣，使用<xref:System.Windows.Media.GradientStop>物件指定漸變中的顏色及其位置。  
  
 下面的示例使用 來<xref:System.Windows.Media.RadialGradientBrush>繪製 的<xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>。 下圖顯示了繪製的矩形。  
  
 ![使用 RadialGradientBrush 繪製的矩形](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")  
使用徑向漸層筆刷繪製的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 有關該類的詳細資訊，<xref:System.Windows.Media.RadialGradientBrush>請參閱[使用純色和漸變概述進行繪畫](painting-with-solid-colors-and-gradients-overview.md)。  
  
<a name="paintwithimage"></a>
## <a name="paint-with-an-image"></a>使用圖像繪製  
 用<xref:System.Windows.Media.ImageBrush>油漆區域<xref:System.Windows.Media.ImageSource>。  
  
 下面的示例使用<xref:System.Windows.Media.ImageBrush>來繪製 的<xref:System.Windows.Shapes.Shape.Fill%2A>。 <xref:System.Windows.Shapes.Rectangle> 下圖顯示了繪製的矩形。  
  
 ![ImageBrush 所繪製的矩形](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")  
使用圖像繪製的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 有關該類的詳細資訊，<xref:System.Windows.Media.ImageBrush>請參閱[使用圖像、繪圖和視覺物件進行繪畫](painting-with-images-drawings-and-visuals.md)。  
  
<a name="paintwithdrawing"></a>
## <a name="paint-with-a-drawing"></a>使用繪圖繪製  
 a<xref:System.Windows.Media.DrawingBrush>用 繪製區域<xref:System.Windows.Media.Drawing>。 可以<xref:System.Windows.Media.Drawing>包含形狀、圖像、文本和媒體。  
  
 下面的示例使用 來<xref:System.Windows.Media.DrawingBrush>繪製 的<xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>。 下圖顯示了繪製的矩形。  
  
 ![使用 DrawingBrush 繪製的矩形](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")  
使用繪圖畫筆繪製的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 有關該類的詳細資訊，<xref:System.Windows.Media.DrawingBrush>請參閱[使用圖像、繪圖和視覺物件進行繪畫](painting-with-images-drawings-and-visuals.md)。  
  
<a name="paintwithvisual"></a>
## <a name="paint-with-a-visual"></a>使用視覺物件繪製  
 用<xref:System.Windows.Media.VisualBrush><xref:System.Windows.Media.Visual>物件繪製區域。 Visual 物件的示例包括<xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Page>、<xref:System.Windows.Controls.MediaElement>和 。 還<xref:System.Windows.Media.VisualBrush>使您能夠將應用程式某一部分的內容投影到另一個區域;它對於創建反射效果和放大螢幕部分非常有用。  
  
 下面的示例使用 來<xref:System.Windows.Media.VisualBrush>繪製 的<xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>。 下圖顯示了繪製的矩形。  
  
 ![使用 VisualBrush 繪製的矩形](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")  
使用視覺筆刷繪製的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 有關該類的詳細資訊，<xref:System.Windows.Media.VisualBrush>請參閱[使用圖像、繪圖和視覺物件進行繪畫](painting-with-images-drawings-and-visuals.md)。  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>
## <a name="paint-using-predefined-and-system-brushes"></a>使用預定義和系統畫筆繪製  
 為方便起見，Windows 演示文稿基礎 （WPF） 提供了一組預定義和系統畫筆，可用於繪製物件。  
  
- 有關可用預定義畫筆的清單，請參閱類<xref:System.Windows.Media.Brushes>。 有關演示如何使用預定義的畫筆的示例，請參閱[使用純色繪製區域](how-to-paint-an-area-with-a-solid-color.md)。  
  
- 有關可用系統畫筆的清單，請參閱類<xref:System.Windows.SystemColors>。 例如，請參閱[使用系統畫筆繪製區域](how-to-paint-an-area-with-a-system-brush.md)。  
  
<a name="commonbrushfeatures"></a>
## <a name="common-brush-features"></a>常見畫筆功能  
 <xref:System.Windows.Media.Brush>物件提供可用於<xref:System.Windows.Media.Brush.Opacity%2A>使畫筆透明或部分透明的屬性。 <xref:System.Windows.Media.Brush.Opacity%2A>值 0 使畫筆完全透明，而<xref:System.Windows.Media.Brush.Opacity%2A>值 1 使畫筆完全不透明。 下面的示例使用 屬性<xref:System.Windows.Media.Brush.Opacity%2A>使<xref:System.Windows.Media.SolidColorBrush>25% 不透明。  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 如果畫筆包含部分透明的顏色，則通過乘法與畫筆的不透明度值組合顏色的不透明度值。 例如，如果畫筆的不向性值為 0.5，並且畫筆中使用的顏色也具有 0.5 的不連續值，則輸出顏色的不向性值為 0.25。  
  
> [!NOTE]
> 與使用畫筆<xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType>屬性更改整個元素的不向性相比，更改畫筆的不向性值更有效。  
  
 您可以使用畫筆<xref:System.Windows.Media.Brush.Transform%2A>或<xref:System.Windows.Media.Brush.RelativeTransform%2A>屬性旋轉、縮放、傾斜和翻譯畫筆的內容。 有關詳細資訊，請參閱[筆刷轉換概述](brush-transformation-overview.md)。  
  
 因為它們是<xref:System.Windows.Media.Animation.Animatable>物件，<xref:System.Windows.Media.Brush>因此可以對物件進行動畫處理。 有關詳細資訊，請參閱[動畫概述](animation-overview.md)。  
  
<a name="freezable_features"></a>
### <a name="freezable-features"></a>Freezable 功能  
 由於該<xref:System.Windows.Freezable>類從類繼承，因此<xref:System.Windows.Media.Brush>提供了幾個特殊功能：<xref:System.Windows.Media.Brush>物件可以聲明為[資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)、在多個物件之間共用和克隆。 此外，除所有類型<xref:System.Windows.Media.Brush>外<xref:System.Windows.Media.VisualBrush>，還可以唯讀，以提高性能並使執行緒安全。  
  
 有關<xref:System.Windows.Freezable>物件提供的不同要素的詳細資訊，請參閱[可凍結物件概述](../advanced/freezable-objects-overview.md)。  
  
 有關無法凍結物件的原因<xref:System.Windows.Media.VisualBrush>的詳細資訊，請參閱<xref:System.Windows.Media.VisualBrush>類型頁。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.Brushes>
- [使用純色和漸層繪製的概觀](painting-with-solid-colors-and-gradients-overview.md)
- [使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)
- [Freezable 物件概觀](../advanced/freezable-objects-overview.md)
- [筆刷範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)
- [ImageBrush 範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)
- [VisualBrush 範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush)
- [如何使用主題](brushes-how-to-topics.md)
- [其他效能建議](../advanced/optimizing-performance-other-recommendations.md)
