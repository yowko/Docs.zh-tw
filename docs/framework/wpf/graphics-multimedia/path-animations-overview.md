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
ms.openlocfilehash: 07628d26c8222c7c01f58826a36a15e13dc31ff4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181872"
---
# <a name="path-animations-overview"></a>路徑動畫概觀
<a name="introduction"></a> 本主題將介紹路徑動畫，它可讓您使用幾何路徑來產生輸出值。 路徑動畫很適合用來沿著複雜路徑移動和旋轉物件。  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>必要條件  
 要理解本主題，您應該熟悉[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]動畫功能。 有關動畫功能的簡介，請參閱[動畫概述](animation-overview.md)。  
  
 由於使用<xref:System.Windows.Media.PathGeometry>物件定義路徑動畫，因此還應熟悉<xref:System.Windows.Media.PathGeometry>和不同類型的<xref:System.Windows.Media.PathSegment>物件。 有關詳細資訊，請參閱[幾何概述](geometry-overview.md)。  
  
<a name="what_is_a_path_animation"></a>
## <a name="what-is-a-path-animation"></a>什麼是路徑動畫？  
 路徑動畫是使用 的<xref:System.Windows.Media.Animation.AnimationTimeline>一<xref:System.Windows.Media.PathGeometry>種類型，用作其輸入。 而不是設置"從"、"到"或"按"屬性（如對 From/To/By 動畫執行）或使用關鍵幀（如用於關鍵幀動畫），而是定義幾何路徑並使用它來設置路徑動畫`PathGeometry`的屬性。 路徑動畫進行時，它會讀取路徑中的 X、Y 和角度資訊，並使用該資訊產生其輸出。  
  
 路徑動畫非常適合用來沿著複雜路徑建立物件的動畫。 沿路徑移動物件的一種方法是使用<xref:System.Windows.Media.MatrixTransform>和<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>沿複雜路徑轉換物件。 下面的示例演示了此技術，<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>方法是使用 物件為<xref:System.Windows.Media.MatrixTransform.Matrix%2A>屬性設置動畫<xref:System.Windows.Media.MatrixTransform>。 <xref:System.Windows.Media.MatrixTransform>應用於按鈕，使其沿曲線路徑移動。 由於<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>屬性設置為`true`，矩形沿路徑的切線旋轉。  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 有關[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]示例中使用的路徑語法的詳細資訊，請參閱[路徑標記語法](path-markup-syntax.md)概述。 有關完整示例，請參閱[路徑動畫示例](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)。  
  
 可以使用<xref:System.Windows.Media.Animation.Storyboard>in[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]和 代碼或在代碼中使用 方法將<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>路徑動畫應用於屬性。 您還可以使用路徑動畫創建 ，<xref:System.Windows.Media.Animation.AnimationClock>並將其應用於一個或多個屬性。 有關應用動畫的不同方法的詳細資訊，請參閱[屬性動畫技術概述](property-animation-techniques-overview.md)。  
  
<a name="animation_types"></a>
## <a name="path-animation-types"></a>路徑動畫類型  
 由於動畫會產生屬性值，因此針對不同的屬性類型會有不同的動畫類型。 要為<xref:System.Double>採用 （如<xref:System.Windows.Media.TranslateTransform.X%2A>屬性<xref:System.Windows.Media.TranslateTransform>） 的屬性設置動畫，請使用生成<xref:System.Double>值的動畫。 要為採用<xref:System.Windows.Point>的屬性設置動畫，請使用生成<xref:System.Windows.Point>值的動畫，等等。  
  
 路徑動畫類屬於命名空間<xref:System.Windows.Media.Animation>，並使用以下命名約定：  
  
 * \<鍵入>*`AnimationUsingPath`  
  
 * \<類型>* 是類動畫的數值型別。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供下列路徑動畫類別。  
  
