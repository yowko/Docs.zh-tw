---
title: WPF 中圖案和基本繪圖概觀
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
ms.openlocfilehash: 47df352c3b001f088f34ea057b34698efc4f4b53
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086800"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a>WPF 中圖案和基本繪圖概觀
本主題概要說明如何使用繪圖<xref:System.Windows.Shapes.Shape>物件。 A<xref:System.Windows.Shapes.Shape>是一種<xref:System.Windows.UIElement>，可讓您將圖形描繪至螢幕。 因為它們是 UI 元素<xref:System.Windows.Shapes.Shape>物件都可以使用內部<xref:System.Windows.Controls.Panel>元素以及大部分的控制項。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供了數層的圖形和轉譯服務存取權。 位於最上層<xref:System.Windows.Shapes.Shape>物件都很容易使用，並提供許多實用的功能，例如版面配置和參與[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]事件系統。  
  
  
<a name="shapes"></a>   
## <a name="shape-objects"></a>Shape 物件  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供數個已準備好使用<xref:System.Windows.Shapes.Shape>物件。  所有的 shape 物件繼承自<xref:System.Windows.Shapes.Shape>類別。 可用的 shape 物件包含<xref:System.Windows.Shapes.Ellipse>， <xref:System.Windows.Shapes.Line>， <xref:System.Windows.Shapes.Path>， <xref:System.Windows.Shapes.Polygon>， <xref:System.Windows.Shapes.Polyline>，和<xref:System.Windows.Shapes.Rectangle>。 <xref:System.Windows.Shapes.Shape> 物件共用下列通用屬性。  
  
-   <xref:System.Windows.Shapes.Shape.Stroke%2A>： 說明如何繪製圖形外框。  
  
-   <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>： 說明圖形外框的粗細。  
  
-   <xref:System.Windows.Shapes.Shape.Fill%2A>： 描述如何繪製形狀的內部。  
  
