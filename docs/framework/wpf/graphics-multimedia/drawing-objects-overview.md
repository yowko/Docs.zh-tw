---
title: 繪圖物件概觀
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ImageDrawing objects [WPF]
- GlyphRunDrawing objects [WPF]
- GeometryDrawing objects [WPF]
- drawings [WPF], about drawings
- Drawing objects [WPF]
- DrawingGroup objects [WPF]
ms.assetid: 9b5ce5c0-e204-4320-a7a8-0b2210d62f88
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3672e4b1deacd8fb50a5318270854daae9c74761
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="drawing-objects-overview"></a>繪圖物件概觀
本主題將介紹<xref:System.Windows.Media.Drawing>物件，並說明如何使用它們來有效率地繪製圖案、 點陣圖、 文字與媒體。 使用<xref:System.Windows.Media.Drawing>物件，當您建立美工圖案、 繪製<xref:System.Windows.Media.DrawingBrush>，或使用<xref:System.Windows.Media.Visual>物件。  
  
 
  
<a name="whatisadrawingsection"></a>   
## <a name="what-is-a-drawing-object"></a>什麼是繪圖物件？  
 A<xref:System.Windows.Media.Drawing>物件描述可見的內容，例如圖形、 點陣圖、 視訊或一行文字。 不同類型的繪圖可描繪不同類型的內容。 以下列出不同類型的繪圖物件。  
  
-   <xref:System.Windows.Media.GeometryDrawing> – 繪製圖形。  
  
-   <xref:System.Windows.Media.ImageDrawing> – 繪製影像。  
  
-   <xref:System.Windows.Media.GlyphRunDrawing> – 繪製文字。  
  
-   <xref:System.Windows.Media.VideoDrawing> – 播放音訊或視訊檔案。  
  
-   <xref:System.Windows.Media.DrawingGroup> – 繪製其他繪圖。 您可以使用繪圖群組，來將其他繪圖結合為單一複合繪圖。  
  
 <xref:System.Windows.Media.Drawing> 物件是多用途;您可以使用許多方式<xref:System.Windows.Media.Drawing>物件。  
  
-   顯示做為映像使用<xref:System.Windows.Media.DrawingImage>和<xref:System.Windows.Controls.Image>控制項。  
  
-   您可以使用它與<xref:System.Windows.Media.DrawingBrush>來繪製物件，例如<xref:System.Windows.Controls.Page.Background%2A>的<xref:System.Windows.Controls.Page>。  
  
-   您可以使用它來描述的外觀<xref:System.Windows.Media.DrawingVisual>。  
  
