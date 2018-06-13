---
title: 如何：在 PathGeometry 內建立多個子路徑
ms.date: 03/30/2017
helpviewer_keywords:
- multiple subpaths [WPF]
- graphics [WPF], subpaths
- subpaths [WPF]
ms.assetid: 104a862c-dde2-4e62-ac87-80660dd1681c
ms.openlocfilehash: 5b129b1bacb5dc2cba87376e8df70e115a5ebd72
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559319"
---
# <a name="how-to-create-multiple-subpaths-within-a-pathgeometry"></a><span data-ttu-id="2c4b6-102">如何：在 PathGeometry 內建立多個子路徑</span><span class="sxs-lookup"><span data-stu-id="2c4b6-102">How to: Create Multiple Subpaths Within a PathGeometry</span></span>
<span data-ttu-id="2c4b6-103">這個範例示範如何建立多個子路徑中的<xref:System.Windows.Media.PathGeometry>。</span><span class="sxs-lookup"><span data-stu-id="2c4b6-103">This example shows how to create multiple subpaths in a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="2c4b6-104">若要建立多個路徑，您建立<xref:System.Windows.Media.PathFigure>的每一個子路徑。</span><span class="sxs-lookup"><span data-stu-id="2c4b6-104">To create multiple subpaths, you create a <xref:System.Windows.Media.PathFigure> for each subpath.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c4b6-105">範例</span><span class="sxs-lookup"><span data-stu-id="2c4b6-105">Example</span></span>  
 <span data-ttu-id="2c4b6-106">下列範例會建立兩個路徑，每個三角形。</span><span class="sxs-lookup"><span data-stu-id="2c4b6-106">The following example creates two subpaths, each one a triangle.</span></span>  
  
 [!code-xaml[GeometrySample#38](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#38)]  
  
 <span data-ttu-id="2c4b6-107">下列範例示範如何藉由建立多個子路徑<xref:System.Windows.Shapes.Path>和[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]屬性語法。</span><span class="sxs-lookup"><span data-stu-id="2c4b6-107">The following example shows how to create multiple subpaths by using a <xref:System.Windows.Shapes.Path> and [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribute syntax.</span></span> <span data-ttu-id="2c4b6-108">每個`M`會建立新的子路徑，讓此範例會建立每個繪製三角形的兩個路徑。</span><span class="sxs-lookup"><span data-stu-id="2c4b6-108">Each `M` creates a new subpath so that the example creates two subpaths that each draw a triangle.</span></span>  
  
 [!code-xaml[GeometrySample#58](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#58)]  
  
 <span data-ttu-id="2c4b6-109">(請注意，此屬性的語法確實建立<xref:System.Windows.Media.StreamGeometry>的輕量型版本<xref:System.Windows.Media.PathGeometry>。</span><span class="sxs-lookup"><span data-stu-id="2c4b6-109">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="2c4b6-110">如需詳細資訊，請參閱[路徑標記語法](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)頁面。)</span><span class="sxs-lookup"><span data-stu-id="2c4b6-110">For more information, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c4b6-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c4b6-111">See Also</span></span>  
 [<span data-ttu-id="2c4b6-112">幾何概觀</span><span class="sxs-lookup"><span data-stu-id="2c4b6-112">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
