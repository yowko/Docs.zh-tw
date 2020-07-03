---
title: 圖形和基本繪圖總覽
description: 在 Windows Presentation Foundation （WPF）中使用立即可用的圖形和數層的轉譯服務，強化您的使用者介面。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- shapes [WPF], about shapes
- basic drawing [WPF]
- vector drawing [WPF], overview
- vectors [WPF], drawing
- Shape objects [WPF]
ms.assetid: 66d7a6d6-e3b6-47bc-8dfe-8a1b26f7d901
ms.openlocfilehash: 41d8f2b87232740c8945bd6a6099aa86dbe77bc6
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853700"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a>WPF 中圖案和基本繪圖概觀
本主題提供如何使用物件繪製的總覽 <xref:System.Windows.Shapes.Shape> 。 <xref:System.Windows.Shapes.Shape>是的一種類型 <xref:System.Windows.UIElement> ，可讓您在螢幕上繪製圖形。 因為它們是 UI 元素，所以 <xref:System.Windows.Shapes.Shape> 物件可以在專案 <xref:System.Windows.Controls.Panel> 和大部分的控制項內使用。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供了數層的圖形和轉譯服務存取權。 在最上層， <xref:System.Windows.Shapes.Shape> 物件很容易使用，並提供許多有用的功能，例如事件系統中的版面配置和參與 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 。  

<a name="shapes"></a>
## <a name="shape-objects"></a>Shape 物件  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供數個現成可用的 <xref:System.Windows.Shapes.Shape> 物件。  所有繪圖物件都是繼承自 <xref:System.Windows.Shapes.Shape> 類別。 可用的繪圖物件包括 <xref:System.Windows.Shapes.Ellipse> 、 <xref:System.Windows.Shapes.Line> 、 <xref:System.Windows.Shapes.Path> 、 <xref:System.Windows.Shapes.Polygon> 、 <xref:System.Windows.Shapes.Polyline> 和 <xref:System.Windows.Shapes.Rectangle> 。 <xref:System.Windows.Shapes.Shape>物件共用下列通用屬性。  
  
- <xref:System.Windows.Shapes.Shape.Stroke%2A>：描述圖形的外框繪製方式。  
  
- <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>：描述圖形外框的粗細。  
  
- <xref:System.Windows.Shapes.Shape.Fill%2A>：描述圖形內部的繪製方式。  
  