-   您可以使用它來列舉的內容<xref:System.Windows.Media.Visual>。  
  
 WPF 提供其他能夠繪製圖形、點陣圖、文字及媒體的物件類型。 例如，您也可以使用<xref:System.Windows.Shapes.Shape>要繪製形狀、 物件和<xref:System.Windows.Controls.MediaElement>控制項提供另一種方式新增視訊到您的應用程式。 因此當您應該使用<xref:System.Windows.Media.Drawing>物件？ 您可以犧牲架構層級功能，以取得效能優勢或當您需要<xref:System.Windows.Freezable>功能。 因為<xref:System.Windows.Media.Drawing>物件缺少支援[配置](../../../../docs/framework/wpf/advanced/layout.md)、 輸入，並將焦點放，它們提供的效能優勢，因此適合用來描述背景、 美工圖案，並針對低層級與繪圖<xref:System.Windows.Media.Visual>物件。  
  
 因為它們是型別<xref:System.Windows.Freezable>物件<xref:System.Windows.Media.Drawing>物件取得數個特殊的功能，包括下列： 它們可以宣告為[資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)、 變成唯讀，以改善的多個物件之間共用效能考量，複製，而且進行安全執行緒。 如需有關所提供的不同功能<xref:System.Windows.Freezable>物件，請參閱[Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
<a name="drawinggeometriessection"></a>   
## <a name="draw-a-shape"></a>繪製圖形  
 若要繪製圖形，您使用<xref:System.Windows.Media.GeometryDrawing>。 幾何繪圖的<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>屬性會描述要繪製，其<xref:System.Windows.Media.GeometryDrawing.Brush%2A>屬性會描述如何應該繪製形狀內部，而且其<xref:System.Windows.Media.GeometryDrawing.Pen%2A>屬性會描述應該如何繪製控制項外框。  
  
 下列範例會使用<xref:System.Windows.Media.GeometryDrawing>繪製圖形。 所描述的圖案<xref:System.Windows.Media.GeometryGroup>和兩個<xref:System.Windows.Media.EllipseGeometry>物件。 圖形內部的繪製與<xref:System.Windows.Media.LinearGradientBrush>和使用繪製控制項外框<xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>。  
  
 這個範例會建立下列<xref:System.Windows.Media.GeometryDrawing>。  
  
 ![橢圓形兩個橢圓形的 GeometryDrawing](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 如需完整的範例，請參閱[建立 GeometryDrawing](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-geometrydrawing.md)。  
  
 其他<xref:System.Windows.Media.Geometry>類別，例如<xref:System.Windows.Media.PathGeometry>可讓您藉由建立曲線和弧形建立更複雜的圖形。 如需有關<xref:System.Windows.Media.Geometry>物件，請參閱[幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)。  
  
 如需有關繪製圖案與未使用的其他方式<xref:System.Windows.Media.Drawing>物件，請參閱[圖案和基本繪圖概觀 WPF 中](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)。  
  
<a name="drawingimagessection"></a>   
## <a name="draw-an-image"></a>繪製影像  
 若要繪製影像，您使用<xref:System.Windows.Media.ImageDrawing>。 <xref:System.Windows.Media.ImageDrawing>物件的<xref:System.Windows.Media.ImageDrawing.ImageSource%2A>屬性會描述要繪製，映像和其<xref:System.Windows.Media.ImageDrawing.Rect%2A>屬性會定義要在繪製影像的區域。  
  
 下列範例會在 (75,75) 繪製 100 x 100 像素的影像。 下圖顯示<xref:System.Windows.Media.ImageDrawing>範例所建立。 若要顯示的範圍加入灰色框線<xref:System.Windows.Media.ImageDrawing>。  
  
 ![100 x 100 ImageDrawing 在&#40;75，75&#41;](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
100 x 100 的 ImageDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 如需有關影像的詳細資訊，請參閱[影像處理概觀](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)。  
  
<a name="playmedia"></a>   
## <a name="play-media-code-only"></a>播放媒體 (僅程式碼)  
  
> [!NOTE]
>  雖然您可以宣告<xref:System.Windows.Media.VideoDrawing>中[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，您只可以載入並播放媒體使用程式碼。 若要播放視訊[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，使用<xref:System.Windows.Controls.MediaElement>改為。  
  
 若要播放的音訊或視訊檔案，您使用<xref:System.Windows.Media.VideoDrawing>和<xref:System.Windows.Media.MediaPlayer>。 有兩種方法可以載入及播放媒體。 第一個方法是使用<xref:System.Windows.Media.MediaPlayer>和<xref:System.Windows.Media.VideoDrawing>本身，和第二個方法是建立您自己<xref:System.Windows.Media.MediaTimeline>搭配<xref:System.Windows.Media.MediaPlayer>和<xref:System.Windows.Media.VideoDrawing>。  
  
> [!NOTE]
>  利用您的應用程式散發媒體時，您無法跟散發影像一樣，使用媒體檔案當作專案資源。 在您的專案檔中，您必須改為將媒體類型設定為 `Content`，並將 `CopyToOutputDirectory` 設定為 `PreserveNewest` 或 `Always`。  
  
 若要播放媒體，而不需建立您自己<xref:System.Windows.Media.MediaTimeline>，執行下列步驟。  
  
1.  建立 <xref:System.Windows.Media.MediaPlayer> 物件。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2.  使用<xref:System.Windows.Media.MediaPlayer.Open%2A>方法以載入的媒體檔案。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3.  建立 <xref:System.Windows.Media.VideoDrawing>。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4.  指定的大小和位置，藉由設定繪製媒體<xref:System.Windows.Media.VideoDrawing.Rect%2A>屬性<xref:System.Windows.Media.VideoDrawing>。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5.  設定<xref:System.Windows.Media.VideoDrawing.Player%2A>屬性<xref:System.Windows.Media.VideoDrawing>與<xref:System.Windows.Media.MediaPlayer>您所建立。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6.  使用<xref:System.Windows.Media.MediaPlayer.Play%2A>方法<xref:System.Windows.Media.MediaPlayer>開始播放媒體。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 下列範例會使用<xref:System.Windows.Media.VideoDrawing>和<xref:System.Windows.Media.MediaPlayer>播放視訊檔案一次。  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 若要取得媒體的詳細計時控制權，請使用<xref:System.Windows.Media.MediaTimeline>與<xref:System.Windows.Media.MediaPlayer>和<xref:System.Windows.Media.VideoDrawing>物件。 <xref:System.Windows.Media.MediaTimeline>可讓您指定是否應該重複視訊。 若要使用<xref:System.Windows.Media.MediaTimeline>與<xref:System.Windows.Media.VideoDrawing>，執行下列步驟：  
  
1.  宣告<xref:System.Windows.Media.MediaTimeline>並設定其計時行為。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2.  建立<xref:System.Windows.Media.MediaClock>從<xref:System.Windows.Media.MediaTimeline>。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3.  建立<xref:System.Windows.Media.MediaPlayer>並用<xref:System.Windows.Media.MediaClock>設定其<xref:System.Windows.Media.MediaPlayer.Clock%2A>屬性。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4.  建立<xref:System.Windows.Media.VideoDrawing>並指派<xref:System.Windows.Media.MediaPlayer>至<xref:System.Windows.Media.VideoDrawing.Player%2A>屬性<xref:System.Windows.Media.VideoDrawing>。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 下列範例會使用<xref:System.Windows.Media.MediaTimeline>與<xref:System.Windows.Media.MediaPlayer>和<xref:System.Windows.Media.VideoDrawing>重複播放視訊。  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 請注意，當您使用<xref:System.Windows.Media.MediaTimeline>，您會使用互動式<xref:System.Windows.Media.Animation.ClockController>從傳回<xref:System.Windows.Media.Animation.Clock.Controller%2A>屬性<xref:System.Windows.Media.MediaClock>控制媒體播放，而不是互動式方法<xref:System.Windows.Media.MediaPlayer>。  
  
<a name="drawtext"></a>   
## <a name="draw-text"></a>繪製文字  
 若要繪製文字，您使用<xref:System.Windows.Media.GlyphRunDrawing>和<xref:System.Windows.Media.GlyphRun>。 下列範例會使用<xref:System.Windows.Media.GlyphRunDrawing>來繪製文字"Hello World"。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 A<xref:System.Windows.Media.GlyphRun>是低階物件適用於搭配固定格式文件簡報和列印的案例。 螢幕上繪製文字的較簡單方式是使用<xref:System.Windows.Controls.Label>或<xref:System.Windows.Controls.TextBlock>。 如需有關<xref:System.Windows.Media.GlyphRun>，請參閱[GlyphRun 物件和圖像 （glyph） 項目簡介](../../../../docs/framework/wpf/advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md)概觀。  
  
<a name="compositedrawingssection"></a>   
## <a name="composite-drawings"></a>複合繪圖  
 A<xref:System.Windows.Media.DrawingGroup>可讓您結合成單一複合繪圖的多個圖形。 使用<xref:System.Windows.Media.DrawingGroup>，您可以將圖形、 影像和文字結合成單一<xref:System.Windows.Media.Drawing>物件。  
  
 下列範例會使用<xref:System.Windows.Media.DrawingGroup>結合兩個<xref:System.Windows.Media.GeometryDrawing>物件和<xref:System.Windows.Media.ImageDrawing>物件。 此範例會產生下列輸出。  
  
 ![多個圖形的 DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")  
複合圖形  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 A<xref:System.Windows.Media.DrawingGroup>也可讓您套用到其內容的不透明度遮罩、 轉換、 點陣圖效果，以及其他作業。 <xref:System.Windows.Media.DrawingGroup> 作業會依下列順序套用： <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>， <xref:System.Windows.Media.DrawingGroup.Opacity%2A>， <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>， <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>， <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>，然後<xref:System.Windows.Media.DrawingGroup.Transform%2A>。  
  
 下圖中顯示的順序<xref:System.Windows.Media.DrawingGroup>作業套用。  
  
 ![DrawingGroup 作業的順序](../../../../docs/framework/wpf/graphics-multimedia/media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
DrawingGroup 作業的順序  
  
 下表描述可用來操作屬性<xref:System.Windows.Media.DrawingGroup>物件的內容。  
  
|屬性|描述|圖例|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|變更的選定部分的不透明度<xref:System.Windows.Media.DrawingGroup>內容。 如需範例，請參閱[操作說明︰控制繪圖的不透明度](http://msdn.microsoft.com/library/68580652-7d32-4d27-93cc-a5148cf4d5ee)。|![具有不透明度遮罩的 DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|一致的方式變更的不透明度<xref:System.Windows.Media.DrawingGroup>內容。 使用這個屬性來讓<xref:System.Windows.Media.Drawing>透明或半透明。 如需範例，請參閱[操作說明︰對繪圖套用不透明度遮罩](http://msdn.microsoft.com/library/d77b420b-9be2-479c-a45e-82f4da30eb9f)。|![具有不同不透明度設定的 DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|適用於<xref:System.Windows.Media.Effects.BitmapEffect>至<xref:System.Windows.Media.DrawingGroup>內容。 如需範例，請參閱[操作說明︰對繪圖套用 BitmapEffect](http://msdn.microsoft.com/library/c5b1de83-8d09-47fb-96db-5f174471f4b5)。|![具有 BlurBitmapEffect 的 DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|剪輯<xref:System.Windows.Media.DrawingGroup>內容區域，您將描述如何使用<xref:System.Windows.Media.Geometry>。 如需範例，請參閱[操作說明︰裁剪繪圖](http://msdn.microsoft.com/library/1f7d8a2c-c3c2-42cb-a542-e6796f9fb058)。|![具有已定義之裁剪區域的 DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|沿著指定的標線將裝置獨立像素貼齊裝置像素。 這個屬性可用於確保在低 DPI 顯示器上呈現清晰的細緻圖形。 如需範例，請參閱[對繪圖套用 GuidelineSet](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-a-guidelineset-to-a-drawing.md)。|![具有與不具 GuidelineSet 的 DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|轉換<xref:System.Windows.Media.DrawingGroup>內容。 如需範例，請參閱[操作說明︰對繪圖套用轉換](http://msdn.microsoft.com/library/0d525f2b-682d-4d67-9660-cf46929fbabd)。|![旋轉後的 DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>   
## <a name="display-a-drawing-as-an-image"></a>將繪圖顯示為影像  
 若要顯示<xref:System.Windows.Media.Drawing>與<xref:System.Windows.Controls.Image>控制，請使用<xref:System.Windows.Media.DrawingImage>為<xref:System.Windows.Controls.Image>控制項的<xref:System.Windows.Controls.Image.Source%2A>並設定<xref:System.Windows.Media.DrawingImage>物件的<xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType>繪製您想要顯示的屬性。  
  
 下列範例會使用<xref:System.Windows.Media.DrawingImage>和<xref:System.Windows.Controls.Image>控制項來顯示<xref:System.Windows.Media.GeometryDrawing>。 此範例會產生下列輸出。  
  
 ![橢圓形兩個橢圓形的 GeometryDrawing](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>   
## <a name="paint-an-object-with-a-drawing"></a>使用繪圖繪製物件  
 A<xref:System.Windows.Media.DrawingBrush>是一種使用繪圖物件繪製區域的筆刷。 您可以使用它來繪製含有繪圖的任何圖形物件。 <xref:System.Windows.Media.Drawing>屬性<xref:System.Windows.Media.DrawingBrush>描述其<xref:System.Windows.Media.DrawingBrush.Drawing%2A>。 要呈現<xref:System.Windows.Media.Drawing>與<xref:System.Windows.Media.DrawingBrush>，將它新增到使用筆刷的筆刷<xref:System.Windows.Media.Drawing>屬性並用來繪製圖形化的筆刷物件，例如控制項或面板。  
  
 下列範例會使用<xref:System.Windows.Media.DrawingBrush>來繪製<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>模式中從建立<xref:System.Windows.Media.GeometryDrawing>。 此範例會產生下列輸出。  
  
 ![並排顯示的 DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
搭配 DrawingBrush 使用的 GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 <xref:System.Windows.Media.DrawingBrush>類別會提供各種不同的自動縮放和並排顯示其內容的選項。 如需有關<xref:System.Windows.Media.DrawingBrush>，請參閱[使用映像、 繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)概觀。  
  
<a name="renderingwithvisualsection"></a>   
## <a name="render-a-drawing-with-a-visual"></a>使用視覺物件呈現繪圖  
 A<xref:System.Windows.Media.DrawingVisual>是一種設計用來呈現繪圖的視覺物件。 開發人員若想要建置高度自訂的圖形化環境，可以選擇直接在視覺分層處理，但這不屬於本概觀的說明範圍。 如需詳細資訊，請參閱[使用 DrawingVisual 物件](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)概觀。  
  
<a name="drawingcontextobjects"></a>   
## <a name="drawingcontext-objects"></a>DrawingContext 物件  
 <xref:System.Windows.Media.DrawingContext>類別可讓您擴展<xref:System.Windows.Media.Visual>或<xref:System.Windows.Media.Drawing>的視覺內容。 許多這類的較低層級圖形物件使用<xref:System.Windows.Media.DrawingContext>因為它會非常有效率的方式說明圖形化的內容。  
  
 雖然<xref:System.Windows.Media.DrawingContext>繪製方法看起來類似的繪製方法<xref:System.Drawing.Graphics?displayProperty=nameWithType>類型，它們是實際非常不同。 <xref:System.Windows.Media.DrawingContext> 是用於保留的模式的圖形系統，而<xref:System.Drawing.Graphics?displayProperty=nameWithType>即時模式圖形系統搭配使用類型。 當您使用<xref:System.Windows.Media.DrawingContext>物件的繪製命令中，您實際上儲存一組轉譯指令 (雖然正確儲存機制而定，提供物件的類型<xref:System.Windows.Media.DrawingContext>)，將稍後使用的圖形系統，;不會繪製在即時的畫面。 如需有關 Windows Presentation Foundation (WPF) 圖形系統的運作方式的詳細資訊，請參閱[WPF 圖形呈現概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)。  
  
 您永遠不會直接具現化<xref:System.Windows.Media.DrawingContext>; 可以不過，購買繪圖內容從特定方法，例如<xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType>和<xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>。  
  
<a name="enumeratevisualcontents"></a>   
## <a name="enumerate-the-contents-of-a-visual"></a>列舉視覺物件的內容  
 除了其他用途，<xref:System.Windows.Media.Drawing>物件也會提供物件模型來列舉的內容<xref:System.Windows.Media.Visual>。  
  
 下列範例會使用<xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A>方法來擷取<xref:System.Windows.Media.DrawingGroup>值<xref:System.Windows.Media.Visual>和列舉它。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.Drawing>  
 <xref:System.Windows.Media.DrawingGroup>  
 [2D 圖形和影像處理](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [WPF 中圖案和基本繪圖概觀](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [WPF 圖形轉譯概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/graphics-multimedia/drawings-how-to-topics.md)
