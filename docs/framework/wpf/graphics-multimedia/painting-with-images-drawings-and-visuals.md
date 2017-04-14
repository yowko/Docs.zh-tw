---
title: "使用影像、繪圖和視覺效果繪製 | Microsoft Docs"
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
  - "筆刷, 以繪圖繪製"
  - "筆刷, 以影像繪製"
  - "筆刷, 使用視覺效果繪製"
  - "使用視覺效果繪製"
  - "繪圖, 使用繪圖"
  - "繪圖, 使用影像"
ms.assetid: 779aac3f-8d41-49d8-8130-768244aa2240
caps.latest.revision: 28
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 27
---
# 使用影像、繪圖和視覺效果繪製
本主題說明如何使用 <xref:System.Windows.Media.ImageBrush>、<xref:System.Windows.Media.DrawingBrush> 與 <xref:System.Windows.Media.VisualBrush> 物件，以影像 <xref:System.Windows.Media.Drawing> 或 <xref:System.Windows.Media.Visual> 繪製區域。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="prereqs"></a>   
## 必要條件  
 若要了解本主題，您應該熟悉 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 所提供的不同筆刷類型及其基本功能。  如需簡介，請參閱 [WPF 筆刷概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md)。  
  
<a name="image"></a>   
## 使用影像繪製區域  
 <xref:System.Windows.Media.ImageBrush> 可以使用 <xref:System.Windows.Media.ImageSource> 來繪製區域。  最常搭配 <xref:System.Windows.Media.ImageBrush> 使用的 <xref:System.Windows.Media.ImageSource> 類型是 <xref:System.Windows.Media.Imaging.BitmapImage>，它可以描述點陣圖形。  使用 <xref:System.Windows.Media.DrawingImage> 可讓您以 <xref:System.Windows.Media.Drawing> 物件進行繪製，但使用 <xref:System.Windows.Media.DrawingBrush> 比較簡單。  如需 <xref:System.Windows.Media.ImageSource> 物件的詳細資訊，請參閱[影像處理概觀](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)。  
  
 若要使用 <xref:System.Windows.Media.ImageBrush> 進行繪製，請建立 <xref:System.Windows.Media.Imaging.BitmapImage> 並用它載入點陣圖內容。  接著，請使用 <xref:System.Windows.Media.Imaging.BitmapImage> 來設定 <xref:System.Windows.Media.ImageBrush> 的 <xref:System.Windows.Media.ImageBrush.ImageSource%2A> 屬性。  最後，將 <xref:System.Windows.Media.ImageBrush> 套用至您要繪製的物件。  在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中，您也可以使用要載入之影像的路徑，設定 <xref:System.Windows.Media.ImageBrush> 的 <xref:System.Windows.Media.ImageBrush.ImageSource%2A> 屬性。  
  
 就像所有 <xref:System.Windows.Media.Brush> 物件，<xref:System.Windows.Media.ImageBrush> 可以用於繪製圖案、面板、控制項與文字等物件。  下圖顯示可以使用 <xref:System.Windows.Media.ImageBrush> 達成的部分效果。  
  
 ![ImageBrush 輸出範例](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-imagebrushexamples.png "wcpsdk\_mmgraphics\_imagebrushexamples")  
ImageBrush 所繪製的物件  
  
 根據預設，<xref:System.Windows.Media.ImageBrush> 會自動縮放其影像的大小以完全填滿繪製的區域，此時如果繪製的區域與影像所使用的外觀比例不相同，影像可能會變形。  您可以將 <xref:System.Windows.Media.TileBrush.Stretch%2A> 屬性的預設值 <xref:System.Windows.Media.Stretch> 變更為 <xref:System.Windows.Media.Stretch>、<xref:System.Windows.Media.Stretch> 或 <xref:System.Windows.Media.Stretch>，以改變這個行為。  由於 <xref:System.Windows.Media.ImageBrush> 是一種 <xref:System.Windows.Media.TileBrush>，因此您可以確切指定影像筆刷填滿輸出區域的方式，甚至建立圖樣。  如需進階 <xref:System.Windows.Media.TileBrush> 功能的詳細資訊，請參閱 [TileBrush 概觀](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)。  
  
