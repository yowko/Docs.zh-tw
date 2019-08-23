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
ms.openlocfilehash: e80132a5467f932e5569787f43427044ba2be256
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929602"
---
# <a name="painting-with-images-drawings-and-visuals"></a>使用影像、繪圖和視覺效果繪製
本主題描述如何使用<xref:System.Windows.Media.ImageBrush>、 <xref:System.Windows.Media.DrawingBrush>和<xref:System.Windows.Media.VisualBrush>物件來<xref:System.Windows.Media.Drawing>繪製具有影像、或的<xref:System.Windows.Media.Visual>區域。  

<a name="prereqs"></a>   
## <a name="prerequisites"></a>必要條件  
 若要了解本主題，您應該熟悉 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 所提供的不同筆刷類型及其基本功能。 如需簡介，請參閱 [WPF 筆刷概觀](wpf-brushes-overview.md)。  
  
<a name="image"></a>   
## <a name="paint-an-area-with-an-image"></a>使用影像繪製區域  
 會<xref:System.Windows.Media.ImageBrush> 使用<xref:System.Windows.Media.ImageSource>繪製區域。 與搭配使用的最<xref:System.Windows.Media.ImageSource>常見類型<xref:System.Windows.Media.Imaging.BitmapImage>是,它會描述點陣圖圖形。 <xref:System.Windows.Media.ImageBrush> 您可以使用<xref:System.Windows.Media.DrawingImage>來繪製<xref:System.Windows.Media.Drawing>使用物件, 但<xref:System.Windows.Media.DrawingBrush>改用是較簡單的方式。 如需<xref:System.Windows.Media.ImageSource>物件的詳細資訊, 請參閱[映射處理總覽](imaging-overview.md)。  
  
 若要使用<xref:System.Windows.Media.ImageBrush>繪製, 請<xref:System.Windows.Media.Imaging.BitmapImage>建立, 並使用它來載入點陣圖內容。 然後, 使用<xref:System.Windows.Media.Imaging.BitmapImage>來<xref:System.Windows.Media.ImageBrush.ImageSource%2A>設定的屬性<xref:System.Windows.Media.ImageBrush>。 最後, 將<xref:System.Windows.Media.ImageBrush>套用至您要繪製的物件。  在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中, 您也可以只<xref:System.Windows.Media.ImageBrush.ImageSource%2A>將的<xref:System.Windows.Media.ImageBrush>屬性設定為要載入之影像的路徑。  
  
 就像<xref:System.Windows.Media.Brush>所有物件一樣<xref:System.Windows.Media.ImageBrush> , 可以用來繪製圖形、面板、控制項和文字等物件。 下圖顯示可<xref:System.Windows.Media.ImageBrush>透過來達成的一些效果。  
  
 ![ImageBrush 輸出範例](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
ImageBrush 所繪製的物件  
  
 根據預設, 會<xref:System.Windows.Media.ImageBrush>將其影像延伸以完全填滿所繪製的區域, 如果繪製的區域與影像的外觀比例不同, 可能會扭曲影像。 您可以變更此行為, 方法是<xref:System.Windows.Media.TileBrush.Stretch%2A>將屬性從的預設<xref:System.Windows.Media.Stretch.Fill>值變更<xref:System.Windows.Media.Stretch.None>為<xref:System.Windows.Media.Stretch.Uniform>、或<xref:System.Windows.Media.Stretch.UniformToFill>。 因為<xref:System.Windows.Media.ImageBrush>是的<xref:System.Windows.Media.TileBrush>類型, 所以您可以確切地指定影像筆刷如何填滿輸出區域, 甚至是建立模式。 如需有關 advanced <xref:System.Windows.Media.TileBrush>功能的詳細資訊, 請參閱[TileBrush 總覽](tilebrush-overview.md)。  
  
<a name="fillingpanelwithimage"></a>   
## <a name="example-paint-an-object-with-a-bitmap-image"></a>範例：使用點陣圖影像繪製物件  
 下列範例會使用<xref:System.Windows.Media.ImageBrush>來<xref:System.Windows.Controls.Panel.Background%2A>繪製<xref:System.Windows.Controls.Canvas>的。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/ImageBrushExample.xaml#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/ImageBrushExample.cs#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/imagebrushexample.vb#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
<a name="drawingbrushintro"></a>   
## <a name="paint-an-area-with-a-drawing"></a>使用繪圖繪製區域  
 可<xref:System.Windows.Media.DrawingBrush>讓您使用圖形、文字、影像和影片繪製區域。 繪圖筆刷內的圖形本身可能會以純色、漸層、影像或甚至另一種<xref:System.Windows.Media.DrawingBrush>方式繪製。 下圖將示範的一些用法<xref:System.Windows.Media.DrawingBrush>。  
  
 ![DrawingBrush 輸出範例](./media/wcpsdk-mmgraphics-drawingbrushexamples.png "wcpsdk_mmgraphics_drawingbrushexamples")  
DrawingBrush 所繪製的物件  
  
 會<xref:System.Windows.Media.DrawingBrush> 使用<xref:System.Windows.Media.Drawing>物件繪製區域。 <xref:System.Windows.Media.Drawing>物件描述可見內容, 例如圖形、點陣圖、影片或一行文字。 不同類型的繪圖可描繪不同類型的內容。 以下列出不同類型的繪圖物件。  
  
- <xref:System.Windows.Media.GeometryDrawing>–繪製圖形。  
  
- <xref:System.Windows.Media.ImageDrawing>–繪製影像。  
  
- <xref:System.Windows.Media.GlyphRunDrawing>–繪製文字。  
  
- <xref:System.Windows.Media.VideoDrawing>–播放音訊或影片檔案。  
  
- <xref:System.Windows.Media.DrawingGroup>–繪製其他繪圖。 您可以使用繪圖群組，來將其他繪圖結合為單一複合繪圖。  
  
 如需<xref:System.Windows.Media.Drawing>物件的詳細資訊, 請參閱[繪圖物件總覽](drawing-objects-overview.md)。  
  
 就像一樣<xref:System.Windows.Media.DrawingBrush.Drawing%2A> <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.ImageBrush>, 會將其延伸以填滿其輸出區域。 您可以從的預設<xref:System.Windows.Media.TileBrush.Stretch%2A> <xref:System.Windows.Media.Stretch.Fill>設定變更屬性, 以覆寫此行為。 如需詳細資訊，請參閱 <xref:System.Windows.Media.TileBrush.Stretch%2A> 屬性 (Property)。  
  
<a name="fillingareawithdrawingbrushexample"></a>   
## <a name="example-paint-an-object-with-a-drawing"></a>範例：使用繪圖繪製物件  
 下列範例顯示如何使用含有三個橢圓形的繪圖來繪製物件。 <xref:System.Windows.Media.GeometryDrawing>是用來描述省略號。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/DrawingBrushExample.xaml#graphicsmmdrawingbrushasbuttonbackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/DrawingBrushExample.cs#graphicsmmdrawingbrushasbuttonbackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/drawingbrushexample.vb#graphicsmmdrawingbrushasbuttonbackgroundexample1)]  
  
<a name="visualbrushsection"></a>   
## <a name="paint-an-area-with-a-visual"></a>使用 Visual 繪製區域  
 所有筆刷最具彈性且功能強大的, <xref:System.Windows.Media.VisualBrush>會<xref:System.Windows.Media.Visual>使用繪製區域。 <xref:System.Windows.Media.Visual>是一種低層級的圖形化類型, 可做為許多實用圖形元件的上階。 例如<xref:System.Windows.Window>,、 <xref:System.Windows.FrameworkElement>和<xref:System.Windows.Controls.Control>類別都是物件的<xref:System.Windows.Media.Visual>所有類型。 使用, 您可以使用幾乎任何[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]繪圖物件繪製區域。 <xref:System.Windows.Media.VisualBrush>  
  
> [!NOTE]
> 雖然<xref:System.Windows.Media.VisualBrush>是<xref:System.Windows.Freezable>物件的類型, 但它的<xref:System.Windows.Media.VisualBrush.Visual%2A> `null`屬性設定為以外的值時, 無法凍結 (成為唯讀)。  
  
 有兩種方式可指定<xref:System.Windows.Media.VisualBrush.Visual%2A>的內容。 <xref:System.Windows.Media.VisualBrush>  
  
- 建立新<xref:System.Windows.Media.Visual>的, 並使用它來<xref:System.Windows.Media.VisualBrush.Visual%2A>設定的屬性<xref:System.Windows.Media.VisualBrush>。 如需範例, 請參閱[範例:使用後面的視覺效果](#examplevisualbrush1)區段繪製物件。  
  
- 使用現有<xref:System.Windows.Media.Visual>的, 這會建立目標<xref:System.Windows.Media.Visual>的重複影像。 接著, 您可以使用<xref:System.Windows.Media.VisualBrush>來建立有趣的效果, 例如反映和縮放比例。 如需範例, 請參閱[範例:建立反映](#examplevisualbrush2)區段。  
  
 當您定義的新<xref:System.Windows.Media.VisualBrush.Visual%2A> <xref:System.Windows.Media.VisualBrush> , 且<xref:System.Windows.Media.Visual>為<xref:System.Windows.UIElement> (例如<xref:System.Windows.UIElement>面板或控制項) 時, 當<xref:System.Windows.Media.VisualBrush.AutoLayoutContent%2A>屬性設定為`true`時, 配置系統會在和其子項目上執行。 不過, 根目錄<xref:System.Windows.UIElement>基本上與系統的其餘部分隔離: 樣式, 而外部配置無法穿透此界限。 因此, 您應該明確指定根<xref:System.Windows.UIElement>的大小, 因為它唯一的<xref:System.Windows.Media.VisualBrush>父系是, 因此它無法自動將本身調整為所繪製的區域。 如需 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中配置的詳細資訊，請參閱[配置](../advanced/layout.md)。  
  
 如同<xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.VisualBrush>和<xref:System.Windows.Media.DrawingBrush>, 會將其內容延伸, 以填滿其輸出區域。 您可以從的預設<xref:System.Windows.Media.TileBrush.Stretch%2A> <xref:System.Windows.Media.Stretch.Fill>設定變更屬性, 以覆寫此行為。 如需詳細資訊，請參閱 <xref:System.Windows.Media.TileBrush.Stretch%2A> 屬性 (Property)。  
  
<a name="examplevisualbrush1"></a>   
## <a name="example-paint-an-object-with-a-visual"></a>範例：使用視覺效果繪製物件  
 下列範例會使用多個控制項與一個面板來繪製矩形。  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/VisualBrushExample.xaml#graphicsmmvisualbrushasrectanglebackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/VisualBrushExample.cs#graphicsmmvisualbrushasrectanglebackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/visualbrushexample.vb#graphicsmmvisualbrushasrectanglebackgroundexample1)]  
  
<a name="examplevisualbrush2"></a>   
## <a name="example-create-a-reflection"></a>範例：建立反映  
 先前的範例示範如何建立新<xref:System.Windows.Media.Visual>的作為背景使用。 您也可以使用<xref:System.Windows.Media.VisualBrush>來顯示現有的視覺效果, 這項功能可讓您產生有趣的視覺效果, 例如反射和縮放比例。 下列範例<xref:System.Windows.Media.VisualBrush> <xref:System.Windows.Controls.Border>會使用來建立包含數個元素之的反映。 下圖顯示的是這個範例產生的輸出。  
  
 ![反映的視覺物件](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
反映後的 Visual 物件  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 如需示範如何放大部分螢幕以及如何建立反映的其他範例，請參閱 [VisualBrush 範例](https://go.microsoft.com/fwlink/?LinkID=160049)。  
  
<a name="tilebrush"></a>   
## <a name="tilebrush-features"></a>TileBrush 功能  
 <xref:System.Windows.Media.ImageBrush>、 <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.TileBrush>和<xref:System.Windows.Media.VisualBrush>是物件的類型。 <xref:System.Windows.Media.TileBrush>物件可讓您對使用影像、繪圖或視覺效果繪製區域的方式有很大的控制權。 例如，您可以用構成圖樣的一系列影像並排顯示來繪製區域，而不是只以單一自動縮放的影像來繪製區域。  
  
 <xref:System.Windows.Media.TileBrush>有三個主要元件: 內容、磚和輸出區域。  
  
 ![TileBrush 元件](./media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
具有單一並排顯示之 TileBrush 的元件  
  
 ![磚 TileBrush 的元件](./media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
具有多個並排顯示之 TileBrush 的元件  
  
 如需<xref:System.Windows.Media.TileBrush>物件之並排顯示功能的詳細資訊, 請參閱[TileBrush 總覽](tilebrush-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.ImageBrush>
- <xref:System.Windows.Media.DrawingBrush>
- <xref:System.Windows.Media.VisualBrush>
- <xref:System.Windows.Media.TileBrush>
- [TileBrush 概觀](tilebrush-overview.md)
- [WPF 筆刷概觀](wpf-brushes-overview.md)
- [影像處理概觀](imaging-overview.md)
- [繪圖物件概觀](drawing-objects-overview.md)
- [不透明度遮罩概觀](opacity-masks-overview.md)
- [WPF 圖形轉譯概觀](wpf-graphics-rendering-overview.md)
- [ImageBrush 範例](https://go.microsoft.com/fwlink/?LinkID=160005)
- [VisualBrush 範例](https://go.microsoft.com/fwlink/?LinkID=160049)
