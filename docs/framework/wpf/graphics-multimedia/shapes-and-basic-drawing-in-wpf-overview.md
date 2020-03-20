---
title: 形狀和基本繪圖概述
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
ms.openlocfilehash: 44104bec478f1fbb10acc0e591af43ea95fecdc5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141324"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a>WPF 中圖案和基本繪圖概觀
本主題概述了如何使用<xref:System.Windows.Shapes.Shape>物件進行繪製。 A<xref:System.Windows.Shapes.Shape>是一種<xref:System.Windows.UIElement>允許您將形狀繪製到螢幕的類型。 由於物件是 UI<xref:System.Windows.Shapes.Shape>元素，因此可以在元素<xref:System.Windows.Controls.Panel>和大多數控制項內使用物件。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供了數層的圖形和轉譯服務存取權。 在頂層，<xref:System.Windows.Shapes.Shape>物件便於使用，並提供許多有用的功能，如佈局和參與[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]事件系統。  

<a name="shapes"></a>
## <a name="shape-objects"></a>Shape 物件  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供了許多現成的<xref:System.Windows.Shapes.Shape>物件。  所有形狀物件都從<xref:System.Windows.Shapes.Shape>類繼承。 可用的形狀物件包括<xref:System.Windows.Shapes.Ellipse> <xref:System.Windows.Shapes.Line> <xref:System.Windows.Shapes.Path>、、、<xref:System.Windows.Shapes.Polygon><xref:System.Windows.Shapes.Polyline>和<xref:System.Windows.Shapes.Rectangle>。 <xref:System.Windows.Shapes.Shape>物件共用以下公共屬性。  
  
- <xref:System.Windows.Shapes.Shape.Stroke%2A>：描述形狀輪廓的繪製方式。  
  
- <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>：描述形狀輪廓的厚度。  
  
- <xref:System.Windows.Shapes.Shape.Fill%2A>：描述形狀內部如何繪製。  
  
