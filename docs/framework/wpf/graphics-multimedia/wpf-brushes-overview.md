---
title: WPF 筆刷概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
ms.openlocfilehash: 794b17c5a7735201296958580540273879398e9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566596"
---
# <a name="wpf-brushes-overview"></a>WPF 筆刷概觀
螢幕上看見的項目是可見的因為它已繪製的筆刷。 例如，筆刷用來描述的按鈕、 文字、 前景和填滿圖形的背景。 本主題介紹的概念與繪製[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]筆刷，並提供範例。 筆刷可讓您以任何項目 (從簡單的純色到複雜的圖樣和影像集) 繪製 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 物件。  
  
<a name="paintingwithbrush"></a>   
## <a name="painting-with-a-brush"></a>使用筆刷繪製  
 A <xref:System.Windows.Media.Brush> "」 使用繪製區域其輸出。 不同筆刷有不同類型的輸出。 某些筆刷繪製利用純色，其他人使用漸層、 模式、 影像或繪圖區域。 下圖顯示每個不同的範例<xref:System.Windows.Media.Brush>型別。  
  
 ![筆刷類型](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")  
筆刷範例  
  
 大部分的 visual 物件可讓您指定繪製的方式。 下表列出一些常見的物件和屬性，您可以使用<xref:System.Windows.Media.Brush>。  
  
|類別|筆刷屬性|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 下列各節說明不同<xref:System.Windows.Media.Brush>類型，並提供每個範例。  
  
<a name="paintwithsolidcolorbrush"></a>   
## <a name="paint-with-a-solid-color"></a>使用純色繪製  
 A<xref:System.Windows.Media.SolidColorBrush>使用純色繪製區域<xref:System.Windows.Media.Color>。 有多種方式來指定<xref:System.Windows.Media.SolidColorBrush.Color%2A>的<xref:System.Windows.Media.SolidColorBrush>： 例如，您可以在 指定其 alpha、 紅、 藍色以及綠色的通道，或使用預先定義的色彩所提供的其中一個<xref:System.Windows.Media.Colors>類別。  
  
 下列範例會使用<xref:System.Windows.Media.SolidColorBrush>來繪製<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。 下圖顯示繪製的矩形。  
  
 ![使用 SolidColorBrush 繪製的矩形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")  
使用 SolidColorBrush 繪製的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 如需有關<xref:System.Windows.Media.SolidColorBrush>類別，請參閱[使用單色和漸層概觀繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)。  
  
<a name="paintwithlineargradientbrush"></a>   
## <a name="paint-with-a-linear-gradient"></a>使用線性漸層繪製  
 A<xref:System.Windows.Media.LinearGradientBrush>使用線形漸層繪製區域。 線性漸層混合不同線，漸層軸的兩個以上的色彩。 您使用<xref:System.Windows.Media.GradientStop>指定的色彩漸層和它們的位置中的物件。  
  
 下列範例會使用<xref:System.Windows.Media.LinearGradientBrush>來繪製<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。 下圖顯示繪製的矩形。  
  
 ![使用 LinearGradientBrush 繪製的矩形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")  
使用 LinearGradientBrush 繪製的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 如需有關<xref:System.Windows.Media.LinearGradientBrush>類別，請參閱[使用單色和漸層概觀繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)。  
  
<a name="paintwithradialgradientbrush"></a>   
## <a name="paint-with-a-radial-gradient"></a>使用放射狀漸層繪製  
 A<xref:System.Windows.Media.RadialGradientBrush>使用放射狀漸層繪製區域。 放射狀漸層在圓圈混合兩個以上的色彩。 如同<xref:System.Windows.Media.LinearGradientBrush>類別，您使用<xref:System.Windows.Media.GradientStop>指定的色彩漸層和它們的位置中的物件。  
  
 下列範例會使用<xref:System.Windows.Media.RadialGradientBrush>來繪製<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。 下圖顯示繪製的矩形。  
  
 ![使用 RadialGradientBrush 繪製的矩形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")  
使用 RadialGradientBrush 繪製的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 如需有關<xref:System.Windows.Media.RadialGradientBrush>類別，請參閱[使用單色和漸層概觀繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)。  
  
<a name="paintwithimage"></a>   
## <a name="paint-with-an-image"></a>使用影像繪製  
 <xref:System.Windows.Media.ImageBrush>使用繪製區域<xref:System.Windows.Media.ImageSource>。  
  
 下列範例會使用<xref:System.Windows.Media.ImageBrush>來繪製<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。 下圖顯示繪製的矩形。  
  
 ![ImageBrush 所繪製的矩形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")  
使用影像繪製的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 如需有關<xref:System.Windows.Media.ImageBrush>類別，請參閱[使用映像、 繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)。  
  
<a name="paintwithdrawing"></a>   
## <a name="paint-with-a-drawing"></a>使用繪圖繪製  
 A<xref:System.Windows.Media.DrawingBrush>使用繪製區域<xref:System.Windows.Media.Drawing>。 A<xref:System.Windows.Media.Drawing>可包含圖形、 影像、 文字與媒體。  
  
 下列範例會使用<xref:System.Windows.Media.DrawingBrush>來繪製<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。 下圖顯示繪製的矩形。  
  
 ![使用 DrawingBrush 繪製的矩形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")  
使用 DrawingBrush 繪製的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 如需有關<xref:System.Windows.Media.DrawingBrush>類別，請參閱[使用映像、 繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)。  
  
<a name="paintwithvisual"></a>   
## <a name="paint-with-a-visual"></a>使用視覺效果繪製  
 A<xref:System.Windows.Media.VisualBrush>使用繪製區域<xref:System.Windows.Media.Visual>物件。 視覺物件的範例包括<xref:System.Windows.Controls.Button>， <xref:System.Windows.Controls.Page>，和<xref:System.Windows.Controls.MediaElement>。 A<xref:System.Windows.Media.VisualBrush>也可讓您從另一個區域，將應用程式的一個部分的專案內容建立反射效果及放大的螢幕部分很有用。  
  
 下列範例會使用<xref:System.Windows.Media.VisualBrush>來繪製<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。 下圖顯示繪製的矩形。  
  
 ![使用 VisualBrush 繪製的矩形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")  
使用 VisualBrush 繪製的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 如需有關<xref:System.Windows.Media.VisualBrush>類別，請參閱[使用映像、 繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)。  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>   
## <a name="paint-using-predefined-and-system-brushes"></a>使用預先定義和系統筆刷繪製  
 為了方便起見，Windows Presentation Foundation (WPF) 提供一組預先定義，而且系統筆刷可用來繪製物件。  
  
-   如需使用預先定義的筆刷的清單，請參閱<xref:System.Windows.Media.Brushes>類別。 如需示範如何使用預先定義的筆刷的範例，請參閱[使用純色繪製區域](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-solid-color.md)。  
  
-   如需可用的系統筆刷的清單，請參閱<xref:System.Windows.SystemColors>類別。 如需範例，請參閱[使用系統筆刷繪製區域](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)。  
  
<a name="commonbrushfeatures"></a>   
## <a name="common-brush-features"></a>常見的筆刷功能  
 <xref:System.Windows.Media.Brush> 物件提供<xref:System.Windows.Media.Brush.Opacity%2A>可用來做為筆刷透明或透明部分的屬性。 <xref:System.Windows.Media.Brush.Opacity%2A>為 0 的值會使筆刷完全透明，而<xref:System.Windows.Media.Brush.Opacity%2A>完全不透明的值為 1 可筆刷。 下列範例會使用<xref:System.Windows.Media.Brush.Opacity%2A>屬性使<xref:System.Windows.Media.SolidColorBrush>25%不透明。  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 如果筆刷包含部分透明的色彩，色彩的不透明度值會結合到筆刷的不透明度值相乘。 例如，如果筆刷的不透明度值為 0.5，而且也有使用筆刷色彩的不透明度值為 0.5，輸出色彩的不透明值 0.25。  
  
> [!NOTE]
>  若要變更筆刷的不透明值，變更整個項目使用的不透明度比更有效率的<xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType>屬性。  
  
 您可以旋轉和調整其規模、 扭曲，翻譯筆刷的內容使用其<xref:System.Windows.Media.Brush.Transform%2A>或<xref:System.Windows.Media.Brush.RelativeTransform%2A>屬性。 如需詳細資訊，請參閱[筆刷轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)。  
  
 因為它們是<xref:System.Windows.Media.Animation.Animatable>物件<xref:System.Windows.Media.Brush>可以動畫顯示的物件。 如需詳細資訊，請參閱 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
<a name="freezable_features"></a>   
### <a name="freezable-features"></a>Freezable 功能  
 因為它繼承自<xref:System.Windows.Freezable>類別<xref:System.Windows.Media.Brush>類別提供數個特殊功能：<xref:System.Windows.Media.Brush>物件可以宣告為[資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)、 在多個物件之間共用，以及複製。 此外，所有<xref:System.Windows.Media.Brush>類型除了<xref:System.Windows.Media.VisualBrush>可以變成唯讀，以改善效能並進行安全執行緒。  
  
 如需有關所提供的不同功能<xref:System.Windows.Freezable>物件，請參閱[Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
 如需有關為什麼<xref:System.Windows.Media.VisualBrush>物件不能是凍結時，請參閱<xref:System.Windows.Media.VisualBrush>類型 頁面。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.Brush>  
 <xref:System.Windows.Media.Brushes>  
 [使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [筆刷範例](http://go.microsoft.com/fwlink/?LinkID=159973)  
 [ImageBrush 範例](http://go.microsoft.com/fwlink/?LinkID=160005)  
 [VisualBrush 範例](http://go.microsoft.com/fwlink/?LinkID=160049)  
 [HOW-TO 主題](../../../../docs/framework/wpf/graphics-multimedia/brushes-how-to-topics.md)  
 [其他效能建議](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