- 用來指定座標和頂點的資料屬性，以裝置獨立像素為單位。  
  
 因為它們衍生自 <xref:System.Windows.UIElement> ，所以 shape 物件可以在面板和大部分控制項內使用。 <xref:System.Windows.Controls.Canvas>面板是特別適合用來建立複雜繪圖的選擇，因為它支援其子物件的絕對位置。  
  
 <xref:System.Windows.Shapes.Line>類別可讓您在兩個點之間繪製線條。 下列範例示範用來指定線段座標和筆觸屬性的數種方法。  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 下圖顯示呈現的 <xref:System.Windows.Shapes.Line> 。  
  
 ![線條圖例](./media/shape-ovw-line2.gif "shape_ovw_line2")  
  
 雖然 <xref:System.Windows.Shapes.Line> 類別確實提供 <xref:System.Windows.Shapes.Shape.Fill%2A> 屬性，但設定它沒有任何作用，因為沒有 <xref:System.Windows.Shapes.Line> 區域。  
  
 另一個常見的圖形是 <xref:System.Windows.Shapes.Ellipse> 。  藉 <xref:System.Windows.Shapes.Ellipse> 由定義圖形的 <xref:System.Windows.FrameworkElement.Width%2A> 和屬性來建立 <xref:System.Windows.FrameworkElement.Height%2A> 。 若要繪製圓形，請指定 <xref:System.Windows.Shapes.Ellipse> 其 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 值相等的。  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 下圖顯示呈現的範例 <xref:System.Windows.Shapes.Ellipse> 。  
  
 ![橢圓形圖例](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")  
  
<a name="paths"></a>
## <a name="using-paths-and-geometries"></a>使用路徑和幾何  
 <xref:System.Windows.Shapes.Path>類別可讓您繪製曲線和複雜的圖形。 這些曲線和圖形會使用物件加以描述 <xref:System.Windows.Media.Geometry> 。 若要使用 <xref:System.Windows.Shapes.Path> ，請建立， <xref:System.Windows.Media.Geometry> 並使用它來設定 <xref:System.Windows.Shapes.Path> 物件的 <xref:System.Windows.Shapes.Path.Data%2A> 屬性。  
  
 有各種不同的 <xref:System.Windows.Media.Geometry> 物件可供選擇。 <xref:System.Windows.Media.LineGeometry>、 <xref:System.Windows.Media.RectangleGeometry> 和類別會 <xref:System.Windows.Media.EllipseGeometry> 描述相當簡單的圖形。 若要建立更複雜的圖形或建立曲線，請使用 <xref:System.Windows.Media.PathGeometry> 。  
  
<a name="pathgeometry"></a>
### <a name="pathgeometry-and-pathsegments"></a>PathGeometry 和 PathSegments  
 <xref:System.Windows.Media.PathGeometry>物件是由一或多個 <xref:System.Windows.Media.PathFigure> 物件所組成，每個物件都 <xref:System.Windows.Media.PathFigure> 代表不同的「圖形」或圖形。 每個 <xref:System.Windows.Media.PathFigure> 都是由一或多個物件所組成 <xref:System.Windows.Media.PathSegment> ，每個物件都代表圖表或圖形的連接部分。 區段類型包括下列各項： <xref:System.Windows.Media.LineSegment> 、 <xref:System.Windows.Media.BezierSegment> 和 <xref:System.Windows.Media.ArcSegment> 。  
  
 在下列範例中， <xref:System.Windows.Shapes.Path> 是用來繪製二次方貝茲曲線。  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 下列影像顯示轉譯的圖形。  
  
 ![路徑圖例](./media/shape-ovw-path2.gif "shape_ovw_path2")  
  
 如需 <xref:System.Windows.Media.PathGeometry> 和其他類別的詳細資訊 <xref:System.Windows.Media.Geometry> ，請參閱[幾何總覽](geometry-overview.md)。  
  
<a name="pathdatastring"></a>
### <a name="xaml-abbreviated-syntax"></a>XAML 縮寫語法  
 在中 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ，您也可以使用特殊的縮寫語法來描述 <xref:System.Windows.Shapes.Path> 。 在下列範例中，縮寫語法是用來繪製複雜的圖形。  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 下圖顯示呈現的 <xref:System.Windows.Shapes.Path> 。  
  
 ![路徑圖例](./media/shape-ovw-path.PNG "shape_ovw_path")  
  
 <xref:System.Windows.Shapes.Path.Data%2A>屬性字串的開頭是 "moveto" 命令，以 M 表示，這會在的座標系統中建立路徑的起始點 <xref:System.Windows.Controls.Canvas> 。 <xref:System.Windows.Shapes.Path>資料參數會區分大小寫。 大寫 M 表示新目前點的絕對位置。 小寫 m 則表示相對座標。 第一個線段是三次方貝茲曲線，開始於 (100,200) 並結束於 (400,175)，使用 (100,25) 和 (400,350) 這兩個控制點繪製。 這個區段是由屬性字串中的 C 命令所表示 <xref:System.Windows.Shapes.Path.Data%2A> 。 同樣地，大寫 C 表示絕對路徑；小寫 c 表示相對路徑。  
  
 第二個線段的開頭為絕對水平 "lineto" 命令 H，它會指定從前面的子路徑的端點 (400,175) 到新端點 (280,175) 繪製的線段。 因為它是水準的 "lineto" 命令，指定的值是*x*座標。  
  
 如需完整的路徑語法，請參閱 <xref:System.Windows.Shapes.Path.Data%2A> 參考和[使用 System.windows.media.pathgeometry> 建立圖形](how-to-create-a-shape-by-using-a-pathgeometry.md)。  
  
<a name="fillpaint"></a>
## <a name="painting-shapes"></a>繪製圖形  
 <xref:System.Windows.Media.Brush>物件是用來繪製圖形的 <xref:System.Windows.Shapes.Shape.Stroke%2A> 和 <xref:System.Windows.Shapes.Shape.Fill%2A> 。 在下列範例中，會指定的筆觸和填滿 <xref:System.Windows.Shapes.Ellipse> 。 請注意，筆刷屬性的有效輸入可以是關鍵字或十六進位色彩值。 如需可用的色彩關鍵字的詳細資訊，請參閱 <xref:System.Windows.Media.Colors> 命名空間中的類別屬性 <xref:System.Windows.Media> 。  
  
```xaml
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
  
 下圖顯示呈現的 <xref:System.Windows.Shapes.Ellipse> 。  
  
 ![橢圓形](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")  
  
 或者，您可以使用屬性專案語法來明確地建立 <xref:System.Windows.Media.SolidColorBrush> 物件，以純色繪製圖形。  
  
```xaml
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
  
 下圖顯示轉譯的圖形。  
  
 ![SolidColorBrush 圖例](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")  
  
 您也可以使用漸層、影像、圖樣等等繪製圖形的筆觸或填滿。 如需詳細資訊，請參閱[使用純色和](painting-with-solid-colors-and-gradients-overview.md)漸層繪製的色彩。  
  
<a name="stretchableshapessection"></a>
## <a name="stretchable-shapes"></a>可縮放的圖形  
 <xref:System.Windows.Shapes.Line>、 <xref:System.Windows.Shapes.Path> 、、 <xref:System.Windows.Shapes.Polygon> <xref:System.Windows.Shapes.Polyline> 和 <xref:System.Windows.Shapes.Rectangle> 類別都有 <xref:System.Windows.Shapes.Shape.Stretch%2A> 屬性。 這個屬性 <xref:System.Windows.Shapes.Shape> 會決定物件內容（要繪製的形狀）如何伸展以填滿 <xref:System.Windows.Shapes.Shape> 物件的版面配置空間。 <xref:System.Windows.Shapes.Shape>物件的版面配置空間是 <xref:System.Windows.Shapes.Shape> 配置系統組態的空間量，因為有明確的 <xref:System.Windows.FrameworkElement.Width%2A> 和設定， <xref:System.Windows.FrameworkElement.Height%2A> 或因為其 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 和 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 設定。 如需 Windows Presentation Foundation 中版面配置的詳細資訊，請參閱[版面](../advanced/layout.md)配置總覽。  
  
 Stretch 屬性可接受下列其中一個值：  
  
- <xref:System.Windows.Media.Stretch.None>： <xref:System.Windows.Shapes.Shape> 物件的內容不會伸展。  
  
- <xref:System.Windows.Media.Stretch.Fill>： <xref:System.Windows.Shapes.Shape> 物件的內容會伸展以填滿其版面配置空間。  不會維持外觀比例。  
  
- <xref:System.Windows.Media.Stretch.Uniform>： <xref:System.Windows.Shapes.Shape> 物件的內容會盡可能伸展以填滿其版面配置空間，同時保留其原始外觀比例。  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>： <xref:System.Windows.Shapes.Shape> 物件的內容會伸展以完全填滿其版面配置空間，同時保留其原始外觀比例。  
  
 請注意，當 <xref:System.Windows.Shapes.Shape> 物件的內容伸展時， <xref:System.Windows.Shapes.Shape> 物件的外框會在延展之後繪製。  
  
 在下列範例中， <xref:System.Windows.Shapes.Polygon> 是用來繪製從（0，0）到（0，1）到（1，1）的極小三角形。 <xref:System.Windows.Shapes.Polygon>物件的 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 會設定為100，而其 stretch 屬性會設定為 Fill。 因此， <xref:System.Windows.Shapes.Polygon> 會伸展物件的內容（三角形）以填滿較大的空間。  
  
```xaml
<Polygon  
  Points="0,0 0,1 1,1"  
  Fill="Blue"  
  Width="100"  
  Height="100"  
  Stretch="Fill"  
  Stroke="Black"  
  StrokeThickness="2" />  
```

```csharp
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
```

<a name="transforms"></a>
## <a name="transforming-shapes"></a>轉換圖形  
 <xref:System.Windows.Media.Transform>類別提供了在二維平面中轉換圖形的方法。  不同類型的轉換包括旋轉（ <xref:System.Windows.Media.RotateTransform> ）、縮放（ <xref:System.Windows.Media.ScaleTransform> ）、扭曲（ <xref:System.Windows.Media.SkewTransform> ）和轉譯（ <xref:System.Windows.Media.TranslateTransform> ）。  
  
 套用至圖形的一種常用轉換就是旋轉。  若要旋轉圖形，請建立， <xref:System.Windows.Media.RotateTransform> 並指定其 <xref:System.Windows.Media.RotateTransform.Angle%2A> 。 <xref:System.Windows.Media.RotateTransform.Angle%2A>45 的會順時針旋轉元素45度，而90的角度會順時針旋轉元素90度; 依此類推。 <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> 如果您想要控制要旋轉元素的點，請設定和屬性。 這些屬性值會以轉換之元素的座標空間表示。 <xref:System.Windows.Media.RotateTransform.CenterX%2A>和的 <xref:System.Windows.Media.RotateTransform.CenterY%2A> 預設值為零。 最後，將套用 <xref:System.Windows.Media.RotateTransform> 至元素。 如果您不想要轉換影響版面配置，請設定圖形的 <xref:System.Windows.UIElement.RenderTransform%2A> 屬性。  
  
 在下列範例中， <xref:System.Windows.Media.RotateTransform> 是用來將圖形左上角（0，0）的圖形旋轉45度。  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 在下一個範例中，另一個圖形也旋轉 45 度，但這次是從點 (25,50) 旋轉。  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 下圖顯示套用兩種轉換的結果。  
  
 ![採用不同中心點的 45 度旋轉](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
  
 在上一個範例中，已將單一轉換套用至每個圖形物件。 若要將多個轉換套用至圖形（或任何其他 UI 元素），請使用 <xref:System.Windows.Media.TransformGroup> 。  
  
## <a name="see-also"></a>另請參閱

- [2D 圖形和影像處理](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [使用純色和漸層繪製的概觀](painting-with-solid-colors-and-gradients-overview.md)
- [幾何概觀](geometry-overview.md)
- [逐步解說：我的第一個 WPF 桌面應用程式](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [動畫概觀](animation-overview.md)
