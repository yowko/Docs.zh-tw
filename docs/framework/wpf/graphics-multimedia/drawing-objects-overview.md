---
title: 繪圖物件概觀
ms.date: 03/30/2017
helpviewer_keywords:
- ImageDrawing objects [WPF]
- GlyphRunDrawing objects [WPF]
- GeometryDrawing objects [WPF]
- drawings [WPF], about drawings
- Drawing objects [WPF]
- DrawingGroup objects [WPF]
ms.assetid: 9b5ce5c0-e204-4320-a7a8-0b2210d62f88
ms.openlocfilehash: 7a5d00eb2fb7c66e5e42d40893806e13717e1d2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186532"
---
# <a name="drawing-objects-overview"></a>繪圖物件概觀
本主題介紹<xref:System.Windows.Media.Drawing>物件，並介紹如何使用它們有效地繪製形狀、點陣圖、文本和媒體。 在<xref:System.Windows.Media.Drawing>創建剪貼畫、使用<xref:System.Windows.Media.DrawingBrush>上畫或使用物件時使用<xref:System.Windows.Media.Visual>物件。  

<a name="whatisadrawingsection"></a>
## <a name="what-is-a-drawing-object"></a>什麼是繪圖物件？  
 <xref:System.Windows.Media.Drawing>物件描述可見內容，如形狀、點陣圖、視頻或文本行。 不同類型的繪圖可描繪不同類型的內容。 以下列出不同類型的繪圖物件。  
  
- <xref:System.Windows.Media.GeometryDrawing>• 繪製形狀。  
  
- <xref:System.Windows.Media.ImageDrawing>• 繪製圖像。  
  
- <xref:System.Windows.Media.GlyphRunDrawing>• 繪製文本。  
  
- <xref:System.Windows.Media.VideoDrawing>• 播放音訊或視頻檔。  
  
- <xref:System.Windows.Media.DrawingGroup>• 繪製其他繪圖。 您可以使用繪圖群組，將其他繪圖結合為單一複合繪圖。  
  
 <xref:System.Windows.Media.Drawing>物件是通用的;有許多方法可以使用<xref:System.Windows.Media.Drawing>物件。  
  
- 可以使用 和<xref:System.Windows.Media.DrawingImage><xref:System.Windows.Controls.Image>控制項將其顯示為圖像。  
  
- 可以將其與 一起<xref:System.Windows.Media.DrawingBrush>用於繪製物件，例如 。 <xref:System.Windows.Controls.Page.Background%2A> <xref:System.Windows.Controls.Page>  
  
- 您可以使用它來描述 的外觀<xref:System.Windows.Media.DrawingVisual>。  
  
- 可以使用它枚舉 的內容<xref:System.Windows.Media.Visual>。  
  
 WPF 提供其他能夠繪製圖形、點陣圖、文字及媒體的物件類型。 例如，您還可以使用<xref:System.Windows.Shapes.Shape>物件繪製形狀，並且<xref:System.Windows.Controls.MediaElement>控制項提供了向應用程式添加視頻的另一種方法。 那麼，何時應該使用<xref:System.Windows.Media.Drawing>物件？ 當您可以犧牲框架級別功能以獲得性能優勢時，或者在需要時需要<xref:System.Windows.Freezable>功能時。 由於<xref:System.Windows.Media.Drawing>物件不支援[佈局](../advanced/layout.md)、輸入和焦點，因此它們提供了性能優勢，非常適合描述背景、剪輯藝術以及使用<xref:System.Windows.Media.Visual>物件的低級繪圖。  
  
 由於它們是類型<xref:System.Windows.Freezable>物件，<xref:System.Windows.Media.Drawing>因此物件具有多個特殊功能，其中包括：它們可以聲明為[資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)、在多個物件之間共用、僅讀以提高性能、克隆和使執行緒安全。 有關<xref:System.Windows.Freezable>物件提供的不同要素的詳細資訊，請參閱[可凍結物件概述](../advanced/freezable-objects-overview.md)。  
  