-   用來指定座標和頂點的資料屬性，以裝置獨立像素為單位。  
  
 因為它們衍生自<xref:System.Windows.UIElement>，shape 物件可以用在面板和大部分的控制項。 <xref:System.Windows.Controls.Canvas>面板是特別適合用來建立複雜的繪圖，因為它支援其子物件的絕對位置。  
  
 <xref:System.Windows.Shapes.Line>類別可讓您在兩點之間繪製一條線。 下列範例示範用來指定線段座標和筆觸屬性的數種方法。  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 下圖顯示轉譯<xref:System.Windows.Shapes.Line>。  
  
 ![線段圖例](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-line2.gif "shape_ovw_line2")  
  
 雖然<xref:System.Windows.Shapes.Line>類別會提供<xref:System.Windows.Shapes.Shape.Fill%2A>屬性，並將它沒有任何作用，因為<xref:System.Windows.Shapes.Line>沒有任何區域。  
  
 另一個常見的圖形是<xref:System.Windows.Shapes.Ellipse>。  建立<xref:System.Windows.Shapes.Ellipse>藉由定義形狀<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>屬性。 若要繪製圓形，指定<xref:System.Windows.Shapes.Ellipse>其<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>值是否相等。  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 下圖顯示呈現的範例<xref:System.Windows.Shapes.Ellipse>。  
  
 ![橢圓形圖例](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")  
  
<a name="paths"></a>   
## <a name="using-paths-and-geometries"></a>使用路徑和幾何  
 <xref:System.Windows.Shapes.Path>類別可讓您繪製曲線以及複雜的圖形。 這些曲線和圖形說明使用<xref:System.Windows.Media.Geometry>物件。 若要使用<xref:System.Windows.Shapes.Path>，您會建立<xref:System.Windows.Media.Geometry>並用它來設定<xref:System.Windows.Shapes.Path>物件的<xref:System.Windows.Shapes.Path.Data%2A>屬性。  
  
 有各種不同的<xref:System.Windows.Media.Geometry>可從中選擇的物件。 <xref:System.Windows.Media.LineGeometry>， <xref:System.Windows.Media.RectangleGeometry>，和<xref:System.Windows.Media.EllipseGeometry>類別描述相對簡單的圖形。 若要建立更複雜的圖形，或建立曲線，使用<xref:System.Windows.Media.PathGeometry>。  
  
<a name="pathgeometry"></a>   
### <a name="pathgeometry-and-pathsegments"></a>PathGeometry 和 PathSegments  
 <xref:System.Windows.Media.PathGeometry> 物件包含一或多個<xref:System.Windows.Media.PathFigure>物件; 每個<xref:System.Windows.Media.PathFigure>代表不同的 「 圖形 」 或圖案。 每個<xref:System.Windows.Media.PathFigure>本身包含一或多個<xref:System.Windows.Media.PathSegment>物件，每個均代表圖形或圖案的已連接的部分。 線段類型包括下列： <xref:System.Windows.Media.LineSegment>， <xref:System.Windows.Media.BezierSegment>，和<xref:System.Windows.Media.ArcSegment>。  
  
 在下列範例中，<xref:System.Windows.Shapes.Path>會用來繪製二次方貝茲曲線。  
  
 [!code-xaml[geometrysample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 下列影像顯示轉譯的圖形。  
  
 ![路徑圖例](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path2.gif "shape_ovw_path2")  
  
 如需詳細資訊<xref:System.Windows.Media.PathGeometry>和其他<xref:System.Windows.Media.Geometry>類別，請參閱[幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)。  
  
<a name="pathdatastring"></a>   
### <a name="xaml-abbreviated-syntax"></a>XAML 縮寫語法  
 在  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，您也可以使用特殊的縮寫的語法來描述<xref:System.Windows.Shapes.Path>。 在下列範例中，縮寫語法是用來繪製複雜的圖形。  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 下圖顯示轉譯<xref:System.Windows.Shapes.Path>。  
  
 ![路徑圖例](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path.PNG "shape_ovw_path")  
  
 <xref:System.Windows.Shapes.Path.Data%2A>屬性字串的開頭"moveto"命令，以 M 指示，以建立路徑的開始點的座標系統中<xref:System.Windows.Controls.Canvas>。 <xref:System.Windows.Shapes.Path> 資料參數會區分大小寫。 大寫 M 表示新的目前點的絕對位置。 小寫 m 則表示相對座標。 第一個線段是三次方貝茲曲線，開始於 (100,200) 並結束於 (400,175)，使用 (100,25) 和 (400,350) 這兩個控制點繪製。 此區段會以中的 C 命令<xref:System.Windows.Shapes.Path.Data%2A>屬性字串。 同樣地，大寫 C 表示絕對路徑；小寫 c 表示相對路徑。  
  
 第二個線段的開頭為絕對水平 "lineto" 命令 H，它會指定從前面的子路徑的端點 (400,175) 到新端點 (280,175) 繪製的線段。 它是水平"lineto"命令，因為指定的值是*x*-協調。  
  
 如需完整的路徑語法，請參閱<xref:System.Windows.Shapes.Path.Data%2A>參考和[使用 PathGeometry 建立圖案](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)。  
  
<a name="fillpaint"></a>   
## <a name="painting-shapes"></a>繪製圖形  
 <xref:System.Windows.Media.Brush> 物件用來繪製形狀<xref:System.Windows.Shapes.Shape.Stroke%2A>和<xref:System.Windows.Shapes.Shape.Fill%2A>。 在下列範例中，筆觸和填滿<xref:System.Windows.Shapes.Ellipse>所指定。 請注意，筆刷屬性的有效輸入可以是關鍵字或十六進位色彩值。 如需可用的色彩關鍵字的詳細資訊，請參閱的內容<xref:System.Windows.Media.Colors>類別中<xref:System.Windows.Media>命名空間。  
  
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
  
 下圖顯示轉譯<xref:System.Windows.Shapes.Ellipse>。  
  
 ![橢圓形](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")  
  
 或者，您可以使用屬性元素語法明確建立<xref:System.Windows.Media.SolidColorBrush>物件來繪製圖案和純色。  
  
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
  
 ![SolidColorBrush 圖例](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")  
  
 您也可以使用漸層、影像、圖樣等等繪製圖形的筆觸或填滿。 如需詳細資訊，請參閱 <<c0> [ 使用純色和漸層概觀繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)。  
  
<a name="stretchableshapessection"></a>   
## <a name="stretchable-shapes"></a>可縮放的圖形  
 <xref:System.Windows.Shapes.Line>， <xref:System.Windows.Shapes.Path>， <xref:System.Windows.Shapes.Polygon>， <xref:System.Windows.Shapes.Polyline>，並<xref:System.Windows.Shapes.Rectangle>類別都有<xref:System.Windows.Shapes.Shape.Stretch%2A>屬性。 此屬性會決定如何<xref:System.Windows.Shapes.Shape>物件的內容 （要繪製的圖形） 會縮放以填滿<xref:System.Windows.Shapes.Shape>物件的版面配置空間。 A<xref:System.Windows.Shapes.Shape>物件的版面配置空間是空間數量<xref:System.Windows.Shapes.Shape>配置版面配置系統，因為明確<xref:System.Windows.FrameworkElement.Width%2A>並<xref:System.Windows.FrameworkElement.Height%2A>設定或因為其<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>和<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>設定。 如需其他有關 Windows Presentation Foundation 中版面配置的詳細資訊，請參閱[版面配置](../../../../docs/framework/wpf/advanced/layout.md)概觀。  
  
 Stretch 屬性可接受下列其中一個值：  
  
-   <xref:System.Windows.Media.Stretch.None>:<xref:System.Windows.Shapes.Shape>物件的內容不會自動縮放。  
  
-   <xref:System.Windows.Media.Stretch.Fill>:<xref:System.Windows.Shapes.Shape>物件的內容會縮放以填滿其版面配置空間。  不會維持外觀比例。  
  
-   <xref:System.Windows.Media.Stretch.Uniform>:<xref:System.Windows.Shapes.Shape>物件的內容會縮放，盡量以填滿其版面配置空間，同時維持原始外觀比例。  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill>:<xref:System.Windows.Shapes.Shape>物件的內容會縮放以完全填滿其版面配置空間，同時維持原始外觀比例。  
  
 請注意，當<xref:System.Windows.Shapes.Shape>物件的內容會縮放，<xref:System.Windows.Shapes.Shape>縮放之後繪製物件的外框。  
  
 在下列範例中，<xref:System.Windows.Shapes.Polygon>若 (1，1) 要用來繪製從 (0，0) 到 (0，1) 非常小的三角形。 <xref:System.Windows.Shapes.Polygon>物件的<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>設為 100，和其縮放屬性設定為 Fill。 如此一來，<xref:System.Windows.Shapes.Polygon>物件的內容 （三角形） 會縮放以填滿較大的空間。  
  
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
 <xref:System.Windows.Media.Transform>類別提供方法來轉換二維平面中的圖形。  不同類型的轉換包括旋轉 (<xref:System.Windows.Media.RotateTransform>)，小數位數 (<xref:System.Windows.Media.ScaleTransform>)、 扭曲 (<xref:System.Windows.Media.SkewTransform>)，以及轉譯 (<xref:System.Windows.Media.TranslateTransform>)。  
  
 套用至圖形的一種常用轉換就是旋轉。  若要旋轉圖形，建立<xref:System.Windows.Media.RotateTransform>並指定其<xref:System.Windows.Media.RotateTransform.Angle%2A>。 <xref:System.Windows.Media.RotateTransform.Angle%2A> 45 的項目 45 順時針旋轉度; 角度 90 則會將元素 90 度順時針旋轉，以此類推。 設定<xref:System.Windows.Media.RotateTransform.CenterX%2A>和<xref:System.Windows.Media.RotateTransform.CenterY%2A>屬性，如果您想要控制哪些項目會旋轉的點。 這些屬性值會以轉換之元素的座標空間表示。 <xref:System.Windows.Media.RotateTransform.CenterX%2A> 和<xref:System.Windows.Media.RotateTransform.CenterY%2A>有預設值為零。 最後，將套用<xref:System.Windows.Media.RotateTransform>的項目。 如果您不想轉換影響版面配置，設定圖形的<xref:System.Windows.UIElement.RenderTransform%2A>屬性。  
  
 在下列範例中，<xref:System.Windows.Media.RotateTransform>來旋轉圖形的左上角 (0，0) 圖形 45 度。  
  
 [!code-xaml[transformssample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 在下一個範例中，另一個圖形也旋轉 45 度，但這次是從點 (25,50) 旋轉。  
  
 [!code-xaml[transformssample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 下圖顯示套用兩種轉換的結果。  
  
 ![不同中心點的 45 度旋轉](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
  
 在上一個範例中，已將單一轉換套用至每個圖形物件。 若要將多個轉換套用至圖形 （或任何其他 UI 項目），使用<xref:System.Windows.Media.TransformGroup>。  
  
## <a name="see-also"></a>另請參閱  
 [2D 圖形和影像處理](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [逐步解說：我的第一個 WPF 傳統型應用程式](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
