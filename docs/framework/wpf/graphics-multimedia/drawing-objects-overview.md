---
title: "繪圖物件概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Drawing 物件"
  - "DrawingGroup 物件"
  - "繪圖, 關於繪圖"
  - "GeometryDrawing 物件"
  - "GlyphRunDrawing 物件"
  - "ImageDrawing 物件"
ms.assetid: 9b5ce5c0-e204-4320-a7a8-0b2210d62f88
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# 繪圖物件概觀
本主題將介紹 <xref:System.Windows.Media.Drawing> 物件，並描述如何使用這些物件有效地繪製圖案、點陣圖、文字和媒體。  當您建立美工圖案、用 <xref:System.Windows.Media.DrawingBrush> 繪圖，或使用 <xref:System.Windows.Media.Visual> 物件時，請使用 <xref:System.Windows.Media.Drawing> 物件。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="whatisadrawingsection"></a>   
## 什麼是繪圖物件？  
 <xref:System.Windows.Media.Drawing> 物件可描繪可見內容，例如圖案、點陣圖、視訊或文字行。  不同類型的繪圖可描繪不同類型的內容。  以下列出不同類型的繪圖物件。  
  
-   <xref:System.Windows.Media.GeometryDrawing> – 繪製圖案。  
  
-   <xref:System.Windows.Media.ImageDrawing> – 繪製影像。  
  
-   <xref:System.Windows.Media.GlyphRunDrawing> – 繪製文字。  
  
-   <xref:System.Windows.Media.VideoDrawing> – 播放音訊檔或視訊檔。  
  
-   <xref:System.Windows.Media.DrawingGroup> – 繪製其他繪圖。  您可以使用繪圖群組，將其他繪圖結合為單一複合繪圖。  
  
 <xref:System.Windows.Media.Drawing> 物件的用途很多，您有許多方法可以使用 <xref:System.Windows.Media.Drawing> 物件。  
  
-   您可以使用 <xref:System.Windows.Media.DrawingImage> 和 <xref:System.Windows.Controls.Image> 控制項，將它顯示為影像。  
  
-   您可以將它與 <xref:System.Windows.Media.DrawingBrush> 搭配使用以繪製物件，例如 <xref:System.Windows.Controls.Page> 的 <xref:System.Windows.Controls.Page.Background%2A>。  
  
-   您可以使用它來描繪 <xref:System.Windows.Media.DrawingVisual> 的外觀。  
  
-   您可以使用它來列舉 <xref:System.Windows.Media.Visual> 的內容。  
  
 WPF 會提供其他型別的物件，這些物件也能夠繪製圖案、點陣圖、文字和媒體。  例如，您也可以使用 <xref:System.Windows.Shapes.Shape> 物件來繪製圖案，而 <xref:System.Windows.Controls.MediaElement> 控制項會提供另一種將視訊加入至應用程式的方法。  因此，何時應該使用 <xref:System.Windows.Media.Drawing> 物件呢？  就是當您可以犧牲架構層級功能以取得效能優點時，或當您需要 <xref:System.Windows.Freezable> 功能時。  因為 <xref:System.Windows.Media.Drawing> 物件不支援[配置](../../../../docs/framework/wpf/advanced/layout.md)、輸入和焦點，所以這類物件所提供的效能優點很適合於描繪背景、美工圖案，以及使用 <xref:System.Windows.Media.Visual> 物件的低階繪圖。  
  
 因為這類物件屬於 <xref:System.Windows.Freezable> 型別物件，所以 <xref:System.Windows.Media.Drawing> 物件會取得幾項特殊功能，包括：這類物件可以宣告為[資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)、供多個物件共用、設成唯讀以提升效能、複製以及設成安全執行緒 \(Thread\-Safe\)。  如需 <xref:System.Windows.Freezable> 物件提供之不同功能的詳細資訊，請參閱 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
