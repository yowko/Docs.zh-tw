---
title: 路徑動畫概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], paths
- path animations [WPF]
ms.assetid: 979c732c-df74-47a6-be96-8e07b3707d53
ms.openlocfilehash: 0f795ad00823e7b1c37221f7417b09d3982c4c18
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44047057"
---
# <a name="path-animations-overview"></a>路徑動畫概觀
<a name="introduction"></a> 本主題將介紹路徑動畫，它可讓您使用幾何路徑來產生輸出值。 路徑動畫很適合用來沿著複雜路徑移動和旋轉物件。  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 若要了解本主題，您應該熟悉[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]動畫功能。 如需動畫功能，請參閱 <<c0> [ 動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
 因為您是使用<xref:System.Windows.Media.PathGeometry>物件來定義路徑動畫，您也應該熟悉<xref:System.Windows.Media.PathGeometry>和不同類型的<xref:System.Windows.Media.PathSegment>物件。 如需詳細資訊，請參閱 <<c0> [ 幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)。  
  
<a name="what_is_a_path_animation"></a>   
## <a name="what-is-a-path-animation"></a>什麼是路徑動畫？  
 路徑動畫是一種<xref:System.Windows.Media.Animation.AnimationTimeline>使用<xref:System.Windows.Media.PathGeometry>做為輸入。 而不是，設定 From、 或由屬性 (就像是針對 From/To/By 動畫) 或使用主要畫面格 （當您使用主要畫面格動畫），您定義幾何路徑並使用它來設定`PathGeometry`路徑動畫的屬性。 路徑動畫進行時，它會讀取路徑中的 X、Y 和角度資訊，並使用該資訊產生其輸出。  
  
 路徑動畫非常適合用來沿著複雜路徑建立物件的動畫。 將沿著路徑的物件是使用單向<xref:System.Windows.Media.MatrixTransform>和<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>轉換沿著複雜路徑物件。 下列範例示範使用的這項技巧<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>來以動畫顯示的物件<xref:System.Windows.Media.MatrixTransform.Matrix%2A>屬性<xref:System.Windows.Media.MatrixTransform>。 <xref:System.Windows.Media.MatrixTransform>會套用至按鈕，使它沿著曲線路徑移動。 因為<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>屬性設定為`true`，矩形會沿著路徑的正切函數旋轉。  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 如需路徑的語法中使用的詳細資訊[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]範例中，請參閱 <<c2> [ 路徑標記語法](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)概觀。 如需完整的範例，請參閱[路徑動畫範例](https://go.microsoft.com/fwlink/?LinkID=160028)。  
  
 您也可以使用屬性來套用路徑動畫<xref:System.Windows.Media.Animation.Storyboard>中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]和程式碼，或使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>在程式碼中的方法。 您也可以使用路徑動畫建立<xref:System.Windows.Media.Animation.AnimationClock>並將它套用至一或多個屬性。 如需套用動畫的不同方法的詳細資訊，請參閱[屬性動畫技術概觀](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)。  
  
<a name="animation_types"></a>   
## <a name="path-animation-types"></a>路徑動畫類型  
 由於動畫會產生屬性值，因此針對不同的屬性類型會有不同的動畫類型。 若要動畫顯示採用的屬性<xref:System.Double>(例如<xref:System.Windows.Media.TranslateTransform.X%2A>屬性<xref:System.Windows.Media.TranslateTransform>)，您使用會產生動畫<xref:System.Double>值。 若要動畫顯示採用的屬性<xref:System.Windows.Point>，您使用會產生動畫<xref:System.Windows.Point>值，並依此類推。  
  
 路徑動畫類別屬於<xref:System.Windows.Media.Animation>命名空間，並使用下列命名慣例：  
  
 *\<Type>* `AnimationUsingPath`  
  
 其中 *\<Type>* 是該類別建立動畫的值類型。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供下列路徑動畫類別。  
  
|屬性類型|對應路徑動畫類別|範例|  
|-------------------|----------------------------------------|-------------|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|[沿著路徑建立物件的動畫 (Double 動畫)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-double-animation.md)|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>|[沿著路徑建立物件的動畫 (矩陣動畫)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md)|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|[沿著路徑建立物件的動畫 (點動畫)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-point-animation.md)|  
  
 A<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>會產生<xref:System.Windows.Media.Matrix>值從其<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.PathGeometry%2A>。 當搭配<xref:System.Windows.Media.MatrixTransform>、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>可以移動路徑的物件。 如果您設定<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>的屬性<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>到`true`，它也會旋轉沿著曲線路徑的物件。  
  
 A<xref:System.Windows.Media.Animation.PointAnimationUsingPath>會產生<xref:System.Windows.Point>從 x 和 y 座標的值及其<xref:System.Windows.Media.Animation.PointAnimationUsingPath.PathGeometry%2A>。 藉由使用<xref:System.Windows.Media.Animation.PointAnimationUsingPath>來以動畫顯示屬性<xref:System.Windows.Point>值，您可以移動沿著路徑的物件。 A<xref:System.Windows.Media.Animation.PointAnimationUsingPath>無法旋轉物件。  
  
 A<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>會產生<xref:System.Double>值從其<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>。 藉由設定<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.Source%2A>屬性，您可以指定是否<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>的 x 座標、 y 座標或角度路徑做為其輸出。 您可以使用<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>旋轉物件，或將它移沿著 x 軸或 y 軸。  
  
<a name="pathanimationinput"></a>   
## <a name="path-animation-input"></a>路徑動畫輸入  
 每個路徑動畫類別都提供<xref:System.Windows.Media.PathGeometry>屬性以指定其輸入。 路徑動畫使用<xref:System.Windows.Media.PathGeometry>來產生其輸出值。 <xref:System.Windows.Media.PathGeometry>類別可讓您描述多個複雜形狀組成的弧線、 曲線和線條。  
  
 核心<xref:System.Windows.Media.PathGeometry>是一堆<xref:System.Windows.Media.PathFigure>物件，這些物件會如此命名，因為每個圖表都會描述中的特定圖形<xref:System.Windows.Media.PathGeometry>。 每個<xref:System.Windows.Media.PathFigure>包含一個或多個<xref:System.Windows.Media.PathSegment>物件，其中每個描述圖的區段。  
  
 區段的類型繁多。  
  
|區段類型|描述|  
|------------------|-----------------|  
|<xref:System.Windows.Media.ArcSegment>|在兩個點之間建立橢圓形弧線。|  
|<xref:System.Windows.Media.BezierSegment>|在兩個點之間建立三次方貝茲曲線。|  
|<xref:System.Windows.Media.LineSegment>|在兩個點之間建立線條。|  
|<xref:System.Windows.Media.PolyBezierSegment>|建立一系列三次方貝茲曲線。|  
|<xref:System.Windows.Media.PolyLineSegment>|建立一系列的線條。|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|建立一系列二次方貝茲曲線。|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|建立二次方貝茲曲線。|  
  
 中的區段<xref:System.Windows.Media.PathFigure>會結合成單一幾何圖形，這個圖形區段的結束點做為下一個區段的起始點。 <xref:System.Windows.Media.PathFigure.StartPoint%2A>屬性<xref:System.Windows.Media.PathFigure>指定從中繪製的第一個區段的點。 每個後續區段都會從前一個區段的結束點開始。 比方說，從垂直線`10,50`要`10,150`可以藉由設定定義<xref:System.Windows.Media.PathFigure.StartPoint%2A>屬性設`10,50`並建立<xref:System.Windows.Media.LineSegment>與<xref:System.Windows.Media.LineSegment.Point%2A>屬性設定`10,150`。  
  
 如需詳細資訊<xref:System.Windows.Media.PathGeometry>物件，請參閱[幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)。  
  
 在  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您也可以使用特殊的縮寫的語法來設定<xref:System.Windows.Media.PathGeometry.Figures%2A>屬性<xref:System.Windows.Media.PathGeometry>。 如需詳細資訊，請參閱 <<c0> [ 路徑標記語法](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)概觀。  
  
 如需路徑的語法中使用的詳細資訊[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]範例中，請參閱 <<c2> [ 路徑標記語法](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)概觀。  
  
## <a name="see-also"></a>另請參閱  
 [路徑動畫範例](https://go.microsoft.com/fwlink/?LinkID=160028)  
 [路徑標記語法](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)  
 [路徑動畫操作說明主題](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [屬性動畫技術概觀](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
