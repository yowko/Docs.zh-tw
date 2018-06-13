---
title: 如何：使用 StreamGeometry 建立圖案
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], shapes
- shapes [WPF], creating with StreamGeometry class
ms.assetid: 08f7c8ce-074b-49cd-9aba-cc9592d4ee51
ms.openlocfilehash: 54819f62b262227017e12b2066a0747107b68900
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560361"
---
# <a name="how-to-create-a-shape-using-a-streamgeometry"></a><span data-ttu-id="ecca1-102">如何：使用 StreamGeometry 建立圖案</span><span class="sxs-lookup"><span data-stu-id="ecca1-102">How to: Create a Shape Using a StreamGeometry</span></span>
<span data-ttu-id="ecca1-103"><xref:System.Windows.Media.StreamGeometry> 輕量級替代方案<xref:System.Windows.Media.PathGeometry>建立幾何圖案。</span><span class="sxs-lookup"><span data-stu-id="ecca1-103"><xref:System.Windows.Media.StreamGeometry> is light-weight alternative to <xref:System.Windows.Media.PathGeometry> for creating geometric shapes.</span></span> <span data-ttu-id="ecca1-104">使用<xref:System.Windows.Media.StreamGeometry>何時該添來描述複雜的幾何，但不是想支援資料繫結、 動畫或修改的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="ecca1-104">Use a <xref:System.Windows.Media.StreamGeometry> when you need to describe a complex geometry but do not want the overhead of supporting data binding, animation, or modification.</span></span> <span data-ttu-id="ecca1-105">例如，由於其效率，<xref:System.Windows.Media.StreamGeometry>類別是用來描述裝飾項不錯的選擇。</span><span class="sxs-lookup"><span data-stu-id="ecca1-105">For example, because of its efficiency, the <xref:System.Windows.Media.StreamGeometry> class is a good choice for describing adorners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecca1-106">範例</span><span class="sxs-lookup"><span data-stu-id="ecca1-106">Example</span></span>  
 <span data-ttu-id="ecca1-107">下列範例會使用屬性語法建立三角形<xref:System.Windows.Media.StreamGeometry>中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ecca1-107">The following example uses attribute syntax to create a triangular <xref:System.Windows.Media.StreamGeometry> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 <span data-ttu-id="ecca1-108">如需有關<xref:System.Windows.Media.StreamGeometry>屬性語法，請參閱[路徑標記語法](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)頁面。</span><span class="sxs-lookup"><span data-stu-id="ecca1-108">For more information about <xref:System.Windows.Media.StreamGeometry> attribute syntax, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecca1-109">範例</span><span class="sxs-lookup"><span data-stu-id="ecca1-109">Example</span></span>  
 <span data-ttu-id="ecca1-110">下一個範例會使用<xref:System.Windows.Media.StreamGeometry>來定義三角形，程式碼中。</span><span class="sxs-lookup"><span data-stu-id="ecca1-110">The next example uses a <xref:System.Windows.Media.StreamGeometry> to define a triangle in code.</span></span> <span data-ttu-id="ecca1-111">此範例會先建立<xref:System.Windows.Media.StreamGeometry>，然後取得<xref:System.Windows.Media.StreamGeometryContext>並使用它來描述三角形。</span><span class="sxs-lookup"><span data-stu-id="ecca1-111">First, the example creates a <xref:System.Windows.Media.StreamGeometry>, then obtains a <xref:System.Windows.Media.StreamGeometryContext> and uses it to describe the triangle.</span></span>  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryTriangleExample.cs#streamgeometrytriangleexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometrytriangleexample.vb#streamgeometrytriangleexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="ecca1-112">範例</span><span class="sxs-lookup"><span data-stu-id="ecca1-112">Example</span></span>  
 <span data-ttu-id="ecca1-113">下一個範例會建立方法，以使用<xref:System.Windows.Media.StreamGeometry>和<xref:System.Windows.Media.StreamGeometryContext>定義幾何形狀，根據指定的參數。</span><span class="sxs-lookup"><span data-stu-id="ecca1-113">The next example creates a method that uses a <xref:System.Windows.Media.StreamGeometry> and <xref:System.Windows.Media.StreamGeometryContext> to define a geometric shape based on specified parameters.</span></span>  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryExample.cs#streamgeometryexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometryexample.vb#streamgeometryexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="ecca1-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ecca1-114">See Also</span></span>  
 <xref:System.Windows.Media.PathGeometry>  
 <xref:System.Windows.Media.StreamGeometry>  
 <xref:System.Windows.Media.StreamGeometryContext>  
 [<span data-ttu-id="ecca1-115">使用 PathGeometry 建立圖案</span><span class="sxs-lookup"><span data-stu-id="ecca1-115">Create a Shape by Using a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)  
 [<span data-ttu-id="ecca1-116">幾何概觀</span><span class="sxs-lookup"><span data-stu-id="ecca1-116">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
