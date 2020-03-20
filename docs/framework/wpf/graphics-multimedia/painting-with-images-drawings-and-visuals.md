---
title: 使用影像、繪圖和視覺效果繪製
ms.date: 03/30/2017
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
ms.openlocfilehash: e0e5e386b32425c87502d18a24e758193c14a5b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186914"
---
# <a name="painting-with-images-drawings-and-visuals"></a>使用影像、繪圖和視覺效果繪製
本主題<xref:System.Windows.Media.ImageBrush>介紹如何使用<xref:System.Windows.Media.DrawingBrush>和<xref:System.Windows.Media.VisualBrush>物件使用圖像、或<xref:System.Windows.Media.Drawing>。 <xref:System.Windows.Media.Visual>  

<a name="prereqs"></a>
## <a name="prerequisites"></a>必要條件  
 若要了解本主題，您應該熟悉 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 所提供的不同筆刷類型及其基本功能。 如需簡介，請參閱 [WPF 筆刷概觀](wpf-brushes-overview.md)。  
  
<a name="image"></a>
## <a name="paint-an-area-with-an-image"></a>使用影像繪製區域  
 用<xref:System.Windows.Media.ImageBrush>油漆區域<xref:System.Windows.Media.ImageSource>。 與 一起使用<xref:System.Windows.Media.ImageSource>的最常見類型<xref:System.Windows.Media.ImageBrush>是<xref:System.Windows.Media.Imaging.BitmapImage>，它描述了點陣圖圖形。 可以使用 物件<xref:System.Windows.Media.DrawingImage>進行繪製<xref:System.Windows.Media.Drawing>，但<xref:System.Windows.Media.DrawingBrush>使用 物件更簡單。 有關<xref:System.Windows.Media.ImageSource>物件的詳細資訊，請參閱[映射概述](imaging-overview.md)。  
  
 要使用 進行<xref:System.Windows.Media.ImageBrush>繪製，請<xref:System.Windows.Media.Imaging.BitmapImage>創建 並使用它來載入點陣圖內容。 然後，使用<xref:System.Windows.Media.Imaging.BitmapImage>設置<xref:System.Windows.Media.ImageBrush.ImageSource%2A>的屬性<xref:System.Windows.Media.ImageBrush>。 最後，將<xref:System.Windows.Media.ImageBrush>應用 到要繪製的物件。  在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中還可以僅設置<xref:System.Windows.Media.ImageBrush.ImageSource%2A><xref:System.Windows.Media.ImageBrush>具有要載入的圖像路徑的屬性。  
  
 與所有<xref:System.Windows.Media.Brush>物件一樣，<xref:System.Windows.Media.ImageBrush>還可用於繪製物件，如形狀、面板、控制項和文本。 下圖顯示了可以使用 可以實現的一<xref:System.Windows.Media.ImageBrush>些效果。  
  
 ![ImageBrush 輸出範例](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
ImageBrush 所繪製的物件  
  
 預設情況下，如果繪製<xref:System.Windows.Media.ImageBrush>區域的縱橫比與圖像不同，則拉伸其圖像以完全填充要繪製的區域，從而扭曲圖像。 可以通過<xref:System.Windows.Media.TileBrush.Stretch%2A>將屬性的<xref:System.Windows.Media.Stretch.Fill>預設值更改為<xref:System.Windows.Media.Stretch.None>來<xref:System.Windows.Media.Stretch.Uniform>更改此行為。 <xref:System.Windows.Media.Stretch.UniformToFill> 因為<xref:System.Windows.Media.ImageBrush>是 的類型<xref:System.Windows.Media.TileBrush>，您可以準確指定影像筆刷填充輸出區域的方式，甚至建立模式。 有關高級<xref:System.Windows.Media.TileBrush>功能的詳細資訊，請參閱[TileBrush 概述](tilebrush-overview.md)。  
  
<a name="fillingpanelwithimage"></a>
## <a name="example-paint-an-object-with-a-bitmap-image"></a>範例：使用點陣圖影像繪製物件  
 下面的示例使用<xref:System.Windows.Media.ImageBrush>來繪製 的<xref:System.Windows.Controls.Panel.Background%2A>。 <xref:System.Windows.Controls.Canvas>  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/ImageBrushExample.xaml#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/ImageBrushExample.cs#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/imagebrushexample.vb#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
<a name="drawingbrushintro"></a>
## <a name="paint-an-area-with-a-drawing"></a>使用繪圖繪製區域  
 A<xref:System.Windows.Media.DrawingBrush>使您能夠使用形狀、文本、圖像和視頻繪製區域。 繪圖畫筆內的形狀可能本身被繪製為純色、漸變、圖像，甚至另一個<xref:System.Windows.Media.DrawingBrush>。 下圖演示了 的一<xref:System.Windows.Media.DrawingBrush>些用途。  
  
 ![DrawingBrush 輸出範例](./media/wcpsdk-mmgraphics-drawingbrushexamples.png "wcpsdk_mmgraphics_drawingbrushexamples")  
DrawingBrush 所繪製的物件  
  
 用<xref:System.Windows.Media.DrawingBrush><xref:System.Windows.Media.Drawing>物件繪製區域。 <xref:System.Windows.Media.Drawing>物件描述可見內容，如形狀、點陣圖、視頻或文本行。 不同類型的繪圖可描繪不同類型的內容。 以下列出不同類型的繪圖物件。  
  
- <xref:System.Windows.Media.GeometryDrawing>• 繪製形狀。  
  
- <xref:System.Windows.Media.ImageDrawing>• 繪製圖像。  
  
- <xref:System.Windows.Media.GlyphRunDrawing>• 繪製文本。  
  
- <xref:System.Windows.Media.VideoDrawing>• 播放音訊或視頻檔。  
  
- <xref:System.Windows.Media.DrawingGroup>• 繪製其他繪圖。 您可以使用繪圖群組，將其他繪圖結合為單一複合繪圖。  
  
 有關<xref:System.Windows.Media.Drawing>物件的詳細資訊，請參閱[繪圖物件概述](drawing-objects-overview.md)。  
  
 像<xref:System.Windows.Media.ImageBrush>一個<xref:System.Windows.Media.DrawingBrush>一<xref:System.Windows.Media.DrawingBrush.Drawing%2A>個，拉伸它來填充其輸出區域。 可以通過從 其預設設置更改<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性來<xref:System.Windows.Media.Stretch.Fill>重寫此行為。 如需詳細資訊，請參閱 <xref:System.Windows.Media.TileBrush.Stretch%2A> 屬性 (Property)。  
  
<a name="fillingareawithdrawingbrushexample"></a>
## <a name="example-paint-an-object-with-a-drawing"></a>範例：使用繪圖繪製物件  
 下列範例顯示如何使用含有三個橢圓形的繪圖來繪製物件。 A<xref:System.Windows.Media.GeometryDrawing>用於描述橢圓。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/DrawingBrushExample.xaml#graphicsmmdrawingbrushasbuttonbackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/DrawingBrushExample.cs#graphicsmmdrawingbrushasbuttonbackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/drawingbrushexample.vb#graphicsmmdrawingbrushasbuttonbackgroundexample1)]  
  
<a name="visualbrushsection"></a>
## <a name="paint-an-area-with-a-visual"></a>使用 Visual 繪製區域  
 在所有畫筆中最通用和最強大的，<xref:System.Windows.Media.VisualBrush>用 油漆區域。 <xref:System.Windows.Media.Visual> A<xref:System.Windows.Media.Visual>是一種低級圖形類型，用作許多有用圖形元件的祖先。 例如，<xref:System.Windows.Window>和<xref:System.Windows.FrameworkElement><xref:System.Windows.Controls.Control>類是所有類型的<xref:System.Windows.Media.Visual>物件。 使用<xref:System.Windows.Media.VisualBrush>，可以使用幾乎任何[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]繪圖物件繪製區域。  
  
> [!NOTE]
> 儘管<xref:System.Windows.Media.VisualBrush>是<xref:System.Windows.Freezable>物件的一種類型，但當其<xref:System.Windows.Media.VisualBrush.Visual%2A>屬性設置為 以外的`null`值時，它不能凍結（使唯讀）。  
  
 有兩種方法可以指定<xref:System.Windows.Media.VisualBrush.Visual%2A>的內容。 <xref:System.Windows.Media.VisualBrush>  
  
- 創建新，<xref:System.Windows.Media.Visual>並用它來設置<xref:System.Windows.Media.VisualBrush.Visual%2A>的屬性。 <xref:System.Windows.Media.VisualBrush> 如需範例，請參閱稍後的[範例：使用視覺效果繪製物件](#examplevisualbrush1)一節。  
  
- 使用現有<xref:System.Windows.Media.Visual>，這將創建目標的<xref:System.Windows.Media.Visual>重複圖像。 然後，可以使用<xref:System.Windows.Media.VisualBrush>創建有趣的效果，如反射和放大倍率。 如需範例，請參閱[範例：建立反映](#examplevisualbrush2)一節。  
  
 當您為 和<xref:System.Windows.Media.VisualBrush.Visual%2A><xref:System.Windows.Media.VisualBrush>定義 new<xref:System.Windows.Media.Visual>時<xref:System.Windows.UIElement>，該 和 是 （如面板或控制項）， 當<xref:System.Windows.UIElement><xref:System.Windows.Media.VisualBrush.AutoLayoutContent%2A>屬性設置為`true`時，佈局系統在 及其子項目上運行。 但是，根<xref:System.Windows.UIElement>基本上與系統的其餘部分隔離：樣式，外部佈局不能滲透到此邊界中。 因此，應顯式指定根<xref:System.Windows.UIElement>的大小，因為它的唯一父級是 ，<xref:System.Windows.Media.VisualBrush>因此它不能自動調整自身大小到要繪製的區域。 如需 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中配置的詳細資訊，請參閱[配置](../advanced/layout.md)。  
  
 喜歡<xref:System.Windows.Media.ImageBrush><xref:System.Windows.Media.DrawingBrush>和<xref:System.Windows.Media.VisualBrush>，拉伸其內容以填充其輸出區域。 可以通過從 其預設設置更改<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性來<xref:System.Windows.Media.Stretch.Fill>重寫此行為。 如需詳細資訊，請參閱 <xref:System.Windows.Media.TileBrush.Stretch%2A> 屬性 (Property)。  
  
<a name="examplevisualbrush1"></a>
## <a name="example-paint-an-object-with-a-visual"></a>範例：使用視覺效果繪製物件  
 下列範例會使用多個控制項與一個面板來繪製矩形。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/VisualBrushExample.xaml#graphicsmmvisualbrushasrectanglebackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/VisualBrushExample.cs#graphicsmmvisualbrushasrectanglebackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/visualbrushexample.vb#graphicsmmvisualbrushasrectanglebackgroundexample1)]  
  
<a name="examplevisualbrush2"></a>
## <a name="example-create-a-reflection"></a>範例：建立反映  
 前面的示例演示如何創建一個用於背景的新<xref:System.Windows.Media.Visual>。 您還可以使用 顯示<xref:System.Windows.Media.VisualBrush>現有視覺物件;此功能使您能夠生成有趣的視覺效果，如反射和放大倍率。 下面的示例使用<xref:System.Windows.Media.VisualBrush>創建包含多個元素的 的<xref:System.Windows.Controls.Border>反射。 下圖顯示的是這個範例產生的輸出。  
  
 ![反映後的 Visual 物件](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
反映後的 Visual 物件  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 如需示範如何放大部分螢幕以及如何建立反映的其他範例，請參閱 [VisualBrush 範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush)。  
  
<a name="tilebrush"></a>
## <a name="tilebrush-features"></a>TileBrush 功能  
 <xref:System.Windows.Media.ImageBrush><xref:System.Windows.Media.DrawingBrush>，是<xref:System.Windows.Media.VisualBrush>物件的類型<xref:System.Windows.Media.TileBrush>。 <xref:System.Windows.Media.TileBrush>物件可對圖像、繪圖或視覺物件繪製區域的方式進行大量控制。 例如，您可以用構成圖樣的一系列影像並排顯示來繪製區域，而不是只以單一自動縮放的影像來繪製區域。  
  
 A<xref:System.Windows.Media.TileBrush>有三個主要元件：內容、磁貼和輸出區域。  
  
 ![TileBrush 元件](./media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
具有單一並排顯示之 TileBrush 的元件  
  
 ![區塊式 TileBrush 的元件](./media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
具有多個並排顯示之 TileBrush 的元件  
  
 有關<xref:System.Windows.Media.TileBrush>物件平鋪功能的詳細資訊，請參閱[TileBrush 概述](tilebrush-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.ImageBrush>
- <xref:System.Windows.Media.DrawingBrush>
- <xref:System.Windows.Media.VisualBrush>
- <xref:System.Windows.Media.TileBrush>
- [TileBrush 概觀](tilebrush-overview.md)
- [WPF 筆刷概觀](wpf-brushes-overview.md)
- [影像處理概觀](imaging-overview.md)
- [繪圖物件概觀](drawing-objects-overview.md)
- [不透明遮罩概觀](opacity-masks-overview.md)
- [WPF 圖形轉譯概觀](wpf-graphics-rendering-overview.md)
- [ImageBrush 範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)
- [VisualBrush 範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush)