- 用來指定座標和頂點的資料屬性，以裝置獨立像素為單位。  
  
 因為它們派生自<xref:System.Windows.UIElement>，形狀物件可以在面板和大多數控制項內使用。 該<xref:System.Windows.Controls.Canvas>面板是創建複雜圖形的一個特別好的選擇，因為它支援其子物件的絕對位置。  
  
 該<xref:System.Windows.Shapes.Line>類使您能夠在兩點之間畫一條線。 下列範例示範用來指定線段座標和筆觸屬性的數種方法。  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 下圖顯示了渲染的<xref:System.Windows.Shapes.Line>。  
  
 ![線條圖例](./media/shape-ovw-line2.gif "shape_ovw_line2")  
  
 儘管<xref:System.Windows.Shapes.Line>類確實提供屬性<xref:System.Windows.Shapes.Shape.Fill%2A>，但設置它不起作用，<xref:System.Windows.Shapes.Line>因為 沒有區域。  
  
 另一個常見的形狀<xref:System.Windows.Shapes.Ellipse>是 。  通過定義<xref:System.Windows.Shapes.Ellipse>形狀<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>屬性創建 。 要繪製圓，請指定<xref:System.Windows.Shapes.Ellipse>其<xref:System.Windows.FrameworkElement.Width%2A><xref:System.Windows.FrameworkElement.Height%2A>和 值相等的 。  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 下圖顯示了渲染<xref:System.Windows.Shapes.Ellipse>的示例。  
  
 ![橢圓形圖例](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")  
  
<a name="paths"></a>
## <a name="using-paths-and-geometries"></a>使用路徑和幾何  
 該<xref:System.Windows.Shapes.Path>類使您能夠繪製曲線和複雜形狀。 這些曲線和形狀使用<xref:System.Windows.Media.Geometry>物件進行描述。 要使用<xref:System.Windows.Shapes.Path>， 創建<xref:System.Windows.Media.Geometry>並使用它來設置<xref:System.Windows.Shapes.Path>物件的屬性。 <xref:System.Windows.Shapes.Path.Data%2A>  
  
 有多種<xref:System.Windows.Media.Geometry>物件可供選擇。 <xref:System.Windows.Media.RectangleGeometry> <xref:System.Windows.Media.EllipseGeometry>和<xref:System.Windows.Media.LineGeometry>類描述相對簡單的形狀。 要創建更複雜的形狀或創建曲線，請使用 。 <xref:System.Windows.Media.PathGeometry>  
  
<a name="pathgeometry"></a>
### <a name="pathgeometry-and-pathsegments"></a>PathGeometry 和 PathSegments  
 <xref:System.Windows.Media.PathGeometry>物件由一個或多個<xref:System.Windows.Media.PathFigure>物件組成;每個<xref:System.Windows.Media.PathFigure>表示不同的"圖形"或形狀。 每個<xref:System.Windows.Media.PathFigure>物件本身由一個或多個<xref:System.Windows.Media.PathSegment>物件組成，每個物件表示圖形或形狀的連接部分。 段類型包括以下內容： <xref:System.Windows.Media.LineSegment>、<xref:System.Windows.Media.BezierSegment>和<xref:System.Windows.Media.ArcSegment>。  
  
 在下面的示例中， a<xref:System.Windows.Shapes.Path>用於繪製二次方貝茲曲線。  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 下列影像顯示轉譯的圖形。  
  
 ![路徑圖例](./media/shape-ovw-path2.gif "shape_ovw_path2")  
  
 有關<xref:System.Windows.Media.PathGeometry>和其他<xref:System.Windows.Media.Geometry>類的詳細資訊，請參閱[幾何概述](geometry-overview.md)。  
  
<a name="pathdatastring"></a>
### <a name="xaml-abbreviated-syntax"></a>XAML 縮寫語法  
 在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中，還可以使用特殊的縮寫語法來描述 。 <xref:System.Windows.Shapes.Path> 在下列範例中，縮寫語法是用來繪製複雜的圖形。  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 下圖顯示了渲染的<xref:System.Windows.Shapes.Path>。  
  
 ![路徑圖例](./media/shape-ovw-path.PNG "shape_ovw_path")  
  
 <xref:System.Windows.Shapes.Path.Data%2A>屬性字串以 M 指示的"moveto"命令開頭，該命令為 座標<xref:System.Windows.Controls.Canvas>系中的路徑建立起點。 <xref:System.Windows.Shapes.Path>資料參數區分大小寫。 大寫 M 表示新當前點的絕對位置。 小寫 m 則表示相對座標。 第一個線段是三次方貝茲曲線，開始於 (100,200) 並結束於 (400,175)，使用 (100,25) 和 (400,350) 這兩個控制點繪製。 此段由<xref:System.Windows.Shapes.Path.Data%2A>屬性字串中的 C 命令指示。 同樣地，大寫 C 表示絕對路徑；小寫 c 表示相對路徑。  
  
 第二個線段的開頭為絕對水平 "lineto" 命令 H，它會指定從前面的子路徑的端點 (400,175) 到新端點 (280,175) 繪製的線段。 因為它是水準的"lineto"命令，因此指定的值是*x*座標。  
  
 有關完整的路徑語法，請參閱引用<xref:System.Windows.Shapes.Path.Data%2A>並使用[路徑幾何創建形狀](how-to-create-a-shape-by-using-a-pathgeometry.md)。  
  
<a name="fillpaint"></a>
## <a name="painting-shapes"></a>繪製圖形  
 <xref:System.Windows.Media.Brush>物件用於繪製形狀的<xref:System.Windows.Shapes.Shape.Stroke%2A>和<xref:System.Windows.Shapes.Shape.Fill%2A>。 在下面的示例中，指定 了 描<xref:System.Windows.Shapes.Ellipse>邊和填充。 請注意，筆刷屬性的有效輸入可以是關鍵字或十六進位色彩值。 有關可用顏色關鍵字的詳細資訊，請參閱<xref:System.Windows.Media.Colors><xref:System.Windows.Media>命名空間中的類的屬性。  
  
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
  
 下圖顯示了渲染的<xref:System.Windows.Shapes.Ellipse>。  
  
 ![橢圓形](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")  
  
 或者，可以使用屬性元素語法顯式創建物件<xref:System.Windows.Media.SolidColorBrush>以繪製具有純色的形狀。  
  
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
  
 您也可以使用漸層、影像、圖樣等等繪製圖形的筆觸或填滿。 有關詳細資訊，請參閱[具有純色和漸變的繪畫概述](painting-with-solid-colors-and-gradients-overview.md)。  
  
<a name="stretchableshapessection"></a>
## <a name="stretchable-shapes"></a>可縮放的圖形  
 <xref:System.Windows.Shapes.Line> <xref:System.Windows.Shapes.Path>、、、<xref:System.Windows.Shapes.Polygon><xref:System.Windows.Shapes.Polyline>和<xref:System.Windows.Shapes.Rectangle>類都具有<xref:System.Windows.Shapes.Shape.Stretch%2A>屬性。 此屬性確定如何拉伸<xref:System.Windows.Shapes.Shape>物件的內容（要繪製的形狀）以填充<xref:System.Windows.Shapes.Shape>物件的佈局空間。 <xref:System.Windows.Shapes.Shape>物件的佈局空間是佈局系統<xref:System.Windows.Shapes.Shape>分配的空間量，因為佈局系統具有顯式<xref:System.Windows.FrameworkElement.Width%2A>設置和<xref:System.Windows.FrameworkElement.Height%2A>設置，也因為它<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>及其和<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>設置。 有關 Windows 演示文稿基礎中佈局的其他資訊，請參閱[佈局](../advanced/layout.md)概述。  
  
 Stretch 屬性可接受下列其中一個值：  
  
- <xref:System.Windows.Media.Stretch.None>：<xref:System.Windows.Shapes.Shape>物件的內容不會拉伸。  
  
- <xref:System.Windows.Media.Stretch.Fill>：<xref:System.Windows.Shapes.Shape>物件的內容被拉伸以填充其佈局空間。  不會維持外觀比例。  
  
- <xref:System.Windows.Media.Stretch.Uniform>：物件<xref:System.Windows.Shapes.Shape>的內容盡可能拉伸以填充其佈局空間，同時保持其原始縱橫比。  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>：物件<xref:System.Windows.Shapes.Shape>的內容被拉伸以完全填充其佈局空間，同時保持其原始縱橫比。  
  
 請注意，當<xref:System.Windows.Shapes.Shape>物件的內容拉伸時，<xref:System.Windows.Shapes.Shape>物件的輪廓在拉伸後繪製。  
  
 在下面的示例中，a<xref:System.Windows.Shapes.Polygon>用於繪製一個非常小的三角形，從 （0，0） 到 （0，1） 到 （1，1）。 物件的<xref:System.Windows.Shapes.Polygon><xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>設置為 100，其拉伸屬性設置為"填充"。 因此，<xref:System.Windows.Shapes.Polygon>物件的內容（三角形）被拉伸以填充更大的空間。  
  
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
 類<xref:System.Windows.Media.Transform>提供了在二維平面中變換形狀的方法。  不同類型的變換<xref:System.Windows.Media.RotateTransform>包括旋轉 （ ）、刻度 （<xref:System.Windows.Media.ScaleTransform>）、傾斜<xref:System.Windows.Media.SkewTransform>（ ）<xref:System.Windows.Media.TranslateTransform>和轉換 （ 。  
  
 套用至圖形的一種常用轉換就是旋轉。  要旋轉形狀，請創建<xref:System.Windows.Media.RotateTransform>並指定其<xref:System.Windows.Media.RotateTransform.Angle%2A>。 a <xref:System.Windows.Media.RotateTransform.Angle%2A> 45 順時針旋轉元素 45 度;角度為 90 沿順時針旋轉元件 90 度;等等。 如果要控制<xref:System.Windows.Media.RotateTransform.CenterX%2A>元素<xref:System.Windows.Media.RotateTransform.CenterY%2A>旋轉的點，則設置 和 屬性。 這些屬性值會以轉換之元素的座標空間表示。 <xref:System.Windows.Media.RotateTransform.CenterX%2A>預設值<xref:System.Windows.Media.RotateTransform.CenterY%2A>為零。 最後，將<xref:System.Windows.Media.RotateTransform>應用 到 元素。 如果不希望變換影響佈局，則設置形狀的<xref:System.Windows.UIElement.RenderTransform%2A>屬性。  
  
 在下面的示例中，a<xref:System.Windows.Media.RotateTransform>用於圍繞形狀的左上角 （0，0） 旋轉 45 度的形狀。  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 在下一個範例中，另一個圖形也旋轉 45 度，但這次是從點 (25,50) 旋轉。  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 下圖顯示套用兩種轉換的結果。  
  
 ![採用不同中心點的 45 度旋轉](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
  
 在上一個範例中，已將單一轉換套用至每個圖形物件。 要將多個轉換應用於形狀（或任何其他 UI 元素），請使用 。 <xref:System.Windows.Media.TransformGroup>  
  
## <a name="see-also"></a>另請參閱

- [2D 圖形和影像處理](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [使用純色和漸層繪製的概觀](painting-with-solid-colors-and-gradients-overview.md)
- [幾何概觀](geometry-overview.md)
- [逐步解說：我的第一個 WPF 桌面應用程式](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [動畫概觀](animation-overview.md)
