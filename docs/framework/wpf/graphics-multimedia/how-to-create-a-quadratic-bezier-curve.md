---
title: 如何：建立二次方貝茲曲線
ms.date: 03/30/2017
helpviewer_keywords:
- Bezier curves [WPF], creating
- quadratic Bezier curves [WPF], creating
- graphics [WPF], quadratic Bezier curves
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
ms.openlocfilehash: 9d389125b6ad09833a16b64cb8f498cc20d4e79c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558887"
---
# <a name="how-to-create-a-quadratic-bezier-curve"></a><span data-ttu-id="a393d-102">如何：建立二次方貝茲曲線</span><span class="sxs-lookup"><span data-stu-id="a393d-102">How to: Create a Quadratic Bezier Curve</span></span>
<span data-ttu-id="a393d-103">這個範例示範如何建立二次方貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="a393d-103">This example shows how to create a quadratic Bezier curve.</span></span>  <span data-ttu-id="a393d-104">若要建立二次方貝茲曲線，使用<xref:System.Windows.Media.PathGeometry>， <xref:System.Windows.Media.PathFigure>，和<xref:System.Windows.Media.QuadraticBezierSegment>類別。</span><span class="sxs-lookup"><span data-stu-id="a393d-104">To create a quadratic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.QuadraticBezierSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a393d-105">範例</span><span class="sxs-lookup"><span data-stu-id="a393d-105">Example</span></span>  
 <span data-ttu-id="a393d-106">在下列範例中，二次方貝茲曲線是取自 (10100) 到 (300100)。</span><span class="sxs-lookup"><span data-stu-id="a393d-106">In the following examples, a quadratic Bezier curve is drawn from (10,100) to (300,100).</span></span> <span data-ttu-id="a393d-107">曲線有 (200200) 的控制點。</span><span class="sxs-lookup"><span data-stu-id="a393d-107">The curve has a control point of (200,200).</span></span>  
  
 <span data-ttu-id="a393d-108">[xaml]</span><span class="sxs-lookup"><span data-stu-id="a393d-108">[xaml]</span></span>  
  
 <span data-ttu-id="a393d-109">在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，您可以使用屬性語法來描述路徑。</span><span class="sxs-lookup"><span data-stu-id="a393d-109">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#54](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 <span data-ttu-id="a393d-110">[xaml]</span><span class="sxs-lookup"><span data-stu-id="a393d-110">[xaml]</span></span>  
  
 <span data-ttu-id="a393d-111">(請注意，此屬性的語法確實建立<xref:System.Windows.Media.StreamGeometry>的輕量型版本<xref:System.Windows.Media.PathGeometry>。</span><span class="sxs-lookup"><span data-stu-id="a393d-111">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="a393d-112">如需詳細資訊，請參閱[路徑標記語法](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)頁面。)</span><span class="sxs-lookup"><span data-stu-id="a393d-112">For more information, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="a393d-113">在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您可能也會繪製二次方貝茲曲線，使用物件項目語法。</span><span class="sxs-lookup"><span data-stu-id="a393d-113">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you may also draw a quadratic Bezier curve using object element syntax.</span></span> <span data-ttu-id="a393d-114">下列範例相當於先前的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="a393d-114">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="a393d-115">這個範例屬於較大型的範例；如需完整範例，請參閱[幾何範例](http://go.microsoft.com/fwlink/?LinkID=159989)。</span><span class="sxs-lookup"><span data-stu-id="a393d-115">This example is part of larger sample; for the complete sample, see the [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a393d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a393d-116">See Also</span></span>  
 [<span data-ttu-id="a393d-117">建立橢圓形弧線</span><span class="sxs-lookup"><span data-stu-id="a393d-117">Create an Elliptical Arc</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)  
 [<span data-ttu-id="a393d-118">建立三次方貝茲曲線</span><span class="sxs-lookup"><span data-stu-id="a393d-118">Create a Cubic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)