<a name="drawinggeometriessection"></a>   
## 繪製圖案  
 若要繪製圖案，您可使用 <xref:System.Windows.Media.GeometryDrawing>。  幾何繪圖的 <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> 屬性描述要繪製的圖案，其 <xref:System.Windows.Media.GeometryDrawing.Brush%2A> 屬性描述應如何繪製圖案的內部，而其 <xref:System.Windows.Media.GeometryDrawing.Pen%2A> 屬性則描述應如何繪製其外框。  
  
 下列範例使用 <xref:System.Windows.Media.GeometryDrawing> 來繪製圖案。  此圖案是由一個 <xref:System.Windows.Media.GeometryGroup> 和兩個 <xref:System.Windows.Media.EllipseGeometry> 物件描述。  此圖案的內部是用 <xref:System.Windows.Media.LinearGradientBrush> 繪製，而其外框則是用 <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen> 繪製。  
  
 這個範例會建立下列 <xref:System.Windows.Media.GeometryDrawing>。  
  
 ![兩個橢圓形的 GeometryDrawing](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.png "graphicsmm\_geodraw")  
GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 如需完整的範例，請參閱 [建立 GeometryDrawing](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-geometrydrawing.md)。  
  
 <xref:System.Windows.Media.PathGeometry> 之類的其他 <xref:System.Windows.Media.Geometry> 類別可讓您建立曲線和弧線，進而建立更複雜的圖案。  如需 <xref:System.Windows.Media.Geometry> 物件的詳細資訊，請參閱[幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)。  
  
 如需其他不用 <xref:System.Windows.Media.Drawing> 物件繪製圖案之方法的詳細資訊，請參閱 [WPF 中圖案和基本繪圖概觀](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)。  
  