<a name="fillingpanelwithimage"></a>   
## 範例：使用點陣圖影像繪製物件  
 下列範例是使用 <xref:System.Windows.Media.ImageBrush> 來繪製 <xref:System.Windows.Controls.Canvas> 的 <xref:System.Windows.Controls.Panel.Background%2A>。  
  
 [!code-xml[BrushOverviewExamples_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/ImageBrushExample.xaml#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/ImageBrushExample.cs#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/imagebrushexample.vb#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
<a name="drawingbrushintro"></a>   
## 使用繪圖繪製區域  
 <xref:System.Windows.Media.DrawingBrush> 可讓您使用圖案、文字、影像與視訊來繪製區域。  繪圖筆刷內的圖案本身就可以用純色、漸層、影像或其他 <xref:System.Windows.Media.DrawingBrush> 來繪製。  下圖示範 <xref:System.Windows.Media.DrawingBrush> 的一些用法。  
  
 ![DrawingBrush 輸出範例](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-drawingbrushexamples.png "wcpsdk\_mmgraphics\_drawingbrushexamples")  
DrawingBrush 所繪製的物件  
  
 <xref:System.Windows.Media.DrawingBrush> 可以使用 <xref:System.Windows.Media.Drawing> 物件繪製區域。  <xref:System.Windows.Media.Drawing> 物件可描繪可見內容，例如圖案、點陣圖、視訊或文字行。  不同類型的繪圖可描繪不同類型的內容。  以下列出不同類型的繪圖物件。  
  
-   <xref:System.Windows.Media.GeometryDrawing> – 繪製圖案。  
  
-   <xref:System.Windows.Media.ImageDrawing> – 繪製影像。  
  
-   <xref:System.Windows.Media.GlyphRunDrawing> – 繪製文字。  
  
-   <xref:System.Windows.Media.VideoDrawing> – 播放音訊檔或視訊檔。  
  
-   <xref:System.Windows.Media.DrawingGroup> – 繪製其他繪圖。  您可以使用繪圖群組，將其他繪圖結合為單一複合繪圖。  
  
 如需 <xref:System.Windows.Media.Drawing> 物件的詳細資訊，請參閱[繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)。  
  
 就像 <xref:System.Windows.Media.ImageBrush> 一樣，<xref:System.Windows.Media.DrawingBrush> 會自動縮放其 <xref:System.Windows.Media.DrawingBrush.Drawing%2A> 以填滿其輸出區域。  您可以變更 <xref:System.Windows.Media.TileBrush.Stretch%2A> 屬性的預設設定 <xref:System.Windows.Media.Stretch>，以覆寫這個行為。  如需詳細資訊，請參閱 <xref:System.Windows.Media.TileBrush.Stretch%2A> 屬性 \(Property\)。  
  
<a name="fillingareawithdrawingbrushexample"></a>   
## 範例：使用繪圖繪製物件  
 下列範例顯示如何使用含有三個橢圓形的繪圖來繪製物件。  <xref:System.Windows.Media.GeometryDrawing> 是用以描述橢圓形。  
  
 [!code-xml[BrushOverviewExamples_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/DrawingBrushExample.xaml#graphicsmmdrawingbrushasbuttonbackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/DrawingBrushExample.cs#graphicsmmdrawingbrushasbuttonbackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/drawingbrushexample.vb#graphicsmmdrawingbrushasbuttonbackgroundexample1)]  
  
<a name="visualbrushsection"></a>   
## 使用視覺效果繪製區域  
 <xref:System.Windows.Media.VisualBrush> 是所有筆刷中功能最多樣化而強大的一種，可以使用 <xref:System.Windows.Media.Visual> 繪製區域。  <xref:System.Windows.Media.Visual> 是一種低階的圖形類型，可做為多種實用圖形元件的祖系。  例如，<xref:System.Windows.Window>、<xref:System.Windows.FrameworkElement> 與 <xref:System.Windows.Controls.Control> 類別都是一種 <xref:System.Windows.Media.Visual> 物件。  透過 <xref:System.Windows.Media.VisualBrush>，您可以使用絕大多數的 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 圖形物件繪製區域。  
  
> [!NOTE]
>  雖然 <xref:System.Windows.Media.VisualBrush> 是一種 <xref:System.Windows.Freezable> 物件，但它在其 <xref:System.Windows.Media.VisualBrush.Visual%2A> 屬性是設為 `null` 以外的值時，將無法凍結 \(設為唯讀\)。  
  
 有兩種方式可以指定 <xref:System.Windows.Media.VisualBrush> 的 <xref:System.Windows.Media.VisualBrush.Visual%2A> 內容。  
  
-   建立新的 <xref:System.Windows.Media.Visual>，並用它來設定 <xref:System.Windows.Media.VisualBrush> 的 <xref:System.Windows.Media.VisualBrush.Visual%2A> 屬性。  例如，請參閱稍後的[範例：使用視覺效果繪製物件](#examplevisualbrush1)一節。  
  
-   使用現有的 <xref:System.Windows.Media.Visual>，它會建立目標 <xref:System.Windows.Media.Visual> 的重複影像。  然後您就可以使用 <xref:System.Windows.Media.VisualBrush> 建立有趣的效果，例如反映與放大。  如需範例，請參閱[範例：建立反映](#examplevisualbrush2)一節。  
  
 當您為 <xref:System.Windows.Media.VisualBrush> 定義新的 <xref:System.Windows.Media.VisualBrush.Visual%2A>，且 <xref:System.Windows.Media.Visual> 為 <xref:System.Windows.UIElement> \(如面板或控制項\) 時，如果 <xref:System.Windows.Media.VisualBrush.AutoLayoutContent%2A> 屬性設為 `true`，配置系統即會在 <xref:System.Windows.UIElement> 及其子項目上執行。  但是根 <xref:System.Windows.UIElement> 會獨立於系統的其他部分之外：樣式與外部配置無發法穿透此界限。  因此，您應該明確指定根 <xref:System.Windows.UIElement> 的大小，因為它唯一的父系為 <xref:System.Windows.Media.VisualBrush>，所以它無法根據繪製的區域自動調整本身的大小。  如需 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中之配置的詳細資訊，請參閱[配置](../../../../docs/framework/wpf/advanced/layout.md)。  
  
 就像 <xref:System.Windows.Media.ImageBrush> 與 <xref:System.Windows.Media.DrawingBrush> 一樣，<xref:System.Windows.Media.VisualBrush> 也會自動縮放其內容以填滿其輸出區域。  您可以變更 <xref:System.Windows.Media.TileBrush.Stretch%2A> 屬性的預設設定 <xref:System.Windows.Media.Stretch>，以覆寫這個行為。  如需詳細資訊，請參閱 <xref:System.Windows.Media.TileBrush.Stretch%2A> 屬性 \(Property\)。  
  
<a name="examplevisualbrush1"></a>   
## 範例：使用視覺效果繪製物件  
 下列範例會使用多個控制項與一個面板來繪製矩形。  
  
 [!code-xml[BrushOverviewExamples_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/VisualBrushExample.xaml#graphicsmmvisualbrushasrectanglebackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/VisualBrushExample.cs#graphicsmmvisualbrushasrectanglebackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/visualbrushexample.vb#graphicsmmvisualbrushasrectanglebackgroundexample1)]  
  
<a name="examplevisualbrush2"></a>   
## 範例：建立反映  
 前述範例顯示了如何建立要做為背景 \(Background\) 的新 <xref:System.Windows.Media.Visual>。  您也可以使用 <xref:System.Windows.Media.VisualBrush> 來顯示現有的視覺效果；這項功能可讓您產生有趣的視覺效果，例如反映與放大。  下列範例會使用 <xref:System.Windows.Media.VisualBrush> 來建立包含幾個項目之 <xref:System.Windows.Controls.Border> 的反映。  下圖顯示的是這個範例產生的輸出。  
  
 ![反映後的 Visual 物件](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.png "graphicsmm\_visualbrush\_reflection\_small")  
反映的 Visual 物件  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 如需示範如何放大部分螢幕以及如何建立反映的其他範例，請參閱 [VisualBrush 範例](http://go.microsoft.com/fwlink/?LinkID=160049) \(英文\)。  
  
<a name="tilebrush"></a>   
## TileBrush 功能  
 <xref:System.Windows.Media.ImageBrush>、<xref:System.Windows.Media.DrawingBrush> 和 <xref:System.Windows.Media.VisualBrush> 為 <xref:System.Windows.Media.TileBrush> 物件的型別。  <xref:System.Windows.Media.TileBrush> 物件可讓您更充分掌控使用影像、繪圖或視覺資料繪製區域的方式。  例如，您可以用構成圖樣的一系列影像並排顯示來繪製區域，而不是只以單一自動縮放的影像來繪製區域。  
  
 <xref:System.Windows.Media.TileBrush> 有三個主要的元件：內容、並排顯示與輸出區域。  
  
 ![TileBrush 元件](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk\_mmgraphics\_defaultcontentprojection2")  
具有單一並排顯示之 TileBrush 的元件  
  
 ![並排顯示之 TileBrush 的元件](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tiledprojection.png "graphicsmm\_tiledprojection")  
具有多個並排顯示之 TileBrush 的元件  
  
 如需 <xref:System.Windows.Media.TileBrush> 物件之並排顯示功能的詳細資訊，請參閱 [TileBrush 概觀](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)。  
  
## 請參閱  
 <xref:System.Windows.Media.ImageBrush>   
 <xref:System.Windows.Media.DrawingBrush>   
 <xref:System.Windows.Media.VisualBrush>   
 <xref:System.Windows.Media.TileBrush>   
 [TileBrush 概觀](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)   
 [WPF 筆刷概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md)   
 [影像處理概觀](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)   
 [繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)   
 [不透明遮罩概觀](../../../../docs/framework/wpf/graphics-multimedia/opacity-masks-overview.md)   
 [WPF 圖形轉譯概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)   
 [ImageBrush 範例](http://go.microsoft.com/fwlink/?LinkID=160005)   
 [VisualBrush Sample](http://go.microsoft.com/fwlink/?LinkID=160049)