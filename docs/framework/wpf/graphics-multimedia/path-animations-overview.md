---
title: "路徑動畫概觀 | Microsoft Docs"
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
  - "路徑動畫"
  - "路徑動畫"
ms.assetid: 979c732c-df74-47a6-be96-8e07b3707d53
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 路徑動畫概觀
<a name="introduction"></a>本主題將介紹路徑動畫，讓您使用幾何路徑來產生輸出值。 路徑動畫很適合用來移動和旋轉物件沿著複雜路徑。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 若要了解本主題，您應該熟悉[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]動畫功能。 如需簡介動畫功能，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
 因為您使用<xref:System.Windows.Media.PathGeometry>物件來定義路徑動畫，您也應該熟悉<xref:System.Windows.Media.PathGeometry>和不同類型的<xref:System.Windows.Media.PathSegment>物件。 如需詳細資訊，請參閱[幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)。  
  
<a name="what_is_a_path_animation"></a>   
## <a name="what-is-a-path-animation"></a>路徑動畫是什麼？  
 路徑動畫是一種<xref:System.Windows.Media.Animation.AnimationTimeline>使用<xref:System.Windows.Media.PathGeometry>做為輸入。 而不是，設定 From、 或屬性 (像您使用 From/To/By 動畫) 或使用主要畫面格 （當您使用主要畫面格動畫），定義幾何路徑，並將它用於設定`PathGeometry`路徑動畫的屬性。 路徑動畫進行時，它會讀取路徑中的 x、 y 和角度資訊並使用該資訊來產生其輸出。  
  
 路徑動畫是適用於複雜路徑的物件非常有用。 其中一種方式將物件沿著路徑是使用<xref:System.Windows.Media.MatrixTransform>和<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>轉換複雜路徑的物件。 下列範例會示範這項技術使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>物件來建立動畫<xref:System.Windows.Media.MatrixTransform.Matrix%2A>屬性<xref:System.Windows.Media.MatrixTransform>。 <xref:System.Windows.Media.MatrixTransform>套用至按鈕，因而會沿著曲線路徑移動。 因為<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>屬性設定為`true`，矩形就會旋轉沿著路徑的正切函數。  
  
 [!code-xml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 如需有關使用中的路徑語法[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]範例中，請參閱[路徑標記語法](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)概觀。 如需完整的範例，請參閱[路徑動畫範例](http://go.microsoft.com/fwlink/?LinkID=160028)。  
  
 您也可以使用屬性來套用路徑動畫<xref:System.Windows.Media.Animation.Storyboard>中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]和程式碼，或使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>程式碼中的方法。 您也可以使用路徑動畫建立<xref:System.Windows.Media.Animation.AnimationClock>並將它套用到一或多個屬性。 如需套用動畫的不同方法的詳細資訊，請參閱[屬性動畫技術概觀](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)。  
  
<a name="animation_types"></a>   
## <a name="path-animation-types"></a>路徑動畫類型  
 動畫會產生屬性值，因為不同的動畫類型有不同的屬性類型。 若要動畫顯示採用的屬性<xref:System.Double>(例如[X](assetId:///P:System.Windows.Media.TranslateTransform.X?qualifyHint=False&autoUpgrade=True)屬性[TranslateTransform](assetId:///T:System.Windows.Media.TranslateTransform?qualifyHint=False&autoUpgrade=True))，您使用的動畫，會產生<xref:System.Double>值。 若要建立採用屬性的動畫<xref:System.Windows.Point>，您使用的動畫，會產生<xref:System.Windows.Point>值，依此類推。  
  
 路徑動畫類別屬於<xref:System.Windows.Media.Animation>命名空間，並使用下列命名慣例︰  
  
 *<>\>*`AnimationUsingPath`  
  
 其中* <> \> *是類別產生動畫的值的型別。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供下列路徑的動畫類別。  
  
|屬性類型|相對路徑動畫類別|範例|  
|-------------------|----------------------------------------|-------------|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|[沿著路徑 （雙動畫） 建立物件](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-double-animation.md)|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>|[沿著路徑動畫 （矩陣動畫） 建立物件](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md)|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|[沿著路徑動畫 （點動畫） 建立物件](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-point-animation.md)|  
  
 A <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>產生<xref:System.Windows.Media.Matrix>值從其<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.PathGeometry%2A>。 當搭配<xref:System.Windows.Media.MatrixTransform>、 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>可以移動路徑上的物件。 如果您設定<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>屬性<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>至`true`，也會旋轉物件沿著路徑的曲線。  
  
 A <xref:System.Windows.Media.Animation.PointAnimationUsingPath>產生<xref:System.Windows.Point>值從 x 和 y 座標的其<xref:System.Windows.Media.Animation.PointAnimationUsingPath.PathGeometry%2A>。 使用<xref:System.Windows.Media.Animation.PointAnimationUsingPath>動畫屬性採用<xref:System.Windows.Point>值，您可以移動路徑上的物件。 A <xref:System.Windows.Media.Animation.PointAnimationUsingPath>無法旋轉物件。  
  
 A <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>產生<xref:System.Double>值從其<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>。 藉由設定<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.Source%2A>屬性，您可以指定是否<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>作為它的輸出會使用 x、 y 軸座標或路徑的角度。 您可以使用<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>旋轉物件，或將它移沿著 x 軸或 y 軸。  
  
<a name="pathanimationinput"></a>   
## <a name="path-animation-input"></a>路徑動畫輸出  
 每個路徑動畫類別提供<xref:System.Windows.Media.PathGeometry>屬性來指定其輸入。 路徑動畫使用<xref:System.Windows.Media.PathGeometry>來產生其輸出值。 <xref:System.Windows.Media.PathGeometry>類別可讓您描述多個複雜的數字組成的弧形、 曲線和程式碼行。  
  
 核心<xref:System.Windows.Media.PathGeometry>是一組<xref:System.Windows.Media.PathFigure>物件; 這些物件如此命名，因為每個圖會說明中的離散圖形<xref:System.Windows.Media.PathGeometry>。 每個<xref:System.Windows.Media.PathFigure>包含一個或多個<xref:System.Windows.Media.PathSegment>物件，其中每個說明圖中的區段。  
  
 有許多類型的區段。  
  
|區段類型|說明|  
|------------------|-----------------|  
|<xref:System.Windows.Media.ArcSegment>|建立兩個點之間的橢圓弧形。|  
|<xref:System.Windows.Media.BezierSegment>|建立兩個點之間的三次方貝茲曲線。|  
|<xref:System.Windows.Media.LineSegment>|會建立兩個點之間的線。|  
|<xref:System.Windows.Media.PolyBezierSegment>|建立一系列三次方貝茲曲線。|  
|<xref:System.Windows.Media.PolyLineSegment>|建立一系列的行。|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|建立一系列二次方貝茲曲線。|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|建立二次方貝茲曲線。|  
  
 中的區段<xref:System.Windows.Media.PathFigure>會結合成單一幾何形狀，會使用區段的結束點做為下一個區段的起始點。 <xref:System.Windows.Media.PathFigure.StartPoint%2A>屬性<xref:System.Windows.Media.PathFigure>指定所繪製的第一個區段的點。 每個後續區段開始的上一個區段的結束點。 例如，垂直列從`10,50`至`10,150`可以藉由設定定義<xref:System.Windows.Media.PathFigure.StartPoint%2A>屬性`10,50`和建立<xref:System.Windows.Media.LineSegment>與<xref:System.Windows.Media.LineSegment.Point%2A>屬性設定為`10,150`。  
  
 如需詳細資訊<xref:System.Windows.Media.PathGeometry>物件，請參閱[幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)。  
  
 在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您也可以使用特殊的縮寫的語法來設定<xref:System.Windows.Media.PathGeometry.Figures%2A>屬性<xref:System.Windows.Media.PathGeometry>。 如需詳細資訊，請參閱[路徑標記語法](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)概觀。  
  
 如需有關使用中的路徑語法[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]範例中，請參閱[路徑標記語法](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)概觀。  
  
## <a name="see-also"></a>另請參閱  
 [路徑動畫範例](http://go.microsoft.com/fwlink/?LinkID=160028)   
 [路徑標記語法](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)   
 [路徑動畫 how to 主題](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [屬性動畫技術概觀](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)