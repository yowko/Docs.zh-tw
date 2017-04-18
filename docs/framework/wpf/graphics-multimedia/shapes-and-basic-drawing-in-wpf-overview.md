---
title: "WPF 中圖案和基本繪圖概觀 | Microsoft Docs"
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
  - "基本繪製"
  - "Shape 物件"
  - "圖案, 關於圖案"
  - "向量繪圖, 概觀"
  - "向量, 繪製"
ms.assetid: 66d7a6d6-e3b6-47bc-8dfe-8a1b26f7d901
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# WPF 中圖案和基本繪圖概觀
本主題概述說明如何使用 <xref:System.Windows.Shapes.Shape> 物件進行繪製。  <xref:System.Windows.Shapes.Shape> 的型別是 <xref:System.Windows.UIElement>，可讓您將圖案繪製至螢幕。  因為它們是 UI 項目，所以 <xref:System.Windows.Shapes.Shape> 物件可以用於 <xref:System.Windows.Controls.Panel> 項目和大部分控制項內。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供數個圖形和呈現服務的存取層級。  在最上層，<xref:System.Windows.Shapes.Shape> 物件十分容易使用，而且提供許多可用功能 \(如配置和參與 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 事件系統\)。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="shapes"></a>   
## 圖案物件  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供一些立即可用的 <xref:System.Windows.Shapes.Shape> 物件。  所有圖案物件都是繼承自 <xref:System.Windows.Shapes.Shape> 類別。  可用的圖案物件包括 <xref:System.Windows.Shapes.Ellipse>、<xref:System.Windows.Shapes.Line>、<xref:System.Windows.Shapes.Path>、<xref:System.Windows.Shapes.Polygon>、<xref:System.Windows.Shapes.Polyline> 和 <xref:System.Windows.Shapes.Rectangle>。<xref:System.Windows.Shapes.Shape> 物件共用下列通用屬性。  
  
-   <xref:System.Windows.Shapes.Shape.Stroke%2A>：描述如何繪製圖案的外框。  
  
-   <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>：描述如何繪製圖案外框的粗細。  
  
-   <xref:System.Windows.Shapes.Shape.Fill%2A>：描述如何繪製圖案內部。  
  
