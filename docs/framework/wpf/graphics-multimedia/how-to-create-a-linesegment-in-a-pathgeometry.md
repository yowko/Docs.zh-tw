---
title: HOW TO：在 PathGeometry 中建立 LineSegment
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- line segments [WPF], creating
- graphics [WPF], line segments
ms.assetid: 0155ed47-a20d-49a7-a306-186d8e07fbc4
ms.openlocfilehash: a6862ab02c288f9cfd1fac4a8c22079b0cf91016
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356178"
---
# <a name="how-to-create-a-linesegment-in-a-pathgeometry"></a><span data-ttu-id="20da2-102">HOW TO：在 PathGeometry 中建立 LineSegment</span><span class="sxs-lookup"><span data-stu-id="20da2-102">How to: Create a LineSegment in a PathGeometry</span></span>
<span data-ttu-id="20da2-103">這個範例會示範如何建立線段 。</span><span class="sxs-lookup"><span data-stu-id="20da2-103">This example shows how to create a line segment.</span></span> <span data-ttu-id="20da2-104">若要建立線段，使用<xref:System.Windows.Media.PathGeometry>， <xref:System.Windows.Media.PathFigure>，和<xref:System.Windows.Media.LineSegment>類別。</span><span class="sxs-lookup"><span data-stu-id="20da2-104">To create a line segment, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.LineSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20da2-105">範例</span><span class="sxs-lookup"><span data-stu-id="20da2-105">Example</span></span>  
 <span data-ttu-id="20da2-106">下列範例繪製<xref:System.Windows.Media.LineSegment>從 （10，50） 到 （200，70）。</span><span class="sxs-lookup"><span data-stu-id="20da2-106">The following examples draw a <xref:System.Windows.Media.LineSegment> from (10, 50) to (200, 70).</span></span> <span data-ttu-id="20da2-107">下圖顯示產生<xref:System.Windows.Media.LineSegment>; 已加入格線背景以顯示座標系統。</span><span class="sxs-lookup"><span data-stu-id="20da2-107">The following illustration shows the resulting <xref:System.Windows.Media.LineSegment>; a grid background was added to show the coordinate system.</span></span>  
  
 <span data-ttu-id="20da2-108">![PathFigure 中的 LineSegment](./media/graphicsmm-pathgeometrylinesegment.png "graphicsmm_pathgeometrylinesegment")</span><span class="sxs-lookup"><span data-stu-id="20da2-108">![A LineSegment in a PathFigure](./media/graphicsmm-pathgeometrylinesegment.png "graphicsmm_pathgeometrylinesegment")</span></span>  
<span data-ttu-id="20da2-109">從 (10,50) 到 (200,70) 繪製的 LineSegment</span><span class="sxs-lookup"><span data-stu-id="20da2-109">A LineSegment drawn from (10,50) to (200,70)</span></span>  
  
 <span data-ttu-id="20da2-110">[xaml]</span><span class="sxs-lookup"><span data-stu-id="20da2-110">[xaml]</span></span>  
  
 <span data-ttu-id="20da2-111">在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中，您可以使用屬性語法來描述路徑。</span><span class="sxs-lookup"><span data-stu-id="20da2-111">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may use attribute syntax to describe a path.</span></span>  
  
```xaml  
<Path Stroke="Black" StrokeThickness="1"    
  Data="M 10,50 L 200,70" />  
```  
  
 <span data-ttu-id="20da2-112">[xaml]</span><span class="sxs-lookup"><span data-stu-id="20da2-112">[xaml]</span></span>  
  
 <span data-ttu-id="20da2-113">(請注意，此屬性語法實際上會建立<xref:System.Windows.Media.StreamGeometry>，輕量版<xref:System.Windows.Media.PathGeometry>。</span><span class="sxs-lookup"><span data-stu-id="20da2-113">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="20da2-114">如需詳細資訊，請參閱[路徑標記語法](path-markup-syntax.md)頁面。)</span><span class="sxs-lookup"><span data-stu-id="20da2-114">For more information, see the [Path Markup Syntax](path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="20da2-115">在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中，您也可以使用物件元素語法來繪製線段。</span><span class="sxs-lookup"><span data-stu-id="20da2-115">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you may also draw a line segment by using object element syntax.</span></span> <span data-ttu-id="20da2-116">下列範例相當於先前的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="20da2-116">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
```xaml  
<Path Stroke="Black" StrokeThickness="1">  
  <Path.Data>  
    <PathGeometry>  
      <PathFigure StartPoint="10,50">  
        <LineSegment Point="200,70" />  
      </PathFigure>  
    </PathGeometry>  
  </Path.Data>  
</Path>  
```  
  
```csharp  
PathFigure myPathFigure = new PathFigure();  
myPathFigure.StartPoint = new Point(10, 50);  
  
LineSegment myLineSegment = new LineSegment();  
myLineSegment.Point = new Point(200, 70);  
  
PathSegmentCollection myPathSegmentCollection = new PathSegmentCollection();  
myPathSegmentCollection.Add(myLineSegment);  
  
myPathFigure.Segments = myPathSegmentCollection;  
  
PathFigureCollection myPathFigureCollection = new PathFigureCollection();  
myPathFigureCollection.Add(myPathFigure);  
  
PathGeometry myPathGeometry = new PathGeometry();  
myPathGeometry.Figures = myPathFigureCollection;  
  
Path myPath = new Path();  
myPath.Stroke = Brushes.Black;  
myPath.StrokeThickness = 1;  
myPath.Data = myPathGeometry;  
```  
  
```vb  
Dim myPathFigure As New PathFigure()  
            myPathFigure.StartPoint = New Point(10, 50)  
  
            Dim myLineSegment As New LineSegment()  
            myLineSegment.Point = New Point(200, 70)  
  
            Dim myPathSegmentCollection As New PathSegmentCollection()  
            myPathSegmentCollection.Add(myLineSegment)  
  
            myPathFigure.Segments = myPathSegmentCollection  
  
            Dim myPathFigureCollection As New PathFigureCollection()  
            myPathFigureCollection.Add(myPathFigure)  
  
            Dim myPathGeometry As New PathGeometry()  
            myPathGeometry.Figures = myPathFigureCollection  
  
            Dim myPath As New Path()  
            myPath.Stroke = Brushes.Black  
            myPath.StrokeThickness = 1  
            myPath.Data = myPathGeometry  
```  
  
 <span data-ttu-id="20da2-117">這個範例屬於較大型的範例；如需完整範例，請參閱[幾何範例](https://go.microsoft.com/fwlink/?LinkID=159989)。</span><span class="sxs-lookup"><span data-stu-id="20da2-117">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20da2-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20da2-118">See also</span></span>
- <xref:System.Windows.Media.PathFigure>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.GeometryDrawing>
- <xref:System.Windows.Shapes.Path>
- [<span data-ttu-id="20da2-119">幾何概觀</span><span class="sxs-lookup"><span data-stu-id="20da2-119">Geometry Overview</span></span>](geometry-overview.md)
