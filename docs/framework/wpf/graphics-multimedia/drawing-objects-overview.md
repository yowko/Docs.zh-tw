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
ms.openlocfilehash: d739865a692fa5ef448eba91369015580e5eda97
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916306"
---
# <a name="drawing-objects-overview"></a>繪圖物件概觀
本主題介紹<xref:System.Windows.Media.Drawing>物件，並說明如何使用它們來有效率地繪製圖形、點陣圖、文字和媒體。 當<xref:System.Windows.Media.Drawing>您建立美工圖案、使用繪製<xref:System.Windows.Media.DrawingBrush>，或使用<xref:System.Windows.Media.Visual>物件時，請使用物件。  

<a name="whatisadrawingsection"></a>   
## <a name="what-is-a-drawing-object"></a>什麼是繪圖物件？  
 <xref:System.Windows.Media.Drawing>物件描述可見內容，例如圖形、點陣圖、影片或一行文字。 不同類型的繪圖可描繪不同類型的內容。 以下列出不同類型的繪圖物件。  
  
- <xref:System.Windows.Media.GeometryDrawing>–繪製圖形。  
  
- <xref:System.Windows.Media.ImageDrawing>–繪製影像。  
  
- <xref:System.Windows.Media.GlyphRunDrawing>–繪製文字。  
  
- <xref:System.Windows.Media.VideoDrawing>–播放音訊或影片檔案。  
  
- <xref:System.Windows.Media.DrawingGroup>–繪製其他繪圖。 您可以使用繪圖群組，來將其他繪圖結合為單一複合繪圖。  
  
 <xref:System.Windows.Media.Drawing>物件很多功能;有許多方式可以使用<xref:System.Windows.Media.Drawing>物件。  
  
- 您可以使用<xref:System.Windows.Media.DrawingImage> <xref:System.Windows.Controls.Image>和控制項，將其顯示為影像。  
  
- 您可以將它與<xref:System.Windows.Media.DrawingBrush>搭配使用，以繪製物件，例如<xref:System.Windows.Controls.Page.Background%2A> <xref:System.Windows.Controls.Page>的。  
  
- 您可以使用它來描述的外觀<xref:System.Windows.Media.DrawingVisual>。  
  
- 您可以使用它來列舉的內容<xref:System.Windows.Media.Visual>。  
  
 WPF 提供其他能夠繪製圖形、點陣圖、文字及媒體的物件類型。 例如，您也可以使用<xref:System.Windows.Shapes.Shape>物件繪製圖形，而控制項則<xref:System.Windows.Controls.MediaElement>提供另一種方式來將影片新增至您的應用程式。 那麼，您應該使用<xref:System.Windows.Media.Drawing>物件嗎？ 當您可以犧牲架構層級功能，以獲得效能優勢或需要<xref:System.Windows.Freezable>功能時。 因為<xref:System.Windows.Media.Drawing>物件不支援配置[、輸入](../advanced/layout.md)和焦點，所以它們會提供效能優勢，使其適合用<xref:System.Windows.Media.Visual>來描述背景、美工圖案和物件的低層級繪圖。  
  
 因為它們是類型<xref:System.Windows.Freezable>物件， <xref:System.Windows.Media.Drawing>所以物件會取得數個特殊功能，包括下列各項：它們可以宣告為[資源](../advanced/xaml-resources.md)，在多個物件之間共用，使其成為唯讀以改善效能、複製和設為安全線程。 如需<xref:System.Windows.Freezable>物件所提供之不同功能的詳細資訊，請參閱可[凍結物件的總覽](../advanced/freezable-objects-overview.md)。  
  
