---
title: HOW TO：建立二次方貝茲曲線
ms.date: 03/30/2017
helpviewer_keywords:
- Bezier curves [WPF], creating
- quadratic Bezier curves [WPF], creating
- graphics [WPF], quadratic Bezier curves
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
ms.openlocfilehash: a5d424f3fda3957bf54d7073d41d9fe2dabb1736
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650089"
---
# <a name="how-to-create-a-quadratic-bezier-curve"></a><span data-ttu-id="1b99f-102">HOW TO：建立二次方貝茲曲線</span><span class="sxs-lookup"><span data-stu-id="1b99f-102">How to: Create a Quadratic Bezier Curve</span></span>
<span data-ttu-id="1b99f-103">此範例示範如何建立二次方貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="1b99f-103">This example shows how to create a quadratic Bezier curve.</span></span>  <span data-ttu-id="1b99f-104">若要建立二次方貝茲曲線，使用<xref:System.Windows.Media.PathGeometry>， <xref:System.Windows.Media.PathFigure>，和<xref:System.Windows.Media.QuadraticBezierSegment>類別。</span><span class="sxs-lookup"><span data-stu-id="1b99f-104">To create a quadratic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.QuadraticBezierSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b99f-105">範例</span><span class="sxs-lookup"><span data-stu-id="1b99f-105">Example</span></span>  
 <span data-ttu-id="1b99f-106">在下列範例中，會從 (10100) 到 (300100) 繪製二次方貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="1b99f-106">In the following examples, a quadratic Bezier curve is drawn from (10,100) to (300,100).</span></span> <span data-ttu-id="1b99f-107">曲線具有 (200200) 的控制點。</span><span class="sxs-lookup"><span data-stu-id="1b99f-107">The curve has a control point of (200,200).</span></span>  
  
 <span data-ttu-id="1b99f-108">[xaml]</span><span class="sxs-lookup"><span data-stu-id="1b99f-108">[xaml]</span></span>  
  
 <span data-ttu-id="1b99f-109">在  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，您可以使用屬性語法來描述路徑。</span><span class="sxs-lookup"><span data-stu-id="1b99f-109">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#54](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 <span data-ttu-id="1b99f-110">[xaml]</span><span class="sxs-lookup"><span data-stu-id="1b99f-110">[xaml]</span></span>  
  
 <span data-ttu-id="1b99f-111">(請注意，此屬性語法實際上會建立<xref:System.Windows.Media.StreamGeometry>，輕量版<xref:System.Windows.Media.PathGeometry>。</span><span class="sxs-lookup"><span data-stu-id="1b99f-111">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="1b99f-112">如需詳細資訊，請參閱[路徑標記語法](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)頁面。)</span><span class="sxs-lookup"><span data-stu-id="1b99f-112">For more information, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="1b99f-113">在  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您可能也會繪製二次方貝茲曲線，使用物件元素語法。</span><span class="sxs-lookup"><span data-stu-id="1b99f-113">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you may also draw a quadratic Bezier curve using object element syntax.</span></span> <span data-ttu-id="1b99f-114">下列範例相當於先前的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="1b99f-114">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="1b99f-115">這個範例屬於較大型的範例；如需完整範例，請參閱[幾何範例](https://go.microsoft.com/fwlink/?LinkID=159989)。</span><span class="sxs-lookup"><span data-stu-id="1b99f-115">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b99f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b99f-116">See also</span></span>
- [<span data-ttu-id="1b99f-117">建立橢圓形弧線</span><span class="sxs-lookup"><span data-stu-id="1b99f-117">Create an Elliptical Arc</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)
- [<span data-ttu-id="1b99f-118">建立三次方貝茲曲線</span><span class="sxs-lookup"><span data-stu-id="1b99f-118">Create a Cubic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)
