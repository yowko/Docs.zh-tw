---
title: WPF 筆刷概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
ms.openlocfilehash: 8a1d05ad48ce75ce67d21d5a4d508015fea879b2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458633"
---
# <a name="wpf-brushes-overview"></a>WPF 筆刷概觀
螢幕上顯示的所有專案都是可見的，因為它是由筆刷繪製。 例如，筆刷是用來描述按鈕的背景、文字的前景，以及圖形的填滿。 本主題介紹使用 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 筆刷繪製的概念，並提供範例。 筆刷可讓您以任何項目 (從簡單的純色到複雜的圖樣和影像集) 繪製 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 物件。  
  
<a name="paintingwithbrush"></a>   
## <a name="painting-with-a-brush"></a>使用筆刷繪製  
 <xref:System.Windows.Media.Brush> 「繪製」含有其輸出的區域。 不同的筆刷具有不同類型的輸出。 有些筆刷會以純色繪製區域，其他則具有漸層、圖樣、影像或繪圖。 下圖顯示每個不同 <xref:System.Windows.Media.Brush> 類型的範例。  
  
 ![筆刷類型](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")  
筆刷範例  
  
 大部分的視覺物件都可讓您指定其繪製方式。 下表列出一些常用的物件和屬性，您可以使用 <xref:System.Windows.Media.Brush>。  
  
|執行個體|筆刷屬性|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>、 <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>、 <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>、 <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 下列各節說明不同的 <xref:System.Windows.Media.Brush> 型別，並提供每個類型的範例。  
  
<a name="paintwithsolidcolorbrush"></a>   
## <a name="paint-with-a-solid-color"></a>以純色繪製  
 <xref:System.Windows.Media.SolidColorBrush> 繪製具有純色 <xref:System.Windows.Media.Color>的區域。 有各種方式可以指定 <xref:System.Windows.Media.SolidColorBrush>的 <xref:System.Windows.Media.SolidColorBrush.Color%2A>：例如，您可以指定其 Alpha、紅色、藍色和綠色的通道，或使用 <xref:System.Windows.Media.Colors> 類別所提供的其中一個預先定義色彩。  
  
 下列範例會使用 <xref:System.Windows.Media.SolidColorBrush> 來繪製 <xref:System.Windows.Shapes.Rectangle>的 <xref:System.Windows.Shapes.Shape.Fill%2A>。 下圖顯示繪製的矩形。  
  
 ![使用 SolidColorBrush 繪製的矩形](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")  
使用 SolidColorBrush 繪製的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 如需有關 <xref:System.Windows.Media.SolidColorBrush> 類別的詳細資訊，請參閱[使用純色和漸層繪製的色彩總覽](painting-with-solid-colors-and-gradients-overview.md)。  
  
<a name="paintwithlineargradientbrush"></a>   
## <a name="paint-with-a-linear-gradient"></a>以線性漸層繪製  
 <xref:System.Windows.Media.LinearGradientBrush> 會以線性漸層繪製區域。 線性漸層會將兩個或多個色彩橫跨一條線，也就是梯度軸。 您可以使用 <xref:System.Windows.Media.GradientStop> 物件來指定漸層中的色彩和其位置。  
  
 下列範例會使用 <xref:System.Windows.Media.LinearGradientBrush> 來繪製 <xref:System.Windows.Shapes.Rectangle>的 <xref:System.Windows.Shapes.Shape.Fill%2A>。 下圖顯示繪製的矩形。  
  
 ![使用 LinearGradientBrush 繪製的矩形](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")  
使用 LinearGradientBrush 繪製的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 如需有關 <xref:System.Windows.Media.LinearGradientBrush> 類別的詳細資訊，請參閱[使用純色和漸層繪製的色彩總覽](painting-with-solid-colors-and-gradients-overview.md)。  
  
<a name="paintwithradialgradientbrush"></a>   
## <a name="paint-with-a-radial-gradient"></a>使用放射狀漸層繪製  
 <xref:System.Windows.Media.RadialGradientBrush> 繪製具有放射漸層的區域。 放射狀漸層會將兩個或多個色彩混合在一個圓形上。 如同 <xref:System.Windows.Media.LinearGradientBrush> 類別，您可以使用 <xref:System.Windows.Media.GradientStop> 物件來指定漸層中的色彩和其位置。  
  
 下列範例會使用 <xref:System.Windows.Media.RadialGradientBrush> 來繪製 <xref:System.Windows.Shapes.Rectangle>的 <xref:System.Windows.Shapes.Shape.Fill%2A>。 下圖顯示繪製的矩形。  
  
 ![使用 RadialGradientBrush 繪製的矩形](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")  
使用 RadialGradientBrush 繪製的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 如需有關 <xref:System.Windows.Media.RadialGradientBrush> 類別的詳細資訊，請參閱[使用純色和漸層繪製的色彩總覽](painting-with-solid-colors-and-gradients-overview.md)。  
  
<a name="paintwithimage"></a>   
## <a name="paint-with-an-image"></a>使用影像繪製  
 <xref:System.Windows.Media.ImageBrush> 繪製具有 <xref:System.Windows.Media.ImageSource>的區域。  
  
 下列範例會使用 <xref:System.Windows.Media.ImageBrush> 來繪製 <xref:System.Windows.Shapes.Rectangle>的 <xref:System.Windows.Shapes.Shape.Fill%2A>。 下圖顯示繪製的矩形。  
  
 ![由 ImageBrush 繪製的矩形](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")  
使用影像繪製的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 如需 <xref:System.Windows.Media.ImageBrush> 類別的詳細資訊，請參閱[使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)。  
  
<a name="paintwithdrawing"></a>   
## <a name="paint-with-a-drawing"></a>使用繪圖繪製  
 <xref:System.Windows.Media.DrawingBrush> 繪製具有 <xref:System.Windows.Media.Drawing>的區域。 <xref:System.Windows.Media.Drawing> 可以包含圖形、影像、文字和媒體。  
  
 下列範例會使用 <xref:System.Windows.Media.DrawingBrush> 來繪製 <xref:System.Windows.Shapes.Rectangle>的 <xref:System.Windows.Shapes.Shape.Fill%2A>。 下圖顯示繪製的矩形。  
  
 ![使用 DrawingBrush 繪製的矩形](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")  
使用 DrawingBrush 繪製的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 如需 <xref:System.Windows.Media.DrawingBrush> 類別的詳細資訊，請參閱[使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)。  
  
<a name="paintwithvisual"></a>   
## <a name="paint-with-a-visual"></a>使用視覺效果繪製  
 <xref:System.Windows.Media.VisualBrush> 使用 <xref:System.Windows.Media.Visual> 物件繪製區域。 視覺物件的範例包括 <xref:System.Windows.Controls.Button>、<xref:System.Windows.Controls.Page>和 <xref:System.Windows.Controls.MediaElement>。 <xref:System.Windows.Media.VisualBrush> 也可讓您從應用程式的某個部分將內容投影到另一個區域;它非常適合用來建立反映效果和螢幕的放大鏡部分。  
  
 下列範例會使用 <xref:System.Windows.Media.VisualBrush> 來繪製 <xref:System.Windows.Shapes.Rectangle>的 <xref:System.Windows.Shapes.Shape.Fill%2A>。 下圖顯示繪製的矩形。  
  
 ![使用 VisualBrush 繪製的矩形](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")  
使用 VisualBrush 繪製的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 如需 <xref:System.Windows.Media.VisualBrush> 類別的詳細資訊，請參閱[使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)。  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>   
## <a name="paint-using-predefined-and-system-brushes"></a>使用預先定義和系統筆刷繪製  
 為了方便起見，Windows Presentation Foundation （WPF）提供一組預先定義和可用來繪製物件的系統筆刷。  
  
- 如需可用預先定義的筆刷清單，請參閱 <xref:System.Windows.Media.Brushes> 類別。 如需顯示如何使用預先定義筆刷的範例，請參閱[使用純色繪製區域](how-to-paint-an-area-with-a-solid-color.md)。  
  
- 如需可用系統筆刷的清單，請參閱 <xref:System.Windows.SystemColors> 類別。 如需範例，請參閱[使用系統筆刷繪製區域](how-to-paint-an-area-with-a-system-brush.md)。  
  
<a name="commonbrushfeatures"></a>   
## <a name="common-brush-features"></a>一般筆刷功能  
 <xref:System.Windows.Media.Brush> 物件會提供可用來將筆刷透明化或部分透明的 <xref:System.Windows.Media.Brush.Opacity%2A> 屬性。 <xref:System.Windows.Media.Brush.Opacity%2A> 值0會使筆刷完全透明，而 <xref:System.Windows.Media.Brush.Opacity%2A> 值1則會使筆刷完全不透明。 下列範例會使用 <xref:System.Windows.Media.Brush.Opacity%2A> 屬性，使 <xref:System.Windows.Media.SolidColorBrush> 25% 不透明。  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 如果筆刷包含部分透明的色彩，則色彩的不透明度值會透過乘法與筆刷的不透明度值結合。 例如，如果筆刷的不透明度值為0.5，而筆刷中使用的色彩也具有不透明度值0.5，則輸出色彩會有不透明度值0.25。  
  
> [!NOTE]
> 變更筆刷的不透明度值會比較有效率，而不是使用其 <xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType> 屬性來變更整個專案的不透明度。  
  
 您可以使用其 <xref:System.Windows.Media.Brush.Transform%2A> 或 <xref:System.Windows.Media.Brush.RelativeTransform%2A> 屬性來旋轉、縮放、扭曲和轉譯筆刷的內容。 如需詳細資訊，請參閱[筆刷轉換總覽](brush-transformation-overview.md)。  
  
 因為它們是 <xref:System.Windows.Media.Animation.Animatable> 物件，<xref:System.Windows.Media.Brush> 物件可以進行動畫。 如需詳細資訊，請參閱 [動畫概觀](animation-overview.md)。  
  
<a name="freezable_features"></a>   
### <a name="freezable-features"></a>Freezable 功能  
 因為它繼承自 <xref:System.Windows.Freezable> 類別，所以 <xref:System.Windows.Media.Brush> 類別提供數個特殊功能： <xref:System.Windows.Media.Brush> 物件可以宣告為[資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)、在多個物件之間共用，以及複製。 此外，除了 <xref:System.Windows.Media.VisualBrush> 以外的所有 <xref:System.Windows.Media.Brush> 類型都可以設為唯讀，以改善效能並使其成為安全線程。  
  
 如需 <xref:System.Windows.Freezable> 物件所提供之不同功能的詳細資訊，請參閱可[凍結物件總覽](../advanced/freezable-objects-overview.md)。  
  
 如需為何無法凍結 <xref:System.Windows.Media.VisualBrush> 物件的詳細資訊，請參閱 <xref:System.Windows.Media.VisualBrush> 類型 頁面。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.Brushes>
- [使用純色和漸層繪製的概觀](painting-with-solid-colors-and-gradients-overview.md)
- [使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)
- [Freezable 物件概觀](../advanced/freezable-objects-overview.md)
- [筆刷範例](https://go.microsoft.com/fwlink/?LinkID=159973)
- [ImageBrush 範例](https://go.microsoft.com/fwlink/?LinkID=160005)
- [VisualBrush 範例](https://go.microsoft.com/fwlink/?LinkID=160049)
- [「如何」主題](brushes-how-to-topics.md)
- [其他效能建議](../advanced/optimizing-performance-other-recommendations.md)