<a name="drawinggeometriessection"></a>   
## <a name="draw-a-shape"></a>繪製圖形  
 若要繪製圖形，您可以使用<xref:System.Windows.Media.GeometryDrawing>。 幾何繪圖的<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>屬性會描述要繪製的形狀，其<xref:System.Windows.Media.GeometryDrawing.Brush%2A>屬性會描述圖形內部的繪製方式，而其<xref:System.Windows.Media.GeometryDrawing.Pen%2A>屬性則描述其外框的繪製方式。  
  
 下列範例會使用<xref:System.Windows.Media.GeometryDrawing>來繪製圖形。 圖形是由<xref:System.Windows.Media.GeometryGroup>和兩個<xref:System.Windows.Media.EllipseGeometry>物件所描述。 圖形的內部會使用<xref:System.Windows.Media.LinearGradientBrush>繪製，而且其外框會<xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>使用繪製。  
  
 這個範例會建立下列<xref:System.Windows.Media.GeometryDrawing>。  
  
 ![兩個橢圓形的 GeometryDrawing](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 如需完整的範例，請參閱[建立 GeometryDrawing](how-to-create-a-geometrydrawing.md)。  
  
 其他<xref:System.Windows.Media.Geometry>類別（ <xref:System.Windows.Media.PathGeometry>例如）可讓您藉由建立曲線和弧形來建立更複雜的圖形。 如需<xref:System.Windows.Media.Geometry>物件的詳細資訊，請參閱[幾何總覽](geometry-overview.md)。  
  
 如需繪製不使用<xref:System.Windows.Media.Drawing>物件之圖形的其他方式的詳細資訊，請參閱[WPF 中的圖形和基本繪圖總覽](shapes-and-basic-drawing-in-wpf-overview.md)。  
  
<a name="drawingimagessection"></a>   
## <a name="draw-an-image"></a>繪製影像  
 若要繪製影像，請使用<xref:System.Windows.Media.ImageDrawing>。 物件的<xref:System.Windows.Media.ImageDrawing.ImageSource%2A>屬性會描述要繪製的影像，而其<xref:System.Windows.Media.ImageDrawing.Rect%2A>屬性會定義繪製影像的區域。 <xref:System.Windows.Media.ImageDrawing>  
  
 下列範例會在 (75,75) 繪製 100 x 100 像素的影像。 下圖顯示範例所<xref:System.Windows.Media.ImageDrawing>建立的。 已加入灰色框線來顯示的範圍<xref:System.Windows.Media.ImageDrawing>。  
  
 ![100 by 100 ImageDrawing 以&#40;75，75繪製&#41; ](./media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
100 x 100 的 ImageDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 如需有關影像的詳細資訊，請參閱[影像處理概觀](imaging-overview.md)。  
  
<a name="playmedia"></a>   
## <a name="play-media-code-only"></a>播放媒體 (僅程式碼)  
  
> [!NOTE]
> 雖然您可以<xref:System.Windows.Media.VideoDrawing>在中[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]宣告，但只能使用程式碼來載入和播放其媒體。 若要播放中[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]的影片， <xref:System.Windows.Controls.MediaElement>請改用。  
  
 若要播放音訊或影片檔案，請使用<xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer>和。 有兩種方法可以載入及播放媒體。 第一種<xref:System.Windows.Media.MediaPlayer>是使用<xref:System.Windows.Media.VideoDrawing>和本身，第二種方式是建立您自己<xref:System.Windows.Media.MediaTimeline>的<xref:System.Windows.Media.MediaPlayer> ，以搭配和<xref:System.Windows.Media.VideoDrawing>使用。  
  
> [!NOTE]
> 利用您的應用程式散發媒體時，您無法跟散發影像一樣，使用媒體檔案當作專案資源。 在您的專案檔中，您必須改為將媒體類型設定為 `Content`，並將 `CopyToOutputDirectory` 設定為 `PreserveNewest` 或 `Always`。  
  
 若要在不自行<xref:System.Windows.Media.MediaTimeline>建立的情況下播放媒體，請執行下列步驟。  
  
1. 建立 <xref:System.Windows.Media.MediaPlayer> 物件。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2. <xref:System.Windows.Media.MediaPlayer.Open%2A>使用方法來載入媒體檔案。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3. 建立 <xref:System.Windows.Media.VideoDrawing>。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4. 藉由設定<xref:System.Windows.Media.VideoDrawing.Rect%2A>的屬性<xref:System.Windows.Media.VideoDrawing>，指定要繪製媒體的大小和位置。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5. 將的<xref:System.Windows.Media.VideoDrawing.Player%2A> <xref:System.Windows.Media.VideoDrawing>屬性設定為您所<xref:System.Windows.Media.MediaPlayer>建立的。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6. 使用的<xref:System.Windows.Media.MediaPlayer>方法來開始播放媒體。 <xref:System.Windows.Media.MediaPlayer.Play%2A>  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 下列範例會使用<xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer>和來播放影片檔案一次。  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 若要對媒體取得額外的時間控制，請<xref:System.Windows.Media.MediaTimeline>使用<xref:System.Windows.Media.MediaPlayer>搭配和<xref:System.Windows.Media.VideoDrawing>物件的。 可<xref:System.Windows.Media.MediaTimeline>讓您指定是否應該重複影片。 若要搭配<xref:System.Windows.Media.MediaTimeline>使用<xref:System.Windows.Media.VideoDrawing>，請執行下列步驟：  
  
1. <xref:System.Windows.Media.MediaTimeline>宣告並設定其計時行為。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2. <xref:System.Windows.Media.MediaClock> 從<xref:System.Windows.Media.MediaTimeline>建立。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3. 建立並使用來設定其<xref:System.Windows.Media.MediaPlayer.Clock%2A>屬性。 <xref:System.Windows.Media.MediaClock> <xref:System.Windows.Media.MediaPlayer>  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4. 建立，並<xref:System.Windows.Media.MediaPlayer>將指派<xref:System.Windows.Media.VideoDrawing.Player%2A> 給的屬性。<xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.VideoDrawing>  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 下列範例會將<xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaPlayer>與和<xref:System.Windows.Media.VideoDrawing>搭配使用，以重複播放影片。  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 請注意，當您<xref:System.Windows.Media.MediaTimeline>使用時，您會使用<xref:System.Windows.Media.MediaClock>從<xref:System.Windows.Media.Animation.ClockController> <xref:System.Windows.Media.Animation.Clock.Controller%2A>的屬性傳回的互動式來控制媒體播放，而不是的互動式方法<xref:System.Windows.Media.MediaPlayer>。  
  
<a name="drawtext"></a>   
## <a name="draw-text"></a>繪製文字  
 若要繪製文字，請使用<xref:System.Windows.Media.GlyphRunDrawing> <xref:System.Windows.Media.GlyphRun>和。 下列範例會使用<xref:System.Windows.Media.GlyphRunDrawing>來繪製「Hello World」文字。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 <xref:System.Windows.Media.GlyphRun>是一個低層級物件，適用于固定格式的檔簡報和列印案例。 將文字繪製到螢幕的較簡單方式是使用<xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.TextBlock>或。 如需的詳細<xref:System.Windows.Media.GlyphRun>資訊，請參閱[GlyphRun 物件簡介和圖像元素](../advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md)總覽。  
  
<a name="compositedrawingssection"></a>   
## <a name="composite-drawings"></a>複合繪圖  
 可<xref:System.Windows.Media.DrawingGroup>讓您將多個繪圖結合成單一複合繪圖。 藉由使用<xref:System.Windows.Media.DrawingGroup>，您可以將圖形、影像和文字結合成單一<xref:System.Windows.Media.Drawing>物件。  
  
 下列範例會使用<xref:System.Windows.Media.DrawingGroup>來結合兩個<xref:System.Windows.Media.GeometryDrawing>物件和一個<xref:System.Windows.Media.ImageDrawing>物件。 此範例會產生下列輸出。  
  
 ![具有多個繪圖的 DrawingGroup](./media/graphicsmm-simple.jpg "graphicsmm_simple")  
複合圖形  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 <xref:System.Windows.Media.DrawingGroup>也可讓您將不透明度遮罩、轉換、點陣圖效果和其他作業套用至其內容。 <xref:System.Windows.Media.DrawingGroup>作業的套用順序如下： <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>、 <xref:System.Windows.Media.DrawingGroup.Opacity%2A>、 <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>、 <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>、 <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>和<xref:System.Windows.Media.DrawingGroup.Transform%2A>。  
  
 下圖顯示套用<xref:System.Windows.Media.DrawingGroup>作業的順序。  
  
 ![作業的 DrawingGroup 順序](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
DrawingGroup 作業的順序  
  
 下表描述您可以用來操作<xref:System.Windows.Media.DrawingGroup>物件內容的屬性。  
  
|屬性|描述|圖例|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|改變所選部分<xref:System.Windows.Media.DrawingGroup>內容的不透明度。 如需範例，請參閱[如何：控制繪圖](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748242(v=vs.90))的不透明度。|![具有不透明度遮罩的 DrawingGroup](./media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|會一致地變更<xref:System.Windows.Media.DrawingGroup>內容的不透明度。 使用此屬性可讓<xref:System.Windows.Media.Drawing>透明或部分透明。 如需範例，請參閱[如何：將不透明度遮罩套用至繪圖](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms753195(v=vs.90))。|![具有不同不透明度設定的 DrawingGroup](./media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|將套用<xref:System.Windows.Media.Effects.BitmapEffect>至內容<xref:System.Windows.Media.DrawingGroup> 。 如需範例，請參閱[如何：將 BitmapEffect 套用至繪圖](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752341(v=vs.90))。|![具有 BlurBitmapEffect 的 DrawingGroup](./media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|使用將<xref:System.Windows.Media.DrawingGroup> <xref:System.Windows.Media.Geometry>內容裁剪至您所描述的區域。 如需範例，請參閱[如何：裁剪繪圖](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms743068(v=vs.90)) 。|![具有已定義之裁剪區域的 DrawingGroup](./media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|沿著指定的標線將裝置獨立像素貼齊裝置像素。 這個屬性可用於確保在低 DPI 顯示器上呈現清晰的細緻圖形。 如需範例，請參閱[對繪圖套用 GuidelineSet](how-to-apply-a-guidelineset-to-a-drawing.md)。|![具有與不具 GuidelineSet 的 DrawingGroup](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|<xref:System.Windows.Media.DrawingGroup>轉換內容。 如需範例，請參閱[如何：將轉換套用至繪圖](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms742304(v=vs.90))。|![旋轉後的 DrawingGroup](./media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>   
## <a name="display-a-drawing-as-an-image"></a>將繪圖顯示為影像  
 若要顯示<xref:System.Windows.Media.Drawing> <xref:System.Windows.Controls.Image>具有控制項的<xref:System.Windows.Controls.Image.Source%2A> <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> <xref:System.Windows.Media.DrawingImage> ，請使用<xref:System.Windows.Media.DrawingImage>做為控制項的，並將物件的屬性設定為您要顯示的繪圖。<xref:System.Windows.Controls.Image>  
  
 下列範例會使用<xref:System.Windows.Media.DrawingImage> <xref:System.Windows.Controls.Image>和控制項來顯示<xref:System.Windows.Media.GeometryDrawing>。 此範例會產生下列輸出。  
  
 ![兩個橢圓形的 GeometryDrawing](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>   
## <a name="paint-an-object-with-a-drawing"></a>使用繪圖繪製物件  
 <xref:System.Windows.Media.DrawingBrush>是一種使用繪圖物件繪製區域的筆刷。 您可以使用它來繪製含有繪圖的任何圖形物件。 的屬性會描述其<xref:System.Windows.Media.DrawingBrush.Drawing%2A>。 <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.Drawing> 若要使用轉譯<xref:System.Windows.Media.Drawing> ，請使用筆刷的屬性將其加入至筆刷，並使用筆刷繪製繪圖物件，例如控制項或面板。 <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.Drawing>  
  
 下列範例<xref:System.Windows.Media.DrawingBrush>會使用，以從<xref:System.Windows.Media.GeometryDrawing>建立<xref:System.Windows.Shapes.Shape.Fill%2A>的模式<xref:System.Windows.Shapes.Rectangle>繪製的。 此範例會產生下列輸出。  
  
 並排顯示![的 DrawingBrush](./media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
搭配 DrawingBrush 使用的 GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 <xref:System.Windows.Media.DrawingBrush>類別提供各種選項來延展和縮放其內容。 如需的詳細<xref:System.Windows.Media.DrawingBrush>資訊，請參閱[使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)。  
  
<a name="renderingwithvisualsection"></a>   
## <a name="render-a-drawing-with-a-visual"></a>使用視覺物件呈現繪圖  
 <xref:System.Windows.Media.DrawingVisual>是一種設計來呈現繪圖的視覺物件類型。 開發人員若想要建置高度自訂的圖形化環境，可以選擇直接在視覺分層處理，但這不屬於本概觀的說明範圍。 如需詳細資訊，請參閱[使用 DrawingVisual 物件](using-drawingvisual-objects.md)概觀。  
  
<a name="drawingcontextobjects"></a>   
## <a name="drawingcontext-objects"></a>DrawingContext 物件  
 類別可讓您<xref:System.Windows.Media.Drawing>使用視覺內容<xref:System.Windows.Media.Visual>填入或。 <xref:System.Windows.Media.DrawingContext> 許多這類較低層級的圖形<xref:System.Windows.Media.DrawingContext>物件都會使用，因為它會非常有效率地描述圖形內容。  
  
 雖然繪製方法看起來類似于<xref:System.Drawing.Graphics?displayProperty=nameWithType>類型的繪製方法，但實際上非常不同。 <xref:System.Windows.Media.DrawingContext> <xref:System.Windows.Media.DrawingContext>會與保留模式圖形系統搭配使用，而<xref:System.Drawing.Graphics?displayProperty=nameWithType>類型則與立即模式圖形系統搭配使用。 當您使用<xref:System.Windows.Media.DrawingContext>物件的繪製命令時，實際上是儲存一組轉譯指令（雖然實際的儲存機制取決於所提供的<xref:System.Windows.Media.DrawingContext>物件類型），而圖形系統稍後會使用此方法; 您不會即時繪製到螢幕上。 如需 Windows Presentation Foundation （WPF）圖形系統運作方式的詳細資訊，請參閱[WPF 圖形轉譯總覽](wpf-graphics-rendering-overview.md)。  
  
 您永遠不會直接<xref:System.Windows.Media.DrawingContext>具現化; 不過，您可以從特定方法（ <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType>例如和<xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>）取得繪圖內容。  
  
<a name="enumeratevisualcontents"></a>   
## <a name="enumerate-the-contents-of-a-visual"></a>列舉視覺物件的內容  
 除了其他用法以外， <xref:System.Windows.Media.Drawing>物件也會提供物件模型來列舉的內容。 <xref:System.Windows.Media.Visual>  
  
 下列範例會使用<xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A>方法來<xref:System.Windows.Media.DrawingGroup>取出的值<xref:System.Windows.Media.Visual> ，並加以列舉。  
  
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
- [HOW-TO 主題](drawings-how-to-topics.md)
