---
title: "TileBrush 概觀 | Microsoft Docs"
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
  - "筆刷, TileBrush"
  - "TileBrush"
ms.assetid: aa4a7b7e-d09d-44c2-8d61-310c50e08d68
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# TileBrush 概觀
<xref:System.Windows.Media.TileBrush> 物件讓您對使用影像、<xref:System.Windows.Media.Drawing> 或 <xref:System.Windows.Media.Visual> 繪製區域的方式擁有更多的控制。  本主題說明如何使用 <xref:System.Windows.Media.TileBrush> 功能對 <xref:System.Windows.Media.ImageBrush>、<xref:System.Windows.Media.DrawingBrush> 或 <xref:System.Windows.Media.VisualBrush> 繪製區域的方式取得更多的控制。  
  
   
  
<a name="prerequisite"></a>   
## 必要條件  
 若要了解本主題，則了解如何使用 <xref:System.Windows.Media.ImageBrush>、<xref:System.Windows.Media.DrawingBrush> 或 <xref:System.Windows.Media.VisualBrush> 類別的基本功能是相當有用的。  如需這些型別的簡介，請參閱[使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)。  
  
<a name="tilebrush"></a>   
## 繪製含有並排的區域  
 <xref:System.Windows.Media.ImageBrush>、<xref:System.Windows.Media.DrawingBrush> 和 <xref:System.Windows.Media.VisualBrush> 都是一種 <xref:System.Windows.Media.TileBrush> 物件。  並排顯示筆刷讓您對使用影像、繪圖或視覺資料繪製區域的方式擁有更多的控制。  例如，您可以用構成圖樣的一系列影像並排顯示來繪製區域，而不是只以單一自動縮放的影像來繪製區域。  
  
 使用並排顯示筆刷繪製區域時牽涉到三個元件：內容、基底並排顯示及輸出區域。  
  
 ![TileBrush 元件](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk\_mmgraphics\_defaultcontentprojection2")  
具有單一並排顯示之 TileBrush 的元件  
  
 ![並排顯示之 TileBrush 的元件](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tiledprojection.png "graphicsmm\_tiledprojection")  
TileMode 為 Tile 之 TileBrush 的元件  
  
 輸出區域就是要繪製的區域，例如 <xref:System.Windows.Shapes.Ellipse> 的 <xref:System.Windows.Shapes.Shape.Fill%2A> 或 <xref:System.Windows.Controls.Button> 的 <xref:System.Windows.Controls.Control.Background%2A>。  下一節會說明 <xref:System.Windows.Media.TileBrush> 的其他兩個元件。  
  
<a name="brushcontent"></a>   
## 筆刷內容  
 <xref:System.Windows.Media.TileBrush> 有三種不同型別，每一種都以不同的內容類型繪製。  
  
-   如果筆刷是 <xref:System.Windows.Media.ImageBrush>，則這個內容是影像。<xref:System.Windows.Media.ImageBrush.ImageSource%2A> 屬性會指定 <xref:System.Windows.Media.ImageBrush> 的內容。  
  
-   如果筆刷是 <xref:System.Windows.Media.DrawingBrush>，則這個內容是繪圖。  <xref:System.Windows.Media.DrawingBrush.Drawing%2A> 屬性指定 <xref:System.Windows.Media.DrawingBrush> 的內容。  
  
-   如果筆刷是 <xref:System.Windows.Media.VisualBrush>，則這個內容是視覺項目。  <xref:System.Windows.Media.VisualBrush.Visual%2A> 屬性指定 <xref:System.Windows.Media.VisualBrush> 的內容。  
  
 您可以使用 <xref:System.Windows.Media.TileBrush.Viewbox%2A> 屬性來指定 <xref:System.Windows.Media.TileBrush> 內容的位置和維度，不過通常會保留 <xref:System.Windows.Media.TileBrush.Viewbox%2A> 的預設值。  根據預設，<xref:System.Windows.Media.TileBrush.Viewbox%2A> 會設定為完整包含筆刷的內容。  如需設定 <xref:System.Windows.Controls.Viewbox> 的詳細資訊，請參閱 <xref:System.Windows.Controls.Viewbox> 屬性頁面。  
  
<a name="thebasetile"></a>   
## 基底並排顯示  
 <xref:System.Windows.Media.TileBrush> 會將其內容投射至基底並排顯示。  <xref:System.Windows.Media.TileBrush.Stretch%2A> 屬性會控制 <xref:System.Windows.Media.TileBrush> 內容如何自動縮放以填滿基底並排顯示。  <xref:System.Windows.Media.TileBrush.Stretch%2A> 屬性接受下列值 \(由 <xref:System.Windows.Media.Stretch> 列舉型別定義\)：  
  
-   <xref:System.Windows.Media.Stretch>：筆刷內容不會自動縮放以填滿並排顯示。  
  
-   <xref:System.Windows.Media.Stretch>：筆刷內容會自動縮放以符合並排顯示。  因為內容的高度和寬度是分開縮放的，所以可能不會保留影像的原始外觀比例 \(Aspect Ratio\)。  也就是說，筆刷內容可能會扭曲以完全填滿輸出並排顯示。  
  
-   <xref:System.Windows.Media.Stretch>：筆刷內容會縮放以完全符合並排顯示的大小。  內容的外觀比例會保留下來。  
  
-   <xref:System.Windows.Media.Stretch>：筆刷內容會縮放以完全填滿輸出區域，並同時保留內容的原始外觀比例。  
  
 下圖說明不同的 <xref:System.Windows.Media.TileBrush.Stretch%2A> 設定。  
  
 ![不同的 TileBrush Stretch 設定](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-stretchenum.png "img\_mmgraphics\_stretchenum")  
  
 在下列範例中，<xref:System.Windows.Media.ImageBrush> 的內容會設定為不會自動縮放以填滿輸出區域。  
  
 [!code-xml[BrushOverviewExamples_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/StretchExample.xaml#graphicsmmnostretchexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/StretchExample.cs#graphicsmmnostretchexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/stretchexample.vb#graphicsmmnostretchexample)]  
  
 根據預設，<xref:System.Windows.Media.TileBrush> 會產生單一並排顯示 \(基底並排顯示\) 並自動縮放該並排顯示以完全填滿輸出區域。  您可以藉由設定 <xref:System.Windows.Media.TileBrush.Viewport%2A> 和 <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> 屬性來變更基底並排顯示的大小和位置。  
  
<a name="basetilesize"></a>   
### 基底並排顯示大小  
 <xref:System.Windows.Media.TileBrush.Viewport%2A> 屬性會判斷基底並排顯示的大小和位置，而 <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> 屬性則會判斷 <xref:System.Windows.Media.TileBrush.Viewport%2A> 是使用絕對或相對座標指定的。  如果是相對座標，則是相對於輸出區域的大小。  \(0,0\) 這個點表示輸出區域的左上角，而 \(1,1\) 則表示輸出區域的右下角。  若要指定 <xref:System.Windows.Media.TileBrush.Viewport%2A> 屬性使用絕對座標，請將 <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> 屬性設定為 <xref:System.Windows.Media.BrushMappingMode>。  
  
 下圖顯示使用相對與絕對 <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> 時 <xref:System.Windows.Media.TileBrush> 輸出之間的差異。  請注意，每個圖例都會顯示並排顯示模式，下一節會說明如何指定並排顯示模式。  
  
 ![相對和絕對檢視區單元](../../../../docs/framework/wpf/graphics-multimedia/media/absolute-and-relative-viewports.png "absolute\_and\_relative\_viewports")  
  
 在下列範例中，會使用影像建立 50% 寬度和高度的並排顯示。  基底並排顯示位於輸出區域的 \(0,0\)。  
  
 [!code-xml[BrushOverviewExamples_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmrelativeviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmrelativeviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmrelativeviewportunitsexample1)]  
  
 下一個範例會將 <xref:System.Windows.Media.ImageBrush> 的並排顯示設為 25 乘以 25 個[與裝置無關的像素](GTMT)。  因為 <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> 是絕對單位，所以不論要繪製的區域有多大，<xref:System.Windows.Media.ImageBrush> 並排顯示都一定是 25 乘以 25 個像素。  
  
 [!code-xml[BrushOverviewExamples_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmabsoluteviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmabsoluteviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmabsoluteviewportunitsexample1)]  
  
<a name="tilingbehavior"></a>   
### 並排顯示行為  
 當基底並排顯示不完全填滿輸出區域，而且指定的並排顯示模式不是 <xref:System.Windows.Media.TileMode> 時，<xref:System.Windows.Media.TileBrush> 會產生並排顯示圖樣。  當並排顯示筆刷的並排顯示不完全填滿輸出區域時，其 <xref:System.Windows.Media.TileBrush.TileMode%2A> 屬性會指定是否應該複製基底並排顯示以填滿輸出區域，如果是的話，應該如何複製基底並排顯示。  <xref:System.Windows.Media.TileBrush.TileMode%2A> 屬性接受下列值 \(由 <xref:System.Windows.Media.TileMode> 列舉定義\)：  
  
-   <xref:System.Windows.Media.TileMode>：只繪製基底並排顯示。  
  
-   <xref:System.Windows.Media.TileMode>：繪製基底並排顯示，並以重複的基底並排顯示填滿其餘區域，使得並排顯示的右邊緣與下一個並排顯示的左邊緣相鄰，上下邊緣也是一樣的情形。  
  
-   <xref:System.Windows.Media.TileMode>：與 <xref:System.Windows.Media.TileMode> 相同，但是替代欄的並排顯示會以水平方式翻轉。  
  
-   <xref:System.Windows.Media.TileMode>：與 <xref:System.Windows.Media.TileMode> 相同，但是替代欄的並排顯示會以垂直方式翻轉。  
  
-   <xref:System.Windows.Media.TileMode>：<xref:System.Windows.Media.TileMode> 和 <xref:System.Windows.Media.TileMode> 的組合。  
  
 下圖說明不同的並排顯示模式。  
  
 ![不同的 TileBrush TileMode 設定](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-tilemodes.png "img\_mmgraphics\_tilemodes")  
  
 在下列範例中，會使用影像繪製 100 像素寬及 100 像素高的矩形。  藉由將筆刷的 <xref:System.Windows.Media.TileBrush.Viewport%2A> 設為 0,0,0.25,0.25，筆刷的並排顯示會佔輸出區域的 1\/4。  筆刷的 <xref:System.Windows.Media.TileBrush.TileMode%2A> 是設定為 <xref:System.Windows.Media.TileMode>，  所以會以並排顯示列填滿矩形。  
  
 [!code-xml[BrushOverviewExamples_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TilingExample.xaml#graphicsmmflipxyexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TilingExample.cs#graphicsmmflipxyexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilingexample.vb#graphicsmmflipxyexample)]  
  
## 請參閱  
 <xref:System.Windows.Media.ImageBrush>   
 <xref:System.Windows.Media.DrawingBrush>   
 <xref:System.Windows.Media.VisualBrush>   
 <xref:System.Windows.Media.TileBrush>   
 [使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/brushes-how-to-topics.md)   
 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [ImageBrush 範例](http://go.microsoft.com/fwlink/?LinkID=160005)   
 [VisualBrush 範例](http://go.microsoft.com/fwlink/?LinkID=160049)