-   指定座標和頂點的資料屬性 \(測量單位為[與裝置無關的像素](GTMT)\)。  
  
 因為它們衍生自 <xref:System.Windows.UIElement>，所以圖案物件可以用於面板和大部分控制項內。  因為 <xref:System.Windows.Controls.Canvas> 面板支援其子物件的絕對位置，所以特別適合用於建立複雜繪圖。  
  
 <xref:System.Windows.Shapes.Line> 類別可讓您繪製兩點之間的線條。  下列範例顯示多種指定線條座標和筆劃屬性的方式。  
  
 [!code-xml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 下列影像顯示呈現的 <xref:System.Windows.Shapes.Line>。  
  
 ![線條圖例](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-line2.png "shape\_ovw\_line2")  
  
 雖然 <xref:System.Windows.Shapes.Line> 類別提供 <xref:System.Windows.Shapes.Shape.Fill%2A> 屬性，但是因為 <xref:System.Windows.Shapes.Line> 沒有任何區域，所以設定它並不會有任何效果。  
  
 另一個通用圖案是 <xref:System.Windows.Shapes.Ellipse>。  而定義圖案的 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 屬性，就可以建立 <xref:System.Windows.Shapes.Ellipse>。  若要繪製圓形，請指定 <xref:System.Windows.FrameworkElement.Width%2A> 值等於 <xref:System.Windows.FrameworkElement.Height%2A> 值的 <xref:System.Windows.Shapes.Ellipse>。  
  
 [!code-xml[ShapeOverviews#ShapesOVW1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 下列影像顯示已呈現 <xref:System.Windows.Shapes.Ellipse> 的範例。  
  
 ![橢圓形圖例](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipse2.png "shape\_ovw\_ellipse2")  
  
<a name="paths"></a>   
## 使用路徑和幾何  
 <xref:System.Windows.Shapes.Path> 類別可讓您繪製曲線和複雜圖案。  這些曲線和圖案是使用 <xref:System.Windows.Media.Geometry> 物件進行描述。  若要使用 <xref:System.Windows.Shapes.Path>，請建立並使用 <xref:System.Windows.Media.Geometry> 來設定 <xref:System.Windows.Shapes.Path> 物件的 <xref:System.Windows.Shapes.Path.Data%2A> 屬性。  
  
 有各種 <xref:System.Windows.Media.Geometry> 物件可以進行選擇。  <xref:System.Windows.Media.LineGeometry>、<xref:System.Windows.Media.RectangleGeometry> 和 <xref:System.Windows.Media.EllipseGeometry> 類別會描述相當簡單的圖案。  若要建立較複雜的圖案或建立曲線，請使用 <xref:System.Windows.Media.PathGeometry>。  
  
<a name="pathgeometry"></a>   
### PathGeometry 和 PathSegments  
 <xref:System.Windows.Media.PathGeometry> 物件是由一個或多個 <xref:System.Windows.Media.PathFigure> 物件組成，而每個 <xref:System.Windows.Media.PathFigure> 都代表不同的「圖形」或圖案。  每個 <xref:System.Windows.Media.PathFigure> 本身都是由一個或多個 <xref:System.Windows.Media.PathSegment> 物件所組成，其中每個物件各代表圖形或圖案的某個連接部分。  區段型別包括下列各項：<xref:System.Windows.Media.LineSegment>、<xref:System.Windows.Media.BezierSegment> 和 <xref:System.Windows.Media.ArcSegment>。  
  
 在下列範例中，<xref:System.Windows.Shapes.Path> 是用來繪製二次方貝茲曲線。  
  
 [!code-xml[geometrysample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 下列影像顯示呈現的圖案。  
  
 ![路徑圖例](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path2.png "shape\_ovw\_path2")  
  
 如需 <xref:System.Windows.Media.PathGeometry> 和其他 <xref:System.Windows.Media.Geometry> 類別的詳細資訊，請參閱[幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)。  
  
<a name="pathdatastring"></a>   
### XAML 縮寫語法  
 在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中，您可能也會使用特殊的縮寫語法，來描述 <xref:System.Windows.Shapes.Path>。  在下列範例中，縮寫語法是用來繪製複雜圖案。  
  
```xaml  
<Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 下列影像顯示呈現的 <xref:System.Windows.Shapes.Path>。  
  
 ![路徑圖例](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path.png "shape\_ovw\_path")  
  
 <xref:System.Windows.Shapes.Path.Data%2A> 屬性字串是以 "moveto" 命令 \(以 M 表示\) 開始，可建立 <xref:System.Windows.Controls.Canvas> 之座標系統的路徑起始點。  <xref:System.Windows.Shapes.Path> 資料參數會區分大小寫。  大寫 M 表示新目前點的絕對位置。  小寫 m 則表示相對座標。  第一個區段是三次方[貝茲曲線](GTMT)，開始於 \(100,200\) 而結束於 \(400,175\)，並使用 \(100,25\) 和 \(400,350\) 這兩個控制點進行繪製。  這個區段是以 <xref:System.Windows.Shapes.Path.Data%2A> 屬性字串中的 C 命令所表示。  同樣地，大寫 C 表示絕對路徑，而小寫 c 則表示相對路徑。  
  
 第二個區段是以絕對水平 "lineto" 命令 H 開始，會指定從前面的子路徑端點 \(400,175\) 開始到新端點 \(280,175\) 繪製一條線。  因為它是水平 "lineto" 命令，所以指定的值是 *x* 座標。  
  
 如需完整的路徑語法，請參閱 <xref:System.Windows.Shapes.Path.Data%2A> 參考和 [使用 PathGeometry 建立圖案](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)。  
  
<a name="fillpaint"></a>   
## 繪製圖案  
 <xref:System.Windows.Media.Brush> 物件是用來繪製圖案的 <xref:System.Windows.Shapes.Shape.Stroke%2A> 和 <xref:System.Windows.Shapes.Shape.Fill%2A>。  在下列範例中，會指定 <xref:System.Windows.Shapes.Ellipse> 的筆劃和填滿。  請注意，筆刷屬性的有效輸入可以是關鍵字或十六進位色彩值。  如需可用色彩關鍵字的詳細資訊，請參閱 <xref:System.Windows.Media> 命名空間中之 <xref:System.Windows.Media.Colors> 類別的屬性。  
  
```  
  
<Canvas Background="LightGray">   
   <Ellipse  
      Canvas.Top="50"  
      Canvas.Left="50"  
      Fill="#FFFFFF00"  
      Height="75"  
      Width="75"  
      StrokeThickness="5"  
      Stroke="#FF0000FF"/>  
</Canvas>  
  
```  
  
 下列影像顯示呈現的 <xref:System.Windows.Shapes.Ellipse>。  
  
 ![橢圓形](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipsefill.png "shape\_ovw\_ellipsefill")  
  
 您也可以使用屬性項目語法明確建立 <xref:System.Windows.Media.SolidColorBrush> 物件，以繪製具有純色的圖案。  
  
```  
  
<!-- This polygon shape uses pre-defined color values for its Stroke and  
     Fill properties.   
     The SolidColorBrush's Opacity property affects the fill color in   
     this case by making it slightly transparent (opacity of 0.4) so   
     that it blends with any underlying color. -->  
  
<Polygon  
    Points="300,200 400,125 400,275 300,200"  
    Stroke="Purple"   
    StrokeThickness="2">  
    <Polygon.Fill>  
       <SolidColorBrush Color="Blue" Opacity="0.4"/>  
    </Polygon.Fill>  
</Polygon>  
```  
  
 下圖顯示呈現的圖案。  
  
 ![SolidColorBrush 圖例](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-solidcolorbrush.png "shape\_ovw\_solidcolorbrush")  
  
 您也可以使用漸層、影像、圖樣和其他項目，來繪製圖案的筆劃或填滿。  如需詳細資訊，請參閱 [使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)。  
  
<a name="stretchableshapessection"></a>   
## 可自動縮放的圖案  
 <xref:System.Windows.Shapes.Line>、<xref:System.Windows.Shapes.Path>、<xref:System.Windows.Shapes.Polygon>、<xref:System.Windows.Shapes.Polyline> 和 <xref:System.Windows.Shapes.Rectangle> 類別都有 <xref:System.Windows.Shapes.Shape.Stretch%2A> 屬性。  這個屬性決定如何自動縮放 <xref:System.Windows.Shapes.Shape> 物件的內容 \(要繪製的圖案\) 以填滿 <xref:System.Windows.Shapes.Shape> 物件的配置空間。  因為明確 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 設定，或因為它的 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 和 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 設定，所以 <xref:System.Windows.Shapes.Shape> 物件的配置空間就是配置系統所配置的 <xref:System.Windows.Shapes.Shape> 空間量。  如需 Windows Presentation Foundation 配置的額外資訊，請參閱[配置](../../../../docs/framework/wpf/advanced/layout.md)概觀。  
  
 Stretch 屬性會取用下列其中一個值：  
  
-   <xref:System.Windows.Media.Stretch>：<xref:System.Windows.Shapes.Shape> 物件的內容不會自動縮放。  
  
-   <xref:System.Windows.Media.Stretch>：<xref:System.Windows.Shapes.Shape> 物件的內容會自動縮放以填滿它的配置空間。  不會保留外觀比例 \(Aspect Ratio\)。  
  
-   <xref:System.Windows.Media.Stretch>：<xref:System.Windows.Shapes.Shape> 物件的內容會盡可能自動縮放到最大，以填滿它的配置空間，並保留它的原始外觀比例。  
  
-   <xref:System.Windows.Media.Stretch>：<xref:System.Windows.Shapes.Shape> 物件的內容會自動縮放，以完全填滿它的配置空間，並保留它的原始外觀比例。  
  
 請注意，自動縮放 <xref:System.Windows.Shapes.Shape> 物件的內容時，會在自動縮放之後繪製 <xref:System.Windows.Shapes.Shape> 物件的外框。  
  
 在下列範例中，<xref:System.Windows.Shapes.Polygon> 是用來繪製從 \(0,0\) 到 \(0,1\) 再到 \(1,1\) 的一個非常小的三角形。  <xref:System.Windows.Shapes.Polygon> 物件的 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 是設定為 100，而它的自動縮放屬性是設定為 Fill。  因此，<xref:System.Windows.Shapes.Polygon> 物件的內容 \(三角形\) 會自動縮放以填滿較大的空間。  
  
```  
...  
<Polygon  
  Points="0,0 0,1 1,1"  
  Fill="Blue"  
  Width="100"  
  Height="100"  
  Stretch="Fill"  
  Stroke="Black"  
  StrokeThickness="2" />  
...  
```  
  
```  
...  
PointCollection myPointCollection = new PointCollection();  
myPointCollection.Add(new Point(0,0));  
myPointCollection.Add(new Point(0,1));  
myPointCollection.Add(new Point(1,1));  
  
Polygon myPolygon = new Polygon();  
myPolygon.Points = myPointCollection;  
myPolygon.Fill = Brushes.Blue;  
myPolygon.Width = 100;  
myPolygon.Height = 100;  
myPolygon.Stretch = Stretch.Fill;  
myPolygon.Stroke = Brushes.Black;  
myPolygon.StrokeThickness = 2;  
...  
```  
  
<a name="transforms"></a>   
## 轉換圖案  
 <xref:System.Windows.Media.Transform> 類別提供方法以二維平面來轉換圖案。  不同的轉換型別包括旋轉 \(<xref:System.Windows.Media.RotateTransform>\)、縮放 \(<xref:System.Windows.Media.ScaleTransform>\)、扭曲 \(<xref:System.Windows.Media.SkewTransform>\) 和平移 \(<xref:System.Windows.Media.TranslateTransform>\)。  
  
 套用至圖案的通用轉換就是旋轉。  若要旋轉圖案，請建立 <xref:System.Windows.Media.RotateTransform>，並指定它的 <xref:System.Windows.Media.RotateTransform.Angle%2A>。  <xref:System.Windows.Media.RotateTransform.Angle%2A> 45 會將項目順時針旋轉 45 度，而 Angle 90 會將項目順時針旋轉 90 度，以此類推。  如果想要控制用來旋轉項目的點，請設定 <xref:System.Windows.Media.RotateTransform.CenterX%2A> 和 <xref:System.Windows.Media.RotateTransform.CenterY%2A> 屬性。  這些屬性值是以正在轉換之項目的座標空間表示。  <xref:System.Windows.Media.RotateTransform.CenterX%2A> 和 <xref:System.Windows.Media.RotateTransform.CenterY%2A> 會具有預設值零。  最後，再將 <xref:System.Windows.Media.RotateTransform> 套用至該項目。  如果不想要轉換影響到配置，請設定圖案的 <xref:System.Windows.UIElement.RenderTransform%2A> 屬性。  
  
 在下列範例中，<xref:System.Windows.Media.RotateTransform> 是用來將圖案從圖案的左上角 \(0,0\) 旋轉 45 度。  
  
 [!code-xml[transformssample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 而在下一個範例中，另一個圖案會旋轉 45 度，但是這次是從點 \(25,50\) 旋轉。  
  
 [!code-xml[transformssample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 下圖顯示套用兩個轉換的結果。  
  
 ![採用不同中心點的 45 度旋轉](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.png "wcpsdk\_graphicsmm\_rotatetransform45degrees")  
  
 在先前的範例中，已將單一轉換套用至每個圖案物件。  若要將多個轉換套用至圖案 \(或其他任何 UI 項目\)，請使用 <xref:System.Windows.Media.TransformGroup>。  
  
## 請參閱  
 [2D 圖形和影像](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)   
 [幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)   
 [逐步解說：WPF 使用者入門](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)