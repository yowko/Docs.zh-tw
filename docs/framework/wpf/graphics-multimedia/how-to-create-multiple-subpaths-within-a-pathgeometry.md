---
title: HOW TO：在 PathGeometry 內建立多個子路徑
ms.date: 03/30/2017
helpviewer_keywords:
- multiple subpaths [WPF]
- graphics [WPF], subpaths
- subpaths [WPF]
ms.assetid: 104a862c-dde2-4e62-ac87-80660dd1681c
ms.openlocfilehash: 286075448cd6a343f8a7b15b2b5005f840f68e1d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111744"
---
# <a name="how-to-create-multiple-subpaths-within-a-pathgeometry"></a><span data-ttu-id="c1760-102">HOW TO：在 PathGeometry 內建立多個子路徑</span><span class="sxs-lookup"><span data-stu-id="c1760-102">How to: Create Multiple Subpaths Within a PathGeometry</span></span>
<span data-ttu-id="c1760-103">此範例示範如何建立多個子路徑中的<xref:System.Windows.Media.PathGeometry>。</span><span class="sxs-lookup"><span data-stu-id="c1760-103">This example shows how to create multiple subpaths in a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="c1760-104">若要建立多個子路徑，您建立<xref:System.Windows.Media.PathFigure>的每一個子路徑。</span><span class="sxs-lookup"><span data-stu-id="c1760-104">To create multiple subpaths, you create a <xref:System.Windows.Media.PathFigure> for each subpath.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1760-105">範例</span><span class="sxs-lookup"><span data-stu-id="c1760-105">Example</span></span>  
 <span data-ttu-id="c1760-106">下列範例會建立兩個路徑，每一個三角形。</span><span class="sxs-lookup"><span data-stu-id="c1760-106">The following example creates two subpaths, each one a triangle.</span></span>  
  
 [!code-xaml[GeometrySample#38](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#38)]  
  
 <span data-ttu-id="c1760-107">下列範例示範如何藉由建立多個子路徑<xref:System.Windows.Shapes.Path>和[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]屬性語法。</span><span class="sxs-lookup"><span data-stu-id="c1760-107">The following example shows how to create multiple subpaths by using a <xref:System.Windows.Shapes.Path> and [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribute syntax.</span></span> <span data-ttu-id="c1760-108">每個`M`會建立新的子路徑，讓此範例會建立兩個路徑每個繪製三角形。</span><span class="sxs-lookup"><span data-stu-id="c1760-108">Each `M` creates a new subpath so that the example creates two subpaths that each draw a triangle.</span></span>  
  
 [!code-xaml[GeometrySample#58](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#58)]  
  
 <span data-ttu-id="c1760-109">(請注意，此屬性語法實際上會建立<xref:System.Windows.Media.StreamGeometry>，輕量版<xref:System.Windows.Media.PathGeometry>。</span><span class="sxs-lookup"><span data-stu-id="c1760-109">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="c1760-110">如需詳細資訊，請參閱[路徑標記語法](path-markup-syntax.md)頁面。)</span><span class="sxs-lookup"><span data-stu-id="c1760-110">For more information, see the [Path Markup Syntax](path-markup-syntax.md) page.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1760-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1760-111">See also</span></span>

- [<span data-ttu-id="c1760-112">幾何概觀</span><span class="sxs-lookup"><span data-stu-id="c1760-112">Geometry Overview</span></span>](geometry-overview.md)