<a name="drawinggeometriessection"></a>
## <a name="draw-a-shape"></a>繪製圖形  
 要繪製形狀，請使用 。 <xref:System.Windows.Media.GeometryDrawing> 幾何圖形的屬性<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>描述要繪製的形狀，其<xref:System.Windows.Media.GeometryDrawing.Brush%2A>屬性描述如何繪製形狀的內部，其<xref:System.Windows.Media.GeometryDrawing.Pen%2A>屬性描述如何繪製其輪廓。  
  
 下面的示例使用 來<xref:System.Windows.Media.GeometryDrawing>繪製形狀。 形狀由 和 兩<xref:System.Windows.Media.GeometryGroup><xref:System.Windows.Media.EllipseGeometry>個物件描述。 形狀的內部用 繪製，<xref:System.Windows.Media.LinearGradientBrush>其輪廓用<xref:System.Windows.Media.Brushes.Black%2A><xref:System.Windows.Media.Pen>繪製。  
  
 本示例創建以下<xref:System.Windows.Media.GeometryDrawing>。  
  
 ![兩個橢圓形的 GeometryDrawing](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 如需完整的範例，請參閱[建立 GeometryDrawing](how-to-create-a-geometrydrawing.md)。  
  
 其他<xref:System.Windows.Media.Geometry>類，例如<xref:System.Windows.Media.PathGeometry>，使您能夠通過創建曲線和圓弧來創建更複雜的形狀。 有關<xref:System.Windows.Media.Geometry>物件的詳細資訊，請參閱[幾何概述](geometry-overview.md)。  
  
 有關繪製不使用<xref:System.Windows.Media.Drawing>物件的形狀的其他方法的詳細資訊，請參閱[WPF 概述 中的形狀和基本圖形](shapes-and-basic-drawing-in-wpf-overview.md)。  
  
<a name="drawingimagessection"></a>
## <a name="draw-an-image"></a>繪製影像  
 要繪製圖像，請使用 。 <xref:System.Windows.Media.ImageDrawing> 物件的屬性描述要繪製的圖像，其<xref:System.Windows.Media.ImageDrawing.Rect%2A>屬性定義繪製圖像的區域。 <xref:System.Windows.Media.ImageDrawing.ImageSource%2A> <xref:System.Windows.Media.ImageDrawing>  
  
 下列範例會在 (75,75) 繪製 100 x 100 像素的影像。 下圖顯示了示例<xref:System.Windows.Media.ImageDrawing>創建的示例。 添加了灰色邊框以顯示 的邊界<xref:System.Windows.Media.ImageDrawing>。  
  
 ![在 &#40;75,75&#41; 繪製之 100 x 100 的 ImageDrawing](./media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
100 x 100 的 ImageDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 如需有關影像的詳細資訊，請參閱[影像處理概觀](imaging-overview.md)。  
  
<a name="playmedia"></a>
## <a name="play-media-code-only"></a>播放媒體 (僅程式碼)  
  
> [!NOTE]
> 儘管可以聲明<xref:System.Windows.Media.VideoDrawing>in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，但只能使用代碼載入和播放其媒體。 要在 中[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]播放視頻，<xref:System.Windows.Controls.MediaElement>請使用  
  
 要播放音訊或視頻檔，請使用 和<xref:System.Windows.Media.VideoDrawing>。 <xref:System.Windows.Media.MediaPlayer> 有兩種方法可以載入及播放媒體。 第一種方法是自己使用<xref:System.Windows.Media.MediaPlayer>和<xref:System.Windows.Media.VideoDrawing>， 第二種方法是創建自己的<xref:System.Windows.Media.MediaTimeline>方法， 與 和<xref:System.Windows.Media.MediaPlayer>一<xref:System.Windows.Media.VideoDrawing>起使用 。  
  
> [!NOTE]
> 利用您的應用程式散發媒體時，您無法跟散發影像一樣，使用媒體檔案當作專案資源。 在您的專案檔中，您必須改為將媒體類型設定為 `Content`，並將 `CopyToOutputDirectory` 設定為 `PreserveNewest` 或 `Always`。  
  
 要在不創建自己的媒體的情況下播放媒體<xref:System.Windows.Media.MediaTimeline>，請執行以下步驟。  
  
1. 建立 <xref:System.Windows.Media.MediaPlayer> 物件。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2. 使用<xref:System.Windows.Media.MediaPlayer.Open%2A>方法載入媒體檔案。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3. 建立 <xref:System.Windows.Media.VideoDrawing>。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4. 通過設置<xref:System.Windows.Media.VideoDrawing.Rect%2A>的屬性<xref:System.Windows.Media.VideoDrawing>來指定繪製媒體的大小和位置。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5. 使用<xref:System.Windows.Media.VideoDrawing.Player%2A><xref:System.Windows.Media.MediaPlayer>創建的 設置<xref:System.Windows.Media.VideoDrawing>的屬性。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6. 使用<xref:System.Windows.Media.MediaPlayer.Play%2A>的方法<xref:System.Windows.Media.MediaPlayer>開始播放媒體。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 下面的示例使用 和<xref:System.Windows.Media.VideoDrawing>a<xref:System.Windows.Media.MediaPlayer>播放一次視頻檔。  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 要獲得對介質的額外計時控制，請使用<xref:System.Windows.Media.MediaTimeline><xref:System.Windows.Media.MediaPlayer>和<xref:System.Windows.Media.VideoDrawing>物件。 <xref:System.Windows.Media.MediaTimeline>使您能夠指定視頻是否應重複。 要將<xref:System.Windows.Media.VideoDrawing><xref:System.Windows.Media.MediaTimeline>和 使用 ， 執行以下步驟：  
  
1. 聲明<xref:System.Windows.Media.MediaTimeline>並設置其計時行為。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2. 從<xref:System.Windows.Media.MediaClock>中<xref:System.Windows.Media.MediaTimeline>創建 。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3. 創建<xref:System.Windows.Media.MediaPlayer>，並使用<xref:System.Windows.Media.MediaClock>來設置其<xref:System.Windows.Media.MediaPlayer.Clock%2A>屬性。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4. 創建<xref:System.Windows.Media.VideoDrawing>並將 分配<xref:System.Windows.Media.MediaPlayer>到<xref:System.Windows.Media.VideoDrawing.Player%2A>的屬性<xref:System.Windows.Media.VideoDrawing>。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 下面的示例使用<xref:System.Windows.Media.MediaTimeline>a<xref:System.Windows.Media.MediaPlayer>和 a<xref:System.Windows.Media.VideoDrawing>反復播放視頻。  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 請注意<xref:System.Windows.Media.MediaTimeline>，使用 時，使用 從<xref:System.Windows.Media.Animation.ClockController><xref:System.Windows.Media.Animation.Clock.Controller%2A>屬性返回的互動式<xref:System.Windows.Media.MediaClock>來控制媒體播放，而不是 使用 的<xref:System.Windows.Media.MediaPlayer>互動式方法。  
  
<a name="drawtext"></a>
## <a name="draw-text"></a>繪製文字  
 要繪製文本，請使用 和<xref:System.Windows.Media.GlyphRunDrawing> <xref:System.Windows.Media.GlyphRun>。 下面的示例使用<xref:System.Windows.Media.GlyphRunDrawing>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 A<xref:System.Windows.Media.GlyphRun>是一個低級物件，用於固定格式的文檔表示和列印方案。 將文本繪製到螢幕的更簡單方法是使用 或<xref:System.Windows.Controls.Label>。 <xref:System.Windows.Controls.TextBlock> 有關 的詳細資訊<xref:System.Windows.Media.GlyphRun>，請參閱[字形 Run 物件和字形元素概述簡介](../advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md)。  
  
<a name="compositedrawingssection"></a>
## <a name="composite-drawings"></a>複合繪圖  
 A<xref:System.Windows.Media.DrawingGroup>使您能夠將多個圖形合併到單個複合圖形中。 通過使用 ，<xref:System.Windows.Media.DrawingGroup>可以將形狀、圖像和文本合併到單個<xref:System.Windows.Media.Drawing>物件中。  
  
 下面的示例使用 將<xref:System.Windows.Media.DrawingGroup>兩<xref:System.Windows.Media.GeometryDrawing>個物件和一個<xref:System.Windows.Media.ImageDrawing>物件組合在一起。 此範例會產生下列輸出。  
  
 ![包含多個圖形的 DrawingGroup](./media/graphicsmm-simple.jpg "graphicsmm_simple")  
複合圖形  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 還<xref:System.Windows.Media.DrawingGroup>使您能夠對其內容應用不一樣蒙版、變換、點陣圖效果和其他操作。 <xref:System.Windows.Media.DrawingGroup>操作按以下順序應用<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>： 、 <xref:System.Windows.Media.DrawingGroup.Opacity%2A>、 <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A> <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>、 <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>、 <xref:System.Windows.Media.DrawingGroup.Transform%2A>、 、 然後 。  
  
 下圖顯示了操作的應用順序<xref:System.Windows.Media.DrawingGroup>。  
  
 ![DrawingGroup 作業的順序](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
DrawingGroup 作業的順序  
  
 下表描述了可用於操作<xref:System.Windows.Media.DrawingGroup>物件內容的屬性。  
  
|屬性|描述|圖例|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|更改內容選定部分的不<xref:System.Windows.Media.DrawingGroup>恰當性。 如需範例，請參閱[操作說明︰控制繪圖的不透明度](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748242(v=vs.90))。|![具有不一視擬面膜的繪圖組](./media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|均勻地更改內容的不<xref:System.Windows.Media.DrawingGroup>均勻性。 使用此屬性可使<xref:System.Windows.Media.Drawing>透明或部分透明。 如需範例，請參閱[操作說明︰對繪圖套用不透明度遮罩](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms753195(v=vs.90))。|![具有不同不透明度設定的 DrawingGroup](./media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|對<xref:System.Windows.Media.DrawingGroup>內容<xref:System.Windows.Media.Effects.BitmapEffect>應用 a。 如需範例，請參閱[操作說明︰對繪圖套用 BitmapEffect](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752341(v=vs.90))。|![具有 BlurBitmapEffect 的 DrawingGroup](./media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|將<xref:System.Windows.Media.DrawingGroup>內容剪輯到使用 描述的區域<xref:System.Windows.Media.Geometry>。 如需範例，請參閱[操作說明︰裁剪繪圖](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms743068(v=vs.90))。|![具有已定義之裁剪區域的 DrawingGroup](./media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|沿著指定的標線將裝置獨立像素貼齊裝置像素。 這個屬性可用於確保在低 DPI 顯示器上呈現清晰的細緻圖形。 如需範例，請參閱[對繪圖套用 GuidelineSet](how-to-apply-a-guidelineset-to-a-drawing.md)。|![具有與不具 GuidelineSet 的 DrawingGroup](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|轉換<xref:System.Windows.Media.DrawingGroup>內容。 如需範例，請參閱[操作說明︰對繪圖套用轉換](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms742304(v=vs.90))。|![旋轉後的 DrawingGroup](./media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>
## <a name="display-a-drawing-as-an-image"></a>將繪圖顯示為影像  
 要顯示<xref:System.Windows.Media.Drawing>具有控制項<xref:System.Windows.Controls.Image>的 ，<xref:System.Windows.Media.DrawingImage>請使用<xref:System.Windows.Controls.Image>作為 控制項<xref:System.Windows.Controls.Image.Source%2A>的，<xref:System.Windows.Media.DrawingImage>並將物件的屬性<xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType>設置為要顯示的圖形。  
  
 下面的示例使用<xref:System.Windows.Media.DrawingImage>和 控制項<xref:System.Windows.Controls.Image>來顯示 。 <xref:System.Windows.Media.GeometryDrawing> 此範例會產生下列輸出。  
  
 ![兩個橢圓形的 GeometryDrawing](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>
## <a name="paint-an-object-with-a-drawing"></a>使用繪圖繪製物件  
 A<xref:System.Windows.Media.DrawingBrush>是一種使用繪圖物件繪製區域的畫筆類型。 您可以使用它來繪製含有繪圖的任何圖形物件。 的屬性<xref:System.Windows.Media.Drawing><xref:System.Windows.Media.DrawingBrush>描述其<xref:System.Windows.Media.DrawingBrush.Drawing%2A>。 要使用<xref:System.Windows.Media.Drawing><xref:System.Windows.Media.DrawingBrush>渲染 ， 使用 畫筆的屬性<xref:System.Windows.Media.Drawing>將其添加到畫筆，並使用畫筆繪製繪圖物件（如控制項或面板）。  
  
 以下示例使用 使用<xref:System.Windows.Media.DrawingBrush>從<xref:System.Windows.Media.GeometryDrawing><xref:System.Windows.Shapes.Shape.Fill%2A>創建的<xref:System.Windows.Shapes.Rectangle>模式繪製 的 。 此範例會產生下列輸出。  
  
 ![並排顯示的 DrawingBrush](./media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
搭配 DrawingBrush 使用的 GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 該<xref:System.Windows.Media.DrawingBrush>類提供了各種選項來拉伸和平鋪其內容。 有關 的詳細資訊<xref:System.Windows.Media.DrawingBrush>，請參閱["具有圖像、繪圖和視覺物件"的繪畫](painting-with-images-drawings-and-visuals.md)概述。  
  
<a name="renderingwithvisualsection"></a>
## <a name="render-a-drawing-with-a-visual"></a>使用視覺物件呈現繪圖  
 是<xref:System.Windows.Media.DrawingVisual>一種視覺物件類型，旨在渲染圖形。 開發人員若想要建置高度自訂的圖形化環境，可以選擇直接在視覺分層處理，但這不屬於本概觀的說明範圍。 如需詳細資訊，請參閱[使用 DrawingVisual 物件](using-drawingvisual-objects.md)概觀。  
  
<a name="drawingcontextobjects"></a>
## <a name="drawingcontext-objects"></a>DrawingContext 物件  
 類<xref:System.Windows.Media.DrawingContext>使您能夠使用可視內容填充<xref:System.Windows.Media.Visual>或<xref:System.Windows.Media.Drawing>。 許多此類較低級別的繪圖物件使用 ，<xref:System.Windows.Media.DrawingContext>因為它非常有效地描述圖形內容。  
  
 儘管<xref:System.Windows.Media.DrawingContext>繪製方法看起來與<xref:System.Drawing.Graphics?displayProperty=nameWithType>類型的繪製方法類似，但它們實際上非常不同。 <xref:System.Windows.Media.DrawingContext>與保留模式圖形系統一起使用，而<xref:System.Drawing.Graphics?displayProperty=nameWithType>該類型與即時模式圖形系統一起使用。 使用<xref:System.Windows.Media.DrawingContext>物件的繪製命令時，實際上存儲一組呈現指令（儘管確切的存儲機制取決於提供<xref:System.Windows.Media.DrawingContext>）的物件類型，圖形系統稍後將使用該指令。您沒有即時繪製到螢幕。 有關 Windows 演示基礎 （WPF） 圖形系統工作原理的詳細資訊，請參閱[WPF 圖形呈現概述](wpf-graphics-rendering-overview.md)。  
  
 你從來沒有直接具現化; <xref:System.Windows.Media.DrawingContext>但是，可以從某些方法（如 和<xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType><xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>獲取繪圖上下文）獲取繪圖上下文。  
  
<a name="enumeratevisualcontents"></a>
## <a name="enumerate-the-contents-of-a-visual"></a>列舉視覺物件的內容  
 除了其他用途外，<xref:System.Windows.Media.Drawing>物件還提供用於枚舉 的物件模型。 <xref:System.Windows.Media.Visual>  
  
 下面的示例使用 方法<xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A>檢索<xref:System.Windows.Media.DrawingGroup>的值<xref:System.Windows.Media.Visual>並枚舉它。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- [2D 圖形和影像處理](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)
- [幾何概觀](geometry-overview.md)
- [WPF 中圖案和基本繪圖概觀](shapes-and-basic-drawing-in-wpf-overview.md)
- [WPF 圖形轉譯概觀](wpf-graphics-rendering-overview.md)
- [Freezable 物件概觀](../advanced/freezable-objects-overview.md)
- [如何使用主題](drawings-how-to-topics.md)
