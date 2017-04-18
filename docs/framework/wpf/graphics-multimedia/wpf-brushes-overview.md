---
title: "WPF 筆刷概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "筆刷, 關於筆刷"
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# WPF 筆刷概觀
您在螢幕上看見的項目之所以可見，是因為它們都是以筆刷繪製的。  例如，筆刷可用以描述按鈕的背景 \(Background\)、文字的前景 \(Foreground\) 及圖案的填滿。  本主題介紹以 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 筆刷繪製的概念並提供範例。  筆刷可以讓您以任何項目 \(從簡單的純色到複雜的圖樣和影像集\) 繪製[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 物件。  
  
<a name="paintingwithbrush"></a>   
## 使用筆刷繪製  
 <xref:System.Windows.Media.Brush> 會以其輸出結果來「繪製」區域。  不同的筆刷有不同類型的輸出。  某些筆刷會以純色繪製區域，其他筆刷則會以漸層、圖樣、影像或繪圖來繪製區域。  下圖顯示每個不同 <xref:System.Windows.Media.Brush> 型別的範例。  
  
 ![筆刷類型](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brushtypes.png "graphicsmm\_brushtypes")  
筆刷範例  
  
 大多數視覺物件都可以讓您指定繪製它們的方式。  下表列出一些您可以搭配 <xref:System.Windows.Media.Brush> 使用的常見物件和屬性。  
  
|類別|筆刷屬性|  
|--------|----------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 下列各節說明不同的 <xref:System.Windows.Media.Brush> 型別，並提供各個型別的範例。  
  
<a name="paintwithsolidcolorbrush"></a>   
## 使用純色繪製  
 <xref:System.Windows.Media.SolidColorBrush> 會使用純色的 <xref:System.Windows.Media.Color> 繪製區域。  有各種方法可以指定 <xref:System.Windows.Media.SolidColorBrush> 的 <xref:System.Windows.Media.SolidColorBrush.Color%2A>：例如，您可以指定其 Alpha、紅色、藍色及綠色色頻，或使用 <xref:System.Windows.Media.Colors> 類別所提供的其中一個預先定義色彩。  
  
 下列範例是使用 <xref:System.Windows.Media.SolidColorBrush> 來繪製 <xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.Shapes.Shape.Fill%2A>。  下圖顯示繪製後的矩形。  
  
 ![使用 SolidColorBrush 繪製的矩形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm\_brush\_ovw\_solidcolorbrush")  
使用 SolidColorBrush 繪製的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 如需 <xref:System.Windows.Media.SolidColorBrush> 類別的詳細資訊，請參閱[使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)。  
  
<a name="paintwithlineargradientbrush"></a>   
## 使用線形漸層繪製  
 <xref:System.Windows.Media.LinearGradientBrush> 會使用線形漸層繪製區域。  線形漸層會沿著某個線條 \(漸層軸\) 混合兩種以上的色彩。  您可以使用 <xref:System.Windows.Media.GradientStop> 物件指定漸層中的色彩及其位置。  
  
 下列範例是使用 <xref:System.Windows.Media.LinearGradientBrush> 來繪製 <xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.Shapes.Shape.Fill%2A>。  下圖顯示繪製後的矩形。  
  
 ![使用 LinearGradientBrush 繪製的矩形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-lineargradientbrush.png "graphicsmm\_brush\_ovw\_lineargradientbrush")  
使用 LinearGradientBrush 繪製的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 如需 <xref:System.Windows.Media.LinearGradientBrush> 類別的詳細資訊，請參閱[使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)。  
  
<a name="paintwithradialgradientbrush"></a>   
## 使用放射狀漸層繪製  
 <xref:System.Windows.Media.RadialGradientBrush> 會使用放射狀漸層繪製區域。  放射狀漸層會在圓圈中混合兩種以上的色彩。  如同 <xref:System.Windows.Media.LinearGradientBrush> 類別，您可以使用 <xref:System.Windows.Media.GradientStop> 物件指定漸層中的色彩及其位置。  
  
 下列範例是使用 <xref:System.Windows.Media.RadialGradientBrush> 來繪製 <xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.Shapes.Shape.Fill%2A>。  下圖顯示繪製後的矩形。  
  
 ![使用 RadialGradientBrush 繪製的矩形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-radialgradientbrush.png "graphicsmm\_brush\_ovw\_radialgradientbrush")  
使用 RadialGradientBrush 繪製的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 如需 <xref:System.Windows.Media.RadialGradientBrush> 類別的詳細資訊，請參閱[使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)。  
  
<a name="paintwithimage"></a>   
## 使用影像繪製  
 <xref:System.Windows.Media.ImageBrush> 會使用 <xref:System.Windows.Media.ImageSource> 繪製區域。  
  
 下列範例是使用 <xref:System.Windows.Media.ImageBrush> 來繪製 <xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.Shapes.Shape.Fill%2A>。  下圖顯示繪製後的矩形。  
  
 ![ImageBrush 所繪製的矩形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-imagebrush.png "graphicsmm\_brush\_ovw\_imagebrush")  
使用影像繪製的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 如需 <xref:System.Windows.Media.ImageBrush> 類別的詳細資訊，請參閱[使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)。  
  
<a name="paintwithdrawing"></a>   
## 使用繪圖繪製  
 <xref:System.Windows.Media.DrawingBrush> 會使用 <xref:System.Windows.Media.Drawing> 繪製區域。  <xref:System.Windows.Media.Drawing> 可以包含圖案、影像、文字及媒體。  
  
 下列範例是使用 <xref:System.Windows.Media.DrawingBrush> 來繪製 <xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.Shapes.Shape.Fill%2A>。  下圖顯示繪製後的矩形。  
  
 ![使用 DrawingBrush 繪製的矩形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-drawingbrush.png "graphicsmm\_brush\_ovw\_drawingbrush")  
使用 DrawingBrush 繪製的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 如需 <xref:System.Windows.Media.DrawingBrush> 類別的詳細資訊，請參閱[使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)。  
  
<a name="paintwithvisual"></a>   
## 使用視覺效果繪製  
 <xref:System.Windows.Media.VisualBrush> 會使用 <xref:System.Windows.Media.Visual> 物件繪製區域。  Visual 物件的範例包括 <xref:System.Windows.Controls.Button>、<xref:System.Windows.Controls.Page> 及 <xref:System.Windows.Controls.MediaElement>。  <xref:System.Windows.Media.VisualBrush> 也可以讓您將應用程式某部分的內容投射到另一個區域，這在建立倒影效果和放大螢幕某些部分時相當有用。  
  
 下列範例是使用 <xref:System.Windows.Media.VisualBrush> 來繪製 <xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.Shapes.Shape.Fill%2A>。  下圖顯示繪製後的矩形。  
  
 ![使用 VisualBrush 繪製的矩形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-visualbrush.png "graphicsmm\_brush\_ovw\_visualbrush")  
使用 VisualBrush 繪製的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 如需 <xref:System.Windows.Media.VisualBrush> 類別的詳細資訊，請參閱[使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)。  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>   
## 使用預先定義的筆刷和系統筆刷繪製  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 提供一組預先定義的筆刷和系統筆刷，方便您快速繪製物件。  
  
-   如需可用之預先定義筆刷的清單，請參閱 <xref:System.Windows.Media.Brushes> 類別。  如需如何使用預先定義筆刷的範例，請參閱 [使用純色繪製區域](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-solid-color.md)。  
  
-   如需可用的系統筆刷的清單。請參閱 <xref:System.Windows.SystemColors> 類別。  如需範例，請參閱 [使用系統筆刷繪製區域](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)。  
  
<a name="commonbrushfeatures"></a>   
## 常見筆刷功能  
 <xref:System.Windows.Media.Brush> 物件提供 <xref:System.Windows.Media.Brush.Opacity%2A> 屬性，可以用來使筆刷變成透明或部分透明。  <xref:System.Windows.Media.Brush.Opacity%2A> 值為 0 會讓筆刷完全透明，<xref:System.Windows.Media.Brush.Opacity%2A> 值為 1 則會讓筆刷完全不透明。  下列範例是使用 <xref:System.Windows.Media.Brush.Opacity%2A> 屬性讓 <xref:System.Windows.Media.SolidColorBrush> 變成 25% 不透明。  
  
 [!code-xml[BrushOverviewExamples_snip#OpacityExample1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 如果筆刷包含部分透明的色彩，色彩的不透明值會以乘法的方式與筆刷的不透明值結合。  例如，如果筆刷的不透明值為 0.5，且筆刷中使用的色彩的不透明值也是 0.5，則輸出色彩的不透明值就會是 0.25。  
  
> [!NOTE]
>  變更筆刷的不透明值比使用項目的 <xref:System.Windows.UIElement.Opacity%2A?displayProperty=fullName> 屬性變更整個項目的不透明值更有效率。  
  
 您可以使用筆刷的 <xref:System.Windows.Media.Brush.Transform%2A> 或 <xref:System.Windows.Media.Brush.RelativeTransform%2A> 屬性，旋轉、縮放、扭曲及平移筆刷的內容。  如需詳細資訊，請參閱 [筆刷轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)。  
  
 因為 <xref:System.Windows.Media.Brush> 物件是 <xref:System.Windows.Media.Animation.Animatable> 物件，所以可以顯示動畫。  如需詳細資訊，請參閱 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
<a name="freezable_features"></a>   
### Freezable 功能  
 <xref:System.Windows.Media.Brush> 類別繼承自 <xref:System.Windows.Freezable> 類別，因此可以提供數項特殊功能：<xref:System.Windows.Media.Brush> 物件可宣告為[資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)、供多個物件共用和複製。  此外，除了 <xref:System.Windows.Media.VisualBrush> 之外的所有 <xref:System.Windows.Media.Brush> 型別都可以變成唯讀以改善效能並成為安全執行緒 \(Thread\-Safe\) 的。  
  
 如需 <xref:System.Windows.Freezable> 物件提供之不同功能的詳細資訊，請參閱 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
 如需 <xref:System.Windows.Media.VisualBrush> 物件為何無法凍結的詳細資訊，請參閱 <xref:System.Windows.Media.VisualBrush> 型別頁面。  
  
## 請參閱  
 <xref:System.Windows.Media.Brush>   
 <xref:System.Windows.Media.Brushes>   
 [使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)   
 [使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)   
 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [筆刷範例](http://go.microsoft.com/fwlink/?LinkID=159973)   
 [ImageBrush 範例](http://go.microsoft.com/fwlink/?LinkID=160005)   
 [VisualBrush 範例](http://go.microsoft.com/fwlink/?LinkID=160049)   
 [HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/brushes-how-to-topics.md)   
 [其他效能建議](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)