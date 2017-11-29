---
title: "使用影像、繪圖和視覺效果繪製"
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
- brushes [WPF], painting with drawings
- painting [WPF], with drawings
- painting [WPF], with images
- painting with visuals [WPF]
- brushes [WPF], painting with images
- brushes [WPF], painting with visuals
ms.assetid: 779aac3f-8d41-49d8-8130-768244aa2240
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 16c3184c329fa83ddf091326c97d6faf2e2c88f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="painting-with-images-drawings-and-visuals"></a>使用影像、繪圖和視覺效果繪製
本主題描述如何使用<xref:System.Windows.Media.ImageBrush>， <xref:System.Windows.Media.DrawingBrush>，和<xref:System.Windows.Media.VisualBrush>物件以使用影像繪製區域<xref:System.Windows.Media.Drawing>，或<xref:System.Windows.Media.Visual>。  
    
  
<a name="prereqs"></a>   
## <a name="prerequisites"></a>必要條件  
 若要了解本主題，您應該熟悉 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 所提供的不同筆刷類型及其基本功能。 如需簡介，請參閱 [WPF 筆刷概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md)。  
  
<a name="image"></a>   
## <a name="paint-an-area-with-an-image"></a>使用影像繪製區域  
 <xref:System.Windows.Media.ImageBrush>使用繪製區域<xref:System.Windows.Media.ImageSource>。 最常見的類型<xref:System.Windows.Media.ImageSource>搭配<xref:System.Windows.Media.ImageBrush>是<xref:System.Windows.Media.Imaging.BitmapImage>，用來描述點陣圖形。 您可以使用<xref:System.Windows.Media.DrawingImage>來繪製使用<xref:System.Windows.Media.Drawing>物件，但它比較容易使用<xref:System.Windows.Media.DrawingBrush>改為。 如需有關<xref:System.Windows.Media.ImageSource>物件，請參閱[影像處理概觀](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)。  
  
 要用以繪製<xref:System.Windows.Media.ImageBrush>，建立<xref:System.Windows.Media.Imaging.BitmapImage>並使用它來載入點陣圖內容。 然後，使用<xref:System.Windows.Media.Imaging.BitmapImage>設定<xref:System.Windows.Media.ImageBrush.ImageSource%2A>屬性<xref:System.Windows.Media.ImageBrush>。 最後，套用<xref:System.Windows.Media.ImageBrush>您想要繪製的物件。  在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，您也可以設定<xref:System.Windows.Media.ImageBrush.ImageSource%2A>屬性<xref:System.Windows.Media.ImageBrush>来載入的映像的路徑。  
  
 如同所有<xref:System.Windows.Media.Brush>物件<xref:System.Windows.Media.ImageBrush>可以用來繪製圖形、 面板、 控制項和文字方塊等物件。 下圖顯示一些可達到的效果<xref:System.Windows.Media.ImageBrush>。  
  
 ![ImageBrush 輸出範例](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
ImageBrush 所繪製的物件  
  
 根據預設，<xref:System.Windows.Media.ImageBrush>兩端之間自動縮放它的映像完全填滿區域正在繪製，可能會使影像扭曲繪製的區域有不同的外觀比例比的映像。 您可以變更此行為變更<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性的預設值從<xref:System.Windows.Media.Stretch.Fill>至<xref:System.Windows.Media.Stretch.None>， <xref:System.Windows.Media.Stretch.Uniform>，或<xref:System.Windows.Media.Stretch.UniformToFill>。 因為<xref:System.Windows.Media.ImageBrush>是一種<xref:System.Windows.Media.TileBrush>，您可以指定完全如何影像筆刷填滿輸出區域，甚至建立模式。 如需有關進階<xref:System.Windows.Media.TileBrush>功能，請參閱[TileBrush 概觀](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)。  
  
<a name="fillingpanelwithimage"></a>   
## <a name="example-paint-an-object-with-a-bitmap-image"></a>範例：使用點陣圖影像繪製物件  
 下列範例會使用<xref:System.Windows.Media.ImageBrush>來繪製<xref:System.Windows.Controls.Panel.Background%2A>的<xref:System.Windows.Controls.Canvas>。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/ImageBrushExample.xaml#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/ImageBrushExample.cs#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/imagebrushexample.vb#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
<a name="drawingbrushintro"></a>   
## <a name="paint-an-area-with-a-drawing"></a>使用繪圖繪製區域  
 A<xref:System.Windows.Media.DrawingBrush>可讓您使用圖形、 文字、 影像和視訊繪製區域。 圖形內部繪圖筆刷可能本身繪製實心色彩、 漸層、 映像，或甚至是另一個<xref:System.Windows.Media.DrawingBrush>。 下圖示範的一些用法<xref:System.Windows.Media.DrawingBrush>。  
  
 ![DrawingBrush 輸出範例](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-drawingbrushexamples.png "wcpsdk_mmgraphics_drawingbrushexamples")  
DrawingBrush 所繪製的物件  
  
 A<xref:System.Windows.Media.DrawingBrush>使用繪製區域<xref:System.Windows.Media.Drawing>物件。 A<xref:System.Windows.Media.Drawing>物件描述可見的內容，例如圖形、 點陣圖、 視訊或一行文字。 不同類型的繪圖可描繪不同類型的內容。 以下列出不同類型的繪圖物件。  
  
-   <xref:System.Windows.Media.GeometryDrawing>– 繪製圖形。  
  
-   <xref:System.Windows.Media.ImageDrawing>– 繪製影像。  
  
-   <xref:System.Windows.Media.GlyphRunDrawing>– 繪製文字。  
  
-   <xref:System.Windows.Media.VideoDrawing>– 播放音訊或視訊檔案。  
  
-   <xref:System.Windows.Media.DrawingGroup>– 繪製其他繪圖。 您可以使用繪圖群組，來將其他繪圖結合為單一複合繪圖。  
  
 如需有關<xref:System.Windows.Media.Drawing>物件，請參閱[繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)。  
  
 像<xref:System.Windows.Media.ImageBrush>、<xref:System.Windows.Media.DrawingBrush>延伸其<xref:System.Windows.Media.DrawingBrush.Drawing%2A>來填滿其輸出區域。 您可以藉由變更覆寫這個行為<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性從其預設值為<xref:System.Windows.Media.Stretch.Fill>。 如需詳細資訊，請參閱 <xref:System.Windows.Media.TileBrush.Stretch%2A> 屬性 (Property)。  
  
<a name="fillingareawithdrawingbrushexample"></a>   
## <a name="example-paint-an-object-with-a-drawing"></a>範例：使用繪圖繪製物件  
 下列範例顯示如何使用含有三個橢圓形的繪圖來繪製物件。 A<xref:System.Windows.Media.GeometryDrawing>用來描述省略符號。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/DrawingBrushExample.xaml#graphicsmmdrawingbrushasbuttonbackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/DrawingBrushExample.cs#graphicsmmdrawingbrushasbuttonbackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/drawingbrushexample.vb#graphicsmmdrawingbrushasbuttonbackgroundexample1)]  
  
<a name="visualbrushsection"></a>   
## <a name="paint-an-area-with-a-visual"></a>使用 Visual 繪製區域  
 最具彈性且功能強大的筆刷，<xref:System.Windows.Media.VisualBrush>使用繪製區域<xref:System.Windows.Media.Visual>。 A<xref:System.Windows.Media.Visual>是低階的圖形化型別做為許多實用的圖形化元件的上階。 例如， <xref:System.Windows.Window>， <xref:System.Windows.FrameworkElement>，和<xref:System.Windows.Controls.Control>類別是所有類型的<xref:System.Windows.Media.Visual>物件。 使用<xref:System.Windows.Media.VisualBrush>，您可以繪製區域與幾乎任何[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]圖形化的物件。  
  
> [!NOTE]
>  雖然<xref:System.Windows.Media.VisualBrush>是一種<xref:System.Windows.Freezable>物件，它無法凍結 （對唯讀） 當其<xref:System.Windows.Media.VisualBrush.Visual%2A>以外屬性設定為值`null`。  
  
 有兩種方式來指定<xref:System.Windows.Media.VisualBrush.Visual%2A>內容的<xref:System.Windows.Media.VisualBrush>。  
  
-   建立新<xref:System.Windows.Media.Visual>並用它來設定<xref:System.Windows.Media.VisualBrush.Visual%2A>屬性<xref:System.Windows.Media.VisualBrush>。 如需範例，請參閱稍後的[範例：使用視覺效果繪製物件](#examplevisualbrush1)一節。  
  
-   使用現有<xref:System.Windows.Media.Visual>，它會建立重複的映像的目標<xref:System.Windows.Media.Visual>。 然後您可以使用<xref:System.Windows.Media.VisualBrush>以建立交錯效果，例如反映和縮放比例。 如需範例，請參閱[範例：建立反映](#examplevisualbrush2)一節。  
  
 當您定義新<xref:System.Windows.Media.VisualBrush.Visual%2A>如<xref:System.Windows.Media.VisualBrush>而且<xref:System.Windows.Media.Visual>是<xref:System.Windows.UIElement>上執行 （例如面板或控制項），這個版面配置系統<xref:System.Windows.UIElement>及其子項目時<xref:System.Windows.Media.VisualBrush.AutoLayoutContent%2A>屬性設定為`true`。 不過，根<xref:System.Windows.UIElement>基本上與系統的其餘部分隔離： 樣式和外部配置無法普及到此界限。 因此，您應該明確指定根大小<xref:System.Windows.UIElement>，因為其唯一的父代是<xref:System.Windows.Media.VisualBrush>，因此它無法自動調整本身所繪製的區域。 如需 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中配置的詳細資訊，請參閱[配置](../../../../docs/framework/wpf/advanced/layout.md)。  
  
 像<xref:System.Windows.Media.ImageBrush>和<xref:System.Windows.Media.DrawingBrush>、<xref:System.Windows.Media.VisualBrush>自動縮放以填滿其輸出區域其內容。 您可以藉由變更覆寫這個行為<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性從其預設值為<xref:System.Windows.Media.Stretch.Fill>。 如需詳細資訊，請參閱 <xref:System.Windows.Media.TileBrush.Stretch%2A> 屬性 (Property)。  
  
<a name="examplevisualbrush1"></a>   
## <a name="example-paint-an-object-with-a-visual"></a>範例：使用視覺效果繪製物件  
 下列範例會使用多個控制項與一個面板來繪製矩形。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/VisualBrushExample.xaml#graphicsmmvisualbrushasrectanglebackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/VisualBrushExample.cs#graphicsmmvisualbrushasrectanglebackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/visualbrushexample.vb#graphicsmmvisualbrushasrectanglebackgroundexample1)]  
  
<a name="examplevisualbrush2"></a>   
## <a name="example-create-a-reflection"></a>範例：建立反映  
 上述範例示範如何建立新<xref:System.Windows.Media.Visual>用來做為背景。 您也可以使用<xref:System.Windows.Media.VisualBrush>顯示現有的 visual; 這項功能可讓您產生有趣的視覺效果，例如反射和縮放比例。 下列範例會使用<xref:System.Windows.Media.VisualBrush>來建立反映的<xref:System.Windows.Controls.Border>，其中包含數個項目。 下圖顯示的是這個範例產生的輸出。  
  
 ![A 反映視覺物件](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
反映後的 Visual 物件  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 如需示範如何放大部分螢幕以及如何建立反映的其他範例，請參閱 [VisualBrush 範例](http://go.microsoft.com/fwlink/?LinkID=160049)。  
  
<a name="tilebrush"></a>   
## <a name="tilebrush-features"></a>TileBrush 功能  
 <xref:System.Windows.Media.ImageBrush><xref:System.Windows.Media.DrawingBrush>，和<xref:System.Windows.Media.VisualBrush>種<xref:System.Windows.Media.TileBrush>物件。 <xref:System.Windows.Media.TileBrush>物件會提供您有大量的控制能力如何繪製區域的映像、 繪圖或視覺效果。 例如，您可以用構成圖樣的一系列影像並排顯示來繪製區域，而不是只以單一自動縮放的影像來繪製區域。  
  
 A<xref:System.Windows.Media.TileBrush>有三個主要元件： 內容、 圖格和輸出區域。  
  
 ![TileBrush 元件](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
具有單一並排顯示之 TileBrush 的元件  
  
 ![元件的並排顯示 TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
具有多個並排顯示之 TileBrush 的元件  
  
 如需有關的並排顯示功能<xref:System.Windows.Media.TileBrush>物件，請參閱[TileBrush 概觀](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.ImageBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 <xref:System.Windows.Media.VisualBrush>  
 <xref:System.Windows.Media.TileBrush>  
 [TileBrush 概觀](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)  
 [WPF 筆刷概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md)  
 [影像處理概觀](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [不透明度遮罩概觀](../../../../docs/framework/wpf/graphics-multimedia/opacity-masks-overview.md)  
 [WPF 圖形轉譯概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [ImageBrush 範例](http://go.microsoft.com/fwlink/?LinkID=160005)  
 [VisualBrush 範例](http://go.microsoft.com/fwlink/?LinkID=160049)