|屬性類型|對應路徑動畫類別|範例|  
|-------------------|----------------------------------------|-------------|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|[沿著路徑建立物件的動畫 (Double 動畫)](how-to-animate-an-object-along-a-path-double-animation.md)|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>|[沿著路徑建立物件的動畫 (矩陣動畫)](how-to-animate-an-object-along-a-path-matrix-animation.md)|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|[沿著路徑建立物件的動畫 (點動畫)](how-to-animate-an-object-along-a-path-point-animation.md)|  
  
 從<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath><xref:System.Windows.Media.Matrix>生成值從<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.PathGeometry%2A>其 。 當 與<xref:System.Windows.Media.MatrixTransform>中使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>時，可以沿路徑移動物件。 如果將 的屬性<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A><xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>設置為`true`，它還會沿路徑的曲線旋轉物件。  
  
 A <xref:System.Windows.Media.Animation.PointAnimationUsingPath> <xref:System.Windows.Point>從 其<xref:System.Windows.Media.Animation.PointAnimationUsingPath.PathGeometry%2A>的 x 座標和 y 座標生成值。 通過使用<xref:System.Windows.Media.Animation.PointAnimationUsingPath>對獲取<xref:System.Windows.Point>值的屬性設置動畫，可以沿路徑移動物件。 無法<xref:System.Windows.Media.Animation.PointAnimationUsingPath>旋轉物件。  
  
 從<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath><xref:System.Double>生成值從<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>其 。 通過設置屬性<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.Source%2A>，可以指定<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>路徑的 x 座標、y 座標還是角度作為其輸出。 可以使用<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>旋轉物件或沿 X 軸或 y 軸移動物件。  
  
<a name="pathanimationinput"></a>
## <a name="path-animation-input"></a>路徑動畫輸入  
 每個路徑動畫類都提供了<xref:System.Windows.Media.PathGeometry>用於指定其輸入的屬性。 路徑動畫使用<xref:System.Windows.Media.PathGeometry>生成其輸出值。 該<xref:System.Windows.Media.PathGeometry>類允許您描述由弧、曲線和線組成的多個複雜圖形。  
  
 在 的核心是<xref:System.Windows.Media.PathGeometry><xref:System.Windows.Media.PathFigure>物件的集合;這些物件之所以如此命名，是因為每個圖形都描述了 中的<xref:System.Windows.Media.PathGeometry>離散形狀。 每個<xref:System.Windows.Media.PathFigure>物件由一個或多個<xref:System.Windows.Media.PathSegment>物件組成，每個物件都描述了圖形的一段。  
  
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
  
 中的線段<xref:System.Windows.Media.PathFigure>合併為單個幾何形狀，該形狀使用線段的端點作為下一個段的起點。 的屬性<xref:System.Windows.Media.PathFigure.StartPoint%2A><xref:System.Windows.Media.PathFigure>指定從中繪製第一個段的點。 每個後續區段都會從前一個區段的結束點開始。 例如，`10,50``10,150`可以通過將<xref:System.Windows.Media.PathFigure.StartPoint%2A>屬性設置為 和`10,50`創建<xref:System.Windows.Media.LineSegment>屬性<xref:System.Windows.Media.LineSegment.Point%2A>設置為 的`10,150`  
  
 有關<xref:System.Windows.Media.PathGeometry>物件的詳細資訊，請參閱[幾何概述](geometry-overview.md)。  
  
 在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中，還可以使用特殊的縮寫語法來設置<xref:System.Windows.Media.PathGeometry.Figures%2A>的屬性。 <xref:System.Windows.Media.PathGeometry> 有關詳細資訊，請參閱[路徑標記語法](path-markup-syntax.md)概述。  
  
 有關[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]示例中使用的路徑語法的詳細資訊，請參閱[路徑標記語法](path-markup-syntax.md)概述。  
  
## <a name="see-also"></a>另請參閱

- [路徑動畫範例](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [路徑標記語法](path-markup-syntax.md)
- [路徑動畫操作說明主題](path-animation-how-to-topics.md)
- [動畫概觀](animation-overview.md)
- [屬性動畫技術概觀](property-animation-techniques-overview.md)
