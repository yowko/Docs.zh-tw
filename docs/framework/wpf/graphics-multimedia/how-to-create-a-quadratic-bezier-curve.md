---
title: 如何：建立二次方貝茲曲線
ms.date: 03/30/2017
helpviewer_keywords:
- Bezier curves [WPF], creating
- quadratic Bezier curves [WPF], creating
- graphics [WPF], quadratic Bezier curves
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
ms.openlocfilehash: caaf967b7cb5447d86dd031beeb16195413b0393
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452067"
---
# <a name="how-to-create-a-quadratic-bezier-curve"></a><span data-ttu-id="cf729-102">如何：建立二次方貝茲曲線</span><span class="sxs-lookup"><span data-stu-id="cf729-102">How to: Create a Quadratic Bezier Curve</span></span>
<span data-ttu-id="cf729-103">這個範例顯示如何建立二次方貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="cf729-103">This example shows how to create a quadratic Bezier curve.</span></span>  <span data-ttu-id="cf729-104">若要建立二次方貝茲曲線，請使用 [<xref:System.Windows.Media.PathGeometry>]、[<xref:System.Windows.Media.PathFigure>] 和 [<xref:System.Windows.Media.QuadraticBezierSegment>] 類別。</span><span class="sxs-lookup"><span data-stu-id="cf729-104">To create a quadratic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.QuadraticBezierSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf729-105">範例</span><span class="sxs-lookup"><span data-stu-id="cf729-105">Example</span></span>  
 <span data-ttu-id="cf729-106">在下列範例中，會從（10100）繪製二次方貝茲曲線至（300100）。</span><span class="sxs-lookup"><span data-stu-id="cf729-106">In the following examples, a quadratic Bezier curve is drawn from (10,100) to (300,100).</span></span> <span data-ttu-id="cf729-107">曲線的控制點為（200200）。</span><span class="sxs-lookup"><span data-stu-id="cf729-107">The curve has a control point of (200,200).</span></span>  
  
 <span data-ttu-id="cf729-108">[xaml]</span><span class="sxs-lookup"><span data-stu-id="cf729-108">[xaml]</span></span>  
  
 <span data-ttu-id="cf729-109">在 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中，您可以使用屬性語法來描述路徑。</span><span class="sxs-lookup"><span data-stu-id="cf729-109">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#54](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 <span data-ttu-id="cf729-110">[xaml]</span><span class="sxs-lookup"><span data-stu-id="cf729-110">[xaml]</span></span>  
  
 <span data-ttu-id="cf729-111">（請注意，此屬性語法實際上會建立 <xref:System.Windows.Media.StreamGeometry>，也就是較輕量的 <xref:System.Windows.Media.PathGeometry>版本。</span><span class="sxs-lookup"><span data-stu-id="cf729-111">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="cf729-112">如需詳細資訊，請參閱[路徑標記語法](path-markup-syntax.md)頁面。)</span><span class="sxs-lookup"><span data-stu-id="cf729-112">For more information, see the [Path Markup Syntax](path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="cf729-113">在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中，您也可以使用物件元素語法繪製二次方貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="cf729-113">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you may also draw a quadratic Bezier curve using object element syntax.</span></span> <span data-ttu-id="cf729-114">下列範例相當於先前的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="cf729-114">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="cf729-115">這個範例屬於較大型的範例；如需完整範例，請參閱[幾何範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry)。</span><span class="sxs-lookup"><span data-stu-id="cf729-115">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf729-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf729-116">See also</span></span>

- [<span data-ttu-id="cf729-117">建立橢圓形弧線</span><span class="sxs-lookup"><span data-stu-id="cf729-117">Create an Elliptical Arc</span></span>](how-to-create-an-elliptical-arc.md)
- [<span data-ttu-id="cf729-118">建立三次方貝茲曲線</span><span class="sxs-lookup"><span data-stu-id="cf729-118">Create a Cubic Bezier Curve</span></span>](how-to-create-a-cubic-bezier-curve.md)