<a name="drawingimagessection"></a>   
## 繪製影像  
 若要繪製影像，您可使用 <xref:System.Windows.Media.ImageDrawing>。  <xref:System.Windows.Media.ImageDrawing> 物件的 <xref:System.Windows.Media.ImageDrawing.ImageSource%2A> 屬性描述要繪製的影像，而其 <xref:System.Windows.Media.ImageDrawing.Rect%2A> 屬性則定義繪製影像的區域。  
  
 下列範例會將影像繪製到位於 \(75,75\) 且為 100 x 100 [像素](GTMT)的矩形中。  下圖顯示此範例所建立的 <xref:System.Windows.Media.ImageDrawing>。  圖中會加入灰色框線以顯示 <xref:System.Windows.Media.ImageDrawing> 的界限。  
  
 ![在 &#40;75,75&#41; 繪製之 100 x 100 的 ImageDrawing](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm\_simple\_imagedrawing\_offset")  
100 x 100 ImageDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 如需影像的詳細資訊，請參閱[影像處理概觀](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)。  
  
<a name="playmedia"></a>   
## 播放媒體 \(僅限程式碼\)  
  
> [!NOTE]
>  雖然您可以在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中宣告 <xref:System.Windows.Media.VideoDrawing>，但您只能使用程式碼載入和播放其媒體。  若要在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中播放視訊，請改用 <xref:System.Windows.Controls.MediaElement>。  
  
 若要播放音訊或視訊檔，您可使用 <xref:System.Windows.Media.VideoDrawing> 和 <xref:System.Windows.Media.MediaPlayer>。  載入及播放媒體的方法有兩種。  第一種方法是使用 <xref:System.Windows.Media.MediaPlayer> 和 <xref:System.Windows.Media.VideoDrawing> 本身的功能，第二種方法是建立您自己的 <xref:System.Windows.Media.MediaTimeline> 來搭配 <xref:System.Windows.Media.MediaPlayer> 和 <xref:System.Windows.Media.VideoDrawing>。  
  
> [!NOTE]
>  使用您的應用程式散發媒體時，您不能像處理影像一樣，將媒體檔案當做專案資源來用。  在專案檔中，您必須改為將媒體類型設為 `Content`，並將 `CopyToOutputDirectory` 設為 `PreserveNewest` 或 `Always`。  
  
 若要在不建立自己的 <xref:System.Windows.Media.MediaTimeline> 的情形下播放媒體，請執行下列步驟。  
  
1.  建立 <xref:System.Windows.Media.MediaPlayer> 物件。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2.  使用 <xref:System.Windows.Media.MediaPlayer.Open%2A> 方法載入媒體檔。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3.  建立 <xref:System.Windows.Media.VideoDrawing>。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4.  設定 <xref:System.Windows.Media.VideoDrawing> 的 <xref:System.Windows.Media.VideoDrawing.Rect%2A> 屬性，指定要繪製媒體的大小和位置。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5.  將 <xref:System.Windows.Media.VideoDrawing> 的 <xref:System.Windows.Media.VideoDrawing.Player%2A> 屬性設定為您建立的 <xref:System.Windows.Media.MediaPlayer>。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6.  使用 <xref:System.Windows.Media.MediaPlayer> 的 <xref:System.Windows.Media.MediaPlayer.Play%2A> 方法，開始播放媒體。  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 下列範例使用 <xref:System.Windows.Media.VideoDrawing> 和 <xref:System.Windows.Media.MediaPlayer> 播放一次視訊檔。  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 若要取得媒體的其他計時控制項，請使用 <xref:System.Windows.Media.MediaTimeline> 搭配 <xref:System.Windows.Media.MediaPlayer> 和 <xref:System.Windows.Media.VideoDrawing> 物件。  <xref:System.Windows.Media.MediaTimeline> 可讓您指定視訊是否應重複。  若要使用 <xref:System.Windows.Media.MediaTimeline> 搭配 <xref:System.Windows.Media.VideoDrawing>，請執行下列步驟：  
  
1.  宣告 <xref:System.Windows.Media.MediaTimeline> 並設定其計時行為。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2.  從 <xref:System.Windows.Media.MediaTimeline> 建立 <xref:System.Windows.Media.MediaClock>。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3.  建立 <xref:System.Windows.Media.MediaPlayer>，並使用 <xref:System.Windows.Media.MediaClock> 設定其 <xref:System.Windows.Media.MediaPlayer.Clock%2A> 屬性。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4.  建立 <xref:System.Windows.Media.VideoDrawing>，並將 <xref:System.Windows.Media.MediaPlayer> 指派給 <xref:System.Windows.Media.VideoDrawing> 的 <xref:System.Windows.Media.VideoDrawing.Player%2A> 屬性。  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 下列範例使用 <xref:System.Windows.Media.MediaTimeline> 搭配 <xref:System.Windows.Media.MediaPlayer> 和 <xref:System.Windows.Media.VideoDrawing>，來重複播放視訊。  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 請注意，當您使用 <xref:System.Windows.Media.MediaTimeline> 時，您是使用 <xref:System.Windows.Media.MediaClock> 的 <xref:System.Windows.Media.Animation.Clock.Controller%2A> 屬性所傳回的互動式 <xref:System.Windows.Media.Animation.ClockController> 來控制媒體播放，而非使用 <xref:System.Windows.Media.MediaPlayer> 的互動式方法。  
  
<a name="drawtext"></a>   
## 繪製文字  
 若要繪製文字，您可使用 <xref:System.Windows.Media.GlyphRunDrawing> 和 <xref:System.Windows.Media.GlyphRun>。  下列範例使用 <xref:System.Windows.Media.GlyphRunDrawing> 繪製文字 "Hello World"。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 <xref:System.Windows.Media.GlyphRun> 是適用於固定格式文件展示和列印案例的低階物件。  在螢幕上繪製文字的較簡單方式是使用 <xref:System.Windows.Controls.Label> 或 <xref:System.Windows.Controls.TextBlock>。  如需 <xref:System.Windows.Media.GlyphRun> 的詳細資訊，請參閱 [GlyphRun 物件和 Glyphs 項目簡介](../../../../docs/framework/wpf/advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md)概觀。  
  
<a name="compositedrawingssection"></a>   
## 複合繪圖  
 <xref:System.Windows.Media.DrawingGroup> 可讓您將多個繪圖組合成單一複合繪圖。  您可以使用 <xref:System.Windows.Media.DrawingGroup>，將圖案、影像和文字組合成單一 <xref:System.Windows.Media.Drawing> 物件。  
  
 下列範例使用 <xref:System.Windows.Media.DrawingGroup> 來組合兩個 <xref:System.Windows.Media.GeometryDrawing> 物件和一個 <xref:System.Windows.Media.ImageDrawing> 物件。  這個範例產生下列輸出。  
  
 ![包含多個圖形的 DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.png "graphicsmm\_simple")  
複合繪圖  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 <xref:System.Windows.Media.DrawingGroup> 也可讓您將不透明遮罩、轉換、點陣圖效果和其他作業套用到其內容。  <xref:System.Windows.Media.DrawingGroup> 作業會按照下列順序加以套用：<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>、<xref:System.Windows.Media.DrawingGroup.Opacity%2A>、<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>、<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>、<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>，然後是 <xref:System.Windows.Media.DrawingGroup.Transform%2A>。  
  
 下圖顯示 <xref:System.Windows.Media.DrawingGroup> 作業的套用順序。  
  
 ![DrawingGroup 作業的順序](../../../../docs/framework/wpf/graphics-multimedia/media/graphcismm-drawinggroup-order.png "graphcismm\_drawinggroup\_order")  
DrawingGroup 作業的順序  
  
 下表說明您可用於操作 <xref:System.Windows.Media.DrawingGroup> 物件內容的屬性。  
  
|屬性|描述|示意圖|  
|--------|--------|---------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|變更 <xref:System.Windows.Media.DrawingGroup> 內容之選定部分的不透明度。  如需範例，請參閱 [How to: Control the Opacity of a Drawing](http://msdn.microsoft.com/zh-tw/68580652-7d32-4d27-93cc-a5148cf4d5ee)。||  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|統一變更 <xref:System.Windows.Media.DrawingGroup> 內容的不透明度。  使用這個屬性，可讓 <xref:System.Windows.Media.Drawing> 變成透明或部分透明。  如需範例，請參閱 [How to: Apply an Opacity Mask to a Drawing](http://msdn.microsoft.com/zh-tw/d77b420b-9be2-479c-a45e-82f4da30eb9f)。||  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|將 <xref:System.Windows.Media.Effects.BitmapEffect> 套用到 <xref:System.Windows.Media.DrawingGroup> 內容。  如需範例，請參閱 [How to: Apply a BitmapEffect to a Drawing](http://msdn.microsoft.com/zh-tw/c5b1de83-8d09-47fb-96db-5f174471f4b5)。||  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|使用 <xref:System.Windows.Media.Geometry>，將 <xref:System.Windows.Media.DrawingGroup> 內容裁剪成您描述的區域。  如需範例，請參閱 [How to: Clip a Drawing](http://msdn.microsoft.com/zh-tw/1f7d8a2c-c3c2-42cb-a542-e6796f9fb058)。||  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|沿著指定的導線，讓[與裝置無關的像素](GTMT)貼齊裝置像素。  這個屬性可確保在低 DPI 的顯示器上清晰呈現細緻的圖形。  如需範例，請參閱 [對圖形套用 GuidelineSet](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-a-guidelineset-to-a-drawing.md)。||  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|轉換 <xref:System.Windows.Media.DrawingGroup> 內容。  如需範例，請參閱 [How to: Apply a Transform to a Drawing](http://msdn.microsoft.com/zh-tw/0d525f2b-682d-4d67-9660-cf46929fbabd)。||  
  
<a name="usingimagedrawing"></a>   
## 將繪圖顯示為影像  
 若要以 <xref:System.Windows.Controls.Image> 控制項顯示 <xref:System.Windows.Media.Drawing>，請使用 <xref:System.Windows.Media.DrawingImage> 做為 <xref:System.Windows.Controls.Image> 控制項的 <xref:System.Windows.Controls.Image.Source%2A>，並將 <xref:System.Windows.Media.DrawingImage> 物件的 <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=fullName> 屬性設定為您要顯示的繪圖。  
  
 下列範例使用 <xref:System.Windows.Media.DrawingImage> 和 <xref:System.Windows.Controls.Image> 控制項來顯示 <xref:System.Windows.Media.GeometryDrawing>。  這個範例產生下列輸出。  
  
 ![兩個橢圓形的 GeometryDrawing](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.png "graphicsmm\_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>   
## 繪製含有繪圖的物件  
 <xref:System.Windows.Media.DrawingBrush> 是一種筆刷，可以用繪圖物件來繪製區域。  您可以使用它來繪製幾乎任何含有繪圖的圖形物件。  <xref:System.Windows.Media.DrawingBrush> 的 <xref:System.Windows.Media.Drawing> 屬性會描述其 <xref:System.Windows.Media.DrawingBrush.Drawing%2A>。  若要使用 <xref:System.Windows.Media.DrawingBrush> 來呈現 <xref:System.Windows.Media.Drawing>，請使用筆刷的 <xref:System.Windows.Media.Drawing> 屬性將它加入至筆刷，並使用筆刷來繪製圖形物件，例如控制項或面板。  
  
 下列範例使用 <xref:System.Windows.Media.DrawingBrush>，採用從 <xref:System.Windows.Media.GeometryDrawing> 建立的圖樣來繪製 <xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.Shapes.Shape.Fill%2A>。  這個範例產生下列輸出。  
  
 ![並排顯示的 DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm\_drawingbrush\_geometrydrawing")  
搭配 DrawingBrush 使用的 GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 <xref:System.Windows.Media.DrawingBrush> 類別會提供各種選項，以便延伸和並排顯示其內容。  如需 <xref:System.Windows.Media.DrawingBrush> 的詳細資訊，請參閱[使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)概觀。  
  
<a name="renderingwithvisualsection"></a>   
## 使用視覺項目來呈現繪圖  
 <xref:System.Windows.Media.DrawingVisual> 是一種為了呈現繪圖所設計的視覺物件。  對於要建置高度自訂圖形環境的開發人員而言，可以選擇直接在視覺分層作業，但本概觀中並未說明此選項。  如需詳細資訊，請參閱[使用 DrawingVisual 物件](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)概觀。  
  
<a name="drawingcontextobjects"></a>   
## DrawingContext 物件  
 <xref:System.Windows.Media.DrawingContext> 類別可讓您用視覺內容填入 \(Populate\) <xref:System.Windows.Media.Visual> 或 <xref:System.Windows.Media.Drawing>。  許多此種低階圖形物件會使用 <xref:System.Windows.Media.DrawingContext>，因為它可有效地描繪圖形內容。  
  
 雖然 <xref:System.Windows.Media.DrawingContext> 繪製方法與 <xref:System.Drawing.Graphics?displayProperty=fullName> 型別的繪製方法類似，但是它們的作用方式十分不同。  <xref:System.Windows.Media.DrawingContext> 適用於保留模式圖形系統，而 <xref:System.Drawing.Graphics?displayProperty=fullName> 型別則適用於立即模式圖形系統。  當您使用 <xref:System.Windows.Media.DrawingContext> 物件的 draw 命令時，實際上會儲存一組呈現指令 \(雖然實際儲存機制取決於提供 <xref:System.Windows.Media.DrawingContext> 的物件型別\) 以在稍後供圖形系統使用，而不是即時繪製至螢幕上。  如需 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 圖形系統運作方式的詳細資訊，請參閱 [WPF 圖形轉譯概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)。  
  
 您不能直接具現化 \(Instantiate\) <xref:System.Windows.Media.DrawingContext>，但是，您可以從某些方法取得繪圖內容，例如 <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=fullName> 和 <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=fullName>。  
  
<a name="enumeratevisualcontents"></a>   
## 列舉視覺項目的內容  
 除了其他用途以外，<xref:System.Windows.Media.Drawing> 物件也會提供物件模式，以便列舉 <xref:System.Windows.Media.Visual> 的內容。  
  
 下列範例使用 <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> 方法，擷取 <xref:System.Windows.Media.Visual> 的 <xref:System.Windows.Media.DrawingGroup> 值並加以列舉。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## 請參閱  
 <xref:System.Windows.Media.Drawing>   
 <xref:System.Windows.Media.DrawingGroup>   
 [2D 圖形和影像](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)   
 [幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)   
 [WPF 中圖案和基本繪圖概觀](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)   
 [WPF 圖形轉譯概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)   
 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/drawings-how-to-topics.md)